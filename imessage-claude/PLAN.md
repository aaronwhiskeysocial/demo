# imessage-claude — Implementation Plan

An always-on Mac service that turns iMessage into a Claude chat. BlueBubbles Server
(running on the same Mac, signed into iMessage) delivers inbound messages to this
bridge over a local webhook; the bridge calls Claude and sends the reply back
through the BlueBubbles REST API. It runs as a launchd LaunchAgent so it starts at
login and restarts itself if it crashes.

This document is written so that a less capable model can implement it without
further design decisions. Follow it in order. Every step ends with a check that
must pass before the next step starts.

**Current state of the repository:** only the scaffold exists — `package.json`,
`tsconfig.json`, `.gitignore`, this file, and installed `node_modules`. `src/` is
empty, so `npm run typecheck` currently reports `TS18003: No inputs were found` — that is expected and
clears as soon as Step 1 adds the first file under `src/`. Start at Step 1.

---

## 0. Rules for the executing model

1. Work through the steps in order. Do not skip a step's tests.
2. After every step run `npm run typecheck && npm test` from `imessage-claude/`. Both must be clean.
3. Commit after every step. Message format: `imessage-claude: step N — <short title>`.
4. Runtime dependency is `@anthropic-ai/sdk` only. Do not add any other runtime dependency.
   Dev dependencies are already installed (`typescript`, `@types/node`). Do not add more.
5. `package.json` and `tsconfig.json` already exist and are correct. Do not change them.
6. TypeScript constraints enforced by `tsconfig.json` (`erasableSyntaxOnly`, `verbatimModuleSyntax`):
   - No `enum`, no `namespace`, no constructor parameter properties (`constructor(private x)`), no `declare` fields.
     Use `as const` objects and union types instead of enums. Declare class fields explicitly and assign them in the constructor.
   - Type-only imports must use `import type { X } from "./y.ts"`.
   - Every relative import ends in `.ts` (example: `import { loadConfig } from "./config.ts"`).
     `tsc` rewrites them to `.js` in `dist/`; Node runs `src/*.ts` directly for tests and `npm run dev`.
   - `__dirname` does not exist (ESM). Use `path.dirname(fileURLToPath(import.meta.url))`.
7. Tests live in `test/*.test.ts`, use `node:test` and `node:assert/strict`, and run with
   `node --test "test/**/*.test.ts"` (already the `npm test` script; a bare directory argument does not work on Node 22).
   Tests import source from `../src/<file>.ts`. Tests must not touch the network, the real home directory, or the real
   Anthropic API. Use `fs.mkdtempSync(path.join(os.tmpdir(), "imc-"))` for data dirs.
   `npm run typecheck` does not cover `test/` (tsconfig includes only `src/`); do **not** add `test/` to `tsconfig.json`
   (it breaks `rootDir`). Node strips types from tests at runtime, so the rule-6 syntax limits apply to tests too.
   Shared test helpers go in `test/helpers.ts` (not `*.test.ts`, so the glob does not run it) and must not call `test()`.
8. Never log or print `BLUEBUBBLES_PASSWORD`, `ANTHROPIC_API_KEY`, or the webhook token. The logger redacts query strings.
9. Do not "remember" a different BlueBubbles or Anthropic API shape from training data. Section 2 is verified
   against the BlueBubbles server source and the installed SDK (`@anthropic-ai/sdk` 0.131). Use it as written.
10. When the plan says "exact signature", implement that signature. Other code may name helpers freely.
11. Keep each file focused. If a file grows past ~400 lines, split it, but keep the exported names listed in section 5.

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
| Send text | `POST /api/v1/message/text` | JSON `{ chatGuid, tempGuid, message, method }`. `method` is `"apple-script"` or `"private-api"`. `tempGuid` is required for apple-script; always send one: `"imessage-claude-" + randomUUID()`. Optional `selectedMessageGuid` (reply-to; only valid with `method: "private-api"`). Response `data` is the sent message; read `data.guid` if it is a string. |
| Start typing | `POST /api/v1/chat/:chatGuid/typing` | No body. Private API only. Typing clears automatically when a message is sent. Do **not** call `DELETE .../typing` (server bug: it starts typing again). |
| Mark chat read | `POST /api/v1/chat/:chatGuid/read` | No body. Private API only. |
| React (tapback) | `POST /api/v1/message/react` | JSON `{ chatGuid, selectedMessageGuid, reaction }`, `reaction` in `love, like, dislike, laugh, emphasize, question` (prefix `-` removes). Private API only. Stretch feature only. |
| Download attachment | `GET /api/v1/attachment/:guid/download` | Raw bytes; `Content-Type` header gives the media type. |
| List webhooks | `GET /api/v1/webhook` | `data` is an array of `{ id: number, url: string, events: string[] }`. |
| Register webhook | `POST /api/v1/webhook` | JSON `{ url: string, events: string[] }`. Use `events: ["new-message"]`. |
| Delete webhook | `DELETE /api/v1/webhook/:id` | Numeric id in the path. |

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
}, { timeout: 120_000 });
```

Note: the SDK transmits `betas` as the `anthropic-beta` HTTP request header, not as a body field,
and posts to `/v1/messages?beta=true`. Tests that inspect the outgoing request must read the header.

Rules:
- Which parameters to send depends on the model. Implement **exactly** this in `claude.ts`:
  ```ts
  export function requestProfile(model: string): { thinking: boolean; effort: boolean; fallbacks: boolean } {
    const m = model.toLowerCase();
    const fallbacks = m.startsWith("claude-opus-5") || m.startsWith("claude-sonnet-5-5") || m.startsWith("claude-fable-5");
    const thinking = fallbacks || m.startsWith("claude-sonnet-5") || /^claude-opus-4-[678]/.test(m) || m.startsWith("claude-sonnet-4-6");
    return { thinking, effort: thinking, fallbacks };
  }
  ```
  `thinking: true` → send `thinking: { type: "adaptive" }`; `effort: true` → send `output_config: { effort }`;
  `fallbacks: true` → send `betas: ["server-side-fallback-2026-07-01"]` and `fallbacks: "default"`.
  For anything else (for example `claude-haiku-4-5`) send none of those.
- Never send `temperature`, `top_p`, `top_k`, `budget_tokens`, or an assistant prefill.
- Never set `tool_choice` (leave it at the default `auto`).
- `response.stop_reason` must be checked before reading content:
  - `"end_turn"` or `"stop_sequence"`: normal.
  - `"max_tokens"` or `"model_context_window_exceeded"`: use the text produced and append `" …"`; log a warning.
  - `"refusal"`: the whole chain declined. Reply with a fixed sentence (see handler) and do not retry.
  - `"pause_turn"` (only with web search): append `response.content` as an assistant message and call once more; if it
    pauses again, use whatever text exists. Reply text = text blocks of the first response followed by those of the second.
  - `"tool_use"` cannot happen (no client tools are defined); treat as `end_turn`.
  - `"compaction"`, `null`, or any value not listed: treat as `"end_turn"` and log a warning that includes the value.
- Reply text = concatenation of all `content` blocks with `type === "text"`, in order. Ignore `thinking`,
  `server_tool_use`, `web_search_tool_result`, and `fallback` blocks.
- Usage: `response.usage.input_tokens`, `output_tokens`, `cache_read_input_tokens`, `cache_creation_input_tokens` (may be null/undefined; treat as 0).
- Typed errors, checked most specific first:
  `Anthropic.AuthenticationError` (401), `Anthropic.RateLimitError` (429), `Anthropic.BadRequestError` (400),
  `Anthropic.APIConnectionError` (network; check **before** `APIError` because it is a subclass),
  `Anthropic.APIError` (anything else). Let the SDK's built-in retries (default 2; retries 408/409/429/5xx and connection errors) run first.
- Conversation history: `messages` must start with a `user` message and alternate roles. Store assistant turns as
  plain text strings. Do not replay thinking blocks across turns (we store text only, so none exist).
- Images: user content blocks `{ type: "image", source: { type: "base64", media_type, data } }` with
  `media_type` in `image/jpeg | image/png | image/gif | image/webp`, placed **before** the text block.
- Validating the key and model without spending tokens: `await client.models.retrieve(model)` (non-beta).
- Client options used: `apiKey`, `timeout` (milliseconds), `maxRetries`, `fetch` (custom fetch for tests).

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
file exists (`process.loadEnvFile` does not override variables that are already set). All values are
validated; a bad value exits with a one-line error naming the variable.

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
| `BRIDGE_PORT` | `8787` | Listen port, integer 0–65535. `0` means pick a free port (used by simulate/tests). |
| `PUBLIC_WEBHOOK_URL` | (unset) | Base URL BlueBubbles should call. When unset the bridge uses `http://127.0.0.1:<actual listening port>`, computed after `listen`. Same Mac, so loopback. |
| `WEBHOOK_TOKEN` | (generated) | 32 hex chars. If unset, generated once and persisted in `<DATA_DIR>/state.json`. |
| `DATA_DIR` | macOS: `~/Library/Application Support/imessage-claude`; else `~/.imessage-claude` | Conversations, state, logs. Created with mode `0o700`. |
| `HISTORY_MAX_TURNS` | `40` | Max user+assistant messages kept per chat (oldest dropped). 2–400. |
| `COALESCE_MS` | `1500` | Wait for follow-up bubbles before replying. 0–10000. |
| `MAX_CONCURRENT` | `4` | Max chats being answered at once. 1–32. |
| `MAX_CHUNK_CHARS` | `1800` | Max characters per outgoing bubble. 200–10000. |
| `MAX_MESSAGES_PER_HOUR` | `60` | Per chat. Beyond it, one notice bubble per hour, then silence. 1–10000. |
| `SEND_METHOD` | `auto` | `auto` (private-api when available, else apple-script), `private-api`, `apple-script`. Affects sending only. |
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

## 5. Directory layout and file manifest (exports are authoritative)

```
imessage-claude/
  package.json (exists)   tsconfig.json (exists)   .gitignore (exists)   .env.example (step 1)   PLAN.md   README.md (step 16)
  src/
    types.ts        shared types only (section 6), incl. Transport and Completer
    config.ts       loadConfig, ConfigError, Config (type)
    log.ts          createLogger, redact, Logger (type)
    bluebubbles.ts  BlueBubblesClient, BlueBubblesError, ServerInfo (type)
    inbound.ts      classifyInbound, normalizeAddress, mentionPattern, stripMention, Dedupe
    chunk.ts        toPlainText, splitForIMessage
    store.ts        ConversationStore, chatFileName
    persona.ts      buildStableSystem, buildDynamicContext
    claude.ts       ClaudeCompleter, requestProfile, verifyModel
    stats.ts        Stats, maskAddress
    commands.ts     handleCommand, isCommand, CommandContext (type)
    queue.ts        ChatQueue
    handler.ts      createHandler, HandlerDeps (type)
    webhook.ts      startServer, ServerDeps (type)
    status.ts       renderStatusPage
    bridge.ts       startBridge, registerWebhookOnce, BridgeOptions, RunningBridge (types)
    launchd.ts      AGENT_LABEL, buildPlist, plistPath, installAgent, uninstallAgent, ExecFn (type)
    doctor.ts       runDoctor, formatChecks, Check (type)
    simulate.ts     FakeBlueBubbles, dmEvent, groupEvent, EchoCompleter, runSimulation
    cli.ts          no exports; defines ConsoleTransport and calls main() at top level
  test/
    helpers.ts      makeConfig, silentLogger   (not a test file)
    config.test.ts  log.test.ts  bluebubbles.test.ts  inbound.test.ts  chunk.test.ts  store.test.ts
    persona.test.ts claude.test.ts  stats.test.ts  commands.test.ts  queue.test.ts  handler.test.ts
    webhook.test.ts launchd.test.ts e2e.test.ts
```

---

## 6. Shared types — `src/types.ts` (write verbatim; extend only where a later step says so)

```ts
import type Anthropic from "@anthropic-ai/sdk";

export type Effort = "low" | "medium" | "high" | "xhigh" | "max";
export type SendMethod = "apple-script" | "private-api";
export type SendMethodSetting = "auto" | SendMethod;
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
export const IGNORE_REASONS: readonly IgnoreReason[] = [
  "not-new-message", "from-me", "tapback", "duplicate", "no-chat", "no-sender",
  "sender-not-allowed", "group-off", "group-not-mentioned", "empty", "audio",
];

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
  receivedAt: number;               // now() when accepted
  sentAt: number | null;            // data.dateCreated
}

export type Classified = { ok: true; message: InboundMessage } | { ok: false; reason: IgnoreReason };

export type ImageMediaType = "image/jpeg" | "image/png" | "image/gif" | "image/webp";

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
export interface CompletionUsage { input: number; output: number; cacheRead: number; cacheWrite: number }
export interface CompletionResult {
  text: string;
  stopReason: string | null;
  model: string;
  usage: CompletionUsage;
}
export type CompletionFailure =
  | { kind: "refusal" } | { kind: "rate-limited" } | { kind: "auth" } | { kind: "network" }
  | { kind: "bad-request"; detail: string } | { kind: "unknown"; detail: string };
export type CompletionOutcome = { ok: true; result: CompletionResult } | { ok: false; failure: CompletionFailure };

export interface Completer { complete(req: CompletionRequest): Promise<CompletionOutcome> }
```

---

## 7. Steps

### Step 1 — Types, config, logger, `.env.example`

Files: `src/types.ts` (section 6), `src/config.ts`, `src/log.ts`, `src/inbound.ts` (only `normalizeAddress` for now), `.env.example`.

`config.ts` (exact `Config` field names; every later step uses these):
```ts
export interface Config {
  bluebubblesUrl: string;          bluebubblesPassword: string;
  claudeModel: string;             claudeEffort: Effort;           claudeMaxTokens: number;   claudeWebSearch: boolean;
  botName: string;                 personaFile: string;
  allowedSenders: Set<string>;     allowAllSenders: boolean;
  groupMode: GroupMode;
  bridgeHost: string;              bridgePort: number;             publicWebhookUrl: string | null;  webhookToken: string | null;
  dataDir: string;                 historyMaxTurns: number;        coalesceMs: number;        maxConcurrent: number;
  maxChunkChars: number;           maxMessagesPerHour: number;
  sendMethod: SendMethodSetting;   typingIndicator: boolean;       readReceipts: boolean;
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
- Booleans accept `true/false/1/0/yes/no` (case-insensitive). Integers are range-checked per section 4
  (`BRIDGE_PORT` accepts 0–65535).
- `allowedSenders` is a `Set<string>` of `normalizeAddress()` values (import with `import { normalizeAddress } from "./inbound.ts"`;
  `inbound.ts` imports `Config` with `import type`, so the cycle is type-only and fine). `allowAllSenders` is true when the list is exactly `*`.
- `dataDir` default depends on `platform` (`darwin` → `~/Library/Application Support/imessage-claude`, else `~/.imessage-claude`).
  `logFile` and `personaFile` defaults derive from the final `dataDir`. `homeDir` is `opts.homeDir ?? os.homedir()`.
- `publicWebhookUrl` = the env value with trailing slashes stripped, or `null` when unset. Do **not** derive it from `bridgePort`.
- Throw `ConfigError` with a message like `BLUEBUBBLES_PASSWORD is required` or `CLAUDE_EFFORT must be one of low, medium, high, xhigh, max (got "fast")`.

`inbound.ts` (this step): only
```ts
export function normalizeAddress(addr: string): string;
```
Rules: trim; if it contains `@` → lowercase. Otherwise keep digits only (drop spaces, dashes, parentheses, dots);
if the original started with `+` → `+` + digits; else if 10 digits → `+1` + digits; else if 11 digits starting with `1` → `+` + digits;
otherwise `+` + digits.

`log.ts`:
```ts
export interface Logger { debug(msg: string, fields?: object): void; info(msg: string, fields?: object): void; warn(msg: string, fields?: object): void; error(msg: string, fields?: object): void; child(fields: object): Logger; flush(): Promise<void> }
export function createLogger(opts: { level: LogLevel; file?: string | null; stderr?: boolean; maxBytes?: number; keep?: number }): Logger;
export function redact(value: unknown): unknown;   // exported for tests
```
- Each line: `{"t":"<ISO>","level":"info","msg":"...", ...fields}`. Writes to the file (append) and, when `stderr` is true, a
  human-readable line to stderr: `01:02:03 INFO  msg key=value`.
- Use **synchronous** I/O (`fs.appendFileSync`, `fs.statSync`, `fs.renameSync`, `fs.mkdirSync({ recursive: true })`) so a line is
  on disk when the call returns; `flush()` resolves immediately. Wrap each write in try/catch and drop the line on error. Never throw.
- `redact` deep-copies objects/strings and replaces `password=...`, `guid=...`, `token=...` query values, anything matching
  `sk-ant-[A-Za-z0-9_-]+`, and any 32-hex-char token given via `createLogger`'s child fields `{ secrets: string[] }` with `***`.
  Simpler rule that satisfies this: `redact` takes an optional second argument `secrets: string[]` and replaces each literal occurrence.
  Apply it to `msg` and every field object before writing.
- Rotation: before each append, if the file size is > `maxBytes` (default 10 MiB), rename `bridge.log` → `bridge.log.1`
  (shifting `.1`→`.2` ... up to `keep`, default 5) and start a new file. Create the directory if missing. Files are created with mode `0o600`.

`.env.example`: every variable from section 4, with a one-line comment each.

Tests (`test/config.test.ts`, `test/log.test.ts`):
- defaults apply when only the two required variables are set; `isDarwin` and `dataDir` follow `platform`; `publicWebhookUrl` is `null` when unset.
- each invalid value (effort, port 70000, boolean `maybe`, integer out of range) throws `ConfigError` naming the variable; port `0` is accepted.
- `ALLOWED_SENDERS="+1 (555) 123-4567, Bob@Example.com"` normalizes to `+15551234567` and `bob@example.com`; `*` sets `allowAllSenders`.
- logger writes a JSON line with a redacted `url` field; rotation renames when `maxBytes` is tiny (e.g. 200); a secret literal is replaced.

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
  constructor(opts: { baseUrl: string; password: string; log: Logger; fetchImpl?: typeof fetch; sendMethod: SendMethodSetting; privateApi?: boolean; timeoutMs?: number })
  readonly privateApi: boolean;                 // from opts (default false); bridge.ts sets it via withCapabilities after serverInfo()
  withCapabilities(opts: { privateApi: boolean; sendMethod: SendMethodSetting }): BlueBubblesClient;  // new instance sharing baseUrl/password/fetch/log
  effectiveMethod(): SendMethod;                // "auto" → privateApi ? "private-api" : "apple-script"; otherwise the setting itself
  ping(): Promise<boolean>;                     // true on HTTP 200 + body.status === 200; false on anything else (never throws)
  serverInfo(): Promise<ServerInfo>;            // throws BlueBubblesError on failure
  sendText(chatGuid: string, text: string, opts?: { replyToGuid?: string }): Promise<{ guid: string | null }>;
  startTyping(chatGuid: string): Promise<void>; // no-op when !privateApi
  markRead(chatGuid: string): Promise<void>;    // no-op when !privateApi
  downloadAttachment(guid: string, maxBytes: number): Promise<{ contentType: string | null; data: Buffer } | null>;
  listWebhooks(): Promise<Array<{ id: number; url: string; events: string[] }>>;
  registerWebhook(url: string, events: string[]): Promise<void>;
  deleteWebhook(id: number): Promise<void>;
}
```
- Build URLs as `new URL(baseUrl.replace(/\/+$/, "") + path)` where `path` starts with `/api/v1/`, then
  `url.searchParams.set("password", password)`. Encode chat GUIDs with `encodeURIComponent`
  (`iMessage;-;+1555` → `iMessage%3B-%3B%2B1555`; `URL` preserves the percent-encoding).
- `sendText`: `const method = this.effectiveMethod()`; body `{ chatGuid, tempGuid: "imessage-claude-" + randomUUID(), message: text, method }`.
  Add `selectedMessageGuid: opts.replyToGuid` **only** when `opts.replyToGuid` is set and `method === "private-api"`; never send it with
  `apple-script`. Retry once after 1 s on network error or HTTP 5xx (`sendText` only; every other method is single-shot).
  Per-request timeout via `AbortSignal.timeout(timeoutMs)` (default 30 s; 60 s for `sendText` because AppleScript can be slow).
- `downloadAttachment`: return `null` when the `Content-Length` header exceeds `maxBytes`, when the downloaded body exceeds `maxBytes`, or on 404.
- Every error path throws `BlueBubblesError` with the HTTP status and the parsed body (if JSON), except `ping` which returns false.
- Log each request at `debug` as `{ method, path }` (never the query string).

Tests (`test/bluebubbles.test.ts`): start an in-process `node:http` server that records requests and returns canned envelopes. Assert:
password query on every call; chat GUID path-encoded; `sendText` body fields; method selection in three cases —
(a) `privateApi: false`, `sendMethod: "auto"` → `apple-script`, no `selectedMessageGuid`;
(b) `privateApi: true`, `sendMethod: "auto"`, `replyToGuid` set → `private-api` with `selectedMessageGuid`;
(c) `privateApi: true`, `sendMethod: "apple-script"`, `replyToGuid` set → `apple-script`, no `selectedMessageGuid`;
retry once on 500 then success; `ping` false on 401; `downloadAttachment` returns null when Content-Length exceeds maxBytes;
`startTyping` makes no request when `privateApi` is false; `deleteWebhook(3)` calls `DELETE /api/v1/webhook/3`.

### Step 3 — Inbound classification and de-duplication

File: `src/inbound.ts` (extend).

```ts
export class Dedupe { constructor(capacity?: number /* 2000 */, seed?: string[]); has(guid: string): boolean; add(guid: string): void; snapshot(): string[] /* newest last, max 500 */ }
export function mentionPattern(botName: string): RegExp;
export function stripMention(text: string, botName: string): string;
export function classifyInbound(event: BBWebhookEvent, ctx: { config: Pick<Config, "allowedSenders" | "allowAllSenders" | "groupMode" | "botName" | "imageUnderstanding">; dedupe: Dedupe; now?: () => number }): Classified;
```
- `mentionPattern(botName)` = `new RegExp("(^|\\s)@?" + escapeRegExp(botName) + "\\b[:,]?", "i")`; write a 3-line `escapeRegExp`.
- `stripMention(text, botName)` = `text.replace(mentionPattern(botName), "$1").replace(/[ \t]{2,}/g, " ").trim()`.
  Example: `"hey @Claude, what's up"` → `"hey what's up"`.
- `Dedupe` is an insertion-ordered `Set`; when size exceeds `capacity`, delete the oldest entry.
- Classification order (return the first matching reason):
  1. `event.type !== "new-message"` → `not-new-message`
  2. `data.isFromMe` → `from-me`
  3. `data.associatedMessageGuid` truthy, or `associatedMessageType` is a non-zero number or a non-empty string → `tapback`
  4. `data.guid` missing or `dedupe.has(guid)` → `duplicate`
  5. `chat = data.chats?.[0]`; `chatGuid = chat?.guid ?? data.chatGuid`; missing → `no-chat`
  6. `sender = data.handle?.address`; missing/empty → `no-sender`
  7. not `allowAllSenders` and `!allowedSenders.has(normalizeAddress(sender))` → `sender-not-allowed`
  8. `isGroup` = chatGuid includes `;+;` or `(chat?.participants?.length ?? 0) > 1`. If isGroup and `groupMode === "off"` → `group-off`.
  9. `let text = (data.text ?? "").replace(/￼/g, "").trim()`. If isGroup and `groupMode === "mention"`:
     if `!mentionPattern(botName).test(text)` → `group-not-mentioned`; else `text = stripMention(text, botName)`.
  10. `images` = attachments with `mimeType` starting `image/`, not `isSticker`, only when `imageUnderstanding` (else `[]`).
      If `data.isAudioMessage` and text is empty → `audio`. If text is empty and images is empty → `empty`.
  11. `dedupe.add(guid)`; return ok with `InboundMessage` (`chatName = chat?.displayName || null`, `receivedAt = (ctx.now ?? Date.now)()`,
      `sentAt = data.dateCreated ?? null`, `senderNormalized = normalizeAddress(sender)`).

Tests (`test/inbound.test.ts`): one test per reason, plus the happy DM path, group mention path (mention stripped as in the example),
group `all` path, U+FFFC-only text with one image → ok with empty text, sticker excluded, allowlist by email, duplicate on second call,
`Dedupe` capacity eviction, `normalizeAddress` cases from step 1.

### Step 4 — Plain text and chunking

File: `src/chunk.ts`.

```ts
export function toPlainText(markdown: string): string;
export function splitForIMessage(text: string, maxChars: number): string[];
```
`toPlainText` rules (apply in this order, line by line where noted):
- Fenced code blocks: remove the ``` fence lines, keep the code lines verbatim (do not apply the rules below inside them).
- Headings `#{1,6} Title` → `Title` (keep a blank line after it).
- Bold/italic markers: `**x**`, `__x__`, `*x*`, `_x_` → `x`, only when the marker pair is on one line, the opening marker is at the
  start of the line or preceded by whitespace/punctuation, and the closing marker is at the end or followed by whitespace/punctuation.
  Never alter markers inside a word (`snake_case_name` stays unchanged).
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

Tests (`test/chunk.test.ts`): each sanitize rule incl. `snake_case_name`; packing; long paragraph split at sentences; hard split of a
5000-char word; emoji-safe hard split; never exceeds max over 50 generated inputs (deterministic loop building random-length words).

### Step 5 — Conversation store

File: `src/store.ts`.

```ts
export class ConversationStore {
  constructor(opts: { dataDir: string; log: Logger; maxTurns: number })
  init(): Promise<void>;                                   // mkdir -p dataDir (0o700) and dataDir/conversations, load state.json
  getHistory(chatGuid: string): Promise<StoredTurn[]>;     // oldest first, at most maxTurns, starts with a "user" turn
  appendTurns(chatGuid: string, turns: StoredTurn[]): Promise<void>;
  reset(chatGuid: string): Promise<void>;                  // deletes the chat file
  getSettings(chatGuid: string): Promise<ChatSettings>;    // from state.json
  setSettings(chatGuid: string, patch: Partial<ChatSettings>): Promise<void>;   // undefined values delete the key
  getState<T>(key: string, fallback: T): Promise<T>;       // generic small values (webhookToken, dedupe snapshot)
  setState(key: string, value: unknown): Promise<void>;
}
export function chatFileName(chatGuid: string): string;    // sha256(chatGuid).slice(0,16) + ".jsonl"
```
- One JSONL file per chat under `<dataDir>/conversations/`: each line is a `StoredTurn`. Appends use `fs.appendFile`. When a file exceeds
  `maxTurns * 4` lines, rewrite it keeping the last `maxTurns` turns (atomic: write `.tmp` then rename).
- `getHistory` drops leading assistant turns and collapses two consecutive same-role turns by joining text with `\n\n`
  so the result alternates and starts with `user`. Skips unparsable lines with a warning.
- `state.json` holds `{ settings: Record<chatGuid, ChatSettings>, kv: Record<string, unknown> }`, written atomically with mode `0o600`.
  Serialize all writes through a single promise chain so concurrent writers cannot interleave.

Tests (`test/store.test.ts`): append/get round trip; trimming to maxTurns; alternation repair; reset; settings patch and delete;
corrupt line tolerated; 20 concurrent `setState` calls all land.

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
export function requestProfile(model: string): { thinking: boolean; effort: boolean; fallbacks: boolean };   // exactly as in 2.3
export class ClaudeCompleter implements Completer {
  constructor(opts: { client?: Anthropic; log: Logger })     // default client: new Anthropic({ timeout: 120_000 })
  complete(req: CompletionRequest): Promise<CompletionOutcome>;
}
export async function verifyModel(client: Anthropic, model: string): Promise<{ ok: true } | { ok: false; detail: string }>;
```
- Build the request exactly as section 2.3. `req.system` maps to system blocks; `cache: true` adds `cache_control: { type: "ephemeral" }`.
- Handle `pause_turn` once. Map stop reasons and errors to `CompletionOutcome` per section 2.3. On `refusal` return `{ ok: false, failure: { kind: "refusal" } }`.
- Log at `info`: `{ model: response.model, stop: stop_reason, in, out, cacheRead, ms }`.
- `verifyModel`: `await client.models.retrieve(model)`; map `NotFoundError` → `{ ok: false, detail: "unknown model" }`,
  `AuthenticationError` → `"invalid API key"`, other errors → their message. Optional extra: if the returned object has a non-null
  `capabilities` and `requestProfile(model).thinking` is true but `capabilities.thinking?.types?.adaptive?.supported === false`,
  return `{ ok: false, detail: "model does not support adaptive thinking; adjust requestProfile" }`.

Tests (`test/claude.test.ts`): construct `new Anthropic({ apiKey: "test", fetch: fakeFetch, maxRetries: 0 })` where
`fakeFetch: typeof fetch` records the request (`JSON.parse(String(init?.body))` and `new Headers(init?.headers).get("anthropic-beta")`)
and returns `new Response(JSON.stringify(body), { status, headers: { "content-type": "application/json" } })`. **The content-type header
is required**: the SDK only parses JSON when it contains `application/json`; otherwise `response.content` is undefined.
A successful body: `{ id: "msg_1", type: "message", role: "assistant", model: "claude-opus-5-5", content: [{ type: "text", text: "hi" }], stop_reason: "end_turn", stop_sequence: null, usage: { input_tokens: 1, output_tokens: 1, cache_read_input_tokens: 0, cache_creation_input_tokens: 0 } }`.
An error body: `{ type: "error", error: { type: "authentication_error" | "rate_limit_error", message: "..." } }` with status 401/429.
For the network case make `fakeFetch` throw `new TypeError("fetch failed")` (the SDK wraps it in `APIConnectionError`).
Assert for Opus 5.5: header `anthropic-beta` equals `server-side-fallback-2026-07-01`; body has `fallbacks: "default"`,
`thinking: { type: "adaptive" }`, `output_config: { effort: "low" }`, `system[0].cache_control` = `{ type: "ephemeral" }`, no `cache_control`
on `system[1]`, no `temperature`, no `betas` key. For Haiku 4.5: no `anthropic-beta` header and no `fallbacks`/`thinking`/`output_config`.
Also: text concatenation over two text blocks; `max_tokens` → suffix `" …"`; refusal mapping; 401 → `auth`; 429 → `rate-limited`;
network → `network`; `pause_turn` continuation sends the first response's content back as an assistant message and concatenates text.
`test/persona.test.ts`: stable text contains bot name and persona text; dynamic text mentions group name and photo count.

### Step 7 — Stats and slash commands

Files: `src/stats.ts`, `src/commands.ts`.

`stats.ts`:
```ts
export class Stats {
  readonly startedAt: number;
  received = 0; ignored: Record<IgnoreReason, number>; replied = 0; errors = 0; commands = 0;
  tokensIn = 0; tokensOut = 0; cacheRead = 0;
  dayKey = ""; repliedToday = 0;
  lastInboundAt: number | null = null; lastReplyAt: number | null = null; lastLatencyMs: number | null = null;
  recent: Array<{ at: number; chat: string /* masked */; latencyMs: number; chunks: number; outcome: "reply" | "command" | "error" }> = [];  // newest first, max 20
  constructor(now?: () => number)                 // initialize `ignored` with every key of IGNORE_REASONS at 0
  noteReceived(): void;                            // received++, lastInboundAt = now()
  noteIgnored(reason: IgnoreReason): void;         // ignored[reason]++ only; no `recent` entry
  noteReply(info: { chat: string; latencyMs: number; chunks: number; usage: CompletionUsage }): void;
  noteCommand(info: { chat: string; latencyMs: number }): void;
  noteError(info: { chat: string; latencyMs: number }): void;
  snapshot(): Record<string, unknown>;
}
export function maskAddress(addr: string): string;
```
- `noteReply`: `replied++`, add usage to `tokensIn/tokensOut/cacheRead`, set `lastReplyAt`/`lastLatencyMs`, push to `recent`, and
  `const k = new Date(now()).toDateString(); if (k !== this.dayKey) { this.dayKey = k; this.repliedToday = 0; } this.repliedToday++;`.
- `snapshot()` returns every counter plus `repliedToday`, `avgLatencyMs` (mean of `recent[].latencyMs`, 0 when empty) and
  `cacheHitPct = tokensIn + cacheRead === 0 ? 0 : Math.round(100 * cacheRead / (tokensIn + cacheRead))`.
- `maskAddress`: phone (no `@`): first 2 characters + `"•••••"` (always five bullets) + last 4 characters, e.g. `"+15551234567"` → `"+1•••••4567"`;
  inputs shorter than 7 characters → `"•••••"`. Email: first character + `"•••@"` + domain, e.g. `"bob@example.com"` → `"b•••@example.com"`.

`commands.ts`:
```ts
export interface CommandContext { chatGuid: string; sender: string; store: ConversationStore; config: Config; stats: Stats; now?: () => number }
export function isCommand(text: string): boolean;                  // starts with "/" followed by a letter
export async function handleCommand(text: string, ctx: CommandContext): Promise<string | null>;  // reply text, or null when not a command
```
Commands (case-insensitive, first token):
- `/help` — lists commands in one bubble.
- `/reset` (alias `/forget`, `/new`) — `store.reset(chatGuid)` → `Fresh start. I've forgotten this conversation.`
- `/status` — model, effort, turns in memory, uptime, `repliedToday` as "replies today".
- `/model` — shows the current model; `/model <id>` sets a per-chat override if `<id>` matches `/^claude-[a-z0-9.-]+$/`, else error text.
  `/model default` removes the override.
- `/effort <low|medium|high|xhigh|max>` — per-chat override; `/effort default` removes it.
- `/persona <text>` — per-chat persona override (max 2000 chars); `/persona clear` removes it; `/persona` shows it.
- Unknown `/xyz` → `I don't know that command. Try /help.`

Tests (`test/commands.test.ts`): each command's effect on the store and its reply; unknown command; non-command returns null.
`test/stats.test.ts`: counters, `recent` capped at 20, `repliedToday` resets on a new day (inject `now`), `maskAddress` for phone and email.

### Step 8 — Per-chat coalescing queue

File: `src/queue.ts`.

```ts
export class ChatQueue {
  constructor(opts: { coalesceMs: number; maxConcurrent: number; process: (chatGuid: string, batch: InboundMessage[]) => Promise<void>; log: Logger })
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
- Errors thrown by `process` are logged at `error` and never stop the queue. Timers are `unref()`'d so they never keep the process alive on their own.
- Remove a chat's entry from all maps when it has nothing pending and is not processing (no unbounded growth).

Tests (`test/queue.test.ts`): two pushes within the window produce one batch of 2; a push during processing produces a second
batch after the first completes; `maxConcurrent: 1` serializes two chats; a throwing `process` does not break later batches;
`drain` resolves. Use real timers with small `coalesceMs` (10 ms).

### Step 9 — Handler

File: `src/handler.ts`.

```ts
export interface HandlerDeps { config: Config; transport: Transport; completer: Completer; store: ConversationStore; stats: Stats; log: Logger; now?: () => number }
export function createHandler(deps: HandlerDeps): (chatGuid: string, batch: InboundMessage[]) => Promise<void>;
```
Behavior for one batch (all messages share `chatGuid`):
0. `const startedAt = now()`; every `latencyMs` below is `now() - startedAt`. `sender` = last message's sender; `chat = maskAddress(sender)`;
   `isGroup` and `chatName` from the last message; `triggerGuid` = last message's guid.
1. Rate limit: keep an in-memory map `chatGuid → timestamps` of handled batches in the last hour (prune entries older than an hour on every call).
   If the count is `>= maxMessagesPerHour`, send `I'm pausing replies in this chat for a bit — too many messages in the last hour.`
   at most once per hour per chat, then return.
2. Join the batch texts with `\n` (skip empty), collect all images.
3. If the joined text `isCommand(...)`: `const reply = await handleCommand(text, { chatGuid, sender, store, config, stats, now })`;
   send `splitForIMessage(reply ?? "", config.maxChunkChars)` in order; `stats.noteCommand({ chat, latencyMs })`; return.
4. If `config.typingIndicator`: `transport.startTyping(chatGuid)` fire-and-forget (catch and log at debug).
5. Settings: `const s = await store.getSettings(chatGuid)`; model = `s.model ?? config.claudeModel`; effort = `s.effort ?? config.claudeEffort`.
6. Images: for each image (max 4), `transport.downloadAttachment(guid, config.maxImageBytes)`. Media type = `contentType` header if it is one of
   the four allowed types, else the payload `mimeType` if allowed, else skip and count it. If any image was skipped, append
   `\n\n[The person attached ${n} photo(s) in a format I can't view.]` to the user text.
7. History: `await store.getHistory(chatGuid)` → `BetaMessageParam[]` (text only). Append the new user turn: content is an array of
   image blocks followed by one text block; if text is empty and there are images, text = `(photo)`.
8. System: `[{ text: buildStableSystem({ botName: config.botName, personaText: s.persona ?? filePersona }), cache: true },
   { text: buildDynamicContext({ now: new Date(now()), timeZone: Intl.DateTimeFormat().resolvedOptions().timeZone, chat: { isGroup, chatName, sender }, imagesAttached: imageBlocks.length }), cache: false }]`.
   `filePersona` is read once at handler creation from `config.personaFile` if it exists (else `null`).
9. `completer.complete({ system, messages, model, effort, maxTokens: config.claudeMaxTokens, webSearch: config.claudeWebSearch })`.
   On failure reply with exactly one bubble:
   - refusal: `I can't help with that one.`
   - rate-limited: `I'm being rate limited right now. Give me a minute and try again.`
   - auth: `My API key isn't working. Whoever runs this Mac needs to check it.` (also log at `error`)
   - network: `I can't reach Claude right now. Try again in a bit.`
   - bad-request/unknown: `Something went wrong on my end. Try again in a minute.` (log detail at `error`)
   Then `stats.noteError({ chat, latencyMs })` and return (do not persist the turn). If sending the error bubble itself throws, log and return.
10. `text = toPlainText(result.text)`; `chunks = splitForIMessage(text, config.maxChunkChars)`; if empty, `chunks = ["(no reply)"]` and `text = "(no reply)"`.
11. Send chunks in order, awaiting each; 300 ms pause between chunks. The first chunk passes `replyToGuid: triggerGuid` when
    `replyThreading === "all"` or (`"group"` and isGroup). If a send throws, log at `error`, `stats.noteError({ chat, latencyMs })`,
    stop sending further chunks and skip items 12–14.
12. If `config.readReceipts`: `transport.markRead(chatGuid)` best-effort.
13. Persist: `at = now()`; `store.appendTurns(chatGuid, [{ role: "user", text: userTextForHistory, at }, { role: "assistant", text, at }])` where
    `userTextForHistory` = the joined text, or `"(photo)"` when it was empty, followed by `" [sent N photo(s)]"` when N > 0 (never store image bytes),
    and the assistant `text` is the plain text from item 10.
14. `stats.noteReply({ chat, latencyMs, chunks: chunks.length, usage: result.usage })`.

Tests (`test/handler.test.ts`) with a `FakeTransport` (records calls, `privateApi` configurable) and a `FakeCompleter`
(scripted outcomes): happy path sends chunked bubbles and persists turns; command path does not call the completer; refusal
sends one bubble and persists nothing; typing/read not called when `config.typingIndicator`/`readReceipts` are false; image download → image block before
text; unsupported image → note appended; rate limit notice once; reply threading only in groups by default; send failure stops further chunks.
Use `makeConfig` from `test/helpers.ts` (define it now; see step 13 for its body) and a silent logger (`createLogger({ level: "error", file: null, stderr: false })`).

### Step 10 — Webhook server and status page

Files: `src/webhook.ts`, `src/status.ts`.

```ts
export interface ServerDeps { host: string; port: number; log: Logger; onEvent: (event: BBWebhookEvent) => void; health: () => Record<string, unknown>; token: string }
export function startServer(deps: ServerDeps): Promise<{ server: import("node:http").Server; port: number; close(): Promise<void> }>;
export function renderStatusPage(): string;   // status.ts
```
- `startServer` listens on `host:port`; the returned `port` is the actual port from `server.address()` (matters when `port` is 0).
  `close()` calls `server.closeAllConnections()` then awaits `server.close()`.
Routes:
- `POST /webhook/<token>`: compare with `crypto.timingSafeEqual` on equal-length buffers (lengths differ → 401 without comparing);
  401 body `{"ok":false}`. If the `Content-Length` header is > 1 MiB respond 413 immediately; also abort at 413 if the streamed body exceeds 1 MiB.
  Parse JSON regardless of content type (400 on failure). Respond `200 {"ok":true}` **before** calling `onEvent` (call it via `setImmediate`
  so a slow handler never delays the response, and wrap it in try/catch → log at `error`).
- `GET /health`: `200` JSON from `deps.health()`.
- `GET /`: `200 text/html` = `renderStatusPage()`.
- Anything else (including non-POST on the webhook path): 404 JSON. Never serve the token anywhere. Set `Cache-Control: no-store` on all responses.

Status page (single self-contained HTML string, no external assets): polls `/health` every 5 s and renders:
title `imessage-claude`, a green/amber/red dot for BlueBubbles reachability, Private API on/off, model + effort, uptime,
big-number tiles from `stats.repliedToday`, `stats.avgLatencyMs`, `stats.tokensIn`/`tokensOut`, `stats.cacheHitPct`, queue depth,
and a "recent" list of the last 20 events (time, masked chat, outcome, latency). Respect `prefers-color-scheme`. Under 250 lines. No frameworks.

Tests (`test/webhook.test.ts`): wrong token → 401 and `onEvent` not called; right token → 200 and `onEvent` receives the parsed body;
oversized body → 413; bad JSON → 400; GET on the webhook path → 404; `/health` returns the health object; `/` returns HTML containing `imessage-claude`.

### Step 11 — Bridge boot sequence

File: `src/bridge.ts`.

```ts
export interface BridgeOptions {
  config: Config; log: Logger; completer?: Completer; fetchImpl?: typeof fetch;
  intervals?: { pingMs?: number; webhookRetryMs?: number; healthMs?: number; dedupeMs?: number };   // defaults 10_000, 60_000, 60_000, 60_000
}
export interface RunningBridge { port: number; ready: Promise<void>; stop(): Promise<void>; health(): Record<string, unknown>; token: string; stats: Stats }
export async function startBridge(opts: BridgeOptions): Promise<RunningBridge>;
export async function registerWebhookOnce(opts: { config: Config; log: Logger; fetchImpl?: typeof fetch }): Promise<string>;  // returns the registered URL
```
- The bridge always builds a `BlueBubblesClient` from `config` (+ `fetchImpl`). `completer` defaults to
  `new ClaudeCompleter({ client: new Anthropic({ timeout: 120_000 }), log })` (the SDK does not throw at construction when no key is set;
  a missing key surfaces as the `auth` failure in the handler).
- `version` = `createRequire(import.meta.url)("../package.json").version` (works from `src/` and `dist/`).

Sequence:
1. `store.init()`. Token: `config.webhookToken ?? await store.getState("webhookToken", null)`; if none, generate `randomBytes(16).toString("hex")`
   and persist. Load the dedupe seed from `store.getState("dedupe", [])`.
2. Start the HTTP server. `const port = server.port`; `const webhookBase = config.publicWebhookUrl ?? \`http://127.0.0.1:${port}\``.
   **`startBridge` resolves here.** Steps 3–6 run in the background and are never awaited by `startBridge`.
   `ready` resolves the first time step 4 succeeds and never rejects. `stop()` may be called before `ready` resolves and must cancel the loops.
3. Connect loop: `client.ping()`; while false, log `warn` once per minute and retry every `pingMs` (do not exit). Then `serverInfo()`;
   `privateApi = info.privateApi && info.helperConnected` (`SEND_METHOD` never changes `privateApi`; it only affects sending through
   `effectiveMethod()`). `transport = client.withCapabilities({ privateApi, sendMethod: config.sendMethod })`.
   Log `info` `{ serverVersion, privateApi, sendMethod: transport.effectiveMethod() }`. If `config.sendMethod === "private-api"` but
   `privateApi` is false, log a `warn` and continue.
4. Webhook registration: `listWebhooks()`; our URL is `${webhookBase}/webhook/${token}`. If an entry with exactly our URL exists, keep it.
   Delete any entry whose URL starts with `${webhookBase}/webhook/` but differs (stale token). Otherwise `registerWebhook(url, ["new-message"])`.
   Failures are logged at `error` and retried every `webhookRetryMs` in the background; the bridge still runs.
5. Wire `onEvent` → `stats.noteReceived()` → `classifyInbound` → `stats.noteIgnored(reason)` (log at `debug`, except `sender-not-allowed` at `info`,
   at most once per sender per hour) or `queue.push(message)`. Events that arrive before step 3 finishes are still classified and queued; the handler
   uses the transport once available (hold a promise for the transport and await it inside `process`). Persist the dedupe snapshot every `dedupeMs` and on stop.
6. Every `healthMs`: `ping()` to update `health().bluebubbles.reachable` and `lastCheckAt`.
7. `stop()`: stop timers and loops, `await server.close()` (which closes all connections), `queue.drain()` with a 20 s cap, persist dedupe, `log.flush()`.
8. `health()` returns `{ ok: bluebubbles.reachable && webhook.registered, version, uptimeSec, model, effort, sendMethod, privateApi,
   bluebubbles: { reachable, serverVersion, lastCheckAt }, webhook: { registered, url: "<webhookBase>/webhook/•••" }, queue: { depth, inFlight }, stats: stats.snapshot() }`.
9. At boot log a `warn` if `allowedSenders` is empty and not `allowAllSenders`: `No ALLOWED_SENDERS configured: every message will be ignored.`
   Log a `warn` if `bridgeHost` is not loopback.

`registerWebhookOnce` runs steps 1, 3 (a single `ping()`; throw `BlueBubblesError` when unreachable) and 4 once, with
`webhookBase = config.publicWebhookUrl ?? \`http://127.0.0.1:${config.bridgePort}\``, and returns the registered URL.

`startBridge` must not call `process.exit`. The CLI handles signals.

Test: covered by `test/e2e.test.ts` in step 13.

### Step 12 — launchd install/uninstall, doctor, tail

Files: `src/launchd.ts`, `src/doctor.ts`.

`launchd.ts`:
```ts
export const AGENT_LABEL = "com.imessage-claude.bridge";
export type ExecFn = (cmd: string, args: string[]) => Promise<{ code: number; stdout: string; stderr: string }>;
export function buildPlist(opts: { nodePath: string; scriptPath: string; workingDirectory: string; logDir: string; envPath: string; homeDir: string }): string;
export function plistPath(homeDir: string): string;    // <homeDir>/Library/LaunchAgents/com.imessage-claude.bridge.plist
export async function installAgent(opts: { config: Config; log: Logger; exec?: ExecFn; nodePath?: string }): Promise<void>;
export async function uninstallAgent(opts: { config: Config; log: Logger; exec?: ExecFn }): Promise<void>;
```
Plist content (XML, exact keys): `Label`; `ProgramArguments` = `[nodePath, scriptPath, "serve"]`; `WorkingDirectory`;
`EnvironmentVariables` = `{ PATH: "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin", HOME: <homeDir>, IMESSAGE_CLAUDE_ENV: <envPath> }`;
`RunAtLoad` true; `KeepAlive` true; `ThrottleInterval` 10; `ProcessType` `Background`; `StandardOutPath` `<logDir>/launchd.out.log`;
`StandardErrorPath` `<logDir>/launchd.err.log`. XML-escape every inserted value.
`installAgent` computes `scriptPath = path.join(config.packageRoot, "dist", "cli.js")`, `workingDirectory = config.packageRoot`,
`logDir = path.dirname(config.logFile)`, `envPath = config.envPath ?? path.join(config.packageRoot, ".env")`, `homeDir = config.homeDir`;
`nodePath` defaults to `process.execPath`. Default `exec` runs `child_process.execFile`.

`installAgent`: refuse unless `config.isDarwin` (throw with a clear message); require `dist/cli.js` to exist (tell the user to run `npm run build`);
create `logDir`; write the plist; run `launchctl bootout gui/<uid>/<label>` (ignore failure); `launchctl bootstrap gui/<uid> <plist>`;
`launchctl kickstart -k gui/<uid>/<label>`; print where logs are and suggest `npm run doctor`. `uid` from `process.getuid?.()`.
`uninstallAgent`: `bootout` then delete the plist.

`doctor.ts`:
```ts
export interface Check { name: string; ok: boolean | null /* null = warning */; detail: string; fix?: string }
export async function runDoctor(opts: { config: Config; log: Logger; fetchImpl?: typeof fetch; exec?: ExecFn; anthropic?: Anthropic }): Promise<Check[]>;
export function formatChecks(checks: Check[]): string;   // ✔ / ✖ / ▲ lines plus fix hints
```
Checks, in order: Node >= 22.18; `.env` found at the resolved path and not group/world-readable (warning with fix `chmod 600 .env`);
required variables present; BlueBubbles ping; server info (version, Private API + helper connected — warning, not failure, when off:
typing/read receipts disabled); Anthropic credentials and model (`verifyModel`); webhook registered for our URL (warning if the bridge has
never run: "will register on first start"); bridge `/health` reachable on `BRIDGE_PORT` (warning if not running); `ALLOWED_SENDERS` non-empty (warning);
on macOS, `pmset -g` parsed for the ` sleep ` line — warning if its value is not `0`, fix `sudo pmset -a sleep 0 disksleep 0` plus the System Settings path;
on macOS, `launchctl print gui/<uid>/com.imessage-claude.bridge` exit code 0 → agent loaded (warning otherwise, fix `npm run install-agent`).

Tests (`test/launchd.test.ts`): plist contains the exact keys/values and escapes `&`; `installAgent` with a fake `exec` records the three
launchctl calls in order and writes the plist under a temp `homeDir`; refuses on non-darwin. `doctor` is exercised in `e2e.test.ts`.

### Step 13 — Simulation and end-to-end test

Files: `src/simulate.ts`, `test/helpers.ts`, `test/e2e.test.ts`.

`test/helpers.ts`:
```ts
export function makeConfig(overrides: Partial<Config> = {}): Config {
  const dataDir = fs.mkdtempSync(path.join(os.tmpdir(), "imc-"));
  const base = loadConfig({ env: { BLUEBUBBLES_PASSWORD: "pw", ANTHROPIC_API_KEY: "x", ALLOWED_SENDERS: "*", DATA_DIR: dataDir, BRIDGE_PORT: "0", COALESCE_MS: "50" }, envPath: null, platform: "linux", homeDir: dataDir });
  return { ...base, ...overrides };
}
export function silentLogger(): Logger;   // createLogger({ level: "error", file: null, stderr: false })
```

`simulate.ts`:
```ts
export class FakeBlueBubbles {
  constructor(opts?: { privateApi?: boolean; password?: string })   // defaults { privateApi: false, password: "pw" }
  start(): Promise<{ url: string; port: number }>; stop(): Promise<void>;
  readonly url: string;
  readonly sent: Array<{ chatGuid: string; message: string; method: string; selectedMessageGuid?: string }>;
  readonly typing: string[]; readonly read: string[]; readonly webhooks: Array<{ id: number; url: string; events: string[] }>;
  attachments: Map<string, { contentType: string; data: Buffer }>;
  deliver(event: BBWebhookEvent): Promise<number>;      // POSTs JSON (content-type: application/json) to every registered webhook URL; returns the last status, 0 when none registered
  waitForSent(count: number, timeoutMs: number): Promise<void>;   // rejects after timeoutMs
}
export function dmEvent(opts: { from: string; text: string; guid?: string; attachments?: BBAttachment[]; isFromMe?: boolean }): BBWebhookEvent;
export function groupEvent(opts: { from: string; text: string; chatGuid?: string; name?: string; guid?: string }): BBWebhookEvent;
export class EchoCompleter implements Completer { /* returns "echo: " + the last user text block, usage zeros, stopReason "end_turn" */ }
export async function runSimulation(opts: { config: Config; log: Logger; text: string; from: string; group: boolean; fakeClaude: boolean }): Promise<string[]>;
```
`FakeBlueBubbles` implements, with the real envelope: `GET /api/v1/ping`; `GET /api/v1/server/info` →
`data: { server_version: "fake", os_version: "fake", private_api: privateApi, helper_connected: privateApi }`; `POST /api/v1/message/text`
(records and returns `data: { guid: "sent-" + n }`); `POST /api/v1/chat/:guid/typing`; `POST /api/v1/chat/:guid/read`;
`GET /api/v1/attachment/:guid/download` (404 envelope when unknown); `GET /api/v1/webhook`; `POST /api/v1/webhook`;
`DELETE /api/v1/webhook/:id` (numeric id in the path; 404 envelope when unknown). Any request whose `password` query differs → 401 envelope.

`runSimulation`: `const fake = new FakeBlueBubbles({ privateApi: true, password: config.bluebubblesPassword }); await fake.start();`
start the bridge with `{ ...config, bluebubblesUrl: fake.url, bridgePort: 0, publicWebhookUrl: null, allowAllSenders: true, coalesceMs: 50, dataDir: tmp, logFile: path.join(tmp, "bridge.log") }`
and `completer: fakeClaude ? new EchoCompleter() : undefined`, `intervals: { pingMs: 50, webhookRetryMs: 50 }`; `await bridge.ready`;
deliver one event; `await fake.waitForSent(1, 60_000)`, then wait a further 2 s to collect extra bubbles; stop everything; return `fake.sent.map(s => s.message)`.

`test/e2e.test.ts` drives `FakeBlueBubbles` and `startBridge` directly (never the network):
`const bridge = await startBridge({ config: makeConfig({ bluebubblesUrl: fake.url, maxChunkChars: 120 }), log: silentLogger(), completer: new EchoCompleter(), intervals: { pingMs: 50, webhookRetryMs: 50 } }); await bridge.ready;`
- DM "hello" → one bubble `echo: hello`; exactly one webhook registered with `["new-message"]`; typing and read recorded when `privateApi: true`,
  not when false.
- Duplicate delivery of the same guid → still one bubble.
- `isFromMe: true` → no bubble.
- `/reset` → the reset reply; the completer was not called.
- Group without mention → nothing; with `@Claude ...` → reply whose first bubble has `selectedMessageGuid` (fake `privateApi: true`).
- User text of three paragraphs (`"a".repeat(100) + "\n\n" + "b".repeat(100) + "\n\n" + "c".repeat(100)`) → echo comes back as multiple bubbles, each ≤ 120 chars.
- A pre-registered stale webhook `${fake-side base}/webhook/deadbeef` is deleted on boot and ours registered (register it via `fake.webhooks.push` before starting the bridge).
- `/health` shows `bluebubbles.reachable: true` and `stats.replied: 1` after the first reply; the health JSON and the log file contain neither the token nor `password=`.
- Bridge started **before** the fake (`intervals: { pingMs: 50, webhookRetryMs: 50 }`): `health().bluebubbles.reachable === false`, then start the fake, `await bridge.ready`, deliver → reply.
- `runDoctor` against the fake reports ping ok and model ok with `anthropic` = `{ models: { retrieve: async () => ({}) } } as unknown as Anthropic`.
- Graceful stop: a completer that resolves after 300 ms, `deliver`, then `stop()` immediately → the bubble is still sent.

### Step 14 — CLI

File: `src/cli.ts` (first line `#!/usr/bin/env node`).

Commands (`node dist/cli.js <cmd>`; `npm run <script>` maps to these):
- `serve` — loadConfig → logger (file + stderr when `process.stderr.isTTY`) → `startBridge` → wait for signals; on `SIGINT`/`SIGTERM` call `stop()` then exit 0.
  Install `process.on("uncaughtException")` and `process.on("unhandledRejection")` handlers that log at `error` and keep running.
- `doctor` — loadConfig (on `ConfigError`, print it as the first failed check and still run the checks that do not need config) → `runDoctor` → print `formatChecks` → exit 1 if any `ok === false`.
- `install` / `uninstall` — call `installAgent` / `uninstallAgent`.
- `tail` — spawn `tail -n 200 -f <LOG_FILE>` with `stdio: "inherit"`.
- `simulate [--text "..."] [--from "+15550001111"] [--group] [--fake-claude]` — `runSimulation`; print each bubble prefixed with `→ `.
- `chat [--ephemeral]` — interactive REPL (`node:readline`) using the real completer and a `ConsoleTransport`. `ConsoleTransport` is a class inside
  `cli.ts` implementing `Transport`: `privateApi = false`; `sendText` prints `→ <text>` and returns `{ guid: null }`; `startTyping`/`markRead` resolve
  immediately; `downloadAttachment` returns `null`. Reuses `createHandler` with chatGuid `console;-;local`; `--ephemeral` uses a temp data dir. Exit with `/quit` or Ctrl-C.
- `register-webhook` — `registerWebhookOnce`; print the URL.
- `--help` / unknown → usage text, exit 2.
Parse args by hand (`process.argv.slice(2)`); no dependency.

Check: `npm run build && node dist/cli.js --help && BLUEBUBBLES_PASSWORD=x ANTHROPIC_API_KEY=x node dist/cli.js simulate --fake-claude --text "hi"` prints `→ echo: hi`. Commit.

### Step 15 — Hardening pass

Go through this checklist; add a test for anything not already covered.
- Loop safety: a webhook with `isFromMe: true` never reaches the completer, even if `handle.address` is allowlisted.
- Concurrency: two different chats are answered in parallel; the same chat never has two completions in flight.
- Idempotency: delivering the same `guid` twice, including across a restart (persisted dedupe snapshot), yields one reply.
- Memory: the rate-limit map, dedupe set, `recent`, and queue maps are all bounded (asserted by inspecting sizes after 3000 synthetic events).
- Oversized or malformed webhook bodies never crash the process.
- Secrets: the log file and `/health` never contain the password, API key, or token (grep in the e2e test).
- Permissions: `DATA_DIR` is `0o700`, `state.json` and log files `0o600` (skip the assertion on Windows).
- Graceful stop finishes an in-flight reply before exiting.

### Step 16 — README

Write `README.md` for the person setting this up (an experienced operator; no domain explanations). Sections:
1. What it does (3 sentences) and the dedicated-Apple-ID recommendation.
2. Requirements: a Mac that stays on, BlueBubbles Server installed and signed into iMessage, Private API enabled (optional, with link to the
   BlueBubbles Private API docs), Node 22.18+ (`brew install node`), an Anthropic API key.
3. Install: clone, `cd imessage-claude`, `npm install`, `npm run build`, `cp .env.example .env && chmod 600 .env`, fill `BLUEBUBBLES_PASSWORD`,
   `ANTHROPIC_API_KEY`, `ALLOWED_SENDERS`; `npm run doctor`; `npm run install-agent`; text the Mac.
4. Day-to-day: `npm run tail`, `npm run doctor`, `/help` in iMessage, how to change the persona (`persona.md`), where data lives, how to uninstall.
5. Keeping the Mac awake: the `pmset` command and the System Settings toggle; the display can sleep but the Mac must not.
6. Configuration reference: the table from section 4.
7. Troubleshooting: "no reply" checklist (allowlist, webhook registered, Private API, BlueBubbles logs), 401 from BlueBubbles (password),
   AppleScript send failures when the Mac is at the login window (enable Private API or auto-login), duplicate replies (two bridges registered → `register-webhook`).
8. Development: `npm run dev`, `npm test`, `npm run simulate -- --fake-claude --text "hi"`, `node dist/cli.js chat`.

No changelog or process notes in the README.

---

## 8. Definition of done

- `npm run typecheck`, `npm test`, and `npm run build` are clean on Linux and macOS.
- `BLUEBUBBLES_PASSWORD=x ANTHROPIC_API_KEY=x node dist/cli.js simulate --fake-claude --text "hi"` prints `→ echo: hi`.
- With real credentials on a Mac: `npm run doctor` is all green except warnings you expect; `npm run install-agent` starts the agent;
  texting the Mac from an allowed number produces a reply with a typing indicator; `/reset` works; a photo gets described;
  `kill -9` of the process results in launchd restarting it within ~10 s (`npm run tail` shows the boot log again).
- The repository contains no secrets. `.env` is git-ignored.

---

## 9. Stretch (only after section 8 passes)

- Tapback acknowledgement: react `like` to the triggering message when a reply takes longer than 8 s (Private API).
- `updated-message` handling for edited messages.
- Daily token budget with a notice bubble when exceeded.
- Contact names via `POST /api/v1/contact/query` for nicer dynamic context in groups.
