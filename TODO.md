# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–4. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [x] 05 Human-centered Design — video VffFArrRSBE (run 5)
- [ ] 06 Ethics — video -kdR_7dCcyI
- [ ] 07 Voting — video 1QpNZXL35NM (lecture 4 refers back to "the voting lectures"; check whether this is the Oct 7 social-choice session — see BUILD_LOG run 4)
- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

## Run 5 — lecture 5 (2026-11-01)

Scope: lecture 5 only. Slide decks re-checked before starting: fall2024 index (no document links),
`fall2024/slides/` and `cs329h/slides/` (both 404), fall2023 index (papers only) and fall2025 index
(no deck links). Still none; transcript-only.

### Transcripts
- [x] 05 Human-centered Design — video VffFArrRSBE (verbatim written, 103 paragraphs; ticks the "Not yet built" line)
- [x] 05 edited transcript (Sonnet copy-edit; parent checks: 103/103 markers, numbers identical, ratio 0.72–0.97 by timestamp)

### Crawl
- [x] Re-check course site for a deck (none: 2024 index no document links, both slides/ paths 404, 2023 papers only, 2025 none)
- [x] sources.md lecture-5 video row

### Wiki
- [x] wiki/05-human-centered-design.md (238 quoted spans swept; only the schedule title, from the site, is not in a transcript)
- [x] Topic pages: new wiki/human-ai-interaction.md; updated, with Sources-so-far lines: rlhf (interface remarks), preference-queries (asking as part of a design process), whose-preferences (designing for some people; fairness, accountability, evaluators), metric-elicitation (lecture 5 does not take up the stakeholder study); cross-links from lectures 1 and 3
- [x] INDEX.md — coverage note, lecture 5 entry, topic list (new human-ai-interaction entry; rlhf, preference-queries, whose-preferences, metric-elicitation lines), not-yet list, numbering note

### Publish
- [x] kb.json — coverage 5/8, 8 topic pages, caveats (partial coverage, Ed-mark counts, lecture 5 names and restorations)
- [x] BUILD_LOG.md — lecture 5 record (the Record below, moved with this section)
- [x] AGENTS.md — lesson: sweep every quoted span against the transcripts by script
- [x] verify_kb.py clean, and its review section read (hard checks pass, 261 formulas render in chat and on github.com; review: partial-coverage note, which INDEX.md states; open boxes are lectures 6–8 and this run's last steps)
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 5

- **Catalog ↔ schedule.** Catalog position 5 "Human-centered Design" (video VffFArrRSBE, 4772 s) is the
  Nov 11 row "Lecture: Human-centered Design", which opens the *Value, Alignment, & Human-centered
  Design* module. The date is not spoken. Evidence: the title, which no other session shares; "given
  we're in 2024" (≈4:46); "we're almost done with the course" (≈55:41); lecture 3's "a whole lecture
  on HCI" (lecture 3, ≈1:05:47). Koyejo defers accountability, fairness, transparency and ethics to "a
  separate lecture" (≈57:58), and AI decisions matching human values to "a couple of lectures from
  now" (≈1:05:39). The schedule has no Ethics row (Nov 13 to Dec 2 are guest lectures), so which session
  catalog lecture 6 *Ethics* records is left for that lecture's run. The Nov 4 guest lecture and Nov 6
  discussion are not in the catalog.
- **Slides.** None published (re-checked as above). The slides are built on tutorials by someone the
  captions call "deank" (≈0:05). On the slides, not in the audio: the paper whose figure cartoons
  prompting (≈44:02), the human–AI pair-programming evaluation paper (≈1:12:31), the source of the
  "problem behind a problem" quote (≈32:29) and Norman's book (≈4:00). Named aloud: PromptCharm
  (≈47:55), and the title "interpreting stable diffusion using cross attention", read out by a student
  (≈54:55). The wiki names only what is spoken. The reading list was not re-read; the wiki cites no
  paper from it.
- **Transcript edit** (Sonnet subagent, 22 tool calls). References: course site text, textbook glossary
  and chapters (grep for spellings only; the textbook has no human-centered design section, only
  participatory design in its chapter 4). The agent reported clean checks; the parent re-ran them:
  103/103 timestamps identical and in order; number inventory identical in both directions; every
  paragraph within 0.72–0.97 keyed by timestamp (body 13,877 → 12,507 words outside `[Ed:]` marks,
  0.901). The low end, [11:49] at 0.72, was read against its original and both neighbours: a collapsed
  false start ("as it gets better it makes it easier to think often as it gets uh as it advances") plus
  filler, with both boundaries as captioned. 29 `[Ed:]` marks, 11 `*Student:*` turns. Restorations
  spot-checked against the captions and accepted: *five whys* ("five W's", beside "ask why" and "five
  levels of depth"), *prompt engineering* ("front engineering", once, beside "prompt engineers"),
  *appropriate reliance* ("appropriate lines" once; captioned correctly a sentence earlier),
  *underreliance*, *overreliance*, *participatory design*, *PromptCharm*, *ArtStation*, *cross
  attention*, *Neuralink*. Parent fix: the header said no course document prints any restored term;
  the course site prints "human-centered design". Kept as captioned and marked unclear: "deank",
  "Nielson", "Mark Weezer", "critique", "close hawk", "four cordon", "BLM".
- **Wiki.** 238 quoted spans on the lecture page swept by script against the edited transcripts
  (lectures 1, 3 and 5) and the captions; the only non-match is the schedule title, from the site. The
  sweep caught two misquotes, both fixed ("is sometimes called" for "It's sometimes called"; "start to
  look" for "starts to look"). The new topic page's 38 spans and every span added to the four updated
  topic pages match; three non-matches on those pages predate this run. Fixed on re-read: PromptCharm is
  named aloud, not only on the slide; the reliance figure's "green parts" are stated as on the slide,
  not identified with the appropriate-reliance cells; "stakeholder mapping", not the lecture's phrase,
  became "identifying the different stakeholders"; the topic page's lecture 1 sentence had merged two
  claims; "the quote attributed to Henry Ford" became "Henry Ford's quote", since the lecture does not
  hedge it. Not supplied: the garbled description of the second diamond (≈33:15), and the fifth of the
  "five things" in evaluation, of which the recording names four (≈1:08:42, ≈1:16:21). Lecture 3's two
  forward references to the HCI lecture are not taken up; the lecture 3 and metric-elicitation pages
  now say so.
