# Preference aggregation: groups, voting and consensus

Many of the course's questions are about more than one person. How do you combine a class's, a
county's or a country's preferences into one decision, one model or one statement? This page
collects what the lectures in this knowledge base say about that.

**Read this first: the course's own voting lectures are not in this knowledge base.** Lecture 4
refers back to "the voting lectures" and to ideas "we covered already, things like social choice and
voting" (lecture 4, ≈0:05). The schedule's candidate is Oct 7, "Aggregated Preference Models via
Social Choice Theory & Game Theory", which is not in the catalog. The catalog lecture titled *Voting*
([lecture 7](07-voting.md)) is a different session: a guest lecture by Colin Megill on Polis, a
platform for mapping a population's opinions. So this knowledge base has **no account of voting
rules or social choice theory as the course taught them**. Say so when asked, rather than filling
the gap. What follows comes from passing references in other lectures and from lecture 7.

**Sources so far:** [lecture 7](07-voting.md) is the main source. [Lecture 1](01-introduction.md)
raises aggregation as a course question. [Lecture 2](02-preference-models.md) asks whether people
share one utility. [Lecture 4](04-mechanism-design.md) ties mechanism design to social choice.
[Lecture 5](05-human-centered-design.md) names social choice as a design tool, and
[lecture 6](06-ethics.md) sketches moral theories that weigh different people's good against each
other.

## Why aggregation comes up

Lecture 1 frames it as a change of scale. Getting one person's preference differs from getting a
whole class's, when the class will not agree even on the size of project groups. That raises how to
aggregate preferences so that they reflect broader values, and what happens when the people giving
them are strategic and game the system (lecture 1, ≈19:57). Its list of open questions also
includes how things change between one human, a group and a whole society (lecture 1, ≈18:26,
≈19:12). [Whose preferences](whose-preferences.md) takes up the companion question
of *which* people are asked.

## One utility or many

The simplest aggregation is to fit one model to everyone. Lecture 2 lays out the options for a
choice model: a single utility shared by everyone, a separate utility for each person, or per-person
parameters tied together (lecture 2, ≈31:52, ≈32:37). "Almost all the ML applications" pool everyone,
while psychology and economics model individual differences as a signal (lecture 2, ≈55:53). Pooling
is a form of aggregation that never names itself as one. See
[discrete choice models](discrete-choice-models.md).

## Social choice in the lectures that remain

The lectures in this knowledge base mention social choice without teaching it.

- **Lecture 4** presents mechanism design as "a combination of some of the ideas we covered already,
  things like social choice and voting, with some ideas from game theory" (≈0:05). "A lot of what we
  said from social choice also applies here." In particular, "as a designer, it's part of your job to
  decide what the desirable outcome is" (≈10:10). Computational complexity "came up with social
  choice" (≈3:12), and incentive compatibility is something "we covered in social choice briefly"
  (≈28:42). The details of that coverage are in the missing lectures. See
  [mechanism design](mechanism-design.md).
- **Lecture 5** lists "social choice as an alternative to hyperpersonalization" among the ways the
  course's tools can enable a human–AI interaction (≈1:17:57). See
  [human–AI interaction](human-ai-interaction.md).

## Weighing people against each other

Lecture 6 is about ethics, not voting, but its moral theories are rules for combining different
people's good (lecture 6, ≈54:12–57:16; see [value alignment](value-alignment.md)).

- **Consequentialism** counts the net good summed "across all people" (≈54:12).
- **A weighted sum** counts a gain for "someone who's starving and has nothing" for more than the same
  gain for someone better off (≈55:43, ≈56:30).
- **A maximin, or complaint, model** does not care about the sum: "The goal is to minimize the
  strongest individual complaint" (≈56:30).

The transmitter-room case in that lecture shows how far apart these rules can land on the same
situation.

## Consensus across difference: Polis and Community Notes

Lecture 7 describes an approach that does not pick a winner. In **Polis**, participants submit short
statements and vote on other people's: agree, disagree or pass (lecture 7, ≈3:57). Each participant
is a row of a sparse vote matrix, and each statement a column (≈7:02). PCA and K-means find groups
of people who vote alike, and the statements that set the groups apart describe "something like a
worldview" (≈7:02, ≈7:48). The output Megill cares most about is the opposite: "given that we see
groups, what statements are common among people who think differently" (≈7:48). The question is
whether "a diversity of opinion" can be used "to recover signal about where interesting consensus
might be" (≈8:34). In a county land-bank conversation, groups that split over whether the land bank
should keep buying land agreed strongly that public access to conserved land "is compatible with
preserving the natural habitat" (≈23:13, ≈23:59).

He does not settle whether this is voting. He leaves open "how close we think that is to voting, or
whether we think that's, or if it's a survey" (≈35:33), and calls it "an emergent survey", "a survey
created by the people taking it" (≈3:57, ≈4:44).

**Community Notes** on Twitter came out of the same idea (≈8:34, ≈45:37). It uses matrix
factorization "in continuous space" rather than clusters, because Twitter "didn't want to establish
liberals and conservatives as the base clusters" (≈46:25). A note is shown when "people who
historically have voted differently on helpfulness both find it helpful" (≈49:31). Here the goal
changes from mapping opinion to picking "the best or single one that we're going to show"
(≈50:17). Megill's view is that "Community Notes is not a misinformation system. It's actually a
collective response system" (≈50:17).

**Group statements written by a model.** Lecture 7 also describes a DeepMind paper in which an LLM
helps "a group to write a collective statement of themselves", aiming for "higher and higher approval
on that statement", and people "like the LLM better than the human" facilitator (≈36:19, ≈37:05). A
Polis prototype would show such a statement back for rating. The hard part is that "the votes come
in over time", so the groups a statement summarizes can change after it is rated (≈40:12, ≈40:59).

## How the approaches compare

| Approach | What is combined | What comes out | Lecture |
| --- | --- | --- | --- |
| Pooled choice model | Everyone's choices, treated as one population | One utility function | 2 |
| Mechanism (an auction) | Bids from strategic participants | An allocation and payments | 4 |
| Moral theories | Each person's good | A right act: the largest sum, a weighted sum, or the smallest worst complaint | 6 |
| Polis | Agree, disagree and pass votes on participants' own statements | Opinion groups, and statements different groups agree on | 7 |
| Community Notes | Helpfulness ratings of proposed notes | One note, shown when raters who usually disagree both rate it helpful | 7 |

## When participants game it

Aggregating many people invites strategic behaviour, which lecture 1 lists among the course's
questions (≈19:57). Lecture 4's answer is mechanism design: rules, often with payments, under which
telling the truth is the best strategy. Lecture 7's answer for Polis is a small attack surface:
moderators gate statements, so participants can only "agree, disagree or pass on statements", and
packing a conversation with your own people mostly makes "one group getting larger" (lecture 7,
≈12:27). Bots change that. They can fake whole clusters, which turns the problem into "an arms race
that just gets to identity" and makes the sample the real question (≈13:12). Megill calls "synthetic
experts" "probably the most dangerous thing" (≈19:21). Detecting a synthetic group is "an open area
of research" (≈15:31). See [lecture 7](07-voting.md#can-it-be-gamed) and
[whose preferences](whose-preferences.md).

## Related pages

- [Lecture 7 — Voting (guest lecture on Polis)](07-voting.md): the full treatment, with every
  question.
- [Whose preferences](whose-preferences.md): which humans are asked, synthetic participants, and
  representation.
- [Mechanism design](mechanism-design.md): aggregation with strategic participants and payments.
- [Value alignment](value-alignment.md): the moral theories of lecture 6.
- [Discrete choice models](discrete-choice-models.md): pooled and individual utility models.
- [Asking humans for preferences](preference-queries.md): the query formats behind each approach.
