---
title: Introduction
lecture: 1
video: https://www.youtube.com/watch?v=ApF2OenMgfc
source: edited from auto-generated YouTube transcript
verbatim: false
original: original/01-introduction.md
---

# Introduction — transcript

Copy-edited from the auto-generated YouTube captions for punctuation, capitalization, sentence boundaries and mis-heard terms; filler words and false starts were removed. The course publishes no slides, so terms were restored from context, the course website and the course textbook's glossary only. The verbatim captions are at `raw/transcripts/original/01-introduction.md`. The lecturer is Sanmi Koyejo. Student questions and comments, which the captions run into the lecturer's speech, are marked *Student:* and the lecturer's resumption *Koyejo:*, only where the change of speaker is evident from content (the captions' `>>` speaker-change marks were also used). Timestamp markers and paragraph breaks are unchanged. Digits are unchanged except: "01" in the captions (≈52:34, twice) is written "o1" (OpenAI's o1 model), and "CS39H" (≈1:16:26) is written "CS 329H".

**This is an edited transcript.** Restored terms:
- *Sanmi Koyejo* ← "Sammy Coua" (≈0:05)
- *CS 329H* ← "CS39H" (≈1:16:26)
- *CS PhD student* ← "CSPD student" (≈6:14)
- *breadth* ← "breath" (≈6:14, 7:00, 26:58)
- *metric elicitation* ← "metricalistation" (≈7:47), "metric illustration" (≈1:08:43)
- *RLHF* ← "our LHF" (≈7:47), "our" (≈32:27), "our LHS" (≈40:13), "RHF" (≈47:12, 1:12:36)
- *Ed* (the course forum) ← "ED" (≈5:29)
- *Bernoulli models* ← "Bernoli models" (≈14:37)
- *ML* (machine learning) ← "MLA" (≈17:40, 23:01, 59:31)
- *querying* ← "quering" (≈10:04, 10:49)
- *elicitation* ← "illustration process" (≈10:49), "istation mechanisms" (≈31:42), "elication" (≈1:09:31)
- *HCI* ← "hi" (≈29:20)
- *Medium* ← "medium" (≈26:58)
- *learning from human preferences* ← "learn from your preferences" (≈27:47, 44:03)
- *Lit surveys* ← "late surveys" (≈25:25)
- *supervised fine-tuning* ← "supervised man tuning" (≈54:52), "supervised machining data" (≈1:01:03)
- *PPO* ← "a PO algorithm" (≈39:28)
- *DPO* ← "DPL" (≈41:00, 50:16), "DO" (≈46:25)
- *SFT* ← "SFD" (≈43:17)
- *OLMo* ← "Elmo" (≈46:25)
- *RewardBench* ← "reward bench" (≈47:12, 53:21)
- *reward models* ← "road models" (≈47:58), "smaller word model" (≈52:34)
- *reinforcement learning from AI feedback* ← "force learning from AI feedback" (≈41:45)
- *o1* ← "01" (≈52:34)
- *recommender systems* ← "recommener systems", "recommended systems" (≈54:06, 54:52)
- *Californian, Stanford, Palo Alto* ← "Californiaian Sanford Palatoto" (≈1:04:53)
- *probabilistic* ← "probabistic", "proistic" (≈1:10:16)
- *the boat(s)* ← "the bolt(s)" (≈1:13:21, 1:14:07; the game-playing agent example)
- *pre-collected* ← "pre-colcted" (≈44:50)
- *reinvigorated* ← "reinvig reinvigorated" (≈33:13)

**Unclear passages**, marked inline with [Ed: …]:
- "V module" (≈3:11) — probably "first module" or similar; not recoverable.
- "She went a little bit faster than I planned." (≈5:29) — unclear who is meant (possibly the teaching fellow).
- "MSRL" (≈7:47) — presumably IRL (inverse reinforcement learning); left unresolved.
- speaker of "I work on papers on this topic…" (≈8:33) — probably the teaching fellow, not Koyejo.
- "intern" (≈13:52) — student speech; perhaps "in turn".
- "rallies" (≈15:23) — "learning preferences of ___ from people"; unknown.
- "I'm going solve settings" (≈24:37) — garbled.
- "the wrote" (≈30:07) — perhaps "rote".
- "colleague D" (≈30:07) — a colleague's name, only an initial heard.
- "build clients to build" (≈40:13) — garbled.
- "like top" (≈41:45) — student question; probably "a topic".
- "a good question we have um like GPUs to work with or run credit" (≈42:32) — student question, garbled; rendered as "Will we have GPUs to work with, or credits?"
- "of advertised" (≈44:50) — perhaps "amortized".
- "who gave a talk last year" (≈47:12) — speaker name not captured.
- "breeding" (≈47:58) — student; perhaps "building".
- "so actually we don't need previous years I think from this class we'll probably these yes" (≈49:30) — garbled.
- "learning premium preferences" (≈50:16) — garbled.
- "over p" (≈53:21) — student; perhaps "overoptimize".
- "no meaningful important points" (≈53:21) — garbled.
- "like an ad" (≈54:06) — student; meaning unclear.
- "part in scope" (≈1:02:35) — perhaps "keep in scope".
- "re label the pref data" (≈1:04:08) — student guess, garbled.

**[0:05]** Hi everyone, I'm Sanmi Koyejo, faculty in computer science. I work broadly in trustworthy machine learning and AI. Just to check that you're in the right room: this is CS 329H, Machine Learning from Human Preferences. Excited to have everyone here today. In addition to myself, we have a teaching fellow, Sang. Say hello. We'll be engaging a ton with Sang over the course of the quarter, so you have many chances to interact with the teaching staff. The plan today, as always for an initial lecture, is a sort of general overview. So we'll get into

**[0:52]** some of the framing of the course. The course is new. This is the second time we've offered it. It was offered first last fall, and this is the second time we're offering the class. We're still figuring out exactly what this course is. The upside is I think it'll be slightly less experimental than last time, so you'll benefit from some of the experiments we did a year ago. But I also think there are some rough edges, so we'll depend on you for feedback on aspects of the course that you think are going well or badly, to further refine it. The course is timely, I think, and for many of us exciting, given lots of engagements in, or aspects of, machine learning that are very explicit

**[1:37]** about using human feedback. Our goal is to engage with some of these questions both on the application side but also, hopefully, much more foundationally, and I mean foundationally in a broad sense. So both the aspects that are about machine learning, but also we'll touch on aspects that tie to things like economics, psychology; we'll play amateur everything. Hopefully not too badly. Some of this will be with the core staff, some of this will be with invited lectures. I'll go through some of this over the course of the class today. Before going into slides, one nice benefit of the fact that this is the second time we're teaching the class is that the

**[2:24]** core staff and other folks have been proactive about putting together a textbook. So we have a textbook. To my knowledge there isn't a textbook on this topic in the world, or if there is, it's not public. So I think it's a unique resource from engaging in this class. There'll be a link in the slides which you'll be able to access for the book and other material, so you'll be able to see all this stuff. It's a very rough cut, so again, be gentle, but do criticize and give us feedback as you go through. But mostly today we'll go through the introduction. Over the course of the quarter we'll go through aspects related to modeling human choice, some of the model-based techniques and the preference learning,

**[3:11]** the third module being model-free optimization, and then finally a module on human values and AI alignment. So that's the rough setup of the course: an intro section and then these four sections. In addition to, like I said, the teaching time, if we look through the syllabus there'll also be quite a few invited lectures. Early October, so roughly at the end of our [Ed: unclear — "V module"] module, we expect to have an invited lecture on topics relevant to the module that we just covered. This iteration of the course is the

**[3:58]** first time we're having homework. Last time it was purely discussion and lecture. This time we're setting it up as 60% homework. You get the first homework soon, in about a week or so. Unlike courses I've been running for a long time, these will be fresh iterations of homework questions, so again I'm sure there'll be some wrinkles. It's a small-to-medium class, so our hope is there's a lot of discussion back and forth, and we can be adaptive to the needs and what you want to learn, but also we can learn a bunch from you on how to improve the material in the course. There's a big

**[4:43]** focus on projects for a class like this. The plan is that you would organize into groups of up to five students, and each group will have a series of deliverables that at the end will be a final project that'll be presented at least to the class group and potentially to additional folks externally. This seems to have worked well, and many of you have taken courses that have a big project flavor, so that's part of our plan for the rest of this class. And then, as mentioned, because there's a bunch of stuff that we're still figuring out, there's a meaningful load on class participation. So we encourage

**[5:29]** you to engage in the class, either in the class itself or on the other artifacts. There'll be aspects of, for instance, giving feedback on the textbook on GitHub. There will be aspects of engaging with questions and answers on Ed, and then, as already mentioned, in-class participation. So I think that's it for logistics. [Ed: unclear — "She went a little bit faster than I planned."] Again, for a class like this on newish topics, I think there's a lot to be gained by the discussion, so my pitch is: consider coming anyway, and hopefully there'll be some value from engaging in the conversation in the class. Good question. The other

**[6:14]** thing to mention: if you're a CS PhD student, this course counts for either your learning and modeling requirement or human and society requirement, which may give you some sense of the kinds of material that we plan to cover. In the end, this is a technical course, so we'll always fall back on machine learning fundamentals. However, intentionally this is scoped as trying to think about what this means. It's about learning from humans. There's going to be a bunch of work thinking about human engagement, societal considerations, a bunch of these other broader questions. So we'll attempt this mix of breadth and

**[7:00]** depth at the same time, with a slight bias towards breadth in the material. Okay, other questions? If not... yes.

*Student:* I guess a little background, like machine...

*Koyejo:* Okay, so this is background of the instructors.

*Student:* Yeah.

*Koyejo:* Sure. I've been at Stanford a couple of years. Before that I was a professor at the University of Illinois. Relevant to this class, I have been working for a while on ways to get human preferences in classic

**[7:47]** machine learning problems. There's a framework we'll talk about briefly today as well, called metric elicitation, that I worked on, which tried to engage with these questions, strongly related to folks in, say, RL that were doing [Ed: unclear — "MSRL"] (presumably IRL, inverse reinforcement learning), and these kinds of ideas in the ecosystem. All of this got exciting once again, I think for many people, with language models and RLHF being a thing. Again, we'll engage a little bit with this and try to place this in some context. We do a little bit of work related to these kinds of questions. There are some interesting questions on academia and industry for this kind of work that I actually hope will be part of the discussion as we go through. I think that's also

**[8:33]** interesting. I think that's it for my background. I'm happy to go into any more depth. Other teaching staff are free to say more about their backgrounds. Everyone has relevant experiences, but...

*Student:* You like it or...

*Koyejo:* [Ed: unclear — speaker attribution; this may be Sang Truong rather than Koyejo] I work on papers on this topic; since 2023 was not too long ago. That's my background.

*Koyejo:* So we'll go through the material for today. Again, feel free to take a look at the textbook once you get a chance. Our goal today is an introduction, to go through some of the framing of the class and maybe set up some of

**[9:18]** how we'll think about the topics as we go through the next few lectures. The broad area is still being defined, but we attempted to mock up a definition that we can critique, actually, a little bit if folks are interested. This class seeks to explore the challenge of efficiently and effectively eliciting values and preferences from individuals or groups or societies and embedding them within AI models and applications. Our specific focus will be on some of the statistical and conceptual foundations and strategies for interactively querying humans to elicit information that can improve learning

**[10:04]** and applications. As discussed and as framed, many of the questions we'll think about in this class will be through the lens of the machine learning question, but we hope to meaningfully engage with broader impacts of this work, in terms of how it affects individuals, society, all these kinds of questions. The "efficiently" there is going to speak to some of the challenges of interacting with people and trying to do this with as few interactions as possible. So there's a term, query efficiency, that we'll talk about a little bit more, that tries to ask questions when you can about sort

**[10:49]** of things like how many samples would you need, how many interactions would you need to get a particular estimate, a particular function, from interacting with some set of agents, and effectively thinking about the quality of the elicitation process. So getting the signal from people. Any questions on the setup, broad framing? Any strong criticism or weak criticism of these thoughts?

*Student:* I'm curious: the word "interactive" seems like some sort of back and forth...

*Koyejo:* Excellent question.

**[11:36]** *Student:* Yeah. So the question is about "interactively" and why we stated "interactively."

*Koyejo:* I'll engage with this a little bit in a couple of slides. But from a certain point of view, all of machine learning is learning from human preferences, so in fact it doesn't narrow the field at all. The reason for this is that a lot of what AI models, machine learning models, are trained to do is effectively to learn from signals that come from people. Many applications of machine learning are, say, medical applications where people label, or actually almost all applications involve humans creating content of some kind, and then we build models to mimic or approximate that content. So from that point of view, all of machine

**[12:21]** learning is machine learning from human preferences. There's also something much more focused: are we trying to build AI as some intelligence goal? We'll talk a bit about this in a little bit, which again directly engages with the idea of learning from humans. Here we're going to focus on settings where we're much more explicit and intentional about the human signal. I think of the settings where humans are labeling data and then you learn from that data as, in some ways, implicit. So there's a preference effect that will show up based on wherever the data

**[13:07]** labeling is coming from. In this class we'll focus on the subset of these questions where the goal of the learning procedure is very explicitly about learning from preferences, often through interactive processes. So exactly as you stated, we'll focus on this, which seems the gap that's most interesting. I think this is again the motivation for this class and trying to think about these questions. It won't cover everything, but that will be our explicit focus. Thank you. It's a good question.

*Student:* I think I like it. I like the broadening of it, because in so many real-world AI applications the data set is immutable, and that's just not the real world, and sampling from humans...

**[13:52]** *Student:* ...like the defense we just witnessed: humans don't agree with themselves 25% of the time.

*Student:* You give the same exact label depending on if you had lunch or not; you get a different answer.

*Student:* And so we have, you know, bringing a distribution that models the actual labeling process of [Ed: unclear — "intern"] (perhaps "in turn").

*Student:* And so I like broadening to include that part, that system, into the entire thing.

*Koyejo:* Yeah. Now this is a super interesting point. We'll touch on this a bit: questions like the inconsistency of humans and how to think about human labels in many settings, and some existing literature or ways of thinking about what this means, how to engage

**[14:37]** with this. We'll talk a bit about models. Now we choose Bernoulli models. I don't know if that's the truth, so we'll talk a bit about at least some framings that I think about this issue. But yeah, things like noise, or at least uncertainty that comes from inconsistent signals from humans. Great point. Okay. As mentioned a little bit in the last slide, our goal is to engage with both the foundations and a variety of strategies for interactively querying humans to elicit information that can improve some kind of learning goal or some kind of application. So

**[15:23]** we'll focus mostly on learning systems that have very explicit human-in-the-loop components, with some bias towards interactive kinds of systems. We'll engage a little bit with some of the foundations. Some of these come from economics, psychology, marketing, statistics. We'll talk about applications. Front of mind for many of us are applications in language, so again, learning preferences of [Ed: unclear — "rallies"] from people, but also a long history of work in things like robotics and, I don't remember what we meant by... oh, logistics, yes. Okay, so explicit logistics; I don't think we'll

**[16:08]** talk much about logistics, but the applications in logistics, for instance, where you're trying to plan delivery or routing or things like that, and you might take preferences into account and think through, or explicitly elicit, preferences as a way to improve things like routing models. All of these we'll focus on through the view of machine learning. What this means is we'll try to set up the problem, try to understand some of the angles of the problem, and then we'll focus on questions related to things like modeling, estimation, evaluation within each of these problem settings. I think part of what this means, and we'll talk through prerequisites a little bit, is that there'll be an assumption that you're

**[16:55]** comfortable with the basics of machine learning, enough to write some simple programs and build simple machine learning models. So train/test/validation splits should not be surprising to you. If they are, we should have a quick chat. Logistic regression should not be surprising to you. You should have taken this class; if it is, again, we should chat to make sure things would be a good fit. So we'll need that component, and we'll think about this as a meaningful part of the problem. The next aspect, the second arm of this, is thinking about what this means in terms of human preferences. How do we think about humans in here? I think

**[17:40]** it's an interesting thing, because depending on where you sit in the ML world, I think we have some aversion to thinking about humans, even though humans are everywhere. You'll see this in how many of you, or even your colleagues, engage with some of these questions. There's an argument made; in fact, I was on a panel last week where someone made an ambitious statement. They said, and I don't know if this will be true, but maybe food for thought for the group, that within a generation (I don't know what a generation might mean, maybe 5 to 10 years) they think all of AI will be HCI. And so actually there won't be an AI thing anymore, in the sense that all the hardest and most interesting questions

**[18:26]** will be about human-computer interaction. I think there's a plausible case to be made for this. We've made meaningful progress on the pure algorithmic side, and many of the questions that seem important to solve to get to applications or impacts that we want seem bottlenecked by how we think about humans within our deployed systems. So we'll try to think about this a bit. Again, some of this will be grounded in literature, so we'll have papers for you to read, but some of this will also be just discussion in the class and thinking about these questions. A bunch of sub-questions show up: various aspects of biases, I think you brought up, or questions of to what extent we should assume rationality in the humans. Is that

**[19:12]** a good assumption, or does it break? Questions of thinking of human errors as noise, and when that might or might not be a good or bad assumption; various kinds of notions of correctness, expertise, and human engagement with AI systems. Often the questions change if it's a human or a group of humans or a broad societal context, so we'll attempt to engage in all of these questions. There's some balance based on expertise, literature, preferences, though again that's something we're open to adjusting based on feedback from the class. So questions, for instance, if

**[19:57]** I'm interested in eliciting a preference: does the problem change if I'm trying to get your preference as an individual versus the whole class's preference? How do I deal with the fact that we won't agree on many things, for instance the size of groups for projects? What does it look like to think of a synthesis and aggregation of preferences, and think about this in ways that might get at broader values? What does this look like in terms of strategic agents that may be trying to gain some coordination system, and are there settings where we can build tools to engage with these kinds of questions? The last bit, but quite important, is that the nature of this class will mean that in

**[20:44]** many settings, we'll almost always have a meaningful ethical angle that we'll try to think through. This shows up in a bunch of different ways. I have a few examples here. For instance, questions of humans: if you're building a system, you're going to deploy it, you pick who is going to give you signal and whose preference you're going to try to get the model to align with, and that choice has an effect downstream. So which humans you're getting preferences from has some meaningful effect. Some of this can be positive, some of this can be tricky and look exploitative. We'll try to engage a little bit with aspects of all

**[21:29]** these questions and not shy away from ethical questions that might be part of what it means to do modern AI and engage with learning from human preferences. Okay, I'll pause for questions or reactions.

*Student:* I have a question about the last part. As we say, we often do data sampling to make sure the data is coming from different scenarios and different sectors, so that a model is trained to handle all sorts of edge cases. Will we also come up in this course with some kind of human sampling, where we make sure that we are taking into

**[22:15]** consideration different groups of humans, for those human preferences to be, in a true sense, ethical human preferences from all groups?

*Koyejo:* Yeah, it's a great question. If we're framing this question in terms of ethics, and maybe representation across different subgroups, are we going to engage in methods that allow us to think about this question carefully? We'll touch on it a little bit. We have at least one lecture that engages the question, though I don't think deeply enough, and I think this is actually a really good point. I don't think the literature is complete on this question. There's a bit of work, and we'll add some of it to references, given the interest, that thinks about versions of this

**[23:01]** human preference learning when you have different groups, and thinking about this question of, say, representative sampling, or other ways to think about balancing preferences across groups. But I'll also mention that I think this is one of those areas where the field, at least the ML subfield, is fairly early on. Other folks have thought about this: there's some work in economics, there's work in ethics broadly, thinking about these questions. I think it's a great project direction if you're thinking about projects: ways of engaging with getting preferences across diverse groups. It's a good question. Okay, yes.

*Student:* Along the line of individual sampling, is there

**[23:48]** machine learning, but...

*Koyejo:* Yeah, this is a fascinating question. The question is, I guess there's a whole literature on learning with limited samples, and so limited data of various kinds. To what extent are we going to engage with that? This is a good one; I hadn't thought about this very specific angle. I actually like that question a lot. We'll engage with this implicitly, because in almost all settings the learning problems that we'll set up will, by construction, require learning with limited samples. Again, engaging with some of what I mentioned before about querying humans being expensive, we're often under some budget constraint on sample size.

**[24:37]** Yeah, it would be good to actually think about maybe being more explicit about that part of the framing. It'll be implicit in problems where we hadn't planned to be that explicit, but it's an excellent, excellent question and it'll show up everywhere. So [Ed: unclear — "I'm going solve settings"] we'll need to learn with limited data. We'll be using some of the tricks of the trade: pre-training, foundation models, all that kind of stuff. Yeah, great question. Thank you. Yes.

*Student:* You mentioned it would be a good topic to explore for the final project. It made me wonder: are most of the final projects coding projects that output something, or are they more research on theoretical questions, or what's the scope of that?

*Koyejo:* Yeah, we'll have more. So this is like, what does the project look like?

**[25:24]** We have a pretty wide breadth of things that would be considered good projects. We'll try to get feedback all the way through. We will have documentation this week as well, saying a bit about our perspective on what makes a good final project. But to your question, theoretical research makes sense. Critical examination of a field makes sense. In some settings, a literature survey might make sense. Lit surveys are harder than people give them credit for; I'll just say that up front. People think it's an easy way to engage, but I actually think a good lit survey is quite hard. Or technical research with code or some other program artifact, all

**[26:11]** these will be in scope. Okay. And also applications: we think about, this is an area that seems to touch lots of different application areas. I think most of you, at least from limited one-quarter experience and also just the zeitgeist, will end up in language, but vision makes sense, makes sense. There's a really fun application, I'll see if we can get someone to show up, but there are some applications in legal and policy that I learned about recently that are kind of cool. So yeah, a bunch of different areas that you can imagine applying these kinds of tools. Feel free to expand, explore, all that fun stuff.

**[26:58]** *Student:* The project of last year is still up on Medium.

*Koyejo:* Oh, okay. Yes, we should add that link somewhere.

*Student:* So if you want to find the project of last year, I can forward it over. It's searchable on the internet.

*Koyejo:* Cool. Everyone searches. It's great. Okay. So, what else to say? This is an emerging topic in some ways. I think the edges of the topic are unclear. It's also broad. We're not going to try to be exhaustive. We have some breadth bias, so we'll try to cover lots of different topics, but we don't expect that we can cover everything that's relevant to this question. So

**[27:47]** some other aspects of this. I talked about this at the beginning a little bit, but in some ways all of AI you can think of as learning from human preferences. In some sense it's a catch-all, so we'll avoid lots of that part of the problem. There's also, beyond the data itself, the fact that people in this room are the people who actually build machine learning and AI models. It's sometimes underappreciated how individual decision-making and choices actually have a meaningful impact on what the actual models are that come out of some production process. You're making choices about which problem you actually want to solve and what's feasible, where you're going to go look for data, what kinds of architectures,

**[28:34]** what kinds of loss functions, what kind of optimization algorithms. All these are individual decisions that have a meaningful impact on AI models. So again, if you want to go the catch-all route, this is a kind of learning from human preferences, because as a designer you're making preference decisions about the algorithm, for instance, the data, the loss functions. This is not what we mean, but I want to say that this, I think, is also a meaningful way of thinking about these kinds of questions. There's a bunch of work on things like model architectures, beyond high-level problem definition, even things like how one builds, most commonly in graphical models and causal inference, where you put a lot of inductive bias in models. But even more general framings often use expertise in various ways. You know,

**[29:20]** people have argued, for instance, that convolutional networks were a thing because people noticed convolution was a good inductive bias and matched things about human vision, for instance. So there are many ways that you can think about expert knowledge and inductive biases. Again, we're not talking about that, but I want to mention that this is important. And then we'll touch a little bit, but we won't go into any meaningful depth, on HCI problems broadly. I think it's super important. The gap is partially expertise, partially scope, so we won't do a super deep dive. I would say, though, that experience or interest in HCI will generally serve you well if this kind of topic is something that you're interested in. So questions about interface, questions

**[30:07]** about process, questions about things, some of these are [Ed: unclear — "the wrote"] things like how do I design a study and get IRB approval. Many in the building, or actually on campus, don't know how to do this because we don't do it that often, but if you're going to do work like this, particularly if you're going to actually query humans, that kind of experience can be very helpful. So some of you, I expect, might consider projects that engage with those kinds of questions; I'm encouraging that as something you might think about. Okay. Just thinking broadly again, this broad framing of human feedback shows up everywhere. I'm showing a nice figure out of a recent paper, borrowing some slides from [Ed: unclear — "colleague D"] talking about how human

**[30:54]** feedback shapes a lot of the explicit machine learning process. As mentioned already, things like data selection, labeling, model selection, training, evaluation, deployment, context. There's a bunch of good work taxonomizing the ways that human preferences end up shaping what we're building in machine learning models. Again, I won't talk too deeply about this, but I want to mention it for grounding my statement about human preferences playing a big role in lots of what we do when we're building models. So all the way from how we construct data sets, and how we might think about questions on things like synthetic data, for instance, which often have explicit judgments

**[31:42]** and decision-making within it, all the way to things like how we specify constraints of various kinds, or real-world constraints embedded into models, various ways of adapting models, and so forth. I'm mentioning it also because, again, it's out of scope for the class, but there's a bunch of work that thinks about ways to capture human preferences to engage with everything on this page. There's work on elicitation mechanisms for constraint specification, for instance, which we're not going to talk about that much, but I think is a very important subset of problems, for instance in logistics problems and planning. Okay. So, examples and applications.

**[32:27]** I'm hoping to also learn from you some of this, because I often learn some cool new things from this. So just to get the elephant out of the way: GPT got a lot more people excited about what it means to use feedback. In many ways it's been argued, depending on where you stand, it's this revisionist thing. Did we expect it? Did we not? I don't know. But of the many innovations that got this to work, in the sense of people getting good experiences engaging with a language model, it's been argued quite strongly that a lot of the work on trying to align to human preferences via things like RLHF made a big difference. So I

**[33:13]** think, again, some of this reinvigorated interest in this area, and a lot of this work builds on a long history of work. A lot of it is particularly for language models and various mechanisms for capturing feedback and building language models. To the earlier comment or question, things like document-level interaction, label consistency queries from humans or experts, word-level interaction. So I have some language model; can I have a human tell me which terms are most influential, or label those terms within a language

**[34:00]** system? Can a human help in thinking of which features to add or remove based on what we think might be important? That's still an important part of most MLOps frameworks and large-scale deployed systems: some human intuition about what might be important features, all the way to things like humans trying to help select model parameters, thinking about both the measurement and then feedback on where models are doing well or failing, and using that signal to improve or explore across ranges of models. Examples of this: versions of this, and again the references are in the slides, so feel free to take a look. So things like

**[34:49]** trying to improve parsers by labeling connections between different words. "Pat ate the cake on the table that I baked last night." And the parser, you know, might say "I baked the table," because it had an incorrect interaction between the term and the noun that it is supposed to be labeling. And you might correct this: human understanding that I baked the cake, and you might include this within a language model system as a way to improve its quality of parsing. So, for instance, getting parts of speech correct, or just more generally trying to get the right structure in examining or explaining a sentence. Some of these are still

**[35:37]** important problems that are worked on independently. Arguably, lots of these things language models seem to be much better at without as much explicit intervention, but some of these questions I think are still quite interesting to think about how to frame, and some of these papers explicitly think about how to get feedback efficiently from people to improve systems that look like this. Okay, so another big line of work: we'll spend some time on this, going through it in some detail, but it's useful to look at some of the early descriptions of some of the work trying to improve learning from human preferences. As many of you know, in the standard

**[36:23]** framework we start with supervised learning from humans. I'm talking about language models now, to give some context. With a language model, as many of you know, you start with some pre-training: generally you train a model to do a good job predicting next words on web data. Once you do that, the common next step is supervised fine-tuning, where you get examples of questions and answers that generally somewhat knowledgeable humans give, that might be relevant for a certain query. And then you get these specialized examples. They're typically much

**[37:08]** smaller. Web data is huge in terms of the token counts; you go down to something of the order of often thousands of examples to do supervised fine-tuning, where the objective is still the same, still doing next-token prediction, but the model gets better at question answering in general from this part of the process. And then the next step is generally this comparison data. This is thought of as querying humans to get some kind of preference signal between different kinds of completions for a certain query. There are various ways of doing it. Sometimes the most

**[37:54]** commonly used approach is pairwise preferences. So I ask a human: I have some framing, some query, I have a set of different completions, and I ask the human which of the completions they prefer. And then I train some model to be better at responding with the preferred response, I guess, from either the pair or a set. So, for instance, if you have four different possible responses, then you might ask the person to pick between the four. Typically this is discrete choice. Typically, again, these are somewhat limited sets of samples. In this class, all of these are important in training language models.

**[38:40]** We'll spend a bit more focus on the step two version of this. Again, this interactive: I think of step one as mostly one-shot. There's a bunch of work offline to query a bunch of people to get good completion examples. Step two is typically best done interactively. Actually, it would be good to engage with some of this, in the sense that some versions of this work do things interactively and some versions do things offline. We'll dive into some of the technical details of those differences over the course of the class. But in either case, you get examples and people label them in terms of preferences. You can think about this narrowly, in terms of narrow preferences for completions. You can think about this more broadly as maybe embedding value somehow

**[39:28]** in terms of what they think a language model should be doing. We'll try to engage in both of those perspectives on this question. And then the next step is the optimization step. Typically two and three are done together, which is a combination of diverse mechanisms. The most popular one is using a reinforcement learning strategy, like a PPO algorithm. We'll touch a bit on this, combined with trying to get preferences through interaction, and over the sequence the model gets better at getting high rewards, so gets better at picking or choosing a completion that's likely to be the same as what a human expert would

**[40:13]** have picked. Okay, any questions on discussion so far? We've outlined some of the existing literature, particularly within language, that has engaged with thinking about learning from human preferences. Any questions so far on the framing and how we think about topics? Yes.

*Student:* Yeah. How much will we do of step three, in terms of training policies with the rewards?

*Koyejo:* Yeah. So the question is how much will we do of step three. How much are we going to implement, for instance, RLHF? The plan is a meaningful amount. I don't know how to answer that question more accurately than that, but our plan is to include implementation. So we'll [Ed: unclear — "build clients to build"]

**[41:00]** some systems and actually test things like this, DPO, other ways of doing performance...

*Student:* Like on language models?

*Koyejo:* Yes, on language models. Yeah, so you have some work on homework, definitely on project. Yeah, it's a good question. Okay. Other questions? Or if anyone knows of other interesting applications that have a similar flavor of human preference measurement to improve algorithmic systems, be it your favorite example. Yes.

**[41:45]** *Student:* I was wondering if reinforcement learning from AI feedback would be [Ed: unclear — "like top"]...

*Koyejo:* Yeah, it's a good question. As a contrast to learning from human feedback, there's also now work thinking about AI judgments, for instance language model judgments, as ways to improve models. Given the thesis of this class, we don't plan to spend a lot of time on those. Often the techniques, at least the machine learning part of the techniques, are effectively the same, with some differences in the query mechanisms, so I think stuff will transfer over reasonably well, but the plan is to focus much more on given feedback that's

**[42:32]** *Student:* [Ed: unclear — "a good question we have um like GPUs to work with or run credit"] Will we have GPUs to work with, or credits?

*Koyejo:* This is a good question. So the question is, are we going to have GPUs or credits to work with? Working on it slower than I would like. Almost definitely have something. The size and scope is not yet clear, but we'll try to figure this out before any meaningful computational homework or projects. Good question. The bottleneck of academic work in this space is compute, almost always. Yeah.

*Student:* Oh, are the homeworks primarily implementation focus?

*Koyejo:* Yeah. So are the homeworks

**[43:17]** implementation? Our plan is a mix: some conceptual, a fair amount of implementation.

*Student:* So in a lot of research, like pure ML research, people don't usually go to steps two and three, where maybe it's model architecture and they'll just do pre-training plus SFT. So I'm curious: are there specific applications where human preferences are just avoided? Or at the industry level it's always done, but on the research side...

*Koyejo:* It's a great question. So the question is, a summary of the question: many ML applications don't do very explicit human preference. Is there

**[44:03]** some gap between, I'll frame this as, research versus academic work, for many kinds of questions? Indeed, most of the published work that engages with real-world learning from human preferences, at least in the machine learning literature, tends to be from industry. I think there are a variety of reasons for this. One is that it is a bit more challenging to do a good job of collecting human preference data. Partially you have to go through a bit more process. In many companies either the process is lower overhead for

**[44:50]** various reasons, so we don't need to delve into details, or we can, I don't know, or the processes are managed by a bunch of people that will do the process for you, so it's more straightforward. It can also be expensive. In many versions of this you want to pay the people that are giving you signals or preferences, particularly the SFT one but even the preference one. And so for many academic research things, in some sense GPU or compute is a sunk cost [Ed: unclear — "of advertised"] (perhaps "amortized"), and this is an additional thing, and people don't always do it. There are few data sets out there, and I think we'll use some of them, like pre-collected

**[45:37]** human preference data sets that one can use. I think I'll frame a lot of the work in the class around either synthetic or existing data sets. I think some of these blocks lead to this gap: who is actually doing the work. Our hope here, so we'll engage with some of these topics, is to build enough foundations such that the more one has to do some of these applied things, the gap is lower: what you need to do to get things off the ground is easier. A specific question was about specific applications that are engaged with differently. I'd say most interesting big language models are not academic models. There are a few

**[46:25]** outliers. There's something out of this company out of Seattle, I forget, they did OLMo, AI2. Yes. And there's some work there that's trying to do meaningful large-scale language models with end-to-end everything. But that's a big one, a very obvious one; there's just not that much end-to-end with all of this process that includes collecting human data. A lot of it will use existing data, like DPO, for instance, which we'll talk about a bit, but famous work engaging in some of these questions uses some public data.

**[47:12]** *Student:* One question: are these reward models, or the relative, some open-source model which we can plug into any model, or does it have to be custom-built to, say, a language model or a vision model that we're building?

*Koyejo:* Yeah. So the question was, are there good downloadable RLHF models, or essentially do we need to build our own? This is a great project question. This is an interesting one, in the sense that there is now more effort in trying to publicly share reward models. There's this RewardBench thing that [Ed: unclear — "who gave a talk last year"] is building, and a few public infrastructure efforts to

**[47:58]** engage with this. The reason I mentioned this is a good research question is that in language in particular, a lot of the signal is that training a reward model separately and then training a language model to fit the reward model tends not to work all that well. The most successful implementations actually update both the language model, like this whole process. So you collect data at the same time as your improvement model.

*Student:* With the kind of model you are [Ed: unclear — "breeding"] (perhaps "building")?

*Koyejo:* Yes. Actually, I can just mention that almost always the reward models are: you take your language model, you cut off the head, and you put on a classifier

**[48:45]** at the end. We'll talk about specifics and what this looks like in a few lectures. By next lecture I think we'll have enough grounding to understand this. Mechanically, it's some big unwieldy model, as big as your language model. Procedurally, it's not fully known why you can't plug and play language models that well with reward models. There are a few hypotheses out there. I think it's active, interesting research. Again, I think an excellent potential project. Particularly if you look at public ones, or public data, trying to ask some questions about why they break sometimes when I try to

**[49:30]** take a language model separately, take a reward model separately, and try to stitch things together. In practice, these are often trained quite close to each other. There are a few explanations in the ether, things like: is this a distribution shift issue? Should we think about the reward models actually learning human preference, or just getting a local approximation that's good for updating the language model? I don't think we know the answer, so very much the frontier of the research base. I think a great, another project idea. [Ed: unclear — "so actually we don't need previous years I think from this class we'll probably these yes"]

*Student:* So I guess there's some recent work, somewhat recent work, that does away with explicitly learning the reward model, like

**[50:16]** DPO.

*Student:* So do you think there is still a case for learning the reward model explicitly, or is this just...

*Koyejo:* Another fascinating question, another great research question. I chuckled to myself. We'll talk about this a fair amount. In fact, the way we've set up the course material, there's a whole section on learning from human preferences implicitly, without, so things like pairwise signals but without an explicit reward model, so things like DPO will show up there, but other kinds, so things like bandits will show up there as well. And then other ways of thinking about [Ed: unclear — "learning premium preferences"] that are explicit about learning a reward model and then using that as part of the optimization

**[51:02]** process, depending on the setting. I think the community is pursuing both. Purely computationally, it's much cheaper not to have a big reward model, because they tend to be big, at least how they're currently implemented, sitting around when you're building these. In RL also, in settings where people can get away with things like behavior cloning, they essentially treat the reinforcement learning problem like a regression problem, and you don't explicitly have a reward model. As a perspective on the problem, I think the reward model itself is valuable as an artifact, because it hopefully tells us something about human

**[51:48]** preferences that we can then maybe examine offline, and it's also useful for evaluating it itself and what it's doing. Most of the field doesn't take that view. The reward model is only useful insofar as it helps you train the learning model that you're interested in. So if you can get away with training a learning model without an explicit reward model and you get similar performance, then many people, many implementations, would do that. So I guess the short answer is you don't need it. In practice, many people prefer not to have it. I think it's valuable, but it's much more of a conceptual, philosophical view than something that I have a great

**[52:34]** practical answer for. I think it's one of those things where, in addition to getting something about the model, it can also give you signals about where things might be breaking. I'd actually be curious, because there are experts in this room, if people have either alternative opinions or expansions of this idea. Yes.

*Student:* I'd say you're 100% right that people aren't using the reward model for anything but getting a better agent, up until o1. And o1 is just using infinite monkeys, where I just sample a thousand and then use a smaller reward model to arbitrate between samples, and then say that's the one I like, and then iterate on that. So that's where the reward model makes a lot of sense, but it has to generalize beyond the local pref data set. And that's, you know, the biggest issue:

**[53:21]** the reward model is easily hackable. If you [Ed: unclear — "over p"] on the reward model, it will just start outputting, it just hacks the reward model, and you don't have enough pref data set to prevent that, other than...

*Koyejo:* Yeah, we'll talk a bit about this overfitting in various ways from reward models. [Ed: unclear — "no meaningful important points"] I'll try to think about it; I think this is an important question that I'd love to get a better answer to, because I'd like to advocate for keeping reward models around more. But yeah, another angle: RewardBench is motivated by this idea of examining reward models themselves to say something about what it is the models are learning. Again, if you think

**[54:06]** they're learning human preferences, there's something there. But the jury is out, and I think most of the field doesn't care all that much. So again, this class is framed as learning from human preferences whether you're explicit or not. So in some ways we're not engaging as directly; this is not a point of view that we need to take for this. We'll talk about algorithms that try to use both, with and without explicit rewards. But it's a fascinating question what you actually need to get at the task. Yes.

*Student:* This is [Ed: unclear — "like an ad"] because recommender systems are probably how a lot of people interact. Preferences...

*Koyejo:* Indeed.

*Student:* Yeah.

*Koyejo:* We'll talk a bit about recommender systems, but what are you going to say?

**[54:52]** *Student:* Oh, like examples of preference.

*Koyejo:* Oh, yeah. Yeah, for sure. Yes. We'll talk about recommender systems and some of the other applications. This question of whether you need reward models as a foundational question, I think that's still okay. Many of you have already seen this, but these are results from a paper you can look up; we'll have this on the slides. They showed in some of this early work that, for instance, on summarization tasks you could get much better results if you explicitly used human feedback and preferences, as opposed to things like the generic pre-trained model, which is noisy, not that bad, not that great; supervised fine-tuning

**[55:38]** improves things a meaningful amount, and then explicit human feedback tends to improve things meaningfully further, and again a lot of this is borne out in the results and in the artifacts that we're using now. So that's motivation for a perspective on the problem. Here are some examples, again in the paper or you can see this in the slides, showing a human reference, a supervised fine-tuning model that tries to answer this question, and then a model that uses human feedback. Okay. So why do we care about this question? It engages a bit with some of the discussion earlier. There are a bunch of different reasons. I don't think it's uniform across people

**[56:23]** who care about this problem. One of them is that sometimes you're interested in signals or evaluations where you don't have a good explicit metric or loss function, so it's unclear what it means to evaluate progress in that setting. For instance, if I want to build a chatbot that's funny, I don't know what the equation is that quantifies funny. Someone here might, but you can imagine getting examples from people, or rankings from people, that say "this statement is funnier than this other statement." This gives you a signal that you can then use to train a model that will improve on this task. So it's useful in settings where explicit

**[57:11]** rewards or costs or losses are just really hard to specify and we think humans are universal experts, or at least good experts, at getting a signal for those questions. Another is settings where stakeholders care a lot about the outcome, and again the specification problem. So things like healthfulness, questions of things like fairness, where again there are many, perhaps reasonable, definitions of what good is; they don't all agree, and you want to use interaction with human preferences as a way to specify a good target, say typically across a large stakeholder group. It's often useful,

**[57:59]** it's sometimes useful when there's some ideal behavior and we don't know how to fully specify it, but we can use evaluation signals as a good proxy. We'll see a bit of this when we construct synthetic evaluators. We'll touch on this a little bit. And then, depending on who I talk to, there are lots of these conversations where really it's just a good proxy for: we know there's a problem, we know that humans are good at fixing this kind of problem, we don't really care about preferences, we just want humans to help us fix our issues. All the way from things like, you know, the model makes a certain kind of spelling mistake all the time. If

**[58:44]** it's a single spelling mistake, sure. If it's a broad range of spelling mistakes, maybe having labelers tell you the different kinds of mistakes the model can make can be more efficient or practical than trying to specify all the settings of this and come out of it. As you can see, there's a broad range, all the way from much more explicit interest in, say, values or preferences for their own sake, and sometimes these are reasons why we engage in this, and sometimes it's just a useful proxy for some real-world outcome that we'd like to get. Okay. Questions? See hands? Okay. So I've given some

**[59:31]** examples of all these, though happy to give more, to fill missing gaps. Okay. There's been a lot of progress over the past couple of years. This is, again, I'd say, one of the more active parts of ML research work. But there are still lots of places where we know that we're missing something. As many of you know, in language models there are explicit biases that the models have that also reflect human biases to a large extent. For instance, many of you might know that chatbots tend to like long answers, and also tend to like giving responses that have

**[1:00:17]** bullets. Apparently these are the two strongest signals in terms of both human preference and language model biases. So if you want to get a good reward score, you want to get a human to say you gave a good answer: make the answer long and give lots of bullets, whether or not you actually answer the question. People just— you look smarter, right? And so you say a lot, as I'm doing now. There are also lots of settings where human preferences are unreliable. We'll talk a bit about reward hacking; I'll give a quick example in a little bit. Some of these can have reward impacts. Some of you know a bunch of the news stories that came out when there were mistakes. Many of

**[1:01:03]** these I guess are defined as things like hallucination, errors in a model for factual queries. That can sometimes be attributed to something that we're missing, potentially in how we construct and train models. Okay. There's work, or gaps, tied to potential ethical issues. In many settings, there's a bunch of the work that will often require experts, so things like supervised fine-tuning data, but often the pairwise preference data is outsourced and sometimes can be

**[1:01:48]** outsourced to settings where it's low cost to get data from individuals. The ethics here are tricky. I don't want to say this as a simple cut-and-dried thing, but I'd like for us to be thinking about engaging with some of these questions. Okay. On one hand, sometimes there can actually be a good job in certain places. In many settings, though, these are often the places where one might outsource labor for things like moderation but also often for training models, and there can be issues in settings where the individuals that try to

**[1:02:35]** improve these models get to see the worst of the signals that the models can create. So signals or, say, images, for instance, that are deeply unethical in various ways or even potentially traumatic, where you might need psychological help after doing some of this work. So it's a challenging open question, one that our field engages with a bit, but one that, again, I'd like us to [Ed: unclear — "part in scope"] for what we're thinking about, and think about these kinds of issues in this class. Okay. Here's a paper I like. No need to read the details; you can look up the reference later.

**[1:03:21]** There's some small chance the author is here. Not sure. No. Okay. It's a Stanford paper. They did this clever thing, I thought clever, where they gave the Pew survey. Some of you might know this is a survey that Pew uses to evaluate values and preferences across typically different societies, the US, different subgroups. So they gave the Pew survey to a language model, and they asked it a bunch of different questions that can give responses, and they tried to check the extent to which any of these responses correlated with different demographic groups. So do the responses look more

**[1:04:08]** like, you know, someone just looking through, on the right-hand side, conservative with less than high school education who makes less than $30,000, as an example. You can do this; this is a perhaps straightforward survey to do. Does anyone know what they found as the highest-correlation group to the survey? What opinions did their analysis suggest that the models captured the best? And it's not a trick question. It's the obvious one. Guesses?

*Student:* [Ed: unclear — "re label the pref data"]

*Koyejo:* Yeah. Some of the pref data, not

**[1:04:53]** completely, though, which is a little bit surprising, but I want to state this as a location. So where in the world do you think the guess is?

*Student:* The US?

*Koyejo:* Okay. So US. More fine-grained than this?

*Student:* California.

*Koyejo:* Yeah. So very California, very US, very around here, actually. It turns out language models like to be Californian, Stanford, Palo Alto kind of people. Perhaps not surprising in retrospect, because, again, perhaps part of the labeling is done all over the world, but, to the earlier point, there's a lot of intervention in the models that ties to people who generally work here, who have political opinions and preferences that match, you know,

**[1:05:41]** people that live around here. And so these kinds of preferences get embedded in language models. So again, part of our goal will be to understand the mechanism by which this happens and the process, either intentionally or unintentionally, but I think also in scope is critiquing and evaluating what ends up being embedded in language models, and as you might imagine this can have downstream impacts of various kinds. Okay, so we talk a lot about language. It's hard to avoid, but there's lots of other stuff that you can do with preference models, and we'll talk through some examples. There's work, for instance, this is I think quite cool work from some colleagues out of Caltech, where

**[1:06:26]** they're building an exoskeleton. For people who cannot walk, who have lost control of part of their limbs, their legs, they have an exoskeleton that helps them walk, and part of the calibration process requires getting signals on what either feels better or worse, or some signal from the human about how well it's working, in order to actually calibrate the exoskeleton. So you can imagine setting up the model some way, asking the user, "Is the setting good for you?", and the setting here involves a bunch of these probes at

**[1:07:11]** the back which have different settings across this array. And all this you have to tune. There's some response tuning curve that you have to fit that is somewhat personalized; each person has some tuning curve that's specialized to them. So you have to answer this question of how do I calibrate the model to the individual. And here the signal that seems most reliable is what the person tells you in terms of how well it works for them. So you could try an absolute value query: is this four out of five in terms of how good this is? Is the problem clear, by the way? Okay. So that's the real-world context, and then a bit of the algorithmics. They found, and we'll argue a bit in many of the applications we look at, that preference queries worked a lot

**[1:07:58]** better. So instead of saying "how good is this on an absolute scale," you ask people to compare two settings of the model, and then you have your algorithmics behind the scenes that can use this pairwise preference as a way to tune this array such that you get hopefully the best behavior in terms of the exoskeleton walking. We'll talk a bit about this. We already talked a bit about preference feedback. We'll talk about dueling bandits, which are a way to think about bandit problems with pairwise preferences explicitly, as a way to frame problems like this in a bunch of different papers where this group is engaged. Okay. Other algorithms: I talked a bit at the beginning about some of my work in

**[1:08:43]** metric elicitation. The idea here is, for various kinds of learning problems, say classification problems, you want to get a signal. There are lots of classification problems where the metric of success is unclear, or there are asymmetric trade-offs, potentially. So there is maybe a differential cost for making different kinds of errors. This shows up a lot in, say, medical application settings, where false positives and false negatives don't cost the same in terms of impact on the individual, and here calibrating your learning problem to actually figure out the right trade-offs can be tricky. And so we've done some work over a few years now thinking about ways of getting pairwise preferences from humans as a way to tune the

**[1:09:31]** preference of the learning model to best align with expert feedback on various kinds of, typically, classification problems, things like this. But we did work on things like fairness problems, learning from stakeholder groups, empirical evaluation. We've done some work looking at how this looks in real-world contexts of various kinds. Okay. So elicitation is interesting. Again, I've mentioned this before, but where individual stakeholders matter, or where the trade-offs are tricky and hard to specify, we found that valuable. Some recent work, recentish, thinking about inverse decision theory. This is this question, it's a similar

**[1:10:16]** kind of question but in a classification setting. Decision theory is this forward process: I have some probabilistic model of the world, I want to come to a decision. The inverse is I want to figure out, again, how to think of trade-offs, and trade-offs in classification problems almost always boil down to thresholds. What do I set my threshold for, if I have a probabilistic model of some behavior? What do I set my threshold for yes/no, if I'm going to make a binary decision, for instance? And so you can think about this as some feedback process. We've done a bit of work; I'll leave you to read details if you're interested, in ways to frame this problem and what comes out of it. Recommendation systems, like you brought up. So, another meaningful high

**[1:11:04]** impact application, in the sense that a lot of our world now is driven by recommendation systems. All the way from things like movies and audio, Spotify, Netflix, there's a bunch of work in this space. At some point this was the coolest part of the AI field. I'm dating myself a bit, but when the Netflix Prize was a thing, Netflix set out a million dollars for whoever could improve their recommendation system algorithms. I tried. We didn't win. We weren't even close, but we gave it a shot. Like many others, everyone did fairly heavy, complicated algorithms that tried to be good at mean square error.

**[1:11:49]** There's a bunch of work building on this, and other parts of the field have tried to make this problem much better specified. But again, a lot of this often boils down to: you're trying to model and capture human preferences over items, movies, objects, things that people might want to buy. There's a bunch of literature, both technical and otherwise, that has come out of this. So various kinds of querying, various kinds of evaluation signals, so things like thumbs up, thumbs down, which is a pairwise thing about an individual item; getting pairwise preferences, ranking preferences, rating preferences. There's a whole literature there that we'll touch on, and we'll again think about how it might apply to other things that we're interested in. We've already

**[1:12:36]** talked about RLHF, so I won't belabor this, but there's additional detail if you're interested. It shows up in reinforcement learning. I, yeah, show the video. So this is work in 2008, which is the first time that people used RL algorithms from human demonstrations to, I guess, automatically learn some policy for actually flying a helicopter. So again, this was way ahead of its time. There's some work from my colleague Dorsa and some of her PhD students doing all sorts of cool things in preference learning for

**[1:13:21]** reinforcement learning applications. So I'd argue RL has engaged with this problem for a long time and has lots of artifacts, but we also try to learn quite a bit from RL settings. They've also done work, it's the same group, looking at ways to learn from demonstrations. I won't play the video for time, but you can take a look, and I've also asked questions about how to model things like comparison data. I'll maybe show this. Some of you might have seen this video. This is now famous as an example of trying to learn or specify a reward function for a game-playing agent. The model is meant to, you know, the boat is supposed to

**[1:14:07]** complete a course. As you can see, it's not completing the course. It turns out it's still getting a good score. Most of you might have already seen this. What the agent learned is there's a very specific set of behavior that you might repeat. It turns out that if you hit those green things at the bottom, you get a bunch of rewards. They respawn at exactly the right timing to hit a bunch of these boats, hit the side, and come back and get the reward over again. So your reward function was "maximize score." The agent figured out "I can get a really high score playing this." Sometimes this is called reward hacking. We'll talk a bit about this and how it shows up, and ways of, okay, ways of engaging with

**[1:14:55]** language models. Okay. So a bunch of factors we think about: how hard is it for the human to specify signals? How do we think about correctness? What happens if there is no correct answer? How do we think about things like truthfulness and strategic behavior? Various kinds of roles of mistakes, expertise, questions like this. In most of the work we'll assume some kind of rational human. We'll engage with this a ton over the course of the lecture, but we'll assume that there exists some kind of reward function, even if we're not being explicit about it, but there exists some sort of explicit deterministic function that tells us what a human would prefer, and we'll

**[1:15:40]** build a lot of our models based on this. But it is an assumption, and at least one invited talk will engage with whether this assumption is reasonable or not and what to do about it. We'll mostly talk about discrete choice kinds of things and parametric models that build around that, a bit about biases, aggregation, a whole bunch of the topics that I talked about. Okay, so that's that about material, a bit of general overview. We're going for breadth over depth for various reasons: again, new space, we're trying to figure out what the edges are that make sense for the class. We'll try to engage with a bunch of different applications. We have a lecture schedule, which you've seen online. Though there

**[1:16:26]** might be some shuffling in terms of topics and speakers, as already mentioned. We assume you have machine learning basics, you can do some basic programming. If you cannot, we should chat, because I think there'll be some challenges in engaging with the course. There's a textbook, and there's this link; the slides will be available, so you can take a look. Next we'll start on material on some existing choice models for the rest of the lecture. All right. Thank you. Welcome to CS 329H.
