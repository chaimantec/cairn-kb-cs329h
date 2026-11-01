# Lecture 2 — Preference Models (discrete choice models)

This lecture lays the technical foundation the rest of the course builds on: **discrete choice
models**. Sanmi Koyejo calls it "one of the foundational methods lectures": by the end, a student
should have the tools to understand the human-preference-learning parts of many modern pipelines,
because "many of the models and approaches people use end up reusing many of these ideas" (≈0:05).
The central assumption is that an unobserved **utility** drives people's choices, made up of a
deterministic part and noise. Fitting a choice model means estimating that deterministic part from
observed choices. With the right noise assumption, a binary choice model is **literally logistic
regression** (or probit regression), a choice among several options is multiclass logistic
regression, and rankings and rating scales get their own extensions (the **Plackett–Luce** and
**ordered logit** models). Along the way the lecture asks what the data can and cannot reveal
(only orderings, never the utility's scale), what "rational" means here (transitivity), and how
**revealed** preferences (real choices) differ from **stated** ones (hypothetical answers). About a
third of the lecture is student questions.

**Date.** This is catalog position 2. It most likely corresponds to the **Sep 25** schedule row,
"Lecture: Individual Preference Models", though the recording does not state its date. Three
things point there. Koyejo says he "alluded to" logistics and delivery applications "last time"
(≈3:58), and that logistic regression was "mentioned in the last class" (≈29:32). Both happen in
[lecture 1](01-introduction.md) (≈16:08, ≈16:55). The lecture also opens on choice models, which
is where lecture 1's recording stops. At the end he pushes the "ideal point model" to "next week"
(≈1:17:39), and the schedule has a second "Individual Preference Models" lecture on Sep 30. That
lecture is not in the catalog.

**No slides.** The lecture is given from slides. It refers to them often, and at one point they
need fixing mid-lecture (≈58:14). The course has not published them. So every claim here is cited
to the transcript by timestamp. The historical references and application papers on the slides
are not read out (≈5:29, ≈9:20), and this page does not supply them. The formulas below are
rebuilt from what Koyejo says aloud, using the symbols he names. Where the captions lose part of an
expression, the page says so.

**What is not covered.** The lecture runs out of time. The exercises are skipped, and the ideal
point model is deferred to the next lecture (≈1:17:39). Neither appears in this recording.

[Edited transcript](../raw/transcripts/02-preference-models.md) ·
[verbatim captions](../raw/transcripts/original/02-preference-models.md) ·
[video](https://www.youtube.com/watch?v=-bych9RfQvw) ·
[course website](https://web.stanford.edu/class/cs329h/fall2024/) · [sources](../sources.md) ·
topic page: [discrete choice models](discrete-choice-models.md)

## What a choice model is

Koyejo describes choice modelling as "a set of tools that help one predict choice behavior of
either individuals or a group, generally within a specific context" (≈0:51). As in most machine
learning, the data are observations: an individual or a group of people making choices. The choice
model is "literally what model can I fit to this data set such that, given a new context, I can
predict the choice that people might make" (≈1:36). The lecture concentrates on standard,
"quote-unquote rational" choice models in the **discrete** setting (≈0:51), because finite choices
are the problems the field works on most (≈10:53).

He asks the class to engage with the **assumptions** these models make. He promises to call them
out as he goes, and says critiquing them is part of the course (≈1:36, ≈10:06). Rationality is the
first he flags (≈10:53); the lecture returns to it at the end (see
[rationality](#rationality-means-transitivity)).

## Where choice models are used

The lecture opens with applications (≈1:36–7:00):

- **Marketing.** A car dealership, or a website that compares and sells cars, wants to predict what
  visitors will prefer. As in all learning, it needs features: of the objects (brand, price and
  other information, encodable many ways) and of the decision makers (expressed preferences,
  demographics, previous cars driven). With these it can predict which car a visitor will choose,
  or how they will rank the options (≈2:23, ≈3:10).
- **Transportation and route planning**, "actually a quite popular real-world application" (≈3:10).
  You can model the whole route as one choice among a discrete set of paths, or break it into steps.
  Such models appear in the route-planning algorithms behind mapping services, and even more in
  logistics planning such as delivery. The features can include weather, traffic, whether a user
  will take a longer but faster route or wants the literal shortest path, and cost: fuel, tolls,
  and how much the user is willing to pay (≈3:58, ≈4:43).
- **Energy**, which fits with planning and logistics. The slide lists papers for other
  applications (≈5:29).
- **Activity sequencing.** Plan the order of an individual's activities over a day, some fixed and
  some adjustable, and whether they drive or walk between them (≈5:29, ≈6:14).
- **Language models**, discussed at length in the previous lectures. The same tools model the
  choices of decision makers "typically in this second stage": preferences across documents
  (≈6:14, ≈7:00). See [RLHF](rlhf.md).

## A short history

"Choice modeling has a long history" (≈7:00). The lecture's timeline, as spoken (≈7:00–8:32):

- The earliest recorded work is by **Thurstone**, on food preferences, in the 1920s.
- Some of this work evolved into applications in economics and utility theory in the 1970s. (The
  caption says "macroeconomics".) Some of the work from that period led to the **Nobel Prize in
  2000** for **McFadden**, "on the theoretical basis for discrete choice".
- Psychology built models long ago that are still key tools. The example given is work by **Luce**
  on "qualitative choice behavior", dated 1959. The caption runs together "Luce", "logit analysis"
  and "qualitative choice behavior" in one breath. It may be reading two references off the slide,
  and this page does not try to separate them.
- Marketing: predicting demand for new products, especially when products cost different amounts
  to produce, so that you can plan what to make.
- Transportation: some of the original transportation planning for the **BART** system was work by
  McFadden. It estimated likely preferences across populations to help decide where to put
  stations.

The references are on the slides, "easy to look up" (≈9:20). Koyejo adds that much of the core
technology was defined in the 1940s to 1960s and is still what is used today. He names
**Bradley–Terry** and **Plackett–Luce** as standard choice models from that era (≈10:06). Of the
two, only Plackett–Luce is named again later in the audio (≈59:02).

## The setup: utility behind every choice

The standard recipe asks humans, individuals or groups, to choose among alternatives. It then
featurizes the items and the individuals, and builds a predictive model on top (≈9:20, ≈10:06).

**Featurized or not.** In the classic settings the context is featurized: a set of features for the
item and a set for the user. In many machine-learning applications there is no explicit
featurization. The context might be a sentence or a whole completion, and the model goes "straight
from phrase completions to a prediction of choice" (≈10:53, ≈11:39).

**Utility.** Discrete choice models are designed to capture the decision processes of individuals,
and sometimes groups. They assume there exists some **utility**. You can think of it as benefit or
value, or as **reward**: "what is called reward" in reinforcement learning "is equivalent to what
economists might call utility" (≈12:25). The key assumption links utility to behaviour. The utility
an individual gets from item A versus item B is a function of how often they choose A over B when
given that choice repeatedly (≈12:25, ≈13:11). The true utility is assumed **unobservable**: a
function that fully describes the choices exists, but you do not get to see it. The hope is to
measure it through preferences that are "stated or revealed over choices" (≈13:11, ≈13:57). The
lecture ends on that distinction (see [below](#revealed-versus-stated-preferences)).

### The formal model

For a sample (or individual) $n$ and items $i$ and $j$, what you observe is the choice. In the
pairwise setting the label $y_{ni}$ is 1 if the person chooses $i$ over $j$ and 0 if not. The same
setup handles choosing one of $K$ options (≈14:43). The modelling assumption is that an underlying
utility function generates these choices, stochastically (≈15:29).

The inputs are features, which the lecture writes generically as $z$. They describe the
individual's attributes, and can also describe the option being picked and all the alternatives
(≈15:29, ≈16:16). A function $h$ maps the features to the utility. In standard machine-learning
notation you could write $x$ for $z$: "X is the featurization of the individual and the choices", and "Y is the
label: did they pick A over B?" (≈16:16). You pick a function class for $h$ that seems a reasonable
description of how features drive choices, "a simple example might be say a linear model", with
parameters $\beta$ (≈17:02). For a linear model, $h$ is a weighted combination of the features
with weights $\beta$.

The utility has "a deterministic component and then some noise component", and "my goal in learning
is to estimate the deterministic component" (≈34:10). Writing $\varepsilon_{ni}$ for the noise:

$$U_{ni} = h(z_{ni}) + \varepsilon_{ni}$$

The choice model is the probability of picking alternative $i$ over all others, which is the
probability that its utility is the largest (≈24:09, ≈24:55):

$$P(y_{ni} = 1) = P\left(U_{ni} \gt U_{nj} \text{ for all } j \neq i\right) = P\left(U_{ni} - U_{nj} \gt 0 \text{ for all } j \neq i\right)$$

The second form, moving $U_{nj}$ to the left-hand side, is the one the rest of the lecture uses.
The options are assumed to be a collectively exhaustive, mutually exclusive, finite set (≈33:24).
Koyejo calls this the most general framing the course will give. There are further
generalizations, but "for this class this is as general as we're going to go" (≈34:10).

**What goes in $z$.** A student asks whether $z$ needs an item subscript, or captures only the
individual (≈17:02). In classic choice models, Koyejo answers, $z$ can be "fairly rich": often a
large featurization of the individual, the item *and the alternatives*. "Your choice may be driven
not only by the item that you like but by what else you're comparing it to", so the alternatives
belong in $z$, and the fitted $\beta$ captures how all these features interact to define the
utility and the probability of picking $i$ over $j$ (≈17:51, ≈18:36). On indices, he suggests $n$
for the sample, $i$ and $j$ for items, and perhaps $k$ for the individual. A student points out
that $n$ could stand for the individual. Koyejo agrees: "nothing breaks if you make N individual" (≈18:36).

### Fitting and predicting

Koyejo asks the class what "fit" means here, calling it an "intentionally naive question" (≈21:00).
Given data samples of $z$ and $y$, a student answers: output the probability that $y$ is one, for
example with a linear model from $z$ to $y$ (≈21:00, ≈21:47). Koyejo spells it out:

- **Estimation** is finding a setting for $\beta$. With a linear $h$ that is a linear model; "if I
  make this a neural network, then this whole thing is a neural network model. I just need to fit
  that neural network model" (≈21:47, ≈22:34).
- **Prediction.** A new individual and item fix $z$, so you can compute $h$, the expected value of
  the utility. You then predict the choice "up to noise" by checking whether $h$ for item $i$ is
  bigger than $h$ for item $j$ (≈21:47, ≈22:34).

## What the data cannot tell you: the utility's scale

"It turns out that you don't actually estimate the utility," or at least the information you get is
insufficient to estimate it fully (≈23:21). Add the same positive constant to every $h$, and the
choice model is unchanged, because both sides of every comparison increase and the ordering stays
the same. Many monotonic transformations also keep the order. So all the data captures is "this
ordering information across alternatives, but it doesn't actually tell you a precise value for
what $U$ is" (≈23:21, ≈24:09). This is "a known issue with these kinds of models", and it "will
come up later in some of the difficulty in getting these things to work" (≈24:09).

The difference form makes this easy to check. An additive shift cancels in $U_{ni} - U_{nj}$.
Koyejo suggests convincing yourself that a global scaling also leaves the choices and their
probabilities unchanged, and that similar things hold for monotonic transformations of various
kinds (≈24:55, ≈25:41).

**Why it matters.** Within one context, where all the alternatives are comparable, this is fine.
But you often want to take a utility model trained in one context or data set, take another trained
in a different one, and compare them. Because the learned utility is only good up to monotonic
transformations, "you generally can't compare across contexts in a meaningful way" (≈25:41,
≈26:26). Koyejo says he does not see this much in the machine-learning literature. Economics,
psychology and other fields that use choice models often assume a **normalization**, for example
fixing the scale and standardizing the variance, so that utilities are on the same scale and
comparable across contexts. Whether that is sufficient is "critiqueable" (≈26:26, ≈27:12).

## Binary choice is logistic regression

The simplest case is two options: pick the item or not. The alternative index $j$ can be dropped,
and the utility is a single number per sample. The person picks the item when it is greater than
zero (≈27:12, ≈28:00). Writing $s_n$ for the features in this example, as the lecture does
(≈28:45):

$$U_n = \beta^\top s_n + \varepsilon_n, \qquad y_n = 1 \text{ if } U_n \gt 0$$

"It's easy to show, and a good exercise for yourself": if the noise is **logistic**, the probability of
choosing the item is the familiar logistic function from logistic regression (≈28:00):

$$P(y_n = 1) = \frac{1}{1 + e^{-\beta^\top s_n}}$$

To fit it, "the actual algorithm I would use is literally logistic regression" (≈28:45). The inputs
are the feature vectors $s_n$, the labels are the binary chose / did not choose, and the fit gives
$\beta$. For a new individual and the same items, plug in their features to predict whether they
will choose (≈28:45, ≈29:32). Logistic regression is "ML 101", and was flagged as a prerequisite
in the previous lecture (≈29:32).

Swap the noise model and you get a different classic model. With **standard normal** noise instead
of logistic, the result is a **probit** binary choice model (≈29:32, ≈30:18).

### Two items: only the difference matters

After a student asks how this connects to the general model (≈33:24), Koyejo restricts the general
setup to two options, so $j$ is 1 or 2, with utilities $U_{n1}$ and $U_{n2}$ (≈34:57, ≈35:44). Only
the difference between them matters. So the model

$$y_{n1} = 1 \text{ if } U_{n1} \gt U_{n2}, \text{ and 0 otherwise}$$

is equivalent to

$$y_{n1} = 1 \text{ if } \tilde U_{n} \gt 0, \text{ and 0 otherwise, where } \tilde U_{n} = U_{n1} - U_{n2}$$

(≈35:44, ≈36:32). The reason is the invariance above: "all that matters in the models is
essentially the differences across the utilities", so they can be collapsed into one (≈36:32,
≈37:18). This is the binary version of the general case. "Literally I would run logistic regression
on a data set that looks like this", and use the resulting $\beta$ to predict future choices
(≈37:18).

### Where the logit comes from: extreme value noise

Next the utility depends explicitly on the features of item 1 and of item 2, $z_{n1}$ and
$z_{n2}$, and the noise terms for the two items are **i.i.d. extreme value**, "one choice that's
convenient" (≈38:05). The goal is $P(y = 1)$, which is exactly $P(\tilde U_n \gt 0)$. Plug the
utility function in and work through the algebra (≈38:52). One way to write the answer keeps the
utilities separate. The probability of choosing item 1 is $e$ raised to its $\beta$-weighted
features, divided by a normalizing constant so that the two probabilities sum to one (≈38:52,
≈39:37):

$$P(y_{n1} = 1) = \frac{e^{\beta^\top z_{n1}}}{e^{\beta^\top z_{n1}} + e^{\beta^\top z_{n2}}}$$

With a shared $\beta$, normalizing out the numerator gives a form in the feature difference
(≈39:37):

$$P(y_{n1} = 1) = \frac{1}{1 + e^{-\beta^\top (z_{n1} - z_{n2})}}$$

The captions garble this second expression ("one over one plus beta 1 -2"). The form above is the
one the spoken steps describe. It is not read off a slide.

"Where might you have seen this?" Most likely in the math of **multiclass logistic regression**
(≈39:37, ≈40:24). Either fix a default class, and all the weights come out as differences, or
reduce multiclass logistic regression to two options: "exact same math". If that is unfamiliar,
it is a useful exercise, "and we may test stuff like this" (≈40:24).

A student asks why one uses extreme value noise rather than standard normal (≈46:39). "Extreme value
noise is what gets you logistic regression." Koyejo does not know which came first historically.
The noise you need "in order to make the whole math work" is i.i.d. extreme value noise (≈46:39).
The captions garble the model he names just before that ("you'll use only regression").

### Building the data set

A student asks how you would actually use logistic regression here (≈44:16). Koyejo's answer:
collect observations $y_n$, binary in this setting, and pick a featurization. The model above "is
exactly equivalent" to setting

$$x_n = z_{n1} - z_{n2}$$

which follows from the fact that only differences matter (≈45:04, ≈45:51). You now have a data set
of pairs $(x_n, y_n)$ for $n = 1, \dots, N$: feature vectors as inputs, binary labels as outputs.
"Once I construct the data set, I can literally call" a model-fitting routine on it (≈45:51). An
earlier student question gets the same answer. The math is identical whether the two options are
choosing this car or not, or choosing car A over car B, and what is fitted is effectively the
difference of the features (≈42:44, ≈43:31).

## Is the noise model right?

Three exchanges probe the noise assumption.

**Independence** (≈40:24). Is it realistic that the noise is i.i.d.? Here it means the randomness in
choosing item 1 is independent of the randomness for item 2, and in real settings there may be
correlation (≈41:11). The math gets more complicated, "but with modern tools it's actually not that
much more difficult". An obvious approach is a hierarchical model with parameters for the noise
terms $\varepsilon_1$ and $\varepsilon_2$ that captures their correlation (≈41:11, ≈41:57). Most
applications use the i.i.d. assumption. It is "probably not reality", but "there are also other things broken
that are not reality here". The closer the modelling choices are to reality, the more accurate
the model. But there are trade-offs with sample size, and pragmatic choices let you fit things at
all. "Are we getting ground truth? Probably not. But often this is a reasonable approximation"
(≈41:57, ≈42:44).

**What real noise looks like** (≈47:24). What does the noise look like in a recommendation engine,
or in voting? Koyejo has never seen that analysis in machine learning, "which is probably telling
about how much we examine our models". He thinks it is a good question, and maybe easy to check.

**Do we even care?** (≈47:24) A student suggests that we just assume a noise model because it
yields a workable model. "Yes and no" (≈48:09). With his machine-learning hat on, there are ways to
check **goodness of fit**. Split into train and test sets, fit on a subset, and check out-of-sample
performance. If the error is high, there are standard interventions: richer features, a different
noise model (examining whether the noise "is in the wrong place"), or a more sophisticated function
class such as a deep network instead of a linear model (≈48:09, ≈48:55). With a statistics hat on,
you would use goodness-of-fit tests (≈49:40). The point he anchors on is that "once you set up the
problem and transform things appropriately, this looks literally like a standard machine learning
problem", so all the standard tools apply directly (≈48:55, ≈49:40). "We care to the extent that we
get a good fit at the end", however fit is measured. He would typically use out-of-sample
performance (≈49:40, ≈50:27).

## More than two options, and any model class

Everything so far plays with the same few objects: function class, noise distribution and the range
of items (≈50:27).

- **Many alternatives.** Allow up to $J$ alternatives with extreme value noise, and the result is
  **multiclass logistic regression** (≈50:27, ≈51:14). Replace the extreme value noise with probit
  noise to get the Gaussian version (≈51:14). These are common modelling choices in practice.
- **Correlated noise.** To capture correlations, assume the noise is Gaussian with a covariance
  describing how the terms are correlated. You then fit both the linear model's parameters and the
  noise correlations, which changes the fitting procedure a little (≈51:14, ≈52:01). Koyejo does not
  think scikit-learn handles correlated noise. statsmodels in Python, or R, would. "You could do it
  yourself. That's also fun. Less and less necessary" (≈52:01, ≈52:48).
- **Any function class.** All the examples use linear models. But once the problem is set up as a
  learning problem, "I can pick any model class I like": a deep learning model, a decision tree, an
  SVM ("I don't think we teach SVMs in our classes anymore"). Fit it with standard machinery:
  stochastic gradient descent, "the hammer we like to use", in scikit-learn, PyTorch or similar
  (≈53:34, ≈54:19).

The recap at ≈52:48 restates the arc. Assume an underlying true utility, convert the choice problem
into an effectively multiclass (binary for binary choices) problem, and remember the degrees of
freedom: differences, and monotonic transformations. You get something monotonically equivalent to
$U$, not $U$ itself. Logistic models come from extreme value noise and probit regression from
Gaussian noise (≈52:48, ≈53:34).

So **every standard concern of model fitting applies** to choice models: bias–variance trade-offs
and overfitting. The more complex the function class mapping $x$ to $y$, the more data you need, or
you overfit (≈54:19, ≈55:07). Koyejo asks the class to define overfitting. A student answers, and he
summarizes: "good training performance, bad test performance", because the model has picked up the
nuances of the training data and doesn't generalize (≈55:07, ≈55:53).

## One utility or many: modelling individuals

A student asks how to handle different individuals making different choices (≈31:04). This is "an
explicit modeling assumption", and like every such assumption it affects the quality of the results.
It trades off against practical concerns like the number of samples and the risk of overfitting
(≈31:52, ≈32:37). The options (≈31:52, ≈32:37):

- **One shared utility.** Everyone makes choices the same way, so the data are multiple observations
  of one utility model.
- **Separate utilities.** Each person has their own. At least in this model there is no benefit from
  modelling them jointly, so fit a separate model for each.
- **Tied parameters.** Each person has their own $\beta$, but the $\beta$ values are tied together,
  for example additively, or by assuming the set of them across individuals is low rank.

Later he returns to the point (≈55:53, ≈56:39). Very often the data are simply **pooled**. "Almost
all the ML applications" he knows of do not distinguish between individuals. Choice models in
psychology and economics do, because they see individual differences as an important signal.
Machine learning is "slowly understanding" that this might matter more and more. If individual
differences matter, pick a model with features of the individual as well as of the items. See also
[whose preferences](whose-preferences.md).

**Students who give no answer.** Two questions ask what happens when someone has no preference
(≈18:36, ≈30:18). The basic model assumes a choice is made: "it'd be awkward to not have a
choice across the K items, for at least this class of models" (≈19:26). A student suggests an
**abstain** option. Koyejo agrees it is a good way to handle this: add "no choice" as a choice and
model it too (≈20:12). In the binary model, that means at least three options (choose, don't
choose, no preference), so the binary model no longer applies directly. It fits the general
$K$-option framework, at the cost of "implicitly modeling a choice of no choice" (≈30:18, ≈31:04).

## Ordered responses: Likert scales and the ordered logit

Beyond binary choices, you might collect **Likert-scale** preferences: how much one prefers an item.
His example: "Am I enjoying this class so far?", answered from one to five (≈56:39, ≈57:28). The
standard model keeps the utility and adds **thresholds**, written $a$, $b$, $c$ and $d$ for five
ordered answers. The answer is 1 if the utility falls below $a$, 2 if it falls between $a$ and $b$,
and so on up to 5 above $d$. In most implementations you fit both the thresholds and $h$. It often
works reasonably well to pre-select the thresholds and fit only $h$ (≈57:28, ≈58:14). Either way it
is a standard maximum likelihood problem, solved with gradient descent over all the parameters
(≈58:14). Implemented this way, with a linear model under the hood and thresholds for $K$ options,
it gives the **ordered logit model**. From the utility and the thresholds you can work out the
probability of each of the $K$ answers, and fit the model to observations (≈58:14).

The slides misbehave at this point ("we need to play with slides a little bit", ≈58:14), so the
lecture may show less than was planned here.

## Rankings: the Plackett–Luce model

When people **rank** items rather than pick one, the lecture uses "a slight alternative version"
that is "generally called the **Plackett–Luce** model" (≈59:02). It is ascribed to the 1970s. It is
used heavily in the biomedical literature for ranking, often in genetics, and sometimes in
econometrics, which calls it the **exploded logit** model. Koyejo does not know why, and suggests it
"might be fun to find out" (≈59:02).

A student's question prompts a clarification (≈1:01:22). Here the observations are **ranked orders**.
Each time an individual comes in they get $J$ items and order them, and you want a probability model
for the ordered list (≈1:01:22, ≈1:02:08). Plackett–Luce builds it as a chain of choices: the
probability of the first choice, times the probability of the second given the first, and so on to
the last (≈59:49, ≈1:02:08). Each factor is a normalized score: the first item's score over the sum
of all $J$ scores; then, conditioned on that first choice, the second item's score over a sum "that
starts at two instead of one"; and so on to the end (≈1:02:08). Writing $i_1, i_2, \dots, i_J$ for
the items in ranked order and $h_{n i}$ for the deterministic utility of item $i$, the spoken
description corresponds to

$$P(i_1, i_2, \dots, i_J) = \prod_{r=1}^{J} \frac{e^{h_{n i_r}}}{\sum_{s=r}^{J} e^{h_{n i_s}}}$$

The lecture calls these "scores" and does not say aloud how a score is computed from the utility.
The exponential form here is the one the extreme value noise of the earlier sections gives, and
Koyejo mentions extreme-value-style noise as the default to depart from (≈59:49). The usual
extensions all apply: a generic function class instead of a linear model, probit noise instead of
extreme value noise, correlated noise (≈59:49).

**Summary as given** (≈1:00:35, ≈1:01:22). You measure individuals' responses to choice queries,
observing them make decisions. The key assumption is that the decision-making is governed by a
utility function. You choose a model for that utility, with features describing the items and
perhaps the individual, and set it up as a machine-learning problem. Then you fit its parameters,
by maximum likelihood with regularization and "all the standard things", to get a model that
predicts future observations.

## Rationality means transitivity

A student asks what happens if someone's preferences over three options are **circular** (≈1:02:58).
Koyejo calls it a great question about a key assumption (≈1:02:58, ≈1:03:43). These models assume
the choices are "effectively linearly orderable". This is what economics means by assuming people
make **rational** choices: "rational here exactly means that you don't end up with this
transitivity mess", where $a$ beats $b$, $b$ beats $c$, and $c$ beats $a$ (≈1:03:43). The setup
does not allow that "outside of noise". Individual observations can be noisy, but in expectation
the preferences are assumed transitive (≈1:03:43).

If the assumption breaks (≈1:04:28):

- The intransitivity can sometimes be explained by **features that are not rich enough**. Add more
  features.
- Other classes of models allow some intransitive preferences. The course does not cover them, but
  Koyejo says he should give references.
- Most of these setups assume the "quote-unquote true" preferences are "quote-unquote rational".

He recounts a discussion from the previous year's offering, with psychologists and marketing people
in the room (≈1:05:15). Noise is one way to explain intransitivity. When observed preferences break
these assumptions, are humans irrational, "the problem because they're not matching our models", or
are the models or the context set up wrong? He begins to give an answer he finds compelling, from a
paper he says he should look up and might add to the reading list, but the sentence is not finished
(≈1:05:15, ≈1:06:05). Instead he lays out the extremes (≈1:06:05). At one end, the rationality
assumption is completely broken and should not be used. At least one talk, "in a week or so", will
discuss whether strong rationality assumptions suit human choice in complex settings like language
models. At the other end, the problem is not being modelled the right way: "if we had sufficient
appropriate context we can almost always think of humans as rational". As he understands it, this
is still debated in economics and elsewhere. For this course he treats it as "a pragmatic modeling
choice", and the course will cover cases where it is "for sure broken" and tools for those cases
(≈1:06:05, ≈1:06:50). See also [noise, inconsistency and rationality](preference-queries.md#noise-inconsistency-and-rationality).

## Revealed versus stated preferences

What does it mean "to actually observe a preference"? (≈1:07:36) There are two broad families, and
Koyejo stresses that the distinction is "actually quite an important idea" (≈1:09:54).

- **Revealed preferences** come from watching people make real choices in real situations, such as
  people coming to the car site and picking the car they want. The data are often offline, but they
  capture real behaviour in real contexts (≈1:07:36).
- **Stated preferences** come from putting people in a room and asking: imagine you were going to
  buy a car; here are some options; which would you pick? For the person this is **hypothetical**.
  They are not putting money down, but working through their mental model of how they would choose
  (≈1:07:36, ≈1:08:22).

**Trade-offs** (≈1:08:22–1:09:54). Stated preferences let you control the context: well-controlled
experiments, balancing, controlling for confounds. Their big weakness is that they may be
unrealistic. People may state one thing and do another, as often happens with election choices.
Revealed preferences have issues of **confounds** and **coverage**. The choices people actually make
may not cover the available options well enough to estimate good parameters for all of them.

**Language models** (≈1:09:07). Koyejo thinks the gap is "not engaged sufficiently in our field".
Language models sit in "a bit of a weird gap", because there is no good grounding in downstream
decisions to separate revealed from stated. But he argues that language-model preference
experiments mostly collect **stated** preferences. Someone is in a room, shown completions, and
asked which they prefer. "There's no cost to making a decision either way." The distinction is
"semi-controversial depending on the setting" (≈1:09:54). See [RLHF](rlhf.md).

**Does the observation type interact with the model?** A student asks whether the choice between
stated and revealed data interacts with the choice of model class (≈1:10:43). Conceptually the two
choices seem orthogonal, Koyejo says. Practically they interact (≈1:11:28). With revealed preferences
you have less control over the sample space. Some choices and some regions of feature space can be
badly undersampled, so a more restricted model is the pragmatic choice. Alternatively, you can do
something more sophisticated to correct for distribution shift (≈1:11:28, ≈1:14:34). With stated
preferences you can design the experiment so that the observations cover all the options, which
makes a more complicated model easier to fit (≈1:13:48). His summary: "they interact with each
other, and the interaction matters", in a way he thinks of as subtle (≈1:14:34).

**Students' examples.** One student describes telling YouTube "I don't want to see this" and then
clicking on it anyway, and asks which signal is right, and whether the two should really be in one
model (≈1:13:03). Another, thinking about the same example, describes a three-year-old grabbing the
phone and swiping and clicking at random (≈1:14:34, ≈1:15:20). An implicit signal such as "did I
complete the video" is very good but needs cleaning, and can mislead if used raw. The captions do
not make it clear where one speaker stops and the next starts in this exchange. Koyejo's response:
"the real world is messy and noisy and you have to make choices" (≈1:15:20).

**Why the gap is real** (≈1:16:07, ≈1:16:53). "It's very well known" that what people say they would
choose and what they actually choose are not the same, so the trade-off is between controlling the
experimental setup and seeing people's real choices. Koyejo's example is an election. Ask people in
this room, on the West Coast in California, who they would vote for, and some may give an answer
they think everyone will agree with, not one they would be uncomfortable stating. A stated
preference folds in who is asking, the context, and how the asker might think of you for that
choice. A revealed preference is the choice people make "when there's some consequence on the
line": a purchase, or some real-world outcome. The two "can actually be like night and day", and
data collected in the same situation under the two settings "in general would not agree" (≈1:16:53,
≈1:17:39).

Two more contributions close the lecture (≈1:17:39, ≈1:18:25). Asked whether anyone uses both kinds
of data, with a dummy variable for the bias, Koyejo says some of it is modelable. He hasn't seen
much work on it, though he would be surprised if there were none. A student then suggests that with
real money on the line people bring risk into their choices and call for different models, while
in a simulation they may behave more like expected-utility maximizers. Koyejo agrees that is part of
it, but says there is additional nuance that makes the separation less clean (≈1:18:25).

## Student questions in this lecture

| ≈ | Question | Short answer |
| --- | --- | --- |
| 17:02 | Does $z$ need an item subscript, or capture only the individual? | $z$ can be rich: individual, item and alternatives; $n$ can index the individual |
| 18:36 | What if someone picks none of the items? | The basic model assumes a choice; an abstain option is a good fix (≈20:12) |
| 21:00 | (Koyejo asks) What does fitting mean? | Find $\beta$; predict by comparing $h$ across items |
| 30:18 | How does the binary model handle "no preference"? | It can't; use three options, implicitly modelling "no choice" |
| 31:04 | Different individuals with different choices? | Shared utility, separate utilities, or tied (additive, low-rank) parameters |
| 33:24 | How does this slide connect to the last? | General $K$-option model restricted to two; only differences matter |
| 40:24 | Is i.i.d. noise realistic? | Probably not; correlated or hierarchical models exist; i.i.d. is the usual approximation |
| 42:44 | Five cars versus choosing one car or not? | Same math; the model uses the feature difference |
| 44:16 | How do you actually use logistic regression here? | Build $x_n = z_{n1} - z_{n2}$ with binary $y_n$ and fit |
| 46:39 | Why extreme value noise, not standard normal? | Extreme value noise is what gives logistic regression |
| 47:24 | What does real noise look like in recommenders or voting? | Never seen the analysis in ML |
| 47:24 | (comment) We don't care what the noise is | "Yes and no": check goodness of fit out of sample |
| 55:07 | (Koyejo asks) What is overfitting? | Good training, bad test performance |
| 1:01:22 | (unclear) about the ranking model | Plackett–Luce models ranked orders, one conditional choice at a time |
| 1:02:58 | What about circular preferences? | Rationality means transitivity; add features, or use other model classes |
| 1:10:43 | Do stated/revealed and model class interact? | Conceptually orthogonal, practically yes: coverage drives model complexity |
| 1:13:03 | YouTube: I say "I don't want to see this", then click anyway | Clarifies the interaction answer |
| 1:14:34 | (comment) A child grabbing the phone; implicit signals need cleaning | "The real world is messy and noisy" |
| 1:17:39 | Does anyone model both, with a dummy variable for the bias? | Some of it is modelable; little work seen |
| 1:18:25 | (comment) Money on the line versus expected utility in simulation | Part of it, with more nuance |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/02-preference-models.md)'s header for the full list.
The ones that touch content:

- The 1959 reference (≈7:45): the caption runs "Luce", "logit analysis" and "qualitative choice
  behavior" together, and may combine two references from the slide.
- "Macroeconomics" (≈7:00), in the history of utility theory, as captioned.
- The second form of the two-item logit (≈39:37), captioned as "one over one plus beta 1 -2".
- The student question at ≈1:01:22 ("the previous slide enforces counts not ordering") is garbled.
  Koyejo's answer is about ranked observations.

## Related pages

- [Discrete choice models](discrete-choice-models.md): the models of this lecture gathered by
  concept.
- [Asking humans for preferences: queries, comparisons and noise](preference-queries.md): including
  revealed versus stated preferences and the rationality assumption.
- [Whose preferences](whose-preferences.md): pooling versus modelling individuals.
- [RLHF and the language-model pipeline](rlhf.md): reward as utility; language-model comparisons as
  stated preferences.
- [Lecture 1 — Introduction](01-introduction.md)
