# Lecture 1 — Introduction

The opening lecture sets out what "machine learning from human preferences" means in this course
and why it is worth a course of its own. Sanmi Koyejo starts from a working definition: the
course studies how to elicit values and preferences from individuals, groups or societies
**efficiently** (with as few human interactions as possible) and **effectively** (getting a good
signal), and how to embed them in AI models. He then narrows the field. In one sense all of
machine learning learns from humans, because people produce the data. This course focuses on
settings where the human signal is **explicit and intentional**, often gathered **interactively**.
The rest of the lecture surveys where that happens: the RLHF pipeline behind modern language
models, a long student discussion about whether reward models are needed at all, why people turn
to preferences in the first place, what still goes wrong (length and bullet-point bias, reward
hacking, whose opinions models end up reflecting), and applications beyond language. Those
applications are an exoskeleton tuned by pairwise comparisons, metric elicitation for
classification trade-offs, recommender systems, and reinforcement learning. Course logistics come
first, and the lecture is unusually interactive: about a quarter of it is student questions.

**No slides.** The lecture is given from slides, refers to them often ("the references are in the
slides", ≈34:00), and says a link to the textbook is on them (≈2:24). The course has not published
them, so every claim here is cited to the transcript by timestamp. Several papers the lecture shows
are **not named in the audio**: the human-feedback taxonomy figure (≈30:07), the summarization
results (≈54:52), the Pew-survey study (≈1:03:21), the exoskeleton work (≈1:05:41) and the 2008
helicopter work (≈1:12:36). This page describes them as the lecture does and does not guess the
citations.

**The recording ends** at about 1:17, just as Koyejo says "next we'll start on material on some
existing choice models for the rest of the lecture" (≈1:16:26). That material is not in this video.

[Edited transcript](../raw/transcripts/01-introduction.md) ·
[verbatim captions](../raw/transcripts/original/01-introduction.md) ·
[video](https://www.youtube.com/watch?v=ApF2OenMgfc) ·
[course website](https://web.stanford.edu/class/cs329h/fall2024/) · [sources](../sources.md)

## Who teaches it

Koyejo introduces himself as computer-science faculty working broadly in trustworthy machine
learning and AI (≈0:05). He has been at Stanford a couple of years and was previously a professor
at the University of Illinois. He has worked for a while on getting human preferences into classic
machine-learning problems, notably through a framework called
**[metric elicitation](metric-elicitation.md)** (≈7:00, ≈7:47). He places that work alongside
related ideas in reinforcement learning, and the caption there is garbled ("MSRL"; probably inverse
reinforcement learning, but unconfirmed). He says the area became exciting again "with language
models and RLHF being a thing" (≈7:47). The teaching fellow is **Sang** (Sang Truong, per the
course website), introduced at ≈0:05. A short passage at ≈8:33 ("I work on papers on this topic")
may be another staff member speaking. The captions do not make the speaker clear.

## How the course runs

This is the course's **second offering**; it was first taught the previous fall. Koyejo expects
it to be "slightly less experimental than last time" but with rough edges, and asks for feedback
(≈0:52). It aims to be foundational "in a broad sense", reaching into economics and psychology as
well as machine learning ("we'll play amateur everything", ≈1:37). Some topics are taught by the
core staff and some by invited speakers (≈1:37, ≈3:11).

**Textbook.** The staff have written a textbook. Koyejo knows of no other textbook on the topic,
"or if there is, it's not public". He calls it "a very rough cut" and asks for criticism (≈2:24).
It is now online at [mlhp.stanford.edu](https://mlhp.stanford.edu/), but that is a later revision
than the one this lecture refers to; see [sources](../sources.md).

**Structure.** After the introduction there are four parts (≈2:24, ≈3:11):

1. modelling human choice;
2. model-based techniques and preference learning;
3. model-free optimization;
4. human values and AI alignment.

Invited lectures follow the modules, the first in early October (≈3:11). The schedule on the
course website groups the term a little differently, under three themes: *Preference Models*,
*Preference Measurement & Optimization*, and *Value, Alignment, & Human-centered Design*.

**Assessment.**

- **Homework.** This is the first offering with homework; the first offering was "purely
  discussion and lecture". Homework is 60% of the grade, and the first assignment was due out "in
  about a week or so". The questions are new, so expect "some wrinkles" (≈3:58).
- **Project.** There is "a big focus on projects": groups of up to five, a series of deliverables,
  and a final project presented to the class and possibly externally (≈4:43).
- **Participation.** It carries "a meaningful load" because the course is still being worked out.
  It includes feedback on the textbook through GitHub, answering questions on Ed, and speaking up
  in class (≈4:43, ≈5:29).

**Who it is for.** For CS PhD students it counts toward either the *Learning and Modeling* or the
*Human and Society* breadth requirement. Koyejo stresses that it is still a technical course that
"will always fall back on machine learning fundamentals", aiming for "breadth and depth at the same
time, with a slight bias towards breadth" (≈6:14, ≈7:00). The prerequisites are the basics of
machine learning and enough programming to build simple models. Train/test/validation splits and
logistic regression "should not be surprising to you"; if they are, "we should have a quick chat"
(≈16:55, ≈1:16:26). It is a small-to-medium class, run for discussion (≈3:58).

## What the course is about

Koyejo offers a definition the staff "mocked up" and invite the class to critique (≈9:18):

> This class seeks to explore the challenge of efficiently and effectively eliciting values and
> preferences from individuals or groups or societies and embedding them within AI models and
> applications. Our specific focus will be on some of the statistical and conceptual foundations
> and strategies for interactively querying humans to elicit information that can improve learning
> and applications.

He unpacks two of its words:

- **Efficiently** is about how costly it is to interact with people. The aim is to learn what you
  need from as few interactions as possible. The term for this is **query efficiency**: how many
  samples or interactions you need to get a particular estimate or function from a set of agents
  (≈10:04, ≈10:49).
- **Effectively** is about the quality of the elicitation process: "getting the signal from
  people" (≈10:49).

### Why "interactively"

A student asks why the definition says *interactively* (≈11:36). Koyejo's answer explains the
course's scope. "From a certain point of view, all of machine learning is learning from human
preferences": almost every application involves humans creating or labelling content that models
then learn to mimic. Read that way, the phrase "doesn't narrow the field at all". So the course
focuses on settings where the learning procedure is **explicitly** about learning from preferences,
often through an interactive process. Ordinary labelled data counts as *implicit*: a preference
effect is baked in by whoever did the labelling, but the learning is not designed around it
(≈12:21, ≈13:07).

A student welcomes the broader framing because real data sets are not fixed facts about the world.
Humans "don't agree with themselves 25% of the time", and the same person gives a different label
depending on whether they have had lunch. So a model of the labelling process itself belongs in the
system (≈13:07, ≈13:52). Koyejo agrees that human inconsistency is a real issue the course will
take up. The standard models of a comparison are **Bernoulli models**, "I don't know if that's the
truth", and part of the course is how to treat noise or uncertainty from inconsistent human signals
(≈14:37). See [asking humans for preferences](preference-queries.md).

## Three threads: the learning problem, the human, and ethics

The course works through three threads together.

**The machine-learning problem.** The course concentrates on learning systems with explicit
human-in-the-loop components, leaning towards interactive ones (≈15:23). It draws on foundations
from economics, psychology, marketing and statistics. Applications come from language, which is
"front of mind for many of us", and also robotics and logistics: planning delivery or routing with
the preferences of the people involved taken into account (≈15:23, ≈16:08). Each problem is
handled "through the view of machine learning": set it up, understand its angles, then study
modelling, estimation and evaluation (≈16:08).

**The human.** Depending on where you sit in machine learning, Koyejo says, there is "some
aversion to thinking about humans, even though humans are everywhere" (≈17:40). He reports a panel
the week before where someone claimed that within a generation (perhaps 5 to 10 years) "all of AI
will be HCI", because the hardest and most interesting questions will be about human–computer
interaction. Koyejo finds the case plausible. Algorithms have made real progress, and much of what
blocks the applications we want now seems to be how humans fit into deployed systems (≈17:40,
≈18:26). The questions this raises:

- human biases;
- whether to assume humans are rational;
- when treating human error as noise is a good or a bad assumption;
- correctness and expertise;
- how things change between one human, a group and a whole society (≈18:26, ≈19:12).

For example, does getting one person's preference differ from getting the whole class's, when the
class will not agree even on project group sizes? How should preferences be aggregated so as to
reflect broader values? What happens when the people giving preferences are **strategic agents**
gaming the system (≈19:57)?

**Ethics.** "We'll almost always have a meaningful ethical angle" (≈19:57, ≈20:44). The basic one:
whoever builds a system picks *which* humans give the signal and whose preferences the model is
aligned to. That choice has downstream effects, some positive, some "tricky and [can] look
exploitative" (≈20:44). See [whose preferences](whose-preferences.md).

A student asks whether the course will cover sampling humans across groups, as data is sampled
across scenarios, so that the preferences represent everyone (≈21:29). Koyejo says at least one
lecture touches on it, "though I don't think deeply enough", and that the literature is incomplete.
The ML subfield is "fairly early on", with more work in economics and ethics, and he suggests it as
a good project direction (≈22:15, ≈23:01).

A student asks whether the course covers **learning from limited samples**. Koyejo says it does,
implicitly and everywhere: querying humans is expensive, so almost every problem in the course runs
under a budget on sample size. That is where "tricks of the trade" such as pre-training and
foundation models come in (≈23:48, ≈24:37).

## What the course deliberately leaves out

Koyejo marks several neighbouring areas as important but out of scope (≈27:47–≈31:42):

- **The "catch-all" senses of the phrase.** Everyone who builds a model makes preference decisions
  about the problem, the data, the architecture, the loss and the optimizer, and those choices
  shape what comes out. So does the expert knowledge built in as inductive bias, as in graphical
  models and causal inference. He cites the argument that convolutional networks succeeded partly
  because convolution matched something about human vision (≈28:34, ≈29:20). "This is not what we
  mean."
- **HCI in depth.** The course touches on human–computer interaction but does not go deep, for
  reasons of expertise and scope. HCI experience "will generally serve you well", including the
  practical side, such as designing a study and getting IRB approval, which many on campus have
  never done. He encourages projects that take this on (≈29:20, ≈30:07). The course's lecture on the
  subject is [lecture 5, Human-centered Design](05-human-centered-design.md).
- **Human feedback across the whole ML pipeline.** He shows a taxonomy figure from a recent paper,
  borrowed from a colleague's slides whose name the captions lose. It shows human feedback shaping
  data selection, labelling, model selection, training, evaluation, deployment and context
  (≈30:07, ≈30:54). He also mentions judgments embedded in synthetic data and in constraint
  specification, including elicitation mechanisms for specifying constraints in logistics and
  planning (≈30:54, ≈31:42).

## Language models: where most people meet preference learning

"Just to get the elephant out of the way": GPT got many more people excited about learning from
feedback. It has been argued "quite strongly" that work on aligning to human preferences, through
methods such as **RLHF**, made a large difference to how good language models feel to use (≈32:27).
Koyejo stresses that this builds on a long history (≈33:13).

**Earlier forms of human feedback in language systems** (≈33:13–≈35:37):

- document-level interaction;
- label-consistency queries to humans or experts;
- word-level interaction, where a human marks which terms are most influential;
- human help choosing which features to add or remove, which he says is still part of most MLOps
  frameworks and large deployed systems;
- human help selecting model parameters and diagnosing where models fail.

His example is **parsing**. Given "Pat ate the cake on the table that I baked last night", a parser
might attach *baked* to *the table*. A human correction that "I baked the cake" can then be fed back
in to improve the parser (≈34:49). Language models now handle many such problems with less explicit
intervention, but how to get that feedback efficiently is still an interesting question (≈35:37).

**The RLHF pipeline**, as the lecture lays it out (≈36:23–≈40:13); see
[RLHF](rlhf.md) for the full treatment:

1. **Pre-training.** Train a model to predict the next word on web data.
2. **Supervised fine-tuning (SFT).** Collect examples of questions with answers from "somewhat
   knowledgeable humans", often on the order of thousands, far fewer tokens than the web data. The
   objective is still next-token prediction, but the model gets better at answering questions.
3. **Comparison data.** Show a human a query and several completions and ask which they prefer.
   The commonest form is **pairwise**; with four candidate responses the person might pick one of
   the four. "Typically this is discrete choice."
4. **Optimization.** Use the preference signal to improve the model, most popularly with a
   reinforcement-learning algorithm such as **PPO**. Over time the model becomes more likely to
   produce the completion a human expert would have picked.

Koyejo notes that steps 3 and 4 ("two and three" in his numbering, which starts after
pre-training) are typically done together. He also contrasts the two human-data steps. Collecting
SFT demonstrations is "mostly one-shot", done offline. Collecting preferences "is typically best
done interactively", though some work does it offline, and the course covers the technical
differences (≈38:40). Preferences can be read narrowly, as preferences between completions, or
broadly, as people embedding their values about what a language model should do (≈38:40, ≈39:28).
The course concentrates on the preference step.

Asked how much the course will implement the optimization step, Koyejo says "a meaningful
amount". Students will build systems and test methods such as RLHF and DPO on language models, in
homework and certainly in projects (≈40:13, ≈41:00). On **reinforcement learning from AI feedback**,
where AI judgments replace human ones, the course will not spend much time. The machine-learning
side is effectively the same, with differences in how queries are made, so the material should
transfer (≈41:45).

The lecture later shows **results from an early paper on summarization** (unnamed in the audio). A
generic pre-trained model is "noisy, not that bad, not that great". Supervised fine-tuning improves
it meaningfully, and explicit human feedback improves it meaningfully further. Example outputs
compare a human reference, an SFT model and a human-feedback model (≈54:52, ≈55:38).

### Industry, academia and data

A student notes that much pure ML research stops at pre-training plus SFT and asks why (≈43:17).
Koyejo agrees that most published work on real-world learning from human preferences comes from
industry (≈44:03). Collecting good preference data takes more process, which companies either find
easier or hand to dedicated teams, and it costs money, since you should pay the people giving you
the signal. In academic work compute is already a sunk cost and human data is an extra one
(≈44:03, ≈44:50). There are few public preference data sets, and the course frames much of its
work around synthetic or existing ones (≈44:50, ≈45:37). Most interesting large language models
are not academic. He names **OLMo**, from AI2 in Seattle, as one effort to build large models end
to end. He adds that well-known work such as **DPO** uses existing public data (≈46:25).

On compute: GPUs or credits are "almost definitely" coming, scale not yet settled. "The bottleneck
of academic work in this space is compute, almost always" (≈42:32). Homework will be "a mix: some
conceptual, a fair amount of implementation" (≈43:17).

## Do we need a reward model?

The longest discussion in the lecture is about reward models. It starts with a student asking
whether there are downloadable reward models or whether you must build your own (≈47:12).

Koyejo calls it "a great project question". There is now more effort to share reward models
publicly, including **RewardBench** (the speaker's name is lost in the captions) and other public
infrastructure (≈47:12). But in language, training a reward model separately and then training a
language model against it "tends not to work all that well". The most successful implementations
update the reward model and the language model together, collecting data as the model improves
(≈47:58). Mechanically, a reward model is almost always the language model itself with its output
head cut off and a classifier put on the end, so it is "as big as your language model" (≈47:58,
≈48:45). Why reward models and language models don't plug and play is "not fully known". One
hypothesis is distribution shift. Another is that the reward model learns only a local
approximation that is useful for updating one particular language model, rather than human
preference itself. "I don't think we know the answer" (≈48:45, ≈49:30).

A student points to work that does away with an explicit reward model, such as **DPO**, and asks
whether there is still a case for one (≈49:30, ≈50:16). Koyejo says the course covers both sides
(≈50:16, ≈51:02):

- **Without an explicit reward model.** A whole section learns from pairwise signals directly.
  DPO appears there, and so do **bandits**.
- **With an explicit reward model.** Other methods learn a reward model and use it in the
  optimization.

The community pursues both. Doing without one is computationally cheaper, because reward models
are big. In RL, too, settings that allow **behaviour cloning** treat the problem as regression with
no reward model (≈51:02).

His own view is that the reward model is **valuable as an artifact**. It may tell us something
about human preferences that we can examine offline, it helps evaluation, and it can show where
things are breaking. "Most of the field doesn't take that view": if you get similar performance
without one, many implementations drop it. "The short answer is you don't need it. In practice,
many people prefer not to have it" (≈51:02, ≈51:48, ≈52:34).

A student pushes back from experience (≈52:34, ≈53:21). Reward models were used for nothing but
training a better agent "up until o1". o1-style systems sample many candidates ("I just sample a
thousand") and use a smaller reward model to pick between them, which makes the reward model useful
in its own right. But then it must generalize beyond its local preference data, and **it is easily
hacked**: optimize hard against it and the policy finds outputs that score well without being good.
Koyejo agrees the course will cover this kind of overfitting to reward models. He says RewardBench
is motivated by examining reward models to learn what they have learned, and that he would like to
argue for keeping them around more. "The jury is out" (≈53:21, ≈54:06). See
[reward hacking](reward-hacking.md).

## Why learn from preferences at all

Koyejo gives several reasons, noting that different people care about the problem for different
ones (≈55:38–≈58:44):

- **No metric exists.** If you want a funny chatbot, "I don't know what the equation is that
  quantifies funny". But people can say which of two statements is funnier, and that comparison is
  a training signal. Preferences help wherever rewards, costs or losses are hard to write down and
  humans are good judges (≈56:23, ≈57:11).
- **Stakeholders disagree about the target.** Healthfulness and fairness have many reasonable
  definitions that don't agree. Interacting with a large group of stakeholders is a way to specify
  a target (≈57:11).
- **An ideal you can recognise but not specify.** Evaluation signals can stand in for behaviour you
  cannot fully describe. The course will see this when it builds synthetic evaluators (≈57:59).
- **A practical way to fix problems.** Sometimes nobody cares about preferences as such; humans are
  just good at spotting and fixing a class of errors. For one spelling mistake, fix it directly. For
  a broad range of them, having labellers point out the kinds of mistake can be cheaper than
  specifying every case (≈57:59, ≈58:44).

So the motivations run from caring about values or preferences for their own sake to using them as
a proxy for some real-world outcome (≈58:44).

## What is still missing

Despite rapid progress, "there are still lots of places where we know that we're missing
something" (≈59:31):

- **Length and bullet points.** Chatbots tend to give long answers with bullet points. These are
  apparently "the two strongest signals" in both human preference and language-model bias. To get
  a good reward score, "make the answer long and give lots of bullets, whether or not you actually
  answer the question" (≈59:31, ≈1:00:17).
- **Unreliable preferences and reward hacking.** In many settings human preferences are
  unreliable, and models exploit the gap (≈1:00:17). See [reward hacking](reward-hacking.md).
- **Hallucination.** Errors on factual queries may be traceable to something missing from how
  models are built and trained (≈1:01:03).
- **The ethics of labelling work.** SFT data often needs experts, but pairwise preference labelling
  is often outsourced to where data from individuals is cheap. Koyejo calls this "tricky" and not
  "cut-and-dried", since it can sometimes be a good job (≈1:01:03, ≈1:01:48). The same places often
  do content moderation. The people improving these models can be shown the worst a model produces,
  including deeply unethical or traumatic images that may leave them needing psychological help
  (≈1:01:48, ≈1:02:35).

**Whose opinions do language models reflect?** Koyejo describes a Stanford paper he likes (unnamed
in the audio) that gave a language model the **Pew survey**, which is used to measure values and
preferences across societies and demographic subgroups (≈1:03:21). The authors asked how well the
model's answers correlated with each group's, for example conservatives with less than a high-school
education earning under \$30,000 (≈1:04:08). He asks the class which group matched best. Students
guess the US, then California. The answer: models come out "very California, very US, very around
here"; language models "like to be Californian, Stanford, Palo Alto kind of people" (≈1:04:53).
He explains this by who intervenes in the models. Labelling may happen all over the world, but much
of the shaping is done by people who work in this area and share its political opinions (≈1:04:53,
≈1:05:41). Understanding how such preferences get embedded, intentionally or not, and critiquing
the result, are both in scope (≈1:05:41). See [whose preferences](whose-preferences.md).

## Beyond language

"We talk a lot about language. It's hard to avoid, but there's lots of other stuff" (≈1:05:41).

**An exoskeleton tuned by comparisons.** Colleagues at Caltech build an exoskeleton that helps
people who have lost control of their legs to walk (≈1:05:41, ≈1:06:26). Calibrating it means
tuning an array of settings to a response curve personal to each user, and the most reliable signal
is what the user says about how well it works (≈1:06:26, ≈1:07:11). You could ask an absolute
question: is this setting a four out of five? The group found, as the course will argue for many
applications, that **preference queries worked a lot better**. Ask the user to compare two
settings, and let the algorithm use the pairwise answers to tune the array (≈1:07:11, ≈1:07:58).
The course will cover **dueling bandits**, bandit problems with pairwise preferences built in, as a
framework for problems like this (≈1:07:58). See [asking humans for preferences](preference-queries.md).

**Metric elicitation.** Many classification problems have no clear measure of success, or have
asymmetric trade-offs where different errors cost different amounts. In medicine, for instance, a
false positive and a false negative do not cost the patient the same (≈1:08:43). Koyejo's group has
worked for several years on getting pairwise preferences from humans to tune a learning model to
expert judgment. The work covers classification, fairness problems, learning from stakeholder
groups and empirical evaluation in real settings (≈1:08:43, ≈1:09:31). The related, more recent
**inverse decision theory** runs decision theory backwards. Decision theory goes forward, from a
probabilistic model of the world to a decision. The inverse asks what trade-off a decision maker is
using, and in classification "trade-offs almost always boil down to thresholds" (≈1:09:31,
≈1:10:16). See [metric elicitation](metric-elicitation.md).

**Recommender systems.** "A lot of our world now is driven by recommendation systems", from movies
to audio (Spotify, Netflix) (≈1:10:16, ≈1:11:04). Koyejo recalls the **Netflix Prize**, a million
dollars for whoever could improve Netflix's recommendation algorithm. He entered and didn't win, "we
weren't even close". Like most entrants, he used heavy algorithms aimed at mean squared error
(≈1:11:04). At bottom the field is about modelling human preferences over items, and it has
produced a literature on kinds of query and feedback: thumbs up or down on a single item, pairwise
preferences, rankings and ratings (≈1:11:49).

**Reinforcement learning.** The lecture shows a video of 2008 work that it describes as the first
time RL algorithms learned a policy from human demonstrations to fly a helicopter, "way ahead of its
time" (≈1:12:36). It mentions work by Koyejo's colleague Dorsa and her students on preference
learning for RL, including learning from demonstrations and modelling comparison data (≈1:12:36,
≈1:13:21). RL "has engaged with this problem for a long time", and the course draws on it
(≈1:13:21). He then shows the now-famous **boat video**. A game-playing agent is meant to
complete a course, but the reward is the score. It learns to repeat one pattern, hitting targets
that respawn on cue again and again, and scores highly without finishing. "Sometimes this is called reward hacking"
(≈1:13:21, ≈1:14:07). See [reward hacking](reward-hacking.md).

## The assumptions the course starts from

Koyejo closes the survey with the factors that shape these problems (≈1:14:55):

- how hard it is for a human to specify the signal;
- what correctness means, and what happens when there is no correct answer;
- truthfulness and strategic behaviour;
- the role of mistakes and expertise.

He is explicit about the starting assumption. Most of the course assumes **some kind of rational
human**: there exists a reward function, even when it is not written down, "some sort of explicit
deterministic function that tells us what a human would prefer", and the models are built on it
(≈1:14:55, ≈1:15:40). "But it is an assumption", and at least one invited talk will question
whether it is reasonable and what to do if it is not (≈1:15:40). The technical core is **discrete
choice** and the **parametric models** built around it, plus biases and aggregation (≈1:15:40). The
recording ends as he turns to "existing choice models" (≈1:16:26).

## Student questions in this lecture

| ≈ | Question | Short answer |
| --- | --- | --- |
| 7:00 | The instructor's background | Stanford, previously Illinois; metric elicitation |
| 11:36 | Why "interactively"? | All ML learns from humans; the course focuses on explicit, often interactive, elicitation |
| 13:07 | (comment) Humans disagree with themselves 25% of the time | Inconsistency and noise are course topics; Bernoulli models may not be "the truth" |
| 21:29 | Sampling humans across groups? | At least one lecture; literature incomplete; good project |
| 23:48 | Learning from limited samples? | Implicitly everywhere: queries are expensive |
| 24:37 | What does a project look like? | Theory, critical examination, a literature survey ("harder than people give them credit for"), technical work with code; any application area (≈25:24, ≈26:11) |
| 26:58 | (comment) Last year's projects are on Medium | — |
| 40:13 | How much of the RL step will we implement? | "A meaningful amount": RLHF, DPO on language models |
| 41:45 | Reinforcement learning from AI feedback? | Not much; the ML side transfers |
| 42:32 | GPUs or credits? | "Almost definitely" something; scale not yet clear |
| 42:32 | Are homeworks implementation? | A mix, a fair amount of implementation |
| 43:17 | Why does research skip preference steps? | Data collection is costly and process-heavy; few public data sets |
| 47:12 | Downloadable reward models? | Some (RewardBench); separately trained ones don't plug in well |
| 49:30 | Is there still a case for explicit reward models after DPO? | Course covers both; Koyejo values them as artifacts |
| 52:34 | (comment) o1-style sampling makes reward models matter, and they're hackable | Agreed; overfitting to reward models is a course topic |
| 54:06 | Recommender systems? | Covered later in the lecture and the course |

## Where the captions are unclear

The edited transcript marks 22 unclear passages; the ones that touch content are:

- "MSRL" (≈7:47), the RL work Koyejo relates metric elicitation to. Probably inverse RL; not
  confirmed.
- "V module" (≈3:11), the module after which the first invited lecture falls.
- The colleague whose slides supplied the human-feedback taxonomy figure (≈30:07), and the speaker
  connected to RewardBench (≈47:12). Neither name is captured.

## Related pages

- [RLHF and the language-model pipeline](rlhf.md)
- [Asking humans for preferences: queries, comparisons and noise](preference-queries.md)
- [Reward hacking](reward-hacking.md)
- [Metric elicitation and inverse decision theory](metric-elicitation.md)
- [Whose preferences: representation, labour and ethics](whose-preferences.md)
