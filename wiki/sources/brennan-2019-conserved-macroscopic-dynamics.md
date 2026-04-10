---
title: "A Quantitative Model of Conserved Macroscopic Dynamics Predicts Future Motor Commands"
type: source
source_type: paper
authors:
  - "Connor Brennan"
  - "Alexander Proekt"
year: 2019
doi: "10.7554/eLife.46814"
tags: [c-elegans, neural-dynamics, manifolds, degeneracy, phase-space, motor-commands, calcium-imaging]
date_ingested: 2026-04-10
key_finding: "Macroscopic neuronal dynamics are conserved across individual C. elegans despite consistent inter-individual differences in neuron activation — a manifold built from ~5% of neurons predicts behavioral switches up to 30 seconds ahead and generalizes across animals."
---

## Overview

Brennan & Proekt develop a method to extract conserved macroscopic dynamics from *C. elegans* whole-brain calcium imaging data. The central insight is that individual neuron activation patterns differ consistently across genetically identical worms performing the same behaviors, yet the global dynamics — expressed as cyclic fluxes through a low-dimensional [[Neural Manifolds|manifold]] — are conserved. The manifold is parameterized by just two variables (phase θ and loop identity α), predicts future motor commands on a cycle-by-cycle basis, and generalizes across individuals observed years apart. This demonstrates a form of [[Degeneracy]]: many microscopic activation patterns map to the same macroscopic dynamics and behavior.

[PDF](../../raw/papers/brennan-2019.pdf)

## Key Findings

### The Averaging Problem

Standard approaches to modeling *C. elegans* neural dynamics fail for a specific reason: individual neuron activation varies consistently across genetically identical animals. This is not random noise — it is structured, reproducible inter-individual variation.

- Only 15 of ~100 recorded neurons could be unambiguously identified across all five animals
- For most neurons, activation differs significantly between individuals in at least one locomotor behavior (e.g., RIML activates consistently across animals during dorsal turns but differently during backward locomotion)
- Averaging neuronal activity across animals produces a pattern that does not resemble any individual worm
- Decoding behavioral state works within each animal (~100% from 15 neurons) but fails completely across animals (chance-level from the same 15 neurons)

This is the fundamental challenge: **simple averaging of microscopic variables destroys behaviorally relevant information**.

### Neuronal Activity vs. Neuronal Dynamics

The paper draws a sharp distinction:

- **Neuronal activity**: the observed activation of individual neurons at each time point — a high-dimensional vector in "activity space"
- **Neuronal dynamics**: the laws of motion governing how the system evolves through phase space — the flux field that determines trajectories

The dynamics are what's conserved across individuals, not the activity. This is why bottom-up models (built from biophysics of individual neurons and synapses) struggle: microscopic parameters are not generalizable, and averaging them disrupts global behavior due to nonlinearities.

### Asymmetric Diffusion Map Modeling

The method extracts dynamics from noisy, high-dimensional, nonlinear neural time series in several steps:

1. **Delay embedding**: Reconstruct phase space from observed neuronal activity using Takens' theorem — the time series and its time-delayed copies span the relevant variables
2. **Asymmetric diffusion mapping**: Construct a transition probability matrix using Gaussian kernels centered on the *next* observed state (not centered symmetrically). This preserves temporal ordering — standard symmetric diffusion maps lose directionality
3. **Spectral analysis**: Extract the dominant cyclic fluxes via the complex eigenvalues/eigenvectors of the asymmetric matrix. Each point gets a phase θ along the dominant flux
4. **Trajectory clustering**: Separate distinct dynamical modes (different loops) to assign flux identity α
5. **Manifold reconstruction**: Average neuronal activity within (θ, α) bins to construct a smooth manifold

The final representation is two-dimensional: **(θ, α)** — phase along a loop and which loop.

### Conserved Manifold Structure

The manifold built from 15 shared neurons across all five animals is nearly identical to one built from all 107 neurons in a single animal. Key results:

- Behavioral state can be decoded from manifold position (θ, α) **83% of the time** across all animals
- A manifold built from four animals accurately decodes the fifth (left-out) animal at **81%**
- The model **predicts the expected time to behavioral switches up to 30 seconds in advance**, validated on a separate cohort of 11 animals observed years later (R² = 0.89)
- Predictions based on manifold dynamics are significantly more accurate than null models based only on dwell time statistics

### Theoretical Argument for Cyclic Fluxes

The paper provides a theoretical motivation for why neuronal dynamics should take the form of cyclic fluxes:

At steady state (probability distribution not changing), the Fokker-Planck equation requires:

dP(X)/dt = 0 = -∇·J(X, t)

The flux J decomposes into a diffusion term and a deterministic driving force. For the flux to be divergence-free (as required at steady state), the deterministic component must be **purely cyclic** — it forms closed loops. This means any non-trivial deterministic dynamics at steady state will be rotational, naturally producing the loop structure the method extracts.

### Degeneracy

The most conceptually important finding: the same macroscopic dynamics emerge from different microscopic activation patterns. This is [[Degeneracy]] — a many-to-one mapping from neural configurations to behavior. The paper argues this makes biological sense: natural selection operates on behavior (the macroscopic level), not on the activation of individual neurons. There is no selection pressure for neuron X to fire identically across individuals, only for the collective dynamics to produce functional behavior.

Prior work on crustacean stomatogastric ganglia (Prinz et al., 2004) showed the same principle: virtually indistinguishable network behavior arises from disparate microscopic configurations. Averaging conductance measurements across individual neurons yields models that fail to burst (Golowasch et al., 2002).

## Methods

- **Organism**: *C. elegans* — 302 neurons total, ~100 head neurons recorded via calcium imaging (GCaMP)
- **Data**: Calcium imaging from Kato et al. (2015) — 5 immobilized worms, ~15 min each. Validation from Nichols et al. (2017) — 11 additional animals
- **Behavioral readout**: Motor command sequences inferred from neuronal activation patterns corresponding to forward locomotion, backward locomotion, dorsal/ventral turns, and reversals
- **Key parameter**: Only 15 neurons consistently identifiable across all individuals — the method works with this sparse subset

## Implications

### For understanding neural computation

The activity of individual neurons is not the right level of description for understanding how a nervous system produces behavior. Even in the simplest model system (302 neurons, fully mapped connectome), individual neuron activation is not conserved across individuals. The conserved quantity is the macroscopic dynamics — the geometry and flow of trajectories through a low-dimensional manifold.

### For the wiki's core themes

- **Converges with the "architecture over units" theme**: [[bennett-2023-history-intelligence-ch1|Bennett (2023)]] argues intelligence differences come from wiring, not the neuronal unit. Brennan & Proekt push further — even the activation patterns within identical wiring vary; what's conserved is the *dynamics* those patterns collectively produce.
- **Extends [[Attractor Dynamics]]**: The manifold loops are limit cycle attractors. Behavioral transitions occur at merge points where loops approach each other and stochastic forces dominate — connecting to [[Neural Noise|noise]] as a driver of behavioral switching.
- **Informs the [[Sparse Coding]] / representation question**: The fact that ~5% of neurons suffice to reconstruct the full dynamics suggests the relevant information is low-dimensional, consistent with the idea that neural representations are structured and redundant.

## Connections to Existing Knowledge

- **[[Attractor Dynamics]]**: Manifold loops are limit cycle attractors; stochastic transitions at merge points explain behavioral switching
- **[[Neural Noise]]**: Noise drives transitions between behavioral states — the system is deterministic when loops are well-separated but stochastic at merge points
- **[[Neural Adaptation]]**: The manifold captures dynamics over time, complementing Adrian's insight that neurons encode change rather than static values
- **[[Predictive Coding]]**: The model predicts future states from current manifold position — the dynamics themselves are predictive

## Open Questions Raised

- Does the manifold framework scale to organisms with more complex nervous systems, or does the higher dimensionality of the dynamics make the approach intractable?
- What is the biological substrate of the conserved manifold? If individual neuron activations differ but dynamics are conserved, what physical properties enforce this constraint?
- How does the manifold change during learning? If an animal acquires a new behavior, does this correspond to a topological change in the manifold (new loop) or a parametric change (modified flow)?
- What determines which neurons are informative for manifold reconstruction? Is there a principled way to identify the ~5% that matter?

## Sources

Brennan & Proekt (2019). eLife 8:e46814.
