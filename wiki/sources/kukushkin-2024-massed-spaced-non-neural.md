---
title: "The Massed-Spaced Learning Effect in Non-Neural Human Cells"
type: source
source_type: paper
authors:
  - "Nikolay V. Kukushkin"
  - "Robert E. Carney"
  - "Tasnim Tabassum"
  - "Thomas J. Carew"
year: 2024
doi: "10.1038/s41467-024-53922-x"
tags: [memory, spacing-effect, creb, erk, mapk, non-neural, cellular-cognition, signaling-cascades, transcription, learning]
date_ingested: 2026-04-28
key_finding: "The massed-spaced learning effect — stronger and more sustained memory from temporally distributed than massed training — is reproduced in two non-neural human cell lines (SH-SY5Y, HEK293) using a CRE-luciferase reporter; four 3-min pulses of forskolin/TPA spaced by 10–20 min produce ~3.9× higher CREB-driven transcription at 24 h than a single equivalent massed pulse, and the effect is blocked by ERK or CREB inhibition. Canonical features of memory do not require neural circuitry — they live in the dynamics of conserved signaling cascades."
---

[PDF](../../raw/papers/kukushkin-2024.pdf)

## Overview

[[nikolay-kukushkin|Kukushkin]], Carney, Tabassum & [[thomas-carew|Carew]] (2024) ask a sharp question: is the **spacing effect** — the well-established observation that distributed training produces stronger memory than the same total training applied in one massed session — a property of *neural circuits*, or of the *signaling cascades* that those circuits run? They answer empirically: it is the latter. Two human non-neural cell lines, SH-SY5Y (neuroblastoma) and HEK293 (embryonic kidney), reproduce the canonical hallmarks of the [[spacing-effect|massed-spaced learning effect]] when "trained" with temporally patterned pulses of forskolin (PKA activator) and/or TPA / phorbol ester (PKC activator). The same molecular signature underwrites the effect: stronger and more sustained activation of ERK / MAPK and [[creb|CREB]], and pharmacological inhibition of either ERK (U0126) or CREB (666-15) blocks it.

The paper is the clearest demonstration to date that memory-like temporal pattern detection is **embedded in the dynamics of conserved cellular signaling cascades**, not in synapses or networks per se. It is the cellular-cognition counterpart of the wiki's central recurring theme — "the learning rules and computational primitives are simple; the magic is in the collective organization."

## Key Findings

### The reporter system

A short-lived, PEST-tagged firefly luciferase ([[creb|CRE-luc]]) under a CRE promoter as a readout of CREB-driven transcription. Stable monoclonal lines of SH-SY5Y and HEK293 cells were generated. The PEST destabilization is essential — without it, accumulated luciferase product would mask the temporal dynamics of transcription. Forskolin (fsk; 2 µM) activates PKA via cAMP; TPA (2 nM) activates PKC; both kinases converge on CREB phosphorylation at S133, which drives transcription via CRE-bound CREB.

### Repetition boosts CRE-dependent transcription and slows its decay

A single 3-min TPA + fsk pulse at t = 0 produces robust luciferase at 4 h post-training. Four 3-min pulses (ITI = 10 min) produce ~1.4× higher luciferase at 4 h. By 24 h, the gap widens dramatically: the single-pulse signal has decayed near baseline while the 4× signal remains robustly elevated — a 2.8-fold ratio for TPA + fsk (n = 14), 3.9× for TPA alone (29% vs 391% above baseline), and a smaller but significant gap for fsk alone. **Repetition does not just amplify; it slows the decay** — exactly the Ebbinghaus forgetting-curve signature of long-term memory in animals.

### Two distinct sensitivities to temporal pattern

- **PKA (forskolin) is more sensitive to *duration* of stimulation** (continuous 4-h vs single 3-min pulse: large difference).
- **PKC (TPA) is more sensitive to the *number* of events** (continuous 4-h vs single pulse: small difference; 4× vs 1×: large difference).
- The two kinases are "tuned" to distinct temporal features. Endogenous neuromodulators that activate both pathways simultaneously (e.g., 5-HT in *Aplysia*) integrate over both axes.

### Optimal ITI

For TPA + fsk and TPA alone the optimal ITI is **10 min**; for fsk alone the optimal ITI is **20 min**. ITIs of 30 min are sub-optimal in all conditions. A non-zero optimal ITI is the central diagnostic of the [[spacing-effect|spacing effect]] — neither massed (ITI = 0) nor maximally distributed is best. The paper also tests a "paired-pulse" control (only the first and last pulse of a 4-pulse protocol, matched in total span) and finds it does not produce sustained transcription: **repetition of >2 events is critical**, not just spread.

### Massed vs spaced is decoded at ERK and upstream of ERK

Western blot immediately after the training protocol: 4×TPA produces significantly stronger phosphorylation of ERK and CREB than massed TPA. So the temporal discrimination occurs at least in part **upstream of ERK** (or by ERK itself). Immunofluorescence shows greater nuclear:cytosol ratio of P-ERK after spaced than massed training — translocation of P-ERK to the nucleus is a key mechanism by which it activates downstream transcription factors like CREB.

### CREB regulation has two arms

At 24 h post-training, the **P-CREB/total CREB ratio** is highest in 4×TPA cells. But the absolute P-CREB level is even more strikingly elevated because **total CREB protein** is also modestly increased in 4×TPA-treated cells while it is *reduced below baseline* in 1×TPA and massed cells. The product (P-CREB ratio × total CREB) gives the absolute CREB phosphorylation, and this is robustly elevated only after spaced training. Suboptimal training therefore not only fails to phosphorylate CREB sustainedly — it actively *down-regulates* CREB. Spaced training preferentially recruits both arms of the regulation.

### ERK and CREB inhibition both block the spacing effect

- **U0126 (ERK inhibitor, 10 µM)** for 1 h or 24 h around training significantly reduces the 24-h luciferase signal in 4×TPA cells, bringing the 4× : massed ratio close to 1. ERK is necessary for the spacing effect.
- **666-15 (CREB inhibitor, 1 µM)** likewise eliminates the 4× : massed difference. The CREB-binding inhibitor prevents transcription downstream of phosphorylation. Curiously, 666-15 itself reduces the P-CREB(S133)/CREB ratio, suggesting that when CREB cannot bind its targets it is disproportionately dephosphorylated and possibly degraded — a feedback loop between CREB binding and CREB stability.
- Both treatments showed a 24-h reduction in P-ERK after 4×TPA, suggesting a CREB-mediated **positive feedback loop** that sustains ERK activity beyond the immediate stimulation period (consistent with reported BDNF / Pousségur 2003 / Roberson 1999 mechanisms).

### Replication in HEK293 (no neural ancestry)

HEK293 cells, derived from embryonic kidney and entirely outside the nervous system, show the same massed-spaced effect: 4×TPA at 24 h produces significantly stronger luciferase induction than 1×TPA or massed TPA, and the P-ERK/total ERK and P-CREB/total CREB ratios are disproportionately elevated. Extending the result from neuroblastoma to a clearly non-neural lineage rules out neuron-like properties of SH-SY5Y as the mechanism.

## Methods

- **Cell lines**: SH-SY5Y (human neuroblastoma) and HEK293 (human embryonic kidney). Both stably transfected with pGL4.29 [luc2P/CRE/Hygro] (Promega) — a destabilizing PEST-tagged firefly luciferase under a CRE promoter. Monoclonal lines selected via the "scratch-and-sniff" method (Karin 1999) and tested for forskolin-induced luciferase induction.
- **Drug treatments**: Forskolin (Amsbio; PKA activator via cAMP); TPA / phorbol ester (CST; PKC activator); U0126 (Tocris; ERK phosphorylation inhibitor); 666-15 (Tocris; CREB transcriptional activity inhibitor). Treatments delivered in serum-free media via gentle perfusion through a needleless syringe / vacuum manifold to minimize mechanical disruption.
- **Readouts**: Luciferase Assay System (Promega) on lysates; Western blots with anti-P-ERK, anti-ERK, anti-P-CREB(S133), anti-CREB, anti-luciferase, anti-β-actin, anti-H3 (CST primary antibodies; LiCor IRDye secondaries; LiCor Odyssey detection); immunofluorescence for nuclear:cytosol ERK localization (Leica SP8 confocal; CellProfiler analysis).
- **Statistics**: Two-tailed paired Student's t-tests on log-ratios (treatment:control), Dunnett's post-hoc following repeated-measures ANOVA where appropriate, GraphPad Prism 10.3.
- **No randomization or blinding** during stimulation (manual timing of pulses requires investigators to know the schedule); blinding was used during Western blot quantification and IF image analysis.

## Implications

### For the wiki's organizing thesis

This paper is the strongest empirical case to date that **memory-relevant temporal pattern detection predates the nervous system** — at least its molecular substrate does. The signaling cascades that decode massed vs spaced training in *Aplysia* sensory neurons (Pagani 2009, Philips 2007/2013, Kukushkin 2022, Wu 2001) are the same cascades present in HEK293 cells, and they decode the same temporal patterns the same way. This sharpens the wiki's organizing claim about how genes encode behavior: **the dynamical building blocks of memory** (PKA / PKC / ERK / CREB cascades with their characteristic activation, persistence, and decay timescales) **are conserved deep below the neural level**, and the nervous system inherited them rather than inventing them.

The control-theoretic reading: cells already had memory-like temporal pattern detection as part of their generic signal-integration machinery. Genes that select among the kinetic parameters of these cascades (decay rates, feedback strengths, downstream coupling) thereby select among the temporal patterns the cell can detect — a continuous mapping from molecular kinetics to behavioral memory dynamics. The nervous system organized these cellular memory primitives into circuits that close sensorimotor loops; the primitives themselves were already there.

### For molecular memory mechanisms

The paper provides a clean experimental separation of two timescales that are typically confounded in animal memory experiments:
1. **PKA-axis duration sensitivity** (slow accumulation of cAMP / sustained PKA phosphorylation events).
2. **PKC-axis count sensitivity** (each pulse triggers a discrete PKC activation event with characteristic rise and fall).

The two kinases converge on CREB but encode different aspects of the temporal pattern. This is the kind of mechanistic split that downstream computational models of the spacing effect (Smolen, Zhang & Byrne 2016; Ajay & Bhalla 2004) have proposed but rarely tested with this clarity. Future work using the CRE-luc system can ask: what temporal features of the input pattern does each kinase decode, and how does their convergence at CREB integrate the two?

### For [[long-term-potentiation|LTP]] and [[hebbian-learning|Hebbian]] frameworks

The result does not displace the role of synapses in memory — the SH-SY5Y / HEK293 lines do not show pairwise activity-dependent plasticity, only temporal pattern detection. But it relocates *some* of the molecular machinery: the CREB-mediated transcriptional consolidation that converts short-term to long-term memory at synapses ([[long-term-potentiation|late-phase LTP]]; protein-synthesis-dependent memory; Kandel's *Aplysia* lineage) operates on dynamics that are also expressed in non-neural cells. The synapse adds the *pairwise* element (which cells the change happens at); the cellular signaling cascade contributes the *temporal-pattern* decoding (which patterns produce the change). Both are necessary for circuit-level associative memory; only the latter is demonstrably non-neural.

### For the [[spacing-effect|spacing effect]] across species

The optimal ITI of 10–20 min in CRE-luc cells is in the same order of magnitude as optimal ITIs reported for *Aplysia* (15 min), *Drosophila* (15 min), *Apis mellifera* (honeybees; ~10 min for olfactory conditioning), and rats (5–15 min for sensitization). The conservation of optimal ITI across species and cell types is striking and suggests that the underlying kinetic time constants (kinase activation, phosphatase recovery, CREB phosphorylation half-life) are evolutionarily set by physical-chemical constraints on the cascade, not tuned independently in each species.

### For [[meister-2022-learning-fast-slow|learning-rate variability]]

[[meister-2022-learning-fast-slow|Meister (2022)]]'s framing — fast Hebbian plasticity but slow representation-building — assumes a fast plasticity mechanism. Kukushkin shows that even at the *non-synaptic* level, the consolidation step is slow: a single pulse decays by 24 h, four spaced pulses persist. Some of the "slow" timescale of mammalian learning may be explained by the molecular consolidation kinetics rather than by representation-building per se — though this paper does not directly distinguish them.

## Connections to Existing Knowledge

### Direct lineage

- **Hermann Ebbinghaus (1885)** — first systematic documentation of the spacing effect. The paper's discussion explicitly invokes the Ebbinghaus forgetting curve as the temporal-decay signature its CRE-luc system reproduces.
- **Eric Kandel and the *Aplysia* program** — cellular models of memory formation in *Aplysia* sensory neurons demonstrated that spaced 5-HT applications produce long-term facilitation (LTF), short-term decay, and CREB-dependent transcriptional consolidation. The 4-pulse protocol the paper uses for cells is a direct adaptation of the canonical 5×5-min 5-HT protocol from *Aplysia*. Carew, the senior author, was a key contributor to this lineage (Mauelshagen, Sherff & Carew 1998 on spaced/massed ratio).
- **Pagani et al. 2009** — SHP2 phosphatase tuning of the optimal spacing interval in *Drosophila* mushroom body neurons. Direct molecular precursor to Kukushkin's framing.
- **Philips et al. 2007, 2013** — ERK phosphorylation timing in *Aplysia* sensory neurons defines effective training patterns. The sensitivity of the spacing effect to ERK kinetics is a *specific*, *quantitative* prediction of these earlier papers that Kukushkin tests in the cell-line system.
- **Kukushkin et al. 2022 (PNAS)** — precise timing of ERK phosphorylation/dephosphorylation determines long-term memory induction in *Aplysia*. The 2024 paper is the cell-culture extension of this 2022 work.

### Connections to wiki pages

- **[[long-term-potentiation|LTP/LTD]]** — late-phase LTP is CREB-dependent and protein-synthesis-dependent; the molecular cascade Kukushkin studies is the one that gates the transition from early- to late-LTP. The wiki's LTP page's note on "calcium-as-trigger" — that downstream cascades persist after the calcium signal is gone — is exactly the dynamics Kukushkin's CRE-luc system measures.
- **[[hebbian-learning|Hebbian Learning]]** — the synaptic-locality and pre/post-coincidence aspects of Hebbian learning are *not* present in non-neural cells. But the **temporal-pattern decoding** that converts coincident events into lasting change is. Kukushkin separates the two: cells have the pattern-decoding machinery without the pairwise-association machinery.
- **[[memory-consolidation|Memory Consolidation]]** — the paper extends the consolidation framework to a single-cell, transcription-only setting. The 24-h timescale of luciferase persistence (matched to mRNA / protein turnover times) is the cellular analog of the days-to-weeks systems-consolidation timescale at the circuit level.
- **[[calcium-signaling|Calcium Signaling]]** — calcium is upstream of CaMKII and PKC; the calcium-as-trigger framing on the calcium page maps directly onto the kinase cascades Kukushkin manipulates.
- **[[synapses|Synapses]]** — the synapse page notes that no non-neural system has *pairwise* activity-dependent plasticity. Kukushkin's result extends this carefully: non-neural cells *do* have temporal-pattern-detecting plasticity (transcriptional consolidation), but they don't have the pairwise component. The synapse contributes *which* connection changes; the cellular cascade contributes *whether* a lasting change happens given the temporal pattern.
- **[[meister-2022-learning-fast-slow|Meister (2022)]]** — connects to the slow timescale of learning. Meister attributes slow lab-learning to representation-building; Kukushkin shows that even at the molecular level, consolidation has 24-h kinetics. The two contributions to slowness (representational + molecular) are not exclusive.
- **[[creb|CREB]]** — the central transcription factor. Kukushkin is the cleanest in vitro demonstration that CREB phosphorylation kinetics decode massed vs spaced patterns.
- **[[cellular-cognition|Cellular Cognition]]** — Kukushkin is the empirical anchor for the framework. Cattaneo et al. 2018, Bhalla & Iyengar 1999, and others had argued for cellular-level computation in signaling cascades; this paper demonstrates a canonical memory phenomenon (spacing effect) in the framework.

## Open Questions Raised

1. **Which kinetic parameters of the cascade set the 10-min optimal ITI?** The paper attributes it to the activation / decay times of PKA and PKC and the integration time of CREB. Specific dynamical models (Smolen-Baxter-Byrne 2008 bistable MAPK; Markevich 2004 multisite phosphorylation; Pagani 2009 SHP2 tuning) make different predictions. A systematic perturbation of cascade time-constants in CRE-luc cells could discriminate.
2. **Is the cellular spacing effect *causally* relevant for animal memory, or just correlated?** The paper's mechanistic case (cascade dynamics in cells match cascade dynamics in *Aplysia* neurons match behavioral spacing in animals) is suggestive but not causal. A genetic / pharmacological intervention that alters the optimal ITI in cells *and* in animals — and shows the shift is consistent with the cellular kinetic prediction — would close the loop.
3. **Does temporal pattern detection in non-neural cells extend beyond spacing?** Other classical learning phenomena — habituation, sensitization, conditioning, blocking, Pavlovian-style associative pairing — have molecular correlates. Which of them are reproducible in CRE-luc-style cell systems? The paper's framework extends naturally to all of them, but each is a distinct empirical question.
4. **What is the role of the positive feedback loop between CREB and ERK?** The paper observes that 666-15 (CREB inhibitor) reduces P-ERK at 24 h, consistent with a CREB → BDNF → ERK feedback loop reported elsewhere. The kinetics and gain of this loop set the persistence of the consolidated state and may be the mechanism that distinguishes "spaced training produces long-term memory" from "spaced training produces short-term memory."
5. **Why does suboptimal training *down-regulate* total CREB?** Kukushkin's incidental finding — 1×TPA and massed TPA reduce total CREB protein at 24 h — suggests an active mechanism that suppresses memory machinery in response to inadequate training. Is this a homeostatic protection mechanism that prevents accumulation of weakly-encoded transcription? Does it have a behavioral analog (e.g., proactive interference)?
6. **Can the CRE-luc system be used to **design** optimal training protocols** — and do those protocols predict memory outcomes in animal experiments? Zhang et al. 2011 (cited as ref 56) computationally designed enhanced learning protocols using *Aplysia* cascade models; Kukushkin's system enables high-throughput empirical optimization. The pipeline (cell-derived training protocol → animal experiment) has not yet been closed.
7. **What is the right framework for relating cellular memory to circuit-level memory?** The paper sketches the relation: synapses add pairwise specificity; cellular cascades supply temporal-pattern decoding. But the formal model — what computations are uniquely circuit-level vs. uniquely cellular vs. shared — is not developed. The wiki's [[cellular-cognition|cellular cognition]] page tracks this thread.

## See Also

- [[nikolay-kukushkin|Nikolay Kukushkin]] — first author
- [[thomas-carew|Thomas Carew]] — senior author; *Aplysia* learning lineage
- [[spacing-effect|Spacing Effect / Massed-Spaced Learning]] — the central concept
- [[creb|CREB]] — the central transcription factor
- [[cellular-cognition|Cellular Cognition]] — the conceptual framework the paper anchors
- [[long-term-potentiation|Long-Term Potentiation and Depression]] — late-phase LTP mechanism, CREB-dependent
- [[memory-consolidation|Memory Consolidation]] — circuit-level analog of the cellular consolidation Kukushkin demonstrates
- [[calcium-signaling|Calcium Signaling]] — upstream of the kinase cascades
- [[hebbian-learning|Hebbian Learning]] — pairwise plasticity not present in non-neural cells; temporal-pattern-decoding is
- [[meister-2022-learning-fast-slow|Meister (2022)]] — slow representation-building vs slow consolidation kinetics
