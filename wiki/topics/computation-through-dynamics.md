---
title: "Computation Through Dynamics"
type: theory
aliases: ["CTD", "computation through neural population dynamics", "dynamical systems framework"]
tags: [dynamical-systems, population-dynamics, motor-cortex, rnn, framework]
source_count: 7
last_updated: 2026-04-30
status: established
---

**Computation Through Dynamics (CTD)** is the stance that a neural population's job is to *be* a dynamical system whose temporal evolution *is* the computation, rather than a code whose instantaneous values represent the answer. Formalized as an explicit framework by [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]], though the lineage runs through Shenoy, Churchland, Sussillo and the larger Stanford / Columbia / Caltech motor-cortex community over 15+ years.

For this wiki, CTD is **the vocabulary**. It names the framework that has been implicit in several ingested sources: [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]]'s computational scaffolds, [[li-2024-prediction-noise-reward|Li et al. (2024)]]'s attractor-driven PaN, [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]'s conserved manifolds. CTD is the general framing; those are specific instantiations.

## The Core Claim

A neural population's state `x(t) ∈ ℝ^N` evolves according to

```
dx/dt = f(x(t), u(t))
```

where `f` is the intrinsic state-update rule (set by circuitry and cellular biophysics) and `u(t)` is external input. The computation is identified with the flow — the trajectories `f` traces through state space as a function of inputs and initial conditions.

### Three consequences

1. **Initial conditions matter.** Where the population *starts* determines what it will do. Preparatory activity in motor cortex is the canonical case — prep state is the initial condition from which movement evolves.

2. **Inputs can be transient or contextual.** Fast inputs perturb the state (`δx`); slow **contextual inputs** shift the operating point `x*` and thereby change the linearized dynamics `A(x*, u*)`. The same circuit can implement different computations in different contexts without any synaptic change — context reshapes `f` locally.

3. **The right level of description is collective, not single-neuron.** Tuning curves of individual neurons are secondary; the variance that drives behavior lives in the collective flow. This is the stance that [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] establish at the extreme — individual neurons fire variably across animals, but the macroscopic dynamics are conserved.

## Methodological Moves

### Linearization around fixed points

Fixed points `x*` where `f(x*) = 0` are the simplest structures in the flow: stable fixed points are the simplest model of memory; unstable fixed points ("saddles") shape trajectories between regions. Near any fixed point, the nonlinear dynamics are approximately

```
d(δx)/dt ≈ A(x*) δx
```

where `A = ∂f/∂x` evaluated at `x*`. The eigenstructure of `A` reveals local behavior (decaying, oscillatory, expansive). Fixed-point finding in trained RNNs (Golub & Sussillo 2018) is the dominant analysis tool in CTD.

### Task-trained RNNs as hypothesis generators

The workflow:
1. Define a task with input-output examples.
2. Train an RNN to perform it.
3. Analyze the trained RNN by finding fixed points, linearizing, and examining dynamics.
4. The RNN's solution is a *hypothesis* — it proposes which dynamical motifs could subserve the computation.
5. Test the hypothesis against recordings from an animal doing the same task.

This is how rotational dynamics (Sussillo et al. 2015), line-attractor decisions (Mante 2013), and curved Bayesian priors (Sohn 2019) were proposed. The hypothesis-generator framing is important: it does not assume the brain uses the RNN's solution, only that the RNN's solution is a candidate worth comparing.

The workflow has a constructive counterpart: [[force-learning|FORCE learning]] ([[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]]) is the foundational existence proof that trained trajectories — periodic outputs, Lorenz-attractor trajectories, 4-bit memories, human motion-capture locomotion — can be carved out of an SCS-chaotic recurrent reservoir by a local-ish learning rule applied to readout or feedback weights. FORCE is the synthesis dual of fixed-point analysis: FORCE constructs the trained dynamics, fixed-point analysis dissects them.

Caveat established by [[brennan-2023-looper-computational-scaffold|Brennan 2023]]: brains and RNNs trained on the same task can find the *same computational scaffold* via *different strategies* (brain learns the general algorithm; RNN exploits dataset statistics). Treat RNN solutions as *one* hypothesis, not *the* solution.

### Slow / contextual inputs

A powerful trick: if a task has multiple contexts that share sensory and motor primitives, the same circuit can implement both by having the context appear as a slow input that shifts `x*`. This is how [[#Line Attractors for Decisions|Mante-style context-dependent decisions]] work: context is not gated at the input; it reshapes `f` locally so that only the relevant input dimension integrates.

## Canonical Motifs

### Preparatory Activity as Initial Condition

Delay-period motor-cortex activity sets up the initial state from which movement-period dynamics evolve. Different reaches ⟹ different preparatory states. More preparation time ⟹ faster reaction times, because the initial condition is better positioned. See [[Preparatory Activity]].

### Output-Null Preparation

Preparation must be behaviorally informative without producing movement. Solution: preparatory activity lives in the **null space** of the motor-output readout — large along dimensions that do not drive muscles. Movement begins when activity rotates from null into output-potent dimensions (Kaufman 2014). See [[Null Space Coding]].

### Rotational Dynamics

During movement, motor-cortex population activity traces rotations in state space, approximated by a low-dimensional linear oscillator. The rotation *generates* muscle activity; it is not a representation of movement parameters. Demonstrated empirically (Churchland 2012) and reproduced by RNNs trained to transform preparatory states into muscle patterns (Sussillo 2015). See [[Rotational Dynamics]].

### Condition-Invariant Signal

A large, direction-agnostic signal triggered by the go cue that transitions the motor cortex population from preparation to movement-generation regions of state space. An input that moves the dynamics across a separatrix (Kaufman 2016).

### Line Attractors for Decisions

In context-dependent 2AFC (Mante et al. 2013), PFC implements the decision by integrating the task-relevant input along a **line attractor** — a linear arrangement of stable fixed points. Context appears as a slow input that selects which sensory dimension integrates; the irrelevant dimension's input decays along orthogonal directions (dynamics quenching, not gating).

### Manifold-Constrained Learning

Recorded population activity lies on a low-dimensional **intrinsic manifold**. BCI learning is fast if the required dynamics stay on the manifold and slow / impossible if they do not (Sadtler 2014). Within-manifold learning proceeds by **neural reassociation** — re-using existing states in new pairings (Golub 2018). Off-manifold learning requires more substantial synaptic-weight changes and takes days (Oby 2019).

This motif is the most consequential for this wiki's control thesis: the intrinsic manifold is the **control-theoretic repertoire** that connectivity and biophysics make accessible, and fast learning operates inside it.

## The Substrate: Random Recurrent Networks and the Chaos Transition

CTD analyses typically train RNNs to perform a task and read out the dynamical motifs that emerge. But the **untrained** substrate — what a generic recurrent network of N rate neurons with random asymmetric couplings does — is the raw material those trained dynamics are carved out of. [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] establish the phase diagram: below a critical gain (`gJ < 1`) the network is silent; above it, the only stable long-time state is **extensively high-dimensional chaos**. Fixed points, limit cycles, and static "spin-glass" states all exist as MFT solutions but are unstable to fluctuations in the asymmetric case.

This matters for CTD in two ways:

- **Initialization**. Task-trained RNNs (Sussillo 2015, Mante 2013, Sohn 2019) are typically initialized above the transition. The trained structure — rotations, line attractors, fixed points — is what task training carves out of the chaotic reservoir. Training suppresses most of the chaos while preserving just enough dynamical richness to solve the task.
- **Available capacity**. Above `gJ = 1`, a macroscopic (∝ N) fraction of Lyapunov exponents are positive. Random RNNs carry, in principle, extensive computational capacity; training selects which subspace is used. See [[Edge of Chaos]] for the framing that cortex and usefully-trained RNNs operate near the transition — where correlation times diverge (long memory) and the dynamics are richly input-sensitive.

The analytical tool that makes statements about this substrate tractable is [[Dynamical Mean-Field Theory|DMFT]], which reduces N coupled equations to a single self-consistent neuron.

## Relationship to the Organizing Principle

CTD is the formal language for the closed-loop sensorimotor control that this wiki treats as the foundation of intelligence. The motor-cortex case — prepare, move, integrate feedback, update — is literally the primitive closed loop. CTD supplies:
- A formalism for each stage (initial conditions, flow, inputs, contextual inputs).
- Specific dynamical motifs that implement each (rotational pattern generation, output-null preparation, line-attractor integration).
- A principled extension to longer timescales (adaptation operates on initial conditions), to more latent variables (decisions are line attractors), and to contextual computation (slow inputs reshape local dynamics).

Every more "cognitive" case in the literature — timing, decision, working memory, category abstraction — is treated in the CTD framework as *the same dynamical machinery* extended, not as a separate faculty.

## Methodological Caveat: dimensionality reduction does not entail computation

[[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] applied non-negative matrix factorization to all 3,510 transistors of an MOS 6502 microprocessor running Space Invaders. Six recovered latent dimensions correlated cleanly with known internal signals — the two-phase clock (CLK0, CLK1OUT) and the read-write line. The figure looks essentially identical to neural-population analyses that find latent dimensions correlated with stimuli or behavior (Cunningham & Yu 2014; Churchland 2012; Mante 2013). Yet recovering "dimension 1 ≈ clock" does not, by itself, reveal how the processor computes — and the chip's full computational hierarchy was *not* recovered by any standard dim-reduction.

The implication for CTD is sharper than a generic methodological warning. Linear (or shallow non-linear) dimensionality reduction recovers necessary but not sufficient evidence that the recovered dimensions *are* the computation. The strongest defense against the critique is the **trained-RNN sufficiency proof**: an RNN that, when run forward, actually generates the target behavior provides a constructive existence proof of one possible mechanism — going beyond correlation to demonstrated capability. For analyses that stop at "dimension X correlates with task variable Y," the chip-NMF result is a direct caution. The [[brennan-2023-looper-computational-scaffold|LOOPER scaffolds]] framework partially addresses this by demanding that recovered structure predict counterfactual perturbations, not just correlate with observed variables.

[[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] generalize the warning: trained networks (and brains) performing across an incompressible world should not be expected to admit short-formal-language summaries at the parameters layer; only the *recipe* (architecture + loss + learning rule + training regime) is communicable. The strongest reading of CTD — that the recovered low-dimensional dynamics *are* the explanation — is in tension with this view. The CTD-compatible response is to treat the dynamics as a property of the recipe rather than of any particular trained instantiation: if randomly initialized networks reliably develop the same dynamics when trained on the same task ([[principles-vs-parameters|principles, not parameters]]), the dynamics are part of what the recipe produces, and the explanatory weight rests on the recipe + training-regime, not on the trained dynamics being separately summarizable. The trained-RNN sufficiency move is what makes this defense work.

## Relation to Adjacent Frameworks

| Framework | Level | Relation to CTD |
|---|---|---|
| [[Attractor Dynamics]] | Mechanism | Attractors are the coarse structures of the flow CTD describes |
| [[Neural Manifolds]] | Geometry | The subspace in which CTD dynamics actually live |
| Computational scaffolds ([[brennan-2023-looper-computational-scaffold|Brennan 2023]]) | Data-driven | LOOPER extracts 1D scaffolds directly from data; CTD typically fits RNNs and linearizes |
| [[Predictive Coding]] | Mechanism | PC proposes a specific `f`; CTD is framework-agnostic about which `f` the brain uses |
| [[Active Inference]] | Normative | AI proposes a specific objective; CTD describes what dynamics *do*, not what they *should* do |
| [[paradigm-pluralism-comp-neuro|Paradigm pluralism]] | Meta | Reads CTD as one paradigm in a multi-paradigm comp-neuro ecology — competitor to coding-style decomposition over what counts as the explanatory primitive, mediator across mechanistic and behavioral targets via shared mathematical language |

## Sources

- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — the review that codifies CTD as a named framework and catalogs its motifs.
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — the chaos transition in random asymmetric rate networks; establishes the dynamical substrate from which trained CTD motifs are carved and anchors the [[Edge of Chaos]] framing of the operating regime.
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — [[force-learning|FORCE learning]]: constructive proof that trained trajectories can be carved out of the SCS chaotic reservoir by local-ish learning applied to readout/feedback weights; preparatory-activity-as-chaos-suppression reading; explicit anti-single-neuronism ("trying to link single-neuron responses to motor actions may thus be misguided") 11 years before the CTD label.
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — methodological caution: NMF on a fully understood microprocessor recovers latent dimensions cleanly correlated with known signals (clock, read-write line) without recovering computational understanding; sharpens the requirement that CTD-style analyses make trained-RNN sufficiency proofs (or counterfactual-prediction tests) load-bearing rather than relying on correlation alone.
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — generalizes the chip-NMF caveat into a [[principles-vs-parameters|principles-vs-parameters]] frame: trained-system parameters are not communicable in any short formal language because the world they encode is incompressible. The CTD-compatible reading is that recovered dynamics are properties of the recipe (architecture + loss + training regime) rather than of any particular trained instantiation; the trained-RNN sufficiency move is what makes the defense work.
- [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT (2026)]] — Kuhnian-pluralist reading: identifies CTD as both competitor (to coding-style and structure-first paradigms over what counts as the explanatory primitive) and mediator (offering shared mathematical language across mechanistic and behavioral targets); flags activity-silent working memory as a load-bearing local anomaly within the dynamical-systems / attractor paradigm.
- [[brette-2018-coding-metaphor|Brette (2018)]] — sympathetic alignment with critique. CTD is largely consistent with Brette's positive program: neural populations as dynamical systems whose evolution *is* the computation, not as substrates for codes; trained RNNs as hypothesis generators rather than literal representational claims; spikes as state transitions in a dynamical system rather than symbols. The residual coding-flavored move that Brette would push back on is the labeling of CTD-discovered structure with task-variable names ("line attractor for decision," "rotation for muscle pattern generation") — these descriptions are useful but should be read as correspondence claims with experimental scope, not as statements that the dynamics *encode* the labeled variables. The sufficiency-proof workflow (trained RNN actually generates the behavior) is essentially the same standard Brette demands of "models that behave."
