# prep — the per-posting brief

Input: `jd.txt` (required), `00-jd-breakdown.md`, `report.md`, `01-cv-tailored.md` if present, `me/cv.md`, `config/profile.yml`, `me/stories.md` if present.

Use `01-cv-tailored.md` as the version of the CV the interviewer has in front of them: whatever was moved to the top or bolded is what they'll ask about first.

Ask before writing only if it changes the brief: which round is next (recruiter screen / technical phone / onsite), and when. All sections are always written — the loop is longer than one round — but the next round decides the emphasis: section 8 is built for it, and the section it tests gets the most detail. Round unknown: weight everything evenly.

Output: `applications/.../02-interview-prep.md`, in this order. It gets read the night before: tables and short lines, no explanatory padding.

```
# {Company} {Role} — Interview Prep

**Round:** {next round, date if known}   **Level:** {from breakdown or inferred from JD}
**Loop:** {from JD / recruiter, else "typical for this kind of role — unconfirmed: ..."}

## 1. What they will probe
| # | JD requirement | Your evidence | Likely question | Story |
```

One row per must-have (reuse M1..Mn from the breakdown when it exists), then the nice-to-haves as B1..Bn. Evidence quotes the CV and starts with `OK`, `PARTIAL` (the CV covers part of the requirement — say which part is missing) or `GAP`. `Story` is an ID from `me/stories.md`; with no story bank yet, the CV bullet a story could be mined from, or `none`. Under the table give the honest answer for each PARTIAL and GAP on a must-have: the adjacent thing they have done, quoted from the CV, and no pretending. If nothing adjacent is on the CV, `[YOU: ...]`.

```
## 2. Tell me about yourself
```

60-90 seconds spoken, about 150-200 words. Present (what you do now, one concrete result) → past (the one or two things that led here) → future (why this role). Every fact from the CV. Tilted to the JD's first three requirements. Written to be said aloud: short sentences, no bullet fragments.

```
## 3. Why {Company}, why this role
```

Two or three reasons built from the JD's own words about the product, the team's problem, or the stack — tied to something the candidate has done. If the real reason has to come from the candidate (why they care about this domain), write `[YOU: ...]` with the question they need to answer, instead of inventing a passion.

```
## 4. Behavioral — questions and the story for each
```

Eight to ten questions: the competencies this JD signals (see the table in `behavioral.md`) plus the standing ones — conflict, failure, ambiguity, a decision with incomplete data. Map each to a story ID. Flag any story used for more than two questions, and any question with no story: that is the list for `stories`.

```
## 5. Technical focus
```

- **Coding:** the topics this JD makes likely, named from its stack and domain (a payments backend means idempotency, concurrency, state machines — not just "arrays and graphs"). Three to five.
- **System design:** two or three prompts close to what this team builds, phrased the way an interviewer would open. Skip for internships and most new-grad loops unless the JD mentions design; say so.
- **Depth questions on your own CV:** for the two projects most relevant to the JD, the follow-ups an engineer would ask — why that design, what broke, what you'd change, how you measured the number on the bullet. These are the questions people fail most often, because they assume their own resume needs no prep.

```
## 6. Concerns and counters
```

What a skeptical interviewer sees in this CV for this role — a gap from section 1, short tenure, a domain switch, level mismatch. One or two sentences each: acknowledge, evidence, move on.

```
## 7. Logistics
```

- **Work authorization:** the answer built from `location.visa_status` in `profile.yml` (still the placeholder text: ask the candidate). Short, factual, same wording every time: status now, whether sponsorship is needed and from when. If the JD says no sponsorship and the candidate needs it, say so here plainly — don't let them find out at the offer stage.
- **Compensation:** when the recruiter asks for a number first, the candidate asks for the range for the level instead ("I'd like to understand the level and the range you've budgeted — I'm sure we can find something that works if it's a fit"). Many US states require the range on the posting; quote it if `jd.txt` or the breakdown has it. Do not supply market numbers from memory — point the candidate to check levels.fyi for the company and level.
- **Questions to ask them:** five, specific to this JD (what the team shipped last, how on-call works, what the first 90 days look like, how this role's success is measured). None that the posting already answers.

```
## 8. Before the round
```

A checklist of at most five items, taken from this brief: the stories to rehearse aloud, the gaps to have an answer for, the one topic to review.

After writing, say in two lines what is thinnest (usually: stories missing, or a GAP on a must-have) and offer the matching command.
