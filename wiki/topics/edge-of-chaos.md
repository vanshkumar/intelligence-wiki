---
title: "Edge of Chaos"
type: theory
aliases: ["criticality", "critical dynamics", "marginal stability"]
tags: [dynamical-systems, rnn, phase-transition, computation, criticality]
source_count: 4
last_updated: 2026-04-22
status: emerging
---

**Edge of chaos** refers to the regime of a recurrent dynamical system poised at the transition between ordered (stationary / periodic) dynamics and chaotic dynamics. The hypothesis — applied to neural networks, cellular automata, and biological systems more generally — is that systems operating near this critical point achieve an optimal tradeoff between **memory** (long correlation times) and **sensitivity** (inputs producing separable state trajectories), yielding maximal computational capacity.

## Theoretical Anchor

The canonical reference for neural networks is [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]], which established that a large random rate network with asymmetric Gaussian couplings undergoes a sharp transition from a silent fixed point to deterministic chaos at gain `gJ = 1`. Near the transition (gJ = 1⁺):

- The correlation time of the flow **diverges** as τ ∝ 1/ε, where ε = gJ − 1.
- The amplitude of fluctuations **vanishes** as ε.
- The Lyapunov exponent **vanishes** as ε²/2.

These diverging/vanishing scales are the hallmark of a continuous phase transition, and the intuition behind "edge of chaos" is that the critical slowing down provides long memory, while the incipient chaos provides input separability.

## Operational Framing

For a recurrent network used as a computational substrate (reservoir computing; trained RNN):

- **Well below the transition** (gJ ≪ 1): inputs decay fast, no memory, no separation of input histories.
- **Well above the transition** (gJ ≫ 1): chaotic dynamics, nearby input trajectories diverge exponentially — past inputs are scrambled into unrecoverable nonlinear mixtures.
- **Near the transition** (gJ ≈ 1): marginal stability. Different input histories produce distinguishable, long-lived state trajectories. The system's state reflects a **nonlinear convolution** of its input history over a long window.

This is the theoretical backing for reservoir computing (echo-state networks, liquid-state machines) which operate random RNNs near this regime by construction, and for the common practice of initializing trainable RNNs with gain slightly above 1 — task training then carves out structured attractors from the nearby chaotic reservoir, as discussed on [[Computation Through Dynamics]].

### Operational Definition from FORCE

[[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] give a constructive operational version. In [[force-learning|FORCE learning]], training performance (cycles required, RMS error, readout weight magnitude) improves monotonically with gain `g` up to `g ≈ 1.5`, then the procedure fails above `g ≈ 1.56` because the feedback signal during training can no longer suppress the network's chaos. The best operating point is **the largest `g` at which FORCE still suppresses chaos** — not a literal critical point of the untrained SCS network, but the upper boundary of the regime in which training can carve trained dynamics out of the reservoir. This is "edge of chaos" made actionable: the operating point is defined by what the learning rule can still do, not by an abstract property of the network.

## Status in Neuroscience

Empirically supported as a framing; mechanistically underspecified as a claim about biology:

- **Cortical network balance**. Balanced E-I networks (van Vreeswijk & Sompolinsky 1996; [[brunel-1999-sparsely-connected-networks|Brunel 2000]]) operate in a high-variance, input-sensitive regime that is often argued to be effectively critical. [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] provides the spiking-network analogue of SCS criticality: near the boundary of the [[Asynchronous Irregular State|AI state]], the coherence time of residual oscillations in the global activity autocorrelation scales as 1/ε (where ε = C/N is the connection sparsity), diverging as N → ∞. The balance point g = 4 is the spiking edge — on one side lies the asynchronous-irregular regime, on the other the synchronous-irregular (ripple or gamma) regime.
- **Neuronal avalanches**. Beggs & Plenz (2003) and subsequent work find power-law distributions of cortical activity bursts consistent with a critical branching process — a spiking-network analog of edge of chaos.
- **Homeostatic mechanisms**. Plausible tuning knobs to keep cortex near criticality include synaptic scaling, intrinsic excitability regulation, and inhibitory gain control.
- **Open question**: whether "edge of chaos" is a literal physical claim about cortical operating point, or a looser metaphor for richly input-sensitive-yet-memoryful dynamics. The hypothesis predicts specific signatures (diverging correlation times, scaling laws) whose experimental status across brain regions is still being worked out.

## Relationship to the Control Thesis

Edge of chaos is a specific answer to the question *what dynamical repertoire should the nervous system maintain as the substrate for control?* If cortex is tuned near the transition, then:

- Sensory inputs leave long-lived traces (supporting working memory and integration, as in line-attractor decisions).
- Nearby initial conditions separate over meaningful timescales (supporting context-dependent and history-dependent control).
- Task training can carve specific trained attractors (rotations, fixed points, line attractors — see [[Computation Through Dynamics]]) out of a dynamically rich background.

In this reading, criticality is the substrate that makes flexible control possible. Where [[Attractor Dynamics|specific attractors]] encode specific control policies, criticality ensures the space of possible policies remains richly accessible.

## Caveats

- Random asymmetric networks at gJ = 1 are *marginally* unstable in a generic way; *trained* cortical networks at their operating point may have rich structured attractors that do not reduce to being near the SCS transition. The edge-of-chaos framing is clearer for untrained reservoirs than for trained cortex.
- The transition point gJ = 1 is specific to the SCS ensemble (Gaussian, zero mean, asymmetric, fully connected). Real connectivity has Dale's law, sparsity, and low-rank structure that shift or restructure the transition. [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] make this explicit at the rate-model level: when the E/I dichotomy is imposed by construction (as in real cortex), the "edge" is the set of parameter-space boundaries separating simple hysteresis, multi-stability, and limit cycles — and their Theorem 4 says any point deep in the limit-cycle regime is close (in bias space) to a hysteresis regime. "Edge of chaos" in a structured E-I network is more a statement about sitting near regime-boundary surfaces in the WC parameter space than about proximity to gJ = 1.
- "Criticality" has been used loosely across fields — the [[sompolinsky-1988-chaos-random-networks|SCS]] transition, Beggs-style avalanche criticality, and Ising-model critical points are related but distinct phenomena.

## Sources

- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — the phase transition to chaos at gJ = 1 in random asymmetric rate networks; theoretical anchor for the edge-of-chaos hypothesis in neural networks.
- [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] — spiking-network analogue: the balance point g = 4 separates asynchronous-irregular from synchronous regimes in sparsely connected E-I integrate-and-fire networks, with critical-slowing-style finite-size coherence times scaling as 1/ε at the boundary.
- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — structured rate-level E-I dynamics: "edge" in real cortex is the set of regime-boundary surfaces between simple hysteresis, multi-stability, and limit cycles, not proximity to gJ = 1; Theorem 4 says any limit-cycle-capable population is close (in bias space) to a hysteresis regime.
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — constructive operational definition: FORCE training is best just below the upper `g` boundary where it still suppresses chaos (`g ≈ 1.5`, fails at `g ≈ 1.56`); the operating point is defined by what the learning rule can still do, not by an abstract property of the untrained network.
