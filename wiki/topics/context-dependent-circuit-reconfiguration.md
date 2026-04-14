---
title: "Context-Dependent Circuit Reconfiguration"
type: concept
aliases: ["circuit reconfiguration", "state-dependent circuit", "effective connectome"]
tags: [circuits, neuromodulation, gap-junctions, development, c-elegans, degeneracy]
source_count: 1
last_updated: 2026-04-14
confidence: emerging
---

Context-dependent circuit reconfiguration is the phenomenon in which **the same anatomical substrate (the same neurons, the same genome) supports different effective circuits depending on physiological state, life stage, or neuromodulatory context.** The "functional connectome" at any moment is a state-dependent subset of the anatomical one, and the selection is governed by systemic signals acting on synaptic (often electrical) coupling or intrinsic excitability.

This is the complement to classic [[Degeneracy]]. Where degeneracy says *different implementations, same behavior* across individuals, context-dependent reconfiguration says *same implementation, different behaviors* within an individual across states. Both sit under the [[Circuit-Behavior Mapping]] umbrella — together they establish that the mapping between circuit implementation and behavior is many-to-many.

## Canonical Example: *C. elegans* CO₂ Chemotaxis

[[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] provide the cleanest demonstration. Starved adults and dauer larvae are both attracted to CO₂ — same sensory cue, same behavioral valence. But downstream processing diverges:

- **AIB** is robustly excited by CO₂ in dauers, silent in adults.
- **AVE** is predominantly inhibited in dauers, silent in adults.
- **AIY** is inhibited in adults, stochastic in dauers.

The dauer-specific AIB excitation requires **BAG–AIB gap junctions** (CHE-7 innexin) — a coupling that is anatomically present in adults but functionally silent — and is gated by **daf-2 insulin/IGF signaling**. The anatomical connectome has not been rewired; a developmental-state signal has redrawn which anatomical connections are functionally active.

The behavioral output differs: starved adults slow forward locomotion; dauers pause and reverse. Same substrate, different effective circuit, different motor program.

See [[C. elegans Chemotaxis Circuit]] for the circuit-level detail.

## Other Instances (Background)

- **Crustacean stomatogastric ganglion**: a ~30-neuron circuit produces qualitatively different motor rhythms (pyloric, gastric) depending on neuromodulatory tone (dopamine, serotonin, peptides). This is the classic literature on circuit reconfiguration; Banerjee is the *C. elegans* counterpart with genetic precision.
- **Cortical state transitions**: awake vs. anesthetized, active vs. quiet wakefulness, REM vs. SWS — all correspond to different effective circuits over the same anatomy, gated by neuromodulatory and thalamocortical state.

These are not yet ingested in the wiki; the Banerjee paper is the first source that directly establishes the phenomenon here.

## Mechanisms of Reconfiguration

Three broad mechanisms can reconfigure a circuit without rewiring it:

1. **Gating electrical synapses**. Innexin/connexin composition, phosphorylation state, or neuromodulator-driven conductance changes can silence or unsilence gap junctions. Banerjee's BAG–AIB coupling is a cleanly genetic example.
2. **Modulating intrinsic excitability**. Neuromodulators shift channel conductances, changing which cells cross threshold in response to a given input.
3. **Modulating synaptic weights / release**. Classical neuromodulation (dopamine, serotonin, norepinephrine) scales transmission at specific synapse populations.

All three produce the same high-level phenomenon: the same anatomy supports a repertoire of effective circuits, and a state vector selects among them.

## Relation to Degeneracy

Both degeneracy and context-dependent reconfiguration decouple implementation from behavior, but in opposite directions:

| Property | Degeneracy | Context-Dependent Reconfiguration |
|---|---|---|
| Across vs. within individual | Across individuals | Within individual, across states |
| Anatomy | Variable (different channel densities, weights, morphology) | Fixed |
| Behavior | Conserved | Varies by state |
| Evolutionary logic | Selection on behavior permits microscopic variability | One substrate supports a life-history repertoire |
| Canonical source | [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] | [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] |

The two are not mutually exclusive — individual dauers presumably also show degeneracy relative to each other while collectively exhibiting the dauer-specific CO₂ response. Both mechanisms compound.

## Implications

**Anatomical connectomes are insufficient.** The *C. elegans* connectome has been exhaustively mapped, yet the CO₂ circuit differs across life stages despite no anatomical rewiring. A static wiring diagram underdetermines function; the effective connectome requires state information.

**Neuromodulation is structurally important, not just a gain term.** Treating neuromodulators as scalar gating on a fixed circuit misses their role in selecting among effective circuits. The Banerjee result shows a systemic endocrine signal (insulin/IGF) reconfiguring the effective circuit via electrical synapse recruitment — this is structural, not gain-like.

**The control thesis accommodates this cleanly.** Genes specify a *repertoire* of accessible control structures; state selects among them. The control-level descriptor (valence: attract to CO₂) is what's preserved across the reconfiguration; the implementation is flexible.

## Sources

- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — life-stage-dependent CO₂ circuit in *C. elegans*; BAG–AIB gap junction and daf-2 as the gating mechanisms.
