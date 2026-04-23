---
title: "FORCE Learning"
type: mechanism
aliases: ["FORCE", "First-Order Reduced and Controlled Error", "Sussillo-Abbott learning"]
tags: [rnn, reservoir-computing, learning-rule, chaos, recursive-least-squares]
source_count: 1
last_updated: 2026-04-22
level: circuit
---

**FORCE learning** (**F**irst-**O**rder, **R**educed and **C**ontrolled **E**rror) is a procedure for training recurrent networks with chaotic spontaneous activity to produce complex coherent outputs while leaving feedback loops intact and unclamped. Introduced by [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]]. The foundational trained-RNN demonstration under what would become [[Computation Through Dynamics|CTD]].

## The Core Move

Traditional learning schemes slowly reduce errors from large to small — this fails for chaotic recurrent networks because early errors, fed back through the loop, drive the network arbitrarily far from the target state. FORCE does the opposite: it **keeps errors small throughout training** by making weight changes large and rapid.

A small residual error is what the procedure needs:

1. It is small enough that the feedback signal during training approximates the target function `f(t)` closely enough to induce the chaotic→non-chaotic transition in the recurrent network (the SCS transition; see [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers 1988]]). Training and chaos suppression turn out to be the same problem.
2. It is large enough that the algorithm samples fluctuations and stabilizes the instabilities they reveal. Echo-state learning (where feedback is clamped to the target) is unstable after training stops because fluctuations were never sampled; FORCE networks are stable.

## Update Rule

Recursive least squares (RLS):

```
e_-(t) = w^T(t - Δt) r(t) - f(t)
w(t) = w(t - Δt) - e_-(t) P(t) r(t)
P(t) = P(t - Δt) - [P(t - Δt) r(t) r^T(t) P(t - Δt)] / [1 + r^T(t) P(t - Δt) r(t)]
P(0) = I / α
```

The matrix `P` is a running estimate of the inverse correlation matrix of `r`, plus regularization `α I`. RLS is a delta rule (error × presynaptic rate) with **multiple effective learning rates — one per principal component** of the network activity. A simpler synapse-specific scalar-rate version also works but is weaker.

## Three Architectures

[[sussillo-abbott-2009-force-learning|Sussillo & Abbott]] introduce three versions:

1. **Readout feedback (1A)**: a linear readout `z = w^T r` is fed back into a random recurrent generator network via random feedback synapses. Only `w` is modified.
2. **Separate feedback network (1B)**: the readout drives a second recurrent network, which in turn feeds back into the generator. `w` and the generator-to-feedback weights are modified. Biologically interpreted as motor cortex + cerebellum or + basal ganglia, where feedback modifications do not disturb the motor cortex itself.
3. **Within-generator (1C)**: no external loop; FORCE is applied to synapses internal to the generator network. A credit-assignment scheme treats every modified neuron as if it were the readout, using the same global scalar error signal.

All three produce comparable results for the demonstrated tasks.

## Chaos Is Beneficial

Networks with recurrent gain `g < 1` are inactive and train poorly; networks with `g > 1` are chaotic ([[sompolinsky-1988-chaos-random-networks|SCS 1988]]) and train better. Training performance (cycles required, RMS error, readout weight magnitude) improves monotonically with `g` up to `g ≈ 1.5`. Above `g ≈ 1.56`, FORCE fails because the feedback signal can no longer suppress the network's chaos.

The best operating point is **the largest `g` at which FORCE still suppresses chaos** — a constructive operational definition of [[Edge of Chaos]]: not a literal critical point of the untrained network, but the upper boundary of the regime in which training can carve trained dynamics out of the reservoir.

## Low-Dimensional Trained Structure

PCA of FORCE-trained activity reveals:

- ~8 leading PCs capture most of the target-function variance for a typical sum-of-sinusoids target on a 1000-neuron network.
- The projections of the readout weight vector `w` onto the top ~50 PCs converge to uniquely specified values across training runs.
- Projections onto smaller-eigenvalue PCs are left free and take different values on different runs.

RLS's PC-specific learning rates split naturally into a **control phase** (large eigenvalue PCs, rate `1/α`) and a **learning phase** (small eigenvalue PCs, rate `1/(Mλ_a)`), with PCs migrating from control to learning as training proceeds. The trained network's activity lives in a low-dimensional subspace selected out of the chaotic reservoir — the in-silico counterpart of the empirical intrinsic manifolds observed in monkey M1 ([[Neural Manifolds]]; Sadtler 2014, Gallego 2017).

## What FORCE Networks Can Produce

A single chaotic RNN, trained by FORCE, can produce:

- Periodic functions (sums of 4 and 16 sinusoids, square waves).
- Chaotic Lorenz attractor trajectories (matching for finite time).
- Sine waves with periods ranging 60 ms to 8 s.
- Highly noisy targets (recovers the underlying signal).
- One-shot non-repeating sequences (via two-readout fixed-point initialization).
- 4-bit input-controlled memory (16 fixed-point attractors; pulsed inputs switch between them).
- Human motion-capture **running and walking** (95 joint angles; one network, two motions, switched by static control input).

Robust to nonlinear distortions and delays in the feedback pathway.

## Connection to Preparatory Activity

To produce a one-shot (non-periodic) sequence, FORCE requires the network to be brought to a fixed point before the sequence starts. An auxiliary readout provides a constant input that induces this fixed point, quenching chaotic activity. Sussillo & Abbott connect this directly to Churchland et al. (2006): the sharp drop in neural variability in motor and premotor cortex just before movement has exactly this character — a chaotic state being quenched into a prepared initial condition ([[Preparatory Activity]]) from which the movement trajectory then evolves. Preparation, in this reading, *is* chaos suppression.

## Biological Plausibility and Open Questions

FORCE requires plasticity on the timescale of the network itself, not on LTP timescales. This is the central biological challenge. Candidates for how biology might achieve effective fast plasticity:

- Short-term plasticity (STP) providing fast functional changes without long-term weight updates.
- Neuromodulatory gating sharply increasing effective plasticity during task-relevant epochs.
- Heterosynaptic or population-level averaging converting many slow changes into one fast effective change.
- Inference at fast timescales combined with slow consolidation.

Other open questions:

- **Error-signal computation.** FORCE assumes a precomputed target and error. Sussillo & Abbott suggest cerebellum-style internal models, but how the brain actually generates task-relevant error signals for motor learning is unresolved.
- **Synapse-specific vs. neuron-specific plasticity.** RLS uses shared `P` for all synapses onto a neuron. Synapse-specific versions are possible but less powerful. How to reconcile with local synaptic plasticity rules is open.
- **Scaling to closed-loop sensorimotor control.** The demonstrations are open-loop (joint angles produced without environmental feedback). Extending to genuine closed-loop control is not addressed.

## Relation to Reservoir Computing

FORCE extends the echo-state / liquid-state tradition (Jaeger & Haas 2004; Maass et al. 2002) in two important ways:

- **Feedback is intact, not clamped.** Echo-state learning clamps the feedback to the target function during training, which produces networks that are unstable after training stops. FORCE's residual error lets the network sample and stabilize fluctuations in the feedback pathway.
- **Chaos is helpful, not a problem.** Echo-state networks are required to be inactive in the absence of input. FORCE turns the chaotic spontaneous activity of generic recurrent networks into a computational advantage.

## Role in the Wiki

FORCE is the constructive existence proof that underlies [[Computation Through Dynamics]]: given a chaotic reservoir, synaptic modification can carve out trajectories that produce arbitrary complex outputs. It is the trained-RNN twin of the CTD analysis program (fixed-point finding and linearization of trained networks, later formalized by Sussillo & Barak 2013 and Golub & Sussillo 2018). The specific result that motor-cortex-like [[Rotational Dynamics|rotational dynamics]] emerge generically in FORCE-trained RNNs (Sussillo et al. 2015) is a direct descendant.

More broadly, FORCE formalizes a picture compatible with the wiki's control thesis: the closed-loop sensorimotor control loop is a chaotic recurrent substrate + learning that carves trained trajectories out of it. The feedback loop is the substrate for modification — "non-destructive, highly flexible, and usable for learning as well as for development and evolution" ([[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]]).

## Sources

- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — the foundational FORCE paper; three architectures; chaos helps; ~8-PC low-dimensional trained structure; motion-capture, 4-bit memory, Lorenz and periodic outputs.
