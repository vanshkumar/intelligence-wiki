---
title: "Spin Glass"
type: concept
aliases: ["spin glasses", "Sherrington-Kirkpatrick model", "SK model", "Edwards-Anderson model"]
tags: [statistical-physics, disordered-systems, hopfield, associative-memory, energy-landscape, mean-field]
source_count: 1
last_updated: 2026-04-27
confidence: established
---

A **spin glass** is the simplest abstract model of a disordered magnetic material: a network of binary spins `S_i ∈ {±1}` coupled by **random** ferromagnetic and antiferromagnetic interactions `J_ij`, with no spatial regularity. The defining feature is **frustration** — competing interactions that cannot all be simultaneously satisfied — which produces a rugged [[Energy Landscape|energy landscape]] with exponentially many metastable states. Spin glasses are central to this wiki not because the brain is a spin glass, but because **the analytical machinery developed to solve them ([[replica-method|replica methods]] + [[Dynamical Mean-Field Theory|DMFT]]) is the foundation of essentially all rigorous theory of large random recurrent neural networks**, including [[attractor-dynamics|Hopfield-style associative memory]].

## The model

The classic Hamiltonian (Edwards–Anderson, 1975):

```
H = − Σ_{⟨i,j⟩} J_ij S_i S_j − h Σ_i S_i
```

where `S_i ∈ {±1}`, `h` is an external field, and the couplings `J_ij` are drawn independently from some symmetric distribution (e.g., Gaussian with mean 0 and variance fixed). Two canonical cases:

- **Edwards–Anderson model** (1975) — finite-dimensional lattice, nearest-neighbor `⟨i,j⟩` couplings only. Mathematically hard; mostly studied numerically.
- **Sherrington–Kirkpatrick (SK) model** (1975) — fully connected, `J_ij ~ 𝒩(0, 1/N)` for all `i ≠ j`. The mean-field limit; exactly solvable in `N → ∞` by replica methods. **The canonical model that Parisi solved.**

Because the couplings come in random signs, no spin configuration can satisfy every bond — the system is **frustrated**. There is no unique ground state; instead, exponentially many metastable configurations sit at low energies, separated by barriers.

## Key phenomena

### Frustration and rugged landscapes

In an unfrustrated ferromagnet, the ground state is unique (all spins aligned) and the energy landscape is convex-like. In a spin glass, the random sign mixture means that for almost any local arrangement, at least one bond is violated, and rearranging to satisfy it violates another. The result is a landscape with:

- **Exponentially many** local minima (metastable states), with energies densely covering an interval.
- **Hierarchical organization** — minima cluster into "valleys within valleys" — captured exactly by Parisi's [[replica-method|hierarchical RSB]] solution.
- **Ultrametric distances**: among any three pure states, the pairwise overlaps satisfy the strong triangle inequality. Pure states sit at the leaves of a tree.

### Phase transition

The SK model has a sharp phase transition at `T_c = J` (for unit-variance couplings):

- **Paramagnetic phase** (`T > T_c`): replica symmetry holds; mean-field analysis with a scalar order parameter `q = ⟨⟨S_i⟩²⟩` works.
- **Spin-glass phase** (`T < T_c`): replica symmetry is **broken**; the order parameter is a function `q(x)` on `[0, 1]` ([[parisi-1979-replica-symmetry-breaking|Parisi 1979]]). The system has many pure states, ergodicity is broken, and the equilibrium decomposes into a hierarchical mixture.

### Slow dynamics, aging, memory effects

Spin glasses exhibit dramatically slow relaxation: when quenched below `T_c`, autocorrelation functions never reach equilibrium on experimental timescales. The system **ages** — its response at time `t` depends on how long it has been since the quench. This is a hallmark of broken ergodicity: the dynamics get trapped in finite portions of state space, hopping between metastable states on glassily distributed timescales.

These dynamical features are described by **out-of-equilibrium DMFT** (Cugliandolo & Kurchan 1993) — the dynamical sibling of Parisi's static RSB. Aging in spin glasses is the cleanest example of how a hierarchical equilibrium structure produces a hierarchical dynamical signature.

## Why spin glasses matter for this wiki

Spin glasses are physics, not biology. Their relevance to biological intelligence is **methodological** and runs through associative memory, learning theory, and rugged-landscape thinking:

### Associative memory: the Hopfield connection

Hopfield's 1982 model of associative memory writes the same Hamiltonian as a spin glass, but with **non-random** couplings:

```
J_ij = (1/N) Σ_μ ξ_i^μ ξ_j^μ      (Hebbian sum over patterns ξ^μ)
```

When the number of stored patterns `p ≪ N`, this is a structured ferromagnet (each `ξ^μ` is a clean basin of attraction). When `p` is comparable to `N`, the cross-talk between stored patterns makes the effective couplings look random — the network behaves like a spin glass, with retrieval competing against catastrophic interference. The replica calculation of **Hopfield capacity** (Amit, Gutfreund, Sompolinsky 1985, 1987) shows:

- **Retrieval phase** for `α = p/N < α_c ≈ 0.138`: clean memory recall.
- **Spin-glass phase** for `α > α_c`: stored patterns are no longer attractors; the network is dominated by spin-glass-like spurious states.

This is a textbook case of how a brain-like system (a Hebbian associative memory) inherits spin-glass physics in the high-load regime. **The capacity bound is the spin-glass transition.**

### Sparse coding pushes back the spin-glass transition

Pure Hopfield is dense (each pattern uses `≈ N/2` active spins). [[Sparse Coding|Sparse codes]] — patterns where only a small fraction of spins are active — raise the capacity beyond the dense `0.138 N` bound, sometimes substantially. This is a quantitative form of the wiki's general theme that [[Sparse Coding|sparseness]] mitigates interference and supports fast Hebbian learning. The analytical handle for "how much" is again the replica calculation, now applied to a sparse Hopfield variant.

### Asymmetric couplings: from spin glass to chaos

The Hopfield/spin-glass picture relies on **symmetric** `J_ij = J_ji`, which guarantees an energy function and detailed balance. Cortical connectivity is broadly **asymmetric** — most synaptic connections are not reciprocated. This is the regime [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] analyze: random asymmetric `J` removes the energy function, and the only stable attractor is **chaos** at high gain. Spin-glass freezing requires symmetric couplings to make sense; the natural cortical regime is the chaotic counterpart and is treated by [[Dynamical Mean-Field Theory|DMFT]] rather than replica methods.

### Energy landscapes in modern deep learning

The picture of an exponentially many-attractor system organized hierarchically has been imported (with varying degrees of justification) into discussions of deep-network loss landscapes (Choromanska et al. 2014). Modern Hopfield networks (Krotov–Hopfield 2016, Ramsauer 2020) use modified energy functions that achieve exponential storage capacity by *avoiding* the spin-glass regime — the energy landscape becomes "spiky" rather than rugged, with wide basins around stored patterns. The ongoing research program on energy-based models (and their connection to attention) inherits the conceptual frame even when the technical analysis differs.

## Spin-glass phenomena that *don't* generalize obviously to brain models

It is worth noting which spin-glass features may **not** carry over:

- **Aging and slow relaxation.** Cortex operates fast; sustained equilibrium below `T_c` and broken ergodicity over experimental timescales is not a typical regime for cortical dynamics. Whether biological associative memory exhibits any analog of aging is largely open.
- **Symmetric couplings.** Most cortical connectivity is asymmetric; spin-glass static analysis applies cleanly only to the symmetric idealization.
- **Equilibrium thermodynamics.** Spin-glass theory is mostly an equilibrium theory (with non-equilibrium dynamical extensions). The brain is driven and dissipative; equilibrium statements need careful translation.

These limitations are part of why this wiki treats spin glasses as a **methodological foundation** rather than a direct biological model.

## Sources

- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — the seed paper that solves the mean-field SK spin glass via hierarchical replica symmetry breaking; introduces the function-valued order parameter `q(x)` and the ultrametric organization of pure states.

## See Also

- [[replica-method|Replica Method & RSB]] — the analytical machinery
- [[Dynamical Mean-Field Theory]] — dynamical sibling, used for chaotic asymmetric networks
- [[energy-landscape|Energy Landscape]] — the rugged-landscape picture
- [[attractor-dynamics|Attractor Dynamics]] — Hopfield networks as structured spin glasses
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — the asymmetric-`J` sibling problem
- [[sparse-coding|Sparse Coding]] — the move that raises Hopfield capacity above the spin-glass bound
