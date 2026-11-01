# Metric elicitation and inverse decision theory

Metric elicitation asks people which outcomes they prefer, and uses the answers to work out what a
classifier should optimize, when the right measure of success is not obvious. It is the line of work
Koyejo brings to the course from his own research. Inverse decision theory is a related line that
infers the trade-off a decision maker is using, here from their answers about individual examples.

**Sources so far:** [lecture 1](01-introduction.md), which introduces both ideas briefly and refers
the class to the papers (≈1:08:43–1:10:16), and [lecture 3](03-model-based-preference-optimization.md),
which develops metric elicitation for binary classification and sketches inverse decision theory.
Lecture 3 defers a third paper, linking metric elicitation to mechanism design, to a later lecture
(lecture 3, ≈1:20:34). The *Mechanism Design* lecture ([lecture 4](04-mechanism-design.md)) does not
take it up in its recording, so that link is not covered in this knowledge base. Lecture 3 also said
it might use its stakeholder study as an example in the course's HCI lecture (≈1:05:47). The
*Human-centered Design* lecture ([lecture 5](05-human-centered-design.md)) does not mention metric
elicitation.

## The problem it addresses

Many classification problems have no clear metric of success, or have **asymmetric trade-offs**,
where different kinds of error cost different amounts (lecture 1, ≈1:08:43). The standard example is
medicine: a false positive and a false negative do not have the same impact on a patient. A false
positive might mean an incorrect cancer diagnosis (lecture 3, ≈8:29, ≈9:15). Calibrating a learning
problem to the right trade-off "can be tricky" (lecture 1, ≈1:08:43).

Lecture 3 makes the stronger claim that choosing the metric "is actually not a free choice", even
for a binary classifier. "Choices of evaluation or utility functions can be as important as every
other choice that you're making in your model design" (≈15:26, ≈16:12, ≈16:58). For the course,
"reward, utility, metric roughly mean the same thing" (≈17:46). Three models fitted to the same data
show the problem: the first has high accuracy and a 90% false positive rate, and a nearest-neighbour
model with lower accuracy, 89%, brings that rate down to 50. Which is better depends on the setting (≈11:35–13:53).

Metrics are also not exchangeable, and the lecture gives two examples (≈20:03, ≈20:50).

- **The Netflix Prize** scored entries by root mean square error on star ratings, though what
  mattered was getting the top of each user's list right. RMSE "did not necessarily correlate"
  with that, and very simple methods often did better on it than the competition's methods
  (≈22:22–24:40).
- **Recidivism prediction.** The tool's maker built it to a fairness notion based on how risk
  scores compared across demographic groups. ProPublica audited it using differences in false
  positive and false negative rates and reached the opposite conclusion. The case led to the
  **impossibility results in fairness**: roughly, "you can pick one, maybe two measures" to satisfy
  at once, "but you can't pick three" (≈27:43–32:22). See [whose preferences](whose-preferences.md).

The details of both are on the [lecture 3 page](03-model-based-preference-optimization.md#choosing-the-metric-is-not-a-free-choice).

## The idea: find each stakeholder's metric by asking

"There is not a right answer, but perhaps for particular stakeholders there's a right answer for
them" (lecture 3, ≈33:08). Metric elicitation is an algorithmic tool to help stakeholders efficiently
select the metric that best matches their preferences, by getting **pairwise preferences** from
them (lecture 3, ≈33:08; lecture 1, ≈1:08:43). Koyejo relates it to bandits, to inverse reinforcement
learning, and to an older elicitation literature in psychology and econometrics. For this course it
is "this combination of utility estimation with active learning" (lecture 3, ≈33:08, ≈33:55).

Lecture 1 describes the framework as how he brought human preferences into classic machine-learning
problems, related to work in reinforcement learning. The captions garble that RL term ("MSRL";
probably inverse reinforcement learning, unconfirmed) (lecture 1, ≈7:00, ≈7:47).

## How the binary case works

Lecture 3 works through binary classification in the noiseless setting. The steps:

1. **A linear metric is one number.** It weights the two kinds of error,
   $A_1 \cdot \mathrm{FP} + A_2 \cdot \mathrm{FN}$, with $A_1$ and $A_2$ the costs of a false
   positive and a false negative. Scale cannot be recovered and does not matter, so the weights can be
   written $\alpha$ and $1 - \alpha$, and only $\alpha$ is unknown (≈34:41, ≈35:27).
2. **Metrics live on the confusion matrix.** Most classification metrics are functions of the
   confusion matrix of true and false positives and negatives. Linear ones are linear in it,
   $\mathrm{tr}(A^\top C)$ for a weight matrix $A$ and confusion matrix $C$ (≈36:13–38:32, ≈46:32).
3. **The best classifier for a linear metric is a threshold.** With equal weights it predicts one
   when $P(y = 1 \mid x)$ is above one half. With weights it thresholds at some $\delta$, a function of
   $A$ that the lecture leaves to the paper (≈41:40, ≈44:08, ≈51:56).
4. **The reachable confusion matrices form a convex set, bounded by thresholds.** The binary matrix
   has only two degrees of freedom. In true-positive and true-negative coordinates the reachable set
   is effectively an ROC curve, "the Pareto frontier of TP TN as two objectives". Its boundary is
   traced by thresholding the conditional probability (≈47:18–51:10). Mixing two classifiers reaches
   any point between them, so the set is convex (≈1:02:38, ≈1:12:52).
5. **So the search is one-dimensional.** A linear function over a convex set is maximized on the
   boundary. Each weighting then corresponds to one threshold, and the four-dimensional problem
   becomes a search along a one-dimensional boundary (≈54:16–55:48).
6. **Binary search with pairwise questions.** Ask the stakeholder which of two classifiers on the
   boundary they prefer, and move towards the preferred side (≈57:19–58:50). This reaches accuracy
   $\epsilon$ in about $\log(1/\epsilon)$ queries. Koyejo is "pretty sure" that is the lower bound
   without further assumptions (≈1:04:14).

The full derivation, with the formulas as the lecture gives them, is on the
[lecture 3 page](03-model-based-preference-optimization.md#the-best-classifiers-are-thresholds).

**What it assumes.** The search needs preferences along the boundary to be unimodal. That rests on a
"weak uniqueness assumption", connected to rationality: a utility exists, is unique, and is close
enough to a linear weighting of errors. When that fails, the approach breaks (lecture 3, ≈58:50,
≈59:36). Noisy answers need a probabilistic version of the search, and finite data makes the boundary
stepwise. The fix from the ROC literature is to take the convex hull (≈1:01:07–1:02:38).

## Its limits

**The questions are hard to answer.** The oracle (the person answering) has to compare classifiers
at the population level, which "needs a fairly sophisticated stakeholder". Koyejo calls this "one of
the big gaps in this line of work" (lecture 3, ≈1:06:35, ≈1:08:07). One way to help is to ground
the stakeholder with scenarios of what each error means, then relate those to population error
rates (≈1:07:21, ≈1:08:07). Asking about single examples is easier, but needs a metric that depends
on $x$, which is a harder space to search. The group deliberately asked population-level questions
so that the question matched the kind of metric being elicited (≈1:08:54, ≈1:09:41). See
[asking humans for preferences](preference-queries.md#population-level-or-example-level-questions).

**It depends on classification's geometry.** It can be carried over to another Pareto frontier,
such as cost against accuracy, only if a choice on the frontier can be mapped back to a model that
achieves it, and the space has the convexity that makes the search easy (≈1:10:29–1:14:24). When
there are only a handful of models, or a cost that cannot be thresholded, the worked-out theory no
longer applies directly (≈1:15:10, ≈1:15:55).

## Extensions

Lecture 1 lists extensions to fairness problems, to learning from groups of stakeholders, and to
empirical evaluation in real-world settings. The work is valuable, Koyejo says, where individual
stakeholders matter or where trade-offs are tricky and hard to specify (lecture 1, ≈1:09:31). Lecture
3 adds handling noise, multiclass settings, and more complex metrics (≈1:05:01). It also mentions an
applied study with stakeholders, in which eliciting this way "seemed to better reflect their
preferences than some other default approach" (≈1:05:47). The multiclass case is harder. The
confusion matrix's degrees of freedom grow roughly quadratically with the number of classes
(≈48:51). The link to mechanism design is deferred (≈1:20:34), and lecture 4 does not return to it. Nor does
lecture 5, the HCI lecture, return to the stakeholder study.

## Inverse decision theory

Decision theory runs forward: "I have some probabilistic model of the world, I want to come to a
decision" (lecture 1, ≈1:10:16). **Inverse decision theory** runs the other way. From feedback, it
asks what trade-off the decision maker is using. In classification "trade-offs almost always boil
down to thresholds" (≈1:10:16). With a probabilistic model of the outcome, a binary decision is
"yes" when the model's probability clears some threshold $t$:

$$\text{decide yes} \iff P(y = 1 \mid x) \ge t$$

where $x$ is the input and $y \in \lbrace 0, 1 \rbrace$ the outcome. Choosing $t$ is choosing the
trade-off between the two kinds of error, so the inverse problem is to recover it from feedback
(≈1:10:16). Lecture 1 gives no formulas, and this rule only restates in symbols the threshold it
describes. Lecture 3 calls the same threshold $\delta$.

Lecture 3 sketches the method in its last minutes, calling inverse decision theory "a concept in
psychology" (≈1:16:42). The machine has already estimated the conditional probabilities, and the
task is to find the threshold from a few answers (≈1:17:29). Unlike metric elicitation, it asks about
**individual examples**, people's preferences over how specific examples are labelled, instead of
comparing population-level performance (≈1:17:29, ≈1:18:15). It is explicit about noise: noise from a
distribution of stakeholders, from error in the algorithm, and from other uncertainty (≈1:19:01,
≈1:19:48). It replaces binary search with **probabilistic bisection**. A prior over possible
thresholds is updated with each label, and you can prove how long it takes until the probability
around one point is high enough, "greater than half, for instance" (≈1:19:48, ≈1:20:34). Koyejo
offers the analogy that fitting the probability model is like pre-training, and finding the
threshold is like preference tuning (≈1:19:01).

## Related pages

- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md): the
  full treatment.
- [Asking humans for preferences](preference-queries.md): query complexity, and what kind of
  question to ask.
- [Whose preferences](whose-preferences.md): fairness and stakeholder disagreement as reasons to
  elicit at all.
- [Lecture 1 — Introduction](01-introduction.md#beyond-language)
- [Human–AI interaction](human-ai-interaction.md): posing a question a stakeholder can answer, as a
  design problem.
