# Masterplan

## What this is

A portable Agent Skills set that gives career advice for the German labour market:
empathetic, AI-aware, optimistic but realistic, and grounded in the advice-seeker's real
constraints.

## Why it is shaped this way

Ported from [study-os-thesis](https://github.com/Tue-StudyOS/study-os-thesis), which solved
the same problem shape for thesis discovery:

- interview until the profile is genuinely deep, and **gate** all discovery on it
- **two-layer discovery** — thin `discover-*` skills produce a temporary verified candidate
  table from live search; a `find-*` skill enriches, ranks, and filters
- **live evidence only** — no bundled database, no model memory, every URL verified in-run
- **honest thin-field reporting** — "not much fits" is a valid, useful answer

The career version adds four things the thesis version does not need: an empathetic
interview stance, task-level AI exposure, blue-collar parity in discovery, and a
self-correction ladder that never silently drops a constraint.

## Phase 1 — the skill set (v1)

| # | Skill | Role |
|---|---|---|
| 1 | `build-career-profile` | Six-dimension profile; the gate for everything else |
| 2 | `career-compass` | Router: framing, profile gate, track choice, drill-down gate |
| 3 | `discover-career-paths` | Live candidate table of occupations and entry routes |
| 4 | `discover-local-openings` | Live candidate table of employers/openings in radius |
| 5 | `find-career-options` | Enrich, verify, no-go filter, rank, self-correct |
| 6 | `assess-ai-exposure` | Task-level AI exposure and durable signal |
| 7 | `plan-career-steps` | Steps, timeline, cost, funding routes, income bridge |
| 8 | `draft-career-outreach` | Application, cold message, internal development talk |

Done when: all eight skills exist, structural checks pass, and two live persona dry-runs
(one career-change, one "grow where I am") hold the invariants in `CLAUDE.md` §6.

## Phase 2 — validation harness (not started)

Ports of the machinery study-os-thesis already has:

- structural test suite (`skills/tests/`) — frontmatter, references, naming
- persona simulation commands and rating rubrics
- packaging script + `dist/` release artifact
- CI workflow running the structural suite

## Phase 3 — coverage (not started)

- More personas across occupational families, education levels, and regions
- Recognition of foreign qualifications as a first-class route
- Regional depth beyond generic Germany-wide sources

## Non-goals

- A job board, a scraper, or a stored database of employers
- Anything that determines benefit eligibility, or gives medical, legal, or financial rulings
- A web UI or backend. These are skills, nothing more.
