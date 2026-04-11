---
title: "Predictive Coding"
type: theory
aliases: ["prediction error minimization", "predictive processing"]
tags: [learning-rule, prediction, cortex, perception]
source_count: 2
last_updated: 2026-04-10
status: established
---

Predictive coding is a theory of neural computation proposing that the brain continuously generates predictions about its sensory input and updates its internal model by minimizing **prediction errors** — the discrepancy between predicted and actual neural activity. When embedded in a closed sensorimotor loop (as in [[li-2024-prediction-noise-reward|PaN]]), prediction is not just a perceptual mechanism but the core operation of a control system — the organism predicts, acts, and updates, with prediction error driving both model refinement and action selection.

## Core Idea

In a predictive coding network, each layer maintains a prediction of what the layer it connects to should look like. Prediction errors (the difference between predicted and actual activity) drive learning: both neural activities and synaptic weights update to reduce these errors. All updates are **local** — each neuron only needs information available at its own synapse.

## Prediction Direction

A key architectural distinction exists between two formulations:

**Top-down predictive coding** (Rao & Ballard): Higher, more abstract layers predict lower, more sensory layers. Predictions flow downward, prediction errors flow upward. The energy function has the form:

$$E = \frac{1}{2}(x_0 - s)^2 + \frac{1}{2}\sum_{l=0}^{L-2}(x_l - f(V_l \, x_{l+1}))^2$$

This implies the brain has a **generative model** — abstract representations at the top reconstruct sensory data at the bottom. Requires separate top-down and bottom-up connection pathways.

**Bottom-up predictive coding** (Bogacz et al.): Lower layers predict upper layers through feedforward weights. The energy function has the form:

$$E = \frac{1}{2}(s - x_0)^2 + \frac{1}{2}\sum_{l=1}^{L-1}(x_l - \text{Relu}(W_{l-1} x_{l-1}))^2$$

Architecturally simpler — one set of weights, computation flows bottom-up. Used by the PaN algorithm in [[li-2024-prediction-noise-reward|Li et al. (2024)]].

The real brain likely uses **both directions** simultaneously — the cortex has massive reciprocal connectivity. However, bidirectional models are harder to analyze because convergence requires the whole system to settle into a consistent state.

## Variants

- **Base Predictive Coding (PC)**: Activities run to convergence, then weights update. Requires an external signal to switch between phases.
- **Monte Carlo Predictive Coding (MCPC)**: Adds noise to activity updates. Can infer posterior distributions over latent variables. Explains stimulus-onset reduction in neural variability observed experimentally.
- **Incremental Predictive Coding (iPC)**: Couples activity and weight updates in alternation every timestep, eliminating the need for a convergence signal. Faster than PC with convergence guarantees.
- **PaN (Prediction and Noise)**: Combines MCPC's noise injection (extended to weights) with iPC's coupled updates. Operates in a closed loop with an environment, producing emergent reward-seeking behavior.

## The Dark Room Problem

A fundamental challenge for predictive coding as a theory of behavior: if the brain minimizes prediction error, the easiest solution is to seek out maximally predictable environments — sitting in a dark room doing nothing. See [[Dark Room Problem]].

## Relationship to Neural Adaptation

Predictive coding at the network level is structurally similar to [[Neural Adaptation]] at the single-neuron level — both encode deviations from an expected baseline rather than absolute values. Adaptation adjusts a neuron's input-output mapping based on recent stimulus history; predictive coding adjusts a layer's representation based on predictions from other layers. The burst-dependent plasticity threshold P̄ in [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] is formally analogous to adaptation — learning is driven by deviations of burst probability from a slowly moving average, not by absolute burst rate.

## Biological Plausibility

Predictive coding is considered more biologically plausible than backpropagation because:
- All updates are local (no need to propagate errors through the full network)
- It naturally accounts for top-down influences on perception
- The prediction error signals map onto known neural response properties

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — extends predictive coding to closed-loop behavior via PaN
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst probability deviation from adaptive baseline as prediction-error-like signal
