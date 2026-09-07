# Status

Living document. Progress, decisions, blockers, dated log.

## Where we are

**Phase 1 — the skill set.** In progress.

| Skill | Status |
|---|---|
| `build-career-profile` | written |
| `career-compass` | written |
| `discover-career-paths` | written |
| `discover-local-openings` | written |
| `find-career-options` | written |
| `assess-ai-exposure` | written |
| `plan-career-steps` | written |
| `draft-career-outreach` | written |

All eight drafted; structural checks pass. Live persona dry-runs still outstanding —
until those have run, treat the set as unvalidated against real behaviour.

Phase 2 (validation harness) and Phase 3 (coverage) not started.

## Decisions

- **2026-09-07** — Architecture ported from `study-os-thesis` rather than designed fresh:
  the profile gate, two-layer live discovery, and honest thin-field reporting all transfer
  directly to career advice.
- **2026-09-07** — Germany-anchored vocabulary (Ausbildung, Umschulung, IHK/HWK,
  Bildungsgutschein), but the location and radius come from the person's profile. Not
  hard-coded to any region.
- **2026-09-07** — Three tracks including "grow where I am", so the skill set never assumes
  that leaving the current job is the answer.
- **2026-09-07** — Blue-collar parity is enforced in the *discovery pool*, not at ranking
  time, because ranking cannot fix a pool that never contained trades.
- **2026-09-07** — Digital-visibility bias treated as a first-class problem: much trade,
  care, and small-employer hiring is never posted online, so absence of postings is
  reported as a visibility limit rather than as absence of work.
- **2026-09-07** — AI exposure is assessed symmetrically and per task, never by collar.
  Blue-collar work is not treated as the safe answer (warehouse picking and routine
  inspection are highly automation-adjacent), and white-collar work is not treated as
  doomed. Software engineering is named as an explicitly uncertain case.
- **2026-09-07** — Advice stays inside the "plannable band": scenarios where AI takes over
  most work are excluded, with the reason stated rather than the worry dismissed — no
  career plan survives them, so they cannot discriminate between options.
- **2026-09-07** — Outreach picks its instrument from the option's visibility marker. For
  trades and small firms a phone script outranks a written Anschreiben, including a line
  for the "we're not hiring" answer, which is the usual one.

## Known gaps

- No automated tests yet — verification is structural checks plus live persona dry-runs.
- **Partial dry-run only.** The warehouse persona exercised the discovery axes and evidence
  quality against live sources (see `findings/2026-09-07-warehouse-persona-run.md`), but the
  turn-by-turn interview, its forced-choice fallback, and its stop rules are still untested,
  and track (a) has never been run. The Phase 2 simulation harness is what closes this.
- Foreign-qualification recognition is mentioned in the profile schema but has no dedicated
  route reference yet.
- Regional source coverage is generic Germany-wide; no local depth.

## Log

- **2026-09-07** — Repo created. Root scaffold: README, CLAUDE.md, MASTERPLAN, STATUS,
  LICENSE, .gitignore. Skill folders stubbed.
- **2026-09-07** — All eight skills written with their 13 reference files, one commit per
  skill. Structural checks pass: folder names match frontmatter, no broken reference
  paths, no skill cites a skill that does not exist, no orphan reference files.
- **2026-09-07** — study-os-thesis contributors credited in the README, resolved against
  the GitHub API rather than commit metadata (two git identities turned out to be one
  person, and another two were the same contributor under different names).
- **2026-09-07** — Live source verification. Caught a real staleness bug in our own files:
  `path-discovery-rules.md` pointed at KURSNET, which the Bundesagentur shut down at the
  start of 2025 after migrating its data to **mein NOW** (`mein-now.de`). Fixed, and the
  episode is now written into the file as the standing example of why programme names must
  be verified live rather than recalled.
  Verified as reachable and correctly described: BERUFENET, the Jobbörse (radius steps
  10/15/25/50/100/200 km, which rung 1 of the ladder now maps onto), mein NOW and its
  Fördernavigator, HWK Lehrstellenbörsen, Lehrstellenradar, Lehrstellenatlas, Innungssuche.
- **2026-09-07** — Warehouse persona dry-run (Reutlingen, track c) against live sources.
  Three defects found and fixed: querying the current occupation returns routes *into* it
  rather than out; official-looking commercial domains were dominating occupation results;
  and automation searches return a vendor and trade-press pipeline that manufactures exactly
  the doom framing the skill set forbids. Full write-up in `findings/`.
