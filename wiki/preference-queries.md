# Asking humans for preferences: queries, comparisons and noise

Every method in this course starts by asking people something. This page collects what the course
says about *how* to ask: absolute ratings or comparisons, one-shot or interactive collection, how
many questions to ask, and what to assume about the answers.

**Sources so far:** [lecture 1](01-introduction.md) and [lecture 2](02-preference-models.md).
Lecture 2 builds the models of human choice that sit on top of these queries; they have their own
page, [discrete choice models](discrete-choice-models.md). Later lectures are not yet in this
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
  to tune a classifier's trade-offs to expert judgment (≈1:08:43, ≈1:09:31).
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

Lecture 2 says what "rational" means in its models: **transitivity**. Preferences are assumed
"effectively linearly orderable", so a cycle (a over b, b over c, c over a) cannot occur "outside of
noise"; individual answers can be noisy, but in expectation preferences are transitive (lecture 2,
≈1:02:58, ≈1:03:43). When data violate it, richer features can sometimes explain the violation, and
other model classes, not covered in the course, allow some intransitivity (≈1:04:28). Whether such
violations show that humans are irrational, or that the model or context is wrong, is still debated;
one view is that "if we had sufficient appropriate context we can almost always think of humans as
rational". The course treats rationality as "a pragmatic modeling choice" and will cover cases where
it is "for sure broken" (≈1:05:15–1:06:50).

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
