---
title: "Generating Coherent Patterns of Activity from Chaotic Neural Networks"
type: source
source_type: paper
authors:
  - "David Sussillo"
  - "L. F. Abbott"
year: 2009
doi: "10.1016/j.neuron.2009.07.018"
tags: [rnn, reservoir-computing, chaos, motor-control, ctd, learning, feedback-loops]
date_ingested: 2026-04-22
key_finding: "FORCE learning trains chaotic RNNs with intact feedback loops to produce complex coherent outputs; keeps error small throughout training rather than reducing it from large; chaos helps, with the edge of chaos (g just below the point where FORCE fails to suppress it) being the best operating regime."
---

[PDF](../../raw/papers/sussillo-abbott-2009.pdf)

## Overview

The paper introduces **FORCE learning** — First-Order, Reduced and Controlled Error — a procedure for modifying synaptic weights in recurrent networks that are spontaneously chaotic, so that they generate a wide variety of desired output patterns while *leaving feedback loops intact*. This is the foundational trained-RNN paper under what would later be named [[Computation Through Dynamics|CTD]]: the network is treated not as a code but as a dynamical system, and training carves coherent trajectories out of a chaotic reservoir.

The central technical move is unusual. Traditional learning reduces errors from large to small; FORCE keeps errors *small throughout training* by making weight changes large and rapid. The small residual error is what allows the feedback signal (the output fed back into the recurrent network) to sample and stabilize instabilities, and it is strong enough to induce the chaotic→non-chaotic transition identified by [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]]. Training and chaos suppression turn out to be the same problem.

## Key Findings

### FORCE learning

A recurrent generator network with N rate neurons `τ dx/dt = -x + g J r + J^Gz z + (inputs)`, `r = tanh(x)`, with coupling strengths drawn from a Gaussian of variance `1/N`. Gain `g` is the SCS gain parameter — `g > 1` places the network in the chaotic regime; Sussillo & Abbott use `g = 1.5`. A linear readout `z = w^T r` is fed back through the recurrent network via feedback synapses `J^Gz`.

Training modifies `w` by recursive least squares (RLS):

```
w(t) = w(t - Δt) - e_-(t) P(t) r(t)
P(t) = P(t-Δt) - [P(t-Δt) r(t) r^T(t) P(t-Δt)] / [1 + r^T(t) P(t-Δt) r(t)]
P(0) = I / α
```

where `e_-(t) = w^T(t - Δt) r(t) - f(t)` is the error before the update and `α` (values 1–100) is the effective learning-rate regularizer. `P` is a running estimate of the inverse correlation matrix of `r`; RLS's multiple effective learning rates (one per principal component) are what makes FORCE work so well. Immediately after the first update, error drops to `-α f(Δt)/(α + r^T r)` — small when `α ≈ N` — and stays small thereafter.

### Three architectures

1. **1A**: the output `z` is fed back into the generator network via strong random feedback synapses; only the readout weights `w` are modified (similar to echo-state networks but with feedback not clamped).
2. **1B**: a separate recurrent **feedback network** sits between the readout and the generator; `w` and the generator-to-feedback synapses are modified. Biologically interpreted as cerebellum or basal ganglia providing feedback that does not disrupt motor cortex itself.
3. **1C**: no external feedback loop at all; FORCE is applied to synapses `J^GG` *within* the generator network. A credit-assignment scheme treats every synaptic-modification neuron as if it were the readout unit, using the same global error signal.

All three work. The first is cleanest but biologically implausible; the second and third are proposed as more biologically realistic.

### Chaos is beneficial

Networks with `g < 1` are inactive pre-training. Networks with `g > 1` are chaotic. Training works better in the chaotic regime — number of training cycles, RMS error, and readout weight magnitude all decrease with increasing `g` up to `g ≈ 1.5`. Beyond `g ≈ 1.56`, FORCE fails because the feedback cannot suppress the chaos. The best operating regime is **just below the upper limit of chaos suppression** — what the authors call the edge of chaos, referring to [[Edge of Chaos]] / Bertschinger & Natschläger (2004).

### Low-dimensional trained dynamics

PCA of trained-network activity shows the first ~8 principal components suffice to reconstruct the output target (sum of four sinusoids, figure 3A). Over training, the readout weight projections onto the leading ~50 PCs converge to uniquely specified values across runs; projections onto smaller-eigenvalue PCs are free and take different values on different runs. RLS's PC-specific learning rates split naturally into a **control phase** (large eigenvalue components, rate `1/α`) and a **learning phase** (small eigenvalue components, rate `1/(Mλ_a)`), with components migrating from control to learning as `M` grows.

### Range of behaviors trained

Single chaotic RNN trained to produce: periodic functions (combinations of 4 and 16 sinusoids, square waves), Lorenz attractor trajectories, sine waves with periods ranging 60 ms to 8 s, noisy targets (recovers underlying signal), one-shot non-repeating sequences (via two-readout fixed-point initialization), 4-bit input-controlled memory (16 fixed-point attractors + transitions, with input-switching), and **human motion-capture running and walking** (95 joint angles; one network, two motions, switched by static input). The architecture is robust to nonlinear distortions and delays in the feedback pathway.

### Link to preparatory activity in motor cortex

To produce a one-shot (non-periodic) sequence, an auxiliary readout drives the network to a fixed point before the sequence starts — terminating chaotic activity and setting up the initial condition. The authors explicitly connect this to Churchland et al. (2006): the sharp drop in neural variability seen in motor and premotor cortex just before a reach has exactly this character — a chaotic state being quenched into a prepared fixed point that seeds the subsequent trajectory.

### "Trying to link single-neuron responses to motor actions may thus be misguided"

In architectures 1A and 1B, the generator network's connectivity remains random even after training — only the readout (and/or feedback) weights change. Individual generator neurons bear little direct relationship to the output. The authors argue this means single-neuron tuning-curve analysis is the wrong level of description; the population modes (extracted by PCA) are what matters. This is the CTD stance stated plainly in 2009, 11 years before the Vyas review named it.

## Methods

- **Architecture**: firing-rate neurons `τ dx/dt = -x + ...` with `τ = 10 ms`; Gaussian coupling variance `1/N`; `N_G` varies by figure (1000–20 000); sparseness parameters `p_GG, p_Gz, ...`.
- **Training**: RLS with `α ∈ [1, 100]`, updates at time interval `Δt` (smaller than integration step); typical training run ≈ 1000τ ≈ 10 s of simulated time.
- **Mixed-feedback sweeps**: interpolate FORCE (`γ = 0`) and echo-state (`γ = 1`) by setting the feedback during training to `γf + (1-γ)z`. FORCE dominates: echo-state (`γ = 1`) converges on only ~50% of trials and the final network is unstable after training stops.
- **Motion capture**: CMU MOCAP library dataset 09_02 (running) and 08_01 (walking), preprocessed to 10× interpolation density. 95 readout units one per joint angle; running and walking switched by four static control inputs (two to initialize fixed points, two to select motion).

## Implications

### Trained dynamics are carved from chaotic reservoirs

FORCE provides the constructive existence proof that the CTD picture of motor cortex can be realized by a local learning rule. Given a random asymmetric recurrent network above the chaos transition, synaptic modification can carve out rotational, oscillatory, square-wave, Lorenz, or motion-capture dynamics. The network is not "designed" for any task; it is a general-purpose dynamical system co-opted by training. This is the prototype demonstration of the reservoir-then-shape picture that anchors [[Computation Through Dynamics]].

### Feedback loops are the substrate for behavior modification

The paper argues that nervous systems are "loops within loops within loops." Adding a feedback loop leaves the original circuit unchanged but opens a flexible new behavioral channel — non-destructive, highly flexible, and usable for learning as well as for development and evolution. This framing bears directly on the control thesis: the closed-loop architecture is the substrate, and learning operates by reshaping the loop's feedback structure rather than by rewriting the underlying circuit.

### Architecture 1B as a biological hypothesis

The feedback-network architecture (separate recurrent network trained via generator→feedback synapses) is proposed as a model for motor cortex + basal ganglia or motor cortex + cerebellum. Plasticity in the second network dominates when a motor task is first learned, while plasticity within motor cortex itself (architecture 1C) is reserved for "virtuoso" highly-trained actions. This is a concrete proposal for how fast manifold-constrained learning and slow structural reshaping divide labor across networks.

### Fast plasticity as a learning requirement

FORCE requires that plasticity act on the timescale of the network (not LTP timescale). The authors flag this as a challenge for biology: LTP-style slow changes cannot implement FORCE directly. How the brain could achieve rapid effective plasticity (perhaps via neuromodulation, short-term plasticity, or ensemble averaging) is left open.

### Anti-single-neuronism

The paper's conclusion that single-neuron activity in trained networks bears little relationship to the output is a prediction: recordings from trained biological circuits should show complex heterogeneous single-neuron activity whose interpretable structure emerges only at the population level. The ensuing 15 years of CTD recordings have confirmed this stance.

## Connections to Existing Knowledge

- **[[Computation Through Dynamics]]**: FORCE is a foundational worked example of the CTD picture. Training carves trajectories out of the SCS chaotic reservoir; fixed-point analysis (later formalized by Sussillo & Barak 2013; Golub & Sussillo 2018) is the analysis dual of FORCE's synthesis.
- **[[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]]**: the SCS chaos transition is the substrate. FORCE operates best just below the upper-`g` limit where feedback can still suppress chaos — a constructive version of the [[Edge of Chaos]] hypothesis.
- **[[Edge of Chaos]]**: FORCE provides a concrete operational meaning: the best `g` is the largest at which the training-time feedback signal can induce the chaos→non-chaos transition in the generator network.
- **[[Preparatory Activity]] / Churchland et al. (2006)**: the two-step initialization procedure (fixed-point-inducing input, then sequence-inducing input) mirrors the empirical drop in neural variability preceding movement. Preparation as chaos suppression.
- **[[Neural Manifolds]]**: the ~8D output-relevant subspace and ~50D uniquely-learned subspace in trained FORCE networks is the early in-silico version of the Sadtler-Golub-Oby intrinsic manifolds in monkey M1, and clarifies that the manifold is *selected by training* out of a generically higher-dimensional chaotic reservoir.
- **[[Rotational Dynamics]]**: Sussillo et al. (2015) later use FORCE-trained networks to show that rotations emerge generically when RNNs are trained to produce muscle patterns; that result is a direct descendant of this paper.
- **[[Credit Assignment]]**: architecture 1C applies the same global error signal to every synapse being modified, treating each neuron "as if it were the readout." This is a simple, cell-autonomous credit-assignment scheme that predates the dendritic lineage (Kording 2001 / Guerguiev 2017 / Sacramento 2018 / Payeur 2020 / Greedy 2022 / Francioni 2026) and makes a different trade: no dendrites, but a global error signal rather than vectorized local error.
- **Reservoir computing (Jaeger & Haas 2004; Maass et al. 2002)**: FORCE generalizes echo-state learning to networks with intact feedback loops and chaotic spontaneous activity. The paper shows pure echo-state learning (`γ = 1`) is unstable after training stops, while FORCE (`γ = 0`) is stable.
- **[[David Sussillo]]**: this is the foundational FORCE paper that established Sussillo's methodological program.

## Open Questions Raised

- **Fast plasticity in biology.** FORCE requires rapid weight changes on the timescale of the network dynamics, not LTP timescales. How could biological synapses achieve the effective rate-of-change that FORCE requires? Candidates: short-term plasticity, neuromodulatory gating, heterosynaptic effects, population averaging across many slow-plasticity synapses.
- **Error-signal generation.** FORCE assumes a precomputed target function and error. In a motor task, the authors speculate the cerebellum might generate an internal model of desired action and compute the discrepancy. But *how* the brain computes the error — especially for multi-output motor tasks — remains unspecified.
- **Synapse-specific vs. neuron-specific plasticity.** RLS is neuron-specific but not synapse-specific: all synapses onto a neuron use shared `P`. A simpler scalar-rate version works but is weaker; how could biology get the RLS benefits (PC-specific learning rates) with a local rule?
- **Connectivity is non-unique.** In architectures 1A and 1B the trained generator connectivity is essentially random; the same task has many trained solutions. What is the right level to characterize such networks — population modes? The authors argue yes, which is the CTD stance.
- **How does this scale to closed-loop control with environment feedback?** The motion-capture example generates joint angles open-loop (no environmental feedback). Extending FORCE to closed-loop sensorimotor control, where proprioception and vision constrain the dynamics, is not addressed.

## Sources

- [PDF](../../raw/papers/sussillo-abbott-2009.pdf)
- Sussillo D, Abbott LF (2009). Generating Coherent Patterns of Activity from Chaotic Neural Networks. *Neuron* 63(4): 544–557. doi:10.1016/j.neuron.2009.07.018
