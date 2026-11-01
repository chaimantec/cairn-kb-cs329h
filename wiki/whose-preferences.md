# Whose preferences: representation, labour and ethics

Learning from human preferences means choosing *which* humans. That choice shapes what a model ends
up valuing, and the work of supplying preferences has costs of its own for the people who do it.
Lecture 1 says this course will "almost always have a meaningful ethical angle" and will "not shy
away" from it (≈19:57, ≈21:29).

**Sources so far:** [lecture 1](01-introduction.md), [lecture 2](02-preference-models.md) on
modelling individuals separately or together, and
[lecture 3](03-model-based-preference-optimization.md) on fairness measures that disagree, and
[lecture 4](04-mechanism-design.md) on who decides what outcome a mechanism aims for and on paying
labellers by harm, and [lecture 5](05-human-centered-design.md) on designing for some people and
leaving others out, fairness, accountability, and stakeholder groups in evaluation. Lecture 5 defers
accountability, fairness, transparency and ethics to "a separate lecture" (≈57:58). The catalog has a
later lecture titled *Ethics* and one titled *Voting*. Neither is yet in this knowledge base.

## Choosing the humans

When you build and deploy a system, you pick who gives you the signal and whose preferences the model
is aligned to, and "that choice has an effect downstream" (lecture 1, ≈20:44). Some effects are
positive and some "can be tricky and look exploitative" (≈20:44).

The problem changes with scale. Getting one person's preference differs from getting a whole class's,
when the class will not agree even on the size of project groups. That raises the questions of how to
**aggregate** preferences in ways that reflect broader values, and of what happens when participants
are **strategic** and try to game the system (≈19:57).

Lecture 4 treats strategic participants through [mechanism design](mechanism-design.md), and it
makes a point that applies to aggregation generally: the person designing the mechanism chooses the
goal. When a student asks whether charging a buyer the most they will pay is a good social outcome,
Koyejo answers that "it's up to the designer to decide what a socially valuable outcome is"
(lecture 4, ≈9:24). Many framings use maximal revenue; welfare is an alternative, and a designer
could build for some other notion of social good (≈9:24–10:55). He notes that there are
philosophical arguments for "capitalist-style revenue maximization" without endorsing or going into
them (≈10:55, ≈11:40).

**Representative sampling.** A student asks whether the course will cover sampling humans across
groups, as one samples data across scenarios, so that the preferences represent all groups (≈21:29,
≈22:15). Koyejo says at least one lecture engages with it, "though I don't think deeply enough", and
that "I don't think the literature is complete on this question". There is some work on preference learning
across groups, through representative sampling or other ways of balancing preferences. The ML subfield
is "fairly early on", with more work in economics and ethics, and he suggests it as a project direction
(≈22:15, ≈23:01).

## One model for everyone, or one each

A choice model has to decide whether different people share one utility. Lecture 2 lays out the
options: a single shared utility, treating everyone's choices as observations of one model; a
separate utility for each person, with no benefit from modelling them jointly; or per-person
parameters tied together, additively or as a low-rank set (≈31:52, ≈32:37). "Almost all the ML
applications" pool everyone. Choice models in psychology and economics model individual differences,
because they treat them as an important signal, and machine learning is "slowly understanding" that
they might matter more and more (≈55:53, ≈56:39). See
[discrete choice models](discrete-choice-models.md).

## Designing for some people, and leaving others out

Lecture 5 raises the same choice from the design side. Ease of use depends on who the users are and
how they were educated, so the right way to frame a design question is "really deeply contextualized.
So who are the people? What are you trying to solve? How do we solve the problem for these people?"
(lecture 5, ≈22:34). That brings an equity question: "if I'm designing for a particular set of people,
am I leaving a bunch of other people that could benefit out?" (≈23:20). Contextualizing forces you to
think about your audience and then about how to broaden it (≈23:20).

The lecture lists fairness and accountability among the things interactive systems must be designed
for (≈57:58). **Fairness** means tools that do not "behave very differently" across gender, sex, other
demographics or socioeconomic factors (≈1:01:46, ≈1:02:33). **Accountability** means thinking through
the consequences of mistakes. A mistranslation is low-risk when you are playing with a chatbot and
high-risk when it is used in an asylum decision: "This is someone's life", and "this happens,
actually, it's a big issue" (≈1:02:33). Stakeholders such as the user or a judge should understand a
tool's gaps, so that accountability is correctly placed (≈1:03:21).

Who evaluates a system is a related choice. Koyejo separates **stakeholder groups**, such as experts,
lay users, teachers, parents and students, from **demographic groups**, and says the target group
makes a big difference to how an evaluation is designed (≈1:15:36, ≈1:16:21). Closing the lecture, he
names "social choice as an alternative to hyperpersonalization" as one of the course's tools for
enabling human–AI interaction (≈1:17:57). See [human–AI interaction](human-ai-interaction.md).

## Whose opinions models end up with

Lecture 1 describes a Stanford paper (not named in the audio) that gave a language model the **Pew
survey**, which Pew uses to measure values and preferences across societies and demographic subgroups
(≈1:03:21). The authors checked how well the model's answers correlated with each group's, for example
conservatives with less than a high-school education earning under \$30,000 (≈1:04:08). Asked which
group matched best, students guessed the US, then California. The answer: "very California, very US,
very around here". Language models "like to be Californian, Stanford, Palo Alto kind of people"
(≈1:04:53).

Koyejo's explanation is who shapes the model. Labelling may be done all over the world, but much of
the intervention comes from people who work here and whose political opinions and preferences match
those of people who live here, "and so these kinds of preferences get embedded in language models"
(≈1:04:53, ≈1:05:41). The course aims to understand how this happens, intentionally or not, and to
critique what ends up embedded, since it can have downstream effects (≈1:05:41).

A related warning about what raters reward, long answers and bullet points, is on
[reward hacking](reward-hacking.md#in-language-models-long-answers-and-bullet-points).

## The labour of labelling

Supervised fine-tuning data often needs experts, but pairwise preference data is often outsourced to
places where labour is cheap (lecture 1, ≈1:01:03, ≈1:01:48). Koyejo calls the ethics "tricky" and not
"cut-and-dried": in some places it can be a good job (≈1:01:48). But these are often the same places
that do content moderation. The people improving the models may be shown the worst a model can produce,
including deeply unethical or traumatic images that may leave them needing psychological help
(≈1:01:48, ≈1:02:35). He calls it "a challenging open question" that the field engages with only a
little (≈1:02:35).

Paying annotators is also part of why academic preference data is scarce: "you want to pay the people
that are giving you signals or preferences" (≈44:50). See [RLHF](rlhf.md#who-does-this-work).

**Paying by harm.** Lecture 4 presents one proposal from Koyejo's group for the problem lecture 1
calls open. Labelling "potentially toxic or psychologically difficult material, both text and image
completions" is part of building modern generative systems (lecture 4, ≈1:15:17). If individual harm
can be connected to an economic value, labellers could be paid according to how much a task is
likely to harm them. A more sensitive item, or a more sensitive person, would be paid much more
(≈1:15:17, ≈1:16:03). One argument for this is fairness: "your payment should be correlated with how
much harm you might be suffering from engaging in that task" (≈1:16:49). Because people asked
directly would have "some incentive to be strategic" (≈1:17:36), the pay is set by a **reverse auction** run on harm
predicted from pairwise feedback (≈1:17:36–1:19:09). The audio reports that it needs much less
information than the baselines and has lower regret than a uniform allocation (≈1:19:09, ≈1:19:55).
Koyejo hedges it three times. It is "not a perfect solution", "not a normative claim that this is
necessarily a good idea", and one lever among several for making the labelling ecosystem "less
psychologically damaging" (≈1:15:17, ≈1:16:03, ≈1:16:49). See
[lecture 4](04-mechanism-design.md#paying-labellers-by-harm-a-reverse-auction).

## Disagreement as a reason to elicit

Disagreement is also a reason to use preferences in the first place. For targets such as healthfulness
or fairness there are "many, perhaps reasonable, definitions of what good is" that "don't all agree".
Interacting with a large stakeholder group is a way to specify a target (lecture 1, ≈57:11). See
[metric elicitation](metric-elicitation.md), which lists fairness problems and stakeholder groups among
its applications.

Lecture 3's example is **recidivism prediction**, a tool used to help judges in sentencing (≈27:43,
≈28:29). The captions name the company "North Point" and the algorithm "compass". Its makers built
it to a fairness notion. Roughly, for different bins of predicted risk, outcomes should be similar
across demographic groups (≈28:29). ProPublica's later analysis used differences in false positive
and false negative rates across groups instead. It found "black defendants were twice as likely to
be incorrectly labeled as higher risk than white defendants" (≈29:15). Koyejo's point is that the
claim the algorithm ignored fairness "is incorrect". Two "maybe well-meaning actors" with different
normative views picked different measures and reached completely different conclusions about the
same results (≈30:03, ≈30:48).

The case helped end the hope, which he says had "maybe a bit of naivety", of one golden fairness
measure that holds everywhere. The **impossibility results in fairness** followed. Roughly, "you can
pick one, maybe two measures to sort of try to maximize at the same time, but you can't pick three",
so there is "no universality" (≈30:48–32:22). Metric elicitation is Koyejo's group's response. "There
is not a right answer, but perhaps for particular stakeholders there's a right answer for them", so
the tool helps each stakeholder find theirs (≈33:08).

## Related pages

- [Asking humans for preferences](preference-queries.md): rationality, noise and strategic behaviour.
- [Discrete choice models](discrete-choice-models.md)
- [Lecture 1 — Introduction](01-introduction.md)
- [Lecture 2 — Preference Models](02-preference-models.md)
- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md)
- [Lecture 4 — Mechanism Design](04-mechanism-design.md)
- [Mechanism design](mechanism-design.md): strategic participants, and who chooses the objective.
- [Human–AI interaction](human-ai-interaction.md): trust, reliance, transparency and evaluation.
- [Lecture 5 — Human-centered Design](05-human-centered-design.md)
