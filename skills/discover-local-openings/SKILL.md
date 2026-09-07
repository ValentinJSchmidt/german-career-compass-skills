---
name: discover-local-openings
description: Build a temporary, profile-specific candidate set of employers and job openings inside a person's commuting radius from live web discovery, using sources with real blue-collar coverage rather than job aggregators, and marking how visible each option is online. Use when a career skill needs local employer or opening candidates for a given occupation and location.
---

# Discover Local Openings

Find 8-15 verified employers or openings inside the person's stated radius for one or more
target occupations. This skill produces a **temporary candidate table only**;
`find-career-options` ranks, filters, and writes the person-facing map.

## Prerequisites

Require a complete six-dimension profile, and at least one target occupation (usually from
`discover-career-paths`, or the person's current occupation for the `grow` and `sideways`
tracks).

The **home location and acceptable radius are hard inputs**. Do not start without them.

This skill requires live web/search access. If browsing or search is unavailable, stop and
say that local discovery cannot run. Do not name employers from model memory — they close,
move, and get bought.

## Workflow

1. Read `references/opening-discovery-rules.md` before searching. The visibility rules there
   are the point of this skill, not a caveat on it.
2. Establish the geographic frame: home town or postcode, the radius in km or minutes, and
   the transport that has to work. Enumerate the towns and districts actually inside that
   radius — searching only the nearest big city misses most small employers.
3. Run **at least four independent source axes**, and the aggregator axis may not be one of
   the first four.
4. Build a raw pool of 20-40 employers or openings.
5. For every candidate, determine and record `visibility`:
   - `posted_online` — a current advertised opening was found and opened
   - `employer_page_only` — the employer is verified and plausibly hiring, but the only
     signal is their own site or a general "Initiativbewerbung welcome" page
   - `offline_likely` — the employer is verified and in scope, but this kind of role in this
     kind of firm is typically filled without an online posting
6. Determine `opening_signal` separately from `visibility`: an employer with no posting is
   still a candidate.
7. Record the distance from home and whether it is reachable by the person's actual
   transport — a 25 km commute is different by car and by bus.
8. Record a **contact path** for every candidate, including offline paths: phone number,
   address for a walk-in, the Innung or chamber that holds the member list.
9. Apply no-gos and constraint flags. Never put personal wording into a query.
10. Return 8-15 candidates where possible, never more than 20.

## Output

A Markdown table with these fields:

```yaml
entity_type: employer | opening
name: string
location: string
distance_from_home: string        # km or minutes, and by which transport
sector: string
size: micro | small | medium | large | unknown
target_occupation: string
visibility: posted_online | employer_page_only | offline_likely
opening_signal: explicit_opening | hiring_page_only | no_posting_found
official_uri: string
contact_path: string              # incl. offline: phone, address, Innung, chamber
source_axis: agentur_jobboerse | employer_page | chamber_boerse | innung_directory | local_press | company_registry | regional_search | aggregator
evidence_summary: string
verified_at: YYYY-MM-DD
confidence: high | medium | low
constraint_flags: string
no_go_flags: string
```

Add a **Search coverage** note naming: which axes were used, which were thin or unavailable,
what share of the pool came from aggregators, and how many candidates are `offline_likely`.

## Evidence Rules

- **Absence of an online posting is not evidence of absence of a job.** `no_posting_found`
  and `offline_likely` are valid, useful results — never a failure, and never a reason to
  down-rank an otherwise good candidate.
- Prefer employer-owned pages and official boards. Aggregator hits are hints that must be
  traced back to an employer-owned or official source before being returned.
- Never invent employers, openings, contact names, phone numbers, or addresses.
- Every included URI must have been opened or verified during this run.
- Mark postings older than eight weeks as possibly filled.
- Do not apply, register accounts, submit forms, or contact anyone. Discovery only.
- Keep the person's private data in the active session only.
