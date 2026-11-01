# Value alignment: intentions, preferences, interests and morality

Value alignment is usually glossed as getting AI to do "what we really want". This page collects what
the course says about what that phrase can mean, and why the answer comes before any choice of method.
The short version, from lecture 6: "what we really want" can be read as what the user **intends**,
what the user **prefers**, what is in the user's **best interest**, or what is **morally right**.
These come apart. Each reading brings its own technical and philosophical problems, and "how you're
understanding the problem might affect the tools that you try to use to solve it" (lecture 6,
≈36:23).

**Sources so far:** [lecture 6](06-ethics.md) is the main source. It is a guest lecture by the
philosopher Daniel Frederick Webber. [Lecture 1](01-introduction.md) names "human values and AI
alignment" as the course's last module, and [lecture 5](05-human-centered-design.md) defers the
question of matching AI decision-making to human values to a later lecture. Webber says at the outset
that "we're not going to solve any deep problems about value in the next hour", and offers "a lay of
the land" rather than a verdict (lecture 6, ≈2:22). [Lecture 7](07-voting.md), a guest lecture
on Polis, describes OpenAI's and Anthropic's projects to gather human values for language models
from the public.

## Where it sits in the course

Lecture 1 lays out the course in four parts after the introduction. The last is "a module on human
values and AI alignment" (lecture 1, ≈3:11). The course site's schedule calls the final theme *Value,
Alignment, & Human-centered Design*, and it opens on Nov 11 with
[lecture 5](05-human-centered-design.md). Lecture 5 says the question "to what extent can we have
decision-making from AI tools match human ethical principles and values" is "part of the goal of the
broader class", and that it will return to it "a couple of lectures from now" (lecture 5, ≈1:05:39).
Lecture 6, the Nov 18 guest lecture, takes that question up. Neither recording says it is the lecture
meant.

Webber's case for a philosopher in the room is that "the interesting questions about value alignment
are not just technical. They're also philosophical, or at least partly philosophical" (lecture 6,
≈1:36, ≈2:22).

## The paperclip AI

The running example is "paperclip AI", "one of the classics in the philosophy literature", attributed
to Nick Bostrom (lecture 6, ≈3:07; the captions spell the name "Bostonramm"). A factory AI given the
final goal of maximizing paper clip production converts "everything around you into paper clips", and
eventually "the whole Earth" (≈3:55). A less powerful system could still lock the workers in, or deny
"system access to the humans who might interfere with its processes or end them" (≈4:41).

The general problem: "how do we design AI agents that will do what we really want, where what we
really want is often more nuanced than what we say that we want" (≈5:28). Better instructions help
only so much. "Once you have on the table a particular failure case, it might be easy to see" what you
should have said, but the hard part "is getting a view of all of the possible failure cases in
advance" (≈7:48). Webber calls it "just the same difficulty that comes with manually specifying a
reward function" (≈7:48, ≈8:34). See [reward hacking](reward-hacking.md).

## Four readings of "what we really want"

| Reading | Aligned if the agent does… | The problem it brings | Where the course's methods fit |
| --- | --- | --- | --- |
| Intention | what the user really intends (≈10:06) | Technical. Deriving intention from "underspecified instructions" may need "a complete model of human language and interaction" (≈10:52, ≈11:39) | Not the course's main tool; Webber wonders whether "an LLM could assist" (≈13:57) |
| Preference | "what the user prefers to have done" (≈16:15) | Technical. Infer preferences "from behavior or feedback". Finite data fit "infinitely many preference or reward functions", and emergencies are rarely observed (≈17:01–18:32) | This is "the motivating insight of machine learning from human preferences, or human feedback" (≈17:01) |
| Best interest | "what's in the user's best interest" (≈19:20) | Technical and philosophical. "Not an entirely empirical question", so behaviour and feedback alone cannot settle it. Philosophers disagree, though there is "a lot of agreement" on goods such as health, safety, liberty, knowledge, relationships and dignity (≈20:06–22:26) | Not by observation alone (≈20:06) |
| Morality | "what's morally right" (≈51:05) | Philosophical. Moral disagreement about cases and about "what the correct moral theory is" (≈54:58, ≈55:43) | Either align to a moral theory or to "people's existing moral views" (≈59:36) |

**Intention versus preference.** Intentions "don't always track what it is we really want", for
example when "I have incomplete information" or "I'm not being perfectly rational" (lecture 6,
≈14:42). The factory owner wants paper clips to make money. If the AI knows staples would make more,
has it given me what I want by doing what I intended? "In one sense, yes. But in another sense, no."
What matters may be "what I would intend if I had all the information and I was thinking perfectly
about it" (≈15:29, ≈16:15).

**Preference versus best interest.** "My preferences can diverge from what is actually good for me in
an objective sense". "A lot of people prefer to smoke", and the factory owner might be better off
"less focused on money" (≈18:32, ≈19:20).

**Everyone, not just the user.** The user-centred readings leave out "really anybody other than the
user. But of course the user is not the only person in the world who matters" (≈50:18, ≈51:05). For
the paperclip AI this is "the most plausible kind of diagnosis of what goes wrong": destroying the
world is "bad for everyone" (≈51:05, ≈51:53). The user still matters: "we do want it to be aligned to
what the user wants when what the user wants is morally acceptable" (≈52:39).

## Paternalism, autonomy and defaults

Aligning to best interests runs into **paternalism**, "choosing what you think is best for someone
rather than letting them decide for themselves" (lecture 6, ≈22:26, ≈23:13). Autonomy is itself
"widely thought to be good for a person". So even an interest-aligned system has "reason to consider
the person's own intentions or preferences anyway" (≈22:26, ≈23:13). The same worry returns for
morality: "even if we did know what the best moral theory was, it might be bad to design AI to act on
that theory if it's not one that is shared by the users" (≈58:50). There is also a practical cost:
users "might just stop using your service" (≈44:51), or find it "a product that people don't want to
use because it doesn't promote their values" (≈58:50).

A student points out that the choice cannot be dodged: "there is no way not to engage with this
question, I think, because of defaults", and since "most people will not bother" to personalize,
"there's a lot of agency in design, picking the default behavior" (lecture 6, ≈47:13). Webber makes
the same point about refusing to act. In a hard case, "to not act is one of the choices that's
available to you" (≈1:02:40, ≈1:03:26).

Lecture 6's pair exercise, a news chatbot personalized to users' preferences or interests, shows these
tensions in one product. Gossip and facts, echo chambers and exposure to opposing views, and breadth
against emotional distress all come up (≈36:23–47:13). Interests "can be at odds with themselves", and
"people have conflicting preferences all the time" (≈43:17, ≈44:02). See
[lecture 6](06-ethics.md#case-study-a-personalized-news-chatbot).

## Moral theories and common-sense morality

A **moral theory** is "a systematic account of morality" that answers questions such as whether to
lie to spare feelings or to "kill one person to save five" (lecture 6, ≈53:25, ≈54:12). Lecture 6
sketches consequentialism ("an act is right if and only if it produces the greatest net good of any
act available"), utilitarianism as one kind of it, weighted sums, a complaint or "maximin model",
non-maximizing views, and deontological views on which "even acts with good consequences can be
wrong" (≈54:12–58:04). See [lecture 6](06-ethics.md#moral-disagreement-and-moral-theories) for each.

**Aligning to a theory.** The risk is the paperclip problem again: "telling your AI to maximize the
good could be a little bit like telling it to maximize paperclip production". It may "figure out a
surprising implication of that goal" (≈1:01:08). And "a lot of these moral theories get pretty wacky
in edge cases" (≈1:00:22).

**Aligning to common sense.** The alternative targets "people's existing moral views": "We're not
trying to make AI morally perfect. The goal is just to have it be as moral as anyone" (≈59:36,
≈1:00:22). Such an agent "would behave more predictably", but may be unpredictable in the same edge
cases, "where maybe common sense runs out" (≈1:01:08). Webber asks "how bad is that in the end?"
(≈1:01:54). One answer comes later. It is bad if the agent "is way more powerful than your typical
person", so that "its mistakes have much greater ramifications". That is also a reason "to be worried
about power seeking" (≈1:05:48, ≈1:06:33).

## The goal before the method

The lecture keeps two questions apart. "What is the goal of value alignment", the "correct end state",
is not yet the question of "what would be the best way of going about actually training an agent"
(lecture 6, ≈30:09, ≈30:56). They are related. If the end state is "the user's revealed preferences",
then "something like, I don't know, inverse reinforcement learning" may make more sense than other
techniques (≈30:56). The course's preference-learning methods address the second reading, and lecture
6 does not claim they settle the others. Webber offers no verdict on which reading is correct. It may
be one throughout, or it may be that "from case to case it makes more sense to focus on one rather
than the other" (≈33:14).

## Gathering values from the public

Lecture 7, a guest lecture by Colin Megill of Polis, describes two attempts by AI companies to gather
human values from outside the company. OpenAI ran "a million dollar grant program" on mapping human
values "to have that be an input to completions" (lecture 7, ≈41:44, ≈42:31). Megill's toy example is
that very gory completions might suit "a horror author" and not "a grade schooler" (≈42:31). "This
kind of stuff in alignment has to do with human values. And cynically, moving risk away from the
organization into some legitimate third party system would be desirable if it was possible" (≈42:31,
≈43:17). Anthropic used Polis with "a random sample" to look at Claude's constitution, and "it did turn
out that everybody was interested in everything. There wasn't a lot of disagreement" (≈44:50).
Lecture 7 does not say which reading of "what we really want" either project aims at. See
[lecture 7](07-voting.md#human-values-for-language-models-openai-and-anthropic).

## Related pages

- [Lecture 7 — Voting (guest lecture on Polis)](07-voting.md): OpenAI's and Anthropic's projects to
  gather values from the public.
- [Preference aggregation](preference-aggregation.md): lecture 6's moral theories as rules for
  weighing people against each other.
- [Lecture 6 — Ethics](06-ethics.md): the full treatment, with every student question.
- [Whose preferences](whose-preferences.md): choosing which humans, aggregation, labour, fairness,
  and people other than the user.
- [Asking humans for preferences](preference-queries.md): revealed and stated preferences, and what
  finite feedback can pin down.
- [Reward hacking](reward-hacking.md): specification failures, from the boat game to the paperclip AI.
- [Human–AI interaction](human-ai-interaction.md): designing for people, trust and reliance.
- [Lecture 1 — Introduction](01-introduction.md) and
  [Lecture 5 — Human-centered Design](05-human-centered-design.md).
