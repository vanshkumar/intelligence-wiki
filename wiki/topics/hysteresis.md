---
title: "Hysteresis"
type: mechanism
aliases: ["bistability", "bistable hysteresis", "neural hysteresis"]
tags: [dynamical-systems, bistability, short-term-memory, attractor, cortical-dynamics]
source_count: 1
last_updated: 2026-04-18
level: circuit
---

**Hysteresis** in a neural population is the presence of two (or more) stable steady states for the same set of input parameters, with transitions between them depending on the history of the system. A slow up-ramp of the stimulus flips the system from the low to the high state at one threshold; a subsequent down-ramp flips it back at a lower threshold. The two thresholds enclose a **hysteresis loop** — a region of parameter space where the stable state depends on where the system came from, not just where it is now.

Hysteresis is the simplest attractor-based substrate for **short-term memory**: the population "remembers" a transient input by remaining in the upper stable state after the input has ended.

## Minimum Dynamical Structure

Hysteresis requires a system with at least two stable fixed points for overlapping ranges of a control parameter. The simplest case is a one-dimensional system with a cubic nonlinearity; in Wilson-Cowan E-I populations, hysteresis emerges from the nonmonotone "kink" in the `dE/dt = 0` isocline caused by the sigmoid nonlinearity combined with sufficient E-E recurrence.

## Wilson-Cowan Conditions

[[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] give the earliest closed-form conditions on when an E-I population exhibits hysteresis:

### Simple hysteresis (two stable states)

**Condition** (sufficient, with refractoriness prefactors rₑ = rᵢ = 1): `c₁ > 9/aₑ`.

**Interpretation**: the E-E coupling strength must exceed a threshold set by `9/aₑ`, where `aₑ` is the slope of the excitatory sigmoid. `1/aₑ` is directly related to the variance of the distribution of thresholds (or synaptic counts) from which the sigmoid was derived — so the condition is a quantitative statement that **the average E-E synaptic count must exceed a function of the variance** of that distribution. Strong enough recurrent excitation, in other words, relative to how heterogeneous the E population is. This is the same "strong E-E recurrence" condition that the subsequent attractor-network memory literature (Amit & Brunel 1997; Wang 2001) identifies for **persistent activity** — hysteresis and persistent activity are two names for the same underlying phenomenon.

### Multiple hysteresis (up to five steady states, three stable)

**Condition**: `aₑaᵢc₂c₃ > (aₑc₁ − 9)(aᵢc₄ + 9)` (Eq. 19).

**Interpretation**: a condition on the **E-I negative feedback loop** strength (c₂c₃) relative to the E-E and I-I internal amplifications. Note that multi-stability with more than two stable states **requires inhibition** — it is unique to the two-variable E-I formulation and cannot occur in purely excitatory populations. Five coexisting stable states can support multi-way categorical selection or multiple working-memory slots, though direct biological instantiation is less well characterized than simple bistability.

## Functional Interpretations

### Short-term memory as attractor persistence

Cragg & Temperley (1955) first proposed hysteresis as a physiological basis for short-term memory: any input of sufficient intensity and duration flips the population into the upper stable state, and that state remains until a reset signal arrives. [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] supply the coupled-equation model that implements this, making Hebb's (1949) reverberatory memory proposal concrete at the population level. The upper stable state is a self-sustaining high-activity configuration — reverberating activity, in Hebb's language.

### Binocular fusion (Fender & Julesz 1967)

Fender & Julesz showed experimentally that binocular fusion exhibits hysteresis: once fused, a pair of stereo images remains fused even as disparities move beyond the range at which fusion would initially occur. Since early binocular interactions occur in V1, this is a direct demonstration of cortical hysteresis. Wilson-Cowan provides the population-level model that reproduces it.

### Persistent activity in working memory

The sustained delay-period firing observed in PFC (Fuster 1973; Goldman-Rakic 1995), lateral intraparietal area (Shadlen & Newsome 2001), and downstream motor preparation is a direct biological instance of the Wilson-Cowan upper stable state. The attractor-network working memory literature (Amit & Brunel 1997; Compte et al. 2000; Wang 2001) formalizes this using spiking E-I networks whose mean-field description reduces to Wilson-Cowan-style equations.

### Noise insensitivity and population thresholds

Wilson & Cowan explicitly flag two important robustness properties of hysteresis:
- **Population threshold**: the transition to the upper state requires a sufficiently strong input; subthreshold inputs do not accidentally flip the state. This provides a form of noise robustness — small fluctuations cannot switch the population.
- **Time-intensity tradeoff**: the required stimulus intensity decreases with stimulus duration; very brief strong stimuli and long weak stimuli both suffice (their "Block-type" strength-duration curve). This is the form commonly observed in the visual system.

## Hysteresis in Context

- **[[Attractor Dynamics]]**: hysteresis is the simplest attractor-based memory mechanism — two point attractors with history-dependent basin of attraction. Contrast with [[brennan-2019-conserved-macroscopic-dynamics|limit-cycle attractors]] for rhythmic output and [[Rotational Dynamics|rotational dynamics]] for time-varying motor patterns.
- **Relationship to [[Limit Cycle|limit cycles]]**: Wilson-Cowan's Theorem 4 proves that any E-I population capable of a limit cycle under some stimulus configuration must also display simple hysteresis under some other stimulus. The two dynamical regimes are not independent — they are two modes of the same substrate, selected by nonspecific biasing inputs.
- **Control-theoretic reading**: hysteresis gives a physical substrate for **binary/categorical state** that persists between explicit transitions. This is the minimum machinery for extending sensorimotor control over time: the population "holds" a command or a decision between the input that specified it and the action that consumes it. Working memory is hysteresis extended to richer state spaces.
- **Contrast with integrators**: a perfect integrator (line attractor) accumulates evidence continuously and supports graded memory; hysteresis supports only discrete states. Both appear in cortex under different conditions.

## Biological Implementations Beyond Wilson-Cowan

- **NMDA-mediated persistent activity** in PFC, PPC, and elsewhere. Slow NMDA kinetics provide the nonlinearity and long timescale needed to maintain an upper stable state against decay.
- **Up and down states** in cortex during slow-wave sleep and anesthesia. Bistable switching between low-activity "down" and high-activity "up" states in local cortical populations — a direct instance of simple Wilson-Cowan hysteresis driven by slow modulatory fluctuations across the hysteresis boundary.
- **Motor program selection** in the basal ganglia. Competitive bistability between action-selection attractors; specific actions are maintained until the next action is selected.
- **Developmental state transitions**. Bistability between transcriptional states during cell-fate decisions uses the same mathematical structure at the molecular-network level.

## Why Hysteresis Matters for the Control Thesis

Hysteresis is the minimum dynamical machinery that extends sensorimotor control **over time**. Without any mechanism for state persistence, control is purely reactive — the motor output depends only on the instantaneous sensory input. Hysteresis introduces **discrete memory states** that carry information forward between explicit transitions, letting the organism act on information that is no longer present at the sensor. Working memory, decision maintenance, and discrete behavioral-state switches are all progressive elaborations of this minimum structure.

The Wilson-Cowan derivation makes the genes-to-function mapping concrete: simple hysteresis requires `c₁ > 9/aₑ`, a condition on two mesoscopic parameters that genes can tune via cell-type-specific synapse counts and receptor densities. The control-theoretic reading of [[Degeneracy]] applies directly — the specific microscopic circuit doesn't matter, as long as the mesoscopic E-E coupling exceeds the threshold.

## Sources

- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — closed-form conditions for simple and multiple hysteresis in E-I populations; hysteresis-as-short-term-memory interpretation; binocular fusion (Fender & Julesz 1967) as cortical experimental demonstration.
