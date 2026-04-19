---
title: "Predictive Coding"
type: theory
aliases: ["prediction error minimization", "predictive processing"]
tags: [learning-rule, prediction, cortex, perception]
source_count: 4
last_updated: 2026-04-18
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

## Predictive Coding as Credit Assignment

[[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] provide the strongest bridge between predictive coding and [[Credit Assignment]] in the wiki. In their dendritic microcircuit model, each cortical layer contains pyramidal neurons (three compartments: soma, basal, apical) and lateral SST interneurons. The interneurons learn to predict and cancel top-down feedback at the apical dendrite, establishing a **self-predicting state** where apical compartments are silent. When a novel teaching signal arrives at the output, interneurons can't explain it away → prediction errors appear at apical dendrites → these errors propagate backward through the network.

The key result: in the weak-feedback limit, the apical prediction error at layer k is exactly the backpropagated error — the output error multiplied by the chain of derivative and weight matrices. **Predictive coding and backpropagation are not competing theories; they are two descriptions of the same dendritic microcircuit.** The prediction error *is* the credit signal.

This unification has a concrete architectural interpretation: the top-down pathway carries the "actual" feedback signal, the lateral (SST interneuron) pathway carries the "predicted" feedback signal, and the apical compartment computes their difference. All plasticity rules are local dendritic prediction error rules of the form dw/dt = η[φ(u) − φ(v)]r, belonging to the dendritic predictive plasticity family (Urbanczik & Senn 2014).

## Historical Root: The Helmholtz Machine

Hierarchical predictive coding descends directly from the [[Helmholtz Machine]] of [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]], which first cast unsupervised learning as variational inference in a network with separate top-down (generative) and bottom-up (recognition) pathways. The [[Variational Free Energy|Helmholtz free energy]] they introduced — `F = Σ Q E − H[Q]` — becomes the predictive-coding energy function when the generative model is linear-Gaussian and the recognition distribution is Gaussian at each layer. Rao & Ballard's (1999) hierarchical predictive coding is best understood as a continuous-latent specialization of the Helmholtz framework, and Friston's free-energy principle generalizes it further to include action ([[Active Inference]]).

The two architectural commitments that survive the lineage intact are:
- **Separate recognition and generative pathways** with independent weights — the top-down pathway predicts, the bottom-up pathway infers, and the two are not forced to be transposes of each other (as in Boltzmann machines).
- **Local prediction-error learning** — all updates depend only on pre- and post-synaptic activity at each synapse, with the error signal computed from the mismatch between top-down prediction and bottom-up signal.

See [[Analysis-by-Synthesis]] for the broader philosophical and historical context.

## Biological Plausibility

Predictive coding is considered more biologically plausible than backpropagation because:
- All updates are local (no need to propagate errors through the full network)
- It naturally accounts for top-down influences on perception
- The prediction error signals map onto known neural response properties
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] show that dendritic prediction errors in mouse visual cortex (Zmarz & Keller 2016, Attinger et al. 2017) are consistent with the self-predicting microcircuit framework

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — extends predictive coding to closed-loop behavior via PaN
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — unifies predictive coding and backpropagation: apical dendritic prediction errors (top-down minus lateral prediction) are analytically equivalent to backpropagated gradients
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst probability deviation from adaptive baseline as prediction-error-like signal
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — historical root: the [[Helmholtz Machine]] introduces variational free-energy learning with separate top-down generative and bottom-up recognition pathways
