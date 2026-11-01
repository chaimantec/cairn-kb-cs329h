# See also — related knowledge bases

Other Cairn knowledge bases whose material bears directly on this course. Each entry gives the
repo URL to pass as `kb` to `kb_read` / `kb_list`, and says what that KB is good for, so you can
decide whether it is worth a turn before reading it. This file is the only place the chat learns
that these siblings exist.

The extra links point at `raw.githubusercontent.com` rather than `github.com/.../blob/...`
because a raw URL returns plain markdown, so they also work as `web_fetch` targets.

CS329H's lecture 1 surveys RLHF, DPO and reward models in words only, with no equations, and
leaves the mechanics to later lectures that this KB does not yet cover. These three courses derive
and implement that machinery. Treat them as other courses' treatments, not as what CS329H teaches.

- **CS224N — Natural Language Processing with Deep Learning** (Stanford, Christopher Manning with
  guest lecturers, Spring 2024).
  KB: `https://github.com/chaimantec/cairn-kb-cs224n` — pass this as `kb` to `kb_read` / `kb_list`.
  Good for the language-model side of learning from preferences, step by step: instruction
  fine-tuning, reward modelling from pairwise comparisons, the KL-penalized RLHF objective, the full
  DPO derivation, RewardBench, and the costs (reward hacking, over-optimization, whose preferences
  get encoded). Lecture 16 is a guest lecture on what came after DPO. **Complete: all 23 lectures.**
  Start at [INDEX](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224n/main/INDEX.md) ·
  [RLHF](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224n/main/wiki/rlhf.md) ·
  [reward modeling](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224n/main/wiki/reward-modeling.md) ·
  [DPO](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224n/main/wiki/direct-preference-optimization.md) ·
  [RewardBench](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224n/main/wiki/rewardbench.md)

- **CS224R — Deep Reinforcement Learning** (Stanford, Chelsea Finn with guest lecturers, Spring 2025).
  KB: `https://github.com/chaimantec/cairn-kb-cs224r` — pass this as `kb` to `kb_read` / `kb_list`.
  Good for the reinforcement-learning side that CS329H's lecture 1 points to: reward learning from
  goal classifiers and from human preferences in robotics-style RL, RLHF and DPO as RL problems, and
  open problems with rewards. **Complete: all 19 lectures.**
  Start at [INDEX](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224r/main/INDEX.md) ·
  [learning rewards from preferences](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224r/main/wiki/preference-learning.md) ·
  [reward learning](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs224r/main/wiki/reward-learning.md)

- **CS336 — Language Modeling from Scratch** (Stanford, Percy Liang and Tatsunori Hashimoto,
  Spring 2026).
  KB: `https://github.com/chaimantec/cairn-kb-cs336` — pass this as `kb` to `kb_read` / `kb_list`.
  Good for the builder's view: preference data collection, reward models, reward
  over-optimization and hacking, and DPO, as they are implemented when training a model.
  **Complete: all 18 lectures.**
  Start at [INDEX](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs336/main/INDEX.md) ·
  [RLHF](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs336/main/wiki/rlhf.md) ·
  [reward models](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs336/main/wiki/reward-models.md) ·
  [preference data](https://raw.githubusercontent.com/chaimantec/cairn-kb-cs336/main/wiki/preference-data.md)
