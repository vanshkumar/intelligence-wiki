---
title: "Chaos in Random Neural Networks"
type: source
source_type: paper
authors:
  - "Haim Sompolinsky"
  - "Andrea Crisanti"
  - "Hans-Jürgen Sommers"
year: 1988
doi: "10.1103/PhysRevLett.61.259"
tags: [random-networks, chaos, dynamical-mean-field-theory, phase-transition, edge-of-chaos, rnn, theory]
date_ingested: 2026-04-15
key_finding: "A large random recurrent network with asymmetric Gaussian couplings undergoes a sharp transition from a silent fixed point to deterministic chaos at gain gJ = 1. The transition and the chaotic flow are described exactly (N → ∞) by a time-dependent mean-field theory."
---

## Overview

Sompolinsky, Crisanti & Sommers (SCS) study a continuous-time network of N nonlinear rate neurons with randomly drawn asymmetric synaptic couplings Jᵢⱼ (i.i.d. Gaussian, zero mean, variance J²/N, Jᵢᵢ = 0). Each neuron obeys

```
ḣᵢ = −hᵢ + Σⱼ Jᵢⱼ φ(hⱼ),   φ(x) = tanh(gx)
```

The only intensive parameter is the dimensionless **gain** `gJ`. Using a time-dependent **dynamical mean-field theory** (DMFT) — exact in the N → ∞ limit — they show:

- **gJ < 1**: the zero fixed point `hᵢ ≡ 0` is globally stable. Activity decays silently.
- **gJ > 1**: the zero fixed point loses stability. The only stable long-time solution of the MFT is a **chaotic flow** whose autocorrelation `C(τ) = ⟨φ(hᵢ(t)) φ(hᵢ(t+τ))⟩` decays monotonically to zero. Fixed points, limit cycles, and "spin-glass" static states all exist in the MFT equations but are all unstable to fluctuations.
- The transition is **sharp** at gJ = 1 in the thermodynamic limit. Near criticality, `h(t) ≈ ε · sech²(εt/√3)` with `ε ≡ gJ − 1`; correlation time diverges as τ ∝ 1/ε.
- The **maximal Lyapunov exponent** λ is obtained from a one-dimensional Schrödinger-like eigenvalue problem for fluctuations about the MFT solution: `λ = −1 + √(1 − E₀)` where E₀ is the ground state energy of the fluctuation potential W(t) = −∂²V/∂Δ². For the chaotic solution λ > 0, vanishing as λ ~ ε²/2 near gJ = 1⁺ and diverging as ln(gJ) in the high-gain Ising limit. The number of positive Lyapunov exponents is extensive (∝ N) above the transition.
- Finite-N simulations (N up to 1000) show an intermediate regime of nonzero fixed points and limit cycles of increasing complexity between gJ = 1 and the chaotic regime; that intermediate regime shrinks to zero as N → ∞, consistent with the MFT prediction of a sharp transition.

[PDF](../../raw/papers/sompolinsky-1988.pdf)

## Key Findings

**1. A sharp chaotic transition at gJ = 1.** In the thermodynamic limit, a random asymmetrically-coupled rate network has exactly two phases as a function of gain: a silent fixed point and a high-dimensional chaotic flow. No fine-tuning is required; it is a generic property of the ensemble.

**2. DMFT reduces N coupled equations to a single self-consistent neuron.** The dynamics of a typical neuron at long times are described by `ḣ(t) = −h(t) + η(t)` where η is a Gaussian process whose covariance `⟨η(t)η(t+τ)⟩ = J² C(τ)` is determined by the single-neuron statistics it generates — a self-consistency closed via `C(τ) = ⟨φ(h(t))φ(h(t+τ))⟩`. The autocorrelation satisfies a classical-mechanics-like equation `Δ̈ = −∂V/∂Δ` in an effective self-consistent potential V. This reduction is the paper's principal technical contribution and the template for decades of DMFT applied to neural dynamics.

**3. Chaos is the generic stable state above criticality.** Among the many candidate solutions of the MFT equations (nonzero fixed points, limit cycles of various amplitudes, static "spin-glass" freezing), only the monotonically decaying autocorrelation — i.e., chaos — is stable to fluctuations. Periodic and static solutions all yield a positive fluctuation eigenvalue, hence unstable.

**4. The Lyapunov exponent is extensively positive.** Above gJ = 1, a macroscopic (∝ N) fraction of Lyapunov exponents are positive. This distinguishes the flow from low-dimensional chaos (few degrees of freedom, few positive exponents): the chaos here is **extensive** and intrinsically high-dimensional, though it lives on a finite-dimensional attractor.

**5. Near-criticality behavior.** As gJ → 1⁺, the flow amplitude vanishes as `h(0) ~ ε` and the timescale diverges as `1/ε`. The Lyapunov exponent vanishes as `ε²/2`. This slowing-down at the edge of chaos is what later theoretical work (Bertschinger & Natschläger 2004; Toyoizumi & Abbott 2011) ties to maximal computational capacity and maximal input sensitivity — the origin of the "edge of chaos" framing for reservoir and trained RNN operation.

## Methods

- **Model**: Continuous-time rate network, tanh nonlinearity, Gaussian i.i.d. asymmetric couplings with Jᵢᵢ = 0 and variance J²/N. The Jᵢⱼ are quenched disorder — fixed per realization, not dynamical variables.
- **Dynamical mean-field theory**: borrowed and extended from spin-glass theory (Sompolinsky & Zippelius 1982). Treats Σⱼ Jᵢⱼ φ(hⱼ) as a Gaussian process whose covariance is self-consistent with single-neuron statistics. Exact in the N → ∞ limit.
- **Stability analysis via a Schrödinger-like operator**. Fluctuations `χᵢⱼ(t, t') = δhᵢ(t)/δhⱼᵒ(t')` are analyzed via a 1D eigenvalue problem whose potential W(t) = −∂²V/∂Δ² is set by the MFT solution. Positive Lyapunov exponent corresponds to a bound state of negative energy.
- **Numerics**: Direct simulation of the N-body ODE for N up to 1000 confirms sharp transition and characterizes the finite-N intermediate regime.

## Implications

### For Computation Through Dynamics

This paper defines what recurrent networks can do *before* training. The [[Computation Through Dynamics|CTD]] program fits RNNs to tasks and reads out the structure of the trained dynamics; but the substrate those trained dynamics are carved out of is precisely the SCS ensemble. Two specific consequences:

- **Initialization regime matters.** RNNs trained for CTD analyses (Sussillo 2015, Mante 2013, Sohn 2019) are typically initialized with gJ > 1 — in the chaotic regime or just above the transition. The trained dynamics (rotations, line attractors, fixed points) are attractor structures *carved out of* the underlying chaotic reservoir. Task training suppresses most of the chaos while preserving just enough dynamical richness for the task.
- **Extensive dimensionality is available.** The macroscopic number of positive Lyapunov exponents means random RNNs contain, in principle, an extensive amount of computational capacity. The question training answers is: which subspace of this flow is used?

### For reservoir computing and the edge of chaos

SCS is the canonical theoretical anchor for the [[Edge of Chaos]] framing. Operating near gJ = 1 — where correlation times diverge and the dynamics are marginally chaotic — was later argued (in a long line: Langton 1990; Bertschinger & Natschläger 2004; Legenstein & Maass 2007; Toyoizumi & Abbott 2011; Sussillo & Abbott 2009 in the FORCE setting) to give the best tradeoff between memory (long timescales) and separability (input sensitivity). Echo state networks and liquid state machines operate in this regime by construction.

### For noise vs. deterministic variability

The chaos here is **deterministic**: Jᵢⱼ are fixed, φ is deterministic, no stochasticity is injected. Yet the resulting activity is irregular, unpredictable at long times, and statistically characterized like a noise process. This is a concrete instance of what deterministic high-dimensional flow contributes to apparent neural variability — an alternative (or complement) to stochastic-channel noise as the source of trial-to-trial variability in cortex.

### For the control thesis

Random recurrent networks are the "blank substrate" of cortical dynamics: before circuitry is shaped by genes and experience, what generic dynamical repertoire is available? SCS answers: above gJ = 1, an extensively high-dimensional chaotic flow living on a low-dimensional manifold. The [[Degeneracy|control-theoretic reading of degeneracy]] can then be restated: genes tune gJ and the structure of J (asymmetry, sparsity, Dale's law) so that the dynamical repertoire available to experience is neither silent nor purely chaotic, but structured enough to be sculpted into task-appropriate control policies.

## Connections to Existing Knowledge

- **[[Computation Through Dynamics]]**: SCS establishes the substrate. CTD-analyzed RNNs are task-trained descendants of SCS networks; training selects task-relevant subspaces from the SCS chaotic reservoir.
- **[[force-learning|FORCE learning]] ([[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]])**: the foundational constructive descendant. Sussillo & Abbott start from the SCS chaotic regime (`g = 1.5`), leave the recurrent connectivity random, and show that simple readout / feedback-weight modification can carve out arbitrary coherent outputs. The best training performance is at the largest `g` where FORCE still suppresses the chaos (`g ≈ 1.5`, fails at `g ≈ 1.56`) — turning SCS's edge-of-chaos slowing-down into a concrete operational prescription for training.
- **[[Attractor Dynamics]]**: SCS's chaotic flow is itself an attractor — a **strange attractor**, not a point, line, or cycle. The paper shows that fixed-point, limit-cycle, and static spin-glass attractors are all *unstable* in random asymmetric networks; chaos is the stable attractor.
- **[[Neural Noise]]**: SCS is the canonical model of **deterministic chaos as a source of apparent neural variability**. Firing-rate irregularity that looks stochastic may be deterministic chaos from recurrent interactions.
- **[[Neural Manifolds]]**: The chaotic attractor lives on a bounded, finite-dimensional manifold inside the N-dimensional state space. The intrinsic manifold observed in recordings (Sadtler 2014; Gallego 2017) is the trained/shaped descendant of this geometrically constrained flow.
- **[[meister-2022-learning-fast-slow|Meister (2022)]]** theme of *simple rules, rich representations*: SCS is a clean example — the rule is a trivial leaky-integrator ODE with random weights, but the collective dynamics are extensively high-dimensional and sensitive to inputs.
- **Contrast with symmetric couplings (Hopfield)**: If Jᵢⱼ = Jⱼᵢ, the dynamics are gradient descent on a spin-glass energy and always converge to fixed points. Asymmetry is what unlocks non-relaxational dynamics — chaos, limit cycles, rotations. This is why cortical circuits, which are broadly asymmetric, are dynamically rich.
- **Structured rate-level sibling**: [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] treats the *structured* E-I counterpart of SCS's random asymmetric ensemble. Where SCS shows that a random asymmetric network generically has only two phases — silent fixed point and high-dimensional chaos — Wilson-Cowan shows that once the E/I dichotomy is imposed by construction and couplings are structured around cell-type separation, the dynamics have a rich three-regime repertoire (simple hysteresis, multiple hysteresis, limit cycles) organized by inequalities on four mesoscopic coupling strengths. The periodic and fixed-point attractors that are *unstable* in the generic random case (SCS) are *stable* once the structural E/I asymmetry and sigmoid nonlinearity are imposed (WC). Real cortex, being structured (Dale's law, cell-type segregation), is closer to the Wilson-Cowan baseline; chaos in cortex requires the additional ingredient of random asymmetric internal coupling within one population. WC is also the founding [[Neural Mass Model]] and the methodological ancestor of the mean-field-reduction tradition SCS operates in at the rate level.
- **Static / equilibrium sibling**: [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] is the static counterpart of SCS for the *symmetric*-coupling random-network problem. Where SCS uses [[Dynamical Mean-Field Theory|DMFT]] to extract time-dependent quantities (autocorrelations, Lyapunov spectrum) for asymmetric `J`, Parisi uses [[replica-method|replica symmetry breaking]] to extract equilibrium quantities (free energy, overlap distribution) for symmetric `J`. The two methods together cover the analytical toolkit by which random-network statements become rigorous: replica handles statics and detailed-balance regimes (Hopfield-style associative memory), DMFT handles dynamics and non-detailed-balance regimes (chaotic cortical-style RNNs). The capacity bound `α_c ≈ 0.138 N` for the Hopfield network (Amit-Gutfreund-Sompolinsky 1985) is the canonical neuroscience application of Parisi's machinery.
- **Spiking-network sibling**: [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] is the spiking analogue of SCS for sparsely connected E-I integrate-and-fire networks. Both reduce an N-body random-network problem to a self-consistent single-neuron picture (DMFT autocorrelation equation vs. Fokker-Planck for the membrane-potential distribution); both establish that "irregular, noise-like" activity in cortex is a generic consequence of the random connectivity ensemble rather than a signature of stochastic channel noise. SCS gives the rate-level chaos transition at gJ = 1; Brunel gives the spiking-level four-regime phase diagram ([[Asynchronous Irregular State|AI]], AR, SR, SI) with the balance point g = 4 as the analogous edge.

## Open Questions Raised

- What changes when couplings are **structured** (Dale's law, sparsity, low-rank perturbations, spatial topography)? Recent work (Mastrogiuseppe & Ostojic 2018 on low-rank RNNs; Schuessler 2020 on training-induced low-rank perturbations of random networks) shows that task training adds low-rank structure on top of the SCS background — how generic is that, and is the brain's connectivity well-described that way?
- What is the role of the **edge of chaos** biologically? Do cortical circuits operate near gJ = 1, and if so, through what homeostatic mechanism is it maintained?
- The chaotic flow is bounded but extensively high-dimensional. What is its **manifold dimensionality** in the SCS model, and how does it relate to the ~10D intrinsic manifolds observed in motor cortex?
- How does the transition shift under **biological constraints** — conductance-based neurons instead of rate, spiking variability, finite population sizes?
- **Short-range connectivity** (raised by SCS themselves): does the transition change when Jᵢⱼ has finite spatial range? This connects to how cortical columns and local microcircuitry differ from the fully-connected SCS setup.
- What is the relationship between SCS-style chaos and **[[Brennan 2019|limit-cycle attractors in *C. elegans*]]**, which are manifestly non-chaotic? Is the *C. elegans* nervous system operating below gJ = 1 and relying on structured couplings to produce its limit cycles, or is it a different dynamical regime entirely?

## Sources

Sompolinsky, Crisanti & Sommers (1988). *Phys. Rev. Lett.* 61(3): 259–262.
