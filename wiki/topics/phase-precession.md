---
title: "Phase Precession"
type: mechanism
aliases: ["theta phase precession"]
tags: [hippocampus, theta-oscillations, spatial-coding, place-cells, spike-timing]
source_count: 1
last_updated: 2026-04-10
level: cellular
---

Phase precession is a phenomenon in the [[Hippocampus]] where a [[Place Cells|place cell's]] firing shifts to progressively earlier phases of the local [[Theta Oscillations|theta cycle]] as the animal moves through the cell's place field. It converts spatial position into a spike timing code.

## Mechanism

When an animal enters a place cell's field, the cell first fires near the trough (late phase) of theta. As the animal traverses the field, each successive theta cycle sees the cell fire at an earlier phase. By the time the animal exits the field, the cell fires near the peak (early phase). The phase of firing within a theta cycle thus encodes how far the animal has progressed through that cell's place field.

Key point: phase precession is measured relative to the **local** theta oscillation at the neuron's septotemporal level, not a global reference. This distinction becomes critical when theta is a travelling wave.

## Interaction with Theta Travelling Waves

[[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] showed that the travelling wave structure of theta gives phase precession a spatial dimension across the hippocampal axis:

- Under **synchronized theta**, all septotemporal levels share the same local phase → phase precession maps them all to the same position → hippocampal output encodes a **point**
- Under a **travelling wave**, each septotemporal level is at a different local phase → phase precession maps each to a different position → hippocampal output encodes a **segment**

This means phase precession is not just a temporal code at one location but a **spatiotemporal code** across the hippocampal axis.

## Causal Relevance

Optogenetic stimulation replicating theta phase precession patterns produced stronger sharp-wave ripple reactivation and more stable place fields than random-phase stimulation (2023), establishing that the phase-position relationship is causally important for memory consolidation.

Entorhinal layer III input manipulation (2025) showed that phase precession slope/range and theta sequences are dissociable — disrupting entorhinal input impaired phase precession but paradoxically strengthened theta sequences.

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — phase precession + travelling wave = segment encoding
