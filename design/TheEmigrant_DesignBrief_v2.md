# The Emigrant — User Flow and Screen Brief

Oct 25, 2026 · @Belinda B.

Release 1 needs **17 screens**, built around one journey: find countries that fit you, check whether your whole household can legally live there, and save it as a plan. This brief walks that journey and lists, per screen, what has to be designed. It is a readable version of the Screen Design Concept v1; where the two differ, the concept holds.

## The journey at a glance

&#91;embedded content: the journey · 12 screens in 3 steps\]

The visitor reaches a first ranking (highlighted) within 90 seconds, and is asked about their household only when they check a route. A returning visitor goes straight from Start to their Move Plan.

## On every screen

Four parts frame every screen, so a visitor always knows where they are and what to do next.

| Part | What it holds | Phone | Desktop |
| --- | --- | --- | --- |
| **Header** | The wordmark (goes to Start, or to the plan once one exists), the **plan rail**, the menu button | top | top |
| **Plan rail** | The three steps: Shortlist · Route · Plan. Each shows current, done or not yet. **Plan is marked "coming"** — never a price | compact | full width in the header |
| **Menu** | Move Plan · Export · Import · How the evidence works · Terms of use · Privacy · Delete my data | slide-in | dropdown |
| **Next-action bar** | The **one** button that moves the visitor on (e.g. "See results"). Always reachable | sticky at the bottom | in the header area |
| **Footer** | The disclaimer line with its link to the full terms — always visible, phone included; the privacy promise in one line; the data version and its date | the disclaimer line at the bottom; the rest inside the menu | bottom of the page |

One rule for every address: **nothing about the household ever appears in a web address.** An address shows at most a country or route name, e.g. `/countries/austria`.

## Part 1 — Getting started and the Shortlist

The goal of this part: **a first country ranking within 90 seconds on a phone**, with at most 7 inputs before it appears.

### 1 · Start — `/`

What The Emigrant does, why it can be trusted, and the way in.

- One sentence on what it does
- The privacy promise: "Your plan stays on this device. No profile or plan data is sent to our server."
- The short disclaimer beside it, with a link to the full terms
- Main button: **"Find where you could go"**
- Secondary: import an existing plan file
- For a returning visitor: **"Continue your plan"**, with when it was last changed

**Next action:** start, or continue. **States:** first visit · terms not yet accepted · returning with a plan · data loading for the first time · offline.

### 1a · Terms of use — accept before first use

A step on Start, not a separate page. Nothing works before it is accepted.

- The terms in five short lines: no responsibility for accuracy, completeness or currency · liability limited as far as the law allows · not legal advice · confirm with the authority or an adviser · your data stays on your device
- Link to the full terms
- Button: **Accept**

**States:** not accepted · accepted (never shown again) · terms changed since you accepted (accept again).

### 2 · Quick profile — `/start/profile`

The fewest questions the first ranking needs: **3 to 4**, on one phone screen each or all on one.

- Each question with a short "why we ask"
- Skippable where a sensible default exists
- A progress indicator
- Sample questions until the criteria are decided: where you live now (for comparing prices) · languages you speak · climate you prefer · how much cost of living matters

**Next action:** "Show my first ranking". **States:** empty · partly answered · complete.

### 3 · Criteria sort — `/shortlist/criteria`

The visitor sorts what matters to them; **the ranking updates after every move**.

- Four piles: **Non-negotiable · Important · Nice to have · Not used**
- A card per criterion; yes/no criteria (e.g. "EU member") look visibly different from scored ones (e.g. "Price level")
- Moving a card: drag it, or tap it and choose a pile; on a keyboard, focus a card and press a key per pile
- A live result summary: how many countries per band, the top Matches. Phone: a small bar above the next-action bar. Desktop: a side column
- The banner "Provisional — set your priorities" until the first move
- Every move announced to screen readers, e.g. "Climate moved to Important. 12 matches."

**Next action:** "See results". **States:** provisional · sorted · a Non-negotiable that leaves no Match (said calmly, naming which one) · one criterion unknown for every country (shown, with the reason).

### 4 · Results — `/shortlist`

The ranking of about 190 countries, in **three bands**: **Matches · Possible (needs checking) · Ruled out** (collapsed by default).

- Each band's header with its count
- Per country: name, score on the known criteria, evidence band and coverage (e.g. "8 of 11 criteria known"), the route label as a quiet tag, and for Ruled out the criterion that rules it out
- Filters: covered routes only (off by default), region. Search by name
- Add to shortlist: up to three; a fourth explains the limit
- **No rank numbers, no "winner"** — the order speaks for itself

**Next action:** "Choose up to three", then "Compare your shortlist". **States:** provisional · no Matches (with what to loosen) · a filter leaves nothing · data updated · some facts out of date.

### 5 · Country — `/countries/{name}`

Everything we know, and don't, about one country, for this household.

- Name, photo (placeholder), band and score for this household, evidence band, route label, and the step to Route where it's covered
  - A small **locator map** showing where the country lies, the country highlighted (Natural Earth, public domain; served from our own site like every other fact)
- Every criterion: value, unit, evidence badge, as-of date, risk class; one tap opens the **source panel**
- Unknown values shown as unknown, with the reason
- "Report an error" on every fact
- Facts the household didn't select, further down, grouped by category

**Next action:** add to / remove from shortlist; "Check the route" where covered. **States:** partly unknown · out of date · machine-translation mark (Costa Rica) · not in shortlist / in it / shortlist full · route not covered yet.

### 6 · Shortlist and compare — `/shortlist/compare`

Up to three countries side by side.

- Criteria as rows, grouped by pile; unknowns visible in their cell; the evidence badge per cell, one tap to its source
- Phone: two columns with a switch for the third, or swipe — your choice as designer; criterion names stay readable
- Remove a country

**Next action:** "Check whether all of you can live there" → Route. **States:** one, two or three countries · a column all unknown · empty.

## Part 2 — Route

The question of this part: **could every member of this household legally live in this country?** It is only answered for **Austria, Costa Rica and Germany** in release 1; every other country is "not covered".

### 7 · Household — `/route/household`

Asked only when Route first needs it, never earlier.

- Why we ask now, and that it stays on this device
- Members: **you, a partner, children** — each with one or more nationalities
- The relationship to the partner: married · registered partnership · durable partnership
- A child's age
- A short "why we ask" next to each item

**Next action:** "See the routes". **States:** empty · one member · partner without a relationship chosen · dual nationality · three children · editing later.

### 8 · Route result — `/route/{country}`

Per country, the residence routes that **appear to apply** to this household. The wording matters: **never "eligible"**, always "conditions that appear to apply".

- Each route: its name and its legal framework
- Per household member, the **condition list**: each condition marked *appears met* · *appears not met* · *unknown* (with what would decide it)
- Requirements, documents, the authority, the official source, the last-verified date, the coverage label
- **The short disclaimer line**, and the line "this is not an eligibility verdict — confirm with the authority or an adviser"
- What is unknown, and why
- Country specifics: **Austria** — the return branch when a member is Austrian. **Costa Rica** — four routes side by side (digital nomad, rentista, pensionado, inversionista), the note for unmarried partners, the machine-translation mark

**Next action:** "Save to your plan" / "Back to your shortlist". **States:** one route appears to apply · several · none (said as conditions, never as a refusal) · partly unknown · partly covered · last-verified date out of date · not covered (→ screen 9).

### 9 · Not covered — inside screen 8, and linked from 4 and 5

Says that we don't cover this yet — **never as a failure, never with a guess**.

- Why: no verified rules for this country, or this household's situation is outside what we cover
- What the household can do: contact the official authority (in general terms); which countries on their shortlist **are** covered

**Three variants:** destination not covered · the household's case not covered in a covered country · partly covered.

## Part 3 — The Move Plan and your data

Everything the visitor builds lives **only in their browser**. These screens let them see it, take it with them, bring it back, or delete it.

### 10 · Move Plan — `/plan`

- The plan rail (Shortlist, Route, **Plan — coming**) and the next action
- The shortlist, with the route status per country
- The chosen criteria, in short
- Which data version the results were calculated on, and what changed since
- Buttons: Export · Import · Delete my data

**States:** empty · Shortlist done · Route done for one or more countries · data updated since the last visit.

### 11 · Export — a sheet on the Move Plan

Saves the plan as a file the visitor keeps.

- What the file contains
- **Optional password**, with a strength hint and the warning that a lost password cannot be recovered
- The short disclaimer line
- Button: Save

**States:** without password · with password · saved · failed.

### 12 · Import — a sheet on the Move Plan, also reachable from Start

- Choose or drop a file
- The password, if the file has one
- **Before anything is replaced:** which copy is newer — the file's or the one on this device — each with its date and a one-line summary
- Buttons: Replace · Keep mine

**States:** file chosen · password asked · wrong password · file can't be imported (not a plan file, damaged, or from a newer app version) · the file is older than this device's plan · imported.

### 13 · Delete my data — a dialog

- What gets deleted: the plan and the stored data
- That it **cannot be undone**
- A suggestion to export first
- Button: Delete

**States:** confirm · deleted (back to the first-visit Start).

## Part 4 — Reading pages and system states

| # | Page | Address | What it holds |
| --- | --- | --- | --- |
| 14 | **Terms of use — full text** | `/terms` | Long-form reading: headings, jump links, the version date |
| 15 | **Privacy** | `/privacy` | What stays on the device; what our server sees in release 1 (error reports: only the fact and the reason; server logs kept 7 days) |
| 16 | **How the evidence works** | `/evidence` | In plain words: the evidence levels E0–E3, the three risk classes, the minimum level per purpose, the three bands, the evidence band, why unknown is never turned into a recommendation, the machine-translation exception. Reached from every evidence badge ("What does this mean?") |
| 17 | **System states** | everywhere | See below |

**The five system states (17):**

- **First load** — the data is downloading; a progress bar. Should rarely be seen (under 5 seconds on a phone)
- **Data updated** — a notice: "Data updated — your results were recalculated", with what changed
- **Offline** — the app works from the stored data; reporting an error waits until back online
- **Storage unavailable** — private browsing or blocked storage: the app works, but nothing is kept; export is the way to keep it
- **Not found** — a page that doesn't exist

## All forms and inputs

Release 1 has **nine places where the visitor types or chooses something**. None of it ever leaves the device, except the error report, which carries only the fact and one fixed reason.

| Where | Inputs | Kind of control | Notes |
| --- | --- | --- | --- |
| 1a Terms | Accept | button | Nothing works before it |
| 2 Quick profile | 3–4 questions (sample: current country, languages, climate, cost importance) | country select with search over \~190 countries, multi-select, radio group, segmented control | Each with "why we ask"; skippable where a default exists |
| 3 Criteria sort | Move each criterion into a pile | drag-and-drop cards, tap-to-move menu, keyboard keys | Counts as one input per move toward the 7-input limit |
| 4 Results | Region filter, "covered routes only" switch, search by name, add to shortlist | select, switch, search field, toggle button | Shortlist max 3 |
| 7 Household | Members (you, partner, children), nationalities per member, relationship, child's age | repeatable member cards, country multi-select, radio group, number input | Asked only when Route needs it |
| 11 Export | Optional password | password field with strength hint | Lost password cannot be recovered |
| 12 Import | Plan file, password if encrypted, replace or keep | file drop zone, password field, two buttons | Shows which copy is newer first |
| 13 Delete | Confirm | destructive button | Cannot be undone |
| Report an error (from any fact) | One of four fixed reasons | radio group, send button | The value is wrong · the source is out of date · the source link is broken · this is the wrong source. **No free text** |

## The components to design

**Design every component, in all its states, in the component gallery before any screen uses it.** Two groups.

### Basics — from Nuxt UI, restyled with your colors and type

The build uses Nuxt UI, so these exist already; you only give them the look.

Button (primary, secondary, ghost, destructive; sizes; loading; disabled) · text input · select · country select with search · number input with unit · checkbox · radio group · switch · segmented control · card · tag/badge · tabs · accordion · modal · bottom sheet (phone) / side panel (desktop) · toast · inline alert (info, warning, error) · progress bar · file drop zone · empty state · loading skeleton · tooltip · link · comparison table · long list.

### Designed new — specific to The Emigrant

| Component | What it shows | Variants and states |
| --- | --- | --- |
| **Evidence badge** | How well a fact is backed | E0 Unknown · E1 Sourced · E2 Audited (designed now, used later) · E3 Verified; each with risk Low/Medium/High; "flagged"; the machine-translation mark; readable without color; compact and full |
| **Source panel** | Where a fact comes from | Source name and link, license, as-of date, level, risk; for E3 who verified it, when and why; "report an error"; sheet on phone, side panel on desktop |
| **Unknown value** | A missing fact, calmly | With its reason: no usable source · below the minimum level · sources contradict · translations disagree; plus "shown but not counted" |
| **Out-of-date marker** | A fact older than it should be | On a value, and in a panel |
| **Evidence band** | How much is known | Strong · Partial · Thin, with the share ("8 of 11 known") |
| **Score** | 0–10 on the known criteria | Never a crown, medal or "best"; absent when nothing is known |
| **Band header** | Matches · Possible · Ruled out | With count; collapsed and expanded |
| **Country row** | One country in the results | Name, score, evidence band, route label, the ruling-out criterion; add to shortlist; very long names. Flags or no flags: your call |
| **Route label** | Whether we cover routes | covered · partly covered · not covered; a quiet tag, never a band |
| **Criterion card** | One criterion to sort | Name, short meaning, yes/no or scored; draggable; in each pile; keyboard moving |
| **Pile** | A priority group | Non-negotiable · Important · Nice to have · Not used; empty, filled, drop target active |
| **Condition list** | One route's conditions per person | appears met · appears not met · unknown (with what would decide it); source, requirement, document |
| **Household member card** | One person | Role, nationalities, relationship, child's age; incomplete and complete |
| **Disclaimer line** | The short legal line | With the link to the full terms; visible on every screen, phone included — beside the privacy promise on Start, and on route results and export |
| **Report-an-error dialog** | Telling us a fact is wrong | The four reasons; send · sent · failed (offline) |
| **Plan rail** | The three steps | current, done, not yet; "Plan — coming"; desktop and phone |
| **Next-action bar** | The one next step | Sticky bottom on phone, header area on desktop |
| **Provisional banner** | "Provisional — set your priorities" | Until the criteria sort is touched |
| **Data-updated notice** | "Data updated — your results were recalculated" | With what changed |
| **Locator map** | Where a country lies | One country highlighted on a simple world or region outline; small countries and islands still findable; a text alternative naming the region; phone and desktop |

## States, and the rules that hold everywhere

**Every screen in two frames — phone (390 × 844) and desktop (1440 × 900) — with every state reachable through a state switcher on the prototype page.** Besides each screen's own states listed above, every screen also shows **loading** (a skeleton), **offline**, and the **data-updated** notice.

**Fixed:**

- **Fonts:** Archivo — condensed for titles, wide for labels — and Martian Mono (values, codes, dates in source panels), served from our own site. They replace Playfair Display, DM Sans and DM Mono
- **Icons:** Iconoir only. **Photos:** your drone photos and Unsplash, served from our own site; placeholders with a caption in the prototypes
- **Nothing loads from another website** — no font service, no linked images, no outside scripts
- **Phone first**; touch targets at least 44 × 44 px; nothing that needs a mouse hover
- **Light and dark colors both defined and checked; screens designed in one mode**, the one you choose
- **Contrast WCAG AA** on all text and controls; **nothing explained by color alone**; full keyboard use; reduced motion respected
- **No winner, crown, confidence percentage, paywall, price** or anything that sells
- **About 190 countries** in every list; layouts survive **text 35 % longer** (German comes in release 2)
- The voice: calm, precise, plain — never selling, never alarming

**Visual direction — chosen (2026-10-25):** Transit Papers, "P v2 · Blue + citrus". It settles what was open here: palette, type scale, spacing, corner radius, shadows, motion, illustration, photo treatment, the wordmark, light or dark as the base, flags or no flags. Its values stand in the design system package (D1).

## The criteria, and where this comes from

**The criteria are decided (2026-10-25).** What it means for the Criteria sort (screen 3):

- Each card shows **topic · measure**, e.g. "Jobs · Unemployment rate", "Healthcare · Life expectancy", "Safety · Political stability and absence of violence", "Education · School enrollment", with a one-line explanation of what it shows **and its limit**.
- Below the piles, one line **"Not available yet"**, not selectable, with the reason "no source we may legally use yet": Visa / residency ease · Taxes · Crypto friendly · Walkability / transport · Culture fit · Expat community · Food quality. Same look as "Not known yet + reason". Taxes and Expat community may still come back.
- "Language · Official languages" is a match / no match against the languages the household speaks, so **the Quick profile asks which languages they speak**.

**Criteria for the prototypes:** Cost · Price level, Rule of law, Jobs · Unemployment rate, Internet · Speed tests, Climate zone, Language · Official languages (match / no match), EU member (yes / no), Time zone distance, Flights · Airports, Natural-hazard risk, Corruption, Safety · Political stability and absence of violence, Healthcare · Life expectancy, Education · School enrollment.

**Sample households:** an Austrian with a non-EU partner, unmarried, in a durable partnership · a married EU + non-EU couple with two children (4 and 11) · an Austrian returning home · a Costa Rica family with one dual national. Use the longest country names too: *Saint Vincent and the Grenadines*, *Democratic Republic of the Congo*, *Bosnia and Herzegovina*, *São Tomé and Príncipe*.

**Deliveries:** D1 the design system and component gallery · D2 the Shortlist screens (1, 1a, 2–6, 10–17) · D3 the Route screens (7–9). I check each against this brief before you freeze it.

**Source:** the Screen Design Concept v1 (`4_concept/design/TheEmigrant_ScreenDesignConcept_v1.md` in the PM repository), which follows Concept v10.3 and the Technical Concept v1.1.2. The OpenDesign prompts you paste are in `TheEmigrant_OpenDesign_Prompts_v1.md` beside it.
