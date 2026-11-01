# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Run 8 — lecture 8 (2026-11-01)

Scope: lecture 8 only. With it, all eight catalog lectures are covered.

### Transcripts
- [x] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI — verbatim written, 92 paragraphs (catalog 4241 s)
- [x] 08 edited transcript (Sonnet copy-edit; parent checks: 92/92 markers, numbers identical, ratio 0.90–1.05 by timestamp; um/uh only 0.5% of the captions, so every paragraph was diffed word by word; two parent fixes)

### Crawl
- [x] Re-check course site for a deck — none: fall2024 index (no document links), fall2024/slides/, cs329h/slides/, fall2023/slides/, fall2025/slides/ (all 404), course root (no deck links). The fall2024 schedule prints "Oct 30 Guest lecture: Joseph Jay Williams (University of Torronto)" [sic]
- [x] sources.md lecture-8 video row

### Wiki
- [x] wiki/08-guest-lecture-joseph-jay-williams.md (237 quoted spans swept; non-matches are the schedule title (site text), the captioned forms (each confirmed in the verbatim captions) and two of the page's own labels)
- [x] Topic pages: new wiki/bandits-and-adaptive-experiments.md (31 spans; non-matches are two schedule titles); updated with Sources-so-far lines and new material: preference-queries, preference-aggregation, whose-preferences, human-ai-interaction (all new spans match after one fix); stale "not yet in this KB" sentences fixed in 04-mechanism-design, mechanism-design, preference-queries, and older ones found by grep in discrete-choice-models, rlhf, human-ai-interaction
- [x] INDEX.md — coverage note (all 8 catalog lectures, plus a no-bandit-lecture warning), lecture 8 entry, topic list (new bandits entry; preference-aggregation, preference-queries, human-ai-interaction, whose-preferences lines), not-yet list, numbering note, guest lecturer in the course summary

### Publish
- [x] kb.json — coverage 8/8, 11 topic pages, instructor field, deck note, caveats (coverage rewritten as the missing schedule sessions, Ed-mark count and parent fix, lecture 8 restorations and figures)
- [x] BUILD_LOG.md — lecture 8 record (the Record below, moved with this section); index row added
- [x] verify_kb.py clean, and its review section read (hard checks pass, 289 formulas render in chat and on github.com; anchors checked by script, 0 bad; review: only this run's open boxes)
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 8

- **Catalog ↔ schedule.** Catalog position 8 "Guest Lecture: Joseph Jay Williams" (video HFrCySzH9QI,
  4241 s) is the Oct 30 row "Guest lecture: Joseph Jay Williams (University of Torronto)" [sic]. The
  date is not spoken. Evidence: lecture 4 (Oct 28) closes "next lecture we have an invited lecture by
  Joseph Jay Williams" (lecture 4, ≈1:20:40); the speaker calls himself "Joseph" in imagined exchanges
  (≈6:12, ≈17:00, ≈1:05:48, ≈1:06:37) and dates his work "From 2012 to 2024" (≈3:56). The title names
  the speaker, and his self-references and topic (A/B testing, as lecture 4 previewed) agree. There is
  no host introduction; the recording ends at ≈1:10:35. No turn is securely the instructor's, so the
  transcript has no *Koyejo:* tags and the wiki says "a questioner".
- **Slides.** He presents from slides; none published. Works shown and not named in the audio: the
  CHI 2023 stress-message paper (authors garbled), AB Scribe (author garbled), "small steps SMS", the
  self-reflection prompts paper, the stories paper ("in csw"), the LLM story-adaptation paper, the LLM
  thought-partner tool, the minority/contextual-bandit study, the adaptive Epsilon Thompson sampling
  paper. "Rob Willer" is kept as captioned. The wiki describes them and cites none.
- **Transcript edit** (Sonnet subagent, 21 tool calls, about 11 minutes). References: 2024 course site
  text, textbook glossary, and the textbook PDF's text layer (spellings only). The parent re-ran the
  checks: 92/92 timestamps identical and in order; number inventory identical both ways (slips kept as
  captioned: "7030", "2080", "6535", "8%" for 80%, "7%" for 70%, "133%"); ratio 0.90–1.05 keyed by
  timestamp (body 12,816 → 12,724 words, counting words inside `[Ed:]` marks). These captions carry
  almost no filler ("um"/"uh" are 0.5% of the words, against 7.5% in lecture 7), so the ratio is no
  guide here; every paragraph was diffed word by word instead. Deletions were stutters and false starts
  ("so what's my i mean", "have have changed", "think of what do i", repeated "like") and restorations;
  insertions were function words ("of the", "are", "it"). Parent fixes: ≈41:52 one "hippo" the agent
  added was removed (the captions have four); the header said *Kahneman* and *Bernoulli* were restored
  from sound alone, but the textbook prints both, so those entries were corrected. 163 `[Ed:]` marks,
  22 `*Student:*` and 22 `*Williams:*` turns. Restorations accepted: *AdapComp(s)* ← "adap comp",
  "adab comp", "Adcom", "ADC", "Arab comp" (sound alone; the captions' most frequent form is "adap
  comp", and the wiki gives the captioned forms); *AB Scribe*; *Thompson sampling* and *Epsilon
  Thompson sampling* (captions and textbook); *algorithm-induced test statistic* (captions give
  "algorithm induced test statistic" at ≈55:48 and ≈1:04:15); *Wald*, *inverse probability weighting*,
  *CHI*, *Trinidad and Tobago*, *Khan Academy*, *ChatGPT*, *Berkeley* (sound alone, listed as such).
  Kept as captioned: the adaptive algorithm's name ("TS positive", "TS postive", "TS postf",
  "Thompson sampling posst"), the audience names "Ron"/"Ronnie", "Rob Willer", "csw".
- **Wiki.** 237 quoted spans on the lecture page swept by script, with lecture 4's transcript as an
  extra source. The read-through before the sweep caught: a bracketed "make[s]"; a quote elided with "…"
  (replaced by the full question); "is also called posterior sampling" for "It's also called…"; a
  three-part process the lecture gives as two parts; a power table headed "with the algorithm-induced
  test" when the recording does not say which analysis the 46% uses (plain Thompson sampling under that
  test has power 17%); an example the speaker abandoned mid-sentence (yoga); "explain what they learned"
  for "explain what they thought they'd learn"; a "gentler" North American response where the subject of
  "much harsher" is garbled; and a misread remark about CHI. Remaining non-matches: the schedule title
  (site text), captioned forms (confirmed in the verbatim captions), two of the page's own labels. The
  inconsistent false-positive figures for Thompson sampling (15%, 13%, captioned "30%" and "133%") are
  reported as said, not reconciled. New topic page *bandits-and-adaptive-experiments* (lectures 1, 3, 4,
  8), opening with the warning that the course's own dueling-bandit and Bayesian-optimization lectures
  are not in the KB; INDEX.md carries the same warning. One misquote on preference-queries ("could
  represent that" for "could you represent that") was fixed by the sweep.
- **Stale coverage sentences from earlier runs.** A grep for "not yet in this" found three pages still
  claiming later lectures were missing although no run since had added to them: discrete-choice-models
  (stale since run 3, including "the catalog's next lecture … is not yet in this knowledge base"), rlhf
  and human-ai-interaction (since run 6). Each now states which lectures it draws on.
