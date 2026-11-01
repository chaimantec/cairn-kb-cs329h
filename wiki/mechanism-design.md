# Mechanism design: auctions, incentives and truthful elicitation

Mechanism design is "the science of rule making": choosing the rules of an interaction so that it
reaches a desirable outcome even when the participants are strategic (lecture 4, ≈0:52, ≈1:39). The
course treats it as social choice combined with game theory (≈0:05). Its interest for learning from
human preferences is that a well-designed mechanism makes telling the truth the best strategy. When
preferences can be expressed as prices, such a mechanism is also a way to **elicit** them honestly
(≈29:29, ≈1:19:55).

**Sources so far:** [lecture 4](04-mechanism-design.md), which is about mechanism design; and two
earlier pointers. [Lecture 1](01-introduction.md) lists strategic participants and truthfulness among
the course's open questions (≈19:57, ≈1:14:55). [Lecture 3](03-model-based-preference-optimization.md)
planned a paper tying metric elicitation to mechanism design and deferred it (≈0:05, ≈1:15:55); the
lecture 4 recording does not take it up. The catalog's *Voting* lecture (7) and the guest lecture by
Joseph Jay Williams (8), which lecture 4 says uses related ideas for A/B testing and online learning
(≈1:20:40), are not yet in this knowledge base.

## Why a preference course studies auctions

The course keeps asking people what they prefer and assuming they answer honestly. Lecture 1 asks
what happens when the people giving preferences are **strategic agents** trying to game the system
(≈19:57), and lists "truthfulness and strategic behavior" among the questions the course will face
(≈1:14:55). Mechanism design is the field that studies this directly.

Lecture 4's bridge is to treat preferences as economic. "If you think of preferences as being
economic, or as able to be economically priced or judged or valued, then preferences are now
grounded here as prices people are willing to pay" (≈11:40). Koyejo calls this incomplete for the
course as a whole, which covers many preferences that are not obviously priced, but "very useful"
where things can be grounded economically (≈11:40, ≈12:25). The key question becomes what value
different stakeholders have for items (≈7:03). Incentive compatibility, defined below, can be read
in a revenue sense, "or you can also think about this in terms of eliciting preferences": the true
value is what the elicitation is after (≈29:29).

## The vocabulary

The definitions below are lecture 4's (≈26:23–27:56). The symbols are this page's, since the lecture
writes none aloud.

- **Items and buyers.** There are $m$ items and $n$ buyers, and each buyer has a value for every
  possible **bundle** of items. Values for bundles need not be additive: a coffee and a cupcake
  together can be worth more, or less, than the two separately (≈15:32, ≈17:05).
- **Type.** A buyer's list of values for every bundle (≈26:23, ≈27:09).
- **Allocation.** The rule deciding which buyers get which items.
- **Payments.** The rule deciding how much each buyer pays.
- **Revenue.** The sum of payments across the buyers who took part (≈27:56).
- **Utility.** A buyer's value for what they win minus what they pay, and zero if they win nothing.
  With value $v_i$ and payment $p_i$ for buyer $i$, the lecture's description is
  $u_i = (v_i - p_i) \cdot \mathbb{1}[i \text{ wins}]$ (≈31:47). In the coffee example a buyer who
  values the pair at 6 and pays 5 gets utility 1 (≈15:32).

**Who chooses the goal.** As in social choice, the designer decides what the desirable outcome is
(≈1:39, ≈9:24). Many framings, and most of lecture 4, take **maximal revenue** as that
outcome. **Welfare** is an alternative, "not that different, some difference of cost and revenue",
and a designer could build for some other notion of social good instead (≈9:24–10:55).

## The properties

- **Incentive compatibility (IC).** Bidding your true value is the best strategy (≈28:42). It is
  defined at three levels, by how much each bidder knows (≈41:09–42:40):
  - **ex ante**: truthful in expectation over values drawn from a known distribution;
  - **ex interim**: bidders know their own value and the distribution of the others', and truth is
    still the dominant strategy;
  - **ex post**, the strongest: bidders know everyone's actual values and should still be truthful.

  There is also work on **approximate** incentive compatibility (≈46:33). Lecture 4 says IC was
  introduced in '72, by someone the captions name "Heritz", and recognized with a Nobel Prize in 2007
  (≈30:14).
- **Individual rationality (IR).** A participant who bids truthfully is no worse off taking part than
  staying out, which lowers the barrier to entry (≈29:29, ≈38:48). It too can be analysed at
  different levels of information (≈47:18).
- **Revenue or welfare.** The designer's objective, from the seller's or society's point of view
  (≈1:20:40).

## Mechanisms compared

| Mechanism | Who wins | What the winner pays | Incentive compatible? |
| --- | --- | --- | --- |
| Posted price | Anyone whose value exceeds the price | The posted price | Not discussed; a sale reveals only that value exceeds price (≈17:51) |
| Highest bid wins, pays own bid (first price) | Highest bidder | Their own bid | No: bid just enough to win (≈19:21, ≈20:08); used for display ads (≈43:26) |
| Second price (Vickrey) | Highest bidder | The second-highest bid | Yes, and individually rational, but not revenue-maximizing (≈31:00–40:21) |
| Second price with reserve | Highest bidder, if above the reserve | The larger of the reserve and the second-highest bid | Not discussed; introduced to guard against a seller–buyer value mismatch and collusively low bids (≈23:11–24:45) |
| Myerson's auction (single item) | Highest positive **virtual value** | The inverse of the virtual-value function at the others' highest virtual value | Yes, and revenue-maximizing (≈47:18–52:45) |
| Generalized second price | Bidders for ranked ad placements in sponsored search | Second-price style; details not given | No, yet "probably the most popular deployed algorithm" (≈44:12, ≈44:59) |

**Why second price is truthful** (lecture 4, ≈32:34–36:30). Overbidding never helps. If you would
have won, you still win at the same price; if you would have lost, you may now win but pay more than
your value. Underbidding never helps either. If you would have won, you may now lose and get
nothing; if you would have lost, you still lose. Koyejo credits this property with much of the
auction's success (≈36:30, ≈37:15). The same argument shows it is individually rational: a truthful
bidder either wins and pays less than their value, or loses and pays nothing (≈39:34).

**Why Myerson's auction exists.** Second price "leaves revenue on the table", because a strong bidder
pays only the weaker bidder's bid. Charging the top bid instead would break incentive compatibility
(≈48:03, ≈48:52). Myerson ('81, a Nobel) found the single-item auction that keeps IC and maximizes
revenue. It works on each bidder's virtual value, a correction of their value computed from their
value distribution, whose formula the lecture does not read out (≈47:18–51:58). When values are
i.i.d. it reduces to second price with a reserve (≈52:45). For two or more items the optimal
auction is, to Koyejo's knowledge, unknown (≈53:31).

**Why mechanisms in use are often not IC.** Values can be expensive to compute; rules must be
explainable; bids can leak into future parameters; and agents may not be risk neutral (≈44:59,
≈45:46). Second price's guarantee is for a single item, while search ads sell ranked bundles of
placements, so search systems use a form that loses the guarantee (≈37:15, ≈44:12).

See [lecture 4](04-mechanism-design.md#three-ways-to-sell) for the classroom discussion of how
students would game each auction.

## Learning inside mechanisms

When a learned model sits inside a mechanism, as it does in modern ad bidding, new questions arise
(lecture 4, ≈54:17–59:40). They include the seller's **regret** against the best price in hindsight;
buyers who **learn to bid**, discovering an item's value only when they win it; arrival-order
settings, the **prophet inequality** (adversarial order, random values) and **secretary problems**
(random order, adversarial values); and learning from **revealed preferences** under pricing. Many of
these are sample-complexity and algorithmic questions of the kind the course asks elsewhere, and
Koyejo thinks their lessons for preference elicitation in AI are underused (≈58:53, ≈59:40). See
[asking humans for preferences](preference-queries.md).

## Mechanisms driven by preference feedback

Lecture 4 closes with two applications from Koyejo's group, built on second price but with values
**predicted from pairwise feedback** rather than bid (≈1:00:29–1:19:55):

- **Pricing digital goods.** A prompt completion's value is unknown until it exists, so neither side
  can price it in advance, an information asymmetry. The mechanism learns to predict each user's
  value for a completion from pairwise comparisons and thumbs up or down on a price. It then runs a
  second-price auction on the predictions: the highest predicted offer wins and pays the second
  highest. With enough examples the predictions are claimed to be good enough to keep high revenue
  and incentive compatibility (≈1:01:16–1:12:57).
- **Paying labellers by harm.** As a **reverse auction**, the same machinery sets pay for labelling
  toxic or psychologically difficult material according to the predicted harm to each labeller.
  Koyejo repeatedly says it is one lever, not a solution, and not a normative claim. It needed much
  less information than regression on observed values and had lower regret than a uniform
  allocation (≈1:14:31–1:19:55). See
  [whose preferences](whose-preferences.md#the-labour-of-labelling).

## Related pages

- [Lecture 4 — Mechanism Design](04-mechanism-design.md): the full lecture, with every student
  question.
- [Asking humans for preferences](preference-queries.md): strategic answerers, revealed preferences,
  and cheap pairwise signals.
- [Whose preferences](whose-preferences.md): aggregation, who decides the desirable outcome, and
  labelling labour.
- [Discrete choice models](discrete-choice-models.md): utility as the quantity a choice reveals.
- [Metric elicitation](metric-elicitation.md): the line of work lecture 3 planned to connect to
  mechanism design.
