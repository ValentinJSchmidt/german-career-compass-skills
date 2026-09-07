# CLAUDE.md

Guidelines for agents working in this repo.

## 1. Think Before Coding

- State assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so.

## 2. Simplicity First

Minimum content that does the job. No speculative features, no abstractions for
single-use text, no configurability nobody asked for.

## 3. Surgical Changes

Touch only what you must. Don't "improve" adjacent skills, wording, or formatting.
Match the existing voice. Every changed line should trace to the request.

## 4. Goal-Driven Execution

Turn tasks into verifiable goals. For skill changes, the verification is a **live dry-run**:
run a persona through `career-compass` and check the invariants below still hold. Structural
checks (folder name == frontmatter `name`, referenced `references/*.md` exist) run before
every push.

---

## 5. Skill authoring rules

```
skill-name/
├── SKILL.md
└── references/          # optional; rubrics and detail live here
```

- Frontmatter is portable YAML: `name` and `description` only.
- `name` must equal the folder name. Lowercase, digits, hyphens.
- `description` says both what the skill does **and** when to use it ("Use when …").
- `SKILL.md` states the core job, a short workflow, the output shape, and the evidence
  rules. Detail goes in `references/`, not in the body.
- No client-specific assumptions, no install instructions inside a skill, no project
  history.
- A skill must be runnable from its own files.

---

## 6. Advising invariants — do not weaken these

These carry the point of the repo. If a change makes any of them softer, it is wrong.

1. **Profile gate.** No discovery runs before all six dimensions are present: Situation,
   Skills, Motivation, Constraints, Direction, No-gos. A thin profile gets an honest
   "I can't personalize this yet", never a generic shortlist dressed up as tailored.
2. **Constraints are filters, not preferences.** Radius, hours, childcare windows,
   mobility, income floor, physical limits. Never silently relax one — name it and let the
   person choose.
3. **Blue-collar parity.** The candidate pool must span ≥3 occupational families and no
   family may exceed ~50% before ranking. Rank by fit, never by prestige or salary.
4. **Digital-visibility honesty.** Absence of online postings is never evidence of absence
   of jobs. `offline_likely` is a valid result with a real next step. Aggregators are a
   minority axis, never the backbone.
5. **Leaving is never the default.** Track (a) "grow where I am" must stay a real answer.
6. **Income bridge.** No plan proposes leaving paid work before the bridge exists.
7. **No invention.** Salaries, openings, training places, funding eligibility, and legal
   entitlements are never generated — only sourced, dated, and verified in-run, with a
   pointer to where the person confirms it.
8. **Task-level AI honesty.** Neither "your job is safe" nor "your job is gone". Jobs are
   bundles of tasks; say which tasks move and which stay, with dated evidence.
9. **Privacy.** Profiles stay in the conversation. Never write a filled profile into
   `references/`, `assets/`, or any repo file.

---

## 7. Workflow

- **[MASTERPLAN.md](MASTERPLAN.md)** — what we build and in what order. Edit only when the
  plan structurally changes.
- **[STATUS.md](STATUS.md)** — the living document: progress, decisions, dated log. Update
  it whenever you work on something.

We work without GitHub issues.

## 8. Commits

Frequent small commits with conventional-commit subjects (`feat:`, `fix:`, `docs:`,
`chore:`), imperative and lowercase. The body explains what and why, not line-by-line how.
Branch off `main` for anything non-trivial.
