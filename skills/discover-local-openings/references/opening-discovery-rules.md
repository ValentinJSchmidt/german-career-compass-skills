# Local Opening Discovery Rules

## The visibility problem — read this first

A large share of hiring in Germany never appears online. This is most true in exactly the
work this skill set is trying to take seriously: trades, care, logistics, cleaning,
hospitality, and small firms generally.

Those jobs travel by:

- **Aushang** — a notice in the window, at the counter, on the works noticeboard
- **Word of mouth** — the current staff know someone
- **Innung, Kammer, and guild lists** — the employer is findable, the vacancy is not
- **The local paper**, the Gemeindeblatt, the municipal board
- **Walk-in and the phone call** — "Do you need anyone?" is still how a lot of Handwerk hires
- **The Agentur** — via an advisor, sometimes without a public posting

A firm with eight employees and a full order book has no reason to write a job ad. The
owner hires the next person who asks.

**Consequences for this skill, all of them binding:**

1. Never report "no jobs found" when what happened is "no postings found online". Those are
   different findings and must be worded differently.
2. `offline_likely` is a first-class result with a real next step, not a dead end and not a
   lower-quality candidate.
3. A thin online result for a trade is a **visibility** result, not a market result. Say so.
4. Search axes with genuine offline-adjacent coverage — chambers, Innungen, registries,
   local press — rank ahead of aggregators, not behind them.
5. Always give the person a contact path they can use without a portal: a number to call, an
   address to visit, a chamber that holds the list.

## Source Axes

| Axis | Purpose | Example query shape |
|---|---|---|
| Agentur für Arbeit Jobbörse | The broadest coverage of non-office work in Germany | `Arbeitsagentur Jobbörse {beruf} {ort} Umkreis` |
| Employer pages | Verify the firm and find "Initiativbewerbung" routes | `{firma} {ort} Karriere Stellenangebote` |
| Chamber boards (IHK / HWK) | Ausbildung, Umschulung, and member firms | `HWK {region} Lehrstellenbörse {gewerk}` |
| Innung / guild directories | **Finds employers that never post at all** | `Innung {gewerk} {landkreis} Mitgliedsbetriebe` |
| Local press & municipal boards | Where small firms actually advertise | `Stellenangebote {landkreis} {beruf} Amtsblatt` |
| Company registry / Branchenverzeichnis | Enumerate firms inside the radius | `{gewerk} Betriebe {ort} Umkreis Verzeichnis` |
| Regional search | Catch what the big boards miss | `{beruf} {kleinstadt} Firma sucht Mitarbeiter` |
| Aggregators | One minority axis only | `{beruf} {ort} Stellenangebot` |

**Aggregators must not dominate.** LinkedIn, Xing, Indeed, StepStone and similar may supply
at most about a quarter of the raw pool, and every aggregator hit must be traced back to an
employer-owned or official source before it is returned. LinkedIn in particular has thin
coverage of trades, care, and small-firm hiring — treating it as the market is exactly the
mistake this file exists to prevent.

## Named starting points

Verified 2026-09-07; re-verify before relying on them.

- **Jobbörse der Bundesagentur** (`arbeitsagentur.de/jobsuche`) — the broadest coverage of
  non-office work in Germany, with a radius filter in fixed steps (10, 15, 25, 50, 100,
  200 km, or a custom radius). Those steps map directly onto rung 1 of the ladder in
  `../../find-career-options/references/self-correction-ladder.md`: widening from 25 to
  50 km is one concrete, checkable move.
- **Handwerkskammer Lehrstellenbörsen**, per chamber and region.
- **Lehrstellenatlas** — a directory of training-authorized trade firms. Lists *employers*
  rather than vacancies, which is precisely what is needed when the vacancy is never posted.
- **Innungssuche** — guild member directories, by trade and district. The single best axis
  for finding firms that hire without ever advertising.

## Geography

- Enumerate the towns, districts, and Landkreise actually inside the radius. Do not search
  only the nearest large city.
- Check reachability by the person's real transport. A 25 km commute by car is routine; by
  regional bus at 05:30 it may be impossible. Where the profile says no car on certain days,
  flag candidates that only work with one.
- Record distance and transport for every candidate. `find-career-options` filters on it.

## Verification

Return a candidate only when the run has verified:

- the employer exists, is currently operating, and is inside the radius
- the work plausibly matches the target occupation
- a reachable contact path — URL, phone, or address
- `visibility` and `opening_signal` are assigned on evidence, not assumed
- no-go conflicts are absent or flagged
- source URL and access date recorded

## Failure Modes

- **Fewer than six verified candidates:** widen by one axis or one step of radius — but only
  within what the profile allows — and record it in the coverage note.
- **The pool is mostly aggregator hits:** re-run with the chamber, Innung, registry, and
  local-press axes before returning anything.
- **Postings exist but none match the constraints:** that is a constraint result, not an
  empty market. Report it as such so the ladder can distinguish the two cases.
- **Nothing posted anywhere for a trade in a rural radius:** this is the expected case, not a
  failure. Return verified employers with `offline_likely`, give the contact paths, and say
  plainly that this kind of work is usually filled by a call rather than a portal.
- **Search unavailable:** stop. Do not name employers from memory.
