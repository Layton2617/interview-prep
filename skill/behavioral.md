# behavioral — story bank and mock

## The story bank: `me/stories.md`

Six to eight stories cover almost every behavioral question. Each one is a real episode with a decision in it.

```
## S3 — Idempotent retry for the ledger writer
**Source:** Acme Corp (cv.md: "Cut duplicate ledger writes ...")
**Competencies:** ownership, technical judgment, dealing with ambiguity
**Headline:** one sentence that could open the answer.
**Situation:** two sentences. Team, system, what was at stake.
**Task:** what was yours specifically.
**Action:** three to five steps, first person singular, including the alternative you rejected and why.
**Result:** the number, and what happened after.
**Reflection:** what you would do differently / what you now do by default.
**Open:** facts still missing (asked, not yet answered).
```

### Mining stories

Start from `me/cv.md`: each bullet with a number or a verb like built / led / migrated / fixed is a candidate. Propose the list ("I see five possible stories here") and let the candidate pick which to do first. IDs are S1, S2, ... in the order stories are added and never change. Stories not mined yet are still written, as a skeleton: Source and whatever the CV supports, every other field left as a question under **Open**.

For each one, interview them — one question at a time:
1. What was going wrong, and what would have happened if nobody did anything?
2. What part was yours? What did the others do?
3. What did you consider and not do? Why?
4. What was the hard moment — a disagreement, a wrong first attempt, a deadline?
5. What was the result, and how do you know? Where does the number come from?
6. What do you do differently now?

Write only what they said plus what the CV says. Anything you'd need to guess goes under **Open** as a question. A story with no conflict, no alternative and no number is a task description; tell them so and dig or drop it.

The CV rarely contains the stories interviewers most want: a failure, a conflict, a time they were wrong. Ask for those directly — class projects, internships and part-time jobs all count for early-career candidates. Until answered, keep them in a last section of the file, `## Asked, not yet answered`.

When the bank changes and the pack in play has a `02-interview-prep.md`, update the Story columns in its sections 1 and 4.

### Competencies

| Competency | Typical question | Listens for |
|---|---|---|
| Ownership | a time you went beyond your role | acted without being asked; followed through to the result |
| Conflict | a disagreement with a teammate or manager | understood the other side; resolved it on substance; relationship intact |
| Failure | a mistake you made | it was actually your mistake; what changed afterwards |
| Ambiguity | a project with unclear requirements | how they created clarity; what they decided without full data |
| Influence | convinced someone without authority | evidence over insistence |
| Delivery | a tight deadline, competing priorities | what they cut, and how they told people |
| Learning | picked up something new fast | the method, not just the outcome |
| Technical judgment | a hard technical decision | alternatives, tradeoffs, how they validated |
| Customer focus | changed something based on user feedback | went to the source; measured after |
| Feedback | received critical feedback | no defensiveness; a concrete change |

Amazon runs its whole behavioral loop off the sixteen Leadership Principles and expects two stories per principle with metrics; for an Amazon pack, tag each story with LPs and mock by principle. Other companies: use the values the JD itself names, nothing more.

## mock behavioral

Pick four or five questions: from section 4 of the prep brief if it exists, else from the competencies the JD signals; always one of failure / conflict. Weight toward the weakest dimension in `me/interview-log.md`.

For each question:
1. Ask it the way an interviewer would, plainly. Wait.
2. Probe at least once on every answer, twice when it is thin, as a real interviewer does: "What was your part specifically?", "What did you consider instead?", "How did you measure that?", "What did your manager say?", "What would you do differently?". Don't rescue a vague answer by asking a leading question.
3. Move on. No feedback yet.

A real answer runs about two minutes — roughly 250-350 words typed. Note it when an answer is far over or far under.

After the last question, step out of character and score each answer. Score the whole exchange, probes included, but content that only came out under a probe caps Structure and Relevance at 3. The table anchors 1, 3 and 5; 2 and 4 are in between.

### Rubric — 1 to 5 per dimension

| | 1 | 3 | 5 |
|---|---|---|---|
| **Substance** | claims, no evidence | specific actions, result not quantified | quantified result, alternatives weighed, reasoning shown |
| **Structure** | wanders, point unclear | STAR present but setup is half the answer | headline first, setup under 20%, lands on the result |
| **Relevance** | answers a different question | right story, noticeable drift | every sentence serves the question asked |
| **Credibility** | "we" throughout, role unclear | role clear, some claims unverifiable | own contribution precise, numbers sourced, limits admitted |
| **Differentiation** | anyone could have said it | competent, forgettable | an insight only someone who did the work would have |

Verdict per answer and for the round: strong hire / hire / lean hire / lean no hire / no hire. Calibrate to the level in the pack: a new grad is not expected to have led a team; a senior is expected to show scope beyond their own tasks.

### Feedback format

Per answer:

```
Q2 — conflict with a teammate
Sub 3  Str 4  Rel 4  Cred 3  Diff 2  → lean hire
Heard: one-sentence paraphrase.
Working: the strongest thing, quoted.
Fix: the one change. Then: "Give me just that part again."
```

Go answer by answer: feedback, wait for the redo, say whether it moved and why, then the next answer. The log keeps the first-attempt scores. Finish with the round verdict.

Patterns worth naming when you see them:
- **"We" answers** — the interviewer cannot hire the team. Every action sentence needs an "I".
- **No result** — the story stops when the work shipped. Ask what happened next.
- **Long runway** — 90 seconds of context before anything happens. Start at the decision.
- **The fake failure** — "I worked too hard". Pick a real one; the reflection is the answer.
- **Blame** — the other person in a conflict story is described as simply wrong. Give their reasoning its due.
- **One story for everything** — repetition across interviewers shows up in the debrief. Map questions to different stories.

After the round: update `me/stories.md` with anything new the candidate said (a number, a detail, a better headline), and log each answer.
