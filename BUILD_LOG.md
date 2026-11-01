# Build log — CS329H knowledge base

The record of how this knowledge base was built and checked, one section per
finished run, in order: each deck's licence notices and lecture pointers, each
transcript's edit and checks, what each figure audit found, each deck's printed
slips, and which slides were rendered as images and why the others were not.
A run's section is its `TODO.md` checklist, moved here verbatim once the run
was committed and pushed. It holds no unchecked box: open work lives only in
`TODO.md`.

It is a build record, **not needed to answer questions**: every fact a learner
needs is on the wiki page, slide file or transcript it concerns. The rules
every build follows, and each lesson in general form, are in
[`AGENTS.md`](AGENTS.md).

## Index

| Lecture | Runs |
| --- | --- |
| 1 Introduction | Run 1 |
| 2 Preference Models | Run 2 |
| 3 Model-based Preference Optimization | Run 3 |

## Runs

_Each finished run's section is appended below._

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
- [x] Commit and push — d22144e, new public repo chaimantec/cairn-kb-cs329h
- [x] PATCH kbUrl onto the catalog entry — re-fetched, kbUrl set; raw INDEX.md returns 200
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

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

## Run 2 — lecture 2 (2026-11-01)

Scope: lecture 2 only. Slide decks re-checked before starting: fall2024 index, `fall2024/slides/`
and `cs329h/slides/` (both 404), fall2023 and fall2025 indexes. Still none; transcript-only.

### Transcripts
- [x] 02 Preference Models — video -bych9RfQvw (verbatim + edited; ticks the "Not yet built" line)

### Crawl
- [x] Re-check course site for a deck (none); sources.md lecture-2 video row

### Wiki
- [x] wiki/02-preference-models.md
- [x] New topic page: wiki/discrete-choice-models.md
- [x] Topic pages updated: preference-queries (ratings and rankings, revealed vs stated, transitivity), rlhf (comparison step as a choice model), whose-preferences (one utility or many); Sources-so-far lines
- [x] INDEX.md — coverage note, lecture 2 entry, topic list, not-yet list, numbering note

### Publish
- [x] kb.json — coverage 2/8, caveats
- [x] AGENTS.md — lesson: key the ratio check by timestamp, re-run the marker diff in the parent
- [x] BUILD_LOG.md — lecture 2 record (the Record below, moved with this section)
- [x] verify_kb.py clean, and its review section read (hard checks pass; review: partial-coverage note, which INDEX.md states; open boxes are lectures 3–8 and this run's last two steps)
- [x] Commit and push — 2e906cc
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 2

- **Catalog ↔ schedule.** Catalog position 2 "Preference Models" (video -bych9RfQvw, 4768 s) is most
  likely the Sep 25 row "Lecture: Individual Preference Models". The date is not spoken. Evidence:
  "alluded to this last time" about logistics/delivery (≈3:58) and "as mentioned in the last class"
  about logistic regression (≈29:32) both match lecture 1 (≈16:08, ≈16:55); the lecture opens on the
  choice models lecture 1's recording stops at; the ideal point model is pushed "to next week"
  (≈1:17:39), and Sep 30 is the second Individual Preference Models row, which is not in the catalog.
  "Over the last couple of lectures" (≈6:14) is loose either way.
- **Slides.** None published (re-checked as above). The lecture's slides needed fixing mid-lecture
  (≈58:14). History references and application papers are on the slides, not in the audio.
- **Transcript edit** (Sonnet subagent, 12 tool calls). The agent reported its marker diff as SAME,
  but its file had 102 of 103 markers: the whole [1:11:28] paragraph was missing. Cause, confirmed
  from the backup its last `sed -i -E` left behind (`…md-E`, removed before commit): that final pass,
  which filled the header placeholders and compacted "U n 2" to "U n2" for the ratio, ran after the
  agent's marker check and deleted the paragraph. Diffing the backup against the final file shows
  nothing else changed. The parent's first
  ratio check paired paragraphs by position, which hid the gap (adjacent ~45 s paragraphs are similar
  in length) until the final pairing came out at 0.26; re-keyed by timestamp it points straight at
  the gap. The parent restored [1:11:28] from the captions. Final checks: 103/103 timestamps identical
  and in order; number inventory differs only by "epsilon one" → "epsilon 1" (≈41:11, listed in the
  header); every paragraph within 0.77–1.06 keyed by timestamp (body 13,073 → 11,922 words, 0.912).
  About 30 restoration lines (Thurstone, McFadden, Luce, Bradley-Terry, Plackett-Luce, ordered and
  exploded logit, Likert, IID, confounds, stated/revealed preference, scikit-learn, PyTorch,
  statsmodels); 21 `[Ed: unclear]` marks. Accepted as made: "real preference" → "revealed
  preference" (≈1:13:48, 1:16:53), "chest model" → "choice model" (≈32:37), "ID" → "IID". Parent
  corrected the header's carried-over "textbook's glossary" line to say the textbook was used for
  spellings only.
- **Wiki.** Every quotation (124 quoted spans) swept by script against the edited transcript; the
  only non-matches are the schedule's wording and one deliberately verbatim caption quote. One
  editorial inference removed before commit (a sentence in whose-preferences saying pooling decides
  whose preferences a model has). The ≈46:39 passage reworded so as not to rest on an `[Ed: unclear]`
  span. Formulas are rebuilt from speech and say so; the two-item logit's second form (≈39:37) is
  garbled in the captions. Bradley–Terry is named once (≈10:06) and never attached to a derived
  model in the audio, and the pages leave it that way.

## Run 3 — lecture 3 (2026-11-01)

Scope: lecture 3 only. Slide decks re-checked before starting: fall2024 index (no document links),
`fall2024/slides/` and `cs329h/slides/` (both 404), fall2023 and fall2025 indexes (no deck links).
Still none; transcript-only.

### Transcripts
- [x] 03 Model-based Preference Optimization — video 7i6WsIzZaeo (verbatim written; ticks the "Not yet built" line)
- [x] 03 edited transcript (Sonnet copy-edit; parent checks: markers, numbers, ratio by timestamp)

### Crawl
- [x] Re-check course site for a deck (none)
- [x] sources.md lecture-3 video row

### Wiki
- [x] wiki/03-model-based-preference-optimization.md
- [x] Topic pages updated, with Sources-so-far lines: metric-elicitation (restructured; lectures 1 and 3), preference-queries (active learning and query complexity, population- vs example-level questions, uniqueness assumption), whose-preferences (recidivism case, impossibility results), rlhf (three remarks)
- [x] INDEX.md — coverage note, lecture 3 entry, topic list, not-yet list, numbering note

### Publish
- [x] kb.json — coverage 3/8, caveats
- [x] BUILD_LOG.md — lecture 3 record (the Record below, moved with this section)
- [x] AGENTS.md — lesson: read each ratio outlier against its neighbours; the agent's explanation is not evidence
- [x] verify_kb.py clean, and its review section read (hard checks pass, 169 formulas render in chat and on github.com; review: partial-coverage note, which INDEX.md states; open boxes are lectures 4–8 and this run's last steps)
- [x] Commit and push — b34c3e5
- [x] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 3

- **Catalog ↔ schedule.** Catalog position 3 "Model-based Preference Optimization" (video
  7i6WsIzZaeo, 4968 s) is the Oct 16 row "Lecture: Model-based Preferences Optimization via
  Preference Elicitation". The date is not spoken. Evidence: the main topic is metric elicitation
  (≈0:05); "last lecture was active learning" (≈0:05, ≈2:22), the Oct 14 row; bandits in a future
  lecture (≈1:22:06), the Oct 21 row; mechanism design "quite a bit later" (≈0:05), the Oct 28 row.
  The schedule's Sep 30 to Oct 14 sessions are not in the catalog. The "lecture on HCI" (≈1:05:47,
  ≈1:09:41) is probably Nov 11 "Human-centered Design", catalog position 5.
- **Slides.** None published (re-checked as above). The reading list (Google Doc export, 1,471
  words, unchanged) names no metric-elicitation, Netflix or recidivism work, so the papers stay
  unnamed. The recidivism company and algorithm stay as captioned ("North Point", "compass"): no
  course document gives a spelling.
- **Transcript edit** (Sonnet subagent, 14 tool calls). References: course site text, textbook
  glossary, and the textbook's metric-elicitation section (§2.17.3), for spellings only. The agent
  reported clean checks and one outlier, [3:07] at 1.13, which it put down to a `*Student:*` tag and an
  `[Ed:]` mark. That was wrong: the paragraph's excess was the student sentence that opens [3:54] in
  the captions ("active learning is for like collecting library data sets…"), moved up to finish the
  question begun at the end of [3:07]. The parent moved it back and listed it in the header. The
  parent also marked "for black" (≈48:51) unclear and marked the student question after it. Final
  checks: 107/107 timestamps identical and in order; number inventory identical in both directions;
  every paragraph within 0.87–1.05 keyed by timestamp (body 14,397 → 13,822 words, 0.960, a lighter
  edit than lectures 1–2); no paragraph has more than six words absent from its original. About 40
  restoration lines, 33 `[Ed: unclear]` marks. Accepted as made: "metricalization" → metric
  elicitation, "RHF" → RLHF, "RMSSE" → RMSE, "censusing" → sentencing, "noise resetting" →
  noiseless setting, "HIL" → HCI (he says HCI at ≈1:05:47), "me design" → mechanism design, and
  "binary" → "binary search" at ≈1:03:27 (word supplied, listed). Speaker turns from ≈1:12:05 to
  ≈1:15:55 rest on the captions' `>>` marks and are flagged on the wiki page.
- **Wiki.** 114 quoted spans swept by script against the edited transcript (timestamp markers
  stripped). The only non-matches are the two schedule titles, which come from the site. Three
  paraphrases inside quote marks were fixed before commit. Fixed on re-read: "I think 2010" is Koyejo
  answering a student's question about the year, not the student's estimate; "overdiagnosis" is
  Koyejo's word, not a student's; an unsupported "time did not allow the planned example" was removed;
  "the most accurate model" was changed to "the first model", since model 3's accuracy is not read
  out. The lecture does not give the formula for the threshold $\delta = g(A)$; a student guesses
  "A1 over A1 plus A2", which Koyejo calls "very close". The page says the formula is not given and
  supplies none. The captioned "TP and TN" summing to $P(y = 1)$ (≈48:04) is noted as inconsistent
  with the lecture's own definitions (≈36:13–36:59), not silently corrected.
