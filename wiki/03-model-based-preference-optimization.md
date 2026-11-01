# Lecture 3 — Model-based Preference Optimization (metric elicitation)

This lecture is a deep dive into **metric elicitation**: using a stakeholder's answers to pairwise
questions to choose the performance metric a classifier should be judged by. Sanmi Koyejo frames it
as a special case of what the course has been building, utility estimation combined with active
learning, narrowed to one setting where the structure is rich enough to give exact algorithms and
query counts (≈5:25–7:44). The argument has three steps. First, choosing a metric is "actually not a
free choice". Metrics that sound equally reasonable rank models differently, as the Netflix Prize and
a recidivism-prediction controversy show (≈15:26–32:22). Second, for binary classification, a linear
metric is two weights on the two kinds of error, the classifiers that optimize such metrics are
thresholds on the predicted probability, and the geometry of the confusion matrix turns the search
for the stakeholder's weights into a search along a one-dimensional boundary (≈34:41–55:48). Third,
binary search over pairwise comparisons finds the weights to accuracy $\epsilon$ in about
$\log(1/\epsilon)$ questions, which Koyejo believes is the best possible without further assumptions
(≈57:19–1:04:14). The last minutes sketch a second line of work, **inverse decision theory**, which
asks about individual examples instead of whole classifiers and handles noise with a probabilistic
bisection search (≈1:16:42–1:20:34).

**Date.** This is catalog position 3. It corresponds to the **Oct 16** schedule row, "Lecture:
Model-based Preferences Optimization via Preference Elicitation". The recording does not state its
date, but the content places it. The main topic "will be on metric elicitation", and "last lecture
was active learning" (≈0:05, ≈2:22), which is the Oct 14 row ("Model-based Preferences Optimization
via Active Learning"). At the end Koyejo says a future lecture will cover bandits (≈1:22:06), the Oct
21 topic, and that mechanism design is coming "quite a bit later" (≈0:05), the Oct 28 topic. The
schedule's sessions between [lecture 2](02-preference-models.md) (Sep 25) and this one, Sep 30 to Oct
14, are not in the catalog. That includes the active-learning lecture this one builds on, with its
car-navigation example (≈3:07).

**No slides.** The lecture is given from slides and a board. Koyejo writes the optimal-classifier
problems on the board and erases one to make room (≈45:44). The course has not published the
slides, so every claim here is cited to the transcript by timestamp. The papers he draws on are
referred to as "the paper" or "the second paper" and not named in the audio, and this page does not
name them. The formulas below are rebuilt from what he says aloud, in his symbols ($A_1$, $A_2$,
$\delta$, $\pi$). Where the captions lose part of an expression, the page says so.

**What is not covered.** He planned three papers and, with three minutes left, had "got through
one" (≈1:15:55). The second is sketched in about four minutes. The third, which ties metric
elicitation to **mechanism design**, is moved to a future lecture (≈1:20:34, ≈1:21:20). Uses in
algorithmic fairness are mentioned and not covered (≈1:21:20).

[Edited transcript](../raw/transcripts/03-model-based-preference-optimization.md) ·
[verbatim captions](../raw/transcripts/original/03-model-based-preference-optimization.md) ·
[video](https://www.youtube.com/watch?v=7i6WsIzZaeo) ·
[course website](https://web.stanford.edu/class/cs329h/fall2024/) · [sources](../sources.md) ·
topic page: [metric elicitation](metric-elicitation.md)

## Where this lecture picks up

Koyejo opens with a summary of the course so far. The course posited a "utility maximization type
perspective", with "Boltzmann style" utility functions, as its key normative claim: choices are
governed by an underlying utility, and the models estimate it (≈0:51, ≈1:37). In the second class
this turned preference choices, whether binary, ranked or other comparisons, into classification
problems, "and so this looks like machine learning" (≈1:37); see
[lecture 2](02-preference-models.md). He calls that "somewhat of a narrow view, but it is the
predominant view". Later sessions tried to widen it to multistakeholder perspectives (≈1:37, ≈2:22).

The last lecture connected this to **active learning**. Instead of having nature hand you the
examples to label, a procedure "explicitly seeks which examples need labeling", and if the world is
structured the right way this learns much faster than labelling found data at random. The measure is
**sample complexity**, or **query complexity**: how many labels are needed to do a good job of the
learning problem (≈2:22, ≈3:07).

A student asks whether active learning is really about utility maximization, or just a way of
collecting labelled data sets (≈3:07, ≈3:54; the question is partly garbled). Koyejo answers that
active learning is a generic procedure that *can be applied* to preference learning, and that "one
of the gaps that seems to exist in the preference learning literature is active learning as a way to
help it be more efficient" (≈3:54). The argument for combining them is about people. The key task
in learning from human preferences is asking humans questions, and "people get bored very quickly"
(≈4:40). Sample collection from people "is fraught because people get tired and it may be
expensive", so tools that speed up learning, like active learning, are "a sort of good combination"
(≈5:25). See [asking humans for preferences](preference-queries.md).

## Narrowing to classification metrics

The new step is to narrow the generic utility-estimation problem to "the specific setting of picking
metrics for classification problems". The utility to elicit is "the relative trade-offs, so say
different costs that people might have" for different errors in cost-sensitive classification
(≈6:12). It is still a preference elicitation problem, approached from the active-learning point of
view: "we'll be very sensitive to the number of times you ask a question, and that'll be one of the
main criteria of success" (≈6:59).

What makes the setting attractive is that query complexity can be **quantified** here. For many of
the big problems in modern machine learning that is hard: "I don't know how to do this for RLHF, as
a specific statement." In settings like this one, "there is work where you can actually give bounds"
on how many samples are needed (≈6:59, ≈7:44). He states simple theorems without proofs and refers
to the papers for details (≈7:44).

## Different errors, different costs

A student asks for a simple example, which is the next slide (≈7:44). Clinical decision-making is
the grounding case: "different kinds of errors have a different real world cost" (≈8:29). A false
positive, predicting a positive outcome when the truth is negative, might mean incorrectly
diagnosing a cancer, which causes real harm to the patient. In medical decision-making "not just
that it makes an error but the specific kind of error actually matters" (≈8:29, ≈9:15). So the
learning problem needs the right metric for the task, which could be one statistic or a weighted
average of several (≈9:15, ≈10:02).

The lecture uses **binary classification** throughout because it is "succinct and sort of easy to
explain" (≈10:47). A model makes one of two decisions, positive or negative, and each example is in
one of two true states. So there are exactly two kinds of mistake: predicting positive when the
truth is negative (a false positive), and predicting negative when the truth is positive (a false
negative). When the costs of the two are asymmetric, human preferences can help to ground them
(≈10:47, ≈11:35).

### Three models, three verdicts

The slide shows three models fitted to the same data set (≈11:35–13:53). Koyejo says these are "real
numbers from a real problem" (≈12:21). Only some of them are read out:

- The **first model** has high accuracy, "maybe 90% false positive rate, 5% false negative rate". If
  you care about overall accuracy it is a good model; it may be quite bad on false positives
  (≈11:35). Prevalence in the population can produce a skew like this (≈11:35, ≈13:07).
- The **second**, a nearest-neighbour model, has lower accuracy, 89%, but its false positive rate
  goes from 90 to 50, and its false negatives are also better (≈12:21).
- The **third**, a support vector machine, has a different accuracy, false positive and false
  negative number again; its numbers are not read out (≈13:07).

Each of the three measures, or some combination, could be the right one in different settings
(≈12:21). Asked which model to pick, a student chooses the second for a medical application, to
have as few false negatives as possible. Koyejo notes that the default for most people is accuracy,
"you may not even bother looking at the other metrics" (≈13:53). On the cancer case, another student
suggests that false positives can be acceptable, and Koyejo adds that "maybe you're okay with
overdiagnosis". A third student points out that in criminal justice "you don't want to falsely
incarcerate someone", so there false positives are bad. In recidivism prediction, a common use
case, overprediction is "a big problem", and you want to be conservative in the other direction
(≈14:38, ≈15:26).

## Choosing the metric is not a free choice

The point of the example is that even in the simplest setting, "choosing the, if you like, utility
function, cost function, loss function, is actually not a free choice. We often think about it as a
free choice" (≈15:26, ≈16:12). The course has dealt with hard cases, such as a reward function for
language model performance or for funniness (≈16:12; see [lecture 1](01-introduction.md)). The claim
here is that even a binary classifier's evaluation is "complicated and contextual". "Choices of
evaluation or utility functions can be as important as every other choice that you're making in your
model design, because they can completely change what you value" (≈16:12, ≈16:58). He calls this
"somewhat underappreciated, but it's the premise of the work I'm going to talk about today" (≈16:58).

**Reward, utility and metric are the same object** for this course. "From the point of view of this
class, reward, utility, metric roughly mean the same thing"; different fields picked different
words for "some quantitative measure of goodness" (≈17:46).

Instead of choosing one of three metrics, you can **weight** the errors: decide "how much more
expensive is a false positive error than a false negative error", and build models that optimize the
weighted combination (≈18:32). Working with the correct predictions instead, true positives and true
negatives, "turns out" to be essentially equivalent (≈19:17). Once weights are allowed, three
common options become "really infinite options", since every real-valued weighting is a valid
measure (≈19:17, ≈20:03).

That would not matter if metrics were exchangeable, if "any metric is as good as any other" because
they all order models the same way. "There are lots of examples showing this is not true" (≈20:03,
≈20:50). The lecture gives two.

### The Netflix Prize

Netflix released a large data set of existing ratings and offered a prize of a million dollars for
predicting the missing ones (≈21:35). Koyejo places it around his PhD years and is unsure of the
dates: he first says the 2010s, then "I think it was earlier than this" (≈21:35). He believes it ran
for about a year, "though that's checkable" (≈22:22). His own team "did okay but not that well"
(≈22:22). Lecture 1 also mentions his entry (≈1:11:04).

The competition metric was the **root mean square error (RMSE)** of the predicted rating against the
user's actual one-to-five-star rating (≈22:22, ≈23:08). But what matters for recommendation is mostly
getting the top of the list right. The first five or so items are what a user sees on the
dashboard, and there is "a strong bias to the top of the list" (≈23:08, ≈23:53). RMSE "did not
necessarily correlate" with getting the $\text{top-}N$ ranking right. Very naive methods, "something very
simple like a PCA thing or just like overall popularity, often did much better than some of the
methods that came out of this competition" (≈23:53). Metrics designed for $\text{top-}N$ ranking would have
suited the task better (≈24:40). For Koyejo it is a salient case of a metric that "on its face sounds
extremely reasonable", average squared error, which "actually like is a bad idea" for the task
(≈24:40, ≈25:25).

Netflix did not use any of the winning methods. Asked the year, Koyejo thinks it was around 2010
(≈25:25). A student suggests Netflix was using matrix factorization methods, and Koyejo says it had
been using that and a content-based method (≈26:11). He explains that the winning methods were
expensive, "lots of these sort of Bayesian hierarchical methods", that could not
run in production at the time. Netflix's internal method was "as good in terms of the things that
actually mattered but much less compute intensive" (≈26:11). He thinks Netflix still got more than a
million dollars' worth of research effort and recruiting out of it (≈26:57). When a student
suggests the lesson is about compute, he pushes back. The winner was good on RMSE, "and I'm saying it
wasn't good necessarily for what they cared about". Because the world is never perfectly
predictable, "relative costs, relative errors do matter, and quantifying it appropriately for the
task can make a big difference" (≈26:57, ≈27:43).

### Recidivism prediction and fairness measures that disagree

The second example is **recidivism prediction**, the risk of reoffence, used to help a judge in
sentencing decisions (≈27:43, ≈28:29). The captions give the company as "North Point" and the
algorithm as "compass"; the lecture gives no spelling. The company cared about accuracy and also
about a notion of fairness. Roughly, for different probability bins of risk, the predictions should
be similar across demographic groups. The name of that notion is garbled in the captions
(≈28:29).

A post-hoc analysis by **ProPublica**, a media company, used a different metric: the differences in
false negative and false positive rates across demographic groups. Koyejo says this "is sometimes
called equal opportunity in the fairness literature", with the caveat that two metrics share the
acronym EO and he sometimes mixes them up (≈28:29, ≈29:15). ProPublica found that "black defendants
were twice as likely to be incorrectly labeled as higher risk than white defendants", with large
disparities in both error rates (≈29:15).

His takeaway is not that the algorithm ignored fairness: the claim that it "was not sensitive to
fairness issues is incorrect", since its makers had a fairness notion and built for it (≈30:03).
Two "maybe well-meaning actors" with different normative views picked different measures and reached
completely different conclusions about the same results. The builder says it has built a fair
algorithm; the auditor, using another measure, disagrees (≈30:03, ≈30:48).

The case led to academic work. There had been "some hope, I think also maybe a bit of naivety, in the
technical fairness community" that a single golden measure would be fair everywhere (≈30:48,
≈31:34). Instead it prompted the **impossibility results in fairness**. For binary classification
with fairness measures, "roughly you can pick one, maybe two measures to sort of try to maximize at
the same time, but you can't pick three". There is "no universality": once several fairness
measures are chosen, not all will be satisfied at once (≈31:34, ≈32:22). See
[whose preferences](whose-preferences.md).

## Metric elicitation: let the stakeholder choose

Koyejo's group took up the question by asking whether human stakeholders could be used to select
metrics that match their preferences (≈32:22, ≈33:08). "The idea was there is not a right answer, but
perhaps for particular stakeholders there's a right answer for them." The goal is "an algorithmic tool
that helps them efficiently select the metric that best aligns with their preferences", which they
called **metric elicitation** (≈33:08).

He relates it to bandits, which the course has not covered yet, to inverse reinforcement learning,
and to an older literature on elicitation in psychology and econometrics. For this class, he says, it
is reasonable to think of elicitation as "this combination of utility estimation with active
learning" (≈33:08, ≈33:55). The lecture stays with binary classification metrics and refers to papers
for the fairness and multiclass settings (≈33:55, ≈34:41).

## Linear metrics: one number to find

Linear binary classification metrics "can all be reduced to" a weighted sum of the two kinds of
error. With $A_1$ and $A_2$ the weights on false positives and false negatives, a classifier $h$ is
scored by

$$A_1 \cdot \mathrm{FP}(h) + A_2 \cdot \mathrm{FN}(h)$$

where $\mathrm{FP}(h)$ and $\mathrm{FN}(h)$ are the rates of each error over the population
(≈34:41, ≈38:32). Eliciting a linear metric means fixing numbers for $A_1$ and $A_2$ (≈34:41).

**Scale cannot be recovered, and does not matter.** Scaling the weights up or down gives the same
metric: it picks the same classifiers and ranks them the same way. Koyejo adds that it is invariant
to monotonic transformations (≈34:41, ≈35:27). So it is "not really two numbers". The weights can be
rescaled to sum to one, and the problem becomes choosing a single $\alpha$, with weights $\alpha$ and
$1 - \alpha$ (≈35:27). The elicitation problem is to find that one number, the relative cost of the
two errors as a population measure of a classifier (≈35:27, ≈36:13). The lecture starts with the
**noiseless** setting, where the algorithm is most straightforward (≈36:13).

## The confusion matrix

Population performance in binary classification is described by four numbers (≈36:13, ≈36:59):

| | model predicts 1 | model predicts 0 |
| --- | --- | --- |
| **ground truth 1** | true positive (TP) | false negative (FN) |
| **ground truth 0** | false positive (FP) | true negative (TN) |

Each is a fraction of the population. True positive is the fraction of times the ground truth is
one and the model predicts one; true negative, ground truth zero and prediction zero. False positives
and false negatives are the two errors (≈36:13, ≈36:59). This is the **confusion matrix**. For $k$
classes it becomes a $k \times k$ matrix, ground truth by prediction, counting the fraction of
examples in each cell. Its cells have no special names beyond the binary case (≈36:59, ≈37:44).

Most classification metrics in use "can be written as some function of the confusion matrix"
(≈38:32). A linear binary metric is a weighted sum of the off-diagonal entries, as above (≈38:32).
More generally, any weighted loss or utility is a linear function of the confusion matrix $C$, with a
weight matrix $A$. Koyejo gives two equivalent ways to write it (≈45:44, ≈46:32):

$$\mathrm{tr}(A^\top C) = \mathrm{vec}(A)^\top \mathrm{vec}(C)$$

## The best classifiers are thresholds

Before the algorithm, a question to the class (≈39:20–41:40). Suppose you know the data distribution
over pairs $(x, y)$. Which classifier $h$ maximizes expected accuracy,

$$\max_h \mathbb{E}\big[\mathbf{1}\lbrace h(x) = y \rbrace\big]$$

or equivalently minimizes the number of mistakes? Here $\mathbf{1}\lbrace \cdot \rbrace$ is $1$ when
its condition holds and $0$ otherwise. The hint is logistic regression, which gives a probability of
$y$ given $x$: you turn it into a decision with a threshold, and there is a "natural threshold that
everyone uses" (≈40:53). The optimal rule is

$$h^\ast(x) = 1 \text{ if } P(y = 1 \mid x) \gt \tfrac{1}{2}, \text{ and } 0 \text{ otherwise}$$

which some people write as the sign of $P(y = 1 \mid x) - \tfrac{1}{2}$, with labels $\pm 1$
(≈41:40, ≈42:27). This, he says, is where logistic regression's semantics come from: it should
recover this probability, which is then thresholded (≈42:27).

Now weight the two kinds of mistake (≈42:27–43:14):

$$\min_h \mathbb{E}\big[A_1 \mathbf{1}\lbrace h(x) = 1, y = 0 \rbrace + A_2 \mathbf{1}\lbrace h(x) = 0, y = 1 \rbrace\big]$$

The first term is the false positive. The captions garble its condition on $y$ (≈43:14), and the
form above follows the lecture's own definition of a false positive (≈36:59). With equal weights it
is the same as counting mistakes (≈43:14). The optimal classifier is again a threshold, now at some
$\delta$:

$$h^\ast(x) = \mathrm{sign}\big(P(y = 1 \mid x) - \delta\big)$$

(≈44:08). A student guesses that $\delta$ is some ratio of the weights, "like A1 over A1 plus
A2, something like this". Koyejo says it is a ratio, says the guess is "very close", admits he does
not remember the exact form offhand, and refers to a paper for it (≈44:08, ≈44:56). Later he calls it a
"g function of the A", $\delta = g(A)$, which the paper works out (≈51:56). **The lecture does not
give the formula for $\delta$**, and this page does not supply one. It is "quite easy to prove for
yourself", at least informally (≈44:56).

The point is the connection. The optimizer of any weighted classification loss "looks like a sort of
threshold classifier", and every weighted loss is linear in the confusion matrix. So linear metrics,
weighted losses and thresholded classifiers line up (≈44:56, ≈46:32, ≈47:18).

## The geometry: which confusion matrices can be reached

The next step is to map out, over all possible classifiers, every **achievable confusion matrix**
(≈47:18).

**Two degrees of freedom.** The binary confusion matrix has four numbers, but only two degrees of
freedom (≈47:18). The entries for each true class sum to a population constant that does not depend
on the classifier. For $y = 1$ the sum is $\pi = P(y = 1)$, and for $y = 0$ it is $1 - \pi$ (≈48:04,
≈51:56, ≈52:41). So from two of the numbers you can always work out the other two (≈48:04). The
captions have him naming "TP and TN" as the pair that sums to $P(y = 1)$ (≈48:04). By the definitions
he gave a few minutes earlier, the two entries with ground truth one are TP and FN (≈36:13, ≈36:59).
$\pi$ is the marginal over the population; the conditional $P(y = 1 \mid x)$ is the object the
classifiers threshold (≈52:41). For multiclass problems the count is not two. The captions give his count as
"k * k minus one"; he says he would have to double-check, and says it grows roughly quadratically
with the number of classes. The multiclass case "gets complicated very quickly", which is why the
lecture skips it (≈48:51, ≈49:37).

**The ROC curve as the boundary.** Using true positives and true negatives as the two coordinates,
the set of achievable pairs is "effectively an ROC curve". As the threshold on a probability model
varies, it traces all the combinations of true positives and true negatives a model can reach on a
data set (≈49:37, ≈50:23). Usually only the top part matters. The bottom part can be reached too, by
deliberately classifying badly ("anti-classifications") (≈50:23). The useful fact is that **the
boundary of the achievable set is given by thresholds of the conditional probability** (≈50:23). So
without knowing the details of your model you can describe every achievable trade-off by trying all
thresholds (≈51:10). A student calls it a Pareto frontier, and Koyejo agrees: "essentially the Pareto
frontier of TP TN as two objectives", for a particular data distribution (≈51:10).

### Why the optimum sits on the boundary

Two facts finish the reduction. The first is a lemma from optimization: when you maximize a linear
function over a convex set, "maxima always lie on the boundary" (≈54:16, ≈55:02). The second is that
**the set of feasible confusion matrices is convex**. Given any two classifiers, you can reach any
point between their confusion matrices by mixing the two classifiers, so interpolating never leaves
the set. This is the same reason any two points on an ROC curve can be joined (≈1:02:38,
≈1:12:52, ≈1:13:37).

Together they give a one-to-one correspondence. The optimum of a linear metric is on the boundary,
every boundary point is a threshold classifier, and so each choice of weights $A$ corresponds to a
threshold $\delta$ (≈53:27, ≈55:02). Finding the metric that matches a stakeholder becomes "searching
along this boundary". Nominally a four-dimensional problem in confusion-matrix space, it becomes a
two-dimensional one through the degrees of freedom and a one-dimensional one through the geometry of
classification (≈55:48). Every point queried is equivalently a point on the boundary, a threshold, a
choice of $A$ or a confusion matrix (≈1:00:22).

## Eliciting by binary search

With the problem one-dimensional and noiseless, "it's like a search 101 problem" (≈57:19). The answer
is **binary search** (≈57:19). It works even if the stakeholder cannot score points directly but can
only answer **pairwise preference queries** along the boundary: "do you prefer the classifier here
versus the classifier here?" (≈58:04). The question can be posed in confusion-matrix space, in
classifier space or in threshold space, whichever makes most sense (≈58:04).

The walk-through runs along five points on the boundary (≈58:04, ≈58:50). The stakeholder prefers B
to A, so the maximum is to the right. They prefer C to B, and D to C, so it is further right still.
Asked about D and E, they prefer D, so the optimum is bracketed, "somewhere between D and E" in
Koyejo's words. People answering the queries are called the **oracle** in this work (≈1:05:01).

**What the search assumes.** A student asks whether anything is known about convexity or concavity
(≈58:50). Koyejo says there is "a weak uniqueness assumption", which he connects to rationality.
There exists a utility driving the person's decisions, it is unique, and it is approximated well
enough by a linear weighting of the errors. The search needs the preferences along the boundary to
be **unimodal**. That comes from the claim that a utility exists within the class being searched,
and when it fails, this approach breaks (≈58:50, ≈59:36).

### What "noiseless" means, and what finite data does

**Noiseless** means the comparisons reflect the person's true preferences (≈1:00:22, ≈1:01:07). If
answers contain errors, as in the Boltzmann setting, a probabilistic variant of the search still
works (≈1:01:07). The second paper, below, handles noise this way.

**Finite data** makes the boundary stepwise instead of smooth, like an empirical ROC curve. The usual
fix in the ROC literature is to connect the steps, since the convex hull is achievable by mixing
classifiers (≈1:01:52, ≈1:02:38). A student notes that with little data the estimated curve can go
back and forth, which is a source of noise calling for a more noise-robust search. Koyejo says this
treatment is expository, but even the original work got "reasonably far" assuming no noise while
dealing with stepwise patterns (≈1:02:38, ≈1:03:27).

### How many questions

The guarantee is "a direct consequence of binary search" (≈1:03:27). You get **accuracy $\epsilon$
in about $\log(1/\epsilon)$ queries** (≈1:04:14). "Unless you make more assumptions or constrain the
problem further, we are pretty sure this is the lower bound": in the worst case there is no way to
ask fewer questions and estimate the trade-off more accurately (≈1:04:14). Koyejo connects this to
his comment at the start: this is a setting constrained enough to quantify query complexity, the
number of questions needed for a good estimate (≈1:04:14, ≈1:05:01; see ≈6:59).

**Extensions** are listed without details: handling various kinds of noise (the method's name is
garbled in the captions), multiclass settings, more complex metrics, and settings with groups of
stakeholders (≈1:05:01). There is also applied work, in a paper, that implemented the idea with
stakeholders. There, eliciting this way "seemed to better reflect their preferences than some other
default approach". Koyejo says he may return to it in the course's lecture on HCI (≈1:05:01,
≈1:05:47). That is the *Human-centered Design* lecture ([lecture 5](05-human-centered-design.md)),
whose recording does not mention metric elicitation.

## The hard part: asking the question

A student asks how such a comparison is actually put to users (≈1:06:35). Koyejo calls this "one of
the big gaps in this line of work". The framing depends on the oracle making **population-level
comparisons** between classifiers (≈1:06:35). To make those answerable you might first ground the
stakeholder in the fact that perfect classification is not possible. Then you could show what false
positive and false negative errors mean in individual scenarios, and relate that to the population
through base error rates (≈1:07:21, ≈1:08:07). Even so, it "needs a fairly sophisticated stakeholder"
(≈1:08:07).

One extension is to let preferences be **contextual**, so that the weights depend on the example and
$A$ conditions on $x$ (≈1:08:54). Elicitation then gets easier, since you can ask about one example
("would you prefer this mistake versus other mistake?"). But the space of metrics gets much more
complicated (≈1:08:54). The group asked population-level queries deliberately, to match the
question's framing to the population-level metrics being elicited. Otherwise "you can actually have a
mismatch between the way you ask in the question and the set of kinds of metrics that you're asking
for", which leads to other errors (≈1:09:41). His takeaway: useful versions of this "need some
meaningful connection between the algorithmic problem and sort of the human problem" (≈1:09:41).
See [asking humans for preferences](preference-queries.md).

## Does it generalize beyond classification?

A student asks whether this is a generic way to pick an operating point on any Pareto frontier with
the right geometry, such as the cost of a model against its accuracy (≈1:10:29). "Yes and no." What
makes it actionable is being able to map a choice on the frontier back to a model that achieves it.
With a mechanism for that "full loop", the same idea applies in principle, but it is much more
complicated in general (≈1:11:18). Accuracy against speed of training, for instance, is "a
complicated one" (≈1:11:18).

The geometry is what is special. The convexity of the feasible confusion matrices is what makes the
connection easy, and another setting would need its own properties checked (≈1:12:05–1:14:24). A
student adds a practical objection. In practice there may be only a hundred or so models, and cost
cannot be thresholded: one model costs 100 dollars and another 110, with nothing in between
(≈1:15:10). Koyejo says the worked-out theory covers the classification setting. Beyond it there is
interest, and his group has tried some extensions, but not in full generality (≈1:15:55). The idea of
a confusion space or Pareto frontier is still "useful and generalizable". People often do research
"very close to something like a ROC curve without knowing it", and pointing that out can help them
see the problem differently (≈1:14:24, ≈1:15:10; the captions leave unclear whether part of this is a
student's comment).

## Inverse decision theory: thresholds from individual examples

In the last minutes Koyejo sketches the second paper (≈1:16:42–1:20:34). It is again about binary
classification, and draws on what he calls "a concept in psychology called **inverse decision
theory**", a way of inferring other people's preferences by thinking about the underlying
preference problem they are solving. The sentence trails off in the audio (≈1:16:42, ≈1:17:29). [Lecture 1](01-introduction.md) introduces the same term (≈1:10:16).

The setting is human–machine interaction. The machine has already estimated conditional
probabilities, and the task is to find the decision rule, the threshold, from a few samples
(≈1:17:29). The difference from metric elicitation is that the queries are about **individual
examples**, not population performance. People are asked for their preferences over the labelling
of specific examples. The threshold that best matches those answers corresponds to the trade-off they
care about (≈1:17:29, ≈1:18:15). Both methods need the probability model first. Koyejo offers an
analogy: getting the model is like pre-training, and finding the weights or threshold for the
decision setting is like preference tuning (≈1:18:15, ≈1:19:01). See [RLHF](rlhf.md).

This paper is "a bit more explicit about sources of noise". It allows noise from a distribution of
stakeholders, from error in the algorithm, and from other sources of uncertainty (≈1:19:01, ≈1:19:48).
The algorithmic change is a **probabilistic bisection** search in place of the deterministic one
(≈1:19:48). It keeps a prior over possible threshold points. Each new label shifts weight towards the
regions the evidence favours. You can prove how long it takes before the probability mass around one
point is high enough, "greater than half, for instance" (≈1:19:48, ≈1:20:34). In the closing summary
Koyejo describes the second paper as using this "for some of the aggregation" (≈1:21:20). The one
place the sketch mentions groups is the noise that comes from a distribution of stakeholders
(≈1:19:48).

## The takeaway

Metric elicitation is "a specific instantiation of the combination of preference estimation and the
sort of classification problems". There is a lot of structure to exploit there (≈1:20:34, ≈1:21:20).
The key takeaway: just as the course has spent time on utility functions in general, the choice of
metric matters even for a simple binary classifier. In that setting, combining active learning with
preference learning can pick utilities that better reflect stakeholder preferences (≈1:21:20,
≈1:22:06). He mentions some detail in the slides and perhaps homework (≈1:22:06), and says a future
lecture covers bandits and other algorithmic tools for preference learning (≈1:22:06).

## Student questions in this lecture

| ≈ | Question | Short answer |
| --- | --- | --- |
| 3:07 | (partly garbled) Isn't active learning about collecting labelled data, not utility maximization? | It is generic, and can be applied to preference learning, where it is under-used (≈3:54) |
| 7:44 | Is there a simple example? | The next slide: different errors cost different amounts, as in medicine |
| 13:53 | (Koyejo asks) Which of the three models would you pick? | Fewest false negatives for medicine; accuracy by default; overdiagnosis may be fine; false positives bad in criminal justice |
| 25:25 | (Koyejo asks) Why did Netflix not use the winners? | Expensive Bayesian hierarchical methods; the internal method was as good where it mattered (≈26:11) |
| 26:57 | (comment) So the lesson is about compute? | No: the winner was good on RMSE, not on what Netflix cared about |
| 39:20 | (Koyejo asks) Which classifier maximizes accuracy if you know the distribution? | Threshold the probability that $y = 1$ at one half (≈41:40) |
| 44:08 | And with weighted errors? | Again a threshold, at a ratio of the weights the lecture leaves to the paper |
| 48:51 | Are there two degrees of freedom in the multiclass case too? | No; roughly quadratic in the number of classes |
| 51:10 | So the boundary is like a Pareto frontier? | Yes, of TP and TN, for a given data distribution |
| 51:10 | What is $\delta$ here? | A function of the weights $A$, worked out in the paper (≈51:56) |
| 51:56 | What is $\pi$? Conditional or marginal? | $\pi = P(y = 1)$, the marginal over the population (≈52:41) |
| 57:19 | (Koyejo asks) What algorithm would you use for the search? | Binary search |
| 58:50 | Do we know anything about convexity or concavity? | A weak uniqueness, rationality-like assumption that makes preferences unimodal |
| 59:36 | Is $A$ given, or are preferences constructed from some $A$? | Each queried point is equally a boundary point, threshold, $A$ or confusion matrix |
| 1:00:22 | Does noise-free mean consistent repeated comparisons? | It means the comparisons reflect true preferences; noisy answers need a probabilistic search |
| 1:01:07 | What does finite data do to the boundary? | It becomes stepwise; connect the steps, since the convex hull is achievable |
| 1:02:38 | (comment) With little data the curve goes back and forth, so search must be noise-robust | Fair; the original work handled stepwise patterns |
| 1:06:35 | How do you actually ask users these questions? | A big gap: population-level comparisons need sophisticated stakeholders |
| 1:10:29 | Does this work on any Pareto frontier, such as cost against accuracy? | Yes and no: you need the full loop back to a model |
| 1:12:05 | Where does the convexity come from? | Feasible confusion matrices form a convex set: mix classifiers to interpolate |
| 1:13:37 | (comment) For training speed the space is unclear | Agreed; the properties would have to be checked |
| 1:15:10 | (comment) In practice there are few models, and cost cannot be thresholded | Beyond the worked-out setting; partial extensions only |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/03-model-based-preference-optimization.md)'s header
for the full list. The ones that touch content:

- The names of the recidivism company and algorithm (≈27:43) are given here as captioned, "North
  Point" and "compass"; the lecture gives no spelling.
- The fairness notion the company used (≈28:29) is garbled ("he types calibration"). Only Koyejo's
  description of it is recoverable.
- The first weighted-error term's condition on $y$ (≈43:14) is garbled; the page follows the
  lecture's definition of a false positive.
- The pair of confusion-matrix entries that sums to $P(y = 1)$ (≈48:04) is captioned "TP and TN",
  which does not match the definitions given at ≈36:13–36:59. The degrees of freedom are captioned
  "integrate freedom".
- The multiclass count (≈48:51) is captioned "k * k minus one", with Koyejo's own caveat that he would
  have to double-check it.
- The student's answer that leads to binary search (≈57:19) is garbled.
- The method for handling noise in the extensions (≈1:05:01) is captioned "public extensions".
- The speaker turns from ≈1:12:05 to ≈1:15:55 rest on the captions' speaker marks and are uncertain.

## Related pages

- [Metric elicitation and inverse decision theory](metric-elicitation.md): this lecture's method
  gathered with lecture 1's introduction to it.
- [Asking humans for preferences](preference-queries.md): query complexity, active learning, and
  population-level versus example-level questions.
- [Whose preferences](whose-preferences.md): the recidivism case and the impossibility results in
  fairness.
- [RLHF and the language-model pipeline](rlhf.md): reward, utility and metric as one object; the
  pre-training and preference-tuning analogy.
- [Lecture 2 — Preference Models](02-preference-models.md): the choice models that turn preferences
  into classification.
- [Lecture 1 — Introduction](01-introduction.md)
