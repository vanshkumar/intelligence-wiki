---
title: "Prefrontal Cortex"
type: brain-region
aliases: ["PFC", "mPFC", "medial prefrontal cortex", "prefrontal"]
tags: [cortex, categorization, decision-making, cognitive-flexibility, rule-learning]
source_count: 3
last_updated: 2026-04-14
---

The prefrontal cortex (PFC) is a region of frontal cortex involved in cognitive functions including categorization, rule learning, decision-making, and cognitive flexibility. In primates, PFC neurons rapidly and flexibly represent learned categories. In rodents, the medial prefrontal cortex (mPFC) — including anterior cingulate cortex (ACC), prelimbic cortex (PL), and medial orbital cortex (MO) — plays an analogous role, though the functional and anatomical homology across species is still debated.

From a control perspective, PFC extends the sensorimotor loop over abstract, rule-governed, and counterfactual variables. Where sensory cortex provides immediate stimulus representations and hippocampus provides spatial/episodic context, PFC builds category-level representations and flexible rules that allow the control system to act on latent structure — "this stimulus is a member of the Go category" rather than "this stimulus has these specific visual features."

## Category Representations in mPFC

[[reinert-2021-pfc-categorization|Reinert et al. (2021)]] used chronic two-photon calcium imaging to track mPFC neurons across the entire course of visual category learning in mice. Key findings:

- **Category-selective neurons emerge gradually** — from 0.03% before learning to ~9% after learning, over weeks of reinforced training
- Selectivity correlates with decoding performance and generalizes to novel stimuli on first presentation
- Two distinct populations: Go-preferring (~73%) and NoGo-preferring (~35%) category-selective cells
- During rule switches, Go-preferring neurons **remap** to the new Go category while NoGo-preferring neurons are **replaced** by a new population
- Category representations persist even during uninstructed behaviors, consistent with semantic memory rather than working memory

This gradual emergence argues that mPFC category representations are built up during learning as part of a specific semantic memory, rather than being instantaneously assigned. The ~9% of neurons becoming category-selective is a [[Sparse Coding|sparse representation]] at the population level — though whether this reflects the sensory-level sparse codes that [[meister-2022-learning-fast-slow|Meister (2022)]] argues are the bottleneck for learning, or a downstream decision-level readout, remains an open question.

## Population Dynamics: Line Attractors for Decisions

PFC is also a canonical site for the [[Computation Through Dynamics]] stance. Mante et al. (2013) showed that context-dependent 2AFC decisions in monkey PFC are implemented as a **line attractor**: the relevant sensory input drives population activity along a single dimension toward a choice boundary, while irrelevant inputs are gated into the null space of the decision axis. The line attractor is a specific [[Attractor Dynamics|cortical attractor motif]] that complements the rotational and preparatory dynamics seen in [[Motor Cortex]]. The scaffold structure recovered from monkey PFC in a working-memory task by [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — branching on stimulus encoding, merging after decision — is a scaffold-level view of the same kind of low-dimensional, decision-oriented PFC dynamics.

## Hippocampal Input During Sleep

[[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] show that mPFC receives structured input from the [[Hippocampus]] during slow-wave sleep: CA1 cells fire 0-100 ms before mPFC cells, driven by sharp-wave/ripple events, with timing compatible with [[Long-Term Potentiation|spike-timing-dependent plasticity]]. This coupling is nearly abolished during REM sleep. The SWR-driven hippocampal→PFC spike timing during SWS may be one mechanism driving the gradual [[Memory Consolidation|consolidation]] of category representations observed by Reinert et al. — each sleep cycle reinforcing and refining the cortical trace.

## Sources

- [[reinert-2021-pfc-categorization|Reinert et al. (2021)]] — gradual emergence of category-selective neurons during visual rule learning in mouse mPFC
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — SWR-driven directional spike timing from hippocampus to mPFC during SWS
- [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] — review of the Computation Through Dynamics framework; reports Mante et al. (2013) line-attractor decisions in monkey PFC
