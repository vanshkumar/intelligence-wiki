---
title: "Hopfield Network"
type: mechanism
aliases: ["Hopfield model", "Hopfield associative memory", "Hopfield net"]
tags: [hopfield, attractor-network, associative-memory, content-addressable-memory, energy-landscape, spin-glass, hebbian-learning, recurrent-network]
source_count: 1
last_updated: 2026-04-27
level: circuit
---

A **Hopfield network** is a fully-connected recurrent network of binary (or `±1`) neurons with **symmetric** Hebbian-stored couplings, whose asynchronous dynamics admit a Lyapunov function ([[energy-landscape|energy]]) and whose stable fixed points act as basins of attraction for [[content-addressable-memory|content-addressable memory]]. Introduced by [[john-hopfield|John Hopfield]] in [[hopfield-1982-collective-computational-abilities|1982]], it is the founding model of [[attractor-dynamics|attractor neural networks]] and the canonical example of how useful computation — error correction, categorization, generalization — can **emerge** as a collective property of simple interacting units. Its analytical solution in the high-load regime via [[replica-method|replica methods]] (Amit, Gutfreund & Sompolinsky 1985, 1987) is the textbook example of [[spin-glass|spin-glass]] physics applied to neural networks.

## The model

Neurons `V_i ∈ {0, 1}` (or equivalently `S_i ∈ {±1}`) with thresholds `U_i` (usually 0). Connection matrix `T_ij` with `T_ii = 0`. **Asynchronous** updates at random times: each neuron `i` reevaluates whether `Σ_j T_ij V_j` exceeds its threshold and updates accordingly.

The defining ingredients:

- **Recurrence with strong back-coupling** — every pair of neurons is mutually connected. Unlike feedforward perceptrons, all the interesting behavior arises from the feedback loops.
- **Symmetric couplings** `T_ij = T_ji` — the case admitting a Lyapunov function. (The asymmetric case admits chaos and is treated by [[sompolinsky-1988-chaos-random-networks|SCS 1988]] / [[Dynamical Mean-Field Theory|DMFT]].)
- **[[hebbian-learning|Hebbian]] storage** — patterns `V^s` are written into `T_ij` by the outer-product rule
  ```
  T_ij = Σ_s (2V_i^s − 1)(2V_j^s − 1),     T_ii = 0
  ```
  (or equivalently `T_ij = Σ_s ξ_i^s ξ_j^s` with `ξ ∈ {±1}`).
- **Asynchronous update** — at each step a random neuron updates. Distinguishes the model from synchronous predecessors (Little 1974); avoids artifacts of forced lock-step that have no biological counterpart.

## The energy function

For symmetric `T`, the function

```
E = −½ Σ_{i ≠ j} T_ij V_i V_j     (+ external field terms if thresholds ≠ 0)
```

is a **Lyapunov function**: `ΔE ≤ 0` on every state update. The dynamics descend the [[energy-landscape|energy landscape]] until a local minimum is reached. Stable states are local minima of `E`; basins of attraction are the regions of state space that flow to a given minimum.

The energy is the same Hamiltonian as an [[spin-glass|Ising model]] — Hopfield himself notes this: "this case is isomorphic with an Ising model." With Hebbian-stored `T`, low-load Hopfield is a structured ferromagnet (each pattern is a clean energy minimum); high-load Hopfield becomes a spin glass (cross-talk between patterns dominates, exponentially many spurious minima emerge).

## Storage capacity

The central quantitative result: a Hopfield network of `N` neurons can store roughly `α_c · N` random patterns before retrieval becomes severely error-prone, with `α_c ≈ 0.14` (and a sharper `α_c ≈ 0.138` from full [[replica-method|replica]] analysis).

### Hopfield's Gaussian-noise estimate (1982)

The expected field on neuron `i` in stored state `V^{s'}` is `(2V_i^{s'} − 1) · N/2`; cross-talk noise from `s ≠ s'` patterns has rms `σ = √[(n − 1) N / 2]`. Treating noise as Gaussian, the single-bit error probability is

```
P = (1 / √(2πσ²)) ∫_{N/2}^∞ exp(−x² / 2σ²) dx
```

At fixed `P`, capacity scales linearly: `n ∝ N`. Hopfield's simulations gave the empirical rule of thumb `n ≈ 0.15 N`.

### Replica solution (AGS 1985, 1987)

Amit, Gutfreund & Sompolinsky used [[parisi-1979-replica-symmetry-breaking|Parisi's]] [[replica-method|replica framework]] to solve the Hopfield network exactly in the `(α, T)` plane, where `α = n/N` and `T` is temperature (noise level on the dynamics). The phase diagram has:

- **Retrieval phase** (`α < α_c ≈ 0.138`, low `T`): stored patterns are stable attractors with sizable basins. Recall is reliable.
- **Spin-glass phase** (`α > α_c` or high `T`): stored patterns lose stability. The system is dominated by exponentially many spurious local minima with no relation to stored patterns — the [[spin-glass|spin-glass]] phase proper.
- **Mixture states** between retrieval and pure spin-glass: combinations of small numbers of patterns can also be stable in some sub-regions.

**The capacity bound *is* the spin-glass transition.** Above `α_c`, the structured-Hebbian-coupling regime of Hopfield becomes indistinguishable from a generic random-coupling spin glass, and stored memories drown in spin-glass spurious states.

### Sparse coding raises the bound

Pure Hopfield is "dense": each pattern has roughly `N/2` active neurons. **[[Sparse Coding|Sparse codes]]**, where only a small fraction `f ≪ 1` of neurons are active in any pattern, raise capacity dramatically — sometimes to capacity scaling super-linearly in `N` rather than linearly. This is one analytical instantiation of the broader theme that sparseness mitigates [[hebbian-learning|Hebbian]] interference. The mushroom-body / cerebellar / hippocampal CA3-DG codes are biological examples consistent with this analytical prediction.

### Modern (dense) Hopfield networks

Krotov-Hopfield (2016) and Ramsauer et al. (2020) replace the quadratic energy with a sharper interaction (e.g., softmax, polynomial of high order). The new energy is shaped to have wide basins around stored patterns separated by *narrow* valleys, rather than the rugged spin-glass-like landscape of dense quadratic Hopfield. This achieves **exponential** storage capacity while avoiding the spin-glass phase entirely. Ramsauer et al. (2020) show that the modern-Hopfield update is essentially equivalent to a transformer attention layer — establishing a direct lineage from Hopfield 1982 to modern large language models.

## Emergent computational properties

Hopfield's foundational claim is that beyond raw storage, the same dynamics yield several other computational capabilities **for free**:

- **Pattern completion / error correction.** A noisy or partial input within a basin recovers the full stored pattern. Empirically (Hopfield 1982, `N = 30, n = 5`): from Hamming distance ≤ 5, the nearest stored pattern is reached >90% of the time.
- **Categorization.** With threshold 0, the system is a forced categorizer: every starting state is assigned to whichever stored pattern it most resembles.
- **Familiarity recognition.** Adding a uniform threshold makes the all-zero state stable; novel inputs flow there. Even at extreme overload (no patterns stable), familiar vs. unfamiliar states differ in **initial processing rate** — a striking emergent two-channel signal.
- **Generalization.** Storing many correlated patterns produces a structured `T̄` such that a partial new pattern stored on `k < N` neurons is completed using mean correlations from past experience.
- **Time-sequence retention (limited).** An asymmetric Hebbian correction `ΔT_ij = A Σ (2V_i^{s+1} − 1)(2V_j^s − 1)` lets the system traverse stored sequences. Length is limited to ~4 in the original paper; extensions go further but the fundamental asymmetric-recurrent-network framing is needed.
- **Memory merging.** Stored patterns at small Hamming distance fuse; this places a quantitative resolution limit on similarity tolerance.
- **Forgetting via saturation.** Bounded `T_ij` (Hebbian increments clipped at a maximum) produces graceful forgetting of distant memories — recent memories overwrite old ones without catastrophic interference. **No special "forgetting circuit" is needed.**

## Robustness

A signature commitment of the Hopfield programme is that the model's collective behavior should be **insensitive to model details**:

- **Asymmetric `T_ij`** — soft-fails: degraded signal/noise but attractor structure preserved. The Hopfield paper offers an elegant argument: when `T_ij ≠ T_ji`, the energy change on a flip splits into a piece identical to the symmetric case (always negative) plus a stochastic piece with mean 0 — equivalent to running the symmetric system at finite temperature.
- **Clipped `T_ij` to ±1** — capacity reduced by factor `2/π` ≈ 0.637, a remarkably mild penalty for radical quantization.
- **Missing reverse synapses** — if `T_ij ≠ 0` then `T_ji = 0` (one-way connections only) — degrades signal/noise by `1/√2`. Failure is gradual as more synapses fail.
- **Noisy / stochastic dynamics** — finite-temperature versions still have well-defined attractors; the basins shrink but persist. AGS analyze the full `(α, T)` phase diagram.

The robustness theme is methodologically central: in [[Degeneracy|biological systems]] which cannot rely on careful component design, the interesting computational properties are the ones that emerge generically from large-population dynamics.

## Hopfield as one pole of the random-recurrent-network problem

The Hopfield network sits at one pole of a broader analytical space:

- **Symmetric `J`, equilibrium statics.** Hopfield network. Energy function exists; attractors are fixed points. Analyzed by [[replica-method|replica methods]]; capacity is `α_c ≈ 0.138`. The spin-glass transition at high load *is* the capacity bound.
- **Asymmetric `J`, dynamic.** [[sompolinsky-1988-chaos-random-networks|SCS 1988]]. No energy function; chaos at high gain (`gJ > 1`). Analyzed by [[Dynamical Mean-Field Theory|DMFT]]. Limit cycles, fixed points, and static spin-glass states exist as solutions but are unstable to fluctuations.
- **Trained (carved out of asymmetric chaos).** [[force-learning|FORCE learning]] ([[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]]) and other training methods carve structured trajectories — line attractors, rotations, fixed points — out of the chaotic background. The [[Computation Through Dynamics|CTD]] view of cortex.
- **Structured (Dale's law, E-I separation).** [[wilson-cowan-1972-ei-populations|Wilson-Cowan]], [[brunel-1999-sparsely-connected-networks|balanced E-I networks]]. Three generic attractor configurations as function of E-I coupling parameters.

The Hopfield network is the **symmetric-equilibrium pole** of this space. Cortical connectivity is broadly asymmetric, placing the natural cortical regime closer to SCS than to Hopfield — which is why this wiki treats Hopfield-style associative memory as a methodologically central rather than a directly cortical model. Hippocampal CA3, with its dense recurrent excitation, is the most plausible direct biological instantiation.

## Biological status

Hopfield himself was upfront about the model's relation to biology: "all modeling is based on details, and the details of neuroanatomy and neural function are both myriad and incompletely known … in the same spirit, I will seek collective properties that are robust against change in the model details." The model is a **statistical-physics universality-class statement** about Hebbian-stored recurrent networks, not a literal model of any specific brain region. Its predictions:

- **Hippocampal CA3** — dense recurrent excitation with [[hebbian-learning|Hebbian]] LTP-driven plasticity is the textbook biological substrate for a Hopfield-style associative memory. Marr (1971) and McNaughton-Morris (1987) embed Hopfield-style attractor dynamics in the trisynaptic loop with sparse DG-CA3 inputs and pattern-completion CA3 dynamics.
- **Cortical working memory** — persistent activity during delay periods can be modeled as a [[wilson-cowan-1972-ei-populations|hysteretic]] Hopfield-like attractor (Amit & Brunel 1997). The [[vyas-2020-computation-through-dynamics|preparatory fixed-point]] structure in mouse ALM (Inagaki 2019) is a clean cortical instance of Hopfield-like discrete attractor memory.
- **Mushroom body** — the Drosophila mushroom body uses sparse-coded Hebbian associations between Kenyon-cell representations and reward / aversion-driven outputs; capacity scaling is consistent with sparse-Hopfield analytical predictions.
- **Neocortex more broadly** — asymmetric, structured (Dale's law), heterogeneous. The Hopfield framework provides the analytical baseline; departures from it (asymmetry, structure, [[Sparse Coding|sparseness]], external drive) are what biological theories of cortical computation must explain.

## Sources

- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — the founding paper. Defines the model, derives the energy function, presents the Gaussian capacity argument and `~0.15 N` empirical rule, and documents the suite of emergent computational properties (error correction, categorization, familiarity, forgetting via saturation).
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — analytical machinery (replica symmetry breaking) used by AGS to compute Hopfield capacity exactly.
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — asymmetric counterpart establishing the chaotic regime.

## See Also

- [[hopfield-1982-collective-computational-abilities|Hopfield 1982 source page]]
- [[content-addressable-memory|Content-Addressable Memory]] — what the network implements
- [[attractor-dynamics|Attractor Dynamics]] — broader dynamical-systems framework
- [[energy-landscape|Energy Landscape]] — the Lyapunov-function picture
- [[spin-glass|Spin Glass]] — high-load Hopfield is a spin glass
- [[replica-method|Replica Method & RSB]] — analytical machinery for Hopfield capacity (AGS 1985, 1987)
- [[hebbian-learning|Hebbian Learning]] — storage rule
- [[sparse-coding|Sparse Coding]] — capacity-boosting move
- [[john-hopfield|John Hopfield]] — author
