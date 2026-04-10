---
title: "Synapses"
type: concept
aliases: ["synapse", "synaptic transmission", "synaptic connection"]
tags: [neuron, plasticity, learning, hebbian-learning, evolution]
source_count: 2
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

## Evolutionary Significance

Individual computational primitives (excitation, inhibition, thresholding, adaptation) all predate neurons — they exist in unicellular signaling cascades. What neurons added was the **network architecture** (massive fan-in/fan-out, reconfigurable graph) and the synapse's unique capacity for pairwise activity-dependent modification. The synapse is what makes networks **learnable**, not just configurable.

Evolutionary biologists identify a bundle of synaptic innovations — speed, spatial precision, scalability, and activity-dependent plasticity — rather than any single property as the key advance.

## Sources

- [[bennett-2023-history-intelligence-ch1|Bennett (2023), Ch. 1]] — synapse as the key computational novelty of neurons
- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — NMDA coincidence detection, calcium-plasticity bridge
