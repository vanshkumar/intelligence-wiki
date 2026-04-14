---
title: "C. elegans Chemotaxis Circuit"
type: brain-region
aliases: ["C. elegans CO2 circuit", "BAG circuit"]
tags: [c-elegans, chemotaxis, sensorimotor, circuit, gap-junctions]
source_count: 1
last_updated: 2026-04-14
---

A compact, well-characterized sensorimotor circuit in *Caenorhabditis elegans* that transforms CO₂ (and other chemosensory cues) into motor output — slowing, reversal, or directed movement. The circuit is a touchpoint for this wiki because (1) *C. elegans* chemotaxis is the kind of ancient, closed-loop sensorimotor controller the control thesis treats as foundational, and (2) it has become the clearest case study for [[Context-Dependent Circuit Reconfiguration]].

## Circuit Architecture

The CO₂-responsive subset of the *C. elegans* nervous system includes a small number of identified neurons linked in a largely feedforward chain with specific lateral and recurrent connections:

- **BAG**: the primary CO₂ sensory neurons. A pair of ciliated sensory neurons expressing the receptor-guanylyl-cyclase *gcy-9*, required for CO₂ detection. BAG is excited by CO₂ in all life stages examined, though response amplitude is reduced in dauer larvae ([[banerjee-2023-life-stage-chemosensation|Banerjee et al., 2023]]).
- **AIY**: a pair of first-layer interneurons receiving BAG input. Inhibited by CO₂ in starved adults; stochastic (mixed excitation/inhibition across animals) in dauers.
- **AIB**: first-layer interneurons with a well-known role in reversal behavior. **Silent to CO₂ in adults**, but **robustly excited in dauers** — the signature life-stage-dependent feature of the circuit.
- **RIG**: interneurons excited by CO₂ in both stages; dauers show earlier termination followed by late inhibition.
- **AVE**: command interneurons in the reversal pathway. Predominantly inhibited in dauers; silent in adults.

Downstream, AVA/AVB/AVD command interneurons drive reversal and forward motor programs via ventral cord motor neurons.

### Gap Junction Coupling

Electrical synapses (gap junctions) constitute a significant fraction of the *C. elegans* connectome and are composed of innexin subunits (the invertebrate counterpart to vertebrate connexins). The **BAG–AIB gap junction**, mediated by the innexin **CHE-7**, is anatomically present in all life stages but **functionally active only in dauers**. Loss of *che-7* abolishes dauer-specific AIB excitation without affecting BAG itself ([[banerjee-2023-life-stage-chemosensation|Banerjee et al., 2023]]).

This is a concrete instance of an electrical synapse being state-gated rather than strictly anatomical — the substrate for [[Context-Dependent Circuit Reconfiguration]].

## State Gating

### Life stage

*C. elegans* has a stress-induced larval arrest stage (the **dauer**) that is non-feeding, long-lived, and behaviorally distinct from reproductive adults. Under favorable conditions, animals progress through larval stages (L1–L4) to reproductive adulthood; under starvation or crowding, L1s arrest as dauers.

Starved adults and dauers are *both attracted* to CO₂, but the downstream circuit differs (see above). The behavioral consequence:
- **Starved adults**: slow forward movement, consistent with foraging/lingering.
- **Dauers**: more prolonged speed decrease, more reversals, consistent with a search/assessment strategy appropriate for an animal seeking a host or favorable substrate rather than food.

### daf-2 insulin/IGF signaling

The **daf-2 insulin/IGF-1 receptor** is the master regulator of dauer formation in *C. elegans*. Beyond its developmental role, daf-2 signaling also gates the CO₂ circuit's effective composition: *daf-2* loss-of-function eliminates the dauer-specific AIB CO₂ response ([[banerjee-2023-life-stage-chemosensation|Banerjee et al., 2023]]). Insulin/IGF signaling is thus acting as a slow, systemic "neuromodulator" whose effect is to change which synapses are in the effective circuit, not to change instantaneous firing rates.

## Role of AIB

AIB is a nodal neuron in the *C. elegans* reversal system. AIB ablation experiments ([[banerjee-2023-life-stage-chemosensation|Banerjee et al., 2023]]) show:
- In **adults**, AIB ablation partially "dauer-izes" behavior — reducing forward-movement reduction and producing more dauer-like pausing. AIB contributes to the adult forward-slowing program.
- In **dauers**, AIB ablation reduces the pause response to CO₂. AIB contributes to the dauer pausing program.
- Artificially raising AIB excitability in adults (via ectopic NaChBac expression) does *not* recapitulate the full dauer motor pattern. AIB recruitment is necessary but not sufficient; the dauer program requires multiple circuit elements in combination.

## Why This Circuit Matters for the Wiki

**Sensorimotor foundation.** The CO₂ chemotaxis circuit is a canonical closed-loop sensorimotor controller: sense CO₂ → interneuron computation → motor program → locomotor adjustment → altered CO₂ sampling. It is the kind of ancient, compact controller that [[Endotaxis]] ([[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al., 2024]]) treats as the foundation that cognitive navigation extends.

**Cleanest case of context-dependent circuit reconfiguration.** *C. elegans* offers genetic precision (single-neuron ablation, innexin knockouts, insulin receptor mutants) that makes the state-dependence of circuit function causally dissectible. Few other systems can demonstrate at this resolution that the effective connectome is a state-dependent subset of the anatomical one.

**Relation to chemotaxis as a universal controller.** [[Endotaxis]] proposes that cognitive navigation repurposes the chemotaxis controller by feeding it an internally generated virtual gradient. Banerjee shows that the chemotaxis controller itself is plastic across life stages — the "module being repurposed" is already a flexible object rather than a fixed primitive.

## Sources

- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — differential CO₂ processing across life stages; BAG, RIG, AIY, AIB, AVE responses; BAG–AIB gap junction (CHE-7) and daf-2 gating.
