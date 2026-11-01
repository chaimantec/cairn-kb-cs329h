# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 1 — lecture 1 (2026-11-01)

Scope: lecture 1 only, of 8 in the catalog. No slide decks are published for
any offering (fall2023, fall2024, fall2025 archives and `slides/` paths checked),
so this is a transcript-only build. The course textbook (mlhp.stanford.edu,
CC BY-NC 4.0) is a 2025–26 revision and is linked, not ingested; it is used
only to cross-check terminology in the transcript edit.

### Transcripts
- [x] 01 Introduction — video ApF2OenMgfc (verbatim + edited)

### Crawl
- [x] Course site index: https://web.stanford.edu/class/cs329h/fall2024/ — 2 pages, 0 documents (all links off-site)
- [x] sources.md (links only; hand-written, crawl inventory empty)

### Wiki
- [x] wiki/01-introduction.md
- [x] Topic pages: rlhf, preference-queries, reward-hacking, metric-elicitation, whose-preferences
- [x] INDEX.md table of contents

### Publish
- [x] kb.json — coverage, materials.method "none", provenance caveats
- [x] LICENSE.md
- [x] SEE_ALSO.md — CS224N, CS224R, CS336 (all complete; RLHF/DPO/reward-model pages confirmed to exist)
- [x] BUILD_LOG.md — lecture 1 record: transcript edit counts and checks (the Record below, moved with this section)
- [x] verify_kb.py clean, and its review section read (hard checks pass; review: partial-coverage note, which INDEX.md states)
- [ ] Commit and push
- [ ] PATCH kbUrl onto the catalog entry
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 1

- **Catalog ↔ schedule.** Catalog position 1 "Introduction" (video ApF2OenMgfc, 4623 s) is the
  Sep 23 schedule row. The recording ends at ≈1:16:26 as Koyejo turns to "existing choice models".
- **Slides.** None published. Checked: fall2024 index (links only off-site docs), `fall2024/slides/`
  and `cs329h/slides/` (404), fall2023 and fall2025 indexes (papers and Google Docs only). The textbook
  link printed on the 2024 site (ai.stanford.edu/~sttruong/mlhp/) timed out; mlhp.stanford.edu serves
  the current revision, whose repo (stair-lab/mlhp) has no commit before 2024-09-24 and was last
  revised 2026-02-13.
- **Reading list** (Google Doc export, 1,471 words) is thematic, not per lecture. It names none of the
  papers lecture 1 shows (taxonomy figure ≈30:07, summarization results ≈54:52, Pew-survey study
  ≈1:03:21, Caltech exoskeleton ≈1:05:41, 2008 helicopter ≈1:12:36), so the wiki leaves them unnamed.
- **Transcript edit** (Sonnet subagent, 13 tool calls). Parent checks: 100/100 timestamps
  identical and in order; number inventory differs only by "01"→"o1" ×2 (≈52:34) and
  "CS39H"→"CS 329H" (≈1:16:26), both deliberate; no paragraph outside the 0.72–1.10 word ratio
  (body 12,576 → 11,184 words, 0.889). About 30 restorations listed in the header; 22 `[Ed: unclear]`
  marks. Parent spot-checked against the verbatim captions: OLMo/AI2 ("Elmo AI2", "company out of
  Seattle"), boat ("bolt"), Medium ("still up on medium"), 25%, 60%, $30,000, "a million dollars",
  "groups of up to five". All accepted. Judgment calls left as the agent made them: speaker turns
  at 7:00, 13:52 and 54:06 may be split imperfectly; the ≈8:33 "I work on papers on this topic" is
  attributed to Koyejo with an `[Ed:]` note that it may be the teaching fellow.
- **Wiki.** Two embellishments caught on re-read and removed before commit: the boat agent
  "circles in one spot" and "boat race", neither of which is in the lecture.
