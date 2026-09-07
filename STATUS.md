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
- Foreign-qualification recognition is mentioned in the profile schema but has no dedicated
  route reference yet.
- Regional source coverage is generic Germany-wide; no local depth.

## Log

- **2026-09-07** — Repo created. Root scaffold: README, CLAUDE.md, MASTERPLAN, STATUS,
  LICENSE, .gitignore. Skill folders stubbed.
- **2026-09-07** — All eight skills written with their 13 reference files, one commit per
  skill. Structural checks pass: folder names match frontmatter, no broken reference
  paths, no skill cites a skill that does not exist, no orphan reference files.
- **2026-09-07** — study-os-thesis contributors credited in the README.
