---
title: "Neural Manifolds"
type: concept
aliases: ["neural manifold", "low-dimensional dynamics", "population dynamics"]
tags: [dynamical-systems, dimensionality-reduction, phase-space, neural-circuits, computation]
source_count: 2
last_updated: 2026-04-10
confidence: established
---

A neural manifold is the low-dimensional surface in neural state space along which population activity is constrained to evolve. Although neural activity is high-dimensional (one dimension per neuron), the collective dynamics often lie on or near a manifold of much lower dimension, reflecting the structured, coordinated nature of neural computation.

## Core Idea

If you record N neurons simultaneously, each time point is a vector in N-dimensional space. In principle, the system could explore all of this space. In practice, neural activity traces out trajectories confined to a low-dimensional subspace — the manifold. The manifold's geometry and the flow of trajectories along it capture the essential dynamics of the system.

## Manifold Structure in C. elegans

[[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] extracted the manifold of *C. elegans* neuronal dynamics and found it can be parameterized by just two variables:
- **θ** (phase): position along a cyclic trajectory (loop)
- **α** (flux identity): which loop the system is on

Different loops correspond to different motor commands (forward locomotion, backward locomotion, etc.). The system evolves deterministically along loops and transitions stochastically between them at merge points — regions where loops approach each other and [[Neural Noise|noise]] dominates.

The manifold built from only 15 neurons (~5% of the nervous system) is nearly identical to one built from all 107 recorded neurons, suggesting the dynamics are low-dimensional and robustly recoverable from sparse observations.

## The Computational Scaffold

[[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] introduce **LOOPER**, which approximates neuronal dynamics as collections of interlocking **1D stable trajectories**. The theoretical argument: in noisy systems optimized to store information, only 1D structures are fully stable — all orthogonal directions push back toward the trajectory, correcting noise perturbations. Higher-dimensional structures contain marginally stable directions where noise accumulates uncorrected.

The resulting **computational scaffold** is a graph of trajectories that branch and merge over time:
- **Branching** = the system making a computational distinction (encoding information)
- **Merging** = the system discarding information no longer task-relevant
- **Persistent separation** = maintained information storage

The scaffold directly reveals *what* information a system stores, *when* decisions are made, and *when* information is discarded — a computational interpretation of manifold geometry, not just a geometric one.

LOOPER supersedes the asymmetric diffusion map method from the [[brennan-2019-conserved-macroscopic-dynamics|2019 paper]], handling trial-based tasks, multiple timescales, and diverse recording modalities (validated on *C. elegans*, mouse LFPs, primate PFC, human fMRI, and RNNs, all with R² > 0.79).

## Extraction Methods

Manifold extraction from neural data typically involves:
1. **Delay embedding** (Takens' theorem) — reconstruct phase space variables from time-delayed copies of observables
2. **Dimensionality reduction** — PCA, diffusion maps, isomap, or similar methods to find the low-dimensional structure
3. **Dynamical analysis** — characterize flow along the manifold (fixed points, limit cycles, transition probabilities)

LOOPER combines these steps using **asymmetric diffusion mapping** (kernels centered on the next observed state to preserve temporal ordering), hierarchical clustering to find stable states, and trajectory extraction via edit distance. The final model parameterizes each point by trajectory identity (α) and phase (θ).

## Relationship to Attractor Dynamics

Neural manifolds and [[Attractor Dynamics]] are complementary descriptions:
- Attractors are the stable states or trajectories the system converges to
- The manifold is the geometric surface on which these attractors and the transitions between them are embedded

In *C. elegans*, the manifold loops are limit cycle attractors. The manifold framework adds the spatial structure — how loops are arranged relative to each other, where they merge, and how the flow varies along them. In trial-based tasks (working memory, theory of mind), the trajectories are not cyclic but sequential — the scaffold's branching structure captures the task's computational demands.

## Manifolds as the Geometry of Control

The neural manifold is the space in which the organism's control dynamics play out. In *C. elegans*, different loops on the manifold correspond to different motor commands — the manifold literally *is* the locomotion control system's state space. Behavioral transitions at merge points are control decisions, driven by [[Neural Noise|noise]] when the system reaches a dynamical ambiguity.

This framing connects manifolds to the [[Degeneracy|degeneracy]] observation: if genes encode behavior by constraining neurons' nonlinear control algorithms, then what's conserved across individuals is the manifold (the control landscape), not the neuronal activations. The manifold is what evolution sees and selects on.

For more complex systems, the manifold framework extends naturally. The computational scaffold ([[brennan-2023-looper-computational-scaffold|Brennan et al., 2023]]) captures not just motor control but any task requiring information storage and decision-making — working memory, categorization, theory of mind. Each of these can be understood as the control loop operating over increasingly abstract state spaces, with the scaffold's branching/merging structure revealing when information enters and leaves the loop.

## Implications

The manifold perspective suggests that the right level of description for neural computation is neither individual neurons nor bulk averages, but the **geometry of population dynamics**. This connects to [[Degeneracy]]: many different microscopic configurations (individual neuron activations) can produce the same manifold structure, because the manifold is a property of the collective dynamics, not of any individual element. The computational scaffold extends this further — architecturally distinct systems (monkey PFC vs. RNN) can share the same scaffold structure despite having nothing in common at the unit level.

## Sources

- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — conserved manifold dynamics in *C. elegans*
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — LOOPER method, computational scaffold, cross-system comparison
