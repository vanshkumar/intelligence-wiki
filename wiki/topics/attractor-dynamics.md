---
title: "Attractor Dynamics"
type: mechanism
aliases: ["attractor networks", "attractor states"]
tags: [dynamical-systems, computation, neural-circuits]
source_count: 9
last_updated: 2026-04-28
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

## Structured Attractors in E-I Populations: Wilson-Cowan

[[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — the structured counterpart to the SCS random-network picture. A two-variable mean-field model of coupled excitatory and inhibitory populations (activities `E(t), I(t)`) has exactly three generic attractor configurations in its (E, I) phase plane:

- **Simple [[Hysteresis|hysteresis]]** (two stable fixed points separated by a saddle): appears when E-E recurrence exceeds a threshold set by the excitatory sigmoid slope, `c₁ > 9/aₑ`. The upper stable fixed point is a persistent-activity state — the attractor-based substrate for short-term memory (Hebb 1949; Cragg & Temperley 1955).
- **Multiple hysteresis** (up to five fixed points, three stable): requires strong E-I negative feedback, `aₑaᵢc₂c₃ > (aₑc₁ − 9)(aᵢc₄ + 9)`. Uniquely E-I; impossible in purely excitatory populations.
- **[[Limit Cycle|Limit-cycle attractor]]** (single unstable fixed point surrounded by a stable periodic orbit): requires `c₁aₑ > c₄aᵢ + 18` — **E-E coupling significantly stronger than I-I coupling**. Limit cycle frequency and amplitude both increase monotonically with input intensity, realizing a frequency-coded intensity representation.

The important **Theorem 4**: any E-I population capable of a limit cycle under some stimulus must also exhibit simple hysteresis under some other stimulus. The same substrate expresses different attractor configurations when nonspecific biases shift it across parameter-space boundaries — a direct instance of [[Context-Dependent Circuit Reconfiguration]] in the attractor framework.

Wilson-Cowan is the structured, low-dimensional, rate-level complement to SCS's generic random-network chaos: the attractor types that SCS finds to be *unstable* in the generic random case (fixed points, limit cycles, multi-stable configurations) are *stable* once the structural E/I asymmetry and sigmoid nonlinearity are imposed. For cortex — which is structured (Dale's law, cell-type segregation) and has the E-I dichotomy by construction — Wilson-Cowan is the right mean-field baseline; chaos requires the additional ingredient of random asymmetric internal coupling within one population.

## Hopfield Attractors and the Spin-Glass Capacity Bound

[[hopfield-1982-collective-computational-abilities|Hopfield (1982)]]-style associative memory is the symmetric-coupling, energy-function counterpart of the random-network picture. For couplings `J_ij = J_ji` the dynamics admit a Lyapunov function `E = −½ Σ_ij J_ij S_i S_j`, so trajectories descend an [[Energy Landscape|energy landscape]] and can only converge to **fixed-point attractors**. [[hebbian-learning|Hebbian]] writing of `p` patterns into the couplings sculpts a basin around each pattern. The same dynamics yield an emergent suite of computational properties — error correction, categorization, familiarity recognition, and graceful soft-failure — that the original Hopfield paper documents in detail and that hold robustly across asymmetric, clipped, and partially-missing variants of the coupling.

The capacity question — how many attractor basins can coexist before catastrophic interference — was answered by Amit, Gutfreund & Sompolinsky (1985, 1987) using the [[replica-method|replica method]] from [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]], sharpening Hopfield's empirical `~0.15 N` rule of thumb. The result sets a sharp bound:

- For `α = p / N < α_c ≈ 0.138`: stored patterns are clean fixed-point attractors with sizable basins. Recall is reliable.
- For `α > α_c`: stored patterns lose stability. The system enters a [[spin-glass|spin-glass phase]] dominated by exponentially many spurious local minima with no relation to the stored patterns.

The capacity bound is **the spin-glass transition** — beyond it, the Hopfield landscape stops looking like a structured ferromagnet and starts looking like a generic frustrated random-coupling system. [[Sparse Coding|Sparse codes]] (small fraction of active spins per pattern) raise this bound by reducing inter-pattern overlap; this is one quantitative form of the wiki's general theme that sparseness mitigates interference.

The Hopfield case is **the symmetric counterpart of [[sompolinsky-1988-chaos-random-networks|SCS]]**: with symmetric `J` you get fixed-point attractors organized as basins in a (possibly rugged) energy landscape, analyzed by replica methods; with asymmetric `J` you get a chaotic attractor with no energy function, analyzed by [[Dynamical Mean-Field Theory|DMFT]]. Cortical connectivity is broadly asymmetric, placing the natural cortical regime closer to SCS than to Hopfield — which is why the wiki treats spin-glass theory as a methodological foundation for associative memory rather than a direct model of cortex. Hopfield's own asymmetry-robustness argument anticipated this: with `T_ij ≠ T_ji` the energy change on a flip splits into a piece identical to the symmetric case plus a stochastic piece with mean 0, so the attractor structure persists with degraded signal-to-noise — a soft bridge into the SCS regime.

## Chaotic Attractors in Random Networks

[[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] establish that in a large network of rate neurons with random asymmetric couplings (mean 0, variance J²/N), the attractor landscape as a function of gain `gJ` has exactly two phases in the N → ∞ limit:

- **gJ < 1**: a single globally stable **point attractor** at zero.
- **gJ > 1**: the zero fixed point destabilizes, and the only stable attractor is a **chaotic attractor** — a strange attractor with a macroscopic (∝ N) number of positive Lyapunov exponents. Nonzero fixed points, limit cycles, and static "spin-glass" freezing states all exist as solutions to the mean-field equations but are all unstable to fluctuations when J is asymmetric.

Two consequences extend the attractor framework:

- **Asymmetry unlocks chaos.** With symmetric J (Hopfield case), the dynamics descend an energy function and can only converge to fixed points. The SCS result shows that breaking detailed balance — via asymmetric Jᵢⱼ — removes the Lyapunov function and admits limit cycles and chaos as generic possibilities. Cortical connectivity, being broadly asymmetric, is in the regime where the richer attractor types are available.
- **Chaos is the generic untrained attractor.** Below the transition the network is silent; above it, no structured (periodic, static) attractor is stable — chaos is what you get. Structured attractors like the rotations and line attractors cataloged elsewhere on this page are **shaped** attractors, produced either by non-random connectivity or by task training that carves low-dimensional stable structure out of the chaotic background. See the substrate discussion on [[Computation Through Dynamics]].

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — attractor analysis of explore/exploit dynamics in PaN
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — limit cycle attractors in *C. elegans* neural manifold
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — 1D stable trajectories as general attractor framework across systems
- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — fixed points, line attractors, rotational dynamics in cortex; fixed-point finding as analysis tool
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — sharp transition from point attractor to chaotic attractor at gJ = 1 in random asymmetric rate networks; structured attractors (fixed points, limit cycles) are unstable in the generic random case
- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — structured rate-level E-I populations have three generic attractor configurations (simple hysteresis, multiple hysteresis, limit cycles) selected by inequalities on four coupling strengths; Theorem 4 on regime interconvertibility by nonspecific biasing inputs
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — the symmetric-`J` half of the random-network problem: hierarchical RSB solution of the SK spin glass, function-valued order parameter `q(x)`, ultrametric organization of pure states; analytical foundation for Hopfield-style associative memory and the capacity bound `α_c ≈ 0.138`
- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — the founding statement of fixed-point attractor networks: symmetric Hebbian-coupled binary neurons, energy function, `~0.15 N` capacity, and the suite of emergent collective properties (error correction, categorization, familiarity recognition, graceful forgetting) that motivate the entire attractor-network programme
- [[friston-2010-free-energy-principle|Friston (2010)]] — frames priors-as-cost-functions on hidden-state motion as **inducing attractors** in the state space the agent occupies. Itinerant / metastable / winner-less-competition dynamics are the multi-attractor correlate of priors over state-trajectories; the [[explore-exploit-tradeoff|exploration / exploitation tension]] becomes the dynamical question of whether the agent's priors induce stable fixed points or itinerant orbits. Figure 3's mountain-car example: a destabilizing prior (negative friction) forces the car out of its starting basin and toward the goal attractor — synthesis of attractor-dynamics with Bayesian inference under [[free-energy-principle|FEP]].
