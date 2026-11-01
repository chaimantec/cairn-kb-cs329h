# Lecture 8 — Guest Lecture: Joseph Jay Williams (adaptive experiments and Thompson sampling)

This is a guest lecture by **Joseph Jay Williams** on **adaptive experimentation**: running A/B
tests that change who gets which version as evidence comes in, and doing it everywhere people are
already sent messages, emails or explanations. His program's goal is "to coach behavior change"
(≈1:36). The talk has two halves. The first (≈0:05–53:25) is the applied case. Everyday touch points
can become small experiments, and people can assign versions in proportion to how likely they think
each one is to be best, which he calls weighted randomization. Beliefs can come from statistical
models, from experts or from crowds, and a contextual bandit can find the subgroup for whom the
average answer is wrong. The second half (≈53:25 to the end) is the statistics. **Thompson sampling**
on a beta–Bernoulli model is the basic algorithm. Williams explains why he would no longer recommend
plain Thompson sampling, because it inflates false positives and loses power. He proposes Epsilon
Thompson sampling, an adaptive version his group developed, and an **algorithm-induced test
statistic** for analysing the data afterwards.

**Date and speaker.** This is catalog position 8, titled *Guest Lecture: Joseph Jay Williams*. It
corresponds to the **Oct 30** schedule row, "Guest lecture: Joseph Jay Williams (University of
Torronto)" (the site's spelling). The recording does not state its date, but three things place it.
[Lecture 4](04-mechanism-design.md), the Oct 28 session, closes with "next lecture we have an invited
lecture by Joseph Jay Williams" on ideas used "for AB testing and other kinds of online learning,
preference optimization settings" (lecture 4, ≈1:20:40). The speaker refers to himself as Joseph
in imagined exchanges with his audience ("What's your intention today, Joseph?", ≈17:00). And he dates
his work "From 2012 to 2024" (≈3:56). He says he is from Trinidad and Tobago (≈0:05) and mentions
what he "put in for tenure" (≈0:05); he does not name his university aloud. The catalog places this
talk last, although on the schedule it came between lecture 4 (Oct 28) and lecture 5 (Nov 11).

**Who is asking.** There is no introduction by the host on the recording, and no turn can be
securely attributed to the course instructor, Sanmi Koyejo. The edited transcript marks every audience
voice as *Student:*, and this page calls them "a questioner". Williams calls on people by what they
are wearing ("sorry, I'm calling you all by what you're wearing", ≈17:46) and by the names captioned
"Ron" and "Ronnie". He also reads questions typed into an online chat ("I wrote this in the chat",
≈7:46). The transcript header lists the speaker attributions it is least sure of.

**No slides.** Williams presents from slides, but the course has not published them, so every claim
here is cited to the transcript by timestamp. He says the talk's first part is "all the talk I gave
yesterday" (≈1:36), and after a break he turns to "the algorithm work" (≈53:25). Papers on his slides
are mostly not named in the audio. The authors of the stress-message paper and several of his
students' names are garbled. This page describes the papers as he does and does not supply
references. See [where the captions are unclear](#where-the-captions-are-unclear).

## The goal: coaching behaviour change

Williams opens with two requests to the audience: leave with a shareable message about the talk and
with "a clear to-do or could-do" (≈0:50, ≈1:36). He then states the goal of his program: "It's to coach
behavior change" (≈1:36). His examples are coaching people to learn more effectively, to manage
stress, and to exercise or eat healthier (≈1:36). The approach is that "we transform everyday
technology touch points into intelligent interventions" (≈1:36).

The work has three components (≈2:22). The first is **adaptive experimentation tools** that make
experimenting easier and faster, which give "more effective interventions": better explanations of
a concept, or messages that help someone deal with stress. The second is **personalized and
contextualized interventions**. The third is adaptive experimentation for science and practice (the
middle of that phrase is garbled). He says he will abbreviate the first two parts (≈2:22).

The long-term vision is put as a question: "by 2034, how do we have on-demand intelligent coaches that
measurably help people think through many problems and change your behavior for good?" (≈3:56). An **intelligent
intervention** is anything that changes behaviour (a text message, an app message, an explanation of
a concept), and it is intelligent in two senses. It tries to give you the best thing at this moment,
"but also true intelligence is about learning. It's constantly testing out ideas so you can learn
what is going to help you" (≈4:42).

## AdapComps: every touch point as a small experiment

His group's framework takes "components of everyday experience" and makes them into AdapComps
(≈4:42; the edited transcript's spelling, restored from captions that vary between "adap comp",
"adab comp", "Adcom", "ADC" and "Arab comp"; what the name abbreviates is not said). It turns a user
interface, "like a text message or a website", into "a microlab for intelligent intervention"
(≈4:42), where ideas are tested and improved over time (≈5:27). His examples:

- **A message of the day.** Many candidate messages are crowdsourced and generated with LLMs and
  people's input, and the system tries to work out which is best for you and when. Sometimes the
  right message is "get up and go for a walk right now", and sometimes it is that "it's okay to feel
  kind of lazy" and take a break (≈5:27).
- **Emails** sent to get students to start homework early. "We take something as boring as email and
  turn that into an intelligent coach": the subject line and the opening are generated in several
  versions and tested (≈6:12).
- **Explanations on a website.** His own website, he admits, gives everyone the same text. It should
  randomize visitors to different explanations, let them say "this was garbage, here's a better
  explanation", and be "AB testing that to figure out which explanations are better on average and
  what works for you at this moment in time" (≈6:12, ≈6:59). In 2013 his group ran such experiments
  on Khan Academy, testing explanations of concepts and messages to motivate students (≈6:59).
- **LLM answers.** "So anything you touch every day could be an intelligent intervention" (≈6:12). He
  is frustrated that language models, which can generate "dozens of versions" of anything, do not
  test them: "Why are they not AB testing LLM components?" A chatbot could test 10 versions of an
  answer, and "They could be AB testing 200 times more than that" (≈6:59, ≈7:46).

## Not enough data? Qualitative A/B comparisons

A questioner, writing in the chat, objects that small exchanges like an email have small effects:
"I'm unclear about how you're going to have sufficient statistical power for these" (≈7:46). Even an email to 100,000 users
is not enough without a large platform's audience, the questioner adds: "You're not going to have
statistical power" (≈8:33).

Williams gives two answers (≈8:33). First, his group works in settings such as education and mental
health where it has built collaborations at scale, and the approach can work with a few hundred
people, even 200. Second, the next step is to drop the requirement for data. His group's paper **AB
Scribe** is "about qualitative AB testing" (≈9:20). Even when writing an email to one person, you
could use a tool to make several versions and think through how each would land. "So you get no data,
it's all in your head, but the process of AB testing would make you lay out alternatives and think
about the impact" (≈9:20).

The questioner points out that A/B testing means something quantitative (≈10:05). Williams agrees
and sets the class an exercise: "come up with a different word for those AB tests that are actually
qualitative" (≈10:05). For now he calls them a "qualitative AB comparison" (≈10:51). Later, restating
his aim, a questioner sums it up: we think about A/B testing formally, "but in reality we just write
one email", and he is pushing people into the space between, using signals such as how the person
replied (≈16:14, ≈17:00). Williams answers, "I have never said it so well myself" (≈17:00). The goal is
"to get us to rethink the way we're making decisions" and to use weighted randomization, something
between 50/50 and all-or-nothing (≈17:00). Even writing two versions of an email and not sending one
means "I build the habit of AB testing, of qualitative AB testing, is progress" (≈17:46).

## Assigning in proportion to belief

The process he lays out for an intelligent intervention has two parts (≈10:51, ≈11:39):

1. **Generate options** easily, for example alternative versions of an email from LLMs and from
   people, and explore that space to come up with better ideas.
2. **Evaluate and execute.** Judge which options look more or less promising, and then execute, which
   means "actually using AB experiments to give people what looks better, to integrate reinforcement
   learning, human judgment" (≈11:39).

The core idea comes as a classroom exchange (≈11:39–13:57). He holds up two imaginary emails and asks,
"What's the probability A is better than B?" With no information a student says 50%. Then why not
assign each email with 50% probability? That is "Classic AB testing" (≈12:24). Now suppose someone
who knows more says there is a 70% chance A is better. The usual reaction is to send A to everyone,
and "That's actually what we all do. We are arrogant, right?" When he sends an email, he sends one
version 100% of the time, with "no randomization" (≈12:24). He quotes Daniel Kahneman ("Daniel kman"
in the captions): "we live in a terrible world, like Daniel Kahneman said, where binary creatures
living in a probabilistic world" (≈12:24).

An adaptive experiment instead says "let's randomize with weighted randomization proportional to our
belief" (≈13:10). If you think there is a 70% chance A is better, give A to 70% of people and B to 30%.
You keep getting data, quantitative or qualitative, and people's reactions may tell you that 70/30
is too high (≈13:10; the captions run the ratios together as "7030" and "2080"). The proposal is to
stop choosing between giving one thing 100% of the time and 50/50, and to assign items
"proportionally to the probability we think that they're the best, where best has to be defined"
(≈13:57).

## Where the probabilities come from

A questioner asks how complex the model behind those probabilities should be, whether it runs in
real time, and how you decide what goes into it (≈13:57, ≈14:43). Williams: "you can always answer
anything that's worth answering in two words, it depends", and "Those are questions we're going to
spend the next 25 years working on" (≈14:43). He promises one model, "for the two-arm case, A and B,
binary outcomes", and says he will show "that that model actually isn't even good enough" (≈14:43).
That model is the [beta–Bernoulli bandit](#the-betabernoulli-bandit-and-thompson-sampling) below.

The other sources of probabilities he describes:

- **Experts.** Someone might set the probabilities with "a crowdsourced mixture of experts": the best
  marketers in the world each give weightings on 10 emails, they are combined, and after the emails
  go out the experts see the results and update their beliefs (≈15:29). He does not know of papers on
  this: "I'm sure five have, but five is basically none. We need a lot more work on getting human
  beings to set those probabilities" (≈15:29).
- **Statistical models.** His group's main work so far is quantitative: Bayesian methods that estimate
  the probabilities from A/B test data (≈17:46, ≈18:32). "That will get you a Nobel Prize in, let's say,
  chemistry, economics or something, but it won't actually help those other billions of people who
  just want to make better decisions" (≈18:32). For them, the qualitative and crowdsourced approaches
  matter, because "8 billion people are not going to run ABs" (≈16:14).
- **A person reading the data, combined with a model.** After the stress-message experiment below, a
  statistical model could say, under some prior assumptions, "there's a 90% chance that this message
  is better for everyone" (≈24:42). Instead, the data could go to a teacher, who looks at it and at how
  their class differs and judges "there's a 76% chance that this is the best message I can show my
  students" (≈25:28). "We might give our model probabilities, but we get a human judgment as well", and
  the two can then be combined with the beta–Bernoulli model (≈25:28).

A questioner says this sounds "very subjective" (≈26:13). Williams replies that "I almost never have
one belief, okay? I have a Bayesian combination of beliefs, okay?" (≈26:13). One teacher can use
straight statistics, another can add their own opinion, a third can crowdsource from students: "these
are all tools in your toolkit" (≈26:59). He admits he is pushing the formal statistical version
because his group has done more of it, but thinks the more subjective methods will help more people
(≈26:59, ≈27:46). Combining people's probabilities is still "a well-defined process: everyone here
gives me a probability and I weight it, I can reproduce it, I can change it, I can evaluate it"
(≈28:33).

Another questioner doubts that probabilities are the right signal at all, since people are bad at
quantifying and the course looks for low-effort feedback: "I wonder how important it is that the
signal is probabilities, given that I guess I don't trust probabilities and that mean anything"
(≈29:21). Williams calls these "great empirical questions" and good hypotheses to pursue (≈29:21,
≈30:07).

## A worked example: the stress message

The example he uses for AB Scribe (≈19:18–21:39) is an email to students before a test, saying
that stress "can actually help you perform better" and need not hurt performance (≈19:18, ≈20:05).
In AB Scribe, the writer selects pieces of the email and makes each an AdapComp, a place to
experiment; an LLM can then be asked for a version of a passage that will work well "for someone
who's very scientific", for instance (≈20:05). Toggling between versions and their combinations is "this thought AB
test" (≈20:53).

The experiment itself is from a paper he dates to CHI 2023 (the venue is captioned "Kai"; the authors'
names are garbled) (≈21:39). The question: "what could I say to you in three minutes, if you're a first
year programming student, that will increase your performance on a test by 4%?" (≈21:39). Drawing on
psychology research, his group varied six elements: the text, the instructions, a video of him saying
it or not, a link to the paper, asking them to explain what they thought they'd learn, and having
them write a note to themselves (≈22:24). The core message was "when you're stressed, it can actually help you
perform better on a test, it doesn't have to hurt you", and "That message on its own is the control
group" (≈22:24). The control's average grade was 76% (≈23:10). The elaborated versions, which explain
that stress can make you pay more attention, did better: he reads the result as "on average about 80%
compared to 75" and then corrects himself ("76.2 or something"); the size of the gain is partly
garbled (≈23:10).

The payoff he draws is speed: "I think we run like six different experiments in a couple months",
where traditional research might take a couple of years to run that many with 200 people (≈23:56).
And the next question is whether to give the winning message to everyone, everywhere. "Nothing in
life is 100" (≈23:56). The answer is to keep generating versions and keep randomizing, qualitatively
or quantitatively (≈23:56, ≈24:42).

## The beta–Bernoulli bandit and Thompson sampling

The formal version is introduced as what is "called a multi…" (the rest of the phrase is garbled,
≈30:07, ≈30:54). Williams calls it "the most fundamental form of reinforcement learning", says "you
can think of this as randomized probability matching", and names the algorithm, **Thompson
sampling**: "It's also called posterior sampling" (≈30:54). He wants to focus on its simplest form
"because I think everyone thinks we've got this and we have not got this" (≈30:54).

**The setting** (≈30:54, ≈31:41). There are two **arms**, for example explanation A and explanation B.
The **reward** is one or zero: someone says they like the explanation or not, clicks on a paper or
not, buys a product or not. A **policy**, or a policy-learning algorithm like Thompson sampling,
decides how to assign, for instance 35% to one arm and 65% to the other.

**The model.** Each arm gets a beta distribution over the probability that a person says yes. The
prior is $\text{Beta}(1, 1)$: "If I have a beta one one distribution, it's like I saw one success, one
failure so far" (≈31:41). It is the uniform distribution, "saying I see no data so far", so a 20%, 40% or
80% chance of a thumbs-up are all equally likely (≈32:28). Each observed reward is "a Bernoulli,
right, drawn with the parameter from that beta distribution", and because "it's a conjugate" the
update is simple (≈32:28). In his notation the first parameter counts successes and the second
failures, each including the prior's one.

His worked numbers (≈33:14):

- Arm one goes to five people; three like it and two do not. Its distribution becomes
  "beta 1 + 3 comma beta 1 + 2", that is, four successes and three failures:

$$\text{Beta}(1, 1) \to \text{Beta}(1 + 3, 1 + 2) = \text{Beta}(4, 3)$$

- Arm two goes to five people and all five like it:

$$\text{Beta}(1, 1) \to \text{Beta}(1 + 5, 1 + 0) = \text{Beta}(6, 1)$$

Arm two's distribution is skewed towards high values, but it is still uncertain: there could be
only a 0.1 probability that people like it, and a lucky sample (≈34:02). With more observations at the
same ratio the distribution becomes "a much more peaked distribution" (≈34:02). He asks the class for
the mean of $\text{Beta}(60, 10)$ against $\text{Beta}(6, 1)$; a questioner answers that it is the same
and that "the variance should be smaller", and Williams gives the mean as "6 over 7" for both (≈34:02,
≈34:50; at ≈34:50 the larger distribution is captioned "beta 16 and 10"). So the best
guess is the same, but the larger counts make you "a lot more confident" (≈34:50). "Every sample you
get is a success or failure, so you can just update the beta parameters" (≈34:50), which makes it "a
great test bed for all these algorithms" and for the qualitative work too (≈35:37).

**Thompson sampling** (≈35:37, ≈36:24). To choose an arm, draw one value from each arm's beta
distribution and "assign the arm that has the highest expected reward" (≈35:37). In his example arm A is
$\text{Beta}(6, 1)$ and a draw gives 0.5; arm B's draw gives 0.4 (arm B is given as "beta 2 and three"
and then as "beta 3 and three"). A's draw is higher, so A is assigned (≈35:37, ≈36:24). Repeating the
draw, "just do it 10,000 times", and counting how often each arm wins gives the probability that A is
better than B according to the algorithm, say 80% or 70% (≈36:24, ≈37:11). With the $\text{Beta}(1, 1)$
prior on both arms, assignment starts at 50/50 (≈37:11).

He stresses how unfinished this is: "I really think we need to do 10 to 15 years of research just with
this. It's super simple and it's not solved." The inference "is actually not trivial, and I think
there are a lot of mistakes people are making when they use these adaptive experiments and don't
realize it" (≈37:11). The second half of the talk is about those mistakes.

## Turning people's beliefs into betas, and weighting people

Because assignment comes from beta distributions, a person's judgment can be turned into one
(≈37:57, ≈38:43). If someone thinks A is 70% likely to be better, you could ask, "could you represent that
as fictional successes and failures?" They might say: imagine 10 earlier observations of each, with
A at eight successes and two failures and B at five and five (≈37:57, ≈38:43). "So now this is super
interesting, right, because we can actually formalize these probabilities that are so slippery"
(≈38:43). He proposes a paper: study how people express the probability that A is better than B, map
it to beta distributions, and give people "interactive explorers or tools" to help them formalize
their intuitions, testing it with people who know what a beta is and people who do not (≈38:43,
≈39:30). (The captions give "7%" at ≈37:57, where the 70% of the example is evidently meant.)

The same move lets you **weight people** (≈39:30, ≈40:19). One audience member thinks arm A is eight
successes and two failures and B five and five; another, who knows more about how people respond to
emails, thinks nine and one against two and eight. The first can say, in effect, count my successes and
failures at one tenth of theirs, "weight his 10 times mine". "And now that's a way of combining
expertise" (≈40:19). The experiment then starts from that combined human judgment, or from a model,
collects data from both quantitative and qualitative measures, and keeps adding new ideas rather than
stopping (≈40:19, ≈41:04).

**Can it be gamed?** A questioner says this "requires a lot of trust and effort on the behalf of
users", and that someone could claim to be very confident to skew the result: "if I say I'm very
confident about something, I try to skew it in one way" (≈41:04). Williams: "Fantastic, that's another
paper" (≈41:04). He improvises its title and abstract on the spot: "eliciting beliefs from people to
get better decision making" even when some parties want to sway the vote, comparing policies for
combining input and weighting schemes, and showing how a scheme suffers when someone uses confidence
to sway the majority (≈41:04, ≈41:52). It applies to lunch, retreats and companies, where decisions
are made by the "hippo", the "highest paid person's opinion" (≈41:52, ≈42:41). "Don't trust the hippo"
(≈42:41).

**Language models for priors.** A questioner says they "do AB tests for all the papers that I write"
(≈42:41), but waiting for human feedback is slow, and asks whether a language model could be used "to
help you quickly, like, refine your prior" by taking on a role (≈43:27). Williams wants a grad student
to work on it: "I think it's a quick, easy, highly impactful paper" (≈43:27). He points to work by
someone at the questioner's university, captioned "Rob Willer", on "using LLMs to simulate human
behavior" (≈43:27). "Using LLMs to simulate human behavior, it's a fantastic idea, to get priors"
(≈44:12).

## Personalized and contextualized interventions

He then flashes the second component, which he will "not talk about too much today" (≈44:12–47:17):

- A paper on an SMS program, captioned "small steps SMS", that sends daily messages to manage stress
  and be happier (≈44:12).
- A paper on prompts for self-reflection, so people personalize advice to their own stressful
  situation (≈44:12, ≈44:59; the title is garbled).
- A paper on stories about what other people are going through, such as handling stress or planning
  for an internship (≈44:59).
- A paper on using an LLM to adapt a written story to your context. "I was shocked, it actually
  outperformed just a human story" (≈45:45, ≈46:30).
- An **LLM as a thought partner** for procrastination: you type what you are putting off, choose the
  style of response (he contrasts a Trinidadian response with a North American one), and the tool generates messages you can edit and regenerate (≈44:59, ≈46:30, ≈47:17).

His point is about interfaces. "It's the interfaces on LLMs that matter. This kind of interface is
night and day" (≈47:17). Give people ways of interacting with the model, tell them what to say, give
them custom prompts. Where people ask for AI's business value, use cases like these, built "using
psychology and" HCI, are what will matter (≈47:17, ≈48:02).

## When the average hurts a minority: contextual bandits

Back to adaptive experimentation (≈48:02): "How can you use adaptive experiments to discover when the
best intervention for a statistical minority is the opposite of what's best on average?" The setting
is an online course, and the reward is whether a student writes a question about what they are
learning (≈48:02). Two messages are tested (≈48:47):

- **Blue, self-focused**: "generate a question because it helps you spot gaps in your knowledge".
- **Red, peer-focused**: "generate a question so your peers might learn more from it".

On average red does better. Split the data by whether students got the previous problem right, and the
picture changes (≈48:47, ≈50:20). High-accuracy students are 80% of the data and 20% got the problem
wrong (the captions give "8%" in several places where 80% is evidently meant, ≈48:47, ≈50:20, ≈51:06).
For the low-accuracy 20%, blue is "substantially better"; for the rest, red is better (≈50:20). Asked
how the average discriminates ("How is actually taking just the average actually discriminating
against a statistical minority?", ≈49:33), a questioner explains the weighting: the 80% group dominates
the combined result (≈49:33). "So when you combine it they get washed out", and a policy of giving
everyone red would mean "you're hurting a statistical minority" (≈50:20).

He asks whether the problem is bigger or smaller without experiments, going on intuition or a few
comments after class. "I think it's bigger" (≈50:20): if three students said they liked one explanation,
he would give it to everyone and miss the subgroup. Experiments "are just a microcosm, a very
well-defined one, of what we're actually doing every day" (≈51:06).

The fix uses **contextual bandits** (≈51:06). Start at 50/50 but run the assignment "separately for
the low accuracy and higher accuracy groups". In the high-accuracy group, evidence builds that red is
better and red gets most assignments (he gives a 70% chance, ≈51:06). In the low-accuracy group the
algorithm stays unsure, near 50/50 (he says "55 45" and later gives the low-accuracy split as "6535",
≈51:06, ≈51:52), "and that not being sure is good because we collect more data" (≈51:06). The adaptive
version gave the smaller group better outcomes (he recalls about 20% better), and "it actually
increases the statistical power to detect that effect", because the uncertain group keeps getting data
(≈51:52, ≈52:40). In the traditional uniform experiment 36% of the minority generated a question; the
adaptive figure is garbled (≈52:40). "Statistical power to detect the best option of minority increased
from 87% to 89" (≈52:40). He translates that into perhaps 50 fewer participants for the same
confidence: "50 less samples to be equally confident is pretty good" (≈52:40).

He asks the class for their own scenarios where choosing what is better for most people might hurt a
minority (≈51:52).

## Why not plain Thompson sampling

After a one-minute break he turns to "the algorithm work" (≈53:25), and gives away the main point
first: "6 years ago I thought, and I run experiments using Thompson sampling, today I would not tell
someone to use that" (≈53:25). Asked to say more: "fortunately this is an easy solution" (≈53:25).

### Epsilon Thompson sampling

**Epsilon Thompson sampling** spends a fixed share of assignments on traditional uniform
randomization: "with probability Epsilon do uniform random" (≈55:01), and otherwise samples as before.
"If Epsilon is 0.1, 10% of the time you do uniform random" (≈55:01). He thinks of it as more
exploration, or as "keep doing some amount of traditional experimentation in order to reduce the biases
of Thompson sampling" (≈54:13). It also guards against a changing world (an explanation people tire
of, a minority the majority result hides, a class that differs next semester) (≈54:13).

### Analysing the data: false positives and power

The second problem is analysis (≈55:01). Many people apply "fancy debiasing stuff, inverse probability
weighting" (the method is captioned "in Proby waiting"), and "I don't think these are working nearly as
effectively as people think they are" (≈55:01).

The standard analysis compares the two arms with a **Wald z test** (captioned "wall"): the difference
between the sample means of the people who liked explanation A and explanation B, and the standard
error of that difference, which "largely depends on the sample sizes" of the two arms (≈58:53). The
test rejects at a cutoff of 1.96 either way, so that with no real difference the false positive rate,
$\alpha$, is 5% (≈1:02:42, ≈1:03:29). With uniform random assignment and a true arm difference of 0.1,
"power is 80% with a sample size of 785" (≈1:03:29). But "the z test is designed for assumptions of
uniform random" (≈55:48), and Thompson sampling breaks those assumptions in two ways.

- **False positives rise.** Suppose both arms truly have mean 0.5 (≈1:00:25). If one arm has a run of
  bad luck, Thompson sampling stops sampling it and puts nearly everyone in the other arm. "Even with
  800 participants" the favoured arm's mean is estimated tightly at 0.5, while the neglected arm keeps
  a low estimate and the test sees a difference: "you put so many participants in one arm that you now
  think there's a difference" (≈1:00:25). In a sentence: "Basically when there's a random low and a
  mean looks lower, you think there's a difference when there isn't actually" (≈59:39). Thompson
  sampling gives "extreme values of the test statistic" (≈1:03:29).
- **Power falls.** When there is a real difference, the test statistic is reduced, "because you
  actually don't put enough samples in the other arm to tell" (≈1:04:15).

The same happens with Bayesian inference: with no true difference, "Thompson sampling will tell you
that the probability of one arm being better being 80% or higher is really, really high", in 53% of
runs by his figure (≈1:01:10, ≈1:01:55). His other tests found the same for t-test-based analyses and
inverse probability weighting (≈58:53, ≈59:39).

The false positive rate he gives for Thompson sampling varies through the talk: "15% compared to 5%" in
a two-arm trial (≈56:35), "13% of the time, not 5%" (≈59:39), "5% instead of 13" (≈1:02:42), a figure
captioned "30%" (≈1:04:15) and one captioned "133%" (≈1:08:12). The recording does not settle which
setting each refers to, and this page does not choose between them.

A questioner asks whether epsilon greedy would do better. "Epsilon greedy is not better", he says;
Epsilon Thompson sampling is, with "a lower false positive rate and better power" (≈1:01:55, ≈1:02:42).

### The algorithm-induced test statistic

His recommended analysis is "an algorithm-induced test statistic", a method "that other people have
developed and we've applied in this context" (≈55:01, ≈57:21). It "takes the z test statistic and it
regenerates it using the algorithm to collect the data": it generates data under a hypothesis (the
word is garbled) "using the algorithm you actually used and gets a different distribution for the test
statistic, and you get a different cutoff value for doing your hypothesis test" (≈55:48, ≈56:35). The
cutoff is chosen so that the false positive rate is 5% under the algorithm actually used: "let's set
the cutoff value to give you 5%" (≈1:04:15). For plain Thompson sampling in his example, the cutoff
moves from 1.96 to 2.6 (≈1:05:02).

That fixes false positives but not power. With Thompson sampling, "the algorithm-induced test controls
false positive rate to 5%, but power is 17%, which is not great" (≈59:39, ≈1:05:02). The reason: "fundamentally
the data are not discriminating" (≈1:05:02). What Epsilon Thompson sampling does "is it will drive
those distributions apart", so the test statistic separates the no-difference and difference cases
again (≈1:05:02). "So you actually need statistically sensitive algorithms" (≈1:05:02).

### Adaptive Epsilon Thompson sampling

Epsilon Thompson sampling uses "10% uniform random if it's big or small, doesn't care" (≈1:08:12), and
asking practitioners to choose $\epsilon$ does not work: "I don't think you want to be asking about
epsilons" (≈1:05:48). His group's adaptive version, which an idea from students produced (the people
named are garbled, ≈1:05:48), instead asks a question practitioners can answer: "what is a small
difference to you?" (≈1:06:37). If the answer is 0.1, then

$$\epsilon = \text{the posterior probability that the arm difference is less than } 0.1$$

so "Epsilon is the probability that the difference between arms is less than 0.1" (≈1:06:37). When the
arms look close, the algorithm runs a lot of uniform randomization and gets good power and false
positive rate; "if the probability is low we get more Thompson sampling" (≈1:07:24). His examples: a
posterior probability of 80% gives "a very nice Epsilon of 80%", and 5% gives 5% (≈1:06:37; the captions
give the first as "8%" in the step-by-step version at ≈1:06:37 and ≈1:07:24). The algorithm's name is
captioned "TS positive", "TS postive", "TS postf" and "Thompson sampling posst"; it is described as
"adaptive Epsilon Thompson sampling" (≈57:21, ≈1:06:37, ≈1:08:59). He thinks it beats existing
algorithms on average because it adapts, giving "a nice trade-off across different sample sizes and
different arm differences, or effect sizes" (≈1:07:24, ≈1:08:12).

### The results he reports

He reads out the power of each approach in his two-arm example (≈1:08:12; the Thompson and Epsilon
Thompson figures also at ≈56:35):

| Assignment | Power |
| --- | --- |
| Uniform random (traditional experiment) | 87% |
| Thompson sampling | 46% |
| Epsilon Thompson sampling | 66% |
| Adaptive Epsilon Thompson sampling ("TS positive") | 82% |

With the adaptive version and the algorithm-induced test, he says, "you will get a fixed false positive
rate of 5%", and the power "will actually be pretty good" (≈1:08:12); it will "better trade off reward,
power and false positive rate" (≈1:08:12). Reward figures are not read out. The recording does not say
which analysis each of the other figures uses. At ≈56:35 the 66% is "Epsilon Thompson sampling with
this algorithm-induced test", but plain Thompson sampling under that test has power 17% (≈59:39,
≈1:05:02), not 46%. "Uniform random gives you better power in a two arm trial" (≈56:35).

His recommendation (≈57:21, ≈58:07, ≈1:08:59): if you run experiments adaptively, use Epsilon Thompson
sampling, ideally the adaptive version, and analyse with the algorithm-induced test. "You also should
modify the way you're doing your statistical tests" (≈58:07). In practice, "tell me what's the small
difference for you where you want to trade off reward and inference", and the algorithm and test
follow (≈1:08:59).

A questioner restates the point as a trade-off between false positives and other errors that changing
the algorithm can improve, adding that "Thompson sampling is like not even on the Pareto frontier"
(≈57:21, ≈58:07). Williams agrees and summarizes: Thompson sampling has issues his group has
characterized; Epsilon Thompson sampling, ideally adaptive, gives statistically sensitive results; and
the analysis must change too (≈58:07).

## How this connects to the rest of the course

These links are this knowledge base's; Williams does not refer to other lectures.

- **Bandits.** Lectures 1 and 3 promised bandits, and lecture 4 followed the schedule's dueling-bandit
  and Bayesian-optimization sessions, which are not in the catalog. This lecture is the knowledge base's
  only worked treatment of a bandit algorithm. Its rewards are a yes or no for one arm at a time, not
  pairwise comparisons. See [bandits and adaptive experiments](bandits-and-adaptive-experiments.md).
- **Asking people.** Williams asks people for a probability that one option is better and turns it into
  pseudo-counts, which is a different question from the ratings and comparisons of earlier lectures.
  See [asking humans for preferences](preference-queries.md).
- **Combining people.** Weighting one person's pseudo-counts ten times another's, and the HiPPO, are
  aggregation questions. See [preference aggregation](preference-aggregation.md).
- **Who loses under the average.** The minority hurt by the average answer is the
  [whose preferences](whose-preferences.md) question in experimental form, and echoes lecture 2's
  choice between pooling everyone and modelling individuals.
- **Strategic participants.** The worry that someone overstates confidence to sway the result is the
  problem [mechanism design](mechanism-design.md) addresses with incentives; Williams treats it as an
  open paper.
- **Interfaces.** AB Scribe and the LLM thought partner are human–AI interaction designs, and his "It's
  the interfaces on LLMs that matter" fits lecture 5. See
  [human–AI interaction](human-ai-interaction.md).

## Summary

Williams wants every message, email and explanation to be a small experiment, with versions assigned
in proportion to how likely each is to be best rather than all-or-nothing or 50/50. Those
probabilities can come from statistical models, from experts and crowds weighted by expertise, or from
a person reading the data, and he wants far more work on getting people to set them. A beta–Bernoulli
model with Thompson sampling is the basic algorithm, and contextual bandits can find a minority for whom
the average answer is wrong. But plain Thompson sampling inflates false positives and loses power, so he
recommends Epsilon Thompson sampling, ideally his group's adaptive version that sets epsilon from what
the user calls a small difference, and an algorithm-induced test statistic that sets the cutoff for
the algorithm actually used.

## Student questions in this lecture

Audience questions; the transcript marks every questioner as a student. See "Who is asking" above.

| ≈ | Question | Short answer |
| --- | --- | --- |
| 7:46 | How is there enough statistical power for small exchanges like an email? | Work at scale in education and health; and qualitative A/B testing with no data |
| 9:20 | A/B testing is quantitative; is there a name for the qualitative kind? | No; invent one. For now, "qualitative AB comparison" |
| 11:39 | (Asked) What is the probability A is better than B? | 50% |
| 13:57 | How complex is the model behind the probabilities, and does it run in real time? | "It depends"; one beta–Bernoulli model today, plus experts and crowds |
| 16:14 | So we should explore the space between formal tests and writing one email? | Yes: rethink decisions and randomize with weights |
| 26:13 | Isn't this very subjective? | A Bayesian combination of beliefs; many tools in a toolkit |
| 29:21 | Are probabilities the right signal, given people can't quantify? | Great empirical questions to pursue |
| 34:50 | (Asked) Means of $\text{Beta}(6, 1)$ and $\text{Beta}(60, 10)$? | The same, $6/7$; the larger has smaller variance |
| 41:04 | Doesn't this need trust, and couldn't people overstate confidence? | "That's another paper"; the HiPPO |
| 42:41 | Could a language model refine the prior instead of slow human feedback? | Yes: LLMs simulating people to get priors |
| 49:33 | (Asked) How does the average discriminate here? | The 80% group outweighs the 20% in the combined result |
| 53:25 | Would you say more about not using Thompson sampling? | Epsilon Thompson sampling and an algorithm-induced test |
| 57:21 | Is the point that Thompson sampling's trade-off between errors can be improved? | Yes; it is not on the Pareto frontier |
| 1:01:55 | Would epsilon greedy be better? | No; Epsilon Thompson sampling is |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/08-guest-lecture-joseph-jay-williams.md)'s header for the
full list; it marks 163 passages `[Ed: unclear]`, mostly short phrases and names. The ones that touch
content:

- *AdapComp* is the edited transcript's spelling of a term captioned "adap comp", "adab comp",
  "Adcom", "ADC" and "Arab comp" (≈1:36–20:53). It is restored from sound; no course document prints
  it, and what it abbreviates is not said.
- *CHI*, the venue of the stress-message paper and the conference he suggests for a questioner's
  paper, is captioned "Kai" and "K" (≈21:39, ≈41:04, ≈42:41), and is restored from sound alone. The paper's authors are garbled.
- *Wald* is restored from "wall" (≈58:53, ≈1:02:42), and *inverse probability weighting* from "in Proby
  waiting" and "invers poity waiting" (≈55:01, ≈59:39), both from sound alone.
- *Kahneman* is restored from "Daniel kman" (≈12:24).
- *Trinidad and Tobago* is restored from "TR and Tobago" (≈0:05); the word after it, captioned "CIA",
  is unclear.
- The adaptive algorithm's name is captioned "TS positive", "TS postive", "TS postf" and "Thompson
  sampling posst" and is not restored.
- The bandit model is introduced as "called a multi…", with the next word garbled (≈30:07).
- Several percentages are evidently slips of the captions or the speaker: "7%" for 70% (≈37:57), "8%"
  for 80% (≈48:47, ≈50:20, ≈51:06, ≈1:06:37, ≈1:07:24), and the false positive figures listed above. The
  adaptive experiment's outcome for the minority is garbled (≈52:40), as is the size of the stress
  message's gain (≈23:10).
- In the Thompson sampling example, arm B is first "beta 2 and three" and then "beta 3 and three"
  (≈35:37, ≈36:24), and the peaked distribution is "beta 60 and 10" and then "beta 16 and 10" (≈34:02,
  ≈34:50).
- The questioners' identities are not known; see "Who is asking" above.

## Related pages

- [Bandits and adaptive experiments](bandits-and-adaptive-experiments.md): the course's bandit
  material across lectures, with this lecture as the main source.
- [Asking humans for preferences](preference-queries.md): eliciting probabilities and pseudo-counts,
  and LLMs as stand-ins for people when setting priors.
- [Preference aggregation](preference-aggregation.md): weighting people's beliefs, and the HiPPO.
- [Whose preferences](whose-preferences.md): the statistical minority that the average hides.
- [Human–AI interaction](human-ai-interaction.md): interfaces for LLMs, AB Scribe.
- [Lecture 4 — Mechanism Design](04-mechanism-design.md): the lecture before this one on the
  schedule, which previews it.
- [Transcript](../raw/transcripts/08-guest-lecture-joseph-jay-williams.md) (edited) and
  [verbatim captions](../raw/transcripts/original/08-guest-lecture-joseph-jay-williams.md).
