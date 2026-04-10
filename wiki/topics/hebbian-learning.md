---
title: "Hebbian Learning"
type: theory
aliases: ["Hebb's rule", "fire together wire together", "Hebbian plasticity"]
tags: [learning-rule, plasticity, synapse, associative-learning]
source_count: 1
last_updated: 2026-04-10
status: established
---

Hebbian learning is the principle that synaptic connections strengthen when pre-synaptic and post-synaptic neurons are active simultaneously — "neurons that fire together wire together." It is the foundational local learning rule in neuroscience.

## The Rule

In its simplest form: if neuron A repeatedly contributes to firing neuron B, the synapse from A to B is strengthened. The change in synaptic weight depends only on **local** variables:
- Pre-synaptic activity
- Post-synaptic activity
- (Optionally) neuromodulatory signals (dopamine, etc.)

This locality is both the rule's strength (biologically plausible — no global error signal needed) and its key constraint.

## The Locality Constraint and Sparse Codes

The locality of Hebbian learning creates a fundamental dependence on neural representations ([[meister-2022-learning-fast-slow|Meister, 2022]]):

A synapse only "sees" whether its pre-synaptic and post-synaptic neurons are active. It cannot determine **why** they are active. When multiple stimuli activate overlapping sets of neurons (distributed codes), a single Hebbian association corrupts others — the interference problem. The synapse from a shared neuron strengthens for one stimulus-action pair and then gets pulled in the wrong direction by another.

[[Sparse Coding|Sparse codes]] solve this: each stimulus activates a unique set of neurons, so each synapse participates in at most one association. This makes Hebbian learning **fast** — a single exposure suffices. The learning rule itself is not the bottleneck; the representation is.

## Speed of Hebbian Plasticity

A common misconception is that synaptic plasticity is slow. In fact, Hebbian modification can occur in a single trial:
- Fear conditioning modifies synapses after one pairing of conditioned stimulus + shock
- The Bruce effect (mate odor recognition) is established in a single mating encounter
- Food aversion learning occurs after one poisoning episode

What's slow is not the plasticity but the **representation building** needed for stimuli that lack pre-existing sparse codes.

## Biological Implementations

Hebbian learning maps onto several known biological mechanisms:
- **Long-term potentiation (LTP)** — sustained strengthening of synapses following correlated activity, especially at NMDA receptor-containing synapses
- **Spike-timing-dependent plasticity (STDP)** — a refinement where the precise timing between pre and post spikes determines whether strengthening or weakening occurs
- **Neuromodulation** — dopamine and other neuromodulators gate or modulate Hebbian plasticity, potentially determining *which* co-active pairs get strengthened (three-factor learning rules)

### The Calcium Bridge

The physical implementation of Hebbian coincidence detection relies on **calcium signaling** ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]). The NMDA receptor is the key molecular device: it requires both pre-synaptic glutamate release AND post-synaptic depolarization to pass calcium — making it a detector of correlated pre/post activity.

The critical distinction is between **calcium-as-state-variable** (transient adaptation effects that vanish when calcium is pumped out) and **calcium-as-trigger** (calcium initiates self-sustaining downstream changes — CaMKII phosphorylation, structural synaptic modification — that persist after calcium is removed). The same ion, same concentration-sensing logic, but **genetically encoded downstream readers** determine whether the effect is transient or lasting. This is how DNA bridges evolutionary timescales to learning rules.

## Relationship to Other Learning Frameworks

- **[[Predictive Coding]]**: Local prediction error minimization can be seen as a generalized form of Hebbian learning — weight updates depend on local activity and local error signals.
- **Backpropagation**: Requires non-local error signals propagated through the network — biologically implausible in its standard form. Predictive coding and related frameworks attempt to approximate backprop with local Hebbian-like rules.
- **[[li-2024-prediction-noise-reward|PaN]]**: Uses local energy gradients for both activity and weight updates, consistent with Hebbian locality. The weight update rule is ∂E/∂W, which depends only on the activities of the two layers the weight connects.

## Sources

- [[meister-2022-learning-fast-slow|Meister (2022)]] — Hebbian learning is fast; the bottleneck is the representation, not the plasticity
- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — calcium as bridge between electrical activity and synaptic plasticity; NMDA as coincidence detector
