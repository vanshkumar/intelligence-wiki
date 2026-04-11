---
title: "Active Inference"
type: theory
aliases: ["active inference framework"]
tags: [predictive-coding, free-energy, perception, action, bayesian]
source_count: 1
last_updated: 2026-04-10
status: emerging
---

Active inference is a theoretical framework proposing that living organisms follow a single imperative: **minimizing the surprise of their sensory observations**. It extends [[Predictive Coding]] from perception to action — when there's a discrepancy between prediction and observation, the organism can either change its beliefs (update internal model) or change the world (take an action that produces input matching its prediction).

Active inference is the closest existing theoretical framework to a control-first view of intelligence: it treats perception and action as two sides of the same closed-loop process. However, its implementations tend to require modular architecture (separate components for planning, action selection, etc.), which limits the "emergent from simple rules" character that [[li-2024-prediction-noise-reward|PaN]] demonstrates. PaN achieves closed-loop control behavior from simpler ingredients — local prediction + noise — without the additional apparatus active inference typically requires.

## Relation to Predictive Coding

Active inference is often described as the action-oriented extension of predictive coding. Where predictive coding explains perception (updating beliefs to match sensory input), active inference explains behavior (acting on the world to make sensory input match beliefs).

The framework is closely associated with Karl Friston's **free energy principle**, which casts both perception and action as minimizing variational free energy — an upper bound on surprise.

## Criticisms

- **Computational cost**: Active inference models require components with separate roles and are computationally expensive to implement
- **Difficulty of understanding**: Critics note these models can be hard to build or understand (Biehl et al., 2021)
- **Not emergent**: Most active inference models do not operate on emergent principles — they have separate modules for action selection, planning, etc., which undermines claims of biological plausibility
- **Scalability**: Scaling active inference models remains an ongoing challenge
- **Noise assumptions**: Active inference and the free energy principle assume that internal noise can be **averaged over** to arrive at long-term behavior. PaN challenges this by showing that noise is **necessary** and cannot be averaged away.

## Contrast with PaN

[[li-2024-prediction-noise-reward|Li et al. (2024)]] shares active inference's idea that actions minimize predictive errors, but differs in key ways:
- PaN does **not** aim to explain or generate Bayes-optimal behavior
- PaN does **not** optimize with respect to any predefined utility function
- PaN's continuous noise injection **prevents** optimality and is **necessary** for its key behaviors
- PaN operates on emergent principles with no separate modules

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — positions PaN as distinct from active inference
