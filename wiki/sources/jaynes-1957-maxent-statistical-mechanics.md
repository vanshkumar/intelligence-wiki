---
title: "Information Theory and Statistical Mechanics"
type: source
source_type: paper
authors:
  - "E. T. Jaynes"
year: 1957
doi: "10.1103/PhysRev.106.620"
tags: [information-theory, maximum-entropy, bayesian-inference, statistical-mechanics, free-energy, foundations]
date_ingested: 2026-04-27
key_finding: "Statistical mechanics is a special case of statistical inference. Given partial information (typically expectation values of certain observables), the unique maximally noncommittal probability distribution is the one that maximizes Shannon entropy subject to those constraints. This Maximum Entropy (MaxEnt) distribution recovers the Boltzmann, canonical, and grand-canonical distributions as special cases — without ergodicity, equal a priori probabilities, or any specifically physical assumption — and provides the formal foundation of the Bayesian-inference view of brain function."
---

[PDF](../../raw/papers/jaynes-1957.pdf)

## Overview

Jaynes (1957) is a physics paper, but its real contribution is meta-theoretical: it dissolves the apparent specialness of statistical mechanics by showing that *all* of its computational machinery is a particular case of probabilistic inference under partial information. Given the constraints `⟨f_k(x)⟩ = Σ_i p_i f_k(x_i)` and normalization `Σ p_i = 1`, the unique distribution that is "maximally noncommittal with regard to missing information" — i.e., that assigns positive weight to every state not absolutely excluded by the constraints, and that satisfies a small set of consistency conditions — is the **maximum-entropy** distribution

`p_i = exp(−λ_0 − λ_1 f_1(x_i) − … − λ_m f_m(x_i))`

with Lagrange multipliers `λ_k` fixed by the constraints. Set `f_1` = energy and you get the Boltzmann distribution; add `f_2` = particle number and you get the grand canonical ensemble; the inverse temperature is exactly the multiplier `λ_1 = 1/kT`; thermodynamic entropy and Shannon entropy are the same quantity (up to Boltzmann's constant, an artefact of historical units).

This paper does not appear, on its face, to be about the brain. It is on the wiki because every probabilistic / Bayesian / free-energy / predictive-coding framework currently used to model the brain — [[Helmholtz Machine]], [[Predictive Coding]], [[Active Inference]], [[Variational Free Energy]] minimization, [[sparse-coding|sparse coding]] under heavy-tailed priors, the efficient-coding hypothesis — rests on the inference-theoretic stance that Jaynes is articulating. MaxEnt is the formal answer to the question *"what prior should an organism use, given the constraints it has registered about its world?"* The control-theoretic reading: an organism's effective behavior is bounded by its inferred world-model; its inferred world-model is bounded by the constraints (sufficient statistics, expectations) it has measured; MaxEnt is what fixes the prior given those constraints. Anything narrower is unjustified; anything broader throws away available information.

## Key Findings

### 1. MaxEnt as the unique unbiased prior

Given a discrete variable `x` taking values `x_1, …, x_n` and known expectations `⟨f_k⟩` of `m` functions, there are infinitely many distributions consistent with those expectations (when `m + 1 < n`). Two desiderata pick one out:

- **Consistency.** The same problem posed in two different ways must give the same answer. Shannon (1948) showed that the *only* measure of uncertainty `H(p_1, …, p_n)` that is continuous, monotonic in `n` for uniform distributions, and consistent under composite events is `H = −K Σ p_i ln p_i` (Appendix A). Other candidates like `−Σ p_i²` (Fisher, Doob) lack the composition property and lead to contradictions when carried far.
- **Maximal noncommitment.** The unbiased choice is the distribution that is *maximally uncertain* (highest H) subject to the known constraints. Anything narrower than MaxEnt smuggles in information not given.

Maximizing `H` subject to `Σ p_i = 1` and `⟨f_k⟩ = Σ p_i f_k(x_i)` via Lagrange multipliers yields `p_i = exp(−λ_0 − Σ_k λ_k f_k(x_i))`, with multipliers fixed by the constraint equations. The partition function `Z(λ_1, …, λ_m) = Σ_i exp(−Σ_k λ_k f_k(x_i))` plays exactly the role it plays in statistical mechanics:

- `λ_0 = ln Z`,
- `⟨f_k⟩ = −∂ ln Z / ∂λ_k`,
- `⟨f_k²⟩ − ⟨f_k⟩² = ∂² ln Z / ∂λ_k²`,
- `S_max = λ_0 + Σ_k λ_k ⟨f_k⟩` (the maximized entropy).

### 2. Statistical mechanics is statistical inference

Section 3 of the paper performs the move that makes the contribution philosophical rather than just technical. Take `f_1` = energy of microstate `i`. Then `λ_1 = 1/kT`, the canonical (Boltzmann) distribution is the MaxEnt distribution, the free energy `F = −kT ln Z` is `−kT λ_0`, and the entropy of thermodynamics equals (up to `k`) the Shannon entropy of the inferred microstate distribution. Add `f_2, …, f_s` = particle numbers of species 1 to s and you get the grand canonical ensemble; the chemical potentials `μ_i = −kT λ_i`. Add `f` = volume and you get the Lewis-Siegert "pressure ensemble"; `μ = λ P / kT`. Any conserved or exchanged quantity can play the role of "energy" — there is no reason energy is special except that it is the quantity people happened to measure first.

The conventional foundations of statistical mechanics — ergodicity, metric transitivity, equal a priori probabilities — turn out to be **unnecessary** for actually doing the calculation. They are interpretive scaffolding around what is, computationally, just maximum-entropy inference under expectation-value constraints. Jaynes explicitly notes (p. 626) that even if a system is provably *not* metrically transitive, MaxEnt still gives the right inferences from the available macroscopic data; metric transitivity is "far from necessary" for the predictive validity of the formalism.

### 3. Subjective vs objective probability, dissolved

Probability theory in physics had been split between an "objective" school (probabilities = long-run frequencies) and a "subjective" school (probabilities = states of knowledge, in the Laplace-Keynes-Jeffreys tradition). Jaynes argues that for the *prediction* problem of statistical mechanics — given macroscopic measurements, predict further macroscopic behavior — the subjective interpretation is mandatory: the question is what we can infer from data, not what frequencies obtain in some imagined ensemble. The objection that subjective probabilities can't be experimentally tested is answered by the n^(1/2) concentration phenomenon: when the number of microscopic degrees of freedom is large, the MaxEnt distribution over macroscopic functions has a vanishingly narrow peak, so the subjective inference and the observed macroscopic behavior agree to extremely high precision, *as long as the constraints used to derive the MaxEnt distribution are physically right*.

This sharpens the empirical content of MaxEnt: it makes definite predictions only when the available constraints are sufficient to make the distribution narrow. With weak constraints, the prediction shades continuously into "no definite conclusion" — which Jaynes argues is the correct epistemic state in such cases. When MaxEnt makes a sharp prediction and the prediction fails, the right response is *not* to abandon the inference framework but to conclude that the enumeration of states (i.e., the laws of physics) was wrong. This is the move that motivated the development of quantum statistics: the failure of classical MaxEnt for diatomic specific heats was evidence that classical mechanics had the wrong state space, not that the inference machinery was flawed.

### 4. Heat, temperature, and force as inference

In Section 5 Jaynes generalizes Clausius's `dS = dQ/T`. If the constraint expectations `⟨f_k⟩` change by `δ⟨f_k⟩` and the constraint functions themselves change by `δf_k`, then

`δS = Σ_k λ_k [δ⟨f_k⟩ − ⟨δf_k⟩] = Σ_k λ_k δQ_k`

where `δQ_k = δ⟨f_k⟩ − ⟨δf_k⟩` is the "heat of the k-th type" — the change in expectation that *cannot* be accounted for by a deterministic change in the function itself. Each constraint thus acquires its own conjugate "temperature" `λ_k`. The conventional thermodynamics of heat and temperature is the special case where `f_1` = energy. The same identity holds for any exchanged quantity: there is a "particle temperature" (chemical potential), a "volume temperature" (pressure / kT), and so on. A thermometer is just a device whose pointer reads off the conjugate Lagrange multiplier of the system in contact with it.

### 5. The pressure ensemble and a nuclear-polarization prediction

Section 5 closes with two applications. The first re-derives the Lewis-Siegert pressure ensemble from MaxEnt under simultaneous energy and volume constraints. The second predicts a *nuclear polarization in a rotating sample*: a body rotating at angular velocity `ω` with moment of inertia `B` has nuclear spins polarized along the rotation axis, equivalent to applying a magnetic field of strength `B ω / ℏ`. The numerical estimate (water rotated at 36 000 rpm yields polarization equal to a ~1/7 gauss field) is offered as testable. The mechanism doesn't require any specific spin-lattice coupling; it falls out of the MaxEnt distribution given the macroscopic constraints alone. (This is the Barnett effect, observed experimentally; Jaynes's derivation is a nontrivial demonstration that MaxEnt produces correct novel physics from inference principles alone, not just re-derivations of known results.)

## Methods

This is a theoretical paper. The "method" is a constructive variational argument:

1. **Posit** a measure of uncertainty `H(p_1, …, p_n)` and require it satisfy three composition / consistency conditions. Shannon's theorem (sketched in Appendix A) forces `H = −K Σ p_i ln p_i`.
2. **Maximize** `H` subject to normalization and any number of expectation-value constraints `⟨f_k⟩ = Σ p_i f_k(x_i)` using Lagrange multipliers.
3. **Identify** the resulting `p_i = exp(−Σ λ_k f_k)` with the canonical / grand-canonical / pressure-ensemble distributions of statistical mechanics, and the multipliers with `1/kT`, chemical potentials, etc.
4. **Apply** the framework to non-physics inference problems — given `⟨x⟩`, infer `⟨x²⟩`, and conversely; observe that the regression curves are non-symmetric (Section 3 example, equations 3-10 and 3-11). This makes vivid that MaxEnt is a general inference procedure, not a physics-specific calculation.
5. **Generalize** Clausius's `dS = dQ/T` to all conjugate-pair constraints (Section 5).

## Implications

### For the Bayesian-brain program

Every contemporary "brain as a Bayesian inference engine" framework — [[Predictive Coding]], the Free Energy Principle, [[Active Inference]], the [[Helmholtz Machine|Helmholtz machine]] lineage, predictive-processing accounts of perception and action — assumes that the brain is constructing probability distributions over hidden causes from partial sensory data. Jaynes provides the answer to *which* distribution: under the MaxEnt criterion, the distribution is fully determined by the constraints (sufficient statistics, expectation values) the brain has registered. The "implicit prior" of a cortical area is, formally, a MaxEnt distribution over the constraints encoded by its synaptic weights and circuit structure. This converts the often-fuzzy claim "the brain has Bayesian priors" into a constructive specification: priors = MaxEnt under the registered constraints, full stop.

### For sparse and efficient coding

The kurtotic / heavy-tailed prior on neural activities used by [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — `g(r) = α Σ log(1 + r_i²)` — is a MaxEnt prior under a soft kurtosis constraint. More broadly, the [[sparse-coding|sparse-coding]] result that V1-like Gabor receptive fields emerge from heavy-tailed priors plus natural-image data is, formally, a Bayesian MAP inference under a MaxEnt prior given the higher-moment statistics of [[natural-image-statistics|natural images]]. The efficient-coding hypothesis (Attneave 1954; Barlow 1961) becomes literally a MaxEnt argument: a sensory system maximizes information transmission under channel-capacity constraints by adopting the MaxEnt encoding distribution.

The point is not that any specific cortical mechanism explicitly computes Lagrange multipliers — it almost certainly does not — but that whichever mechanism the brain uses is *forced* toward a MaxEnt-shaped solution by the constraints it operates under, the same way physical systems are forced toward Boltzmann distributions by their dynamics. The MaxEnt principle is what makes "brain implements Bayesian inference" not vacuous: it specifies the unique unbiased prior given the constraints.

### For the control thesis

An organism's effective control over its environment is bounded by what it can infer about the latent state of the world. What it can infer is bounded by the constraints — the sufficient statistics of its observations — that its sensory and learning machinery has registered. MaxEnt closes the loop: given those constraints, the organism's optimal world-model *is* the MaxEnt distribution. Extending control therefore reduces to extending the set of registered constraints — precisely the slow process of [[sparse-coding|sparse-code construction]] in [[meister-2022-learning-fast-slow|Meister (2022)]] and [[reinert-2021-pfc-categorization|Reinert et al. (2021)]]. The slow timescale of representation building is the timescale of adding new MaxEnt constraints; once added, fast inference and fast Hebbian association become possible.

### For the foundations of free-energy minimization

Variational free energy `F(d; θ, Q) = ⟨E⟩_Q − H[Q]` is, in its general form, *the Lagrangian* whose stationary points are MaxEnt distributions. Maximizing `H[Q]` subject to a constraint on `⟨E⟩_Q` (with `E` = negative log joint of generative model and data) is exactly Jaynes's variational problem. Friston's Free Energy Principle is therefore not an idiosyncratic objective specific to neuroscience — it is the local-recognition specialization of the MaxEnt framework, applied to a generative model with hidden causes. The "minimize free energy" imperative is, formally, "produce the MaxEnt posterior over hidden causes given the sensory constraints."

### What does *not* automatically translate

The paper is about *equilibrium* statistical inference: what to predict given some current macroscopic measurements. Jaynes is explicit that prediction of *time-dependent* phenomena requires the equations of motion in addition to MaxEnt — the inference framework alone cannot generate dynamics. By analogy, the MaxEnt foundation tells us what the brain's *priors* should look like given its constraints, but it does not tell us how those priors are *implemented* in synapses and dynamics. The biological implementation question — predictive-coding circuits, dendritic prediction errors, wake-sleep, etc. — is a separate problem the paper does not address. This matters because some of the recent free-energy-principle literature reads as if MaxEnt-style arguments determine biological mechanism. They do not; they only determine the form of the inference the mechanism must implement.

A second caveat: Jaynes's framework requires the constraint set to be *given*. In statistical mechanics it's given by which observables one happens to measure (energy, particle number, volume). In biology, the analog is *which sufficient statistics the brain has chosen to register* — and this is itself a learned property of the organism, shaped over evolutionary and developmental time. The framework therefore assumes away the very thing biologists want to explain. MaxEnt tells you the optimal prior given the constraints; it doesn't tell you which constraints to register. That second question — call it the constraint-discovery problem — is the deep one for understanding how brains build their world-models, and it is *not* answered by Jaynes.

## Connections to Existing Knowledge

- **[[Predictive Coding]]** — predictive-coding energy functions are MaxEnt log-priors on neural activity plus prediction-error terms. The kurtotic prior `g(r) = α Σ log(1 + r_i²)` in [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] is a MaxEnt prior under a kurtosis constraint; the Gaussian prior is the MaxEnt prior under a variance constraint.
- **[[Variational Free Energy]]** — variational free energy `F = ⟨E⟩_Q − H[Q]` is the Lagrangian whose stationary points are MaxEnt distributions. Free-energy minimization is, in its general form, MaxEnt inference.
- **[[Active Inference]]** — Friston's Free Energy Principle is the embodied / recurrent specialization of Jaynes's MaxEnt framework. The "implicit prior" Friston invokes is, formally, a MaxEnt prior over the constraints the agent has registered.
- **[[Helmholtz Machine]]** — Dayan-Hinton 1994's `−F` lower bound is a special case of the Jaynes variational identity, with the constraint being the data likelihood and the recognition distribution Q playing the role of the inferred MaxEnt approximation to the true posterior.
- **[[sparse-coding|Sparse Coding]]** — heavy-tailed priors that produce sparse codes from natural images are MaxEnt priors under higher-moment (kurtosis, sparsity) constraints. The Olshausen-Field optimization is Bayesian MAP inference under such a prior.
- **[[natural-image-statistics|Natural Image Statistics]]** — the efficient-coding hypothesis, when made formal, is a MaxEnt argument: the optimal encoding distribution maximizes entropy subject to channel-capacity and input-statistics constraints.
- **[[Hopfield Network]]** — the Boltzmann distribution `p(s) ∝ exp(−E(s)/T)` over Hopfield states is the MaxEnt distribution under an energy constraint. The connection of Hopfield-style energy-based memory to MaxEnt explains why temperature is a meaningful control parameter for retrieval dynamics.
- **[[Spin Glass]] / [[Replica Method]]** — replica-method calculations in disordered systems compute averages over MaxEnt (Gibbs) distributions; the framework of statistical mechanics that the replica trick assumes is the framework Jaynes is showing is general inference.
- **[[Energy Landscape]]** — the "energy" of a Hopfield or spin-glass state is, in MaxEnt terms, just the negative log of an unnormalized prior. Energy-landscape thinking and MaxEnt thinking are the same picture from different angles.
- **[[meister-2022-learning-fast-slow|Meister (2022)]]** — the "sparse code as Bayesian prior" framing of fast vs slow learning is sharpened by MaxEnt: building a sparse code = registering a new constraint; the MaxEnt prior over states-given-constraints determines what the system finds plausible. Slow learning is the slow timescale of constraint accumulation.

## Open Questions Raised

- **The constraint-discovery problem.** MaxEnt determines the prior given the constraints, but says nothing about *which* constraints (sufficient statistics) a brain should register. Real organisms must choose, from an enormous set of possible observables, which ones to track over evolutionary and developmental time. Is there a principled second-order theory — MaxEnt over constraint-sets, or something analogous — that picks which constraints to register? This is the question that distinguishes adaptive intelligence from frozen Bayesian prior-machinery.
- **Where does the brain implement MaxEnt priors?** If predictive-coding circuits are computing MaxEnt-like inferences, *which* anatomical structure encodes the constraints? Synaptic weights? Recurrent dynamics? Dendritic compartments? The Jaynes framework is implementation-agnostic, but biology is not. Pinning the constraints to specific cellular substrates would let one predict how priors should change under specific perturbations (LTP/LTD, dendritic plasticity, etc.).
- **Non-equilibrium inference.** Jaynes is explicit that his framework is for *equilibrium* prediction; time-dependent phenomena need additional structure. Real brains are emphatically out-of-equilibrium dynamical systems on every timescale shorter than learning. The correct extension of MaxEnt to non-equilibrium inference (max-caliber, path-MaxEnt) is an active research area in physics; its application to neural dynamics is largely open.
- **Sufficient statistics in learned codes.** When the cortex builds a [[sparse-coding|sparse code]], it is implicitly choosing which statistics of the input distribution to register as constraints. Can we read out, from a recorded neural population, which "MaxEnt constraints" it has come to use? Maximum-entropy models of neural population activity (Schneidman et al. 2006; Tkačik et al. 2014) attempt exactly this — and their success at predicting higher-order correlations from pairwise constraints is a direct empirical bite at the question.
- **Does the dark-room problem dissolve under MaxEnt?** The [[Dark Room Problem]] — why don't free-energy-minimizing agents seek out maximally predictable environments? — looks different from the MaxEnt angle. MaxEnt is *unbiased* given constraints, not minimum-surprise; an agent that registers richer constraints over time (i.e., extends control) has a *higher*-entropy prior, not a lower one. The dark-room agent has impoverished its constraint set, which is the opposite of what MaxEnt-style intelligence does.

## Sources

- Full text: [Jaynes (1957), "Information Theory and Statistical Mechanics," *Phys. Rev.* 106(4), 620–630](../../raw/papers/jaynes-1957.pdf).
- Companion paper: Jaynes (1957b), "Information Theory and Statistical Mechanics II," *Phys. Rev.* 108, 171, extends the formalism to time-dependent (irreversible) processes via the density matrix — the foundation of what became "max-caliber" / path-MaxEnt inference.
