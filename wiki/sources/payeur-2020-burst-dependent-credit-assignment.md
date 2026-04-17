---
title: "Burst-Dependent Synaptic Plasticity Can Coordinate Learning in Hierarchical Circuits"
type: source
source_type: paper
authors:
  - "Alexandre Payeur"
  - "Jordan Guerguiev"
  - "Friedemann Zenke"
  - "Blake A. Richards"
  - "Richard Naud"
year: 2020
doi: "10.1101/2020.03.30.015511"
tags: [credit-assignment, synaptic-plasticity, bursting, dendrites, backpropagation, hierarchical-learning, pyramidal-neurons]
date_ingested: 2026-04-10
key_finding: "Burst-dependent synaptic plasticity, combined with dendritic compartmentalization, short-term plasticity, and inhibitory microcircuits, enables biologically plausible credit assignment in hierarchical circuits that approximates backpropagation gradients."
---

## Overview

This paper proposes a biologically plausible solution to the [[Credit Assignment]] problem in hierarchical neural circuits. The core mechanism: high-frequency bursts in pyramidal neurons serve as an instructive signal that allows higher cortical areas to steer plasticity in lower areas. The sign of plasticity depends on whether the postsynaptic neuron fires a burst (→ LTP) or an isolated spike (→ LTD), and burst probability is controlled by top-down feedback via [[Dendritic Computation|apical dendrites]]. Combined with short-term synaptic plasticity for multiplexing feedforward and feedback signals, and inhibitory microcircuits for linearization, this yields a local, spike-based learning rule that approximates loss-function gradients across multiple layers.

[PDF](../../raw/papers/payeur-2020.pdf)

## Key Findings

### The Credit Assignment Problem

In hierarchical networks, a neuron multiple synapses away from the output cannot directly observe the effect of its activity on behavior. In machine learning, backpropagation solves this by computing gradients layer by layer, but standard backprop requires:
1. Symmetric feedforward and feedback weights (weight transport problem)
2. Non-local error information at each synapse
3. Separate forward and backward passes
4. A non-spiking, continuous framework

Previous biologically plausible alternatives have failed to scale to challenging tasks (CIFAR-10, ImageNet). This paper shows that known properties of cortical neurons — dendrites, bursting, STP, inhibition — are sufficient.

### Burst-Dependent Plasticity Rule

The learning rule is local and spike-based:

**dw_ij/dt = η[B_i(t) − P̄_i(t)] · E_i(t) · Ẽ_j(t)**

Where:
- **B_i** = burst events in postsynaptic neuron i
- **P̄_i** = running average of burst probability (the adaptive threshold)
- **E_i** = event train of postsynaptic neuron i
- **Ẽ_j** = eligibility trace of presynaptic neuron j

When a postsynaptic event is a burst (B > P̄), the weight strengthens (LTP). When it is an isolated spike (B < P̄), the weight weakens (LTD). The burst probability threshold P̄ adapts slowly (~1-10 s), making the rule sensitive to *changes* in burst probability rather than absolute levels — analogous to [[Neural Adaptation]].

This captures a well-established experimental finding: the frequency dependence of synaptic plasticity, where high-frequency pairing produces LTP and low-frequency pairing produces LTD.

### Top-Down Steering via Apical Dendrites

Pyramidal neurons have two functionally distinct dendritic compartments:
- **Basal dendrites / perisomatic region**: receive feedforward (bottom-up) input
- **Apical dendrites**: receive feedback (top-down) input from higher areas

Top-down feedback modulates the probability of bursting via voltage-gated calcium channels (VGCCs) in the apical dendrites. Regenerative activity in apical dendrites (dendritic calcium spikes) can trigger somatic bursts. This means higher areas control the *sign* of plasticity in lower areas — they act as a "teaching signal" that doesn't need to specify the exact synaptic change, only whether to potentiate or depress.

### Ensemble Multiplexing

A critical challenge: how can feedforward and feedback signals coexist in the same neurons without interference? The solution is **short-term synaptic plasticity (STP)**:

- **Feedforward synapses** exhibit **short-term depression (STD)** → they transmit **event rate** (the bottom-up signal encoding stimulus information)
- **Feedback synapses** exhibit **short-term facilitation (STF)** → they transmit **burst rate** (the top-down credit signal)

This means a pyramidal ensemble simultaneously encodes:
- Event rate in the perisomatic compartment (for downstream feedforward processing)
- Burst probability in the apical compartment (reflecting top-down credit)

The two signals are multiplexed through the same neurons but separated by STP type and dendritic compartment.

### Approximation to Backpropagation

At the ensemble level (averaging across neurons in a population), the burst-dependent learning rule approximates loss-function gradients, given two conditions:

1. **Linearity**: Burst probabilities respond linearly to feedback input. Achieved by inhibitory microcircuits — somatostatin-positive interneurons targeting apical dendrites keep burst probabilities in a linear operating range, preventing saturation.

2. **Alignment**: Feedback weights are approximately symmetric with feedforward weights. Achieved by a separate learning rule on feedback connections that uses the same burst-dependent error signal to align feedback with feedforward weights over training.

When both conditions hold, the ensemble weight update approximates:

**ΔW ∝ (p − p̄) ⊙ e ≈ error signal sent backwards**

which is equivalent to the backpropagation gradient.

### Performance on Challenging Tasks

The ensemble-level burst-dependent learning rule, with learned feedback weights and recurrent linearization, achieves:

| Task | This paper | Backprop |
|------|-----------|----------|
| MNIST | 1.1% error | ~1.1% |
| CIFAR-10 | 20.1% error | ~20% |
| ImageNet | 56.1% top-5 error | ~45% top-5 |

This dramatically outperforms previous biologically plausible algorithms. The gap on ImageNet is attributed to inability to use recurrent linearization in convolutional layers due to memory constraints.

Training feedback weights is critical — fixed random feedback weights (as in feedback alignment) perform much worse on CIFAR-10.

### Falsifiable Predictions

1. **STP polarization**: Bottom-up (feedforward) synaptic projections should exhibit predominantly STD; top-down (feedback) projections should exhibit predominantly STF along the sensory hierarchy
2. **Burst variance and learning**: The *variance* of burst probabilities across a neural population should correlate with errors made during learning
3. **Apical inhibition disrupts learning**: Manipulating somatostatin-positive interneurons that target apical dendrites should impair hierarchical credit assignment and disrupt learning in cortical circuits

## Methods

- **Spiking simulations**: Two-compartment pyramidal neuron model (soma + apical dendrite) with VGCCs, inhibitory interneurons (PV+ perisomatic, SST+ apical-targeting), using the Auryn simulator
- **Ensemble-level model**: Coarse-grained rate model derived from the spiking model under mean-field assumptions, used for deep network experiments
- **Deep network**: Convolutional layers + fully-connected layers, trained with the burst-dependent rule on CIFAR-10, ImageNet, and MNIST

## Implications

### For the wiki's core question (how does the brain learn)

This paper offers a concrete, biologically grounded answer to how hierarchical credit assignment could work in cortex. It bridges local [[Hebbian Learning]] (the burst-dependent rule is fundamentally local — pre/post activity only) with global error-driven learning (the post signal is enriched by dendritic computation to carry credit information from higher areas). This resolves the apparent tension between "Hebbian rules are simple" ([[meister-2022-learning-fast-slow|Meister]]) and "the brain clearly learns complex hierarchical representations."

### For understanding biological architecture

The paper reframes several known biological features as computational necessities for credit assignment:
- **Dendritic compartmentalization** → separates feedforward from feedback processing
- **Distinct STP at feedforward vs. feedback synapses** → enables signal multiplexing
- **Inhibitory microcircuits (SST+ interneurons)** → linearize the credit signal
- **Burst/spike distinction** → encodes the sign of the teaching signal

These are not arbitrary biological details — they are the minimum architecture required for gradient-based learning in a spiking network.

## Connections to Existing Knowledge

- **[[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]]**: The direct conceptual precursor. Kording & Konig proposed the same core architecture — two integration sites, burst-gated plasticity, STP-based multiplexing of activity and error signals — and proved it could implement backpropagation in principle. Payeur et al. bring this to biophysical fidelity (spiking neurons, VGCCs, inhibitory linearization, learned feedback alignment) and scale (CIFAR-10, ImageNet). The 2001 paper also demonstrates a self-supervised variant (Imax-style) not explored by Payeur et al.
- **[[guerguiev-2017-segregated-dendrites|Guerguiev, Lillicrap & Richards (2017)]]**: The immediate precursor — co-author Guerguiev's earlier work. First spiking implementation of credit assignment with segregated dendrites, using plateau potentials and two phases. Payeur et al. advance this by eliminating the phase requirement (continuous burst/spike multiplexing), adding biophysical calcium dynamics (VGCCs), and introducing inhibitory linearization. The feedback alignment that Guerguiev showed emerging during training is made explicit and learned in Payeur.
- **[[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]**: Parallel development from the Senn lab (Bern). Sacramento uses a predictive coding interpretation — errors are mismatches at apical dendrites between top-down feedback and lateral interneuron predictions. Payeur uses a burst probability interpretation. Both eliminate the phase requirement and produce backprop-equivalent learning; they represent alternative formalizations of the same biological architecture.
- **[[Hebbian Learning]]**: The burst-dependent rule is Hebbian (local pre/post) but the "post" signal is enriched by dendritic computation to carry hierarchical credit. Bridges Hebbian locality with deep learning
- **[[Synapses]]**: Exploits distinct STP properties (STD vs STF) at feedforward vs feedback synapses; reframes STP as a computational mechanism for signal multiplexing
- **[[Action Potential]]**: Burst vs. isolated spike distinction exploits dendritic regenerative activity (calcium spikes in apical dendrites via VGCCs)
- **[[Predictive Coding]]**: The error signal (burst probability deviation from baseline) has a predictive coding flavor — the moving average P̄ is an expectation, and learning is driven by deviations from it
- **[[Neural Adaptation]]**: The adaptive threshold P̄ is formally analogous to neural adaptation — encoding relative changes in burst probability rather than absolute values

## Open Questions Raised

- Does this mechanism work for temporal credit assignment (sequences, delayed rewards), or only for spatial credit assignment across layers?
- How does this interact with neuromodulatory systems (dopamine, norepinephrine)? The gating term M(t) in the model abstracts over all neuromodulation — what fills that role biologically?
- Can the mechanism support unsupervised learning, or does it require a supervised teaching signal? The authors note that bursting, NMDA-spike cooperativity, and feedforward inhibition could potentially be adapted for unsupervised sequence learning
- Does the STP polarization prediction (STD feedforward, STF feedback) hold across cortical areas? Current evidence is mixed

## Sources

Payeur et al. (2020). bioRxiv preprint, 2020.03.30.015511.
