---
title: "Haim Sompolinsky"
type: person
tags: [theoretical-neuroscience, dynamical-systems, statistical-physics, random-networks]
affiliation: "Hebrew University of Jerusalem; Harvard University (Center for Brain Science)"
source_count: 2
last_updated: 2026-04-27
---

Haim Sompolinsky is a theoretical physicist and computational neuroscientist whose work spans spin-glass theory, random neural networks, balanced E-I dynamics, and theories of neural coding and learning. He brought the apparatus of disordered-systems statistical physics — dynamical mean-field theory, replica methods, path integrals — to bear on cortical dynamics, producing several of the foundational results in the field.

Selected contributions relevant to this wiki:

- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — the sharp stationary-to-chaos transition at gJ = 1 in random asymmetric rate networks, solved exactly by [[Dynamical Mean-Field Theory|DMFT]]. Theoretical anchor for the [[Edge of Chaos]] framing and the substrate for modern trained-RNN analyses under [[Computation Through Dynamics]].
- **Balanced E-I networks** (van Vreeswijk & Sompolinsky 1996, 1998) — asynchronous irregular firing as a generic property of balanced excitation-inhibition, explaining the variability and low correlations observed in cortex without invoking stochastic noise at the single-neuron level. Brought to the spiking integrate-and-fire level by [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] with Fokker-Planck methods; see [[Excitation-Inhibition Balance]] and [[Asynchronous Irregular State]].
- **Associative memory and attractor networks** (Amit, Gutfreund & Sompolinsky 1985, 1987) — the canonical replica-method calculation of Hopfield capacity (`α_c ≈ 0.138 N`), built directly on [[parisi-1979-replica-symmetry-breaking|Parisi's (1979) hierarchical RSB framework]]. Among the first applications of [[replica-method|replica methods]] outside of physics, and the analytical foundation for the modern theory of associative memory.

## Methodological Lineage

Sompolinsky's toolkit is the **disordered-systems pair** developed in the 1970s–80s spin-glass program:

- **[[replica-method|Replica method]] / RSB** (Parisi 1979 → MPV 1986) — used for static, equilibrium properties of symmetric-coupling networks: Hopfield-network capacity, Gardner volumes for the perceptron, generalization bounds. Sompolinsky's associative-memory work is the canonical neuroscience application.
- **[[Dynamical Mean-Field Theory|DMFT]]** (Sompolinsky & Zippelius 1981 for spin-glass dynamics; SCS 1988 for random rate networks) — used for time-dependent properties of symmetric *or* asymmetric networks: chaos transitions, autocorrelation decays, balanced-state irregularity.

The two methods are conceptually parallel — both reduce `N`-body random systems to tractable single-degree-of-freedom problems in `N → ∞` — and they cover, between them, most of what is rigorously known about large random recurrent networks. Sompolinsky has used both extensively across his career.

## Relevant Work in This Wiki

- [[sompolinsky-1988-chaos-random-networks|Chaos in Random Neural Networks (1988)]] — the dynamical (DMFT) result.
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — the static (RSB) result whose machinery underwrites his associative-memory work.

## Sources

- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]]
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — methodological progenitor for AGS-style associative-memory calculations.
