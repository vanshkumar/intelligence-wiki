---
title: "Hippocampal Theta Oscillations Are Travelling Waves"
type: source
source_type: paper
authors:
  - "Evgueniy V. Lubenov"
  - "Athanassios G. Siapas"
year: 2009
doi: "10.1038/nature08010"
tags: [hippocampus, theta-oscillations, travelling-waves, spatial-coding, electrophysiology]
date_ingested: 2026-04-10
key_finding: "Theta oscillations in CA1 are travelling waves propagating along the septotemporal axis, implying the hippocampus encodes a spatial segment rather than a single point."
---

## Overview

This paper overturns the prevailing view that [[Theta Oscillations]] are synchronized across the [[Hippocampus]]. Using multielectrode recordings from stratum oriens of CA1 in freely behaving rats, Lubenov & Siapas show that theta oscillations are **travelling waves** propagating roughly along the septotemporal axis. The wave's spatial wavelength (~11–15 mm) is commensurate with the hippocampal length, meaning each septotemporal position gets a unique theta phase. Combined with [[Phase Precession]], this implies the hippocampus instantaneously represents a **segment** of physical space, not a point.

[PDF](../../raw/papers/lubenov-2009.pdf) | [Transcript](../../raw/papers/lubenov-2009.md)

## Key Findings

**1. Theta oscillations are travelling waves.** Phase differences across recording sites in stratum oriens of CA1 are systematic, not random. The phase gradient is ~21°/mm, propagation speed ~80–107 mm/s, wavelength ~11–15 mm, and predominant direction is septal → temporal along the septotemporal axis.

**2. Wavelength matches hippocampal length.** This is functionally significant: one wavelength ≈ one hippocampal length means each septotemporal position maps to a unique theta phase. If the wavelength were much shorter, multiple positions would share the same phase (degenerate map). If much longer, phase differences would be too small to be useful.

**3. Spiking waves match LFP waves.** The travelling wave isn't just an LFP artifact — spiking activity of CA1 pyramidal cells is also modulated as a travelling wave consistent with the LFP pattern. This was confirmed by recording at the pyramidal cell layer.

**4. Segment encoding via travelling wave + phase precession.** Under synchronized theta, all septotemporal levels share the same local theta phase, so [[Phase Precession]] maps them all to the same point in space — a **point** representation. Under a travelling wave, each septotemporal level is at a different local phase at any instant, so phase precession maps each to a different point — a **segment** representation. The time zone analogy: it's noon in New York while 9am in LA; different septotemporal levels are "doing their noon activity" at different moments.

**5. Place field size gradient adds resolution structure.** Place field size increases along the septotemporal axis (small fields septally, large temporally). Combined with the travelling wave, within each theta cycle the hippocampal output sweeps from fine to coarse spatial resolution.

## Methods

**Key methodological insight:** Recordings were made in **stratum oriens** specifically because theta phase is depth-invariant there (~400 μm range). In stratum radiatum, theta phase has a steep depth gradient — small electrode depth errors between sites would mimic lateral phase differences, confounding the travelling wave measurement.

**Recording setup:** Multielectrode arrays targeting stratum oriens of CA1, with 24 tetrodes and 4 single reference electrodes. 4×8 grid spanning ~5 mm² of hippocampus. Rats ran on a linear track.

**Analysis:** Instantaneous phase differences computed between each grid location and a reference tetrode. Phase gradient fitted with a plane at each time point. Wave parameters (direction, speed, wavelength) extracted from the fitted planes.

**Two-stage chronic electrode array experiments:** Phase 1 confirmed depth in stratum oriens; phase 2 recorded during behavior.

## Implications

**For hippocampal computation:**
- The hippocampus is topographically organized not just in space but in **time** — theta phase maps onto the septotemporal axis, creating an instantaneous spatial readout.
- Travelling waves may be necessary (not just present) for maintaining a consistent phase code, given that place field sizes vary along the septotemporal axis (theoretical work, 2017).
- The distinction between point and segment encoding has consequences for downstream readout — targets receiving hippocampal output could potentially extract position, direction, and spatial context from the phase-structured activity.

**For understanding neural oscillations broadly:**
- Oscillations that appear synchronized at coarse measurement may be travelling waves at fine spatial resolution. This challenges interpretations of coherence/synchrony across brain regions.
- Travelling waves in cortex have since been found across sensory, motor, and cognitive systems (Nature Reviews Neuroscience, 2018).

**Open causal question:** No experiment has specifically disrupted the travelling wave property while preserving theta itself. Existing work (theta scrambling, phase-specific inhibition) establishes that theta and theta phase matter, but not whether the spatial propagation is computationally necessary. The experiment — imposing synchronous theta across the septotemporal axis — would require independent phase control at multiple sites simultaneously.

## Proposed Wave Generation Mechanisms

The paper proposes three (likely co-contributing) mechanisms:

1. **Delayed excitation from a single oscillator** — the medial septum, whose projections are topographically organized along the septotemporal axis with different transmission delays
2. **Propagation in an excitable network** — CA3 recurrent connections, where disinhibited slices show pulse propagation at ~0.1–0.15 m/s matching the observed wave speed
3. **Frequency gradient in coupled oscillators** — entorhinal cortex neurons have intrinsic theta-range frequencies that decrease dorso-ventrally; faster oscillators lead in phase, producing a travelling wave

## Connections to Existing Knowledge

- **[[Theta Oscillations]]**: This paper fundamentally reframes the spatial structure of hippocampal theta — from synchronized clock to travelling wave with computational implications.
- **[[Phase Precession]]**: The travelling wave gives phase precession a new dimension — it's no longer just a temporal code at one location, but a spatiotemporal code across the hippocampal axis.
- **[[Place Cells]]**: Place field properties (location, size) interact with the travelling wave to produce the segment representation. The septotemporal gradient in field size adds resolution structure.
- **[[Hippocampus]]**: Establishes the hippocampus as representing a spatial segment rather than a point, with the septotemporal axis as a key organizational dimension.

## Open Questions Raised

- Is the travelling wave property **causally necessary** for spatial behavior, or would synchronized theta work just as well?
- What is the computational advantage of segment over point encoding? Does the segment representation support planning, prediction, or multi-scale spatial reasoning?
- How does the travelling wave interact with sharp-wave ripples and memory consolidation?
- Are travelling waves a general principle of hippocampal computation, or specific to theta during active exploration?

## Follow-Up Work

- **Patel et al. (2012)**: Confirmed travelling waves along the full septotemporal axis
- **Zhang & Jacobs (2015)**: Confirmed in humans (posterior → anterior propagation)
- **Entorhinal cortex (2020, eLife)**: Medial entorhinal cortex also activates as a travelling wave
- **Phase code consistency (2017)**: Theoretical work showing the travelling wave is necessary for a consistent phase code given variable place field sizes
