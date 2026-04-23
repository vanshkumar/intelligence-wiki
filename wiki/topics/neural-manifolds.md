---
title: "Neural Manifolds"
type: concept
aliases: ["neural manifold", "low-dimensional dynamics", "population dynamics"]
tags: [dynamical-systems, dimensionality-reduction, phase-space, neural-circuits, computation]
source_count: 6
last_updated: 2026-04-22
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

## The Intrinsic Manifold Constrains Learning

The strongest within-subject evidence that manifolds are real constraints on learning comes from BCI experiments in primate motor cortex, reviewed in [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]]:

- **Sadtler et al. (2014)**: monkeys readily learn BCI perturbations that require only within-manifold dynamics (hours) but struggle with off-manifold perturbations. The intrinsic manifold is a ~10D subspace containing the bulk of M1 population variance during reaching; perturbations that push the cursor mapping off this subspace are not learnable on short timescales.
- **Golub et al. (2018)**: within-manifold learning proceeds by **neural reassociation** — animals re-use neural states from their pre-learning repertoire, pairing them differently with cursor targets, rather than discovering new states. Learning is a change of *mapping* from state to action, not a change of *state repertoire*.
- **Oby et al. (2019)**: multi-day training can eventually access out-of-repertoire (within-manifold) and even off-manifold states, revealing multiple learning mechanisms operating at different timescales.
- **Wärnberg & Kumar (2019)**: RNN modeling shows off-manifold learning requires substantial synaptic-weight changes, whereas within-repertoire reassociation requires smaller changes to inputs or minor weight adjustments.

Interpretation for this wiki: the intrinsic manifold is the **control-theoretic repertoire** — the set of dynamical states connectivity and cellular biophysics make accessible. Fast learning operates inside the repertoire; slow, structural learning reshapes it. This is a direct empirical anchor for the control-theoretic reading of [[Degeneracy]]: genes and connectivity constrain the manifold (the accessible dynamical repertoire), and experience reassociates within it at fast timescales. Multi-day off-manifold learning ([[Memory Consolidation|consolidation]]-timescale) is what slow structural change looks like.

## Implications

The manifold perspective suggests that the right level of description for neural computation is neither individual neurons nor bulk averages, but the **geometry of population dynamics**. This connects to [[Degeneracy]]: many different microscopic configurations (individual neuron activations) can produce the same manifold structure, because the manifold is a property of the collective dynamics, not of any individual element. The computational scaffold extends this further — architecturally distinct systems (monkey PFC vs. RNN) can share the same scaffold structure despite having nothing in common at the unit level.

## Theoretical Baseline: The Manifold of a Random RNN

Before connectivity is shaped by genes or experience, what manifold does a random recurrent network occupy? [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] answer this for the canonical random-asymmetric-coupling ensemble: above the chaotic transition (gain gJ > 1), the network's activity lives on a **bounded, finite-dimensional attractor embedded in N-dimensional state space**. The flow on it is deterministically chaotic, with a macroscopic (∝ N) number of positive Lyapunov exponents.

This is the theoretical counterpart to the empirical manifolds observed in recordings (Sadtler 2014; Gallego 2017; Brennan & Proekt 2019). The ~10D intrinsic manifold of motor cortex or the 2D loop structure of *C. elegans* can be read as the trained/shaped descendant of this generic dynamical repertoire — connectivity structure (Dale's law, sparsity, low-rank task-relevant perturbations) constrains the SCS flow to a specific lower-dimensional subset. Manifold-constrained BCI learning is, in this framing, reassociation within the trained manifold; off-manifold learning is restructuring of the flow itself.

### In-silico counterpart: FORCE-trained manifolds

[[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] provide the in-silico version. PCA of [[force-learning|FORCE]]-trained activity shows the output target is captured by ~8 leading PCs, and the readout weight projections onto the top ~50 PCs converge to uniquely specified values across training runs; projections onto smaller-eigenvalue PCs are free and differ across runs. The trained manifold is carved out of the SCS chaotic reservoir: training selects a low-dimensional subspace within the generically high-dimensional chaotic flow, and within it determines a smaller uniquely-specified structure, leaving the remaining dimensions free. This is the mechanistic model for why empirical manifolds are low-dimensional and why BCI manifold-constrained learning is possible — the manifold is what training selects.

## Sources

- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — conserved manifold dynamics in *C. elegans*
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — LOOPER method, computational scaffold, cross-system comparison
- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — BCI manifold-constrained learning (Sadtler 2014, Golub 2018, Oby 2019) as strongest within-subject evidence that manifolds are real constraints on learning
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — theoretical baseline: random asymmetric rate networks have an extensively high-dimensional chaotic flow on a bounded finite-dimensional attractor; the substrate from which shaped/trained manifolds are carved
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — in-silico counterpart: FORCE-trained RNNs show ~8-PC output-relevant and ~50-PC uniquely-determined subspaces carved out of the chaotic reservoir by training; mechanistic model for empirical intrinsic manifolds
