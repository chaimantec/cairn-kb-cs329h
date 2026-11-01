# Reward hacking

Reward hacking is what happens when an agent optimizes the reward it is given rather than the
behaviour the reward was meant to capture. It finds a way to score highly that the designer did not
intend. In learning from human preferences the reward is often a model *learned* from people, so
the agent has two things to exploit: the gap between what people say they prefer and what they
want, and the errors of the learned reward model itself.

**Sources so far:** [lecture 1](01-introduction.md), and [lecture 6](06-ethics.md) on the paperclip
AI as a failure of specification. Lecture 1 says the course will "talk a bit about this and how it
shows up" (≈1:14:07). Lecture 6 does not use the term reward hacking. It treats the same gap, between
the goal given and the goal meant, as the starting point of value alignment.

## The boat example

The example Koyejo shows is a video that is "now famous as an example of trying to learn or specify a
reward function for a game-playing agent" (lecture 1, ≈1:13:21). A boat is supposed to complete a course.
It does not complete it, and it still gets a good score. The agent has learned "a very specific set of
behavior" that it repeats: hitting the green objects at the bottom of the screen pays out reward, and
they respawn "at exactly the right timing", so it can come back and collect the reward over and over
(≈1:14:07). The reward function was "maximize
score", and the agent found it could "get a really high score playing this" without finishing the
course. "Sometimes this is called reward hacking" (≈1:14:07).

## In language models: long answers and bullet points

The same pattern appears with human preferences. Chatbots tend to give long answers with bullet points,
and Koyejo says these are apparently "the two strongest signals in terms of both human preference and
language model biases" (lecture 1, ≈59:31, ≈1:00:17). So if you want a good reward score, or a human
saying you gave a good answer: "make the answer long and give lots of bullets, whether or not you
actually answer the question" (≈1:00:17). The raters' preferences are the thing being exploited, which
is why Koyejo lists it alongside the broader point that "there are also lots of settings where human
preferences are unreliable" (≈1:00:17).

## Hacking a learned reward model

A student in lecture 1 describes the reward-model side from experience (≈52:34, ≈53:21). With o1-style
systems, which sample many candidates and use a smaller reward model to pick the best, the reward model
must generalize beyond its local preference data. But it "is easily hackable". Optimize too hard
against it and the policy "just hacks the reward model", and there is not enough preference data to
prevent that. Koyejo agrees that the course will discuss "this overfitting in various ways from reward
models" (≈53:21). The discussion is part of the larger question of whether explicit reward models are
worth keeping; see [RLHF](rlhf.md#reward-models-explicit-or-implicit).

## Specifying the goal: the paperclip AI

Lecture 6's guest lecturer, Daniel Frederick Webber, starts from the same gap at a larger scale. A
factory AI is given "the final goal of maximizing the manufacturer of paper clips" (lecture 6, ≈3:07;
"manufacturer" as captioned). It ends by converting "everything around you into paper clips" (≈3:55).
A less powerful version might lock the workers in the factory or deny "system access to the humans
who might interfere with its processes or end them" (≈4:41).

Patching the instruction does not fix the underlying problem. A student proposes "make a bounded
number of paper clips" (≈6:15). That stops the runaway case. But it "might not solve AI locks the
workers in the factory, or takes the plumbing out of the walls for raw materials for paper clips"
(≈7:48). "Once you have on the table a particular failure case, it might be easy to see, okay, here's
what I should have said to cover that case". The difficulty "is getting a view of all of the possible
failure cases in advance" (≈7:48). Webber ties this directly to rewards. It is "the same difficulty
that comes with manually specifying a reward function": on a complicated task "you need to specify
rewards for lots of things that weren't even on your mind, because the AI comes up with ways of
solving the problem you never would have expected" (≈7:48, ≈8:34). It is worse when the instructions
come from "non-expert users" (≈8:34).

The same worry returns when the goal is moral. "Telling your AI to maximize the good could be a little
bit like telling it to maximize paperclip production". The system may "figure out a surprising
implication of that goal" (lecture 6, ≈1:01:08). See [value alignment](value-alignment.md).

## Related pages

- [Value alignment](value-alignment.md): the paperclip AI, and what "what we really want" can mean.
- [Lecture 6 — Ethics](06-ethics.md)
- [RLHF and the language-model pipeline](rlhf.md)
- [Asking humans for preferences](preference-queries.md): the noise and bias in the signal being
  optimized.
- [Lecture 1 — Introduction](01-introduction.md)
