---
title: "Synapses"
type: concept
aliases: ["synapse", "synaptic transmission", "synaptic connection"]
tags: [neuron, plasticity, learning, hebbian-learning, evolution]
source_count: 4
last_updated: 2026-04-10
confidence: established
---

A synapse is the junction between two neurons where signals are transmitted, typically via chemical neurotransmitter release. It is the physical substrate for [[Hebbian Learning]] and arguably the most important computational innovation of the nervous system.

## Why Synapses Matter for Learning

The synapse is the only known biological structure where **two specific cells' activity states converge and connection strength can be modified based on their joint activity** ([[bennett-2023-history-intelligence-ch1|Bennett, 2023]]). This is the physical prerequisite for any form of associative learning:

- **Pre-synaptic neuron** releases neurotransmitter when it fires
- **Post-synaptic neuron** responds based on its receptor complement
- **Synaptic strength** can be modified based on the correlation between pre and post activity — the basis of [[Hebbian Learning]]

No known non-neural system has true pairwise activity-dependent plasticity. Physarum slime mold flow networks were examined as a candidate but found to respond to local flow magnitude, not correlated activity of two connected nodes.

## Computational Primitives

Synapses implement several computational operations:

**Excitatory transmission**: Neurotransmitter (typically glutamate) depolarizes the post-synaptic neuron, increasing its probability of firing. Excitatory synapses enable signal propagation and association.

**Inhibitory transmission**: Neurotransmitter (typically GABA) hyperpolarizes or shunts the post-synaptic neuron, decreasing its probability of firing. Inhibition enables:
- Competitive dynamics for [[Sparse Coding]] (winner-take-all)
- [[Divisive Normalization]] (gain control via shunting inhibition)
- Coordinated motor control ("do this, not that")
- Temporal structuring of activity

**Coincidence detection**: The NMDA receptor requires both pre-synaptic glutamate AND post-synaptic depolarization to open, passing calcium. This makes it a molecular coincidence detector for correlated activity — the biophysical implementation of Hebbian coincidence ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]).

## Synaptic Plasticity

Connection strength is not fixed — it changes based on activity patterns:

- **Long-term potentiation (LTP)**: Sustained strengthening following correlated pre/post activity. Triggered by calcium influx through NMDA receptors.
- **Long-term depression (LTD)**: Sustained weakening following uncorrelated or anti-correlated activity.
- **Spike-timing-dependent plasticity (STDP)**: The precise timing of pre and post spikes determines the direction and magnitude of change.

The calcium-as-trigger mechanism ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]) is what makes synaptic changes lasting: calcium initiates self-sustaining downstream cascades (CaMKII phosphorylation, structural modification) that persist after calcium is removed. Genetically encoded downstream proteins determine whether a calcium signal produces transient or lasting change.

## Short-Term Plasticity and Signal Multiplexing

Beyond lasting changes in connection strength, synapses exhibit **short-term plasticity (STP)** — transient, activity-dependent changes in transmission efficacy on timescales of milliseconds to seconds. Two forms are computationally significant:

- **Short-term depression (STD)**: Repeated presynaptic activity depletes vesicles, reducing transmission. STD acts as a high-pass filter, preferentially transmitting the **onset** or **rate** of presynaptic activity rather than sustained firing.
- **Short-term facilitation (STF)**: Repeated presynaptic activity builds up residual calcium in the terminal, increasing release probability. STF acts as a low-pass filter, preferentially transmitting **sustained** or **high-frequency** activity.

[[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] show that the differential distribution of STP types across synapse classes enables **signal multiplexing** in cortical circuits: feedforward (bottom-up) synapses exhibit predominantly STD, transmitting **event rate** (the neuron's sensory representation), while feedback (top-down) synapses exhibit predominantly STF, transmitting **burst rate** (the [[Credit Assignment|credit signal]] from higher areas). This allows a single pyramidal neuron ensemble to simultaneously carry both its feedforward representation and the top-down teaching signal, separated by STP type and [[Dendritic Computation|dendritic compartment]].

The STP polarization prediction — STD feedforward, STF feedback along the sensory hierarchy — is a key falsifiable prediction of the burst-dependent credit assignment framework.

## Multi-Synaptic Boutons

A single presynaptic axon can contact the same postsynaptic neuron at **multiple points** on different dendritic branches — structures called multi-synaptic boutons (MSBs). Electron microscopy shows ~4 presynaptic axon synapses per postsynaptic neuron on average (Kincaid et al. 1998), and MSBs occur ~11.5% of the time in rats in enriched environments (Jones et al. 1997). Critically, **LTP increases MSBs 6-fold** (Toni et al. 1999) — learning actively replicates synaptic contacts.

[[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] show that repeated synaptic inputs across dendritic branches directly increase a neuron's computational capacity — modeling repeated inputs as a *k*-tree, performance monotonically improves with *k* and approaches a parameter-matched fully connected network. This reframes MSBs not as redundancy but as a mechanism by which learning **grows the computational architecture** of individual neurons.

## Evolutionary Significance

Individual computational primitives (excitation, inhibition, thresholding, adaptation) all predate neurons — they exist in unicellular signaling cascades. What neurons added was the **network architecture** (massive fan-in/fan-out, reconfigurable graph) and the synapse's unique capacity for pairwise activity-dependent modification. The synapse is what makes networks **learnable**, not just configurable.

Evolutionary biologists identify a bundle of synaptic innovations — speed, spatial precision, scalability, and activity-dependent plasticity — rather than any single property as the key advance.

## Sources

- [[bennett-2023-history-intelligence-ch1|Bennett (2023), Ch. 1]] — synapse as the key computational novelty of neurons
- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — NMDA coincidence detection, calcium-plasticity bridge
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — STP multiplexing: STD at feedforward synapses transmits event rate, STF at feedback synapses transmits burst rate
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — multi-synaptic boutons as computational architecture; LTP-induced MSBs increase single-neuron capacity
