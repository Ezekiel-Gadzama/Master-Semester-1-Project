# Managing Software Development — course agent

Read this file after the workspace `AGENTS.md`. Then follow `AGENTS.md` §3 (materials → **Course chat** → team chat → slides → report).

Official course Telegram export: `Course chat/` (latest `ChatExport_*`). Search it for this case’s code and title (e.g. C1, Satera) for deadlines, room, and instructor corrections. If an instructor message changes the report date, that date wins and goes on the title page.

Team chat is `{team name} chat/` at the workspace root (currently `Temporary name chat/`). Search only messages about this case.

Then read `CASE-RULES.pdf` in this course folder (every case). Then that case’s `Materials/`. If this file and `CASE-RULES.pdf` disagree, the PDF wins unless course chat is an instructor correction.

Do not start the report until those sources are read.

## What every case is

Same day shape, same deliverables, same grading. The case sheet only adds what is specific to that case (questions, readings, constraints).

- **Slides:** 8 maximum, PDF on Moodle before slot 3. White background, black text, no template. Slide title is the claim. At most 6 bullets, 12 words, 24 pt. Tag every line `[F]` or `[A]`.
- **Report:** the same argument in sentences, in the same order. **5 pages maximum for the body**, not counting the title page, references and appendix. **11 pt** (CASE-RULES: 11–12 pt). Due the Friday one week later, 23:59, unless Moodle says otherwise.
- Allowed sources: the case, the lectures, and the readings named on the case sheet (including MSDBOK where named). Anything else scores nothing.

## Title page

One page, using `coursereporttitle`. CASE-RULES title slide is team, members, **who did what** — the report title page is the same: a Member / Contribution table via `\member{Name}{what they did}`. Fill contributions; do not invent them.

Citation-key wording for MSD reports:

> Citation key. “p.N” is a page of the case and “Exhibit N” a case exhibit. “L1a s.N” and “L1b s.N” (or the lecture codes the case sheet names) are slide numbers in the course lectures. [A] marks an assumption: the case is silent, so it cites nothing. Appendix A lists what each assumption rests on and what changes if it is wrong.

Cite the actual case and lecture bib keys in that paragraph (`\parencite{...}`). Always write `p.` — never `pp.` — including ranges and lists: `p.~5`, `p.~1--2`, `p.~1, 9`. Same for slides: `L1a s.12--13`, not `ss.`

## LaTeX format (whole course)

Match `Satera-C1-Report.docx`. Do not invent a different layout per case. Every MSD report uses `11pt,letterpaper`, `\input{../../common/preamble}`, then `\input{../preamble}`.

- Page: US Letter. Margins 0.945 in left/right, 0.866 in top/bottom.
- Body: Calibri-metric (`carlito`), 11 pt, line spacing 1.079, 5 pt between paragraphs, no first-line indent.
- Heading 1: 13 pt bold, 10 pt above, 4 pt below. Heading 2: 11.5 pt bold, 6 pt above, 3 pt below.
- Title page (one page, not counted): title 22 pt bold, subtitle 13 pt, course/date 11 pt, team 12 pt, Member/Contribution table 11 pt, citation key 9.5 pt italic.
- Captions 9 pt. References hanging indent 0.8 cm.
- Body ≤ 5 pages. `\clearpage` before references and before the appendix so they do not count.

Do not change report wording to fit the limit; the format above is what makes it fit.

## Report order (answer first)

1. Recommendation — one sentence, then what changes.
2. Why — one root problem, not a list. Reasons carry the recommendation; each runs through a named lecture or reading concept **used**, not just labelled.
3. What we do — who, by when, how we know it worked.
4. What could go wrong — the risk that would change the answer, usually the load-bearing assumption.
5. What changed since the presentation — only if the answer moved after cross-examination; say what changed it.
6. References, then Appendix A (assumptions table).

## Facts, assumptions, concepts

- Every claim cites the case (page or exhibit) or a named lecture/reading. An uncited claim is an opinion and scores nothing.
- `[A]` is the exception: the case is silent. Mark it, say what it rests on, and what changes if it is wrong. An assumption written as a fact is graded as a wrong fact.
- Facts come from the case. Logic comes from the course. Use the concept so that deleting the name would lose the explanation.
- One root problem. Describe behaviour, do not verdict on personality or character. Check what an exhibit measures before quoting it. A plan needs an owner, a date, and a success measure.

## C1 (Satera) — extra constraints from that sheet

Still read `c1-satera/Materials/C1-SATERA-Assignment.pdf` and the HBS case. Short reminder only:

- Tiger team, 30 days, no new hires, no extra budget, no relief on the schedule.
- People problem (leadership, teamwork, process), not a technical fix.
- Questions: one root; evidence vs assumptions; 30-day plan with owner/date/measure; biggest risk and fallback.
- Reasoning must run through L1a / L1b as those lectures define the concepts.
