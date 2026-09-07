---
name: find-career-options
description: Turn a complete career profile into a ranked, evidence-backed option map by delegating live discovery to discover-career-paths and discover-local-openings, then filtering hard on the person's constraints and self-correcting out loud when the field is thin. Use when someone asks which jobs, occupations, employers, or next steps actually fit their situation and location.
---

# Find Career Options

Produce an honest option map for one of three tracks. This skill carries no static list of
jobs or employers: it obtains temporary candidate tables from the `discover-*` skills, then
enriches, filters, ranks, and — when the field is thin — self-corrects visibly.

## Prerequisites

Require a complete six-dimension profile: Situation, Skills, Motivation, Constraints,
Direction, No-gos. If any dimension is missing or shallow, stop and invoke
`build-career-profile`. **Do not produce a shortlist on a partial profile.**

Requires live web/search access. If unavailable, say so and do not guess from model memory.

## Modes

| Mode | Question it answers | Discovery |
|---|---|---|
| `grow` | How do I get further where I am? | Skip path discovery. Use the current occupation; run `assess-ai-exposure` on it; use `discover-career-paths` only for internal-progression and Weiterbildung routes. |
| `sideways` | Same work, better fit for my life? | `discover-local-openings` for the current occupation and close neighbours across the radius. |
| `change` | What else could I do? | `discover-career-paths` first, then `discover-local-openings` for the top paths. |

`career-compass` sets the mode. If invoked directly without one, ask which it is.

## Workflow

1. Verify the six dimensions and read the constraints, noting which are **hard**.
2. Read `references/self-correction-ladder.md` before searching, so you know what you may
   and may not relax later.
3. Run discovery for the mode. Require the exact candidate-table schemas from
   `discover-career-paths` and `discover-local-openings`, including `visibility`,
   `opening_signal`, `distance_from_home`, `constraint_flags`, and `no_go_flags`.
4. **Filter on hard constraints before ranking.** Radius and transport, hours, fixed care
   windows, shift tolerance, physical limits, licences, work permit. A candidate that
   violates a hard constraint does not enter the ranking — it goes to the excluded list with
   the reason.
5. Apply no-gos. Do not silently drop borderline entries: keep them with a visible warning
   unless the conflict is confirmed.
6. Count what survives. **If fewer than four options survive, walk the ladder** in
   `references/self-correction-ladder.md` — one rung at a time, each rung stated out loud.
7. For the surviving options, enrich with live evidence: what the work actually involves,
   entry route and duration, what employers in this radius ask for, and the contact path.
8. Run `assess-ai-exposure` for the top options before delivering, so the map carries a
   task-level outlook rather than a guess.
9. Verify every URL immediately before output.
10. Rank by fit to the profile. Never by prestige, salary alone, or how modern an occupation
    sounds. Never down-rank an option for being `offline_likely`.
11. Produce the map using `references/option-map-schema.md`.

## Output

Follow `references/option-map-schema.md`. It specifies the required map-level caveats — the
visibility caveat and the search-coverage note — and the per-option fields.

If nothing survives, say so plainly, name the binding constraint and how much room would
open up if it moved, and stop. **A padded list is worse than an honest short one.**

## Rules

- Never invent openings, salaries, training places, funding eligibility, or entry
  requirements. Point to where the person confirms it: Agentur für Arbeit, Jobcenter, IHK,
  HWK, or the employer.
- Every URL in the output was opened during this run. Mark postings older than eight weeks
  as possibly filled and evidence older than three years as stale.
- **Never present "nothing found online" as "no work exists."** Carry `visibility` through
  to the person in plain words, and give an offline contact path wherever it applies.
- Never silently relax a constraint. The ladder is walked out loud or not at all.
- Do not rank by AI exposure, and do not sort into "safe" and "doomed". Exposure is reported
  per option, per task, as one input among several.
- Do not apply, register, or contact anyone on the person's behalf.
- Keep private data in the session. Keep personal wording out of every web query.

## Self-Check

Before delivering:

- all six dimensions were present
- both candidate tables were live-verified, with a search-coverage note
- hard constraints were applied as filters **before** ranking
- the raw path pool spanned ≥3 occupational families, or the coverage note says why not
- aggregators did not dominate the opening pool
- every `offline_likely` option carries a usable offline contact path
- if the field was thin, the ladder was walked visibly and the binding constraint named
- the visibility caveat is present
- every URL was verified in this run
