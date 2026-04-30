---
title: "Maximum Entropy Principle"
type: theory
aliases: ["MaxEnt", "MaxEnt principle", "principle of maximum entropy", "Jaynes principle"]
tags: [bayesian-inference, information-theory, statistical-mechanics, free-energy, foundations, predictive-coding, sparse-coding]
source_count: 1
last_updated: 2026-04-27
status: established
---

The **maximum-entropy principle** (MaxEnt) states that, given a set of expectation-value constraints `⟨f_k⟩` on a probability distribution `p_i`, the unique distribution that is "maximally noncommittal with regard to missing information" is the one that maximizes the Shannon entropy `H = −Σ p_i ln p_i` subject to those constraints. The result is `p_i ∝ exp(−Σ_k λ_k f_k(x_i))`, with Lagrange multipliers `λ_k` fixed by the constraints. Introduced in this form by [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] as the constructive criterion underlying statistical mechanics, MaxEnt has become the formal foundation of the Bayesian-brain program: every "implicit prior" invoked in [[predictive-coding|predictive coding]], the [[Variational Free Energy|free-energy principle]], [[active-inference|active inference]], and [[sparse-coding|sparse coding]] is, formally, a MaxEnt distribution under whichever constraints the system has registered.

## The principle

Given a discrete state space `x_1, …, x_n`, a known set of expectation values `⟨f_k(x)⟩ = Σ_i p_i f_k(x_i)` for `k = 1, …, m`, and the normalization `Σ_i p_i = 1`, infinitely many distributions are typically consistent with the constraints. MaxEnt picks the unique one that maximizes Shannon entropy:

`maximize H(p) = −Σ_i p_i ln p_i  subject to  ⟨f_k⟩ = Σ_i p_i f_k(x_i),  Σ_i p_i = 1.`

Lagrange-multiplier elimination gives

`p_i = exp(−λ_0 − Σ_k λ_k f_k(x_i)),  Z(λ) = Σ_i exp(−Σ_k λ_k f_k(x_i)),  λ_0 = ln Z`

with the multipliers determined by the constraint equations `⟨f_k⟩ = −∂ ln Z / ∂λ_k`. The maximized entropy is `S_max = λ_0 + Σ_k λ_k ⟨f_k⟩`.

## Why MaxEnt is unique

Two desiderata force this answer:

1. **Consistency.** The same problem posed in different ways must give the same answer. Shannon (1948) showed that the only measure of uncertainty satisfying continuity, monotonicity, and the composition law is `H = −K Σ p_i ln p_i`. Other candidate measures (e.g., `−Σ p_i²`) lack the composition property and produce contradictions when carried far.
2. **Maximal noncommitment.** Anything narrower than the MaxEnt distribution smuggles in information not given by the constraints. The MaxEnt distribution assigns positive weight to every state not absolutely excluded — the maximally honest representation of one's actual ignorance.

## Special cases that recover known distributions

- **Constraint = mean** → exponential distribution.
- **Constraint = mean + variance** → Gaussian distribution (the MaxEnt distribution on the real line under those moments). This is why Gaussian priors are the "default" in Bayesian inference: they are the maximally noncommittal continuous distribution under mean and variance constraints.
- **Constraint = energy of microstate** → Boltzmann distribution `p_i ∝ exp(−E_i / kT)`. The Lagrange multiplier `λ_1 = 1/kT` is the inverse temperature.
- **Constraint = energy + particle numbers** → grand canonical ensemble. The conjugate multipliers are the chemical potentials.
- **Constraint = energy + volume** → Lewis-Siegert pressure ensemble.
- **Constraint = no information** (only normalization) → uniform distribution. This recovers Laplace's principle of insufficient reason as a degenerate special case.
- **Constraint = a kurtosis-like measure** → heavy-tailed (e.g., Cauchy-like, Student-t-like) distributions. These are the priors that produce sparse codes when used in MAP inference.

The fact that the canonical, grand-canonical, and pressure ensembles of statistical mechanics drop out of MaxEnt without any specifically physical assumption is the central content of [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]: statistical mechanics is a special case of statistical inference.

## Why this matters for the brain

The brain is constructing probability distributions over hidden causes from partial sensory data. Jaynes's framework says: given the constraints (sufficient statistics, expectation values) the brain has registered, the unique unbiased prior is the MaxEnt distribution under those constraints. This converts the otherwise-fuzzy claim "the brain has Bayesian priors" into a constructive specification.

### Predictive coding

The Rao-Ballard energy function ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]) has the form

`E = (1/σ²) ‖I − f(Ur)‖² + (1/σ²_td) ‖r − r^td‖² + g(r) + h(U)`

where `g(r)` is a negative log-prior on activities. With `g(r) = α Σ r_i²`, the prior is Gaussian — the MaxEnt prior under a variance constraint. With `g(r) = α Σ log(1 + r_i²)`, the prior is heavy-tailed — the MaxEnt prior under a kurtosis-like constraint, which produces sparse codes. Predictive coding, viewed through the MaxEnt lens, is MAP inference under a MaxEnt prior whose constraints are encoded in the choice of `g`.

### Free-energy principle and variational inference

Variational free energy `F(d; θ, Q) = ⟨E⟩_Q − H[Q]` is *the Lagrangian* whose stationary points are MaxEnt distributions. Maximizing `H[Q]` subject to a constraint on `⟨E⟩_Q` (with `E` = negative log joint of generative model and data) is exactly the Jaynes variational problem. [[karl-friston|Friston]]'s [[free-energy-principle|free-energy principle]] ([[friston-2010-free-energy-principle|Friston 2010]]) is therefore not idiosyncratic to neuroscience — it is the local-recognition specialization of MaxEnt inference applied to a generative model with hidden causes and actions.

### Sparse and efficient coding

Heavy-tailed priors that produce [[sparse-coding|sparse codes]] from natural images are MaxEnt priors under higher-moment constraints. The efficient-coding hypothesis of Attneave (1954) and Barlow (1961), made formal, is a MaxEnt argument: a sensory system maximizes information transmission under channel-capacity constraints by adopting the MaxEnt encoding distribution. The convergence of multiple optimization criteria on V1-like Gabor receptive fields under [[natural-image-statistics|natural-image]] training (sparse coding, ICA, predictive coding, efficient coding) is unified by the observation that all are doing MaxEnt-style inference under different but related constraints derived from the same input distribution.

### Energy-based memory

The Boltzmann distribution `p(s) ∝ exp(−E(s)/T)` over [[hopfield-network|Hopfield-network]] states is the MaxEnt distribution under an energy constraint. Temperature `T = 1/λ` is the conjugate Lagrange multiplier. The fact that energy-based memory models have a meaningful "temperature" parameter for retrieval dynamics is, in this language, just the statement that they are MaxEnt distributions whose Lagrange multiplier can be tuned.

### Population-activity modeling

A direct empirical bite: maximum-entropy models of multi-neuron spike-train data (Schneidman, Berry, Segev & Bialek 2006; Tkačik et al. 2014) fit a MaxEnt distribution to recorded activity using only pairwise correlations as constraints, then ask how well it predicts higher-order statistics. The success of pairwise MaxEnt models at predicting near-zero higher-order correlations in retinal populations is a *direct* empirical instance of MaxEnt inference being the right framework for neural-population-level prediction, with the constraints chosen to be biologically plausible (pairwise spike-spike correlations).

## Heat, temperature, and thermodynamic forces are inference

Jaynes generalizes Clausius's `dS = dQ/T` to all conjugate-pair constraints:

`δS = Σ_k λ_k [δ⟨f_k⟩ − ⟨δf_k⟩] = Σ_k λ_k δQ_k`

where `δQ_k` is the "heat of the k-th type" — the part of `δ⟨f_k⟩` not accounted for by deterministic changes in `f_k` itself. Each constraint thus has its own conjugate "temperature." Conventional thermodynamic temperature is the special case where `f_1` = energy. The same identity holds for any exchanged quantity. The lesson: the rich algebra of thermodynamics — extensivity, Maxwell relations, conjugate-pair structure — is a consequence of the MaxEnt variational form, not of physical law specifically. Wherever the brain runs MaxEnt-style inference, it inherits this structure: there is, in principle, a "neural-activity temperature," a "synaptic-strength temperature," etc., conjugate to whatever constraints the system has registered.

## What MaxEnt does *not* tell us

- **Which constraints to register.** MaxEnt determines the prior given the constraints, not the constraints themselves. The constraint-discovery problem — what sufficient statistics an organism should track over evolutionary and developmental time — is the deep open question for adaptive intelligence, and Jaynes's framework does not address it.
- **How to implement it.** The framework is implementation-agnostic. Whether the brain implements MaxEnt-shaped inference in synaptic weights, recurrent dynamics, dendritic compartments, or some combination is a separate (biological) question.
- **Time-dependent prediction.** Equilibrium MaxEnt requires the equations of motion in addition to the inference framework to predict dynamics. Real brains are out-of-equilibrium dynamical systems on every timescale shorter than learning. The non-equilibrium extension ("max-caliber" / path-MaxEnt) exists in physics; its application to neural dynamics is largely open.

## Relationship to other concepts

- **[[variational-free-energy|Variational Free Energy]]** — variational free energy is the Lagrangian whose stationary points are MaxEnt distributions; free-energy minimization *is* MaxEnt inference.
- **[[predictive-coding|Predictive Coding]]** — predictive-coding energy functions are MaxEnt log-priors plus prediction-error terms.
- **[[active-inference|Active Inference]]** — the embodied / recurrent specialization of MaxEnt to agents that act on their environments.
- **[[sparse-coding|Sparse Coding]]** — heavy-tailed activity priors are MaxEnt priors under higher-moment constraints.
- **[[natural-image-statistics|Natural Image Statistics]]** — efficient-coding-style optimization on natural images is MaxEnt inference under input-statistics constraints.
- **[[helmholtz-machine|Helmholtz Machine]]** — the Helmholtz free energy `−F = log p(d|θ) − KL[Q‖P]` is a special case of the Jaynes variational identity.
- **[[hopfield-network|Hopfield Network]]** / **[[energy-landscape|Energy Landscape]]** — the Boltzmann distribution over Hopfield states is the MaxEnt distribution under an energy constraint.
- **[[spin-glass|Spin Glass]]** / **[[replica-method|Replica Method]]** — replica-method calculations average over MaxEnt (Gibbs) distributions; the framework being averaged over is MaxEnt by construction.
- **[[hebbian-learning|Hebbian Learning]]** / **[[meister-2022-learning-fast-slow|Meister (2022)]]** — building a sparse code = registering a new constraint; MaxEnt over states given constraints determines what the system finds plausible. The slow timescale of representation building is the timescale of constraint accumulation.

## Sources

- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — "Information Theory and Statistical Mechanics." Establishes MaxEnt as the unique unbiased prior under expectation-value constraints; derives the canonical / grand-canonical / pressure-ensemble distributions; identifies thermodynamic temperature with the energy-conjugate Lagrange multiplier; reframes statistical mechanics as statistical inference.
