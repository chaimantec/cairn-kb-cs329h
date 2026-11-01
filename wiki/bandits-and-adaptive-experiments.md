# Bandits and adaptive experiments

A **bandit** problem, in the form this knowledge base covers, is a repeated choice between options
("arms"). Each choice yields a reward, and the chooser must balance trying options to learn about them
against giving people the one that looks best. An **adaptive experiment** is an A/B test run as a
bandit: who gets which version changes as the evidence comes in. This page collects what the lectures
in this knowledge base say about both.

**Read this first: the course's own bandit lectures are not in this knowledge base.** The schedule has
two sessions on them, Oct 21 "Lecture: Model-free Preference Optimization via Dueling Bandits" and
Oct 23 "Lecture: Model-free Preference Optimization via Bayesian Optimization", and neither is in the
catalog. So there is **no account here of dueling bandits as the course taught them**, nor of Bayesian
optimization. Say so when asked. What the knowledge base has is a guest lecture on adaptive
experimentation by Joseph Jay Williams ([lecture 8](08-guest-lecture-joseph-jay-williams.md)), which
works through a two-arm bandit with **Thompson sampling**. It also has passing references in lectures 1,
3 and 4.

**Sources so far:** [lecture 8](08-guest-lecture-joseph-jay-williams.md) is the main source.
[Lecture 1](01-introduction.md) places bandits in the course plan and previews dueling bandits.
[Lecture 3](03-model-based-preference-optimization.md) relates metric elicitation to bandits.
[Lecture 4](04-mechanism-design.md) measures online learning by regret and uses bandits in one
application.

## Where bandits sit in the course

Lecture 1 puts bandits in the part of the course that learns from preferences "without an explicit
reward model", alongside DPO (lecture 1, ≈50:16). It previews **dueling bandits**, "a way to think
about bandit problems with pairwise preferences explicitly", as a frame for problems like tuning an
exoskeleton from a user's comparisons of two settings (lecture 1, ≈1:07:58). See
[asking humans for preferences](preference-queries.md#absolute-ratings-versus-comparisons).

Lecture 3 relates its query-efficient method for choosing a classifier's metric to bandits: "So we
haven't talked that much about bandits yet but we will" (lecture 3, ≈33:08). It ends by saying a future
lecture covers "bandits and sort of other kinds of algorithmic tools that can help us in preference
learning" (lecture 3, ≈1:22:06). See [metric elicitation](metric-elicitation.md).

Lecture 4 follows the dueling-bandit and Bayesian-optimization sessions on the schedule. It opens by
linking its material to "asking questions about bandits, preference modeling, preference
optimization" (lecture 4, ≈0:52). It also refers back to regret as covered "last lecture" (lecture 4,
≈55:48; see [lecture 4](04-mechanism-design.md) for how the date is inferred).

## The setting: arms, rewards and a policy

Lecture 8 gives the simplest version (≈30:54, ≈31:41). There are two **arms**, for example two
explanations of a concept, A and B. The **reward** is one or zero: the person says they like the
explanation or not, clicks or not, buys or not. A **policy**, or a policy-learning algorithm, decides
what share of people get each arm. Williams calls this "the most fundamental form of reinforcement
learning" (lecture 8, ≈30:54).

The rewards here are yes-or-no outcomes for one arm at a time. They are not the pairwise comparisons
that dueling bandits are built on (lecture 1, ≈1:07:58).

Williams's motivation is that most decisions are all-or-nothing. You send one version of an email to
everyone, or at best split 50/50 in a classic A/B test. He asks instead for weighted randomization:
assign versions "proportionally to the probability we think that they're the best, where best has to be
defined" (lecture 8, ≈13:57). A bandit algorithm is one way to set those probabilities. People are
another (see [below](#probabilities-from-people)).

## Thompson sampling on a beta–Bernoulli model

Each arm gets a **beta distribution** over its unknown probability of a success (a thumbs-up). The
prior $\text{Beta}(1, 1)$ is uniform: "it's like I saw one success, one failure so far" (lecture 8,
≈31:41, ≈32:28). Each reward is a Bernoulli draw with that arm's success probability, and because the
beta is conjugate to it, updating is counting (≈32:28, ≈34:50). Williams's worked example, with the
first parameter counting successes and the second failures (≈33:14):

$$\text{Beta}(1, 1) \to \text{Beta}(1 + 3, 1 + 2) = \text{Beta}(4, 3)$$

for an arm where three of five people said yes, and

$$\text{Beta}(1, 1) \to \text{Beta}(1 + 5, 1 + 0) = \text{Beta}(6, 1)$$

for an arm where all five did. More data at the same ratio leaves the mean where it is and narrows the
distribution: $\text{Beta}(6, 1)$ and $\text{Beta}(60, 10)$ both have mean $6/7$, and the second is "a
much more peaked distribution" (≈34:02, ≈34:50).

**Thompson sampling**, "also called posterior sampling" (≈30:54), chooses an arm by drawing one value
from each arm's beta distribution and assigning the arm with the higher draw (≈35:37, ≈36:24). Repeat
the draw many times, "just do it 10,000 times", and the share of wins estimates the probability that
one arm is better (≈36:24, ≈37:11). Assignment therefore tracks belief: 50/50 under the uniform prior,
and drifting towards the arm that looks better as data comes in. Williams calls it "randomized
probability matching" (≈30:54).

## Probabilities from people

Because assignment comes from beta distributions, lecture 8 suggests letting people supply them.
Someone who thinks A is 70% likely to be better can be asked to express that "as fictional successes
and failures", for instance eight successes and two failures for A against five and five for B
(lecture 8, ≈37:57, ≈38:43). Several people's pseudo-counts can be combined with weights, counting an
expert's "10 times mine" (≈39:30, ≈40:19). A person who reads an experiment's data can give their own
probability that a message is best, to be combined with the model's (≈25:28). Williams wants research on
how people express these beliefs and on tools that help them (≈38:43, ≈39:30). See
[asking humans for preferences](preference-queries.md#asking-for-a-probability-that-one-option-is-better)
and [preference aggregation](preference-aggregation.md#weighing-people-against-each-other).

## Contextual bandits: when the average is wrong for a subgroup

A single bandit learns what works best on average. Lecture 8's example is two messages encouraging
students in an online course to write a question (≈48:02, ≈48:47). The peer-focused message wins on
average, but for the 20% of students who got the previous problem wrong, the self-focused message is
"substantially better" (≈50:20). A **contextual bandit** runs the assignment "separately for the low
accuracy and higher accuracy groups" (≈51:06). The group where the evidence is clear moves towards its
better message. The group where it is not stays near 50/50, "and that not being sure is good because we
collect more data" (≈51:06). Williams reports better outcomes for the minority and higher power to
detect the difference: "Statistical power to detect the best option of minority increased from 87% to
89" (≈52:40). See [whose preferences](whose-preferences.md#the-minority-the-average-hides).

## Reward against inference

The second half of lecture 8 is about what adaptive assignment does to the analysis afterwards.
Williams: "6 years ago I thought, and I run experiments using Thompson sampling, today I would not tell
someone to use that" (≈53:25). The problem is not the reward, it is the inference. A standard **Wald z
test** assumes uniform random assignment (≈55:48, ≈58:53). Under Thompson sampling, an arm that has
an unlucky start gets few further participants, it keeps its low estimate, and the test reports a
difference that is not there (≈59:39, ≈1:00:25). When a real difference exists, too few people reach
the weaker arm to show it, so power falls (≈1:04:15).

His recommendations (≈54:13–1:08:59):

- **Keep some uniform randomization.** Epsilon Thompson sampling assigns uniformly at random with
  probability $\epsilon$, and otherwise uses Thompson sampling. It also protects against a world that
  changes and a minority the majority hides (≈54:13, ≈55:01).
- **Set $\epsilon$ from what counts as a small difference.** His group's adaptive version sets
  $\epsilon$ to the posterior probability that the arm difference is less than a threshold the user
  chooses, such as 0.1. When the arms look close it randomizes more; when that probability is low it
  uses more Thompson sampling (≈1:06:37, ≈1:07:24).
- **Analyse with an algorithm-induced test statistic.** Simulate the test statistic under the
  algorithm actually used, and set the cutoff so that the false positive rate is 5% (≈55:48, ≈56:35,
  ≈1:04:15).

The approaches he compares:

| Assignment | How it assigns | What lecture 8 says |
| --- | --- | --- |
| One version to everyone | 100% to the arm believed best | "That's actually what we all do. We are arrogant, right?" (≈12:24) |
| Uniform random (classic A/B test) | 50/50 | Best power in a two-arm trial: 87% in his example (≈56:35, ≈1:08:12) |
| Thompson sampling | Draw from each arm's posterior, assign the higher | Inflated false positives; power 46% (≈56:35, ≈1:08:12) |
| Epsilon greedy | Not described | "Epsilon greedy is not better" (≈1:01:55) |
| Epsilon Thompson sampling | Uniform with probability $\epsilon$, else Thompson | Power 66% with the algorithm-induced test (≈56:35) |
| Adaptive Epsilon Thompson sampling | $\epsilon$ = posterior probability that the arms differ by less than a chosen amount | Power 82%, false positive rate fixed at 5% (≈1:08:12) |
| Contextual bandit | Separate assignment per subgroup | Better outcomes for a minority; power 87% to 89% (≈52:40) |

Thompson sampling's false positive rate is given differently at different points in the talk (15%,
13%, and figures captioned "30%" and "133%"), and the recording does not say which analysis each power
figure uses; [lecture 8](08-guest-lecture-joseph-jay-williams.md#the-results-he-reports) sets out what
is said where.

## Regret

Lecture 4 measures online learning by **regret**. For a seller learning prices it is "the difference
between the cumulative revenue for the seller versus the best price that they could have gotten in
hindsight" (lecture 4, ≈55:48). A buyer learning to bid competes with "the best fixed bids in
hindsight" (lecture 4, ≈56:33, ≈57:19). Lecture 4's application to pricing prompt completions, which
mixes "some of the online learning bandit things" with mechanism design (lecture 4, ≈1:00:29), reports
lower regret from pairwise feedback than from a uniform allocation (lecture 4, ≈1:19:09, ≈1:19:55). See
[mechanism design](mechanism-design.md).

Lecture 8 does not use the word regret. It speaks of trading off "reward, power and false positive
rate" (lecture 8, ≈1:08:12).

## Related pages

- [Lecture 8 — Guest Lecture: Joseph Jay Williams](08-guest-lecture-joseph-jay-williams.md): the full
  treatment, with the worked numbers and every question.
- [Asking humans for preferences](preference-queries.md): dueling bandits, comparisons, and asking
  people for probabilities.
- [Whose preferences](whose-preferences.md): the subgroup the average hides.
- [Preference aggregation](preference-aggregation.md): weighting several people's beliefs.
- [Mechanism design](mechanism-design.md): regret in online pricing and bidding.
- [Metric elicitation](metric-elicitation.md): another query-efficient, interactive method.
