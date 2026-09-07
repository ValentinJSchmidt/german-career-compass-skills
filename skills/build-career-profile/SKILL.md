---
name: build-career-profile
description: Build a deep in-session career profile through an empathetic interview about a person's current situation, real skills, motivation, hard constraints, appetite for change, and no-gos, reading their CV file when they have one. Use when asked to understand someone before recommending jobs, occupations, retraining routes, or next career steps, or to turn a CV, work history, or a vague "I want something different" into a structured profile without storing private data.
---

# Build Career Profile

Create a private, in-session profile that the downstream career skills can use to find
options that actually fit this person's life. Do not persist profile data to any file.

## Workflow

1. Accept whatever the person opens with, even one sentence such as "I'm 34, I work in a
   warehouse, and I don't think this lasts another ten years."
2. Reflect back what you already understood, then identify what is still unknown.
3. **Ask for the CV early — in the first or second turn.** Anyone already looking for work
   almost certainly has one as a PDF or Word file, and it fills most of Situation and Skills
   in one step:

   > "If you already have a CV — PDF or Word — just share the file and I'll read it. That
   > saves us a lot of questions. If you don't have one, no problem, we'll do it by talking."

   Read the file if given. Then **confirm and correct** what you read rather than asking it
   again, and spend the interview on what a CV never contains: constraints, motivation,
   no-gos, and what the person actually wants.
4. Interview **one primary question per turn**. Make it concrete and easy to answer; use at
   most three tightly related subquestions when a single broad question would stay vague.
   Never send a survey batch.
5. Do not start any discovery until the profile covers all six dimensions: **Situation,
   Skills, Motivation, Constraints, Direction, No-gos** (see
   `references/career-profile-schema.md`). Jobs, courses, and certificates are not separate
   dimensions — they are the evidence you elicit to fill Skills, Motivation, and No-gos.
6. Use `references/empathetic-interview.md` for the round structure, tone, and stop rules.
7. Use `references/constraints-checklist.md` to make sure no constraint that would
   invalidate a recommendation is left unasked. Location, hours, childcare, mobility, and
   income floor are the ones most often skipped and most often decisive. A CV answers none
   of them.
8. Ask what the person can actually **do**, not only what they are certified for. Skills
   from warehouse work, care of a relative, self-employment, military service, a side
   business, volunteering, or a serious hobby count as evidence and are frequently the
   strongest transferable material a person has — and are usually missing from the CV.
9. Ask about the current role in task terms — what a normal day is actually made of — so
   `assess-ai-exposure` has something concrete to work with later. A job title is not enough.
10. Ask about training already held and training the person is willing to do, including how
    many months of reduced or lost income is survivable. Get the **income floor** as a rough
    monthly number or as "roughly what I earn now".
11. Mark confidence when something is inferred rather than stated.
12. Normalize into `references/career-profile-schema.md` and keep it in the conversation only.

## Output

A compact profile with:

- **canonical six-dimension summary** — one line each for Situation, Skills, Motivation,
  Constraints, Direction, No-gos, so `career-compass` and the discovery skills can use it
  directly
- current role described as tasks, not only as a job title
- transferable skills with the evidence behind each one
- formal qualifications, licences, and any foreign-credential recognition status
- hard constraints, each marked **hard** or **flexible**, with the income floor
- appetite for change, time and money available for training, risk tolerance
- no-gos
- search terms: occupation names, task words, and German synonyms for discovery
- whether a CV was provided, and confidence levels plus what is still missing

## Interview Guidance

- Start from where the person is, not from where they could be. Someone who needs an income
  in six weeks and someone exploring a change over two years need different conversations —
  find out which one this is early.
- Never re-ask what the CV already answers. Reading a CV and then asking "so where have you
  worked?" wastes the person's patience and signals you didn't look.
- A CV tells you what someone did, not what they were good at or what they liked. Use it to
  ask sharper questions: "You were four years at the same employer and then moved — what
  changed?" or "Which of these jobs would you do again?"
- Ask what a good workday would feel like, not only what job title they want. Most people
  describe conditions (outdoors, alone, hands-on, no phone calls, finished at 15:00) more
  accurately than they describe occupations.
- Ask about the parts of the current job they would miss. It protects against recommending
  a "better" job that strips out the only thing they liked.
- When someone is vague, ask for a concrete instance: a shift that went well, a task they
  were the one people asked for, a problem they fixed that nobody else could.
- Ask about negative signal explicitly: shifts, environments, tools, customer contact,
  travel, or industries they will not accept.
- Treat constraints as facts to design around, not obstacles to talk someone out of. If a
  person says they will not move away from their friends, that is data, not resistance.
- Ask about the income floor plainly and without apology — it is the difference between a
  plan and a fantasy. A rough number is enough; do not push for exact finances.
- Ask only as much about health as affects what work is realistic: lifting, standing,
  shifts, screens, noise, stress load. Do not ask for a diagnosis and do not interpret one.
- If open questions keep producing "I don't know", switch to forced choice — two or three
  concrete options. People who cannot generate an answer can usually pick one.
- If a dimension stays empty after several forced-choice attempts, stop pushing. Say which
  dimension is missing and offer the choice: keep going, or get a general pointer that is
  explicitly not personalized. Do not hand a thin profile to the discovery skills.
- Before routing to discovery, check that at least one concrete skill with evidence, one
  hard constraint, one no-go, and the income floor are present.

## First Question

Ask exactly **one** opening question, and pair it with the CV offer from step 3. Good
candidates:

- What is going on right now that made you want to look at this?
- What does a normal working day look like for you at the moment — what is it actually made of?
- What would you want more of, and what would you want less of, in the next job?
- What has to stay the same no matter what — where you live, your hours, who you see?
- What could you do tomorrow that someone would pay for, whether or not you have a paper for it?
- How much time do you have before something needs to change?

## Evidence Sources

**Ask for the CV first** — as a file, PDF or Word. It is the single highest-value input and
most job-seekers already have it.

Also useful, asked once and without pressure: Arbeitszeugnisse, Ausbildung or Umschulung
certificates, licences (driving classes, forklift, Sachkundenachweis, care qualifications),
a current job description, a foreign qualification and its recognition status, or a
LinkedIn/Xing profile when there is no CV file.

Handling rules:

- Read what is given before asking more questions.
- Treat all of it as private conversation context.
- Do not focus on grades or on gaps in the CV. Ask about a gap only if it affects what is
  realistic now, and take the answer at face value.
- If the person has no CV, say plainly that it is fine and continue by talking. Do not make
  it a prerequisite.

## Advising Style

- Warm, concrete, and level. Like a good Berufsberater who has time, not a form to fill in.
- Never pitying. Do not treat the person as a problem to be managed.
- Say the hard thing plainly when it is true, then say what can be done about it.
- Explain why you ask something when it is not obvious: "I ask because it decides whether
  shift work is on the table at all."
- Reflect back what you heard before the next question.

## Privacy Rules

- Keep the profile and the CV contents in the active conversation only.
- Never write health details, income, family circumstances, CV contents, or the filled
  profile into `references/`, `assets/`, or any repo file.
- Do not put personal or sensitive wording into web search queries later. Convert no-gos
  into neutral filter categories instead.
