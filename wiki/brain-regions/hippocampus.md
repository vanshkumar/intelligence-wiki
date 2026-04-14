---
title: "Hippocampus"
type: brain-region
aliases: ["hippocampal formation", "HPC"]
tags: [limbic-system, memory, spatial-navigation, theta, learning]
source_count: 3
last_updated: 2026-04-14
---

The hippocampus is a bilateral structure in the medial temporal lobe critical for spatial navigation, episodic memory formation, and learning. It is one of the most studied brain regions in neuroscience and a primary site for investigating biological learning mechanisms.

## Anatomy

### Subfields

- **CA1** — the primary output region; receives input from CA3 and entorhinal cortex. Contains [[Place Cells]] with spatially tuned firing fields.
- **CA3** — a recurrent network with extensive connections between its own neurons. Proposed as a site for pattern completion and associative memory. Its recurrent connections can propagate activity pulses at ~0.1–0.15 m/s.
- **Dentate gyrus** — receives input from entorhinal cortex; proposed role in pattern separation.
- **Subiculum** — output region projecting to cortical and subcortical targets.

### Laminar Structure

Within CA1, distinct layers have different electrophysiological properties:
- **Stratum oriens** — theta phase is depth-invariant (~400 μm), making it ideal for measuring lateral phase organization ([[lubenov-2009-theta-travelling-waves|Lubenov & Siapas, 2009]])
- **Stratum pyramidale** — the pyramidal cell layer; theta phase reversal occurs here
- **Stratum radiatum** — steep theta phase gradient with depth, making lateral phase measurements unreliable

### Septotemporal Axis

The hippocampus has a long axis running from the septal (dorsal) pole to the temporal (ventral) pole. Key gradients along this axis:
- **Place field size** increases from septal (small, fine resolution) to temporal (large, coarse resolution)
- **[[Theta Oscillations]]** propagate as a travelling wave from septal → temporal at ~80–107 mm/s
- In humans, the equivalent axis runs posterior → anterior (due to evolutionary rotation)

## Theta Oscillations and Travelling Waves

[[Theta Oscillations]] (4–10 Hz) are prominent in the hippocampal LFP during active exploration and REM sleep. Previously assumed to be synchronized across the hippocampus, [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] showed they are actually **travelling waves** propagating along the septotemporal axis.

The travelling wave's spatial wavelength (~11–15 mm) matches the hippocampal length, giving each septotemporal position a unique theta phase. Combined with [[Phase Precession]], this means the hippocampus instantaneously represents a **segment** of space rather than a single point.

## Role in Learning and Memory

The hippocampus extends the sensorimotor control loop's temporal and spatial reach. Where basic control operates on the immediate sensory present, hippocampal circuits enable the organism to act on spatial context (where am I relative to where I've been?) and recent episodic history (what happened here before?).

The hippocampus is central to:
- **Spatial memory** — encoding and retrieving spatial maps via place cells, giving the control loop access to allocentric spatial structure beyond the current sensory view
- **Episodic memory** — forming memories of specific events in context, extending control over contingencies that require remembering unique past episodes
- **[[Memory Consolidation]]** — transferring information to cortical long-term storage (systems consolidation), involving sharp-wave ripples during sleep and rest. [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] show that during SWS, CA1 cells fire 0-100 ms before [[Prefrontal Cortex|mPFC]] cells in an SWR-driven, directional pattern — timing compatible with spike-timing-dependent [[Long-Term Potentiation|plasticity]]. These interactions are nearly abolished during REM sleep, suggesting distinct consolidation mechanisms across sleep stages.

## Candidate Algorithm: Endotaxis

[[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] propose that the hippocampus implements [[Endotaxis]] — a circuit that computes an internal "virtual odor" signal monotonic in graph distance to a chosen target, then feeds it into the ancient chemotaxis controller. In this view, the [[Place Cells|place-field size gradient]] along the septotemporal axis reflects functional differentiation: small-field point cells for location encoding, medium-field map cells for learned connectivity, and very-large-field goal cells for target proximity. The circuit motif — sparse place-selective population → convergent Hebbian readout — is the same motif realized in the insect [[Mushroom Body]], suggesting a shared computational solution for cognitive navigation across deeply divergent lineages.

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — theta oscillations are travelling waves along the septotemporal axis
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — SWR-driven directional spike timing from CA1 to mPFC during SWS
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — endotaxis as candidate computation for hippocampal cognitive navigation
