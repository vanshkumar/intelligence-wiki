---
title: "Neuronal Dynamics — Chapter 1: Introduction: Neurons and Mathematics"
type: source
source_type: book
authors:
  - "Wulfram Gerstner"
  - "Werner M. Kistler"
  - "Richard Naud"
  - "Liam Paninski"
year: 2014
doi: ""
tags: [biophysics, neuron-models, integrate-and-fire, shunting-inhibition, divisive-normalization, dynamical-systems]
date_ingested: 2026-04-10
key_finding: "Even the simplest neuron model (leaky integrate-and-fire) reveals the membrane as an RC circuit; conductance-based inhibition can implement divisive normalization, a canonical neural computation."
---

## Overview

Chapter 1 introduces the mathematical foundations of single-neuron modeling, progressing from the ideal spiking neuron concept through the leaky integrate-and-fire (LIF) model to conductance-based extensions. The chapter establishes that a neuron is fundamentally an RC circuit below threshold, with the only nonlinearity being the spike-and-reset mechanism — but that this simplicity hides important limitations (no adaptation, bursting, or subthreshold oscillations) that motivate the Hodgkin-Huxley framework in Chapter 2.

The most computationally significant result in this chapter is the derivation of **shunting inhibition** as the biophysical basis for [[Divisive Normalization]].

[PDF](../../raw/books/neuronal_dynamics/chunk-1.pdf) | [Transcript](../../raw/books/neuronal_dynamics/chunk-1-transcript.md) | [Intuition Transcript](../../raw/books/neuronal_dynamics/chunk-1-intuition-transcript.md)

## Key Findings

### The Leaky Integrate-and-Fire Model

The simplest mathematical neuron: membrane as capacitor (charge storage), ion channels as resistor (leak), resting potential as battery. The membrane potential follows:

$$\tau_m \frac{du}{dt} = -(u - u_{rest}) + RI(t)$$

Below threshold the model is **linear** — the membrane passively integrates incoming currents with exponential decay (time constant τ_m = RC). When voltage reaches a threshold, a spike is emitted as a point event and voltage resets. This threshold-and-reset is the only nonlinearity.

The RC circuit analogy is physically grounded: the lipid bilayer is a literal dielectric (capacitor), leak channels are literal conductances (resistor), and the Nernst potential provides the voltage source (battery).

### Limitations of LIF

The model cannot produce:
- **Adaptation** — firing rate decrease during sustained input (requires slow negative feedback)
- **Bursting** — clusters of spikes followed by silence (requires additional slow variables)
- **Inhibitory rebound** — spiking after release from inhibition (requires specific channel types)
- **Subthreshold oscillations** — voltage fluctuations below threshold (requires resonant dynamics)

All of these require additional state variables beyond membrane voltage, motivating the full Hodgkin-Huxley treatment.

### Shunting Inhibition and Divisive Normalization

The chapter's most important computational result. When inhibition is modeled as a conductance (not just a current), its effect depends on circuit topology and reversal potential:

**Subtractive inhibition**: Off-path inhibition, or inhibition with reversal potential far from rest. Shifts the input-output curve laterally — subtracts a constant from the effective input.

**[[Divisive Normalization|Divisive (shunting) inhibition]]**: Requires **two conditions simultaneously**:
1. The inhibitory synapse must be **on-path** between excitatory input and spike initiation zone
2. The inhibitory reversal potential must be **near the resting potential** (E_i ≈ V_rest)

When both hold, the inhibitory conductance g_i appears only in the **denominator** of the steady-state signal equation — it scales the gain of the excitatory drive. The signal becomes proportional to g_e / (g_leak + g_i), where g_e is excitatory conductance. This compresses the input-output curve proportionally rather than shifting it, preserving discriminability across the full operating range.

When E_i drifts from V_rest, a subtractive component appears in the numerator — the division becomes impure.

## Implications

- The LIF model, despite its simplicity, captures the essential integration-and-threshold logic of neural computation. It explains why synaptic inputs sum and decay, and why timing of inputs matters (temporal integration).
- [[Divisive Normalization]] via shunting inhibition is recognized as a **canonical neural computation** appearing across sensory systems (retina, V1, auditory cortex). Its biophysical substrate is simple — conductance-based inhibition with appropriate placement and reversal potential.
- The chapter frames the neuron as a dynamical system, setting up the key insight developed in Chapter 2: all interesting neural dynamics arise from variables being out of equilibrium.

## Connections to Existing Knowledge

- **[[Divisive Normalization]]**: This chapter provides the biophysical derivation of how inhibition implements gain control
- **[[Sparse Coding]]**: Divisive normalization shapes how many neurons respond to a given stimulus and at what rates — directly relevant to maintaining sparse representations
- **[[Predictive Coding]]**: Normalization could implement prediction error scaling, adjusting error signal gain based on context
- **[[Hebbian Learning]]**: The LIF model is the substrate on which synaptic inputs are integrated; understanding integration clarifies what signals are available to drive plasticity

## Open Questions Raised

- Where does the membrane-as-RC-circuit analogy break down? (Addressed in Chapter 2: ions carry chemical identity, not just charge)
- How do the limitations of LIF (no adaptation, bursting, oscillations) affect network-level computation and learning?

## Sources

Textbook chapter. Two transcript sessions: one systematic walkthrough, one focused on building physical intuition for shunting inhibition and the RC circuit analogy.
