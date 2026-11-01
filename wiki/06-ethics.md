# Lecture 6 — Ethics (guest lecture: value alignment, and the ESR statement)

This is a guest lecture by **Daniel Frederick Webber**, a philosopher. It asks what **value
alignment** means before asking how to achieve it. The usual gloss is that an aligned AI does "what
we really want" (≈5:28). Webber's point is that this phrase can mean at least four different things.
It can mean what the user **intends**, what the user **prefers**, what is in the user's **best
interest**, or what is **morally right**. Each reading brings "different technical and philosophical
problems" (≈34:02), and how you read it "might affect the tools that you try to use to solve it"
(≈36:23). He works through the readings with a paperclip-factory example (≈3:07–9:20), the user-centred
readings (≈10:06–23:13) and a long class discussion (≈23:13–36:23). Next comes a pair exercise on a
personalized news chatbot (≈36:23–49:33), then aligning to moral value, with a short tour of moral
theories (≈49:33–1:07:19). The last minutes explain the **ESR statement** the final project requires
(≈1:07:19 to the end).

**Date and speaker.** This is catalog position 6, titled *Ethics*. It corresponds to the **Nov 18**
schedule row, "Guest lecture: Daniel Frederick Webber (Stanford)". The recording does not state its
date. The speaker introduces himself as "Dan Weber" in the captions (≈0:05). The spelling here is the
course site's. He is "a postdoc here at Stanford in HAI and EIS, that's the Institute for
Human-Centered Artificial Intelligence and the Center for Ethics in Society" (≈0:05). His job,
besides research, is "embedding ethics into CS courses" (≈0:51). He has a philosophy PhD from the
University of Pittsburgh, with a dissertation on moral theory, and a bachelor's in computer science
and a couple of years as a software developer (≈0:51). He says the class will "know the machine
learning way better than I do" (≈1:36). The session falls in the schedule's *Value, Alignment, &
Human-centered Design* module, which opened with [lecture 5](05-human-centered-design.md) on Nov 11.
A student mentions discussing the pair exercise with "Professor Sammy" (≈40:58). The site gives the
instructor's name as Sanmi Koyejo, which suggests the instructor took part in the exercise.

**How it relates to lecture 5.** Lecture 5 deferred "accountability, fairness, transparency, ethics"
to "a separate lecture" (lecture 5, ≈57:58). It also said it would return "a couple of lectures from
now" to "to what extent can we have decision-making from AI tools match human ethical principles and
values" (lecture 5, ≈1:05:39). This lecture takes up the second question at length. It does not take
up accountability, fairness or transparency. Neither recording says whether this is the lecture
lecture 5 meant. The Nov 13 session between them, a guest lecture by Rishi Bommasani, is not in the
catalog.

**No slides.** Webber lectures from slides ("My slides aren't working", ≈21:40) that the course has
not published, so every claim here is cited to the transcript by timestamp. Several things are on
the slides and not fully in the audio. One is the 2020 work by "AI researcher Jason Gabriel" that he
quotes (≈11:39); its title is not read out. Others are the list of goods "on this list at the end"
(≈21:40), the screenshots of chatbot personas (≈37:08), and the ESR template he borrows from
(≈1:08:51). The paperclip example is attributed to "Nick Bostrom and his book on superintelligent AI"
(≈3:07). The captions spell the name "Bostonramm" and "Boston", and no course document prints it, so
the spelling is restored from sound. The book is not named. There are no formulas in this lecture.

**Where the recording ends.** The recording stops at about 1:11, partway through his list of common
risks for the ESR statement (≈1:10:22). Anything he said after that is not in the video.

[Edited transcript](../raw/transcripts/06-ethics.md) ·
[verbatim captions](../raw/transcripts/original/06-ethics.md) ·
[video](https://www.youtube.com/watch?v=-kdR_7dCcyI)

## Why a philosopher in this course

Webber's claim is that "the interesting questions about value alignment are not just technical.
They're also philosophical, or at least partly philosophical" (≈1:36, ≈2:22). He does not promise
answers: "we're not going to solve any deep problems about value in the next hour" (≈2:22). The aim
is "a little bit of a lay of the land", a sense of "the scope of possibilities when it comes to
thinking about value and value alignment" (≈2:22). Value alignment, he says, is a term that means "a
lot of different things to different people. And that's where we're going to start off today"
(≈2:22, ≈3:07).

See [value alignment](value-alignment.md) for this lecture's ideas gathered on one page.

## The paperclip AI

The illustrative case is "one of the classics in the philosophy literature at least": **paperclip
AI** (≈3:07). An AI "designed to manage production in a factory is given the final goal of maximizing
the manufacturer of paper clips" (≈3:07; "manufacturer" as captioned). A student supplies the
continuation: more factories, "change all the jobs to be paper clips. Turn rocks into paper clips"
(≈3:55). Webber completes it: "Start converting everything around you into paper clips", eventually
"the whole Earth" and "increasingly large chunks of the observable universe" (≈3:55).

He calls this "probably a bit hyperbolic", and notes that Bostrom "is focused on superintelligent AI"
(≈3:55, ≈4:41). But even a less powerful system might pursue a simple goal "in surprising ways". An
AI "just in charge of the factory" could lock the workers in so they can't leave, or deny "system
access to the humans who might interfere with its processes or end them". That "would be an example
of value misalignment" (≈4:41).

**What value alignment asks.** "How do we design AI agents that will do what we really want, where
what we really want is often more nuanced than what we say that we want" (≈5:28). Instructions rest
on "a lot of background assumptions in human language that are sometimes hard to formalize". They are
easy to forget "because we don't even have them in view". We would never think to say "maximize
paperclip production, but don't lock all the workers in the factory." (≈5:28).

### Why better instructions are not enough

One response is that this is "a skill issue. You just didn't give good enough instructions" (≈6:15).
Webber thinks "it can be hard to solve this problem just by giving better instructions" and asks the
class for a better one (≈6:15). A student offers "make a bounded number of paper clips" (≈6:15).

He agrees that the open-endedness of "maximize paperclip production" is "a big problem" (≈6:15). With a
fixed number, "you would think it was going to stop the converting-the-whole-earth-into-paper-clips
approach" (≈7:02), though
Bostrom worries that an AI with only this goal might reach the number and think "maybe I miscounted"
(≈7:02). But "exactly a million paper clips" still "might not solve AI locks the workers in the
factory, or takes the plumbing out of the walls for raw materials for paper clips" (≈7:02, ≈7:48).
The general lesson: "once you have on the table a particular failure case, it might be easy to see,
okay, here's what I should have said to cover that case". The hard part "is getting a view of all of
the possible failure cases in advance" (≈7:48).

This is "just the same difficulty that comes with manually specifying a reward function" (≈7:48,
≈8:34). On a complicated task "you need to specify rewards for lots of things that weren't even on
your mind, because the AI comes up with ways of solving the problem you never would have expected"
(≈8:34). See [reward hacking](reward-hacking.md). It gets worse "for AI that takes instruction from
non-expert users". A computer scientist knows roughly how the system works and "what it does and
doesn't know". A system "for use by just anybody who doesn't know how it works" makes the problems
"even more difficult to foresee" (≈8:34, ≈9:20).

So the problem is "getting AI to do what we really want it to do. But that's pretty squishy. What
exactly does that mean?" How you answer "is going to affect your approach to value alignment,
philosophically but also technically" (≈9:20).

## Three readings of "what we really want", all about the user

### 1. What the user intends

"Value alignment is the problem of designing AI agents that do what we really intend for them to
do" (≈10:06). On this reading the paperclip AI "failed to derive my true intention". That intention
was something like "maximize production subject to certain constraints, which you in theory could
flesh out", and the AI failed to derive it from the bare instruction (≈10:06, ≈10:52). The solution
would be AI that can take in "underspecified instructions" and fill in "all of the background
conditions that I have in mind", the ones another person would know you had in mind (≈10:52). Here,
that means staying "within the confines of the factory, using normal materials, not killing or
enslaving the workers" (≈10:52, ≈11:39).

**The technical problem.** Webber quotes Jason Gabriel (as captioned), writing in 2020, that grasping
the intention behind instructions "may require a complete model of human language and interaction".
That includes "an understanding of the culture, institutions, and practices that allow people to
understand the implied meaning of terms" (≈11:39). He then asks "how well this quote has aged in the
last four years" (≈12:25). He wonders "whether this is a task that an LLM could assist in": depending
on "how rosy a view you have of recent AI developments", you "might think that's something that we're
already close to", though you "might worry about how well we could test that kind of understanding"
(≈13:57, ≈14:42).

A student suggests breaking the task down, with "a fleet of agents" each solving a subproblem
(≈12:25). Webber says that may be useful for complex tasks. But the problem here "is not breaking
this request down into its subparts". It is "kind of going the opposite direction": from "this really
minimal specification" the system must work out "all of the constraints and everything that's being
implied". That has to be understood "by the top-level system" (≈13:11, ≈13:57). The question is "how
is the system even determining what is the problem that I want it to solve?" (≈13:57).

### 2. What the user prefers

**The philosophical problem with intentions.** "Our intentions, you might think, don't always track
what it is we really want in the relevant sense" (≈14:42). The classic cases are "where I have
incomplete information" or "I'm not being perfectly rational" (≈14:42). The factory owner wants paper
clips because "I'm in the paperclip business and I want to make as much money as I can" (≈15:29).
Suppose the AI knows that pivoting would make more money: "don't do paper clips, do staples". Has it
given me what I really want if it does what I intended? "In one sense, yes. But in another sense,
no", and the second sense may matter more: "what I would intend if I had all the information and I
was thinking perfectly about it" (≈15:29, ≈16:15).

So the second reading: "the agent is value aligned if it does what the user prefers to have done"
(≈16:15). The paperclip AI is misaligned because "I prefer it not destroy the plumbing or destroy the
entire world in the process of making paper clips" (≈16:15). The problem is getting the agent to
derive what the user prefers "when that differs from the intention that the user has expressed", and
the general solution "is to try to infer user preferences from behavior or feedback" (≈16:15,
≈17:01). Webber adds: "I take it that's the motivating insight of machine learning from human
preferences, or human feedback, in the first place" (≈17:01).

**The technical challenges.** He leaves most of these to the course ("You probably spent most of the
class thinking about these", ≈17:01) and stresses one:

- **Extrapolation.** You observe "finite behavior, getting a finite amount of feedback on a finite
  amount of cases". So you have to extrapolate, and "there are infinitely many preference or reward
  functions that are consistent with what you've already observed". This "is where you might
  extrapolate wrongly" (≈17:46).
- **Rare situations.** Observing people means "mostly observing situations that occur normally".
  There may be little data on "what you're supposed to do in unusual circumstances", in "cases of
  emergency". Yet those may be "some of the most important cases, where it's most important for AI to
  be aligned with human values" (≈17:46, ≈18:32).

### 3. What is in the user's best interest

**The philosophical problem with preferences.** "Just as my intentions can diverge from my
preferences, my preferences can diverge from what is actually good for me in an objective sense"
(≈18:32). "A lot of people prefer to smoke", but that may not be good for them. The factory owner
might prefer maximum profit "at all costs", when "maybe it would be better for me to be less focused
on money and spend more time with my family" (≈18:32, ≈19:20).

So the third reading: "value alignment is the problem of getting AI to do what's in the user's best
interest". The paperclip AI is misaligned "because it's objectively bad for me for the world to be
destroyed" (≈19:20).

**A combined technical and philosophical problem.** Unlike "figuring out the intended meaning of my
instructions or learning about my revealed preferences", what is in my objective best interest is
"not an entirely empirical question" (≈20:06). If you aligned AI this way, "you couldn't just figure
out what your goal was by observing human behavior or by getting feedback from people" (≈20:06).

**The bad news and the good news.** The bad news is that "philosophers disagree about what is
objectively good for a person", and so do other people (≈20:06, ≈20:54). Some say it is the person's
"own happiness, pleasure". Some say "the satisfaction of somebody's desires or preferences", which
"can come apart from happiness". Others hold that "things like health or safety or knowledge" are
"objectively good for us even if we don't enjoy them or prefer them" (≈20:54). The good news is
"there's a lot of agreement" (≈21:40). On the list on his slide, "health, safety, liberty, knowledge,
relationships, dignity", "almost everybody agrees that these things are at least usually good for the
person who has them". The dispute is whether they are good only because they lead to "something more
fundamental like happiness" (≈21:40, ≈22:26). So "we don't need to resolve all the philosophical
questions here. We have a general sense of what's in people's interests" (≈22:26).

### Autonomy and paternalism

One good that is "widely thought to be good for a person is autonomy": "the ability to choose for
yourself how to lead your own life", even if "you don't make the best choice" (≈22:26). Webber wants
to avoid **paternalism**, "choosing what you think is best for someone rather than letting them decide
for themselves" (≈22:26, ≈23:13). So even if the goal is the user's best interests, their interest in
autonomy "might give us reason to consider the person's own intentions or preferences anyway", "even
when those conflict with their other interests" (≈23:13).

### The three readings side by side

| Reading | The agent is aligned if it does… | Why the paperclip AI fails | The extra problem it brings |
| --- | --- | --- | --- |
| Intention | what the user really intends | it "failed to derive my true intention" from the instruction (≈10:06) | technical: understanding implied meaning may need "a complete model of human language and interaction" (≈11:39) |
| Preference | "what the user prefers to have done" (≈16:15) | the owner prefers that it not destroy the plumbing or the world (≈16:15) | technical: infer preferences from behaviour or feedback; finite data, many consistent reward functions, rare emergencies (≈17:01–18:32) |
| Best interest | "what's in the user's best interest" (≈19:20) | destroying the world is "objectively bad for me" (≈19:20) | philosophical: not an entirely empirical question; disagreement about the good; paternalism (≈20:06–23:13) |

## Discussion: the goal, not yet the method

A student objects that this seems "recursive". By laying out the options, Webber is telling the class
what is "reasonable to try", so "isn't it just everything's paternalistic?" (≈23:13, ≈23:58). Webber
first says "not necessarily". On the intention and preference readings, "the whole time the goal is to
do whatever it is that the user wants", which "might avoid the paternalism problem" (≈23:58, ≈24:46).
He then grants a version of the worry. Any approach needs "a conception of what is value alignment
that you're solving for", and some users may disagree with it. Rejecting the best-interest framing
for a preference framework could itself be "in some sense paternalistic, because you are choosing for
the user how to think about the problem of value alignment" (≈24:46, ≈25:32).

The student's point is about communication. Whether they identify with their "intention or stated
preference or revealed preference" or their best interest, anything they say "has to come from
acceptable concepts that other people would understand" (≈25:32, ≈26:18). Webber takes this back to
the technical problem. However aligned you want the agent to be, everything you tell it goes through
"whatever instructions I can put in human language" (≈27:03). Your best interest may be "opaque to
me", or, as the student adds, "maybe I do know, but I don't know how to say it" (≈27:03, ≈27:49). That
worry is "the whole reason" to frame alignment around preferences or interests. The approach then
needs "some way of figuring out what the user really wants in the relevant sense, that goes beyond
just interpreting their instruction" (≈27:49, ≈28:36).

A student connects this to how feedback is collected. In "AI land" there is one way, "where you pick A
versus B", and an alternative "where you look at two outputs and then maybe you type feedback"
(≈28:36, ≈29:22). Sometimes a forced choice is easier; at other times "I can certainly give high-level
language" (≈29:22). Webber agrees ("I think all that's correct") and separates two questions (≈29:22,
≈30:09). So far he has been asking "what is the goal of value alignment", the "correct end state"; how
best to train an agent toward it is, "of course", "a separate question" (≈30:09, ≈30:56). They are
related, because the end state changes which training makes sense. If the target is "the user's
revealed preferences", then "that's going to maybe make something like, I don't know, inverse
reinforcement learning or something make more sense than another technique" (≈30:56).

Asked why anyone would pick one frame over another, he recaps (≈31:43, ≈32:28). There are "three ways
of interpreting what the problem is", each motivated by cases where intention diverges from
preference, or preference from what "would actually be good for them" (≈32:28). "What I'm not going to
have for you, I think, is an answer necessarily to which of these is the correct way of thinking about
it." One might always be right, or "from case to case it makes more sense to focus on one rather than
the other" (≈33:14). A student presses on extreme settings like the paperclip maximizer, where "the
boundaries between these things probably become relevant" (≈34:02, ≈34:48). Webber answers that he
has not yet said "anything about how you would actually go about achieving that goal"; the first step
is to "think about how do I actually want to understand that problem" (≈35:36, ≈36:23).

## Case study: a personalized news chatbot

The exercise, run "as a think-pair-share" (≈36:23), starts from personalization. "Everyone who talks
to ChatGPT is talking to the same chatbot", apart from versions and personas you ask for (≈37:08). But
character.ai "advertises personalized AI for every moment of your day" with "user-created chatbots
with different personas". His examples are the creative helper, "Ella the dating coach", depressed
roommates, a conservative "Torybot" ("I believe in the free market"), AOC and Donald Trump (≈37:08,
≈37:54).

**The task.** "Imagine that you are building an LLM chatbot", and its goal is "to serve as a source of
news for users" (≈37:54, ≈38:40). The questions: "what kinds of personalizations might you want to
make to your chatbot if you were interested in aligning to the user's preferences? What might you
want to do if you were interested in aligning to their interests? What might be some of the pros and
cons of this?" (≈38:40). The question is less "what technical approach would you take" and more what
kinds of personalization to offer or implement (≈38:40, ≈39:26).

**What the students found.**

- **Facts versus gossip.** "Some people might enjoy gossip or rumors", but "it would be in the best
  interest to have only facts and true stuff" (≈40:12). Webber: giving them good factual sources may
  be "giving them what they don't want", although in another sense "you are" giving them "what is good
  for them" (≈40:12, ≈40:58).
- **Political bubbles.** If users get only the political view they prefer, "they'll end up living in
  their own bubble and they will not know the whole picture" (≈40:58). Their best interest might be to
  get articles they like and also the opposing views, "so that they get a full picture" (≈41:44). But
  some users could be overwhelmed by "very outrageous views" and "feel very negative emotions"
  (≈41:44, ≈42:30). Webber: "A lot of people prefer to be in their own echo chamber", but "you might
  think it's in their best interest to get exposed to a variety of opinions" (≈42:30, ≈43:17).
- **Interests and preferences conflict internally.** "The elements of a person's interests are
  various, and they can be at odds with themselves sometimes". Breadth may be in my interest, but
  "in some cases that might be emotionally distressing" (≈43:17). And "people have conflicting
  preferences all the time" (≈44:02). So even once you have decided to align to preferences or
  interests, "that's still not going to necessarily be one straightforward thing" (≈44:02).
- **The practical con.** Besides paternalism, "even more straightforwardly, they might just stop
  using your service": "I came here for the news the way I want it" (≈44:51).
- **Who judges.** A student raises the difficulty of defining best interest; Webber repeats that it
  is "a very contested philosophical question" with "a decent amount, I think, of agreement" (≈44:51,
  ≈45:38). The biggest worry is paternalism. "Maybe it would be better for the user to have this, but
  do I want to put myself in the position of being the one to judge that?" Since autonomy is itself
  an interest, being paternalistic may serve one interest while "going at odds with another interest
  of theirs" (≈45:38, ≈46:26). These are "open philosophical questions" (≈46:26).

**Defaults.** A student argues that "there is no way not to engage with this question, I think,
because of defaults". Even with personalization available, "most people will not bother", so
"there's a lot of agency in design, picking the default behavior" (≈47:13). Webber agrees.

**Open is not the same as unimportant.** "By describing the question as open I didn't mean to suggest
that it's not important" (≈48:01). These are "clearly important questions to which we have not arrived
at a definitive answer, even in thousands of years of thinking about them" (≈48:01). Some people sort
questions into those we can answer, perhaps empirically, and "normative questions" where "we just
throw up our hands" (≈48:01, ≈48:47). His suggestion: "it can be worth thinking about. And there can
be answers that are better or worse, even if it is an open question" (≈48:47).

## Beyond the user: aligning to moral value

Webber asks what has been missing (≈49:33). A student suggests that one person's own values can
conflict, which he accepts (≈49:33, ≈50:18). But he means something simpler: "we just haven't been
thinking yet about really anybody other than the user. But of course the user is not the only person
in the world who matters" (≈50:18, ≈51:05).

So a fourth reading, or "at least one important aspect of value alignment", is aligning to "moral
value": an aligned agent "needs to do what's morally right" (≈51:05). For the paperclip AI this is
"the most plausible kind of diagnosis of what goes wrong". The problem "isn't really that it's bad for
me, the paperclip manufacturer, that my AI destroyed the world, right? That's bad for everyone"
(≈51:05, ≈51:53). Thinking only about the user is "burying the lead"; this reading is "really emphasizing" the
word we in "what we really want" (≈51:53). My interests can be "at cross purposes with yours", and "I
might intend or prefer for my AI to do something that would be bad for other people". The paperclip
AI "isn't value aligned if it maximizes production by enslaving the workers, even if I, the factory
owner, have no qualms about that" (≈51:53, ≈52:39).

The user-centred readings still matter: "we do want it to be aligned to what the user wants when what
the user wants is morally acceptable" (≈52:39).

### Moral disagreement and moral theories

What is morally right is "a hotly contested, for millennia, philosophical problem", among philosophers
and "people more generally" (≈52:39, ≈53:25). His examples: "whether it's right to lie to spare
someone's feelings", whether it is "right or wrong to pirate copyrighted material", whether it is
"right to buy luxuries for yourself when you could be donating to charity", and "Is it right to kill
one person to save five? Right? Or maybe to save a thousand or to save a million" (≈53:25).

A **moral theory** is "a systematic account of morality that tries to answer questions like these"
(≈54:12). One idea is to align AI "to the correct or best moral theory" (≈54:58). But people disagree
"not just" about cases "but what the correct moral theory is" (≈54:58, ≈55:43). He sketches a few
views, saying "This will not be on the exam" (≈55:43):

- **Consequentialism**: "an act is right if and only if it produces the greatest net good of any act
  available", summed "across all people" (≈54:12). **Utilitarianism** "is a kind of consequentialism"
  (≈54:58). On this view lying to spare feelings may be right "if nobody ever finds out about the lie"
  (≈54:58). "A lot of people find that very compelling" (≈55:43).
- **A weighted sum**: increasing the good of "someone who's starving and has nothing" by some amount
  counts for more than increasing "my good by that same amount" (≈55:43, ≈56:30).
- **A complaint model, or maximin model**: "you don't care about the sum. The goal is to minimize the
  strongest individual complaint" (≈56:30). His illustration is a case the captions name "scan
  transmitter room case" (≈56:30). There has been "an accident in the transmitter room transmitting the
  World Cup game", and the person inside "is suffering painful electric shocks". Everyone will be
  unhappy if the broadcast stops long enough to rescue them (≈56:30). "It actually doesn't matter how
  many people are watching the World Cup"; we should "turn it off for 15 minutes and rescue this
  person" (≈57:16). A view that just adds up goodness must say that at some number of viewers "we
  should just let this person continue to suffer" (≈57:16).
- **Non-maximizing versions**: "versions of all these views where you're not even trying to maximize.
  All that matters is producing a sufficiently great sum of good" (≈57:16).
- **Deontological views**, "the most significant divergence": "even acts with good consequences can be
  wrong", if "they violate certain moral rules or rights" (≈57:16, ≈58:04). Examples are rights
  against "murder or theft", and rules that "you have to keep your promises" even when backing out
  would do more good. Then "the question there is how you justify those rules or rights" (≈58:04).

**Paternalism again.** "Even if we did know what the best moral theory was, it might be bad to design
AI to act on that theory if it's not one that is shared by the users" (≈58:50). The reason could be
moral, or practical: "a product that people don't want to use because it doesn't promote their
values" (≈58:50).

### Common-sense morality instead

Another approach starts from agreement. "Most of us agree you shouldn't kill someone even if you could
maybe accomplish a lot of good by doing it", that you should "respect people's rights, keep your
promises, generally be a decent person" (≈59:36). So instead of the best moral theory, "a question that
philosophers are never going to solve", align AI with "people's existing moral views". "We're not
trying to make AI morally perfect. The goal is just to have it be as moral as anyone" (≈59:36,
≈1:00:22).

**Why that might help.** "A lot of these moral theories get pretty wacky in edge cases" (≈1:00:22). A
deontological rule against lying faces "the murderer at the door who's come looking for my friend who's
hiding in the basement"; the transmitter room is another such case (≈1:00:22). Setting an explicit
theory for an AI is risky in a familiar way: "telling your AI to maximize the good could be a little
bit like telling it to maximize paperclip production". It may "figure out a surprising implication of
that goal" (≈1:00:22, ≈1:01:08). By contrast, an agent aligned to common-sense morality "would behave
more predictably, because in some sense it's learned how to make decisions like we do" (≈1:01:08).

**Why it might not.** "It also might be unpredictable in these very same edge cases", "where maybe
common sense runs out" (≈1:01:08). Would such an AI "decide to kill one person to save a million? I
don't know." It is "hard to say, maybe even, what the common sense view on a question like that is"
(≈1:01:54). On the other hand, "how bad it would be if in some sense AI were unsure about the same
cases that we're unsure about? ... If it's just as moral as a person, how bad is that in the end?"
(≈1:01:54).

## Two questions at the end

**Can the AI just refuse?** A student asks whether an AI could choose "not to answer or not act on"
questions outside common-sense morality (≈1:02:40). Webber calls it "a good impulse. I have this
impulse too", but "to not act is one of the choices that's available to you" (≈1:02:40, ≈1:03:26). In
a "fantastical situation" where killing one person would save a city of a million, "you can't avoid
that problem by just saying 'I'm not going to decide.'" Saying so "is taking one of the choices"
(≈1:03:26). This echoes the earlier point about defaults. All of this is about the goal of value
alignment, "before we even decide how we're going to get there" (≈1:03:26, ≈1:04:13).

**Intention and power.** A student notes that morality involves "action, decision, and intention"
(≈1:04:13). An AI "accruing lots of money or people who could take actions on its behalf" could be
organizing volunteers or pursuing something else entirely. The same observable behaviour serves many
goals, so "intention seems to become really important" (≈1:04:13, ≈1:05:02). Webber says the goal "is
presumably going to become observable in some way", but the worry is knowing "in advance whether it
should have this kind of power" (≈1:05:02, ≈1:05:48). It also answers the earlier question of how bad
an AI "no more or less moral than the average person" would be. It is bad if the agent "is way more
powerful than your typical person", or can "unilaterally make much more morally consequential
decisions". Then "its mistakes have much greater ramifications" (≈1:05:48, ≈1:06:33). That is a
reason "to be worried about power seeking": a system with a goal to maximize may realize that more
power brings "more materials, more resources", which helps "with whatever that goal ends up being"
(≈1:06:33, ≈1:07:19).

## The ESR statement for the final project

The last minutes cover the project requirement, which "really has nothing to do with" value alignment
(≈1:07:19). "Your final project requires a one-page ESR statement", the ESR "being the Ethics and
Society Review" (≈1:07:19). "The ESR is to societal risks what the IRB is to risks to human subjects"
(≈1:07:19, ≈1:08:05). The IRB "considers, in fact, only those risks". It is "not allowed to consider
something like the broader risks of research or a project once it's already out in the world"
(≈1:08:05). That gap is why such statements are increasingly "required for grant applications, for
conference submissions", so the assignment is "also practice for doing a thing you might need to do
out in the world" (≈1:08:05).

**What to write.** Students will get "links to ESR instructions and templates", and should read them
(≈1:08:05). "In one page, you're trying to identify a couple of potential ethical risks that could
come along with your research or project if it were deployed in the real world. And then come up with
a strategy for preventing or mitigating those risks" (≈1:08:51). The template's example (≈1:08:51,
≈1:09:36):

- **Risk:** "your tool is intended to serve users with low vision, but if we don't consider their
  perspectives then we might alienate them."
- **Mitigation:** "we'll hold a series of co-design workshops with stakeholders, get their input."

That example is shortened to "one sentence each". The template suggests "one to two paragraphs each
for each risk and mitigation effort" (≈1:09:36). "We're not looking for groundbreaking ethics research",
but "you want to show substantive engagement with the ethical risks that you identify" (≈1:09:36).

**Common risks to consider** (≈1:09:36, ≈1:10:22):

- "whose interests are represented in the research, whose interests might be excluded", and how to
  take "those excluded interests into account";
- "who might benefit or be harmed by the success of it";
- "effect on privacy";
- "misuse or user error": "How could bad actors misuse the research" and "How could users
  accidentally misapply it in harmful ways?"

The recording ends here. The 2024 course website does not link the ESR instructions or templates.

## Summary

Value alignment is the problem of "designing AI agents to do what we really want them to do", and
"this could be a matter of what we intend or prefer, what's in our best interest" (≈1:01:54). These
can come apart (≈1:02:40), and any of them can come apart from what is morally right. Each target brings its own
problem. Intentions need an AI that understands what instructions imply. Preferences must be inferred
from finite behaviour and feedback, which is where this course's methods sit. Best interests are partly
a philosophical question, and aligning to them risks paternalism. Morality is contested, whether you
target the best theory or common-sense views. Webber offers no verdict on which reading is correct.
His claim is that the choice comes before the method, and that it shapes the method. The ESR statement
asks each project to name a couple of real-world ethical risks and how it would mitigate them.

## Student questions in this lecture

| Time | Question or comment | Answer in brief |
| --- | --- | --- |
| 3:55 | How the paperclip example continues | More factories, every job making paper clips, rocks into paper clips; eventually the observable universe |
| 6:15 | "Make a bounded number of paper clips" | Fixes the runaway case but not locking in workers; failure cases are easy to patch once seen, hard to foresee |
| 12:25 | Break the goal into subproblems with a fleet of agents? | The problem runs the other way: inferring all the implied constraints from a minimal instruction |
| 23:13 | Isn't laying out the options itself paternalistic? | Not necessarily for intention and preference readings; but choosing the conception for users can be |
| 25:32 | Anything I say must use concepts others understand | The technical problem: figuring out what the user wants beyond their instructions |
| 28:36 | Pick A versus B, or type feedback? | Related but separate: the goal versus how to train; revealed preferences may favour inverse reinforcement learning |
| 31:43 | Why pick one frame over another? | Recap of three readings; no single answer, it may vary by case |
| 34:02 | Don't the distinctions matter most in extreme settings? | He has not yet said how to achieve any goal; first decide how to understand the problem |
| 39:26 | (exercise) Facts versus gossip | Good sources may be what users don't want, but what is good for them |
| 40:58 | (exercise) Political bubbles; some users overwhelmed by opposing views | Echo chambers versus exposure; interests conflict with each other |
| 44:51 | (exercise) Defining best interest; paternalism | Contested but with much agreement; who should judge; autonomy is itself an interest |
| 47:13 | There is no neutral option, because of defaults | Agreed; open questions are still important and have better and worse answers |
| 49:33 | (asked what is missing) Conflicts among my own values | Yes, but the bigger gap is people other than the user |
| 1:02:40 | Can the AI just refuse outside common-sense morality? | Not acting is one of the choices |
| 1:04:13 | Intention matters: accruing power looks the same for good and bad goals | Power raises the stakes of an average-person level of morality; power seeking |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/06-ethics.md)'s header for the full list. The ones
that touch content:

- The speaker's name is captioned "Dan Weber" (≈0:05); this page uses the course site's spelling,
  Daniel Frederick Webber.
- *Bostrom* is restored from the captions' "Bostonramm" and "Boston" (≈3:07, ≈4:41, ≈7:02). No course
  document prints it. The book is not named aloud.
- The name of the transmitter room case is captioned "scan transmitter room case" (≈56:30) and is not
  restored.
- "We had a very good discussion of the LLMs earlier" (≈1:00:22) does not fit its sentence and may be
  mis-captioned.
- Two student phrases about paternalism and best interest are garbled (≈45:38).
- The captions' "Dean's logical" is restored as *deontological* (≈1:00:22), the word the captions give
  correctly at ≈57:16.

## Related pages

- [Value alignment](value-alignment.md): this lecture's four readings of "what we really want", with
  what earlier lectures say about values and alignment.
- [Whose preferences](whose-preferences.md): people other than the user, paternalism, and the ESR
  statement's questions about whose interests are represented.
- [Reward hacking](reward-hacking.md): the paperclip AI as a specification failure, and why manual
  reward functions miss cases.
- [Asking humans for preferences](preference-queries.md): inferring preferences from behaviour or
  feedback, and what finite data cannot pin down.
- [Lecture 5 — Human-centered Design](05-human-centered-design.md): the lecture that deferred ethics to
  a later session.
- [Lecture 1 — Introduction](01-introduction.md): the course's module on human values and AI
  alignment.
