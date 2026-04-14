---
title: "Self-Supervised Behavior"
type: theory
aliases: ["SSB"]
tags: [learning-framework, emergent-behavior, autonomy]
source_count: 2
last_updated: 2026-04-13
status: emerging
---

Self-supervised behavior (SSB) is a framework proposed by [[li-2024-prediction-noise-reward|Li et al. (2024)]] to describe agents whose goal-directed behavior emerges from internal dynamics rather than optimization of an external objective. It is positioned as distinct from both reinforcement learning and [[Active Inference]].

SSB is fundamentally a theory of closed-loop sensorimotor control: the agent senses, predicts, acts, and updates — continuously, with no separation between learning and behaving. Goal-directed behavior is not layered on top of a control loop; it *is* the control loop operating under noise. This makes SSB a natural starting point for understanding how more complex cognitive capacities (memory, planning, abstraction) might emerge as extensions of basic sensorimotor dynamics.

## Defining Features

1. **Internal, local loss with no environmentally defined global utility function** — the agent's updates are driven entirely by local prediction errors. The environment never provides a reward signal.
2. **Autonomous operation with continual learning** — no external entity directs the agent. No separation between training and deployment.
3. **Self-selected goals with evidence of improving performance on those goals** — goals emerge from internal dynamics, and the agent demonstrably gets better at achieving them over time.

## Distinction from Reinforcement Learning

RL assumes an external Markov Decision Process with a reward function, and the agent optimizes expected return. In SSB, the "reward-seeking" behavior is an emergent consequence of prediction error minimization under noise — the network doesn't *know* it's seeking reward. There is no reward function being optimized.

## Distinction from Active Inference

Active inference aims for Bayes-optimal behavior and frames both perception and action under a single variational objective. SSB makes no optimality claims — continuous noise injection prevents optimality and is necessary for the framework's key behaviors.

## Current Status

SSB is currently instantiated only through the PaN algorithm. The framework is conceptually ambitious but early-stage. Key open questions include whether SSB-type agents can handle temporal credit assignment, learn sensory representations, and scale to realistic environments.

## Ethological Support

[[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] provide the strongest ethological fit to date. Mice in an overnight labyrinth exhibit rich, structured behavior — efficient exploration, one-shot home-path learning, sudden-insight transitions — in conditions where **no reward signal is provided at all**. Exploration is the dominant behavioral mode regardless of reward availability (see [[intrinsic-exploration|intrinsic exploration]]). This is consistent with SSB's central claim that goal-directed behavior emerges from internal loop dynamics rather than external utility.

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — introduces the SSB framework
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — ethological support: rich structured behavior in unrewarded mice
