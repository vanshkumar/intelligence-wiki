---
title: "Self-Supervised Behavior"
type: theory
aliases: ["SSB"]
tags: [learning-framework, emergent-behavior, autonomy]
source_count: 4
last_updated: 2026-04-29
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

## Historical Root: Self-Supervised Perceptual Learning

The "self-supervised" framing has a distinct precursor in the [[Helmholtz Machine]] of [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]], which was motivated as "hierarchical self-supervised learning that may relate to the function of bottom-up and top-down cortical processing pathways." In the Helmholtz machine, the learning signal is the consistency between a generative model's top-down predictions and a recognition model's bottom-up inferences — no external teacher, no reward signal, just the network training itself against its own two views of the same data.

SSB inherits this *no-external-teacher* commitment but extends it from perceptual inference to closed-loop sensorimotor behavior. Where the Helmholtz machine's self-supervision is over static sensory data (train the generative and recognition models against each other), SSB's is over an embodied control loop (let the agent's own predictions drive action, and use the resulting prediction errors to update the model). Both frameworks replace external supervision with internal consistency — the Helmholtz machine does it for perception, SSB does it for behavior. [[Active Inference]] is the intermediate bridge, using the same [[Variational Free Energy|free-energy]] functional for both perception and action.

## Compatibility with Brette's coding critique

[[brette-2018-coding-metaphor|Brette (2018)]] and self-supervised behavior are largely aligned. Both reject the framing that organisms maximize an externally-defined objective (reward in standard RL, Shannon information in efficient coding) and instead seek principles that operate from the inside of the closed sensorimotor loop. SSB's emergent reward-seeking from local prediction + noise is a candidate mechanistic implementation of the kind of organism-internal information processing Brette's [[subjective-physics|subjective physics]] specifies at the conceptual level. PaN-style learning operates over relations between predictions, sensations, and actions — exactly the lawful structure subjective physics identifies as the right unit of analysis. The frameworks differ in their starting assumptions (PaN is a specific neural-network model; subjective physics is a conceptual framework) but converge on the same picture of intelligence as emerging from closed-loop dynamics rather than from inversion of generative models or extraction of efficient codes.

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — introduces the SSB framework
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — ethological support: rich structured behavior in unrewarded mice
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — historical root: the [[Helmholtz Machine]] as self-supervised perceptual learning
- [[brette-2018-coding-metaphor|Brette (2018)]] — conceptual ally: the [[subjective-physics|subjective physics]] / [[sensorimotor-contingencies|sensorimotor contingencies]] framework that SSB's emergent goal-seeking is a candidate mechanistic implementation of.
