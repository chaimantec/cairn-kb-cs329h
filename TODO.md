# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–3. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [ ] 04 Mechanism Design — video zkHTbb-0Gns
- [ ] 05 Human-centered Design — video VffFArrRSBE
- [ ] 06 Ethics — video -kdR_7dCcyI
- [ ] 07 Voting — video 1QpNZXL35NM
- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

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
- [x] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

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
