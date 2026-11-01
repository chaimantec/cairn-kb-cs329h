# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–2. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [ ] 03 Model-based Preference Optimization — video 7i6WsIzZaeo
- [ ] 04 Mechanism Design — video zkHTbb-0Gns
- [ ] 05 Human-centered Design — video VffFArrRSBE
- [ ] 06 Ethics — video -kdR_7dCcyI
- [ ] 07 Voting — video 1QpNZXL35NM
- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

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
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

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
