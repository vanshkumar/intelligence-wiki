---
title: "Supervised and Unsupervised Learning with Two Sites of Synaptic Integration"
type: source
source_type: paper
authors:
  - "Konrad P. Kording"
  - "Peter Konig"
year: 2001
doi: "10.1023/A:1013776130161"
tags: [credit-assignment, dendrites, backpropagation, bursting, calcium-spike, self-supervised-learning, pyramidal-neurons, synaptic-plasticity]
date_ingested: 2026-04-16
key_finding: "Pyramidal neurons' two sites of synaptic integration (basal and apical dendrites) provide two independent variables per neuron — activity and a learning signal — enabling implementation of both supervised (backpropagation) and self-supervised learning rules that are structurally unavailable to single-site point neurons."
---

## Overview

This paper proposes that cortical pyramidal neurons, with their two functionally distinct dendritic compartments — basal (perisomatic) and apical — provide the minimal architectural substrate needed for gradient-based learning rules. The key insight: most learning algorithms derived from objective functions require **two variables per neuron** — one for the forward-pass activity and one for the derivative of the objective function with respect to that activity (the error/learning signal). Point neuron models, with a single integration site, conflate these two roles. A two-site neuron separates them, and cortical pyramidal neurons are naturally two-site neurons.

The paper demonstrates this with two proof-of-principle implementations: backpropagation of error (supervised) and an Imax-style mutual-information-maximization rule (self-supervised). In both cases, controlled mixing experiments show that collapsing the two sites into one produces a fundamental tradeoff between representing stimuli and learning correctly — a tradeoff absent from the two-site model.

[PDF](../../raw/papers/kording-konig-2001.pdf)

## Key Findings

### The Two-Variable Architecture

The neuron model has two output variables:
- **A** (activity / firing rate) — determined primarily by **basal dendritic** input. This is the neuron's feedforward representation. Transmitted downstream as single spikes.
- **D** (dendritic burst rate) — determined primarily by **apical dendritic** input, modulated by somatic activity. Transmitted downstream as bursts of action potentials triggered by dendritic calcium spikes.

Communication between compartments:
1. **Soma → apical**: backpropagating action potentials (Stuart & Sakmann 1994)
2. **Apical → soma**: regenerative calcium spikes (Larkum et al. 1999b), which produce prolonged depolarization and somatic bursts

The two signals share the same axon but are separated by **short-term synaptic plasticity**: strongly depressing synapses respond only to tonic single spikes (transmitting A), while strongly facilitating synapses respond only to bursts (transmitting D). This is the **STP multiplexing** proposal.

### Anatomical Routing of Information Streams

The paper maps the two-variable architecture onto cortical anatomy:
- **Bottom-up (feedforward)** projections — from sensory thalamus or lower cortical areas — preferentially target **basal dendrites** via layer 4 spiny stellates
- **Top-down (feedback)** projections — from higher cortical areas and long-range lateral connections — preferentially target **apical dendrites** via layer 1 terminations

This is an approximation (acknowledged as partial) but establishes the principle: the anatomical routing of cortical connections is consistent with separating feedforward activity from feedback credit signals.

### Backpropagation Implementation

Under specific assumptions:
- Basal synapses learn only when calcium spikes fire: **ΔW_basal = β D_post A_pre** (burst-gated Hebbian)
- Apical synapses learn by standard Hebbian rule: **ΔV_apical = β A_post A_pre**
- All basal synapses are strongly depressing (V_basal = 0), all apical strongly facilitating (W_apical = 0)
- Transfer function: **D_post = (V_apical D_pre) A_post(1 - A_post)**

The resulting dynamics are **identical to backpropagation**: the error δ is replaced by the burst rate D, yielding ΔW ∝ δA_pre and δ = A(1 - A)Wδ. Errors are transmitted by bursts via top-down connections and processed in the apical dendrite; core signal processing occurs in the soma via feedforward action potentials.

The X-OR demonstration confirms that the two-site network learns a nonlinear function that no single-site Hebbian network can learn (since single-site Hebbian learning approximately searches for principal components).

### The One-Site No-Go Result

The paper's deepest contribution is a **structural argument** that the tradeoff between representing and learning is inherent to single-site neurons:

> "Whenever the objective is not exclusively a function of the neuron's activity, the learning signal cannot be identical to the desired neuronal activity. It can only influence the weights via the one variable, the somatic activity, and therefore needs to distort this activity."

Controlled mixing experiments (parameterized by α, the relative influence of somatic activity on learning) demonstrate this tradeoff empirically. As α increases (approaching a one-site model), performance degrades for both supervised (Fig. 2C) and self-supervised (Fig. 3C) learning. Two sites are not a convenience — they are **structurally necessary** for any objective-based learning that goes beyond PCA/ICA.

### Self-Supervised Learning

The same two-site architecture implements an Imax-style algorithm (Becker & Hinton 1992) that maximizes mutual information between outputs of parallel processing streams. Two streams receive overlapping but partially independent input; the network must extract the shared (coherent) variable and ignore the stream-specific one. Key features:
- Winner-take-all competition at the calcium spike level (only the neuron with highest D_post fires bursts, based on weak inhibition abolishing calcium spikes — Larkum 1999)
- Plasticity triggered only by bursts: ΔW = β D_post(A_pre - W)
- Learning stabilization via activity-dependent weight homeostasis

The network learns to extract coherent information across streams (normalized correlation → 1.0). The one-site control again fails: large α produces correct representation but no learning; small α enables learning but distorts representation.

## Methods

- Rate-based simulation of two-variable neuron model
- X-OR task for supervised learning (3-layer network: input → hidden → output)
- Two-stream coherence extraction task for self-supervised learning (two parallel streams with shared abscissa position but independent ordinate position)
- Controlled mixing experiments parameterized by α to quantify the one-site vs. two-site performance gap

## Implications

### For the control thesis

The two-site architecture is what allows the sensorimotor control loop to tune its own internal processing hierarchy. Without dendritic compartmentalization, deeper layers of the processing pipeline can only learn via PCA-like unsupervised rules — they have no access to error signals from the output. With two sites, the error flows backward via bursts while the forward signal flows via single spikes, and the two do not interfere. This extends the loop's reach over more complex sensory-to-motor transformations — the machinery for hierarchical credit assignment is built into the individual neuron's morphology.

### As seed of the burst-dependent credit assignment lineage

This paper establishes the conceptual framework that [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] later implements in full biological detail:

| Feature | Kording & Konig (2001) | Payeur et al. (2020) |
|---------|----------------------|---------------------|
| Neuron model | Rate-based, two variables A and D | Spiking, two-compartment with VGCCs |
| Compartmentalization | Basal = feedforward, apical = feedback | Same, with explicit dendritic calcium dynamics |
| Burst/spike distinction | D (burst rate) vs A (firing rate) | B (burst events) vs E (event rate) |
| Plasticity rule | ΔW ∝ D_post × A_pre | ΔW ∝ (B - P̄) × E × Ẽ |
| STP multiplexing | Depressing (A) vs facilitating (D) | STD (events) vs STF (bursts) |
| Inhibitory role | Not modeled | SST+ interneurons linearize burst probability |
| Feedback alignment | Assumes symmetric weights (via apical Hebbian) | Learned via burst-dependent rule |
| Scale | X-OR | CIFAR-10, ImageNet |
| Self-supervised variant | Yes (Imax coherence) | Not demonstrated |

The 2001 paper proves the architectural move works in principle; Payeur 2020 provides the biophysically detailed implementation, the scale, and the falsifiable predictions (STP polarization, burst variance).

## Connections to Existing Knowledge

- **[[Credit Assignment]]**: This is the first proposal that the burst/spike distinction + dendritic compartmentalization could implement gradient-based credit assignment in cortex. The 2001 paper is the conceptual seed; [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] is the mature implementation.
- **[[Dendritic Computation]]**: Argues that the apical dendrite's role is not just integrating input but **carrying a distinct computational variable** — the learning signal. This is the theoretical origin of the "two compartments for two purposes" framing.
- **[[Hebbian Learning]]**: The burst-gated plasticity rule (ΔW ∝ D_post × A_pre) is Hebbian — it depends only on local pre/post variables — but the "post" variable is enriched by dendritic computation to carry error information. This is the conceptual bridge between Hebbian locality and gradient-based learning, made explicit 19 years before Payeur et al.
- **[[Synapses]]**: First proposal that STP type distribution (facilitating vs depressing) serves as a signal multiplexing mechanism, not just a transmission property.
- **[[Action Potential]]**: The burst vs. single spike distinction is reframed as carrying two distinct information channels over the same axon — activity and error — made possible by the BAC firing mechanism (Larkum et al. 1999).

## Open Questions Raised

- Can the self-supervised variant (Imax-style coherence across streams) be implemented with the full spiking/STP machinery of Payeur et al. (2020)? The 2001 paper proves the principle; the modern spiking implementation remains undone.
- What is the actual transfer function D = g(apical input, A) in vivo? The backprop implementation requires D ∝ A(1 - A) — the sigmoid derivative — which is a strong biophysical assumption. The shape of the BAC firing response curve is incompletely characterized.
- The paper assumes that calcium spike generation is continuous (probabilistic). How does the discrete, all-or-nothing character of dendritic calcium spikes affect the gradient computation? Is stochastic bursting (noisy threshold) sufficient for the statistics to produce a useful gradient signal?

## Sources

Kording, K.P. & Konig, P. (2001). Supervised and Unsupervised Learning with Two Sites of Synaptic Integration. *Journal of Computational Neuroscience*, 11, 207-215.
