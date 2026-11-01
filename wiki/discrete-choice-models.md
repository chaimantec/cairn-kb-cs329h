# Discrete choice models: utility, noise and the logit family

A discrete choice model predicts which of a finite set of options a person will pick. It assumes
an unobserved **utility** behind each option and fits that utility from observed choices. In this
course these models are the technical foundation for learning from human preferences. Lecture 2
says that once you have them, you have the tools to understand the preference-learning parts of
many modern pipelines, because those pipelines reuse the same ideas
([lecture 2](02-preference-models.md), ≈0:05). This page gathers the models by concept. The lecture
page has the full argument, the student discussion and the history.

**Sources so far:** [lecture 1](01-introduction.md), which names discrete choice as the course's
technical core, and [lecture 2](02-preference-models.md), which builds the models. Later lectures
are not yet in this knowledge base. The course publishes no slides, so the formulas here are
rebuilt from what the lecturer says aloud, in his symbols.

## Where the course places them

Lecture 1 sets the starting assumption. Most of the course assumes "some kind of rational human":
a reward function exists, even when nobody writes it down, and the models are built on it. The
technical core is discrete choice and the parametric models built around it (lecture 1, ≈1:14:55,
≈1:15:40). In the language-model pipeline, the human comparison step is "typically" discrete
choice (lecture 1, ≈37:54); see [RLHF](rlhf.md). Lecture 2 makes the link to reinforcement learning
explicit: "what is called reward" there "is equivalent to what economists might call utility"
(lecture 2, ≈12:25).

## The model

For a sample or individual $n$ choosing among items, the observation is which item was picked. In
the pairwise case $y_{ni}$ is 1 if the person chose item $i$ over item $j$, and 0 otherwise. The
same setup covers picking one of $K$ options (lecture 2, ≈14:43). Features $z$ (also written $x$)
describe the individual, the item and the alternatives. A function $h$ from some chosen class, such
as a linear model with parameters $\beta$, maps them to utility (≈15:29–17:02). The utility is a
deterministic part plus noise:

$$U_{ni} = h(z_{ni}) + \varepsilon_{ni}$$

The probability of choosing $i$ is the probability that its utility beats every alternative's:

$$P(y_{ni} = 1) = P\left(U_{ni} - U_{nj} \gt 0 \text{ for all } j \neq i\right)$$

(≈24:55, ≈34:10). Fitting means estimating the deterministic part. Prediction compares $h$ across
items, "up to noise" (≈21:47, ≈22:34). Two assumptions sit underneath. The options form a finite,
mutually exclusive, collectively exhaustive set (≈33:24). And the true utility is **unobservable**:
it is measured only through preferences "stated or revealed over choices" (≈13:11, ≈13:57). See
[the setup](02-preference-models.md#the-setup-utility-behind-every-choice).

## Only orderings are identified

Adding a constant to every utility, scaling them all, or applying many monotonic transformations
leaves every choice unchanged. So the data carry only "ordering information across alternatives"
and never "a precise value for what U is" (lecture 2, ≈23:21, ≈24:09, ≈25:41). A consequence is
that utility models learned in different contexts cannot generally be compared. Economics and
psychology often impose a normalization, such as a fixed scale and standardized variance, to make
them comparable. The lecture says machine learning rarely does this (≈25:41–27:12). See
[what the data cannot tell you](02-preference-models.md#what-the-data-cannot-tell-you-the-utilitys-scale).

## The noise model picks the classic model

Lecture 2 builds every variant from three ingredients: the function class, the noise distribution
and the range of items (≈50:27). The noise choice decides which classic model you get:

| Options | Noise | Model | Fitted as | ≈ |
| --- | --- | --- | --- | --- |
| Two (choose or not) | logistic | binary logit | logistic regression | 28:00, 28:45 |
| Two (choose or not) | standard normal | binary probit | probit regression | 29:32 |
| Two items | i.i.d. extreme value | logit in the feature difference | logistic regression on $x_n = z_{n1} - z_{n2}$ | 38:05–39:37, 45:04 |
| Up to $J$ | i.i.d. extreme value | multiclass logit | multiclass logistic regression | 50:27 |
| Up to $J$ | Gaussian (probit) | "the Gaussian version of the same thing" | — | 51:14 |
| Up to $J$ | Gaussian with a covariance | correlated-noise model | fit $\beta$ and the noise correlations (statsmodels, R) | 51:14–52:48 |
| Rating scale, 1 to $K$ | — | ordered logit (thresholds) | maximum likelihood, gradient descent | 56:39–58:14 |
| Ranking of $J$ items | extreme value style (or probit, correlated) | Plackett–Luce ("exploded logit") | product of conditional choices | 59:02–1:02:08 |

For two items with i.i.d. extreme value noise and a shared $\beta$, the choice probability is a
logistic function of the feature difference (≈39:37):

$$P(y_{n1} = 1) = \frac{e^{\beta^\top z_{n1}}}{e^{\beta^\top z_{n1}} + e^{\beta^\top z_{n2}}} = \frac{1}{1 + e^{-\beta^\top (z_{n1} - z_{n2})}}$$

The captions garble the second form, so it is reconstructed from the spoken steps. The lecture
points to the multiclass logistic regression derivation as the place students have seen this
before, and warns "we may test stuff like this" (≈40:24). Asked why extreme value noise, the answer
is that "extreme value noise is what gets you logistic regression" (≈46:39).

The lecture names **Bradley–Terry** as a standard choice model alongside Plackett–Luce (≈10:06),
but does not return to it by name in the audio. Its slides may have done so; they are not
published. See [binary choice](02-preference-models.md#binary-choice-is-logistic-regression),
[more than two options](02-preference-models.md#more-than-two-options-and-any-model-class) and
the [ordered logit and Plackett–Luce sections](02-preference-models.md#ordered-responses-likert-scales-and-the-ordered-logit).

## It is ordinary machine learning

The point lecture 2 keeps returning to is that "once you set up the problem and transform things
appropriately, this looks literally like a standard machine learning problem" (≈48:55). Any model
class works: a neural network, a decision tree, an SVM, fitted with stochastic gradient descent in
scikit-learn or PyTorch (≈22:34, ≈53:34, ≈54:19). Every standard concern applies: bias–variance
trade-offs, overfitting, and the need for more data as the function class grows (≈55:07). Whether
the noise model is right is checked the usual way, through goodness of fit on held-out data, with
features, noise model or function class changed if the fit is poor (≈48:09–50:27). The i.i.d. noise
assumption is "probably not reality", but often a reasonable approximation. Correlated noise can be
modelled, for example with a hierarchical model, with the usual trade-off against sample size
(≈41:11–42:44). Koyejo has never seen an
analysis, in machine learning, of what the noise in real preference data looks like (≈47:24).

## Individuals: pool, separate or tie

One utility for everyone, a separate utility per person, or per-person parameters tied together
(additively, or as a low-rank set) are all modelling choices, traded off against sample size
(lecture 2, ≈31:52, ≈32:37). Machine-learning applications almost always pool. Psychology and
economics model individual differences, which machine learning is "slowly understanding" might
matter (≈55:53, ≈56:39). See [whose preferences](whose-preferences.md).

## Assumptions to keep in view

- **Every respondent makes a choice.** A person with no preference does not fit the basic model.
  One fix is to add an explicit **abstain** option, which models "a choice of no choice"
  (≈19:26–20:12, ≈30:18, ≈31:04).
- **Rationality, meaning transitivity.** Preferences are assumed "effectively linearly orderable"
  in expectation, so a cycle such as $a$ over $b$ over $c$ over $a$ cannot happen except through
  noise. When it does appear, richer features may explain it, and other model classes (not covered)
  allow some intransitivity. Whether violations show irrational humans or mis-specified models is
  still debated; the course treats rationality as "a pragmatic modeling choice" (lecture 2,
  ≈1:02:58–1:06:50). See
  [noise, inconsistency and rationality](preference-queries.md#noise-inconsistency-and-rationality).
- **What kind of observation.** Revealed and stated preferences can disagree "like night and day",
  and the kind of data you have affects how complex a model you can fit (≈1:07:36–1:17:39). See
  [revealed versus stated preferences](preference-queries.md#revealed-versus-stated-preferences).

## Not yet in this knowledge base

Lecture 2 defers the **ideal point model** to the next lecture and skips its planned exercises
(≈1:17:39). The schedule's next lecture on individual preference models (Sep 30) is not in the
catalog, and the catalog's next lecture, *Model-based Preference Optimization*, is not yet in this
knowledge base.

## Related pages

- [Lecture 2 — Preference Models](02-preference-models.md)
- [Asking humans for preferences: queries, comparisons and noise](preference-queries.md)
- [RLHF and the language-model pipeline](rlhf.md)
- [Whose preferences](whose-preferences.md)
