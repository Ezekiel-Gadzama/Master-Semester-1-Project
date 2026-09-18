# Masters Semester 1 — Agent Rules

Canonical instructions for **every** AI (Cursor, Codex, Claude Code, Copilot, ChatGPT, etc.).
Do not duplicate this file. Claude reads `CLAUDE.md`, Copilot reads `.github/copilot-instructions.md`;
both point here. Course-specific operating rules live only in that course’s `Agent.md`.

This workspace is two courses: **Managing Software Development** and **Requirement Engineering**.
Open this parent folder, not a single course.

---

## 1. How to work

- **Do strictly what the task says.** Do not rewrite report wording to “improve” it unless asked.
- **Do not invent.** Facts, page numbers, slide numbers, deadlines, member contributions, and
  citations come from materials, chats, or slides. If a source is silent, mark an assumption or
  leave a placeholder.
- Read **sources in the order in §3** before writing or updating a report.
- British English in reports. Chat replies to the user in English.
- **No AI watermarks or encoded characters.** Never insert hidden Unicode: zero-width
  spaces/joiners (U+200B–U+200D), BOM, soft hyphens, bidi overrides, Unicode tags,
  variation selectors, private-use code points, or homoglyphs used as watermarks.
  After any edit (including paste from Word, Google Docs, or chat), scan the changed
  `.tex`/`.bib` and strip those characters. In LaTeX source use ASCII plus markup
  (`---`, ` `` ` `''`, `\textperiodcentered`, `~`), not Unicode punctuation copied
  from a word processor. Visible curly quotes or em dashes in Markdown rules files
  are allowed; they must not appear in report source.

---

## 2. Layout

```
AGENTS.md                         # this file (all AIs)
CLAUDE.md                         # @AGENTS.md
.github/copilot-instructions.md   # points here
.vscode/  .cursor/rules/  common/

<Team name> chat/                 # team Telegram export (e.g. Temporary name chat/)
Managing Software Development/
  Agent.md
  Course chat/                    # official course Telegram export
  CASE-RULES.pdf                  # MSD-only; named from that Agent.md
  <assignment>/                   # e.g. c1-satera
    report.tex  ref.bib  .latexmkrc
    Materials/                    # brief, case/spec, lectures
    slides (pptx/pdf if present)
Requirement Engineering/
  Agent.md
  Course chat/                    # same convention when exported
  <assignment>/
```

The team chat folder is `{team name} chat/` at the workspace root. The course chat folder is
always `<course>/Course chat/`. Re-export Telegram into those folders; use the **latest**
`ChatExport_*` by date.

---

## 3. Before writing or updating any assignment

Do this every time, for every course. Skip a step only if that folder does not exist yet.

1. This file (layout and title page).
2. `<course>/Agent.md` (how that course grades and what sources it allows).
3. Course-wide rule documents named in that `Agent.md` (MSD: `CASE-RULES.pdf`).
4. The assignment’s `Materials/` — brief, source document, named lectures/readings.
5. **Official course chat:** `<course>/Course chat/` → latest `ChatExport_*/messages.html`.
   Search for this assignment (code, case title, “deadline”, “report”, “slides”).
   Instructor messages win over the handout when they correct a date, room, or deliverable.
6. **Team chat:** `{team name} chat/` → latest `ChatExport_*/messages.html`.
   Search for the same assignment only. Use it for decisions, who did what, slide links,
   and what changed after the presentation. Ignore other courses and other assignments.
7. **Slides** for this assignment (pptx/pdf in the assignment folder, or the link the team
   chat names). The report is the same argument in sentences, in the same order as the slides.
8. Then write or update the report. Set the title-page **Submitted** date from the official
   deadline (course chat, else `Agent.md` / brief). Fill `\member{Name}{contribution}` from
   team chat if people said who did what; otherwise leave the placeholder — do not guess.

Do not load an entire Telegram export into context. Search `messages.html` (and `messages2.html`
if split) for the assignment’s identifiers first, then read the matching messages.

If sources disagree: instructor course-chat correction > course `Agent.md` / official PDF >
assignment brief > team chat > old draft.

---

## 4. Title page (one page)

Every report uses `coursereporttitle`. Do not add extra decoration (no horizontal rule under
the subtitle).

1. Title
2. Subtitle
3. Course, university, term, then the submission date
4. Team name
5. **Member / Contribution** — one `\member{Name}{what they did}` row per person
6. Citation-key paragraph (wording from the course `Agent.md`)

The body starts on the next page. The title page, references and appendix do not count toward
a page cap.

---

## 5. LaTeX

- MSD: `11pt,letterpaper`, `\input{../../common/preamble}`, `\input{../preamble}`.
- Other courses: `12pt,a4paper`, `\input{../../common/preamble}` until that `Agent.md` says
  otherwise.
- `biblatex` + biber. `\bibliography{ref.bib}` after the preamble input.
- After any change to `report.tex`, `ref.bib` or a preamble: run `latexmk` **from the
  assignment folder** so `.latexmkrc` copies the shareable PDF (`$pdf_copy_name`). That copy
  is the deliverable. Confirm its timestamp updated.
- Edit `common/preamble.tex` only when **both** courses should change.

---

## 6. New assignment

1. Copy `common/assignment-template` to `<Course>/<id>/`.
2. Put the brief and sources in `Materials/`. Put slides in the assignment folder when you have them.
3. Put Telegram exports in `{team} chat/` and `<course>/Course chat/` (latest `ChatExport_*`).
4. Set `$pdf_copy_name`. Fill the title page from §4 and the course `Agent.md`.

---

## 7. Git commit messages

Commit as the human authors only. **Never** list an AI as a contributor.

- One-line subject (optional short body). Do not append trailers.
- Never add `Co-authored-by`, `Signed-off-by`, `Made-with`, `Generated-by`, or similar
  for Cursor, Claude, Copilot, ChatGPT, Codex, Composer, Gemini, or any other agent
  (including `Cursor <cursoragent@cursor.com>`). GitHub/GitLab treat those as authors.
- After `git commit`, run `git log -1 --format=%B`. If an AI trailer is present, recreate
  the commit so the message is clean **before** push. Do not skip hooks.
- Keep the hook at `.githooks/commit-msg` installed as `.git/hooks/commit-msg` so those
  trailers are stripped even if a tool appends them.
