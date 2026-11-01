# Lecture 4 — Mechanism Design (auctions, incentive compatibility, and pricing with preferences)

This lecture introduces **mechanism design**, "the science of rule making": how to set the rules of
an interaction so that it still reaches a desirable outcome even when the participants are
strategic (≈0:52, ≈1:39). Sanmi Koyejo presents it as a combination of social choice, which the
course has met in its voting lectures, and game theory, applied to actors "that may be adversarial
or may be malicious" (≈0:05, ≈0:52). For this course, the payoff is that mechanisms can **elicit
preferences truthfully**: when preferences are grounded as the prices people would pay, a mechanism
that makes bidding your true value the best strategy is also a way to learn that value (≈29:29,
≈1:19:55). Most of the lecture works through auctions. It covers posted prices, simple auctions and
the second-price (Vickrey) auction; the two core properties, **incentive compatibility** and
**individual rationality**; Myerson's revenue-maximizing auction; and how learning enters
mechanisms (≈13:58–59:40). The last twenty minutes present work from Koyejo's group. It prices
**digital goods** such as prompt completions with an auction driven by pairwise feedback, and turns
the same mechanism into a **reverse auction** that pays data labellers according to the harm a
labelling task may do them (≈1:00:29–1:19:55).

**Date.** This is catalog position 4. It corresponds to the **Oct 28** schedule row, "Lecture:
Aggregated Preference Optimization via Mechanism Design". The recording does not state its date,
but the content places it. Koyejo closes by saying "next lecture we have an invited lecture by
Joseph Jay Williams" (≈1:20:40), which is the Oct 30 row. He says regret was covered in work "that
we did last lecture" (≈55:48; the name of that work is garbled) and refers to "the way we've talked
about regret over the past couple of lectures" (≈57:19). That matches the Oct 21 and Oct 23 rows on
dueling bandits and Bayesian optimization. The opening links today's material to "bandits,
preference modeling, preference optimization" (≈0:52), and he mentions an in-class pairwise exercise
in the last lecture (≈1:10:40, ≈1:11:25). [Lecture 3](03-model-based-preference-optimization.md)
(Oct 16) had called mechanism design "quite a bit later". The Oct 21 and Oct 23 sessions are not in
the catalog.

The lecture also refers back to "the voting lectures" and to incentive compatibility as something
"we covered in social choice briefly" (≈0:05, ≈28:42). So a social-choice lecture came before this
one. The schedule's candidate is Oct 7, "Aggregated Preference Models via Social Choice Theory &
Game Theory". The catalog's lecture 7, titled *Voting*, turned out to be the Dec 2 guest lecture
by Colin Megill on Polis ([lecture 7](07-voting.md)), so the voting lectures are not in the catalog.
See [preference aggregation](preference-aggregation.md) for what the remaining lectures say about
social choice.

**No slides.** The lecture is given from slides, which the course has not published, so every claim
here is cited to the transcript by timestamp. The slides carry references that are not read out:
history references (≈4:43), a colleague's talk that the revenue figures are borrowed from (≈5:30),
and the papers behind the closing applications. This page does not name them. The two sources
Koyejo names for further study are a tutorial and a course; both names are garbled in the captions
(see [Further reading](#further-reading)). He writes no formulas aloud. The few expressions below
are rebuilt from his spoken descriptions, and the page says where it chooses its own symbols.

**What is not covered.** Lecture 3 deferred a paper linking metric elicitation to mechanism design
to "when we talk about mechanism design" (lecture 3, ≈1:20:34). This recording does not take it up.
The planned Q&A at the end is dropped for time (≈1:19:55).

[Edited transcript](../raw/transcripts/04-mechanism-design.md) ·
[verbatim captions](../raw/transcripts/original/04-mechanism-design.md) ·
[video](https://www.youtube.com/watch?v=zkHTbb-0Gns) ·
[course website](https://web.stanford.edu/class/cs329h/fall2024/) · [sources](../sources.md) ·
topic page: [mechanism design](mechanism-design.md)

## What mechanism design is

A mechanism is a set of rules for an interaction, such as an auction or a pricing scheme.
Mechanism design asks how to choose those rules so that, even if participants choose to be
strategic, "the overall ecosystem still works correctly to lead to some desirable outcome" (≈1:39).
Strategic here means anything participants might do in their own interest: being adversarial, or
pursuing their own preferences in "whatever way that they choose to engage" (≈1:39). As in social
choice, part of the designer's job is to decide what the desirable outcome is. The rest is to work
out "the rules of the game, if you like, or the rules of the interaction", so that the outcome is
reached anyway (≈1:39, ≈2:25).

The field was traditionally studied in economics and borrows from game theory. Koyejo dates its
growth in computing to "roughly ... when large internet companies became a thing", when it turned
out to be extremely useful for real-world computing tasks (≈2:25, ≈3:12). The computing literature
added questions such as computational complexity, which also came up with social choice, and what
happens when "a machine learning model is part of the mechanism" (≈3:12).

## Where it has had impact

Auctions and pricing are "one of the clearest successes" of the field, and the lecture spends most
of its time on them (≈3:12, ≈3:58). Koyejo's examples:

- **Spectrum auctions.** When regulation changed and some of the radio spectrum was put up for
  bidding, mechanism design was used to set up the bidding process. The bidders "clearly" were
  self-interested and wanted to maximize profit, and the process had to be set up so that good
  outcomes were likely anyway (≈3:58, ≈4:43). The captions are garbled at the join between these
  two paragraphs.
- **Web pricing.** Auctions and pricing are "used a ton" by web companies, for example by Amazon in
  deciding the pricing and ordering of items (≈4:43).
- **Search advertising.** Google uses these ideas to power "the ad buying process behind search"
  (≈5:30). In figures he borrows from a colleague's talk, Google's 2016 ad revenue was \$79 billion
  out of total revenue of 89.6, "definitely the vast majority" (≈5:30). For Facebook the figure is
  not read out, but "everything else is a rounding error compared to what was tied to ad revenue"
  (≈5:30, ≈6:17). What powers these ad processes are auction ideas from mechanism design, "many of
  them directly borrowing, some of them with small adjustments" (≈6:17).

The point is that the field has had "a huge impact on society generally", because its tools are now
used for pricing, auctions and many kinds of collective decision-making (≈6:17).

## The question for this course: inferring economic preferences

The question that leads to these tools is whether we can infer people's **economic preferences**:
"what actual value or price do different stakeholders, in this case buyers, have for certain items"
(≈7:03; the words before "economic preferences" are garbled). A mechanism in this setting decides
**which buyers receive what items** and **how much they pay** for each (≈7:03). The goal is to do
this so that a societally desirable outcome results. Often that means the amount paid is
commensurate with the value, and "whoever values the item the most actually gets to win a bid for
that item if they bid their true value" (≈7:03, ≈7:50).

**The coffee shop.** The running example has three possible items: a coffee, a cupcake, or a coffee
and a cupcake together. Two buyers each have a price they think each one is worth, meaning how much
they would be willing to pay (≈7:50). The mechanism's task is to design the interaction so that,
for instance, the buyer who values the cupcake most wins it (≈8:38). The buyers have an incentive to
be strategic. "They want the item, but they also want to pay as little as they can", so there is a
tension between gaming the system and their intrinsic value for the items (≈8:38).

This is how the lecture ties to preferences. "If you think of preferences as being economic, or as
able to be economically priced or judged or valued, then preferences are now grounded here as
prices people are willing to pay" (≈11:40). Koyejo calls this incomplete for the course as a whole,
which has covered many preferences that are not obviously quantifiable in money. But where things
can be grounded economically, the approach "can be very useful" (≈11:40, ≈12:25). He stresses that
mechanism design is an entire field with whole classes of its own, and that the lecture only
touches the surface (≈12:25).

### Who decides what a good outcome is

A student takes the cupcake numbers: one buyer will pay \$3 and the other \$2. If the price is set
to extract the \$3, isn't that exploiting the buyer, and is it a good outcome in a social setting
(≈8:38, ≈9:24; part of the question is garbled)? Koyejo's answer is that "it's up to the designer
to decide what a socially valuable outcome is" (≈9:24). Many framings use maximal revenue as the
desirable outcome, and most of the lecture follows them. It is about strategic behaviour and how to
"avoid being fooled by strategic behavior", framed around maximizing revenue as the societal good
(≈9:24, ≈10:10). There are other notions, such as **welfare**, which he describes as "not that
different, some difference of cost and revenue" (≈10:55). A designer could pick a different social
outcome and design a mechanism for it (≈10:55). He notes, without going into them, that there are
philosophical arguments for why people consider "capitalist-style revenue maximization" a good way
to design markets (≈10:55, ≈11:40).

## Three ways to sell

Koyejo asks the class how they would sell the items, taking revenue as the goal for now (≈13:58).

### Posted prices

The obvious mechanism, used in most places that are not auctions, is to post a price and let people
decide whether to buy based on their value (≈13:58). His example prices are "150 for the coffee and
350 for the cupcake", priced individually, so the combination costs the sum (≈14:45). He adds them
to five, so they read as \$1.50 and \$3.50. The buyer values the coffee and cupcake together at 6,
so they buy, and their **utility** is their value minus the price, $6 - 5 = 1$ (≈14:45, ≈15:32).

A student asks whether prices are additive. In this framework, values for sets of items need not
be additive: the setup "allows for prices across sets of items that are not additive", which seems
to match real behaviour, where people value sets of things differently from the individual things
(≈15:32). Koyejo's illustration is choosing a class. You might weigh the instructor you would work
with on a project, whether your friends are taking it, and a promise of "10 GPUs per student". Some
decision makers care about one thing only, but for many "really the combination matters", and the
trade-offs "may not be additive" (≈16:18, ≈17:05).

What does a sale at a posted price tell you? If someone buys, "their value must be higher than your
stated price", since under this model they buy only if their utility is positive. "You don't learn
that much about individual preferences, but you learn at least some directional signal" (≈17:51).
See [revealed versus stated preferences](preference-queries.md#revealed-versus-stated-preferences).

### An auction where the highest bid wins

Next, an auction: everyone bids, and the winning bid gets the item (≈17:51, ≈18:36). You might hope
this gives more signal about people's actual values, since bids should be correlated with them.
"They might not, and in fact a lot of the literature ... is about what might individual buyers do in
this setting and how might they try to game this system" (≈18:36).

Asked how they would game it, a student answers: "you only bid the minimum amount you have to"
(≈19:21). Koyejo fills it out. If you can bid last, you see what everyone else will bid; if your
value is higher than the current maximum, "you just go a little bit above" and win (≈19:21, ≈20:08).
That is reasonable for the strategic individual, but bad for the other goals. It is a bad outcome if
social welfare is taken as maximum revenue. It is not ideal for learning people's true values
either, because people are now "incentivized to bid to win, and winning is just different than
actually bidding what they value the item at" (≈20:08).

### The second-price auction

In a **second-price auction**, everyone bids and the highest bidder wins, but "the amount you pay is
not the highest bid. You pay the second highest bid" (≈20:54). This "partially mitigates" the
strategy just described (≈20:54). For the discussion, Koyejo assumes no two bids are equal, so there
are no ties (≈21:39).

Students probe it. One points out that they could "just bid like a million dollars". Koyejo agrees
that you can always win this way, as long as you are willing to pay the second price (≈21:39,
≈22:26). Another gives the counter: "someone could get annoyed that you did that and then bid
\$999,000". "Again, everyone's strategic." Now the second-highest bid is far above your value
(≈22:26).

**Reserve prices.** The seller's view of an item's value may not match the buyers'. One fix, which
also guards against buyers colluding to bid too low, is a **reserve price**, a minimum selling price
(≈23:11, ≈23:58). The highest bidder wins only if their bid is above the reserve, and pays the
larger of the reserve and the second-highest bid:

$$\text{price paid} = \max(\text{reserve price}, \text{second-highest bid})$$

This mitigates both the value mismatch and some of the adversarial bidding, since the seller is
guaranteed at least the reserve (≈23:58, ≈24:45). Asked whether the reserve is hidden, Koyejo says
either design is possible; in this setting it is "known and public" (≈24:45).

The second-price auction "is sometimes also called the **Vickrey auction**". That work, done in '61,
"eventually led to a Nobel Prize". Koyejo notes that many economics Nobel Prizes have gone to work on
mechanism design (≈25:34). The computing literature followed with questions of computability,
learnability when a learning algorithm sits in the middle, and strategic behaviour of agents in
different settings (≈25:34).

## The formal setup

There are $m$ items and $n$ buyers. Each buyer has a value for every possible **bundle** of items
(≈26:23). The list of a buyer's values across all bundles, "a vector enumerating the value for every
possible bundle", is called their **type** (≈26:23, ≈27:09; the first time the term is spoken it is
garbled). In the coffee example, the value for nothing is zero and there is a number for every
combination (≈27:09).

A sales mechanism is defined by two functions (≈27:09):

- an **allocation**, which decides which buyers get which items; and
- **payments**, which define how much each buyer pays.

The **revenue** is "the sum of payments across all the buyers that participated", which is one
possible target to maximize (≈27:56). Buyers can usually bid whatever they like, and because they
are often incentivized to be strategic, they "may bid something that's not their true value"
(≈27:56). The rest of the lecture is about designing mechanisms that make true bids more likely
(≈27:56, ≈28:42).

## Two properties a mechanism should have

Koyejo names the core properties one usually wants (≈28:42, ≈29:29):

- **Incentive compatibility (IC).** The mechanism incentivizes agents to bid their true value, "so
  they're likely to bid truthfully". It can be read in the revenue-maximizing sense, "or you can also
  think about this in terms of eliciting preferences": the true value is the target of an
  elicitation mechanism (≈28:42, ≈29:29).
- **Individual rationality (IR).** Mostly from the buyer's point of view: buyers should have
  "nothing to lose by participating in the mechanism versus not". This "reduces the barrier to
  entry" for choosing to take part (≈29:29, ≈30:14).

Incentive compatibility is "another canonical idea", with "yet another Nobel Prize, in 2007". It
was "originally introduced by" someone whose name the captions give as "Heritz", in '72 (≈30:14). It
was formalized mainly in economics and later taken up widely, increasingly in computer science
(≈30:14). See [mechanism design](mechanism-design.md) for the properties gathered in one place.

## Why the second-price auction is incentive compatible

**The claim** (stated informally, with formal proofs left to the references): in a second-price
auction "every bidder will maximize their utility by bidding truthfully". Bidders "cannot do better
by ... trying to be strategic" and bidding something other than their true value (≈31:00, ≈31:47).

**Utility.** A bidder's utility is the value they place on the item they win, minus their payment,
"times an indicator selecting for whether or not they won" (≈31:47). In symbols this page chooses
(not the slide's), with $v_i$ bidder $i$'s value and $p_i$ their payment,

$$u_i = (v_i - p_i) \cdot \mathbb{1}[i \text{ wins}]$$

So a winner's utility is positive if they pay less than their value, zero if they lose (or pay
exactly their value), and negative if they overpay (≈35:45).

**Bidding above your value** (≈32:34–34:57). The tempting idea is to bid high, since you pay the
second price, not your bid.

- If you would have won anyway, because you had the highest value, you still win, and the price does
  not change. You gain nothing (≈32:34, ≈33:20).
- If you would have lost, because someone else values the item more, bidding high might make you
  win. But then the second price is likely above your value, so you pay more than the item is worth
  to you, and your utility goes from positive to negative (≈33:20, ≈34:08).

**Bidding below your value** (≈34:57–36:30).

- If you would have won, a low bid may fall below someone else's truthful bid. You lose the item and
  get zero utility (≈34:57).
- If you would have lost anyway, you still lose, and the utility is zero (≈35:45, ≈36:30).

Either way, bidders "don't do any better in the mechanism by strategically choosing to bid lower
... or higher" (≈36:30). Koyejo credits this property with much of the second-price auction's
success (≈36:30). For "a rational buying agent their best action is to bid your true value for the item"
(≈37:15, ≈38:02). He adds that lots of search mechanisms use second price even though they are not
well matched to it. The second-price result is about a single item, while in search "you're bidding
over a bundle of items" (≈37:15).

**Is it best for the seller too?** A student asks. "Not necessarily": second price satisfies
incentive compatibility, "but it's not the revenue maximizer mechanism" (≈38:02, ≈38:48). That
question returns with Myerson's auction, below.

**Individual rationality.** The second-price auction is also individually rational: "each bidder
is no worse off participating than not when they choose to bid their true value" (≈38:48). If you
bid your true value, you either win and pay the second price, which is below your value, so your
utility is positive; or you lose to someone who values the item more, and pay nothing (≈39:34). So
"they lose nothing by choosing to engage as long as they choose to use the true value" (≈40:21).

## Incentive compatibility at three levels of information

Analyses usually go further by treating buyers' values as samples from a **probability
distribution** over bundles (≈40:21; the word before "values" is garbled). Koyejo lists three
standard definitions as definitions rather than in detail. The thing to take away is that they
differ in how much information each bidder has about the rest of the mechanism (≈41:09):

- **Ex ante IC.** Purely distributional. There is a distribution over all bidders' values, and the
  designer wants "truthfulness in expectation over values, given knowledge of the distribution"
  (≈41:09).
- **Ex interim IC.** Slightly stronger. "Bidders know their value and distributions over others'
  values", and truthfulness should still be the dominant strategy, "the best thing to do" (≈41:54).
- **Ex post IC.** The strongest. A bidder knows "actual values of everybody", not distributions,
  and should still be incentivized to be truthful (≈41:54, ≈42:40). He first says "actual bids" and
  corrects himself to "actual values".

Individual rationality can be analysed in the same way, "at different levels of bidder information"
(≈46:33, ≈47:18).

## Mechanisms in use that are not incentive compatible

Many mechanisms in the world are known not to be incentive compatible, or are complex enough that
the full analysis has not been done (≈42:40). Without IC, "a strategic actor may do better by
picking a bid that's not their true value", and the designer loses the guarantee that participants
bid truthfully (≈43:26). Examples:

- **First-price auctions**, "often what display ads use": the winner pays what they bid (≈42:40,
  ≈43:26).
- **Generalized second-price auctions**, used in sponsored search such as Google's (≈44:12). The
  second-price claim is for multiple bidders and a single item. In search ads you are bidding over a
  ranking of multiple placements (≈44:12; part of the sentence is garbled). People have shown
  strategies that game these auctions; in his words, "it's known not to be incentive
  compatible, I think, and yet it's still probably the most popular deployed algorithm" (≈44:12,
  ≈44:59). Koyejo calls this "an interesting cognitive dissonance". A setting with strong guarantees
  inspired the idea, it was transferred to a new setting where the guarantee is lost, and it is used
  anyway (≈44:59).
- **More complex combinatorial auctions**, which are either known not to be IC or not yet fully
  analysed (≈44:59).

The issues that break incentive compatibility in practice include (≈44:59, ≈45:46):

- figuring out the values might be computationally expensive;
- the rules, and how easy they are to explain;
- leakage between the bidding process and the auction mechanism, for instance when bids feed into
  parameters that shape future bidding (partly garbled);
- agents that are not risk neutral, which invalidates the assumptions the analysis makes about them.

There is also work on **approximate** incentive compatibility, which measures how far a mechanism
departs from it (≈46:33).

## Myerson's revenue-maximizing auction

The student's question about revenue has an answer for single items. It is "due to Myerson", in
'81, with "another Nobel, I think a third Nobel Prize" (≈47:18). Myerson showed "the
revenue-maximizing single item auction, which is a somewhat more complicated second price" (≈47:18).

**The trade-off it resolves.** In a second-price auction, "a stronger bidder always pays the weaker
bidder's bid", so the seller's revenue depends heavily on the other participants' values (≈48:03).
The seller would like to be paid the top bidder's true value. But charging the top bid loses
incentive compatibility, because buyers can then be strategic and "actually bid something else and
end up paying less" (≈48:03, ≈48:52). So paying the highest price loses strategic usefulness, while
second price is strategically correct but "leaves revenue on the table" (≈48:52).

**The mechanism** (≈48:52–51:58). Assume bidder $i$'s value has a distribution with a pdf he calls
$f$, supported on $[0, 1]$; the values are normalized to lie between zero and one (≈48:52,
≈49:39).

1. For each bidder, compute a **virtual value**. It is a function of the bid and of that bidder's
   value distribution. Koyejo describes it as "value minus some normalized notion of the
   distribution of values for that individual bidder", a "CDF correction" (≈49:39, ≈50:27). The
   formula is on the slide and is not read out.
2. Solicit bids from all the buyers. If every virtual value is below zero, the item is not allocated
   and the mechanism ends (≈50:27).
3. Otherwise, allocate the item to the buyer with the **highest virtual value** (≈51:12).
4. The winner pays a thresholded bid. Take the maximum of everyone else's virtual bids, which must
   be above zero, and map it back to a value with the inverse of the virtual-value function
   (≈51:12, ≈51:58).

"So it's effectively the second price for the virtual bids", transformed back to values (≈51:12,
≈51:58). Myerson showed that this keeps incentive compatibility, so bidding your true value is
still optimal, and that it is revenue-maximizing: it gets the seller the most revenue possible while
all bidders are still incentivized to bid truthfully (≈51:58, ≈52:45).

**The i.i.d. case.** When buyers' values are i.i.d., with the same distribution, the mechanism
becomes a standard second-price auction with a reserve price (≈52:45; the captions garble the
reserve). The reason is that the virtual values are then "offsets of each other", and the price
paid looks like the inverse function applied to a maximum with zero (≈52:45).

There is also work on multiple units of the same item (≈52:45, ≈53:31). But beyond one item, "we
don't know how to do even two items optimally", as far as Koyejo knows, in the sense of a
revenue-maximizing, incentive-compatible auction (≈53:31). He calls this surprising and suggests it
as "a really hard problem to solve" for anyone theoretically inclined (≈53:31, ≈54:17).

## Learning inside mechanisms

Modern ad-bidding systems have learned models "under the hood" that predict prices or placement, so
a body of work connects learning methods with mechanisms (≈54:17, ≈55:03). Examples Koyejo lists:

- **Online learning for revenue.** A buyer, or a population of buyers, arrives repeatedly, say over a
  week, and decides whether to buy at the current price. This can be the fixed-price setting from
  the start of the lecture or a richer mechanism (≈55:03). The measure is **regret**: "the difference
  between the cumulative revenue for the seller versus the best price that they could have gotten
  in hindsight" (≈55:48). It has been studied with adversarial buyer values, stochastic buyer
  values, truthful buyers, and various kinds of strategic buyers (≈55:48, ≈56:33).
- **Learning to bid.** Here the buyer is the learner, updating how they bid from what the mechanism
  and other participants reveal over time. In a simple version the buyer starts knowing nothing,
  learns an item's value only when they win it, and tries to compete with "the best fixed bids in
  hindsight", again measured as regret (≈56:33, ≈57:19).
- **Arrival-order problems.** In what the captions render as "profit inequality" problems, the
  **prophet inequality**, buyers arrive in adversarial order with random valuations. In **secretary
  problems** (captioned "sector problems"), buyers arrive in random order but valuations are
  adversarial, "some notion of worst case" (≈57:19, ≈58:08). The two settings differ in which of the
  two things, order or valuations, is adversarial (≈58:08).
- **Learning from revealed preferences with pricing.** You observe individual buyers' actions over
  iterations, predict their future behaviour, and design pricing around it (≈58:53).

Many of the questions are learning-theoretic. How many training examples do you need, a standard
sample complexity question? How do you learn a preference function that captures buying behaviour,
and how does that tie to the mechanism's choices (≈58:53, ≈59:40)? Koyejo's reason for presenting
the area is that it holds "lots of lessons for the task of preference elicitation and preference
optimization in AI" that are underused (≈59:40; partly garbled).

## Pricing digital goods with pairwise feedback

The first application combines "a bit of" something the captions garble as "illustration", online
learning and bandits, and mechanism design in one preference setting (≈59:40, ≈1:00:29). Its subject is
**digital goods**: prompt completions, synthesized images, and also things like ad placements
(≈1:00:29). The work is presented as Koyejo's group's ("when we did this", ≈1:05:54), and the paper is
not named in the audio.

**Why digital goods are different.** In a standard auction, bidders know the item ahead of time,
something about the market, and often the mechanism itself (≈1:01:16). With a digital good, "you
don't know how good the response is going to be" until the work is done (≈1:01:16). Imagine a
generative-model company that wants to price prompt completions. That is not how it works now, which
is "all fixed price, no options" (≈1:02:03). But economic incentives could lead to variable
pricing, and an auction is a reasonable way to do it. The problem is that nobody knows how good the
completion is before seeing it (≈1:02:03). The seller cannot know the value until the completion
exists, and the buyer cannot decide whether a completion is worth a price before seeing it, so
"someone has to make the decision first, and it's unclear how to engage in this setting" (≈1:02:50,
≈1:03:36). Unlike standard pricing, "the item is actually not a real thing until the process is
complete" (≈1:04:22).

A student names this **information asymmetry** between the two parties and gives an example. A
painting sold at auction destroyed itself, through a built-in paper shredder, as soon as the sale
completed (≈1:04:22, ≈1:05:09; the auction house and artist are garbled in the captions). Koyejo:
"the art included destroying the art". To an artist this may look reasonable; to a buyer it may seem
adversarial (≈1:05:09, ≈1:05:54). Another student offers a modern case: a model that "thinks for
like 2 minutes, and then it spits out zero tokens". Koyejo calls it "a great, actually very modern,
one that was not available when we did this" (≈1:05:54).

**The setting.** Bidders submit offers to fulfil requests before seeing the responses, and a
resource behind the scenes, such as computation, has to be allocated among, say, a billion requests
(≈1:05:54, ≈1:06:41). The goal is fair pricing, where users lack the complete information they would
have in a standard auction. The mechanism should help users form their valuation, and it should
still be incentive compatible, so that bidding one's true value for the completion is optimal "which
ahead of time they don't know" (≈1:06:41, ≈1:07:29). Formally there is a set of users, with user $i$
at time $t$ making a request $x$. The mechanism chooses whether to fulfil it. Each agent has a true
utility $\mu_{it}$ for the allocation and reports a utility $r_{it}$. The aim is an auction that is
utility-maximizing and incentive compatible, given only the requests and the reported utilities
(≈1:07:29, ≈1:08:15, ≈1:09:05).

Compared with existing work, the gaps are that agents do not know their values for outcomes ahead
of time, that uncertainty plays a big role "particularly in these kinds of stochastic generative
model settings", and that values may change over time with context, so the mechanism must be dynamic
(≈1:09:05, ≈1:09:54).

**The mechanism** is built on pairwise and other partial preferences (≈1:09:54):

1. **Learn to predict value.** An initial stage learns a function that predicts, from the request
   $x$, the value of a response. The training signal is pairwise preferences ("would you like this
   or this as a completion to your prompt") or thumbs up and thumbs down on a price ("if I synthesize
   this, would you pay \$2"). These are "low-signal responses to various kinds of simple
   pairwise-type queries" (≈1:10:40, ≈1:11:25). Koyejo recalls the last lecture's in-class pairwise
   exercise, where people "argued strongly" for different answers, as a reminder that individual
   variance is high (≈1:10:40, ≈1:11:25).
2. **Run a second-price auction on predictions.** Because prices are not known ahead of time, the
   mechanism uses predicted values. A user submits $x$, the mechanism predicts each bidder's value for
   the completion, "the highest predicted offer wins the auction, and then they pay the second
   highest predicted offer" (≈1:11:25, ≈1:12:57).

The claim is that once the predictor has seen enough examples, it predicts values well enough that
second-price pricing on the predictions keeps the properties wanted, high revenue and incentive
compatibility (≈1:12:12). Koyejo offers it as a mechanism for direct pricing in
information-asymmetric settings such as digital-good auctions (≈1:13:44). See
[mechanism design](mechanism-design.md) and
[asking humans for preferences](preference-queries.md).

## Paying labellers by harm: a reverse auction

The second application turns the problem around: "instead of trying to price items for user
completions, we wanted to try for the opposite" (≈1:14:31). Modern generative AI systems need people
to label "potentially toxic or psychologically difficult material, both text and image completions"
(≈1:15:17). If individual harm can be connected to an economic value, people can be paid according
to how much harm a labelling task may cause them (≈1:15:17, ≈1:16:03). A sensitive item, or a person
more sensitive to that material, would command a much higher price than a less sensitive item or
person (≈1:16:03).

Koyejo hedges this repeatedly. It is "not a perfect solution", "not a normative claim that this is
necessarily a good idea", and "not as 'this is the solution for everything'". It is one possible
lever toward a labelling ecosystem that is "less psychologically damaging" (≈1:15:17, ≈1:16:03,
≈1:16:49). One argument for it is fairness: "your payment should be correlated with how much harm
you might be suffering from engaging in that task" (≈1:16:49).

If you simply asked people how much harm they expect, they would have an incentive to be strategic,
so a mechanism is needed here too (≈1:17:36). It is a **reverse auction**: the values are now
negative, and the aim is to minimize the harm people suffer (≈1:17:36, ≈1:18:23). The same machinery
applies. A predictor estimates each person's negative utility for a completion from pairwise
feedback, and then "we do the second price thing just like before" (≈1:18:23, ≈1:19:09).

**Results** (shown briefly; details in the paper, not named in the audio). The baselines are
observing values directly and regressing on them, and a uniform allocation that does not take
individual values into account (≈1:19:09, ≈1:19:55; the second baseline's wording is garbled).
Pairwise feedback "uses much less information". Its regret, the gap from the best possible
allocation to the predicted allocation, is "much lower than, say, a uniform allocation" (≈1:19:09,
≈1:19:55). Across the population it also gives a better distribution of another loss, whose name is
garbled in the captions (≈1:19:55). See
[whose preferences](whose-preferences.md#the-labour-of-labelling).

## Summary, and what comes next

Koyejo's closing summary (≈1:19:55, ≈1:20:40). Mechanism design is designing rules so that
strategic behaviour by participants still leads to a desirable outcome. This course's interest is in
how it engages with **truthfully eliciting** stakeholder preferences, or optimizing them. The main
evaluation measures are **incentive compatibility**, **individual rationality**, and revenue,
utility, or "some other notion of social welfare".

The next lecture is an invited talk by **Joseph Jay Williams**, on related ideas used "for AB testing
and other kinds of online learning, preference optimization settings" (≈1:20:40). The catalog places
it last, as lecture 8; it is not yet in this knowledge base.

## Further reading

Koyejo names two sources, both garbled in the captions.

- Much of the lecture is borrowed from "a great tutorial by" someone the captions call "Ellen", and
  collaborators. He strongly recommends it (≈1:20:40, ≈1:21:27).
- "Tim", whose surname the captions give as "Ruffgarden", now at Columbia, "teaches an excellent
  course". This lecture is "roughly lecture one or two of what he covers" (≈1:21:27).

No course document gives either name, so they stay as captioned. The course's
[reading list](../sources.md#course-website) is organized by theme, not by lecture.

## Student questions in this lecture

| ≈ | Question | Short answer |
| --- | --- | --- |
| 8:38 | (partly garbled) Charging the buyer who will pay \$3 rather than \$2 exploits them; is that a good social outcome? | The designer decides what is socially valuable; most framings use revenue, and welfare is an alternative |
| 15:32 | Is the price additive? | Values for bundles need not be additive, which matches real behaviour |
| 19:21 | (Koyejo asks) How would you game a standard auction? | Bid only the minimum you have to, ideally last, just above the current maximum |
| 20:54 | (Koyejo asks) Why might second price be interesting? | A student suggests ties; Koyejo assumes unique bids |
| 21:39 | (comment) I could just bid a million dollars | You always win, as long as you are willing to pay the second price |
| 22:26 | (comment) Someone could then bid \$999,000 | Yes: everyone is strategic, and now the second price is far above your value |
| 24:45 | Is the reserve price hidden? | Either is possible; here it is known and public |
| 38:02 | Is second price also best for the seller? | No; it is IC but not revenue-maximizing (Myerson's auction is) |
| 1:04:22 | (comment) This is information asymmetry, like the painting that destroyed itself at auction | Koyejo agrees; to a buyer it may seem adversarial |
| 1:05:09 | Was it an NFT? | No, a real painting with a paper shredder |
| 1:05:54 | (comment) A model can think for 2 minutes and output zero tokens | "A great, actually very modern" example of the issue |
| 1:13:44 | (comment) The painting later sold for more because of its history | "A fun meta mechanism": destroying things to raise prices |

## Where the captions are unclear

See the [edited transcript](../raw/transcripts/04-mechanism-design.md)'s header for the full list.
The ones that touch content:

- The words before "economic preferences" in the lecture's key question (≈7:03) are garbled.
- Part of the student's question about the \$3 cupcake (≈9:24) is garbled, and who says it is
  uncertain.
- The name for a buyer's list of bundle values is garbled the first time (≈26:23); at ≈27:09 he
  calls it their "type".
- The person who introduced incentive compatibility in '72 is captioned "Heritz" (≈30:14).
- One word describing second price's status (≈37:15) is garbled, and so is part of the contrast
  with generalized second price (≈44:12).
- The reserve price in Myerson's i.i.d. case is captioned "buy in" (≈52:45).
- The name of the earlier work on regret, "that we did last lecture", is garbled (≈55:48).
- The terms *prophet inequality* and *secretary problems* are restored from "profit inequality"
  and "sector problems" (≈57:19, ≈58:08), from the sound and Koyejo's own descriptions; no course
  document prints them.
- The auction house and artist in the shredded-painting story are garbled (≈1:04:22, ≈1:13:44).
- The second baseline and the last loss in the labelling results are garbled (≈1:19:09, ≈1:19:55).
- The tutorial author and the instructor recommended at the end are captioned "Ellen" and "Tim
  Ruffgarden" (≈1:20:40, ≈1:21:27).

## Related pages

- [Mechanism design: auctions, incentives and truthful elicitation](mechanism-design.md): this
  lecture's concepts gathered in one place, with what lectures 1 and 3 say about strategic agents.
- [Asking humans for preferences](preference-queries.md): prices as revealed preferences, and
  pairwise and thumbs-up feedback as cheap signals of value.
- [Whose preferences](whose-preferences.md): who decides the desirable outcome, and paying
  labellers by harm.
- [RLHF and the language-model pipeline](rlhf.md): pricing prompt completions.
- [Lecture 3 — Model-based Preference Optimization](03-model-based-preference-optimization.md):
  the lecture that deferred a mechanism-design paper to this one.
- [Lecture 2 — Preference Models](02-preference-models.md): utility as value, and revealed versus
  stated preferences.
- [Lecture 1 — Introduction](01-introduction.md): strategic agents among the course's open
  questions.
