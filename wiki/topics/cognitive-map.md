---
title: "Cognitive Map"
type: concept
aliases: ["mental map", "spatial map", "internal map"]
tags: [navigation, representation, hippocampus, latent-learning]
source_count: 1
last_updated: 2026-04-14
confidence: established
---

A cognitive map is an internal neural representation of the spatial structure of an environment that supports navigation between arbitrary start and goal points — including to locations never experienced along a direct path. Introduced conceptually by Tolman (1948) on the basis of **latent learning** experiments showing rats use knowledge of maze structure acquired without reward.

## Why It Matters for the Control Thesis

A cognitive map is the canonical example of memory extending the reach of closed-loop sensorimotor control. Without a map, the organism can only act on immediate sensory input. With a map, the same sensorimotor loop can plan routes through unseen portions of space, return home from novel locations, and route-efficiently between arbitrary points. The map is not a separate faculty layered on top of control — it is a set of learned internal signals that feed back into the same control loop, extending what the loop can do.

## Representational Requirements

A useful cognitive map must support three operations:
1. **Mapping** — acquire the connectivity of the environment from experience
2. **Goal tagging** — associate specific locations with behavioral significance (food, water, home, threat)
3. **Readout** — compute, at the animal's current location, a signal that guides movement toward a chosen goal

Different theoretical proposals differ in how each is implemented.

## Computational Proposals

- **Graph + search** (Schölkopf & Mallot 1995; Gaussier et al. 2002; many others) — store an explicit graph; run a search algorithm from current state to goal. Requires accessory mechanisms to propagate signals backward through the graph.
- **Propagating wave / diffusion** (Glasius et al. 1996; Ponulak & Hopfield 2013) — injecting activity at the goal and letting it diffuse produces a gradient the animal can follow.
- **Successor representation** ([[Successor Representation|SR]]; Dayan 1993; Stachenfeld et al. 2017) — each state represented by a time-discounted prediction of future state occupancy; enables efficient value computation.
- **Endotaxis** ([[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. 2024]]; see [[Endotaxis]]) — feed-forward gradient ascent on an internally computed "virtual odor" that decays with graph distance; reuses the ancient chemotaxis controller.
- **Predictive map / transition model** (Fang et al. 2023) — learn transition probabilities, then do prospective rollouts.

The endotaxis proposal is distinctive in requiring no planning or backward-propagation step and in reusing a pre-existing sensorimotor module, making it the most parsimonious of the circuit-level accounts.

## Biological Substrates

- **Hippocampus** — classical vertebrate substrate; [[Place Cells]], grid cells, and related cell types provide the representational scaffolding. Latent learning, one-shot homing, and route efficiency in rodent tasks all depend on hippocampal integrity.
- **[[Mushroom Body]]** — proposed invertebrate substrate. Kenyon cells (sparse, place-like in some contexts) converge onto mushroom body output neurons via plastic synapses — the same sparse→dense Hebbian-convergence motif that endotaxis proposes for vertebrates.
- **Entorhinal cortex** — grid cells provide a structured basis that may feed the hippocampal map.

## Latent Learning as Diagnostic

The defining feature of cognitive-map learning is that it happens **without reward**. Rats that passively explore a maze without food subsequently navigate efficiently when food is introduced, as if they had been building a map all along. This is incompatible with pure reward-driven learning and was the original motivation for Tolman's cognitive-map hypothesis. Modern support: [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] mice explore persistently without reward and then navigate efficiently when reward is added; the endotaxis map-learning phase ([[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. 2024]]) completes entirely during the reward-free exploratory random walk.

## Sources

- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — endotaxis as circuit-level cognitive-map algorithm; explains one-shot homing, few-shot reward navigation, and efficient patrolling from a single Hebbian circuit
