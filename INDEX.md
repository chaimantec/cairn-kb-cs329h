# CS329H — Machine Learning from Human Preferences (Stanford, Autumn 2024)

CS329H is a Stanford graduate course on capturing human and societal preferences and values in AI
systems, taught by **Sanmi Koyejo** with teaching fellow Sang Truong. It covers how to elicit
preferences from people efficiently and effectively, and how to build them into models. The course
website names three threads: inverse reinforcement learning, metric elicitation, and reinforcement
learning from human feedback. It mixes lectures, invited speakers and student-led paper discussions,
with homework (60%) and a group project (40%). Lecture 6 is a guest lecture by the philosopher Daniel
Frederick Webber, lecture 7 one by Colin Megill of Polis, an open source platform for mapping
public opinion, and lecture 8 one by Joseph Jay Williams on adaptive experimentation.

> **Coverage: all 8 catalog lectures.** This knowledge base covers **lecture 1 (Introduction)**,
> **lecture 2 (Preference Models)**, **lecture 3 (Model-based Preference Optimization, on metric
> elicitation)**, **lecture 4 (Mechanism Design)**, **lecture 5 (Human-centered Design)**,
> **lecture 6 (Ethics, a guest lecture on value alignment)**, **lecture 7 (Voting, a guest lecture
> on Polis and Community Notes)** and **lecture 8 (a guest lecture by Joseph Jay Williams on adaptive
> experiments and Thompson sampling)**. The catalog holds 8 of the course's sessions, not the whole
> schedule. The missing sessions that the lectures refer to are named below; they are not in this KB.
>
> **No voting lecture.** Despite its catalog title, lecture 7 is not the course's lecture on voting.
> The course's voting and social-choice lectures (lecture 4 refers back to them) are not in the
> catalog, so this KB has **no account of voting rules or social choice theory as the course taught
> them**. Say so when asked; [preference aggregation](wiki/preference-aggregation.md) collects what
> the other lectures say. Some sessions on the schedule are not in the catalog at all. Lecture 2 defers the
> ideal point model to one of them, and lecture 3 builds on an active-learning lecture (Oct 14)
> that is not in the catalog either. Lecture 4 follows bandit and Bayesian-optimization sessions
> (Oct 21 and 23) that are not in the catalog, so the KB has **no account of dueling bandits or Bayesian
> optimization as the course taught them**. Lecture 8, a guest lecture, is its only worked treatment
> of a bandit algorithm (Thompson sampling on two arms with yes-or-no rewards); see
> [bandits and adaptive experiments](wiki/bandits-and-adaptive-experiments.md).
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
> Optimization via Mechanism Design" lecture; lecture 5 is the Nov 11 "Human-centered Design" lecture;
> lecture 6, titled *Ethics* in the catalog, is the Nov 18 guest lecture by Daniel Frederick Webber;
> lecture 7, titled *Voting* in the catalog, is the Dec 2 guest lecture by Colin Megill (Polis);
> lecture 8 is the Oct 30 guest lecture by Joseph Jay Williams. Each page gives the evidence.

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
- [Lecture 5 — Human-centered Design](wiki/05-human-centered-design.md): what it takes for AI tools
  to work for people, with HCI as the frame around the course's technical methods. Covers HCI and the
  Norman door (bad design, not bad users), prompting as the AI version of a confusing door, technology
  that "disappears", the interface arc from punch cards to GUIs and from code to prompting to chat,
  technology-centric versus user-centric design (and supervised fine-tuning and preference tuning as
  a fix for an interface problem), design thinking (five whys, Henry Ford's faster horses, the double
  diamond's discover, define, develop and deliver stages), human–AI interaction as a field and the
  design, enable and evaluate steps (the course's tools sit in "enable"), prompt engineering as an
  interface problem, the PromptCharm example of a hybrid interface for image prompts, trust and
  reliance (appropriate reliance, over- and underreliance), fairness, accountability, transparency
  (the aspirin and MRI argument) and ethics, human, computer and mixed initiative, and how to evaluate
  human–AI interaction (quantitative versus qualitative, intrinsic versus extrinsic, metrics, what,
  who and when). Includes a table of every student question.

- [Lecture 6 — Ethics (guest lecture: value alignment)](wiki/06-ethics.md): Daniel Frederick
  Webber, a philosopher at Stanford, on what "do what we really want" can mean. Covers the paperclip
  AI and why better instructions, like manual reward functions, miss failure cases; three readings
  centred on the user (what they intend, what they prefer, what is in their best interest) and the
  technical and philosophical problem each brings (implied meaning, inferring preferences from finite
  feedback, disagreement about the good); autonomy and paternalism; the goal of alignment versus the
  training method (revealed preferences and inverse reinforcement learning); a pair exercise on a
  personalized news chatbot (facts versus gossip, echo chambers, conflicting interests, defaults);
  aligning to moral value, with a tour of moral theories (consequentialism, utilitarianism, weighted
  sums, maximin and the transmitter-room case, deontology) and common-sense morality; refusing to act
  as a choice; power seeking; and the one-page ESR (Ethics and Society Review) statement the final
  project requires. Includes a table of every student question.
- [Lecture 7 — Voting (guest lecture: Polis and Community Notes)](wiki/07-voting.md): Colin Megill,
  who has run the open source platform Polis for about 13 years. Despite the catalog title, not a
  lecture on voting rules. Covers how Polis works (participants write statements, others agree,
  disagree or pass; a sparse vote matrix; PCA and K-means to find opinion groups; statements common to
  people who think differently), a county land-bank conversation as a worked example, whether it can
  be gamed (the Uber case in Taiwan, bots, synthetic citizens and experts, identity and the sample),
  the paper with Anthropic on language models in Polis (grounded summarization, topic modelling,
  "scarily good" vote prediction and its risks), deployments, LLM-written group statements (a DeepMind
  paper), OpenAI's grant program and Anthropic's constitution experiment on human values, how
  Community Notes adapted the idea (matrix factorization, notes shown when raters who usually
  disagree both find them helpful, "a collective response system"), open problems (new clustering,
  vote prediction), and a student's challenge to calling Polis "emergent". Includes a table of every
  question.
- [Lecture 8 — Guest Lecture: Joseph Jay Williams (adaptive experiments and Thompson sampling)](wiki/08-guest-lecture-joseph-jay-williams.md):
  the Oct 30 guest lecture on adaptive experimentation for behaviour change. Covers his program's goal
  ("to coach behavior change") and everyday touch points made into experiments ("AdapComps": messages,
  emails, website explanations, LLM answers); the objection that small exchanges lack statistical
  power, and qualitative A/B comparisons with the AB Scribe tool; assigning versions in proportion to
  the probability each is best (weighted randomization); where those probabilities come from
  (statistical models, experts, crowds, a person reading the data); a stress-message experiment with
  first-year programming students; the beta–Bernoulli bandit and Thompson sampling, with worked
  numbers; turning people's beliefs into pseudo-counts and weighting experts, gaming and the "hippo";
  LLMs to simulate people for priors; personalized interventions and why LLM interfaces matter;
  contextual bandits and the statistical minority the average hides; and why he no longer recommends
  plain Thompson sampling (inflated false positives, lost power), with Epsilon Thompson sampling, his
  group's adaptive version, and the algorithm-induced test statistic. Includes a table of every
  question.

Every catalog lecture is now in this KB. The schedule sessions missing from the catalog are listed in
the coverage note above.

## Topics

Each topic page gathers one concept across lectures, and says at the top which lectures it draws on.

- [Preference aggregation: groups, voting and consensus](wiki/preference-aggregation.md): what the
  lectures say about combining many people's preferences, and the warning that the course's own
  voting and social-choice lectures are not in this KB. Covers aggregation as a change of scale
  (lecture 1), one shared utility or many (lecture 2), the passing references to social choice in
  lectures 4 and 5, lecture 6's moral theories as rules for weighing people (sums, weighted sums,
  maximin), Polis and Community Notes as consensus across difference (lecture 7), weighting people's
  beliefs and the "highest paid person's opinion" (lecture 8), a table comparing the approaches, and
  gaming. Lectures 1, 2 and 4–8 (lecture 7 is the main source).
- [Bandits and adaptive experiments](wiki/bandits-and-adaptive-experiments.md): what the KB has on
  bandits, with the warning that the course's own dueling-bandit and Bayesian-optimization lectures are
  not in it. Covers where bandits sit in the course plan (lectures 1, 3, 4), arms, rewards and policies,
  Thompson sampling on a beta–Bernoulli model with worked numbers, priors from people's beliefs,
  contextual bandits for subgroups, what adaptive assignment does to statistical tests (false
  positives, power, Epsilon Thompson sampling, the algorithm-induced test), a table comparing
  assignment policies, and regret (lecture 4). Lectures 1, 3, 4 and 8 (lecture 8 is the main source).

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
  with preference-driven auctions (lecture 4); supervised fine-tuning and preference tuning as a fix
  for an interface problem, and benchmarks versus lived experience (lecture 5).
- [Asking humans for preferences: queries, comparisons and noise](wiki/preference-queries.md): query
  efficiency; explicit versus implicit preference signals; absolute ratings versus pairwise
  comparisons (the exoskeleton result); ratings and rankings and the models for each; dueling
  bandits; active learning and query complexity (with metric elicitation's $\log(1/\epsilon)$
  bound); one-shot versus interactive collection; population-level versus example-level questions;
  revealed versus stated preferences; human inconsistency, Bernoulli models, rationality as
  transitivity, the uniqueness assumption behind binary search, and the rational-human assumption;
  prices as revealed preferences, strategic answerers and incentive compatibility (lecture 4);
  queries as tools for enabling a human–AI interaction, and human preference as an evaluation
  signal (lecture 5); what preference signals can and cannot stand in for, and A-versus-B against
  typed feedback (lecture 6); participants writing the statements others vote on, vote prediction,
  and elicitation at scale (lecture 7); asking for a probability that one option is better, turning it
  into pseudo-counts, and LLMs as stand-ins for setting priors (lecture 8). Lectures 1–8.
- [Mechanism design: auctions, incentives and truthful elicitation](wiki/mechanism-design.md): the
  vocabulary (types, allocation, payments, revenue, utility), incentive compatibility at three levels
  of information and individual rationality, a table comparing posted prices, first- and
  second-price auctions, reserve prices, Myerson's auction and generalized second price, learning
  inside mechanisms, and the two preference-driven mechanisms from lecture 4. Lectures 1, 3 and 4
  (lecture 4 is the main source).
- [Human–AI interaction and human-centered design](wiki/human-ai-interaction.md): why the course
  cares about HCI, technology-centric versus user-centric design, design thinking and the double
  diamond, where the course's preference tools fit (enabling an interaction, between designing and
  evaluating it), posing questions people can answer (metric elicitation, PromptCharm), trust and
  reliance, transparency, and evaluating human–AI systems (how, what, who, when), and why interfaces
  to LLMs matter (AB Scribe, an LLM thought partner). Lectures 1, 3, 5 and 8 (lecture 5 is the main
  source).
- [Value alignment: intentions, preferences, interests and morality](wiki/value-alignment.md): what
  "what we really want" can mean, with a table of the four readings, the problem each brings and where
  the course's preference methods fit; the paperclip AI; paternalism, autonomy and defaults; aligning
  to a moral theory or to common-sense morality; power seeking; why the goal comes before the
  method; and OpenAI's and Anthropic's projects to gather values from the public (lecture 7).
  Lectures 1, 5, 6 and 7 (lecture 6 is the main source).
- [Reward hacking](wiki/reward-hacking.md): the boat game-playing agent, length and bullet-point bias in
  chatbots, over-optimizing against a learned reward model, and the paperclip AI as a specification
  failure, the "same difficulty" as manually specifying a reward function (lecture 6). Lectures 1
  and 6.
- [Metric elicitation and inverse decision theory](wiki/metric-elicitation.md): using pairwise
  preferences to set a classifier's trade-offs when errors have asymmetric costs. Covers why the
  metric matters (Netflix Prize, recidivism prediction), the six steps of the binary-classification
  method from linear metrics to binary search, its assumptions and limits, the extensions, and
  inverse decision theory (inferring a decision threshold from answers about individual examples,
  with probabilistic bisection). Lectures 1 and 3; neither lecture 4 nor lecture 5 takes up the
  material lecture 3 deferred to them.
- [Whose preferences: representation, labour and ethics](wiki/whose-preferences.md): choosing which
  humans to ask; aggregation and strategic agents; representative sampling; one shared utility
  versus one per person; the Pew-survey finding that language models reflect Californian opinions;
  the ethics of outsourced preference labelling; fairness measures that disagree (the
  recidivism-prediction case) and the impossibility results in fairness; who decides a mechanism's
  goal, and paying labellers by harm (lecture 4); designing for some people and leaving others out,
  fairness, accountability (the asylum-translation example), and stakeholder groups as evaluators
  (lecture 5); people other than the user, paternalism and defaults, and the ESR statement's
  questions about whose interests a project represents (lecture 6); who is in the sample, synthetic
  participants, and replacing people with models (lecture 7); the statistical minority whose best option
  is the opposite of the average's (lecture 8). Lectures 1–8.

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
