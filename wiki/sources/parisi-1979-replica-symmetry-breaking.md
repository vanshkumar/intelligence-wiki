---
title: "Infinite Number of Order Parameters for Spin-Glasses"
type: source
source_type: paper
authors:
  - "Giorgio Parisi"
year: 1979
doi: "10.1103/PhysRevLett.43.1754"
tags: [spin-glass, replica-method, statistical-physics, disordered-systems, mean-field, sherrington-kirkpatrick, energy-landscape]
date_ingested: 2026-04-27
key_finding: "The order parameter for a mean-field spin glass is not a number but a function q(x) on [0,1]; replica symmetry must be broken hierarchically into a (in the limit) infinite ladder of order parameters."
---

[PDF](../../raw/papers/parisi-1979.pdf)

## Overview

A three-page *Physical Review Letters* by [[giorgio-parisi|Giorgio Parisi]] that quietly rewrites what an "order parameter" can be. In the [[spin-glass|Sherrington–Kirkpatrick (SK)]] mean-field model of a spin glass, the standard replica-symmetric Ansatz `Q_αβ = q` (Edwards–Anderson) gives a negative zero-temperature entropy and disagrees with Monte Carlo simulations. Parisi shows that the way out is to break replica symmetry **hierarchically**: parametrize the n × n replica matrix `Q_αβ` by `2N+1` numbers `(q_0, …, q_N; m_1, …, m_N)` arranged in a nested block structure, and then take `N → ∞`. The order parameter becomes a **function** `q(x)` on `[0, 1]` rather than a scalar. Convergence in `N` is fast (most of the correction is captured at `N = 1`), the zero-temperature entropy goes to zero with `N`, and quantities like the magnetic susceptibility and internal energy become integrals over `q(x)`. The Fischer relation `χ = β[1 − q_EA]` is broken because `q_EA = max_x q(x)` differs from the "averaged" overlap that drives `χ`.

This is the seed of the **Parisi solution** — what later became known as **hierarchical replica symmetry breaking (RSB)**, the ultrametric organization of pure states (Mézard, Parisi, Sourlas, Toulouse, Virasoro 1984), and a paradigm for understanding disordered systems generally. Parisi's 2021 Nobel Prize in Physics cites this lineage. For this wiki the relevance is methodological: Parisi's static replica framework is the partner of [[Dynamical Mean-Field Theory|DMFT]] (its dynamical sibling), and is the analytical machinery underneath every capacity calculation for Hopfield-style associative memory networks (Amit, Gutfreund & Sompolinsky 1985, 1987). It is also the conceptual ancestor of modern thinking about rugged [[Energy Landscape|energy landscapes]] in deep networks.

## Key Findings

### 1. The replica-symmetric Ansatz fails

In the replica trick, `⟨ln Z⟩` is computed via `lim_{n→0} (⟨Z^n⟩ − 1)/n`, which introduces an `n × n` matrix order parameter `Q_αβ` (zero on diagonal). The naive Ansatz

```
Q_αβ = q     (constant for α ≠ β)
```

is invariant under permutations of the replica indices ("replica symmetric"). For the SK model this gives:

- A negative entropy at zero temperature: `S(0) = −0.17` (must be `≥ 0`).
- Predictions at variance with Monte Carlo simulations of the SK Hamiltonian.

So either the replica trick is wrong or the Ansatz is wrong. Parisi commits to the latter: the true `Q_αβ` is **not** invariant under index permutations — replica symmetry is spontaneously broken.

### 2. The hierarchical Ansatz: a tower of order parameters

Parametrize `Q_αβ` by introducing integers `m_0 = 1, m_1, m_2, …, m_N, m_{N+1} = 0` (with `m_i / m_{i+1}` integer) and values `q_0, q_1, …, q_N`. The `(α, β)` entry is set by the *deepest* level at which the indices `α/m_i` and `β/m_i` first agree:

```
Q_αβ = q_i  iff  ⌈α/m_{i+1}⌉ ≠ ⌈β/m_{i+1}⌉  but  ⌈α/m_i⌉ = ⌈β/m_i⌉
```

Block-diagonally: at the coarsest level (`m_1`) the matrix takes value `q_0` between blocks; within an `m_1`-block but across `m_2`-sub-blocks it takes `q_1`; and so on, until at the finest level `q_N`. For `N = 0` (1 parameter) you recover the replica-symmetric case; for `N = 1` (3 parameters) you recover the case Parisi had analyzed in a companion paper (Ref. 7).

The free energy (near the critical temperature `T_c`, with `τ ∝ T_c − T`) becomes a polynomial in `q_i` and `m_i`:

```
F(q_i, m_i) = Σ_i (m_i − m_{i+1})·[ −τ q_i² − (1/4) q_i⁴ + (1/3)(2m_i − m_{i+1}) q_i³ ]
            + Σ_{i, j>i} (m_i − m_{i+1})(m_j − m_{j+1}) q_i q_j²
```

(Eq. 5 of the paper). One must **maximize** `F` over `q_i, m_i` — not minimize — a counterintuitive feature of the replica trick that comes from analytic continuation in `n` to `n = 0`, where `F` flips sign in the relevant subspace.

### 3. Convergence in N is fast

Stationarity gives the saddle-point values

```
q_0 = τ + C^{(N)} τ² + O(τ³)
q_i = B_i^{(N)} τ + O(τ²),   m_i = L_i^{(N)} τ + O(τ²)
```

with explicit `N`-dependent constants. Plugging back in,

```
F(τ) = (1/3) τ³ + F_4 τ⁴ + F_5(N) τ⁵ + O(τ⁶)
F_4 = 1/4   (independent of N)
F_5(N) = 9/20 − 1/(5(2N+1)⁴)
```

Most of the correction is captured at `N = 1`. The zero-temperature entropy improves rapidly:

| `N`        | `S(0)`  | `U(0)`    |
|------------|---------|-----------|
| 0 (RS)     | −0.17   |           |
| 1          | −0.01   | −0.7652   |
| 2          | −0.003  | −0.7636   |
| ∞ (Parisi) | → 0     |           |

The `N → ∞` limit is the **Parisi solution** — and was eventually proved to be the exact solution of the SK model by Talagrand (2006), confirming a 27-year-old conjecture.

### 4. The order parameter is a function q(x)

In the `N → ∞` limit, encode `(q_i, m_i)` as a piecewise-constant function `q(x)` on `[0, 1]`:

```
q(x) = q_i  for  m_i ≤ x ≤ m_{i+1}
```

Near `T_c`, Parisi finds the explicit form

```
q(x) = (1/3) x + O(τ²)   for  x < 3τ
q(x) = τ + O(τ²)         for  x > 3τ
```

— a linear ramp that saturates at a plateau. **Replica symmetry is unbroken iff `q(x)` is constant.** A function-valued order parameter codes a continuous (in fact: hierarchical / ultrametric) organization of the system's pure states — the physical content that this paper opens but does not fully unpack ("the physical interpretation of this function is unclear at the present moment and it should be the subject of further investigations" — Parisi himself).

### 5. Susceptibility, internal energy, and the broken Fischer relation

In the SK model, magnetic susceptibility `χ` and internal energy `U` are now integrals of `q(x)`:

```
χ = ∫₀¹ β [1 − q(x)] dx
U = ∫₀¹ {β [q²(x) − 1] / 2} dx
```

The Edwards–Anderson order parameter `q_EA = ⟨⟨S⟩²⟩` (the "frozen" overlap of a single pure state with itself) is identified with the maximum:

```
q_EA = max_x q(x)
```

But `χ` integrates `1 − q(x)` over all `x`, not just at the maximum, so the **Fischer relation**

```
χ = β [1 − q_EA]      (replica-symmetric prediction)
```

does **not** hold. Monte Carlo simulations of the SK model already pointed to this violation; the Parisi solution explains it analytically — `χ` "feels" the entire distribution of overlaps among pure states, not just the self-overlap of one.

## Methods

A theoretical/analytical paper. The technical apparatus:

- **Replica trick.** Compute `⟨ln Z⟩_J = lim_{n→0} (⟨Z^n⟩_J − 1)/n` over the disorder distribution of couplings `J_ij`, treating `n` as a positive integer and analytically continuing to `n = 0`.
- **Mean-field free energy near `T_c`.** Taylor expansion of `F(Q)` to fourth order in `Q` (Eq. 2). The cubic `Tr Q³` term and the quartic `Σ_αβ Q_αβ⁴` term are kept; the latter is the unique fourth-order term responsible for replica-symmetry breaking.
- **Hierarchical Ansatz.** Eq. 4 in the paper: a recursive block structure indexed by `(m_1, …, m_N)`, sketched algebraically as `Q_αβ = q_i` whenever the integer-valued ladder of `α/m_j` and `β/m_j` agrees from `j = 1` down to level `i` and disagrees at level `i + 1`.
- **Saddle-point evaluation.** `n → 0` limit of Eq. 5 → free energy as polynomial in `(q_i, m_i)`. Stationarity conditions give the leading-order saddle.
- **Encoding as a function.** Eq. 10–11: define `q(x) = q_i` on `m_i ≤ x ≤ m_{i+1}` and take `N → ∞`.

## Implications

### Within physics

The Parisi solution is now considered the exact solution of the mean-field SK spin glass (rigorously proved by Talagrand 2006). Its structural content — that the equilibrium state of a generic disordered system can decompose into a *hierarchy* of pure states organized **ultrametrically** (the distance between any three states satisfies the strong triangle inequality `d(a,c) ≤ max(d(a,b), d(b,c))`) — was made explicit in Mézard, Parisi, Sourlas, Toulouse & Virasoro (1984). The cavity method (Mézard, Parisi & Virasoro 1986) is the alternative, more probabilistic re-derivation of the same content. Together these tools opened up the analytical study of disordered systems generally: structural glasses, optimization problems (graph coloring, K-SAT, traveling salesman), error-correcting codes, and neural networks.

### For theoretical neuroscience

The relevance for the wiki is mostly **methodological** rather than directly biological. The paper makes no biological claim, but the methods it pioneered are the analytical backbone of large parts of theoretical neuroscience:

- **Hopfield network capacity calculations.** Amit, Gutfreund & Sompolinsky (1985, 1987) used replica methods to compute the storage capacity of the Hopfield model: `α_c ≈ 0.138 N` random patterns can be stored before catastrophic interference. The replica-symmetric calculation gives one estimate; replica-symmetry breaking refines it. Without Parisi's framework these calculations are not analytically tractable.
- **Sibling of [[Dynamical Mean-Field Theory|DMFT]].** DMFT (Sompolinsky 1981 for spin-glass dynamics, [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers 1988]] for random rate networks) is the *dynamical* counterpart of replica methods. Both reduce an `N`-body random system to a tractable effective single-degree-of-freedom problem in the `N → ∞` limit; replica is for **static** equilibrium quantities (free energy, overlap distributions), DMFT is for **time-dependent** quantities (autocorrelations, Lyapunov exponents). The two together cover the analytic toolkit by which statements about large random networks become rigorous.
- **Rugged [[Energy Landscape|energy landscapes]].** The picture of disordered systems with exponentially many metastable states organized hierarchically informs how we think about both biological associative memory (a many-attractor system that must store overlapping patterns) and the loss landscapes of trained neural networks. Choromanska et al. (2014) proposed an explicit analogy between deep-network loss landscapes and mean-field spin glasses; modern Hopfield networks (Krotov & Hopfield 2016; Ramsauer et al. 2020) exploit the same energy-based picture to recover transformer-style attention.
- **Memory as control over longer horizons.** Under the wiki's organizing principle ([[overview|sensorimotor control]]), associative memory is one of the central mechanisms by which biology extends control across time and counterfactuals. The capacity, geometry, and retrievability of stored patterns — which the Parisi machinery quantifies — sets the theoretical limits of what such an extension can achieve.

### What the paper itself flags as unresolved

Parisi is explicit that the *physical interpretation* of the function `q(x)` is, in 1979, unclear: "the physical interpretation of this function is unclear at the present moment and it should be the subject of further investigations." The interpretation that emerged over the next five years — `q(x)` as the cumulative distribution of overlaps between pure states, with the hierarchical block structure tracking ultrametric tree depth — is not in the 1979 paper. The Hessian-eigenvalue check ("at least one eigenvalue should be zero, corresponding to infinite replicon susceptibility") was carried out (de Almeida–Thouless line, Bray–Moore) and confirmed the consistency.

## Connections to Existing Knowledge

- **[[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]]** — the dynamical-mean-field analogue. SCS analyzes a random *asymmetric* network (no Lyapunov function, no equilibrium thermodynamics) and finds chaos at `gJ = 1`. Parisi 1979 analyzes a random *symmetric* system in equilibrium and finds replica-symmetry breaking. The two results bracket the random-recurrent-network problem from the static and dynamic ends.
- **[[Dynamical Mean-Field Theory]]** — sibling method. Both reduce `N`-body random problems to effective single-degree-of-freedom problems; replica handles statics (free energy, overlap distribution), DMFT handles dynamics (autocorrelations, Lyapunov exponents).
- **[[Haim Sompolinsky]]** — the most prolific user of these methods in theoretical neuroscience. The Amit–Gutfreund–Sompolinsky line of Hopfield-capacity calculations rests on Parisi's framework.
- **[[Attractor Dynamics]]** — Hopfield networks (symmetric `J`) live in the regime where Parisi's static analysis applies; their capacity and retrieval radius are computed by replica methods. The chaotic regime ([[sompolinsky-1988-chaos-random-networks|SCS]], asymmetric `J`) is the dynamical counterpart.
- **[[hopfield-1982-collective-computational-abilities|Hopfield (1982)]]** — the structured-coupling neural-network model that AGS (1985, 1987) would analyze with Parisi's framework. Hopfield identifies the symmetric-Hebbian-coupling network with the Ising / spin-glass Hamiltonian explicitly and points to Kirkpatrick-Sherrington 1978; this is the bridge that brings the replica-method machinery into theoretical neuroscience.
- **[[Sparse Coding]]** — the catastrophic-interference limit that motivates sparse codes is exactly the limit that replica calculations quantify in Hopfield networks; sparsity raises the capacity beyond the dense `0.138 N` bound.

## Open Questions Raised

- **What does an ultrametric organization of memories look like in cortex?** If associative memory in cortex is governed by an energy-landscape picture in the spirit of Hopfield, do the metastable attractors organize ultrametrically (hierarchical clustering) or in some flatter way? Empirical signature: the distribution of pairwise overlaps between recalled memory states.
- **Is replica symmetry broken in trained recurrent networks?** Trained RNNs (under [[Computation Through Dynamics|CTD]]) carve structured low-dimensional manifolds out of a chaotic random-network reservoir. The static analog of this question — what does the equilibrium overlap distribution between trained and random states look like — is not resolved.
- **Where does RSB intersect the [[Edge of Chaos]] picture?** The de Almeida–Thouless instability (where the replica-symmetric solution becomes unstable) is a static analog of the SCS chaos transition. Are there biological circuits whose effective parameters sit near both transitions?
- **Modern Hopfield networks and attention.** Modern (dense) Hopfield networks (Krotov–Hopfield 2016, Ramsauer 2020) achieve exponential storage capacity by replacing the quadratic energy with a softmax-like potential; the structural analog of the Parisi solution in this regime is not fully worked out and connects directly to the energy-based reading of transformer attention.
- **Does spin-glass theory predict capacity bounds for [[force-learning|FORCE-trained]] RNNs?** The static-replica machinery would, in principle, bound the number of distinct trajectories that can be stably encoded by a fixed-size chaotic reservoir; this seems open.

## Sources

- Parisi, G. (1979). "Infinite Number of Order Parameters for Spin-Glasses." *Phys. Rev. Lett.* **43**(23), 1754–1756. [PDF](../../raw/papers/parisi-1979.pdf)

## See Also

- [[giorgio-parisi|Giorgio Parisi]] — author
- [[replica-method|Replica Method & Replica Symmetry Breaking]] — methodological context
- [[spin-glass|Spin Glass]] — concept page (covers the SK Hamiltonian as canonical mean-field instance)
- [[energy-landscape|Energy Landscape]] — the rugged-landscape picture in which RSB lives
- [[Dynamical Mean-Field Theory]] — dynamical sibling method
