---
title: "Theta Oscillations"
type: mechanism
aliases: ["theta rhythm", "hippocampal theta", "theta waves"]
tags: [oscillations, hippocampus, spatial-navigation, memory, electrophysiology]
source_count: 1
last_updated: 2026-04-10
level: circuit
---

Theta oscillations are 4–10 Hz rhythmic fluctuations in the local field potential (LFP) of the [[Hippocampus]], prominent during active exploration, locomotion, and REM sleep. They strongly modulate the spiking of hippocampal neurons and are thought to play a key role in spatial coding, memory, and temporal organization of neural activity.

## Spatial Structure: Travelling Waves

The prevailing view prior to 2009 was that theta oscillations are synchronized across the hippocampus. [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] overturned this, showing that theta oscillations in CA1 are **travelling waves** propagating along the septotemporal axis:

- **Phase gradient**: ~21°/mm
- **Propagation speed**: ~80–107 mm/s
- **Wavelength**: ~11–15 mm (commensurate with hippocampal length)
- **Direction**: predominantly septal → temporal

The wavelength matching the hippocampal length is functionally significant: each septotemporal position gets a unique theta phase, creating an unambiguous topographic map.

## Interaction with Phase Precession

[[Phase Precession]] relates a neuron's firing phase (within the local theta cycle) to the animal's position within that neuron's place field. The travelling wave adds a critical dimension:

- **Synchronized theta** → all septotemporal levels at the same local phase → phase precession maps them to the same point → **point** representation
- **Travelling wave** → each septotemporal level at a different local phase → phase precession maps each to a different point → **segment** representation

Phase precession is measured relative to the **local** theta oscillation at each neuron's septotemporal level. The travelling wave ensures these local references are staggered in time, like time zones.

## Generation Mechanisms

Three mechanisms likely co-contribute to generating the travelling wave:

1. **Medial septum** — topographically organized projections with different transmission delays along the septotemporal axis
2. **CA3 recurrent network** — excitable network propagation at ~0.1–0.15 m/s, matching observed wave speed
3. **Entorhinal cortex** — intrinsic oscillation frequencies decrease dorso-ventrally; a frequency gradient in coupled oscillators naturally produces a travelling wave (faster oscillators lead in phase)

## Functional Roles

- **Temporal organization**: Theta provides a reference clock for spike timing codes ([[Phase Precession]], theta sequences)
- **Spatial coding**: The travelling wave enables segment (not point) encoding of position
- **Memory**: Theta phase is causally relevant — scrambling theta regularity impairs working memory (Etter et al. 2023), and phase-specific inhibition dissociates external-cue vs internal-cue navigation (Siegle & Wilson 2014)
- **Communication**: Theta coherence between hippocampus and other regions (prefrontal cortex, entorhinal cortex) is thought to coordinate information flow

## Open Questions

- Is the travelling wave property **causally necessary** for spatial behavior?
- How does the travelling wave interact with sharp-wave ripples during memory consolidation?
- Are travelling waves present in non-spatial hippocampal computations?

## Sources

- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — theta as travelling wave, segment encoding
