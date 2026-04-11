---
title: "Dendritic Computation"
type: concept
aliases: ["dendritic processing", "apical dendrites", "dendritic compartments"]
tags: [pyramidal-neurons, dendrites, computation, credit-assignment, calcium]
source_count: 2
last_updated: 2026-04-10
confidence: established
---

Dendritic computation refers to the information processing performed within the dendritic tree of a neuron, beyond simple summation of inputs at the soma. Pyramidal neurons in cortex have functionally distinct dendritic compartments that receive different classes of input and perform different computations, making the single neuron a more powerful computational unit than a simple point integrator.

## Compartmentalization in Pyramidal Neurons

Cortical pyramidal neurons have two major dendritic compartments:

- **Basal dendrites / perisomatic region**: Receive **feedforward (bottom-up)** input from lower cortical areas and thalamus. This is where the neuron integrates sensory-driven signals.
- **Apical dendrites**: Receive **feedback (top-down)** input from higher cortical areas and thalamic matrix neurons. This is where contextual, predictive, and error signals arrive.

This separation means a single neuron has access to both bottom-up evidence and top-down expectations, integrated in different compartments. The interaction between compartments — particularly whether apical input triggers regenerative dendritic events — determines the neuron's output mode.

## Dendritic Regenerative Activity

Apical dendrites contain voltage-gated calcium channels (VGCCs) that can produce **dendritic calcium spikes** — regenerative events analogous to somatic action potentials but mediated by calcium rather than sodium. When apical input is strong enough, a calcium spike propagates toward the soma and can trigger a **burst** of somatic action potentials (high-frequency doublet or triplet, ISI < 16 ms).

This burst/spike distinction is computationally significant: [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] show that whether a neuron bursts or fires isolated spikes determines the **sign of synaptic plasticity** at its input synapses (burst → LTP, isolated spike → LTD). Top-down feedback therefore controls plasticity in lower areas by modulating burst probability — a mechanism for [[Credit Assignment]].

## Single Neurons as Multi-Layer Networks

Beyond compartmentalization, the branching structure of the dendritic tree itself provides computational power. [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] model a single neuron's dendrite as a sparse binary tree ANN (*k*-tree) where each dendritic branch node takes 2 inputs and applies a nonlinearity before passing its output toward the soma. This makes a single biological neuron internally equivalent to a multi-layer network — not a point integrator.

Key results:
- A single dendritic tree (1-tree) significantly outperforms a linear classifier (the point-neuron proxy) on binary image classification (MNIST: 92.2% vs 87.5%)
- When the same input is repeated across *k* subtrees — modeling **multi-synaptic boutons (MSBs)**, where the same presynaptic axon contacts the same dendrite at multiple points — performance monotonically increases and approaches a parameter-matched 2-layer fully connected network
- MSBs are biologically real: ~4 synapses per postsynaptic neuron, 11.5% MSBs in enriched environments, and **LTP increases MSBs 6-fold** (Toni et al. 1999)

This means learning doesn't just tune synaptic weights — it **replicates connections** across dendritic branches, directly increasing the neuron's computational capacity. The dendritic tree's branching structure is not just a wiring convenience; it is the substrate for nonlinear, multi-layer computation within a single cell.

## Escaping the Star Topology

The [[Action Potential|star topology constraint]] of single-compartment neuron models (all gating variables couple only through shared voltage) limits dynamical richness. Dendritic compartments provide an escape route: each compartment has its own local voltage, and the coupling between compartments adds degrees of freedom. This allows the neuron to perform computations — like separating feedforward from feedback signals — that a point neuron cannot.

## Role in Credit Assignment

In the burst-dependent credit assignment framework:
1. Feedforward input to basal dendrites drives **event rate** (the neuron's representation of its input)
2. Feedback input to apical dendrites modulates **burst probability** (the teaching signal from higher areas)
3. Short-term plasticity separates these signals: feedforward synapses use STD (transmit events), feedback synapses use STF (transmit bursts)
4. Inhibitory microcircuits (somatostatin-positive interneurons targeting apical dendrites) linearize the burst probability response, ensuring the credit signal is faithfully transmitted

## Sources

- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — apical dendrites as the substrate for top-down steering of plasticity via burst control
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — dendritic trees as multi-layer networks; single neurons can solve complex classification tasks
