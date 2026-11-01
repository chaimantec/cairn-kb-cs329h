# Human–AI interaction and human-centered design

The course's methods learn from what people say they prefer. This page collects what the course says
about the **people on the other side of the interface**: why human–computer interaction (HCI) matters
to learning from preferences, how a design process finds the problem worth solving, where the
course's technical tools fit in that process, what it takes for people to trust and rely on an AI
tool appropriately, and how to evaluate a human–AI system.

**Sources so far:** [lecture 5](05-human-centered-design.md) is the main source.
[Lecture 1](01-introduction.md) explains why the course cares about HCI and what it leaves out, and
[lecture 3](03-model-based-preference-optimization.md) shows how hard it is to pose a preference
question people can answer. Lecture 5 calls its own treatment caricatured on purpose: "I'm going to
take somewhat caricatured extreme perspectives on many fields in order to make a point" (lecture 5,
≈1:39). Later lectures are not yet in this knowledge base.

## Why the course cares about HCI

Lecture 1 reports a panel at which someone claimed that within a generation "all of AI will be HCI",
because the hardest and most interesting questions will be about human–computer interaction. Koyejo
finds the case plausible: much of what now blocks the applications we want seems to be how humans fit
into deployed systems (lecture 1, ≈17:40, ≈18:26). He also says the course touches
HCI without going deep, for reasons of expertise and scope, and that HCI experience, including the
practical side of designing a study and getting IRB approval, "will generally serve you well" (lecture 1, ≈29:20, ≈30:07).

Lecture 5 is the course's lecture on the subject. Its thesis is that when people struggle with a
technology, the fault is the design, not the user. Its example is the Norman door, which leaves you
unsure whether to push, pull or slide (lecture 5, ≈2:26, ≈3:13). For language models, the equivalent
is hunting for "the special prompt, magic prompt" that makes the model do what you want. "This is a
failure of our design of the tool" (≈4:46, ≈6:20). Within that frame, learning from human preferences
"is a powerful tool as part of the toolbox of building AI technologies that work better for people"
(≈3:13, ≈4:00).

## Technology-centric and user-centric design

**Technology-centric design** improves the technology for its own sake, against "some abstracted,
metricized user, often like a number that we're chasing" (lecture 5, ≈24:05). Koyejo argues that "a lot
of AI work is roughly in this space", and that it is reasonable when a technology's norms of use are
already established (≈24:05, ≈24:51). **User-centric design** starts from the stakeholders' problems
and needs (≈24:51). The risk on the technology side is that "everything becomes a potential application
of whatever tool you're building" (≈25:36).

He reads the course itself against this. It started from a user-interface problem, abstracted it, and
has so far been "purely technical", and one "could finish an entire PhD here on something like chatbots
or user interface and never do a user study" (≈27:54, ≈28:40). He also reads preference tuning as an
interface fix. By "our best understanding", a base model already "has all the knowledge to do all the
things chatbots do, but it's just extremely hard to interface with". On this view, supervised
fine-tuning and preference tuning "solve the interface problem" (≈27:08), which he calls "an analogy,
not complete". See [RLHF](rlhf.md).

## Design thinking: find the problem behind the problem

Design thinking asks you to "go back and ask why" before solving the stated problem, for several
iterations (the "five whys"), until you reach a root cause (lecture 5, ≈30:10, ≈30:57). The example is
Henry Ford's quote, "if I had asked people what they wanted, they would have said
faster horses" (≈30:57). The **double diamond** organizes it in four stages: *discover* (diverge over
the problem: field studies, interviews, surveys, market research), *define* (converge on root causes:
participatory design, grouping causes, affinity diagrams), *develop* (diverge over solutions:
storytelling, prototyping) and *deliver* (converge on a minimum viable product) (≈32:29–36:20). In
practice the process repeats, an "expanding loop" rather than a single pass (≈37:07, ≈37:52). The
lecture page has the [stage table](05-human-centered-design.md#the-double-diamond).

## Where the course's tools fit

Lecture 5 describes human–AI interaction as a field built from three parts: **humans** (AI
researchers, model developers, domain experts, end users), **AIs** (language models, dialogue and audio
systems, recommenders, autonomous driving), and the **interaction** between them, which may be
collaborative, assistive, or about understanding the AI (≈38:39–40:13). Work in the field proceeds in
three steps: **design** the interaction, **enable** it, and **evaluate** it (≈41:00–42:30).

The course's methods belong to the middle step. "Most of the work in this middle is about tooling, and
most of what we've covered in this class is in some ways you can think of as tools that you can bring
to bear to make the interaction probably easier". The examples are personalization and "getting
pairwise preferences from people" (≈41:45). In its summary the lecture lists AI tools that keep
learning from interactions such as preferences, personalization, and "social choice as an alternative
to hyperpersonalization" (≈1:17:57).

**Asking questions people can answer** is where the two sides meet. Lecture 3's metric elicitation
needs a stakeholder to compare two classifiers by their performance over a whole population. Koyejo
calls posing that question "one of the big gaps in this line of work"; it "needs a fairly sophisticated
stakeholder" (lecture 3, ≈1:06:35, ≈1:08:07). His takeaway is that useful elicitation needs "some
meaningful connection between the algorithmic problem and sort of the human problem" (≈1:09:41). He
said he might return to this in the HCI lecture. The lecture 5 recording does not mention metric
elicitation, but it makes the same point about prompting. PromptCharm's user studies found
"significant conceptual gaps when a novice user writes prompts for image creation": people know the
image they want but cannot put it into a prompt the model follows (lecture 5, ≈48:41). Its answer is
an interface that exposes the automatic prompt rewrite, offers styles and term weights, supports cheap
exploration and history, and shows which image regions each word affected (≈49:28–54:10). See
[asking humans for preferences](preference-queries.md).

## Trust and reliance

**Trust** is "some evaluation of the belief for confidence and reliability, integrity, honesty"; it is
"really a human property", now applied to machines too. **Reliance** is depending on something to
perform a task "irrespective of whether trust is present" (lecture 5, ≈58:44, ≈59:31). Crossing a human
decision maker's choice with whether the AI is right gives four cases (≈59:31, ≈1:00:16):

| | AI is correct | AI is incorrect |
| --- | --- | --- |
| **Human accepts** | appropriate reliance | overreliance (automation bias) |
| **Human rejects** | underreliance | appropriate reliance |

Users miscalibrate both ways. They "either trust too much and don't appreciate the corners of where the
tool can actually work, or they have one bad experience and then think that the tool is garbage"
(≈57:13). What sometimes helps: explanations; showing uncertainty, although "people tend not to be good
at actual percentages" and bucket into low, medium and high; letting users decide when to see
suggestions; and showing that processing is happening, which helps people judge how hard a task is
(≈1:00:16–1:01:46).

On transparency, lecture 5 states both sides. One argument is "that you shouldn't trust models that you
can't understand", and the other is "that we actually don't understand lots of things we trust", such
as aspirin, or MRI for most doctors (≈1:04:08, ≈1:04:53). Fairness, accountability and ethics are
covered on [whose preferences](whose-preferences.md).

## Evaluating a human–AI system

Lecture 5 organizes evaluation by four questions: how, what, who and when (≈1:08:42).

- **How.** Quantitative measures (task completion, accuracy, time) and qualitative ones (surveys, what
  frustrated users) (≈1:09:27). In language models the two diverge: "people's lived experiences with
  models often diverge from what the benchmarks say", which Koyejo reads as a problem with the
  quantification (≈1:10:13). Intrinsic evaluation tests the model alone. Extrinsic evaluation tests it
  inside a real task, which is slower "but it can often reveal gaps in the intrinsic" (≈1:10:59,
  ≈1:11:45). Metrics can be existing validated ones or new ones made for the context (≈1:12:31).
- **What.** The model, the interface, and the end-to-end system, best evaluated separately and then as a
  whole (≈1:13:18, ≈1:14:04). Goals differ. Generated code can be scored by passing tests, by similarity
  to reference code, or by asking "a human to give preferences on the code outcomes" (≈1:14:49).
- **Who.** Lay users, domain experts, or automated evaluation, with "LM as a judge" increasingly popular
  (≈1:15:36). Stakeholder groups such as experts, teachers, parents and students are distinct from
  demographic groups (≈1:15:36, ≈1:16:21).
- **When.** Instantly, over a short interaction, over a deployment of a week or more, or in
  longitudinal studies over months or years (≈1:16:21, ≈1:17:09).

"Evaluation itself becomes a design problem" (≈1:18:44).

## Related pages

- [Lecture 5 — Human-centered Design](05-human-centered-design.md): the full treatment, with every
  student question.
- [Asking humans for preferences](preference-queries.md): the kinds of questions the course asks, and
  what people can answer.
- [Whose preferences](whose-preferences.md): designing for some people and leaving others out,
  fairness, accountability and labelling labour.
- [RLHF and the language-model pipeline](rlhf.md): preference tuning as a solution to an interface
  problem.
- [Metric elicitation](metric-elicitation.md): a worked case where the question posed to the
  stakeholder is the hard part.
- [Lecture 1 — Introduction](01-introduction.md) and
  [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md).
