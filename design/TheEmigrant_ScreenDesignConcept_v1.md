# The Emigrant — Screen Design Concept v1

**AgentHub Policy 2.5**

**In conception** under the Operationsfreigabe `AR261024_92`, until the owner releases it · 2026-10-24 · PM TheEmigrant,
for Belinda Baumgartner.

**What it is.** The conception the owner designs release 1 from in OpenDesign: the design system it asks for, every
screen, element and page with its content, behaviour, data and states, and how a delivery is checked, frozen and
handed to the build. **It does not set the look** — the look is the owner's, within the fixed elements below.

**What it derives from.** Concept v10.3, *What the first release's screens must show* (the brief — its must-shows stand
there and hold over this file where the two differ) and *Evidence model*; Technical Concept v1.1.2, *The frontend*,
*The snapshot*, *Testing*; Roadmap v1.0.1, *the design track*. **The prompts the owner pastes into OpenDesign** stand
in `TheEmigrant_OpenDesign_Prompts_v1.md` beside this file, derived from it.

---

## 1 · The tool, and what it hands back

**OpenDesign** (open-design.ai, Apache-2.0, local-first) renders HTML/CSS prototypes from prompts, against an active
**design-system package**: a folder with `manifest.json`, `DESIGN.md` (the brand contract, prose for agents) and
`tokens.css` (the compiled semantic tokens), optionally `tailwind-v4.css`, `design-tokens.json` and
`components.html`. Every render reads the active package. Export: ZIP of HTML, CSS and assets, standalone HTML, PDF.

**Why this fits the build.** The frontend is Nuxt UI 4 on Tailwind CSS v4. A package whose `tailwind-v4.css` and
`tokens.css` bind to Nuxt UI's semantic variables (`--ui-primary`, `--ui-bg`, `--ui-text`, `--ui-border`, …) and its
seven colour aliases (primary, secondary, success, info, warning, error, neutral) is adopted by the build almost as
is: the tokens become the app's `main.css` and `app.config.ts`, and the HTML screens are the reference the frontend
lane builds against. **The package is therefore the first delivery, and it is part of the handed-over design, not a
by-product.**

**How the work runs in OpenDesign** — the order the prompt pack follows:

1. **The design system** — the package `the-emigrant`, created from prompt DS-1, refined, then the component gallery
   (DS-2) rendered against it until every component and state stands.
2. **The screens**, one prompt each, in the order of §5. Each prompt is self-contained: it repeats the shared context
   block, so a screen can be re-rendered on its own.
3. **Every screen in two frames** — phone (390 × 844) and desktop (1440 × 900) — with **every state of §6 reachable
   through a prototype-only state switcher** on the page, so that one HTML file shows a screen whole.
4. **Finalize design package**, export ZIP — one per delivery.

## 2 · Fixed, and open

**Fixed** (Concept v10.3, *Ambition and constraints*; brief, *Principles*):

- **Type:** Playfair Display (display), DM Sans (text and UI), DM Mono (values, codes, dates in source panels) — self-hosted.
- **Icons:** Iconoir. **Images:** the owner's drone photography; Unsplash images, served from our own server.
- **Nothing loads from another domain** — no font CDN, no hotlinked image, no third-party script. In the prototypes,
  images are placeholders with a caption naming the intended photo; fonts are referenced as local files.
- **Phone first.** The 90-second first ranking is measured on a phone.
- **Light and dark tokens, screens in one base mode** *(`AR261024_94`)*: both modes are defined and AA-checked in
  `tokens.css` and shown in the gallery; the screens are designed once, in the base mode the owner chooses.
- **The old palette is a reference, not binding** *(`AR261024_95`)*: Meridian Deep's base — navy `#131C30`, midnight
  `#0A0F1E`, parchment `#F5EFE6`, cyan `#00C9B1` / `#007B6E`, gold `#E0B341`, coral `#FF6B47` — is given to DS-1 as a
  starting point, kept or left while refining.
- **One product, no per-step colours** (R1-2): the old Meridian Deep palette's four product tints
  (`the-emigrant-platform`, `app/assets/css/main.css`) are retired.
- **No winner, no crown, no confidence percentage, no paywall, nothing that earns money or announces it will.**
- **WCAG AA** on every text and control, full keyboard use, nothing carried by colour alone.
- **Built for about 190 countries**, of which a handful have a covered route.
- **English in release 1, German from release 2**: every layout survives text 35 % longer.

**Open** — the owner's, in the design system: palette, scale, spacing, radius, elevation, motion, illustration,
photography treatment, the wordmark's lockup, light or dark as the base.

## 3 · The design system — what the package must contain

**One package, `the-emigrant`**, built on Nuxt UI 4's component vocabulary: where Nuxt UI has the component
(`UButton`, `UInput`, `USelectMenu`, `UBadge`, `UCard`, `UModal`, `USlideover`, `UTabs`, `UAccordion`, `UTable`,
`UProgress`, `UToast`, `UAlert`, `UFileUpload`, `UCheckbox`, `URadioGroup`, `USwitch`), the design restyles it through
tokens rather than inventing a new one. Custom components are designed only where Nuxt UI has none — the domain
components below.

### 3.1 Foundations, in `DESIGN.md` and `tokens.css`

| Foundation | Must define |
|---|---|
| **Colour** | Seven semantic roles mapped to Nuxt UI's aliases, each a 50–950 ramp; surfaces (bg, elevated, muted, accented, inverted), text (default, muted, dimmed, highlighted, inverted), border (default, muted, accented); **the evidence and band roles of 3.3**; light and dark mode — every pair checked to AA |
| **Type** | A scale with roles — display, h1–h4, body, body-small, label, caption, value (mono), code — sizes for phone and desktop, line heights, the longest German word wrapping |
| **Space and layout** | A spacing scale; the grid at phone (4 columns, 16 px gutter), tablet (8), desktop (12, content max-width); the touch target, at least 44 × 44 px |
| **Shape and depth** | Radius scale; elevation levels with their use (card, sheet, modal, toast) |
| **Motion** | Durations and easings; what moves when the ranking updates; `prefers-reduced-motion` behaviour |
| **Focus** | One visible focus ring, AA against every surface |
| **Iconography** | Iconoir's size steps; which icon stands for which concept (evidence, source, unknown, stale, covered, export, import, delete, report) |
| **Voice** | Calm, precise, plain; never selling, never alarming; how unknown, stale and not-covered are said; the disclaimer line's tone |

### 3.2 Generic components — from Nuxt UI, restyled

Button (primary, secondary, ghost, destructive; sizes; loading; disabled) · text input, select, country select with
search over ~190 entries, number input with unit · checkbox, radio group, switch, segmented control · card · tag/badge ·
tabs · accordion · modal · bottom sheet (phone) / side panel (desktop) · toast · inline alert (info, warning, error) ·
progress (determinate, indeterminate) · file drop zone · empty state · skeleton · tooltip · link · table (compare) ·
pagination or virtual list.

### 3.3 Domain components — the brief's, designed new

Each one is designed with every variant and state listed, in the gallery (DS-2) **before** any screen uses it.

| Component | Variants and states |
|---|---|
| **Evidence badge** | E0 Unknown · E1 Sourced · E2 Audited (release 3 — designed now, unused) · E3 Verified; each with risk class Low · Medium · High; "flagged" (medium risk at E1 in Shortlist); the "verified through machine translation" mark on E3; readable without colour (label or glyph); compact (in a list) and full (in a panel) |
| **Source panel** | Source name and link, licence, as-of date, level, risk class; for E3 the verifier, role, verification date and why the source applies; the editorial label (firsthand, editorial, source-only) where a note exists; the machine-translation line and the quoted Spanish words; "report an error"; sheet on phone, side panel on desktop |
| **Unknown value** | The calm unknown, with its reason: no licensable source · below the minimum level for this purpose · contradictory sources · translations disagree; the shown-but-not-counted variant (a value below the minimum, shown with its level) |
| **Stale marker** | An as-of date past the claim type's freshness — on a value, in a panel |
| **Evidence band and coverage** | Strong · Partial · Thin, with the known share behind it (e.g. "8 of 11 criteria known") |
| **Score** | The 0–10 score on known criteria — **never a crown, rank medal or "best"**; absent where nothing is known |
| **Result band header** | Matches · Possible (needs checking) · Ruled out — with its count; collapsed and expanded |
| **Country row** | Flag-free or flag (owner's choice — flags are a design decision, and some households read them politically), name, score, evidence band, route label, and for Ruled out the criterion that rules it out; select-for-shortlist; long names |
| **Route label** | covered · partly covered · not covered — a quiet tag, never a band |
| **Criterion card** | Name, short meaning, pass/fail or scored; draggable and tap-to-move; in each of the three piles and in "not used"; the keyboard way to move it |
| **Pile** | Non-negotiable · Important · Nice to have · not used — empty, with cards, drop target active |
| **Condition list** | Per household member: each condition with its state — appears met · appears not met · unknown (with what would decide it) — its source, the requirement and the document |
| **Household member card** | Role (you, partner, child), nationalities (one or more), relationship, a child's age; incomplete and complete |
| **Disclaimer line** | The short line, with the way to the full terms; on route results, exports, Start |
| **Report-an-error dialog** | The claim named; the fixed reasons *(`AR261024_96`)* — the value is wrong · the source is out of date · the source link is broken · this is the wrong source for this claim — no free text; send; sent; failed (offline) |
| **Plan rail** | Shortlist · Route · Plan — current, done, not yet, **Plan marked "coming"** (a step, never a price); horizontal on desktop, compact on phone |
| **Next-action bar** | The one action that moves the plan on, always reachable — sticky at the bottom on phone, in the header region on desktop |
| **Provisional banner** | "Provisional — set your priorities" until the criteria sort has been touched |
| **Snapshot notice** | "Data updated — your results were recomputed", with what changed |

## 4 · The structure

### 4.1 The shell, on every screen

- **Header:** wordmark (to Start, or to the plan once one exists), the plan rail, a menu.
- **Menu:** Move Plan · Export · Import · How the evidence works · Terms of use · Privacy · Delete my data.
- **Next-action bar** — one action, always; the brief's "next action one tap away from any screen".
- **Footer** (desktop; in the menu on phone): the disclaimer link, the privacy promise in one line, the data version
  and date.

### 4.2 The screens and pages, and their addresses

**No household data in an address.** Criteria, weights, the household and the shortlist live in IndexedDB; an address
carries at most a country slug or a route slug, which tells nothing about the household. The country slug follows the
public pages' shape (`/countries/{slug}`, Technical Concept *The snapshot*), so that release 2's public page and the app's
country screen can share an address.

| # | Screen or page | Address | In the brief |
|---|---|---|---|
| 1 | Start | `/` | 1 |
| 1a | Terms of use — the acceptance step | `/` (step) | 1, as "accepted before first use" |
| 2 | Quick profile | `/start/profile` | 2 |
| 3 | Criteria sort | `/shortlist/criteria` | 3 |
| 4 | Results | `/shortlist` | 4 |
| 5 | Country | `/countries/{slug}` | 5 |
| 6 | Shortlist and compare | `/shortlist/compare` | 6 |
| 7 | Household | `/route/household` | 7 |
| 8 | Route result | `/route/{country-slug}` | 8 |
| 9 | Not covered | within 8, and from 4 and 5 | 9 |
| 10 | Move Plan | `/plan` | 10 |
| 11 | Export | `/plan` (sheet) | 10 |
| 12 | Import | `/plan` (sheet), and from Start | 1, 10 |
| 13 | Delete my data | `/plan` (dialog) | 10 |
| 14 | **Terms of use — full text** | `/terms` | implied by 1 and the disclaimer line |
| 15 | **Privacy — what stays on your device** | `/privacy` | implied by the privacy promise |
| 16 | **How the evidence works** | `/evidence` | **new** — what E0–E3, risk, the bands and unknown mean |
| 17 | **System states** — first load, data updated, offline, storage unavailable, not found | global | **new** |

Rows 14–17 go beyond the brief's ten, decided with `AR261024_93`.

### 4.3 The journey, and the 90 seconds

Start → (terms) → quick profile → **provisional ranking at once** → criteria sort, the ranking live beside or under
it → results → country → shortlist of up to three → compare → **Route: household asked here, not before** → route
result per country → Move Plan, export.

**At most 7 inputs before the first ranking**, quick profile and criteria sort together (UX standard). **Which inputs
is not decided:** it follows release 1's criteria set, which the owner decides from M1's `B00` survey. The design
works with the sample set in §7 and slots that take the final set without a redesign: a quick profile of 3 to 4
questions, each on one phone screen or all on one, and the criteria sort counting as one input per move.

## 5 · The screens

For each: its purpose, what it shows in order of importance on a phone, what it does, what it takes from the
engine, and its next action. **The states named are those of §6 that apply.**

### 1 · Start
- **Purpose:** what The Emigrant does, why it can be trusted, and the way in.
- **Shows:** one sentence on what it does · the privacy promise ("Your plan stays on this device. Nothing about you is
  sent anywhere.") · **the disclaimer beside it**, short, with the way to the full terms · the way in ("Find where you
  could go") · import an existing plan file · for a returning visitor: "Continue your plan", with the plan's last change.
- **Next action:** start, or continue.
- **States:** first use · terms not yet accepted · returning with a plan · first load of the data · offline.

### 1a · Terms of use — acceptance
- **Shows:** the terms' essentials in five lines (no responsibility for accuracy, completeness or currency; liability
  limited to the extent permitted by law; not legal advice; confirm with the authority or an adviser; your data stays
  on your device), the full terms one tap away, **accept** — nothing is usable before it.
- **States:** not accepted · accepted (the step does not show again) · terms changed since accepted (accept again).

### 2 · Quick profile
- **Purpose:** the fewest inputs the first ranking needs.
- **Shows:** 3–4 questions (sample: where you live now — for the cost level; languages you speak; climate you prefer;
  how much the cost of living matters), each with why it is asked, skippable where the engine has a default; progress.
- **Next action:** "Show my first ranking".
- **States:** empty · partly answered · complete.

### 3 · Criteria sort
- **Purpose:** sort the criteria into Non-negotiable, Important, Nice to have; the ranking updates after every move.
- **Shows:** the three piles and "not used" · criterion cards, pass/fail visibly different from scored · a live
  result summary (band counts, the top of Matches) — on phone a peek bar above the next-action bar, on desktop a
  column · the provisional banner until the first move.
- **Does:** drag, or tap a card and choose its pile; keyboard: focus a card, a key per pile; every move announced to
  screen readers ("Climate moved to Important. 12 matches.").
- **Next action:** "See results".
- **States:** provisional · sorted · a non-negotiable that leaves no Match (said calmly, with which one) · all unknown
  for one criterion (shown, with the reason).

### 4 · Results
- **Purpose:** the ranking, in three bands, for ~190 countries.
- **Shows:** band headers with counts — Matches, Possible (needs checking), Ruled out (collapsed) · per country: name,
  score on known criteria, evidence band and coverage, route label as a quiet tag, for Ruled out the criterion that
  rules it out · filters: covered routes only (off by default), region · search by name · add to shortlist (up to
  three; the fourth explains the limit) · the provisional banner while it applies.
- **Order** inside each band as the evidence model says (Matches by score then coverage; Possible by coverage then
  score; Ruled out by failed non-negotiables then score) — **the design shows no rank number**; the order speaks.
- **Next action:** "Compare your shortlist" once one country is chosen; before, "Choose up to three".
- **States:** provisional · empty Matches (with what to loosen) · filter leaves nothing · data updated · stale facts present.

### 5 · Country
- **Purpose:** everything we know, and don't, about one country, for this household.
- **Shows:** name, photo (placeholder), band and score for this household, evidence band, route label and the step to
  Route where covered · every criterion: value, unit, evidence badge, as-of date, risk class, one tap to the source
  panel · unknown values as unknown, with reason · editorial notes with their label · "report an error" on every claim
  · facts the household did not select, below, by category.
- **Next action:** add to shortlist / remove; "Check the route" where covered.
- **States:** unknown and partly known · stale · machine-translation mark (Costa Rica) · not in shortlist / in it /
  shortlist full · route not covered yet.

### 6 · Shortlist and compare
- **Shows:** up to three countries side by side, criteria as rows grouped by pile, unknowns visible in their cell, the
  evidence badge per cell, one tap to each source · on phone: two columns with a switch for the third, or swipe —
  the owner's choice, and the criterion names stay readable · remove a country.
- **Next action:** "Check whether all of you can live there" → Route.
- **States:** one country · two · three · a column all unknown · empty (nothing chosen yet).

### 7 · Household
- **Purpose:** asked only when Route first needs it.
- **Shows:** why we ask now · members: you, a partner, children — each with one or more nationalities, the
  relationship (married, registered partnership, durable partnership), a child's age · why each item is asked · that it
  stays on the device.
- **Next action:** "See the routes".
- **States:** empty · one member · partner without relationship set · dual nationality · three children · edit later.

### 8 · Route result
- **Purpose:** per country, the routes that appear to apply to this household.
- **Shows:** for each route: its name and regime, **"conditions that appear to apply" — never "eligible"** · per
  household member, the condition list (appears met · appears not met · unknown, with what would decide it) ·
  requirements, documents, authority, official source, last-verified date, coverage label · **the short disclaimer
  line** · the line that this is not an eligibility verdict and to confirm with the authority or an adviser · what is
  unknown and why · Austria: the return branch where a member is Austrian; Costa Rica: four routes side by side, the
  unmarried-partner note, the machine-translation mark.
- **Next action:** "Save to your plan" / "Back to your shortlist".
- **States:** one route appears to apply · several · none appears to apply (said as conditions, not a refusal) · partly
  unknown · partly covered · stale last-verified date · not covered (→ 9).

### 9 · Not covered
- **Shows:** that we do not cover this destination, or this household's case, yet — and why (no verified rules; the
  household's combination is outside the covered regimes) · never a failure, never a guess · what the household can do
  (the official authority, in general terms; the countries on its shortlist that are covered).
- **Variants:** destination not covered · household case not covered in a covered country · partly covered.

### 10 · Move Plan
- **Shows:** the plan rail (Shortlist, Route, **Plan — coming**) · the next action · the shortlist with its route
  status per country · the criteria in short · the data version the results were computed on, and what changed since ·
  export · import · "delete my data".
- **States:** empty · Shortlist done · Route done for one or more · data updated since last visit.

### 11 · Export (sheet)
- **Shows:** what the file holds · optional password (strength hint; that a lost password cannot be recovered) · **the
  short disclaimer line** · save.
- **States:** without password · with password · saved · failed.

### 12 · Import (sheet)
- **Shows:** choose or drop a file · password where the file is encrypted · **which copy is newer** — the file's and
  the device's, with dates and a one-line summary each — before anything is replaced · replace / keep.
- **States:** file chosen · password asked · wrong password · file cannot be imported (not a plan file, damaged, from
  a newer app version) · the file is older than the device's plan · imported.

### 13 · Delete my data (dialog)
- **Shows:** what is deleted (the plan, the cached data) · that it cannot be undone · export first · delete.
- **States:** confirm · deleted (back to first use).

### 14 · Terms of use — full text · 15 · Privacy
- Long-form reading pages: headings, anchors, the date of the version; Privacy says what the server sees in release
  1 (error reports: claim and reason only; server logs for 7 days) and what never leaves the device.

### 16 · How the evidence works
- E0–E3 in plain words, the three risk classes, the minimum level per purpose, the three bands, the evidence band,
  why unknown is never turned into a recommendation, the machine-translation exception. Reached from every evidence
  badge's panel ("What does this mean?").

### 17 · System states
- **First load** of the data (progress; under the 5-second phone budget it should rarely be seen) · **data updated**
  (notice, results recomputed, what changed) · **offline** (works from the cached data; reporting an error waits) ·
  **storage unavailable** (private mode or blocked IndexedDB: the app works, nothing is kept, export is the way to
  keep it) · **not found**.

## 6 · States — the matrix

The brief's states, and where each is designed. ● designed on that screen · — does not occur.

| State | 1 | 1a | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| empty | — | — | ● | ● | ● | — | ● | ● | — | — | ● | — | — | — |
| provisional | — | — | — | ● | ● | ● | ● | — | — | — | ● | — | — | — |
| unknown and partly known | — | — | — | ● | ● | ● | ● | — | ● | — | — | — | — | — |
| not covered | — | — | — | — | ● | ● | ● | — | ● | ● | ● | — | — | — |
| stale | — | — | — | — | ● | ● | ● | — | ● | — | ● | — | — | — |
| import fails / wrong password | ● | — | — | — | — | — | — | — | — | — | — | — | ● | — |
| import would replace a newer plan | — | — | — | — | — | — | — | — | — | — | — | — | ● | — |
| terms not yet accepted | ● | ● | — | — | — | — | — | — | — | — | — | — | — | — |
| first use, privacy promise and disclaimer | ● | ● | — | — | — | — | — | — | — | — | — | — | — | — |

Plus on every screen: **loading** (skeleton) and **offline**, and the shell's **data updated** notice.

## 7 · Content for the designs — real shapes, sample values

**The prototypes use real shapes, so that the design breaks where the product would.** Values are samples and say so
in the prototype ("sample data").

- **Countries:** the full list of ~190, so that the list, search and filters are tested at scale; the longest names —
  *Saint Vincent and the Grenadines*, *Democratic Republic of the Congo*, *Bosnia and Herzegovina*, *São Tomé and
  Príncipe*. Covered routes only for **Austria, Costa Rica, Germany**.
- **Sample criteria** (from research 2's list, pending the owner's criteria set): cost of living (price level against
  home), rule of law, tax burden, unemployment, internet speed, climate zone, official languages (pass/fail), EU member
  state (pass/fail), time zone distance, airports with international flights, natural-hazard risk, corruption perception.
- **Values with units and dates:** "Price level 71 (Austria = 100) · ICP 2021 · as of 2024-05-30"; an unknown with
  "no licensable source"; a stale value with an as-of date three years old.
- **Households:** Belinda-like (Austrian citizen, non-EU partner, unmarried, durable partnership) · married EU + non-EU,
  two children (4, 11) · an Austrian returning home · a Costa Rica family with one dual national.
- **Routes:** Austria — EU residence documentation for an EU citizen; the national permit for an unmarried non-EU
  partner; the return branch. Costa Rica — digital nomad (with the family threshold), rentista, pensionado,
  inversionista.

## 8 · Accessibility, and the measures the build will check

- AA contrast on every text, icon that carries meaning, focus ring and control state; evidence, band and route label
  each readable without colour.
- Full keyboard use, including the criteria sort; a logical focus order; a skip link; focus moved into and back out of
  every sheet and dialog.
- Touch targets ≥ 44 px; nothing that needs a hover.
- Live regions for the ranking's updates; the band counts announced.
- `prefers-reduced-motion` respected; no motion carries information.
- **The build checks these with axe and Playwright** (Technical Concept, *Testing*); the design should pass them on
  paper first.

## 9 · The deliveries, the freeze and the hand-over

| # | Delivery | Holds | Needed by |
|---|---|---|---|
| **D1** | **The design system** | The OpenDesign package `the-emigrant` — `manifest.json`, `DESIGN.md`, `tokens.css`, `tailwind-v4.css`, `design-tokens.json`, `components.html` (the gallery of §3, every component in every state, light and dark) | M2's screen bundles |
| **D2** | **The Shortlist screens** | Screens 1, 1a, 2–6, 10–17 — phone and desktop, every state | M2's screen bundles |
| **D3** | **The route screens** | Screens 7–9 — phone and desktop, every state | M3's screen bundles |

**The freeze check — the PM's, per delivery, reported as gaps before the owner freezes it:**

1. Every must-show of the brief for the screens in it, ticked against the HTML.
2. Every component of §3 used is the gallery's, in the gallery's states — no screen-local variant.
3. Every state of §6 for its screens reachable through the state switcher.
4. Phone and desktop frames for every screen.
5. No external request: fonts, images and scripts local (checked in the export's HTML).
6. The forbidden list absent: winner, crown, confidence percentage, paywall, price, anything announcing revenue.
7. The disclaimer line where the brief places it.
8. Contrast pairs from `tokens.css` at AA.

**The owner freezes** a delivery once its gaps are closed or accepted. **The hand-over is a ticket** that brings the
export into `docs/design/{delivery}/` on `rollup` and, for D1, adopts `tokens.css` and `tailwind-v4.css` as the app's
theme in `frontend/` — the first two in M2's `B00`, the third in M3's `B00`.

**After the freeze, a change is a new version of the delivery**, frozen again: a screen built against a design that
moved underneath it is the drift the freeze exists to prevent.

## 10 · Decided — put to the owner

| Question | Answer | Approval |
|---|---|---|
| Pages beyond the brief's ten | Terms, privacy, how the evidence works and the system states join D2 as screens 14–17 | `AR261024_93` |
| Light, dark, or both | Tokens for both, AA-checked; screens in the owner's base mode only | `AR261024_94` |
| The old Meridian Deep palette | A non-binding starting point in DS-1; the per-product tints stay retired | `AR261024_95` |
| Report an error's reasons | The four fixed reasons of §3.3, no free text; also B04's endpoint's set in M1 | `AR261024_96` |
| When the hand-over tickets are written | Each when its delivery is frozen, from the export's files | `AR261024_99` |
