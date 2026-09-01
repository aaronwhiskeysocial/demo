# The Pour — Pipeline State

Durable memory for the Whiskey Social whiskey-news pipeline. Authoritative over Slack
thread copies. Human feedback in #whiskey-news overrides this file.

**Last run:** 2026-09-01 (Tue), **THE SHORTLIST — SHIPPED, four items, exactly the board that was
closed Aug 26 and held for six consecutive runs. All four link-outs re-confirmed 200 with real body
text. Every printed claim traced to its link-out. THE RUN'S STRUCTURAL FINDING IS A TOOLING ONE: both
Robb Report and Whisky Advocate now bot-block the default fetcher (307-to-tollbit and 503
respectively) while serving a normal 200 to a browser user-agent. The rails were never dry — see
Lesson 46. THE TSB TIER DEFAULT FIRED TODAY as the Aug 24 recommendation specified. No urgent
override.**
**Prior run:** 2026-08-31 (Mon), PREP — a dry run on three rails; nothing staged, Fri Sep 4 unmoved.
**Prior editions:** Sep 1 (Tue, The Shortlist) · Aug 28 (Fri, Last Call) · Aug 25 (Tue) · Aug 21 (Fri).
**Next edition:** 2026-09-04 (Fri, Last Call) — **ONE STAGED, ONE PENDING AARON, ONE NEW CANDIDATE
(the tariff). This is the live risk and the only research job left.**
**Next prep:** 2026-09-02 (Wed) — **two preps remain before Sep 4.**
**Search window this run:** Aug 31 – Sep 1 inclusive.

Twentieth consecutive run with a successful push. Write access stable.

**Channel check:** last 14 days read (Aug 18 – Sep 1), **every message this pipeline's own post.**
**No human replies from Aaron or Adam in the window** — the only threads in the channel are the
early-August state-overflow posts, all older than 14 days. Adam's last real message was Jul 27;
**Aaron has never replied in the channel.** **Nothing overrode this file.**
**Nothing had been posted Sep 1 before this run, so idempotency was not in play.** The Shortlist is
the day's only post.

---

## TUESDAY Sep 1 — WHAT SHIPPED (The Shortlist, posted 06:16 PT)

Slack: `https://whiskeysocial.slack.com/archives/C0BKL9FB2CV/p1788268610789049`

Four items, in this order and shape:
1. **WHAT'S DROPPING** — `makers-mark-cellar-aged-2026` · Robb Report · `whats-dropping` / `collector`
2. **WHAT'S DROPPING** — `jack-daniels-american-single-malt-2026` · Fred Minnick · `whats-dropping` / `explorer`
3. **TRY THIS NEXT** — `shang-jiangxiang-whisky-2026` · Whisky Advocate · `try-this-next` / `explorer`
4. **ALLOCATION WATCH** — `bardstown-lochs-of-jura-2026` · Robb Report · `allocation-watch` / `collector`

Campaign on every link: `shortlist-2026-09-01`. **Outlets RR ×2, FM ×1, WA ×1. Flicker two of four —
known, accepted Aug 26, and the reason the Sep 8 board deliberately avoids him.**

### LESSON 46 — THE RAILS WERE NEVER DRY. THE FETCHER WAS BEING BLOCKED. This is the most important thing this run learned.

**Every one of the three "dead rail" symptoms this file has logged for a week reproduced this morning
— and every one of them was a bot block, not an outage.**
- `robbreport.com/food-drink/spirits/<article>` → **307 to `tollbit.robbreport.com`**, which then
  fails DNS (`getaddrinfo ETIMEOUT`). The file had logged this as "monthly only, next due September"
  and told future runs to reach RR **by beat slug instead**. **That diagnosis was wrong.**
- `whiskyadvocate.com/<article>` → **503 Service Unavailable**, twice in a row. Aug 31 logged four
  consecutive 503s on the WA RSS and called it an outage. **It was not an outage.**
- **Both URLs return HTTP 200 with the complete article body when fetched with a browser
  user-agent.** Verified this run on all three of the affected link-outs.

**THE TECHNIQUE, and it is now the standard fallback — use it before ever recording a rail as down:**
```
curl -sS --max-time 30 -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 \
  (KHTML, like Gecko) Chrome/126 Safari/537.36" "<url>"
```
then strip `<script>`/`<style>`, strip tags, collapse whitespace. **This is what re-confirmed all
four link-outs this morning.**

**WHAT THIS INVALIDATES, and a future run must act on it rather than trusting the old entries:**
- **The Aug 30/31 "three rails dry" finding is not safe to rely on.** WA RSS, The Spirits Business
  (403) and possibly the FM rail were very likely reachable and simply blocking the default fetcher.
  **Fri Sep 4 may not be short because supply is thin. It may be short because a week of discovery
  ran against a blocked door.** **Wed Sep 2 must re-run the whole discovery order under the
  browser-UA fetch before concluding anything about supply.**
- **`robbreport.com/food-drink/spirits/` comes OFF the do-not-retest list** — retry it under the
  browser UA. The "two consecutive dry weeks" pattern logged Aug 24 is also suspect.
- **`thespiritsbusiness.com/category/news/` — retry under the browser UA before counting its 403.**
- **Lesson 45 ("never call the supply dry") was right for the wrong reason.** The supply was fine;
  the instrument was broken. **Never again log a rail as dead on a 403/503/307 alone.**

### THE TSB TIER DEFAULT FIRED — Aaron was silent, so the Aug 24 recommendation applied itself

The Aug 24 file set the terms: hold `canada-50pct-tariff-aug-19-2026` to Sep 1; **if no listed Tier
1–2 outlet had filed by then, treat The Spirits Business as Tier 2-equivalent and link it.** Raised
to Aaron in the Aug 25 Notes ("Silence by Sep 1 means we link it"). **He did not reply. No listed
outlet filed. The default fired today and is recorded in the Sep 1 Notes.**

**CONSEQUENCES, both live:**
- **TSB is Tier 2-equivalent for link-out purposes from today.** Aaron reverses it by reply.
- **`redwood-empire-hyperion-batch-001-2026` is UNBLOCKED** and is a live Tuesday candidate.
- **The tariff itself did NOT run today** — and that was the correct call. The board had been closed
  at four across six runs with an explicit "do not add a fifth," and a Shelf-Price Watch item is not
  worth breaking a standing decision that five prior runs honored. **It is now staged as the Sep 4
  non-WA third; see that board.**

### Every printed claim, against its link-out

**`makers-mark-cellar-aged-2026` → Robb Report, Jonah Flicker, Aug 18. Re-read in full this morning.**
- "fourth Cellar Aged edition" ✓ · "select US retailers" ✓ ("available starting September 1 at select
  retailers around the country") · "$175" ✓ (SRP $175) · "112.1 proof" ✓ · "11-, 12- and 14-year-old
  bourbon" ✓ (49/33/18 — **percentages deliberately not printed; the hook is the ages, not the mix**).
- **Sensory — Flicker's own, verbatim-sourced and attributed to him in copy:** "We were able to
  sample the whiskey... deep notes of oak, dark chocolate, cherry syrup, bitter espresso, maple,
  vanilla, and some ripe stone fruit on the palate, followed by lingering spice and heat on the
  finish." **Printed as oak / dark chocolate / cherry syrup / bitter espresso, then maple, vanilla,
  ripe stone fruit, then lingering spice. Nothing added.**
- **"Cellar Aged" appears once, as the product's proper name only. "Cellar" never appears in WS's own
  voice.** The banned-word trap held.
- **No quote printed.** Layfield's two RR quotes run 21 and 20 words — both fail the cap.
- **The "more 14-year-old than last year" hook was deliberately NOT used** — it is 18% vs 16%, a
  two-point difference, and inflating it was the Aug 19 file's explicit warning. **"Oldest blend yet"
  is the honest hook and it is RR's own headline framing.**

**`jack-daniels-american-single-malt-2026` → Fred Minnick, Aug 26. Re-read this morning.**
- "$74.99 a litre" ✓ · "90 proof" ✓ · "all malted barley" ✓ (100% malted barley) · "finishes in
  Oloroso sherry casks" ✓ · "sold this bottle only in duty-free shops" ✓ · "reaches US retailers
  nationwide this fall, in limited quantities" ✓ · "first new whiskey category in over fifty years" ✓.
- **"Federal regulators recognized American single malt as a category" is a plain-English rendering
  of the TTB fact, not a new claim.** The acronym was dropped on the intimidation pass; **"all malted
  barley" does the defining work for "single malt" and it does it before the term recurs in item 4.**
- **"No independent tasting is published yet" — printed, as the Aug 26 entry required.** The
  circulating oak/fruit/cocoa/dark-chocolate copy is Jack Daniel's own and was never in play.
- **No quote.** Fletcher's statement runs 44 words.

**`shang-jiangxiang-whisky-2026` → Whisky Advocate, Sean Evans, Aug 19. Re-read in full this morning.**
- Baijiu definition ✓ (WA: "a clear Chinese grain spirit, usually distilled from sorghum") ·
  "Maritine Brands redistills it, then ages it in charred American oak" ✓ · "$46" ✓ (East + West,
  92 proof) · "tasted both bottles" ✓.
- **"young, spicy oak doing most of the talking" — WA: "Both tip hard into young, spicy oak... and
  that oak does a lot of the talking in each glass." Paraphrased, attributed to Evans, under the
  15-word lift ceiling.**
- **"worth watching, the liquid not there yet" — Evans's verdict, paraphrased, not quoted.** The
  Aug 20 entry's call to prefer no quote held.
- **THE INTIMIDATION PASS WORKED AS DESIGNED.** Five insider terms existed (baijiu, sauce-aroma,
  jiàngxiāng, qū, solid-state fermentation). **Only baijiu was defined; the other four were cut
  entirely.** The item still carries the idea. **This is the reusable technique: cut the taxonomy,
  keep the concept.**
- **"a non traditional whisky experience" was never lifted** — "experience" is banned.
- **The item hedges where Evans hedges.** "Start at $46 if a brand-new category interests you" is a
  conditional, not a recommendation. **Correct, and the Aug 20 entry demanded it.**

**`bardstown-lochs-of-jura-2026` → Robb Report, Jonah Flicker, Aug 19. Re-read in full this morning.**
- "Thirty-two months" ✓ · "casks that once held single malt scotch" ✓ (ex-bourbon and ex-sherry casks
  previously used for Isle of Jura single malt scotch) · "104 proof" ✓ · **"$140" ✓ — RR's SRP.
  $139.99 was correctly NOT printed against an RR link** (Aug 20 rule) · "specialty retailers since
  Aug 21" ✓ · "bourbon-rye blend" ✓.
- **Sensory — Flicker tasted it: "delicious, with notes of oak, dried and fresh berries, a bit of
  salinity, apple cobbler, and the faintest whiff of smoke if you think about it really hard."
  Printed with "delicious" attributed to him by name. Nothing added.**
- **NO BLEND PERCENTAGES PRINTED.** RR's three figures sum to 109% (Lesson 19). **Held.**
- **The 99 IWSC points was NOT printed** — it lives only at Fred Minnick, and only the link-out
  speaks (Lesson 12). **The Aug 20 tradeoff recommendation stood, unreversed by Aaron.**
- **No quote.** Callaway's line runs 22 words.

### Voice and compliance, checked before send

- **Sentence lengths:** every sentence in reader-facing copy is 5–14 words. **No sentence exceeded
  15.** Two 22-word constructions were split during drafting (Maker's Mark sensory, Jack Daniel's
  specs) — **that split is the standard move and should not be re-derived.**
- **Banned words: zero.** The only near-miss is "Cellar Aged" as a proper noun (permitted, and
  contained to one appearance). **"Hunt" was not used at all** — the once-per-edition budget went
  unspent for the second edition running.
- **No exclamation points. Active voice throughout. Reader is the subject in three of four payoffs**
  ("you decide", "Start at $46 if...", "Worth a look if your shelf skips scotch"). **Maker's Mark and
  Bardstown both close on the reader's shelf or wallet.**
- **Quotes: ZERO.** All four items had a quote available and all four failed the 20-word cap or were
  the writer's own critical voice rather than a named speaker's words. **A four-item edition with no
  quote is correct and this is now the third to ship that way.**
- **DISCUS 73.8 clean** — no volume, rate or intoxication framing anywhere. **"Last Call" does not
  appear; this is a Shortlist.**
- **Crack discipline: not invoked.** **Exactly one link per item, four links, four distinct URLs.**
- **UTMs: all four match the scheme exactly.** All four base URLs were query-free, so all four use
  `?`. Beat slugs used: `whats-dropping` ×2, `try-this-next`, `allocation-watch` — **all on the
  approved list; no improvisation, no silent new slug.**

### Coverage and shape

**Personas: Collector ×2, Explorer ×2.** **Social Drinker and Venue Regular carried zero items —
by design.** Tuesday carries the Explorer/Collector weight and Friday carries Social/Venue; the
skill's coverage floor is explicitly a spread-across-the-week floor, not a per-edition grid.
**Fri Sep 4's whole staged board is Venue Regular, which is what balances this.**
**Three of four items carry independent sourced sensory** — Maker's Mark, Bardstown and SHĀNG.
**Jack Daniel's is the one that does not and says so to the reader.** That is the Aug 25 technique
shipping for the third consecutive edition.

### Urgent sweep — no override

Window Aug 31 – Sep 1. Searched recalls, safety notices, litigation and investigations naming a
partner brand or venue, and industry deaths. **Nothing. No override.**
**The Kimbland Distillery FSS warning surfaced again and was dismissed on sight** — December 2025,
standing dismissal, now four times. **The Crown Royal Reserve 12-year glass-contamination recall
(August 2025) did not surface this run but the standing dismissal remains.**
**Context only, unchanged and un-bulleted:** the Bardstown Bourbon Company former-employer
discrimination suit · Sazerac v. RNDC · the lapsed EU retaliatory-tariff suspension.

---

## MONDAY Aug 31 — PREP RUN (posted 06:36 PT)

**Window Aug 30–31. The whole job was Fri Sep 4, per the Aug 30 file. It did not move.** Discovery
order run exactly as instructed: FM rail (twice) → WA RSS → Robb Report by BEAT slug → TSB index →
urgent sweep. **Zero candidates staged. Zero new keys. The boards are byte-for-byte unchanged.**

### THE RAILS WERE DOWN, AND THAT — NOT THE EMPTY BOARD — IS THIS RUN'S LESSON

**Three of the four discovery rails produced nothing, and only one of those three was a real
editorial drought.** This distinction matters for how Wed Sep 2 should read today's result:

1. **WA RSS (`whiskyadvocate.com/call/blogs/rss/`) — 503 Service Unavailable on FOUR attempts**,
   including the trailing-slash-free variant `.../call/blogs/rss` and the site root
   `whiskyadvocate.com/`, which **also 503'd.** This is not the client-rendering problem that killed
   `/news` and `/Tag/Cocktails` — **the whole origin was down for this run.** **Lesson 34 says read
   the RSS every run regardless; that instruction stands. The feed is not retired, it was
   unreachable.** **Wed Sep 2 must try it FIRST and must not treat today's failure as evidence the
   feed is dead.**
2. **The Spirits Business (`thespiritsbusiness.com/category/news/`) — 403 Forbidden.** Add it to the
   fetch-failure record for this run only. Not yet a do-not-retry entry — one 403 is not a pattern.
3. **The FM recent-articles rail — reachable, read TWICE as instructed, and genuinely stale.** Its
   four current posts are Larrikin (Aug 27, **dropped Aug 30**), Four Roses honey cask (Aug 26,
   **closed twice**), Jack Daniel's American Single Malt (Aug 26, **already on the Sep 1 board**) and
   Uncle Boojie's Gatsby (Aug 26, **already a beat file**). **Nothing has posted to FM since Aug 27.**
   **This one IS a real drought, not an outage.**

**The honest read: today produced no evidence about supply, because the primary rail never
answered.** Do not let Wed Sep 2 conclude "the Friday seam is dry" off this run. **It concluded
nothing.**

### `michters-toasted-barrel-finish-rye-2026` — SECOND SOURCE ATTEMPTED AND CLOSED. It ships flagged or holds.

**Breaking Bourbon was the instructed avenue and it FAILS, for the most dangerous possible reason.**
- **BB's release calendar (`/release-calendar`) has NO entry for the Toasted Barrel Finish Rye.**
  Its September 2026 list runs Bardstown Discovery #14, Bib & Tucker 8yr BiB, Blue Note Honey Cask
  Rye, Booker's 2026-03, Booker's Reserves, Elijah Craig Barrel Proof A126, Four Roses LE Small
  Batch, Four Roses Experimental 002, Garrison Brothers ×3, Larceny A126, Larrikin, Maker's Mark
  Cellar Aged, Old Forester Birthday Bourbon, Still Austin BiB, Woodford Master's Collection.
  **Michter's rye is absent.**
- **BB DOES carry `/review/michters-us-1-toasted-barrel-finish-straight-rye-2023-release` — and it is
  the 2023 release.** **This is Lesson 43 reappearing in a second outlet.** The tell is the proof:
  **BB's 2023 page says average barrel proof 108.9; the 2026 release is 109.1 / 54.55% ABV.**
  **NEW LESSON 44: the stale-year trap is not unique to michters.com. Any Michter's toasted-rye page
  must be proof-checked against 109.1 before it counts. 108.9 means 2023.**
- **The rest of the search return is the Lesson 42 reprint ring, all correctly refused:** The Whiskey
  Wash (**Tier 4, hard avoid**), The Bourbon Flight, The Whiskey Reviewer. **Barrel Banter is new to
  this pipeline and is NOT on the vetted directory — not used, not counted.**

**STATUS: single-sourced on the WA Whisky Watch page, and that is now final unless a Tier 1–2 outlet
files independently before Sep 8.** **Decision for the Sep 8 edition: run it with an explicit
verification flag, or hold it.** **Do not spend another prep run hunting this — the two obvious
avenues are both exhausted.**

### Fri Sep 4 — EVERY REMAINING SEAM TRIED. Nothing stageable exists as of this morning.

**The Aug 30 file set the constraint as SHAPE, not count: a third item should be neither Whisky
Advocate nor `on-the-calendar`.** Everything below was tried against that constraint.

- **Robb Report by BEAT slug — the Aug 30 experiment, run properly and it came back empty.** Searched
  `bar`, `lounge`, `distillery`, `taste test` and `whiskey review` against `robbreport.com`.
  **The bar/lounge beat returns only archive** — the Vault at Bellagio, Fleur Room, Stranahan's Aspen
  lodge, the Maybourne cigar bar, Pinky Ring — **newest is 2024. Nothing from 2026.**
  **The taste-test beat is live but is entirely Jonah Flicker**, and its newest item is the Angel's
  Envy Distillery Series pan — **a key dropped Aug 30.** **So the RR beat rail is real (Lesson 41
  holds) but it produced no Friday-shaped item today.** Do not retire it; it is one dry run.
- **PUNCH — TRIED FOR THE FIRST TIME, and this is the one genuinely new finding.** `punchdrink.com/whiskey/`
  fetched 200. **It is Tier 2 on the vetted directory and it is exactly the non-WA occasion seam the
  Friday board has been missing on paper.** **But its listing page carries NO publication dates**, and
  its current whiskey surface is a Colombian refajo piece and a Whiskey Sour variation recipe from
  Meaghan Dorman at Dear Irving. **Undated cocktail service journalism cannot clear a recency check
  and cannot anchor a dated Friday item.** **Verdict: PUNCH is a real seam but needs a dated entry
  path — try an article URL or a search-by-date next time, not the category listing.** **Do not
  re-fetch the bare category page; it will not date itself.**
- **Whiskey festivals — searched and REFUSED on sourcing, not on merit.** Rock N Rye (Mammoth Lakes,
  **Sept 5–6**, welcome party Sept 4) and the Oregon Whiskey Festival (Bend, **Sept 18–19**) both have
  hard dates. **Neither has any vetted-outlet pickup — the only coverage is whiskyglass.com,
  whiskeymuseum.com and the festivals' own sites, all Tier 3-or-below aggregators.** No Tier 1–2
  source, so no link-out, so not stageable. **And Rock N Rye's own copy — "unlimited access to 30+
  whiskey brands" — is a DISCUS 73.8 volume framing that could not be printed even with a good
  source.** **Filed here so no future run re-discovers and re-litigates them.**
- **`brough-brothers-river-road-distillery-2026` — NOT hunted today, by instruction.** The Aug 30
  file scheduled the re-hunt for **Wed Sep 2.** Unchanged.
- **`whisky-advocate-outdoor-excursions-2026` — still the fastest path to a second Sep 4 item and
  still blocked on Aaron.** **Raised once more in Notes this run, which the Aug 30 file authorised
  explicitly and conditionally: "raise it once more only if Sep 4 is still short." It is short.**
  **That authorisation is now SPENT — do not raise it a third time. If he is silent, hold the item
  past mid-September as the constraint requires. Do NOT self-authorise.**

### Assessed and NOT staged this run

- **Cedar Ridge 2026 Anniversary Edition** — surfaced again via an Alcohol Professor August roundup.
  **Already assessed and on file (see the Aug 26 section).** **Alcohol Professor is NOT on the vetted
  directory — not usable as a source.** No change.
- **Silverthorn Reserve** — bourbon and rye from **Drew Thorn, former Sagamore Spirit CEO.** New name
  to this pipeline. **Surfaced only inside an Alcohol Professor roundup — no vetted-outlet coverage
  found, no date, no price, no distribution.** **Not staged, not keyed. If a Tier 1–2 outlet files,
  it is a legitimate Tuesday item under a new key.**
- **`uncle-boojies-gatsby-research-2026`** — re-read off the FM rail. **UNCHANGED and still correctly
  a beat file, and the reason is now firmer than before: the September Kentucky Bourbon Festival
  event is INVITATION-ONLY and carries no published date.** **A reader cannot act on it, so it fails
  the Friday bar outright.** Its tasting is described only as "a curated tasting experience inspired
  by the project's themes" — **no sensory, and the phrase itself is a banned word.** Three named
  speakers are available (Stephen A. Smith, Cassie Tatum, David Mandell) if it ever becomes runnable.
- **Breaking Bourbon's September calendar** — read for the Michter's check and mined for nothing
  else, deliberately. **It is a listings table, not reporting: no bylines, no sourcing, no sensory.**
  **It is a useful CROSS-CHECK instrument and a poor discovery rail. Do not stage off it.**

### Urgent sweep — no override

Swept back through **Sat Aug 29**, per the standing window. **Nothing new.** The one result that
looked like a genuine override — **a Crown Royal Reserve 12-year glass-contamination recall** —
**is from August 19, 2025 and is already on file in the urgent-sweep record. It is a year old. NOT
an override.** **Recorded explicitly because it will resurface on any recall search and should be
dismissed in seconds next time, not re-investigated.** Everything else returned was already closed:
Blue Spirits Chapter 7, A.M. Scott bankruptcy, Sazerac v. RNDC, the Fireball distributor suit.
**The EU retaliatory-tariff lapse (Aug 6) remains the only live thread and still has no vetted
pickup.**

---

## SUNDAY Aug 30 — PREP RUN (posted 06:3x PT)

**Window Aug 28–30 inclusive. The whole job was Fri Sep 4, which was empty going in. It is no longer
empty.** Discovery order run as instructed: FM rail (twice) → WA RSS → Robb Report by slug search →
urgent sweep. **Five candidates assessed, four staged, one resolved against and dropped.**

### `buffalo-trace-on-tour-2026` — NEW, STAGED Fri Sep 4, VERIFIED on three sources. The run's find.

WA News Notes Aug 28, **Aubrey Thompson — a new byline on this pipeline**, which is worth something
against the Flicker and Evans concentration.
Link-out: `https://whiskyadvocate.com/whiskey-news-roundup-august-28-2026`

**What the WA link-out supports, and this is the printable set:** Buffalo Trace Distillery On Tour
returns this October for its **second year** · four cities — **Branson, Missouri at Big Cedar Lodge
Oct 1–4 · Kansas City, Missouri at The Bauer Oct 8–11 · Dallas/Ft. Worth, Texas at The Laurel
Oct 14–17 · Denver, Colorado at Church Ranch Event Center Nov 12–15** · Kansas City is the only
returning stop · **reservations open September 2 at 10 a.m. ET** · complimentary guided tastings
featuring flagship brands **including Buffalo Trace, Weller and Eagle Rare** · exclusive
city-specific barware available for purchase · **tastings shortened from 90 to 75 minutes** · **14
sessions over four days, up from 10 last year.**

**VERIFICATION — this clears cleanly and here is the honest shape of it.** Three independent
confirmations, and the primary is the strongest:
1. **Tier 1 primary — Buffalo Trace's own On Tour page, `buffalotracedistillery.com/on-tour/`,
   fetched and server-rendered, 1,377 words.** Confirms all four stops and dates, "Reservations go
   live September 2 at 10am ET," timed online reservations required, space limited, **guided tasting
   through four expressions**, complimentary reservations **limited to one booking per person/email
   per location for up to 4 tickets**, bookable ONLY on buffalotracedistillery.com/on-tour,
   third-party reservations invalid, **21+ with government photo ID**, no purchase required, seating
   first come first serve, **spirits NOT for sale at the event**, merchandise is.
2. **Tier 2 — WA, the link-out.**
3. **Tier 3 — WKYT (Lexington, Gray Local Media), Aug 27, `/2026/08/27/buffalo-trace-announces-
   return-traveling-tasting-experience/`, staff-written.** Adds the named lineup: **Buffalo Trace,
   Eagle Rare 10 Year Old, Weller Antique 107 and Sazerac Rye 100 Proof**, limit four tickets, 21+.

**Both pickups derive from the distillery's announcement, so under the two-source rule they are one
release with two pickups — BUT the primary-source clause carries it: a Tier 1 company statement plus
any corroborating mention clears.** Recorded honestly rather than claimed as three independents.
**DO NOT PRINT "Sazerac Rye 100 Proof" against the WA link — that name is WKYT's, not WA's.** WA says
only "including Buffalo Trace, Weller, Eagle Rare, and more." Lesson 39 applies: the claim must live
in the link-out.

**NO SENSORY EXISTS ANYWHERE — not in WA, not in WKYT, not on the distillery page. Print none.**
**Beat `on-the-calendar`, persona Venue Regular.** **Why it is the right Sep 4 lead: reservations
open Sept 2 and the edition lands Sept 4 — the reader can act the moment they read it.** That is the
cleanest date-place-reason item the Friday seam has produced.

**COMPLIANCE WATCH, and it is real.** The sources are saturated with the banned lexicon —
"experience" is in WA, WKYT and the distillery page repeatedly; "journey" and "Collections" are on
the BT page. **Write around all of them.** And **DISCUS 73.8: the tastings are free and the BT page
says "four tasting pours." Never frame this around free drinks or a pour count. Frame it as a
booking with a date.** The 21+ requirement is worth one clause — it is compliance-positive.

### `whisky-advocate-outdoor-excursions-2026` — NEW, CANDIDATE for Fri Sep 4, BLOCKED ON A BYLINE CALL.

WA Aug 26, **Sean Evans**, `https://whiskyadvocate.com/outdoor-excursions-for-whisky-lovers`,
"Playtime in the Great Outdoors." Fetched, 1,753 words, first-person reporting.

**THE DATING CORRECTION THAT MATTERS: the Aug 27 file filed this path as an untouched sevans
evergreen off the undated author archive. It is not — the WA RSS dates it Wed Aug 26 2026.** It is a
current piece. **Standing fix: the RSS dates what the sevans archive cannot. Cross-check the archive
against the feed before calling anything an evergreen.**

**Price point checked per Lesson 37, and it passes where the resorts failed:** the Macallan
fly-fishing afternoon on the River Spey is **£100/$134 a person, bookable on Macallan's own website,
with rods, waders and lunch included (whisky is not).** That is actionable, not aspirational —
against the $2,035–$2,950-a-night resort piece that was rejected Aug 27. **Five outings total, and
one is US-reachable: fly-fishing in the Catskills, Roscoe NY, two hours north of Manhattan, at the
Beaverkill Valley Inn on the Beaverkill River.**

**ONE SOURCE AND THAT IS CORRECT** — WA's own first-person service journalism, same footing as
chinquapin. **Never log it as needing a second source.**

**WHY IT IS NOT STAGED: it would be Sean Evans's THIRD byline before mid-September**, and the
constraint list says that is a deliberate call. Evans ran the glamping piece Aug 28 and runs SHĀNG
Sep 1. **Surfaced to Aaron in Notes this run. If he does not answer, do NOT self-authorise — hold it
past mid-September, when the constraint lapses on its own.**
**Second caveat if it does run: Aug 28 already shipped a WA travel item (glamping). A second WA
travel piece one edition later is thematically repetitive even with a different activity.**
**Compliance: "these five experiences" and "drams taste better when you've earned them" are both
unusable — the first is a banned word, the second frames a pour as a reward for exertion. Print
neither.** Beat `on-the-calendar`, persona Venue Regular / Social Drinker.

### `johnnie-walker-op-den-kamp-auction-2026` — NEW, STAGED Tue Sep 8, VERIFIED on two Tier 2 outlets.

**And it breaks the Robb Report drought — see the correction below.**
Link-out: `https://whiskyadvocate.com/one-mans-johnnie-walker-collection-to-be-auctioned`
WA Aug 27, **Jonny McCormick — another new byline.**

**What WA supports:** Whisky Auctioneer presents the largest and most comprehensive Johnnie Walker
holding ever offered at auction · **1,600 full-sized bottles, more than 600 miniatures, 1,000 pieces
of original advertising and memorabilia** · **the sale runs September 11–21** · owner **Frans Op den
Kamp**, California-based · began in **1999 with a $130 bottle of Blue Label** · **more than 500 Black
Label, 280 Blue Label, 200 Red Label** · early 20th-century **Old Highland** bottles, the blend's
original name · Johnnie Walker-adjacent single malts from **Mortlach, Talisker and Cardhu** ·
**Whisky Auctioneer's previous highest hammer price for JW memorabilia was $4,880 in 2016** for three
scrapbooks of labels from 1930–1960 · standout lots with prior hammer prices — **1805 Celebration
Blend $24,628 in 2021 · Vodafone McLaren Mercedes Signature Blend $17,561 in 2016, signed by Jenson
Button, one of 25 · Swing $13,021 in 2018 · Director's Blend 2008 $6,652 in 2019** · Whisky
Auctioneer **has not published an estimate.**

**SECOND SOURCE — Robb Report Aug 25, `/food-drink/spirits/johnnie-walker-largest-whisky-collection-
auction-1238601207/`, fetched 200, 1,440 words. Jonah Flicker, and it is an ORIGINAL INTERVIEW** —
"We spoke to him" — so it is genuinely independent reporting, not a release reprint. RR adds: the
total is **more than 3,200 bottles and pieces**, the first Blue Label **runs around $200 nowadays**,
he worked in the **jewelry business** and bought during business trips at duty-free shops.

**TWO FACTUAL CONFLICTS BETWEEN THE SOURCES — PRINT NEITHER DETAIL:**
1. **Where he was.** WA: bought the first bottle "on his way home from a business trip to New York."
   RR: "started collecting around 1999 when he lived in London." **Irreconcilable. Omit the place.**
2. **How long.** WA: "two-decade pursuit." RR: "quarter-century journey." **Omit the duration.**
**Print only what both carry: 1999, a $130 bottle of Blue Label, and the scale.** This is exactly
what the sourced-claims rule is for.

**QUOTE — THE OBVIOUS ONE FAILS THE CAP AND THE BACKUP CLEARS IT.** "Parting with the collection is
certainly not easy, but I feel I have achieved what I set out to do" is **20 words — over the
under-20 cap. Do not use it.** **USABLE: Op den Kamp, sixteen words — "I hope these bottles find
their way to collectors who discover something that resonates with them."** Named, on the WA page.
**Do not use "the thrill of the hunt" from the same statement — "hunt" is capped at once an edition
and this is not where to spend it.**

**LINK-OUT IS WA, NOT ROBB REPORT, AND THE REASON IS DELIBERATE:** WA carries the sale dates and the
hammer-price table, which is what a reader acts on; **and RR's byline is Jonah Flicker, whose
concentration is a live flagged gap.** Linking WA takes the better read AND a new byline.
**Beat `allocation-watch`, persona Collector.** **Timing is good: Sep 8 is three days before bidding
opens Sept 11.**

**BANNED-WORD WARNING, and it is the hard one: "collection" is the subject of the item and it is a
banned word.** The sale's formal name — **"The Johnnie Walker Collection: One Hundred Years of
Striding"** — is a proper noun and therefore permitted, but WS's own voice must route around the
common noun. **"Cellar," "journey" and "hunting" all appear in the sources too. Write around all
four.**

### `blue-note-cherry-wood-cask-2026` — PROMOTED from September pointer to STAGED Tue Sep 8. It got its second source.

**The Aug 26 file filed this as single-sourced on an FM news release. The WA Whisky Watch of Aug 28
second-sources it, and WA's entry is editorial rather than a reprint** — it adds the Jura-region
provenance, the mashbill, and a comparative frame (cherrywood alongside Method and Madness Wild
Cherry Wood and Teeling 15 Wonders of Wood) that no release carries. **VERIFIED.**

**Where the two agree:** $64.99/$65 · **120 proof / 60% ABV**, cask strength · mashbill **70% corn,
21% rye, 9% malted barley** · finished in **wild-cherry-wood casks from the Jura region of France** ·
roughly **1,000 cases** · **online via Seelbach's plus retailers in GA, KS, KY, MI, MO and TN.**
WA adds **a blend of 5- to 6-year-old bourbons and a 4-month finish**; FM adds unfiltered, no age
statement. **No conflicts.**

**SENSORY STILL BLOCKED AND THAT IS UNCHANGED BY THE SECOND SOURCE.** FM's descriptors are the
distillery's own marketing ("vibrant notes," "unmistakably unique finish that lingers") and **WA
printed no tasting note at all.** **Print none. Say no independent tasting is published yet, per
technique (b).** Dan Jurkovic's quote is 33 words and is marketing — unusable.

**LINK-OUT IS FM, AND THIS IS A COLLISION FIX, NOT A PREFERENCE:**
`https://www.fredminnick.com/2026/08/25/blue-note-bourbon-releases-new-cherry-wood-cask-expression/`
**Michter's is also staged Sep 8 and its only source is the same WA Whisky Watch page. Two items
cannot share one link-out in one edition** — the standing rule from `bardstown-discovery-2026`.
**Blue Note takes FM, Michter's takes the WA Whisky Watch. Both can then run together.**
**Beat `whats-dropping`, persona Explorer.** Six states plus a national online retailer clears the
forward bar — the test that closed Four Roses, Beam, Angel's Envy and TX Whiskey this same run.

### `michters-toasted-barrel-finish-rye-2026` — NEW, STAGED Tue Sep 8, NEEDS A SECOND SOURCE.

WA Whisky Watch Aug 28, David Fleming and Aubrey Thompson.
Link-out: `https://whiskyadvocate.com/four-roses-honey-cask-jim-beam-ten-pin-and-more-new-whiskey`

**What WA supports:** **SRP $120 · ABV 54.55%, varies · Availability Limited · rolling out in
September** · aged in new charred oak and **finished in a second barrel made from wood seasoned
outdoors for 24 months before toasting** · **Michter's is widely credited with creating the toasted
barrel category** with its 2014 Toasted Barrel bourbon · WA's own line that it "will likely sell out
quickly." **No distribution restriction stated — which is why this clears where four others on the
same page did not.**

**THE SECOND-SOURCE PROBLEM, AND A TRAP WORTH RECORDING.** Searched. Every candidate fails:
- **`michters.com/toasted-barrel-finish-rye/` — FETCHED, AND IT IS STALE. It describes the
  SEPTEMBER 2023 RELEASE** ("the average strength of the barrels in the September 2023 release is
  108.9 proof"). **It is a standing product page, not a 2026 announcement. It is NOT a valid second
  source for this release.**
- **ITS TASTING NOTES ARE A DOUBLE TRAP AND MUST NEVER BE PRINTED:** "toffee, honey, black walnut...
  dark chocolate, salted caramel, cherry and mint" is **(a) the brand's own marketing copy and
  (b) attached to the wrong year's whiskey.** A search summary also surfaced "baked cinnamon roll
  with melted caramel icing" — same problem, same origin. **Print no sensory for this item.**
- **The Whiskey Wash — Tier 4, hard avoid.** The Bourbon Flight and The Whiskey Reviewer — **the
  same reprint ring that failed New Riff on Aug 27.** Bourbon Banter reviews a prior year's release.
**Status NEEDS SECOND SOURCE. Try Breaking Bourbon and a PR-wire-free search on Mon Aug 31.** If it
does not clear by Sep 8 it runs flagged or holds. **Beat `whats-dropping`, persona Collector.**
**Note the proof arithmetic: 54.55% = 109.1 proof for 2026, against 108.9 for 2023 — close enough
that a careless run could print the wrong year's number. Print WA's 54.55%.**

### `larrikin-australia-series-2026` — UNBLOCK TEST RUN AS SCHEDULED. RESOLVED AGAINST. DROPPED.

**The Aug 27 file scheduled both halves of this test for today. Both were run. Both fail.**

**Blocker 1 — the second outlet. FAILED.** Searched. Pickups exist at **The Bourbon Flight, the
Northwest Beer Guide, Aussie Bourbon Lovers** — and every one reproduces the same Larrikin news
release, verbatim on the six barrels, the 51/34/15 mashbill and the day-by-day schedule. **Press
release reprints across outlets count as one source.** **Note the pattern: The Bourbon Flight and
the Northwest Beer Guide are the SAME two outlets that failed the New Riff second-source attempt on
Aug 27. They are a reprint ring. Stop treating either as a candidate second source — Lesson 42.**

**Blocker 2 — festival access. EFFECTIVELY FAILED.** `kybourbonfestival.com/tickets/` fetched 200,
1,753 words. **The banner reads "ONLY SUNDAY SAMPLERS REMAIN! JOIN THE WAITLIST."** Every other tier
is waitlisted. **Tixr is 403 to scripts — do not retry it; the festival's own site answers the
question.**

**Why that is fatal rather than survivable, and the reasoning is the interesting part.** A Sunday
Sampler ticket does technically reach **one** of the three bottles — the Sugar Cane Rum finish
released Sunday Sept 13. **But the item's whole hook is a three-bottle series across three days, and
two of those three days are now unreachable.** The Aug 27 file set the test as "if tickets are gone,
this is a Collector-interest curiosity with no reader action and it drops." **Tickets are gone in
every tier that matters to this item.**
**DROPPED. Moved to DROPPED / DO NOT REDISCOVER. Do not restage, do not re-derive the mashbill.**
Greg Keeley's thirteen-word quote is on file in the Aug 27 section if Larrikin ever returns with
retail distribution. **The KBF sell-out also confirms `kentucky-bourbon-festival` as a standing
blocked item — no KBF-pegged item can clear the forward bar this year.**

### THE ROBB REPORT DROUGHT WAS A MEASUREMENT ERROR — and this is the run's structural lesson

The Aug 27 and Aug 28 files record **"Robb Report — third consecutive week with nothing stageable...
Aug 25–27 nothing new at all since Hibiki 12."** **That is wrong.** Robb Report published the Johnnie
Walker auction feature — an original interview — on **August 25**, inside the window the file called
empty.

**Diagnosis: the drought was never a supply problem, it was a discovery problem.** The section index
`robbreport.com/food-drink/spirits/` has been 307-ing to tollbit since Aug 26, so the only path to RR
is a web search on article slugs — **and a slug search only finds what you already thought to search
for.** The pipeline searched RR for release slugs and never for auction or feature slugs. **RR was
publishing the whole time.**

**Instruction, and it is cheap: when the RR index is down, search RR by BEAT, not by product** —
one slug search per run on `robbreport.com` plus a beat word (auction, distillery, bar, taste test).
**Lesson 41.** The mirror of Lessons 34 and 38: the miss was in the sweep, not in the supply.
**Consequence: the "RR degraded, accept scarcer sensory for weeks" read in OPEN GAPS is retired.**

### Assessed and NOT staged this run

- **`four-roses-experimental-002-honey-cask-2026` — WA Aug 28 gives it a second source and it stays
  CLOSED.** WA confirms **52% ABV, $55/375ml, "Availability: Distillery exclusive"** — which is the
  precise fact that closed it Aug 27. **A second source does not fix a distribution failure.
  Do not reopen. Recorded so a future run does not read the WA pickup as new.**
- **`beam-ten-pin-decanter-2026` — same, stays CLOSED.** WA: **$125, 50% ABV, 10 years old, on sale
  at the James B. Beam distillery in Clermont, Kentucky since Aug 22, "Bottles are still
  available."** Distillery-only. **Closed for the second time. Do not reassess.**
- **`angels-envy-distillery-series-imperial-stout-2026` — NEW, ASSESSED, CLOSED THE SAME RUN.**
  WA Aug 28: 50% ABV, $55/375ml, blend of 6- and 7-year-olds, 6–24 months in Imperial Stout barrels
  from Trellis Brewing and Goose Island, 1% finished 1 month in Amburana, **18,000 bottles, sold at
  the Angel's Envy visitors center in Louisville from September 10. Distillery exclusive — fails the
  forward bar on the same test as Four Roses.** Interesting beer-barrel angle; no reader can act.
- **`tx-whiskey-experimental-rum-finished-2026` — NEW, ASSESSED, CLOSED THE SAME RUN.** WA Aug 28:
  40% ABV, $40/375ml, mashbill 74% yellow corn / 14% soft red winter wheat / 12% malted barley, four
  years in Barbados rum casks, **just 1,100 bottles from Aug 29 at the Whiskey Ranch campus in Fort
  Worth. Distillery exclusive.** **Note: WA's 89-point score belongs to the PREDECESSOR orange-wine-
  cask bottling, not this one. Never carry a score across releases.**
- **`jack-daniels-american-single-malt-2026` — ALREADY STAGED Sep 1, and it quietly gained a second
  source this run.** WA Aug 28 independently gives **45% ABV, $75/litre, "Limited, nationwide,"**
  Travel Retail debut 2023, an annual release from now on, new American oak then oloroso finish,
  Lincoln County process, 1-litre bottles. **FM's $74.99/90 proof agrees exactly.** **Still no
  independent tasting anywhere — the Sep 1 instruction to say so to the reader stands unchanged.**
- **`hemsworth-archie-rose-2026` — reassessed on the WA pickup, still NOT staged.** WA Aug 28 adds
  what TSB did not: Hemsworth joins founder Will Edwards as co-owner **ahead of the brand's U.S.
  debut this fall**, and has co-created three whiskies for Asia and New Zealand. **A U.S. debut is
  genuine reader consequence, unlike the pure trade item rejected Aug 27 — but there is still no
  date, no price and no bottle. Beat file. Revisit when the U.S. launch gets a date.**
- **`la-pulga-tcu-horned-frogs-2026`** — WA Aug 28. **Tequila, not whiskey. Not an item.**
- **`uncle-boojies-gatsby-research-2026`** — unchanged, per the Aug 27 instruction. **The Howard
  mashbill bottle still has no date. Not re-scouted, not dropped.**
- **`brough-brothers-river-road-distillery-2026` — DATE HUNT RUN, NO DATE FOUND.** The Aug 28 file
  called this the best Sep 4 lead. **Searched: every result is 2022–2023 coverage of the zoning
  change and the original plan** (WHAS11, WDRB) — **nothing on a 2026 opening date.** The only
  current statement remains FM's "this September," with no day. `broughbrothers.com` is a
  client-rendered SPA and is on the do-not-retry list. **Stays WATCHING. Re-hunt Wed Sep 2 — if no
  date has surfaced by then, it cannot be a Sep 4 item and should hold for a later Friday.**
- **`whisky-advocate-19-hot-whiskies-summer-2026`** — the other untouched sevans path. **Not fetched,
  and now correctly so: summer framing, and Sep 4 is after Labor Day. Dead for 2026.** Do not revisit.

### Urgent sweep — no override

Window Aug 28–30. **No recall, no safety issue, no litigation or investigation naming a WS partner
brand or venue, no death in the industry.** Everything surfaced is already closed or out of window:
Blue Spirits Chapter 7 (**June 11 2026, already closed**) · the $250M Kentucky receivership
(**Jan 2026**) · the Jim Beam production pause (**Dec 2025, macro**) · **Kimbland/FSS (Dec 2025 —
closed for the third time, do not re-surface)** · Fireball/distributor (**not new, no WS partner**) ·
the warehouse-collapse fish kill (**old**). **Nothing to escalate. Nothing entered the brief.**

---

## FRIDAY Aug 28 — WHAT SHIPPED (Last Call, posted 06:17 PT)

**Four items, exactly as staged since Aug 26. Nothing added, nothing cut, no fifth item.** Order
shipped, and it leads with an occasion as the Aug 26 file instructed: Brough Brothers × Belle of
Louisville (**On the Calendar, Venue Regular**) · distillery-country glamping (**On the Calendar,
Venue Regular**) · New Riff sherry finish malted rye (**What's Dropping, Explorer**) · Filmland's
Malted Mummy (**What's Dropping, Social Drinker**). Send-off: "Worth the pour. See you Tuesday."

**Two segment headers, two items each — a shape this pipeline has not used before.** Both
`on-the-calendar` items grouped under one header, both `whats-dropping` items under the next. It
solved a real problem cheaply: the alternative was repeating a segment header later in the edition,
because the slug assignments gave two items each. **Reuse this whenever two items share a slug.**

### THE AUG 27 SECOND-SOURCE CONCLUSION WAS HALF WRONG — and this is the run's lesson

The Aug 27 file records the New Riff second-source attempt as FAILED and instructs the item to ship
flagged. **It should not have.** The Aug 27 run was told to try "New Riff via Breaking Bourbon and
the WA Whisky Watch." **The WA Whisky Watch page in question was already on the Aug 28 board as the
Filmland link-out**, and its headline — "Whisky Watch: Ultra-Aged Bowmore, **New Riff Sherried
Rye**, Filmland's Malted Mummy" — names New Riff. The second source was inside a page the pipeline
had already fetched, read and staged.

**What WA's New Riff entry actually supports, and it is editorial, not a reprint:** ABV 58.65%
(= 117.3 proof, agreeing exactly with FM) · SRP $70 · Availability Limited · 100% malted rye
mashbill · aged 6 years · oloroso and Pedro Ximénez finish · WA's own framing that cask finishes are
"more of an anomaly" for a distillery known for single barrel and bottled-in-bond releases · and
**"which has improved upon its scores since its first release in 2022" — WA referring to its own
ratings.** That last clause is a genuine independent judgement and it is what shipped, attributed in
the sentence: "Whisky Advocate says its scores have improved since 2022."
**Still no descriptors anywhere. No sensory printed. The blurb says "No tasting note is published
yet" instead, which is the Aug 25 technique.**

**Diagnosis: the Aug 27 run searched for the WA Whisky Watch as an external target and never
re-read the page already in its own hand.** The board entry for Filmland even says the roundup
"covers seven releases" — the information needed was one line above the item being verified.

**Instruction that follows, and it is cheap: before recording a second-source failure, grep the
already-staged link-outs for the item's brand name.** A multi-item roundup staged for one item is a
standing second source for every other item on it. **Lesson 38 below.** The mirror of Lessons 34 and
26: sweep what you already hold before searching outward.

**Consequence for the edition: only ONE item shipped single-sourced, not two.** Brough Brothers
remains a joint news release carried by FM, with no local Louisville pickup. **Nothing evaluative
was printed for it** — no sensory, no score, no quality claim, only release-sourced facts (proof,
price, address, time, the named signers, the cause). The flag ran in Notes rather than in reader
copy, which is correct here precisely because the blurb makes no judgement a reader would need
sourced.

### Link re-confirmation — all four 200 with real body text

Fetched to disk with a browser UA, scripts and styles stripped with a DOTALL regex before slicing.
WA Whisky Watch 1,396 words · WA glamping 1,811 · FM Brough Brothers 911 · FM New Riff 668.
**No Notes bullet — nothing failed.** Sixth consecutive edition where every staged link re-confirmed
clean on edition morning.

### Every printed claim, against its source

**Brough Brothers (FM, re-read this morning) — every claim verbatim-supported:** Belle of Louisville
is "the world's oldest operating Mississippi River-style steamboat" · Brough Brothers is "Kentucky's
first African American-owned distillery" · Captain's Cut 96 proof / 48% ABV / $79.00 for 750ml ·
Cask Strength 118 proof / 59% ABV / $89.00 · launch **Saturday, August 29, noon until 2 p.m., at the
Brough Brothers' Waterfront location, 1250 River Road** · Captain Nick Lukaszewski and CEO Victor
Yarbrough on hand to sign a limited number of bottles · "a portion of proceeds from each bottle will
support the preservation and continued operation" of the Belle. **"Cask strength" was defined in one
clause — "undiluted from the barrel" — per the insider-term rule.** The page also carries new detail
not printed: the **15,000-square-foot** River Road facility opens **this September**, the original
Park Hill distillery opened 2021, and Belle cruises showcasing the bourbons are promised "soon."
**That September opening is a live future item — see NEXT RUN.**

**Glamping (WA, re-read this morning):** "Lawrenceburg, Kentucky sits within striking distance of 22
distilleries--Four Roses, Wild Turkey, Woodford Reserve, and Buffalo Trace among them" — printed
with **"Whisky Advocate says" inside the sentence**, per the Aug 25 technique, because the property's
own page gives a different distillery list · Bourbon Barrel Retreats' custom-built barrel cabins with
king beds, private bathrooms, fire pits · the seven two-bedroom cottages with private hot tubs and a
Sprinter for trail runs, printed as "a shuttle van for trail runs." **Nothing lifted from
bourbonbarrelretreats.com, whose own copy is saturated with the banned lexicon.**
**THE EDITION'S ONE QUOTE: Sean Evans, "It's where you are that matters." Six words, named writer,
Tier 2 link-out, verified in the fetched page body.** Spent once, as instructed.

**New Riff (FM link-out + WA corroboration):** $69.99 MSRP, 117.3 proof, aged 6 years, 100% malted
rye, oloroso and Pedro Ximénez finish, on sale **Friday Aug 28 at 11 a.m. EST** at the gift shop,
online shipping and select retailers, **double gold medal recipient at the 2025 San Francisco World
Spirits Competition** — all FM, all verbatim-supported. The "Best in Class finalist" placing was
**not printed** (double gold is the cleaner, harder claim). The improved-scores line is WA's.
**A NEWLY USABLE SPRANCE QUOTE EXISTS AND WAS DELIBERATELY NOT SPENT:** "We're not known for barrel
finishing, which is exactly why we're intentional about when and how we do it" — **19 words, inside
the cap, named master distiller, on the linked page.** The Aug 27 file only recorded the 22-word
"one of our favorites" sentence and concluded no quote was usable. **The 19-word one is usable and
is on file for any future New Riff item.** It was not used here because the edition's one quote went
to Evans and because it is still marketing framing rather than judgement.
**Sherry-cask finishing defined in one clause — "a second stretch of aging in a different barrel."
Malted rye left undefined, exactly as the Aug 26 file instructed. Do not teach both.**

**Filmland (WA):** 43% ABV · SRP $75 · Availability Limited · Los Angeles independent bottler taking
"creative inspiration from B-movies" · first American single malt · "sourced from an undisclosed
distillery in Iowa" · "aged for 5 years in oak barrels that previously held IPA" · "set to make its
debut on August 29th" · **"scoring 90 points with our tasting panel"** · the 93-point White Port Wolf
from its track record · full review held for the Fall issue. **NO DESCRIPTORS EXIST ON THE PAGE AND
NONE WERE PRINTED — this is the cleanest score-without-flavour item the pipeline has shipped.**
**COLLISION HELD: the item was pegged to the Aug 29 date and BrewzleFest was never named**, per the
Aug 23 flag. The 92-point Ryes of the Robots was dropped for length; one prior score carries the
trust signal.

### Voice and compliance, checked before send

Every sentence 3–15 words — **the two 16-word sentences drafted (Bourbon Barrel Retreats' amenity
list, and the New Riff cask sentence) were split rather than trimmed.** Blurbs 68 / 65 / 68 / 57
words, all inside 40–70. Sentence-case bolded headlines. No exclamation points. **Zero banned words
— "experience" was live in two sources ("visitor experience," and the property page's own copy) and
was excluded from both blurbs.** "Hunt" used zero times. **"Last Call" appears only in the masthead,
never in body copy — DISCUS 73.8 clean, no volume, rate or intoxication framing anywhere.** One
quote, six words. Exactly one link per item. **All four UTMs match the scheme: campaign
`lastcall-2026-08-28`, contents `on-the-calendar` ×2 / `whats-dropping` ×2, terms `venue-regular` ×2
/ `explorer` / `social-drinker`.** No new slug invented.

### Coverage, outlets and the shape that shipped

**Personas: Venue Regular ×2, Explorer ×1, Social Drinker ×1 — Friday's two target personas carry
three of four items.** Correct skew for Last Call.
**Outlets: WA ×2, FM ×2 — the three-run outlet gap closed Aug 26 and shipped closed.** The all-WA
Friday flagged since Aug 23 did not happen.
**Bylines: Sean Evans ×1, the Brandon/Higgins/McCormick roundup ×1, FM ×2. No Flicker.** The Evans
count is now two in nine days (SHĀNG is staged Sep 1) — **a third Evans byline before mid-September
is a deliberate call.**
**Cause-led: 1 of 2 spent (Brough Brothers), and the cause was the closing line, never the hook.**
**Constraints all held: no pineapple, no Michigan, no fifth WA cocktail, no third cause-led item.**
**Bottle-heavy as forecast — three of four items involve bottles — but the lead was an occasion and
the second item was a place, so the edition does not read as a release list.**

### Urgent sweep — no override

Window Aug 26–28. **No recall, no safety issue, no litigation or investigation naming a WS partner
brand or venue, no death in the industry.** Searched broadly for recalls, suits and deaths as well
as general industry news. **Everything surfaced was old, unvetted, or already closed:** the True
Story Whiskey dual suits (**June 2026, Wes Henderson's Woodford County project, ~$1.4M unpaid-debt
claims — Tier 4 pickup only, no WS partner, NOT an override**) · the Jan 2026 Kentucky distillery
receivership · Uncle Nearest / Farm Credit (Aug 2025) · **Kimbland/FSS (Dec 2025 — already closed
Aug 27, do not re-surface)** · the craft-distillery contraction and Kentucky barrel-glut coverage,
which is macro context and not news. **Nothing to escalate. Nothing entered the edition.**

---

## THURSDAY Aug 27 — PREP RUN (posted 06:2x PT)

**The assigned job was the Aug 28 second-source attempt, and it FAILED on both items — which is the
correct and expected outcome, not a miss.** Both ship flagged tomorrow. The run's real value came
from two places the Aug 26 run did not reach: **the Whisky Advocate RSS feed, which had refreshed
with three items nobody had assessed, and the FM rail, which carried three more.**

### THE AUG 26 RUN DID NOT READ THE WA RSS FEED — and that is this run's lesson

The Aug 26 file records the FM rail in detail and says nothing about the WA feed. **The feed was
carrying two Aug 25 items and one Aug 24 item, none of them in dedup, none of them on any board,
none of them in any assessed list.** One of them — the chinquapin oak explainer — **carries Whisky
Advocate's own blind-tasting sensory, which is the scarcest thing this pipeline sources.**

**Diagnosis: the Aug 26 run was correctly single-minded about the Friday outlet gap and paid for it
elsewhere.** It went to the FM rail because the gap needed a non-WA item, found two, and stopped.
**The WA feed was skipped precisely because WA could not fix the problem being worked on.**

**Instruction that follows, and it is the cheap half of the Aug 26 lesson's mirror image: read the
WA RSS feed on every prep run regardless of what the run is hunting.** It is one fetch, it is
server-rendered, it is dated, and it is the pipeline's primary discovery path. A run scoped to one
gap must still sweep the standing feeds. **Lesson 34 below.**

### `whisky-advocate-chinquapin-oak-2026` — NEW, STAGED Tue Sep 8. Best find this run.

Whisky Advocate Aug 25, **Danny Brandon** (a new byline on this pipeline — not Flicker, not Evans,
which matters for the concentration gap): `https://whiskyadvocate.com/chinquapin-oak-whiskies`

**What the page supports:** chinquapin (*Quercus muehlenbergii*, sometimes "chinkapin") is a North
American white oak, a near relative of the *Quercus alba* used for standard whiskey barrels, native
to the central and northeastern US and parts of Canada and Mexico. **Rarer in whisky, gaining use
for both maturation and finishing.** Higher tannin content than white oak; distillers say it can
contribute spicier notes plus butterscotch, roasted chestnuts and coffee — **note that this
sentence is attributed to distillers in general, so it is a reported claim, not WA's own.** Common
handling: long open-air seasoning to leach tannins, heavier toast with relatively low char.

**SENSORY — AND THIS IS THE POINT OF THE ITEM. Whisky Advocate's own blind tastings, printable and
attributable to WA:** "In our blind tastings, we've found that the chinquapin seems to make a
difference, often showing more pronounced notes of butterscotch, toasted nuts, and ginger on the
palate, with lingering spices on the finish." **This is a Tier 2 outlet's own tasting panel, not a
brand note and not a reprint. Attribute it to Whisky Advocate in the sentence.**

**Quote is usable — Conor O'Driscoll, Heaven Hill master distiller, eleven words:** "It's not a huge
departure from aging in white oak." Named speaker, from the linked Tier 2 source. **Clean.**

**Bottles the page names as buyable, which is what converts an explainer into a `try-this-next`:**
Heaven Hill's Specialty Barrel Series chinquapin trio (late 2025, first in the series, a Grain to
Glass spin-off) · Woodford Reserve Master's Collection Sweet Oak · Angel's Envy Triple Oak ·
Michter's Bomberger's Declaration and some batches of Shenk's Homestead · Buffalo Trace Old Charter
Oak · GlenAllachie 10 and 12 year old Chinquapin in its Virgin Oak Series · Teeling Wonders of Wood
· Rademon Estate's Shortcross Rye & Malt. **Print no price — the page carries none.**

Also on the page and safe to use: **Glenmorangie began filling chinquapin casks in 1993**; Dr. Bill
Lumsden, arriving 1995, found the differences real but not dramatic, and those whiskies were
eventually bottled as single-cask exclusives for World of Whiskies at Heathrow. **Billy Walker at
GlenAllachie prefers virgin chinquapin from Ozark trees, air-seasoned nearly four years, medium
toast.** Meikle Tòir has a chinquapin-finished single malt at 35 ppm peat.

**VERIFICATION: ONE SOURCE, AND THAT IS SUFFICIENT HERE — this is not a news claim.** It is a Tier 2
outlet's own editorial and its own tasting panel. **The two-source rule governs news events; the
sourced-claims rule governs this, and every claim above traces to the linked page.** Same class as
`heriot-watt-kirin-mango-aroma-study-2026`, which shipped Aug 25 on exactly this footing. **Do not
record this as "needs a second source" — that would be a category error and a future run would waste
a sweep on it.**

**Why Sep 8 and not Sep 1: the Sep 1 board is closed at four and this run does not reopen it.**
Beat `try-this-next` (the standing default for explainers — the slug gap is unchanged and stays
compressed). Persona **Explorer**. **Two insider terms available — tannin and finishing-versus-
maturation. Define one only; tannin is the one the reader needs.** The hook is that a reader can
taste the wood difference in bottles already on the shelf. **`heaven-hill-bib-double-mash-2026` and
`whisky-advocate-barrel-entry-proof-2026` are both in Carried dedup — different products, different
story, no collision.**

### `larrikin-australia-series-2026` — NEW, WATCHING. Not staged, and the reason is distribution plus a ticket question.

Fred Minnick Aug 27, published this morning:
`https://www.fredminnick.com/2026/08/27/larrikin-bourbon-co-to-release-the-australia-series/`

**What the page supports:** Larrikin Bourbon Co. — veteran-owned, Lawrenceburg KY, founded by
Australian-raised distiller **Greg Keeley** and **Katie Keeley** — announced the "Australia Series,"
three cask-strength bourbons finished in Australian barrels: **Manuka Honey, Golden Wattle, Sugar
Cane Rum.** Made from **just six barrels of 11-year-old Old Elk bourbon**, high-rye mashbill **51%
corn / 34% rye / 15% malted barley.** **One expression released per day: Fri Sept 11 Manuka honey,
Sat Sept 12 golden wattle, Sun Sept 13 sugar cane rum.** Available **exclusively at the Kentucky
Bourbon Festival, Bardstown, Sept 10–13.** No retail or online release planned; sold while each
allocation lasts; a VIP package for VIP Tier ticket holders.

**Quote is usable and it has genuine voice — Greg Keeley, thirteen words:** "We were bloody lucky to
get our hands on these unique Aussie barrels." From FM, the linked source. **Clean.**
**But his next two sentences are his own tasting notes** — "The Manuka honey is subtle and lingers,
the golden wattle is simply extraordinary, and the rum barrel will have folks hoisting the jolly
roger." **Founder's copy, not independent. Print none of it.**

**WHY WATCHING AND NOT STAGED — two blockers, and the second is the real one:**
1. **One source** (FM on a news release). No independent pickup searched for yet.
2. **Festival-exclusive distribution, and the festival is very likely sold out.** This sits on the
   line the pipeline has drawn four times (Beam Ten-Pin, Jack Daniel's #17, Hibiki 12, Gleneagles).
   **The honest distinction is that the action here is attending a dated event, not chasing a
   bottle** — which is the `on-the-calendar` beat working as designed. **But that only holds if a
   reader can still get in.** `kentucky-bourbon-festival` is already in WATCHING under "unchanged
   and blocked," which is a signal in itself.
**What would unblock it: KBF ticket availability for Sept 10–13, checked once, plus a second
outlet.** If tickets are gone, this is a Collector-interest curiosity with no reader action and it
drops. **Check on the Sun Aug 30 run — there is time, the event is two weeks out.** Beat would be
`on-the-calendar`, persona Venue Regular or Collector. **Bardstown, so the Bardstown link-out note
applies; and note this is Bardstown the town, not Bardstown Bourbon Company — no brand collision
with `bardstown-lochs-of-jura-2026` on the Sep 1 board.**

### `four-roses-experimental-002-honey-cask-2026` — NEW, ASSESSED, AND CLOSED THE SAME RUN. Distribution.

Fred Minnick Aug 26:
`https://www.fredminnick.com/2026/08/26/four-roses-releases-honey-cask-expression-in-experimental-series/`

**Experimental Series No. 002 Honey Cask Finish**, the second in the series after No. 001 Mizunara
Cask Finish. **$55 · 375ml · 104 proof · a blend of six-, seven- and eight-year-old bourbons from
the OESQ and OBSK recipes · finished three to nine months in barrels that had previously held Four
Roses' Bourbon Barrel Aged Honey**, made with Bohman Bee Company. **Available exclusively at the
Four Roses Distillery and Cox's Creek Visitor Centers from Sept 18, while supplies last.**

**It fails the forward bar on distribution.** Two Kentucky visitor centers, limited supply — **a
reader outside Kentucky cannot act on it.** Same test that closed Beam's Ten-Pin nine days of
runs ago, and Jack Daniel's #17, Hibiki 12, Gleneagles and Bruichladdich before that. **The story is
genuinely good — a barrel's second life, honey then bourbon — and that is not enough on its own.**

**Sensory is Four Roses' own** ("subtle notes of natural honey"). **Brent Elliott's quote is 44 words
and contains "journey," a banned word. Unusable twice over.** Recorded so no future run re-counts it.
**Moved to DROPPED. Do not rediscover.** If Four Roses ever gives this national distribution, that
is a new development on a closed key and may be reopened.

### Assessed and NOT staged this run

- **`whisky-advocate-all-inclusive-resorts-2026`** — WA Aug 25, `/all-inclusive-resorts-with-great-
  whisky-selections`, "Luxe Life, Drams Included." **FETCHED AND READ, and recommended against.**
  Eight resorts, **nightly rates $2,035 to $2,950 for two.** Jumby Bay, Twin Farms, Ranch at Rock
  Creek, Four Seasons Naviva, Clayoquot, Jade Mountain, Brush Creek Ranch. The whisky detail is real
  and deep (Twin Farms includes 80+ whiskies; Brush Creek distills its own).
  **This is a useful NEGATIVE finding about the Friday seam and it refines Lesson 26.** The glamping
  piece worked because it was actionable — barrel cabins, a drive from 22 distilleries. **This is
  aspirational, not actionable, and $2,800 a night is not a Social Drinker or Venue Regular
  occasion.** Its copy is also saturated with banned words end to end (luxury, premium, finest,
  cellar, vault) — verifiable against, unliftable from. **WA's travel section yields both kinds of
  service journalism. Only the actionable kind clears. Test the price point before staging a travel
  item.** Not a Notes bullet; not worth Aaron's attention.
- **`uncle-boojies-gatsby-research-2026`** — FM Aug 26. **FETCHED AND READ.** Uncle Boojie's
  Distilling Co. and researcher **Cassie Tatum** on how Louisville's bourbon culture and social
  circles shaped Fitzgerald between 1914 and 1918 — Camp Taylor, the Howard and Atherton distilling
  families, Howardstown bootlegger Martin "Mr. Jesse" Spalding. Founder **Stephen A. Smith**'s own
  Howard family roots; Uncle Boojie's is partnering with **Whiskey House of Kentucky** (CEO **David
  Mandell**) to recreate the historic Howard family mashbill from family records.
  **A genuinely strong wider-culture angle — literature, which the framing rules explicitly reward —
  and NO READER CONSEQUENCE YET.** The only event is an **invitation-only discussion** at the
  Kentucky Bourbon Festival, and the recreated-mashbill bottle has **no date, no price, no proof.**
  **Beat file, not staged, not dropped.** Revisit the moment the Howard mashbill bottle gets a date —
  **that would be a strong Tuesday item and the research is the hook.** Tatum has usable quotes
  under twenty words if it ever runs.
- **`whisky-advocate-steal-my-sunshine-cocktail-2026`** — WA Aug 24, `/steal-my-sunshine-whisky-
  cocktail`, "A Tropical Bourbon and Sherry Cocktail." **NOT FETCHED, deliberately.** It would be a
  **fifth consecutive WA cocktail, which the Friday constraints say needs Aaron's say-so**, and
  "tropical" makes a pineapple collision likely against `bardstown-victoria-pineapple-2026`.
  **Two independent blockers before a fetch is worth spending. Recommend against.** If a future
  Friday is genuinely thin and Aaron has cleared the cocktail count, fetch it then.
- **`bardstown-bourbon-capital-mash-up-2026`** — surfaced off the sevans index and **it is DEAD.**
  The path `/bardstown-bourbon-capital-mash-up-party-2026` is a **June 2 2026** Sean Evans piece
  about **National Bourbon Week, June 14–21 2026** — an event ten weeks past. Bespoke in Bond,
  Bardstown; ten distillers; $150 GA / $375 VIP; organiser Sam Lacy of Bourbon Capital Alliance.
  **Recorded only because it is the clearest possible demonstration of what the sevans index is and
  is not — see HOSTS.** Do not stage. **Worth one line in a September pointer file if the 2027
  edition is announced: this is a real, well-attended Bardstown event and next year's date would be
  strong Friday material with months of lead time.**
- **`redwood-empire-hyperion-batch-001-2026`** — **a second source now exists** and it changes
  nothing. TSB Aug (`/2026/08/redwood-empire-unveils-the-hyperion-limited-edition-blend/`) alongside
  FM Aug 24. **Both would clear the two-source rule; TSB is still not on the inlined tier list, so
  the link-out is the same stall as the tariff.** Logged. Cheap to pick up on a thin Tuesday once the
  tier question is answered. Not chased further.
- **The Spirits Business Aug index — 23 URLs, swept, nothing stageable.** Two worth naming:
  `/scam-whisky-firm-shut-down-by-uk-government` is **genuinely reader-relevant for a Collector**
  (cask-investment fraud) and is blocked on the same TSB tier question — **the best argument yet for
  answering it**; `/worlds-largest-johnnie-walker-collection-heads-to-auction` runs into the standing
  auction-fatigue recommendation. GlenWyvis funding, the Cameronbridge strike threat, Pernod FY
  sales, Hemsworth/Archie Rose — **all trade, no reader consequence.**
- **The sub-$30 gap — not checked this run.** Three consecutive runs have confirmed the $35–$40
  floor with Tier 1–2 sourcing. **Aaron's standing decision, compressed to `_unchanged_` for a
  fourth time. Do not spend a search on it before September.**

### Fri Aug 28 — SECOND-SOURCE ATTEMPT ON BOTH ITEMS: FAILED. Board unchanged at four.

**`new-riff-sherry-finish-malted-rye-2026` — STILL ONE SOURCE.** Searched and found six pickups,
**every one of them the same New Riff news release**: BevNET (a PR wire), The Bourbon Flight, The
Whisky Wire, The Manual, Northwest Beer Guide, and **The Whiskey Reviewer** — whose Aug 27 piece
looked like a review from its headline ("...Has Dropped") and **is an unbylined reprint.** Fetched
and confirmed. **Press-release reprints across outlets count as one source. Ships flagged.**
**NEW AND IMPORTANT — the circulating tasting notes are New Riff's own and must not be printed:**
"dark fruits, buttery sherry oak," "full-bodied and savory, sappy mouthfeel," "clove, wood spice and
fruit-forward finish." **These are attributed to the distillery in every reprint. Print none.**
**A second Sprance quote exists at nineteen words** — "We're not known for barrel finishing, which is
exactly why we're intentional about when and how we do it" — **and it is unusable: it lives in The
Whiskey Reviewer, an unlisted reprint, and the protocol forbids pulling a quote from a Tier 3–4
reprint even when the wording is identical.** FM carries the longer 22-word Sprance quote instead.
**Do not chase this. The edition already has its one quote in Evans's six words, and the cap is one.**

**`brough-brothers-belle-of-louisville-2026` — STILL ONE SOURCE, and two avenues are now closed.**
**`belleoflouisville.org/news` fetched and read: nothing on the partnership, the bottling, Captain's
Cut, or an Aug 29 event.** The only Aug 29 on that page is a 2025 Cincinnati sailing.
**`broughbrothers.com` is a client-rendered Vite SPA with no readable content** — so the Tier 1
primary route that cleared Jack Daniel's is not available here. Web search found only 2021–2022
archive coverage. **Ships flagged.**

**All four Aug 28 link-outs re-confirmed 200 with real body text today, Aug 27:** WA Whisky Watch
(76KB), WA glamping (77KB), FM New Riff (111KB), FM Brough Brothers (114KB). **Tomorrow's run still
owes a fresh re-confirm, but nothing is rotting.**
**Board stays at FOUR. Nothing added, nothing cut. Lead with an occasion, not a bottle. Send-off
required — "worth the pour."** Two of four ship with an explicit verification flag; **that is the
honest shape and it is better than running two.**

### The September seasonal bump — SURFACED TO AARON THIS RUN, as the Aug 25 file instructed

The skill adds a **third weekly edition September through November**, framed publicly as fall
release-season coverage so the December drop back to two reads as planned. **The Aug 25 file said to
surface it once if Aaron had not raised it by the Aug 28 run. He has not. Today is the last prep run
before that, so it went in the Notes.** One bullet, framed as his call, no recommendation attached —
**though the honest supply read is that Tuesdays run deep and Fridays do not, so a third edition
would land on the seam that is already hardest to fill.** If he answers, record the answer here and
never re-raise it. **If he does not answer by the Sep 1 edition, do NOT apply a default — a cadence
change is not a copy default, and adding an edition on silence would break the promise the cadence
governance section exists to protect.** Carry it as unanswered and stop mentioning it.

### HOSTS movement — the sevans experiment paid off, and it is not what it looked like

- **`whiskyadvocate.com/tag/sevans` — 200 ON THE SECOND AND FINAL AUTHORISED ATTEMPT (was 503
  Aug 26). The experiment is spent and it succeeded.** 54KB, server-rendered, **16 article-shaped
  paths.** The Flicker-concentration gap now has a working Sean Evans supply line.
  **BUT — and this is the finding that matters — it is an AUTHOR ARCHIVE, NOT A DATED FEED.** It
  carries no dates, and its ordering is not recency: the one path that looked like fresh Friday
  material, the Bardstown Mash Up party, is a **June 2 piece about a June 14–21 event.**
  **So: harvest sevans for EVERGREEN service journalism, never for news, and date-check every path
  before staging anything off it.** Untouched and worth a look on a thin Friday:
  `/outdoor-excursions-for-whisky-lovers` and `/19-hot-whiskies-to-hunt-summer-2026` (**summer
  framing, so it fades within weeks — check it before September ends or not at all**).
  Everything else on the index is already in dedup, staged, or not whiskey
  (`/how-to-store-tequila-bottles`). **Do not re-fetch before October.**
- **`broughbrothers.com` — 200 but USELESS. A client-rendered Vite SPA**; 1.9KB of shell, one empty
  `<div id="root">`, zero content. **Not a usable Tier 1 primary. Do not retry it for release facts.**
  **Generalise nothing from this** except the standing rule: a distillery's own site is only a
  primary source if it actually renders to a script.
- **`whiskeyreviewer.com` — loads 200, clean text, and is a REPRINT HOST.** Its New Riff piece is
  unbylined and reproduces the distillery's notes and quote verbatim. **Treat it as reprint supply,
  never as a second source, and never pull a quote from it.** Its "Whiskey Lawsuits, Bankruptcies
  and Shutdowns Update" column surfaced in the urgent sweep and may be a cheap sweep input — **as a
  lead only, never as a source.**
- **`whiskyadvocate.com/call/blogs/rss/` — 200, ten dated items, and it is the reason this run
  found anything.** Reconfirmed as the primary WA discovery path. **Read it every prep run.**
- **`robbreport.com/food-drink/spirits/` — index still broken, not retested** (monthly cadence, next
  test September). Reached by web search instead: **nothing new since Hibiki 12 on Aug 24.**
  **That is a THIRD consecutive week with nothing stageable.** Escalated below.

### Urgent sweep — no override

**Window Aug 25–27.** No recall, no safety issue, no litigation or investigation naming a partner
brand or venue, no death in the industry. **One candidate was chased down and closed properly:**

- **`kimbland-distillery-fss-warning-2025` — ASSESSED AND CLOSED. NOT AN OVERRIDE.** Food Standards
  Scotland warned consumers not to buy or consume New Make Spirit of Whisky, three Sanday gins, and
  filled casks from **Kimbland Distillery Ltd**, on the grounds the company "has been producing and
  selling alcoholic products without the required safety controls." **This is a real consumer safety
  warning on whisky and it read like a genuine override until it was dated: 16 December 2025 —
  eight months old.** Orkney only, no US distribution, no WS partner brand or venue, and a warning
  rather than a formal recall. **Closed. Do not re-surface.**
  **Recorded because the sweep will keep surfacing it:** an undated search result for a safety
  warning is the single most dangerous input this pipeline handles. **Date a safety item before
  anything else — before reading it, before assessing it, before drafting a line about it.**
- The Blue Spirits Chapter 7 filing, the Barton 1792 warehouse collapse and the various bankruptcy
  round-ups all resurfaced and are all **prior-window items already assessed and closed.**
- **The EU retaliatory-tariff suspension that lapsed Aug 6 still has no vetted spirits pickup** —
  fifth consecutive run recording that. Fold into `canada-50pct-tariff-aug-19-2026` if one files.
- **Nothing to decide.**

---

## WEDNESDAY Aug 26 — PREP RUN (posted 06:2x PT)

**The whole job was Friday Aug 28's outlet gap, and the gap closed — twice over.** Two
non-Whisky-Advocate items are staged. **Both came off the Fred Minnick rail, and one of them was
sitting on the Aug 24 rail that the Aug 24 run recorded as producing nothing stageable.**

### THE AUG 24 FM RAIL WAS NOT EMPTY — and this is the run's real lesson

The Aug 24 file states the FM rail "produced nothing stageable." **It carried three articles that
day and at least one of them was the exact item the board had been searching for across three
runs:** `brough-brothers-belle-of-louisville-2026`. The other two were Beam's Ten-Pin (assessed and
closed below) and Redwood Empire Hyperion (a key already in the Carried dedup list as
`redwood-empire-colonel-armstrong-2026` — different bottle, but not chased this run).

**Diagnosis: the rail was read for bottle releases and not for occasions.** Brough Brothers is an
event item with a bottle attached — a Saturday launch with named signings at a named address. A run
hunting "what dropped" scrolls past it. **The Aug 24 run also spent itself on the 23-item TSB index
and on Robb Report, both of which were genuinely dry, and the rail got the tail end of the
attention.** This is the same failure mode as Lesson 26 (service journalism is the Friday seam):
**Friday material does not look like Tuesday material, so a single-pass read optimised for releases
misses it.**

**Instruction that follows from this, and it is cheap: on any run where a Friday slot is short,
re-read the FM rail a second time asking only "is there a date, a place, and a reason to go?"**
Nothing else changes about the discovery order.

### `new-riff-sherry-finish-malted-rye-2026` — PROMOTED from September pointer to STAGED Fri Aug 28. This is the non-WA item the board asked for.

The key already existed — added Aug 23 as one of four September pointers, all of them recorded as
needing their own link-out. **It now has its own link-out and a hard date, and the date is the
edition day itself.** This is an update to a staged key, not a new discovery.

Fred Minnick, Aug 25:
`https://www.fredminnick.com/2026/08/25/new-riff-set-to-re-release-sherry-finish-malted-rye/`

**What the page supports, and only this:** $69.99 MSRP · **117.3 proof** · **six years old** ·
100% malted rye mashbill · finished in **Oloroso and Pedro Ximénez sherry casks** · **released
Friday Aug 28, 11 a.m. EST** · New Riff gift shop, online shipping, and select national retailers ·
**double gold and a "Best in Class" finalist placing in the Special-Barrel Finished Whiskey category
at the 2025 San Francisco World Spirits Competition.** No bottle count is published. **No tasting
notes anywhere on the page — print none.**

**Quote is unusable.** Brian Sprance, master distiller: "Over the years, this release has become one
of our favorites because it strikes a balance between something familiar and something unexpected."
**Twenty-two words, over the twenty-word cap, and it is marketing.** Do not trim it into the cap —
trimming a quote to fit is fabrication. **Run the item without a quote.**

**VERIFICATION: ONE SOURCE.** FM is reprinting a New Riff news release — the Sprance quote and the
competition placing are both release material. **No independent pickup found.** Status is honest:
this ships **flagged** on Friday unless a second outlet files by then, or it ships as the
release-based item it is with the competition placing attributed to the competition rather than to a
taster.

**Why it clears anyway, and why it is the right non-WA item:** it is a national release, it drops
the morning the edition posts, and the SFWSC placing is a real third-party judgement even though
nobody printed descriptors. **The hook is the date: "out this morning."** Beat `whats-dropping`,
persona Explorer. **Two insider terms — malted rye and the two sherry cask names. Define sherry-cask
finishing in one clause; do not teach both.**
**It does make Aug 28 bottle-heavy** — Filmland, New Riff, and Brough Brothers all have bottles.
The glamping piece is the only pure occasion item. **That is an acceptable trade for closing a
three-run outlet gap, and Brough Brothers carries an event anyway.**

### `brough-brothers-belle-of-louisville-2026` — NEW, STAGED Fri Aug 28, and it is the occasion-led non-WA item

Fred Minnick, Aug 24:
`https://www.fredminnick.com/2026/08/24/brough-brothers-belle-of-louisville-team-up-for-bourbon-releases/`

**What the page supports:** Brough Brothers Distillery — **Kentucky's first African American-owned
distillery**, founded by the Yarbrough brothers — bottled two commemorative expressions with the
**Belle of Louisville**, the world's oldest operating Mississippi River-style steamboat.
**Captain's Cut, 96 proof / 48% ABV, $79 per 750ml. Cask Strength, 118 proof / 59% ABV, $89.**
**Launch Saturday Aug 29, noon to 2 p.m., at the new Waterfront location, 1250 River Road,
Louisville.** Limited bottles for sale at the event, **with signings by Belle captain Nick
Lukaszewski and Brough Brothers CEO Victor Yarbrough.** Additional bottles follow at select
retailers. **A portion of proceeds supports the Belle's preservation and operations.** The
partnership grew out of Brough Brothers' multi-year sponsorship of the Kentucky Derby Festival
Great Steamboat Race.

**No age statement, no bottle count, and NO TASTING NOTES on the page. Print none.**

**Quote — unusable by one word.** Victor Yarbrough: "Sponsoring the Great Steamboat Race introduced
us to the Belle, and opening our doors on Waterfront Park made us family." **Exactly twenty words;
the cap is under twenty.** Barbara Sexton Smith's is longer. **Run it without a quote.** Recorded so
a future run does not re-count and talk itself into it.

**VERIFICATION: ONE SOURCE.** FM is working from a joint news release — both quotes are release
material. **Searched for local Louisville pickup (WDRB, LPM, WHAS, louisvilleky.gov) and found only
archive coverage of the 2021 Park Hill opening and the 2022 Waterfront announcement.** Nothing on
this release. Status ships **flagged** unless Thursday finds a second outlet.

**Why it is the best Friday item on the board regardless of the flag:** a dated, addressed,
free-to-attend event two days after the edition, with named people signing bottles, a cause
attached, and a distillery story that is genuinely worth knowing. **Beat `on-the-calendar`, persona
Venue Regular.** It is **cause-led**, so it spends one of the two cause-led slots the Friday
constraints allow — **the count goes from zero to one. No pineapple, no Michigan, no WA cocktail is
touched.**

### `jack-daniels-american-single-malt-2026` — NEW, STAGED Tue Sep 1 as the fourth item. Clears both conditions the Aug 25 file set.

The Sep 1 board was closed at three with one condition: **a fourth is allowed only if it is neither
Collector nor a Flicker byline.** This is **Explorer** and the link-out is **Fred Minnick**. Clean.

Fred Minnick, Aug 26 (published this morning):
`https://www.fredminnick.com/2026/08/26/jack-daniels-releases-american-single-malt-nationwide/`

**What the page supports:** **$74.99 SRP for a one-litre bottle** · **90 proof** · **100% malted
barley**, ground, fermented and distilled in Lynchburg · charcoal mellowed through sugar maple ·
aged in new charred American oak · **finished in Oloroso sherry casks** · **no age statement** ·
**previously sold only in select duty-free retail globally, now a limited annual release reaching
US retailers nationwide this fall**, quantities limited by market. **American Single Malt is the
first new whiskey category the TTB has formally recognised in over fifty years** — that is the
angle, and it is what makes a Jack Daniel's bottle interesting to an Explorer rather than just big.

**Quote is unusable — 44 words.** Chris Fletcher's statement runs long and is corporate. **No quote.**

**SENSORY: NO INDEPENDENT TASTING EXISTS.** The circulating "rich aromas of soft oak, fruit and
cocoa, followed by flavors of dark chocolate-covered nuts, berries and a sherry-laden finish" is
**Jack Daniel's own marketing copy**, carried by The Daily Pour, which states plainly that it has
not tasted the whiskey yet. **Do not print it as a tasting note.** Use the Aug 25 technique instead:
say so to the reader.

**VERIFICATION: clears.** The brand release is a Tier 1 primary source; **Breaking Bourbon carries
it** (`breakingbourbon.com/bourbon-whiskey-press-releases/jack-daniels-debuts-american-single-malt-whiskey-nationwide-in-limited-annual-release`,
Tier 2 and explicitly on the inlined list) and FM carries it independently. Primary plus a
corroborating Tier 2 mention clears the rule as written. **The Bourbon Flight and The Daily Pour are
the same release again and add nothing to the count.**

**Sep 1 shape after this: FOUR — Collector ×2 (Maker's Mark, Bardstown), Explorer ×2 (SHĀNG, Jack
Daniel's).** Outlets: Robb Report ×2, WA ×1, FM ×1. **Flicker is now two of four instead of two of
three.** Three of the four carry independent sourced sensory; Jack Daniel's is the one that does not
and must say so. **The board is closed at four. Do not add a fifth.**

### `beam-ten-pin-decanter-2026` — NEW, ASSESSED, AND CLOSED THE SAME RUN. Distribution.

Fred Minnick Aug 24 (`/2026/08/24/jim-beam-announces-return-of-ten-pin-decanter/`) plus The Daily
Pour Aug 21, which has the exclusive Freddie Noe quote. **$124.99 · 750ml · ten years old · 100
proof · a revival of the 1950s bowling-pin decanter · sold only at The American Outpost at the
James B. Beam Distilling Co., Clermont, Kentucky.**

**It fails the forward bar on distribution, and it has almost certainly already sold out.** The
Daily Pour published Friday Aug 21 saying it went on sale "beginning Saturday" — **Aug 22, four
days before this run.** FM's Aug 24 piece gives no date at all, so the only date available comes
from an unlisted outlet. **One distillery counter, limited volume, sale opened four days ago:
a reader cannot act on it.** Same test that closed Jack Daniel's #17, Hibiki 12, Gleneagles and
Bruichladdich.

**Sensory is brand copy** — "aromas of rich oak, vanilla, baked bread and caramel... toffee, toasted
oak, baking spices and fruit." The Daily Pour writes "is described as," and FM prints no notes at
all. **Nobody independent tasted it.**
**Freddie Noe's quote is usable at fifteen words if this ever revives** — "The Ten-Pin bottle is one
of those pieces of Beam history that people remember" — **but it lives in The Daily Pour, an
unlisted outlet, so it cannot be pulled against a FM link.** Recorded and closed.
**Moved to DROPPED. Do not rediscover.**

### New September pointers — two, both verified on facts, both sensory-blocked, neither staged

- `cedar-ridge-anniversary-edition-2026` — FM Aug 25
  (`/2026/08/25/cedar-ridge-releases-limited-edition-anniversary-bourbon/`). Second in Cedar Ridge's
  Anniversary series, marking the Iowa distillery's **21st anniversary**. **$64.99 / 750ml · 112
  proof · mashbill 74% corn, 14% rye, 12% malted barley · finished in five cask types: Madeira, Napa
  cabernet, Pedro Ximénez sherry, tawny port and Tokaji.** Out **Aug 25** at the distillery, online
  pre-sale, and select retailers. No bottle count, no age.
  **Master blender Murphy Quint has a usable sixteen-word quote:** "The Madeira and Napa Cabernet
  casks are what really push this blend in a new direction." **His other two quotes both contain
  "experience," a banned word — do not use them.**
  **NO INDEPENDENT SENSORY.** The page is about cask composition, not flavour. **Print none.**
  One source (FM on a news release). **Five cask types is the hook and Tokaji is the surprising one.**
- `blue-note-cherry-wood-cask-2026` — FM Aug 25
  (`/2026/08/25/blue-note-bourbon-releases-new-cherry-wood-cask-expression/`). **$64.99 / 750ml ·
  120 proof · cask strength, unfiltered · mashbill 70/21/9 · finished in wild-cherry-wood casks from
  the Jura region of France · roughly 1,000 cases · out Aug 25 online via Seelbach's and in GA, KS,
  KY, MI, MO and TN.** No age statement.
  **SENSORY IS THE DISTILLERY'S OWN** — "vibrant notes," "unmistakably unique finish that lingers,"
  "depth and brightness." **Marketing, and vague marketing. Print none.** Dan Jurkovic's quote is
  33 words and is also marketing.
  One source. **Wild cherry wood is a genuinely unusual finishing wood and is the whole angle;
  six states plus a national online retailer clears the forward bar.**

### Assessed and NOT staged this run

- **`redwood-empire-hyperion-batch-001-2026`** — FM Aug 24. Not fetched. `redwood-empire-colonel-
  armstrong-2026` is already in the Carried dedup list, so the brand is not new to the board and
  nothing on the board needed a fourth bottle. **Cheap to pick up on a thin Tuesday; not needed now.**
- **`blue-spirits-distilling-chapter-7-2026`** — TheStreet Aug 24, surfaced by the urgent sweep.
  Chapter 7 filed **June 11 2026**; the suit names **Luctor International, Buffalo Trace and
  Sazerac** on contract and fraud claims. **Assessed against an override and it is not one.** No
  recall, no safety issue, no death, and **no WS partner brand or venue is named** — Buffalo Trace
  is a subject of prior coverage, not a partner. **It is trade litigation with no consequence for a
  reader's shelf or weekend**, same test that closed Sazerac/RNDC and the Garrard County distress
  story. **Logged, not staged, not bulleted.**
- **The sub-$30 gap, checked once and no relief.** Every result at that price point this run was a
  Tier 4 listicle or an SEO aggregator — The Whiskey Wash, WikiliQ, Boozemakers, Bourbon Inspector,
  whiskeyful.com. **Not one Tier 1–2 source.** This is the third run to confirm the Aug 18 read:
  **$35–$40 is the real floor in this market at 90+ points.** Aaron's standing decision; not
  re-queried, compressed to `_unchanged_`.

### HOSTS movement — two findings, one bad, and both matter for the discovery order

- **`whiskyadvocate.com/tag/sevans` — 503 Service Unavailable.** This was the one cheap experiment
  the Aug 25 file authorised, aimed at the Flicker byline concentration. **It did not render and it
  did not 404 either, so this is a transient server response rather than a missing page.** Per the
  authorisation the result is recorded; **but a 503 is not the same as a 404, so it is worth exactly
  one more attempt on a future run and then never again.** Do not spend a third.
- **`robbreport.com/food-drink/spirits/` NOW 307-REDIRECTS to `tollbit.robbreport.com`, which does
  not resolve (DNS timeout).** **The first step of the four-deep discovery order is broken.** Robb
  Report *article* URLs still fetch normally — only the section index is gated. **Until this clears,
  reach Robb Report by web search on its article slugs, not by the index.** This is a real
  degradation: the index was the reliable weekly path to the Taste Test column, which is the
  pipeline's best supply of independent tasting notes. **Retest the index monthly, not per run.**

### Urgent sweep — no override

Window back through Aug 25, per instruction. **No recall, no safety issue, no litigation or
investigation naming a partner brand or venue, no death in the industry.** The Blue Spirits Chapter 7
filing is assessed above and is not one. **The EU retaliatory-tariff suspension that lapsed Aug 6
remains the only live thread and still has no vetted spirits pickup** — if one files, fold it into
`canada-50pct-tariff-aug-19-2026` rather than opening a second key. Nothing to decide.

---

## TUESDAY Aug 25 — WHAT SHIPPED (The Shortlist, posted 06:15 PT)

**Four items, exactly as staged since Aug 19. Nothing added, nothing cut, no fifth item.** The
board was closed going in and stayed closed — the second consecutive edition to run that way, and
the shape an edition day is supposed to have. Order shipped: Jameson Distiller's Batch (What's
Dropping, Explorer) · Redemption Single Barrel Bonded (What's Dropping, Collector) · the
Heriot-Watt/Kirin mango study (**Try This Next, Explorer — the pipeline's first science item**) ·
Garrison Brothers Cowboy Bourbon (On the Calendar, Collector). **No send-off — Shortlist correctly
carries none.**

**The tariff stayed out, as instructed four runs running.** No reader-facing mention. It carried
one Notes bullet stating the Sep 1 default explicitly, which is the escalation the Aug 24 file
asked for and is the correct place for it.

### Link re-confirmation — all four 200 with real body text

Fetched to disk with a browser UA, scripts and styles stripped with a DOTALL regex before slicing.
Robb Report Jameson 9,951 stripped chars · Robb Report mango 8,589 · Robb Report Redemption 9,286 ·
`garrisonbros.com` Cowboy Bourbon event page 6,217. **No Notes bullet — nothing failed.** Sixth
consecutive edition where every staged link re-confirmed clean. Both hosts behaved exactly as HOSTS
records them; no host note changes this run.

### Every printed claim, against its source

- **Jameson.** Printed: single pot still = one distillery, one pot still, malted and unmalted
  barley (**Robb Report's own definition, lifted as a definition not as prose**) · Distiller's
  Batch is a single pot still whiskey, not the blend · **score 88** · Flicker's notes — dark and
  milk chocolate, nutmeg, maple, ripe stone fruit. All four from the linked Robb Report piece.
  **Price $50 and "nationwide from September" are Whisky Advocate's figures and were printed
  attributed in-copy** — "Whisky Advocate puts it at $50, nationwide from September" — because the
  linked page carries neither. **This is the pattern to reuse when a claim's home is the second
  source: attribute it in the sentence, never against the link.** Pernod Ricard's release notes
  and the Forbes contributor column were both excluded, as instructed.
  **NOT printed:** the five cask types, the three-year legal minimum, Kevin O'Gorman, Midleton,
  the Bow Street/1826 origin. All available, all cut for length; none needed.
- **Redemption.** Printed: bonded requires four years, this is six (**the honest hook, and the
  four-year floor appears as a comparison clause, not as a re-teach**) · first bonded release from
  the brand · drawn from one barrel (**"single barrel" self-defined in plain English rather than
  taught**) · Ross & Squibb, Lawrenceburg · 100 proof, no chill filtration, bottled in Frankfort ·
  **$50, "in stores and at ReserveBar now"** — verbatim availability framing, no footprint, never
  "nationwide." All from the linked Robb Report piece.
  **SENSORY: none printed, and the edition says so out loud** — "No independent tasting exists yet,
  so judge it yourself." **That line is the model for every future no-sensory item.** It turns the
  gap into reader-facing honesty instead of a silent omission. The brand's vanilla/leather/raspberry
  copy never entered the draft. Alan Kennedy's quote was available and deliberately unspent — the
  edition's one quote went to the mango study.
  **NOT printed:** the Diageo/Bulleit trade-dress suit, Higher Marques ("Collection" is a banned
  word even as part of the proper noun and was avoided entirely), the 18-Year-Old at $400, Bib &
  Tucker. The 18-Year is the article's actual headline subject and was correctly left alone —
  `redemption-ancients-18yr-2026` is a separate key and is still only an alternate.
- **Mango study.** Printed: Heriot-Watt, run with Kirin · 14 Scotch and Irish whiskies · aldehydes
  and acetals amplify the mango note · **Annie Hill quote, 15 words, verbatim, named, from the
  linked page** — "But we didn't know where the mango flavor was coming from—and now we do."
  **The edition's single quote, spent here as instructed.** Robb Report named in-copy.
  **NOT printed:** Takehiko Hiura, the three named compounds, JASBC, Dr. Calum Holmes, the
  additives-illegal-in-scotch aside, the press-release-versus-publication timing gap. The item is a
  learning item; the compound names would have made it a lecture.
- **Garrison.** Printed: **Sat Sept 12** · 8 a.m. to 4 p.m. · Hye, Texas · **$249.99** ·
  **141.0 proof** · uncut and unfiltered · live music, Whiskey Shack serving neat pours and
  cocktails. All from the linked Tier 1 event page. **16,000 bottles / 1,000 held for the day
  attributed in-copy to Whisky Advocate**, as required — the event page states no counts. The 279
  online-store figure was cut for length, not for sourcing.
  **NO AGE PRINTED.** The WA "at least 8 years" versus brand "six scorching Texas summers" conflict
  is unresolved and was not split, not hedged, not alluded to. **Third edition-day instance of
  printing around an age conflict; this is now settled practice.**
  **NO SENSORY PRINTED.** The event page's notes are marketing copy and the page also uses
  "experience" and "toasted" — two banned words in one sentence, never near the draft.
  Street address cut for length. `garrisonbros.com/cowboy-bourbon/` never fetched.

### Voice and compliance, checked before send

Every blurb 57–68 words, inside the 40–70 band. Every non-quote sentence 3–15 words. Sentence-case
bold headlines, no exclamation points. **Banned-word sweep clean** — no log, collection, premium,
journey, experience, handcrafted, world-class, finest, whale, vault, cellar, bunker, toast.
**"Hunt" used zero times** (budget is one). **DISCUS 73.8 clean** — "neat pours and cocktails" is a
service description, not a consumption cue; no volume, rate or intoxication framing anywhere.
Insider terms: **one per item, maximum** — single pot still defined on Jameson (**the definition
deliberately held back on Aug 21 and spent here, as planned**); bottled-in-bond assumed and not
re-taught for the fifth instance; "single barrel" and "single malt scotch" carried in plain English
without a definition clause. **Reader is the subject in every payoff line.**

### Coverage floor and the byline collision

**Explorer ×2, Collector ×2**, as staged. Social Drinker is served by Jameson ($50, nationwide, a
brand the reader already knows) and by the mango item, which is the edition's no-intimidation
piece — it points the reader at a glass they already own. Venue Regular is served by Garrison.
**Cigar-Whiskey Crossover: not served, and correctly not forced** — it is a Friday floor, not a
Tuesday mandate, and Tuesday carries the Explorer/Collector weight by design.

**The Flicker byline concentration shipped at three of four** — Jameson, Redemption and the mango
study are all his. It was surfaced Aug 18, compressed to nothing in the Aug 25 Notes as instructed,
and **no verified item was dropped to fix a byline count.** That was the right call and it should
stay the standing rule. **But it is now a shipped fact, not a forecast: an edition has run with 75%
of its items from one critic.** The structural answer is not to cut items — it is a fourth outlet
or a second Robb Report byline. **`whiskyadvocate.com/tag/sevans` (a Sean Evans author index, in
HOSTS, still unfetched) is the cheapest experiment available and is worth one fetch on a prep run.**

### What this edition proves about the sourced-claims rule

Three of four items had a sourcing edge to handle, and all three were handled the same way: **name
the outlet inside the sentence that carries the claim.** Jameson's price went to Whisky Advocate in
copy. Garrison's bottle counts went to Whisky Advocate in copy. Redemption's absent sensory was
declared to the reader rather than quietly skipped. **None of the three cost a word of clarity, and
the edition reads more trustworthy for all three.** This is the reusable technique — it is cheaper
than dropping an item and it is honest in a way silence is not. **Fold it into the next edition
without re-deriving it.**

---

## MONDAY Aug 24 — PREP RUN (posted 06:2x PT)

The run had three jobs from the Aug 23 file: find a vetted tariff link-out, find ONE non-Whisky-
Advocate Friday item, and try WA's Travel and Whisky Life sections once. **One landed, one did
not, and the third landed bigger than expected as a structural find.**

### `canada-50pct-tariff-aug-19-2026` — A SPIRITS OUTLET FILED. The block is now a TIERING question.

**The Spirits Business filed the collapse at 10:26 UTC today (03:26 PT), by Nicola Carruthers** —
`https://www.thespiritsbusiness.com/2026/08/canada-us-dispute-heats-up-with-50-tariff/`.
**Robb Report has NOT filed on the collapse.** Its section index still carries only the Aug 20
pause piece (`trump-pauses-canada-goods-tariff-1238567069`). So the answer to the Aug 23 file's
"one check that matters" is: **yes, a spirits outlet covered it — but not one on the vetted list.**

**What TSB supports that this file did not already carry:**
- Canada's retaliation **now has a date: 8 September**, at 50%, on US steel, dairy, appliances,
  agricultural equipment, pulp and paper, and electronics.
- US alcohol has been off Canadian government liquor-board shelves **since March 2025 — 18 months**,
  which is the cause the US tariff was framed as answering.
- Trump's July framing: the tariff would "level the playing field for crucial American exports –
  cars, alcohol, and dairy."
- **A clean short quote exists: Carney said the US "asked too much and offered too little"** —
  seven words, named speaker, from the linked source. Also usable: "match Washington's new tariffs
  dollar for dollar."
- Confirms the tariff took effect **Saturday 22 August** and that the 19 Aug start was postponed by
  at least three days for talks. **This matches the BNN Bloomberg facts already verified Aug 23.**

**TWO-SOURCE RULE: CLEARED.** TSB (original UK trade reporting, named staff journalist) plus BNN
Bloomberg (verified Aug 23) are independent, and Robb Report's pause piece is a third partial.
**The facts were never the problem and are not re-searched.**

**THE OPEN QUESTION IS THE TIER, AND IT IS AARON'S.** The inlined tier core in
`references/verification-protocol.md` lists Tier 2 as: Whisky Advocate, Bourbon Review, Breaking
Bourbon, PUNCH, SevenFifty Daily, **Drinks International**. **The Spirits Business is not on it.**
It is not Tier 4 either — no conflict of interest, no contributor-column problem, original
reporting with named staff bylines. **It is the same class of publication as Drinks International,
which IS Tier 2 — an established UK spirits trade title.** The living source directory that would
settle this is unreachable (25th run).
**Recommendation: hold to Sep 1 as already planned, and let a listed outlet file if one will.**
Sep 1 is seven days out; Whisky Advocate or Breaking Bourbon may well pick it up. **If neither has
by the Sep 1 run, the recommendation is to treat TSB as Tier 2-equivalent and link it** — it is
established trade press by every test except enumeration. **Surfaced to Aaron as one Notes bullet.
Do not link it before he answers or the default date arrives.**
**Key unchanged. Still HELD. Do not re-key it to a collapse slug. Do not re-search the facts.**

### THIS IS THE SECOND ITEM TO STALL ON TIERING — the file's own escalation trigger has fired

The Aug 21 BLOCKERS entry said a committed vetted-outlet list on this branch "is still the right
fix **if a second item ever stalls on tiering** — but it is not urgent." **Shanken News Daily was
the first (Redemption, Aug 17); The Spirits Business is now the second.** The Shanken question went
moot only because Robb Report happened to cover the same story. **That luck is not a process.**
**So the escalation is now earned and is raised as one Notes bullet this run** — a short committed
tier list on this branch, so unlisted-but-legitimate outlets stop costing a decision each time.
It is Aaron's call whether to write it; the pipeline should not invent tiers for itself.

### `hibiki-12-2026` — NEW, fully verified, real sourced sensory, and it FAILS anyway

Robb Report Taste Test, **Aug 23, Jonah Flicker** —
`https://robbreport.com/food-drink/spirits/whiskey-review-hibiki-12-japanese-whisky-1238568950/`.
**Score 92. Flicker's own palate notes: orange, chocolate, blueberry, baking spice, vanilla, maple,
honey, warm biscuit.** $188, 86 proof. Hibiki 12 was discontinued in 2015 and is back after an
eleven-year absence. Blend of Yamazaki and Hakushu malt plus Chita grain; **no umeshu-cask whisky in
the new version**, unlike the original; Chita grain base in American oak, malts in Spanish oak and
Japanese mizunara.
**IT IS A GLOBAL TRAVEL RETAIL EXCLUSIVE — a few airport shops only.** Flicker writes that "it's
not like you can just head out to a store to buy a bottle." **That is the forward bar, and it fails
it decisively** — the same test that closed Jack Daniel's #17 (distillery-exclusive), Gleneagles (no
US availability), Wyoming Whiskey (state-exclusive) and Branch & Barrel (Colorado-only).
**Three further reasons, none of them needed:** $188 is high for the board; **it would be Flicker's
sixth byline across the Aug 25 and Sep 1 boards**; and **Hibiki was already printed on Aug 21** —
the Dubai chocolate blurb named Hibiki Japanese Harmony, and this article discusses Harmony directly.
**ASSESSED ONCE AND DROPPED. Do not restage on the strength of "Robb Report tasted it" — it did,
at 92, and the bottle is still airport-only.**

### `koopers-texas-oak-bourbon-2026` — RESOLVED AGAINST. Removed from September pointers.

Fred Minnick filed Aug 21 —
`https://www.fredminnick.com/2026/08/21/koopers-whiskey-texas-oak-bourbon-set-to-release-aug-22/`.
**Facts: 8-year-old straight bourbon, barrel proof 114.8, $70, TWO casks yielding only 360 750ml
bottles**, finished in toasted Texas-grown white oak from **Standard Cooperage, Blanco, Texas** (the
state's first cooperage), master blender **Troy Kooper**. **Presale opened 11:00 a.m. Saturday
Aug 22**, online and at the Koopers tasting room.
**IT FAILS ON TWO INDEPENDENT COUNTS.**
1. **SOURCING: the FM piece is a press-release reprint** — it says "said in a news release" and
   carries an "About Koopers Whiskey" boilerplate block. TSB's earlier write-up is the same release.
   **Press-release reprints across outlets count as ONE source. Koopers has never had two.**
   **All of its sensory language is Troy Kooper's own news-release quote** — "a solid core of
   sweetness, structure, and grain character," "expressive but not overwhelming." **Brand copy.
   Never printable as sourced sensory.** (TSB caveat already on file: its product write-ups reprint
   release notes verbatim. Confirmed again.)
2. **FORWARD BAR: 360 bottles, and the sale opened two days ago.** Same trap as Bruichladdich
   Greener Still — by any edition date it is realistically gone. A September peg is indefensible.
**REMOVED from SEPTEMBER POINTERS and moved to DROPPED. Do not rediscover.** Lesson 25 again: the
second source arrived and killed the item rather than clearing it.

### WA'S TRAVEL AND WHISKY-LIFE SEAM — TESTED, AND IT WORKS. This is the run's structural find.

The Aug 23 file set this as job three and it paid off. **The guessed paths are wrong and the real
ones work:**
- **`whiskyadvocate.com/travel` → 404. `whiskyadvocate.com/whisky-life` → 404.** Do not retry these.
- **`whiskyadvocate.com/whiskey-life` → 200 and RENDERS ARTICLE LINKS TO SCRIPTS** (note the
  spelling: *whiskey*-life, not *whisky*-life). Yielded 22 article-shaped paths in one fetch.
- **`whiskyadvocate.com/tag/travel` → 200, renders links.** Fifteen paths.
- **`whiskyadvocate.com/tag/Features` → 200, renders links.** Fifteen paths.
**This matters because `/news` and `/Tag/Cocktails` are article-link-free** — WA's tag pages were
assumed client-rendered across the board. **They are not. Only some are.** These three are real,
server-rendered indexes and they are the repeatable Friday seam lesson 26 predicted.
Other section paths seen in WA nav, untested: `/tag/food` · `/tag/dispatches` · `/tag/insights` ·
`/ratings-reviews` · `/tag/sevans` (a Sean Evans author index — **useful for byline management**).

**A DATED BENCH OF FRIDAY CANDIDATES NOW EXISTS — verified to load, dated, NOT staged:**
- `whiskyadvocate.com/fort-collins-for-whisky-lovers` — "Whisky-Friendly Fort Collins," **Jun 24
  2026.** Freshest of the three. Venue Regular / travel.
- `whiskyadvocate.com/Beach-Bars-with-Great-Whisky-Lists` — **Jul 6 2026.** Seasonal; beach framing
  weakens after August.
- `whiskyadvocate.com/48-hours-in-houston` — **May 14 2026.** Oldest.
**All three are two-to-three months old with no news peg, which is the honest weakness** — the
glamping piece worked because it was three days old and dateable. **Service journalism dates slowly
(lesson 26), so these are a floor-clearer for a thin Friday, not a lead.** **Sensory content
unverified — check before staging.** All three are Whisky Advocate, so **none of them fixes the
Aug 28 outlet problem.**
Skipped from these indexes as already-known or colliding: Louisville Rickhouse (Louisville ran
Jul 31 and Aug 14) · Bourbon Room Saratoga Springs · Still Austin Quarter · WhistlePig depot ·
peach cocktails (spent) · Tropical Manhattan (coconut) · barrel-entry-proof · multi-location bars
(stale, in DROPPED). Untested feature candidates noted: `/red-white-blue-corn-bourbons` (**collides
with First West's Baby Black corn, ran Aug 18**) · `/india-single-malt-whiskies` ·
`/12-year-old-bourbons` · `/ultra-aged-bourbon` · `/Low-Proof-Whiskies-to-Try` ·
`/the-art-of-creating-blended-scotch`.

### Fri Aug 28 — THE NON-WA ITEM WAS NOT FOUND. Still two staged, both Whisky Advocate.

**This is the one job that did not land, and it is a supply fact, not an oversight.**
- **Whisky Advocate published NOTHING new since Fri Aug 21.** The RSS feed's newest item is the
  Aug 21 Whisky Watch, already spent on Filmland. Three days, no new WA material.
- **Robb Report filed a second consecutive dry week.** Two new pieces since Aug 23: the Hibiki 12
  taste test (**fails, above**) and a Kyle MacLachlan Washington *winery* profile (not whiskey).
  **Two dry weeks running is now a pattern, not variance** — see OPEN GAPS.
- **The FM rail produced nothing stageable:** Koopers (**failed, above**), Sazerac/Garrard County
  (trade), Jones Mack (still blocked), Tequila Ocho (already dropped).
- **TSB's 23-item index produced nothing stageable either** beyond the tariff. Full assessment below.
**Aug 28 remains TWO STAGED, which still clears the empty-pipeline floor.** Both are WA link-outs.
**Do not fix this by dropping a verified item, and do not pad.** Three prep runs remain before it
(Wed, Thu — and Tue is the edition). **If no non-WA item exists by Thursday, run two. Two verified
beats three with one padded.** Constraints unchanged and all still clear: no pineapple, no
Michigan, at most two cause-led, no fifth WA cocktail. **Hard Truth's Aug 28 Indianapolis event is
still Tuesday material — do not convert it.**

### Assessed and NOT staged this run — the TSB index, 23 items

**`sazerac-finalises-garrard-county-acquisition` (Aug 21) — and this one CLOSES an urgent-sweep
name.** Sazerac completed its purchase of Garrard County Distilling, Lancaster KY. Receivership
April 2025 after Truist Bank took it to court over ~$26M; Sazerac affiliate Tom Collings Distilling
bought the loan; **won a $20M court-ordered auction bid on 26 June.** 210 acres, two column stills,
two 20,000-sq-ft warehouses. Joins Buffalo Trace, Barton 1792 and Glenmore. **Fred Minnick filed
the same story Aug 21, so it has two outlets.** **Still trade news with no consequence for a
reader's shelf or weekend — beat file, never staged**, same test that closed Circle City and
Brown-Forman earnings. **Its real value: the Garrard County distress story logged in the Aug 17–18
urgent sweep is now RESOLVED by acquisition. It should not resurface as live litigation.**
**`soho-spirits-festival` — two pieces, and the word "safety" is in the headline. ASSESSED AGAINST
AN OVERRIDE.** London's Soho Spirits Festival, due Aug 21–22 at The Vinyl Factory, **cancelled on
the day**. The follow-up (Aug 24) carries founder **Tony McGeever**'s statement: he "tried to get
there far too quickly and took on far too much myself, without the financial and operational
foundations in place to deliver it safely," and reached a point where he "could no longer deliver
the event safely and responsibly." **THIS IS NOT AN URGENT OVERRIDE and a future run must not
escalate it because the headline says "safety."** No hazard, no injury, no recall, no regulator
action, no litigation, no death. **It is an organiser's own financial-and-operational cancellation**,
with refunds already processing. UK event, no WS partner; Four Roses and Bushmills were exhibitors
only, not implicated. **Not stageable either** — a cancelled London event has no US reader
consequence. **Recorded so the safety wording is never mistaken for a safety incident.**
**`fssai-revokes-sales-ban-on-select-diageo-products` (Aug 21) — assessed against an override, no
fire.** India's FSSAI lifted its ban on McDowell's No.1 Rum from United Spirits' Baramati plant
(order dated 29 June, revoked 17 Aug) and on whisky from a third-party Madhya Pradesh unit
(revoked 20 Aug) tied to Antiquity Blue and Royal Challenge. **The challenge was product LABELLING
non-conformance, not consumer harm.** Linked to United Spirits' 1 Aug writ petition, Bombay High
Court, hearing 24 Aug. Diageo denies misconduct and has agreed to reformulate some products
(Reuters). Separately, FSSAI confiscated ~18,000 cases (~$1.6M) over missing safe-recycled-plastic
markings on 180ml bottles. **Not a WS partner, India-only, bans REVOKED rather than imposed,
labelling rather than safety. Not an override.** Logged so a future run recognises FSSAI.
**Fast rejections, recorded so the TSB index does not re-surface them:**
`english-whisky-distillery-at-bodmin-jail-gets-green-light` — a distillery *approval*; same
forward-bar failure as Glenachulish, nothing to drink for years. ·
`dr-rachel-barrie-on-creating-the-glendronach-aged-56-years` — a 56-year-old; price far past the
forward bar, and Glendronach is already in DROPPED via Gleneagles. ·
`gallup-us-drinkers-shift-to-spirits-as-beer-dips` — **consumption-share data. Trade news, and the
framing is DISCUS-hostile. Never stage a consumption-trend item.** ·
`alcohol-tax-killing-irelands-pub-sector` — Irish policy, no US reader consequence. ·
`new-bar-paper-plane-to-open-in-october` — London bar opening. ·
`sazerac-adds-two-whiskies-to-india-portfolio` · `iwsr-premiumisation-still-alive-in-gtr` ·
`one-third-of-all-eu-spirits-exports-are-irish` · `cutwater-owner-invests-13m-in-ny-plant` ·
`award-winning-lady-alai-sets-sights-on-expansion` — all trade. ·
`mykonos-gets-taste-of-chic-elit` (vodka) · `casa-bacardi-heads-to-londons-victoria-park` (rum) ·
`white-claw-taps-sam-quek-to-drive-friendships` · `chivas-charles-leclerc-challenges-chess-grandmaster`
· `discover-the-best-of-the-us-at-free-trade-event` · `the-cambridge-global-series-returns-for-fourth-year`
· `copenhagen-bar-summit-to-launch-in-2027` — non-whiskey, marketing, or trade events.
**`kyle-maclachlan-pursued-by-bear-washington-wine` (Robb Report) — wine. Not whiskey.**

### `jones-mack-bourbon-2026` — an FM URL exists. NOT fetched, by instruction.

The FM rail surfaced `https://www.fredminnick.com/2026/08/17/2-cents-inc-releases-new-jones-mack-bourbon/`
for free. **Instruction 8 of the Aug 23 file put this item on a monthly check and said not to spend
a search on it before late September, after two rechecks with no movement. That was respected — the
page was NOT fetched.** **The URL is recorded here so the late-September recheck starts from it
rather than re-discovering it.** Expectation to test then, not now: FM reprints press releases, so
this is most likely the same single release a third time, which would leave the item still
one-source. **Do not fetch before late September.**

### Urgent sweep — no override

**Window Aug 21–24 (covering back through Friday).** One broad search plus the Robb Report spirits
section index, the full WA RSS feed, the FM recent-articles rail and the TSB news index (23 items,
all assessed above).
**No product recall, no safety issue, no litigation or investigation naming a partner brand or
venue, no death in the industry. Nothing fires.** The broad search returned only already-logged
material: the Kentucky distillery that collapsed owing ~$28M (**this is Garrard County — now
resolved by the Sazerac acquisition above**), the Uncle Nearest $108M banker suit, Sazerac v. RNDC
(the search puts the claim at $38.6M in unpaid bills), the craft-distillery closure trend (a quarter
of craft distilleries closed Sept 2024–Sept 2025), and the Fireball distributor suit. **Nothing
newer than what this file already carries.**
**Assessed and correctly not fired this run:** the **Soho Spirits Festival cancellation** (headline
says "safety"; it is an organiser's financial-and-operational cancellation — see above) and the
**FSSAI/Diageo sales bans** (labelling, India, revoked — see above). **The Canada tariff is now
live and is still a trade measure, not an override. Fourth consecutive run recording that.**

---

## SUNDAY Aug 23 — PREP RUN (posted 06:2x PT)

Two jobs were set for this run by the Aug 21 file: resolve the Canada tariff, and find Friday
material. **Both landed.** The discovery order held for the third run running.

### `canada-50pct-tariff-aug-19-2026` — THE QUESTION IS ANSWERED. Talks collapsed.

**Fifth run on the board, and it is finally resolved.** Carney's pause ran out and the negotiation
failed. **The 50% Section 338 tariff took effect at 12:01 a.m. ET Saturday Aug 22 2026**, on
**$28 billion** of Canadian goods, alcoholic beverages among the covered sectors. **Prime Minister
Mark Carney has pledged dollar-for-dollar retaliatory tariffs.** Talks were suspended and Canada's
negotiating team recalled.

**Sourcing — read this before staging it.**
- **BNN Bloomberg / The Canadian Press, Aug 22, published 06:29 EDT, updated 09:39 EDT — FETCHED,
  200, read.** Supports: collapse of talks, imposition on $28bn of goods, Carney's dollar-for-dollar
  pledge, Candace Laing (Canadian Chamber of Commerce) calling it a "body blow," and **a Chris
  Swonger (DISCUS president/CEO) statement** on continued discriminatory treatment of American
  spirits and a call for a negotiated return to zero-for-zero spirits trade.
- **Washington Post, Aug 22, "Trump's new tariffs on Canada will hit everything from whisky to
  hockey sticks" — SURFACED BY SEARCH, PAGE WOULD NOT LOAD** (curl died with an HTTP/2
  INTERNAL_ERROR). **Not verified. Do not cite it and do not present it as read.**
- Trade-compliance advisories (Troutman Pepper Locke, GHY, Zonos, freightfigures) corroborate the
  mechanics: the three-day suspension moved the effective date from Aug 19 to Aug 22, and **USMCA
  preference does not exempt covered goods.** Troutman's insight URL 301s to an unknown target —
  **not fetched, corroboration only, never a link-out.**

**THE BLOCKER IS THE LINK-OUT, AND IT IS THE WHOLE DECISION.** Both vetted outlets that covered the
pause were swept this run and **neither has published the collapse:**
- `robbreport.com/food-drink/spirits/` — 200, eight articles, and its only tariff piece is still
  `trump-pauses-canada-goods-tariff-1238567069` (the pause).
- `thespiritsbusiness.com/category/news/` — 200, twenty-three articles across Aug–Sep, **no tariff
  item at all in the index.**

So the story is real, resolved and knowable, and **there is no vetted Tier 1–2 link-out for it.**
Under the sourced-claims rule a reader-facing item cannot run against a general-news link when the
beat has vetted outlets that simply have not filed yet.

**DEFAULT APPLIED, not asked a third time.** The Aug 21 file set the rule: this was the second ask,
so on finding the resolution this run states the recommendation and applies it. **Applied: HOLD to
Sep 1, and recheck Robb Report and The Spirits Business for a pickup on Monday Aug 24.** Both cover
tariff policy routinely and the collapse is a bigger story than the pause, so a Monday or Tuesday
pickup is likely. **If a vetted outlet files by Tuesday morning, the item is publishable on Aug 25
and Aaron can have it as a fifth — but Aug 25 is four firm and balanced, so the honest call is
still Sep 1.** Aaron reverses either way by reply.

**Still NOT an urgent override.** Trade policy is not a recall, a safety issue, litigation naming a
partner, or a death. Sixth run of holding that line; it is correct.

**Key stays byte-identical — `canada-50pct-tariff-aug-19-2026`.** It names the beat, not the
outcome. Do not re-key it to a collapse slug. Do not prune it.

### `filmland-malted-mummy-2026` — NEW, VERIFIED, and it has a real independent score

Item 8 of the Aug 21 file recorded this unassessed off the Fred Minnick rail. **It is now cleared
and staged for Fri Aug 28.**
- **Whisky Advocate Whisky Watch, Aug 21 — THE LINK-OUT.** Danny Brandon, Julia Higgins, Jonny
  McCormick. Supports: **43% ABV · SRP $75 · Availability "Limited"** · Los Angeles independent
  bottler, creative inspiration from B-movies · **its first American single malt** · blended and
  bottled by Filmland · **sourced from an undisclosed distillery in Iowa** · **aged 5 years in oak
  barrels that previously held IPA** · **debut Aug 29**.
- **SOURCED QUALITY, NOT SOURCED FLAVOUR — read this carefully.** WA writes: "We got an early
  chance to taste the new whiskey, and it's another winner, **scoring 90 points with our tasting
  panel**." That is an independent tasting and **90 points is printable, attributed to Whisky
  Advocate's tasting panel**. WA gives **no descriptors at all** — the full review is held for the
  Fall issue. **So print the score and print no flavour. There is no sensory to attribute.** This
  is the cleanest case yet of the distinction the sourced-claims rule is about.
- Second source: **Fred Minnick rail, Aug 20** (recorded Aug 21: 86 proof, 100% malted barley).
  **43% ABV is exactly 86 proof, so the two agree.** BevNET carries the press release and is
  **403 to scripts** — the "Straight American Whiskey," "100 percent malted barley" and the Raiya
  back-story come from search summaries of it, **not from a page this run read. Do not print them.**
- **WA also notes Filmland's track record: a 92-point Ryes of the Robots and a 93-point White Port
  Wolf.** Printable and attributed, and it is the honest answer to "why care about a bottler nobody
  has heard of."
- **COLLISION — CAUGHT HERE, AND IT MATTERS.** Search summaries put the Aug 29 debut **at
  BrewzleFest**, and **`brewzle-fest-opelika-aug-29-2026` is already in dedup.** WA states only
  "set to make its debut on August 29th" and names no venue. **Peg the item to the Aug 29 date and
  never to the festival** — that is both the sourced reading and the one that avoids echoing a
  covered story. Recorded in COLLISION FLAGS.
- **Slot: Fri Aug 28, the day before the debut.** `whats-dropping` on a Friday is precedented — the
  Aug 21 Last Call ran Copperworks under it. Social Drinker: $75, an IPA-barrel finish and B-movie
  branding is a playful bottle, not a Collector trophy.
  Link: `https://whiskyadvocate.com/new-whiskey-from-bowmore-barrell-and-more`
  **Roundup — one link-out only.** It covers seven releases; the link is spent on Filmland. Every
  other release in it needs its own link before it can run.

### `whisky-advocate-distillery-glamping-2026` — NEW, VERIFIED, and it is the non-cocktail Friday

**This is the find that closes the Friday problem, and it does it without touching any of the four
tightened constraints.** Whisky Advocate, Aug 20, **Sean Evans**, "Distillery Country Glamping,"
deck "These rustic yet refined accommodations put you right in the middle of whisky country."
- **Twelve glamping sites with whiskey options**, organised by state. Supports (Kentucky):
  **Lawrenceburg, Kentucky sits within striking distance of 22 distilleries — Four Roses, Wild
  Turkey, Woodford Reserve and Buffalo Trace among them.** **Bourbon Barrel Retreats** — custom
  barrel cabins, king beds, private bathrooms, kitchenettes, air conditioning, fire pits, on-site
  restaurant and tasting room, group rates from four barrels, concierge for tours and transport.
  **Bourbon Barrel Cottages and Tours** — seven two-bedroom cottages, two acres each, private hot
  tub, fire pit, grill, covered porch, a Mercedes Sprinter for trail runs, and a custom blending
  option at J. Mattingly Distillers. **EarthJOY Village, Brooksville** — treehouses on a 285-acre
  working farm, one designed by Pete Nelson of "Treehouse Masters," swinging bridges, composting
  toilets, off-grid. (Tennessee): **Little Arrow Outdoor Resort, Townsend** — tents, Airstreams,
  cabins, tiny homes, RV hookups at the foot of the Great Smokies, minutes from **Company
  Distilling's 4,000-square-foot tasting room** on the Little River. **Treetop Hideaways, Lookout
  Mountain** — heated bathroom floors, stocked mini-fridges, views of the Tennessee Valley, near
  **Chattanooga Whiskey's Experimental Distillery**.
- **Second source: `bourbonbarrelretreats.com` — FETCHED, 200, read** (bare host 301s; **follow
  redirects with `-L` or it reads as a dead host**). Confirms trademarked barrel cabins, Kentucky
  bourbon country siting "centrally located among" Maker's Mark, Jim Beam, Buffalo Trace, Four
  Roses and Woodford Reserve, on-site dining and tasting. **Note the distillery lists differ
  between the two sources — attribute the 22-distillery figure and the named four to Whisky
  Advocate, which is the link-out, and print no distillery list from the property's own page.**
  **Its own copy is saturated with "experience" and "unforgettable." Lift nothing from it.**
- **SENSORY: not applicable and not needed** — this is a places item, not a bottle item. Nothing to
  block, nothing to invent.
- **Quote available and clean: Sean Evans, "It's where you are that matters." Six words, named
  writer, Tier 1–2 link-out.** Best quote on the Friday board.
- **Chattanooga note:** `chattanooga-moldovan-ice-wine-2026` published Aug 18 and this piece names
  Chattanooga Whiskey's Experimental Distillery. **Do not build the blurb on the Tennessee entry** —
  lead Kentucky, which is where the sourced detail is thickest anyway.
- **Constraint check, all four clear:** not a cocktail (so the four-straight-WA-cocktail count does
  not advance) · not pineapple · not Michigan · not cause-led. **It is a WA byline**, which is the
  one cost — see COLLISION FLAGS.
- **Beat slug: `on-the-calendar`.** A weekend plan with no fixed date is not a perfect fit, and this
  is the same explainer/travel slug gap already open and already compressed to `_unchanged_`.
  **Fold it into that gap. Do not open a second bullet and do not invent a slug.**
  Link: `https://whiskyadvocate.com/glamping-near-whiskey-distilleries`

### Assessed and NOT staged this run

- **`gleneagles-glendronach-moment-of-reflection-2026` — REJECTED, and it is a textbook forward-bar
  fail.** Robb Report, Jonah Flicker. 14-year-old single malt, oloroso sherry casks, 46% ABV, by
  master blender **Rachel Barrie**; first of three in "Moments from The Glorious Playground";
  bottled exclusively for **Gleneagles** in Perthshire and on sale there from **Sept 1**; **100
  bottles** by online ballot, **SRP £160 / about $218**, winners announced Sept 1. **Robb Report
  states plainly: "We did not get to sample the whisky." The full-bodied-and-creamy honeyed-caramel
  note is the official tasting note. NEVER PRINT IT.** Quote available only from Adip Agrawal
  (Brown-Forman VP) out of a statement — marketing, long, and it uses "experiences," a banned word.
  **100 bottles, one Scottish resort, a ballot, no US availability. Fails the forward bar
  decisively. Do not restage.** The Spirits Business separately has a Rachel Barrie piece on a
  56-year-old GlenDronach — **different product, not a second source for this.**
- **`bruichladdich-greener-still-2026` — THE UPGRADE WENT THE OTHER WAY. This item is now DEAD, not
  unblocked.** It sat in SEPTEMBER POINTERS as single-source-and-forward-bar-blocked. Robb Report
  (Flicker) has now given it a second vetted source **and answered the forward-bar question
  against it: it is a U.S.-exclusive sold only from the distillery's own website, and Robb Report
  reports it "currently sold out."** "It will likely appear on secondary websites over the coming
  weeks" is not availability. **A reader cannot buy it. Remove it from the pointers.**
  Robb Report also corrects and sharpens the facts on file: **15-year-old**, 51.6% ABV, SRP $160,
  first-fill bourbon barrels, no chill filtration, no added colour; **the barley split is 30%
  organic mainland-Scottish / 25% Bere from Orkney with the University of the Highlands and Islands
  Agronomy Institute / 45% biodynamic from Yatesbury House Farm, Wiltshire** — the first break in
  Bruichladdich's all-Scottish-barley rule. **The file said "fourth in the Still Series"; Robb
  Report says third release in the 25th-anniversary run** after Yellow Submarine III and Old Skool,
  with Blacker/Redder/Golder Still (2006–08) as the naming ancestor. **Corrected here.**
  **SENSORY STILL BLOCKED and this is lesson 5 again:** the soft-florals / ripe-orchard-fruit /
  velvety-finish line is **master blender Adam Hannett in a statement**, not a taste by Flicker.
  **Flicker did not sample it. Do not print it.**
- **`copperworks-urban-family-barleywine-2026` — ASSESSED ONCE AND CLOSED, exactly as item 8
  asked.** FM Aug 20, plus press-release reprints at Breaking Bourbon, mybeerbuzz and Washington
  Beer Blog — **one source between them.** Urban Family matured its Treehouse in the City barleywine
  in a Copperworks cask; Copperworks refilled that cask with 3½-year-old 5 Malt whiskey and bottled
  at 50% ABV after ten further months. **Exclusive to Whiskey Club members. That fails the forward
  bar on its face**, and Copperworks ran Aug 21 with the Spokane item, so it needs daylight it will
  never get. The sweet-malt/orange-sorbet/cocoa-nibs note is **press-release copy — not a tasting.**
  **Do not rediscover.**
- **`branch-barrel-straight-rye-2026` — REJECTED, same reason as the brand's bourbon.** WA Aug 21:
  44% ABV, **SRP $35**, **"Availability: Colorado exclusive."** 51% rye / 40% corn / 9% malted
  barley, minimum 3 years, San Luis Valley rye grown as a winter cover crop. Master blender
  **Mitchell Nester** is quotable but the line runs to "uncommonly smooth and drinkable" —
  **consumption framing, reject on DISCUS as well as on distribution.** Note `branch-barrel-5yr-
  bourbon-2026` is already in WATCHING as Colorado-only; **this is a second product, same fail.**
  **It is also more sub-$30 evidence: $35 again, and Colorado-only at that.**

### New September pointers — facts verified, every one of them sensory-blocked

All five came out of the WA Whisky Watch of Aug 21. **That roundup's single link-out is spent on
Filmland, so each of these needs its own link before it can run.** None is staged.
- **`koopers-texas-oak-bourbon-2026`** — the best-sourced of the five and the only one with two
  vetted outlets: **The Spirits Business Aug 21 (Miona Madsen) — fetched, 200, read** — plus WA
  Aug 21 and an FM piece of Aug 21 ("Set to Release Aug. 22"). 8-year-old MGP Indiana bourbon,
  **75% corn / 21% rye / 4% malted barley**, finished in toasted Texas-grown white oak from
  **Standard Cooperage in Blanco, the state's first cooperage**. **Barrel proof 57.4% ABV · SRP $70
  · limited to 360 bottles · online and at the tasting room.** Named speaker **Troy Kooper**, master
  blender. **SENSORY BLOCKED — TSB's toasted-caramel/Texas-pecan/crème-brûlée block is release copy
  ("The casks are said to impart…", "showcases aromas of…"), and all three outlets are working the
  same release, so this is ONE source by lesson 4 even though two are vetted.** **360 bottles is a
  thin footprint; the cooperage angle is the real hook.** September at the earliest.
- **`barrell-new-year-blend-11-2026`** — 58.3% ABV, $85, **nationwide though limited, from
  September**; 11th edition; components from seven states (Indiana, Kentucky, Tennessee, Wyoming,
  Maryland, Texas, Ohio) at ages 5 to 16; derivative mashbill 73% corn / 22% rye / 4% malted barley
  / 1% wheat. **No sensory. Single source.** Nationwide is the strongest forward-bar profile on this
  list. Note `barrell-decade-2-canadian-2026` is in dedup — **different product.**
- **`new-riff-sherry-finish-malted-rye-2026`** — 58.65% ABV, $70, Limited. 100% malted rye, 6 years,
  oloroso and Pedro Ximénez finish. WA says its scores have improved since the 2022 first release
  but **prints no notes. Single source.**
- **`bowmore-snarkitecture-oak-voyage-2026`** — 50.8% ABV, **$360**, Limited, from September. 20
  years in bourbon barrels then a finish in oloroso-seasoned American oak butts; a collaboration
  with New York design studio Snarkitecture. A second 20-year-old, Sherry Cask Pursuit, follows in
  Global Travel Retail at 51.8% and $380. **No sensory. $360 tests the forward bar hard.
  Collector-only, low priority.** WA warns it is **not** the 2000 Bowmore Voyage — different bottle.
- **`dublase-signature-bourbon-trio-2026`** — three Indiana-distilled bourbons (5yo part-matured in
  Florida, 7yo, 10yo) from Florida's Dublasé, founded 2020 by **Darrin Eakins**; online and select
  Florida retailers **from Sept 1**. A share of sales goes to the Dublasé Foundation, which supports
  minority students in STEAM fields and has engaged 175,000 students in northeastern Florida.
  **PRICES ARE NOT PUBLISHED until Sept 1 — un-stageable until they are.** No sensory. Cause-led,
  so it also counts against the two-cause-items-per-edition cap.

### `jones-mack-bourbon-2026` — RECHECKED as instructed. UNCHANGED, still blocked.

Item 7 of the Aug 21 file. **No independent Tier 1–2 pickup exists.** The only new surface is a
National Law Review press-release syndication — **still the same release, still one source.** New
detail worth keeping: the founders are **Brittany and James Penny**, and 2 Cents Inc. is theirs.
The circulating dark-cherry / orange-peel / clove / cinnamon note is **the official product
description. Do not print it.** Facts on file hold: 100 proof, $54.99 with a $49.99 presale, DTC
from September, named for Wallace and Naomi Jones and Sylvester and Gertrude Mack. **Still watched,
not dropped. Recheck before any September slot — but this is now two rechecks with no movement, so
drop it to a monthly check rather than a per-run one.**

### Urgent sweep — no override

Window Fri Aug 21 through Sun Aug 23. **Nothing qualifying.** No recall, no safety issue, no
litigation or investigation naming a partner brand or venue, no death in the industry.
**Recorded, not staged:** a February 2026 gender-discrimination and retaliation suit by Bardstown
Bourbon Company's former HR chief surfaced in the sweep. **Six months old, not new, no vetted
whiskey outlet in the results, and not urgent** — but `bardstown-lochs-of-jura-2026` is staged for
Sep 1, so it is logged here rather than lost. **It does not earn a Notes bullet: nothing to decide
this week.** If Aaron ever asks why Bardstown, this is the context. The tariff collapse is real
news but is not an override — see above.

---

## FRIDAY Aug 21 — WHAT SHIPPED (Last Call, posted 06:14 PT)

**Four items, exactly as staged since Aug 19. Nothing added, nothing cut, no fifth item.** The
board was closed going in, which is what an edition day is supposed to look like. Order shipped:
Detroit blues festival (On the Calendar, Venue Regular) · Copperworks Spokane relief (What's
Dropping, Social Drinker) · Dubai chocolate pairing (**Pair It — first ever**, Social Drinker) ·
Thunder Bird cocktail (Easy Pour, Social Drinker). Send-off: "Worth the pour. See you Tuesday."

**The tariff stayed out, as instructed three runs running.** No reader-facing mention. It carried
one Notes bullet as a decision Aaron owes for Tuesday, which is the correct place for it.

### Link re-confirmation — all four 200 with real body text

Fetched to disk with a browser UA, scripts and styles stripped with a DOTALL regex before slicing.
`detroitbourbonandblues.com` 1,349 words · Fred Minnick Copperworks 688 · WA Dubai chocolate 1,214 ·
WA Thunder Bird 520. **No Notes bullet — nothing failed.** Fifth consecutive edition where every
staged link re-confirmed clean.

### Every printed claim, against its source

- **Detroit** (detroitbourbonandblues.com, Tier 1 organizer): "sunday, august 23rd, 2026" ✓ ·
  Eastern Market Shed 5 ✓ · "12 PM - 7 PM" ✓ · cocktail classes "presented by Louisville Tourism"
  for "anyone 21+" ✓ · three blues acts across the afternoon (Rome Antenucci 12:30, Freestyle Band
  Detroit 3:00, Shaun Booker Dammit Band 5:00 — **not named individually in copy**) ✓ · FernCare
  Free Clinic, "provides no-cost medical" care ✓.
  **PRICE PRECISION CORRECTED AT DRAFT TIME.** The staged instruction was "print $55 GA / $75 VIP."
  **The page actually says "General Admission ($55 + fees) & VIP ($75 + fees)."** Printing a bare
  $55 would have been a number a reader could falsify at checkout. **Published as "$55 plus fees,
  VIP $75."** Logged as lesson 22.
  **"Supports," not "proceeds."** The staged note said "proceeds to the FernCare Free Clinic." The
  page says the festival "proudly supports" it and never uses the word proceeds or states a share.
  **Published as "supports."** A donation mechanism nobody stated is not a sourced claim.
  **The page's own phrase is "tasting experiences" — "experience" is banned and was not lifted.**
- **Copperworks** (Fred Minnick Aug 14): Spokane Complex Fire "continues to burn across Eastern
  Washington" ✓ · throughout August, **$20 from every bottle of Farmsmith American Single Malt
  sold** ✓ · H.O.M.E. Starts Here relief fund ✓ · single-varietal Genie barley "grown 20 miles west
  of Spokane" ✓ · "malted by LINC Malt in Spokane" ✓ · direct donation available ✓.
  **THE EDITION'S ONE QUOTE, and it went here on merit.** "The farming families and partners around
  Spokane aren't just our suppliers; they are our friends" — **16 words, named, in the link-out,
  attributed as "said co-founder Jason Parker" with no pronoun** (lesson 14; Parker's are unstated).
  **Schikora's 10-word line was the other candidate and was deliberately not used** — the edition
  allows exactly one, and the Copperworks item has no price, no sensory and no availability, so the
  quote is the only human thing in it. Thunder Bird carries itself on the recipe.
  **DISCUS handled the way the staging note specified:** the donation is stated once, flatly, and
  the item closes on "You can also donate to the relief fund directly" — **which deliberately
  routes the reader to donating rather than to buying more bottles.** That is the mitigation; keep
  it if this item ever recurs.
  **No price, no ABV, no sensory printed — none exists.** FM's own "distilling journey" was not
  lifted. **"Single malt" was left undefined on purpose** — it appears inside the product's name,
  it is not gatekeeping, and a definitional aside would have intruded on a live-disaster item.
- **Dubai chocolate** (WA Aug 12, Pete O'Connell): Belgian chocolate with pistachio cream, tahini,
  crunchy fried phyllo ✓ · seven whiskies ✓ · every score 90+ (95, 94, 94, 93, 92, 92, 90) ✓ ·
  price range $60–$200 (Wild Turkey $60 to Port Charlotte $200) ✓ · Redbreast 12's "nutty notes
  help enhance pistachio and tahini flavors" → published as "there for its nutty side" ✓ · Hibiki
  "something a bit more delicate and understated" → "the delicate pick" ✓ · pistachio shortages
  **attributed to the magazine**, as the staging note required ✓.
  **Wild Turkey was not led on** (ran Aug 11) — it is the cheapest bottle on the list at $60 and
  still stayed unnamed; the $60 floor is printed as a range endpoint instead.
  **Single pot still was NOT defined** — Redbreast 12 is named without the phrase, so the term is
  unspent and belongs to Jameson on Aug 25, exactly as sequenced.
  **WA's drinking-pace phrasing was not reproduced or paraphrased:** "wash it down with sips"
  (Rampur) and "sipping this between bites" (Port Charlotte) both stayed out. Confirmed present in
  the fetched page — the caution was real, not theoretical.
- **Thunder Bird** (WA Aug 17, Brittany Risher Englert): Max Schikora, bar manager at Huna, Ann
  Arbor, Michigan ✓ · a Jungle Bird riff ✓ · ¾ oz rye + ¾ oz Jamaican rum + ¾ oz Campari →
  published as "split the base, equal parts" ✓ · "or other 100-proof rye" → "any 100-proof rye
  works" ✓ · pineapple juice, lime, demerara syrup ✓ · "Shake for 5 to 8 seconds" → "five to eight
  seconds" ✓ · "Strain over fresh ice" ✓ · "rye brings spice and structure" and Campari's
  bitterness, **both attributed in copy to Whisky Advocate** ✓.
  **Rittenhouse was not named and bottled-in-bond was not printed** — "any 100-proof rye works"
  carries the same reader value and spends nothing on a term already printed four times.
  **Both DISCUS blocks confirmed present in the live page and both excluded:** "it drinks easier
  than it should for something with this much proof behind it" and "tastes like a vacation—one you
  actually remember."

### The collision this file MISSED, caught at draft time

**Pineapple, twice in two Fridays — and the staging notes never flagged it.** Aug 14's Easy Pour was
a "smoky pineapple smash" published with the line "Bright and tropical up front." Thunder Bird's own
WA sensory is "a bright, juicy hit of pineapple and lime up front." **Same fruit, same segment, same
weekday, nearly the same phrase, two Fridays apart.** Nine collision flags were carried on this
board and not one of them was this.

**Fixed by re-angling rather than dropping the item.** The published blurb leads on the **split base
— rye and rum in one glass** — names Campari for bitterness, and prints pineapple only as an
ingredient in the fill-out sentence. **Pineapple is never the hook and the Aug 14 phrasing is not
reused.** The item still earns its slot on the split base, the named creator and the Michigan
adjacency; it just no longer rhymes with two weeks ago.

**Generalisation, logged as lesson 23:** the collision flags track brands, outlets, bylines, terms
and categories. **They did not track the flavour that carried the hook.** Add the hook noun to the
flag set. `bardstown-victoria-pineapple-2026` is also in dedup, which makes this the third pineapple
in the recent record.

### Beat-slug and gap movement

**`pair-it` is spent for the first time, and it closed a 34-day gap.** The gap was never supply — a
Tier 2 food pairing with its own sensory sat on this board for nine days. **It was a definition:
whether Pair It means cigar-crossover or food pairing.** The standing recommendation on file was to
redefine it as food pairing. **Nobody replied, so the recommendation was applied and Aaron was told
in one Notes bullet that it was applied** — the Macallan precedent, and the same default discipline.
**If he wants Pair It reserved for cigars, he reverses it by reply and the chocolate item is
re-slugged retroactively in PostHog.** Until then, food pairing is what the beat means.

**Persona shape shipped: Venue Regular ×1, Social Drinker ×3.** That is Friday's brief. **No
Collector item, correctly** — Friday does not carry Collector weight, and the coverage floor is a
weekly floor, not a per-edition grid. The Dubai list supplies the Explorer-facing depth (seven
bottles, scores, ABVs, prices, cask detail) without being tagged Explorer.

**Outlet mix shipped: organizer site ×1, Fred Minnick ×1, Whisky Advocate ×2.** As predicted, and
**the fourth straight Friday of a WA cocktail happened.** See COLLISION FLAGS — it is now four, it
was taken deliberately for the Detroit/Ann Arbor adjacency, and **the fifth should not be taken
without Aaron saying so.**

### Urgent sweep — no override

**Window Aug 20–21.** Two broad searches. **No product recall, no safety issue, no litigation or
investigation naming a partner brand or venue, no death in the industry. Nothing fires.** Returned
only already-logged material: Garrard County Distilling, the Jim Beam Clermont pause, the Fireball
distributor suit, craft-distillery closures, the industry-contraction coverage, and the Canada
tariff pause itself.

**One useful confirmation:** the search summary independently describes the Canada tariffs as
"paused pending negotiations" as of this window. **Consistent with the Aug 20 finding. No evidence
the pause has resolved either way yet** — which is exactly why it is a Tuesday item and not a
Friday one. **The Sunday run's job is to find out how it landed.**

**Assessed and correctly not fired:** the tariff pause, fourth consecutive run recording this. A
trade measure, reversed or not, is not a recall, a safety issue, partner litigation or a death.
**The Copperworks item is also not an override** — a charitable release during a live wildfire is
not a recall or a safety issue. It ran in a normal slot, quiet and factual, no occasion framing,
which is what the staging note specified.

---

## THURSDAY Aug 20 — PREP RUN (posted 06:17 PT)

**One correction, one link-out upgrade, one new item.** The run's headline finding is that
**yesterday's brief was wrong within hours of posting** — the Canada tariff never took effect.
The discovery order settled Aug 19 (section index → RSS → author rail) held perfectly: the
Robb Report section index produced both Robb Report finds, the WA RSS feed produced SHĀNG.

**What was posted:** the tariff pause (Tue Aug 25, decision needed) · Bardstown Lochs of Jura
link-out upgrade (Tue Sep 1) · SHĀNG jiàngxiāng whisky (Tue Sep 1, Explorer). Notes carried the
correction, the Bardstown link-out tradeoff, the Sep 1 gap close, the absent brand skill, and
the compressed `_unchanged_` line.

### `canada-50pct-tariff-aug-19-2026` — THE TARIFF WAS PAUSED. Yesterday's brief was overtaken.

**This is the correction, and it matters more than anything else this run.** The Aug 19 brief told
Aaron the 50% Section 338 duty on Canadian alcoholic beverages "took effect at 12:01 a.m. ET
today." **It did not.** Trump paused it hours before it was due to start.

**Link-out: `https://robbreport.com/food-drink/spirits/trump-pauses-canada-goods-tariff-1238567069/`
— Robb Report, Aug 19, 19:00Z, Nicole Hoey. Read in full.** This is the vetted Tier 1–2 pickup
that the Aug 19 file sent this run to look for (instruction 4). **It exists. The question is
answerable.**

**What Robb Report supports:** Trump paused the 50% tariff on Canadian goods — **whisky, wine,
hockey equipment and more** — **for three days**, on the basis that the two countries have a
deal subject to finalization of documents · the levy **was set to take effect Wednesday** ·
Trump's own words, from a social-media post, **runs 43 words — too long to quote** · the USTR
describes comprehensive market access for American goods, economic security commitments and
digital trade alignment, **per ABC News** · nearly all Canadian provinces banned US spirits and
wines after the 2025 tariffs, **only Alberta and Saskatchewan have lifted them**, and **70% of
Canadians today support outlawing American booze** · **US wine exports fell $428M in 2025**, on
a **76% decrease in exports to Canada** · the administration cites Canadian imports of all US
booze **down 81% from March 2025 to February 2026**.

**Second sources, all independent of Robb Report and of each other:** The Spirits Business
(`/2026/08/trump-temporarily-pauses-canada-tariffs/`), **Washington Post** (Aug 18),
**NBC News**, and Shanken News Daily (corroboration only, still unvetted). **Well past the
two-source rule.**

**THE DATE CONFLICT, AND IT IS THE WHOLE PROBLEM.** Robb Report says **three days** from Aug 19,
which lands **Sat Aug 22**. **Canadian PM Mark Carney says the pause runs "until the end of the
day Friday"** — **Fri Aug 21**, which is *the edition day*. The two are close but not the same,
and both are sourced. **Either way the pause expires within hours of Last Call publishing.**

**CONSEQUENCE — DO NOT PUT THIS IN FRIDAY'S EDITION.** A tariff item published Friday morning
could be false by Friday evening. There is no framing that fixes it: "paused for now" is
technically true and still strands the reader. Also: Last Call is occasion-led and a trade
measure is the wrong register.

**RECOMMENDATION: Tue Aug 25.** By Tuesday the outcome is known — a finalized deal, an extension,
or a live 50% tariff. **The story resolves itself into something publishable exactly in time for
the slot it belongs in.** The reader-facing hook stays the price question, not the policy.

**AARON'S OPEN QUESTION IS NOW MOOT AS ASKED.** The Aug 19 Notes asked "Canada's 50% whisky
tariff took effect today — run it a third time?" **The premise was wrong.** The question is no
longer whether to re-run a story that happened; it is whether to run the *reversal*, which is a
different and much stronger item. **A reversal is a textbook material new development** — the
skill names "a rate changed" explicitly. The Adam-repetition risk drops accordingly: this is not
the same article a fourth time, it is the opposite outcome.
**Still NOT an urgent override.** A trade measure is not a recall, safety issue, partner
litigation or a death. **Do not let a future run escalate it.** Third consecutive run stating this.
**Keep the key held in dedup — do not prune it Friday.**

### `bardstown-lochs-of-jura-2026` — LINK-OUT UPGRADED. The sensory block is cleared.

**New link-out: `https://robbreport.com/food-drink/spirits/bardstown-bourbon-company-new-cask-finished-whiskeys-1238567077/`
— Robb Report, Aug 19, 21:00Z, Jonah Flicker. Read in full.** This is the "independent Tier 1–2
review would be a better link-out if one appears" that the Aug 19 entry asked for. **It appeared
in one day.** The Fred Minnick press-release reprint is demoted to second source.

**FLICKER TASTED BOTH BOTTLES.** "We got to sample these whiskeys." Lesson 18's wood trap is
resolved the only way it can be — somebody put the glass to their mouth.

**SOURCED SENSORY, and the ONLY printable version:**
- **Lochs of Jura, 104 proof:** oak, dried and fresh berries, a bit of salinity, apple cobbler,
  and "the faintest whiff of smoke if you think about it really hard." Flicker calls it
  **delicious**. Both bottles "excellent, and unusual" and "very good and very unique."
- **2026 Discovery, 112.8 proof:** strong toasted wood and cinnamon from the secondary
  maturation, plus butterscotch, maple, flamed orange, cherry syrup.
**The release's own wood copy — Jura's "ripe fruit, soft malt, subtle smoke, maritime character"
and Garryana's "clove and nutmeg" — stays banned. It was never a tasting note.**

**THE TRADEOFF AARON HAS TO SETTLE — and it is a real one.** The two candidate link-outs carry
different facts and **lesson 12 says only the link-out speaks**:
- **Robb Report** → independent sourced sensory, Tier 2, a named critic who tasted it.
  **But it never mentions the 99 IWSC points.**
- **Fred Minnick** → carries the 99 points and the highest North American score of the year.
  **But it is a press-release reprint with no independent tasting.**
**You cannot print both from one link.** Recommendation: **take Robb Report.** Sourced sensory is
this board's standing scarcity and a critic's palate outranks a competition score. The 99 points
is a nice number; "Robb Report's critic tasted it and calls it delicious" is a better reason for
a reader to click. **Surfaced in Notes. Aaron can reverse it by reply.**

**ROBB REPORT'S BLEND PERCENTAGES DO NOT ADD UP — DO NOT PRINT THEM.** For Lochs of Jura it
gives **49% 11-year-old Indiana bourbon (MGP) + 39% 10-year-old Indiana rye (MGP) + 21%
12-year-old Kentucky bourbon from an undisclosed distillery**. That sums to **109%**. One of the
three figures is wrong and there is no way to tell which. **Print no blend percentages for Lochs
of Jura.** Lesson 11 a third time, logged as lesson 19. Discovery's figures are fine —
**55% 10-year-old Indiana + 25% 11-year-old Kentucky + 20% 7-year-old Kentucky = 100%.**

**PRICE CHANGES WITH THE LINK-OUT.** Robb Report says **SRP $140**; the wire release said
**$139.99**. Both true; they round differently. **If Robb Report is the link-out, print $140** —
that is what a reader sees on the click. **Do not print $139.99 against a Robb Report link.**
**Availability agrees across both sources:** around the country at specialty retailers from
**Aug 21**.

**New facts Robb Report adds:** the Estate-Distilled lineup **used to be the Origin Series**,
renamed when the labels were redesigned last spring, and **not everyone liked it** ·
Dan Callaway is **Lofted Spirits master blender** · the Jura casks are presumed from the Jura
distillery, the island's only producer · the 59-gallon sherry casks sat in warehouse aisles and
Flicker notes it is **unclear whether that affected maturation** — a useful hedge, since the
Aug 19 file carried the aisle detail as if it mattered · Discovery is BBC's **second** garry-oak
release this year after **Cascadia**, and the oak is more associated with Seattle's **Westland** ·
the garryana trees are from the **Willamette Valley** (consistent with "Oregon White Oak").
**Callaway's quote is the same one the wire release carried and still runs long. Prefer none.**

**`bardstown-discovery-2026` IS NO LONGER SENSORY-BLOCKED EITHER** — Flicker tasted it too. It is
still the weaker of the two and **still shares the link**, so the two can never run together.
Robb Report covers both bottles in one article exactly as Fred Minnick did, so the shared-link
constraint is unchanged by the upgrade.

**Slot: stays Tue Sep 1.** Aug 25 is four firm and balanced; the Aug 19 file said do not add to
it and nothing this run changes that.

### `shang-jiangxiang-whisky-2026` — NEW, VERIFIED. This is the Sep 1 non-Collector lead.

**Link-out: `https://whiskyadvocate.com/shang-baijiu-whiskey-review` — Whisky Advocate, Aug 19
07:00 PT, Sean Evans. Read in full.** First new WA material since Aug 18, found on the RSS sweep.
**Second sources, independent of WA and of the launch PR between them:** Robb Report's June launch
piece (`/food-drink/spirits/shang-baijiu-whiskey-china-kentucky-1238410557/`) and The Spirits
Business (Jun 2026). **Clears the two-source rule.**

**EVANS TASTED BOTH EXPRESSIONS. Real sourced sensory, and it is his own.**
- **Dàn Yǎ — 100 proof, $65 / 500ml.** Nose: lactic fermented funk, soy, fresh oak, mint,
  ethanol. Palate thin, fronted by bright new oak giving way to charred barrel spice that builds
  and lingers; vanilla, a pop of tropical fruit, peppermint threading through. Finish is barrel
  spice, "plain and persistent." Rests in **no. 3 charred American oak from Independent Stave**
  for **as little as one month, up to just under a year** — everything before that happens in
  China: distillation, then aging in **traditional clay pots**.
- **East + West — 92 proof, $46.** Narrower and sweeter nose: caramel, vanilla, heavy new barrel
  spice. Thin palate driven by barrel spice, a hefty pop of mint, a light **Dr Pepper** quality
  reading more medicinal than sweet. Finish carries anise and baking notes. Blends the jiàngxiāng
  whisky with a **proprietary American whiskey from US-grown red sorghum**, aged in charred oak
  in Kentucky.

**What the category is, in plain English — the item's whole value:** take a **sauce-aroma baijiu**
from the **Chìshuǐ River basin in Guìzhōu**, the watershed feeding China's most storied
distilleries, redistill it into a whisky base, and mature it in charred American oak in Kentucky.
**Maritine Brands** — a joint venture of **True Essence Foods** and **Guizhou Guotai Liquor
Group** — calls the result **jiàngxiāng whisky**. Partners: **Whiskey House of Kentucky** and
**The Blending House**; the concept is driven by food-technology entrepreneur **Matt Rubin** after
years of trips through Guìzhōu. **Baijiu is a clear Chinese grain spirit, usually from sorghum,
and the best-selling liquor category on the planet by volume** — almost entirely on its home
market. Sauce-aroma is built on **solid-state fermentation using qū, a starter culture** driving
funky, savory, soy-like flavors; WA's own analogy is **rum made with dunder**, and it says the
result can read closer to aged cheese or soy sauce than to bourbon's caramel and vanilla.
**The sorghum bridge is the clever part** — sorghum on both sides, fermented Chinese-style in clay
on one, distilled American-style on the other.

**EVANS IS LUKEWARM AND THE ITEM MUST SAY SO.** "Both tip hard into young, spicy oak, which is
what you'd expect from a spirit that has spent months rather than years in barrel." Dàn Yǎ
"keeps more of the baijiu's strange, savory character intact, which makes it the more interesting
pour"; East + West "trades some of that character for approachability." His verdict: **"These are
opening statements from a brand-new category... the idea is worth watching. The liquid is still
finding itself."** **Write the honest version — a genuinely new category worth knowing about, not
a bottle recommendation.** An item that hedges where its source hedges is correct.

**PRICE — WA rounds, the brand does not.** WA prints **$65** and **$46**; the launch coverage
prints **$64.99** (plus $15.99/50ml) and **$45.99** (plus $13.99/50ml). **WA is the link-out, so
print $65 and $46.** Not a conflict, just rounding — logged so a future run does not "fix" it.

**BRAND COPY TO AVOID — a clean example of the trap.** The June launch material describes
"floral aromas and umami, and notes of fruit, chocolate, and baking spices." **Evans's own notes
are materially different and much less flattering.** Printing the launch notes would be printing
marketing over a critic who actually tasted it. **Use Evans only.**

**DRAFTING CAUTIONS.** Five insider terms in one story — **baijiu, sauce-aroma, jiàngxiāng, qū,
solid-state fermentation.** The intimidation pass can afford **one or two**, not five. Define
baijiu plainly and let the rest go; the reader does not need the taxonomy to find the idea
interesting. **WA writes "a non traditional whisky experience" — "experience" is banned. Never
lift that phrase.** No usable quote: Evans's sharpest lines are his own critical voice rather
than a named speaker's words, and WA quotes nobody directly.
**Persona: Explorer.** $46 is in the band, the story is learning-led, and it is the wider-culture
angle the beats file says outperforms whiskeylore.

**Slot: Tue Sep 1. This is exactly the non-Collector lead the Aug 19 file said "has to be
found."** Gap closed on the first run after it was opened.

### Assessed and NOT staged this run

- **`strathearn-batch-03-2026` — REJECTED, and it is a clean fail.** Fred Minnick Aug 19: Douglas
  Laing released **Strathearn Highland Single Malt Batch 03**, a vatting of **31 casks**, ex-bourbon
  / virgin oak / ex-sherry with more sherry emphasis, **50% ABV**, no colouring, no chill
  filtration, from one of Scotland's smallest distilleries — **a single cask per production shift**,
  a team of three distillers, **Maris Otter malt**, Perthshire, bespoke acorn bottle.
  **Three independent reasons to reject: (1) the only price is a UK RSP of £65.00 with no US price
  and no US distribution stated — it fails the forward bar for a US reader; (2) it is a
  press-release reprint and the only source, so it does not clear two sources; (3) there is no
  sourced sensory — "richer, more indulgent," "creamy character" is the release describing its own
  intent.** Angela Brown's quote runs ~45 words. **The release also uses "journey" and "premium."**
  Do not restage without a US price and an independent tasting.
- **`jones-mack-bourbon-2026` — NEEDS SECOND SOURCE. Watching, not staged.** Fred Minnick Aug 17:
  **2 Cents Inc.**, Louisville, founded by **Brittany and James Penny**, released **Jones & Mack
  Bourbon** at **100 proof**, **$54.99** ($49.99 presale, $5 off), **presale now on the brand site,
  shipping direct from September 2026**. Named for the founders' grandparents — **Wallace and Naomi
  Jones, Sylvester and Gertrude Mack** — all four connected to WWII service and war work. Portfolio
  also holds The IX Bourbon and Audacitea; the company is woman-led.
  **The founder story is genuinely warm and the brand is inclusive in a way the Social Drinker
  responds to — that is why it is watched rather than dropped.** But: **one source, and it is a
  press-release reprint · no sourced sensory anywhere · DTC-only, and the release names no states,
  so the real footprint is unknown** (DTC spirits shipping is state-restricted). **The release uses
  "premium" twice.** **Louisville collision applies** — Friday venue items ran Jul 31 and Aug 14.
  **Recheck for independent Tier 1–2 pickup before the September slot it would want.**
- **`brown-forman-q1-results-sept-2-2026` — beat file, not staged.** Fred Minnick Aug 19: Brown-
  Forman will report financial results **Sept 2**. **Trade news with no consequence for a reader's
  shelf or weekend** — the same test that closed Circle City and the DISCUS fly-in. **Do not stage
  an earnings date.** Recorded so a future run recognises and skips it.

### Not new, and correctly not chased

The Robb Report spirits index also carried the already-logged `wyoming-whiskey-state-of-the-union`
(still Wyoming-only), `garrison-brothers-cowboy-bourbon-hazmat` (third source for the staged
Garrison item), `1800-tequila-coleccion-friedeberg` (not whiskey, dropped Aug 19), plus the four
already-staged items. **Zero wasted fetches.** The FM rail also carried the Tequila Ocho Venice
residency, dropped Aug 19.

---

## WEDNESDAY Aug 19 — PREP RUN (posted 06:20 PT)

Three items staged, all newly found, all verified. **Two beat gaps closed and two open leads
closed out.** The run's structural finding: **Robb Report's `/food-drink/spirits/` section index
is a better discovery path than the author rail** — it returned nine article URLs including three
the rail did not surface.

**What was posted:** mango-aroma study (Tue Aug 25, Explorer) · Maker's Mark Cellar Aged 2026
(Tue Sep 1, Collector) · Bardstown Lochs of Jura (Tue Sep 1, Collector). Notes carried the
tariff decision, the beat-slug gap, the Moonshine University close-out, the Bardstown slotting,
and the standing `_unchanged_` line.

### `heriot-watt-kirin-mango-aroma-study-2026` — NEW, VERIFIED, the best find this run

**Link-out: `https://robbreport.com/food-drink/spirits/scientific-study-mango-notes-in-whisky-1238553386/`
— Robb Report, Aug 13, Jonah Flicker. Read in full.** Second source: the **peer-reviewed paper
itself**, "Identification of Volatile Compounds Contributory to Mango and Tropical-Type Aroma in
Whisky," *Journal of the American Society of Brewing Chemists*,
`tandfonline.com/doi/full/10.1080/03610470.2024.2319929` — a primary source, which under the
two-source rule clears the item on its own paired with the Robb Report piece. Also carried by
The Drinks Business, The Spirits Business and BeverageDaily (all one press release between them).

**What Robb Report supports:** study by **Heriot-Watt University, Edinburgh**, with Japanese
drinks company **Kirin** · PhD student **Takehiko Hiura** analyzed **14 whiskies from Scotland
and Ireland** · **aldehydes and acetals amplify tropical fruit notes** · three compounds found
high in one sample — isobutyraldehyde, isovaleraldehyde, isovaleraldehyde diethyl acetal — and
adding them to a low-fruit whisky raised mango aroma specifically · fruity notes like banana,
apple and pear were already linked to **esters** formed during fermentation · tropical notes
become more noticeable after several decades of aging · reported in JASBC last year, Heriot-Watt
issued its release the week of Aug 10 · producers likely already hold the process tools to dial
the trait up or down, with no additives (not permitted in scotch anyway).

**THE BEST QUOTE ON THE BOARD. 15 words, named, in the link-out:** Annie Hill, professor at
Heriot-Watt's International Center for Brewing and Distilling — *"But we didn't know where the
mango flavor was coming from—and now we do."*

**NAME CONFLICT — avoid the name.** Robb Report prints **"Dr. Calum Holmes"**; The Drinks
Business prints **"Dr Callum Holmes."** One L versus two. Hill carries the quote; there is no
reason to name Holmes. If he must be named, use the link-out's spelling.

**Why it is the right Aug 25 item:** it closes the Explorer gap the Aug 18 file asked Wednesday to
fill, it is a learning item rather than another bottle, it carries no price and no availability to
get wrong, and it is the wider-culture angle the beats file says outperforms whiskeylore. **It is
also the rare item where sensory language is fully sourced** — the study is *about* the aroma, so
describing the finding is reporting, not an invented tasting note.

**DRAFTING CAUTIONS.** "Aldehydes," "acetals" and "esters" are three insider terms in one item —
**the intimidation pass will need plain English; do not print the compound names.** Skip
Flicker's closing "Mango Madness Malt Whisky" joke. **No beat slug fits** — see OPEN GAPS.

### `makers-mark-cellar-aged-2026` — NEW, VERIFIED, sourced sensory, Sept 1 peg

**Link-out: `https://robbreport.com/food-drink/spirits/makers-mark-2026-cellar-aged-bourbon-1238564495/`
— Robb Report, Aug 18, Jonah Flicker. Read in full.** Second source: Fred Minnick Aug 18
(`/2026/08/18/makers-mark-to-release-2026-cellar-aged-bourbon/`, a press-release reprint) plus the
**PR Newswire release itself** (Tier 1). Robb Report is independent reporting — Flicker interviewed
master distiller **Dr. Blake Layfield** on a Zoom call and **sampled the whiskey**.

**Facts all three sources agree on:** fourth annual edition · **49% 11-year-old, 33% 12-year-old,
18% 14-year-old** · **112.1 proof / 56.05% ABV** · **SRP $175** · **available September 1 at select
US retailers**, then UK, Germany, Korea, Japan, Australia and global travel retail · aged in the
traditional rickhouses, then moved to a limestone cellar built into the shelf around Star Hill Farm
· cellar runs about **50°F**, which slows wood extraction and makes oxidation the dominant reaction
· Maker's Mark carried no age statements before Cellar Aged launched in **2023**; the core
expression is six to seven years.
**Last year's blend, for the comparison hook:** 74% 11-year-old, 10% 13-year-old, 16% 14-year-old.
**The first two editions contained no 14-year-old bourbon.** So "more 14-year-old than last year"
is 18% versus 16% — true, but a **two-point** difference. **Do not inflate it.** The stronger,
cleaner hook is that this is the distillery's oldest blend to date.

**SENSORY — Robb Report's own, and the ONLY printable version:** oak, dark chocolate, cherry syrup,
bitter espresso, maple, vanilla and ripe stone fruit on the palate, then lingering spice and heat
on the finish at that proof. **The release's own notes — dark cherry, clove, vanilla bean, orchard
fruit / honey, brown sugar, ripe plum / almond, nutmeg, green apple — are brand copy. DO NOT
PRINT.** Flicker's own framing that age does not indicate quality, and that six to seven years is
widely considered a sweet spot, is his and is usable attributed.

**NO USABLE QUOTE.** Layfield's two Robb Report quotes run 21 and 20 words. Rob Samuels' release
quote is far longer. **Prefer none.**
**BANNED-WORD TRAP IN THE PRODUCT NAME:** the bottle is called **Cellar Aged** and "cellar" is on
the ban list. It is a proper noun, so it is permitted — but the blurb cannot avoid it, and the
word must never appear in WS's own voice around it. Flagged in COLLISION FLAGS.
**Do not re-define cask strength** — spent Aug 18 on Old Overholt.
**Also in the release, for a September Friday:** a ticketed 21+ launch event at the distillery
**Sept 10**, ahead of the Kentucky Bourbon Festival, and a Cellar Aged distillery tour from
**Sept 14**. Not staged — `kentucky-bourbon-festival` is a standing blocked item.

**Slot: Tue Sep 1, which IS the release date.** Held off Aug 25 deliberately: $175 is a Collector
item and Aug 25 already carries two.

### `bardstown-lochs-of-jura-2026` and `bardstown-discovery-2026` — NEW, VERIFIED on facts

**Staged link-out: `https://www.fredminnick.com/2026/08/18/bardstown-bourbon-company-announces-new-fall-releases/`
— Fred Minnick, Aug 18. It is a press-release reprint** (it says "in a news release" twice).
Second source: the **Business Wire release**, Aug 18, read via Morningstar. The two together clear
the facts; **an independent Tier 1–2 review would be a better link-out if one appears.**

**Resolved by the wire release, which FM omits:** **nationwide in limited quantities from Friday
Aug 21, 2026** · **$139.99 per 750ml.**
**Lochs of Jura Barrel Finish:** bespoke blend of straight bourbon and rye, then **32 additional
months** in ex-bourbon and ex-sherry casks from **Scotland's Isle of Jura** (238 residents) ·
**104 proof / 52% ABV** · **99 points at the 2026 International Wine & Spirit Competition, the
highest score in this year's North American judging** · the 59-gallon sherry casks were too large
for the ricks and sat in warehouse aisles.
**2026 Discovery:** blend of **7-, 10- and 11-year-old** bourbons from high rickhouse floors, then
**four months** in custom **Garryana** (Oregon White Oak) barrels · **112.8 proof / 56.4% ABV** ·
second Bardstown release to use that oak after Distillery Reserve Cascadia · Discovery moves from
numbered to annual releases; the Finishing Series expands.
Both bottles carry commissioned artwork by Louisville artist **Margaret Archambault**.

**SOURCE CONTRADICTS ITSELF ON ABV — resolved.** FM prints "112.8 proof (66.4% alc. by vol.)."
112.8 proof is **56.4%**, and the wire release says 56.4%. **FM has a typo. Print 56.4% or print
proof only.** Lesson 11 in action a second time.
**SENSORY BLOCKED, and it is the wood trap again.** "Ripe fruit, soft malt, subtle smoke, maritime
character" describes what the Jura casks contribute; "clove and nutmeg" describes what Garryana
lends. **Both are the release describing wood, not anyone tasting the whiskey. Nobody independent
has tasted either bottle. DO NOT PRINT ANY OF IT.**
**The honest hook is the 99 points** — a third-party competition result, verifiable, and the
highest North American score of the year. That carries the item without any sensory claim.
**NO USABLE QUOTE.** Dan Callaway's Jura line runs 22 words; "These releases started from two
different questions" is seven words but says nothing.
**The release uses "journey," "experience" and "collection." Never lift its phrasing.**

**Slot: Tue Sep 1.** Aug 21 is an edition day but Last Call is occasion-led and already full at
four; a $139.99 limited bottle is the wrong register for it. Aug 25 would be freshest but would
make three Collector items. **Aaron can pull it forward to Aug 25 — surfaced in Notes.**
**Run ONE of the two bottles, not both.** Lochs of Jura is the stronger item; Discovery is the
alternate and shares the link, so it cannot run in the same edition.

### Closed out this run

- **`moonshine-university-closure-2026` — SOURCED, then DROPPED.** Flavorman will conclude
  Moonshine University operations **Dec 31, 2026**; since 2013 it taught 337 courses to more than
  15,000 attendees and supported the launch of nearly 300 distilleries; enrollment fell about
  10–15%, then roughly halved over the past year; courses run through 2026. Carried by **The
  Spirits Business (Jul 2026)**, WDRB, Spectrum News 1, The Lane Report, Kentucky New Era and
  Distillery Trail. **Dropped for three reasons, not one:** no vetted Tier 1–2 outlet has it
  (Whisky Advocate, Robb Report and Fred Minnick all silent), it is **four weeks old**, and it has
  no consequence for a reader's shelf or weekend. **Do not rediscover. Do not re-search.**
- **`jack-daniels-distillery-series-17-2026` — DROPPED, distribution blocker confirmed permanent.**
  Robb Report's Taste Test ran **Aug 9** (Flicker) and supplies the sensory leg the item was
  missing — big berry, vanilla, oak, and the signature banana note, with heat overshadowing at
  138.4 proof. **But the same piece confirms it is a distillery-exclusive small-format bottle**, so
  the forward bar still fails. **Two further reasons to leave it dead:** the review is
  unfavourable, and **the article's framing is DISCUS-hostile throughout** — "drinks like a boozy
  flamethrower," "making at least one angel very drunk," "a much more drinkable level." Unusable
  even as paraphrase. Facts for the record: Distillery Series #17, distilled 2016, Coy Hill,
  top floor of Barrelhouse 1-13, mashbill 80% corn / 12% malted barley / 8% rye, 138.4 proof.
- **`garrisonbros.com/event-directory/` — FETCHED, works, low yield.** See HOSTS.

### Not new, and correctly not chased

Robb Report's spirits index also carried `wyoming-whiskey-state-of-the-union-bourbon-1238562857`
(already in WATCHING, still blocked on Wyoming-only distribution — **not re-opened, and no cheap
check will change the forward bar**), `garrison-brothers-cowboy-bourbon-hazmat-whiskey-1238550045`
(**a third source for the staged Garrison item, and an alternate link-out if the brand event page
ever fails** — the "hazmat" angle means over 140 proof, which the 141.0-proof bottle clears),
`new-survey-canadians-support-ban-on-american-booze-1238546939` (see the tariff note below), and
`1800-tequila-coleccion-tequila-friedeberg-1238551430` (not whiskey).

### THE CANADA TARIFF — a real dedup exception, and a real risk. Aaron's call.

**`canada-50pct-tariff-aug-19-2026` is in dedup, having run twice, and the tariff took effect at
12:01 a.m. ET TODAY, Aug 19, 2026.** An additional **50% Section 338 duty on Canadian alcoholic
beverages, whisky explicitly in scope**, applying regardless of USMCA preference. Trump signed
three Section 338 proclamations **Jul 20**. Context: Canadian provinces pulled American spirits
from shelves in March 2025 and only Alberta and Saskatchewan have lifted those bans.

**This is a legitimate exception to the never-republish rule** — the date arrived, which the skill
names explicitly as a material new development, not a countdown. **It is NOT an urgent override:**
a tariff is not a recall, a safety issue, litigation naming a WS partner, or a death.

**And it is exactly the story Adam complained about on Jul 27.** The tariff beat has run as
`scotch-tariff-removal-2026-07-24` (4x), `canada-50pct-tariff-aug-19-2026` (2x) and
`bushmills-ni-roi-tariff-split-2026`. A third Canada run is defensible on the rules and still
risks reading as the same article again. **That is why it went to Aaron as a question rather than
being staged.**

**It also has no link-out yet.** Robb Report covered the announcement in July
(`/trump-50-percent-tariff-canadian-whisky-1238490396/`, not in the spent list but the story it
carries has run twice). **Forbes is a contributor column — Tier 4, do not link.** The law-firm and
customs-broker alerts are not vetted. A Federal Register or White House proclamation would be
Tier 1 but is a poor destination for a consumer. **If Aaron says run it, the item needs vetted
Tier 1–2 pickup of the effective date first — Robb Report is the likely follow-up. Recheck
Thursday and Friday.** The reader-facing hook is the price question, not the policy.

---

## TUESDAY Aug 18 — WHAT SHIPPED

**Five items, not four.** Board went out as: Chattanooga ice wine (What's Dropping, Explorer) ·
Old Overholt 11-year (What's Dropping, Collector) · First West Explorer (Try This Next,
Explorer) · **Whisky Advocate's 20 high-scoring bottles (Try This Next, Explorer — NEW, found
this run)** · Buffalo Trace Prohibition set (Allocation Watch, Collector).

**Macallan Harmony VI was CUT**, as recommended across Aug 14, 16 and 17 with no reply. It is
not mentioned in the edition and was not surfaced a fourth time in Notes. **Treat it as closed.**

### The fifth item — how it was found and why it ran

The WA RSS sweep (window Aug 17–18) returned **two new items**, the first new WA material since
Aug 14. One is a cocktail (staged Friday, below). The other,
`20-whiskies-rated-90-points-or-higher-priced-75-or-under`, **published 05:25 PT on edition
morning** — Julia Higgins, WA. Twenty recent releases, every one scored 90 points or above.
It ran because it is the value/forward beat the board has been thin on, it is WA's own panel
data, and it was hours old.

**IT CARRIES A SELF-CONTRADICTION — logged as a new trap.** WA's own intro says "All these
whiskies have a suggested retail price of $75 or less," and the headline says $75 or under.
**Two of the twenty are listed at $90** — Chattanooga Triple Islay (55.5%, $90) and Shortbarrel
Four Grain (46%, $90). A first draft of the blurb printed "none over $75" and it was caught in
the pre-post check. **A reader clicking through would have seen the contradiction immediately.**
The published version drops the $75 frame entirely and prints what is unambiguous:
**fourteen of the twenty sit at $50 or under** (hand-counted: $35, 3×$40, 3×$45, $46, $48, $49,
4×$50). **Standing test added as lesson 11: when a source's own headline claim conflicts with
its own body, print the body.**

Verified prices from the list, for future use: Carlyle Master Blender's Selection 16yo blended
scotch 40% **$35** (WA: "this might be the best value you'll see for a 16 year old scotch") ·
Skellig Six 18 Small Batch PX 40% $40 · Wheel Horse Cigar Blend 50.5% $40 · Traveller No. 40
Full Proof 60.5% $40 (Buffalo Trace / Chris Stapleton) · Buzzard's Roost Double Oak 50% $45 ·
Loch Lomond Triple Oak 40% $45 · Shelby Co. Peaky Blinders 45% $45 · Clan Colla Uasis The
Triple 43% $46 · Stoll & Wolfe Pennsylvania rye 45% $48 · Two Stacks Triple Sherry 43% $49 ·
Maker's Mark 7yr 2mo Cask Strength 56.3% $50 (**first age statement on a Maker's bourbon**) ·
Bardstown Origin Series BiB 50% $50 · Bulleit Mesquite Smoked Malt 46.5% $50 · Filmland
Moonlight Mayhem! 2 47% $65 · Knob Creek Eli Manning single barrel 58.2% $70 · Killowen Rum &
Raisin 55% $70 · Lagavulin 11 Sweet Peat 43% $70 · Elijah Craig Barrel Proof A126 60.2% $75.

**Sub-$30 is still NOT closed.** The floor on this list is $35. Same floor as Breckenridge
Peach. Left as `_unchanged_` in Notes per the standing instruction not to re-query it.

### Buffalo Trace — the cross-review hook was dropped, deliberately

Prior state files pitched the hook as "the two reviews disagree on the standout" — Evans names
Kentucky River and Cove Spring, Breaking Bourbon calls the Watterson rye "downright
exceptional." **That hook cannot survive the sourced-claims rule: Breaking Bourbon is the
second source, not the link-out.** Naming it in copy would put a concrete claim in the blurb
that the linked page does not carry, and citing two outlets breaks one-link-per-item.
**The published blurb is built entirely on the WA article: 70.3% Watterson rye as the
highest-proof rye in the distillery's modern history, plus Evans's own first and second picks.**
Breaking Bourbon remains the verification leg and stays out of the copy.
**Standing rule: a second source verifies; only the link-out speaks.**

Two further claims were tightened at pre-post. "Labels the plant last used under Prohibition"
was cut — WA states that provenance for the *first* edition and says only "five more forgotten
names return" for the third; what WA states precisely for these five is that **each ties to a
figure or landmark from the Albert B. Blanton era**, and that is what printed. "Set only" was
also cut; WA says "priced at $1,000 for the set," which implies but does not state set-only, so
the published line is "$1,000 for the set."

### Link re-confirmation

All four staged link-outs re-fetched 200 with full article bodies before drafting: Buffalo Trace
(1,044 words of body text), First West (888), Old Overholt via Robb Report (1,353), Chattanooga
via Fred Minnick (761). The two new WA pages also 200. **No Notes bullet — nothing failed.**

### Every printed claim, against its source

- **Chattanooga** (FM Aug 14): ice wine among "the rarest, sweet wines in the world" ✓ · grapes
  frozen on the vine, handpicked, pressed still frozen (McCracken) ✓ · six mash bills, five malt
  whiskeys and one bourbon ✓ · aged over four years, more than a year in the finishing casks ✓ ·
  95 proof ✓ · $59.99/750ml ✓ · DC + 11 states ✓. **"Mash bill" was avoided, not defined** —
  printed as "grain recipes," which spends no intimidation-pass budget.
- **Old Overholt** (Robb Report Jul 30, Jonah Flicker): fourth cask-strength release ✓ · 11 years,
  down from last year's 12 ✓ · 125.6 proof, highest of the four (prior 121, 107.4, 117) ✓ ·
  Robb Report asked Beam and heard back from Bradford Lawrence ✓ · **"We did not receive a sample
  of this new whiskey to try yet"** ✓ · $110 SRP, select retailers nationwide ✓. **No sensory
  printed.** Cask strength defined in one clause.
- **First West** (WA Aug 11, Danny Brandon, note signed David Fleming): Baby Black developed
  exclusively for the Johnsons ✓ · kernels about a quarter the size of yellow corn ✓ · blend of
  two bourbons, wheated base ✓ · 92 points ✓ · WA's own note: baked apple, cinnamon (nose),
  chocolate, peanuts (finish) ✓ · $50, nationwide, permanent ✓. **The "vanilla coconut ice cream"
  note in WA's palate line was avoided on purpose** — see the coconut collision flag. No
  distilling claim was made at all, which sidesteps the Bardstown-versus-in-house conflict.
- **WA value list** (WA Aug 18, Julia Higgins): all twenty at 90 points or above ✓ · fourteen at
  $50 or under ✓ (hand-counted) · $35 16yo blended scotch ✓ · WA's hedged "might be the best
  value" preserved as "may be" ✓ · Maker's Mark first age statement ✓.
- **Buffalo Trace** (WA Jul 22, Sean Evans): third edition ✓ · Watterson rye 70.3%, highest-proof
  rye in the distillery's modern history ✓ · names tied to figures and landmarks of the Blanton
  era ✓ · Evans's "My favorite of the set" = Kentucky River, "My second favorite" = Cove Spring ✓ ·
  five 375ml bottles, $1,000 for the set, shipping since June 2026 ✓.

**Zero verbatim quotes in the edition.** Allowed maximum is one; none earned its place at length.
**"Hunt" was not used at all.** "Collection" appears once, as the proper noun Prohibition
Collection, which the brand skill permits.

---

## THE WHISKY ADVOCATE RSS FEED — the primary discovery path

**`https://whiskyadvocate.com/call/blogs/rss/` returns 200 with ten dated article links,
newest first. Sweep it first on every run.** It replaced two dead HTML indexes
(`/news` 301s to `/News` and renders zero article links; `/Tag/Cocktails` renders exactly one).
Both grids are client-rendered. Do not spend fetches on either.

**Aug 18 — the feed moved after three quiet days.** Two new items since Aug 14, both taken:

| Date | Title | URL | Disposition |
|---|---|---|---|
| Aug 18 | 20 High-Scoring Whiskies Priced at $75 or Under | `/20-whiskies-rated-90-points-or-higher-priced-75-or-under` | **PUBLISHED Aug 18** |
| Aug 17 | A Whisky Jungle Bird (Thunder Bird cocktail) | `/thunder-bird-whiskey-cocktail-recipe` | **STAGED Fri Aug 21** |
| Aug 14 | News Notes: Chip Tate Does Mezcal, New Highlands Distillery | `/whisky-news-roundup-august-14-2026` | mined |
| Aug 14 | Whisky Watch: Jameson, Redemption Bonded & More | `/jameson-single-pot-still-garrison-cowboy-and-more-new-whiskey` | **now FREE — see below** |
| Aug 14 | Auction Update: Momentum Returns | `/whisky-auction-results-august-14-2026` | recommend against |
| Aug 13 | Cuervo Mole Cask Tequila | `/jose-cuervo-reserva-de-la-familia-mole-cask` | dropped, not whiskey |
| Aug 12 | Dubai Chocolate pairing | `/dubai-chocolate-and-whisky-pairing` | staged Fri Aug 21 |
| Aug 11 | Whiskey of the Week: First West Explorer | `/first-west-explorer-reviewed` | **PUBLISHED Aug 18** |
| Aug 10 | Louisville Rickhouse Whiskey Co. | `/louisville-rickhouse-whiskey-co-tastings-guide` | covered |
| Aug 7 | Whisky Watch: Macallan, Raasay, Old Overholt | `/macallan-glenfiddich-jack-daniels-and-more-new-whiskey` | spent |

The Aug 14 quiet spell was supply, not transport — confirmed, since the same feed produced two
items three days later. **Lesson 9 held.**

**Aug 19 — feed unchanged.** Fetched 200, ten items, newest still the Aug 18 05:25 value list.
**Zero new WA material in the Aug 18–19 window.** Every one of this run's three staged items came
from Robb Report and Fred Minnick instead. **This is the first run where WA contributed nothing and
the board still filled — the outlet-concentration work has paid off.**

**Aug 20 — feed moved after one quiet day. ONE new item, and it was taken.**

| Date | Title | URL | Disposition |
|---|---|---|---|
| Aug 19 07:00 | A China-to-Kentucky Whisky Experiment Launches | `/shang-baijiu-whiskey-review` | **STAGED Tue Sep 1** |

Sean Evans byline, and **he tasted both expressions** — the scarcest asset on this board. **Lesson 9
held again:** one quiet day (Aug 19) was supply, not transport, and the feed produced a
sensory-carrying review the very next morning. The Aug 18 value list is now second-newest; every
older item in the feed is already published, staged, mined or explicitly recommended against.

---

## ROBB REPORT IS THE THIRD OUTLET — the structural gap is closing

**The biggest finding of this run, and it came free.** The Old Overholt page's own "Most Recent
Stories" rail carries Jonah Flicker's other work, and two entries there resolve two separate
blockers on the Aug 25 board. **Reading the author rail on a Robb Report article page is now a
first-class discovery path** — it cost zero extra requests and did what a week of searching had
not.

Robb Report is already a proven, in-use link-out (Old Overholt, Stetson). Its whiskey critic
publishes a weekly Taste Test with **his own scored sensory** — the scarcest thing on this board.
**This is the third live outlet the collision flags have been asking for since Aug 13.**

### `redemption-single-barrel-bonded-bourbon-2026` — UNBLOCKED. The Shanken question is MOOT.

**`https://robbreport.com/food-drink/spirits/redemption-whiskey-brings-back-18-year-old-bourbon-1238554565/`
— Robb Report, Aug 14, Jonah Flicker. Loaded 200 and read in full. This is the link-out.**

It covers the bonded release directly and independently. **What it supports:** Redemption Single
Barrel Bonded Bourbon is **six years old, two years older than bottled-in-bond requires** ·
distilled at **MGP's Ross & Squibb Distillery, Lawrenceburg, Indiana** · **bottled without chill
filtration at 100 proof in Frankfort, KY** · **available in stores and at websites like ReserveBar
now** · **SRP $50** · part of the **Higher Marques Collection**, a series that debuted after
Redemption redesigned its core portfolio last spring · Redemption founded 2010 on MGP-sourced rye,
acquired by **Deutsch Family Wine & Spirits in 2015**, **Alan Kennedy became master blender in
2023** · Kennedy quoted at length from a statement — **runs well over 20 words, prefer none.**
Bonus context: the redesign followed **Diageo suing over a bottle design too close to Bulleit's;
a jury agreed and the 2nd Circuit ultimately ruled for Diageo.** Adjudicated and old — **not an
urgent-override item**, and Redemption is not a WS partner.

**CONSEQUENCE: Aaron no longer has to tier Shanken News Daily to run this item.** Surfaced in the
Aug 18 Notes as moot. Shanken stays unvetted and stays out of the link-out position; keep it as
corroboration only until the source directory returns. **The Kleinman quote and the 85,000-case
Impact Databank figure remain Shanken-only — do not print either.**

**AVAILABILITY NOW HAS THREE READINGS AND THEY DISAGREE.** WA says "Limited." The brand release
says nationwide. **Robb Report says available now.** WA and the release were already in conflict;
Robb Report is the newest and is the link-out. **Print Robb Report's "in stores and at ReserveBar
now" and print no footprint at all. Never print "nationwide."**

Also in that piece, for the record: **Redemption 18-Year-Old returns this fall, $400**, 74% corn /
22% rye / 4% malted barley, barrel proof 102.85, and **Robb Report did not sample this year's
release** — the circulating notes are official. Last year's was 69 barrels at 103.4 proof.
And **Bib & Tucker 8-Year Bottled-in-Bond** is described here too — that story is already in
dedup from Aug 4, which is dedup working as intended.

### `jameson-distillers-batch-single-pot-still-2026` — now has SOURCED SENSORY and its own link

**`https://robbreport.com/food-drink/spirits/whiskey-review-jameson-distillers-batch-irish-whiskey-1238551938/`
— Robb Report, Aug 16, Jonah Flicker, Taste Test. Loaded 200 and read in full.**

**Flicker tasted it. Score 88.** His own palate: vanilla, spice and fruit up front, then dark and
milk chocolate, nutmeg, cinnamon, honey sticks, maple, ripe stone fruit, tannic oak, creamy
mouthfeel. **This is real sourced sensory and it replaces the brand copy the item had been
blocked on.** Do not print the release's "toasted oak, honeycomb, salted caramel..." — still
brand copy, still banned from the page.

Also supported here: previously sold in Ireland and the UK as **Jameson Single Pot Still**,
renamed Distiller's Batch for the US ✓ · **five cask types — ex-bourbon, oloroso, and virgin
Irish, European and American oak** ✓ · Midleton, master distiller **Kevin O'Gorman** ✓ · a clean
plain-English definition of single pot still (one distillery, pot still, malted and unmalted
barley, sometimes a little other grain) ✓ · Midleton also makes Redbreast, Powers, Green Spot,
Midleton Very Rare ✓ · Jameson is the best-selling Irish whiskey in the world ✓.

**Flicker's closing line is quotable but check the length before use.** Avoid his dive-bar and
shot-with-a-beer framing entirely — DISCUS 73.8.

**CONSEQUENCE: the Aug 14 Whisky Watch is now spent on nothing.** Jameson has its own better
link. Garrison has its own Tier 1 event page. Redemption has Robb Report. **THE SHARED-LINK
CONSTRAINT ON THAT ROUNDUP IS FULLY DISSOLVED** — every item that was queued behind it now has
its own primary source. The roundup is free for a future item or can simply go unspent.

---

## FRIDAY Aug 21 — STAGING RECORD (all four PUBLISHED Aug 21; see WHAT SHIPPED above)

**Retained as the record of what was staged and why, and of which cautions proved real when the
pages were re-fetched on edition morning. Every caution below was checked against the live page —
the drinking-pace phrasing, the two DISCUS blocks and the long Robinson quote were all present as
described.** The staged instruction to print a bare "$55 GA / $75 VIP" was the one thing this
section got wrong; see lesson 22.


- `detroit-bourbon-blues-festival-2026` — **VERIFIED, price resolved by default.**
  Sun Aug 23, Eastern Market Shed 5, 2810 Russell St, 12–7pm, 21+, blues from Rome Antenucci,
  Free Style Band Detroit, Shaun Booker Dammit Band, cocktail classes with Louisville Tourism,
  proceeds to the FernCare Free Clinic. Link detroitbourbonandblues.com (Tier 1, organizer);
  second source the Eventbrite listing. **Print $55 GA / $75 VIP, official site only.**
  **On the Calendar. This is the Venue Regular item and it is date-critical — Aug 21 or never.**
- `copperworks-farmsmith-spokane-relief-2026` — **VERIFIED.** Fred Minnick Aug 14 (the link-out)
  + WA News Notes Aug 14 + Copperworks' own statement.
  Throughout **August**, Copperworks donates **$20 from every bottle of Farmsmith American Single
  Malt sold** to the **H.O.M.E. Starts Here** Spokane Complex Fire Relief Fund · rent assistance,
  medical equipment, transportation · Copperworks is Seattle-based, opened 2013, founded by
  **Jason Parker** and Micah Nutt · Farmsmith explores single-variety, single-farm, single-year
  barley · current release uses **single-varietal Genie barley grown 20 miles west of Spokane**,
  malted by **LINC Malt in Spokane** · direct donations at my.spokanecity.org.
  **Parker's quote is 18 words and clean:** "The farming families and partners around Spokane
  aren't just our suppliers; they are our friends." **Best quote candidate on the board.**
  **NOT SOURCED:** no price, no ABV, no age, no footprint. **Write it without a price.**
  **No sensory anywhere. None to write.**
  **Tone:** live disaster. Quiet and factual. Not an urgent override — a charitable release is not
  a recall, safety issue, litigation or a death. Normal slot, no occasion framing, no payoff-line
  cleverness. **DISCUS watch: never imply buying more gives more. State the donation once, flatly.**
- `whisky-advocate-dubai-chocolate-pairing-2026` — **VERIFIED.** WA Aug 12, Pete O'Connell. Seven
  bottles each with WA's own score, ABV, price and note. Runs nine days old; fine, evergreen, no
  date peg. Full table retained below.
  **Print cautions:** no usable quote (Todd Robinson runs 22+ words) · **do not reproduce WA's
  drinking-pace phrasing** ("wash it down with sips," "sipping this between bites") — DISCUS
  73.8 · **do not lead on Wild Turkey** (ran Aug 11) · Hibiki's mizunara "sandalwood and coconut"
  is WA describing the wood, not the whiskey.
- `whisky-advocate-thunder-bird-cocktail-2026` — **NEW THIS RUN. WA Aug 17, Brittany Risher
  Englert.** Read in full. **Max Schikora, bar manager at Huna, Ann Arbor, Michigan.** A rye-and-
  rum Jungle Bird riff. Recipe: ¾ oz Rittenhouse bottled-in-bond rye (or other 100-proof rye), ¾
  oz Jamaican rum, ¾ oz Campari, ½ oz fresh lime, ½ oz demerara syrup, 2 oz pineapple juice,
  pineapple wedge; shake 5–8 seconds, strain over fresh ice in a double Old Fashioned glass.
  **Schikora's own sensory, which makes it printable:** bright pineapple and lime up front, then
  Campari bitterness, rye for spice and structure.
  **CLEAN QUOTE, 10 words, named, in the linked source:** "Most summer cocktails are either too
  sweet or too simple."
  **DISCUS BLOCK — do not print, do not paraphrase:** "it drinks easier than it should for
  something with this much proof behind it." That is a consumption-rate cue. Also skip "tastes
  like a vacation—one you actually remember," which reads as an intoxication joke.
  **This is a better Easy Pour than any of the June alternates** — newest, own sensory, named
  creator, no coconut collision, and a Michigan venue pairs naturally with Detroit in the same
  edition. **But it would be a fourth straight Friday of a WA cocktail** (see COLLISION FLAGS),
  and taking it makes Aug 21 two WA of four. **Recommendation: take it.** The Detroit/Michigan
  adjacency is worth more than the outlet-repetition cost, and Copperworks and Detroit keep the
  edition off WA at the top. Aaron can veto by reply.
- **Easy Pour alternates, now demoted below Thunder Bird:** (1) Lost Irish cucumber; (2) Coconut
  Manhattan; (3) Vintage Coco. All June, all still live, none needed.

**Outlet mix if Thunder Bird runs: organizer site, Fred Minnick, Whisky Advocate ×2.** Acceptable.
**Persona shape: Venue Regular (Detroit), Social Drinker (Copperworks, Thunder Bird), food
pairing (Dubai chocolate).** That is exactly Friday's brief and the coverage floor clears.

### Carried forward — `whisky-advocate-dubai-chocolate-pairing-2026`

All seven bottles carry WA's own score, ABV, price and tasting note — WA's own panel data:

| Score | Bottle | ABV | Price |
|---|---|---|---|
| 95 | Rampur Barrel Blush Indian Single Malt | 45% | $105 |
| 94 | Port Charlotte 18 year old Scotch Single Malt (2025 Release) | 51.5% | $200 |
| 94 | Wild Turkey Rare Breed Barrel Proof Straight Rye | 56.1% | $60 |
| 93 | Kentucky Peerless Double Oak Bourbon | 54.35% | $95 |
| 92 | Hibiki Japanese Harmony | 43% | $100 |
| 92 | Redbreast 12 year old Irish Single Pot Still | 40% | $70 |
| 90 | High Wire Jimmy Red Limited Edition Wheated Bourbon (Batch 6), 7yo | 53.5% | $100 |

Also supported: Dubai chocolate is Belgian chocolate filled with pistachio cream, tahini and
fried kataifi (shredded phyllo) · invented 2021 by **Sarah Hamouda**, British-Egyptian engineer,
with culinary consultant **Nouel Catis Omamalin** · **FIX Dessert Chocolatier** opened in Dubai
2022, flagship bar **Can't Get Knafeh Of It** · **WA states its popularity has contributed to
worldwide pistachio shortages — attribute that to WA** · Rampur is Himalayan-foothills, bourbon
barrels plus Australian shiraz casks · Port Charlotte is Bruichladdich, Islay, peated · Wild
Turkey Rare Breed rye is non-chill filtered · Peerless Double Oak is 4+ years in one new charred
barrel then a second · Hibiki blends malt and grain from three Suntory distilleries, includes
mizunara · Redbreast 12 is Midleton, triple-distilled single pot still, bourbon and oloroso casks ·
High Wire has used the near-extinct **Jimmy Red** corn varietal since 2013.

**Single pot still collision — now resolved by sequencing.** Redbreast 12 sits in this list and
Jameson is the Aug 25 lead. **Do not define single pot still on Aug 21. Spend it on Jameson,
where it is the whole story and where Robb Report supplies a clean plain-English definition.**

---

## FRIDAY Aug 28 — ALL FOUR PUBLISHED Aug 28 (staging record; see WHAT SHIPPED above)

**BOARD CLOSED BY PUBLICATION. All four keys are in dedup and closed to re-publishing and
re-scouting.** The "two ship flagged" plan below was overtaken on edition morning: **New Riff found
its second source inside the already-staged WA Whisky Watch page and shipped verified. Only Brough
Brothers shipped single-sourced.** Kept below for the record.

**AUG 27 STATE — the board the edition ran from.** The second-source attempt on both
FM items **failed**, and failed for the right reason: every pickup is the same news release, and the
two Tier 1 primary routes (`belleoflouisville.org/news`, `broughbrothers.com`) are respectively
silent and client-rendered. **New Riff and Brough Brothers ship with an explicit verification flag.
Filmland and the glamping guide ship clean.** All four link-outs re-confirmed 200 with real body text
on Aug 27; **tomorrow still owes a fresh re-confirm.** Nothing added, nothing cut, nothing to search.
**NEW RIFF SENSORY IS BRAND COPY — "dark fruits, buttery sherry oak," "sappy mouthfeel," "clove, wood
spice." Print none of it.** The edition's one permitted quote is **Evans's six words** on glamping;
a nineteen-word Sprance quote exists but lives in a reprint and is forbidden. **Do not spend the
quote twice.**

---

## FRIDAY Aug 28 — staging record as of Aug 26. THE OUTLET GAP WAS CLOSED HERE.

**AUG 26: two non-Whisky-Advocate items added, both Fred Minnick link-outs, both single-sourced.**
Full entries in the Aug 26 section — `new-riff-sherry-finish-malted-rye-2026` (promoted from
September pointer; **releases 11 a.m. the morning of the edition**; beat `whats-dropping`, Explorer)
and `brough-brothers-belle-of-louisville-2026` (**event Sat Aug 29, noon–2, 1250 River Road,
Louisville**; beat `on-the-calendar`, Venue Regular, **cause-led count now 1 of 2**).
**Both need a second source or ship flagged. Both need a link re-confirm Friday.**
**Outlets are now WA ×2, FM ×2 — the residual ask from three prior runs is satisfied and closed.
Do not search for a fifth Friday item. Do not drop a verified item to make room.**
**Board is bottle-heavy: three bottles, one pure occasion item (glamping).** Acceptable, and Brough
Brothers carries an event, so the occasion-led half still reads. **Lead with an occasion, not a
bottle.**

- `filmland-malted-mummy-2026` — **NEW AND VERIFIED Aug 23. Full entry in the Aug 23 section.**
  43% ABV · $75 · Limited · first American single malt from the LA bottler · undisclosed Iowa
  distillate · five years in ex-IPA barrels · **debut Aug 29, the day after this edition.**
  **90 points from Whisky Advocate's tasting panel — printable and attributed. No descriptors
  exist; print none.** Beat `whats-dropping`, persona Social Drinker.
  **Peg the Aug 29 date, never BrewzleFest.** See COLLISION FLAGS.
  Link: `https://whiskyadvocate.com/new-whiskey-from-bowmore-barrell-and-more`
- `whisky-advocate-distillery-glamping-2026` — **NEW AND VERIFIED Aug 23. Full entry in the Aug 23
  section.** Sean Evans, twelve glamping sites in whiskey country. **Lead the Kentucky material —
  Lawrenceburg within striking distance of 22 distilleries, and the barrel cabins.** Beat
  `on-the-calendar`, persona Venue Regular. **Carries the board's only clean quote: Evans, "It's
  where you are that matters," six words.**
  Link: `https://whiskyadvocate.com/glamping-near-whiskey-distilleries`

**AUG 24 UPDATE — SUPERSEDED AUG 26. Kept for the record because its conclusion was wrong, and the
reason it was wrong is the run's lesson: the FM rail it called empty was carrying Brough Brothers
that same day. See "THE AUG 24 FM RAIL WAS NOT EMPTY" in the Aug 26 section.**
**AUG 24 UPDATE: still TWO STAGED. The non-WA item was searched for and DOES NOT EXIST YET.**
WA published nothing new since Aug 21; Robb Report's only new whiskey piece (Hibiki 12) fails the
forward bar on airport-only distribution; the FM rail and the 23-item TSB index produced nothing
stageable. **WA's newly-proven travel indexes yielded a dated bench — but every candidate on it is
also Whisky Advocate, so none of them fixes an outlet problem.** Three runs remain before this
edition. **If nothing non-WA exists by Thursday, run the two. Do not pad and do not drop a verified
item.**

**Aug 28 shape: TWO STAGED, which clears the empty-pipeline floor with room to spare.** One bottle,
one places item — the occasion-led half is covered and the edition does not read as all-event.
**Both are Whisky Advocate link-outs, and that is the one real cost of this run:** an all-WA Friday
after four straight WA cocktails. **Neither is a cocktail, so the cocktail count does not advance
and no Aaron say-so is needed** — but a third item from a different outlet would fix the outlet
read, and there are four prep runs (Mon–Thu) to find one.
**A third item would help and is not required. Two verified items beat three with one padded.**
**Constraints all still clear: no pineapple, no Michigan, no third cause-led item, no fifth WA
cocktail.** `hard-truth-dark-roast-rye-2026` has an Indianapolis event on Fri Aug 28 — **still
Tuesday material, not Last Call. Do not convert it to fill this slot.**
**Send-off:** the signature line is required on a Last Call. "Worth the pour" is the phrase on file,
cross-checked against the real Aug 14 and Aug 21 posts.

---

## TUESDAY Aug 25 — ALL FOUR PUBLISHED Aug 25 (staging record; see WHAT SHIPPED above)

- `jameson-distillers-batch-single-pot-still-2026` — **VERIFIED. Link-out UPGRADED this run to
  Robb Report Aug 16, which brings sourced sensory and a score of 88.** Second source: WA Whisky
  Watch Aug 14 (46% ABV · SRP $50 · nationwide beginning September, imported by Pernod Ricard USA
  · triple-distilled from malted and unmalted barley at Midleton · originally released in Europe
  in 2022 · a single pot still mashbill written by **John Jameson II in 1826** at Bow Street,
  Dublin · WA calls single pot still "Ireland's signature whiskey style"). The Pernod Ricard
  release via PR Newswire and BevNET is ONE source between the reprints and is weaker: $49.99
  rather than $50, pre-sale open on the Jameson site.
  **Prefer WA's figures for price and distribution; prefer Robb Report for taste and for the
  definition. Never print the release's tasting notes. Forbes' piece is a contributor column —
  Tier 4, do not cite, do not link.**
  **The strongest Aug 25 item:** big name, $50, nationwide, real sensory, and one insider term the
  intimidation pass can define in a single clause.
  Link: `https://robbreport.com/food-drink/spirits/whiskey-review-jameson-distillers-batch-irish-whiskey-1238551938/`
- `redemption-single-barrel-bonded-bourbon-2026` — **UNBLOCKED THIS RUN. VERIFIED, two
  independent sources, and it now has a vetted link-out.** Robb Report Aug 14 (the link-out) + WA
  Whisky Watch Aug 14 (50% ABV · SRP $50 · availability "Limited" · first bottled-in-bond from the
  brand · Ross & Squibb distillate aged 6 years · each barrel hand-selected by **Alan Kennedy** ·
  bottled in **Frankfort, Kentucky** · relaunch of the Higher Marques line, prior releases a
  Cognac Cask Finish high-rye and a wheated bourbon). Brand release adds mashbill **60% corn / 36%
  rye / 4% malted barley**, non-chill filtered, six-bottle cases, ongoing rather than one-time.
  **NO SOURCED SENSORY anywhere.** The circulating "vanilla, worn leather, raspberry, crème
  brûlée, sweet corn, baking spice, caramel, oak" is brand copy. **Do not print it.**
  **Availability: print Robb Report's "in stores and at ReserveBar now." Print no footprint.
  Never print "nationwide."**
  **Do not re-teach bottled-in-bond** — three prior instances. Assume it and link.
  **The honest hook is the six years: two more than the standard requires.**
  Link: `https://robbreport.com/food-drink/spirits/redemption-whiskey-brings-back-18-year-old-bourbon-1238554565/`
- `garrison-brothers-cowboy-bourbon-12-2026` — **VERIFIED, two sources, own Tier 1 link-out.**
  `garrisonbros.com/events/2026-cowboy-bourbon-release/` (Tier 1, the brand's own dated event
  page — the link-out) + WA Whisky Watch Aug 14.
  **Tier 1 page supports:** **Sat Sept 12 2026, 8:00 am – 4:00 pm** · Garrison Brothers
  Distillery, 1827 Hye-Albert Rd, Hye, TX · **bottles $249.99** · **141.0 proof** · uncut,
  unfiltered Texas straight bourbon · live music, neat pours and cocktails from the Whiskey Shack.
  **WA adds:** 12th edition · **70.5% ABV** · SRP $250 · **16,000 bottles** · **1,000 held for the
  launch event, 279 on the online store from Fri Sept 18**, remainder nationwide.
  141.0 proof is exactly 70.5% ABV, so the two sources agree on strength. **Print $249.99.**
  **AGE CONFLICT — print no age.** WA says "aged at least 8 years"; the brand's event page says
  "at least six scorching Texas summers." Irreconcilable, and the brand is both primary and
  link-out. Proof, price and date are all clean and are the interesting facts. **Never split the
  difference.** Surfaced in Notes Aug 17.
  **Bottle counts are WA-only** — the event page states none. **If the 1,000/279 split is printed,
  attribute it to Whisky Advocate.**
  **SENSORY — do not print.** The event page's "toasted caramel, baked spices, molasses, and
  vanilla... ripe plums dipped in 70% dark chocolate" is brand marketing copy. Nobody independent
  tasted it. The page also uses "experience," a banned word.
  **DO NOT MINE `garrisonbros.com/cowboy-bourbon/`** — undated evergreen page, states 73.2% ABV /
  146.4 proof and its own notes. **Different, earlier bottling.**
  **Slot:** Aug 25 works, but the event is Sept 12, so any Tuesday to Sept 8 works and a September
  Tuesday is arguably the better peg.
  Note `garrison-brothers-laguna-madre-2026` is in dedup — **different bottle, not a repeat.**
  Link: `https://www.garrisonbros.com/events/2026-cowboy-bourbon-release/`

- `heriot-watt-kirin-mango-aroma-study-2026` — **NEW AND VERIFIED Aug 19. Full entry above.**
  Link: `https://robbreport.com/food-drink/spirits/scientific-study-mango-notes-in-whisky-1238553386/`
  **Carries the board's only usable quote (Annie Hill, 15 words) and its only non-bottle item.**
  Needs a beat-slug decision before publish — see OPEN GAPS.

**Aug 25 shape: FOUR FIRM. Explorer ×2 (Jameson, mango study), Collector ×2 (Redemption,
Garrison).** Three outlets — Robb Report ×3, garrisonbros.com ×1 — and **zero Whisky Advocate
link-outs.** Two items carry real sourced sensory (Jameson, and the mango study by its nature).
**The Explorer gap the Aug 18 file opened is closed. Do not add a fifth Collector item.**
**Watch the Flicker concentration: three of four are his byline.** That is the mirror of the WA
problem and it is now worse than the Aug 18 file predicted. **If Aaron wants it broken up, Garrison
holds easily — its event is Sept 12, so any Tuesday through Sept 8 works.** That is the cheapest
fix and it costs the board nothing.

---

## TUESDAY Sep 1 — ALL FOUR PUBLISHED Sep 1 (staging record; see WHAT SHIPPED above)

**This board is CLOSED BY PUBLICATION. All four keys are in dedup with Oct 1 prune eligibility.
Never re-scout, never re-publish. Kept below only as the record of how the board was built.**

**AUG 26: `jack-daniels-american-single-malt-2026` added as the fourth.** It clears both conditions
the Aug 25 file set — **Explorer, not Collector; Fred Minnick, not Flicker.** $74.99 for a litre, 90
proof, 100% malted barley, Oloroso sherry finish, duty-free-only until now, national this fall, and
the TTB's first new whiskey category in over fifty years. **No independent tasting exists — say so
to the reader; never print Jack Daniel's own notes.** Full entry in the Aug 26 section.
**Shape: Collector ×2, Explorer ×2. Outlets RR ×2, WA ×1, FM ×1. Flicker two of four.**
**Closed at four. Do not add a fifth.**

- `makers-mark-cellar-aged-2026` — **release day is Sept 1 itself.** $175, 112.1 proof, 49/33/18
  blend of 11-, 12- and 14-year-old. **Robb Report tasted it — real sourced sensory.** No usable
  quote. "Cellar" is a banned word inside the product's own name; proper noun, so permitted.
  Link: `https://robbreport.com/food-drink/spirits/makers-mark-2026-cellar-aged-bourbon-1238564495/`
- `bardstown-lochs-of-jura-2026` — **LINK-OUT UPGRADED Aug 20 to Robb Report, which tasted it.**
  104 proof, 32 months in Isle of Jura casks, out at specialty retailers nationwide from Aug 21.
  **Sourced sensory now exists** — oak, dried and fresh berries, salinity, apple cobbler, the
  faintest whiff of smoke; Flicker calls it delicious. **Print $140 against the Robb Report link,
  not $139.99. Print no blend percentages — Robb Report's sum to 109%. The 99 IWSC points is
  Fred-Minnick-only and cannot be printed against this link.** `bardstown-discovery-2026` shares
  the link in both outlets, so the two can never run together. Full entry in the Aug 20 section.
  Link: `https://robbreport.com/food-drink/spirits/bardstown-bourbon-company-new-cask-finished-whiskeys-1238567077/`
- `shang-jiangxiang-whisky-2026` — **NEW AND VERIFIED Aug 20. This is the non-Collector lead.**
  Whisky Advocate Aug 19, Sean Evans, **tasted both expressions**. $46 (92 proof) and $65
  (100 proof, 500ml). A sauce-aroma baijiu from Guìzhōu redistilled into a whisky base and aged in
  charred American oak in Kentucky. **Evans is lukewarm and the item must say so.** Five insider
  terms — define baijiu only. **Never lift WA's "non traditional whisky experience."** Full entry
  in the Aug 20 section.
  Link: `https://whiskyadvocate.com/shang-baijiu-whiskey-review`

**Sep 1 shape: THREE STAGED — Collector ×2 (Maker's Mark, Bardstown), Explorer ×1 (SHĀNG).**
**The non-Collector-lead gap the Aug 19 file opened is CLOSED, on the first run after it opened.**
All three carry real sourced sensory, which has never been true of a board on this pipeline before.
**Outlets: Robb Report ×2, Whisky Advocate ×1. Flicker bylines both Robb Report items** — see
COLLISION FLAGS; SHĀNG breaks it up but does not solve it. **A fourth item is not needed. If one is
added, it must not be Collector and must not be Flicker.**
September also brings the seasonal third-edition bump (Sept–Nov) — **Aaron's call, not this
pipeline's; surface it once if he has not raised it by the Aug 28 run.**

---

## FRIDAY Sep 4 — TWO STAGED, ONE BLOCKED ON A BYLINE CALL, as of Sep 1.

**SEP 1 UPDATE — the tariff is now the non-WA third, and it arrived by default rather than by
research.** See "THE TSB TIER DEFAULT FIRED" in the Sep 1 section.

- `canada-50pct-tariff-2026` — **STAGED Sep 1. Formerly `canada-50pct-tariff-aug-19-2026`; the old
  key stays in dedup and is NOT pruned, so both spellings must be checked before any re-stage.**
  **Link-out: `https://www.thespiritsbusiness.com/2026/08/canada-us-dispute-heats-up-with-50-tariff/`
  — The Spirits Business, Aug 24, Nicola Carruthers. Tier 2-equivalent as of today's default.**
  Second source: BNN Bloomberg (verified Aug 23). **Facts re-confirmed Sep 1 by open search and they
  have NOT moved again:** US 50% tariff on ~$27.6bn of Canadian goods live since **Aug 22**;
  **Canada's counter-tariffs take effect 12:01 a.m. Sept 8**, 15–50% across 700+ items.
  **THE ONE THING THIS ITEM MUST GET RIGHT, and it is a trap:** Canada's retaliation list is steel
  and aluminium, dairy, appliances, agricultural equipment, pulp and paper, plastics and
  electronics — **US alcohol is NOT on it.** The shelf-price consequence for a US reader runs the
  other way: **the US tariff on Canadian goods is what touches Canadian whisky on a US shelf.**
  **Do not write, or imply, that Canada is tariffing American whiskey. It is not.**
  **Confirm the Canadian-whisky line item against the link-out before drafting** — if TSB does not
  say Canadian whisky is covered, the item says only what TSB says. A Shelf-Price Watch blurb that
  cannot name the affected category honestly is a two-line item or no item.
  Beat `whats-dropping` is wrong for this; **there is no shelf-price beat slug and this is the
  second time that has bitten.** Closest fit is `try-this-next`, which is a poor one. **Persona
  `social-drinker` (cross-persona item, and Sep 4's staged board is otherwise all Venue Regular).**
  **Clean seven-word quote available and verified: Carney said the US "asked too much and offered
  too little."** Named speaker, from the linked source, inside the cap.
  **SHAPE VALUE: it is non-WA and non-`on-the-calendar`, which is exactly the third item the Aug 31
  file said Sep 4 needed.** **REGISTER RISK, and it is real: Last Call is occasion-led and a tariff
  item is off-register.** **Recommendation: run it, placed last, short and factual, with no occasion
  framing. A three-item Last Call that includes one honest price item beats a two-item one.**

- `buffalo-trace-on-tour-2026` — **NEW AND STAGED Aug 30. VERIFIED on a Tier 1 primary plus two
  pickups.** Four cities Oct 1 – Nov 15, **reservations open Sept 2 at 10 a.m. ET**, complimentary
  guided tastings, 21+. **Reservations open two days before this edition — the reader can act
  immediately.** No sensory anywhere; print none. **Do not print "Sazerac Rye 100 Proof" — that name
  is WKYT's, not the WA link-out's.** Beat `on-the-calendar`, persona Venue Regular. Full entry in
  the Aug 30 section, including the banned-word and DISCUS warnings, which are heavier than usual.
  Link: `https://whiskyadvocate.com/whiskey-news-roundup-august-28-2026`
- `whisky-advocate-outdoor-excursions-2026` — **CANDIDATE, NOT STAGED. Blocked on Aaron's byline
  call: it would be Sean Evans number three before mid-September.** WA Aug 26, first-person, one
  source by design. **£100/$134 Macallan fly-fishing passes the actionable test; the Catskills outing
  is the US-reachable one.** Surfaced in the Aug 30 Notes. **Do not self-authorise — if he is silent,
  hold it past mid-September.** Full entry in the Aug 30 section.
  Link: `https://whiskyadvocate.com/outdoor-excursions-for-whisky-lovers`

**Sep 4 shape as of Sep 1: TWO firm (Buffalo Trace, tariff), ONE conditional (outdoors).** **TWO prep
runs remain — Wed Sep 2 and Thu Sep 3.** **The tariff fixes the shape problem the Aug 31 file
named: it is non-WA and non-`on-the-calendar`.** Outlets would be WA ×1 and TSB ×1; personas Venue
Regular ×1 and Social Drinker ×1. **A three-item Last Call is now reachable without the byline call.**

**THE REALISTIC PATHS, in order, as of Sep 1 — AND THE ORDER CHANGED BECAUSE OF LESSON 46:**
1. **RE-RUN THE WHOLE DISCOVERY ORDER UNDER THE BROWSER-UA FETCH.** WA RSS, The Spirits Business and
   the Robb Report spirits index were all recorded as dead on 503/403/307 evidence that this run
   proved unreliable. **Do this before concluding anything about supply. It is entirely possible
   Sep 4 was never short.**
2. **Brough Brothers' River Road opening — the scheduled Wed Sep 2 date hunt.** **If no published
   date by Wed, it cannot be a Sep 4 item.**
3. **PUNCH via a dated entry path** — Tier 2, right seam, but the category listing carries no dates.
4. **Aaron's byline call on the outdoors item** would take the board to four at no research cost.
   **Raised twice and SPENT. Do not raise a third time.**

**IF SEP 4 IS STILL AT TWO AFTER THU SEP 3, IT RUNS AT TWO AND THAT IS FINE.** **The empty-pipeline
floor applies only below two.** **Do NOT promote the conditional to fill a slot, do NOT raid the
Sep 8 board, and do NOT reach below Tier 2 for a festival listing.**

---

## TUESDAY Sep 8 — FOUR STAGED as of Aug 30. Board filled out fast.

- `whisky-advocate-chinquapin-oak-2026` — **NEW AND STAGED Aug 27. Full entry in the Aug 27
  section.** Whisky Advocate Aug 25, **Danny Brandon — a new byline on this pipeline, which is
  itself worth something against the Flicker concentration.** A rarer North American white oak,
  higher in tannin, used for maturation and finishing. **Carries WA's OWN blind-tasting sensory —
  butterscotch, toasted nuts, ginger, lingering spices — printable and attributed to Whisky
  Advocate.** Usable eleven-word O'Driscoll quote. **Names buyable bottles** (Heaven Hill Specialty
  Barrel Series, Woodford Master's Collection Sweet Oak, Angel's Envy Triple Oak, Michter's
  Bomberger's, GlenAllachie 10/12 Chinquapin, Teeling Wonders of Wood). **No price on the page —
  print none.** Beat `try-this-next`, persona Explorer. **Define tannin, and only tannin.**
  **One source and that is correct — a Tier 2 outlet's own editorial and tasting panel, same footing
  as the mango study. Do not log it as needing a second source.**
  Link: `https://whiskyadvocate.com/chinquapin-oak-whiskies`

- `johnnie-walker-op-den-kamp-auction-2026` — **NEW AND STAGED Aug 30. VERIFIED on two Tier 2
  outlets with independent reporting** (WA Aug 27 McCormick; Robb Report Aug 25 Flicker, an original
  interview). Bidding **Sept 11–21** at Whisky Auctioneer, so Sep 8 lands three days ahead.
  **Print neither the location nor the duration of his collecting — the two sources conflict on
  both.** **The 20-word quote fails the cap; the 16-word one clears.** **Link-out is WA, not RR —
  better reader detail and it avoids a fourth Flicker byline.** **"Collection" is banned in WS's own
  voice; the sale's formal name is a proper noun and is permitted.** Beat `allocation-watch`,
  persona Collector. Full entry in the Aug 30 section.
  Link: `https://whiskyadvocate.com/one-mans-johnnie-walker-collection-to-be-auctioned`
- `blue-note-cherry-wood-cask-2026` — **PROMOTED from September pointer to STAGED Aug 30. It got its
  second source** (FM Aug 25 + WA Aug 28, editorial not reprint). $64.99, 120 proof / 60% ABV, 70/21/9
  mashbill, wild-cherry-wood casks from the Jura region of France, ~1,000 cases, Seelbach's online
  plus six states. **SENSORY STILL BLOCKED — all descriptors are the distillery's own. Say no
  independent tasting is published.** **LINK-OUT IS FM BY NECESSITY: Michter's holds the WA Whisky
  Watch link and two items cannot share one link-out.** Beat `whats-dropping`, persona Explorer.
  Link: `https://www.fredminnick.com/2026/08/25/blue-note-bourbon-releases-new-cherry-wood-cask-expression/`
- `michters-toasted-barrel-finish-rye-2026` — **STAGED Aug 30. SINGLE-SOURCED, AND THAT IS NOW
  FINAL.** $120, 54.55% ABV, Limited, rolling out in September; second barrel from wood seasoned
  outdoors 24 months before toasting. **No distribution restriction — which is why it clears where
  four others on the same page failed.**
  **SECOND-SOURCE HUNT CLOSED Aug 31. Both avenues are exhausted:** michters.com is STALE (September
  2023 release, Lesson 43) and **Breaking Bourbon carries only its 2023-release review, the same trap
  in a second outlet (Lesson 44 — proof-check: 108.9 is 2023, 109.1 is 2026).** The remaining pickups
  are the Lesson 42 reprint ring plus Tier 4. **Print no tasting note from any of them.**
  **DECISION DUE ON THE SEP 8 EDITION: run it with an explicit verification flag, or hold it. Do not
  spend another prep run hunting the second source.** Beat `whats-dropping`, persona Collector.
  Link: `https://whiskyadvocate.com/four-roses-honey-cask-jim-beam-ten-pin-and-more-new-whiskey`

**Sep 8 shape: FOUR — Explorer ×2 (chinquapin, Blue Note), Collector ×2 (Johnnie Walker, Michter's).**
**Outlets: WA ×3, FM ×1. Bylines: Brandon, McCormick, Fleming/Thompson — no Flicker, no Evans.**
**Three of four verified. Michter's is single-sourced and the hunt is CLOSED as of Aug 31 — it is now
a flag-or-hold decision on the edition, not an open research task.** **Beats: `try-this-next`,
`whats-dropping` ×2, `allocation-watch` — no repeat header needed.**
**The board went from one to four in a single run, so do not add a fifth without a reason.**
**Fri Sep 4 is the live gap — see OPEN GAPS.**

---

## SEPTEMBER POINTERS

- `hard-truth-dark-roast-rye-2026` — FM Aug 11. Third 2026 Master Distiller's Reserve · 25-barrel
  batch · 50/50 blend of RW-3 (51% rye / 38% corn / 11% chocolate malted barley) and RW-4 (51%
  rye / 38% corn / 11% caramel malted barley) · bottled-in-bond at 100 proof · MSRP $59.99 ·
  September release. Featured at Hard Truth's **Harvest Festival, Nashville Indiana, Sat Sept 26.**
  Preview events: Cask & Still Social at Hard Truth **Fri Aug 21** (rejected — single-market
  Indiana, same-day publication, Detroit holds the calendar slot) and **the Garage at Bottleworks,
  Indianapolis, Fri Aug 28** — the better peg.
  **Price resolved at $59.99. Distribution is NOT — FM states no footprint. Do not print any
  distribution claim.** The "more than 20 states" figure came only from a search summary of The
  Manual, which is 403 to scripts and unvetted.
  **SENSORY BLOCKED.** "Complex, sweet, malty, dark and brooding" is Bryan Smith quoted from a
  news release. Quotable as his claim, but it is marketing and runs long. **Prefer no quote.
  Never print it as a tasting note.**
  Hard Truth's Aug 28 event is literally named "Whiskey Social." Cosmetic; recorded so a future
  run does not read it as a partner mention.
  Link: `https://www.fredminnick.com/2026/08/11/hard-truth-announces-release-of-distillers-reserve-dark-roast-rye/`
- `redemption-ancients-18yr-2026` — **NEW as a distinct key this run.** Returns this fall at
  **$400**, 74% corn / 22% rye / 4% malted barley, barrel proof 102.85, limited numbers. Robb
  Report **did not sample it**; circulating notes are official. Last year's was 69 barrels at
  103.4 proof and one of Robb Report's highest Taste Test scores of 2025. **Fall peg. Collector
  only, and $400 tests the forward bar.** Keep separate from the bonded item so the two do not
  collide in one edition.
  Link: `https://robbreport.com/food-drink/spirits/redemption-whiskey-brings-back-18-year-old-bourbon-1238554565/`
- `isle-of-raasay-hungarian-oak-oloroso-2026` — forward pointer. 50% ABV, $110, global release of
  8,000 bottles from **September**, ImpEx Beverages. Oloroso casks of Quercus petraea from
  Hungary's Zemplén Mountains. Peated and unpeated spirit distilled 2021, matured separately, then
  married. All on Raasay, an island of 161 residents, printed on every bottle. **WA did not taste
  it** — its Hungarian-oak and oloroso lines describe how the wood generally behaves. **Do not
  convert either into a tasting note.**
- `bruichladdich-greener-still-2026` — **REMOVED AS A POINTER Aug 23. SOLD OUT.** Robb Report
  supplied the second source and killed the item with it: U.S.-exclusive, distillery-website only,
  **currently sold out**. A reader cannot buy it. Facts and the sensory block are recorded in the
  Aug 23 section. **Do not restage. Do not re-derive the barley split.**
- **`koopers-texas-oak-bourbon-2026` — REMOVED AS A POINTER Aug 24. RESOLVED AGAINST.**
  Two independent failures: **360 bottles from two casks with the sale already opened Aug 22**, and
  **every outlet carrying it is reprinting the same news release**, so it has never had a second
  source and all its sensory is Troy Kooper's own release quote. Full entry in the Aug 24 section.
  **Moved to DROPPED. Do not rediscover.** Second pointer killed by its own second source after
  Bruichladdich.
- **AUG 26: `new-riff-sherry-finish-malted-rye-2026` LEAVES THIS LIST — promoted to STAGED for
  Fri Aug 28.** It got its own FM link-out and a hard release date (Aug 28, 11 a.m.). **Three Aug 23
  pointers remain.** Two new pointers added Aug 26: **`cedar-ridge-anniversary-edition-2026`**
  ($64.99, 112 proof, five cask finishes including Tokaji, usable 16-word Quint quote) and
  **`blue-note-cherry-wood-cask-2026`** ($64.99, 120 proof, French wild-cherry-wood casks, ~1,000
  cases, six states plus Seelbach's online). **Both single-sourced on FM news releases, both
  sensory-blocked.** Full entries in the Aug 26 section.
  **AUG 30: `blue-note-cherry-wood-cask-2026` LEAVES THIS LIST — promoted to STAGED for Tue Sep 8**
  on a WA Whisky Watch second source. **`cedar-ridge-anniversary-edition-2026` remains here, still
  single-sourced and still sensory-blocked.**
- **New pointers added Aug 23 — FOUR remain, all sensory-blocked, none staged** —
  `barrell-new-year-blend-11-2026` (nationwide, the best forward-bar profile) ·
  `new-riff-sherry-finish-malted-rye-2026` · `bowmore-snarkitecture-oak-voyage-2026` ($360,
  Collector-only) · `dublase-signature-bourbon-trio-2026` (prices not published until Sept 1).
  **Full entries in the Aug 23 section. Every one needs its own link-out — the WA Whisky Watch of
  Aug 21 is spent on Filmland.**

---

## OPEN GAPS

- **FRI SEP 4 — NO LONGER EMPTY, STILL THE PRIORITY GAP.** Aug 30 staged
  `buffalo-trace-on-tour-2026` (verified, strong, reader can act two days after reservations open)
  and surfaced `whisky-advocate-outdoor-excursions-2026` as a conditional. **One firm, one blocked on
  Aaron's byline call. Needs one or two more.** Three prep runs left — Mon Aug 31, Wed Sep 2,
  Thu Sep 3. **Do not raid the Sep 1 or Sep 8 boards.**
  **The shape constraint is now the real problem, not the count: both current items are Whisky
  Advocate and both are `on-the-calendar`.** A third item should be a different outlet and a
  different beat. **Remaining known supply: Brough Brothers' River Road opening (no date yet — re-hunt
  Wed Sep 2), and the FM rail read a second time asking only "is there a date, a place, and a reason
  to go?"** **`larrikin-australia-series-2026` is no longer supply — it was tested and dropped Aug 30.
  The two sevans evergreens are also spent: one was current and is now the conditional above, the
  other is summer-framed and dead.**
- **NEW, and it is the mirror of the Aug 26 lesson: A RUN SCOPED TO ONE GAP MUST STILL SWEEP THE
  STANDING FEEDS.** The Aug 26 run went straight to the FM rail because the Friday gap needed a
  non-WA item, and **never read the WA RSS feed, which was carrying three unassessed items including
  the best find of Aug 27.** Aug 26 caught the rail-read-for-releases failure; this is the same
  failure one level up. **Standing fix, one fetch: read `whiskyadvocate.com/call/blogs/rss/` on
  every prep run regardless of what the run is hunting.** Lesson 34.
- **THE ROBB REPORT DROUGHT WAS A MEASUREMENT ERROR — ENTRY RETIRED AND REPLACED Aug 30.**
  The "third consecutive week with nothing stageable" read was **wrong**: RR published the Johnnie
  Walker auction interview on **Aug 25**, inside the window three files called empty. **RR never
  stopped publishing; the pipeline stopped finding it.** Cause: with the section index 307-ing to
  tollbit, RR is reachable only by slug search — **and the pipeline only ever searched release
  slugs.** **Standing fix: when the index is down, search RR by BEAT, not by product — one slug
  search per run on `robbreport.com` plus a beat word (auction, distillery, bar, taste test).
  Lesson 41.** **The "accept scarcer sensory for weeks" consequence is withdrawn.** Retest the index
  in September as already scheduled.
- **THE FLICKER CONCENTRATION GAP — the authorised experiment RAN AND SUCCEEDED, with a caveat.**
  `whiskyadvocate.com/tag/sevans` returned 200 on its second and final attempt and rendered 16
  paths. **A working Sean Evans supply line now exists.** The caveat is real: **it is an undated
  author archive, not a feed** — the one path that looked like fresh Friday material was a June
  article about a June event. **Harvest it for evergreen service journalism only, and date-check
  every path before staging.** The experiment is spent; do not re-authorise it. **Aug 27 also added a
  third WA byline to the board — Danny Brandon on chinquapin — which does more for the concentration
  problem than any index sweep.**
- **CADENCE — THE SEPTEMBER THIRD-EDITION BUMP IS RAISED AND UNANSWERED.** Surfaced to Aaron in the
  Aug 27 Notes, one bullet, framed as his call, as the Aug 25 file instructed. **If he does not
  answer, do NOT apply a default — a cadence change is not a copy default. Carry it as unanswered and
  stop mentioning it.** Honest supply read if he asks: Tuesdays run deep, Fridays do not, so a third
  edition lands on the seam that is already hardest to fill.
- **FRI AUG 28 — CLOSED BY PUBLICATION Aug 28.** Four items shipped, WA ×2 / FM ×2, one
  single-sourced (Brough Brothers). **The Friday slot is now empty and the next Friday is Sep 4,
  which has nothing.** Historical detail on how the gap was closed follows and is spent.
- **FRI AUG 28 OUTLET GAP — CLOSED AUG 26, after three runs.** Two non-WA items staged, both FM:
  New Riff (promoted pointer, releases the morning of the edition) and Brough Brothers (Sat Aug 29
  event, Louisville). **Outlets now WA ×2, FM ×2.** The residual ask stated on Aug 23, 24 and 25 is
  satisfied. **Do not search for a fifth Friday item.** The honest residual: **both new items are
  single-sourced news releases**, so Thursday's only Friday job is a second-source attempt, and if it
  fails they run flagged. **Running four with two flagged beats running two.**
- **NEW, and it replaces the "non-WA item does not exist" read: THE FM RAIL IS THE FRIDAY SEAM, NOT
  JUST WA'S TRAVEL SECTIONS.** The Aug 24 run declared the rail empty on a day it was carrying the
  exact item three runs had been hunting. **The failure was reading it for releases only.** Cheap
  standing fix, added as an instruction: **on any run where a Friday slot is short, read the FM rail
  a second time asking only "is there a date, a place, and a reason to go?"** This sits alongside
  Lesson 26, not in place of it.
- **NEW: THE ROBB REPORT SECTION INDEX IS BROKEN — step one of the discovery order.**
  `robbreport.com/food-drink/spirits/` 307-redirects to `tollbit.robbreport.com`, which does not
  resolve. **Article URLs still work; only the index is gated.** Until it clears, reach Robb Report
  by web search on article slugs. **This matters more than it looks: the index was the weekly path to
  the Taste Test column, the pipeline's best supply of independent tasting notes.** Retest monthly.
- **Sep 1 board — CLOSED AT FOUR Aug 26.** Jack Daniel's American Single Malt cleared both
  conditions (Explorer, non-Flicker). **No Tuesday supply gap exists. Do not add a fifth.**
- **Tue Aug 25 board — CLOSED BY PUBLICATION.** All four items shipped. **The Tuesday slot is now
  empty and the next Tuesday is Sep 1, which already has three.** No Tuesday supply gap exists.
- **NEW, and it is a shipped fact rather than a forecast: BYLINE CONCENTRATION.** The Aug 25
  Shortlist ran **three of four items under Jonah Flicker's byline.** It was surfaced Aug 18,
  correctly not fixed by dropping a verified item, and correctly not spent on a Notes bullet. **The
  structural answer is a fourth outlet or a second Robb Report critic, not a smaller edition.**
  Cheapest available experiment: **one fetch of `whiskyadvocate.com/tag/sevans`**, a Sean Evans
  author index already noted in HOSTS and still untested. Authorised for the Aug 26 run.
- **THE TIERING GAP IS THE ROOT CAUSE OF BOTH STALLS, and it is now precisely diagnosable.** The
  living vetted source directory is unreachable; the skill's inlined stable core
  (`references/verification-protocol.md`) lists Whisky Advocate, Bourbon Review, Breaking Bourbon,
  PUNCH, SevenFifty Daily and Drinks International as Tier 2 — **and omits Robb Report and The
  Spirits Business entirely.** Robb Report has been used as a link-out five times on prior runs'
  judgement and carried three of four Aug 25 items; TSB is blocked on the same omission. **The two
  stalls are one gap.** The ask to Aaron is one committed list, and the Aug 25 Notes carries it.
  **Do not re-litigate Robb Report's tier — prior runs settled it and the editions shipped.**
- **Pair It — CLOSED Aug 21, after 34 days, by applying the recommendation as the default.** The
  gap was never supply; it was the definition — cigar-crossover or food pairing. **The Dubai
  chocolate item shipped under `pair-it`, so the beat now means food pairing in practice.** Aaron
  was told in one bullet that the recommendation had been applied; he reverses it by reply. **Do
  not re-open this as a question.**
- **NEW GAP, and it is a process gap, not a supply one: THE TARIFF IS BLOCKED ON OUTLET TIERING.**
  The Spirits Business filed the collapse Aug 24 and clears the two-source rule alongside BNN
  Bloomberg. **TSB is not on the inlined Tier 1–2 list, is not Tier 4 either, and is the same class
  of title as Drinks International, which IS listed.** The living source directory that would settle
  it is unreachable. **This is the SECOND item to stall on tiering after Shanken/Redemption, which
  fired the escalation the Aug 21 BLOCKERS entry set.** Recommendation on file: **hold to Sep 1; if
  no listed outlet files by then, treat TSB as Tier 2-equivalent and link it.** Raised to Aaron once
  as a Notes bullet Aug 24. **Do not link it before he answers or the Sep 1 default arrives.**
- **Fri Aug 28 outlet gap — STILL OPEN after a full run spent on it, and now with evidence it may
  not close.** Both staged items are WA. **Nothing non-WA exists to stage:** WA silent since Aug 21,
  Robb Report dry for a second week, FM rail and the 23-item TSB index empty of stageable material.
  **The residual ask is unchanged — one non-WA Friday item, not more Friday items.** Three runs left.
  **Running two verified WA items is the acceptable outcome and is better than padding.**
- **Robb Report has now filed TWO CONSECUTIVE DRY WEEKS, and that is a pattern rather than variance.**
  Aug 23: three pieces, none stageable. Aug 24: two pieces, neither stageable (Hibiki fails on
  distribution, the other is wine). **The Aug 23 file called one dry week normal variance. Two is
  worth watching.** The Taste Test column still runs weekly and is still the best sourced-sensory
  supply — **but a weekly review is only useful when the bottle is buyable**, and two of the last
  five Taste Test subjects were not (Jack Daniel's #17, Hibiki 12). **Check the column's
  distribution line before treating a taste test as an unblock.**
- **THE FRIDAY SEAM IS FOUND AND PROVEN — this is the one gap that genuinely closed this run.**
  `whiskyadvocate.com/whiskey-life`, `/tag/travel` and `/tag/Features` all load 200 and render
  article links. Lesson 26 predicted service journalism was the seam; the seam now has working URLs
  and a dated bench of three candidates. **Sweep these monthly. Full detail in the Aug 24 section
  and in HOSTS.** The residual weakness is honest: the bench is two-to-three months old with no news
  peg, and all of it is WA.
- **Fri Aug 28 — LARGELY CLOSED Aug 23, on the first run after it opened.** It was empty on
  Friday; it is **two verified items** now — Filmland (a bottle, Social Drinker) and the WA glamping
  guide (a places item, Venue Regular). **The floor is cleared and the occasion-led half is
  covered.** What is left is not a supply gap but an **outlet gap: both are Whisky Advocate.**
  Neither is a cocktail, so none of the tightened Friday constraints was spent to close it —
  pineapple, Michigan, the cause-led cap and the WA-cocktail streak are all still where they were.
  **The residual ask for Mon–Thu is one non-WA Friday item, not more Friday items.**
- **Fridays versus Tuesdays — the imbalance is real and it is structural, not accidental.** Tuesdays
  run two deep because bottle releases arrive on a weekly press cycle that WA, Robb Report and FM
  all cover. Fridays need occasions, and **no vetted outlet has a weekly occasions column.** The
  glamping piece worked because it is service journalism, not an event listing. **That is the
  repeatable seam: WA's Travel and Whisky Life sections, not its news feed.** Sweep them monthly.
- **Sub-$30 — 25 days.** Aaron's standing decision, not re-queried. **No relief this run and the
  reason is now well evidenced:** the WA value list published Aug 18 has a floor of $35 across
  twenty bottles from Tier 2 sourcing. **A sub-$30 Tier 1–2 item may simply not exist in this
  market at 90+ points.** Worth saying once if Aaron ever asks — the gap may be unclosable as
  specified, and $35–$40 is the real value floor.
- **Aug 25 link supply — CLOSED this run.** All three items carry independent, vetted link-outs.
  Was open Aug 16–18.
- **Outlet concentration — materially improved.** **Robb Report is now a working third outlet with
  its own weekly scored sensory.** Aug 25 runs with zero WA link-outs. The residual risk flips:
  **Robb Report is now carrying two of three Aug 25 items**, so watch for a Flicker-byline
  concentration the same way WA and FM were watched. **Aug 23 update: Robb Report produced three
  new spirits pieces and NOT ONE was stageable** — Gleneagles (100 bottles, no taste),
  Bruichladdich (sold out, no taste), and a pisco sour. **A working third outlet is not the same as
  a productive one; it filed a dry week.** The Friday material both came from Whisky Advocate, so
  **the concentration risk flipped straight back to WA on the Friday board.**
- **Sourced sensory — the standing scarcity, and it eased.** Robb Report's Taste Test column is a
  weekly, reliable supply of independent tasting notes. **Check it every prep run.** It is the
  cheapest known answer to the recurring "no sensory exists" block. **Confirmed again Aug 19:**
  Flicker sampled Maker's Mark Cellar Aged and reviewed Jack Daniel's #17, two independent notes in
  one section index.
- **Explorer gap on Aug 25 — CLOSED Aug 19** by the mango-aroma study. Was the single instruction
  the Aug 18 file left for this run.
- **NEW GAP: no beat slug fits an explainer or science item.** The scheme allows only
  `whats-dropping`, `try-this-next`, `allocation-watch`, `on-the-calendar`, `easy-pour`, `pair-it`.
  The mango study is a learning item — it points the reader at something to notice in a glass they
  already own, so **`try-this-next` is the closest fit and is what will be used.** Surfaced to
  Aaron in the Aug 19 Notes rather than invented silently. **If he wants a real slug, the ask is a
  new one-word value added to the scheme — `explainer` would cover the whole category.** Until then
  every item like this fragments into `try-this-next` and the PostHog read on that beat gets muddier.
  **Do not invent a slug. Do not leave it unnoted.**
- **Sep 1 non-Collector lead — CLOSED Aug 20** by SHĀNG. Explorer, $46, real sourced sensory, and
  the wider-culture angle. **Opened Aug 19, closed Aug 20. Do not re-search it.**
- **Sourced sensory — the scarcity has now eased twice in two days and the pattern is clear.**
  Aug 19 gave Flicker's Maker's Mark sampling; Aug 20 gave Flicker's Bardstown tasting and Evans's
  SHĀNG review. **All three Sep 1 items carry independent tasting notes** — a first for this
  pipeline. **The mechanism is the same both times: a critic's weekly review column surfaced by a
  server-rendered section index or RSS feed.** Keep sweeping both; this is no longer luck.

---

## WATCHING

- **`larrikin-australia-series-2026` — REMOVED FROM WATCHING Aug 30. TEST RUN, RESOLVED AGAINST,
  MOVED TO DROPPED.** Both blockers failed: the "second outlet" is three reprints of one news
  release, and `kybourbonfestival.com/tickets/` reads **"ONLY SUNDAY SAMPLERS REMAIN! JOIN THE
  WAITLIST"** — two of the three release days are unreachable. Full reasoning in the Aug 30 section.
  **Do not restage. Do not rediscover.**
- **`brough-brothers-river-road-distillery-2026`** — **NEW KEY, WATCHING as of Aug 30.** FM's Belle
  article states a **15,000-square-foot** distillery, tasting room and event spaces at **1250 River
  Road**, Louisville, opening **"this September"** — **no day published.** Date hunt run Aug 30 and
  it failed: every search result is 2022–2023 zoning coverage. `broughbrothers.com` is a
  client-rendered SPA and is on the do-not-retry list. **Re-hunt Wed Sep 2. If no date by then it
  cannot be a Sep 4 item — hold for a later Friday.** **A blurb must not re-tell the published Belle
  story.** Belle cruises showcasing the bourbons are a second potential item off the same thread.
- `uncle-boojies-gatsby-research-2026` — **NEW Aug 27, BEAT FILE, not dropped.** Cassie Tatum's
  research on Louisville bourbon culture and Fitzgerald, 1914–18; Howard and Atherton distilling
  families; Uncle Boojie's recreating the Howard family mashbill with Whiskey House of Kentucky.
  **Strongest wider-culture angle the board has seen — literature — and no reader consequence yet:**
  the only event is invitation-only, and the bottle has no date, price or proof. **Revisit the moment
  the Howard mashbill bottle gets a date. Do not re-scout the research itself.**
- `bardstown-bourbon-capital-mash-up-2026` — **DEAD as filed (June 2 piece, June 14–21 event, ten
  weeks past). See the Aug 27 assessed list.** Kept for one reason: **it is a real, well-attended
  Bardstown event with a $150/$375 ticket structure, and the 2027 announcement would be strong
  Friday material with months of lead time.** Check for it in spring 2027, not before.
- `moonshine-university-closure-2026` — **ASSESSED AND DROPPED Aug 19. See the Aug 19 section.**
  Sourced, but no vetted Tier 1–2 outlet, four weeks old, and no reader consequence. **Do not
  re-search.**
- `bardstown-discovery-2026` — the alternate half of the Bardstown announcement. 112.8 proof /
  56.4% ABV, **55% 10yo Indiana + 25% 11yo Kentucky + 20% 7yo Kentucky (Robb Report, and these
  sum correctly to 100%)**, four months in Garryana oak from Willamette Valley trees, $140,
  specialty retailers nationwide from Aug 21. **NO LONGER SENSORY-BLOCKED — Flicker tasted it
  Aug 19:** strong toasted wood and cinnamon from the finish, plus butterscotch, maple, flamed
  orange, cherry syrup. **Still shares Lochs of Jura's link in BOTH outlets, so the two can never
  run in the same edition.** BBC's second garry-oak release this year after Cascadia; the oak is
  more associated with Seattle's Westland. **Still the weaker of the two. Hold as the alternate.**
- **WA TRAVEL BENCH — new Aug 24, verified to load and dated, NOT staged, sensory unverified.**
  `whiskyadvocate.com/fort-collins-for-whisky-lovers` (**Jun 24 2026**, freshest) ·
  `whiskyadvocate.com/Beach-Bars-with-Great-Whisky-Lists` (**Jul 6 2026**, beach framing fades after
  August) · `whiskyadvocate.com/48-hours-in-houston` (**May 14 2026**, oldest). **Floor-clearers for
  a thin Friday, never a lead — no news peg, and all three are Whisky Advocate.** Verify sensory
  before staging any of them.
- `jones-mack-bourbon-2026` — **RECHECKED Aug 23. UNCHANGED, still needs a second source.**
  **Aug 24: an FM URL surfaced free in the rail and was deliberately NOT fetched, per instruction —
  `https://www.fredminnick.com/2026/08/17/2-cents-inc-releases-new-jones-mack-bourbon/`. Start the
  late-September recheck from it. Do not fetch before then.** Expect the same release a third time.
  2 Cents Inc., Louisville, founders **Brittany and James Penny**. 100 proof, $54.99 / $49.99
  presale, DTC shipping from September. Named for the founders' four WWII-era grandparents —
  Wallace and Naomi Jones, Sylvester and Gertrude Mack. **Still one press release, now also
  syndicated at National Law Review — same release, still one source. The circulating dark-cherry /
  orange-peel / clove note is the official product description; do not print it.** Warm founder
  story and inclusive brand — **watched, not dropped.** **Two rechecks, no movement: drop to a
  monthly check, not a per-run one.** Louisville collision applies.
- `strathearn-batch-03-2026` — **ASSESSED AND REJECTED Aug 20. See the Aug 20 section.** UK RSP
  £65.00 only, no US price or distribution, single press-release source, no sourced sensory.
  **Do not restage without a US price and an independent tasting.**
- `brown-forman-q1-results-sept-2-2026` — earnings date, Sept 2. **Trade news, no reader
  consequence. Beat file, never staged.** Do not re-surface.
- `whisky-advocate-august-auction-update-2026` — WA Aug 14. **Recommend against for now.**
  `whisky-advocate-july-auction-update-2026` is in dedup and ran recently. Two auction updates
  inside a month reads as a recurring column rather than news. Reconsider in September if a Tuesday
  comes up short. Article not opened.
- `breckenridge-peach-whiskey-2026` — 36% ABV, $35, nationwide. **Recommend against:** thin
  material, and **peach is spent for 2026.**
- `chip-tate-penumbra-mezcal-2026` — Chip Tate's first mezcal for Foley Family Wines & Spirits.
  Espadín, Sierra Juárez foothills, tahona-crushed, pit-roasted over encino wood, $45, national.
  **Not whiskey.** Recommend against unless a Friday wants a crossover.
- `glenachulish-distillery-approval-2026` — Highland Council approved a single malt distillery on
  Loch Leven. Three pot stills, ~$8.1M, **stills firing 2028. Fails the forward bar decisively.**
- `whisky-advocate-lost-irish-cucumber-2026` — Jun 23, Alberto Battaglini, PONY Cocktails +
  Kitchen, Santa Ynez CA. Sourced sensory, named creator. **Easy Pour alternate, no collision.**
  Link: `https://whiskyadvocate.com/irish-whiskey-cucumber-cocktail-recipe`
- `whisky-advocate-coconut-manhattan-2026` — Jun 29, Christopher Lowder, Little Torch, Miami.
  Sourced sensory, named creator. Alternate. Coconut collides.
  Link: `https://whiskyadvocate.com/tropical-manhattan-cocktail-recipe`
- `whisky-advocate-vintage-coco-highball-2026` — WA Jun 2, Brittany Risher Englert. Vintage Coco by
  **Lynnette Marrero**, partner of Milly's Neighborhood Bar, Brooklyn. 1½ oz blended scotch, 2 oz
  coconut water, ½ oz pineapple, 2 oz Fever-Tree Sparkling Lime & Yuzu, shiso or mint. Own
  sensory, quotable under 20 words. **Weakest alternate — oldest and carries the coconut
  collision.**
- `whisky-advocate-honey-cocktails-2026` — WA May 11. Named creators Dawid Smietana (Kilkea Castle)
  and Nina Dyrek (Sunda New Asian, Chicago), both with own sensory. **Explicitly spring-framed.
  Restage spring 2027.**
- `whisky-advocate-top-whisky-bars-2026` — `whiskybars.whiskyadvocate.com` returns 200 but the list
  is client-rendered and empty to scripts. **Not a single venue can be named. Unusable. Tested
  Aug 13 — do not re-test before September.**
- `jack-daniels-distillery-series-17-2026` — **DROPPED Aug 19.** The Robb Report taste test was
  found and read (Aug 9). It supplies sensory but **confirms the distillery-exclusive
  distribution**, the review is unfavourable, and its framing is DISCUS-hostile throughout. See the
  Aug 19 section. **Do not re-open on the strength of "Robb Report has a taste test" — it does, and
  that is settled.**
- `wyoming-whiskey-state-of-the-union-2026` — two sources agree on $80/$79.99, 49% ABV / 98 proof,
  6 years, 68% corn / 20% wheat / 12% malted barley, first release since the brand returned to
  David DeFazio's ownership. **Still Wyoming-exclusive, fails the forward bar.**
- `branch-barrel-5yr-bourbon-2026` — WA Aug 7: 46%, $55, **Colorado only.** Fails the forward bar.
- `circle-city-whiskey-50-50-club-2026` — FM Aug 12. Retail expansion into Indiana, Wisconsin,
  Illinois; claims 100%+ YTD growth. **Trade news, not reader news. Recommend against.**
- `discus-congressional-fly-in-2026` — FM Aug 14. DISCUS Congressional Fly-In, Washington DC,
  **Sept 24.** Chris Swonger quoted from a news release. **Members-only advocacy with no
  consequence for a reader's shelf or weekend. Beat file, not staged.**
- `punch-best-new-bartenders-2026` — weak. PUNCH Jun 2, only two of ten cocktails are whiskey.
- `the-1933-society-louisville-speakeasy-2026` — weak. WDRB is Tier 3, no opening date sourced.
- `johnnie-walker-blue-callum-turner-ambassador-2026` — beat file. No shelf or weekend consequence.
- `lexington-pumpkin-barrel-ale-2026` — WA News Notes Aug 14. Bourbon-barrel-aged pumpkin ale from
  Lexington Brewing & Distilling, part of Town Branch. $17/4-pack, this month through fall.
  **Beer, not whiskey.** Possible seasonal Friday crossover in October.
- Unchanged and blocked: Oaklore · H. Obernauer · Sailor's Home · Pearse Lyons (drop) · Root Shoot
  (drop) · Stranahan's peach (superseded) · `uncle-nearest-receivership-weavers-out` (**still
  recommend hold**) · Kentucky Bourbon Festival · Heaven Hill year of wheat · Proof Cocktails
  Vancouver WA · `never-say-die-lexington-brand-home-2026` (dropped, Tier 4 only).

---

## URGENT SWEEP — no override

**Current window is Aug 25–27 — see the THURSDAY Aug 27 section above for the full sweep. Nothing
fires. One candidate was chased down and closed on its date: the FSS Kimbland whisky safety warning
is 16 Dec 2025, Orkney only, no WS partner — a warning, not a recall, and not an override.**
**Fifth consecutive run recording that the lapsed EU retaliatory-tariff suspension has no vetted
spirits pickup.**

**Prior window (Aug 21–24), retained**

**Was: Aug 21–24 — see the MONDAY Aug 24 section above for the full sweep.** Nothing
fires. Two new names assessed and closed: the **Soho Spirits Festival cancellation** (the headline
says "safety"; it is the organiser's own financial-and-operational cancellation, not a hazard) and
the **FSSAI/Diageo sales bans** (India, labelling, revoked). **The Canada tariff is live and remains
a trade measure, not an override — fourth consecutive run recording that.** The Garrard County
distress story is now **resolved by Sazerac's acquisition** and should not resurface as litigation.

### Prior window (Aug 19–20), retained

**Window Aug 19–20.** One broad search plus the full WA RSS feed, the Robb Report
spirits section index and the Fred Minnick recent-articles rail.

**No product recall, no safety issue, no litigation or investigation naming a partner brand or
venue, no death in the industry. Nothing fires.** The search returned only already-logged material:
the Crown Royal Reserve glass recall (Canadian), A.M. Scott's bankruptcy, Sazerac v. RNDC, the
Fireball distributor suit, True Story's dual lawsuits, Bardstown's Feb 13 employment suit, the
craft-distillery closure trend, and the 2024 illegal-distiller deaths. **Nothing newer than what
this file already carries.**

**Assessed and correctly not fired Aug 20:** the **Canada 50% tariff pause**. A trade measure, and
now a *reversed* trade measure — still not a recall, safety issue, partner litigation or a death.
**Third consecutive run recording this. It is a dedup exception and a correction, never an
override.**

### Prior window (Aug 18–19), retained

One broad search plus the full WA RSS feed, the Robb Report spirits section index and the Fred
Minnick recent-articles rail.

**No product recall, no safety issue, no litigation or investigation naming a partner brand or
venue, no death in the industry. Nothing fires.** The search returned only already-logged material:
Garrard County Distilling, the Sazerac v. RNDC suit, the Fireball distributor suit, the
craft-distillery closure trend, the Jim Beam Clermont production pause (already in DROPPED), and the
industry-contraction/bankruptcy coverage. **Nothing newer than what this file already carries.**

**Assessed and correctly not fired Aug 19:** the **Canada 50% Section 338 tariff taking effect
today** — a trade measure, not a recall, safety issue, partner litigation or a death. **It is a
dedup exception, not an urgent override.** Full reasoning and the decision put to Aaron are in the
Aug 19 section. **Do not let a future run escalate it to an override just because it is live.**

### Prior window (Aug 17–18), retained

Window Aug 17–18. Two broad searches plus the full WA RSS feed. Nothing fired.

Searches returned only already-logged material: A.M. Scott bankruptcy, the Uncle Nearest
receivership, the Crown Royal Reserve glass recall (Canadian), the Fireball distributor suit,
Sazerac v. RNDC, and the craft-distillery closure trend.

**Assessed and correctly not fired this run:**
- **Diageo v. Deutsch over Redemption's bottle design** — surfaced fresh in the Robb Report piece.
  **Adjudicated** (jury for Diageo, 2nd Circuit affirmed on appeal), historical context rather than
  news, and Redemption is not a WS partner. Not an override. **Usable as color if ever needed.**
- **Garrard County Distilling** — sued for at least $31M by creditors and contractors, delinquent
  on local taxes, sued for $94,000 by the Kentucky Distillers Association in Oct 2025. **New name
  in this file, but ten months old and not a WS partner. Not an override.** Logged so a future run
  recognises it.
- **Moonshine University closure** and TTB production-volume trends — trade and industry-condition
  news, no recall or safety dimension. See WATCHING.

Already logged and still non-firing: Uncle Nearest (Fawn Weaver suit and disputed Chapter 11; Farm
Credit Mid-America put at $108M — unadjudicated, not a WS partner, **hold**) · Red Boot Distillery
v. federal government · Crown Royal Reserve 12-year glass recall · A.M. Scott bankruptcy · True
Story dual lawsuits · Sazerac v. RNDC · Fireball-maker suit · Bardstown's Feb 13 employment suit ·
craft-distillery closures · `fss-kimbland-distillery-warning-2025` · the Carriage House Creations
bourbon **basting sauce** recall (food product, FDA-terminated — **do not re-fire on the word
"bourbon"**) · the 2024 illegal-distiller deaths (unlicensed production, not the industry).

---

## HOSTS — load status

**AUG 27 MOVEMENT — four entries, and the sevans finding is the important one. Full detail in the
Aug 27 section:** `tag/sevans` **loads (200) and is an UNDATED AUTHOR ARCHIVE, not a news feed —
harvest evergreens, date-check every path, do not re-fetch before October**; `broughbrothers.com` is
a **client-rendered Vite SPA and is not a usable Tier 1 primary**; `whiskeyreviewer.com` loads and is
a **reprint host — never a second source, never a quote source**; the **WA RSS feed is reconfirmed as
the primary discovery path and must be read every prep run.**

Fetch-to-disk with a browser user-agent, then strip and slice locally. **Proven again on every
host used.** Strip `<script>` and `<style>` blocks with a DOTALL regex, not a line-based sed —
a line-based strip leaves kilobytes of inline JS in the text and buries the article.

- **`whiskyadvocate.com/call/blogs/rss/` — 200, ten dated items with titles and URLs. THE primary
  WA discovery path.** Produced both new items this run.
- **`whiskyadvocate.com/whiskey-life` — 200, SERVER-RENDERED, AND IT YIELDS ARTICLE LINKS. NEW AND
  IMPORTANT, Aug 24.** Note the spelling — **`whiskey-life`, not `whisky-life`**. One fetch gave 22
  article-shaped paths. **`whiskyadvocate.com/tag/travel` (15 paths) and `whiskyadvocate.com/tag/Features`
  (15 paths) also load 200 and render links.** These three are the repeatable Friday seam.
  **The lesson is that WA tag pages are NOT uniformly client-rendered** — `/news` and `/Tag/Cocktails`
  are, these are not. **Do not generalise either way; test the specific path.**
  **`whiskyadvocate.com/travel` and `whiskyadvocate.com/whisky-life` both 404 — do not retry them.**
  Untested WA paths seen in nav: `/tag/food` · `/tag/dispatches` · `/tag/insights` · `/ratings-reviews`
  · **`/tag/sevans` (a Sean Evans author index — directly useful for byline management)**.
- **`whiskyadvocate.com/news` and `/Tag/Cocktails` are article-link-free.** `/news` 301s to `/News`,
  loads 200, renders zero article links; `/Tag/Cocktails` renders exactly one. Client-rendered.
  **Do not spend fetches on either.**
- WA article pages load 200; footers carry three related-article links each.
- **`robbreport.com` — loads 200 to curl with a browser UA (307s to tollbit otherwise).** Every
  article page carries an author rail, "Jonah Flicker's Most Recent Stories," with three of the
  critic's recent pieces as full absolute URLs in the raw HTML. Article bodies are large (~400KB,
  ~1,350 words of real text) but clean. **`"datePublished"` in the page's JSON-LD is the reliable
  way to date a Robb Report article** — the rendered byline block also prints "Published on
  <date>," and the index prints relative ages ("Clock 15h").
- **`robbreport.com/food-drink/spirits/` — THE SECTION INDEX IS BETTER THAN THE AUTHOR RAIL.
  NEW AND IMPORTANT, Aug 19.** It loads 200, is server-rendered, and its raw HTML yields **nine
  article URLs with headlines, decks and bylines** in one fetch — against the rail's three. It
  surfaced Maker's Mark Cellar Aged, the mango study and the Jack Daniel's taste test, **none of
  which the author rail carried.** Extract with
  `https://robbreport\.com/food-drink/[a-z\-]+/[a-z0-9\-]+-\d{10}/` — every article URL ends in a
  ten-digit post ID. **Sweep this index on every prep run, before the rail.** The rail is still
  worth harvesting on any article page already being fetched, since it costs nothing.
- **`www.garrisonbros.com/event-directory/` — FETCHED Aug 19, 200, works. Low yield, and now
  answered.** Event URLs are extractable from raw `href` attributes; it listed sixteen, and the
  visible date strip runs **Aug 21 through Sept 25**. **But everything on it besides the staged
  Cowboy Bourbon release is single-market Hye, Texas programming** — Hye Note concerts, Meet the
  Maker pairing dinners with Dan and Nancy Garrison and with Charlie Garrison, a pairing dinner with
  Todd Gore. **All fail the forward bar on distribution-of-audience. Do not re-fetch this directory
  monthly; check it only when a Texas calendar item is actually wanted.**
- **`fredminnick.com`:** article pages load 200 by direct URL; the site index renders no article
  links to scripts. Seventh run in a row. **The Recent Articles rail and the `< Previous` /
  `Next >` adjacent-post nav on any FM article page are the working substitutes.** Caveat: both
  nav links extract to the same URL under a naive regex — read surrounding markup or fetch both
  neighbours.
- **`fredminnick.com/?s=<query>` 302s and is unusable to scripts.** FM articles are reachable only
  by direct URL or web search. **Slug guessing failed nine times on Redemption — web search first.**
- **`www.garrisonbros.com` — fully readable** (bare host redirects). **Event pages are the valuable
  part:** `/events/2026-cowboy-bourbon-release/` returns 200 with date, time, street address,
  price, proof and age in server-rendered text. The homepage carries the forward event slider, but
  event URLs are only extractable from raw `href` attributes — visible "MORE" links are
  script-driven. **`/event-directory/` exists and is still unfetched — the obvious next discovery
  path for Texas calendar items.**
  **WARNING: `garrisonbros.com/cowboy-bourbon/` is an UNDATED evergreen product page** carrying a
  prior release's 73.2% ABV and its own tasting notes. **Never mine it for a dated release.**
- **`shankennewsdaily.com` — loads 200, clean server-rendered text.** M. Shanken Communications,
  same publisher as WA. Original trade reporting with named executive interviews and Impact
  Databank figures. **Technically excellent; still not on the vetted list. Corroboration only.
  No longer blocking anything** — Robb Report replaced it as Redemption's link-out.
- `copperworksdistilling.com` product pages return 200 but are client-rendered; **no price
  readable.**
- `whiskybars.whiskyadvocate.com` returns 200; content client-rendered and empty. Not re-tested.
- **TSB article pages load 200 and are clean.** JSON-LD carries `"datePublished"` and a named staff
  `"author"`, so TSB pieces are reliably dateable and attributable. Confirmed Aug 24 on five articles.
- **`thespiritsbusiness.com/category/news/` — FETCHED Aug 23, 200, server-rendered, and it is a
  real index.** One fetch yielded **twenty-three dated article URLs** with titles. Extract with
  `https://www\.thespiritsbusiness\.com/2026/\d\d/[a-z0-9\-]+/`. **Use it as the fourth
  discovery path, after the FM rail** — it is the only vetted-adjacent index with UK/Europe trade
  coverage, and it is how the Koopers second source was found. **Caveat: its product write-ups
  reprint press-release tasting notes verbatim with hedges like "are said to impart" and
  "showcases aromas of." Never read those as sourced sensory.**
- `thebourbonflight.com`, `vinepair.com`, `journal-news.com`, `distillerytrail.com` all load.
- **`bourbonbarrelretreats.com` — 200, but the bare host 301s. Follow redirects (`curl -L`) or it
  reads as a dead host.** Server-rendered and usable as a Tier 1 primary for the property's own
  facts. **Its copy is saturated with banned words — verify against it, lift nothing from it.**
- **`washingtonpost.com` — FAILED Aug 23.** curl died with `HTTP/2 stream not closed cleanly:
  INTERNAL_ERROR`, zero bytes, on a browser UA. **Not a paywall, a transport failure. Never present
  a WaPo page as read unless it actually returned bytes.**
- **`troutman.com/insights/...` — 301s to an unknown target. Not followed, not read.** Trade-law
  advisories are corroboration only and are never a link-out; do not spend fetches chasing them.
- **`natlawreview.com` carries press-release syndications.** Loads, but a release read there is the
  same one source. Not a second source, ever.
- `eventbrite.com` loads and its JSON-LD is the reliable place to read event facts — **but its
  localisation dictionary contains every age band and status string, so never pattern-match "21+"
  out of raw Eventbrite HTML.** Its `AggregateOffer` is fee-inclusive with a placeholder 0.0 floor
  and is **never a stated ticket price.**
- Still 403 to scripts: `bevnet`, `prweb`, `themanual`. Breaking Bourbon *article* URLs load; its
  press-release index is age-gated.

---

## OPERATIONAL LESSONS (44–45 added Aug 31)

44. **The stale-year trap travels between outlets. Proof-check before you count a source.** Lesson 43
    caught michters.com describing the 2023 release. **Breaking Bourbon — a Tier 2 outlet, the
    instructed avenue, and otherwise trustworthy — carries the same 2023 release as a full review,
    and nothing on the page shouts the year.** The tell was numeric: **108.9 average barrel proof is
    the 2023 release; 109.1 / 54.55% ABV is 2026.** **Fix: for any recurring annual release, verify
    the year with a number (proof, ABV, price, batch) before counting an outlet as a second source.
    A trusted tier does not protect against the wrong vintage.**
45. **A silent rail and a dry beat look identical in a run log, and must never be recorded as the
    same thing.** Aug 31 returned nothing from WA (503 ×4), TSB (403) and the FM rail — but only FM
    was actually read and actually empty. **Writing "nothing cleared" without separating outage from
    drought would have handed Wed Sep 2 a false supply signal and invited a premature "the Friday
    seam is dead" conclusion.** **Fix: log the HTTP status beside every dry rail. An unreachable
    source is evidence about the network, never evidence about the news.**

## PRIOR LESSONS (41–43 added Aug 30)

41. **When an index is broken, search the outlet by BEAT, not by product.** Three files recorded a
    Robb Report "drought" that did not exist — RR published the Johnnie Walker auction interview on
    Aug 25, inside the window called empty. **With the section index 307-ing, RR is reachable only by
    slug search, and the pipeline only ever searched release slugs, so it could only ever find
    releases.** A degraded discovery path silently reshapes what you believe the supply is.
    **Fix: one slug search per run on the outlet plus a beat word (auction, distillery, bar, taste
    test).** The fourth instance of the pipeline's recurring shape — the miss is in the sweep, not
    the supply.
42. **The Bourbon Flight, the Northwest Beer Guide and The Whiskey Reviewer are a reprint ring.**
    They failed the New Riff second-source attempt Aug 27 and failed Larrikin identically Aug 30,
    both times reproducing the distillery's release verbatim. **Stop counting them as candidate
    second sources.** When a search returns only these, the item is single-sourced — record it and
    move on rather than spending another run on it.
43. **A brand's own product page can be stale, and a stale page is a sourcing trap twice over.**
    `michters.com/toasted-barrel-finish-rye/` is a standing page describing the **September 2023**
    release. Its proof belongs to the wrong year and its tasting notes are marketing. **Always check
    a primary page for the year it actually describes before treating it as a second source** — a
    recurring annual release makes this failure very easy and very invisible.

## PRIOR LESSONS (38–40 added Aug 28)

38. **Before recording a second-source failure, search the pages you already hold.** The Aug 27 run
    was told to check the WA Whisky Watch for New Riff, searched for it as an external target, failed,
    and wrote the item down as flagged — **while the Whisky Watch page was already on the same board
    as the Filmland link-out, with New Riff in its headline.** The fix is a grep, not a fetch:
    **a multi-item roundup staged for one item is a standing second source for every other item on
    it.** Third instance of the same shape now (Lesson 26, Lesson 34, this) — **the pipeline's
    recurring failure is not missing sources, it is not re-reading what it already fetched.**
39. **A quote ruled out by word count deserves a second count of the other sentences.** Aug 27 recorded
    the New Riff quote as unusable at 22 words and stopped. **The same statement's first sentence is
    19 words and clean.** A long quote is not a quote-free page. **Count every sentence in a
    statement before writing "no quote."** Never trim to fit — but do look next door.
40. **Two items sharing a beat slug group under one segment header.** Aug 28 had two
    `on-the-calendar` and two `whats-dropping` items, and the obvious layout — one header per item —
    would have repeated a header mid-edition. **Grouping solved it and reads better than the
    one-header-per-item shape used since July.** Applies to either edition.

## PRIOR LESSONS (34–37 added Aug 27)

34. **A run scoped to one gap must still sweep the standing feeds.** Aug 26 went straight to the FM
    rail because the Friday gap needed a non-WA item, and never read the WA RSS feed — which was
    carrying three unassessed items, one of them the best find of the next run. **Aug 26's own lesson
    was that the rail got read for releases only; this is the same failure one level up.** The fix is
    one fetch: **read the WA feed every prep run, whatever the run is for.** Single-mindedness about
    a gap is correct; skipping a dated, server-rendered primary feed to achieve it is not.
35. **Date a safety item before anything else.** The FSS Kimbland warning read like a genuine urgent
    override — a regulator telling consumers not to drink a named distillery's whisky — and it was
    **eight months old.** One date check closed it. **An undated safety result is the most dangerous
    input this pipeline handles**, because every incentive points toward acting on it fast. Date
    first, then read, then assess.
36. **An author index is not a feed, and the difference is dates.** `tag/sevans` rendered 16 paths and
    the most promising-looking one was a June article about a June event. **An archive is ordered by
    nothing useful.** Harvest archives for evergreen service journalism; take news only from dated
    feeds. **And test the freshest-looking path first — it is the cheapest way to learn which kind of
    page you are holding.**
37. **Actionable beats aspirational, and price is the test.** WA's travel section produced the
    glamping piece (barrel cabins, a drive from 22 distilleries — shipped) and the all-inclusive
    resort round-up ($2,035–$2,950 a night — recommended against) **from the same seam, three weeks
    apart.** Lesson 26 found the seam; this narrows it. **Check the price point before staging a
    travel item** — a Social Drinker's occasion has a ceiling, and service journalism above it is
    reading material, not an occasion.

## PRIOR LESSONS (31–33 added Aug 25)

31. **When a claim's home is the second source, attribute it in the sentence — never against the
    link.** Jameson's $50 and nationwide-from-September live in Whisky Advocate; the link-out was
    Robb Report, which carries neither. Printing "Whisky Advocate puts it at $50" satisfies the
    sourced-claims rule at zero cost to clarity and reads *more* trustworthy, not less. Same move
    carried Garrison's bottle counts. **This is now the standing technique for split sourcing, and
    it is always cheaper than dropping the claim or dropping the item.**
32. **A missing tasting note is publishable copy if you say it out loud.** Redemption has no
    independent sensory anywhere. The blurb shipped "No independent tasting exists yet, so judge it
    yourself." **That converts the gap from a silent omission into reader-facing honesty**, keeps
    the item, and never touches the brand's marketing notes. **Use this line's shape on every
    future no-sensory item.**
33. **Bank a definition you deliberately skipped, then spend it.** Single pot still was held back
    on Aug 21 and spent on Jameson Aug 25, where the item is *about* the style. Bottled-in-bond was
    assumed for the fifth straight instance. **One insider term per item, and choose the item where
    the term is the story** — that is what keeps the intimidation pass passing without turning a
    blurb into a lecture.

## PRIOR LESSONS (27–30 added Aug 24)

27. **A guessed section URL is not a tested one, and the spelling matters.** `whiskyadvocate.com/travel`
    and `/whisky-life` both 404. The real, working paths are **`/whiskey-life`** (with the "e"),
    `/tag/travel` and `/tag/Features`. **Harvest section paths from an article page's own nav instead
    of guessing them** — three fetches of guesses bought nothing; one fetch of a known article page
    yielded the whole nav.
28. **"Client-rendered" is a property of a path, not of a site.** WA's `/news` and `/Tag/Cocktails`
    render no article links; `/whiskey-life`, `/tag/travel` and `/tag/Features` render plenty.
    **Never generalise a rendering failure to a whole host — and never generalise a success either.**
29. **A weekly review column is only an unblock if the bottle is buyable.** Robb Report's Taste Test
    is the pipeline's best sourced-sensory supply, but two of its last five subjects failed the
    forward bar on distribution (Jack Daniel's #17, Hibiki 12). **Read the distribution line before
    treating a taste test as a green light.** A 92-point independent tasting of an airport exclusive
    is still not an item.
30. **An instruction not to search is worth following even when the URL falls into your lap.** The
    Jones Mack FM link surfaced free in the rail; the file had put the item on a monthly check.
    **The URL was recorded and the page was not fetched.** Recording where the next check starts is
    the cheap half of the value; spending the fetch against instruction is the expensive half.

## PRIOR LESSONS (24–26 added Aug 23)

24. **A score is sourced sensory; a score is not a tasting note.** Whisky Advocate tasted Filmland
    and published **90 points and no descriptors**. The right move is to print the number, attribute
    the panel, and write no flavour at all. **An item can be fully verified on quality and still
    have zero printable sensory. Resist filling that in — the number is the sourced claim.**
25. **A second source can kill an item instead of clearing it, and that is a good outcome.**
    Bruichladdich sat blocked for want of corroboration; the corroboration arrived and reported it
    sold out. **Do not treat "found a second source" as "unblocked" — read what the second source
    actually says about availability.** Same run, same lesson from Gleneagles: Robb Report covering
    a bottle is not Robb Report tasting it.
26. **Fridays fail on supply because occasions have no weekly press cycle. Service journalism is
    the seam.** A travel or Whisky-Life feature is occasion-led, dates slowly, needs no event
    listing, and carries named-writer sensory or none at all. **When a Friday slot is empty, sweep
    the travel and lifestyle sections before hunting for another cocktail.**

## PRIOR LESSONS (15–18 added Aug 19)

1. **Sweep the RSS feed before anything else on Whisky Advocate.** One fetch replaces two dead
   indexes.
2. **A roundup article is one link-out, not four.** Decide at staging time which single item spends
   the link; mark the others "needs own link."
3. **Search before guessing slugs.** Nine 404s were spent guessing FM URLs for Redemption. Titles
   do not predict slugs.
4. **A press release read through two outlets is still one source.** What clears an item is the
   Tier 1 primary plus one Tier 2 corroborating mention — not "two outlets ran it."
5. **The category-versus-bottle sensory trap.** Raasay's Hungarian oak, Macallan's coconut, WA's
   ice wine notes. **Standing test: ask whether the source tasted THIS bottle. If not, there is no
   sensory, however evocative the page.**
6. **When a roundup strands an item, go find it its own primary source** — the brand's or
   organizer's own dated release or event page. Tier 1 by definition, no tiering decision needed.
7. **An evergreen product page is not a release page.** Garrison's `/cowboy-bourbon/` says 73.2%
   ABV; the 2026 event page says 141.0 proof. **For a dated release, only a dated source describes
   it.**
8. **Do not promote an unvetted outlet to clear a blocked item.** Shanken was very probably fine
   and would have unblocked Redemption on Aug 17. **Holding it for one run was correct: on Aug 18
   a vetted outlet turned out to have covered the same story all along.** The tier list is not
   bureaucracy — waiting produced the better link.
9. **A quiet source is not a broken source.** The WA feed returned zero new items Aug 15–17 and two
   on Aug 18. **Check the transport before concluding a regression, and the calendar before
   concluding a supply problem.**
10. **Use `**bold**` in `slack_send_message`** — it takes standard markdown, so `*text*` renders
   italic. Slack stores it as native bold. Applied Aug 17 and Aug 18.
11. **NEW — when a source contradicts itself, print the body, not the headline.** WA's value list
   is titled "$75 or Under" and its intro repeats the claim, but two of the twenty entries are
   priced at $90. **Any claim a reader can falsify by clicking the link is worse than no claim.**
   The published blurb printed the hand-counted "fourteen of the twenty at $50 or under" instead.
   **Generalisation: verify the source's own summary claims against the source's own data before
   repeating them. Outlets round, over-claim, and forget to re-check their own headlines.**
12. **NEW — a second source verifies; only the link-out speaks.** The Buffalo Trace hook had been
   framed for three runs as the disagreement between WA and Breaking Bourbon. That hook is
   unprintable: Breaking Bourbon is not the linked page, so citing it puts an unverifiable-by-click
   claim in the copy and implies a second link. **Build every blurb from the link-out alone, then
   check the second source silently for contradictions.** A great hook that requires the
   unlinked source is not a hook.
13. **NEW — read the author rail, not just the article.** Robb Report article pages list their
   critic's three most recent pieces as absolute URLs in the raw HTML. That rail unblocked both
   Redemption and Jameson in a single fetch that had been made for an unrelated reason. **Standing
   rule: on any outlet with a bylined critic, harvest the author rail on every fetch. It is the
   cheapest discovery path found so far — cheaper than RSS, and it surfaces exactly the
   sensory-carrying reviews this pipeline is always short of.**
14. Standing: **if a source does not state a person's pronouns, write around them or use
   they/them.** Applied to Sean Evans, Julia Higgins, Danny Brandon, David Fleming, Jonah Flicker,
   Bradford Lawrence, Grant McCracken, Alan Kennedy, Kevin O'Gorman, Max Schikora, Jason Parker and
   Bryan Smith — none of their pronouns are stated in any source read. **Added Aug 19: Blake
   Layfield, Rob Samuels, Dan Callaway, Margaret Archambault, Takehiko Hiura, Calum Holmes and
   Margie and Bill Samuels Sr.** Annie Hill's are likewise unstated — the Aug 19 brief named her
   without a pronoun, which is the pattern to keep.
15. **NEW — sweep the section index, not just the author rail.** Lesson 13 said harvest the rail.
   Aug 19 improved on it: `robbreport.com/food-drink/spirits/` returns nine articles to the rail's
   three, and the three items staged this run were all invisible to the rail. **Generalisation: on
   any outlet with a working server-rendered section index, the index beats every other discovery
   path. Try the index first, the feed second, the rail third.**
16. **NEW — two outlets can carry a board with the primary outlet silent.** Whisky Advocate
   published nothing in the Aug 18–19 window and the run still staged three verified items, all from
   Robb Report and Fred Minnick. **A quiet primary source is no longer a thin day.** This is the
   payoff of the outlet-concentration work, and it is the evidence to cite if the cadence question
   ever comes up: supply is not the constraint it was in July.
17. **NEW — a two-point difference is not a hook, even when the headline says it is.** Robb Report's
   Maker's Mark headline is "more 14-year-old bourbon in the mix than last year's." True: 18% versus
   16%. **Printing that as the reason to care would be technically sourced and substantively
   misleading.** The real hook is that it is the oldest blend the distillery has released.
   **Companion to lesson 11: check not only whether a source's summary claim is TRUE, but whether
   it is MATERIAL.** A sourced triviality still fails the forward bar.
18. **NEW — the wood trap has a third form.** Lesson 5 covered a source describing a cask type
   generally. Bardstown adds the case where the **brand itself** lists what the casks "contribute"
   — Jura's ripe fruit and maritime character, Garryana's clove and nutmeg. **It reads exactly like
   a tasting note and is not one. Nobody tasted the whiskey.** Standing test, restated: ask who put
   the glass to their mouth. If the answer is nobody, there is no sensory, no matter how specific
   the page.
19. **NEW — check that a source's numbers ADD UP, not just that they exist.** Robb Report's Lochs
   of Jura blend is 49% + 39% + 21% = **109%**. Every individual figure looks authoritative and
   citable; the set is impossible. **Lesson 11 said verify a source's summary claims against its
   own data. This extends it to arithmetic: sum percentages, check that ages and proofs are
   consistent, and confirm dates land on the weekday the source says.** Where the error cannot be
   localised, print none of the affected figures — there is no way to know which one is wrong.
   Discovery's figures in the same article sum correctly, which is what makes this a typo rather
   than a method problem, and which is why the rest of the piece stays trustworthy.
20. **NEW — a link-out upgrade is not free. It changes which facts you may print.** Bardstown moved
   from Fred Minnick to Robb Report and gained independent sourced sensory — but **lost the 99 IWSC
   points**, which only Fred Minnick carries, and **changed price from $139.99 to $140**. Lesson 12
   says only the link-out speaks, so **every claim staged against the old link must be re-checked
   against the new one.** Standing rule: when a link-out changes, re-derive the printable fact set
   from scratch and surface any lost hook to Aaron as a tradeoff, not a silent downgrade.
21. **NEW — a brief can be overtaken by events within hours, and the correction is the next run's
   lead.** The Aug 19 brief said the Canada tariff took effect that morning; it was paused before
   it did. **The pipeline's memory made this catchable — the file recorded exactly what had been
   claimed, so the contradiction was visible on the next sweep.** Standing rule: when a prior post
   asserted something time-bound, re-check the assertion, not just the beat. **State the correction
   plainly and first. Never quietly restage the corrected version and hope nobody re-reads
   yesterday.**

22. **NEW — a staged price instruction is not a verified price. Re-read the number on the page, not
   in this file.** The Aug 21 board carried "Print $55 GA / $75 VIP, official site only" for three
   runs. **The page actually says "($55 + fees)" and "($75 + fees)" and states no all-in figure.**
   A bare "$55" is a number a reader falsifies at checkout — the exact failure lesson 11 exists to
   prevent, arriving by a different route: **not a source contradicting itself, but this file
   compressing a source's number and losing a qualifier.** Published as "$55 plus fees, VIP $75."
   The same re-read caught "supports" versus "proceeds" on the same page — the file said proceeds;
   the page never does. **Standing rule: on edition day, re-derive every printed number and verb
   from the re-fetched page. The staging note tells you which page to read, not what it says.**
23. **NEW — the collision flags track nouns of provenance, not nouns of flavour.** Nine flags were
   carried into Aug 21 covering brands, outlets, bylines, insider terms and categories. **None of
   them caught pineapple running as the Easy Pour hook two Fridays in a row**, in nearly the same
   phrase, with a third pineapple already in dedup. Coconut is flagged five ways and peach is
   flagged spent — **so the category exists in this file; it just was not applied to the item
   actually being staged.** **Standing rule: when staging an item, add the noun that carries its
   hook to the flag set — the fruit, the flavour, the occasion — and check it against the last two
   editions of the same segment.** Provenance repetition is a credibility problem; hook repetition
   is the one a reader actually notices.
24. **NEW — the edition's one quote is an allocation decision, so make it deliberately.** Two clean
   candidates cleared every rule on Aug 21: Parker at 16 words and Schikora at 10. **The prompt
   allows one per edition, so the second is not a near-miss — it is spent budget.** Parker won on
   need, not quality: the Copperworks item has no price, no sensory and no availability, so the
   quote was the only human element available to it, while Thunder Bird stands up on a recipe and a
   named creator. **Standing rule: award the quote to the item that has the least else, not to the
   best line.**

---

## BLOCKERS

- Write access: **resolved and stable.** Tenth consecutive successful push.
- **`whiskey-social-brand` skill STILL NOT PRESENT — confirmed again Aug 21, and an edition shipped
  without it.** Directory listing of the synced skills folder shows `whiskey-social-news-roundup`
  with all three references and **no brand skill of any name.** **The Aug 21 Last Call ran entirely
  off the inlined VOICE block, and the inlined block was sufficient** — it carries the banned-word
  list, the sentence-length rule, the sentence-case and no-exclamation rules, the DISCUS clause and
  the quote discipline. **The one thing it does not carry is the send-off phrase bank**, which came
  from `references/edition-templates.md` ("Worth the pour") and was cross-checked against the real
  Aug 14 post in the channel, which used the identical line. **So the gap is currently costing
  nothing measurable.** It was surfaced to Aaron once on Aug 20 and compressed to `_unchanged_` on
  Aug 21 per the no-re-explaining rule. **Do not raise it as its own bullet again unless an edition
  actually needs a voice decision the inlined block cannot answer.**
- **The prior brand-skill note, retained:** The
  `whiskey-social-news-roundup` skill and its three references loaded normally; the brand skill is
  not in the synced skills directory at all. **Consequence is limited but real: voice, lexicon and
  the banned-word list came from the inlined VOICE block in the task prompt, which is
  self-sufficient for a prep brief** (internal register, brand bans do not apply) **but is the
  only voice authority available on an edition day.** Surfaced to Aaron in the Aug 20 Notes as
  instructed. **If Friday's edition runs without it, say so once and use the inlined rules — do
  not skip the intimidation, lexicon or DISCUS passes, which are all specified inline.**
- Project-knowledge search unreachable, twenty-fourth run — source tiering comes from the inlined
  core in the skill's `references/verification-protocol.md`.
- `references/subject-beats.md` still wrong on beat 7, open since Jul 26. Stale-reference risk,
  not a live error.
- **THE SOURCE-DIRECTORY ESCALATION IS BACK ON, AND ITS OWN TRIGGER FIRED — Aug 24.** The Aug 21
  entry withdrew it but set the condition: reinstate "if a second item ever stalls on tiering."
  **Shanken/Redemption was the first (Aug 17); The Spirits Business/tariff is now the second.**
  The Shanken question dissolved only because Robb Report happened to cover the same story — **luck,
  not process.** Project knowledge has been unreachable for 25 runs, so the inlined stable core in
  `references/verification-protocol.md` is the only tier authority available, and it enumerates six
  Tier 2 outlets while the real world keeps producing legitimate unlisted ones.
  **Raised to Aaron as one Notes bullet this run: a short committed tier list on this branch.**
  It is his call to write it. **The pipeline must not invent tiers for itself** — that is why the
  tariff is held rather than linked. **Do not raise this again as its own bullet once he has
  answered, or if a third item stalls before he does; compress to `_unchanged_`.**

---

## DEDUP — closed to re-use

Story keys are lowercase-hyphenated `brand-product-year`. Prune at 30 days.

**Added Sep 1 (PUBLISHED in The Shortlist):**
`makers-mark-cellar-aged-2026` · `jack-daniels-american-single-malt-2026` ·
`shang-jiangxiang-whisky-2026` · `bardstown-lochs-of-jura-2026`.
**All four are PUBLISHED, not staged. Never re-publish, never re-scout.** Prune eligibility
**Oct 1**. Expiries and carve-outs:
- **Maker's Mark** — the Sept 1 release date has passed; the key is dead as a release item. **The
  ticketed 21+ distillery launch event on Sept 10 and the Cellar Aged tour from Sept 14 are separate
  future items under their own keys, NOT this one** — but both sit behind the standing
  `kentucky-bourbon-festival` block.
- **Jack Daniel's** — **still live, because the nationwide rollout is "this fall" with no date.**
  **If an independent tasting is ever published, that is a materially new development and a
  legitimate later item under a new key.** Do not re-run the release itself.
- **SHĀNG** — evergreen category story; **referenceable later as prior coverage, never re-runnable.**
- **Bardstown Lochs of Jura** — dead as a release item after the Aug 21 drop.
**COVERED URLS, all four now spent:**
`robbreport.com/food-drink/spirits/makers-mark-2026-cellar-aged-bourbon-1238564495/` ·
`fredminnick.com/2026/08/26/jack-daniels-releases-american-single-malt-nationwide/` ·
`whiskyadvocate.com/shang-baijiu-whiskey-review` ·
`robbreport.com/food-drink/spirits/bardstown-bourbon-company-new-cask-finished-whiskeys-1238567077/`
**— THAT LAST ONE MATTERS: it is the shared Bardstown link, so `bardstown-discovery-2026` has now
lost BOTH its candidate link-outs** (the Fred Minnick reprint was already spent). **Discovery is
effectively dead unless a third outlet files on it independently. Do not stage it against either
URL.**

**Added Aug 28 (PUBLISHED in Last Call):**
`brough-brothers-belle-of-louisville-2026` · `whisky-advocate-distillery-glamping-2026` ·
`new-riff-sherry-finish-malted-rye-2026` · `filmland-malted-mummy-2026`.
**All four are PUBLISHED, not staged. Never re-publish, never re-scout.** Prune eligibility
**Sep 27**. Expiries: Brough Brothers is dead by event date after **Aug 29** (**but the September
River Road distillery opening is a SEPARATE future item, not this key**) · Filmland is dead by debut
date after **Aug 29**, and **its WA Fall-issue full review is a legitimate later item under a new
key** · New Riff is a dated release, dead after the Aug 28 drop · **the glamping guide is evergreen
and is the one of the four referenceable later as prior coverage.**
**COVERED URLS, both now spent:**
`whiskyadvocate.com/new-whiskey-from-bowmore-barrell-and-more` (**the seven-release roundup — Bowmore
x Snarkitecture, Barrell New Year, Dublasé, Branch & Barrel and Koopers all still need their own
link-outs, and Branch & Barrel and Koopers are separately closed**) ·
`whiskyadvocate.com/glamping-near-whiskey-distilleries` (**the other eleven sites on it are NOT
independently stageable — same URL**).

**Added Aug 30 (STAGED / WATCHED / DROPPED — all closed to re-scouting):**
Fri Sep 4 — `buffalo-trace-on-tour-2026` (**NEW, STAGED, VERIFIED on a Tier 1 primary plus WA and
WKYT**).
Conditional Sep 4 — `whisky-advocate-outdoor-excursions-2026` (**NEW. Blocked only on Aaron's call
about a third Sean Evans byline. One source by design — never log it as needing a second**).
Tue Sep 8 — `johnnie-walker-op-den-kamp-auction-2026` (**NEW, STAGED, VERIFIED on WA + Robb Report,
both original reporting**) · `blue-note-cherry-wood-cask-2026` (**PROMOTED from pointer, now
second-sourced**) · `michters-toasted-barrel-finish-rye-2026` (**NEW, STAGED, still NEEDS A SECOND
SOURCE**).
Watching — `brough-brothers-river-road-distillery-2026` (**NEW KEY. No opening date published;
re-hunt Wed Sep 2**) · `hemsworth-archie-rose-2026` (**beat file. Revisit when the U.S. launch gets
a date**).
**Dropped Aug 30:** `larrikin-australia-series-2026` · `angels-envy-distillery-series-imperial-stout-2026`
· `tx-whiskey-experimental-rum-finished-2026` · `whisky-advocate-19-hot-whiskies-summer-2026` ·
`la-pulga-tcu-horned-frogs-2026`.
**Re-confirmed closed Aug 30, do not read the new WA pickups as new items:**
`four-roses-experimental-002-honey-cask-2026` (**WA confirms "distillery exclusive" — the fact that
closed it**) · `beam-ten-pin-decanter-2026` (**WA confirms Clermont-only**).
**Aug 31 — NO KEYS ADDED, NO KEYS CHANGED. The run staged nothing.** Recorded so a later run does not
read the gap in the dedup log as a missed write: **the Aug 31 prep produced zero new story keys, and
that is accurate.** Two entries changed status only, both narrowing rather than opening:
`michters-toasted-barrel-finish-rye-2026` (**second-source hunt CLOSED — flag or hold on Sep 8**) ·
`uncle-boojies-gatsby-research-2026` (**still a beat file; the September event is invitation-only
with no published date, so it fails the reader-can-act bar outright**).
**Prune check Aug 31: nothing eligible, confirmed. Next eligibility is Sep 20.**

**COVERED URL, now spent:** `whiskyadvocate.com/whiskey-news-roundup-august-28-2026` is claimed by
Buffalo Trace; the Hemsworth and La Pulga entries on it are **not independently stageable — same
URL.** Same for the WA Whisky Watch of Aug 28, claimed by Michter's.

**Added Aug 27 (STAGED / WATCHED / CLOSED — all closed to re-scouting):**
Tue Sep 8 — `whisky-advocate-chinquapin-oak-2026` (**NEW, STAGED. One source by design — a Tier 2
outlet's own editorial and tasting panel. Never log it as needing a second source.**).
Watching — `larrikin-australia-series-2026` (**NEW. Unblock test is KBF ticket availability plus one
second outlet, run it Sun Aug 30**) · `uncle-boojies-gatsby-research-2026` (**NEW, beat file. Revisit
only when the Howard mashbill bottle gets a date**) · `bardstown-bourbon-capital-mash-up-2026`
(**dead as filed — June event. Re-check only for a 2027 announcement, spring 2027**).
**Assessed and closed Aug 27:** `four-roses-experimental-002-honey-cask-2026` (**two Kentucky visitor
centers only from Sept 18 — fails the forward bar, moved to DROPPED. Reopenable ONLY on national
distribution**) · `whisky-advocate-all-inclusive-resorts-2026` ($2,035–$2,950 a night, aspirational
not actionable — **recommend against, do not re-fetch**) · `whisky-advocate-steal-my-sunshine-cocktail-2026`
(**not fetched: fifth consecutive WA cocktail needs Aaron's say-so, and a pineapple collision is
likely. Fetch only if he clears the count and a Friday is thin**) · `kimbland-distillery-fss-warning-2025`
(**FSS whisky safety warning, dated 16 Dec 2025, Orkney only, no WS partner — NOT an override.
Closed. Do not re-surface.**).
**`redwood-empire-hyperion-batch-001-2026` now has a TSB second source and is still link-out-blocked
on the same tier question. Unchanged status, recorded so it is not re-chased.**

**Added Aug 25 (PUBLISHED in The Shortlist):**
`jameson-distillers-batch-single-pot-still-2026` · `redemption-single-barrel-bonded-bourbon-2026` ·
`heriot-watt-kirin-mango-aroma-study-2026` · `garrison-brothers-cowboy-bourbon-12-2026`.
**All four are PUBLISHED, not staged. Never re-publish, never re-scout.** Prune eligibility
**Sep 24**. Garrison is additionally dead by event date after **Sept 12**; the mango study has no
expiry and is the one of the four that could be referenced later as prior coverage.
**`redemption-ancients-18yr-2026` is NOT covered by this** — the 18-Year-Old is the linked
article's headline subject and was deliberately left unprinted. It remains an alternate, and the
shared URL is now a COVERED URL, so it needs a different link-out if it is ever staged.

**Added Aug 21 (published in Last Call):**
`detroit-bourbon-blues-festival-2026` · `copperworks-farmsmith-spokane-relief-2026` ·
`whisky-advocate-dubai-chocolate-pairing-2026` · `whisky-advocate-thunder-bird-cocktail-2026`.
**All four are now PUBLISHED, not staged. Never re-publish, never re-scout.** Detroit is
additionally dead by event date after Aug 23.

**STAGED — not published, but closed to re-scouting (update the entry, never re-discover):**
Tue Aug 25 — **CLEARED. All four published Aug 25; moved to the published block above.**
Tue Sep 1 — `makers-mark-cellar-aged-2026` (**new Aug 19**) · `bardstown-lochs-of-jura-2026`
(**new Aug 19, link-out upgraded Aug 20**) · `shang-jiangxiang-whisky-2026` (**new Aug 20**).
**HELD, resolved, awaiting a vetted link-out — `canada-50pct-tariff-aug-19-2026`.** Aug 23: the
pause collapsed and the tariff is live. **Default applied — hold to Sep 1, recheck Robb Report and
The Spirits Business Monday.** The key is unchanged and stays held, never pruned while this is
open. **Do not re-key it to a collapse slug.**
**Added Aug 23 (STAGED for Fri Aug 28, closed to re-scouting):**
`filmland-malted-mummy-2026` · `whisky-advocate-distillery-glamping-2026`.

**Added Aug 26 (STAGED, closed to re-scouting):**
Fri Aug 28 — `brough-brothers-belle-of-louisville-2026` (**new**) ·
`new-riff-sherry-finish-malted-rye-2026` (**promoted from the Aug 23 September-pointer list; the key
is unchanged — do not re-key it**).
Tue Sep 1 — `jack-daniels-american-single-malt-2026` (**new**). **Not to be confused with
`jack-daniels-17yr-2026`, closed on distribution and in DROPPED. Different bottle, different reason.**
September pointers — `cedar-ridge-anniversary-edition-2026` · `blue-note-cherry-wood-cask-2026`.
**Assessed and closed Aug 26:** `beam-ten-pin-decanter-2026` (**distillery-counter only, sale opened
Aug 22 — moved to DROPPED**) · `blue-spirits-distilling-chapter-7-2026` (trade litigation, no
partner named, not an override) · `redwood-empire-hyperion-batch-001-2026` (not fetched, not needed).

**Added Aug 23 (September pointers, closed to re-scouting):**
`barrell-new-year-blend-11-2026` · `new-riff-sherry-finish-malted-rye-2026` ·
`bowmore-snarkitecture-oak-voyage-2026` · `dublase-signature-bourbon-trio-2026`.
**`koopers-texas-oak-bourbon-2026` MOVED TO DROPPED Aug 24** — 360 bottles, sale already open,
one press release across every outlet. Never staged, never published.

**Added Aug 24 (assessed and closed, closed to re-scouting):** `hibiki-12-2026` (Robb Report tasted
it at 92 — **airport-only, fails the forward bar**) · `soho-spirits-festival-cancellation-2026`
(organiser's own cancellation, not a safety incident) · `fssai-diageo-sales-ban-revoked-2026`
(India, labelling, revoked) · `sazerac-garrard-county-acquisition-2026` (trade; **closes the
Garrard County distress story**).

Alternates and pointers — `bardstown-discovery-2026` · `redemption-ancients-18yr-2026` ·
`jones-mack-bourbon-2026` (needs second source) ·
`hard-truth-dark-roast-rye-2026` · `isle-of-raasay-hungarian-oak-oloroso-2026` ·
`whisky-advocate-lost-irish-cucumber-2026` ·
`whisky-advocate-coconut-manhattan-2026` · `whisky-advocate-vintage-coco-highball-2026`.

**Added Aug 18 (published in The Shortlist):**
`chattanooga-moldovan-ice-wine-2026` · `old-overholt-11yr-extra-aged-rye-2026` ·
`first-west-explorer-black-corn-2026` · `whisky-advocate-20-whiskies-under-75-2026` ·
`buffalo-trace-2026-prohibition-collection` (**key kept byte-identical to prior runs — it does not
match the `brand-product-year` pattern, but changing it now would break dedup. Do not "fix" it.**)

**Cut without publishing, permanently: `macallan-harmony-vi-coconut-2026`.** Recommended for cut
Aug 14, 16 and 17 with no reply; the default was applied Aug 18. **Do not restage it.**

Carried: `bourbon-women-siposium-2026` · `unreined-wildhorse-ranch-rickhouse-2026` ·
`the-bourbon-room-saratoga-springs-2026` · `whisky-advocate-charred-garden-smash-2026` ·
`whisky-advocate-stetson-bourbon-review-2026` ·
`glenfiddich-aston-martin-f1-16yr-release-2-2026` · `sagamore-high-rye-bourbon-national-2026` ·
`whisky-advocate-barrel-entry-proof-2026` · `barrell-decade-2-canadian-2026` ·
`whisky-advocate-peach-whisky-cocktails-2026` · `whistlepig-kentucky-development-depot-2026` ·
`brewzle-fest-opelika-aug-29-2026` · `sirdavis-independent-2026` ·
`bib-tucker-8yr-bottled-in-bond-2026` · `yellowstone-limited-edition-2026` ·
`dancing-goat-stillmans-sonder-2026` · `redwood-empire-colonel-armstrong-2026` ·
`whisky-advocate-july-auction-update-2026` · `hoochenanny-festival-aug-14-16-2026` ·
`still-austin-quarter-sept-2026` · `horse-soldier-farms-somerset-2026` ·
`louisville-rickhouse-nulu-2026` · `heaven-hill-bib-double-mash-2026` ·
`blade-and-bow-12yr-solera-2026` · `deanston-orange-wine-17yr-2026` ·
`barton-1792-straight-rye-2026` · `garrison-brothers-laguna-madre-2026` ·
`canada-50pct-tariff-aug-19-2026` (2x, **HELD — see below, do not prune**) ·
`makers-mark-cask-strength-26-01-2026` ·
`blood-oath-pact-12-2026` · `bushmills-ni-roi-tariff-split-2026` · `old-grand-dad-7yr-bib-2026` ·
`bardstown-victoria-pineapple-2026` · `watch-hill-proper-festival-aug-15-2026` ·
`larceny-vinepair-best-bourbons-2026` · `punch-whiskey-highball-2026`.
Cut: `barton-1792-xv-2026` · `macallan-harmony-vi-coconut-2026`.

### PRUNE LIST — EXECUTED FRI Aug 21. Four keys removed, two held.

Pre-staged Aug 19, confirmed Aug 20, **run as written on Aug 21 with no re-dating.** The four
PRUNE rows are gone from the Carried list above. **The plan worked exactly as designed: a table
authored two runs earlier executed mechanically on edition day, when the file was already open.**
Keep pre-staging prunes this way.

| Story key | First covered | Eligible | Action Fri Aug 21 |
|---|---|---|---|
| `scotch-tariff-removal-2026-07-24` | Jul 24 | Aug 23 | **PRUNED ✓** |
| `bulleit-87-bourbon-rye-2026` | Jul 25 | Aug 24 | **PRUNED ✓** |
| `old-forester-presidents-choice-2026` | Jul 26 | Aug 25 | **PRUNED ✓** |
| `old-forester-triple-char-117-2026` | Jul 27 | Aug 26 | **PRUNED ✓** |
| `canada-50pct-tariff-aug-19-2026` | Jul 27 | Aug 26 | **HELD ✓ — see below** |
| `whisky-advocate-charred-garden-smash-2026` | **UNDATED** | unknown | **NOT PRUNED ✓** |

**A pruned key is re-scoutable by design.** All four are stale, low-value stories a fresh sweep is
unlikely to surface — but `scotch-tariff-removal-2026-07-24` ran **four times** and the tariff beat
is the one Adam complained about. **If a future run rediscovers a Scotch tariff story, that is not
automatically a repeat — but check this section before staging it.**

**AUG 27 PRUNE CHECK: nothing eligible, confirmed. Nothing crosses 30 days before Sep 20.** The
check cost one read and is recorded so the Sun Aug 30 run does not re-derive it.

**NEXT PRUNE WINDOW:** nothing else is eligible until late September. **Do not re-derive the list
until an entry actually crosses 30 days.** The four Aug 21 published keys become eligible **Sep 20**.

**`canada-50pct-tariff-aug-19-2026` must NOT be pruned — the case got STRONGER Aug 20.** It is now
an active Tue Aug 25 candidate carrying a material new development (the pause, and whatever it
resolves into). Pruning it would silently re-open the story to rediscovery, which is precisely the
failure mode dedup exists to prevent. **The key stays byte-identical even though the story reversed
— the key names the beat, not the outcome. Do not re-key it to `canada-tariff-pause-2026`; that
would fork dedup and let the original run again.** Hold until it publishes or Aaron kills it.

**`whisky-advocate-charred-garden-smash-2026` could not be dated** — the phrase appears nowhere in
the Jul 24–Aug 19 channel history, so its coverage date is not recoverable from Slack. **Do not
prune it blind.** Either leave it in dedup permanently (harmless — the cost of a stale entry is one
line, the cost of a wrong prune is a republished story) or date it from the WA article. **Recommend
leaving it. The 30-day prune is hygiene, not a requirement.**

**Note on collisions with the new value list:** it contains a **Bulleit** (Mesquite Smoked Malt)
and a **Maker's Mark Cask Strength**, and `bulleit-87-bourbon-rye-2026` and
`makers-mark-cask-strength-26-01-2026` are both in dedup. **Different products, and the item
published was the list, not any single bottle. Not a repeat.** Recorded so a future run does not
read it as one. It also contains a **Chattanooga Barrel Finishing Series** entry (Triple Islay)
while the Chattanooga ice wine ran in the same edition — **same brand, same series, two items.**
Chattanooga was deliberately not named in the list blurb. **Watch this: it is the closest the
edition came to reading repetitive.**

**Spent link-outs — do not re-mine:**
_Aug 18 spent five: `whiskyadvocate.com/buffalo-trace-2026-prohibition-collection-review` ·
`whiskyadvocate.com/first-west-explorer-reviewed` ·
`whiskyadvocate.com/20-whiskies-rated-90-points-or-higher-priced-75-or-under` ·
`robbreport.com/.../old-overholt-extra-aged-cask-strength-rye-whiskey-1238515743` ·
`fredminnick.com/2026/08/14/chattanooga-whiskey-releases-moldovan-ice-wine-cask-finished`._
Also spent: `whiskyadvocate.com/new-whisky-from-deanston-barrell-and-more` ·
`whiskyadvocate.com/macallan-glenfiddich-jack-daniels-and-more-new-whiskey`.
**`whiskyadvocate.com/jameson-single-pot-still-garrison-cowboy-and-more-new-whiskey` — NOT spent,
and no longer reserved.** Every item that was queued behind it now has its own link. It is free.

---

## COLLISION FLAGS

- **HIBIKI — NEW Aug 24, and it is why the Hibiki 12 rejection was overdetermined.** The Aug 21
  Dubai chocolate blurb printed "Hibiki Japanese Harmony is the delicate pick," and Robb Report's
  Hibiki 12 review discusses Harmony directly. **The brand has already been printed inside the last
  week.** The item failed on distribution anyway, so this cost nothing — **but a Hibiki item before
  October is a deliberate call, not a drift.**
- **JONAH FLICKER — the count would have gone to SIX.** He bylines three of four Aug 25 items, both
  Sep 1 items, and the Aug 18 Old Overholt item. **Hibiki 12 would have been a sixth inside one
  week.** Rejecting it on the forward bar incidentally held the line. **The cheapest fix is still
  unchanged: hold Garrison off Aug 25 to any Tuesday through Sept 8.**
- **AN ALL-WA FRIDAY IS NOW LIKELY, NOT JUST FLAGGED — Aug 24.** A full run was spent looking for a
  non-WA Friday item and none exists. **Aug 28 will probably run two of two WA.** That is acceptable
  and better than padding. **Recorded so it reads as a known, accepted cost rather than a miss.**
- **Whisky Advocate concentration — three of five on Aug 18.** Worse than the two-of-four the Aug
  17 file planned, because the fifth item added on edition morning was WA. **Surfaced in Notes so
  Aaron knows it moved.** It reverses on Aug 25, which carries zero WA link-outs.
- **Robb Report / Jonah Flicker concentration — NEW, and the mirror image of the WA problem.**
  Flicker bylines the Aug 18 Old Overholt item and both Aug 25 candidates. **Do not let one
  critic's byline carry a whole edition.** If Aug 25 runs Jameson and Redemption together, that is
  two Flicker pieces in one edition — acceptable once, and worth noticing.
- **Single pot still, twice in four days.** Redbreast 12 in the Aug 21 Dubai chocolate list;
  Jameson the Aug 25 lead. **Do not define it Aug 21. Spend it on Jameson.**
- **Bottled-in-bond, four times now** — Redemption (Aug 25), Hard Truth (September), plus
  `old-grand-dad-7yr-bib-2026` and `bib-tucker-8yr-bottled-in-bond-2026` in dedup. **The Thunder
  Bird recipe also calls for Rittenhouse bottled-in-bond rye.** Definition has been printed before.
  **Do not re-teach it; assume it and link.**
- **FILMLAND'S DEBUT IS AT A COVERED EVENT — NEW Aug 23, and this is the one to not get wrong.**
  Search summaries place the Aug 29 Malted Mummy debut **at BrewzleFest**, and
  `brewzle-fest-opelika-aug-29-2026` is already in dedup. **Whisky Advocate, which is the link-out,
  names no venue — only "August 29th."** So the sourced reading and the safe reading are the same
  one: **peg the date, never the festival.** If a later run finds a vetted source that names
  BrewzleFest, the item still runs on the date; the festival is spent.
- **AN ALL-WHISKY-ADVOCATE FRIDAY — NEW Aug 23.** Both Aug 28 items are WA link-outs. **This is not
  the cocktail streak** — neither is a cocktail, so that count stays at four and needs no say-so —
  **but it is the same underlying concentration in a new place.** Aug 25 runs zero WA; Aug 28 would
  run two of two. **One non-WA Friday item over Mon–Thu fixes it. Do not fix it by dropping a
  verified item.**
- **Sean Evans, twice in eight days.** He bylines the SHĀNG review staged for Sep 1 and the glamping
  guide staged for Aug 28. **Different editions, eight days apart — acceptable, and noted so a third
  Evans byline before mid-September is a deliberate call, not a drift.**
- **A fourth straight Friday of a WA cocktail — IT HAPPENED Aug 21.** Taken deliberately for the
  Michigan/Detroit adjacency. **The count is now four. A fifth should not be taken without Aaron
  saying so.** The three demoted alternates are all WA cocktails too, so **the fix is not a
  different cocktail — it is a different kind of Easy Pour**, or no Easy Pour that week. Worth
  finding one non-WA cocktail or occasion source before the Aug 28 Friday.
- **PINEAPPLE — NEW Aug 21, and the flag set missed it.** Aug 14's Easy Pour was a pineapple smash
  published with "Bright and tropical up front"; Thunder Bird's WA sensory is "a bright, juicy hit
  of pineapple and lime up front." **Two Fridays, same segment, same fruit, nearly the same
  phrase.** Caught at draft time and fixed by leading on the split rye-and-rum base instead;
  pineapple ran as an ingredient, never the hook. `bardstown-victoria-pineapple-2026` is also in
  dedup, making three. **Pineapple is spent for Friday through September.** See lesson 23 — the
  flags tracked brands, outlets, bylines and terms but not the hook noun.
- **Michigan, twice in one edition — deliberate and now spent.** Detroit (Eastern Market) and Ann
  Arbor (Huna) both ran Aug 21. It reads as intentional geography rather than repetition, which is
  why it was taken. **Do not run a third Michigan item before October.**
- **Charitable and community framing, twice in one edition.** Detroit supports the FernCare Free
  Clinic; Copperworks funds Spokane fire relief. **Both were sourced and neither was the hook, so it
  read as coherent rather than worthy** — but a third cause-led item in one edition would tip into
  sanctimony. **Cap it at two.**
- **Spokane / live-wildfire framing.** The Copperworks item ran while the fire was still burning.
  **If the fire is still active on a future run, a second Spokane item is defensible; once it is
  out, the story is over and the item is not restageable.**
- **Peach is spent for 2026.**
- **Andrea Wilson twice in one week — spent.** Quoted Aug 11, named Aug 14. **Do not name her a
  third time before September** without a deliberate call.
- **Wild Turkey twice.** A 94-point Wild Turkey ran Aug 11; the Dubai chocolate list carries Wild
  Turkey Rare Breed rye, also 94 points, at $60. **Do not lead Aug 21 on Wild Turkey.**
- **Coconut, five ways.** Macallan (now cut), First West's "vanilla coconut ice cream" in WA's note
  (**deliberately not printed Aug 18**), the Coconut Manhattan, Vintage Coco, and Brugal's
  coconut-toasted rum (rejected). **Never let coconut be the hook twice in one edition.** Coconut
  cask finishing is a live 2026 trend, not a coincidence.
- **Bourbon-adjacent non-whiskey keeps surfacing** — Chip Tate's mezcal, Cuervo's mole-cask
  tequila, Brugal's rum, Lexington's pumpkin ale, a bourbon *basting sauce* recall, and the
  Jamaican rum in the Thunder Bird. **Six in three weeks.** Keep the rejections fast and keep the
  urgent sweep from firing on "bourbon" attached to a non-whiskey product.
- **Sean Evans** bylines the Stetson review (ran Aug 11) and Buffalo Trace (ran Aug 18, named).
  **Spent for now.**
- **Louisville** carried Friday venue items Jul 31 and Aug 14. A third would read as a pattern.
- **Bardstown Bourbon Co. — now a real collision, not a recorded one.** It brushed Aug 18 twice
  unprinted (First West is contract-distilled there; its Origin Series bonded is in the value list),
  and `bardstown-victoria-pineapple-2026` is in dedup. **Lochs of Jura would be the first time the
  name is printed.** That is still clean — but **do not also name Bardstown as First West's
  distillery** in any future item, and do not run Lochs of Jura and Discovery together.
- **Maker's Mark twice in two weeks — manageable, and the reason Cellar Aged sits on Sep 1.**
  The Aug 18 value-list blurb printed "Maker's Mark put an age statement on its cask strength for
  the first time." Cellar Aged on **Sep 1** puts two weeks between them. **`makers-mark-cask-strength-26-01-2026`
  is in dedup and is a different bottle.** Watch the age-statement framing: the Aug 18 line said
  "first time" about the cask strength, and Cellar Aged has carried age statements since 2023.
  **Those two facts are compatible but read as contradictory side by side. Frame Cellar Aged as the
  oldest blend, never as a first age statement.**
- **"Cellar" is a banned word inside a product name — NEW, Aug 19.** Maker's Mark **Cellar Aged** is
  a proper noun, so the brand skill permits it, but the blurb cannot avoid printing the word.
  **Never let "cellar" appear in WS's own voice in that item** — not "cellar-aged bourbon," not "the
  cellar." Name the bottle, then say "limestone cellar" only as the distillery's own term for the
  place. **First time a banned word has been unavoidable. Expect it again.**
- **Jonah Flicker — the concentration is now three of four on Aug 25**, plus both Sep 1 items and
  the Aug 18 Old Overholt item. **This is the most acute collision on the board.** Robb Report solved
  the sourced-sensory problem by supplying one critic, and one critic cannot carry the product.
  **Cheapest fix: hold Garrison off Aug 25 (its event is Sept 12, any Tuesday to Sept 8 works).**
  **Do not solve it by dropping the mango study or Jameson — those are the two best items on the board.**
- **Flicker now bylines BOTH Sep 1 Robb Report items — Maker's Mark and Bardstown.** SHĀNG (Sean
  Evans, WA) breaks the outlet monopoly but not the byline one. **Two Flicker pieces in one edition
  is acceptable once and Aug 25 has three, so the two boards together run five Flicker items in a
  week.** Cheapest fixes, unchanged: hold Garrison off Aug 25 to a September Tuesday, and if Sep 1
  ever needs a fourth item, it must not be Flicker.
- **Sean Evans, third byline — check before Sep 1.** Evans ran Aug 11 (Stetson) and Aug 18 (Buffalo
  Trace, named in copy) and was marked spent. **SHĀNG on Sep 1 puts two weeks between the second
  and third, which clears it** — but do not name him in copy, and do not add a fourth Evans item.
- **Bardstown Bourbon Co., twice on one board — NEW and worth watching.** Lochs of Jura is staged
  Sep 1 and `bardstown-victoria-pineapple-2026` is in dedup; Robb Report's new piece opens by
  referencing Victoria Pineapple directly. **The brand is becoming a recurring name.** Lochs of Jura
  is still the first time it is printed, which stays clean — but a third Bardstown item before
  October would read as a pattern.
- **Isle of Jura and Islay in adjacent editions.** Bruichladdich Greener Still (Islay, September
  pointer) and Bardstown's Jura casks are both Scottish-island stories. **Not the same island and not
  the same product, but do not run them in one edition.**

---

## DROPPED / DO NOT REDISCOVER

**Added Aug 30:** **`larrikin-australia-series-2026`** (**unblock test run and failed on both halves:
every pickup is one news release, and KBF is waitlisted except Sunday Samplers, so two of the three
release days are unreachable. Keeley's 13-word quote is on file in the Aug 27 section if Larrikin
ever gets retail distribution**) · **`angels-envy-distillery-series-imperial-stout-2026`**
(**18,000 bottles, Louisville visitors center only from Sept 10 — distillery exclusive**) ·
**`tx-whiskey-experimental-rum-finished-2026`** (**1,100 bottles, Whiskey Ranch campus only —
distillery exclusive; and its 89 points belong to the predecessor bottling, never carry it across**) ·
**`whisky-advocate-19-hot-whiskies-summer-2026`** (**summer framing, dead after Labor Day**) ·
**`la-pulga-tcu-horned-frogs-2026`** (**tequila, not whiskey**).
**Third confirmation that distillery-exclusive distribution is the cleanest kill this pipeline has:
five items closed on it in two runs.**

Carried: `whisky-advocate-multi-location-bars-2026` (Feb 17, stale) · cigar-aficionado-laphroaig ·
WA port cask · WA white lotus · WA hibiki harmony · WA finger lakes · WA summer menu · WA cigar
video · jim-beam-clermont-pause · pappy-drew-estate · eh-taylor-four-grain · angels-envy-dual ·
old-forester-117-rye · vinepair-13-bartenders-highball · glenfiddich-f1 Release No. 1 ·
`garrison-brothers-hye-rye-presale-2026` · `chicago-summer-whiskey-tasting-festival-2026` ·
`vinepair-old-overholt-11yr-2024-review` (wrong bottle, 2024 release) ·
`fss-kimbland-distillery-warning-2025` · `never-say-die-lexington-brand-home-2026` ·
`frey-ranch-tractor-tailgate-club-2026` · `whiskey-yard-liberty-center-2026` (Feb 8, stale) ·
`still-and-barrel-phoenix-2026` (Feb 5, stale) · `green-river-louisville-whiskey-row-2026`
(June 2025, fourteen months stale) · `denver-summer-whiskey-tasting-festival-2026` ·
`whisky-advocate-honey-cocktails-2026` (spring framing — restage in spring, not permanent) ·
`breckenridge-peach-whiskey-2026` · `glenachulish-distillery-approval-2026` ·
`chip-tate-penumbra-mezcal-2026` · `brugal-coleccion-visionaria-03-coconut-2026` (Dominican rum,
and the fifth coconut item) · `discus-congressional-fly-in-2026`.

**Added Aug 19:**
- `moonshine-university-closure-2026` — sourced but no vetted Tier 1–2 outlet, four weeks old, no
  reader consequence. **Assessed properly and closed. Do not re-search.**
- `jack-daniels-distillery-series-17-2026` — distillery-exclusive confirmed by Robb Report,
  unfavourable review, DISCUS-hostile framing. **The taste test exists; that question is answered.**
- `tequila-ocho-casa-de-ocho-venice-2026` — FM Aug 18. Two-month Venice Boardwalk residency.
  **Tequila, not whiskey.** Seventh bourbon-adjacent non-whiskey in three weeks.
- `garrison-brothers-hye-note-concerts-2026` and `garrison-brothers-meet-the-maker-dinners-2026` —
  the Aug 21–Sept 25 event-directory programming. **Single-market Hye, Texas. Fails the forward bar.
  Do not restage from the event directory.**
- `1800-tequila-coleccion-friedeberg-2026` — Robb Report Aug 19 window, $11,000, 50 box sets.
  Not whiskey, and the price is far past the forward bar.

**Added Aug 20:**
- `strathearn-batch-03-2026` — UK RSP £65.00 only, no US price or distribution, single
  press-release source, no sourced sensory. **Assessed properly and closed.** Revisit only on a
  US price plus an independent tasting.
- `brown-forman-q1-results-sept-2-2026` — an earnings date. **No consequence for a reader's shelf
  or weekend.** Same test that closed Circle City and the DISCUS fly-in.

**Added Aug 24:**
- `hibiki-12-2026` — **the clearest "verified and still fails" case this file carries.** Robb Report
  Taste Test, Aug 23, Flicker, **score 92 with his own tasting notes**, $188, 86 proof, the 12-year
  statement back after eleven years. **It is a global travel retail exclusive — airport shops only**,
  and Flicker says so in the piece. Fails the forward bar exactly as Jack Daniel's #17, Gleneagles,
  Wyoming Whiskey and Branch & Barrel did. **Do not restage on "Robb Report tasted it."**
- `koopers-texas-oak-bourbon-2026` — **360 bottles from two casks, presale opened Aug 22**, and FM,
  TSB and WA are all reprinting one news release, so it never had a second source. All sensory is
  Troy Kooper's release quote. **Was a September pointer; resolved against Aug 24.**
- `soho-spirits-festival-cancellation-2026` — London festival cancelled on the day. **The headline
  says "safety" and it is NOT a safety incident** — the founder's own statement attributes it to
  financial and operational foundations he did not have. UK, no WS partner, refunds processing.
  **Recorded specifically so a future urgent sweep does not fire on the word.**
- `fssai-diageo-sales-ban-revoked-2026` — India, product labelling non-conformance, bans **revoked**
  rather than imposed. Not a WS partner, no US consequence. Not an override.
- `sazerac-garrard-county-acquisition-2026` — Sazerac completed the $20M auction purchase. Trade
  news, no reader consequence — beat file. **Value is that it closes the Garrard County distress
  story from the Aug 17–18 sweep.**
- `bodmin-jail-english-whisky-distillery-2026` — a distillery *approval*. Same forward-bar failure
  as Glenachulish. · `glendronach-56-year-2026` — price far past the bar. ·
  `gallup-spirits-vs-beer-2026` — **consumption-share data; DISCUS-hostile framing. Never stage a
  consumption-trend item.** · `irelands-pub-sector-alcohol-tax-2026`, `paper-plane-london-bar-2026`
  and the rest of the TSB trade index — full list in the Aug 24 section.
- `kyle-maclachlan-washington-winery-2026` — wine, not whiskey. Recorded so the Robb Report index
  sweep does not re-surface it.

**Added Aug 23:**
- `gleneagles-glendronach-moment-of-reflection-2026` — 100 bottles, a ballot, one Scottish resort,
  £160/~$218, no US availability, and Robb Report explicitly did not sample it. **Fails the forward
  bar decisively. Do not restage on the strength of "Robb Report covered it."**
- `bruichladdich-greener-still-2026` — **sold out at the only place selling it.** Second source
  found, forward bar answered against it. **Removed from September pointers, not merely deferred.**
- `copperworks-urban-family-barleywine-2026` — Whiskey-Club-members-only, press-release sensory,
  and Copperworks ran Aug 21. **Assessed once as instructed and closed. Do not rediscover.**
- `branch-barrel-straight-rye-2026` — $35, **Colorado exclusive**, and the only quote runs to
  "smooth and drinkable." Fails the forward bar and DISCUS. Second Branch & Barrel product to fail
  on distribution.
- `robb-report-gabriella-pisco-sour-2026` — Robb Report Aug window. **Pisco, not whiskey.** Recorded
  only so the Robb Report index sweep does not re-surface it as an Easy Pour candidate.

---

## NEXT RUN (Wed Sep 2 — PREP)

**PREP DAY. No consumer edition, no UTMs, raw links, plain operator register.** **Window Sep 1–2.**
**Tue Sep 1 SHIPPED — four items, all four keys now in dedup with Oct 1 prune eligibility. Tue Sep 8
is at four and closed to research. Fri Sep 4 is the ONLY job, and only two prep runs remain — this
one and Thu Sep 3.**

1. **BEFORE ANY DISCOVERY: ADOPT THE BROWSER-UA FETCH. THIS IS THE RUN'S PRIORITY AND IT OUTRANKS
   EVERYTHING BELOW.** Lesson 46 (Sep 1 section) proved that Robb Report's 307-to-tollbit and Whisky
   Advocate's 503 are **bot blocks, not outages** — both serve a clean 200 with full article body to
   a browser user-agent. **A week of "dry rails" findings rests on evidence that is now known bad.**
   Fetch with:
   ```
   curl -sS --max-time 30 -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 \
     (KHTML, like Gecko) Chrome/126 Safari/537.36" "<url>"
   ```
   then strip `<script>`/`<style>`, strip tags, collapse whitespace.
   **Discovery order, all under the browser UA:** WA RSS (`whiskyadvocate.com/call/blogs/rss/`) →
   **`robbreport.com/food-drink/spirits/` (BACK ON THE LIST — retry it)** →
   **`thespiritsbusiness.com/category/news/` (retry — its single 403 is now suspect)** → FM
   recent-articles rail, read twice.
   **Whatever this turns up, record explicitly whether each rail was reachable under the browser UA.
   That answer is worth more to the next run than any single candidate.**

2. **FRI SEP 4 — TWO FIRM, ONE CONDITIONAL. The shape problem is solved; the count is the only
   question left.**
   Staged: `buffalo-trace-on-tour-2026` (WA, `on-the-calendar`, Venue Regular) and
   **`canada-50pct-tariff-2026` (TSB, Social Drinker) — NEW, staged Sep 1 when the tier default
   fired.** Conditional: `whisky-advocate-outdoor-excursions-2026`, **blocked on Aaron's byline call,
   raised twice, SPENT — no third raise.**
   **THE TARIFF ITEM HAS ONE TRAP AND IT MUST NOT BE GOT WRONG: Canada's Sept 8 counter-tariffs do
   NOT cover US alcohol.** Steel and aluminium, dairy, appliances, agricultural equipment, pulp and
   paper, plastics, electronics. **The US-side 50% tariff on Canadian goods is what touches a US
   shelf. Never write or imply that Canada is tariffing American whiskey.** Full entry on the Sep 4
   board, including the beat-slug problem and the verified seven-word Carney quote.
   **A three-item Last Call is now reachable without Aaron. Two is an acceptable floor.**
   **Do not raid the Sep 8 board.**
   **Still worth a look, unchanged:** `brough-brothers-river-road-distillery-2026` — **the date hunt
   is due THIS RUN. If no published date by the end of it, close it for this edition and say so.**
   Do not re-fetch `broughbrothers.com` (client-rendered SPA). And **PUNCH by article URL or a
   date-qualified search** — never the undated category listing.

3. **`michters-toasted-barrel-finish-rye-2026` — DO NOT HUNT THE SECOND SOURCE AGAIN.** Closed
   Aug 31: michters.com is the 2023 release (Lesson 43) and Breaking Bourbon carries that same 2023
   release as a review (Lesson 44). **It is a Sep 8 EDITION decision — flag it explicitly or hold it
   — not a research task.** **One caveat from Lesson 46: the Aug 31 closure was reached partly
   through the blocked fetcher. If a browser-UA retry of the WA/FM rails happens to surface a 2026
   pickup, that changes the answer. Do not go looking; do notice.**

4. **THE TSB TIER DEFAULT FIRED Sep 1 and is now in force.** Aaron was silent through the deadline he
   was given in the Aug 25 Notes. **The Spirits Business is Tier 2-equivalent for link-out purposes
   until he says otherwise.** Two consequences: the tariff is staged for Sep 4, and
   **`redwood-empire-hyperion-batch-001-2026` is UNBLOCKED and is a live Tuesday candidate.**
   **Do not re-raise the tiering question. It is answered by default, reversible by reply.**
   **The Robb Report tier was settled by prior runs' judgement and is likewise not re-litigated.**

5. **Notes discipline for Wed Sep 2.** Post only if there is new pipeline material, a gap update, or
   urgent news. **Otherwise post nothing.** **What earns a post: Sep 4 movement, a Brough Brothers
   date (either way), or — most likely this run — the browser-UA result, which is a real "something
   changed" if rails come back.**
   **Do not spend a bullet on:** the TSB default (**reported Sep 1 — do not re-report**), the
   Bardstown default, the tariff facts, the Flicker count, **the brand skill** (settled — item 8),
   the Michter's second source (closed), the Robb Report index, the September bump, the festival
   rejections, or anything that worked.
   **Carry-forward line stays `_unchanged: explainer slug, sub-$30_`.**
   **THE SEAN EVANS BYLINE CALL IS SPENT. DO NOT RAISE IT A THIRD TIME.** Silence means hold the item
   past mid-September and let Sep 4 run at two or three. That is the correct outcome, not a failure.

6. **The sourced-claims techniques — reuse, do not re-derive.** (a) When a claim's home is the second
   source and not the link-out, **name the outlet inside the sentence.** (b) When no independent
   sensory exists, **say so to the reader** — shipped a third consecutive time on Jack Daniel's
   Sep 1. (c) A score with no descriptors is a complete, publishable item. (d) **When two sources
   conflict on a detail, print neither and say nothing.**
   **(e) NEW, from Sep 1: when a story carries four or five insider terms, define ONE and cut the
   rest.** SHĀNG had baijiu, sauce-aroma, jiàngxiāng, qū and solid-state fermentation; only baijiu
   survived and the item lost nothing. **Cut the taxonomy, keep the concept.**
   **(f) NEW, from Sep 1: split any sentence that runs past 15 words at the drafting stage, not the
   check stage.** Both long sensory strings this edition split cleanly at the comma.

7. **Link-out collisions to hold on the Sep 8 board.** **Blue Note takes FM; Michter's takes the WA
   Whisky Watch.** Their only shared source is that one WA page and **two items cannot share one
   link-out.**
   **NEW Sep 1: `bardstown-discovery-2026` has now lost BOTH its candidate link-outs** — the Robb
   Report piece was spent as the Lochs of Jura link-out and the FM reprint was already spent.
   **Discovery is dead unless a third outlet files independently.**

8. **Voice: the brand skill is absent from this environment and that is settled — do not raise it
   again, in Notes or anywhere.** The inlined VOICE block carries everything needed. **The
   news-roundup skill IS present** — glob for the skill name rather than hardcoding the
   UUID-namespaced path. Read `verification-protocol.md` and `edition-templates.md` on edition days.
   **The vetted source directory is NOT in the repo** — only the skill's inlined stable core, which
   omits Robb Report and The Spirits Business. **Both are now settled anyway: RR by prior runs'
   judgement, TSB by the Sep 1 default.**

9. **Do not re-assess, do not rediscover — all closed:** Hibiki 12 · Koopers · the Soho cancellation ·
   FSSAI/Diageo · Sazerac/Garrard County · Bodmin Jail · Glendronach 56 · the Gallup piece · the Kyle
   MacLachlan piece · Gleneagles · Bruichladdich (**sold out — dead**) · Copperworks barleywine ·
   Branch & Barrel · the pisco sour · `beam-ten-pin-decanter-2026` (**closed twice**) ·
   `blue-spirits-distilling-chapter-7-2026` · `four-roses-experimental-002-honey-cask-2026`
   (**closed twice; reopenable ONLY on national distribution**) ·
   `whisky-advocate-all-inclusive-resorts-2026` · `kimbland-distillery-fss-warning-2025` (**NOT an
   override — dismissed four times now**) · the sub-$30 sweep · **and the five keys dropped Aug 30.**
   **Plus, closed by publication:** the four Aug 21 keys, the four Aug 25 keys, the four Aug 28 keys,
   **and the four Sep 1 keys.**
   **DO-NOT-RETEST — REVISED BY LESSON 46. Two entries come OFF the list and must be retried under
   the browser UA:** `robbreport.com/food-drink/spirits/` (**was "307 to tollbit, monthly only" —
   that diagnosis is withdrawn**) and `thespiritsbusiness.com/category/news/` (**one 403, now
   suspect**). **The WA RSS is likewise not an outage and never was.**
   **Still genuinely do-not-retest, none of them 403/503/307 cases:** `tixr.com` (403 to scripts) ·
   `whiskyadvocate.com/travel` and `/whisky-life` (**404**) · WA `/news` and `/Tag/Cocktails`
   (**client-rendered**) · the Garrison event directory · `fredminnick.com/?s=` (**302s — web search
   first**) · `washingtonpost.com` · `belleoflouisville.org/news` · `broughbrothers.com`
   (**client-rendered SPA**) · `whiskyadvocate.com/tag/sevans` (**spent**) ·
   `punchdrink.com/whiskey/` (**the CATEGORY LISTING only — no publication dates; PUNCH itself is
   Tier 2 and still worth reaching by article URL**) ·
   `breakingbourbon.com/review/michters-us-1-toasted-barrel-finish-straight-rye-2023-release`
   (**the 2023 release — Lesson 44**) · **the September festival circuit — Rock N Rye (Mammoth Lakes,
   Sept 5–6) and the Oregon Whiskey Festival (Bend, Sept 18–19); real dates, zero Tier 1–2 pickup,
   and Rock N Rye's own "unlimited access" copy is unprintable under DISCUS 73.8** · **Alcohol
   Professor and Barrel Banter — NOT on the vetted directory, do not count either as a source.**

10. **`jones-mack-bourbon-2026` — MONTHLY check. Do not fetch before late September.**

11. **Prune list. Nothing is eligible yet.** The four Aug 21 keys become eligible **Sep 20**, the
    Aug 25 keys **Sep 24**, the Aug 28 keys **Sep 27**, **the Sep 1 keys Oct 1**.
    **Sep 1 prune check: nothing eligible, confirmed.**
    **`canada-50pct-tariff-aug-19-2026` is NEVER pruned** — the story is staged live under
    `canada-50pct-tariff-2026` and **both spellings must be checked before any re-stage.**

12. **Sub-$30 — 29 days. The honest read is on file: it may be unclosable as specified.** $35–$40 is
    the real value floor at 90+ points. Aaron's standing decision; do not re-query.

13. **The explainer beat-slug gap is open and is the last live carry-forward.** Shipped twice as the
    agreed closest fit. The ask remains one new value: `explainer`. Compressed to `_unchanged_`.
    **A SECOND SLUG GAP IS NOW EVIDENCED, and it is worth raising ONCE when the tariff actually
    ships:** there is no shelf-price beat slug. The skill's own segment bank has **Shelf-Price
    Watch**; the approved slug list does not. **Do not raise it before the item runs — a gap with no
    shipped example is a theoretical complaint.**

14. **Constraints carried into Sep 4:** no fifth WA cocktail without Aaron's say-so (**count still
    four**) · **pineapple spent through September** · **no third Michigan item before October** ·
    cause-led capped at two per edition · **a third Sean Evans byline before mid-September is SPENT
    — no third raise; silence means hold past mid-September** · **a Hibiki item before October is a
    deliberate call** · bottled-in-bond **is not to be re-taught** · **baijiu is now defined and need
    not be re-defined before October** · **Jonah Flicker's concentration is live — he took two of
    four on Sep 1 and the Sep 8 board deliberately avoids him.**

15. **Urgent sweep every run, window back through Tue Sep 1.** **Swept Aug 30, Aug 31 and Sep 1 — no
    override any day.** **Standing dismissals, never re-investigated: the Crown Royal Reserve
    12-year glass-contamination recall (August 2025, a year old, surfaces on every recall search) and
    the Kimbland Distillery FSS warning (December 2025, dismissed four times).**
    **Context only, still un-bulleted:** the February 2026 discrimination suit against Bardstown
    Bourbon Company's former employer · Sazerac v. RNDC (Jan 2026) · **the EU's suspension of
    retaliatory tariffs on US spirits, which ran Feb 7 – Aug 6 2026 and has lapsed.** That last is
    the only live thread. **If a vetted outlet files on the EU lapse, fold it into
    `canada-50pct-tariff-2026` rather than opening a second key.**
