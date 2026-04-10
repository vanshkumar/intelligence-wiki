---
title: "Neural Adaptation"
type: mechanism
aliases: ["sensory adaptation", "firing rate adaptation", "spike-frequency adaptation"]
tags: [encoding, dynamic-range, sensory-processing, rate-coding]
source_count: 2
last_updated: 2026-04-10
level: cellular
---

Neural adaptation is the phenomenon where neurons adjust their input-output relationship over time, encoding **relative changes** rather than absolute stimulus values. Discovered by Edgar Adrian as one of three universal features of neurons ([[bennett-2023-history-intelligence-ch1|Bennett, 2023]]).

## The Problem It Solves

Natural stimulus variables span enormous ranges — light intensity varies a million-fold from starlight to sunlight, pressure on skin varies across orders of magnitude. But neural firing rates cap at ~500 Hz. Without adaptation, neurons would saturate at high intensities and be silent at low ones, wasting most of their dynamic range.

Adaptation solves this by **remapping**: the neuron continuously adjusts its sensitivity so that the current operating range maps onto the full firing rate range. The result is that neurons encode **deviations from the recent baseline**, not the absolute stimulus level.

## Biophysical Mechanisms

Several ion channel mechanisms produce adaptation at different timescales ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]):

- **I_M** (muscarinic K⁺ current): Slow negative feedback at spiking voltages. Accumulates across spikes, progressively hyperpolarizing the membrane and reducing firing rate. Produces **spike-frequency adaptation** — the same sustained input elicits progressively fewer spikes.
- **I_K[Ca]** (calcium-dependent K⁺ current): Adaptation gated by intracellular calcium concentration rather than voltage directly. Calcium accumulates during spiking and activates K⁺ channels. When calcium is pumped out, the effect vanishes — calcium IS the memory (transient, unlike calcium's role in synaptic plasticity).
- **Na⁺ inactivation (h)**: The fast inactivation of sodium channels during sustained depolarization contributes to short-timescale adaptation and refractoriness.

## Computational Significance

Adaptation predates neurons — bacterial chemotaxis uses the same principle (encoding temporal gradients of chemical concentration rather than absolute levels). In neurons, it serves several functions:

- **Dynamic range compression** — maps the relevant stimulus range onto the available firing rate range
- **Change detection** — responses emphasize stimulus onsets, offsets, and transitions over static states
- **Temporal decorrelation** — removes slow correlations in input, highlighting the informative (changing) parts

## Relationship to Other Concepts

- **[[Predictive Coding]]**: Adaptation is conceptually related to prediction error signaling — encoding deviations from a baseline is structurally similar to encoding prediction errors. However, adaptation is a single-neuron mechanism operating on temporal statistics, while predictive coding is a network-level theory about hierarchical prediction.
- **[[Divisive Normalization]]**: Related but distinct. Adaptation is temporal (responses decrease over time to sustained input). Normalization is spatial/population (responses scale relative to other neurons' activity). Both serve gain control but operate on different axes.
- **[[Neural Noise]]**: Adaptation affects signal-to-noise properties by concentrating the neuron's dynamic range around the current operating point.

## Sources

- [[bennett-2023-history-intelligence-ch1|Bennett (2023), Ch. 1]] — Adrian's discovery of adaptation as a universal neuronal feature
- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — biophysical mechanisms of adaptation (I_M, I_K[Ca])
