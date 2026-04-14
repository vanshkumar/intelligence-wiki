---
title: "Endotaxis"
type: theory
aliases: ["virtual odor navigation", "internal gradient ascent"]
tags: [navigation, cognitive-map, chemotaxis, hebbian-learning, neuromorphic]
source_count: 1
last_updated: 2026-04-14
status: emerging
---

Endotaxis is a proposed neural algorithm for cognitive navigation that **repurposes the ancient chemotaxis control module** by computing an internal "virtual odor" — a signal that declines with graph distance to a chosen target. The animal then follows this signal uphill using the same closed-loop gradient-ascent controller that evolved for tracking real chemical gradients. Proposed by [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]].

## The Core Move

Every motile species has chemotaxis — an evolutionarily ancient sensorimotor controller that turns a scalar gradient signal into directed movement (bacteria, worms, insects, mammals all share this capability). Rather than inventing new machinery for map-based navigation, endotaxis generates an **internal** signal with the same gradient structure and feeds it into the existing chemotaxis module. No new controller is required; only an internal signal generator.

This is the sharpest circuit-level instantiation in the wiki of the organizing principle that intelligence *extends* sensorimotor control rather than replacing it.

The chemotaxis controller being repurposed is itself not a fixed primitive. [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] show that even in *C. elegans*, the CO₂ chemotaxis circuit is life-stage-dependent — different interneurons are recruited in dauer larvae vs. starved adults despite identical anatomy. The "module being repurposed" by endotaxis-style internal gradient generation is already a flexible, [[Context-Dependent Circuit Reconfiguration|state-reconfigurable]] object. See also [[C. elegans Chemotaxis Circuit]].

## The Circuit

Four neuron types with strictly local Hebbian plasticity:

- **Point cells**: one-hot location encoders (small place fields). Assumed present from initial environment exposure.
- **Map cells**: all-to-all recurrent layer. Hebbian synapses between map cells strengthen when two are co-active in rapid succession → the recurrent weight matrix `M` converges to the environment's adjacency matrix `A`.
- **Goal cells**: convergent readout. When a resource cell fires (animal is at food/water/home), the goal-cell synapses imprint the current map-cell activity pattern.
- **Resource cells + mode switch**: select which virtual odor gets routed to the chemotaxis module.

## The Theorem

With perfect map learning (`M = A`) and goal synapses set at target `y` (`gₖ = v(y)`), the goal signal at location `x` is the matrix element

    Eₓᵧ = v(y) · v(x)

of `E = (γ⁻¹I − A)⁻ᵀ (γ⁻¹I − A)⁻¹`. For small neural gain γ:

    Eₓᵧ → γ^(2 + Dₓᵧ)

where Dₓᵧ is the **shortest graph distance** from y to x. The goal signal decays exponentially and monotonically with graph distance — so local gradient ascent on this signal finds the shortest path, with no planning machinery, no backprop, and no supervisor.

## Critical Gain

The largest useful gain is bounded by stability: γ < γ_c = 1/λ_max(A). For typical graphs with 2–4 edges per node, γ_c ≈ 0.3. A single parameter set (γ ≈ 0.29, θ ≈ 0.26, α = 1) works across structurally dissimilar environments (ring, binary tree, Tower of Hanoi). The tradeoff: higher γ extends spatial reach, lower γ stays safely away from instability. A saturating activation function (Fig. 7) roughly doubles the usable range.

## Three Behaviors in One Circuit

- **Exploration**: random walk while map synapses Hebbian-learn the adjacency matrix.
- **Goal-directed navigation**: once a resource is encountered, goal synapses imprint in one shot; the agent ascends the goal signal to return.
- **Patrolling**: add habituation in point cells (sensitivity decays with visits, recovers on timescale τ). Recently-visited locations produce weaker map output, so gradient ascent on a uniform "neglect" goal steers the agent toward unvisited regions. With β = 1.2, τ = 100 on the Rosenberg labyrinth, the agent executes a perfect 252-step patrol.

This unifies the three navigation modes documented in [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] under a single circuit.

## One-Shot Homing — A Clean Test Case

When the agent first enters an environment, only the entrance point cell fires. A single goal synapse from that point cell to a "home" goal cell gets potentiated *before any map exists*. As the map fills in during subsequent exploration, the home goal signal spreads through the graph by the resolvent dynamics — so the animal can home directly from locations it has never returned to. Mice show exactly this behavior after a single inbound traversal.

## Relation to the Successor Representation

The matrix `Y = (γ⁻¹I − A)⁻¹` is formally similar to the **successor representation** (Dayan 1993; Stachenfeld et al. 2017; Fang et al. 2023) — but the interpretation differs. In SR, γ is a *temporal discount factor* from RL theory. In endotaxis, γ is a *neural gain* — a parameter of circuit dynamics, with no time-horizon semantics. The agent has no time horizon; it wants the shortest path. See [[Successor Representation]].

## Predictions for Biology

- **Place-field size gradient across cell types**: point < map < goal. Matches the septotemporal gradient in the hippocampus (Kjelstrup et al. 2008).
- **Sudden place-field emergence**: goal cells should develop fully-formed place fields after a single salient event — matching Bittner et al. (2017)'s observation of calcium-plateau-driven CA1 place field formation.
- **Convergent-Hebbian motif** realized in the insect [[Mushroom Body]] (Kenyon cells → MBONs) and proposed for the vertebrate [[Hippocampus]]. Same computational motif across deeply divergent lineages.

## Limitations

- Discrete graphs, not continuous environments (though point cells with overlapping receptive fields should generalize).
- Trial-and-error at each decision — no sequence-level planning; the agent samples local options and picks the best.
- The mode switch is given, not derived. Where and how is it implemented biologically?
- No mechanism for online adjustment of γ to match environmental connectivity statistics.

## Sources

- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — introduces endotaxis as a circuit model of cognitive navigation
