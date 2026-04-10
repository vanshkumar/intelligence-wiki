---
title: "Place Cells"
type: concept
aliases: ["place fields", "hippocampal place cells"]
tags: [hippocampus, spatial-coding, navigation, memory]
source_count: 1
last_updated: 2026-04-10
confidence: established
---

Place cells are neurons in the [[Hippocampus]] (primarily CA1 and CA3) that fire when an animal occupies a specific location in its environment — the cell's **place field**. Discovered by John O'Keefe in 1971, they are the foundation of the hippocampal spatial map.

## Place Field Properties

- **Location selectivity**: Each place cell has a preferred spatial location where it fires maximally
- **Size gradient**: Place field size increases along the septotemporal axis — small fields septally (fine resolution), large fields temporally (coarse resolution). This gradient interacts with the theta travelling wave to produce a multi-resolution spatial representation ([[lubenov-2009-theta-travelling-waves|Lubenov & Siapas, 2009]])
- **Remapping**: Place fields can remap when the environment changes, providing distinct spatial representations for different contexts

## Spike Timing and Phase Precession

Place cells don't just encode position through firing rate — their spike timing relative to the local [[Theta Oscillations|theta cycle]] carries additional information via [[Phase Precession]]. A place cell's firing shifts to progressively earlier theta phases as the animal traverses its field, converting position-within-field into a phase code.

## Interaction with Theta Travelling Waves

At any given septotemporal level, only place cells whose fields overlap the animal's current position are active. The travelling wave structure of theta means different septotemporal levels are at different local theta phases simultaneously. Combined with phase precession and the place field size gradient, this produces an instantaneous hippocampal output that sweeps from fine to coarse spatial resolution within each theta cycle.

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — place field size gradient interacts with travelling wave for segment encoding
