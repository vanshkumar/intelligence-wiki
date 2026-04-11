---
title: "Credit Assignment"
type: concept
aliases: ["credit assignment problem", "structural credit assignment", "temporal credit assignment"]
tags: [learning, plasticity, hierarchical-learning, backpropagation, computation]
source_count: 1
last_updated: 2026-04-10
confidence: established
---

The credit assignment problem asks: how can a neuron deep in a hierarchical circuit determine whether to strengthen or weaken its synapses in order to improve the organism's behavior? The neuron cannot directly observe the behavioral outcome — it only has access to local signals (its own inputs and outputs). Yet somehow, learning in cortex produces hierarchical representations that require coordinated changes across multiple layers.

Credit assignment is what allows the sensorimotor control loop to tune its own internal processing hierarchy. Without it, only the final output layer can learn from behavioral outcomes — deeper layers are locked. With it, the entire processing pipeline (from early sensory representations to motor output) can be shaped by whether the organism's actions succeed, extending the control loop's reach over more complex, multi-step sensory-to-motor transformations.

## Two Forms

**Structural (spatial) credit assignment**: Which synapses in a multi-layer network should change, and in which direction, to reduce output error? This is the problem backpropagation solves in machine learning.

**Temporal credit assignment**: When a reward or punishment arrives after a sequence of actions, which earlier actions and neural states deserve credit or blame? This is the problem temporal difference learning addresses.

## Why It's Hard Biologically

In machine learning, backpropagation computes exact gradients by propagating error signals backward through the network. This requires:
1. **Weight transport** — feedback connections must be exactly symmetric with feedforward connections
2. **Non-local information** — each synapse needs the error signal from the output, not just its local pre/post activity
3. **Separate phases** — distinct forward (inference) and backward (learning) passes
4. **Continuous, non-spiking signals** — standard backprop operates on real-valued activations

None of these hold in biological neural circuits.

## Biological Solutions

### Burst-Dependent Plasticity

[[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] propose that the burst/spike distinction in pyramidal neurons solves structural credit assignment. Top-down feedback via [[Dendritic Computation|apical dendrites]] controls burst probability, and the sign of plasticity depends on whether the postsynaptic neuron bursts (→ LTP) or fires isolated spikes (→ LTD). This is a local rule that approximates backpropagation gradients at the ensemble level, given linearization by inhibitory microcircuits and learned feedback weight alignment.

### Neuromodulatory Gating

Dopamine reward prediction error signals can gate [[Hebbian Learning|Hebbian plasticity]] — the "three-factor learning rule" (pre activity × post activity × neuromodulator). This addresses temporal credit assignment but only coarsely: the dopamine signal is global and scalar, raising the question of how it gets routed to the specific synapses that were causally responsible.

### Predictive Coding

[[Predictive Coding]] frameworks propose that local prediction errors at each level of a hierarchy provide the error signals needed for credit assignment, avoiding the need for explicit backward passes. The relationship between predictive coding and backpropagation is an active area of research.

## Sources

- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst-dependent plasticity as biologically plausible credit assignment in hierarchical circuits
