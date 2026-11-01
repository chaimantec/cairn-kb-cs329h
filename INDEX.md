# CS329H — Machine Learning from Human Preferences (Stanford, Autumn 2024)

CS329H is a Stanford graduate course on capturing human and societal preferences and values in AI
systems, taught by **Sanmi Koyejo** with teaching fellow Sang Truong. It covers how to elicit
preferences from people efficiently and effectively, and how to build them into models. The course
website names three threads: inverse reinforcement learning, metric elicitation, and reinforcement
learning from human feedback. It mixes lectures, invited speakers and student-led paper discussions,
with homework (60%) and a group project (40%).

> **Coverage: lectures 1–4 of 8.** This knowledge base covers **lecture 1 (Introduction)**,
> **lecture 2 (Preference Models)**, **lecture 3 (Model-based Preference Optimization, on metric
> elicitation)** and **lecture 4 (Mechanism Design)** of the eight catalog lectures. Questions about
> later lectures (human-centered design, ethics, voting, and the guest lecture by Joseph Jay
> Williams) **cannot be answered from this KB yet**. Say so rather than answering from the lecture 1 overview, which only
> previews them. Some sessions on the schedule are not in the catalog at all. Lecture 2 defers the
> ideal point model to one of them, and lecture 3 builds on an active-learning lecture (Oct 14)
> that is not in the catalog either. Lecture 4 follows bandit and Bayesian-optimization sessions
> (Oct 21 and 23) that are not in the catalog.
>
> **No slides.** The course has not published its slides for any offering, so this KB is built
> from the lecture transcripts. Pages cite **transcript timestamps** (≈MM:SS), not slide numbers.
> Some papers shown on the slides are not named in the audio. The wiki describes them as the lecture
> does and does not guess the reference.
>
> **Numbering.** Files use the **catalog position** (lecture 1 = `01-…`). The catalog's order does
> not follow the website schedule; for example, the Williams guest lecture is catalog position 8 but
> fell on Oct 30. Lecture 1 is the Sep 23 introduction on the schedule; lecture 2 is most likely the
> Sep 25 "Individual Preference Models" lecture; lecture 3 is the Oct 16 "Model-based Preferences
> Optimization via Preference Elicitation" lecture; lecture 4 is the Oct 28 "Aggregated Preference
> Optimization via Mechanism Design" lecture. Each page gives the evidence.

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
- [Lecture 2 — Preference Models (discrete choice models)](wiki/02-preference-models.md): choice
  models from the ground up. Applications (marketing, route planning, activity sequencing, language)
  and a short history (Thurstone, McFadden, Luce, BART); utility as a deterministic part plus noise,
  and why only orderings are identified; binary choice as logistic or probit regression; the
  two-item logit as logistic regression on feature differences; extreme value, Gaussian and
  correlated noise; multiclass models; pooling versus modelling individuals; Likert scales and the
  ordered logit; rankings and the Plackett–Luce ("exploded logit") model; rationality as
  transitivity; and revealed versus stated preferences. Includes a table of every student question.
- [Lecture 3 — Model-based Preference Optimization (metric elicitation)](wiki/03-model-based-preference-optimization.md):
  choosing a classifier's metric by asking a stakeholder. Why active learning suits preference
  elicitation; asymmetric error costs (the medical example, three models with different error
  rates); why the metric is "not a free choice" (the Netflix Prize and RMSE, the recidivism-prediction
  dispute and the impossibility results in fairness); linear metrics as two weights on false
  positives and false negatives; the confusion matrix and its two degrees of freedom; why optimal
  classifiers for weighted errors are thresholds; the ROC boundary, convexity and the reduction to a
  one-dimensional search; binary search over pairwise comparisons and its $\log(1/\epsilon)$ query
  bound; the gap in posing population-level questions; whether it generalizes beyond
  classification; and a sketch of inverse decision theory with probabilistic bisection. Includes a
  table of every student question.
- [Lecture 4 — Mechanism Design](wiki/04-mechanism-design.md): designing rules so strategic
  participants still produce a desirable outcome, and why that is a way to elicit preferences
  truthfully. Covers where it has had impact (spectrum auctions, web pricing, search ads); preferences
  as the prices people would pay (the coffee-and-cupcake example, non-additive bundle values); who
  decides the desirable outcome (revenue versus welfare); posted prices, pay-your-bid auctions and
  how students would game them; the second-price (Vickrey) auction, reserve prices, and the informal
  proof that bidding truthfully is optimal; incentive compatibility (ex ante, ex interim, ex post)
  and individual rationality; deployed mechanisms that are not incentive compatible (first price,
  generalized second price); Myerson's revenue-maximizing auction with virtual values; learning
  inside mechanisms (regret, learning to bid, prophet and secretary problems); and two applications
  from Koyejo's group, pricing prompt completions with a second-price auction on values predicted
  from pairwise feedback, and a reverse auction that pays data labellers by predicted harm. Includes
  a table of every student question.

Catalog lectures not yet in this KB: 5 Human-centered Design · 6 Ethics · 7 Voting ·
8 Guest Lecture: Joseph Jay Williams.

## Topics

Each topic page gathers one concept across lectures, and says at the top which lectures it draws on.

- [Discrete choice models: utility, noise and the logit family](wiki/discrete-choice-models.md): the
  model (utility = deterministic part + noise), identification only up to ordering, a table mapping
  noise assumptions to models (logit, probit, multiclass, correlated noise, ordered logit,
  Plackett–Luce), fitting them as ordinary machine learning, pooling versus individual models, and the
  assumptions to keep in view. Lectures 1–2.

- [RLHF and the language-model pipeline](wiki/rlhf.md): pre-training, SFT, comparison data and PPO as
  lecture 1 lays them out; why preference collection is best done interactively; reward models
  (what they are mechanically, why separately trained ones don't plug in, DPO and behaviour cloning
  as ways to do without one, and Koyejo's case for keeping them); RLAIF; why academia does less of
  this than industry; the comparison step as a choice model, reward as utility, and language-model
  preference data as stated preferences (lecture 2); reward, utility and metric as one object, and
  why query counts are unknown for RLHF (lecture 3); pricing prompt completions and paying labellers
  with preference-driven auctions (lecture 4).
- [Asking humans for preferences: queries, comparisons and noise](wiki/preference-queries.md): query
  efficiency; explicit versus implicit preference signals; absolute ratings versus pairwise
  comparisons (the exoskeleton result); ratings and rankings and the models for each; dueling
  bandits; active learning and query complexity (with metric elicitation's $\log(1/\epsilon)$
  bound); one-shot versus interactive collection; population-level versus example-level questions;
  revealed versus stated preferences; human inconsistency, Bernoulli models, rationality as
  transitivity, the uniqueness assumption behind binary search, and the rational-human assumption;
  prices as revealed preferences, strategic answerers and incentive compatibility (lecture 4).
  Lectures 1–4.
- [Mechanism design: auctions, incentives and truthful elicitation](wiki/mechanism-design.md): the
  vocabulary (types, allocation, payments, revenue, utility), incentive compatibility at three levels
  of information and individual rationality, a table comparing posted prices, first- and
  second-price auctions, reserve prices, Myerson's auction and generalized second price, learning
  inside mechanisms, and the two preference-driven mechanisms from lecture 4. Lectures 1, 3 and 4
  (lecture 4 is the main source).
- [Reward hacking](wiki/reward-hacking.md): the boat game-playing agent, length and bullet-point bias in
  chatbots, and over-optimizing against a learned reward model.
- [Metric elicitation and inverse decision theory](wiki/metric-elicitation.md): using pairwise
  preferences to set a classifier's trade-offs when errors have asymmetric costs. Covers why the
  metric matters (Netflix Prize, recidivism prediction), the six steps of the binary-classification
  method from linear metrics to binary search, its assumptions and limits, the extensions, and
  inverse decision theory (inferring a decision threshold from answers about individual examples,
  with probabilistic bisection). Lectures 1 and 3.
- [Whose preferences: representation, labour and ethics](wiki/whose-preferences.md): choosing which
  humans to ask; aggregation and strategic agents; representative sampling; one shared utility
  versus one per person; the Pew-survey finding that language models reflect Californian opinions;
  the ethics of outsourced preference labelling; fairness measures that disagree (the
  recidivism-prediction case) and the impossibility results in fairness; who decides a mechanism's
  goal, and paying labellers by harm (lecture 4). Lectures 1–4.

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
