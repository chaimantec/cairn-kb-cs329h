# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–4. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [x] 04 Mechanism Design — video zkHTbb-0Gns (run 4)
- [ ] 05 Human-centered Design — video VffFArrRSBE
- [ ] 06 Ethics — video -kdR_7dCcyI
- [ ] 07 Voting — video 1QpNZXL35NM
- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

## Run 4 — lecture 4 (2026-11-01)

Scope: lecture 4 only. Slide decks re-checked before starting: fall2024 index (no document links),
`fall2024/slides/` and `cs329h/slides/` (both 404), fall2023 index (papers only) and fall2025 index
(no deck links). Still none; transcript-only.

### Transcripts
- [x] 04 Mechanism Design — video zkHTbb-0Gns (verbatim written, 106 paragraphs; ticks the "Not yet built" line)
- [x] 04 edited transcript (Sonnet copy-edit; parent checks: markers, numbers, ratio by timestamp)

### Crawl
- [x] Re-check course site for a deck (none)
- [x] sources.md lecture-4 video row

### Wiki
- [x] wiki/04-mechanism-design.md
- [x] Topic pages: new wiki/mechanism-design.md; updated, with Sources-so-far lines: preference-queries (prices as revealed preferences, strategic answerers), whose-preferences (who decides a mechanism's goal, paying labellers by harm), rlhf (pricing completions, labelling), metric-elicitation (lecture 4 does not take up the deferred paper)
- [x] INDEX.md — coverage note, lecture 4 entry, topic list, not-yet list, numbering note

### Publish
- [x] kb.json — coverage 4/8, caveats
- [x] BUILD_LOG.md — lecture 4 record (the Record below, moved with this section)
- [x] AGENTS.md — lesson: a doubled word is not always a stutter; a term restored from sound alone says so
- [x] verify_kb.py clean, and its review section read (hard checks pass, 261 formulas render in chat and on github.com; review: partial-coverage note, which INDEX.md states; open boxes are lectures 5–8 and this run's last steps)
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 4

- **Catalog ↔ schedule.** Catalog position 4 "Mechanism Design" (video zkHTbb-0Gns, 4910 s) is the
  Oct 28 row "Lecture: Aggregated Preference Optimization via Mechanism Design". The date is not
  spoken. Evidence: "next lecture we have an invited lecture by Joseph Jay Williams" (≈1:20:40), the
  Oct 30 row; regret covered in work "that we did last lecture" (≈55:48, name garbled) and "over the
  past couple of lectures" (≈57:19), matching Oct 21 (dueling bandits) and Oct 23 (Bayesian
  optimization), neither in the catalog; an in-class pairwise exercise "last lecture" (≈1:10:40);
  lecture 3 put mechanism design "quite a bit later". The lecture refers back to "the voting
  lectures" and to incentive compatibility "covered in social choice briefly" (≈0:05, ≈28:42), so a
  social-choice session preceded it; Oct 7 is the candidate, and whether catalog lecture 7 *Voting*
  records it is left for that lecture's run.
- **Slides.** None published (re-checked as above). The revenue figures (≈5:30) come from a
  colleague's talk, history references (≈4:43) and the two closing applications' papers (Koyejo's
  group) are on the slides only; none is named on the wiki. The reading list was not re-read this
  run; the wiki cites no paper from it. The deferred metric-elicitation/mechanism-design paper from
  lecture 3 is not taken up in this recording; metric-elicitation.md now says so.
- **Transcript edit** (Sonnet subagent, 22 tool calls). References: course site text, textbook
  glossary, and the textbook's mechanism-design section (§5.10), for spellings only. The agent
  reported clean checks; the parent re-ran them: 106/106 timestamps identical and in order; number
  inventory identical in both directions; every paragraph within 0.74–0.97 keyed by timestamp (body
  13,374 → 12,091 words outside `[Ed:]` marks, 0.904). Parent fixes: "running error" → "rounding
  error" (≈6:17); at ≈10:55 the agent had collapsed the captions' "not not super kind of obvious" to
  "not", which may flip the sentence, now `[Ed: unclear]`; at ≈9:24 a garbled restatement the agent
  put in Koyejo's turn was moved back into the student's (by content; the captions' `>>` marks are
  inconsistent there); "Ellen" (≈1:20:40) marked unclear. Header notes added: Vickrey and Myerson
  spelled as in the textbook; *prophet inequality* and *secretary problems* restored from "profit
  inequality" and "sector problems" and the lecturer's descriptions, with no course document
  printing either (accepted, and the wiki gives the captioned forms); names kept as captioned
  ("Heritz", "Ellen", "Ruffgarden", "Vansky"), consistent with lecture 3's "North Point"; uncertain
  speaker turns at ≈9:24 and ≈1:13:44–1:14:31. 37 `[Ed:]` marks. Accepted as made: "physicious" →
  malicious, "victory auction" → Vickrey auction, "Meerson"/"what my showed" → Myerson, "patients"
  → payments (revenue is the sum of payments, ≈27:09), "x anti-"/"expost" → ex ante/ex post IC,
  "IP user" → i-th user, "geni" → GenAI.
- **Wiki.** 152 quoted spans on the lecture page swept by script against the edited transcript
  (markers stripped); the only non-matches are the two schedule titles, one nested quotation, and two
  names inside `[Ed:]` marks. All quoted spans added to topic pages match. Fixed on re-read: three
  paraphrases inside quote marks; a timestamp slip (≈19:55 for ≈1:19:55); a sentence asserting the
  garbled "illustration" at ≈1:00:29 was "elicitation" (lecture 3's precedent, but a guess here), now
  given as captioned; "an incentive to overstate" → the lecture's "some incentive to be strategic";
  "most of the literature" → "many framings"; the comparison table's IC column for reserve price and
  generalized second price, which the lecture does not assess. Not supplied: the virtual-value
  formula, which is not read out. "150 and 350" are read as \$1.50 and \$3.50 because he adds them
  to five; the page says it is a reading.
