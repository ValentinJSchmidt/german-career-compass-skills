# Status

Living document. Progress, decisions, blockers, dated log.

## Where we are

**Phase 1 — the skill set.** In progress.

| Skill | Status |
|---|---|
| `build-career-profile` | not started |
| `career-compass` | not started |
| `discover-career-paths` | not started |
| `discover-local-openings` | not started |
| `find-career-options` | not started |
| `assess-ai-exposure` | not started |
| `plan-career-steps` | not started |
| `draft-career-outreach` | not started |

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

## Known gaps

- No automated tests yet — verification is structural checks plus live persona dry-runs.
- Foreign-qualification recognition is mentioned in the profile schema but has no dedicated
  route reference yet.
- Regional source coverage is generic Germany-wide; no local depth.

## Log

- **2026-09-07** — Repo created. Root scaffold: README, CLAUDE.md, MASTERPLAN, STATUS,
  LICENSE, .gitignore. Skill folders stubbed.
