---
title: "Mouse Prefrontal Cortex Represents Learned Rules for Categorization"
type: source
source_type: paper
authors:
  - "Sandra Reinert"
  - "Mark Hübener"
  - "Tobias Bonhoeffer"
  - "Pieter M. Goltstein"
year: 2021
doi: "10.1038/s41586-021-03452-z"
tags: [prefrontal-cortex, categorization, learning, two-photon-imaging, category-selectivity, rule-learning, semantic-memory]
date_ingested: 2026-04-11
key_finding: "Category-selective neurons in mouse medial prefrontal cortex emerge gradually during learning, generalize to novel stimuli, and flexibly remap during rule switches — suggesting PFC category representations are part of semantic memory, not instantaneously recruited."
---

## Overview

This paper tracks the formation of category representations in mouse medial prefrontal cortex (mPFC) across the entire learning process using chronic two-photon calcium imaging. Mice learn to categorize sinusoidal gratings by one feature dimension (spatial frequency or orientation) in a Go/NoGo task, then switch to a different rule. The key finding: category-selective neurons emerge *gradually* during training, starting from near-zero selectivity in naive animals and building up over weeks of reinforced learning. These representations generalize immediately to novel stimuli, and during a rule switch, Go-preferring neurons remap to the new Go category while NoGo-preferring neurons are replaced by a new population. This gradual emergence argues that mPFC category representations are part of a specific semantic memory built up during learning, rather than being instantaneously assigned or recruited ad hoc.

[PDF](../../raw/papers/reinert-2021.pdf)

## Key Findings

### Task Design

Mice (n = 11) were trained on a Go/NoGo visual categorization task with sinusoidal gratings varying along two dimensions: orientation and spatial frequency. At any time, one dimension was the relevant feature for categorization (e.g., spatial frequency determines Go vs NoGo), while the other was irrelevant. Training proceeded in stages, gradually increasing the number of stimuli from 2 up to 18 (and finally 36 for generalization testing). Two-photon imaging sessions (T1–T8) were interleaved across the training timeline.

After learning Rule 1, the relevant and irrelevant dimensions were swapped (Rule 2), requiring the mice to recategorize the same stimuli according to a different feature.

### Mice Learn Rule-Based Categorization

All mice achieved >66% correct within 10–40 sessions, with considerable individual variability. Key behavioral results:
- Mice generalized to novel stimuli on their first presentation, performing equally well on novel and experienced stimuli
- Untrained mice showed no effect of either stimulus feature on categorization — the selectivity is learned, not innate
- Categorization was based on the relevant dimension only; the irrelevant dimension had no systematic effect on choices

### Gradual Emergence of Category Selectivity

Category-selective neurons were identified using a category-tuning index (CTI): values near 1 indicate strong differences in activity between categories, values near 0 indicate none. Threshold: CTI > 0.1.

- **Before learning (T1)**: Only 0.03% ± 0.03% of mPFC neurons were category-selective. Essentially none.
- **After learning (T5)**: 8.8% ± 2.2% of neurons were category-selective.
- CTI correlated with Bayesian decoding performance (Spearman's rho = 0.41, P = 2.2 × 10⁻³⁰), confirming that category-selective cells reliably encode category information.
- The emergence was **gradual**: individual neurons showed characteristic time courses of acquiring selectivity, with Go-preferring neurons tracking the gradual acquisition of category Rule 1 and NoGo-preferring neurons following later.

This gradual build-up — over days to weeks of reinforced training — is the central finding. It argues against models where PFC neurons are instantaneously recruited or assigned to represent task-relevant categories.

### Two Populations with Distinct Dynamics

Category-selective cells split into two groups:
- **Go-preferring** (~73% of category-selective cells at T5): higher firing rates for Go-category stimuli
- **NoGo-preferring** (~35% at T5): higher firing rates for NoGo-category stimuli

The populations showed more overlap than expected by chance. Both developed selectivity gradually, but Go-preferring neurons emerged somewhat earlier, consistent with Go responses being more actively reinforced (water reward).

### Rule Switch: Remapping vs. Replacement

When the categorization rule switched (Rule 1 → Rule 2):
- **Go category-selective neurons remapped**: they switched their responses to track the new Go category. The same neurons that preferred one set of stimuli under Rule 1 now preferred a different set under Rule 2.
- **NoGo category-selective neurons were replaced**: they lost selectivity after the rule switch, and a new set of cells became NoGo category-selective for the newly defined categories.
- **Rule 2 was learned faster**: steeper learning curve slope (P = 1.9 × 10⁻⁷) and earlier inflection point (P = 9.3 × 10⁻⁷) compared to Rule 1, despite reaching the same maximum performance.

This asymmetry between Go and NoGo populations during rule switching is striking. It suggests different mechanisms or different functional roles for the two populations — Go neurons may track the "target" category flexibly, while NoGo neurons are more tied to specific stimulus-category associations.

### Mixed Selectivity and Multiple Task Variables

Beyond pure category selectivity, mPFC neurons showed **mixed selectivity** — modulation by combinations of category, choice (lick vs no-lick), and reward. Clustering analysis revealed neurons modulated primarily by category (clusters 1, 2, 3), by choice and reward (cluster-like groupings), and by specific combinations of task parameters (clusters 4, 5, 9). This is consistent with recent findings in primate and mouse PFC of mixed selectivity after animals learn cognitive tasks.

### Category Tuning Generalizes Across Tasks

After learning both rules, mPFC neurons that were category-selective maintained their selectivity even when tested with uninstructed behaviours (whisking, eye movements). The category signal was not simply a motor or decision-related correlate — it persisted in passive viewing contexts, consistent with a genuine semantic representation.

## Methods

- **Subjects**: 11 head-fixed mice, female C57BL/6 × DBA/2 F1 hybrids
- **Imaging**: Chronic two-photon calcium imaging (GCaMP6m) through a microprism implant over mPFC, cortical layer 2/3. 8 imaging sessions (T1–T8) spanning the entire learning process.
- **Stimuli**: 36 sinusoidal gratings varying in orientation (6 levels) and spatial frequency (6 levels)
- **Task structure**: Go/NoGo with water reward for correct Go responses; time-out for false alarms
- **Analysis**: Category-tuning index (CTI) for individual neurons; Bayesian decoder for population-level readout; generalized linear model to assess individual neuron contributions of category, choice, and reward
- **Stereotaxic verification**: Imaging regions confirmed within mPFC (ACC, PL, MO regions)

## Implications

### For understanding how representations form during learning

This paper provides direct evidence that category representations in PFC are **gradually built up** during learning — they are part of the memory of the learned categories, not instantaneously assigned working memory states. This is phenomenologically consistent with [[meister-2022-learning-fast-slow|Meister's (2022)]] claim that slow learning reflects slow representation building. However, there are important caveats: Reinert images PFC (likely the decision/readout side), not sensory cortex (where Meister's sparse codes would be built). The gradual emergence of PFC selectivity could reflect slow upstream sensory code construction, slow rule learning at the PFC level, or both — the experiment can't distinguish these.

### For understanding rule switching and flexibility

The asymmetric dynamics during rule switching — Go neurons remapping, NoGo neurons being replaced — suggest that PFC category representations are not monolithic. Different populations may serve different functional roles (target detection vs. inhibition), with different update mechanisms. The faster learning of Rule 2 demonstrates savings/transfer, though the mechanism is underspecified.

## Connections to Existing Knowledge

- **[[Sparse Coding]]**: The ~9% of mPFC neurons becoming category-selective is a sparse representation at the population level. The gradual emergence is consistent with the idea that useful representations must be built before efficient learning can occur. However, PFC category selectivity is more likely a decision-level readout than the sensory-level sparse code that Meister's framework centers on.
- **[[Hebbian Learning]]**: The gradual, reinforcement-dependent emergence of selectivity is consistent with Hebbian-like processes building category representations over many exposures. The rule-switch dynamics (remapping vs replacement) suggest more complex mechanisms than simple Hebbian association.
- **[[Credit Assignment]]**: How does the brain determine which mPFC neurons should become category-selective? The gradual, distributed emergence (many neurons independently developing selectivity) is more consistent with local learning rules than centralized assignment.

## Open Questions Raised

- Is the gradual emergence of PFC category selectivity driven by slow building of upstream sensory representations (consistent with Meister), slow learning of the categorization rule in PFC itself, or both?
- Why do Go-preferring and NoGo-preferring neurons show asymmetric dynamics during rule switching? What determines whether a neuron remaps vs. loses selectivity?
- Would passive pre-exposure to the grating stimuli (without reinforcement) accelerate subsequent category learning? This would directly test whether the bottleneck is sensory representation building.
- How do the mPFC category representations interact with sensory cortex representations during learning? Simultaneous imaging of both areas would be needed.
- Is the mixed selectivity (category × choice × reward) a feature or a bug? Does it enable flexible recombination of representations, or does it reflect incomplete separation of decision variables?

## Sources

Reinert et al. (2021). *Nature*, 593, 411–417.
