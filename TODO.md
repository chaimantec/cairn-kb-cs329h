# KB build — CS329H

Open work only. Every run reads this file in full before doing anything and does
only unchecked work. Tick a box the moment its artifact is written, and commit
this file with it. When a run is committed and pushed, move its section verbatim
to [`BUILD_LOG.md`](BUILD_LOG.md): nothing ticked stays here.

## Not yet built

Requested so far: lectures 1–7. Each line below is a lecture in the catalog that no run has
covered yet. Before starting one, re-check the course site for a slide deck (see `AGENTS.md`).

- [ ] 08 Guest Lecture: Joseph Jay Williams — video HFrCySzH9QI

## Run 7 — lecture 7 (2026-11-01)

Scope: lecture 7 only.

### Transcripts
- [x] 07 Voting — video 1QpNZXL35NM (lecture 4 refers back to "the voting lectures"; check whether this is the Oct 7 social-choice session — see BUILD_LOG run 4) — verbatim written, 96 paragraphs. It is not: it is the Dec 2 guest lecture by Colin Megill (Polis)
- [x] 07 edited transcript (Sonnet copy-edit; parent checks: 96/96 markers, numbers identical, ratio 0.57–1.00 by timestamp; 32 paragraphs below 0.72, 3 after removing um/uh, all diffed word by word; two parent fixes)

### Crawl
- [x] Re-check course site for a deck — none: fall2024 index (no document links), fall2024/slides/, cs329h/slides/, fall2023/slides/, fall2025/slides/, fall2026/ (all 404), fall2023 index (papers only), fall2025 index (`slides_NN` labels are unlinked text), course root (Autumn 2026, no deck links); fall2024 site text unchanged since run 6
- [x] sources.md lecture-7 video row

### Wiki
- [x] wiki/07-voting.md (311 quoted spans swept; non-matches are two schedule titles (site text), the captioned forms (each confirmed in the verbatim captions) and three of the page's own labels)
- [x] Topic pages: new wiki/preference-aggregation.md (36 spans swept); updated, with Sources-so-far lines: whose-preferences, preference-queries, value-alignment (all new spans match); stale lecture-7 sentences fixed in mechanism-design and 04-mechanism-design
- [x] INDEX.md — coverage note (plus a no-voting-lecture warning), lecture 7 entry, topic list (new preference-aggregation entry; whose-preferences, preference-queries, value-alignment lines), not-yet list, numbering note, guest lecturer in the course summary

### Publish
- [x] kb.json — coverage 7/8, 10 topic pages, instructor field, deck note, caveats (partial coverage, Ed-mark count and parent fixes, no voting lecture, lecture 7 names and restorations)
- [x] BUILD_LOG.md — lecture 7 record (the Record below, moved with this section); index row added
- [x] verify_kb.py clean, and its review section read (hard checks pass, 262 formulas render in chat and on github.com; anchors checked by hand; review: partial-coverage note, which INDEX.md states; open boxes are lecture 8 and this run's last steps; no sibling KB on disk cites CS329H's coverage)
- [ ] Commit and push
- [ ] Move this run's section to BUILD_LOG.md; TODO.md keeps only open work

### Record — lecture 7

- **Catalog ↔ schedule.** Catalog position 7 "Voting" (video 1QpNZXL35NM, 4408 s) is the Dec 2 row
  "Guest lecture: Colin Megill (Polis)", the last session before the Dec 4 project expo. It is **not**
  the Oct 7 social-choice session that run 4 left open. The date is not spoken. Evidence: the speaker
  introduces himself (captioned "Colin McIll", platform "Polus", ≈0:05); "as per conversations with
  Sanmi and students" (≈2:26); "Thank you so much, Colin" (≈1:12:36); the Anthropic paper "last year"
  and presented "in July of 2023 last year" (≈2:26, ≈36:19). A questioner says "in the class we've
  gone through voting and its robustness in some detail" (≈10:08), so the course's voting lectures came
  earlier; lecture 4 (Oct 28) already referred back to them. The Oct 7 session, and the Nov 20 Domingue
  guest lecture, are not in the catalog. 04-mechanism-design.md and mechanism-design.md said lecture 7
  might settle which session the voting lectures were; both now say it does not. The recording runs to
  ≈1:13:22.
- **Slides.** None; he presents from a browser (the Polis site, a conversation report, articles, a
  GitHub issue, screenshots). Works shown and not fully named: the Anthropic paper (title not read
  out), a DeepMind paper (title partly captioned, ending "democratic liberation"), the Birdwatch
  paper, the article proposing Polis to Twitter, a Community Notes blog post, Polis's paper on
  generalizing Community Notes. The wiki describes them and cites none.
- **Transcript edit** (Sonnet subagent, 19 tool calls). References: 2024 course site text (prints
  "Colin Megill (Polis)" and "Sanmi Koyejo"), textbook glossary and chapters (spellings only; it prints
  Community Notes, Birdwatch, matrix factorization). The parent re-ran the checks: 96/96 timestamps
  identical and in order; number inventory identical both ways (two stutter digits kept: "20, 2013" at
  ≈8:34, "10, 10" at ≈43:17); ratio 0.57–1.00 keyed by timestamp (body 13,542 → 10,426 words, 0.770;
  "um"/"uh" are 7.5% of the captions). 32 paragraphs fell below 0.72; with um/uh removed from the
  original, three (7:48 0.71, 53:19 0.64, 54:05 0.67). No paragraph exceeds 1.00, so no neighbour
  gained words. Every low paragraph was diffed word by word for deleted spans that are not filler or a
  repeat of nearby words; the rest were stutters, false starts ("what would be amenable like what",
  "that were like cluster of groups", "who who are") and restorations. Parent fixes: ≈13:12 the opening
  "it" restored ("it makes one group larger"); ≈8:34 "Discord" returned to the captions' lower-case
  "discord" (consensus amid disagreement, not the product), header entry corrected. 77 `[Ed:]` marks,
  16 `*Student:*`, 25 `*Koyejo:*` and 35 `*Megill:*` turns (speaker tag by the site's spelling).
  Restorations accepted: *Polis* ← "Polus", "PS", "poll", "polls", "polish", "polless" (course site);
  *Megill* ← "McIll" (site); *Sanmi* ← "semi" (site); *Anthropic*, *OpenAI* (correct forms elsewhere in
  the captions); *Claude* ← "cloud" (≈30:10; "Claude's constitution" at ≈44:50); *K-means* ← "Canadians",
  "C means", "Kines" ("K means" at ≈7:02); *Elon* ← "Eli" (≈47:57; "Elon" at ≈45:37, ≈47:10); *topic
  modeling* ← "top modeling" (≈30:56; correct at ≈30:10); *Bluesky*, *Birdwatch*, *matrix
  factorization*, *Uruguay*, *limerick*, *Turing*, *amenable*, *ostensibly*; *DeepMind* ← "de mind"
  (sound alone; listed as such). Kept as captioned: researchers' and authors' names (several
  unclear-marked), "Kevin Roose", "Deb Roy", "Chris Somerfield", "Keith", "Rishi", "Satra", "UNP",
  "Harvey", "Bowling Green", the model names "01" and "40", "Science Po". Koyejo's audience turns are
  inferred; the header lists the least sure; the wiki names him only where secure (≈2:26, ≈10:08,
  ≈28:36 hedged, ≈54:51–≈57:09, ≈1:12:36) and otherwise says "a questioner".
- **Wiki.** 311 quoted spans on the lecture page swept by script, with lectures 1, 4 and 6 as extra
  sources for cross-references. The read-through before the sweep caught three misquotes ("is
  material" for "that's material", a bracketed "want[s]", and a span skipping the transcript's repeated
  "what the paper"), one ranking claim about the Ed-mark count, and a Koyejo attribution at ≈28:36 that
  needed hedging. The remaining non-matches are two schedule titles (site text), the captioned forms
  (each confirmed in the verbatim captions) and three of the page's own labels. The page writes the vote
  matrix entries as $v_{ij}$ and says the notation is the page's, not the lecture's. New topic page
  *preference-aggregation* (lectures 1, 2, 4–7; 36 spans, one non-match, the schedule title). It opens by
  stating that the course's voting and social-choice lectures are not in the KB; INDEX.md carries the
  same warning. A kb.json caveat drafted as "the most garbled captions in the KB so far" was rewritten as
  the count before commit.
