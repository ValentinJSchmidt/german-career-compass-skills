# Persona dry-run: warehouse worker near Reutlingen

**Date:** 2026-09-07 · **Track:** (c) change direction · **Live web:** yes

## Persona

Marco, 34, Fachlagerist near Reutlingen. Day is scanner-guided picking, shift handover,
stock corrections; trains new starters. Staplerschein.

- Two kids, **pickup 16:00 — hard**
- **No car Tuesday/Thursday evenings** (partner needs it)
- **Max ~30 km**, explicitly to stay near friends
- **Income floor ~2,100 € net**, max 3 months reduced
- No-gos: night shifts, relocation
- Worried scanner picking disappears

## What held

- **Profile gate.** Six dimensions present, discovery ran only after that.
- **Offline axis works, concretely.** Kreishandwerkerschaft Reutlingen supervises 30 Innungen
  covering ~3,700 firms with ~27,000 employees, and publishes a member-business listing.
  That is a directory of *employers*, not vacancies — exactly the input needed when the
  vacancy is never posted. `offline_likely` is a usable result here, not a hedge.
- **Chamber-call-first holds.** HWK Reutlingen runs Bildungsakademien in **Reutlingen and
  Tübingen — both inside the 30 km radius** — with a named Weiterbildung contact and a phone
  number. Search could *not* confirm Umschulung/Teilqualifikation specifics, so the honest
  output is "call and ask", which is what the skill already instructs.
- **Binding constraint was identified correctly, and it was not the radius.** Early shift
  (roughly 06:00–14:30) fits the 16:00 pickup fine. What cuts hardest in logistics is the
  **exclusion of late and night shifts** — so the ladder's diagnosis step mattered, and
  widening the radius would have been the wrong first move.
- **A real task-level nuance surfaced**, of the shape the rubric asks for: physically
  demanding tasks get automated *and* the remaining roles get more tightly clocked, against
  persistently high staff turnover. That is "the job changes shape and gets harder", not
  "the job disappears" — more useful to Marco than either headline.

## What broke — three defects, all fixed

### 1. Querying the current occupation returns routes *into* it

Searching Marco's own job title returned page after page of Umschulungen **into**
Lagerlogistik. He already has that job and wants out. The search engine cannot infer
direction.

**Fix:** `path-discovery-rules.md` now forbids the current occupation name as the primary
query term in `change` mode and gives explicit direction-framed and task-led query shapes.

### 2. Official-looking domains that are not official

The occupation search was dominated by commercial training-provider marketing, including a
domain built to read as governmental. An agent could easily have cited it as an official
source for entry requirements.

**Fix:** `path-discovery-rules.md` now lists what counts as official
(`arbeitsagentur.de`, `mein-now.de`, chamber and ministry domains) and states that a domain
merely *containing* an official-sounding word is not one. Provider pages may establish that
a course exists locally — never an occupation's requirements, duration, or demand.

### 3. Automation searches return a doom pipeline

This was the most serious one. Searching AI exposure for warehouse work returned almost
entirely vendor material, ad-funded trade press, and one training-provider blog whose fear
framing *is* its sales pitch. Followed naively, that pipeline produces exactly the
catastrophizing the skill exists to prevent — while looking like research.

**Fix:** `ai-exposure-rubric.md` gained a source-bias section: separate capability from
deployment, treat demos and press releases as neither, weight labour-market and chamber
sources above trade press and vendors, read provider warnings as marketing, ask what firm
size the evidence is actually about, and mark the assessment as weakly evidenced where only
vendor sources exist.

## Honest limits of this run

- Discovery axes and evidence quality were exercised against live sources. The **turn-by-turn
  interview was not** — persona answers were supplied up front rather than elicited over many
  turns, so the interview's pacing, its forced-choice fallback, and its stop rules remain
  untested.
- Track (a) "grow where I am" was not run at all.
- No output was produced end-to-end for a real person to react to.

The Phase 2 simulation harness is what would close this properly.
