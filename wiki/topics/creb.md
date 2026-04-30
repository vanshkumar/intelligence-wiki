---
title: "CREB"
type: mechanism
aliases: ["cAMP response element-binding protein", "CREB1", "P-CREB", "phospho-CREB", "S133 phosphorylation"]
tags: [transcription, memory, signaling-cascades, ltp, late-phase-ltp, immediate-early-genes, gene-expression, plasticity, molecular]
source_count: 1
last_updated: 2026-04-28
level: molecular
---

**CREB** (cAMP response element-binding protein) is a transcription factor that binds the cAMP response element (CRE: 5′-TGACGTCA-3′) and, upon phosphorylation at serine 133, drives transcription of immediate-early genes critical for converting transient cellular events into lasting molecular and synaptic changes. CREB is one of the most-studied molecular nodes in memory research and is broadly conserved across cell types — from *Aplysia* sensory neurons (where Eric Kandel's lab established its role in long-term sensitization) to mammalian cortex (where it gates [[long-term-potentiation|late-phase LTP]]) to non-neural human cell lines (where [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] demonstrate its central role in the [[spacing-effect|spacing effect]]).

## What CREB does

- **Binds CRE** in promoters of target genes — including itself (autoregulation), BDNF, c-fos, *c/ebp*, *zif268*, and many other immediate-early genes (IEGs).
- **Drives transcription only when phosphorylated at S133** — the modification recruits the CREB-binding protein (CBP) coactivator, which acetylates histones and bridges CREB to the basal transcription machinery.
- **Integrates signals from many upstream kinases** — PKA, PKC, ERK, CaMKII, CaMKIV, p38 MAPK, Akt, and others all phosphorylate S133, directly or indirectly. CREB therefore acts as a central integrator of cellular experience, summing inputs from cAMP, calcium, growth factors, and stress signals.
- **Output is sustained on the timescale of hours to days**: once phosphorylated and bound, CREB-driven transcription persists until the kinase activity dissipates and S133 is dephosphorylated by PP1 / PP2A. The slow decay of CREB phosphorylation is one component of the timescale of memory consolidation.

## Why CREB matters for memory

Disruption of CREB (genetic deletion, expression of dominant-negative variants, antisense oligonucleotides, pharmacological inhibition) selectively impairs **long-term** memory while leaving short-term memory intact. This dissociation — established across *Aplysia*, *Drosophila*, mice — places CREB at the bottleneck between transient cellular events and lasting consolidation. The molecular logic:

1. A behaviorally relevant stimulus (training event) activates upstream kinases (PKA, ERK, CaMKII, etc.).
2. Kinases phosphorylate CREB at S133, transiently boosting its transcriptional activity.
3. If the kinase activity is sustained or repeated, CREB binds CBP and drives transcription of IEGs.
4. IEG products feed back into the cell — modifying neurotransmitter release machinery, growth factor levels (e.g., BDNF), and structural proteins — to produce a lasting change.
5. The lasting change supports the long-term phase of memory: late-phase LTP, long-term facilitation, long-term sensitization.

The **transient → sustained transition** is what makes CREB a memory gate. Brief stimulation produces transient phosphorylation that decays without driving transcription. Repeated or properly timed stimulation produces sustained phosphorylation that crosses the threshold for transcriptional output.

## Decoding temporal patterns at CREB

[[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] demonstrate that CREB phosphorylation is **the single best predictor of whether a temporal pattern of stimulation produces lasting cellular response**. In CRE-luciferase non-neural human cells:

- 4×TPA training (4 pulses, ITI 10 min) at 24 h: P-CREB(S133)/CREB ratio significantly elevated; total CREB protein modestly elevated.
- 1×TPA or massed training: P-CREB ratio only slightly elevated; total CREB protein *reduced below baseline*.
- The product (P-CREB ratio × total CREB) gives the absolute amount of phosphorylated CREB available for transcription, and this is robustly elevated only after spaced training.

So the spacing effect is decoded at CREB through **two arms**: phosphorylation rate and total CREB protein level. Spaced training preferentially recruits both. Suboptimal training actively *down-regulates* total CREB at 24 h — a negative-regulation arm whose function is unclear (homeostatic protection? proactive interference?).

## Positive-feedback loops sustain the consolidated state

Several positive-feedback loops involve CREB and explain how transient activation can produce lasting change:

- **CREB → BDNF → ERK → CREB**: phosphorylated CREB drives BDNF transcription; BDNF activates ERK; ERK phosphorylates CREB. [[kukushkin-2024-massed-spaced-non-neural|Kukushkin (2024)]] observes that 666-15 (CREB inhibitor) reduces P-ERK at 24 h post-training, consistent with this loop.
- **CREB → CRTC1**: a CREB-regulated transcription coactivator that can sustain CREB-dependent transcription independently of S133 phosphorylation (Uchida et al. 2017).
- **CREB → ATF4 / CREB2 degradation**: CREB-driven transcription includes degradation pathways for the transcriptional repressor ATF4 / CREB2, lifting transcriptional inhibition.

The combination of multiple positive feedback loops with different time constants is what allows the cellular response to persist for hours after the kinase activity has decayed. The kinetics of these loops set the duration of consolidated memory.

## CRE-luciferase as a memory readout

The destabilizing PEST-tagged firefly luciferase under a CRE promoter (Garcia-Alai et al. 2006) used by [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] is the simplest and cleanest available readout of CREB-dependent transcription. The PEST sequence reduces luciferase half-life from ~hours to ~minutes, so accumulated luciferase reflects *ongoing* transcription rather than the integrated transcriptional history. In stable monoclonal cell lines this provides a tractable in vitro system for studying memory-relevant cellular dynamics — high-throughput, no animals, no ethics complications, and orders of magnitude faster than learning experiments in animals.

## CREB across cell types

A central claim of the [[kukushkin-2024-massed-spaced-non-neural|Kukushkin (2024)]] paper: CREB is broadly conserved, and its transcriptional dynamics in non-neural human cells (SH-SY5Y neuroblastoma, HEK293 embryonic kidney) reproduce the canonical features of memory observed in neurons. Although CREB *targets* differ across cell types — neurons have many neuron-specific IEGs (neurotransmitter biosynthesis enzymes, synaptic vesicle proteins) while non-neural cells have their own — the **dynamical logic** of cAMP / kinase activation → S133 phosphorylation → sustained transcription is the same. This is the empirical foundation of [[cellular-cognition|cellular cognition]].

## Relationship to other concepts

- **[[spacing-effect|Spacing Effect]]** — CREB is the transcription factor whose phosphorylation kinetics decode massed vs spaced patterns.
- **[[long-term-potentiation|LTP/LTD]]** — late-phase LTP is CREB-dependent and protein-synthesis-dependent. The CREB cascade gates the transition from early- to late-LTP. The wiki's [[long-term-potentiation|LTP]] page on "calcium-as-trigger" describes the upstream events that lead to CREB phosphorylation.
- **[[calcium-signaling|Calcium Signaling]]** — calcium activates CaMKII / CaMKIV, both of which phosphorylate CREB at S133. The "calcium-as-trigger" pathway has CREB as its principal downstream node.
- **[[memory-consolidation|Memory Consolidation]]** — CREB-dependent transcription is the cellular component of consolidation. The systems-level consolidation hippocampus → cortex (Wierzynski 2009) is built on top of synapse-level consolidation gated by CREB.
- **[[hebbian-learning|Hebbian Learning]]** — Hebbian coincidence at NMDA receptors leads to calcium influx, which leads to CREB phosphorylation. CREB is the gate that decides whether Hebbian coincidence produces *lasting* change.
- **[[cellular-cognition|Cellular Cognition]]** — CREB's conservation across cell types is the molecular foundation of the cellular-cognition framework.

## Sources

- [[kukushkin-2024-massed-spaced-non-neural|Kukushkin, Carney, Tabassum & Carew (2024)]] — demonstrates CREB phosphorylation kinetics decoding massed vs spaced training in non-neural human cells; pharmacological CREB inhibition (666-15) blocks the spacing effect; spaced training preferentially elevates both P-CREB(S133)/CREB ratio and total CREB protein at 24 h.
