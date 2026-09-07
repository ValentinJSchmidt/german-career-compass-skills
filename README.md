# German Career Compass — Agent Skills

A portable set of [Agent Skills](https://code.claude.com/docs/en/skills) for career advice
in the German labour market.

The advice is meant to be **empathetic, AI-aware, and optimistic but realistic**. It treats
skilled trades, care, logistics, and public-sector work as first-class options rather than
fallbacks, and it takes the person's actual situation — location, hours, kids, income
floor, mobility, wanting to stay near friends — as hard constraints rather than
preferences.

These skills perform **live web discovery**. They do not ship a database of jobs,
occupations, or employers, and they will not guess from model memory when search is
unavailable.

## The skills

| Skill | What it does |
|---|---|
| `career-compass` | **Start here.** Interviews the person, then routes to the right track. |
| `build-career-profile` | Builds the six-dimension profile every other skill gates on. |
| `discover-career-paths` | Live discovery of fitting occupations and entry routes. |
| `discover-local-openings` | Live discovery of employers and openings inside the person's radius. |
| `find-career-options` | Enriches, verifies, ranks, and self-corrects into an honest option map. |
| `assess-ai-exposure` | What AI is actually changing in a role — at task level, with dated sources. |
| `plan-career-steps` | Concrete route: steps, timeline, cost, funding routes, income bridge. |
| `draft-career-outreach` | Application, cold message, or an internal development conversation. |

`career-compass` calls the others. You can also invoke any of them directly.

## Three tracks

After the interview, `career-compass` asks which of these you want — never assuming that
leaving is the answer:

- **(a) Grow where I am** — advance or become AI-ready in the current role or employer
- **(b) Move sideways** — same field, better fit for my constraints
- **(c) Change direction** — a new occupation, including trades and retraining routes

## Install

Copy the skill folders into a skills directory your agent reads:

```bash
# Available in every project
cp -r skills/* ~/.claude/skills/

# Or just this project
mkdir -p .claude/skills && cp -r skills/* .claude/skills/
```

Then start with: *"I want career advice"* or invoke `career-compass` directly.

Each skill is a self-contained folder (`SKILL.md` + optional `references/`) with portable
YAML frontmatter, so it works in any client that supports Agent Skills — Claude Code,
Codex, OpenCode, and similar.

## What these skills will not do

- Invent salaries, job openings, training places, or funding **eligibility**
- Tell you that you qualify for a benefit or programme — only where to confirm it
  (Agentur für Arbeit, Jobcenter, IHK, HWK)
- Give medical, legal, or financial determinations
- Advise leaving paid work before there is an income bridge
- Store your profile anywhere. Everything stays in the conversation.

## A caveat worth reading

A lot of hiring in Germany never appears online — especially in trades, care, and small
firms, where jobs travel by Aushang, guild and chamber contacts, word of mouth, the local
paper, or a phone call. Web search under-finds exactly those jobs.

So these skills mark options as `posted_online`, `employer_page_only`, or `offline_likely`,
and treat `offline_likely` as a real result with a real next step, not a dead end. **A thin
online result for a trade is a visibility limit, not proof that there is no work.** Take
any "nothing found" with a grain of salt and make the phone call.

## Credit

The architecture this repo is built on — the deep-interview profile gate, two-layer live
discovery, verified-evidence option maps, and honest thin-field reporting — was developed by
the team behind [study-os-thesis](https://github.com/Tue-StudyOS/study-os-thesis), which
does the same thing for finding a thesis.

That design is theirs. This repo points it at career advice.

**study-os-thesis contributors:**

- Domi
- Maximilian Schnitt ([@mxs01](https://github.com/mxs01))
- Valentin Schmidt ([@ValentinJSchmidt](https://github.com/ValentinJSchmidt))
- [@dxmme](https://github.com/dxmme)

Thanks to all of them — the good ideas in this repo mostly came from there.

## License

MIT
