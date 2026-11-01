# CS329H — Machine Learning from Human Preferences (Stanford, Autumn 2024)

CS329H is a Stanford graduate course on capturing human and societal preferences and values in AI
systems, taught by **Sanmi Koyejo** with teaching fellow Sang Truong. It covers how to elicit
preferences from people efficiently and effectively, and how to build them into models. The course
website names three threads: inverse reinforcement learning, metric elicitation, and reinforcement
learning from human feedback. It mixes lectures, invited speakers and student-led paper discussions,
with homework (60%) and a group project (40%).

> **Coverage: lecture 1 of 8.** This knowledge base covers only **lecture 1 (Introduction)** of the
> eight catalog lectures. Questions about later lectures (preference models, model-based preference
> optimization, mechanism design, human-centered design, ethics, voting, and the guest lecture by
> Joseph Jay Williams) **cannot be answered from this KB yet**. Say so rather than answering from
> the lecture 1 overview, which only previews them.
>
> **No slides.** The course has not published its slides for any offering, so this KB is built
> from the lecture transcripts. Pages cite **transcript timestamps** (≈MM:SS), not slide numbers.
> Some papers shown on the slides are not named in the audio. The wiki describes them as the lecture
> does and does not guess the reference.
>
> **Numbering.** Files use the **catalog position** (lecture 1 = `01-…`). The catalog's order does
> not follow the website schedule; for example, the Williams guest lecture is catalog position 8 but
> fell on Oct 30. Lecture 1 is the Sep 23 introduction on the schedule.

## Lectures

- [Lecture 1 — Introduction](wiki/01-introduction.md): what "learning from human preferences" means
  in this course (efficient, effective, explicit and often interactive elicitation, as opposed to the
  sense in which all ML learns from humans); course logistics, prerequisites and modules; the RLHF
  pipeline for language models; a long student discussion of whether reward models are needed (DPO,
  RewardBench, o1-style sampling, hackability); four reasons to learn from preferences; what still
  goes wrong (length and bullet bias, reward hacking, labelling labour, models reflecting
  Californian opinions on the Pew survey); applications beyond language (a comparison-tuned
  exoskeleton, metric elicitation, inverse decision theory, recommender systems and the Netflix
  Prize, RL from demonstrations); and the rational-human assumption the course starts from.
  Includes a table of every student question.

Catalog lectures not yet in this KB: 2 Preference Models · 3 Model-based Preference Optimization ·
4 Mechanism Design · 5 Human-centered Design · 6 Ethics · 7 Voting · 8 Guest Lecture: Joseph Jay
Williams.

## Topics

Each topic page gathers one concept across lectures. All currently draw on lecture 1 only, and each
says so at the top.

- [RLHF and the language-model pipeline](wiki/rlhf.md): pre-training, SFT, comparison data and PPO as
  lecture 1 lays them out; why preference collection is best done interactively; reward models
  (what they are mechanically, why separately trained ones don't plug in, DPO and behaviour cloning
  as ways to do without one, and Koyejo's case for keeping them); RLAIF; why academia does less of
  this than industry.
- [Asking humans for preferences: queries, comparisons and noise](wiki/preference-queries.md): query
  efficiency; explicit versus implicit preference signals; absolute ratings versus pairwise
  comparisons (the exoskeleton result); dueling bandits; one-shot versus interactive collection;
  human inconsistency, Bernoulli models, and the rational-human assumption.
- [Reward hacking](wiki/reward-hacking.md): the boat game-playing agent, length and bullet-point bias in
  chatbots, and over-optimizing against a learned reward model.
- [Metric elicitation and inverse decision theory](wiki/metric-elicitation.md): using pairwise
  preferences to set a classifier's trade-offs when errors have asymmetric costs; inferring a decision
  threshold from feedback.
- [Whose preferences: representation, labour and ethics](wiki/whose-preferences.md): choosing which
  humans to ask; aggregation and strategic agents; representative sampling; the Pew-survey finding
  that language models reflect Californian opinions; the ethics of outsourced preference labelling.

## Raw materials

- [`raw/transcripts/`](raw/transcripts/): one transcript per lecture, `[MM:SS]`-marked. **Read these
  edited transcripts**, which are copy-edited for punctuation and mis-heard terms. Each lists its
  restorations and marks unclear passages `[Ed: …]` in its header. The verbatim auto-captions are
  in [`raw/transcripts/original/`](raw/transcripts/original/), for checking exactly what was said.
- [`sources.md`](sources.md): the course website, the reading list, the course textbook, and the
  lecture videos, with canonical URLs. It also explains why the online textbook
  ([mlhp.stanford.edu](https://mlhp.stanford.edu/)) is linked but not used as a source: it is a
  2025–26 revision, not the text the 2024 lectures used.
- There is no `raw/slides/` content and no `raw/images/`: the course publishes no slides.

## Related knowledge bases

[`SEE_ALSO.md`](SEE_ALSO.md) lists the Cairn KBs for CS224N, CS224R and CS336. They derive and
implement the RLHF, DPO and reward-model machinery that CS329H's lecture 1 only surveys. Use them for
"how does it work mathematically" questions, and say that the answer comes from another course.

## Licence

See [`LICENSE.md`](LICENSE.md). The explanatory writing is CC BY 4.0; the lecture content and
transcripts are not offered under that licence.
