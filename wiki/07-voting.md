# Lecture 7 — Voting (guest lecture: Colin Megill on Polis and Community Notes)

This is a guest lecture by **Colin Megill**, who has spent "about 13 years" on **Polis**, an open
source platform for gathering a population's opinions (≈0:05). In Polis, participants write short
statements, and other participants agree with them, disagree or pass. The result is a sparse matrix
of votes. Polis runs PCA and K-means on that matrix to find opinion groups, then looks for statements
that people in different groups agree on (≈3:57, ≈7:02, ≈7:48). That idea of consensus across
difference became "the foundation for the conversation with Twitter" about **Community Notes**
(≈8:34). The talk is built around a paper Polis wrote with Anthropic "on opportunities and risks for
using large language models with Polis" (≈2:26). It covers the method (≈2:26–8:34), a long exchange
on whether the method can be gamed (≈9:21–21:39), and a worked example from a county land bank
(≈21:39–25:31). Then come language models inside Polis (≈25:31–33:14), deployments (≈33:14–35:33),
LLM-written group statements (≈35:33–41:44), OpenAI's and Anthropic's projects on human values
(≈41:44–45:37) and Community Notes (≈45:37–53:19). The last twenty minutes are open problems and a
student's challenge to the claim that Polis is "emergent" (≈55:37 to the end).

**Date and speaker.** This is catalog position 7, titled *Voting*. It corresponds to the **Dec 2**
schedule row, "Guest lecture: Colin Megill (Polis)", which was the last session before the project
expo. The recording does not state its date. The speaker introduces himself at ≈0:05 (the captions
spell the surname "McIll" and the platform "Polus"; the spellings here are the course site's). He
says he is focusing on the Anthropic paper "as per conversations with Sanmi and students" (≈2:26),
and the session ends with "Thank you so much, Colin" (≈1:12:36). He calls the Anthropic paper the one
"we wrote with Anthropic last year" and says they presented it to DeepMind "in July of 2023 last
year" (≈2:26, ≈36:19), which puts the talk in 2024.

**This is not the course's voting lecture.** [Lecture 4](04-mechanism-design.md) (Oct 28) already
referred back to "the voting lectures". In this talk a questioner says that "in the class we've gone
through voting and its robustness in some detail" (≈10:08). So the course's own treatment of voting
came earlier. The schedule's candidate is Oct 7, "Aggregated Preference Models via Social Choice
Theory & Game Theory", and that session is not in the catalog. The title *Voting* is the catalog's.
Polis does collect votes, and Megill leaves open "how close we think that is to voting, or whether
we think that's, or if it's a survey" (≈35:33). There is no lecture on voting rules or social choice
theory in this knowledge base; see [preference aggregation](preference-aggregation.md) for what the
course's lectures do say about it.

**Who is asking.** The questions come from the audience. The edited transcript marks some turns as
the instructor's, Sanmi Koyejo, and the rest as students'. Koyejo is named at ≈2:26 and closes the
session (≈1:12:36). His other turns are inferred from content, such as "we've talked about this
before" (≈10:08) and "when we've engaged with you on this" (≈55:37). The transcript header lists the
attributions it is least sure of. This page names Koyejo only where the attribution is secure, and
otherwise says "a questioner".

**No slides.** Megill presents from a browser rather than a deck: the Polis site, a conversation
report, articles, a GitHub issue and screenshots ("I'll just grab that really quickly", ≈10:54; "grab
a report here", ≈21:39). The course has published none of it, so every claim here is cited to the
transcript by timestamp. Several works he shows are described but not fully named in the audio:
the Anthropic paper, whose title is not read out; a DeepMind paper whose title is only partly
captioned (≈35:33); the Birdwatch paper (≈46:25); the article that proposed Polis to Twitter
(≈45:37); and a paper on generalising Community Notes (≈51:48, ≈52:33). This page describes them as
he does and does not supply references. Many names in this lecture are garbled in the captions; see
[where the captions are unclear](#where-the-captions-are-unclear).

## The speaker and the project

Megill's background is "international relations and political science from undergrad", followed by
startups (≈0:52). Polis "was developed as a for-profit pro-social startup between 2012 and 2016 when
we open sourced", and the for-profit "wound down and transitioned into a nonprofit in 2019"; he went
from CEO to president of the nonprofit (≈0:52). He compares the model to Wikipedia, Khan Academy and
Signal, "which are open source nonprofit tech" (≈0:52, ≈1:40). The platform "is deployed by the
national government United Kingdom, Finland, Singapore, Taiwan, and Amsterdam, Netherlands, and
others", plus "a whole bunch of hobbyists" (≈1:40).

He uses the word *Polis* for several things, and says so. There is the website, where you can "log
in, use it for free"; the repo, "the tech itself that people fork"; a methodology, "which is in a
paper"; and "a community, and usage, and users". "Generally Polis refers to that zone of stuff"
(≈2:26, ≈3:12).

## What Polis does

Polis "is a system where people can submit statements and those statements are shown randomly one at
a time to other users", who vote on them (≈3:57). The captions garble the list of options there,
but he gives it plainly a sentence later: people "agree, disagree or pass on statements submitted by
others" (≈3:57). Three design choices follow from that.

- **It is not built around replies.** "Everything that people submit is intended to be an atomic
  statement, which goes into a pool" (≈3:57).
- **It takes whatever votes it gets.** "It's greedy. It'll take any amount of voting that people do"
  (≈3:57).
- **The participants write the survey.** "The kind of intuition for this right off the bat is like an
  emergent survey", "a survey created by the people taking it" (≈3:57, ≈4:44). He places it between
  Reddit, "an upvote site", and something "a little bit more formal", since "someone will start a
  conversation with a population and it can be used in a random sample" (≈4:44).

"The idea is to make meaning of perspectives at scale" (≈4:44). The inspiration was "Occupy Wall
Street" and the Arab Spring. Platforms like Twitter "were useful for mobilization" but struggled to
support "coherent conversations that allowed people to write collective documents" (≈4:44, ≈5:29).
In Occupy, individuals would say "this is what it's about", each asserting "that they were speaking
for everyone". "They're right about some of it but not about all of it", the movement fragmented,
and "it was difficult to produce demands" (≈5:29). What appealed was "systems that got more coherent
the more people interacted" (≈5:29).

### The data and the algorithm

The underlying data is a matrix. "Each statement that people submit is a feature, and then each
participant is a row, and the row is a voting record" (≈7:02). An entry is "a null if they didn't
see it, otherwise it's a one for agree, a negative one for disagree, or zero for pass" (≈7:02). The
lecture writes no symbols; in this page's shorthand, participant $i$'s vote on statement $j$ is

$$v_{ij} = \begin{cases} 1 & \text{agree} \cr -1 & \text{disagree} \cr 0 & \text{pass} \cr \text{null} & \text{not seen} \end{cases}$$

and most entries are null, which is why he calls it "a sparse matrix" (≈3:57, ≈6:16).

This matrix "is amenable to doing PCA and then K-means on, to identify patterns" (≈7:02). The
clustering is of **people**: "You're clustering people, and then you find statements that
differentiate those people", and a set of such statements forms "something like a worldview that's
different than the others" (≈7:02, ≈7:48). Then comes the step that matters most to him: "given that
we see groups, what statements are common among people who think differently" (≈7:48). "This metric
is really what the paper ... we published put forward", implemented "in the codebase back in 20, 2013"
as captioned (≈7:48, ≈8:34). The question behind it is "if you have a diversity of opinion, can you
use that to recover signal about where interesting consensus might be" (≈8:34).

He stresses how simple it is: "a sparse matrix with PCA, and then we look across the groups for what
groups had in common", with "no deep learning". It is "a system that we kind of set and forget",
which facilitators can use "without concern that PCA or K-means are going to do anything crazy"
(≈6:16).

### A worked example: the land bank conversation

Asked how statements actually arise (≈20:54, ≈21:39), he opens a report from a conversation in "a
13,000 person county with four islands in Washington state". The issue was the county's **land
bank**, "a public institution buying up real estate to keep it rural and agrarian", and whether it
"should continue to conserve more and more land" (≈21:39, ≈22:26). The county's name is garbled in
the captions.

The conversation started from a prompt "even just as general as, we're going to discuss the land
bank. What are your thoughts and feelings on it?" (≈22:26). Then "some hundreds of people", "some
single digit percentage of the county", "submitted about 300 statements, cast tens of thousands of
the votes" (≈22:26, ≈23:13).

- **Agreement across groups.** "People generally agreed between groups very strongly that having
  access to the land that's preserved ... is compatible with preserving the natural habitat"
  (≈23:13).
- **Disagreement between groups.** "The question about whether or not it should keep going was
  controversial", that is, whether it is "reducing the land available in the island for development
  and for residents" (≈23:13, ≈23:59). Statements like this have "more loading on the PCA out to the
  right" (≈23:13).

So what comes back is "not a question but actually a whole bunch of responses to the prompt".
"Not everybody submits a statement, but everybody has an opportunity to vote" (≈23:59). A student
sums it up: "people can submit a statement and then people are saying if they agree with it or not"
(≈23:59, ≈24:45). Each statement then "forms part of other people's voting record", and the data set
is "voting records per participant as rows, where each column is a feature and a statement"
(≈24:45, ≈25:31).

## Can it be gamed?

A student asks how robust PCA plus K-means is "as a trustworthy way of getting at consensus", and
"what are the risks of, say, an adversary trying to break this voting mechanism" (≈9:21, ≈10:08). A
second questioner, whom the transcript takes to be Koyejo, adds "I also don't share your strong
optimism for robustness". The confidence, on this reading, comes from PCA and K-means being "classic,
reasonably well understood algorithms", "not from specifically looking at robustness and attacking
consensus via those mechanisms" (≈10:08, ≈10:54).

**The Uber case.** Megill answers that Polis "has been used in adversarial circumstances at nation
scale", most prominently "the usage in Uber in Taiwan" (≈10:54). Uber made "an adversarial attempt
... by sending all their drivers to the conversation", on the question of "whether Uber should be
legal and how" (≈11:40). His argument is that participants have "a very small surface area".
Statements pass through moderators, so a statement the moderators reject is "a no-op". After that,
"you can agree, disagree or pass on statements. This is the surface area you have for gaming"
(≈11:40, ≈12:27). Sending your own people "might have created a larger group, it might have skewed
the sample. But it was kind of one group getting larger", so the method was "kind of naturally immune
to the first thing" (≈12:27, ≈13:12).

**Bots, and why it comes down to the sample.** Bots change this. "Now, it's off the shelf for
Anthropic to build a bot" that votes consistently on statements it has not seen, and you "could say
create three different clusters that really don't exist at all" (≈13:12). "I think that basically is
an arms race that just gets to identity." The question then becomes "what is the sample and how do we
know?", which Polis deliberately leaves to whoever runs a conversation: it "is a tool that can be used
with any sample and we're intentionally agnostic about it" (≈13:12, ≈13:59). The most promising
answer he sees is "in the ZK, anonymous but verified identity space". He mentions experiments that
claim "anonymous voting with ZK passport verification", including referendums "in Russia with this
tech", but "I don't think there's a clear winner yet" (≈13:59, ≈14:45).

**Detecting synthetic groups is open.** When pushed on real people who collude (≈15:31), he calls it
"an open area of research". He would want to know how much variance there is within a group. Polis
has no "checks or metrics or methods to say this group looks synthetic" (≈15:31). The simple case is
"a hundred people have exactly the same vote record". It is harder if you assume "LLMs vote
differently than humans do, where they vote tighter" (≈16:17).

**What an attacker would want.** A student asks for "a concrete adversarial objective" (≈16:17,
≈17:03). His example is the UK's **Policy Lab**, a policy innovation unit with "a collective
intelligence unit". Such units find a minister who "wants to do something new" and run a
consultation, here an ecological one involving "fishermen and people in tourism and people in
industry or transportation or local citizens" (≈17:03, ≈17:49). If it were open at nation scale, "an
industry player who was in fisheries" with an economic interest could add "three very distinct
worldviews and personalities of synthetic citizens that don't exist", "way more dogmatic", in effect
"synthetic extremist groups" pushing its line (≈17:49, ≈18:36).

"I think synthetic experts is probably the most dangerous thing" (≈19:21). If "200 economists in
this group" warn that "our transportation system is going to collapse within 3 months", then "that's
material" if they are real, and very hard to untangle if they are not (≈20:08). LLMs can "draw on
theories and draw on projections or lots of documents" and even "build up effectively a legal case
level grounded opposition" skewed "towards a financial actor". That is "a pretty confusing thing to
unwind for a public servant" (≈20:08, ≈20:54). "If this gains more and more power ... we can
anticipate more and more sophisticated opposition" (≈20:54).

Later, Koyejo says that what has interested him most in past conversations is "the adversarial
angle", "what is gameable", and that he now appreciates more that Megill wants to "push on the
usefulness side of this" (≈55:37). Megill agrees. That is "where I feel the most agency". Because "each individual
conversation is firewalled from each other conversation", the sample and context are "closer to the
responsibility of the owner", which lets Polis "stay out of that" at some cost (≈55:37, ≈56:23).

## Language models inside Polis: the Anthropic paper

The paper with Anthropic asks "what kinds of tasks can the LLM perform within a Polis conversation
and how well will it perform?" They "looked at a number of things like moderation, summarization and
vote prediction" (≈26:18).

**Summarization** was "one of the most promising results", and the question was "whether or not we
can ground a summary in statements" (≈26:18). Polis is close to shipping it. The current approach
grounds at the level of clauses (the captions garble the exact phrase), "so it doesn't really get to
go past a handful of words without grounding it somewhere in the data" (≈27:04). Claude "back in
2023" was "quite good at doing topic modeling from the reports" (≈30:10). Asked whether topic
modelling is "an alternative to the PCA plus clustering", he says the model does it in context, but
after the PCA and K-means, using them as a statistical step to "build on top of" (≈30:56, ≈31:42).
The design principle is "formal ways of feeding in, in a structured way to the prompt, statistical
outputs of previous steps", so "we're not asking the LLM to do very much except the narrative bit",
and whatever it says it "has to ground ... immediately before it moves on". He calls this "a
containment, a unit of hallucination" (≈31:42). He points to Harvey, "the little lawyer from OpenAI",
as an example of breaking work into subtasks "to drive down hallucinations" (≈32:28).

**Vote prediction** worked too well for comfort. Given more of a participant's statements and votes,
the model was asked to predict the next vote, and "it is quite scarily good at predicting people's
votes. I think this is a particular surface area for risk" (≈27:04). The method was "basically giving
it more and more statements, progressively more", and "as you give it more of the participant's vote
history it gets better" (≈28:36). He names two risks. One is that "both actors" can "build good
synthetic voters". The other is that people "mistake the systems for voters" and "use an LLM to
lazily replace people in social research and further intermediate the public from institutions"
(≈27:50).

A questioner, whom the transcript takes to be Koyejo, pushes back: "if you have a good predictor of people's preferences that seems a net win for
correctly capturing people's preferences" (≈28:36, ≈29:25). Megill grants that "people being more
complicated than the models is one thing". His worry is a "weekend hack project" with a system prompt
like "pretend you're a citizen of Romania and the PM is talking to you", which produces stereotypes,
and then "if people believe that it's that good, it ends up out in public institutions" (≈29:25,
≈30:10). For how the course's own lectures treat predicting individual choices, see
[discrete choice models](discrete-choice-models.md).

## Where Polis has been used

He gives three examples of how deployments handle sampling (≈33:14–35:33).

- **A UNP survey by vehicle.** "You get into a vehicle and then go around and then stop every nth
  person and ask them if they'll ride for a few blocks" and answer questions, with "politicians in the
  tuk tuk", so "there's connection to power". That gave "an emergent sample of text, an emergent sample
  of votes" as stage one, followed by "more random sampling in other digital processes". It was also
  run in Pakistan and Bhutan, with "some tens of thousands of people" (≈33:14, ≈34:00). The place of
  the first survey is garbled in the captions.
- **A Finnish public institution** the captions call "Satra", which ran "18,000 people" last year and
  runs conversations "regularly at nation scale" on its own instance (≈34:00, ≈34:48).
- **The Taiwan Uber conversation**, above (≈10:54).

All of them are "basically trying to do some ethnographic research on a population" (≈34:48,
≈35:33).

## Writing a group's statement for it

"DeepMind just dropped a paper, very recently", whose title he reads as "AI can help humans find
common ground with" followed by two words the captions give as "democratic liberation" (≈35:33).
(He uses the word "deliberation" himself later, at ≈51:02.) It cites the Anthropic paper as
inspiration (≈36:19). The question is "can we have the LLM help a group to write a collective
statement of themselves and can we get higher and higher approval on that statement?", in settings
like a citizens' assembly where "the facilitator might be writing the group statement" (≈36:19,
≈37:05). The paper's assertion is that people "like the LLM better than the human", and Megill thinks
"the statements are fantastic" (≈37:05). The researchers' names are garbled; he places the work at
MIT and the UK (≈37:05, ≈37:50).

Asked whether this is a synthesis engine for finding the groups (≈37:50), he explains what Polis has
always done. It "would visualize the clusters and then show them back to people", labelled with "a
set of statements that have voting patterns". The participant had to "reconstruct something in your
head about what the worldview of a cluster is", which is demanding and "changes over time" (≈37:50,
≈38:36). So Polis has two outputs with "two really different goals": a per-cluster snapshot, and a
report that gives "more of an overview". One is for the facilitator or data scientist; the other is
"to show you yourself back to you" (≈38:36, ≈39:24).

A GitHub issue under discussion would show "a collective statement back to people" and have them
rate it, using two models the captions render "01" and "40" (≈39:24, ≈40:12). The hard part is
time. "The votes come in over time and comments come in over time", so if people rate statements and
"the clusters change, how do you manage that"? "I don't think it's impossible, I think it's tricky"
(≈40:12, ≈40:59).

## Human values for language models: OpenAI and Anthropic

**OpenAI's grant program.** "Last year OpenAI was interested in" mapping human values "to have that
be an input to completions" (≈41:44). "It was a million dollar grant program, they gave away
\$10,000 grants", and he advised teams (≈42:31). His toy example: "if you have horror authors, we
might differentiate a horror author from a grade schooler", and very gory completions might go to one
and not the other. Another is that a model "will refuse to write a poem about Trump but it will write
a limerick about Biden" (≈42:31). "This kind of stuff in alignment has to do with human values. And
cynically, moving risk away from the organization into some legitimate third party system would be
desirable if it was possible" (≈42:31, ≈43:17). The program produced "10, 10 different open source
projects" (as captioned), and a prototype of "Polis entirely as chat" that recorded open text and
summarized participants as it went (≈43:17). He expects "agent elicitation" to let a model "follow up
with people to get the next stage of level of detail after they submit a statement" (≈44:04).

**Anthropic's constitution experiment.** Anthropic "tried to look at Claude's constitution using a
random sample in Polis about values". "It did turn out that everybody was interested in everything.
There wasn't a lot of disagreement", "maybe not the most promising result for this one but
interesting that they did the experiment" (≈44:50). It was "written up by Kevin Roose" (≈45:37).

See [value alignment](value-alignment.md) for lecture 6's question of what aligning to "what we
really want" can mean.

## Community Notes

"The work with Twitter began in 2021", after an article suggested "that Twitter use Polis for
misinformation", and Polis started talking to Twitter "in 2022, early 2022" (≈45:37). He shows a
screenshot of "Rishi explaining Community Notes back to Elon Musk" (≈45:37).

**How it differs from Polis.** The Birdwatch paper keeps the goal "to highlight consensus", but "the
specific basis for it is not actually PCAs. They do a matrix factorization" that "works in continuous
space" (≈46:25). "They didn't want to cluster because they didn't want to establish liberals and
conservatives as the base clusters". People might "self-identify with a cluster" (≈46:25). It "aims
to identify notes that people on Twitter will find helpful, including people with different points of
view" (≈47:10).

**The back end.** A questioner asks whether the fact-checking is "a different infrastructure"
(≈47:57, ≈48:43). For a given tweet, people in the system "can all propose notes and they have to
include a link out to some grounding". Others "rate a note as helpful or not helpful" (≈48:43). The
note that is shown "is going to have enough votes, and the votes are going to be from people who are
predicted to vote different". "So if people who historically have voted differently on helpfulness
both find it helpful then it's likely to be shown" (≈49:31).

**Reception and limits.** It "fact checks Elon and fact checks the White House", so "there's general
acceptance between the right and left that it's a fair system" (≈47:57). But "if Twitter becomes a
fire hose of misinformation, there's only so much that a fact check" can do "if people aren't seeing
content to begin with", and the feed algorithm "matters a lot too" (≈47:57).

**Not a misinformation system.** A questioner, whom the transcript takes to be Koyejo, notes that
"while ostensibly Polis is still powering this, the goal is completely different" from Polis's: here
the aim is to pick "the best or single one that we're going to show" (≈49:31, ≈50:17). Megill
agrees, and says what he told Twitter: "Community Notes is not a misinformation system. It's actually
a collective response system" (≈50:17). When a Twitter product VP posted an end-of-year thank-you,
Community Notes "collectively responded" (≈50:17). "You guys think you're building a system for
misinformation that has aspects of deliberation, but you're not, you're building a general system for
deliberation and collective response that you're only applying to misinformation" (≈51:02). That has a
dark side. If "everyone doesn't like a person", "you have group informed harassment", so
"constraining collective response systems to the task" is "a bleeding edge area of research that
actually does need to be solved" (≈51:48). Polis wrote a paper arguing the system "is generalizable"
and "can be adapted to produce mass public opinion", and he hopes someone tests it on Bluesky, which
has an API, so it is now "a hack project level thing" (≈52:33, ≈53:19).

## The larger hope

Polis "has continued to be a focal point for political scientists and CS to connect" (≈53:19). "The
big dream here is that there's an opportunity to connect open source systems for mapping public
views, since we have all this open data now, to these policy innovation units" (≈54:05, ≈54:51).

## Open problems for computing

Koyejo lists where he sees computing helping: "summarization", "describing groups and grounding",
"predicting individual preferences ... or individual judgments, or voting", which can cut both ways,
and "a very basic scalability thing" (≈56:23, ≈57:09). He asks where Megill thinks "computing can be
most impactful" (≈57:09). Megill names two problems.

- **New forms of clustering.** "We don't necessarily want to use K-means" (≈57:09, ≈57:55). They
  have tried graph-based clustering and know there are "more PCs, there's more dimensionality, and
  there's hierarchal clustering approaches", but "we don't have a compelling reason to advance that"
  (≈57:55, ≈58:40). The algorithm names in this passage are garbled. LLMs open further options, such
  as weighting statements by topic or by how substantive they are, or reconstructing "the logic" of
  an argument ("if the land bank purchases more land then there is less land available for
  residents"). That would let you "look at sides in the argument based on voting records very
  differently", but "it's quite abstract" (≈58:40–1:00:14). Novel clustering "is better at finding
  expert signal", telling a group that is "voting differently and it's high signal" from noise
  (≈1:01:48).
- **Vote prediction**, which is "closer to home". Polis "doesn't do any vote prediction" (≈1:00:14).
  Community Notes does it by matrix factorization, and there are papers "using large language models
  to do vote prediction as well" (≈1:00:59). It is promising "because there's room to benchmark on
  open data", and "it's closer to being immediately valuable and deployable" (≈1:01:48).

## Is anything emergent?

A student challenges the word he keeps using. "There's a lot of references to the platform allowing
opinions and issues to naturally emerge", yet "you're using a very fixed algorithm to do the
clustering". Choices like which clusters to amplify "are all actually just subjectivities"
(≈1:01:48, ≈1:02:34).

Megill concedes part of it. Polis "is defensible as emergent" in that "any participant can submit any
statement at any time", and "the clusters are, it's unsupervised learning. It's a function of the
voting data" (≈1:03:21). But "we could drop the word emergent as fuzzy". It is more accurate to say
the clusters "are not dependent on the natural language" and are "totally a function of participant"
behaviour (≈1:03:21, ≈1:04:09). On trust, Polis's approach is "to open source code and to allow people
to run it themselves"; putting the whole thing on chain "is an extreme level of trust that has user
experience implications" (≈1:04:54).

The student clarifies. The concern is not where the code runs but who interprets the results. As it
stands, "it very much feels like Overton window", with "strict containment because the clusters are
the only thing that bubble up" (≈1:05:41, ≈1:06:26). Megill's answer is data access. Polis will soon
ship "a series of five raw data files" in a "read only API form", so people can pull "the raw votes
matrix" into a notebook and "get to work making meaning of it", though "for a participant to make
meaning of raw data ... is a bit of a lift" (≈1:06:26–1:07:59).

The student then proposes that participants pose meta-level questions about what the clusters are,
and that enough of these would be "just sufficient to declare clusters" (≈1:08:45–1:10:18). Megill
asks how you would reconcile 18,000 participants' answers (≈1:09:32), and suggests an issue on
GitHub and a notebook on the open data, since "whatever you do has to work across a data set like
that" (≈1:10:18, ≈1:11:04). The largest open-data conversation, Bowling Green, is "like 2,000 people,
quarter million votes" (≈1:11:04, ≈1:11:50). "The elicitation mode does matter based on the scale"
(≈1:11:50). The student closes with an analogy: "people in Excel can build a Turing machine", so
letting people add any question might be "the irreducible computational substrate". Megill: "I'd
love to read that paper" (≈1:12:36).

## How this connects to the rest of the course

These links are this knowledge base's, not the lecture's; the speaker does not refer to other
lectures.

- **Aggregation.** Polis is a way of combining many people's views that looks for statements
  different groups share rather than a single winner. [Preference aggregation](preference-aggregation.md)
  gathers what the lectures say about combining preferences.
- **Who is in the sample.** Polis leaves the sample to the deployer, and synthetic participants
  threaten exactly that. See [whose preferences](whose-preferences.md).
- **How preferences are asked for.** Agree, disagree or pass on statements the participants
  themselves wrote is a different query format from the ratings and pairwise comparisons of earlier
  lectures. See [asking humans for preferences](preference-queries.md).
- **Strategic participants.** Gaming a Polis conversation is a case of what lecture 1 calls
  strategic agents (lecture 1, ≈19:57). [Mechanism design](mechanism-design.md) is the course's
  treatment of rules that hold up when participants are strategic, through prices and payments. Polis
  relies on a small attack surface and moderation instead.

## Summary

Polis turns a population's statements and votes into a sparse participant-by-statement matrix, finds
opinion groups with PCA and K-means, and looks for statements that people in different groups agree
on. Community Notes adapted the same goal with matrix factorization in continuous space. The Anthropic
paper found language models useful for summarization when every claim is grounded in the data, and
"scarily good" at vote prediction, which is both an opportunity and a risk: synthetic voters, and
institutions tempted to replace people. Megill's view of gaming is that the attack surface is small,
but that bots turn the problem into one of identity and sampling. Collective response systems need
constraining. Better clustering and vote prediction are open problems for computing.

## Student questions in this lecture

Audience questions, including the instructor's. See "Who is asking" above for how the transcript
attributes them.

| ≈ | Question | Short answer |
| --- | --- | --- |
| 6:16 | Clarify the technology: people make comments, and then? | Statements are features, participants rows; PCA then K-means |
| 7:02 | So it is the people that are clustered? | Yes; then find statements that differentiate the groups |
| 9:21 | How robust is PCA plus K-means against an adversary? | Used adversarially at nation scale (Uber in Taiwan); small attack surface |
| 10:08 | Isn't the confidence from classic algorithms rather than robustness analysis? | Answered with the Uber case and the bot and identity problem |
| 14:45 | So the path forward is identity verification? And colluding real people? | Open research: within-group variance, detecting synthetic groups |
| 16:17 | What would a concrete adversarial objective look like? | A fisheries interest adding synthetic citizens and synthetic experts |
| 20:54 | How do the questions arise on the platform? | They are statements responding to a general prompt; the land bank example |
| 27:50 | Is vote prediction just in-context prompting? | Yes, with progressively more of a participant's votes |
| 28:36 | Isn't a good predictor of preferences a net win? | Stereotyped simulations, over-trusted by institutions |
| 30:56 | Is LLM topic modelling an alternative to PCA plus clustering? | In context, but built on top of PCA and K-means |
| 37:50 | Is the LLM a synthesis engine for finding groups? | Polis always showed clusters back; snapshot versus report |
| 47:57 | Is the fact-checking separate infrastructure? | Notes with links, shown when people who usually disagree both rate them helpful |
| 49:31 | Isn't the goal different from Polis's? | Yes: Community Notes is a collective response system |
| 52:33 | Is it organizational, since the technology exists? | Bluesky has an API; a hack-project-level thing |
| 56:23 | Where can computing be most impactful? | New forms of clustering; vote prediction |
| 1:01:48 | Is anything really emergent with a fixed algorithm? | Statements are emergent; clusters are a function of votes; drop the word |
| 1:05:41 | Could participants control the interpretation end to end? | Raw data files and a read-only API, for notebooks |
| 1:08:45 | Could meta-level questions declare the clusters? | How to reconcile 18,000 answers? Open a GitHub issue |
| 1:12:36 | Is posing any question an irreducible computational substrate? | "I'd love to read that paper" |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/07-voting.md)'s header for the full list; it has 77
`[Ed: unclear]` marks, mostly names and short phrases. The ones that
touch content:

- The speaker's name is captioned "Colin McIll" and the platform "Polus" (≈0:05); this page uses the
  course site's spellings, Megill and Polis. The captions also give the platform as "poll", "polls",
  "polish" and "polless".
- The algorithm is captioned "K means" at ≈7:02 and "Canadians", "C means" and "Kines" elsewhere; it
  is restored as K-means throughout.
- The voting options at ≈3:57 are captioned "agree to pass on"; the full list, "agree, disagree or
  pass", is given in the same paragraph.
- The DeepMind paper's title ends in words captioned "democratic liberation" (≈35:33), and *DeepMind*
  itself is restored from "de mind"; no course document prints it.
- *Claude* is restored from "cloud" at ≈30:10; the captions give "Claude's constitution" at ≈44:50.
- *Elon* is restored from "Eli" at ≈47:57; the captions give "Elon" at ≈45:37 and ≈47:10.
- The two model names at ≈40:12 are captioned "01" and "40" and are not identified.
- The researchers behind the DeepMind paper, the authors of the article proposing Polis to Twitter,
  the author of a Community Notes blog post, and a writer on technology policy are all garbled
  (≈37:05, ≈45:37, ≈47:10, ≈44:04). "Kevin Roose", "Deb Roy", "Chris Somerfield", "Keith" and "Rishi"
  are kept as captioned.
- The place names of the land bank conversation and the UNP survey are garbled (≈21:39, ≈33:14), as
  are the Finnish institution ("Satra", ≈34:00) and the UK consultation's subject (≈17:49).
- The clustering algorithms he names at ≈57:55 and the term at the start of ≈58:40 are garbled.
- The questioners' identities are inferred; see "Who is asking" above.

## Related pages

- [Preference aggregation](preference-aggregation.md): what the lectures say about combining many
  people's preferences, with Polis and Community Notes as this lecture's contribution.
- [Whose preferences](whose-preferences.md): sampling, synthetic participants, and replacing people
  with models.
- [Asking humans for preferences](preference-queries.md): statements and votes as a query format,
  vote prediction, and how elicitation changes with scale.
- [Value alignment](value-alignment.md): OpenAI's grant program and Anthropic's constitution
  experiment as attempts to gather human values for language models.
- [Mechanism design](mechanism-design.md): the course's treatment of strategic participants.
- [Lecture 4 — Mechanism Design](04-mechanism-design.md): the lecture that refers back to the
  course's voting lectures.
- [Transcript](../raw/transcripts/07-voting.md) (edited) and
  [verbatim captions](../raw/transcripts/original/07-voting.md).
