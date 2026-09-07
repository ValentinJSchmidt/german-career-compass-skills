# Career Path Discovery Rules

## Source Axes

Use several, so the pool is not just whatever a search engine ranks first.

| Axis | Purpose | Example query shape |
|---|---|---|
| BERUFENET / occupation database | Authoritative occupation profiles, entry requirements, tasks | `BERUFENET {beruf} Zugangsvoraussetzungen Tätigkeiten` |
| Training databases | Real routes: Ausbildung, Umschulung, Weiterbildung | `mein NOW Weiterbildungssuche {beruf} Umschulung` |
| Chambers (IHK / HWK) | Trades and commercial routes, Teilqualifikation, Meister | `HWK {region} Umschulung Teilqualifikation {gewerk}` |
| Task similarity | Occupations sharing tasks with the current role | `Berufe mit {tätigkeit} {tätigkeit} Quereinstieg` |
| Sector associations | Occupations inside an industry, incl. small ones | `{branche} Verband Berufsbilder Einstieg` |
| Shortage analysis | Where employers are actually looking | `Engpassberufe {bundesland} Fachkräftemangel Analyse` |
| Employer evidence | What employers really require vs. the formal rule | `{beruf} Quereinsteiger willkommen Stellenbeschreibung` |
| Regional search | Occupations that exist locally, not nationally | `{beruf} {region} Betriebe Ausbildung` |

## Blue-Collar Parity

The point of this rule: search engines and general model priors both skew toward office and
tech work. Without a quota, a warehouse worker gets recommended "Datenanalyst" and nothing
they might actually want.

Occupational families:

`trades` · `care_health` · `logistics_production` · `public_sector` ·
`service_hospitality` · `technical_it` · `commercial_office`

Rules for the raw pool, applied **before** narrowing:

- The pool must contain candidates from **at least three** families.
- **No single family may exceed ~50%** of the raw pool.
- If the profile points strongly at one family, still surface adjacent families — a
  Handwerk route beside a technical one, a care route beside a service one.
- Do not add a token trade to satisfy the quota. If a family genuinely does not fit the
  profile or the constraints, say so in the Search coverage note instead of padding.

Then rank by **fit to the profile**. Never rank by prestige, expected salary, or how modern
an occupation sounds. For many profiles a Handwerk route is the better outcome on income and
security than the office route someone assumed they should want.

Do **not** rank on AI exposure at this stage, and do not treat trades as the safe answer.
Exposure is `assess-ai-exposure`'s job, it is assessed per task, and it does not resolve into
"trades safe, office exposed".

## Named starting points

Verified 2026-09-07. **Re-verify before relying on any of them** — this is exactly the kind
of detail that goes stale, and the example below shows why.

- **BERUFENET** (`web.arbeitsagentur.de/berufenet`) — occupation profiles, tasks, entry
  requirements. The authoritative source for "what does this job actually involve".
- **mein NOW** (`mein-now.de`) — the Bundesagentur's training and further-education search,
  carried jointly with all 16 Länder. It **replaced KURSNET**, which was shut down at the
  start of 2025 after its data was migrated. Anything still telling people to use KURSNET is
  out of date; treat that as the standing warning about programme names.
- **Handwerkskammer Lehrstellenbörsen** — run per chamber, regionally. Also
  **Lehrstellenradar** (`handwerk.de`) and the **Lehrstellenatlas**, a directory of
  training-authorized firms — useful because it lists *employers* rather than vacancies.
- **Innungssuche** — guild directories, per trade and per district.

## Entry Routes

Always look for the shortest honest route, not only the full qualification. For one
occupation there are often several, with very different demands on time and money:

- **Ausbildung** — full, usually 2-3.5 years, dual
- **Verkürzte Ausbildung** — shortened for prior experience or a previous qualification
- **Umschulung** — retraining, often 2 years, sometimes funded
- **Teilqualifikation** — modular, employable after each module, much shorter runway
- **Weiterbildung / Aufstiegsfortbildung** — Meister, Fachwirt, Techniker, built on existing
  qualification
- **Quereinstieg** — direct entry, learning on the job; common in care, logistics, sales,
  IT, and driving
- **Internal progression** — the same employer, more responsibility; the cheapest route and
  the one people forget
- **Studium** — only where it is genuinely required

For someone with a short runway or a hard income floor, **Teilqualifikation, Quereinstieg,
and internal progression matter more than the full qualification.** Surface them first.

## Two traps this search walks into

Both were observed in a real run. Check for them explicitly.

### Querying the current occupation returns routes *into* it

Someone who is already a Fachlagerist and wants out will, if you search their job title,
get pages full of Umschulungen **into** that job. The search engine cannot tell which
direction you meant.

In `change` mode, the current occupation name must **not** be the primary query term. Query
the tasks instead, and use explicit direction framings:

- `Berufe mit {tätigkeit} {tätigkeit} Quereinstieg` — task-led
- `Alternativen zu {beruf} Wechsel mit Erfahrung` — direction-led
- `von {beruf} zu` / `Umstieg aus {beruf}` — explicit direction
- `{gewerk} Quereinsteiger mit Lagererfahrung` — carries the experience across

### Official-looking domains that are not official

Searches for training and occupation facts return a large volume of commercial
training-provider marketing, some of it on domains chosen to look governmental.

**Official for these purposes:** `arbeitsagentur.de` (and its subdomains),
`mein-now.de`, chamber domains (`hwk-*.de`, `ihk*.de`, `khs-*.de`), ministry and
Landesbehörde domains, `anerkennung-in-deutschland.de`.

**Not official, regardless of how the domain reads:** any site whose name merely contains
"arbeitsamt", "umschulung", "weiterbildung", or similar, and every training provider,
comparison portal, and course marketplace.

Never source an occupation's entry requirements, duration, or demand from a provider or a
portal. Providers describe the course they are selling, not the occupation. Use them only to
learn that a course exists locally, then verify the facts against an official source.

## Verification

Return a candidate only when the run has verified:

- the occupation exists under that name, from an official source
- its realistic entry routes and what they actually require
- typical duration, or an explicit `unknown`
- a plausible overlap with the person's existing skills or tasks
- no-go conflicts are absent or flagged
- the evidence has a source URL and an access date

## Failure Modes

- **Fewer than six verified candidates:** broaden by one adjacent occupational family or one
  more source axis, and say in the coverage note that the field was thin.
- **The pool is one family:** that is a search failure, not a result. Re-run with family
  terms explicitly added before returning anything.
- **The profile's constraints exclude nearly everything:** do not force candidates. Return
  what survives and name the binding constraint so `find-career-options` can walk the ladder.
- **Search unavailable:** stop. Do not fall back on model memory for entry requirements or
  training durations.
