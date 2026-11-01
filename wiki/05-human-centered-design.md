# Lecture 5 — Human-centered Design (design thinking, human–AI interaction, and evaluation)

This lecture steps back from the course's technical methods to ask what it takes for an AI tool to
**work for people**. Sanmi Koyejo calls it "a bit of a departure" from the course so far, which "has
been primarily methods focused" (≈0:53). He uses human–computer interaction (HCI) as a broader frame
around the course's narrower technical scope (≈0:53). His thesis comes from the Norman door: when
people struggle with a technology, "that's not the right way to think about this problem. The right
way to think about this problem is that it's bad design" (≈3:13). In that frame, learning from
human preferences "is a powerful tool as part of the toolbox of building AI technologies that work
better for people" (≈3:13, ≈4:00). The lecture covers technology-centric versus user-centric design
(≈24:05–28:40), and design thinking with its double-diamond method (≈29:25–37:52). It then turns to
human–AI interaction as a field (≈37:52–43:16), prompting as an interface problem and one system
built to ease it (≈44:02–56:28), and trust, reliance, fairness, accountability, transparency and
who initiates an interaction (≈56:28–1:08:42). The last ten minutes cover **how to evaluate
human–AI interaction** (≈1:08:42–1:18:44).

**Date.** This is catalog position 5. It corresponds to the **Nov 11** schedule row, "Lecture:
Human-centered Design", the opening session of the *Value, Alignment, & Human-centered Design*
module. The recording does not state its date. The title matches, and no other session on the
schedule covers this subject. Koyejo says "given we're in 2024" (≈4:46) and "we're almost done with
the course" (≈55:41). [Lecture 3](03-model-based-preference-optimization.md) (Oct 16) had pointed
ahead to "a whole lecture on HCI" (lecture 3, ≈1:05:47).

**No slides.** The lecture is given from slides that the course has not published, so every claim
here is cited to the transcript by timestamp. Koyejo says the slides are "built off of a couple of
tutorials" by someone whose name the captions garble (≈0:05), and that this is "not my core area,
but it's an area that I'm learning a lot about" (≈0:05). Several papers are shown on the slides
without being named aloud: a paper whose figure cartoons prompting (≈44:02), and the paper on
evaluating human–AI pair programming that the evaluation section draws on (≈1:12:31). This page does
not guess them. The one system named aloud is the prompt-writing tool **PromptCharm**, read out as the
reference at the bottom of its slide (≈47:55; the captions spell it "prompt charm"). There are no formulas in this lecture.

**What is not covered.** Lecture 3 said it might use its metric-elicitation stakeholder study as an
example "when we go back there", and might spend more time in "the HCI lecture" on the link between
the algorithmic problem and the human problem (lecture 3, ≈1:05:47, ≈1:09:41). This recording does
not mention metric elicitation. Koyejo also defers two topics: accountability, fairness, transparency
and ethics get "a separate lecture" (≈57:58), and matching AI decisions to human values comes "a
couple of lectures from now" (≈1:05:39).

[Edited transcript](../raw/transcripts/05-human-centered-design.md) ·
[verbatim captions](../raw/transcripts/original/05-human-centered-design.md) ·
[video](https://www.youtube.com/watch?v=VffFArrRSBE) ·
[course website](https://web.stanford.edu/class/cs329h/fall2024/) · [sources](../sources.md) ·
topic page: [human–AI interaction and human-centered design](human-ai-interaction.md)

## HCI, and a warning about caricature

HCI "is broadly a discipline that thinks about designing technology from a human perspective"
(≈0:53). Koyejo contrasts it with "what I'd argue most of engineering and computer science is good
at, which is starting with an engineering problem and solving directly there" (≈1:39). One way to
put it is "applying the scientific method to the art of design" (≈1:39). The sentence after that,
attributed to someone the captions call "Nielson", is garbled.

He states a caveat at the start that applies to the whole lecture: "I'm going to take somewhat
caricatured extreme perspectives on many fields in order to make a point. Indeed, everything is much
more of a spectrum" (≈1:39). He repeats it later: "for discussion purposes I'm going to be somewhat
extreme and say things like black and white. The real world really isn't" (≈26:23).

## The Norman door, and the AI version of it

**Norman doors** are doors that leave you unsure how to operate them (≈2:26). Is it a push or a
pull? It has a handle, but what the handle does is not clear. There may be several places to grab
it. Or neither push nor pull is right, because it is a sliding door (≈2:26). One response is to blame
the user: "we're not clever enough to engage with technology" (≈2:26). The lecture's thesis is that
this is the wrong way to see it. The problem is bad design. Infrastructure, whether doors or "things
like artificial intelligence tools that we're building", fails people "because they're not designed
appropriately" (≈3:13). Norman is "the author of the paper, the book at the bottom" of the slide,
which sets out the design-thinking framing (≈4:00).

Koyejo maps the door onto AI tools through three questions (≈4:00–5:33):

1. **What the user wants to do.** For a door, it is "how do I get into a room". For most people using
   AI, it is "how do I solve a particular task using some AI tool" (≈4:00).
2. **What the user actually ends up doing.** For a door, "how do I operate the door". For language
   models in 2024, the main affordance is finding "the special prompt, magic prompt, I need so that I
   can get this language model to do the thing that I want it to do" (≈4:46). "In some ways it's the
   way the world is now, but I think one might argue it is really weird that this is the way the world
   is" (≈4:46).
3. **How the user learns to use it.** You rarely bump into the same door twice. You learn from
   previous encounters, read labels, or guess and retry (≈5:33). For AI tools there is "special sauce
   about how to create good prompts", talking to other people, and prompt guidelines from influencers
   (≈5:33, ≈6:20). Or, he argues, "most of us just play till we figure out something that works"
   (≈6:20).

Prompting is "this extra art thing that's not science" (≈6:20). It requires "this messy, unclear
process, also unclear outcomes", because you don't know what you will get (≈7:06). His conclusion:
"in at least a well-designed world it's reasonable to argue that this shouldn't be a problem. This is
a failure of our design of the tool" (≈6:20).

**Do we understand AI tools well enough to design them?** A student points out that door builders
understand doors, and doubts that this extends to AI (≈7:06). Koyejo calls it "a fascinating point"
(≈7:06). Part of the gap in AI is "that we don't know that much about the internals of the tools.
Yes and no" (≈7:55). What we know is a "mix of knowledge, some scientific, some emerging, some
folklore about what works and what doesn't work" (≈7:55). It "makes the problem harder, for sure"
(≈8:42). Many tools rest on an optimization technique "which we hope works and is stable", so there
may be brittleness that a door designer would not face (≈8:42, ≈9:29). "But I want to separate that
from trying at all and building tools so that they're usable and better designed" (≈9:29).

## Technology that disappears

A well-designed technology hides its own effort: "if a technology is designed well enough, you
should actually not know that a lot of effort was put in" (≈9:29). The odd consequence is that
"somehow you get no credit if you do a perfect job because it disappears" (≈9:29, ≈10:16). He quotes
an author whose name the captions garble ("Mark Weezer"): "The most profound technologies are those
that disappear. They weave themselves into the fabric of everyday life until they're
indistinguishable from it" (≈10:16).

Part of this is psychology: once something is easy enough it becomes automatic and moves into the
background (≈10:16). Some of it comes from practice. But much of it can come from design that is
simply intuitive, with "not a big learning curve" (≈10:16). "You don't require an instruction manual"
(≈10:16, ≈11:02). His examples are pointing devices and touchscreens (≈11:02). The lecture then asks
how AI technology could be made as intuitive. Koyejo says he will at least mention where the
course's preference methods "might make this more effective" (≈11:02).

## Bridging human function and computer function

HCI can be described as bridging the gap between "what humans can do, or human function broadly",
and "what computers may or may not be good at" (≈11:49). Both sides matter, because as technology
advances "it often makes it easier to imagine ways that you could better bridge the gap" (≈11:49).

On the computing side, interfaces went from punch cards, to the command line ("still useful but
requires high expertise"), to graphical user interfaces (GUIs), pointing devices and touch screens
(≈12:34). He admits "I have seen a punch card. I've never used one" (≈12:34). These were built "to
make it easier for people to interface with computers" (≈13:20). GUIs use "metaphors for objects":
"the icon looks like the thing you want to do" (≈13:20, ≈14:05). Phones have been made "more and
more intuitive", and he reads much of the work on VR and AR the same way (≈14:05).

**Extending the human or extending the computer?** A student asks what the distinction is (≈14:05).
Koyejo calls his account "a story". Part of what happened is "natural technology getting better", and
part is "intentional design thinking to make it easier for people to engage", which is the part he is
focusing on (≈14:52). Punch cards and command lines partly reflected what was possible when computers
began. Interfaces changed "intentionally as a way to bridge easy human cognitive processes and ease
of interacting" (≈14:52, ≈15:38). In the alternative world, computers just get better at being
computers, by speed or parallel processing: "a better and better GPU doesn't necessarily help a
user" (≈15:38). The contrast is with "intentionally trying to think through what makes it easy for
people to engage with technology" (≈15:38).

**The same arc in AI.** Early AI required expertise: "you're writing code as a way to engage with
the tool" (≈17:10). Prompting needs a different kind of expertise, "but it is still a somewhat
specialized skill" (≈17:10). Chatting is less specialized again (≈17:10, ≈17:56). So the move is
"from using code as a way to interface to using prompting as a way to interface to now maybe using
chatting" (≈17:56). Some of the success of these tools comes from the fact that "it's partially just
easier for people, particularly non-expertly trained people, to think about solving real problems"
with them (≈17:56). But "this is not complete", and "the chasm seems wider here than it does maybe in
general computing" (≈18:42). The open question is which interfaces and affordances would make AI
tools easier to use for the problems people actually want to solve (≈18:42).

Two student questions follow.

- **Neuralink** (≈18:42). Koyejo does not see it as built specifically for AI. It is "an interface
  choice maybe", though any interface choice affects AI technology (≈18:42, ≈19:28). Speculating,
  which he says he is doing "wildly", he expects adoption to take time (≈19:28). The current
  technology is "very impressive" but "still quite limited in bandwidth" (≈19:28, ≈20:15). There is
  also a "social governance problem", and it is "still a risky procedure" (≈20:15, ≈21:01). The
  people most positively affected so far, to his knowledge, are people with a disease or
  neurological disorder for whom it solves an explicit problem (≈21:01).
- **Education** (≈21:48). A student asks how education fits, for example whether learning to read
  counts. Koyejo agrees the description is "a bit fuzzy". It assumes "ease of use is a zero learning
  curve thing", but people are educated in particular ways: pointing may need no education, "as my
  kids have taught me", while typing does (≈21:48). His answer is to contextualize: "the right way to
  think about these questions are really deeply contextualized. So who are the people? What are you
  trying to solve? How do we solve the problem for these people?" (≈22:34). That raises equity: "if
  I'm designing for a particular set of people, am I leaving a bunch of other people that could
  benefit out?" (≈23:20).

## Technology-centric versus user-centric design

**Technology-centric design** is "pushing on technology for technology's sake" (≈24:05). We may or
may not account for users, or we have "some abstract notion of users. They're not any kind of real
user. It's some abstracted, metricized user, often like a number that we're chasing" (≈24:05). It is
"actually very reasonable" when a technology already has well-established norms of use (≈24:05,
≈24:51). Koyejo argues "a lot of AI work is roughly in this space", along with pure computing work
like the GPU example (≈24:51).

**User-centric design** centres the user instead. You ask "what can I do to make the user solve
their problem most efficiently", and you design around "the problems, the needs, the focus of the
stakeholders" (≈24:51). The risk of technology-centric design is that "everything becomes a potential
application of whatever tool you're building": you have a cool tool and search for somewhere it is
useful (≈25:36). "The point is not that this has no place". The two approaches solve different
problems (≈25:36).

**Chatbots as a mix.** A student suggests that chat is both. It adapted a technology to a user
problem, which is user-centred, but because it is imperfect "you have to figure out how to prompt
it" (≈25:36, ≈26:23). Koyejo agrees that chatbots are "a mix" (≈26:23). He connects this to the
course's earlier lectures. The base language model, before supervised fine-tuning or RLHF, is by "our
best understanding" one that "has all the knowledge to do all the things chatbots do, but it's just
extremely hard to interface with". On this reading, "what supervised fine-tuning and preference
tuning does is solve the interface problem" (≈27:08). He flags this as "an analogy, not complete"
(≈27:08). There are big models you can chat with without supervised fine-tuning, but "they're worse
at chat", so "chats are a way to close the interface gap" (≈27:54). See [RLHF](rlhf.md).

**The course itself as an example.** The other side of the mix is this class. "We started with a user
interface problem. We abstracted it out. It's still a technical problem, and most of what we've
covered in the class so far is purely technical" (≈27:54, ≈28:40). You "could finish an entire PhD
here on something like chatbots or user interface and never do a user study, just building better
technology in a purely technical sense" (≈28:40).

## Design thinking

The key HCI approach to these problems "is what is known as design thinking", which "challenges the
ways engineers and computer scientists focus on engaging with problems" (≈29:25). The caricature of
the engineer is that you find a problem, find a solution, and then, to write more papers, think of
other solutions to the same problem, "iterating over different ways of solving the problem" (≈29:25,
≈30:10).

Design thinking reframes that. Instead of taking a stated problem and solving "some quantification,
some operationalization" of it, "you take the problem and actually go back and ask why" (≈30:10). Why
is this a problem that needs solving? You repeat this over several iterations: "It's sometimes
called five whys" (≈30:10; the captions spell it "five W's"). "The five is not important"; it stands
for about five levels of depth (≈30:10, ≈30:57). The goal is to identify "the root cause of whatever
it is that technology is meant to solve", going "beyond surface level to deeper introspection"
(≈30:57).

The quote he gives is from Henry Ford: "if I had asked people what they wanted, they would have said
faster horses" (≈30:57). If the problem is getting from A to B faster, the obvious solution is to
make horses faster. The better question leads to a different tool (≈31:43). Within design, "framing
is often seen as a key creative step", and designers report the need "to get to the problem behind a
problem" presented by a client, sometimes called "creating a fresh perspective" (≈31:43, ≈32:29).
The source of this quotation is on the slide and not read out.

### The double diamond

One popular way to operationalize this "is called the double diamond method" (≈32:29). The first
diamond is the **problem** diamond, where you ask the why questions. The second is the **solution**
diamond (≈32:29, ≈33:15; the captioned description of the second is garbled). Each is a diamond
because "you intentionally start with divergence first": ask broad questions, then converge on a
small set of root causes or one root cause. The solution side works the same way: diverge over many
possible solutions, then converge on a good one for the context (≈33:15).

The four stages, which he later summarizes as "discover the problem, define a problem, develop the
solution, and then refine or deliver the solution" (≈37:07), are:

| Stage | Diamond | What happens | Tools named in the lecture |
| --- | --- | --- | --- |
| **Discover** (research) | problem, divergent | Understand the broad scope behind the issue | field studies, interviews, surveys, environmental factors and context, people's education, market research, identifying the different stakeholders (≈34:47) |
| **Define** (synthesis) | problem, convergent | Narrow down to specific root causes | participatory design (talk to stakeholders, perhaps jointly, to reach consensus on the issue), analytical approaches that group related causes, affinity diagrams (≈34:47, ≈35:34) |
| **Develop** (ideation) | solution, divergent | Generate many potential solutions | storytelling (think through a user in a specific context), prototyping ("build quick and dirty solutions quickly") (≈34:01, ≈36:20) |
| **Deliver** | solution, convergent | Settle on one solution | a minimum viable product (≈34:01, ≈36:20) |

Within computing, "the HCI areas are the ones that do this the most", and education does a great deal
of it too (≈34:01, ≈34:47). The hope after the define stage is a root cause "at a deeper level than
the original specification of the problem, which can be vague", as in the horse and car example
(≈35:34, ≈36:20).

The double diamond is "a useful mnemonic", but in practice, for research and for products, "it's not
a one-time process" (≈37:07). You observe, generate ideas, find root causes, prototype, test, deploy,
find what you missed, and observe again (≈37:07). So rather than a cycle you can picture "an
expanding loop", spiralling out over time (≈37:52).

## Human–AI interaction as a field

Closest to this class is what design thinking means for **human–AI interaction**, which "more and
more ... is being formalized as a field" (≈37:52). People name it at different levels of abstraction:
human–AI interaction, human–LLM interaction, and a third the captions garble (≈38:39). Anchoring on a
technology type is "partially technologist", but it is a useful way to organize skills and tools
(≈38:39).

The field has three parts (≈38:39–40:13):

- **The humans.** AI researchers, model developers, domain experts, and end users, each with different
  needs and goals. "Context matters a ton" (≈38:39, ≈39:25).
- **The AIs.** Large language models, but also dialogue and audio systems, recommender systems and
  autonomous driving (≈39:25).
- **The interaction**, "maybe the key new thing here". It can be collaborative, or assistive, with the
  AI helping a human do something, or about understanding, with humans trying to understand AI tools
  (≈40:13).

**How the work proceeds.** First, figure out who the human is. In research the researcher often has
some agency over this; in a product, the product may define the stakeholders (≈40:13, ≈41:00). The
AI usually exists already but "needs some improvements to make it easier to bridge this interface
gap" (≈41:00). Then come three steps:

1. **Design**: why they should interact, what needs to be done to make it happen, in what instances
   and context (≈41:00).
2. **Enabling the interaction**: what can be brought to bear to make it easier (≈41:00, ≈41:45).
   "Most of the work in this middle is about tooling, and most of what we've covered in this class is
   in some ways you can think of as tools that you can bring to bear to make the interaction probably
   easier" (≈41:45). His examples are easing the burden of interaction "by personalization, by getting
   pairwise preferences from people" (≈41:45). "We mostly covered pairwise preferences, but we'll
   cover here briefly other kinds of ways of getting choice or other notions of preference from
   people" (≈41:45, ≈42:30).
3. **Evaluation**, "which we haven't talked a lot about but I think is super important" (≈42:30). See
   [Evaluating human–AI interaction](#evaluating-humanai-interaction) below.

This is where the lecture places the course's methods: they are tools for the middle step. He
notes that the material is "part of like a three or four hour tutorial", and part of entire
disciplines. "LLMs are newish but still there are people whose PhDs are about this" (≈43:16).

## Prompting as an interface

Koyejo calls prompt engineering "our favorite tooling" (≈43:16, ≈44:02). As an interface, it "has been
studied and thought of as quite challenging" (≈44:02). A user interface is traditionally meant to take
a high-uncertainty problem and make it clear, "very clear what the interaction should be to solve a
particular task" (≈44:02). He shows a figure from a paper (not named aloud) that cartoons what
prompting does instead (≈44:02, ≈44:49). You start with high uncertainty and reduce it a little with
prompting strategies and shared best practices, but "it's still a little bit brittle" (≈44:49). Then
something changes and uncertainty comes back. He gives the example "OpenAI changes the version number
under the hood": "something changed under the hood and your solution completely breaks" (≈44:49,
≈45:35). This happens with open-source tooling too, because "technology is evolving all the time"
(≈45:35).

So the language interface cuts both ways. It is "freeing", and it makes AI technology easier to use
in principle. But it "arguably causes lots of new challenges", because it makes it hard to reach the
usual UX goal of "a clear interface approach that has low uncertainty and high reliability" (≈45:35,
≈46:23). He offers a quote "some of you might like": "prompt engineers exist to tickle ChatGPT in the
right spot so that it coughs up the answers" (≈46:23). In real settings a prompt is engineered until
it "actually starts to look a little bit like command line languages", a format that matches templates. "In
principle should be natural language, in practice are highly stylized, specialized things" (≈47:10).

## Example: PromptCharm, a hybrid interface for image prompts

One response is **hybrid user interfaces**: adding GUIs in the middle of prompts to improve usability
(≈47:55). Koyejo's example comes "from colleagues that wrote this talk". It is a system for writing
prompts for image generation, "a reference at the bottom called PromptCharm" (≈47:55). It follows the design
process above.

**Research.** User studies found "significant conceptual gaps when a novice user writes prompts for
image creation". Users often have a clear image or style in mind but struggle to articulate it in a
prompt the model will follow (≈48:41). The paper identified **five major user needs** (≈48:41,
≈49:28):

1. automatically recommending and revising text prompts;
2. balancing automation and user control;
3. support for exploring different ways of framing prompts;
4. version control, so users can go back to what worked earlier;
5. explanations for generated content, so it is easier to see what worked.

**Design.** The features he describes (≈49:28–54:10):

- **Automatic prompt revision, exposed to the user.** Rewriting the user's prompt is "now standard
  actually in many commercial language models. They don't show this to you" (≈49:28). He has no
  percentage, "because I don't know the IP of the companies", but knows specific cases where "many of
  the language models have something in the middle that rewrites your prompts in a way that is more
  likely to work" (≈50:15). PromptCharm shows the rewrite. "I want a painting of a wolf sitting next
  to a human child in front of the moon" might be expanded with an artist's style and "trending on
  ArtStation" (≈50:15). The user can then change the terms if the rewrite misses (≈51:02).
- **Finding similar items.** If you cannot remember an artist's name, it suggests artists or styles
  (≈51:02).
- **Weighting terms.** You can click a word, phrase or style and weight it up or down (≈51:02,
  ≈51:50).
- **Exploration.** Quick prototyping from a drop-down of styles, iterating cheaply on small,
  low-resolution versions. "This works really well with the diffusion technology itself" (≈51:50,
  ≈52:37).
- **History**, so you can go back (≈52:37).
- **Explanations.** For each term it tries to show which parts of the image correspond to it. This
  "helps with building mental models and mental maps of what the technology is doing", which makes
  intervening easier (≈52:37, ≈53:24).
- **Direct manipulation.** Remove an object, such as a mountain in the background, and inpaint
  (≈53:24). Adobe tools let you do this kind of thing (≈53:24, ≈54:10).

The point is to make the technology much easier to use, "as opposed to just write your prompt and
then spend your whole PhD figuring out the right prompt" (≈54:10). He adds briefly that the
evaluation looked at users' accuracy on various tasks with the tool, compared with other approaches
they could have tried (≈56:28).

**Students on the example.** One student says turning a mental picture into words is "a fundamentally
pretty hard problem", even between humans, and suggests police sketches as an application (≈54:10).
Koyejo agrees it "sounds right to me as a cool application" (≈54:55). Another asks whether the mapping
from words to image regions is computed after the fact, as a kind of attribution (≈54:55). Koyejo's
answer names a method the captions garble. The student reads the paper's title from the slide,
"interpreting stable diffusion using cross attention" (≈54:55; "cross detention" in the captions).
Koyejo says "it's better than nothing" (≈54:55). Interpretability tools still need work to be "fully
robust and stable", and robustness has always been the issue, "but I think there are tools that seem
good enough for people to start building interfaces" (≈54:55, ≈55:41).

## What to design for in interactive systems

Koyejo lists what good interactive systems have to consider (≈56:28–58:44):

- **Human cognition and perception.** "The more cognitively loaded the task, the more you want to
  make it easy for humans to be creative" (≈56:28).
- **Trust and reliance.** Ideally users can depend on the tool, where appropriate, to do its task
  reliably. Reliability and "calibrated trust" matter, and getting them right "can be tricky" (≈57:13).
  Users "either trust too much and don't appreciate the corners of where the tool can actually work,
  or they have one bad experience and then think that the tool is garbage" (≈57:13).
- **Accountability, fairness, transparency, ethics.** Tools should work for a broad range of people and
  "don't perpetuate bias or discrimination based on different stakeholder groups as much as
  possible", which he frames as a normative goal many hold (≈57:58). A separate lecture covers these
  in more depth (≈57:58).
- **Personalization, adaptation and easy feedback**, so that individual users with their own
  preferences can engage with the tool, "and improve over time to better align with human
  preferences" (≈57:58, ≈58:44).

### Trust and reliance

**Trust** is "some evaluation of the belief for confidence and reliability, integrity, honesty. It's
really a human property", though we increasingly apply it to machines and agents (≈58:44).
**Reliance** is "depending on someone or something to perform a specific function or task
irrespective of whether trust is present", so the two are distinct (≈59:31).

The lecture then crosses a human decision maker's response with whether the AI's decision is correct
(≈59:31, ≈1:00:16; the captions garble the name of the figure):

| | AI is correct | AI is incorrect |
| --- | --- | --- |
| **Human accepts** | appropriate reliance | **overreliance**, "often sometimes called automation bias" |
| **Human rejects** | **underreliance** | appropriate reliance |

The design goal is a system "such that you're in the green parts of this setup" (≈1:00:16). The colours
are on the slide; he says it straight after describing the two cases of appropriate reliance. The overreliance case is a human who "accepts almost no matter what the AI says" (≈59:31).
Koyejo does not go into the technology, which "a bit more in the reference material" covers, but he
mentions four things that sometimes help (≈1:00:16–1:01:46):

- **Explanations**, as in PromptCharm.
- **Showing uncertainty.** "I think the research is still open on this", because "people tend not to be
  good at actual percentages. They bucket into big ranges like low, medium, high", which is "at least
  my understanding, of the best research in this space" (≈1:00:16, ≈1:01:01). Even so, it can calibrate
  users to what the AI is good or bad at (≈1:01:01).
- **User agency** over when to see results: "self-prompted suggestions as opposed to things being
  automated" (≈1:01:01).
- **Showing the processing.** Seeing that work is happening helps people judge how hard a task is. "Even
  though in some ways it's a bad thing because people are waiting, it can actually be good", since it
  helps them build calibrated trust (≈1:01:46).

### Fairness, accountability, transparency and ethics

- **Fairness**: tools that do not "behave very differently" across gender, sex, other demographics or
  socioeconomic factors, so that they work for diverse populations (≈1:01:46, ≈1:02:33).
- **Accountability**: thinking through the consequences of mistakes and building that into how systems
  are built and evaluated (≈1:02:33). A mistranslation is low-risk when you are playing with a chatbot,
  and high-risk when the translation is used in an asylum decision: "This is someone's life", and "this
  happens, actually, it's a big issue" (≈1:02:33). Stakeholders such as the user or a judge should
  understand the tool's gaps, so that accountability is correctly placed (≈1:03:21).
- **Transparency**, which he calls "slightly controversial" (≈1:03:21). One common argument is "that
  you shouldn't trust models that you can't understand". The counter-argument is "that we actually
  don't understand lots of things we trust" (≈1:04:08). People like to use aspirin as the example: we
  know about the outcome but not the mechanism all that well (≈1:04:08). Similarly, "most doctors, for
  instance, don't understand MRI in any kind of technical detail"; hospitals have physicists for that
  (≈1:04:08, ≈1:04:53). "I don't know where the field will land" (≈1:04:53). Explainability can still
  be a useful way to calibrate users (≈1:04:53).
- **Ethics**: how human–AI interactions play out in the wider world, bridging different stakeholders'
  ethical perspectives, and "to what extent can we have decision-making from AI tools match human
  ethical principles and values" (≈1:04:53, ≈1:05:39). This is "part of the goal of the broader class",
  and he will return to it "a couple of lectures from now" (≈1:05:39). See
  [whose preferences](whose-preferences.md).

## Who starts the interaction

Interaction design also asks who initiates (≈1:05:39–1:07:10):

- **Human initiative.** The human is the creator and the computer is a tool. The goal is to make it
  easy for the human, for example to be creative (≈1:05:39, ≈1:06:25).
- **Computer initiative.** The computer acts, perhaps automatically. "The human is the audience, the
  computer is the creator", and the goal is a computational outcome that meets the need. Automated art
  is one example, which he calls controversial (≈1:06:25).
- **Mixed initiative**, where many real-world systems sit. "Mixed initiative systems allow for
  collaboration where the user and the system both take an active role in carrying out tasks and making
  decisions" (≈1:07:10). Doing it well means coupling automated services with direct manipulation that
  encourages creativity. One way is agents that "take actions only when the agent believes ... that they
  will have greater expected value than not doing anything" for the user (≈1:07:10).

**Summary of interaction design** (≈1:07:55, ≈1:08:42). Ideally the interaction is seamless, with no
explicit instruction manual. That comes from understanding how humans interact with the world and
extending those affordances, and from design thinking's root causes and iteration. The aim is
applications "that users actually want to use as opposed to have to". Beyond usability there are
"maybe unseen human factors": psychological and cognitive aspects, trust and reliance, ethics and
fairness.

## Evaluating human–AI interaction

The last ten minutes are on evaluation, organized by four questions: "how are we evaluating, what is
being evaluated, who is doing the evaluating, when do we evaluate" (≈1:08:42). (Near the end he says
"I forgot there were five things"; the recording names the four above, ≈1:16:21.)

### How: methods, types and metrics

**Methods** (≈1:09:27–1:10:59). *Quantitative* evaluation, "which is I think what we're best at", finds
a number for what should happen: task completion, how many questions were answered correctly, whether
the user completed the task, how long it took (≈1:09:27). *Qualitative* evaluation is more open-ended:
surveys, asking people, asking why a model got questions wrong, what users liked, whether they were
frustrated. A good design study usually includes some (≈1:09:27).

He finds the gap between the two "striking" in language models. Benchmarks rank models fairly
precisely, but "people's lived experiences with models often diverge from what the benchmarks say"
(≈1:09:27, ≈1:10:13). His own view is that this points to "some issue with the quantification", so we
should build better quantitative tools that capture what people like (≈1:10:13). Both kinds "carry
signal": quantitative to compare, rank and select, qualitative to understand the why and to design
better measures (≈1:10:13, ≈1:10:59).

**Types** (≈1:10:59–1:11:45). *Intrinsic* evaluation takes the model on its own, as benchmarks do, and
"may or may not involve users in any explicit way"; log likelihood or benchmark completion are
examples (≈1:10:59). *Extrinsic* evaluation asks how helpful the model is in a real downstream task.
For a coding assistant you evaluate within the coding context, rather than on a benchmark of code
completion tests (≈1:10:59, ≈1:11:45). The two can give very different signals. Intrinsic is faster;
extrinsic is slower "but it can often reveal gaps in the intrinsic" (≈1:11:45).

**Metrics** (≈1:11:45–1:13:18). Some work validates metrics as measures of things like productivity,
such as lines of code added with a coding tool, or cost (≈1:12:31). The choice is between existing
validated metrics and a new one that better captures the context (≈1:12:31, ≈1:13:18). Koyejo says
this part follows a paper "referenced at the end" on evaluating human–AI pair programming, which he
calls "a good read" (≈1:12:31). Its title is not read out.

### What is being evaluated

The object can be "the model, it can be the HCI, it can be the whole end to end" (≈1:13:18). His example
is a code-review tool (its name is garbled in the captions), in which a reviewer asks for a defensive
coding practice and either the reviewer or the author can be the AI. Colours mark code to be added or
removed (≈1:13:18, ≈1:14:04). There is an underlying technology, an HCI interface, and the end-to-end
system. "Most good evaluations do these things separately and then think about the end to end as the
whole thing" (≈1:14:04).

Evaluations also have different **goals**, such as utility and satisfaction (≈1:14:04). For generated
code you could check whether it passes tests, measure its textual similarity to reference code, "or you
could ask a human to give preferences on the code outcomes" (≈1:14:49). "It's a huge design space", and
good studies "pick a subset of these that are most relevant to the context" (≈1:14:49).

### Who evaluates

Lay users, domain experts, or automated evaluation, where "LM as a judge is more and more popular"
(≈1:15:36). "It's tricky to design systems that work for everybody" (≈1:15:36). Koyejo separates
stakeholder groups (experts, lay users, teachers in education, parents, students trying to learn) from
demographic groups. The target group makes a big difference to how you design the evaluation (≈1:15:36,
≈1:16:21).

### When to evaluate

At different time scales: instantly, at the time of interaction; over a short interaction of a few
rounds; over the long term, deploying a tool for a week or more; and in longitudinal studies over weeks,
months or years (≈1:16:21, ≈1:17:09).

## Summary

The goal is that "if one does this well, then you can harness various kinds of AI techniques in ways
that actually solve people's problems and respect people's needs, goals, and values in real-world
contexts" (≈1:17:09, ≈1:17:57). The lecture took two perspectives (≈1:17:57, ≈1:18:44):

- **Enabling human–AI interactions**, the step where the course's tools live. AI tools can keep learning
  from interactions such as preferences, and interaction settings can help a tool be more personalized.
  He names "social choice as an alternative to hyperpersonalization, calling back some of our tooling
  from the class so far" (≈1:17:57).
- **Evaluation**, which maps use cases, users and evaluation mechanisms. "Evaluation itself becomes a
  design problem of picking a design setup for the evaluation that best matches what you're actually
  trying to build" (≈1:18:44).

## Student questions in this lecture

| ≈ | Question | Short answer |
| --- | --- | --- |
| 7:06 | Door builders understand doors; does that extend to AI? | Partly not: we know little about the internals, which makes it harder, but that is separate from trying to build usable tools |
| 14:05 | What is the difference between extending the human and extending the computer? | Technology getting better on its own versus intentional design to make engagement easy; a faster GPU need not help a user |
| 18:42 | What about Neuralink? | An interface choice, not specific to AI; impressive but limited in bandwidth, risky, with a social governance problem |
| 21:48 | Where does education fit, for example learning to read? | Ease of use is not a zero learning curve; contextualize who the users are, and watch who is left out |
| 25:36 | (comment) Chat is both user-centred and technology-centred | Yes, a mix: supervised fine-tuning and preference tuning solve an interface problem |
| 54:10 | (comment) Putting a mental picture into words is fundamentally hard; police sketches? | A cool application |
| 54:55 | Is the word-to-image mapping computed after the fact? | An interpretability method based on cross attention; better than nothing, not fully robust |
| 1:04:08 | (on the transparency example) What is it? | Aspirin |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/05-human-centered-design.md)'s header for the full list.
The ones that touch content:

- The author of the tutorials the slides are built on is captioned "deank" (≈0:05).
- The sentence attributed to "Nielson" after "applying the scientific method to the art of design" is
  garbled (≈1:39).
- The author of the "most profound technologies" quote is captioned "Mark Weezer" (≈10:16).
- The description of the second diamond is garbled (≈33:15), and so is one discovery method after
  "survey" (≈34:47).
- The third level of human–AI interaction is captioned "human-BLM" (≈38:39); the same word appears
  for the model behind the prompt rewriter (≈50:15).
- The interpretability method used for PromptCharm's explanations is captioned "close hawk" (≈54:55).
- The name of the trust-and-reliance figure is captioned "four cordon" (≈59:31), and the phrase about
  how mental models affect trust is garbled (≈57:13).
- The code-review tool is captioned "critique" (≈1:13:18).
- Terms restored from sound alone, with the captioned form: *five whys* ("five W's", ≈30:10),
  *prompt engineering* ("front engineering", once, ≈46:23), *PromptCharm* ("prompt charm", ≈47:55),
  *ArtStation* ("art station", ≈50:15), *cross attention* ("cross detention", ≈54:55),
  *underreliance* and *overreliance* ("underlyance", "overreiance", ≈59:31, ≈1:00:16), *participatory
  design* ("participator design", ≈34:47), *Neuralink* ("Neurolink", ≈18:42).

## Related pages

- [Human–AI interaction and human-centered design](human-ai-interaction.md): this lecture's ideas
  gathered with what lectures 1 and 3 say about HCI and about asking people questions they can answer.
- [Asking humans for preferences](preference-queries.md): where the course's preference methods sit in
  the design, enable and evaluate steps, and human preference as an evaluation signal.
- [RLHF and the language-model pipeline](rlhf.md): supervised fine-tuning and preference tuning as a
  solution to the interface problem.
- [Whose preferences](whose-preferences.md): designing for one group and leaving others out, fairness,
  accountability, and stakeholder groups in evaluation.
- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md): the
  lecture that pointed ahead to this one.
- [Lecture 1 — Introduction](01-introduction.md): the "all of AI will be HCI" claim and the course's
  stated limits on HCI.
