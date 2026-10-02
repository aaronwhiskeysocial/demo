# imessage-claude — Implementation Plan

An always-on Mac service that turns iMessage into a Claude chat. BlueBubbles Server
(running on the same Mac, signed into iMessage) delivers inbound messages to this
bridge over a local webhook; the bridge calls Claude and sends the reply back
through the BlueBubbles REST API. It runs as a launchd LaunchAgent so it starts at
login and restarts itself if it crashes.

This document is written so that a less capable model can implement it without
further design decisions. Follow it in order. Every step ends with a check that
must pass before the next step starts.

---

## 0. Rules for the executing model

1. Work through the steps in order. Do not skip a step's tests.
2. After every step run `npm run typecheck && npm test` from `imessage-claude/`. Both must be clean.
3. Commit after every step. Message format: `imessage-claude: step N — <short title>`.
4. Runtime dependency is `@anthropic-ai/sdk` only. Do not add any other runtime dependency.
   Dev dependencies are already installed (`typescript`, `@types/node`). Do not add more.
5. `package.json` and `tsconfig.json` already exist. Do not change them unless a step says so.
6. TypeScript constraints enforced by `tsconfig.json` (`erasableSyntaxOnly`, `verbatimModuleSyntax`):
   - No `enum`, no `namespace`, no constructor parameter properties (`constructor(private x)`), no `declare` fields.
     Use `as const` objects and union types instead of enums.
   - Type-only imports must use `import type { X } from "./y.ts"`.
   - Every relative import ends in `.ts` (example: `import { loadConfig } from "./config.ts"`).
     `tsc` rewrites them to `.js` in `dist/`; Node runs `src/*.ts` directly for tests and `npm run dev`.
   - `__dirname` does not exist (ESM). Use `path.dirname(fileURLToPath(import.meta.url))`.
7. Tests live in `test/*.test.ts`, use `node:test` and `node:assert/strict`, and run with `node --test "test/**/*.test.ts"` (quote the glob; a bare directory argument does not work on Node 22).
   Tests import source from `../src/<file>.ts`. Tests must not touch the network, the real
   home directory, or the real Anthropic API. Use `fs.mkdtempSync(path.join(os.tmpdir(), "imc-"))` for data dirs.
8. Never log or print `BLUEBUBBLES_PASSWORD` or `ANTHROPIC_API_KEY`. The logger redacts query strings.
9. Do not "remember" a different BlueBubbles or Anthropic API shape from training data. Section 2 is verified
   against the BlueBubbles server source and the installed SDK (`@anthropic-ai/sdk` 0.131). Use it as written.
10. When the plan says "exact signature", implement that signature. Other code may name helpers freely.
11. Keep each file focused. If a file grows past ~400 lines, split it, but keep the exported names in this plan.

---

## 1. What we are building

**Goal.** Text the Mac's iMessage address from any iPhone and get a Claude reply in the same
thread, with typing indicators, read receipts, photo understanding, multi-bubble replies for
long answers, and slash commands (`/reset`, `/help`, ...). One command installs it as a
launchd agent; one command diagnoses the setup.

**Recommended deployment.** A Mac mini signed into a *dedicated* Apple ID for the assistant
(not the owner's personal Apple ID). Messages you send to your own Apple ID arrive with
`isFromMe: true` and cannot be distinguished from the bridge's own replies, so a dedicated
Apple ID is what makes "text the bot from my phone" work. The README must say this.

**Non-goals (v1).** Sending images or files back; voice messages; SMS relay specifics;
multi-user web UI; any cloud component. The bridge binds to `127.0.0.1` and talks only to
the local BlueBubbles server and `api.anthropic.com`.

---

## 2. Verified external contracts (do not deviate)

### 2.1 BlueBubbles REST API

- Base URL: `BLUEBUBBLES_URL` (default `http://127.0.0.1:1234`).
- Auth on **every** request: query parameter `password=<BLUEBUBBLES_PASSWORD>` (the server also
  accepts `guid` and `token` as aliases; use `password`).
- Response envelope for every endpoint:
  `{ "status": <int>, "message": <string>, "data": <any>, "error"?: { "type": string, "error": string } }`.
  Treat HTTP status >= 400 or `status >= 400` in the body as failure.
- Chat GUIDs contain `;` and `+` (examples: `iMessage;-;+15551234567` for a DM,
  `iMessage;+;chat123456789` for a group, `any;-;+15551234567` also valid for sending).
  **Always `encodeURIComponent()` a chat GUID when it appears in a URL path.**

| Purpose | Method and path | Body / notes |
|---|---|---|
| Ping | `GET /api/v1/ping` | Reachability + password check. HTTP 200 and body `status === 200` means OK. |
| Server info | `GET /api/v1/server/info` | `data` is an object. Read `data.private_api` (boolean) and `data.helper_connected` (boolean) when present; also `data.server_version`, `data.os_version`. If the fields are absent treat Private API as unavailable. |
| Send text | `POST /api/v1/message/text` | JSON `{ chatGuid, tempGuid, message, method }`. `method` is `"apple-script"` or `"private-api"`. `tempGuid` is required for apple-script; always send one: `"imessage-claude-" + randomUUID()`. Optional `selectedMessageGuid` (reply-to; forces private-api). Response `data` is the sent message; read `data.guid` if it is a string. |
| Start typing | `POST /api/v1/chat/:chatGuid/typing` | No body. Private API only. Typing clears automatically when a message is sent. Do **not** call `DELETE .../typing` (server bug: it starts typing again). |
| Mark chat read | `POST /api/v1/chat/:chatGuid/read` | No body. Private API only. |
| React (tapback) | `POST /api/v1/message/react` | JSON `{ chatGuid, selectedMessageGuid, reaction }`, `reaction` in `love, like, dislike, laugh, emphasize, question` (prefix `-` removes). Private API only. Not used in v1 except as a stretch feature. |
| Download attachment | `GET /api/v1/attachment/:guid/download` | Raw bytes; `Content-Type` header gives the media type. |
| List webhooks | `GET /api/v1/webhook` | `data` is an array of `{ id: number, url: string, events: string[] }`. |
| Register webhook | `POST /api/v1/webhook` | JSON `{ url: string, events: string[] }`. Use `events: ["new-message"]`. |
| Delete webhook | `DELETE /api/v1/webhook/:id` | |

Private API (typing, read receipts, reactions, reply threading) requires the BlueBubbles
"Private API" helper to be enabled on the Mac. When it is not, sending still works with
`method: "apple-script"`. The bridge must never fail a reply because a Private API call failed:
typing/read calls are best-effort and their errors are logged at `debug`.

### 2.2 BlueBubbles webhook payload

BlueBubbles POSTs JSON to the registered URL with **no custom headers**, so the shared secret
must live in the URL itself. Payload shape for the event we register:

```json
{
  "type": "new-message",
  "data": {
    "guid": "p:0/ABCD-1234-...",
    "text": "Hey, what's up?",
    "isFromMe": false,
    "dateCreated": 1772642539012,
    "subject": null,
    "handle": { "address": "+15551234567", "service": "iMessage", "country": "US" },
    "attachments": [
      { "guid": "...", "mimeType": "image/jpeg", "transferName": "IMG_0001.jpeg", "totalBytes": 123456, "isSticker": false }
    ],
    "chats": [
      { "guid": "iMessage;-;+15551234567", "chatIdentifier": "+15551234567", "displayName": "",
        "participants": [ { "address": "+15551234567", "service": "iMessage" } ] }
    ],
    "associatedMessageGuid": null,
    "associatedMessageType": null,
    "balloonBundleId": null,
    "expressiveSendStyleId": null,
    "isAudioMessage": false,
    "hasPayloadData": false
  }
}
```

Facts to rely on:
- Our own outgoing replies come back as `new-message` with `isFromMe: true`.
- Tapbacks (reactions) arrive as `new-message` with `associatedMessageGuid` set and/or
  `associatedMessageType` non-null and non-zero (it may be a number like `2000` or a string).
- The same message can be delivered more than once. De-duplicate on `data.guid`.
- When a message has an attachment, `text` may be empty or contain U+FFFC (object replacement
  character). Strip U+FFFC before deciding whether the text is empty.
- `handle` can be `null` for `isFromMe` messages. `chats` may be empty in rare cases; ignore such messages.
- Group detection: `chat.guid` contains `;+;` **or** `chat.participants.length > 1`.

### 2.3 Claude API (installed SDK: `@anthropic-ai/sdk` 0.131)

Use the beta messages surface so server-side refusal fallbacks are available:

```ts
import Anthropic from "@anthropic-ai/sdk";
const client = new Anthropic({ timeout: 120_000 }); // apiKey comes from ANTHROPIC_API_KEY

const response = await client.beta.messages.create({
  model: "claude-opus-5-5",                         // default; configurable
  max_tokens: 2048,                                 // deliberately short: iMessage replies
  betas: ["server-side-fallback-2026-07-01"],       // only together with fallbacks:"default"
  fallbacks: "default",                             // Anthropic picks the fallback on a policy refusal
  thinking: { type: "adaptive" },                   // thinking is always on for Opus 5.5
  output_config: { effort: "low" },                 // low | medium | high | xhigh | max
  system: [
    { type: "text", text: STABLE_SYSTEM_PROMPT, cache_control: { type: "ephemeral" } },
    { type: "text", text: dynamicContext },         // date, chat info: AFTER the cached block
  ],
  messages,                                         // Anthropic.Beta.BetaMessageParam[]
  tools: webSearchEnabled ? [{ type: "web_search_20260209", name: "web_search", max_uses: 3 }] : undefined,
});
```

Rules:
- Model families and which parameters to send (implement as `requestProfile(model)` in `claude.ts`):
  - `claude-opus-5*`, `claude-sonnet-5*`, `claude-fable-5*`, `claude-opus-4-6/4-7/4-8`, `claude-sonnet-4-6`:
    send `thinking: { type: "adaptive" }` and `output_config.effort`.
  - Only `claude-opus-5*`, `claude-sonnet-5-5*`, `claude-fable-5*`: also send `betas` + `fallbacks: "default"`.
  - Anything else (for example `claude-haiku-4-5`): send neither `thinking`, nor `output_config`, nor `fallbacks`/`betas`.
- Never send `temperature`, `top_p`, `top_k`, `budget_tokens`, or an assistant prefill.
- Never set `tool_choice` (leave it at the default `auto`).
- `response.stop_reason` must be checked before reading content:
  - `"end_turn"` or `"stop_sequence"`: normal.
  - `"max_tokens"`: use the text produced and append `" …"`; log a warning.
  - `"refusal"`: the whole chain declined. Reply with a fixed sentence (see commands/handler) and do not retry.
  - `"pause_turn"` (only with web search): append `response.content` as an assistant message and call once more; if it pauses again, use whatever text exists.
  - `"tool_use"` cannot happen (no client tools are defined); treat as `end_turn`.
- Reply text = concatenation of all `content` blocks with `type === "text"`, in order. Ignore `thinking`,
  `server_tool_use`, `web_search_tool_result`, and `fallback` blocks.
- Usage: `response.usage.input_tokens`, `output_tokens`, `cache_read_input_tokens`, `cache_creation_input_tokens` (may be null/undefined; treat as 0).
- Typed errors, checked most specific first:
  `Anthropic.AuthenticationError` (401), `Anthropic.RateLimitError` (429), `Anthropic.BadRequestError` (400),
  `Anthropic.APIConnectionError` (network; check **before** `APIError` because it is a subclass),
  `Anthropic.APIError` (anything else). Let the SDK's built-in retries (default 2) handle 429/5xx first.
- Conversation history: `messages` must start with a `user` message and alternate roles. Store assistant turns as
  plain text strings. Do not replay thinking blocks across turns (we store text only, so none exist).
- Images: user content blocks `{ type: "image", source: { type: "base64", media_type, data } }` with
  `media_type` in `image/jpeg | image/png | image/gif | image/webp`, placed **before** the text block.
- Validating the key and model without spending tokens: `await client.models.retrieve(model)` (non-beta).

---

## 3. Architecture

```
iPhone ──iMessage──▶ Mac mini
                      ├── BlueBubbles Server (:1234)  ──POST /webhook/<token>──▶  imessage-claude (:8787, 127.0.0.1)
                      │        ▲                                                   │
                      │        └──── REST: typing, send text, mark read ◀──────────┤
                      │                                                            ├── per-chat queue (coalesce 1.5 s, serial per chat)
                      │                                                            ├── ConversationStore (JSONL per chat on disk)
                      │                                                            └── Claude (api.anthropic.com)
                      └── launchd LaunchAgent keeps imessage-claude alive, starts at login
```

Inbound pipeline (one webhook request):

1. `webhook.ts` checks the path token (constant-time compare), limits the body to 1 MiB, parses JSON,
   responds `200 {"ok":true}` immediately, and hands the parsed body to `inbound.ts`.
2. `inbound.ts` turns the raw payload into either an `InboundMessage` or an `IgnoreReason`
   (not new-message, from me, tapback, duplicate, no chat, no sender, sender not allowed, group not mentioned, empty).
3. `queue.ts` groups accepted messages per chat, waits `COALESCE_MS` for rapid follow-up bubbles, merges them,
   and runs `handler.ts` for one chat at a time (serial per chat, at most `MAX_CONCURRENT` chats globally).
4. `handler.ts`: rate limit → slash command? → typing indicator → load history → download images →
   `claude.ts` → sanitize + chunk → send bubbles → mark read → persist turns → stats.

---

## 4. Configuration

Config comes from environment variables. `config.ts` first calls `process.loadEnvFile(envPath)` if the
file exists (`envPath` defaults to `<package root>/.env`; `process.loadEnvFile` does not override variables
that are already set). All values are validated; a bad value exits with a one-line error naming the variable.

| Variable | Default | Meaning |
|---|---|---|
| `BLUEBUBBLES_URL` | `http://127.0.0.1:1234` | BlueBubbles server base URL. |
| `BLUEBUBBLES_PASSWORD` | (required) | Server password; sent as `?password=`. |
| `ANTHROPIC_API_KEY` | (required unless the SDK finds other credentials) | Read by the SDK. `doctor` verifies it. |
| `CLAUDE_MODEL` | `claude-opus-5-5` | Model ID, exact string, no date suffix. |
| `CLAUDE_EFFORT` | `low` | One of `low, medium, high, xhigh, max`. |
| `CLAUDE_MAX_TOKENS` | `2048` | Integer 256–16000. |
| `CLAUDE_WEB_SEARCH` | `false` | `true` adds the `web_search_20260209` server tool with `max_uses: 3`. |
| `BOT_NAME` | `Claude` | Name used in the system prompt and for group mentions. |
| `PERSONA_FILE` | `<DATA_DIR>/persona.md` | Optional extra system-prompt text appended to the stable block. |
| `ALLOWED_SENDERS` | (empty) | Comma-separated phone numbers (E.164 preferred) and emails. `*` allows everyone. Empty means nobody gets a reply (safe default; `doctor` and the boot log say so). |
| `GROUP_MODE` | `mention` | `off` (ignore groups), `mention` (reply when `@BotName` or `BotName` appears), `all` (reply to every allowed message). |
| `BRIDGE_HOST` | `127.0.0.1` | Bind address. Warn loudly at boot if not loopback. |
| `BRIDGE_PORT` | `8787` | Listen port. |
| `PUBLIC_WEBHOOK_URL` | `http://127.0.0.1:<BRIDGE_PORT>` | Base URL BlueBubbles should call. Same Mac, so loopback. |
| `WEBHOOK_TOKEN` | (generated) | 32 hex chars. If unset, generated once and persisted in `<DATA_DIR>/state.json`. |
| `DATA_DIR` | macOS: `~/Library/Application Support/imessage-claude`; else `~/.imessage-claude` | Conversations, state, logs. |
| `HISTORY_MAX_TURNS` | `40` | Max user+assistant messages kept per chat (oldest dropped). |
| `COALESCE_MS` | `1500` | Wait for follow-up bubbles before replying. 0–10000. |
| `MAX_CONCURRENT` | `4` | Max chats being answered at once. |
| `MAX_CHUNK_CHARS` | `1800` | Max characters per outgoing bubble. 200–10000. |
| `MAX_MESSAGES_PER_HOUR` | `60` | Per chat. Beyond it, one notice bubble per hour, then silence. |
| `SEND_METHOD` | `auto` | `auto` (private-api when available, else apple-script), `private-api`, `apple-script`. |
| `TYPING_INDICATOR` | `true` | Send typing indicator while thinking (Private API only). |
| `READ_RECEIPTS` | `true` | Mark chat read after replying (Private API only). |
| `IMAGE_UNDERSTANDING` | `true` | Download image attachments and pass them to Claude. |
| `MAX_IMAGE_BYTES` | `5242880` | Skip larger images (5 MiB). |
| `REPLY_THREADING` | `group` | `off`, `group`, `all`: first bubble replies to the triggering message (`selectedMessageGuid`; Private API only). |
| `LOG_LEVEL` | `info` | `debug, info, warn, error`. |
| `LOG_FILE` | `<DATA_DIR>/logs/bridge.log` | JSON lines; rotated at 10 MiB, 5 files kept. |

`.env.example` (create it in step 1) lists every variable above with its default commented, and the two
required ones uncommented and empty.

---

## 5. Directory layout and file manifest

```
imessage-claude/
  package.json            (exists)      tsconfig.json (exists)      .gitignore (exists)
  .env.example            PLAN.md (this file)                       README.md (step 16)
  src/
    types.ts        shared types (section 6)                              exports: types only
    config.ts       load + validate config                                 loadConfig, Config, ConfigError
    log.ts          JSON-lines logger with rotation + redaction           createLogger, Logger
    bluebubbles.ts  REST client implementing Transport                     BlueBubblesClient, BlueBubblesError
    inbound.ts      payload -> InboundMessage | IgnoreReason               classifyInbound, normalizeAddress, Dedupe
    chunk.ts        markdown -> plain text, split into bubbles             toPlainText, splitForIMessage
    store.ts        conversation + state persistence                       ConversationStore
    persona.ts      system prompt builder                                  buildStableSystem, buildDynamicContext
    claude.ts       Claude completer                                       ClaudeCompleter, requestProfile, Completer (type)
    commands.ts     slash commands                                         handleCommand
    queue.ts        per-chat coalescing serial queue                       ChatQueue
    handler.ts      one coalesced inbound -> reply                         createHandler
    stats.ts        in-memory counters                                     Stats
    webhook.ts      HTTP server (webhook, /health, / status page)          startServer
    status.ts       status page HTML                                       renderStatusPage
    bridge.ts       boot sequence: wires everything, webhook registration  startBridge
    launchd.ts      plist generation, install/uninstall                    buildPlist, installAgent, uninstallAgent
    doctor.ts       diagnostics                                            runDoctor
    simulate.ts     fake BlueBubbles server + end-to-end simulation        FakeBlueBubbles, runSimulation
    cli.ts          command dispatcher (bin)                               main
  test/
    config.test.ts  log.test.ts  bluebubbles.test.ts  inbound.test.ts  chunk.test.ts  store.test.ts
    persona.test.ts claude.test.ts  stats.test.ts  commands.test.ts  queue.test.ts  handler.test.ts
    webhook.test.ts launchd.test.ts e2e.test.ts
```

---

## 6. Shared types — `src/types.ts` (write verbatim, then extend only if a later step says so)

```ts
import type Anthropic from "@anthropic-ai/sdk";

export type Effort = "low" | "medium" | "high" | "xhigh" | "max";
export type SendMethod = "apple-script" | "private-api";
export type GroupMode = "off" | "mention" | "all";
export type ReplyThreading = "off" | "group" | "all";
export type LogLevel = "debug" | "info" | "warn" | "error";

/** Raw webhook body from BlueBubbles. Only the fields we read; everything is optional on purpose. */
export interface BBWebhookEvent {
  type?: string;
  data?: BBMessage;
}
export interface BBMessage {
  guid?: string;
  text?: string | null;
  isFromMe?: boolean;
  dateCreated?: number;
  subject?: string | null;
  handle?: { address?: string | null; service?: string | null } | null;
  attachments?: BBAttachment[] | null;
  chats?: BBChat[] | null;
  chatGuid?: string | null;                // older servers put it here
  associatedMessageGuid?: string | null;
  associatedMessageType?: number | string | null;
  balloonBundleId?: string | null;
  isAudioMessage?: boolean;
  error?: number | null;
}
export interface BBAttachment {
  guid?: string;
  mimeType?: string | null;
  transferName?: string | null;
  totalBytes?: number | null;
  isSticker?: boolean;
}
export interface BBChat {
  guid?: string;
  chatIdentifier?: string | null;
  displayName?: string | null;
  participants?: Array<{ address?: string | null; service?: string | null }> | null;
}

export type IgnoreReason =
  | "not-new-message" | "from-me" | "tapback" | "duplicate" | "no-chat" | "no-sender"
  | "sender-not-allowed" | "group-off" | "group-not-mentioned" | "empty" | "audio";

export interface InboundImage { guid: string; mimeType: string | null; bytes: number | null; name: string | null }

export interface InboundMessage {
  guid: string;
  chatGuid: string;
  isGroup: boolean;
  chatName: string | null;          // group display name, else null
  sender: string;                   // raw address as BlueBubbles gave it
  senderNormalized: string;         // normalizeAddress(sender)
  text: string;                     // trimmed, U+FFFC removed, mention stripped in groups
  images: InboundImage[];           // image attachments only (mimeType image/*), stickers excluded
  receivedAt: number;               // Date.now() when accepted
  sentAt: number | null;            // data.dateCreated
}

export type Classified = { ok: true; message: InboundMessage } | { ok: false; reason: IgnoreReason };

export interface DownloadedImage { mediaType: "image/jpeg" | "image/png" | "image/gif" | "image/webp"; base64: string }

/** Everything the handler needs from BlueBubbles. The real client, the console client and test fakes implement it. */
export interface Transport {
  readonly privateApi: boolean;
  sendText(chatGuid: string, text: string, opts?: { replyToGuid?: string }): Promise<{ guid: string | null }>;
  startTyping(chatGuid: string): Promise<void>;
  markRead(chatGuid: string): Promise<void>;
  downloadAttachment(guid: string, maxBytes: number): Promise<{ contentType: string | null; data: Buffer } | null>;
}

export interface StoredTurn { role: "user" | "assistant"; text: string; at: number }

export interface ChatSettings { model?: string; effort?: Effort; persona?: string }

export interface CompletionRequest {
  system: Array<{ text: string; cache: boolean }>;
  messages: Anthropic.Beta.BetaMessageParam[];
  model: string;
  effort: Effort;
  maxTokens: number;
  webSearch: boolean;
}
export interface CompletionResult {
  text: string;
  stopReason: string | null;
  model: string;
  usage: { input: number; output: number; cacheRead: number; cacheWrite: number };
}
export type CompletionFailure =
  | { kind: "refusal" } | { kind: "rate-limited" } | { kind: "auth" } | { kind: "network" } | { kind: "bad-request"; detail: string } | { kind: "unknown"; detail: string };
export type CompletionOutcome = { ok: true; result: CompletionResult } | { ok: false; failure: CompletionFailure };

export interface Completer { complete(req: CompletionRequest): Promise<CompletionOutcome> }
```

---

## 7. Steps

### Step 1 — Types, config, logger, `.env.example`

Files: `src/types.ts` (section 6), `src/config.ts`, `src/log.ts`, `.env.example`.

`config.ts` (exact `Config` field names; every later step uses these):
```ts
export interface Config {
  bluebubblesUrl: string;          bluebubblesPassword: string;
  claudeModel: string;             claudeEffort: Effort;           claudeMaxTokens: number;   claudeWebSearch: boolean;
  botName: string;                 personaFile: string;
  allowedSenders: Set<string>;     allowAllSenders: boolean;
  groupMode: GroupMode;
  bridgeHost: string;              bridgePort: number;             publicWebhookUrl: string;  webhookToken: string | null;
  dataDir: string;                 historyMaxTurns: number;        coalesceMs: number;        maxConcurrent: number;
  maxChunkChars: number;           maxMessagesPerHour: number;
  sendMethod: "auto" | SendMethod; typingIndicator: boolean;       readReceipts: boolean;
  imageUnderstanding: boolean;     maxImageBytes: number;          replyThreading: ReplyThreading;
  logLevel: LogLevel;              logFile: string;
  packageRoot: string;             envPath: string | null;         isDarwin: boolean;         homeDir: string;
}
export class ConfigError extends Error {}
export function loadConfig(opts?: { env?: NodeJS.ProcessEnv; envPath?: string | null; platform?: NodeJS.Platform; homeDir?: string }): Config;
```
- `opts.env` defaults to `process.env`; tests pass their own object. The `.env` path is resolved in this order:
  `opts.envPath` (a string uses it, `null` skips file loading) → `env.IMESSAGE_CLAUDE_ENV` → `<packageRoot>/.env`.
  Call `process.loadEnvFile(envPath)` only when the file exists and `opts.env === process.env` (it mutates the real
  environment and does not overwrite variables that are already set). `packageRoot` is the directory containing
  `package.json`, derived from `import.meta.url` (`src/` and `dist/` are both one level below it).
- Booleans accept `true/false/1/0/yes/no` (case-insensitive). Integers are range-checked per section 4.
- `allowedSenders` is a `Set<string>` of `normalizeAddress()` values. In this step create `src/inbound.ts` containing only
  `normalizeAddress` (spec in step 3); step 3 extends that file. `allowAllSenders` is true when the list is exactly `*`.
- `dataDir` default depends on `platform` (`darwin` → `~/Library/Application Support/imessage-claude`, else `~/.imessage-claude`).
  `logFile` and `personaFile` defaults derive from the final `dataDir`. `homeDir` is `opts.homeDir ?? os.homedir()`.
- `publicWebhookUrl` default derives from `bridgePort`. Strip trailing slashes.
- Throw `ConfigError` with a message like `BLUEBUBBLES_PASSWORD is required` or `CLAUDE_EFFORT must be one of low, medium, high, xhigh, max (got "fast")`.

`log.ts`:
```ts
export interface Logger { debug(msg: string, fields?: object): void; info(...): void; warn(...): void; error(...): void; child(fields: object): Logger; flush(): Promise<void> }
export function createLogger(opts: { level: LogLevel; file?: string | null; stderr?: boolean; maxBytes?: number; keep?: number }): Logger;
export function redact(value: unknown): unknown;   // exported for tests
```
- Each line: `{"t":"<ISO>","level":"info","msg":"...", ...fields}`. Writes to the file (append) and, when `stderr` is true, a
  human-readable line to stderr: `01:02:03 INFO  msg key=value`.
- `redact` deep-copies objects/strings and replaces `password=...`, `guid=...`, `token=...` query values and anything that
  looks like `sk-ant-...` with `***`. Apply it to every field object before writing.
- Rotation: when the file exceeds `maxBytes` (default 10 MiB), rename `bridge.log` → `bridge.log.1` (shifting `.1`→`.2` ... up
  to `keep`, default 5) and start a new file. Create the directory if missing. Never throw from a log call.

`.env.example`: every variable from section 4, with a one-line comment each.

Tests (`test/config.test.ts`, `test/log.test.ts`):
- defaults apply when only the two required variables are set; `isDarwin` and `dataDir` follow `platform`.
- each invalid value (effort, port, boolean, integer out of range) throws `ConfigError` naming the variable.
- `ALLOWED_SENDERS="+1 (555) 123-4567, Bob@Example.com"` normalizes to `+15551234567` and `bob@example.com`; `*` sets `allowAllSenders`.
- logger writes a JSON line with redacted `url` field; rotation renames when `maxBytes` is tiny (e.g. 200).

Check: `npm run typecheck && npm test`. Commit.

### Step 2 — BlueBubbles client

File: `src/bluebubbles.ts`.

```ts
export class BlueBubblesError extends Error {
  status: number | null; body: unknown;
  constructor(message: string, status: number | null, body?: unknown) { super(message); this.name = "BlueBubblesError"; this.status = status; this.body = body; }
}
export interface ServerInfo { serverVersion: string | null; osVersion: string | null; privateApi: boolean; helperConnected: boolean; raw: unknown }
export class BlueBubblesClient implements Transport {
  constructor(opts: { baseUrl: string; password: string; log: Logger; fetchImpl?: typeof fetch; sendMethod: SendMethod; privateApi?: boolean; timeoutMs?: number })
  readonly privateApi: boolean;                 // from opts (default false); bridge.ts sets it after serverInfo()
  withCapabilities(opts: { privateApi: boolean; sendMethod: SendMethod }): BlueBubblesClient;  // returns a new instance sharing fetch/log
  ping(): Promise<boolean>;                     // true on HTTP 200 + body.status === 200; false on anything else (never throws)
  serverInfo(): Promise<ServerInfo>;            // throws BlueBubblesError on failure
  sendText(chatGuid, text, opts?): Promise<{ guid: string | null }>;
  startTyping(chatGuid): Promise<void>;         // no-op when !privateApi
  markRead(chatGuid): Promise<void>;            // no-op when !privateApi
  downloadAttachment(guid, maxBytes): Promise<{ contentType: string | null; data: Buffer } | null>;  // null when larger than maxBytes (check Content-Length first, then actual size) or 404
  listWebhooks(): Promise<Array<{ id: number; url: string; events: string[] }>>;
  registerWebhook(url: string, events: string[]): Promise<void>;
  deleteWebhook(id: number): Promise<void>;
}
```
- Build URLs with `new URL(path, baseUrl)` and `url.searchParams.set("password", password)`. Encode chat GUIDs with `encodeURIComponent`.
- `sendText`: body `{ chatGuid, tempGuid: "imessage-claude-" + randomUUID(), message: text, method }` where `method` is
  `"private-api"` only if `this.privateApi && sendMethod !== "apple-script"`, else `"apple-script"`; if `opts.replyToGuid`
  and privateApi, add `selectedMessageGuid` (and method becomes `"private-api"`). Retry once after 1 s on network error or HTTP 5xx.
  Timeout per request via `AbortSignal.timeout(timeoutMs)` (default 30 s; 60 s for sendText because AppleScript can be slow).
- Every error path throws `BlueBubblesError` with the HTTP status and the parsed body (if JSON), except `ping` which returns false.
- Log each request at `debug` as `{ method, path }` (never the query string).

Tests (`test/bluebubbles.test.ts`): start an in-process `node:http` server that records requests and returns canned
envelopes. Assert: password query on every call; chat GUID path-encoded (`iMessage;-;+1555` → `iMessage%3B-%3B%2B1555`);
sendText body fields and method selection in all three cases; retry once on 500 then success; `ping` false on 401;
`downloadAttachment` returns null when Content-Length exceeds maxBytes; `startTyping` makes no request when `privateApi` is false.

### Step 3 — Inbound classification and de-duplication

File: `src/inbound.ts`.

```ts
export function normalizeAddress(addr: string): string;
export class Dedupe { constructor(capacity?: number /* 2000 */, seed?: string[]); has(guid: string): boolean; add(guid: string): void; snapshot(): string[] /* newest last, max 500 */ }
export function mentionPattern(botName: string): RegExp;      // (^|[\s@])<escaped name>\b[:,]?  case-insensitive
export function stripMention(text: string, botName: string): string;
export function classifyInbound(event: BBWebhookEvent, ctx: { config: Pick<Config, "allowedSenders" | "allowAllSenders" | "groupMode" | "botName" | "imageUnderstanding">; dedupe: Dedupe; now?: () => number }): Classified;
```
- `normalizeAddress`: trim; if it contains `@` → lowercase. Otherwise keep digits only (drop spaces, dashes, parentheses, dots);
  if it started with `+` keep it; if no `+` and 10 digits → `+1` + digits; if no `+` and 11 digits starting with `1` → `+` + digits;
  otherwise `+` + digits.
- Classification order (return the first matching reason):
  1. `event.type !== "new-message"` → `not-new-message`
  2. `data.isFromMe` → `from-me`
  3. `data.associatedMessageGuid` truthy, or `associatedMessageType` is a non-zero number or a non-empty string → `tapback`
  4. `data.guid` missing or `dedupe.has(guid)` → `duplicate` (add to dedupe after passing every check below — i.e. add only when returning ok)
  5. chat = `data.chats?.[0]`; `chatGuid = chat?.guid ?? data.chatGuid`; missing → `no-chat`
  6. sender = `data.handle?.address`; missing/empty → `no-sender`
  7. not `allowAllSenders` and `!allowedSenders.has(normalizeAddress(sender))` → `sender-not-allowed`
  8. isGroup = chatGuid includes `;+;` or `(chat?.participants?.length ?? 0) > 1`. If isGroup and `groupMode === "off"` → `group-off`;
     if `groupMode === "mention"` and the text does not match `mentionPattern(botName)` → `group-not-mentioned`
  9. text = `(data.text ?? "").replace(/￼/g, "").trim()`; in groups with mention mode, `stripMention` first.
     images = attachments with `mimeType` starting `image/`, not `isSticker`, only when `imageUnderstanding`.
     If `data.isAudioMessage` and text is empty → `audio`. If text is empty and images is empty → `empty`.
  10. Return ok with `InboundMessage` (chatName = `chat.displayName || null`).

Tests (`test/inbound.test.ts`): one test per reason, plus the happy DM path, group mention path (mention stripped), group `all` path,
U+FFFC-only text with one image → ok with empty text, sticker excluded, allowlist by email, duplicate on second call, `Dedupe` capacity eviction.

### Step 4 — Plain text and chunking

File: `src/chunk.ts`.

```ts
export function toPlainText(markdown: string): string;
export function splitForIMessage(text: string, maxChars: number): string[];
```
`toPlainText` rules (apply in this order, line by line where noted):
- Fenced code blocks: remove the ``` fence lines, keep the code lines verbatim.
- Headings `#{1,6} Title` → `Title` (keep a blank line after it).
- Bold/italic markers: `**x**`, `__x__`, `*x*`, `_x_` → `x` (only when the marker pair is on one line).
- Inline code `` `x` `` → `x`.
- Links `[text](url)` → `text (url)`; bare autolinks `<https://...>` → `https://...`.
- Bullets: lines starting with `- `, `* `, `+ ` → `• `; numbered lists keep their numbers.
- Tables: lines that are only `|---|` separators are dropped; other table rows replace `|` with ` · ` and trim.
- Horizontal rules (`---`, `***`) removed.
- Collapse 3+ consecutive blank lines to 2; trim trailing spaces; trim the whole result.

`splitForIMessage`:
- Empty/whitespace input → `[]`.
- Split into paragraphs on blank lines. Greedily pack whole paragraphs into a chunk while `chunk.length + 2 + para.length <= maxChars`.
- A single paragraph longer than `maxChars` is split at sentence boundaries (`. `, `! `, `? `, newline) and finally hard-split at
  `maxChars` if a sentence is still too long. Never cut inside a surrogate pair (use `Array.from(text)` for hard splits).
- Every returned chunk is non-empty, trimmed, and `<= maxChars`. Concatenating chunks with `\n\n` reproduces the text up to whitespace.

Tests (`test/chunk.test.ts`): each sanitize rule; packing; long paragraph split at sentences; hard split of a 5000-char word;
emoji-safe hard split; never exceeds max over 50 random inputs (seeded loop building random words).

### Step 5 — Conversation store

File: `src/store.ts`.

```ts
export class ConversationStore {
  constructor(opts: { dataDir: string; log: Logger; maxTurns: number })
  init(): Promise<void>;                                   // mkdir -p dataDir/conversations, load state.json
  getHistory(chatGuid: string): Promise<StoredTurn[]>;     // oldest first, at most maxTurns, starts with a "user" turn
  appendTurns(chatGuid: string, turns: StoredTurn[]): Promise<void>;
  reset(chatGuid: string): Promise<void>;                  // deletes the chat file
  getSettings(chatGuid: string): Promise<ChatSettings>;    // from state.json
  setSettings(chatGuid: string, patch: Partial<ChatSettings>): Promise<void>;   // undefined values delete the key
  getState<T>(key: string, fallback: T): Promise<T>;       // generic small values (webhookToken, dedupe snapshot)
  setState(key: string, value: unknown): Promise<void>;
  listChats(): Promise<Array<{ chatGuid: string; turns: number; lastAt: number | null }>>;
}
export function chatFileName(chatGuid: string): string;    // sha256(chatGuid).slice(0,16) + ".jsonl"
```
- One JSONL file per chat: each line is a `StoredTurn`. Appends use `fs.appendFile`. When a file exceeds `maxTurns * 4` lines,
  rewrite it keeping the last `maxTurns` turns (atomic: write `.tmp` then rename).
- `getHistory` drops leading assistant turns and collapses two consecutive same-role turns by joining text with `\n\n`
  so the result alternates and starts with `user`. Skips unparsable lines with a warning.
- `state.json` holds `{ settings: Record<chatGuid, ChatSettings>, kv: Record<string, unknown> }`, written atomically.
  Serialize writes through a single promise chain so concurrent writers cannot interleave.

Tests (`test/store.test.ts`): append/get round trip; trimming to maxTurns; alternation repair; reset; settings patch and delete;
corrupt line tolerated; concurrent `setState` calls all land.

### Step 6 — Persona and Claude completer

Files: `src/persona.ts`, `src/claude.ts`.

`persona.ts`:
```ts
export function buildStableSystem(opts: { botName: string; personaText: string | null }): string;
export function buildDynamicContext(opts: { now: Date; timeZone: string; chat: { isGroup: boolean; chatName: string | null; sender: string }; imagesAttached: number }): string;
```
Stable block (keep wording tight; this is the product voice):
- Identity: `You are ${botName}, a personal assistant that talks over iMessage from a Mac that is always on.`
- Medium rules: replies are plain text (no markdown, no headers, no tables, no code fences); short paragraphs; usually under
  120 words unless the person asks for detail; long answers are fine but break into paragraphs because each becomes a bubble;
  one question at a time; match the person's tone; use emoji only if they do.
- Honesty rules: say when unsure; do not invent facts, phone numbers, prices, or links; if asked to do something the bridge
  cannot do (send files, make calls, set reminders), say so plainly.
- Memory rule: you remember this chat's recent messages only; `/reset` clears them.
- Then `personaText` verbatim if present.

Dynamic block (one short paragraph): current date/time with time zone, whether this is a DM or a group (name, when present),
the sender's address, and `N photo(s) attached to this message` when applicable.

`claude.ts`:
```ts
export function requestProfile(model: string): { thinking: boolean; effort: boolean; fallbacks: boolean };
export class ClaudeCompleter implements Completer {
  constructor(opts: { client?: Anthropic; log: Logger })
  complete(req: CompletionRequest): Promise<CompletionOutcome>;
}
export async function verifyModel(client: Anthropic, model: string): Promise<{ ok: true } | { ok: false; detail: string }>;  // models.retrieve
```
- Build the request exactly as section 2.3. `req.system` maps to system blocks; `cache: true` adds `cache_control: { type: "ephemeral" }`.
- Handle `pause_turn` once. Map stop reasons and errors to `CompletionOutcome` per section 2.3. On `refusal` return `{ ok: false, failure: { kind: "refusal" } }`.
- Log at `info`: `{ model: response.model, stop: stop_reason, in, out, cacheRead, ms }`.
- Timeout: pass `{ timeout: 120_000 }` as the second argument to `create`.

Tests (`test/claude.test.ts`): use `new Anthropic({ apiKey: "test", fetch: fakeFetch })` where `fakeFetch` returns canned JSON
`Response`s (the SDK accepts a custom `fetch` in its constructor options). Assert the outgoing request body for Opus 5.5
(betas, fallbacks, thinking, output_config, cache_control placement, no temperature), for Haiku 4.5 (none of those),
text concatenation, `max_tokens` suffix, refusal mapping, 401 → `auth`, 429 after SDK retries → `rate-limited`
(construct the client with `maxRetries: 0` for that test), and `pause_turn` continuation sends the assistant content back.
`test/persona.test.ts`: stable text contains bot name and persona text; dynamic text mentions group name and photo count.

### Step 7 — Stats and slash commands

Files: `src/stats.ts`, `src/commands.ts`.

`stats.ts`:
```ts
export class Stats {
  readonly startedAt: number;
  received = 0; ignored: Record<IgnoreReason, number>; replied = 0; errors = 0; commands = 0;
  tokensIn = 0; tokensOut = 0; cacheRead = 0;
  lastInboundAt: number | null = null; lastReplyAt: number | null = null; lastLatencyMs: number | null = null;
  recent: Array<{ at: number; chat: string /* masked */; latencyMs: number; chunks: number; outcome: "reply" | "command" | "error" | "ignored" }> = [];  // last 20, newest first
  constructor(now?: () => number)
  noteReceived(): void;
  noteIgnored(reason: IgnoreReason): void;
  noteReply(info: { chat: string; latencyMs: number; chunks: number; usage: CompletionResult["usage"] }): void;
  noteCommand(info: { chat: string; latencyMs: number }): void;
  noteError(info: { chat: string; latencyMs: number }): void;
  snapshot(): object;        // plain JSON: all counters plus repliedToday (since local midnight) and avgLatencyMs over `recent`
}
export function maskAddress(addr: string): string;   // "+15551234567" -> "+1•••••4567", "bob@example.com" -> "b•••@example.com"
```

`commands.ts`:
```ts
export interface CommandContext { chatGuid: string; sender: string; store: ConversationStore; config: Config; stats: Stats; now?: () => number }
export function isCommand(text: string): boolean;                  // starts with "/" followed by a letter
export async function handleCommand(text: string, ctx: CommandContext): Promise<string | null>;  // reply text, or null when not a command
```
Commands (case-insensitive, first token):
- `/help` — lists commands in one bubble.
- `/reset` (alias `/forget`, `/new`) — `store.reset(chatGuid)` → `Fresh start. I've forgotten this conversation.`
- `/status` — model, effort, turns in memory, uptime, messages handled today.
- `/model` — shows the current model; `/model <id>` sets a per-chat override if `<id>` matches `/^claude-[a-z0-9.-]+$/`, else error text.
  `/model default` removes the override.
- `/effort <low|medium|high|xhigh|max>` — per-chat override; `/effort default` removes it.
- `/persona <text>` — per-chat persona override (max 2000 chars); `/persona clear` removes it; `/persona` shows it.
- Unknown `/xyz` → `I don't know that command. Try /help.`

Tests (`test/commands.test.ts`): each command's effect on the store and its reply; unknown command; non-command returns null.
`test/stats.test.ts`: counters, `recent` capped at 20, `maskAddress` for phone and email.

### Step 8 — Per-chat coalescing queue

File: `src/queue.ts`.

```ts
export class ChatQueue {
  constructor(opts: { coalesceMs: number; maxConcurrent: number; process: (chatGuid: string, batch: InboundMessage[]) => Promise<void>; log: Logger; setTimeoutImpl?: typeof setTimeout; clearTimeoutImpl?: typeof clearTimeout })
  push(message: InboundMessage): void;
  readonly depth: number;        // messages waiting (not yet processing)
  readonly inFlight: number;     // chats currently processing
  drain(): Promise<void>;        // resolves when nothing is pending or in flight (for shutdown and tests)
}
```
- `push` appends to the chat's pending list and (re)starts that chat's timer for `coalesceMs`. When the timer fires and the chat is
  not already processing and `inFlight < maxConcurrent`, take the whole pending list as one batch and call `process`. If the chat
  is processing, the batch waits until it finishes (then runs immediately, without a new coalesce delay). If the global cap is hit,
  the chat waits in a FIFO of ready chats.
- Errors thrown by `process` are logged at `error` and never stop the queue.

Tests (`test/queue.test.ts`): two pushes within the window produce one batch of 2; a push during processing produces a second
batch after the first completes; `maxConcurrent: 1` serializes two chats; a throwing `process` does not break later batches;
`drain` resolves. Use real timers with small `coalesceMs` (10 ms) to keep tests simple.

### Step 9 — Handler

File: `src/handler.ts`.

`handler.ts`:
```ts
export interface HandlerDeps { config: Config; transport: Transport; completer: Completer; store: ConversationStore; stats: Stats; log: Logger; now?: () => number }
export function createHandler(deps: HandlerDeps): (chatGuid: string, batch: InboundMessage[]) => Promise<void>;
```
Behavior for one batch (all messages share `chatGuid`):
1. Rate limit: keep an in-memory map `chatGuid → timestamps` of handled batches in the last hour. If the count is `>= maxMessagesPerHour`,
   send `I'm pausing replies in this chat for a bit — too many messages in the last hour.` at most once per hour per chat, then return.
2. Join the batch texts with `\n` (skip empty), collect all images. `triggerGuid` = last message's guid. `sender` = last message's sender.
3. If the joined text `isCommand(...)`: reply with `handleCommand` result (chunked), `stats.commands++`, return.
4. If `config.typingIndicator`: `transport.startTyping(chatGuid)` fire-and-forget (catch and log at debug).
5. Settings: `const s = await store.getSettings(chatGuid)`; model = `s.model ?? config.claudeModel`; effort = `s.effort ?? config.claudeEffort`.
6. Images: for each image (max 4), `transport.downloadAttachment(guid, config.maxImageBytes)`. Media type = `contentType` header if it is one of
   the four allowed types, else the payload `mimeType` if allowed, else skip and remember the count of skipped images (HEIC and others).
   If any image was skipped, append `\n\n[The person attached ${n} photo(s) in a format I can't view.]` to the user text.
7. History: `await store.getHistory(chatGuid)` → `BetaMessageParam[]` (text only). Append the new user turn: content is an array of
   image blocks followed by one text block; if text is empty and there are images, text = `(photo)`.
8. System: `[{ text: buildStableSystem({ botName, personaText: s.persona ?? filePersona }), cache: true }, { text: buildDynamicContext(...), cache: false }]`.
   `filePersona` is read once at handler creation from `config.personaFile` if it exists.
9. `completer.complete(...)`. On failure reply with exactly one bubble:
   - refusal: `I can't help with that one.`
   - rate-limited: `I'm being rate limited right now. Give me a minute and try again.`
   - auth: `My API key isn't working. Whoever runs this Mac needs to check it.` (also log at `error`)
   - network: `I can't reach Claude right now. Try again in a bit.`
   - bad-request/unknown: `Something went wrong on my end. Try again in a minute.` (log detail at `error`)
   Then `stats.noteError()` and return (do not persist the turn).
10. `text = toPlainText(result.text)`; `chunks = splitForIMessage(text, config.maxChunkChars)`; if empty, chunks = `["(no reply)"]`.
11. Send chunks in order, awaiting each; 300 ms pause between chunks. The first chunk passes `replyToGuid: triggerGuid` when
    `replyThreading === "all"` or (`"group"` and isGroup). If a send throws, log at `error`, `stats.noteError()`, stop sending further chunks.
12. If `config.readReceipts`: `transport.markRead(chatGuid)` best-effort.
13. Persist: `store.appendTurns(chatGuid, [{ role: "user", text: userTextForHistory, at }, { role: "assistant", text, at }])` where
    `userTextForHistory` is the joined text plus `[sent N photo(s)]` when images were attached (never store image bytes).
14. `stats.noteReply({ chat: maskAddress(sender), latencyMs, chunks: chunks.length, usage })`.

Tests (`test/handler.test.ts`) with a `FakeTransport` (records calls, `privateApi` configurable) and a `FakeCompleter`
(scripted outcomes): happy path sends chunked bubbles and persists turns; command path does not call the completer; refusal
sends one bubble and persists nothing; typing/read not called when `privateApi` is false; image download → image block before
text; unsupported image → note appended; rate limit notice once; reply threading only in groups by default; send failure stops further chunks.

### Step 10 — Webhook server and status page

Files: `src/webhook.ts`, `src/status.ts`.

```ts
export interface ServerDeps { config: Config; log: Logger; stats: Stats; onEvent: (event: BBWebhookEvent) => void; health: () => object; token: string }
export function startServer(deps: ServerDeps): Promise<{ server: import("node:http").Server; port: number; close(): Promise<void> }>;
export function renderStatusPage(): string;   // status.ts
```
Routes:
- `POST /webhook/<token>`: compare with `crypto.timingSafeEqual` on equal-length buffers (401 otherwise, body `{"ok":false}`);
  read body up to 1 MiB (413 beyond); parse JSON (400 on failure); respond `200 {"ok":true}` **before** calling `onEvent`
  (call it on the next tick so a slow handler never delays the response). Non-JSON content types are still parsed as JSON.
- `GET /health`: `200` JSON from `deps.health()`.
- `GET /`: `200 text/html` = `renderStatusPage()`.
- Anything else: 404 JSON. Never serve the token anywhere. Set `Cache-Control: no-store` on all responses.

Status page (single self-contained HTML string, no external assets): polls `/health` every 5 s and renders:
title `imessage-claude`, a green/amber/red dot for BlueBubbles reachability, Private API on/off, model + effort, uptime,
big-number tiles (replies today, average latency, tokens in/out, cache hit %), queue depth, and a "recent" list of the last
20 events (time, masked chat, outcome, latency). Respect `prefers-color-scheme`. Keep it under 250 lines. No frameworks.

Tests (`test/webhook.test.ts`): wrong token → 401 and `onEvent` not called; right token → 200 and `onEvent` receives the parsed body;
oversized body → 413; bad JSON → 400; `/health` returns the health object; `/` returns HTML containing `imessage-claude`.

### Step 11 — Bridge boot sequence

File: `src/bridge.ts`.

```ts
export interface BridgeOptions { config: Config; log: Logger; transportFactory?: (info: ServerInfo | null) => Transport; completer?: Completer; fetchImpl?: typeof fetch }
export interface RunningBridge { port: number; stop(): Promise<void>; health(): object; token: string; stats: Stats }
export async function startBridge(opts: BridgeOptions): Promise<RunningBridge>;
```
Sequence:
1. `store.init()`. Token: `config.webhookToken ?? await store.getState("webhookToken", null)`; if none, generate `randomBytes(16).toString("hex")`
   and persist. Load the dedupe seed from `store.getState("dedupe", [])`.
2. Start the HTTP server (so `/health` works even while BlueBubbles is down).
3. Connect loop: `client.ping()`; while false, log `warn` once per minute and retry every 10 s (do not exit). Then `serverInfo()`;
   compute `privateApi = info.privateApi && info.helperConnected` (respect `SEND_METHOD` overrides) and create the final transport with
   `withCapabilities`. Log `info` `{ serverVersion, privateApi, sendMethod }`.
4. Webhook registration: `listWebhooks()`; our URL is `${publicWebhookUrl}/webhook/${token}`. If an entry with exactly our URL exists,
   keep it. Delete any entry whose URL starts with `${publicWebhookUrl}/webhook/` but differs (stale token). Otherwise `registerWebhook(url, ["new-message"])`.
   Failures here are logged at `error` and retried every 60 s in the background; the bridge still runs.
5. Wire `onEvent` → `classifyInbound` → `stats.noteIgnored` or `queue.push`. Persist the dedupe snapshot every 60 s and on stop.
6. Every 60 s: `ping()` to update `health().bluebubbles.reachable` and `lastCheckAt`.
7. `stop()`: stop timers, `server.close()`, `queue.drain()` with a 20 s cap, persist dedupe, `log.flush()`.
8. `health()` returns `{ ok, version, uptimeSec, model, effort, sendMethod, privateApi, bluebubbles: { reachable, serverVersion, lastCheckAt }, webhook: { registered, url: "<masked token>" }, queue: { depth, inFlight }, stats: stats.snapshot() }`.
9. At boot log a `warn` if `allowedSenders` is empty and not `allowAllSenders`: `No ALLOWED_SENDERS configured: every message will be ignored.`
   Log a `warn` if `bridgeHost` is not loopback.

`startBridge` must not call `process.exit`. The CLI handles signals: on `SIGINT`/`SIGTERM` call `stop()` then exit 0.

Test: covered by `test/e2e.test.ts` in step 13.

### Step 12 — launchd install/uninstall, doctor, tail

Files: `src/launchd.ts`, `src/doctor.ts`.

`launchd.ts`:
```ts
export const AGENT_LABEL = "com.imessage-claude.bridge";
export function buildPlist(opts: { nodePath: string; scriptPath: string; workingDirectory: string; logDir: string; envPath: string }): string;
export function plistPath(homeDir: string): string;    // ~/Library/LaunchAgents/com.imessage-claude.bridge.plist
export async function installAgent(opts: { config: Config; log: Logger; exec?: ExecFn; nodePath?: string; homeDir?: string }): Promise<void>;
export async function uninstallAgent(opts: { config: Config; log: Logger; exec?: ExecFn; homeDir?: string }): Promise<void>;
export type ExecFn = (cmd: string, args: string[]) => Promise<{ code: number; stdout: string; stderr: string }>;
```
Plist content (XML, exact keys): `Label`; `ProgramArguments` = `[nodePath, scriptPath, "serve"]`; `WorkingDirectory`;
`EnvironmentVariables` = `{ PATH: "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin", HOME: <home>, IMESSAGE_CLAUDE_ENV: <envPath> }`;
`RunAtLoad` true; `KeepAlive` true; `ThrottleInterval` 10; `ProcessType` `Background`; `StandardOutPath` `<logDir>/launchd.out.log`;
`StandardErrorPath` `<logDir>/launchd.err.log`. (`config.ts` already honors `IMESSAGE_CLAUDE_ENV`, step 1.)
`scriptPath` is the absolute path to `dist/cli.js` (derive from `import.meta.url`); `nodePath` defaults to `process.execPath`.

`installAgent`: refuse unless `config.isDarwin` (throw with a clear message); require `dist/cli.js` to exist (tell the user to run `npm run build`);
write the plist; run `launchctl bootout gui/<uid>/<label>` (ignore failure); `launchctl bootstrap gui/<uid> <plist>`; `launchctl kickstart -k gui/<uid>/<label>`;
print where logs are and `npm run doctor`. `uid` from `process.getuid?.()`.
`uninstallAgent`: `bootout` then delete the plist.

`doctor.ts`:
```ts
export interface Check { name: string; ok: boolean | null /* null = warning */; detail: string; fix?: string }
export async function runDoctor(opts: { config: Config; log: Logger; fetchImpl?: typeof fetch; exec?: ExecFn; anthropic?: Anthropic }): Promise<Check[]>;
export function formatChecks(checks: Check[]): string;   // ✔ / ✖ / ▲ lines plus fix hints
```
Checks, in order: Node >= 22.18; `.env` found at the resolved path; required variables present; BlueBubbles ping; server info
(version, Private API + helper connected — warning, not failure, when off: typing/read receipts disabled); Anthropic credentials and
model (`verifyModel`); webhook registered for our URL (warning if the bridge has never run: "will register on first start");
bridge `/health` reachable on `BRIDGE_PORT` (warning if not running); `ALLOWED_SENDERS` non-empty (warning); on macOS,
`pmset -g` parsed for ` sleep ` value — warning if not `0` with fix `sudo pmset -a sleep 0 disksleep 0` and the System Settings path;
on macOS, `launchctl print gui/<uid>/com.imessage-claude.bridge` exit code 0 → agent loaded (warning otherwise, fix `npm run install-agent`).

`tail` command (in `cli.ts`): spawn `tail -n 200 -f <LOG_FILE>` with `stdio: "inherit"`.

Tests (`test/launchd.test.ts`): plist contains the exact keys/values; `installAgent` with a fake `exec` records the three launchctl calls
in order and writes the plist to a temp home; refuses on non-darwin. `doctor` checks are exercised in `e2e.test.ts` against the fake server
(ping ok, info ok) with a fake `exec` returning canned `pmset` output.

### Step 13 — Simulation and end-to-end test

File: `src/simulate.ts`.

```ts
export class FakeBlueBubbles {
  constructor(opts?: { privateApi?: boolean; password?: string })
  start(): Promise<{ url: string; port: number }>; stop(): Promise<void>;
  readonly sent: Array<{ chatGuid: string; message: string; method: string; selectedMessageGuid?: string }>;
  readonly typing: string[]; readonly read: string[]; readonly webhooks: Array<{ id: number; url: string; events: string[] }>;
  attachments: Map<string, { contentType: string; data: Buffer }>;
  deliver(event: BBWebhookEvent): Promise<number>;      // POSTs to every registered webhook URL, returns last status
  waitForSent(count: number, timeoutMs: number): Promise<void>;
}
export function dmEvent(opts: { from: string; text: string; guid?: string; attachments?: BBAttachment[] }): BBWebhookEvent;
export function groupEvent(opts: { from: string; text: string; chatGuid?: string; name?: string; guid?: string }): BBWebhookEvent;
export class EchoCompleter implements Completer { /* returns "echo: " + last user text, usage zeros */ }
export async function runSimulation(opts: { config: Config; log: Logger; text: string; from: string; group: boolean; fakeClaude: boolean }): Promise<string[]>;  // returns the bubbles that were "sent"
```
`FakeBlueBubbles` implements, with the real envelope, exactly: `/api/v1/ping`, `/api/v1/server/info`, `/api/v1/message/text`,
`/api/v1/chat/:guid/typing` (POST), `/api/v1/chat/:guid/read`, `/api/v1/attachment/:guid/download`, `/api/v1/webhook` (GET/POST/DELETE).
It rejects any request whose `password` query differs with HTTP 401 `{ status: 401, message: "..." }`.

`runSimulation`: start the fake on a random port, start the bridge with `BLUEBUBBLES_URL` pointed at it, `BRIDGE_PORT: 0` (random; `startServer`
must support port 0 and report the actual port; `publicWebhookUrl` must then be computed after listen), `allowAllSenders: true`,
`coalesceMs: 50`, `dataDir` = a temp dir; deliver one event; `waitForSent(1, 60_000)` (or until 2 s pass with ≥1 bubble, to collect
multi-bubble replies); stop everything; return `sent.map(s => s.message)`.

`test/e2e.test.ts` (uses `EchoCompleter`, never the network):
- DM: "hello" → one bubble `echo: hello`; webhook was registered once with `["new-message"]`; typing and read called when `privateApi: true`,
  not called when false.
- Duplicate delivery of the same guid → still one bubble.
- Our own echo (`isFromMe: true`) → no bubble.
- `/reset` → the reset reply, completer not called.
- Group without mention → nothing; with `@Claude` → reply with `selectedMessageGuid` set.
- Long completer text (3 paragraphs totalling > maxChunkChars with maxChunkChars=120) → multiple bubbles, each ≤ 120 chars.
- Stale webhook with a different token is deleted on boot and ours registered.
- `/health` shows `bluebubbles.reachable: true` and `replied: 1` after the first reply.
- `runDoctor` against the fake reports ping ok and model check via a fake `anthropic` (`{ models: { retrieve: async () => ({}) } }` cast).

### Step 14 — CLI

File: `src/cli.ts` (first line `#!/usr/bin/env node`; after `npm run build`, `chmod +x dist/cli.js` is not needed because `bin` is run through `node`).

Commands (`node dist/cli.js <cmd>`; `npm run <script>` maps to these):
- `serve` — loadConfig → logger (file + stderr when `process.stdout.isTTY`) → `startBridge` → wait for signals.
- `doctor` — loadConfig (tolerate `ConfigError`: print it as the first failed check) → `runDoctor` → print `formatChecks` → exit 1 if any `ok === false`.
- `install` / `uninstall` — build first is required; call `installAgent` / `uninstallAgent`.
- `tail` — tail the log file.
- `simulate [--text "..."] [--from "+15550001111"] [--group] [--fake-claude]` — `runSimulation`; print each bubble prefixed with `→ `.
- `chat` — interactive REPL in the terminal using the real completer and a `ConsoleTransport` (prints bubbles, no BlueBubbles). Reuses `createHandler`
  with a fixed chatGuid `console;-;local` and a temp or real data dir (`--ephemeral` for temp). Exit with `/quit` or Ctrl-C.
- `register-webhook` — one-off: run steps 1, 3 and 4 of the bridge boot without serving (useful when the public URL changed).
- `--help` / unknown → usage text, exit 2.
Parse args by hand (`process.argv.slice(3)`); no dependency.

Check: `npm run build && node dist/cli.js --help && node dist/cli.js simulate --fake-claude --text "hi"` prints `→ echo: hi`
(set `BLUEBUBBLES_PASSWORD=x` and `ANTHROPIC_API_KEY=x` in the environment for that run). Commit.

### Step 15 — Hardening pass

Go through this checklist and fix anything missing; add a test for each fix.
- Loop safety: a webhook with `isFromMe: true` never reaches the completer, even if `handle.address` is in the allowlist.
- Concurrency: two different chats are answered in parallel; the same chat never has two completions in flight.
- Idempotency: delivering the same `guid` twice (even across a restart, via the persisted dedupe snapshot) yields one reply.
- Startup without BlueBubbles: `serve` keeps running, `/health` reports `reachable: false`, and it recovers when the fake starts later (test with the fake started after the bridge).
- Oversized or malformed webhook bodies never crash the process (`uncaughtException`/`unhandledRejection` handlers in `cli.ts` log and keep running).
- Logs never contain the password, API key, or token: grep the log file in the e2e test for `password=` and the token string.
- Graceful stop finishes an in-flight reply before exiting (test: slow completer + `stop()` → bubble still sent).

### Step 16 — README

Write `README.md` for the person setting this up (an experienced operator; no domain explanations). Sections:
1. What it does (3 sentences) and the dedicated-Apple-ID recommendation.
2. Requirements: a Mac that stays on, BlueBubbles Server installed and signed into iMessage, Private API enabled (optional, with link to the
   BlueBubbles Private API docs), Node 22.18+ (`brew install node`), an Anthropic API key.
3. Install: clone, `cd imessage-claude`, `npm install`, `npm run build`, `cp .env.example .env`, fill `BLUEBUBBLES_PASSWORD`, `ANTHROPIC_API_KEY`,
   `ALLOWED_SENDERS`; `npm run doctor`; `npm run install-agent`; text the Mac.
4. Day-to-day: `npm run tail`, `npm run doctor`, `/help` in iMessage, how to change the persona (`persona.md`), where data lives, how to uninstall.
5. Keeping the Mac awake: the `pmset` command and the System Settings toggle; note that the display can sleep but the Mac must not.
6. Configuration reference: the table from section 4.
7. Troubleshooting: "no reply" checklist (allowlist, webhook registered, Private API, BlueBubbles logs), 401 from BlueBubbles (password),
   AppleScript send failures when the Mac is at the login window (enable Private API or auto-login), duplicate replies (two bridges registered → `register-webhook`).
8. Development: `npm run dev`, `npm test`, `npm run simulate -- --fake-claude --text "hi"`, `node dist/cli.js chat`.

No changelog or process notes in the README.

---

## 8. Definition of done

- `npm run typecheck`, `npm test`, and `npm run build` are clean on Linux and macOS.
- `node dist/cli.js simulate --fake-claude --text "hi"` prints `→ echo: hi`.
- With real credentials on a Mac: `npm run doctor` is all green except warnings you expect; `npm run install-agent` starts the agent;
  texting the Mac from an allowed number produces a reply with a typing indicator; `/reset` works; a photo gets described;
  killing the process (`kill -9`) results in launchd restarting it within ~10 s (`npm run tail` shows the boot log again).
- The repository contains no secrets. `.env` is git-ignored.

---

## 9. Stretch (only after section 8 passes)

- Tapback acknowledgement: react `like` to the triggering message when a reply takes longer than 8 s (Private API).
- `updated-message` handling for edited messages.
- Daily token budget with a notice bubble when exceeded.
- Contact names via `POST /api/v1/contact/query` for nicer dynamic context in groups.
