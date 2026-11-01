# Asking humans for preferences: queries, comparisons and noise

Every method in this course starts by asking people something. This page collects what the course
says about *how* to ask: absolute ratings or comparisons, one-shot or interactive collection, how
many questions to ask, and what to assume about the answers.

**Sources so far:** [lecture 1](01-introduction.md) only. The models of human choice that the course
builds on these queries start in later lectures, which are not yet in this knowledge base.

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

**Dueling bandits** are bandit problems with pairwise preferences built in. The course will use them
as a framework for interactive comparison problems like the exoskeleton (≈1:07:58).

## One-shot versus interactive collection

In the language-model pipeline, collecting demonstrations for supervised fine-tuning is "mostly
one-shot": a large offline effort to get good examples. Collecting preferences "is typically best done
interactively", although some work does it offline. The course covers the technical differences
(lecture 1, ≈38:40).

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

The course's working assumption is stated plainly. Most of the work assumes "some kind of rational
human": there exists a reward function, "some sort of explicit deterministic function that tells us
what a human would prefer", even when it is not written down, and the models are built on it. "But it
is an assumption", and at least one invited talk will challenge it (lecture 1, ≈1:14:55, ≈1:15:40).
The technical core is **discrete choice** and the **parametric models** built around it (≈1:15:40).

## Related pages

- [Whose preferences](whose-preferences.md): who gets asked, and what that does to the model.
- [Reward hacking](reward-hacking.md): what goes wrong when a model optimizes against learned
  preferences.
- [Lecture 1 — Introduction](01-introduction.md)
