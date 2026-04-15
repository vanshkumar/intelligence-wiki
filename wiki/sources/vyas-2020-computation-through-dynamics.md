---
title: "Computation Through Neural Population Dynamics"
type: source
source_type: paper
authors:
  - "Saurabh Vyas"
  - "Matthew D. Golub"
  - "David Sussillo"
  - "Krishna V. Shenoy"
year: 2020
doi: "10.1146/annurev-neuro-092619-094115"
tags: [dynamical-systems, motor-cortex, rnn, review, ctd, manifolds, preparatory-activity]
date_ingested: 2026-04-14
key_finding: "Names and codifies the Computation Through Dynamics (CTD) framework — the stance that a neural population's job is to be a dynamical system whose evolution *is* the computation — and synthesizes a decade of motor-cortex and cognition results (preparatory activity as initial condition, output-null preparation, rotational dynamics, line-attractor decisions, manifold-constrained learning) under that frame."
---

## Overview

Vyas, Golub, Sussillo & Shenoy (2020), published in *Annual Review of Neuroscience*, is a review and manifesto for the dynamical-systems perspective on neural computation. The paper codifies the framework as **Computation Through Dynamics (CTD)** — the claim that a neural population's job is to *be* a dynamical system `dx/dt = f(x, u)` whose temporal evolution *is* the computation, rather than a code whose instantaneous values represent the answer.

For this wiki, the review functions as a **vocabulary and scaffold**: it names the stance that has been implicit in several ingested sources ([[brennan-2023-looper-computational-scaffold|Brennan 2023]], [[li-2024-prediction-noise-reward|Li 2024]]), it catalogs the concrete motifs the stance has uncovered (preparatory activity as initial condition, output-null dimensions, rotational dynamics, line attractors for decisions, condition-invariant signals, manifold-constrained learning), and it supplies the mathematical primer (linearization around fixed points, null spaces, linear subspaces, manifolds) needed to read the rest of the literature fluently.

[PDF](../../raw/papers/vyas-2020.pdf)

## The CTD Framework

**Core claim.** A population's computation is identified with the flow of a dynamical system. Three ingredients:
- **State** `x(t)` — an N-dimensional vector of firing rates (typically analyzed after dimensionality reduction to a P-dimensional subspace, P ≪ N).
- **Dynamics** `f` — the intrinsic state-update rule, determined by circuitry and cellular biophysics. Often nonlinear and high-dimensional; analyzed by linearization around fixed points or via multiple local linear models (SLDS).
- **Input** `u(t)` — external drive. Can act as a transient perturbation (e.g., sensory input) or as a slow **contextual input** that reshapes `f` by moving the operating point in state space (A and B matrices in the linearized equation `d(δx)/dt = A(x*, u*)δx + B(x*, u*)δu`).

**Methodological consequence.** Two complementary modeling approaches:
- **Data modeling**: fit `f` (often as an RNN) to recorded neural activity, then analyze the fit via fixed-point finding and linearization.
- **Task-based modeling**: train an RNN on the task, then examine its dynamics to generate falsifiable hypotheses for the brain.

The review treats RNN training as a *hypothesis generator* — the RNN proposes which dynamical motifs could subserve a computation, and those motifs are then tested against neural data.

## Core Dynamical Motifs

### Motor control

1. **Preparatory activity as initial condition.** Delay-period activity in motor cortex (M1 / PMd) is the initial state from which movement-period dynamics evolve. Different reaches require different preparatory states; behavioral benefits of longer delays (faster reaction times) are predicted by the framework. Supports the **initial-condition hypothesis** (preparatory activity sets up the dynamics) over a representational hypothesis (preparation as subthreshold movement). See [[Preparatory Activity]].

2. **Output-null dimensions.** Preparation happens without movement because preparatory activity is structured to lie in the **null space** of the motor-output readout — large and behaviorally informative along input dimensions that do not drive muscles. Movement begins when activity rotates from null into output-potent dimensions. Generalizes beyond motor cortex to any context where computation must occur without driving a downstream region. See [[Null Space Coding]].

3. **Rotational dynamics** (Churchland et al. 2012). Motor-cortex population activity during reaching traces rotations in state space. A simple oscillator (low-dimensional limit cycle) generates the multiphasic muscle patterns needed for reaching. The rotations *produce* behavior rather than *represent* movement parameters. See [[Rotational Dynamics]].

4. **Condition-invariant signal (CIS)** (Kaufman et al. 2016). A go-cue-triggered population-level state shift that transitions the motor-cortex population from the preparation region of state space to the movement-generation region. Interpreted as an input that moves the dynamics across a separatrix.

5. **Motor adaptation operates on preparatory dimensions** (Vyas et al. 2018, 2020). In visuomotor rotation learning, preparatory states systematically shift across trials; disrupting preparation via microstimulation disrupts the trial-by-trial update computation. Learning is implemented as repositioning the initial condition, not as retuning movement-period dynamics.

### Manifold-constrained learning

The most consequential empirical result in the review for this wiki's themes:

- **Sadtler et al. (2014)**: BCI-perturbed monkeys readily learn within-manifold perturbations (hours) but struggle with off-manifold perturbations (not learnable in short timescales). The intrinsic manifold — a ~10D subspace containing existing population variance — constrains what learning can easily achieve.
- **Golub et al. (2018)**: within-manifold learning proceeds by **neural reassociation** — animals re-use neural states from their pre-learning repertoire, pairing them differently with cursor targets, rather than discovering new states.
- **Oby et al. (2019)**: multi-day training can eventually access out-of-repertoire (within-manifold) and even off-manifold states, revealing multiple learning mechanisms at different timescales.
- **Wärnberg & Kumar (2019)**: RNN modeling shows off-manifold learning requires substantial synaptic-weight changes, whereas within-repertoire reassociation is cheap.

This result is the strongest empirical case in the review for treating the intrinsic manifold as a **control-theoretic repertoire** — the set of accessible dynamical states constrained by connectivity and cellular biophysics, within which fast learning occurs.

### Cognition

- **Motor timing** (Wang 2018, Remington 2018, Egger 2019). Timing intervals are encoded by the *speed* of state evolution along a low-dimensional trajectory, modulated by tonic thalamocortical input acting as a contextual gain on the dynamics.
- **Context-dependent decision-making** (Mante et al. 2013). PFC implements context-dependent 2AFC (random-dot motion with relevant/irrelevant features) via a **line attractor**: a linear arrangement of stable fixed points along which sensory inputs integrate. Context-irrelevant inputs decay quickly along orthogonal directions — "dynamics quenching" rather than gating.
- **Working memory** (Chaisangmongkon 2017). Category-match tasks solved via slow, stable "trajectory tunnels" connecting rest, sample, memory, test, and decision states. Misclassification = noise pushing state into the wrong tunnel.
- **Bayesian priors in dynamics** (Sohn 2019). Low-dimensional curved manifolds across the population implement Bayes-optimal priors by warping the neural representation.

## Mathematical Scaffolding

The review's extended primer is the reason it's useful as a reference:
- **Linear dynamical systems (LDS)**: `dx/dt = Ax + Bu`. Eigenstructure of A determines expansive, decaying, or oscillatory behavior. Useful as a first pass and as a *local* approximation to nonlinear dynamics.
- **Fixed points** (`f(x*) = 0`): simplest model of memory; linear approximations around fixed points capture local nonlinear behavior; found numerically in trained RNNs (Golub & Sussillo 2018).
- **Null space**: for `y = Cx`, inputs `x` with `Cx = 0` have no effect on the output — the substrate for output-null preparation.
- **Linear subspaces**: hyperplanes through the origin where P-dimensional population variance concentrates.
- **Manifolds**: low-dimensional topological spaces embedded in the high-dimensional state space; differ from linear subspaces by allowing curvature. Ring attractors, limit cycles, curved priors.

## Implications

**For the organizing principle of this wiki.** The review is effectively a monograph on sensorimotor control and its dynamical-systems formalization. The motor-cortex case is the foundational closed loop this wiki is organized around — prepare, move, sense feedback, update — and CTD supplies the formal language for each stage. Preparatory activity as initial condition, output-null preparation, rotational pattern generation, and context-as-slow-input are all control-theoretic structures that scale up to extend the loop over longer timescales (motor adaptation) and more latent variables (decision, timing, working memory). The review makes explicit that "cognition" in this literature is treated as the *same dynamical machinery* extended, not as a separate faculty.

**For the control-theoretic reading of [[Degeneracy]].** The manifold-constrained learning results (Sadtler / Golub / Oby) are the cleanest empirical case in the literature for the claim that connectivity and cellular biophysics constrain the *dynamical repertoire* of accessible states, and that fast learning operates inside that repertoire rather than expanding it. This is what the genes→control→structure reading of degeneracy predicts at the learning level: genes set the manifold; experience reassociates within it; structural change is slow and rare.

**For RNNs as a methodology.** CTD legitimizes task-trained RNNs as hypothesis generators for biological dynamics, while also flagging ([[brennan-2023-looper-computational-scaffold|Brennan 2023]]) that RNNs may find different strategies than biology on the same task. The two papers together are the current best statement of how to use and not to use RNNs in systems neuroscience.

**For the critique of representational thinking.** The review repeatedly contrasts CTD with a "representational" stance — where single neurons code for specific parameters and the population is read as a bag of such codes. CTD says: the variance that drives behavior is in the collective flow, not in tuning curves. This is a framing the wiki has been implicitly adopting; Vyas et al. make it explicit and argue it has survived empirically over a decade.

## Connections to Existing Knowledge

- **[[Computation Through Dynamics]]**: the framework itself. The review's main contribution to the wiki's vocabulary.
- **[[Preparatory Activity]]**, **[[Null Space Coding]]**, **[[Rotational Dynamics]]**: the three motor-cortex motifs each get their own page.
- **[[Motor Cortex]]**: combined M1 / PMd / SMA page built primarily from this review.
- **[[Neural Manifolds]]**: extended with BCI manifold-constrained learning (Sadtler/Golub/Oby) as the strongest within-subject evidence that manifolds are real constraints on learning.
- **[[Attractor Dynamics]]**: extended with line-attractor decision-making (Mante 2013) and fixed-point linearization as an analysis tool.
- **[[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]]**: same broad stance; LOOPER extracts 1D scaffolds directly from data, CTD analyzes RNN fits. Complementary methodologies.
- **[[li-2024-prediction-noise-reward|Li et al. (2024)]]**: PaN is a CTD-style model — attractor landscape drives behavior, noise drives exploration. The review provides the formal context PaN sits in.
- **[[Degeneracy]] / [[Circuit-Behavior Mapping]]**: intrinsic manifold as a dynamical-repertoire constraint; fast learning within the repertoire, slow learning beyond it.

## Open Questions Raised

- **How is the input-output structure of a brain region organized?** What shapes the local dynamics of `f`, and how do inputs from other regions contextualize it? Recording across many regions simultaneously is required; progress is underway (NeuroPixels, zebrafish whole-brain imaging).
- **Is falsification of CTD models experimentally feasible?** Testing CTD requires high-fidelity control of population activity (optogenetic spatiotemporal patterning). Possible in principle; rare in practice.
- **What determines the intrinsic manifold?** Is it primarily anatomical connectivity, cellular biophysics, slow developmental tuning, or all three? Manifold-constrained learning (Sadtler) makes the existence of the constraint concrete but leaves its substrate open.
- **Do the CTD motifs observed in motor cortex generalize to sensory and associative areas in the same form?** Rotational dynamics, preparatory null-space structure, and CIS are motor-cortex-specific in current evidence; the review speculates they may be instances of more general motifs.
- **What is the relationship between multiple coexisting timescales of learning?** Fast within-repertoire reassociation (hours, Golub) vs. slower out-of-repertoire / off-manifold learning (days, Oby). Are these distinct mechanisms (synaptic tagging, consolidation) or a continuum?
- **Can CTD be unified with credit-assignment accounts** ([[payeur-2020-burst-dependent-credit-assignment|Payeur 2020]])? The CTD literature focuses on what the dynamics *do*; credit-assignment literature focuses on how synapses get tuned to produce them. The two should compose.
- **How do contextual inputs biologically implement the state-space shifts they produce in models?** Thalamocortical tonic input (Wang 2018) is one candidate; neuromodulation is another.

## Sources

- Vyas, S., Golub, M. D., Sussillo, D., & Shenoy, K. V. (2020). Computation Through Neural Population Dynamics. *Annual Review of Neuroscience*, 43, 249–275. [PDF](../../raw/papers/vyas-2020.pdf)
