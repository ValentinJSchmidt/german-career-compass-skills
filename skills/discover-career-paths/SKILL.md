---
name: discover-career-paths
description: Build a temporary, profile-specific candidate set of occupations and entry routes in the German labour market from live web discovery, spanning trades, care, logistics, public sector, service, technical, and commercial work. Use when a career skill needs occupation candidates and entry routes without relying on a static list of jobs.
---

# Discover Career Paths

Find 8-14 verified occupation candidates and entry routes for a complete career profile.
This skill produces a **temporary candidate table only**. `find-career-options` does the
final ranking, constraint filtering, and the person-facing option map.

## Prerequisites

Require a complete six-dimension profile: Situation, Skills, Motivation, Constraints,
Direction, No-gos. If any dimension is missing or shallow, return to `build-career-profile`
before searching.

This skill requires live web/search access. If browsing or search is unavailable, stop and
say that path discovery cannot run without live sources. Do not guess occupations from
model memory — occupation names, entry requirements, and training durations change.

## Workflow

1. Convert the profile into search terms: German occupation names, **task words**, and
   sector words. Task words matter more than titles — "Kommissionierung", "Schichtübergabe",
   "Qualitätskontrolle" find better matches than "Lagerist".
2. Read `references/path-discovery-rules.md` before searching.
3. Run **at least four independent source axes** from that file before ranking anything.
4. Build a raw pool of 20-40 occupations across occupational families, applying the
   **blue-collar parity rule** in the rules file. Check the pool composition before you
   narrow it — ranking cannot repair a pool that never contained trades.
5. For each surviving candidate verify from an official or authoritative public source: that
   the occupation exists under that name, its realistic entry routes, typical entry
   requirements, and training duration.
6. Record which of the person's constraints each path may conflict with — shifts, physical
   demands, commute realities, hours, licences. Flag, do not silently drop.
7. Apply no-gos. Keep personal or sensitive wording out of every web query; convert no-gos
   into neutral filter categories locally.
8. Return 8-14 candidates where possible, never more than 20.

## Output

A Markdown table with these fields:

```yaml
entity_type: career_path
name: string                      # German occupation name; add English where useful
occupational_family: trades | care_health | logistics_production | public_sector | service_hospitality | technical_it | commercial_office
entry_route: ausbildung | verkuerzte_ausbildung | umschulung | teilqualifikation | weiterbildung | quereinstieg | studium | internal_progression
typical_entry_requirement: string # what is actually required, not what is nice to have
typical_duration: string          # with source, or unknown
task_overlap: string              # which of the person's existing tasks/skills carry over
source_axis: berufenet | training_database | chamber | task_similarity | sector_association | shortage_analysis | employer_evidence | regional_search
official_uri: string
evidence_summary: string
verified_at: YYYY-MM-DD
confidence: high | medium | low
constraint_flags: string          # profile constraints this path may conflict with
no_go_flags: string
```

Add a short **Search coverage** note naming which source axes were used, which were thin or
unavailable, and the occupational-family composition of the raw pool before narrowing.

## Evidence Rules

- Prefer official sources: `arbeitsagentur.de` and BERUFENET for occupation profiles and
  entry requirements, chamber sites (IHK, HWK) for training routes, ministry and
  sector-association pages for regulated occupations.
- Never invent occupations, entry requirements, training durations, salaries, or demand.
- Every included URI must have been opened or verified during this run.
- Mark evidence older than three years as stale — entry requirements and training rules change.
- Distinguish **what an occupation requires** from **what employers commonly ask for**. They
  differ, and the gap is often where a Quereinstieg exists.
- Do not confuse a shortage list with a guarantee of a job. Shortage means employers are
  looking, not that this person will be hired.
- Keep the person's private data in the active session only.
