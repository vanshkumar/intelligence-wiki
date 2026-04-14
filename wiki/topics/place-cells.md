---
title: "Place Cells"
type: concept
aliases: ["place fields", "hippocampal place cells"]
tags: [hippocampus, spatial-coding, navigation, memory]
source_count: 2
last_updated: 2026-04-14
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

## Place-Field Size Gradient as Cell-Type Signature

[[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] propose a mechanistic account of the place-field size gradient: different hippocampal cell populations may correspond to different functional roles in the [[Endotaxis]] circuit, with place-field size determined by position in the circuit.

- **Point cells** (smallest fields) — local position encoders; feed the map layer
- **Map cells** (medium fields) — recurrently connected; learn environment connectivity via Hebbian coincidence; pool activity over neighborhoods in the graph
- **Goal cells** (very large fields) — converge over much of the environment; represent proximity to tagged locations

This matches Kjelstrup et al. (2008)'s observed 10× field-size gradient along the septotemporal axis, and the reports of goal-cell-like very-large-field cells in rat cortex (Hok et al. 2005). The endotaxis model also predicts **sudden single-event place-field formation** for goal cells — consistent with Bittner et al. (2017)'s observation of calcium-plateau-driven CA1 place-field emergence.

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — place field size gradient interacts with travelling wave for segment encoding
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — mechanistic account of the place-field size gradient as cell-type signature in an endotaxis circuit
