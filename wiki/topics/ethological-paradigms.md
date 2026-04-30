---
title: "Ethological Paradigms"
type: concept
aliases: ["naturalistic tasks", "ethology-first neuroscience", "2AFC critique"]
tags: [methodology, behavior, experimental-design, learning-rate]
source_count: 3
last_updated: 2026-04-29
confidence: emerging
---

Ethological paradigms are experimental designs that let animals behave in task structures resembling their natural repertoire — multi-step foraging, spatial navigation, overnight unsupervised exploration — in contrast to trial-based laboratory paradigms (2AFC, fixed-duration trials, delay-match-to-sample) that tightly constrain the animal's behavioral options. The argument for them is empirical: ethological tasks reveal learning dynamics, decision rates, and behavioral structure that trial-based tasks cannot resolve.

## The Critique of 2AFC

[[meister-2022-learning-fast-slow|Meister (2022)]] argues from literature review that laboratory 2AFC tasks occupy the *slowest* corner of biological learning — animals extract ~10⁻⁴ bits per trial, compared to ~1 bit per trial for fear conditioning, Bruce effect, and food aversion. Task complexity does not explain this gap: simple 2AFC (1 bit) is slower than maze navigation (9+ bits). What differs is whether the task falls within the animal's natural repertoire and whether pre-existing [[Sparse Coding|sparse codes]] for the relevant stimuli exist.

[[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] make the argument empirical. In the same lab, same species, same time period:

- **2AFC**: ~100 decisions/hour, thousands of trials to criterion
- **Labyrinth**: ~2000 decisions/hour (20× higher), asymptotic navigation after ~10 rewards, one-shot home-path learning, sudden insight transitions

The labyrinth exposes behavioral phenomena (one-shot learning, sudden insight, intrinsic exploration, local turning biases) that are structurally invisible in 2AFC.

## Why Trial-Based Paradigms Miss Real Learning

Several features of lab 2AFC actively obscure learning dynamics:

1. **Low decision throughput** — trial structure caps decisions at hundreds per session, so fast learning cannot be distinguished from slow learning at the per-event level
2. **Averaging across animals** — smooth population learning curves hide individual sudden-insight transitions that appear discretely in single-animal data ([[Sudden Insight]])
3. **Narrow behavioral repertoire** — the task provides only two choices, so behaviors like persistent exploration, home-path learning, or local turning biases cannot be measured
4. **Arbitrary stimulus-response mappings** — tasks often require associations the animal has no pre-existing [[Sparse Coding|sparse code]] for, so the paradigm ends up measuring *representation building* rather than *associative learning*
5. **Removed from closed-loop structure** — trial-based tasks clamp the sensorimotor loop to a single decision point per trial, suppressing the continuous sense-predict-act-update dynamics that constitute normal operation

## Relation to the Control Thesis

Ethological paradigms align naturally with the wiki's organizing principle. If intelligence begins with closed-loop sensorimotor control, then the correct experimental substrate is one where the loop runs continuously and the animal's action shapes its next sensory input. Trial-based paradigms artificially open the loop between trials, destroying the temporal structure in which the nervous system actually operates. Naturalistic tasks preserve the loop and reveal what it is actually doing.

## Counterpoint

2AFC and related paradigms are not useless: they provide the precise parametric control needed to dissect specific computations (adaptation, discrimination thresholds, evidence accumulation). The argument is not that trial-based tasks should be abandoned but that they should be understood as one corner of behavioral space — and that the fast-learning, ethologically natural corner is where the most dramatic features of biological intelligence become visible.

## Methodological link to the coding-metaphor critique

[[brette-2018-coding-metaphor|Brette (2018)]] gives the deepest reason trial-based paradigms produce the appearance of clean coding results: tightly controlled experiments are precisely the conditions under which "the brain encodes parameter X" is most defensible — because the experimenter has fixed everything else. Outside that regime, [[neural-coding|tuning curves]] are context-dependent (orientation tuning depends on surround, on task, on locomotion, on prior auditory stimuli) and "encoding" claims fail. Ethological paradigms are not just behaviorally richer; they expose the *contextual fragility* of coding-style descriptions and force theory in the direction of full sensorimotor loops ([[sensorimotor-contingencies|sensorimotor contingencies]] / [[subjective-physics|subjective physics]]). The wiki's ethological thread and Brette's coding critique are the same critique at different levels: behavioral (Rosenberg, Meister) and theoretical (Brette).

## Sources

- [[meister-2022-learning-fast-slow|Meister (2022)]] — literature-wide critique: learning rates span 10,000×, with slow 2AFC tasks as outliers
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — empirical demonstration: overnight labyrinth exposes learning phenomena invisible in 2AFC
- [[brette-2018-coding-metaphor|Brette (2018)]] — theoretical complement: trial-based paradigms are the conditions under which coding-style descriptions are most plausible because everything is held fixed; ethological paradigms expose the context-dependence that makes coding-style descriptions fail outside the lab.
