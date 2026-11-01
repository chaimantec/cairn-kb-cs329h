# RLHF and the language-model pipeline

Reinforcement learning from human feedback (RLHF) is how this course's most visible application
works. A pre-trained language model is fine-tuned on human demonstrations, people are asked which
of several outputs they prefer, and the model is optimized to produce what they prefer. The course
treats it as one instance of a broader problem, learning from explicit human preference signals,
rather than as the whole subject. Its specific interest is the step where preferences are collected.

**Sources so far:** [lecture 1](01-introduction.md), which surveys the pipeline without
equations; [lecture 2](02-preference-models.md), which supplies the choice models behind the
comparison step and comments on language-model preference data; and three remarks in
[lecture 3](03-model-based-preference-optimization.md), which is about classification metrics, not
language models. Later lectures are not yet in this
knowledge base.

## Why it matters to the course

Koyejo opens the language-model part of the lecture with "the elephant": GPT got many more people
excited about learning from feedback. Of the many innovations behind language models that people
enjoy using, it has been argued "quite strongly" that aligning to human preferences, through methods
like RLHF, made a big difference (lecture 1, ≈32:27). He adds that this "reinvigorated interest" in
an area with a long history (≈33:13). He also says his own earlier work on human preferences in
classic machine learning became exciting again "with language models and RLHF being a thing"
(≈7:47).

## The pipeline, step by step

Lecture 1 lays out the standard framework (≈36:23–≈40:13):

1. **Pre-training.** Train a model to predict the next word on web data.
2. **Supervised fine-tuning (SFT).** Gather examples of questions and answers from "somewhat
   knowledgeable humans". These sets are far smaller than web data, often on the order of thousands
   of examples. The objective is unchanged (next-token prediction), but the model becomes better at
   answering questions in general (≈36:23, ≈37:08).
3. **Comparison data.** Query humans for a preference between completions of the same prompt. The
   most common form is **pairwise**: which of two completions do you prefer? With four candidates,
   the person might pick one of the four. "Typically this is discrete choice", over fairly small
   sets of samples (≈37:08, ≈37:54).
4. **Optimization.** Use the preference signal to update the model. The most popular method is a
   reinforcement-learning algorithm such as **PPO**. Over the sequence of updates the model gets
   better at earning high reward, meaning it more often produces the completion a human expert would
   have picked (≈39:28, ≈40:13).

Koyejo numbers these from SFT, so in his words "typically two and three are done together":
preference collection and optimization are interleaved (≈39:28). He contrasts the two human-data
steps. SFT demonstrations are "mostly one-shot", collected offline. Preference collection "is
typically best done interactively", although some work collects it offline, and the course covers
the technical differences (≈38:40). The course puts "a bit more focus" on the preference step
(≈38:40).

What a preference label *means* is open. Narrowly, it is a preference between two completions.
Broadly, labellers may be embedding their values about what a language model should do. The course
engages with both readings (≈38:40, ≈39:28).

## Evidence that the preference step helps

The lecture shows results from an early paper on summarization (not named in the audio). A generic
pre-trained model is "noisy, not that bad, not that great". Supervised fine-tuning improves it "a
meaningful amount", and explicit human feedback improves it "meaningfully further". Koyejo says this
is "borne out ... in the artifacts that we're using now" (≈54:52, ≈55:38).

## Reward models: explicit or implicit

In the standard pipeline the preference data trains a **reward model**, which the optimizer then
maximizes. Lecture 1 spends a long student-led discussion on whether that model is needed
(≈47:12–≈54:06).

**What a reward model is, mechanically.** Almost always it is the language model with its output
head cut off and a classifier attached. It is therefore "some big unwieldy model, as big as your
language model" (≈47:58, ≈48:45).

**Why off-the-shelf reward models are hard to use.** Public reward models now exist, for example
through **RewardBench** (≈47:12). But training a reward model separately and then training a language
model against it "tends not to work all that well". The most successful implementations update both
together, collecting data as the model improves (≈47:58). Why they don't plug and play is "not fully
known". Hypotheses include distribution shift, or the reward model learning only a local
approximation that is good for updating one particular language model rather than human preference
itself. Koyejo calls this frontier research and a good project (≈48:45, ≈49:30).

**Doing without one.** Methods such as **DPO** learn from pairwise preferences directly, with no
explicit reward model. The course has a whole section on learning from preferences without an
explicit reward model, covering DPO and also bandits, alongside methods that learn one and optimize
it (≈49:30, ≈50:16). The community pursues both. Going without is cheaper, because reward models are
big, and RL has a parallel in **behaviour cloning**, which treats the problem as regression with no
reward model (≈51:02).

**The case for keeping it.** Koyejo values the reward model as an artifact. It may tell us something
about human preferences that can be examined offline, it supports evaluation, and it can show where
things break (≈51:02, ≈52:34). "Most of the field doesn't take that view": the reward model matters
only insofar as it helps train the model you want. "The short answer is you don't need it. In
practice, many people prefer not to have it" (≈51:48).

A student adds that reward models became useful in their own right with o1-style systems, which
sample many candidates and use a smaller reward model to choose among them. That makes
generalization beyond the preference data critical, and reward models are easily hacked (≈52:34,
≈53:21). See [reward hacking](reward-hacking.md).

## Variants and neighbours

- **Reinforcement learning from AI feedback**, using AI judgments (for example, language-model
  judgments) instead of human ones, is mentioned but not a focus. The machine-learning side is
  effectively the same, with different query mechanisms (lecture 1, ≈41:45).
- **Earlier human feedback in language systems** includes document- and word-level interaction,
  label-consistency queries, feature selection, and corrections to parsers (≈33:13–≈35:37). See
  [lecture 1](01-introduction.md#language-models-where-most-people-meet-preference-learning).

## The comparison step as a choice model

Lecture 2 treats the human comparison step as one more application of discrete choice models: the
same tools model "the choices of decision makers", "typically in this second stage", across
documents (≈6:14, ≈7:00). Two links make the connection. **Reward is utility**: "what is called
reward" in reinforcement learning "is equivalent to what economists might call utility" (≈12:25).
And the context need not be hand-featurized: a model can go "straight from phrase completions to a
prediction of choice" (≈11:39). The lecture does not work through a language-model example in the
audio. The models themselves are on the [discrete choice models](discrete-choice-models.md) page.

Koyejo also argues that language-model preference experiments mostly collect **stated**
preferences. Someone is shown completions in a room and asked which they prefer, and "there's no
cost to making a decision either way". He thinks the field does not engage enough with the gap
between stated and revealed preferences (lecture 2, ≈1:09:07). See
[revealed versus stated preferences](preference-queries.md#revealed-versus-stated-preferences).

## Remarks from the metric-elicitation lecture

Lecture 3 is not about language models, but it makes three remarks that bear on them. First,
"reward, utility, metric roughly mean the same thing" from the course's point of view (≈17:46).
Second, counting the human queries a problem needs is hard here: "I don't know how to do this for
RLHF, as a specific statement", unlike the classification setting, where bounds exist (≈6:59,
≈7:44). Third, Koyejo offers an analogy for the classification methods it covers. Getting the
probability model is like pre-training, and finding the weights or threshold for the decision
setting is like preference tuning (≈1:19:01). See [metric elicitation](metric-elicitation.md).

## Who does this work

Most published work on real-world learning from human preferences comes from industry. Collecting
preference data takes more process and money, since annotators should be paid, and there are few
public preference data sets. The course frames much of its work around synthetic or existing data
(lecture 1, ≈44:03–≈45:37). Koyejo names **OLMo**, from AI2, as an exception that builds large
models end to end, and notes that well-known work such as DPO uses public data (≈46:25). The course
plans to implement RLHF-style methods, including DPO, on language models in homework and projects
(≈40:13, ≈41:00).

## Known failure modes

- Reward scores, and human raters, favour long answers with bullet points regardless of whether the
  question is answered (lecture 1, ≈59:31, ≈1:00:17).
- Optimizing hard against a reward model finds outputs that exploit it ([reward hacking](reward-hacking.md)).
- The preferences built into a model reflect whoever shaped it; see
  [whose preferences](whose-preferences.md).

## Related pages

- [Asking humans for preferences](preference-queries.md): pairwise versus absolute queries, and noise.
- [Discrete choice models](discrete-choice-models.md): the utility models behind comparison data.
- [Lecture 1 — Introduction](01-introduction.md)
- [Lecture 2 — Preference Models](02-preference-models.md)
- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md)
- [Metric elicitation](metric-elicitation.md): the classification setting lecture 3's remarks come from.
