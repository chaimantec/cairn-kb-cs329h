# How this knowledge base is organized

This repo is the knowledge base for **CS329H — Machine Learning from Human Preferences**. It is read
by Cairn's in-extension AI chat, which starts at `INDEX.md`, fetches files over
raw.githubusercontent.com and follows relative markdown links.

The chat never reads this file. It is for whoever builds the KB, and Claude Code
loads it into every step of every build agent, so keep it to the rules every
lecture's build follows. The per-lecture record (licence notices, audit findings,
printed slips, which slides were rendered and why) goes in
[`BUILD_LOG.md`](BUILD_LOG.md); anything the chat needs goes in `INDEX.md`.

## Layout

| Path                | Contents                                                      |
| ------------------- | ------------------------------------------------------------- |
| `INDEX.md`          | Entry point. Course summary + annotated table of contents.    |
| `wiki/`             | Durable pages: one per lecture, plus cross-lecture topics.    |
| `raw/slides/`       | Empty: the course publishes no slides (see below).          |
| `raw/transcripts/`  | Edited transcripts with `[MM:SS]` paragraph marks — the ones to read. |
| `raw/transcripts/original/` | Verbatim auto-captions, the reference for what was said. |
| `raw/pdfs/`         | Gitignored. Nothing downloaded: the site links no documents. |
| `raw/images/`       | None: no slides to render.                                   |
| `sources.md`        | Crawl inventory: source URL → local file, fetch date.         |
| `TODO.md`           | Open work only. Finished runs move to `BUILD_LOG.md`.       |
| `BUILD_LOG.md`      | Finished runs, one section each. Not needed to answer questions. |

## Conventions

- **INDEX.md is the front door.** The chat reads it first on every conversation.
  Every wiki page must appear there with a one-line description of what it holds.
  An unindexed page is effectively invisible.
- **Relative links only** (`[gradient descent](gradient-descent.md)`,
  `[slides](../raw/pdfs/lecture03.pdf)`). Absolute GitHub URLs break when the
  repo is renamed or forked.
- **Cite everything.** Claims trace back to a transcript timestamp or a slide.
- **Never invent course content.** If the transcript is unclear at some point,
  say so on the page. Do not fill the gap from outside knowledge — the chat
  presents these pages as authoritative material from this course.
- **Prose over fragments.** The chat quotes these pages to learners; bullet
  fragments quote badly.
- **Math in LaTeX**: `$...$` inline, `$$...$$` displayed. Renders both in
  Cairn's chat and on github.com. Never inside a code fence — that shows the
  source instead of the formula. Define each symbol on first use, and follow the
  course's own notation rather than a tidier one, since the learner is comparing
  the page against the lecturer's board.
- **Transcripts stay verbatim.** Captions spell notation out as speech ("theta
  sub j"); reconstructing it as $\theta_j$ belongs in `wiki/`, not in
  `raw/transcripts/`.

## This course

- **No slides exist publicly** (Autumn 2023/2024/2025 sites and `slides/` paths checked). The KB is
  transcript-only: `kb.json` `materials.method` is `none`. Cite transcript timestamps as `(≈MM:SS)`.
  Before declaring a later lecture deck-less, re-check the site — a deck may have been posted since.
- **Unnamed papers.** The lectures show papers on slides without naming them aloud. Describe them as
  the lecture does and say the reference is not in the audio. Do not identify them from outside
  knowledge, and do not borrow a citation from the reading list unless it clearly is the same work.
- **The textbook is not a source.** mlhp.stanford.edu (CC BY-NC 4.0) is a 2025–26 revision, not the
  2024 text. It may be used to check spellings during a transcript edit; take no content from it.
- **Numbering is by catalog position**, which does not follow the site schedule (the catalog puts
  the Oct 30 guest lecture last). Map each lecture to its schedule date from its transcript content,
  and state the mapping on its page.
- **Transcript edit.** Delegate the copy-edit to a Sonnet subagent with the verbatim captions, the
  course site text and the textbook glossary as terminology references. Check in the parent: identical
  timestamp sequence, number-inventory diff of the bodies, per-paragraph word ratio within
  0.72–1.10. The agent marks speaker turns `*Student:*` / `*Koyejo:*` and unclear passages
  `[Ed: unclear — "…"]`.
  Key the ratio check **by timestamp, not by position**, and re-run the marker diff in the parent
  rather than trusting the agent's report: a dropped paragraph shifts a positional pairing, and
  neighbouring ~45-second paragraphs are similar enough in length to pass.
- **Topic pages** open with a `**Sources so far:**` line naming the lectures they draw on. Update
  it when a later lecture adds to the page, and update the coverage note in `INDEX.md` and the
  "not yet in this KB" lecture list with it.

## Rebuilding

Built and updated by the `cairn-kb` skill. To add newly released lectures,
append entries to `TODO.md` and re-run the skill — it only does unchecked work.
When a run is committed and pushed, move its `TODO.md` section verbatim to
`BUILD_LOG.md`, so `TODO.md` keeps only open work. Add here only a lesson
that applies to every lecture, stated in general form.
