---
title: "Intrinsic Exploration"
type: concept
aliases: ["exploration drive", "exploration as default", "intrinsic motivation"]
tags: [behavior, exploration, motivation, autonomy]
source_count: 1
last_updated: 2026-04-13
confidence: emerging
---

Intrinsic exploration refers to the observation that animals explore their environments **without requiring external reward**, and that exploration often dominates behavior even when reward is available. This reframes the [[Explore-Exploit Tradeoff]]: exploration is not a fraction of behavior strategically balanced against exploitation, but the **default operating mode** of a nervous system, occasionally interrupted by episodes of exploitation.

## Empirical Grounding

[[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] provide the clearest recent demonstration. In an overnight labyrinth task:

- **Unrewarded mice** explore persistently throughout the session, with no reward signal anywhere in the apparatus
- **Rewarded mice**, after learning the rewarded end-node, still spend ~75–95% of their time exploring unrewarded branches of the maze
- Three behavioral modes appear — *explore*, *drink*, *leave* — and *explore* is dominant in both conditions

This is not a failure of learning (the mice know where the water is and can reach it directly) nor a failure of exploitation (they do drink when in the reward zone). Exploration simply persists as the default behavioral state.

## Theoretical Significance

### For the control thesis

Under the wiki's organizing principle, this is exactly what one would expect: the closed sensorimotor loop runs continuously. Without external reward, the loop still has to do something — and what it does is sample its environment. Exploration is not a policy choice; it is the baseline operation of the loop. External reward biases which trajectories the loop prefers but does not initiate the looping itself.

### For self-supervised frameworks

[[self-supervised-behavior|Self-supervised behavior]] ([[li-2024-prediction-noise-reward|Li et al. 2024]]) predicts that goal-directed behavior emerges from internal dynamics + noise without an external utility function. Rosenberg's unrewarded mice are a strong ethological fit: the animals exhibit rich structured behavior (efficient coverage, multi-second navigation sequences, one-shot home-path learning) with no reward-defining signal from the environment.

### Against purely reward-driven accounts

Standard RL formulations treat exploration as instrumental — a means of reducing uncertainty about where the reward is. Rosenberg's data are incompatible with the strong form of this claim: exploration does not decay to near-zero once reward is localized, and it is present at similar rates in animals that have no reward at all.

## Candidate Mechanisms

- **Neural noise in a prediction-driven loop** — [[li-2024-prediction-noise-reward|PaN]] shows that noise + local prediction is sufficient to drive continuous behavioral sampling with emergent bimodal states. Unrewarded-but-exploring animals may be "all noise, no stable reward attractor."
- **Locus coeruleus / norepinephrine tone** — modulates neural gain and the [[Explore-Exploit Tradeoff]]; persistent mid-level tone could enforce a baseline exploratory mode.
- **Novelty/uncertainty signals** — proposed in intrinsic-motivation RL; biological implementation remains underspecified.
- **Genetically constrained local biases** — Rosenberg's four turning biases (SD ~0.03 across animals) produce efficient exploration from local rules, suggesting the structure of exploration is partly built-in rather than discovered.

## Open Questions

- What is the neural signature of "exploration mode" vs "exploitation mode"? Is it a shift in neuromodulatory state, an attractor transition, or a higher-level controller switching?
- Why do rewarded mice continue to explore at high rates? Is it hedging (the environment might change), intrinsic reward, or simply that reward does not suppress the default mode?
- Does intrinsic exploration have a developmental trajectory? Juvenile mice are famously more exploratory — what controls the set-point?

## Sources

- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — exploration dominant mode in both rewarded and unrewarded mice; exploration efficiency governed by genetically-stable local biases
