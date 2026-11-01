# Metric elicitation and inverse decision theory

Metric elicitation asks people which outcomes they prefer, and uses the answers to work out what a
classifier should optimize, when the right measure of success is not obvious. It is the line of work
Koyejo brings to the course from his own research. Inverse decision theory is a related, more recent
line that infers the trade-off a decision maker is using from their decisions.

**Sources so far:** [lecture 1](01-introduction.md) only, which introduces both ideas briefly and
refers the class to the papers for detail (≈1:10:16). Later lectures are not yet in this knowledge
base.

## The problem it addresses

Many classification problems have no clear metric of success, or have **asymmetric trade-offs**,
where different kinds of error cost different amounts (lecture 1, ≈1:08:43). The standard example is
medicine: a false positive and a false negative do not have the same impact on a patient. Calibrating
a learning problem to the right trade-off "can be tricky" (≈1:08:43).

## The approach

Koyejo's group has worked "over a few years now" on getting **pairwise preferences** from humans and
using them to tune a learning model to expert feedback, typically for classification problems
(≈1:08:43, ≈1:09:31). The lecture lists extensions to fairness problems, to learning from groups of
stakeholders, and to empirical evaluation in real-world settings (≈1:09:31). The work is valuable,
he says, where individual stakeholders matter or where trade-offs are tricky and hard to specify
(≈1:09:31).

He describes it as the framework he worked on to bring human preferences into classic
machine-learning problems, related to work in reinforcement learning. The captions garble that RL
term ("MSRL"; probably inverse reinforcement learning, unconfirmed) (≈7:00, ≈7:47).

The course frames this as one of several **query** problems: whether to ask for comparisons or
absolute scores, and how many to ask. See [asking humans for preferences](preference-queries.md).

## Inverse decision theory

Decision theory runs forward: "I have some probabilistic model of the world, I want to come to a
decision" (lecture 1, ≈1:10:16). **Inverse decision theory** runs the other way. From feedback, it
asks what trade-off the decision maker is using. In classification "trade-offs almost always boil
down to thresholds" (≈1:10:16). With a probabilistic model of the outcome, a binary decision is
"yes" when the model's probability clears some threshold $t$:

$$\text{decide yes} \iff P(y = 1 \mid x) \ge t$$

where $x$ is the input and $y \in \lbrace 0, 1 \rbrace$ the outcome. Choosing $t$ is choosing the
trade-off between the two kinds of error, so the inverse problem is to recover it from feedback
(≈1:10:16). The lecture gives no formulas; this rule only restates in symbols the threshold it
describes. Koyejo leaves the details to the papers (≈1:10:16).

## Related pages

- [Asking humans for preferences](preference-queries.md)
- [Whose preferences](whose-preferences.md): fairness and stakeholder disagreement as reasons to
  elicit at all.
- [Lecture 1 — Introduction](01-introduction.md#beyond-language)
