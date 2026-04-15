---
title: "Attractor Dynamics"
type: mechanism
aliases: ["attractor networks", "attractor states"]
tags: [dynamical-systems, computation, neural-circuits]
source_count: 4
last_updated: 2026-04-14
level: circuit
---

Attractor dynamics describe neural computation in terms of dynamical systems that evolve toward stable states (**attractors**). A network's state space contains multiple attractors, and the system's behavior is understood by which attractor it occupies, how stable that attractor is, and how the system transitions between attractors.

## Core Concepts

- **Fixed-point attractor**: A single stable state the system converges to (e.g., a stored memory pattern in a Hopfield network)
- **Line attractor**: A continuous set of stable states forming a line in state space
- **Attractor basin**: The region of state space from which trajectories converge to a given attractor
- **Attractor stability**: Determined by the Jacobian of the system dynamics — eigenvalues with negative real parts indicate stability

## Role in PaN

[[li-2024-prediction-noise-reward|Li et al. (2024)]] uses attractor dynamics to explain emergent [[Explore-Exploit Tradeoff|explore/exploit behavior]] in predictive networks:

In the two-neuron PaN system, fixed points are x₀ = s, x₁ = Ws (with W arbitrary), forming **line attractors** in the (x₀, x₁, W) parameter space.

- **No-reward attractor** (s = 0): x₀ = 0, x₁ = 0, W arbitrary. A line along the W-axis. **Unstable under noise** because x₁ = 0 sits exactly on the decision boundary — any motor noise flips the action randomly.
- **Reward attractor** (s = 0.5): x₀ = 0.5, x₁ = 0.5W, W arbitrary. **Stable under noise** because x₁ is nonzero (when W ≠ 0), placing the system away from the decision boundary.
- **Bridge**: The trajectory the system takes when transitioning between attractors, corresponding to exploration behavior.

The three-phase behavioral cycle: sit on reward attractor (exploit) → noise causes drift toward the attractor edge (W → 0) → transit through unstable no-reward region (explore) → land on reward attractor again (exploit).

Stability is formally analyzed via the Jacobian of the stochastic differential equation (SDE) approximation of the discrete PaN dynamics.

## Attractors as Control Structures

From a control-theoretic perspective, attractors are the dynamical structures through which the nervous system implements sensorimotor control. The *C. elegans* limit cycle loops ([[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt, 2019]]) are locomotion control programs — not descriptions of behavior but the mechanism by which the nervous system produces it. The [[Degeneracy|degeneracy]] observation (conserved attractor structure despite variable neurons) follows naturally: if genes encode behavior by shaping neurons' local control algorithms, the attractor landscape is what evolution selects on.

In PaN ([[li-2024-prediction-noise-reward|Li et al. (2024)]]), the attractor landscape organizes reward-seeking behavior in a closed sensorimotor loop — the agent doesn't compute a policy and then act, it *is* the attractor dynamics. Learning (weight changes) reshapes the attractor landscape, and memory, planning, and representation-building can all be understood as machinery that extends the reach of these control structures over longer timescales and more latent variables.

## Broader Context

Attractor dynamics are a major framework in computational neuroscience, used to model:
- **Memory storage and retrieval** (Hopfield networks)
- **Decision-making** (competing attractor states representing different choices)
- **Working memory** (persistent activity maintained by attractor states)
- **Motor control** (movement trajectories as attractor landscapes)

## Limit Cycle Attractors and Neural Manifolds

[[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] demonstrate that *C. elegans* neuronal dynamics trace **limit cycle attractors** — closed loops in a low-dimensional [[Neural Manifolds|manifold]] parameterized by phase (θ) and loop identity (α). Different loops correspond to different motor commands.

Behavioral transitions occur at **merge points** where loops approach each other. At these regions, the system's trajectory becomes dominated by stochastic forces ([[Neural Noise|noise]]), enabling transitions between behavioral states. Where loops are well-separated, the dynamics are deterministic and predictable — the system's position on the manifold predicts behavioral switches up to 30 seconds ahead.

This connects attractor dynamics to [[Degeneracy]]: the manifold structure (the attractors and their arrangement) is conserved across individuals, even though the underlying neuron activation patterns differ.

## Stable Trajectories as Attractors

[[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] generalize the attractor framework: in noisy systems optimized to store information, the relevant attractors are **1D stable trajectories** — all orthogonal directions are contracting, so noise is corrected. The branching and merging of these trajectories (the [[Neural Manifolds|computational scaffold]]) directly maps to the computations performed. This unifies limit cycle attractors (continuous locomotion in *C. elegans*) and transient trajectories (trial-based working memory) under a single framework: both are 1D stable structures whose topology encodes computational strategy.

## Attractors in Cortex: Fixed Points, Line Attractors, Rotations

[[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] catalog attractor structures observed in primate cortex under the [[Computation Through Dynamics|CTD]] framework:

- **Stable fixed points for motor preparation.** In mouse ALM, delay-period activity moves toward stable fixed points corresponding to movement directions; optogenetic perturbation either relaxes back to the fixed point (robust) or hops to a different fixed point producing an incorrect action (Inagaki et al. 2019). A clean discrete-attractor picture of preparation.
- **Line attractor for context-dependent decisions.** PFC in a context-dependent 2AFC task implements the decision by integrating the task-relevant input along a **line attractor** — a linear arrangement of stable fixed points (Mante et al. 2013). Context appears as a slow input that selects which sensory dimension integrates; the irrelevant dimension's input decays along orthogonal directions (dynamics quenching, not gating).
- **Rotational dynamics as approximate limit cycles.** Motor-cortex population activity during reaching traces [[Rotational Dynamics|rotations]] in state space — an approximate low-dimensional oscillator that generates multiphasic muscle patterns (Churchland 2012). Rotations are an instance of limit-cycle-like structure in the cortex, parallel to *C. elegans* locomotion loops at a different scale.
- **Fixed-point finding as methodology.** Fixed-point localization in trained RNNs (Golub & Sussillo 2018) followed by local linearization is the dominant analysis tool for extracting attractor structure from trained networks. This methodology underlies much of the CTD literature.

Across these cases, the same pattern recurs: the relevant computational objects are **structures in the flow** (fixed points, line attractors, limit cycles), and the computation is the trajectory the system takes through them given its inputs.

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — attractor analysis of explore/exploit dynamics in PaN
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — limit cycle attractors in *C. elegans* neural manifold
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — 1D stable trajectories as general attractor framework across systems
- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — fixed points, line attractors, rotational dynamics in cortex; fixed-point finding as analysis tool
