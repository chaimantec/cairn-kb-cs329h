# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–6. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [ ] 07 Voting — video 1QpNZXL35NM (lecture 4 refers back to "the voting lectures"; check whether this is the Oct 7 social-choice session — see BUILD_LOG run 4)
- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

## Run 6 — lecture 6 (2026-11-01)

Scope: lecture 6 only. Slide decks re-checked before starting: fall2024 index (no document links),
`fall2024/slides/`, `cs329h/slides/`, `fall2023/slides/`, `fall2025/slides/`, `fall2026/` (all 404),
fall2023 index (papers only), fall2025 index (no deck links), and the course root, which now carries
an Autumn 2026 offering (no deck links). Still none; transcript-only.

### Transcripts
- [x] 06 Ethics — video -kdR_7dCcyI (verbatim written, 92 paragraphs; the "Not yet built" line moved here)
- [x] 06 edited transcript (Sonnet copy-edit; parent checks: 92/92 markers, numbers identical, ratio 0.65–0.92 by timestamp, eight low outliers read and accepted)

### Crawl
- [x] Re-check course site for a deck (none, as above)
- [x] sources.md lecture-6 video row, Autumn 2026 row

### Wiki
- [x] wiki/06-ethics.md (320 quoted spans swept; non-matches are the schedule title, captioned forms and one nested-quote span)
- [x] Topic pages: new wiki/value-alignment.md; updated, with Sources-so-far lines: whose-preferences, reward-hacking, preference-queries; cross-links from lectures 1 and 5 and human-ai-interaction
- [x] INDEX.md — coverage note, lecture 6 entry, topic list (new value-alignment entry; reward-hacking, preference-queries, whose-preferences lines), not-yet list, numbering note, guest lecturer in the course summary

### Publish
- [x] kb.json — coverage 6/8, 9 topic pages, instructor field, deck note, caveats (partial coverage, Ed-mark count, lecture 6 names and restorations)
- [x] BUILD_LOG.md — lecture 6 record (the Record below, moved with this section)
- [x] AGENTS.md — Autumn 2026 root added to the deck check; guest-lecturer speaker tag
- [x] verify_kb.py clean, and its review section read (hard checks pass, 261 formulas render in chat and on github.com; anchors checked by hand; review: partial-coverage note, which INDEX.md states; open boxes are lectures 7–8 and this run's last steps)
- [x] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 6

- **Catalog ↔ schedule.** Catalog position 6 "Ethics" (video -kdR_7dCcyI, 4261 s) is the Nov 18 row
  "Guest lecture: Daniel Frederick Webber (Stanford)", in the *Value, Alignment, & Human-centered
  Design* module. The date is not spoken. Evidence: the speaker introduces himself (captioned "Dan
  Weber") as a Stanford postdoc in HAI and the Center for Ethics in Society (≈0:05), and Webber is the
  only such row; a student mentions discussing the exercise with "professor Sammy" (≈40:58). Lecture 5
  deferred accountability, fairness, transparency and ethics to "a separate lecture" and matching AI
  decisions to human values to "a couple of lectures from now"; lecture 6 takes up the second and not
  the first, and neither recording says it is the lecture meant. The Nov 13 Bommasani guest lecture
  between them is not in the catalog. The recording ends at ≈1:10:22 (video 1:11:01), partway through
  the ESR risk list.
- **Slides.** None published (re-checked as above; the course root is now the Autumn 2026 offering,
  newly listed in sources.md). He lectures from slides ("My slides aren't working", ≈21:40). On the
  slides, not fully in the audio: the 2020 Jason Gabriel work he quotes (≈11:39), the list of goods
  (≈21:40), the character.ai persona screenshots (≈37:08), the ESR template example (≈1:08:51).
  Bostrom's book is described, not named (≈3:07). The wiki names none of them beyond what is spoken.
  The 2024 site links no ESR instructions or templates; the Autumn 2026 page's impact-statement
  requirement belongs to a different offering and was not used.
- **Transcript edit** (Sonnet subagent, 13 tool calls). References: 2024 course site text, textbook
  glossary and chapters (spellings only; the textbook prints none of Bostrom, deontological, Jason
  Gabriel, character.ai, ESR, Ethics and Society Review). The parent re-ran the checks: 92/92 timestamps
  identical and in order; number inventory identical both ways; ratio 0.65–0.92 keyed by timestamp
  (body 12,249 → 10,080 words, 0.823; the lecturer's speech is heavy with "uh", "you know", "sort of").
  Eight paragraphs fell below 0.72 (7:02 0.65, 45:38 0.66, 48:01, 13:11, 33:14, 35:36, 43:17, 44:02 at
  0.71–0.72). Each was diffed word by word against its original and read with both neighbours: the
  drops are filler and collapsed false starts ("it might be that ... it might be that"), plus captioned
  garble moved into `[Ed:]` marks at 45:38; no neighbour exceeds 0.92, so nothing moved across a marker.
  Parent fixes: ≈35:36 "I don't think I'm trying to say" restored to "I don't think, I'm not trying to
  say"; an inserted "figure out" at the start of ≈1:04:13 removed; a residual "Uh," at ≈37:08 removed;
  the header's claim that *deontological* (≈1:00:22, "Dean's logical") rests on sound alone corrected —
  the captions give "deontological" at ≈57:16. A word-level scan for edited words absent from each
  original found no other insertions beyond grammar (subjects, "will", "may", "among"). 4 `[Ed:]` marks,
  45 `*Student:*` turns, speaker tag `*Webber:*`. Restorations accepted: *Bostrom* ← "Bostonramm",
  "Boston" (sound alone); *intention* ← "attention" (≈1:04:13, the student's own word two sentences
  earlier); *ESR* ← "SR" (≈1:07:19); *postdoc*, *ChatGPT*, *accruing*, *co-design*, *tightrope*. Kept as
  captioned: "Dan Weber", "EIS", "Jason Gabriel", "professor Sammy", "scan transmitter room case" (the
  case is not attributed), "of the LLMs" (≈1:00:22). The murderer-at-the-door case is named aloud and
  not attributed.
- **Wiki.** 320 quoted spans on the lecture page swept by script; the sweep caught four misquotes, all
  fixed ("would stop the converting…" for "it was going to stop…", "is going to be a separate question"
  for "it's going to be…", "is going to maybe make" for "that's going to maybe make", and a paraphrase
  in quote marks in the questions table). The remaining non-matches are the schedule title (site text),
  the captioned forms (each confirmed in the verbatim captions) and one span with nested quote marks
  whose words match. The new topic page's 81 spans and every span added to the four updated pages match.
  New topic page *value-alignment* (lectures 1, 5, 6); lecture 6 adds nothing to the rlhf page.
