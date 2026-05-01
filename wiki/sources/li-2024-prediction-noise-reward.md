---
title: "Neuron-level Prediction and Noise can Implement Flexible Reward-Seeking Behavior"
type: source
source_type: paper
authors:
  - "Chenguang Li"
  - "Jonah Brenner"
  - "Adam Boesky"
  - "Sharad Ramanathan"
  - "Gabriel Kreiman"
year: 2024
doi: "10.1101/2024.05.22.595306"
tags: [predictive-coding, neural-noise, reward-seeking, emergent-behavior, attractor-dynamics, explore-exploit]
date_ingested: 2026-04-10
key_finding: "Local predictive updates plus internal noise are sufficient for neural networks to exhibit flexible reward-seeking behavior without any external reward function."
---

## Overview

This paper introduces **PaN (Prediction and Noise)**, an algorithm demonstrating that neural networks can implement reward-seeking behavior using only two ingredients: local predictive updates and internal noise. Networks autonomously explore environments, switch between exploration and exploitation phases, adapt to changes in architecture and environment, and form task preferences — all without an explicit reward function or external control signals.

The authors position PaN against two backgrounds: the **emergent view** of the brain (behavior arises from interactions of many small components using local rules, not from specialized modules) and the [[Dark Room Problem]] in [[Predictive Coding]] (a prediction-error-minimizing agent could trivially minimize error by doing nothing). PaN's key insight is that [[Neural Noise]] solves the dark room problem by destabilizing unrewarding states while leaving rewarding states stable.

[PDF](../../raw/papers/li-2024.pdf) | [Transcript](../../raw/papers/li-2024-transcript.md)

## Key Findings

**1. Noise creates asymmetric stability across states.** In the simplest case (two neurons, one weight), the no-reward attractor has all fixed points on the decision boundary (x₁ = 0), making it inherently fragile under noise. The reward attractor has x₁ = Ws ≠ 0, placing it away from the decision boundary and making it robust to perturbation. This asymmetry means noisy predictive networks naturally spend more time in rewarding states.

**2. Networks prefer maximally rewarding actions.** Larger sensory signals allow the network to fixate on an action with smaller weights, which reduces the amplification of activity noise through the prediction term. Weight decay emerges naturally (not from explicit regularization) as a consequence of minimizing prediction error under noise.

**3. Explore/exploit switching is emergent, not designed.** [[Attractor Dynamics]] explain the behavioral phases: the network sits on a reward attractor (exploitation), noise causes it to drift toward the attractor's edge, it transits through the unstable no-reward region (exploration), and lands on a reward attractor again. This produces a bimodal entropy distribution — distinct behavioral states — unlike ε-greedy which produces uniform random exploration.

**4. Networks adapt to internal and external changes.** PaN networks handle architectural changes (neurons added/removed mid-simulation), dynamic reward mappings (reward associations flipped), and even changes in motor interface (rotational → translational control).

**5. Networks form autonomous preferences.** Between equally rewarding tasks, preferences emerge based on:
- **Noise patterns and weight initialization** — different random seeds produce different preferences (analogous to individual behavioral differences in genetically identical organisms)
- **Connectivity density** — more connections from an input neuron to the hidden layer biases the network toward that action
- **Learning rate modulation** — when the weight learning rate exceeds the activity learning rate for a given action, the network strongly prefers it (weights "lock in" before activities can explore alternatives). The biological analog is [[dopamine]] modulating synaptic plasticity rates (Coddington et al., 2023).

## Methods

PaN combines elements from two prior predictive coding algorithms:
- **MCPC (Monte Carlo Predictive Coding)**: adds noise to activity updates
- **iPC (Incremental Predictive Coding)**: couples activity and weight updates in alternation (rather than running activities to convergence, then updating weights), eliminating the need for an external control signal

**The PaN algorithm** (Algorithm 1): At each timestep, the network gets sensory input from its previous action, updates all layer activities J times using the gradient of the predictive energy (with noise injected), updates weights once (with noise injected), clips weights to [-2, 2], and selects the next action via argmax of the last layer.

**Predictive energy:**

$$E(t) = \frac{1}{2}(s(t) - x_0(t))^2 + \frac{1}{2}\sum_{l=1}^{L-1}(x_l(t) - \text{Relu}(W_{l-1}(t)x_{l-1}(t)))^2$$

The first term anchors the bottom layer to sensory input. Each subsequent term measures how well layer l-1 predicts layer l through the weights. Note: predictions flow **bottom-up** (lower layers predict upper layers), which differs from classic Rao & Ballard top-down predictive coding.

**Attractor analysis:** The two-neuron system is formalized as a stochastic differential equation. Fixed points are x₀ = s, x₁ = Ws. Stability is analyzed via the Jacobian of the SDE.

Environments tested: two-action bandits, six-action bandits with linearly spaced rewards, 2D open-field navigation with reward landscapes, changing environments, and multi-landscape preference tasks. All experiments run on CPUs.

## Implications

**For theories of biological learning:**
- Reward-seeking may not require a reward function at all — it can emerge from prediction error minimization under noise. This challenges the centrality of reward signals in standard RL models of the brain.
- Dopamine's role may be more subtle than RL assumes: not defining what's rewarding, but biasing *which* emergently-selected goals get preferred through learning rate modulation.
- The inverted-U relationship between noise and performance (too little → fixation, too much → random, intermediate → optimal) connects to known roles of neuromodulators like norepinephrine in regulating the [[Explore-Exploit Tradeoff]].

**For understanding evolution's investments (the wiki's reading, not Li et al.'s claim):**
- The paper demonstrates that *in their toy network*, prediction + noise produces reward-seeking-like behavior without a reward function. The wiki has at times generalized this to "evolution didn't need to invent goal-directed behavior — only to shape it." That extrapolation is interpretive, not stated in the paper. Whether the toy result scales to real organisms is open (the paper acknowledges this; see Open Questions below).

**The paper proposes a new framework: [[Self-Supervised Behavior]] (SSB)**, defined by three features:
1. Internal, local loss with no environmentally defined utility function
2. Autonomous operation with continual learning
3. Self-selected goals with evidence of improving performance on those goals

## Connections to Existing Knowledge

- **[[Predictive Coding]]**: PaN builds directly on the predictive coding framework (Bogacz et al., Rao & Ballard), but extends it from perception to closed-loop behavior in environments.
- **[[Active Inference]]**: PaN shares the idea that actions minimize predictive errors, but differs fundamentally — active inference aims for Bayes-optimal behavior and assumes noise can be averaged over, while PaN requires noise and does not optimize any global objective.
- **[[Attractor Dynamics]]**: The attractor framework provides the theoretical backbone for understanding PaN's behavioral phases. Connects to Hopfield networks and dynamical systems approaches in neuroscience.
- **[[Explore-Exploit Tradeoff]]**: PaN offers a mechanistic, emergent account of explore/exploit switching that doesn't require a designed parameter (like ε in ε-greedy).
- **[[Computation Through Dynamics]]**: PaN is a local-rule instantiation of the CTD stance. Each neuron follows a simple predictive-update rule, but the reward-seeking behavior is a property of the population's dynamics — specifically, the asymmetric stability of attractors under noise. The "computation" lives in the dynamical structure (fragile vs. robust fixed points), not in any one neuron's activity, and cannot be read off a single unit — exactly the move [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] formalize.
- **Steve Byrnes' cortex-as-prediction-layer model**: PaN is more radical — it doesn't need a separate steering subsystem for basic reward-seeking. However, PaN's bottom-up prediction direction doesn't match the top-down prediction assumed in Byrnes' framework and classic predictive coding.

## Open Questions Raised

- Can PaN handle **temporal credit assignment** (delayed rewards)? Currently limited to immediate sensory feedback.
- Can PaN learn useful **sensory representations** from high-dimensional input, as standard predictive coding can?
- How would PaN handle **aversive stimuli** — signals the network should learn to minimize contact with?
- Would adding **recurrent connections** (enabling working memory, temporal integration) extend PaN's capabilities to more realistic tasks?
- What is the relationship between PaN's noise-driven exploration and **norepinephrine/locus coeruleus** modulation of neural gain?
- Is PaN's mechanism relevant to any specific biological circuit, or is it purely a proof of sufficiency for minimal neural systems?
