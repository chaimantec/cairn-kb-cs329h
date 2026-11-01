# Asking humans for preferences: queries, comparisons and noise

Every method in this course starts by asking people something. This page collects what the course
says about *how* to ask: absolute ratings or comparisons, one-shot or interactive collection, how
many questions to ask, and what to assume about the answers.

**Sources so far:** [lecture 1](01-introduction.md), [lecture 2](02-preference-models.md),
[lecture 3](03-model-based-preference-optimization.md) and [lecture 4](04-mechanism-design.md).
Lecture 2 builds the models of human choice that sit on top of these queries; they have their own
page, [discrete choice models](discrete-choice-models.md). Lecture 3 counts the queries a specific
elicitation problem needs, and asks what kind of question people can answer. Lecture 4 asks what
happens when the people answering are strategic, and treats prices as preferences; that material
has its own page, [mechanism design](mechanism-design.md). Lecture 5 places these queries inside a
larger design process and treats human preference as one way to evaluate a system; that material has
its own page, [human–AI interaction](human-ai-interaction.md). Later lectures are not yet in this
knowledge base.

## Efficient and effective elicitation

The course's working definition asks how to elicit preferences **efficiently and effectively**
(lecture 1, ≈9:18).

- **Efficiency** is a budget. Interacting with people is costly, so the aim is to learn what you need
  from as few interactions as possible. The term the course uses is **query efficiency**: how many
  samples or interactions are needed to estimate a given quantity or function from a set of agents
  (≈10:04, ≈10:49).
- **Effectiveness** is the quality of the elicitation process: whether you actually get the signal
  from people (≈10:49).

Because human queries are expensive, almost every problem in the course is a problem of learning from
limited samples, under a budget on sample size (≈23:48, ≈24:37).

**Active learning** is the course's main tool for this. Instead of labelling whatever examples nature
provides, the procedure "explicitly seeks which examples need labeling". In a suitably structured
problem it learns much faster, as measured by **sample complexity** or **query complexity**, the
number of labels needed (lecture 3, ≈2:22, ≈3:07). Koyejo argues it fits preference learning
especially well, because "people get bored very quickly", and collecting samples from people "is
fraught because people get tired and it may be expensive" (≈4:40, ≈5:25). He also calls active
learning a gap in the preference-learning literature (≈3:54). The lecture on active learning itself
(Oct 14 on the schedule) is not in the catalog. Lecture 3 recaps it.

Query complexity can rarely be pinned down. "I don't know how to do this for RLHF," Koyejo says, but
in structured settings there are bounds (lecture 3, ≈6:59, ≈7:44). In
[metric elicitation](metric-elicitation.md) for binary classification, binary search over pairwise
comparisons reaches accuracy $\epsilon$ in about $\log(1/\epsilon)$ questions. He is "pretty sure"
that is the lower bound without further assumptions (≈1:04:14).

## Explicit versus implicit preference signals

In one sense "all of machine learning is learning from human preferences": almost every data set was
created or labelled by people, and models learn to mimic it (lecture 1, ≈11:36, ≈12:21). Koyejo calls
that signal *implicit*. A preference effect is baked in by whoever labelled the data, but the learning
is not designed around it. The course studies the *explicit* case, where the learning procedure is
deliberately about learning from preferences, "often through interactive processes" (≈12:21, ≈13:07).

## Absolute ratings versus comparisons

You can ask a person for an **absolute** judgment (is this setting a four out of five?) or for a
**comparison** (which of these two is better?).

The lecture's clearest case is an exoskeleton from colleagues at Caltech. Each user's response curve
is personal, and the most reliable signal is what the user says about how well a setting works
(≈1:06:26, ≈1:07:11). The group found that **preference queries worked a lot better** than absolute
ones: ask the user to compare two settings, and let the algorithm turn the pairwise answers into a
tuning of the device (≈1:07:11, ≈1:07:58). Koyejo says the course will make the same argument "in many
of the applications we look at" (≈1:07:11).

Comparisons appear throughout the lecture's examples:

- **Language models.** RLHF's comparison step is most commonly pairwise. With four candidate
  responses, the person might pick one of the four. "Typically this is discrete choice" (≈37:54). See
  [RLHF](rlhf.md).
- **Humour and other unspecifiable targets.** Nobody can write down the equation for "funny", but
  people can say which statement is funnier, and that ranking is a training signal (≈56:23).
- **Classification trade-offs.** [Metric elicitation](metric-elicitation.md) uses pairwise preferences
  to tune a classifier's trade-offs to expert judgment (≈1:08:43, ≈1:09:31). Lecture 3 shows that
  pairwise questions are enough. Binary search works even when the stakeholder can only say which
  of two classifiers they prefer, not score either one (lecture 3, ≈58:04).
- **Recommender systems.** The field has developed many kinds of query and feedback: thumbs up or down
  on a single item, pairwise preferences, rankings and ratings (≈1:11:49).

Lecture 2 models each kind of answer. A pairwise choice, or a choice of one of $K$ options, is a discrete choice model,
fitted as logistic or probit regression. A rating on a scale, such as a Likert-scale "Am I enjoying
this class so far?" answered from one to five, gets an **ordered logit** model with thresholds. A full
ranking of $J$ items gets the **Plackett–Luce** model, built as a chain of conditional choices
(lecture 2, ≈56:39–1:02:08). See [discrete choice models](discrete-choice-models.md).

**Dueling bandits** are bandit problems with pairwise preferences built in. The course will use them
as a framework for interactive comparison problems like the exoskeleton (≈1:07:58).

## One-shot versus interactive collection

In the language-model pipeline, collecting demonstrations for supervised fine-tuning is "mostly
one-shot": a large offline effort to get good examples. Collecting preferences "is typically best done
interactively", although some work does it offline. The course covers the technical differences
(lecture 1, ≈38:40).

## Population-level or example-level questions

A query has to be something a person can answer, and lecture 3 names this as "one of the big gaps"
in metric elicitation (≈1:06:35). The method asks a stakeholder to compare two classifiers by their
performance over a whole population, which "needs a fairly sophisticated stakeholder" (≈1:08:07). To
help, you can ground them in the fact that no classifier is perfect. Then show scenarios of what a
false positive or a false negative means, and relate those to the population through base error
rates (≈1:07:21, ≈1:08:07).

Questions about **single examples** ("would you prefer this mistake versus other mistake?") are
easier to answer. But the metric being elicited then has to depend on the example, which makes the
space of metrics much more complicated (≈1:08:54). Koyejo's group deliberately asked
population-level questions, so that the framing of the question matched the population-level metric
being elicited. A mismatch between "the way you ask in the question and the set of kinds of metrics
that you're asking for" leads to other errors (≈1:09:41). His takeaway is that useful elicitation
needs "some meaningful connection between the algorithmic problem and sort of the human problem"
(≈1:09:41). The inverse decision theory work in the same lecture takes the other route and asks
about the labelling of individual examples (≈1:17:29, ≈1:18:15).

## Asking as part of a design process

Lecture 5 puts the course's queries in a wider frame. Human–AI interaction work has three steps:
design the interaction, enable it, and evaluate it. The course's methods are tools for the middle step:
"most of what we've covered in this class is in some ways you can think of as tools that you can bring
to bear to make the interaction probably easier" (lecture 5, ≈41:45). His examples are easing the
burden of interaction "by personalization, by getting pairwise preferences from people" (≈41:45).

The lecture's main example shows how hard it is for people to say what they want. PromptCharm's user
studies found "significant conceptual gaps when a novice user writes prompts for image creation":
users have a clear image or style in mind but trouble articulating it (≈48:41). Its answer is an
interface rather than a better question. It exposes the automatic prompt rewrite, suggests styles,
lets users weight terms up or down, and supports quick, cheap exploration (≈49:28–52:37). Lecture 3
reached a similar conclusion about metric elicitation: useful elicitation needs "some meaningful
connection between the algorithmic problem and sort of the human problem" (lecture 3, ≈1:09:41).

Preferences also appear as an **evaluation** signal. Generated code can be scored by whether it passes
tests, by its similarity to reference code, "or you could ask a human to give preferences on the code
outcomes" (lecture 5, ≈1:14:49). Quantitative and qualitative evaluations "carry signal" of different
kinds (≈1:10:13). Lecture 5 also reports, as its understanding of the research, that people "tend not
to be good at actual percentages" and bucket uncertainty into low, medium and high (≈1:01:01). That
remark is about people reading uncertainty that a tool shows them, not about answering queries.

## Revealed versus stated preferences

Lecture 2 asks what it means "to actually observe a preference", and calls the answer "actually quite
an important idea" (≈1:07:36, ≈1:09:54). There are two broad families.

**Revealed preferences** are real choices in real situations: people coming to a car website and
picking a car. They capture real behaviour, but come with **confounds** and gaps in **coverage**,
because the choices people happen to make may not cover the options well enough to estimate them all
(≈1:07:36, ≈1:09:54). **Stated preferences** are hypothetical answers: "imagine you were going to buy
a car; which would you pick?" Nobody puts money down. They let you run well-controlled experiments,
but may be unrealistic, because people state one thing and do another (≈1:08:22, ≈1:09:07). Koyejo's
example is an election. Asked in a California classroom who they would vote for, people may give an
answer they think the room agrees with. A stated preference folds in who is asking and how the answer
will be seen; a revealed one is made "when there's some consequence on the line". The two "can
actually be like night and day", and data from the same situation collected both ways "in general
would not agree" (≈1:16:07–1:17:39).

**Language-model preference data is mostly stated.** Someone is shown completions in a room and
asked which they prefer, and "there's no cost to making a decision either way". Koyejo thinks the
field has not engaged with this gap enough (lecture 2, ≈1:09:07). See [RLHF](rlhf.md).

**The kind of data affects the model you can fit.** Conceptually the two choices are independent;
practically they interact. Revealed data are skewed by whatever the world happens to show you, so
some options are badly undersampled, and a simpler, more restricted model is the pragmatic choice
(or a correction for distribution shift). A stated-preference experiment can be designed so every
option is covered, which makes a richer model easier to fit (≈1:11:28–1:14:34). Students raise the
YouTube case, where someone tells the site they don't want a video and then keeps clicking on it,
and implicit signals such as whether a video was finished, which are good but need cleaning
(≈1:13:03, ≈1:15:20).

**Prices as revealed preferences.** Lecture 4 grounds preferences as the prices people are willing
to pay (≈11:40). A sale at a posted price is a revealed preference with little resolution. If
someone buys, "their value must be higher than your stated price", so "you don't learn that much
about individual preferences, but you learn at least some directional signal" (lecture 4, ≈17:51).
An auction might reveal more, since bids should be correlated with values, but only if bidders have
no reason to shade them (≈18:36). Lecture 4 also lists learning "with various kinds of revealed
preferences" under pricing, observing buyers' actions over iterations to predict their future
behaviour, among the questions where learning meets mechanisms (≈58:53).

## Noise, inconsistency and rationality

Human answers are not clean. A student notes that people "don't agree with themselves 25% of the
time", and give a different label depending on whether they have had lunch. So the labelling process
itself needs modelling (lecture 1, ≈13:07, ≈13:52). Koyejo agrees. The standard models of a comparison
are **Bernoulli models** (a comparison's outcome treated as a random draw), and "I don't know if that's
the truth". Part of the course is how to treat the noise or uncertainty that comes from inconsistent
human signals (≈14:37).

The course raises several questions about the human side (≈18:26, ≈19:12):

- how far to assume people are rational;
- when treating human error as noise is a good assumption;
- what correctness and expertise mean;
- how the problem changes between one person, a group and a society.

It also asks what happens when the people answering are **strategic agents** who may try to game the
system (≈19:57), and what to do about truthfulness and strategic behaviour (≈1:14:55).

Lecture 4 takes this up through **mechanism design**: setting the rules of the interaction so that
answering truthfully is each participant's best strategy, the property called **incentive
compatibility**. Koyejo reads it as an elicitation property as well as an economic one, since "the
true value you can think of as the target that you might be interested in in this elicitation
mechanism" (lecture 4, ≈29:29). In a second-price auction, bidding your true value is optimal
(≈31:00–36:30). In a pay-your-bid auction it is not: students immediately proposed bidding "the
minimum amount you have to" (≈19:21). Lecture 4's closing applications predict each person's value
from cheap signals, pairwise comparisons between completions and thumbs up or down on a stated
price, which it calls "low-signal responses to various kinds of simple pairwise-type queries". The
mechanism is then run on the predicted values (≈1:10:40, ≈1:11:25). See
[mechanism design](mechanism-design.md).

Lecture 2 says what "rational" means in its models: **transitivity**. Preferences are assumed
"effectively linearly orderable", so a cycle (a over b, b over c, c over a) cannot occur "outside of
noise"; individual answers can be noisy, but in expectation preferences are transitive (lecture 2,
≈1:02:58, ≈1:03:43). When data violate it, richer features can sometimes explain the violation, and
other model classes, not covered in the course, allow some intransitivity (≈1:04:28). Whether such
violations show that humans are irrational, or that the model or context is wrong, is still debated;
one view is that "if we had sufficient appropriate context we can almost always think of humans as
rational". The course treats rationality as "a pragmatic modeling choice" and will cover cases where
it is "for sure broken" (≈1:05:15–1:06:50).

Lecture 3 shows what such an assumption buys. Binary search for a stakeholder's metric needs their
preferences to be unimodal along the search. That rests on "a weak uniqueness assumption", which
Koyejo connects to rationality: a utility exists, is unique, and is well approximated by the class
being searched. When it fails, the method breaks (lecture 3, ≈58:50, ≈59:36). If answers are noisy,
as in the Boltzmann setting, a probabilistic version of the search is needed (≈1:01:07, ≈1:19:48).

The course's working assumption is stated plainly. Most of the work assumes "some kind of rational
human": there exists a reward function, "some sort of explicit deterministic function that tells us
what a human would prefer", even when it is not written down, and the models are built on it. "But it
is an assumption", and at least one invited talk will challenge it (lecture 1, ≈1:14:55, ≈1:15:40).
The technical core is **discrete choice** and the **parametric models** built around it (≈1:15:40),
which lecture 2 develops; see [discrete choice models](discrete-choice-models.md).

## Related pages

- [Whose preferences](whose-preferences.md): who gets asked, and what that does to the model.
- [Reward hacking](reward-hacking.md): what goes wrong when a model optimizes against learned
  preferences.
- [Discrete choice models](discrete-choice-models.md): the models fitted to these answers.
- [Lecture 1 — Introduction](01-introduction.md)
- [Lecture 2 — Preference Models](02-preference-models.md)
- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md)
- [Metric elicitation](metric-elicitation.md): a worked case where the number of queries is known.
- [Mechanism design](mechanism-design.md): eliciting values from strategic participants.
- [Lecture 4 — Mechanism Design](04-mechanism-design.md)
- [Human–AI interaction](human-ai-interaction.md): where queries sit in designing, enabling and
  evaluating an interaction.
- [Lecture 5 — Human-centered Design](05-human-centered-design.md)
