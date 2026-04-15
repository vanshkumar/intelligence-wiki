---
title: "Rotational Dynamics"
type: mechanism
aliases: ["neural rotations", "rotational motif", "motor cortex rotations"]
tags: [motor-cortex, dynamical-systems, ctd, pattern-generation, oscillators]
source_count: 1
last_updated: 2026-04-14
level: circuit
---

**Rotational dynamics** is a motif in which motor-cortex population activity during movement traces out rotations in state space — approximately the flow of a low-dimensional linear oscillator. The rotations *generate* the multiphasic muscle activity required for reaching rather than *represent* movement parameters. Established empirically by Churchland et al. (2012) and reproduced by task-trained RNNs (Sussillo et al. 2015). Reviewed in [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]].

## The Finding

Across reach conditions, after aligning to movement onset, motor-cortex population activity in the top two or three principal components traces out rotations in the same direction for all conditions. The rotations account for a large fraction of the movement-period variance and are present in PMd, M1, and during grasping (Rouse & Schieber 2018). A similar motif appears in human speech articulator cortex during speech production (Stavisky 2019), suggesting the rotational motif is not specific to arm reaching but to time-varying motor pattern generation generally.

## Interpretation: Pattern Generation, Not Representation

The classical framing of motor cortex posited that M1 activity *represents* movement parameters — direction, velocity, muscle force — and that muscle activity is read out from this representation. The rotational-dynamics finding reframes this:

- A low-dimensional oscillator naturally produces multiphasic, time-varying patterns.
- Muscle activity during reaching is multiphasic and time-varying.
- So the simplest account of motor-cortex dynamics is that it *is* the oscillator generating muscle activity, not a code about the movement.

Sussillo et al. (2015) provided a sufficiency test: RNNs trained to transform preparatory-like inputs into realistic muscle patterns developed low-dimensional oscillators as their internal solution, reproducing the Churchland rotational structure without being constrained to do so.

## Subtleties

### Rotations are an approximation

True motor-cortex dynamics are nonlinear; rotations are the *linearized* behavior around a fixed point, capturing a large fraction of variance but not all of it. Linearization around fixed points ([[Computation Through Dynamics|CTD]] primer) is the tool that makes rotations visible and quantifiable.

### Rotations as basis, not readout

The rotational motif is best interpreted as a **basis for generating muscle activity** rather than a direct readout. The muscle patterns come from an output-potent projection of the rotating state through the corticospinal mapping. The rotations in M1 and the muscle patterns are related by a readout, not identical.

### Rotations don't exist upstream or downstream

[[vyas-2020-computation-through-dynamics|Vyas et al.]] emphasize: rotational dynamics are present in M1 and PMd but not in supplementary motor area (SMA) nor in muscle activity itself (Lara et al. 2018a). Both upstream and downstream representations are multiphasic and complex, but the rotational *geometry* is specific to motor cortex. This argues against "rotations everywhere in motor systems" and for "rotations as a specific computational trick motor cortex uses."

### Untangling

Russo et al. (2018, 2019) show that a large portion of the response during movement is used for **untangling** — keeping nearby neural states from being followed by divergent behavioral outcomes. High tangling amplifies noise; low tangling is robust. Rotational geometry in M1 has low tangling; SMA achieves low divergence differently (keeping track of context). Pattern-generation rotations are one way to achieve the low-tangling desideratum.

## Relation to Broader Themes

**Limit cycles as control primitives.** Rotational dynamics is a cortical instance of a much older control-theoretic motif: limit-cycle attractors produce rhythmic output from steady input. [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]'s *C. elegans* manifold structure is another limit-cycle-like motif at the whole-nervous-system scale. The same dynamical object — a closed orbit in state space — shows up from worm locomotion to primate reach generation. A reasonable reading: **evolution re-uses limit cycles wherever rhythmic or time-structured motor output is required**, and genes constrain the conditions under which such cycles emerge ([[Degeneracy#Control-Theoretic Interpretation]]).

**Pattern generation vs. representation.** The rotational motif is the cleanest case of the CTD framework's central methodological point: the variance that drives behavior is in collective dynamics, not in tuning curves of individual neurons. Single-neuron responses during reaching are complex, multiphasic, and heterogeneous; the population-level structure that makes them coherent is the rotation.

## Open Questions

- **What drives the rotation?** A well-timed input at movement onset ([[Computation Through Dynamics#Condition-Invariant Signal|CIS]]) transitions the state into the rotational regime, but the specific input and its origin (thalamus, other cortical areas) are not fully characterized.
- **Do rotations appear in non-motor domains when time-structured output is needed?** Speech cortex shows them; what about sequence generation in HVC, or time-structured cognitive operations?
- **What is the relationship between the rotational basis in M1 and the spinal pattern generators?** Both produce time-varying output; how is labor divided?

## Sources

- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — review; Churchland 2012, Sussillo 2015, Lara 2018a, Russo 2018/2019, Stavisky 2019 cited for rotational dynamics.
