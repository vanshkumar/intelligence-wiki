---
title: "Place Cells"
type: concept
aliases: ["place fields", "hippocampal place cells"]
tags: [hippocampus, spatial-coding, navigation, memory]
source_count: 4
last_updated: 2026-04-29
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

## Methodological Caveat: tuning ≠ computational role

Place-field tuning is a paradigm case of inferring computational role from observed selectivity — a place cell with a tight field at position `(x, y)` is taken to represent that position. [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] caution that tuning, generally, is not a clean inversion: in their microprocessor experiment, several transistors showed strong simple- or complex-tuning to pixel luminance, yet were not directly involved in luminance computation — they were upstream or downstream of nonlinearly related quantities, with apparent tuning arising from game-stage statistics. The general claim: a unit can compute something, be upstream of something, be downstream of something, or be entirely orthogonal to something and still show strong apparent tuning to that quantity. For place cells, this is partially mitigated by the [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis circuit-level account]], which makes a constructive proposal for how the tuning arises mechanistically (point/map/goal cells with specific connectivity) — going beyond "this cell is tuned to position" to a mechanism that generates the tuning. The chip warning sharpens the standard required for tuning-based inferences in spatial coding: a constructive mechanism that *generates* the tuning is what distinguishes a computational claim from a correlational one.

## Coding Caveat: "encoding location" is a correspondence claim, not a representational one

[[brette-2018-coding-metaphor|Brette (2018)]] sharpens the methodological caution further. The claim that place cells "encode location" is a *correspondence claim with experimental scope*: under the conditions of the experiment (animal in a defined arena, position tracked from outside, neural activity recorded), place-cell firing rate covaries with position. This is the technical sense of [[neural-coding|coding]]. It does not entail that the cell *represents* location to the brain in any sense the brain has access to — the brain does not have an external observer's view of "the animal at position (x, y)." What the brain has is the lawful covariation between place-cell activity, theta phase, head direction signals, vestibular signals, locomotor signals, and the actions the animal is taking. Position, for the brain, is the manipulable structure of these covariances — closer to [[subjective-physics|subjective physics]] than to coding-style representation.

The [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis circuit-level account]] is broadly consistent with this reading: map cells learn the *adjacency structure* of the environment (a relation among place activations and movements), and goal cells imprint on this relational structure. The mechanism is closer to learning sensorimotor laws than to encoding spatial coordinates. Brette's critique therefore does not undermine the empirical observations about place cells; it recontextualizes their interpretation: "place cells encode location" should be read as "place-cell firing covaries with position under the conditions of the experiment," with the underlying mechanism being relational learning of sensorimotor structure rather than spatial coordinate representation.

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — place field size gradient interacts with travelling wave for segment encoding
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — mechanistic account of the place-field size gradient as cell-type signature in an endotaxis circuit
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — methodological caution that tuning curves do not, by themselves, reveal computational role; constructive mechanistic accounts of tuning are required to support computational claims
- [[brette-2018-coding-metaphor|Brette (2018)]] — coding caveat: "place cells encode location" is a correspondence claim with experimental scope; the brain has only lawful covariations among place activations, head direction, vestibular signals, and actions, not access to "the animal at (x, y)." Position, for the brain, is the manipulable structure of these covariances.
