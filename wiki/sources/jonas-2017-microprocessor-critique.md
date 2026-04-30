---
title: "Could a Neuroscientist Understand a Microprocessor?"
type: source
source_type: paper
authors:
  - "Eric Jonas"
  - "Konrad Paul Kording"
year: 2017
doi: "10.1371/journal.pcbi.1005268"
tags: [methods-critique, philosophy-of-neuroscience, marr-levels, connectomics, lesion-studies, tuning-curves, dimensionality-reduction, granger-causality, criticality, what-is-understanding]
date_ingested: 2026-04-29
key_finding: "Standard neuroscience analyses applied to a fully understood microprocessor (MOS 6502, full netlist, every transistor state simulable) produce results that look superficially similar to neural findings but do not yield understanding even when ground truth is known — implying that more data alone will not solve neuroscience and that methods need ground-truth-anchored validation."
---

## Overview

Jonas & Kording (2017) is a methodological-philosophical thought experiment dressed as an empirical paper. The setup: take an artificial system whose computation we understand at every Marr level — the MOS 6502 microprocessor (Apple I, Commodore 64, Atari 2600), with 3,510 transistors, a fully reverse-engineered netlist, and a cycle-accurate simulator that gives access to every wire voltage and every transistor state. Run three "behaviors" on it (Donkey Kong, Space Invaders, Pitfall). Then apply the dominant analysis methods of contemporary systems neuroscience — connectomics, lesion studies, single-unit tuning curves, spike-word correlations, local-field-potential / power-spectrum analysis, Granger causality, dimensionality reduction — and ask whether those methods recover the understanding we already have.

The authors find that every method produces results that look superficially like results from real brains — apparent "cell types," lesion-specific behavioral deficits, simple and complex tuning curves, weak pairwise / strong global correlations, 1/f LFP spectra often interpreted as self-organized criticality, dimensionality-reduced components correlated with behavioral variables, and Granger-inferred functional connectivity. Yet for the processor, where ground truth is known, none of these methods yields a satisfying [[marrs-levels-of-analysis|computational/algorithmic-level]] account of how the chip actually runs Donkey Kong. The paper's punch line: the problem is not that neuroscientists *could not* understand a microprocessor — the problem is that they *would not* understand it given the methods currently in use.

This is the founding paper of a genre — methodology validated against ground-truth artificial systems before being applied to brains — and a sustained methodological caution against the assumption that the data shortage is the bottleneck.

[PDF](../../raw/papers/jonas-2017.pdf)

## Key Findings

### What does it mean to understand a system?

The paper opens by sharpening "understanding" as a benchmark. It draws on three traditions:

- **Lazebnik (2002), "Can a biologist fix a radio?"** — argues that understanding is operationalized by ability to *fix* a broken implementation. If you cannot identify which damaged component caused which symptom, your model is descriptive, not mechanistic.
- **Marr & Poggio (1982), three [[marrs-levels-of-analysis|levels of analysis]]** — computational (what problem is solved?), algorithmic (what representations and procedures?), implementational (what physical realization?). Understanding a system means having coherent answers at all three levels and knowing how they connect.
- **Replace-with-synthetic test** — a region is understood when its inputs, transformation, and outputs are characterized well enough that a synthetic substitute could replace it (the goal of sensory and memory neuroprosthetics).

For the processor, the authors claim full understanding at all three levels: at the computational level it implements a stored-program finite-state machine over registers and memory; at the algorithmic level there are well-known modular designs (instruction fetcher, decoder, ALU, registers, byte-wide adder built from 1-bit adders, NAND gates from transistors); at the implementational level we have the silicon layout of every transistor. The challenge they then issue: do the methods of systems neuroscience, given access to far more complete data than is available for any brain, recover this hierarchy?

### Connectomics: cell types without computational meaning

Apply the [Jonas & Kording (2015)](https://elifesciences.org/articles/04250) cell-type discovery method (a stochastic blockmodel for spatial connectivity) to a region of the netlist (X, Y, S register block). The method recovers transistor "types" — clocked transistors (which retain digital state), inverters (C1 or C2 to ground), and various ALU/data-bus controllers — distinguished by spatial connectivity patterns. The result superficially matches what cell-type clustering of neural connectomes produces.

But there is only **one** physical type of transistor. The recovered "cell types" are spatial-layout artifacts and local-versus-global circuitry combinations, not principled computational modules. The full connectome plus a working stochastic blockmodel does not recover the chip's hierarchical organization. Connectomics gives the substrate; getting from substrate to function requires algorithms that go beyond cell-type clustering — and we do not have them.

### Lesions: false-positive specificity

Lesion every single transistor by clamping it to a fixed state, and ask which lesions abolish each game. Result: 1,560 transistors break all three games; 1,565 are inert; the remainder break specific subsets — including 98 transistors specific to Donkey Kong, 39 to Pitfall, 49 to Space Invaders. A neuroscientist looking at this would conclude that there exist *Donkey Kong neurons*, *Pitfall neurons*, *Space Invaders neurons*.

This is grossly misleading. The transistors implement generic operations like full-adders. Their game-specificity is an indirect consequence of which generic operations happen to be load-bearing for which game's particular code path. The paper observes that **Lazebnik (2002) made the identical critique of molecular biology** — shooting radios with metal particles will not tell you what the components do. The general lesson: lesion-specific behavioral deficits do not identify the *role* of the lesioned element in computation; they identify which generic operations a particular behavior happens to require.

A complementary failure: lesions cannot isolate a single computation. To learn what a "Donkey Kong transistor" actually does, you would need to lesion it while the processor performs an isolated computation that the transistor uniquely participates in — a near-impossibility for a system whose behavior involves many interleaved generic operations. The same problem dominates neuroscience: tasks engage too much circuitry simultaneously to license the inference from "lesion changes behavior" to "this region performs that computation."

### Tuning curves: tuned does not mean involved

Plot each transistor's "spike rate" (rising-edge transition rate) as a function of the most recently displayed pixel's luminance. A subset of transistors show clean simple-tuning (single-peak, Gaussian-like) and complex-tuning (multimodal) curves. The figure looks like a V1 paper.

The transistors with strong luminance tuning are *not* directly involved in luminance computation. They relate to brightness through long, highly nonlinear computational paths and happen to correlate with luminance via game-stage statistics. The paper's general claim: **a neuron can compute something, be upstream of something, be downstream of something, or be entirely orthogonal to something, and still show strong apparent tuning to that quantity**. Tuning-curve interpretation is therefore not a reliable route from observed selectivity to computational role. This generalizes to receptive-field analyses in V1 ([[natural-image-statistics|Hubel & Wiesel-style]]), [[place-cells|place cells]], and category-selective neurons in [[prefrontal-cortex|PFC]] ([[reinert-2021-pfc-categorization|Reinert et al. 2021]]).

### Spike-word correlations: weak pairwise, strong global — but it does not mean what it seems

Compute a "spike-word" analysis (Schneidman et al. 2006) over 64 transistors. Pairwise correlations are very weak. Spike-word distributions diverge dramatically from the shuffled (independent) baseline — interpreted in neural data as "weak pairwise / strong collective correlations" and often taken as evidence of synergistic, complex coding.

In the chip, the underlying interactions are simple deterministic Boolean logic — yet the same statistical signature appears. The paper's caution: weak-pairwise/strong-global correlation patterns do not distinguish complex neural codes from simple deterministic systems with structured interactions. Inferring "neural coding principles" from spike-word statistics is therefore unsafe.

### LFP-like averages and 1/f power spectra: epiphenomena of underlying machinery

Spatially averaged transistor switching activity (a chip analog of [[neural-mass-model|local field potential]]) shows roughly power-law (~1/f) spectra over a wide band, very similar to cortical LFP. Spectral analysis identifies region-specific oscillations or "rhythms." These are exactly the signatures often interpreted in neuroscience as evidence of [[edge-of-chaos|self-organized criticality]] or as functional cortical rhythms.

In the chip, the rhythms reflect the interaction of a single transistor type with the chip's clock and load patterns; their specific frequencies and locations are epiphenomena, not computational signals. The paper warns against attributing computational significance to oscillation frequencies or to power-law spectra without an independent mechanistic anchor. This is a sharp caution for the cortical-rhythm and edge-of-chaos literatures: similar statistics emerge from systems with very different underlying computations.

### Granger causality: partially right, partially wrong, no way to tell which

Run conditional Granger causality on five LFP-like regions across the three games. Some recovered relationships are correct (registers affect ALU; decoder affects status bits); others are misleading (decoding "is independent" of accumulator; accumulator-to-registers connection missed in some games). The fundamental limitation: Granger causality measures predictive power, not mechanistic causation, and the link from past-predicts-future to "cause" is tentative at best. Even in a fully observed system with a known ground truth, Granger inferences are partly right and partly wrong with no internal way to tell which is which.

### Dimensionality reduction: latent components correlate with known signals but do not reveal computation

Apply non-negative matrix factorization (NMF) to the activity of all 3,510 transistors during Space Invaders. Six latent dimensions appear. Their time-courses correlate strongly with known internal signals — the two-phase clock (CLK0, CLK1OUT), the read-write line (RW). This looks exactly like neural population analyses that find latent dimensions correlated with stimuli or behavioral variables (Cunningham & Yu 2014; Churchland et al. 2012; Mante et al. 2013).

Yet recovering "dimension 1 ≈ clock" does not reveal how the processor computes — just as recovering manifold dimensions correlated with reach direction does not, by itself, reveal how motor cortex generates reaches. The paper's caution for [[computation-through-dynamics|CTD]]-style analyses: dim-reduced components that correlate with behavioral or task variables are at best partial constraints on the underlying computation, not the computation itself. Linear methods miss nonlinear dependencies and hierarchical organization, and the correlation with a known signal is not the same as a mechanism by which that signal is computed.

### What might actually work

The paper closes with constructive suggestions for what would have helped on the processor — and, by analogy, the brain:

- **Better experimental isolation**: lesion experiments would be more meaningful if combined with simultaneous control of the exact code being executed at the moment of lesion. The corresponding biological move is reaching tasks that isolate one aspect of motor computation.
- **Better theory**: knowing in advance that the chip *has* adders would let you search for them. The corresponding biological move is concrete computational hypotheses (specific algorithms for working memory, decision-making, etc.).
- **Methods that explicitly search for hierarchical structure** — methods that assume modular nesting and ask which modules exist, rather than methods that flatten everything to time series.
- **Methods that transfer across instances** — neuroscience methods should generalize across animals, just as a chip-analysis method should generalize across chips. Methods that overfit one dataset are bad science.
- **Use known artifacts as test beds** — engineered systems with ground truth (microprocessors, trained ANNs) are sanity-check platforms for neuroscience methods, in the way that bioinformatics methods are validated on synthetic genomes before being applied to biology.

## Methods

The MOS 6502 was reverse-engineered by the Visual6502 team via chemical decapping, microscope imaging, and computational extraction of the silicon-layout connectivity, producing a transistor-accurate netlist of 3,510 enhancement-mode transistors plus 1,018 inferred depletion-mode pullups. A C++ simulator runs the netlist at ~1,000 processor clock cycles per wallclock second; 10 simulated seconds of each of three games (Donkey Kong, Space Invaders, Pitfall) was acquired with full per-transistor state on every clock edge, ~1.5 GB/s of state data.

To analogize transistor activity to neural spikes, transistor off-to-on transitions were treated as "spikes." Most analyses used 10 representative transistors with sufficient switching variance for raster-style displays; full-population analyses (NMF, lesion studies) used all 3,510. Lesions were modeled as forcing a transistor's input high (constant "on" state) and measuring whether the chip drew the first frame of each game. Tuning curves used SI luminance because it sampled the luminance space most uniformly. Spike-word analysis followed Schneidman et al. (2006) on 64 transistors near the mean firing rate. LFP-like signals were spatial Gaussian-weighted (σ = 500 µm) averages of transistor switching, low-pass filtered. Granger causality used conditional models of order 20 (BIC plateau) on the LFP-like signals. Dimensionality reduction was non-negative matrix factorization (NMF) with 6 latent dimensions.

## Implications

### A bound on how much "more data" can help

The paper is, in effect, a thought experiment that pushes the data-availability axis to its extreme. For the processor we have what neuroscientists dream of — every neuron's complete activity, every wire's voltage, the full connectome, the ability to lesion any element with surgical precision, behavioral readouts whose ground truth we know. Standard methods still fall short. The implication is not that more data is useless — it is that the marginal value of data is bounded by the analysis methods being applied to it. The bottleneck is not exclusively, or even primarily, data; the bottleneck is methods, theory, and the ability to anchor analyses to ground truth.

### Methodological skepticism for several wiki threads

The paper's specific cautions land directly on themes the wiki has been tracking:

- **The connectome → function gap.** Even with a complete netlist and full activity, connectomics-style cell-type discovery does not recover hierarchical computational organization. This converges with the wiki's [[degeneracy|degeneracy]] thread ([[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt 2019]], [[banerjee-2023-life-stage-chemosensation|Banerjee et al. 2023]]) — a known structure underdetermines function — but extends it from biology into a system where we *know* the function.
- **Tuning ≠ computational role.** Strong luminance tuning in transistors that have nothing to do with luminance generation directly cautions tuning-curve interpretation in V1, [[place-cells]], and category-selective neurons in [[prefrontal-cortex|PFC]] ([[reinert-2021-pfc-categorization|Reinert 2021]]). What a neuron is "tuned to" is not necessarily what it computes.
- **Dim-reduction caveat for [[computation-through-dynamics|CTD]].** Latent components correlated with behavioral or task variables are necessary but not sufficient evidence that those variables are computed by the population. CTD-style fixed-point analyses partially address this by demanding that the dynamics generate the behavior (sufficiency tests), but the warning stands for any analysis that stops at "this dimension correlates with X."
- **1/f spectra as criticality signatures.** The chip produces power-law LFP-like spectra without being near any computational critical point. Cautions inferences from cortical 1/f to [[edge-of-chaos|criticality / edge-of-chaos]]; statistical signatures alone are not mechanism.
- **Lesion specificity.** Behavioral deficits from local lesions are about which generic computations a behavior happens to require, not about a computational specialization of the lesioned region. Tempers strong inferences from lesion or perturbation studies to "neuron X computes Y."
- **Granger causality.** Functional-connectivity graphs derived from time-series prediction recover some true relationships and some spurious ones, with no internal way to discriminate.

### What the paper does not claim

The paper is careful in its scoping. It does not claim the brain *is* a microprocessor; it explicitly notes the brain is analog, biophysically complex, parallel beyond current chips, with vastly more module diversity and a different (evolutionary) design process. The argument is methodological: if your method does not work on a system simpler than the brain that you understand, you have no principled basis to expect it to work on the brain. Arguments that methods will work for brains *because brains are different from chips* require independent justification.

The paper also explicitly endorses connectomics as a *first* step — for the chip, the connectome is what enables the simulation in the first place — while pointing out that connectome alone, without further analytical machinery, does not deliver computational understanding.

## Connections to Existing Knowledge

- [[degeneracy|Degeneracy]]: Jonas & Kording show *known-structure-underdetermines-function* in a system where we know both the structure and the function — a stronger version of the [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt]] and [[banerjee-2023-life-stage-chemosensation|Banerjee]] biological cases. The chip has only one physical transistor type, yet behavioral lesion specificity and connectivity-cluster analyses produce many "types" — a methodological correlate of degeneracy.
- [[computation-through-dynamics|Computation Through Dynamics]] and [[neural-manifolds|Neural Manifolds]]: dim-reduction-correlated-with-behavior is exactly what CTD-style analyses produce in motor cortex ([[vyas-2020-computation-through-dynamics|Vyas et al. 2020]]). Jonas & Kording's chip-NMF result tempers the strongest reading of those findings: latent dimensions can correlate cleanly with task variables in a system whose computation those dimensions do not capture. CTD's strongest defense against the critique is the *sufficiency test* — RNNs whose recovered dynamics actually produce the target behavior — which goes beyond correlation.
- [[edge-of-chaos|Edge of Chaos]]: 1/f LFP spectra are often invoked as evidence cortex is poised at a critical point. The chip produces similar spectra without any computational critical state; spectral signatures alone cannot distinguish criticality from non-critical dynamics with structured switching. The criticality literature needs mechanistic anchors beyond spectral exponents.
- [[konrad-kording|Konrad Kording]]: bridges his methodological/data-science work (this paper, plus the Jonas & Kording 2015 cell-type-discovery method whose limitations the paper itself documents) with his computational-credit-assignment lineage ([[kording-konig-2001-two-integration-sites|2001]], [[jones-2020-dendritic-computation-power|2020]]) and his constructive methodological sequel ([[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]]).
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]]: the constructive sequel by the same second author. Where this paper demonstrates that standard methods fail to recover Marr-level understanding *even with ground truth*, Lillicrap & Kording (2019) argue we should expect that — trained systems performing at human level across a complex world should resist short-formal-language description at the parameters layer, and the appropriate target is the *principles* (architecture, plasticity rules, developmental program). Together the two papers make the negative + constructive case for the [[principles-vs-parameters|principles-vs-parameters]] reorganization of the neuroscience program.
- [[marrs-levels-of-analysis|Marr's Levels of Analysis]]: the paper's evaluative framework. The processor is understood at all three levels; standard neuroscience methods recover none of them cleanly. Marr's framework is the right benchmark for "what understanding looks like" in this wiki.
- [[circuit-behavior-mapping|Circuit-Behavior Mapping]]: provides a methodological warning for the umbrella thesis that the circuit↔behavior map is many-to-many. Even when you have full ground truth on both ends and the mapping is fully deterministic, current analytical methods cannot recover the mapping from observation.
- [[brette-2018-coding-metaphor|Brette (2018)]]: the philosophical-companion paper. Jonas-Kording show that even with full ground truth, methods do not recover Marr-level understanding. Brette argues that even where methods produce results, the framework that gives them meaning ([[neural-coding|neural coding]]) is incoherent as a basis for theories of brain function. The two papers form a two-front critique: methods do not work, and the metaphor that interprets them is wrong. Together they call for ground-truth-anchored validation of methods *and* a reframing of theory in terms of [[subjective-physics|subjective physics]] / [[sensorimotor-contingencies|sensorimotor contingencies]].
- Predictive-coding / Bayesian-brain frameworks ([[predictive-coding|Rao-Ballard]], [[free-energy-principle|Friston]]): Jonas & Kording's critique applies *less* directly here because predictive-coding theories make architectural and dynamic predictions that go beyond statistical signatures. But the general methodological point — analysis methods need ground-truth-anchored validation — applies to any framework that infers cortical computation from neural recordings.

## Open Questions Raised

- What analysis methods *would* recover the processor's computational hierarchy from data, and what would be required to validate them as transferable to neural systems? The paper opens a research programme but does not solve it.
- Is the appropriate test bed an artificial system (microprocessor, trained ANN) or a small biological system whose computation we partially know (*C. elegans*, mouse retina)? Each has different artifacts.
- Are there analytical signatures that *do* distinguish computationally-loaded structure from the chip-style epiphenomena? Specifically, do sufficiency tests (do the recovered dynamics actually generate the behavior, as in trained-RNN modeling) provide a stronger discriminator than correlation-based tests?
- For [[computation-through-dynamics|CTD]] specifically: how much of the explanatory weight rests on (a) the recovered low-dimensional dynamics as a faithful summary of computation, vs. (b) the trained-RNN sufficiency proof? The chip-NMF finding pushes toward (b) being load-bearing.
- What does it look like to "fix" a brain? Memory neuroprosthetics ([[wierzynski-2009-sleep-hpc-pfc|Berger et al. 2011]]) and sensory neuroprosthetics gesture at one operationalization of understanding — the replace-with-synthetic test. Are there partial successes that demonstrate the levels-of-understanding framework is achievable in neural systems?

## Sources

- Jonas, E. & Kording, K. P. (2017). Could a neuroscientist understand a microprocessor? *PLoS Computational Biology* 13(1):e1005268. DOI: 10.1371/journal.pcbi.1005268.
- Lazebnik, Y. (2002). Can a biologist fix a radio? *Cancer Cell* 2(3):179–182.
- Marr, D. & Poggio, T. (1982). *Vision*. MIT Press.
