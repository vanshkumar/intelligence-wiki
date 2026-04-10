---
title: "One Dimensional Approximations of Neuronal Dynamics Reveal Computational Strategy"
type: source
source_type: paper
authors:
  - "Connor Brennan"
  - "Adeeti Aggarwal"
  - "Rui Pei"
  - "David Sussillo"
  - "Alexander Proekt"
year: 2023
doi: "10.1371/journal.pcbi.1010784"
tags: [neural-dynamics, manifolds, computation, working-memory, c-elegans, primate, fmri, rnn, degeneracy]
date_ingested: 2026-04-10
key_finding: "Neuronal dynamics across diverse systems (C. elegans to human fMRI) can be approximated as interlocking 1D trajectories whose branching and merging — the 'computational scaffold' — directly reveals what information the system stores, when decisions are made, and when information is discarded."
---

## Overview

This paper introduces **LOOPER**, a general method for extracting simple, interpretable models of neuronal dynamics from complex, noisy, nonlinear neural time series. LOOPER approximates dynamics as collections of interlocking **1D stable trajectories**, producing a **computational scaffold** — a graph of branching and merging trajectories that directly maps to the computations the system performs. The method generalizes [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]], superseding the earlier asymmetric diffusion map approach with a more flexible framework that handles trial-based tasks, multiple timescales, and diverse recording modalities. LOOPER is validated across five systems: RNNs, *C. elegans* calcium imaging, mouse visual cortex LFPs, primate prefrontal cortex neurons, and human fMRI BOLD signals.

[PDF](../../raw/papers/brennan-2023.pdf)

## Key Findings

### Why 1D Trajectories?

The paper provides a theoretical argument for why optimized neural dynamics should be well approximated by 1D trajectories:

In noisy dynamical systems (ẋ = f(x, u) + ε), information stored in initial conditions degrades over time via diffusion. To counteract this, the system must minimize two properties:
- **Divergence**: the rate at which nearby trajectories separate (information loss)
- **Tangling**: when trajectories from different initial conditions cross or approach, making the future state ambiguous

Minimizing both simultaneously constrains the dynamics to **1D stable trajectories** — structures where all orthogonal directions push back toward the trajectory, correcting noise perturbations. Higher-dimensional stable structures (sheets, volumes) inevitably contain marginally stable directions where noise accumulates. This is why neuronal population trajectories in cortical areas involved in movement planning specifically avoid divergence and tangling.

### LOOPER Method

LOOPER builds on diffusion mapping but departs from the 2019 asymmetric diffusion map approach in important ways:

1. **Asymmetric diffusion mapping** — same core idea (center kernels on next observed state to preserve temporal ordering), but now applied generally to trial-based and continuous data
2. **Hierarchical clustering** — coarse-grain the transition probability matrix using minimum description length (MDL) to find stable states while preserving divergence
3. **Trajectory extraction** — cluster repeated state sequences into trajectories using a modified edit distance, then interpolate to produce continuous 1D curves
4. **Computational scaffold** — assign each experimental timepoint a trajectory ID and phase, producing a graph of branching/merging trajectories over time

The final model: dynamics along each trajectory α evolve via a Markov chain (α, θ)ₜ₊₁ = M·(α, θ)ₜ. The system follows a trajectory in an ordered fashion, with stochastic switches between trajectories at merge/branch points.

### The Computational Scaffold

The scaffold is the paper's central conceptual contribution. It is a graph showing trajectory identity over time, where:

- **Branching** = the system making a computational distinction. When trajectories diverge, the system is encoding information that distinguishes conditions (e.g., different stimulus values, different task states)
- **Merging** = the system discarding information. When trajectories converge, the system has decided that a distinction is no longer task-relevant
- **Persistent separation** = the system maintaining stored information across time

The scaffold directly reveals the computational strategy: *what* information is stored, *when* decisions are made, and *when* information is discarded. This is not inferred post hoc — it emerges automatically from the trajectory extraction.

### Cross-System Comparison: Monkey vs. RNN

The most striking result. A monkey prefrontal cortex and an RNN trained on the same working memory task (compare two vibrotactile frequencies F1 and F2) show:

- **Completely different neuronal activity**: CCA finds ~25% variance explained in monkey, ~51% in RNN across canonical dimensions. Linear projections that maximize similarity explain almost no variance.
- **Identical computational scaffold structure**: same number of trajectories, same branching pattern (diverge on F1 encoding, bifurcate on F1 vs. F2 comparison), same convergence at task end

However, the systems employ **different computational strategies**:
- **Monkey (general algorithm)**: stores F1, compares to F2 — works correctly on all novel combinations
- **RNN (exploit strategy)**: discovers that F1=20 and F1=40 give identical F2 comparison results, so it merges their representations. This "exploit" fails on novel F1/F2 combinations where the merged values would need to be distinguished

The scaffold **predicts the specific errors the RNN will make on novel stimuli** — confirmed at 99% accuracy. This demonstrates that the scaffold captures not just the geometry but the actual computational content of the dynamics.

### Cross-Scale Validation

LOOPER faithfully reconstructs dynamics across vastly different systems and scales:

| System | Signal type | Reconstruction R² |
|--------|-----------|-------------------|
| RNN | LSTM unit activity | 0.99 |
| *C. elegans* | Calcium imaging (GCaMP) | 0.79 |
| Mouse | Visual evoked LFPs | 0.87 |
| Primate | PFC single neurons | 0.80 |
| Human | fMRI BOLD | 0.84 |

LOOPER also outperforms HMMs on task decoding while matching reconstruction accuracy, because LOOPER's trajectory structure is inherently interpretable.

### Human Theory of Mind

Applied to fMRI BOLD signals from a theory of mind task (do shapes in a video appear to interact mentally?), LOOPER extracts two trajectories that diverge ~5 seconds before the subject's behavioral response — consistent with gradual evidence accumulation during the movie, culminating in a binary decision. Brain regions with highest trajectory separation cluster in left-hemisphere areas associated with language processing and social cognition (dorsomedial PFC, temporal parietal junction).

## Methods

- **LOOPER pipeline**: Diffusion mapping → hierarchical clustering (MDL) → trajectory extraction (edit distance) → scaffold construction
- **Key assumption**: Neuronal dynamics can be well approximated by 1D stable trajectories. This holds for trial-based classification tasks but may not hold for open-ended, continuous interaction with the environment
- **Parameters**: Three main — neighborhood size, repopulation density, total bins. Method is robust to the latter two; neighborhood size should approximate the number of similar trials

## Implications

### Computational scaffold as a universal language

The scaffold provides a common language for comparing computations across architecturally distinct systems. The monkey-RNN comparison demonstrates this: despite having nothing in common at the level of individual units, the two systems' scaffolds are directly comparable and reveal both shared structure (same branching pattern) and different strategies (general vs. exploit). This could enable systematic comparison of how different brain regions, species, or artificial systems solve the same computational problem.

### Biological vs. artificial learning strategies

When trained on the same stimulus statistics, the monkey learns the general algorithm while the RNN exploits dataset-specific shortcuts. This resonates with the wiki's recurring theme that biological systems invest in general-purpose representations and strategies, while the specific learning rules are simple. The RNN's "exploit" strategy is a form of overfitting to the training distribution — something biological evolution may specifically select against because environments change.

### Relationship to the 2019 paper

LOOPER supersedes the asymmetric diffusion map method from [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]. The 2019 method relied on eigendecomposition to find cyclic fluxes, which only works when a single rotational mode dominates. LOOPER directly extracts trajectories without assuming cyclic structure, handles multiple timescales, works on trial-based data, and produces the computational scaffold as an interpretable output. The *C. elegans* results from 2019 are reproduced and extended.

## Connections to Existing Knowledge

- **[[Neural Manifolds]]**: LOOPER is the current best method for extracting interpretable manifold structure; the computational scaffold adds a computational interpretation to the geometric description
- **[[Degeneracy]]**: The monkey-RNN comparison extends the concept from "same dynamics despite different neuron activation" to "same computational scaffold despite different architectures entirely"
- **[[Attractor Dynamics]]**: 1D stable trajectories are attractors; branching/merging at specific points mirrors the attractor transition framework
- **[[Sparse Coding]] / [[meister-2022-learning-fast-slow|Meister (2022)]]**: The scaffold reveals what information is stored — directly related to the question of whether the representation or the learning rule is the bottleneck
- **[[Predictive Coding]]**: The scaffold shows when and where the system stores predictive information about future task events

## Open Questions Raised

- Does the 1D trajectory assumption hold for open-ended tasks involving continuous interaction with a changing environment (e.g., spatial navigation, foraging)?
- Can the computational scaffold reveal how biological systems *learn* a task — does the scaffold restructure during learning, and if so, how?
- Why do biological systems consistently find general strategies while RNNs exploit dataset statistics? Is there a structural or learning rule difference that drives this, or is it simply a consequence of evolutionary selection pressure for generalization?
- Can scaffolds be compared formally (not just visually) across systems to quantify computational similarity?

## Sources

Brennan et al. (2023). PLoS Computational Biology 19(1): e1010784.
