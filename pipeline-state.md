# The Pour — Pipeline State

Durable memory for the Whiskey Social whiskey-news pipeline. Authoritative over Slack
thread copies. Human feedback in #whiskey-news overrides this file.

**Last run:** 2026-08-23 (Sun), **PREP — the tariff question is ANSWERED, and Fri Aug 28 went
from empty to two staged.**
**Prior run:** 2026-08-21 (Fri), EDITION — Last Call, four items, prune executed.
**Prior editions:** Aug 21 (Fri, Last Call) · Aug 18 (Tue, The Shortlist) · Aug 14 (Fri) · Aug 11 (Tue).
**Next edition:** 2026-08-25 (Tue, The Shortlist).
**Next prep:** 2026-08-24 (Mon).
**Search window this run:** Aug 20–23 (covering back through Friday; Saturday does not run).

Twelfth consecutive run with a successful push. Write access stable.

**Channel check:** last 14 days read (Aug 9 – Aug 23). **No human replies from Aaron or Adam in
the window.** All 29 parent messages in the read are automated Pour posts authored through this
pipeline; the threads hanging off the older ones are this pipeline's own state-fallback dumps from
the write-access period, not replies. Adam's last real message was Jul 27 ("Seems to be creating
the same articles over and over"), now outside the window; **Aaron has never replied in the
channel.** **Nothing overrode this file.** **Nothing had been posted Aug 23 before this run, so
idempotency was not in play** — the newest message in the channel was the Aug 21 06:14 PT edition.

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

## FRIDAY Aug 28 — TWO STAGED (was EMPTY at the start of this run)

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

## TUESDAY Aug 25 — FOUR FIRM (mango study added Aug 19)

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

## TUESDAY Sep 1 — THREE STAGED, and the gap is closed

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
- **New pointers added Aug 23, all five sensory-blocked, none staged** —
  `koopers-texas-oak-bourbon-2026` (best sourced: TSB + WA + FM, but one release between them;
  360 bottles) · `barrell-new-year-blend-11-2026` (nationwide, the best forward-bar profile) ·
  `new-riff-sherry-finish-malted-rye-2026` · `bowmore-snarkitecture-oak-voyage-2026` ($360,
  Collector-only) · `dublase-signature-bourbon-trio-2026` (prices not published until Sept 1).
  **Full entries in the Aug 23 section. Every one needs its own link-out — the WA Whisky Watch of
  Aug 21 is spent on Filmland.**

---

## OPEN GAPS

- **Pair It — CLOSED Aug 21, after 34 days, by applying the recommendation as the default.** The
  gap was never supply; it was the definition — cigar-crossover or food pairing. **The Dubai
  chocolate item shipped under `pair-it`, so the beat now means food pairing in practice.** Aaron
  was told in one bullet that the recommendation had been applied; he reverses it by reply. **Do
  not re-open this as a question.**
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
- `jones-mack-bourbon-2026` — **RECHECKED Aug 23. UNCHANGED, still needs a second source.**
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

**Window Aug 19–20 (this run).** One broad search plus the full WA RSS feed, the Robb Report
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

Fetch-to-disk with a browser user-agent, then strip and slice locally. **Proven again on every
host used.** Strip `<script>` and `<style>` blocks with a DOTALL regex, not a line-based sed —
a line-based strip leaves kilobytes of inline JS in the text and buries the article.

- **`whiskyadvocate.com/call/blogs/rss/` — 200, ten dated items with titles and URLs. THE primary
  WA discovery path.** Produced both new items this run.
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

## OPERATIONAL LESSONS (24–26 added Aug 23)

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
- **The unreachable source directory cost nothing this run, and the Aug 17 escalation is
  withdrawn.** It blocked Redemption for exactly one day; a vetted outlet then turned out to cover
  the story. **A committed vetted-outlet list on this branch is still the right fix if a second
  item ever stalls on tiering — but it is not urgent, and it was right not to raise it with Aaron
  as its own Notes bullet.**

---

## DEDUP — closed to re-use

Story keys are lowercase-hyphenated `brand-product-year`. Prune at 30 days.

**Added Aug 21 (published in Last Call):**
`detroit-bourbon-blues-festival-2026` · `copperworks-farmsmith-spokane-relief-2026` ·
`whisky-advocate-dubai-chocolate-pairing-2026` · `whisky-advocate-thunder-bird-cocktail-2026`.
**All four are now PUBLISHED, not staged. Never re-publish, never re-scout.** Detroit is
additionally dead by event date after Aug 23.

**STAGED — not published, but closed to re-scouting (update the entry, never re-discover):**
Tue Aug 25 — `jameson-distillers-batch-single-pot-still-2026` ·
`heriot-watt-kirin-mango-aroma-study-2026` (**new Aug 19**) ·
`redemption-single-barrel-bonded-bourbon-2026` · `garrison-brothers-cowboy-bourbon-12-2026`.
Tue Sep 1 — `makers-mark-cellar-aged-2026` (**new Aug 19**) · `bardstown-lochs-of-jura-2026`
(**new Aug 19, link-out upgraded Aug 20**) · `shang-jiangxiang-whisky-2026` (**new Aug 20**).
**HELD, resolved, awaiting a vetted link-out — `canada-50pct-tariff-aug-19-2026`.** Aug 23: the
pause collapsed and the tariff is live. **Default applied — hold to Sep 1, recheck Robb Report and
The Spirits Business Monday.** The key is unchanged and stays held, never pruned while this is
open. **Do not re-key it to a collapse slug.**
**Added Aug 23 (STAGED for Fri Aug 28, closed to re-scouting):**
`filmland-malted-mummy-2026` · `whisky-advocate-distillery-glamping-2026`.

**Added Aug 23 (September pointers, closed to re-scouting):** `koopers-texas-oak-bourbon-2026` ·
`barrell-new-year-blend-11-2026` · `new-riff-sherry-finish-malted-rye-2026` ·
`bowmore-snarkitecture-oak-voyage-2026` · `dublase-signature-bourbon-trio-2026`.

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

## NEXT RUN (Mon Aug 24 — PREP)

**Prep run, internal register, no UTMs, raw links.** The next edition is **Tue Aug 25 (The
Shortlist)**, four firm.

1. **THE ONE CHECK THAT MATTERS: has a vetted outlet filed on the tariff collapse?** Sweep
   `robbreport.com/food-drink/spirits/` and `thespiritsbusiness.com/category/news/` for it first.
   **The story itself is resolved and does not need re-reporting** — the tariff has been live since
   12:01 a.m. ET Sat Aug 22, on $28bn of goods, with Carney pledging dollar-for-dollar retaliation.
   **The only open question is the link-out.** If one exists, the item becomes publishable and Aaron
   can have it Aug 25 as a fifth; **the standing recommendation is still Sep 1, because Aug 25 is
   four firm and balanced.** If none exists, say nothing new — **it is applied-by-default now, and
   re-noting it would be the fourth mention.** **Do not re-search the tariff facts.**
2. **Tue Aug 25 — FOUR FIRM. Do not add. Re-confirm the four link-outs on Tuesday morning, not
   Monday.** Jameson, mango study (both Robb Report), Redemption (Robb Report), Garrison
   (garrisonbros.com event page). **Do not re-search any of the four.** Live issue is the **Flicker
   concentration, three of four bylines** — if Aaron wants it broken up, **Garrison holds to any
   Tuesday through Sept 8** and that costs the board nothing.
3. **Fri Aug 28 — TWO STAGED, and the ask has changed shape.** It is no longer "find Friday
   material"; it is **"find ONE non-Whisky-Advocate Friday item."** Both staged items are WA
   link-outs. **Two verified items already clear the floor, so a third is a nice-to-have and must
   never be a padded one.** Constraints unchanged and all still clear: no pineapple, no Michigan,
   at most two cause-led, no fifth WA cocktail without Aaron's say-so. **Do not convert Hard Truth's
   Indianapolis Aug 28 event into a Last Call item — it is Tuesday material.**
4. **The seam that actually produced this run's Friday item: WA's Travel and Whisky Life sections,
   not its news feed.** Service journalism dates slowly and suits an occasion edition. **Try
   `whiskyadvocate.com` Travel and Whisky Life once on Monday** — a non-cocktail, non-event Friday
   source is the structural fix for the Friday problem, and one has now worked.
5. **Discovery order, now four deep and evidence-backed: Robb Report section index → WA RSS feed →
   FM recent-articles rail → The Spirits Business news index.** All four load and the fourth is
   new this run. **Do not vary the order.** Note Robb Report filed a dry week (three pieces, none
   stageable) — **that is normal variance, not a broken path.**
6. **Sep 1 — THREE STAGED, gap closed, all three carry sourced sensory. Do not add a fourth.** If
   one is added it must be neither Collector nor Flicker. The tariff item lands here if it gets a
   link-out.
7. **Do not re-assess, do not rediscover:** Gleneagles · Bruichladdich Greener Still (**sold out —
   dead, not deferred**) · Copperworks barleywine (**item 8 is closed**) · Branch & Barrel rye ·
   the Robb Report pisco sour. All five were assessed Aug 23 and are in DROPPED.
8. **`jones-mack-bourbon-2026` is now a MONTHLY check, not a per-run one.** Two rechecks, no
   movement. Do not spend a search on it before late September.
9. **Five new September pointers exist and every one is sensory-blocked** — Koopers, Barrell New
   Year, New Riff, Bowmore/Snarkitecture, Dublasé. **The WA Whisky Watch of Aug 21 is spent on
   Filmland, so each needs its own link before it can run.** Barrell has the best forward-bar
   profile (nationwide); Dublasé is un-stageable until prices publish Sept 1.
10. **Aaron owes one decision, and it has a firm default date. Bardstown link-out:** Robb Report's
   tasting or Fred Minnick's 99 IWSC points — not both. Recommendation on file is Robb Report.
   **If no reply by the Aug 28 run, apply it as the default and say so once**, per the Macallan
   precedent. **Compressed to `_unchanged_` until then.**
11. **Closed by default, do not re-surface as questions:** Pair It now means food pairing (applied
   Aug 21) · the explainer/travel beat-slug gap (the glamping item folds into it; **do not open a
   second bullet and do not invent a slug**) · sub-$30 (**Branch & Barrel at $35, Colorado-only, is
   more evidence the Tier 1–2 floor is $35–$40, not that supply was missed**).
12. **If Aaron has not raised the September seasonal third-edition bump by the Aug 28 run, surface
   it once.** Sept–Nov adds a third weekly edition per the skill. **Say the honest constraint in the
   same bullet: Fridays are the thin side, and a third weekly edition needs a fuller board than
   Aug 28 has.** His call, worth exactly one bullet.
13. Urgent sweep, window back through Sun Aug 23. **Recorded and deliberately un-bulleted:** a
   February 2026 discrimination suit against Bardstown Bourbon Company's former employer surfaced in
   the Aug 23 sweep. Six months old, no vetted whiskey outlet, nothing to decide. **Context only,
   for a Sep 1 item.**
14. **Do not re-derive the prune list.** Executed Aug 21; nothing eligible until late September. The
   four Aug 21 published keys become eligible **Sep 20**.
15. Do not re-test the WA bars subdomain before September. Do not re-fetch `/news` or
   `/Tag/Cocktails`. Do not re-fetch the Garrison event directory. Do not surface Macallan,
   Moonshine University, Jack Daniel's #17, Strathearn or Brown-Forman earnings — all closed.
