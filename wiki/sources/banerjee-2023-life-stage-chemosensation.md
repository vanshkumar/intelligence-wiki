---
title: "Differential Processing of a Chemosensory Cue Across Life Stages Sharing the Same Valence State in Caenorhabditis elegans"
type: source
source_type: paper
authors:
  - "Navonil Banerjee"
  - "Hao-Wei Shih"
  - "Dona Rojas Palato"
  - "Paul W. Sternberg"
  - "Elissa A. Hallem"
year: 2023
doi: "10.1073/pnas.2218023120"
tags: [c-elegans, chemosensation, circuit-reconfiguration, degeneracy, development, gap-junctions, insulin-signaling]
date_ingested: 2026-04-14
key_finding: "The same chemosensory cue (CO₂) with the same behavioral valence (attraction) is processed through functionally distinct microcircuits in starved adults vs. dauer larvae — same genome, same neurons, different effective circuit, gated by BAG–AIB gap junctions and daf-2 insulin signaling."
---

## Overview

Banerjee, Shih, Rojas Palato, Sternberg & Hallem (2023) ask what looks at first like a surprising question: if two life stages of the same animal are attracted to the same cue, do they use the same circuit? The answer, in *C. elegans* CO₂ chemotaxis, is **no**. Starved adults and dauer larvae — both attracted to CO₂ — engage different downstream interneurons, with different polarities, producing different motor programs. The difference is gated by state-dependent electrical coupling (BAG–AIB gap junctions via CHE-7 innexin) and by daf-2 insulin/IGF signaling.

This is a clean counterpoint to [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]: Brennan showed *different implementations → same behavior* across individuals; Banerjee shows *same genome, same cue, same valence → different implementations* across life stages of one animal. Together they establish that the mapping between neural circuit and behavior is many-to-many in both directions.

[PDF](../../raw/papers/banerjee-2023.pdf)

## Key Findings

**1. Same cue, same valence, different life stages.** Both starved adults and dauer larvae are attracted to CO₂ (a cue that well-fed adults avoid). Behaviorally, however, dauers show a **more prolonged speed decrease and more reversals**, while adults mostly slow forward locomotion.

**2. Divergent downstream processing.** Calcium imaging at each node of the established CO₂ circuit reveals stage-dependent responses:
- **BAG** (primary CO₂ sensory neurons): excited in both stages, but **reduced response amplitude in dauers** (not explained by *gcy-9* receptor expression).
- **RIG**: excited in both, but dauers show **early termination followed by late inhibition**.
- **AIY**: **inhibited in adults**; **stochastic in dauers** (excitation in some animals, inhibition in others).
- **AIB**: **robust CO₂-evoked excitation in dauers, absent in adults** — the signature life-stage difference.
- **AVE**: **predominantly inhibited in dauers, silent in adults**.

**3. Dauer-specific AIB excitation requires BAG–AIB gap junctions.** Genetic ablation of the CHE-7 innexin subunit abolishes AIB excitation in dauers. The BAG→AIB electrical coupling is a dauer-specific feature of the effective connectome — not a rewiring of anatomy, but a state-dependent recruitment of a latent pathway.

**4. daf-2 insulin signaling gates the reconfiguration.** *daf-2* (insulin/IGF-1 receptor) loss-of-function eliminates dauer-specific AIB excitation. Insulin signaling thus acts non-cell-autonomously as a developmental-state gate on circuit function.

**5. AIB is necessary but not sufficient for the dauer motor pattern.** Ablating AIB in adults partially "dauer-izes" their behavior (reduces the forward-movement-reduction phenotype, producing more dauer-like pausing). But **artificially raising AIB excitability in adults** (via ectopic bacterial sodium channel NaChBac expression) does *not* recapitulate the dauer pattern. So AIB recruitment is one of several state-dependent changes; the full motor program requires multiple circuit elements in combination.

**6. Behavioral read-out of the circuit reconfiguration.** The different motor programs are consistent with life-history: starved adults slow to linger in a food-rich patch; dauers (a stress-induced, non-feeding larval stage) pause and reverse, consistent with a more thorough search/assessment strategy appropriate for an animal that is seeking a host or a favorable substrate rather than food.

## Methods

- **Behavior**: CO₂ chemotaxis assays quantifying speed, reversals, and pausing in starved adults vs. dauer larvae.
- **Calcium imaging**: GCaMP recordings from identified neurons (BAG, RIG, AIY, AIB, AVE) under controlled CO₂ pulses.
- **Genetics**: mutations in *gcy-9* (CO₂ receptor), *che-7* (innexin, gap junction), and *daf-2* (insulin receptor); cell-specific rescue; AIB-specific ablation and NaChBac expression.
- **Analysis**: trial-by-trial response classification; correlation of calcium transients with locomotor state.

## Implications

**For the organizing principle of this wiki.** The control-theoretic reading of [[Degeneracy]] asserts that genes constrain neuronal dynamics rather than specifying circuits, and that the same macroscopic behavior can emerge from different microscopic implementations. Banerjee shows the logical complement: the *same* genome and the *same* anatomical connectome can instantiate different *effective* circuits depending on physiological state. Valence (attraction to CO₂) is conserved across life stages; the circuit implementing that valence is not. Implementation and behavior are decoupled in both directions — many implementations to one behavior, and one substrate to many behaviors — which is the core claim of the new [[Circuit-Behavior Mapping]] umbrella.

**For the connectome.** The BAG–AIB gap junction is anatomically present but functionally gated by life stage. This cautions against reading "the" *C. elegans* connectome as a static wiring diagram: the functionally active connectome is a state-dependent subset of the anatomical one, and the selection is governed by systemic signals (insulin) acting on electrical synapse composition.

**For the endotaxis / chemotaxis thread.** [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] treats chemotaxis as the ancient sensorimotor controller that cognitive navigation repurposes. Banerjee shows that the "ancient controller" is itself not monolithic — even in *C. elegans*, the chemotaxis circuit is plastic and reconfigurable. This doesn't challenge the endotaxis framing but enriches it: the module being repurposed has its own internal flexibility, and higher-level control may exploit that flexibility.

**For neuromodulation.** Insulin/IGF signaling is a systemic developmental signal that turns out to act directly on circuit composition via electrical synapse recruitment. This blurs the line between "development" and "neuromodulation" — daf-2 is acting like a slow, global neuromodulator whose effect is not to change firing rates but to change which synapses are in the effective circuit.

## Connections to Existing Knowledge

- **[[Degeneracy]]**: the complement case. Same genome + same cue + same valence → different circuits. This extends the degeneracy framework to include context-dependent reconfiguration.
- **[[Circuit-Behavior Mapping]]**: the umbrella page linking classic degeneracy (many-to-one) and context-dependent reconfiguration (one-to-many) as two faces of the implementation-behavior decoupling.
- **[[Context-Dependent Circuit Reconfiguration]]**: the phenomenon specifically, distinguished from degeneracy by the fact that the reconfiguration occurs *within an individual* across states, not across individuals.
- **[[C. elegans Chemotaxis Circuit]]**: the circuit-level page detailing BAG, AIY, AIB, AVE, RIG.
- **[[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]**: complementary degeneracy in *C. elegans* — variable individual neuron activations, conserved macroscopic dynamics.
- **[[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]]**: chemotaxis as the foundational sensorimotor controller; Banerjee reveals that controller's internal flexibility.
- **[[Synapses]]**: gap junctions as a functionally gated substrate for circuit reconfiguration.
- **[[Dopamine|Neuromodulation]]**: insulin signaling as a systemic circuit-level modulator.

## Open Questions Raised

- What other *C. elegans* sensorimotor circuits show life-stage-dependent reconfiguration? Is CO₂ chemotaxis an outlier, or is stage-dependent circuit identity the norm?
- What is the molecular mechanism by which daf-2 signaling gates AIB's recruitment into the CO₂ circuit? Does it alter innexin composition, receptor expression, or intrinsic excitability — or all three?
- Are there analogous state-dependent gap-junction reconfigurations in mammalian circuits? Electrical synapses are present in many vertebrate circuits; whether they are similarly gated by systemic signals is largely unknown.
- Does the same sensory neuron (BAG) carry different information in the two life stages, or does the downstream divergence transform a common signal differently? The reduced BAG response amplitude in dauers hints at the former.
- Can this framework generalize the [[Successor Representation]] / endotaxis formal overlap — if the same sensory gradient can be routed through different interneuron populations, does that correspond to different "value functions" in a control-theoretic sense?
- What determines which subset of the anatomical connectome is "active" at any given time? Is there a principled way to read off the effective connectome from a physiological state vector?

## Sources

- Banerjee, N., Shih, H.-W., Rojas Palato, D., Sternberg, P. W., & Hallem, E. A. (2023). Differential processing of a chemosensory cue across life stages sharing the same valence state in *Caenorhabditis elegans*. *PNAS*, 120. [PDF](../../raw/papers/banerjee-2023.pdf)
