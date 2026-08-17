# The Pour — Pipeline State

Durable memory for the Whiskey Social whiskey-news pipeline. Authoritative over Slack
thread copies. Human feedback in #whiskey-news overrides this file.

**Last run:** 2026-08-17 (Mon), **prep — POSTED.**
**Prior run:** 2026-08-16 (Sun), prep, posted.
**Last edition:** 2026-08-14 (Fri, Last Call). Prior edition Aug 11 (Tue, The Shortlist).
**Next edition:** 2026-08-18 (Tue, The Shortlist) — tomorrow.
**Next prep:** 2026-08-19 (Wed).
**Search window this run:** Aug 15–17.
A light run by design, as the Aug 16 file instructed. Two staged items materially advanced.

Seventh consecutive run with a successful push. Write access stable.

**Channel check:** last 14 days read (Aug 3 – Aug 17). **No human replies from Aaron or Adam in
the window.** Every parent message Aug 3 – Aug 16 is an automated Pour post authored through this
pipeline. Thread replies exist only on posts Aug 9 and older and are this pipeline's own PIPELINE
STATE overflow from the period when pushes were failing. Adam's last real message was Jul 27
("Seems to be creating the same articles over and over"), outside the window and already addressed
by the dedup discipline. **Nothing overrode this file.** The channel's most recent post before this
run was Sun Aug 16, so nothing had been posted today and idempotency was not in play.

---

## MONDAY Aug 17 — what this run actually found

Both explicit assess-today tasks are resolved. **Garrison Brothers Cowboy is unblocked** — it now
has its own Tier 1 link-out and no longer competes for the Whisky Watch. **Redemption has a
credible link candidate** that turns on one tiering decision only Aaron can make. Two new
candidates assessed and both rejected. Urgent sweep clean. Whisky Advocate published nothing.

### Posted to the channel

Two staged items: Garrison Cowboy and Redemption, both Aug 25. Notes carried the Shanken tiering
call, the Garrison age conflict, and the WA supply note. Macallan compressed to `_unchanged_`
for the third run — it has now been surfaced Aug 14, Aug 16 and Aug 17.

### Tuesday's four links re-confirmed early

Not a re-scout — a load check, done because tomorrow is an edition day and it costs four requests.
**All four load 200 with real article bodies:** Buffalo Trace (1,085 words), First West Explorer
(923), Old Overholt via Robb Report (1,374), Chattanooga via Fred Minnick (760). Tomorrow's run
still owns the re-confirm step, but no link is dead as of today. Not surfaced in Notes — nothing
for a human to do.

---

## THE WHISKY ADVOCATE RSS FEED — the primary discovery path (found Aug 16)

**`https://whiskyadvocate.com/call/blogs/rss/` returns 200 and yields ten dated article links
with titles, newest first.** It is now the primary discovery path for Whisky Advocate.

This matters because **the WA HTML indexes regressed this run.** As of Aug 14 the state file
recorded `/Tag/Cocktails` rendering ~12 article links. Today:

- `whiskyadvocate.com/news` — 301 to `/News`, loads 200 with a browser UA, **zero article links.**
  Nav and stylesheets only. The article grid is now client-rendered.
- `whiskyadvocate.com/Tag/Cocktails` — 200, **exactly one article link**
  (`/peach-and-whisky-cocktail-recipes`, already covered). Effectively dead as an index.

The RSS feed replaces both. It is cheap, dated, and complete for the last ten posts.
**Sweep the RSS feed first on every run.** Keep reading WA article-page footers as the
secondary path — they still carry three related-article links each.

**Aug 17 update — the feed is UNCHANGED from Aug 16. Ten items, newest still Aug 14.**
Whisky Advocate published nothing Aug 15, 16 or 17. This is the first time the RSS sweep has
returned zero new items, and it is the whole reason today was thin. It is a supply observation,
not a host failure — the feed returned 200 and parsed cleanly. **Do not read a quiet weekend as a
broken feed;** re-check Wed Aug 19 before drawing any cadence conclusion.

Feed contents as read Aug 16 and re-read unchanged Aug 17 (Aug 6 – Aug 14), for dedup reference:

| Date | Title | URL |
|---|---|---|
| Aug 14 | News Notes: Chip Tate Does Mezcal, New Highlands Distillery | `/whisky-news-roundup-august-14-2026` |
| Aug 14 | Whisky Watch: Jameson, Redemption Bonded & More | `/jameson-single-pot-still-garrison-cowboy-and-more-new-whiskey` |
| Aug 14 | Auction Update: Momentum Returns | `/whisky-auction-results-august-14-2026` |
| Aug 13 | Cuervo Mole Cask Tequila | `/jose-cuervo-reserva-de-la-familia-mole-cask` |
| Aug 12 | Dubai Chocolate pairing | `/dubai-chocolate-and-whisky-pairing` (staged Aug 21) |
| Aug 11 | Whiskey of the Week: First West Explorer | `/first-west-explorer-reviewed` (staged Aug 18) |
| Aug 10 | Louisville Rickhouse Whiskey Co. | `/louisville-rickhouse-whiskey-co-tastings-guide` (covered) |
| Aug 7 | Whisky Watch: Macallan, Raasay, Old Overholt | `/macallan-glenfiddich-jack-daniels-and-more-new-whiskey` (spent) |
| Aug 7 | News Notes | `/whisky-news-roundup-August-7-2026` |
| Aug 6 | Stetson bourbon review | `/stetson-bourbon-review` (covered) |

---

## THE SHARED-LINK CONSTRAINT — new standing rule

**A Whisky Watch roundup is ONE link-out, not four.** The Aug 14 Whisky Watch carries six
separate releases: Jameson, Bruichladdich Greener Still, Garrison Brothers Cowboy, Redemption
Bonded, Chattanooga ice wine, and Breckenridge Peach. Three of those are now staged.

The edition rule is **exactly one link per item.** Two items pointing at the same URL is a
formatting failure and reads as padding to anyone who clicks. So:

- **Spend the Aug 14 Whisky Watch on ONE item.** Recommend **Jameson** — it is the strongest
  Explorer item on the Aug 25 board and the roundup leads with it.
- **Redemption and Garrison Cowboy each need their own Tier 1–2 link before they can run.**
  Neither has one yet. See their entries below for what was searched and what failed.
- Chattanooga escapes this entirely — it has an independent Fred Minnick article.

This is the same shape as the Aug 7 Whisky Watch, already marked a spent link-out. **Treat every
Whisky Watch as a single spendable link from the moment it is first mined.**

**Aug 17 — the constraint is now largely dissolved, by finding the items their own links.**
Garrison has its own Tier 1 event page. Redemption has a Shanken candidate pending Aaron's call.
Chattanooga always had Fred Minnick. **So the Aug 14 Whisky Watch is still reserved for Jameson,
but nothing else is now waiting on it.** This is the pattern to repeat: **when a roundup strands an
item, the fix is to go find that item its own primary source — usually the brand's own dated
release or event page — not to queue it behind the roundup.** Two of three strandings cleared in
one run at a cost of about six requests.

---

## TUESDAY Aug 18 — FOUR FIRM. Macallan out, Chattanooga in.

Board: Buffalo Trace (Collector, heavy sensory) · First West Explorer (Explorer, sensory, $50
nationwide) · Old Overholt 11-year (Collector, no sensory) · **Chattanooga Moldovan ice wine
(Explorer, no sensory, non-WA link)** · Raasay as a September pointer.

**Macallan Harmony VI — recommend CUT, unchanged since Aug 13, surfaced in the Aug 14 Notes and
again today.** Default if no reply: cut it. Chattanooga takes the slot.

**Shape after the swap — materially better than Aug 14's read:**
- Outlets go from three-of-four WA to **two WA, one Robb Report, one Fred Minnick.** This is the
  best outlet mix any Tuesday board has carried.
- Persona balance improves: Collector 2, Explorer 2, versus three-of-four Collector before.
- Sourced sensory still only two of four (Buffalo Trace, First West). Chattanooga carries none and
  that is fine — see its print caution below.
- First West remains the Try This Next lead and the only sub-$60 nationwide bottle.

- `buffalo-trace-2026-prohibition-collection` — VERIFIED, two independent Tier 2 reviews each with
  its own tasting notes: WA Jul 22 (Sean Evans, link-out) and Breaking Bourbon. Third edition ·
  five 375ml bottles, set only, **$1,000** · shipping since June via Sazerac's distributor network ·
  five revived Stagg-era names from Blanton's presidency — Henry Watterson, Kentucky River,
  John G. Carlisle, Walter B. Duffy, Cove Spring · cartons keep the prescription cut-out.
  Strengths: Carlisle 50%, Duffy 53.5% (10+14yo blend), Kentucky River 50%, Cove Spring Uncut 60.1%,
  **Watterson rye 70.3%, highest-proof rye in the distillery's modern history.** **The hook: the two
  reviews disagree on the standout** — Evans names Kentucky River then Cove Spring, Breaking Bourbon
  calls the Watterson rye "downright exceptional." Wheatley quote runs long. Avoid vault/cellar/
  whale framing entirely on a $1,000 set.
  Link: `https://whiskyadvocate.com/buffalo-trace-2026-prohibition-collection-review`
- `first-west-explorer-black-corn-2026` — VERIFIED. WA Aug 11, Danny Brandon, note signed David
  Fleming. 92 points · 47.5% · $50 · **nationwide, permanent.** WA's own note: nose ginger, dried
  herbs, cinnamon, caramel, baked apple, vanilla, barrel char; palate nutmeg, almond, vanilla
  coconut ice cream; finish chocolate, spice, peanuts. Two bourbons blended — wheated base 70%
  yellow dent / 18% wheat / 12% malted barley, plus ryed 70% **Baby Black** corn / 18% rye / 12%
  malted barley. Age-stated 5 years, some older liquid. Rick and Ricky Johnson; grain interest from
  the family popcorn business. Sister label to 15 Stars. **Print WA's "contract-distilled at
  Bardstown Bourbon Co.," never the brand's "100% in-house."** Never mix the brand's own notes
  (cherry, banana pudding, meringue) with WA's. The butter/peppermint line is the Johnsons' claim.
  Link: `https://whiskyadvocate.com/first-west-explorer-reviewed`
- `old-overholt-11yr-extra-aged-rye-2026` — VERIFIED. Robb Report Jul 30 (Jonah Flicker, original
  reporting — exclusive response from **Bradford Lawrence**, Beam) + WA Whisky Watch Aug 7. Fourth
  in the line, **11yo at 125.6 proof, the highest of the four** · SRP $110 · select retailers
  nationwide, on shelf since July · distilled spring 2014 · three Clermont warehouses · core
  Overholt roughly 51% rye · proof went 80 → 86 in 2022 with a four-year age statement added.
  **NO INDEPENDENT SENSORY — Robb Report states it received no sample.** Circulating notes are the
  brand's. Honest hook: the proof went up and the age came down. Do not frame it as an upgrade.
  Lawrence's quote runs long; a clean 10-word fragment exists but prefer no quote.
  Link: `https://robbreport.com/food-drink/spirits/old-overholt-extra-aged-cask-strength-rye-whiskey`
- `chattanooga-moldovan-ice-wine-2026` — **NEW THIS RUN. VERIFIED, two independent Tier 1–2
  sources.** Fred Minnick Aug 14 (the link-out) and WA Whisky Watch Aug 14.
  **What FM supports:** eighth entry in the Barrel Finishing Series · ice wine casks from one of
  Moldova's oldest wineries, in the hills above the Black Sea · a blend of **six mash bills, five
  malt whiskeys and one bourbon** · specialty toasted malts including a malted barley grown on
  Italy's coast near Venice and two types of malted wheat · **aged over four years, including more
  than a year in the finishing casks** · **bottled at 95 proof** · available at the Chattanooga
  Whiskey Experimental Distillery **Thursday Aug 13** · on shelves in **DC, FL, GA, IL, MD, MN, MO,
  NJ, NY, TN, TX, WI** — that is **eleven states plus DC** · **$59.99 / 750ml** · limited online
  shipping via Seelbachs.com · Grant McCracken is Founding Distiller.
  **What WA adds independently:** 47.5% ABV (consistent with FM's 95 proof) · $60 · availability
  given as "at the distillery and online" — **narrower than FM's state list; print FM's, it is the
  more specific and more recent claim, and FM is the link-out.**
  **PRINT CAUTION — the sensory trap.** WA's "honey, lychee, stone fruits, and bright citrus" is
  **WA describing ice wine as a category of wine.** It is not a tasting note for this whiskey.
  **Neither source tasted this whiskey. No sensory exists. Do not write any.** This is the same
  trap already logged on Raasay's Hungarian oak and Macallan's coconut.
  McCracken's quotes are about process (frozen grapes, matching mash bills to cask) — usable as
  voice, not as sensory. The ice-wine explainer is the natural intimidation-pass definition.
  Link: `https://www.fredminnick.com/2026/08/14/chattanooga-whiskey-releases-moldovan-ice-wine-cask-finished/`
- `macallan-harmony-vi-coconut-2026` — staged, **recommended cut, second run of asking.** Fresh
  Coconut 46.3% $185 nationwide; Toasted Coconut 43.3% $185 travel-retail. Kirsteen Campbell,
  sherry-seasoned American oak and bourbon barrels. Concludes a six-year run of 12 NAS whiskies
  begun 2021. Packaging uses discarded coconut fibres. **Coconut is cask intent and brand framing,
  not a WA tasting note — do not print it as sensory.** If Aaron reverses the cut, the edition runs
  five and Chattanooga is the one to hold, not Macallan.
- `isle-of-raasay-hungarian-oak-oloroso-2026` — staged, forward pointer. 50% ABV, $110, global
  release of 8,000 bottles from **September**, ImpEx Beverages. Oloroso casks of Quercus petraea
  from Hungary's Zemplén Mountains. Peated and unpeated spirit distilled 2021, matured separately,
  then married. All on Raasay, an island of 161 residents, printed on every bottle. **WA did not
  taste it** — its lines about Hungarian oak and oloroso describe how the wood generally behaves.
  **Do not convert either into a tasting note.**

---

## FRIDAY Aug 21 — THREE FIRM. Non-WA gap CLOSED.

- `detroit-bourbon-blues-festival-2026` — **VERIFIED, price resolved by default.**
  Sun Aug 23, Eastern Market Shed 5, 2810 Russell St, 12–7pm, 21+, blues from Rome Antenucci,
  Free Style Band Detroit, Shaun Booker Dammit Band, cocktail classes with Louisville Tourism,
  proceeds to the FernCare Free Clinic. Link detroitbourbonandblues.com (Tier 1, organizer);
  second source the Eventbrite listing. **Print $55 GA / $75 VIP, official site only.**
- `copperworks-farmsmith-spokane-relief-2026` — **NEW THIS RUN. VERIFIED. This is the non-WA item
  the board has wanted since Aug 13.**
  Sources: Fred Minnick Aug 14 (the link-out, and the fullest version) + WA News Notes Aug 14
  (independent Tier 2 corroboration) + Copperworks' own statement (Tier 1 primary).
  **What both sources support:** throughout **August**, Copperworks donates **$20 from every bottle
  of Farmsmith American Single Malt sold** to the **H.O.M.E. Starts Here** Spokane Complex Fire
  Relief Fund · the fund provides rent assistance, medical equipment, transportation and other
  necessities · Copperworks is Seattle-based, opened 2013, founded by **Jason Parker** and Micah
  Nutt · Farmsmith explores single-variety, single-farm, single-year barley · the current release
  uses **single-varietal Genie barley grown 20 miles west of Spokane**, malted by **LINC Malt in
  Spokane** · direct donations also possible at my.spokanecity.org.
  **Parker's quote is 18 words and clean:** "The farming families and partners around Spokane
  aren't just our suppliers; they are our friends." Named, real, in both linked sources. **This is
  the best quote candidate on the Aug 21 board.**
  **NOT SOURCED — do not invent:** no price, no ABV, no age, no distribution footprint for
  Farmsmith. The Copperworks product page is client-rendered and returned no readable price this
  run. **The item does not need a price; write it without one.**
  **No sensory anywhere. None to write.**
  **Tone and compliance:** this is a live disaster. Write it quiet and factual. It is NOT an
  urgent-override item — the override bar is recall, safety, litigation, or a death in the
  industry, and a charitable release is none of those — so it runs in the normal slot. But no
  payoff-line cleverness and no occasion framing. State the fact, name the fund, link out.
  **DISCUS watch:** never imply that buying more gives more. State the donation once, flatly.
  Link: `https://www.fredminnick.com/2026/08/14/new-copperworks-release-to-help-fund-spokane-firefighting-effort/`
- `whisky-advocate-dubai-chocolate-pairing-2026` — **VERIFIED.** Full detail in the block below.
  Serves Pair It if the beat is redefined; otherwise runs as Try This Next.
  Link: `https://whiskyadvocate.com/dubai-chocolate-and-whisky-pairing`
- **Easy Pour — coverable from alternates, not staged as a new item.** Ranked: (1) Lost Irish
  cucumber, newest and no collision; (2) Coconut Manhattan; (3) Vintage Coco, oldest and colliding.

**Outlet mix now: organizer site, Fred Minnick, Whisky Advocate — plus a WA cocktail if an
alternate runs.** That is one WA of three firm, versus two of two before this run. The gap that
has been open since Aug 13 is closed. **If an Easy Pour alternate runs it makes two WA of four,
which is acceptable, but it would also be a fourth straight Friday of a WA cocktail** — see
COLLISION FLAGS. Copperworks arriving makes it easier to simply skip the cocktail this week.

### Carried forward — `whisky-advocate-dubai-chocolate-pairing-2026`

**WA, Aug 12 2026, "Dubai Chocolate: How to Pair This Viral Dessert with 7 Stunning Whiskies,"
Pete O'Connell.** Runs Aug 21 nine days old — fine for an evergreen pairing feature with no date peg.
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

Also supported: Dubai chocolate is Belgian chocolate filled with pistachio cream, tahini and fried
kataifi (shredded phyllo) · invented 2021 by **Sarah Hamouda**, British-Egyptian engineer, with
culinary consultant **Nouel Catis Omamalin** · **FIX Dessert Chocolatier** opened in Dubai 2022,
flagship bar **Can't Get Knafeh Of It** · **WA states its popularity has contributed to worldwide
pistachio shortages — attribute that to WA, it is their claim** · Rampur is Himalayan-foothills,
bourbon barrels plus Australian shiraz casks · Port Charlotte is Bruichladdich, Islay, peated ·
Wild Turkey Rare Breed rye is non-chill filtered · Peerless Double Oak is 4+ years in one new
charred barrel then a second · Hibiki blends malt and grain from three Suntory distilleries,
includes mizunara · Redbreast 12 is Midleton, triple-distilled single pot still, bourbon and oloroso
casks · High Wire has used the near-extinct **Jimmy Red** corn varietal since 2013.

**Print cautions:** (1) **No usable quote** — Todd Robinson's lines run 22 words and longer; prefer
none. (2) **Do not reproduce WA's phrasing around drinking pace** ("wash it down with sips,"
"sipping this between bites") — DISCUS 73.8. (3) **Do not lead on Wild Turkey** — see COLLISION
FLAGS. (4) Hibiki's mizunara "sandalwood and coconut" is WA describing the wood; do not make it
the hook.

**New collision noted this run:** Redbreast 12 in this list is a **single pot still** Irish whiskey,
and Jameson Distiller's Batch — staged for Aug 25 — is also single pot still, and WA's Jameson
write-up names Redbreast explicitly. Not a blocker four days apart, but **do not let "single pot
still" be the teaching moment in both editions.** Spend it on Jameson, where it is the whole story.

---

## TUESDAY Aug 25 — THREE STAGED. Garrison unblocked, Redemption on a tiering call.

- `jameson-distillers-batch-single-pot-still-2026` — **NEW THIS RUN. VERIFIED.**
  Sources: WA Whisky Watch Aug 14 (the link-out) + the Pernod Ricard release of Aug 11, carried by
  PR Newswire and BevNET. Those reprints are ONE source between them; WA is the independent second.
  **What WA supports:** **46% ABV · SRP $50 · nationwide beginning September, imported by Pernod
  Ricard USA** · a single pot still whiskey, not a blend — a departure from Jameson's flagship
  profile · triple-distilled from a mash of **malted and unmalted barley** at **Midleton Distillery**
  near Cork, by master distiller **Kevin O'Gorman** · matured in **five cask types**: first- and
  second-fill bourbon, oloroso from the Antonio Páez Lobato cooperage, and virgin Irish, American
  and European oak · **originally released in Europe in 2022** as Jameson Single Pot Still ·
  historical peg: a single pot still mashbill written by **John Jameson II in 1826** at Bow Street
  Distillery, Dublin · WA calls single pot still "Ireland's signature whiskey style" and names
  Redbreast, Spot, Method and Madness, Powers and Midleton Very Rare as portfolio siblings.
  **From the release only, and weaker:** $49.99 rather than WA's $50, and pre-sale open now on the
  Jameson site. **Prefer WA's figures; the pre-sale is worth one clause if the item runs early.**
  **NO SOURCED SENSORY.** The release's "toasted oak, honeycomb, salted caramel, dark chocolate,
  spicy toffee, cinnamon, ginger, orange peel" is **brand copy. Do not print it.** Forbes' piece is
  a contributor column — **Tier 4, do not cite, do not link.**
  **Why it is the strongest Aug 25 item:** big recognizable name, $50, nationwide, and a genuine
  insider term the intimidation pass can define in one plain clause — single pot still means malted
  and unmalted barley, distilled in a pot still, at one Irish distillery.
  Link: `https://whiskyadvocate.com/jameson-single-pot-still-garrison-cowboy-and-more-new-whiskey`
- `redemption-single-barrel-bonded-bourbon-2026` — **ASSESSED THIS RUN as instructed. VERIFIED on
  facts, BLOCKED on a link.**
  Sources: WA Whisky Watch Aug 14 (Tier 2) + the brand release of Aug 13 via PR Newswire and BevNET
  (Tier 1 primary, reprints count as one). Two sources, clean.
  **What WA supports:** **50% ABV · SRP $50 · availability "Limited"** · the brand's **first
  bottled-in-bond whiskey** · **Ross & Squibb-sourced distillate aged 6 years** · each barrel
  hand-selected by master blender **Alan Kennedy** · bottled by Redemption in **Frankfort, Kentucky**
  · marks the relaunch of the Higher Marques line, whose prior releases were a Cognac Cask Finish
  high-rye and a wheated bourbon · **begins rolling out next month, in stores and at
  reservebar.com** · separately, **Redemption's Ancients Series 18 year old returns this fall at
  $400**, a blend of ultra-aged MGP barrels, matching last year's price.
  **From the release only:** mashbill **60% corn / 36% rye / 4% malted barley**, non-chill filtered,
  six-bottle cases, ongoing rather than one-time, $49.99.
  **CONFLICT TO RESOLVE BEFORE PRINT:** WA says availability is **"Limited."** The brand release
  says **nationwide.** These do not agree. **Print WA's "limited," or print neither and say only
  that it rolls out next month in stores and at reservebar.com.** Never print "nationwide."
  **NO SOURCED SENSORY.** The circulating "vanilla, worn leather, raspberry, crème brûlée, sweet
  corn, baking spice, caramel, oak" is **brand copy from the release. Do not print it.**
  **THE LINK BLOCKER — Aug 17: a credible candidate found, pending ONE decision.**
  Prior state: no independent link existed. Nine FM slug guesses 404'd, FM's `?s=` endpoint 302s,
  and Gear Patrol, Bourbon Lens, Northwest Beer Guide, The Whiskey Reviewer and The Whisky Wire are
  all unvetted, Tier 3–4, or hard avoids.
  **NEW: `shankennewsdaily.com`, Aug 13 — "Deutsch Extends Redemption At The Higher End After
  Successful Brand Revamp." Loaded 200 and read in full.** This is **original reporting, not a
  reprint.** It carries an interview with **Dan Kleinman, chief marketing officer, Deutsch Family
  Wine & Spirits** ("tells SND") and Impact Databank data that appears in no other write-up:
  **Redemption is at roughly 85,000 cases in the US market**, and Kleinman puts the brand "up very
  high single digits" year-to-date in a declining bourbon segment. It independently confirms
  **$50, a six-year minimum, and Alan Kennedy as master blender**, and frames the six years as
  **two years longer than bottled-in-bond requires** — a genuinely better hook than the release copy.
  It also corroborates **The Ancients 18-year-old returning this fall at $400.**
  **USABLE QUOTE — the first clean one this item has had.** Kleinman, 18 words, in the linked
  source: "We're pairing the individuality of hand-selected single barrel with the discipline of
  bottled-in-bond, which makes this really unique." Named, real, under 20. Verified by hand count.
  **THE OPEN DECISION — outlet tiering, and it is Aaron's, not this pipeline's.**
  Shanken News Daily is **not on the inlined vetted list.** In its favour: it is M. Shanken
  Communications, **the same publisher as Whisky Advocate**, which is Tier 2; it is established
  trade press; and this piece is plainly original reporting. Against: it is unlisted, and the living
  source directory in project knowledge — which would settle it — has been unreachable for
  twenty-two runs. **Do not silently promote an unvetted outlet to Tier 2 to unblock an item.**
  Surfaced in Notes Aug 17. **If Aaron approves it, Redemption clears completely and can run
  alongside Jameson, since it no longer needs the Whisky Watch.** If he declines, hold it — the
  September rollout means holding still costs nothing.
  **Note the availability conflict is NOT resolved by Shanken** — it says only "next month" and
  states no footprint. WA's "Limited" versus the release's "nationwide" still stands.
  **Never print "nationwide."**
  Link candidate: `https://www.shankennewsdaily.com/2026/08/13/40660/deutsch-extends-redemption-at-the-higher-end-after-successful-brand-revamp/`
- `garrison-brothers-cowboy-bourbon-12-2026` — **UNBLOCKED THIS RUN. VERIFIED, two sources, and it
  now has its OWN Tier 1 link-out.** This was assigned task 3 for today and it is done.
  Sources: **`garrisonbros.com/events/2026-cowboy-bourbon-release/` (Tier 1, the brand's own dated
  event page — the link-out)** + WA Whisky Watch Aug 14 (Tier 2). Two independent sources.
  **What the Tier 1 event page supports:** **Sat Sept 12 2026, 8:00 am – 4:00 pm** ·
  **Garrison Brothers Distillery, 1827 Hye-Albert Rd, Hye, TX** · **bottles $249.99** ·
  **141.0 proof** · uncut, unfiltered Texas straight bourbon · **"at least six scorching Texas
  summers" in the barrel barn** · live music, neat pours and cocktails from the Whiskey Shack.
  **What WA adds independently:** 12th edition · **70.5% ABV** · SRP $250 · **16,000 bottles** ·
  **1,000 bottles held for the launch event, 279 on the online store from Fri Sept 18**, remainder
  nationwide.
  **Cross-check — the numbers agree where it matters.** 141.0 proof is exactly 70.5% ABV, so the
  Tier 1 page and WA are consistent on strength. $249.99 and WA's $250 are the same figure; **print
  $249.99, it is the brand's own and the link-out's.**
  **CONFLICT TO RESOLVE BEFORE PRINT — age.** WA says **"aged at least 8 years."** The brand's own
  event page says **"at least six scorching Texas summers."** Six versus eight. These do not
  reconcile, and the brand is both the primary and the link-out. **Recommendation: print no age at
  all.** The proof, the price and the date are the interesting facts and all three are clean. If an
  age must appear, use the brand's six and attribute it. **Never split the difference.** Surfaced
  in Notes Aug 17.
  **BOTTLE COUNTS REMAIN SINGLE-SOURCE.** The 16,000 total and the 1,000/279 split are WA only —
  the event page states no counts. The 1,000/279 split is the most interesting Collector detail on
  the item, so **if it is printed, attribute it to Whisky Advocate.**
  **SENSORY — do not print.** The event page carries "toasted caramel, baked spices, molasses, and
  vanilla... ripe plums dipped in 70% dark chocolate." That is **the brand's own marketing copy**,
  the same posture already refused on Jameson, Redemption and Hard Truth. Nobody independent tasted
  this release. It also runs through "decadent" and "intensely flavorful," and the page's own
  "experience" is a banned word. **Write no sensory.**
  **DO NOT MINE THE EVERGREEN PRODUCT PAGE — new trap, logged below as a lesson.**
  `garrisonbros.com/cowboy-bourbon/` is the undated brand page and states **73.2% ABV / 146.4
  proof**, plus its own tasting notes ("burnt wood, gun smoke, toasted marshmallows"). **That is a
  DIFFERENT, earlier release.** Printing from it would have put the wrong proof in the edition.
  **Only the dated event page describes the 2026 bottling.**
  **Slot:** staged Tue Aug 25, but the event is Sept 12 — **it also runs fine on any Tuesday up to
  Sept 8**, and a September Tuesday is arguably the better peg. No urgency either way.
  Note `garrison-brothers-laguna-madre-2026` is in dedup — **different bottle, not a repeat.**
  `garrison-brothers-hye-rye-presale-2026` was dropped separately.
  Link: `https://www.garrisonbros.com/events/2026-cowboy-bourbon-release/`

---

## SEPTEMBER POINTERS

- `hard-truth-dark-roast-rye-2026` — **ASSESSED THIS RUN as instructed. Article opened in full.**
  FM Aug 11. **Third 2026 Master Distiller's Reserve · 25-barrel batch · a 50/50 blend of RW-3
  (51% rye / 38% corn / 11% chocolate malted barley) and RW-4 (51% rye / 38% corn / 11% caramel
  malted barley) · bottled-in-bond at 100 proof / 50% ABV · MSRP $59.99 · September release.**
  Featured at Hard Truth's **Harvest Festival, Nashville Indiana, Saturday Sept 26.** Two preview
  events: **Cask & Still Social at Hard Truth, Fri Aug 21**, with live jazz from Louisville's
  Bourbon & Brass Quintet, and **Whiskey Social at the Garage at Bottleworks, Indianapolis, Fri
  Aug 28.** Both offer small plates, distiller intros, tasting stations, and limited bottles.
  **THE OPEN QUESTION IS NOW NARROWER, NOT CLOSED. Price is resolved at $59.99. Distribution is
  NOT — FM's article states no state footprint at all.** The "more than 20 states" figure surfaced
  only in a search summary of The Manual, which is 403 to scripts and unvetted. **Do not print any
  distribution claim.** Without one, the forward bar rests on the September date and the festival.
  **SENSORY IS BLOCKED.** "Complex, sweet, malty, dark and brooding" is **Bryan Smith quoted from a
  news release** — brand copy, and the same words already flagged on Aug 14. Technically it is a
  named speaker in the linked source, so it is quotable *as his claim*, but it is marketing and it
  runs long. **Prefer no quote.** Never print it as a tasting note.
  **The Aug 21 preview event was considered for Friday and rejected** — single-market Indiana, same
  day as publication, and Detroit already holds the calendar slot. **The Aug 28 Indianapolis event
  is the better peg** if Hard Truth runs at all.
  Note the coincidence: Hard Truth's Aug 28 event is literally named "Whiskey Social." Cosmetic,
  no action, recording it so a future run does not read it as a partner mention.
  Link: `https://www.fredminnick.com/2026/08/11/hard-truth-announces-release-of-distillers-reserve-dark-roast-rye/`
- `bruichladdich-greener-still-2026` — **NEW, single source (WA Whisky Watch Aug 14).** 51.6% ABV,
  $160, **Limited.** 15 year old unpeated Islay single malt, the last of three 25th-anniversary
  bottlings after Yellow Submarine III and Old Skool. Distilled from organic, biodynamic and bere
  barleys — the biodynamic from Yatesbury House Farm in Wiltshire, England, Bruichladdich's sole
  exception to its all-Scottish-barley rule; the bere grown on Orkney with the University of the
  Highlands and Islands Agronomy Institute. Entirely first-fill bourbon casks. Fourth in the Still
  Series after Blacker Still, Redder Still, Golder Still. No sensory.
  **"Limited" at $160 tests the forward bar.** Collector-only. **Shares the spent Whisky Watch
  link.** Low priority — behind Garrison.

---

## OPEN GAPS

- **Pair It — 29 days, actionable, unchanged.** A Tier 2 food pairing with its own sensory is on
  the board. The gap is a definition, not supply. **Recommend redefining as food pairing.**
  Surfaced Aug 13 and Aug 14; compressed to `_unchanged_` today and Aug 14. Do not re-explain.
- **Sub-$30 — 24 days.** Aaron's decision, not re-queried per standing instruction. No relief this
  run. Nothing found Aug 14–16 under $30 from a Tier 1–2 source. Cheapest new item is Breckenridge
  Peach at $35, and it is rejected on other grounds.
- **Aug 21 non-WA supply — CLOSED this run** by Copperworks. Open Aug 13–16, four days.
- **Aug 25 link supply — LARGELY CLOSED Aug 17.** Was: three staged items, one usable link between
  them. Now Garrison has its own Tier 1 link and Redemption has a candidate pending Aaron's tiering
  call. **Jameson keeps the Whisky Watch.** Residual gap: Redemption only, and it is a decision
  rather than a supply problem. Open Aug 16–17, one day.
- **Outlet concentration — the standing structural gap, and it eased this run.** Whisky Advocate and
  Fred Minnick had been carrying nearly everything. Aug 17 added **two new working outlets**:
  `garrisonbros.com` (Tier 1 primary) and `shankennewsdaily.com` (pending tiering). **Brand and
  organizer primary sources are the cheapest way to break the two-outlet dependency** — they are
  Tier 1 by definition and need no tiering decision.

---

## WATCHING

- `whisky-advocate-august-auction-update-2026` — WA Aug 14, "Auction Update: Momentum Returns."
  **Recommend against for now.** `whisky-advocate-july-auction-update-2026` is in dedup and ran
  recently. A new month of data is technically a new development, but two auction updates inside a
  month reads as a recurring column rather than news, and it would spend a fourth WA link.
  Reconsider in September if a Tuesday comes up short. Article not opened.
- `breckenridge-peach-whiskey-2026` — WA Whisky Watch Aug 14. **36% ABV, $35, nationwide.**
  Second flavored whiskey from Breckenridge. **Recommend against:** 36% ABV flavored whiskey is
  thin material, and peach has now appeared three times — `whisky-advocate-peach-whisky-cocktails-2026`
  covered, Stranahan's peach superseded, Garrison's Hye Rye dropped. **Peach is spent for 2026.**
- `chip-tate-penumbra-mezcal-2026` — WA News Notes Aug 14 and FM Aug 13. Chip Tate, Balcones
  founder, first mezcal, for Foley Family Wines & Spirits. Espadín from the Sierra Juárez foothills,
  tahona-crushed, pit-roasted over encino wood, **$45, national.** **Not whiskey.** The Balcones
  lineage is the only whiskey hook. **Recommend against** unless a Friday wants a crossover item.
- `glenachulish-distillery-approval-2026` — WA News Notes Aug 14. Highland Council approved a new
  single malt distillery on Loch Leven near Ballachulish Bridge. Three pot stills, shop, tasting
  rooms, café. ~$8.1M, construction next year, **stills firing 2028.** Backed by the family behind
  Bar 1890 at Creag Mhor Lodge. **Two years out — fails the forward bar decisively.** Beat file.
- `whisky-advocate-vintage-coco-highball-2026` — WA Jun 2, Brittany Risher Englert. Vintage Coco by
  **Lynnette Marrero**, partner of Milly's Neighborhood Bar, Brooklyn. 1½ oz blended scotch, 2 oz
  coconut water, ½ oz pineapple, 2 oz Fever-Tree Sparkling Lime & Yuzu, shiso or mint. Marrero's own
  sensory, quotable under 20 words. **Third-ranked Easy Pour alternate** — oldest of the three and
  carries the coconut collision. Promote only if the other two die.
- `whisky-advocate-lost-irish-cucumber-2026` — Jun 23, Alberto Battaglini, PONY Cocktails + Kitchen,
  Santa Ynez CA. Sourced sensory, named creator. **First-ranked Easy Pour alternate, no collision.**
  Link: `https://whiskyadvocate.com/irish-whiskey-cucumber-cocktail-recipe`
- `whisky-advocate-coconut-manhattan-2026` — Jun 29, Christopher Lowder, Little Torch, Miami.
  Sourced sensory, named creator. Second-ranked alternate. Coconut collides.
  Link: `https://whiskyadvocate.com/tropical-manhattan-cocktail-recipe`
- `whisky-advocate-honey-cocktails-2026` — WA May 11. Named creators Dawid Smietana (Kilkea Castle)
  and Nina Dyrek (Sunda New Asian, Chicago), both with their own sensory. **Rejected for Aug 21:
  explicitly framed as spring cocktails.** Restage spring 2027.
- `whisky-advocate-top-whisky-bars-2026` — subdomain `whiskybars.whiskyadvocate.com` returns 200 but
  the list is client-rendered and empty to scripts. **Not a single venue can be named. Unusable.**
  **Tested Aug 13 — do not re-test before September.** Not re-tested this run, correctly.
- `jack-daniels-distillery-series-17-2026` — WA Aug 7: 69.2% ABV, $45/375ml, barrels laid down 2016
  on the top floor of Barrelhouse 1-13 on Coy Hill. **Blocked on distribution — distillery
  exclusive.** Robb Report has a taste test, a possible sensory leg **if** distribution ever clears.
- `wyoming-whiskey-state-of-the-union-2026` — two sources (WA Aug 7 and FM agree on $80/$79.99,
  49% ABV / 98 proof, 6 years, 68% corn / 20% wheat / 12% malted barley, first release since the
  brand returned to David DeFazio's ownership). **Still Wyoming-exclusive, fails the forward bar.**
- `branch-barrel-5yr-bourbon-2026` — WA Aug 7: 46%, $55, Colorado only. Fails the forward bar.
- `circle-city-whiskey-50-50-club-2026` — FM Aug 12. Retail expansion into Indiana, Wisconsin,
  Illinois; claims 100%+ YTD growth. **Trade news, not reader news. Recommend against** — same shape
  as Frey Ranch, dropped Aug 13. Unchanged.
- `discus-congressional-fly-in-2026` — **NEW, assessed and rejected.** FM Aug 14, Tier 1 subject.
  DISCUS invites members to a Congressional Fly-In in Washington DC on **Sept 24** to meet federal
  lawmakers. Chris Swonger, DISCUS president and CEO, quoted from a news release. **Recommend
  against: members-only industry advocacy with no consequence for a reader's shelf or weekend.**
  Fails the forward bar decisively — same shape as Circle City and Frey Ranch, both dropped.
  **Beat file, not staged.** Worth noting only if policy ever moves in a way that reaches shelf
  prices, which this does not.
- `punch-best-new-bartenders-2026` — weak. PUNCH Jun 2, only two of ten cocktails are whiskey.
- `the-1933-society-louisville-speakeasy-2026` — weak. WDRB is Tier 3, no opening date sourced.
- `johnnie-walker-blue-callum-turner-ambassador-2026` — beat file. No shelf or weekend consequence.
- `lexington-pumpkin-barrel-ale-2026` — WA News Notes Aug 14. Bourbon-barrel-aged pumpkin ale from
  Lexington Brewing & Distilling, part of Town Branch. $17/4-pack, this month through fall.
  **Beer, not whiskey.** Possible seasonal Friday crossover in October. Not staged.
- Unchanged and blocked: Oaklore · H. Obernauer · Sailor's Home · Pearse Lyons (drop) · Root Shoot
  (drop) · Stranahan's peach (superseded) · `uncle-nearest-receivership-weavers-out` (**still
  recommend hold**) · Kentucky Bourbon Festival · Heaven Hill year of wheat · Proof Cocktails
  Vancouver WA.

---

## URGENT SWEEP — no override

Window Aug 16–17. Three passes: a broad recall/litigation/investigation/death search, a second
targeted pass on recalls and industry obituaries, and the full Whisky Advocate RSS feed.

**No product recall, no safety issue, no litigation or investigation naming a partner brand or
venue, no death in the industry.** Nothing fires.

Both searches returned only already-logged material: A.M. Scott bankruptcy, the Uncle Nearest
receivership, the Canadian Crown Royal Reserve glass recall, the Fireball distributor suit, and the
craft-distillery closure trend. **All previously assessed as non-firing and none of it is new.**

**Two near-misses checked and correctly not fired this run:**
- A **Carriage House Creations recall of bourbon basting sauces** (undeclared soy and peanuts) is a
  **food product, not a whiskey**, and the FDA has already terminated the recall. Not our category
  and not live. Recording it so a future run does not re-fire it on the word "bourbon."
- A **2024 case of an illegal distiller causing three deaths** surfaced again. **Two years old and
  not the industry** — unlicensed production. Already outside the override bar.

**Considered and correctly not fired: the Copperworks Spokane fire item.** The Spokane Complex Fire
is a live disaster, but the override bar is a recall, a safety issue, litigation, or a death **in
the industry**. A distillery donating to relief is none of those. It runs in the normal Friday slot,
written quiet. Recording the reasoning so a future run does not re-litigate it.

Already logged and still non-firing: Uncle Nearest (Fawn Weaver suit and disputed Chapter 11; Farm
Credit Mid-America put at $108M — unadjudicated, not a WS partner, **hold**) · Red Boot Distillery v.
federal government · Crown Royal Reserve 12-year glass recall (Canadian) · A.M. Scott bankruptcy ·
True Story dual lawsuits · Sazerac v. RNDC · Fireball-maker suit · Bardstown's Feb 13 employment
suit · craft-distillery closures · `fss-kimbland-distillery-warning-2025`.

---

## HOSTS — load status

Fetch-to-disk with a browser user-agent then slice locally. **Proven again on every host used.**

- **`whiskyadvocate.com/call/blogs/rss/` — 200, ten dated items with titles and URLs. THE primary
  WA discovery path from now on.** See the RSS section above.
- **REGRESSION: `whiskyadvocate.com/news` and `/Tag/Cocktails` are now article-link-free.**
  `/news` 301s to `/News`, loads 200, renders zero article links. `/Tag/Cocktails` renders exactly
  one. Both grids are client-rendered. The Aug 14 note that the Tag index was merely "shallow" is
  **superseded — it is now effectively dead.** Do not spend fetches on either. Use RSS.
- WA article pages load 200 and their footers still carry three related-article links each.
- **`fredminnick.com`: article pages load 200 by direct URL; the site index renders no article links
  to scripts.** Sixth run in a row. **The Recent Articles rail on any FM article page remains the
  working substitute** and surfaced both Aug 14 stories this run.
- **NEW: FM's search endpoint `fredminnick.com/?s=<query>` 302s and is unusable to scripts.**
  Combined with the dead index, **FM articles are reachable only by direct URL or web search.**
  Slug guessing is expensive and failed nine times on Redemption this run — **web search first.**
- **NEW: `garrisonbros.com` — fully readable, and its structure matters.** Note the canonical host
  is `www.garrisonbros.com`; the bare host redirects. **Its event pages are the valuable part:**
  `/events/2026-cowboy-bourbon-release/` returned 200 with date, time, street address, price, proof
  and age in clean server-rendered text. **The homepage carries the full forward event slider**, and
  event URLs are only extractable from raw `href` attributes — the visible "MORE" links are
  script-driven, so a text-only scrape misses them. **`/event-directory/` exists and was not fetched
  — it is the obvious next discovery path for future Texas calendar items.**
  **WARNING: `garrisonbros.com/cowboy-bourbon/` is an UNDATED evergreen product page** carrying a
  prior release's 73.2% ABV and its own tasting notes. **Never mine it for a dated release.**
- **NEW: `shankennewsdaily.com` — loads 200 to scripts, clean server-rendered article text.**
  M. Shanken Communications, same publisher as Whisky Advocate. Carries original trade reporting
  with named executive interviews and Impact Databank figures. **Technically excellent source;
  tiering is unresolved — see the Redemption entry.**
- **NEW: `fredminnick.com` adjacent-post nav is a working discovery path.** With FM's index dead and
  `?s=` search 302ing, the `< Previous` / `Next >` links on any FM article page walk the publication
  timeline. **This is how the Aug 17 Brugal post was found** — nothing else would have surfaced it.
  Caveat: both nav links extract to the same URL under a naive regex, so **read the surrounding
  markup or just fetch both neighbours.** Cheaper and more reliable than slug guessing.
- `copperworksdistilling.com` product pages return 200 but are client-rendered; **no price readable.**
- `whiskybars.whiskyadvocate.com` returns 200; content client-rendered and empty. Not re-tested.
- `robbreport.com` loads via curl (307 to tollbit otherwise). `thespiritsbusiness.com`,
  `thebourbonflight.com`, `vinepair.com`, `journal-news.com`, `distillerytrail.com` all load.
- `eventbrite.com` loads and its JSON-LD is the reliable place to read event facts — **but its
  localisation dictionary contains every age band and status string, so never pattern-match "21+"
  out of raw Eventbrite HTML.** Its `AggregateOffer` is fee-inclusive with a placeholder 0.0 floor
  and is **never a stated ticket price.**
- Still 403 to scripts: `bevnet`, `prweb`, `themanual`. Breaking Bourbon *article* URLs load; its
  press-release index is age-gated.

---

## OPERATIONAL LESSONS (lessons 6–9 added Aug 17)

1. **Sweep the RSS feed before anything else on Whisky Advocate.** One fetch replaced two dead
   indexes and surfaced every new item on this board. Cost: one request. The two index fetches that
   preceded it returned nothing.
2. **A roundup article is one link-out, not four.** Formalised above as THE SHARED-LINK CONSTRAINT.
   This run staged three items out of one Whisky Watch before noticing; the constraint should be
   applied **at staging time**, not discovered at edition time. **When mining a roundup, immediately
   decide which single item will spend the link and mark the others "needs own link."**
3. **Search before guessing slugs.** Nine 404s were spent guessing Fred Minnick URLs for Redemption
   before establishing that no such article could be found. The Hard Truth and Chattanooga URLs both
   came free from a web search result. Slug guessing is only worth it when the title is known
   verbatim, and even then the Charred Garden Smash lesson (Aug 14) says titles do not predict slugs.
4. **A press release read through two outlets is still one source.** Both FM and WA carried the
   identical Jason Parker quote on Copperworks, and identical Bryan Smith copy on Hard Truth. What
   clears these items is the Tier 1 primary (the brand's own statement) plus one Tier 2 corroborating
   mention — not "two outlets ran it."
5. **The category-versus-bottle sensory trap keeps recurring and now has three instances.** Raasay's
   Hungarian oak, Macallan's coconut, and now WA's ice wine notes. In every case an outlet describes
   how a *material* behaves and it reads like a tasting note for the *whiskey*. **Standing test: ask
   whether the source tasted THIS bottle. If not, there is no sensory, however evocative the page.**
6. **When a roundup strands an item, go find it its own primary source.** The Aug 16 file queued
   Garrison and Redemption behind a single Whisky Watch link. The fix was not to wait — it was to
   fetch the brand's own dated pages. Garrison cleared outright in about four requests.
   **Standing rule: a stranded item's first move is the brand's or organizer's own dated release or
   event page, not another trade-press search.** Tier 1 by definition, and no tiering decision.
7. **An evergreen product page is not a release page — new instance of a familiar trap.**
   Garrison's `/cowboy-bourbon/` says 73.2% ABV; the 2026 event page says 141.0 proof (70.5%).
   Same brand, same product name, different bottling, and only one is dated. **Standing test: for a
   dated release, only a dated source describes it.** This is the sibling of the category-versus-
   bottle sensory trap in lesson 5 — both are "the page is about something adjacent to the thing."
8. **Do not promote an unvetted outlet to clear a blocked item.** Shanken News Daily is very
   probably fine and would unblock Redemption immediately. It is still not on the vetted list, and
   the temptation to reclassify it *because* it is convenient is exactly the pressure the tier list
   exists to resist. **Surface it as a decision; never resolve it silently.**
9. **A quiet source is not a broken source.** The WA RSS feed returned zero new items for the first
   time. The feed was healthy — WA simply did not publish Aug 15–17. **Check the transport before
   concluding a regression, and check the calendar before concluding a supply problem.**
10. Standing from Aug 14: **use `**bold**`** in `slack_send_message` — it takes standard markdown, so
   `*text*` renders italic. **Note the Aug 16 post did NOT apply this** despite the file claiming it
   was standing; applied today. Cosmetic, not surfaced in Notes.
7. Standing from Aug 14, still applied: **if a source does not state a person's pronouns, write
   around them or use they/them.** Applied to Grant McCracken, Alan Kennedy, Kevin O'Gorman, Jason
   Parker and Bryan Smith in the notes above — none of their pronouns are stated in any source read.

---

## BLOCKERS

- Write access: **resolved and stable.** Sixth consecutive successful push.
- Project-knowledge search unreachable, twenty-second run — source tiering comes from the inlined core
  in the skill's `references/verification-protocol.md`, read in full this run.
- `references/subject-beats.md` still wrong on beat 7, open since Jul 26. Stale-reference risk,
  not a live error.
- **The unreachable source directory now has a live cost, for the first time.** It has been a
  twenty-two-run annoyance handled by the inlined tier core. Today it **blocked a real item** —
  Shanken News Daily cannot be tiered without it, so Redemption waits on a human. **If this recurs,
  the fix worth proposing is a short vetted-outlet list committed to this branch** so tiering
  survives project-knowledge being down. Worth raising with Aaron if a second item ever stalls the
  same way; not worth a Notes bullet on its own today.

---

## DEDUP — closed to re-use

Story keys are lowercase-hyphenated `brand-product-year`. Prune at 30 days.

**Nothing published this run** — prep runs add no keys. Staged-but-unpublished keys are tracked in
their slot sections above, not here. Aug 17 added nothing; the dedup list is byte-identical to Aug 16.
**All four candidates assessed today were checked against it and none collided.**

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
`scotch-tariff-removal-2026-07-24` (4x) · `canada-50pct-tariff-aug-19-2026` (2x) ·
`bulleit-87-bourbon-rye-2026` (2x) · `old-forester-triple-char-117-2026` ·
`old-forester-presidents-choice-2026` · `makers-mark-cask-strength-26-01-2026` ·
`blood-oath-pact-12-2026` · `bushmills-ni-roi-tariff-split-2026` · `old-grand-dad-7yr-bib-2026` ·
`bardstown-victoria-pineapple-2026` · `watch-hill-proper-festival-aug-15-2026` ·
`larceny-vinepair-best-bourbons-2026` · `punch-whiskey-highball-2026`.
Cut: `barton-1792-xv-2026`.

**Pruning:** oldest entry Jul 24, **twenty-four days**. First prune **Aug 23** — six days out.
Expect `scotch-tariff-removal-2026-07-24` to fall first, followed by the Jul 24–27 cluster.
**The Wed Aug 19 run should pre-stage the prune list so Aug 23 is mechanical.**

**Spent link-outs — do not re-mine:**
_Aug 17: no new link-out was spent. Garrison moved OFF the Whisky Watch onto its own Tier 1 page,
which reduces pressure on the reserved WA link rather than adding to this list._
`whiskyadvocate.com/new-whisky-from-deanston-barrell-and-more` (Sagamore, Deanston, Sailor's Home,
Pearse Lyons) · `whiskyadvocate.com/macallan-glenfiddich-jack-daniels-and-more-new-whiskey`
(Macallan, Raasay, Old Overholt) · **`whiskyadvocate.com/jameson-single-pot-still-garrison-cowboy-and-more-new-whiskey`
— NOT yet spent, but reserve it for ONE item. Recommend Jameson.**

---

## COLLISION FLAGS

- **Whisky Advocate concentration — materially improved this run.** Aug 18 goes from three-of-four
  WA to two-of-four once Chattanooga replaces Macallan. Aug 21 goes from two-of-two to one-of-three
  with Copperworks in. **Both fixes came from Fred Minnick.** The dependency has simply moved: WA
  and FM are now carrying nearly everything. **A third outlet is the next structural need** — Robb
  Report holds Old Overholt and is the only other live one.
- **Single pot still, twice in four days.** Redbreast 12 sits in the Aug 21 Dubai chocolate list;
  Jameson Distiller's Batch is the Aug 25 lead and WA's write-up names Redbreast. **Spend the
  teaching moment on Jameson.** Do not define single pot still twice.
- **Bottled-in-bond, three times.** Redemption (Aug 25 candidate), Hard Truth (September), and
  `old-grand-dad-7yr-bib-2026` and `bib-tucker-8yr-bottled-in-bond-2026` already in dedup. The
  definition has been printed before. **Do not re-teach it; assume it and link.**
- **Peach is spent for 2026** — Breckenridge Peach rejected, `whisky-advocate-peach-whisky-cocktails-2026`
  covered, Stranahan's superseded, Garrison Hye Rye dropped.
- **Andrea Wilson twice in one week — spent.** Quoted Aug 11, named Aug 14. **Do not name her a
  third time before September** without a deliberate call.
- **Wild Turkey twice.** A 94-point Wild Turkey ran Aug 11; the Dubai chocolate list carries Wild
  Turkey Rare Breed rye, also 94 points, at $60. **Do not lead Aug 21 on Wild Turkey.**
- **Coconut, five ways now** — Macallan Harmony VI (cut resolves this), First West Explorer's
  "vanilla coconut ice cream" in WA's note, the Coconut Manhattan alternate, Vintage Coco, and as of
  Aug 17 Brugal's coconut-toasted-cask rum (rejected, not whiskey). **Never let coconut be the hook
  twice in one edition.** The frequency is a real editorial hazard, not a coincidence — coconut cask
  finishing is simply a live 2026 trend.
- **Bourbon-adjacent non-whiskey keeps surfacing** — Chip Tate's mezcal, Cuervo's mole-cask tequila,
  Brugal's rum, Lexington's pumpkin ale, and a bourbon *basting sauce* recall. **Five in two weeks.**
  All correctly rejected. Recording the pattern so the rejections stay fast and the urgent sweep does
  not fire on the word "bourbon" attached to a non-whiskey product.
- **Four straight Fridays of a WA cocktail** if any Easy Pour alternate runs Aug 21. **Copperworks
  arriving makes skipping the cocktail the cleaner fix.**
- **Sean Evans** bylines both the Stetson review (ran Aug 11) and the Buffalo Trace review (Aug 18).
  Aug 11's sensory ran attributed to Whisky Advocate rather than to Evans, so Aug 18 may name him.
- **Louisville** carried Friday venue items Jul 31 and Aug 14. A third would read as a pattern.

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
`whisky-advocate-honey-cocktails-2026` (spring framing — restage in spring, not permanent).

**Added Aug 16:** `breckenridge-peach-whiskey-2026` (36% ABV flavored, and peach is spent) ·
`glenachulish-distillery-approval-2026` (stills fire 2028, fails the forward bar) ·
`chip-tate-penumbra-mezcal-2026` (not whiskey).

**Added Aug 17:** `brugal-coleccion-visionaria-03-coconut-2026` — FM Aug 17. Dominican **rum**, not
whiskey. $69.99, select retailers nationwide, French oak casks toasted with Dominican coconuts, by
fifth-generation Maestra Ronera Jassil Villanueva Quintana; final release of a three-part series.
**Rejected on category, and it would also be the fifth coconut item.** Source also leans on
"ultra-premium" and "journey," both banned. · `discus-congressional-fly-in-2026` — Sept 24 DC
lobbying event, no reader consequence (full reasoning under WATCHING).

---

## NEXT RUN (Tue Aug 18 — The Shortlist, an EDITION day)

1. **Load whiskey-social-brand FIRST.** Not post-hoc. Then this file.
2. **Do not re-scout the four.** All four links were load-checked Aug 17 and returned full article
   bodies. Re-confirm they still load, then draft.
3. **Cut Macallan.** Surfaced Aug 14, Aug 16 and Aug 17 with no reply. **Default is cut, and three
   runs of silence is the answer.** Chattanooga takes the slot and fixes both the Collector skew and
   the outlet mix. Do not surface Macallan a fourth time — just cut it and stop mentioning it.
4. **Board of four:** Buffalo Trace (Collector, heavy sensory) · First West Explorer (Explorer,
   sensory, $50 nationwide — **the Try This Next lead and the only approachable price**) · Old
   Overholt 11-year (Collector, no sensory) · Chattanooga ice wine (Explorer, no sensory, **Fred
   Minnick link — that is the point of it**).
5. **Print WA's "contract-distilled at Bardstown Bourbon Co.," never the brand's "100% in-house."**
   Never mix the brand's notes (cherry, banana pudding, meringue) with WA's.
6. **Old Overholt has no independent sensory** — Robb Report got no sample. Say so or say nothing.
   The honest hook is that the proof went up and the age came down. Not an upgrade.
7. **Buffalo Trace's hook is that the two reviews disagree on the standout** — Evans names Kentucky
   River and Cove Spring, Breaking Bourbon calls the Watterson rye "downright exceptional."
   **Avoid vault/cellar/whale framing entirely on a $1,000 set.**
8. **Chattanooga has NO sensory. WA's "honey, lychee, stone fruits, bright citrus" describes ice
   wine the drink, not this whiskey. Do not print it.** The hook is the cask — ice wine is pressed
   from grapes frozen on the vine, and casks of it are rare in whiskey. That explainer is also the
   natural intimidation-pass definition. Print FM's eleven-states-plus-DC list, not WA's narrower
   "distillery and online."
9. **Coverage floor check:** this board is Explorer and Collector only, which is correct for a
   Tuesday. Do not force a Social Drinker or Venue Regular item into it — Friday carries those.
10. **Sean Evans** bylines both the Stetson review (ran Aug 11) and Buffalo Trace. Aug 11 attributed
   its sensory to Whisky Advocate rather than to Evans, **so Aug 18 may name him.**
11. **Do not re-teach bottled-in-bond** (three prior instances) and **do not define single pot still**
   — spend that on Jameson later. **"Hunt" once per edition maximum.**
12. UTMs: `?utm_source=whiskeysocial&utm_medium=pour&utm_campaign=shortlist-2026-08-18&utm_content=<beat>&utm_term=<persona>`.
   Beats available: `whats-dropping`, `try-this-next`, `allocation-watch`. **All lowercase.**

## THEN (Wed Aug 19 — prep)

1. **Sweep the WA RSS feed first**, window Aug 18–19. It returned zero new items Aug 15–17, so
   expect a backlog rather than a drought. Walk FM's adjacent-post nav from the Aug 17 Brugal post.
2. **Pre-stage the dedup prune list** for Aug 23 so the prune is mechanical, not a judgement call.
3. **Fri Aug 21 is three firm** — Detroit, Copperworks, Dubai chocolate. **Do not add a fourth
   unless it is strong**, and skipping the WA cocktail is the cleaner call now that Copperworks
   landed (it would otherwise be a fourth straight Friday of one).
4. **Aug 25 board:** Jameson firm on the Whisky Watch · Garrison firm on its own Tier 1 link ·
   Redemption still waiting on Aaron's Shanken tiering call. **Do not re-search Redemption** — the
   blocker is a decision, not supply. If Aaron has not replied by Aug 19, note it once more; if he
   has not replied by the Aug 25 run, hold the item rather than defaulting it in. **An unvetted
   outlet is not a silent default the way a recommended cut is.**
5. **Fetch `garrisonbros.com/event-directory/`** — untried, and the obvious source for Texas calendar
   items now that the host is proven.
6. Do not search Pair It or sub-$30 — both are Aaron's standing decisions. Do not re-test the WA bars
   subdomain before September. Do not re-fetch `/news` or `/Tag/Cocktails`.
7. Urgent sweep Aug 17–19.
