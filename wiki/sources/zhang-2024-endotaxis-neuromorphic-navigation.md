---
title: "Endotaxis: A Neuromorphic Algorithm for Mapping, Goal-Learning, Navigation, and Patrolling"
type: source
source_type: paper
authors:
  - "Tony Zhang"
  - "Matthew Rosenberg"
  - "Zeyu Jing"
  - "Pietro Perona"
  - "Markus Meister"
year: 2024
doi: "10.7554/eLife.84141"
tags: [navigation, cognitive-map, chemotaxis, mushroom-body, hippocampus, hebbian-learning, successor-representation]
date_ingested: 2026-04-14
key_finding: "A simple 3-layer Hebbian circuit can repurpose the ancient chemotaxis module for cognitive navigation by computing an internal 'virtual odor' — a signal that provably declines with graph distance to a chosen target — accounting for one-shot homing, few-shot reward learning, and efficient patrolling observed in mice."
---

## Overview

Zhang, Rosenberg, Jing, Perona & Meister (2024) propose **endotaxis**: a biologically plausible neural circuit that generates *internal* gradient signals ("virtual odors") and then follows them using the ancient chemotaxis control module shared across all motile animals. The key move is computational: rather than invent new machinery for cognitive navigation, reuse the closed-loop sensorimotor controller that evolved for odor tracking and feed it an internally generated signal that carries spatial-structural information.

This paper is the mechanistic complement to [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]]. Where the empirical paper documented what mice actually do in a labyrinth (few-shot reward learning, one-shot homing, efficient patrolling), endotaxis is the circuit-level proposal for *how* they might do it. Both come from the same lab.

[PDF](../../raw/papers/zhang-2024.pdf)

## Key Findings

**1. The circuit.** Four neuron types, connected feedforward with one recurrent stage, all plasticity strictly [[Hebbian Learning|Hebbian]] and local:

- **Point cells** (`uᵢ`): one-hot location code (small place fields) — assumed present from the start of environment exposure
- **Map cells** (`vᵢ`): all-to-all recurrent layer; learns the adjacency matrix of the environment graph via Hebbian coincidence as the animal traverses edges. Input `wᵢ = uᵢ + Σⱼ Mᵢⱼ vⱼ`, output `vᵢ = γ wᵢ` (linear) or saturating (nonlinear variant).
- **Goal cells** (`rₖ`): sum map-cell activity via learned synapses `Gₖⱼ`. When a resource cell fires, the current map-cell activity pattern is written into `Gₖ` — "tagging" that location with a virtual odor.
- **Resource cells + mode switch**: select which virtual odor (food, water, home, "neglect") is routed to the chemotaxis module for gradient ascent.

**2. The central theorem.** With perfect map learning (`M = A`, the adjacency matrix) and the goal synapses set at target location `y` (`gₖ = v(y)`), the goal signal at location `x` becomes

    Eₓᵧ = v(y) · v(x) = [(γ⁻¹I − A)⁻¹ᵀ (γ⁻¹I − A)⁻¹]ₓᵧ

For small gain γ, this quantity is **monotonically related to the shortest graph distance** between x and y:

    Eₓᵧ → γ^(2 + Dₓᵧ)    as γ → 0

So the map-cell recurrent dynamics automatically compute a signal that looks like an exponentially-decaying odor gradient over the environment graph. Gradient ascent on this signal ≡ shortest-path navigation — no planning, no backprop, no supervisor.

**3. Critical gain γ_c.** Stability bound: γ < 1/λ_max(A). For graphs with 2–4 edges per node, γ_c ≈ 0.3. Below → goal signal well-behaved and monotonic over useful ranges; above → dynamics unstable and the distance relationship breaks down. This is a genuine design tradeoff: higher γ extends the spatial reach but approaches the instability boundary. A saturating nonlinearity (Fig. 7) increases the useful gain range by ~2×.

**4. Explains Rosenberg 2021 quantitatively.**
- **Few-shot reward learning**: goal synapses potentiate on a *single* visit to the rewarded location, using the already-learned map. One reinforcement → full goal signal across the graph.
- **One-shot homing**: when the agent first enters a new environment, the entrance point cell fires immediately. A single goal synapse from that point cell to a "home" goal cell gets potentiated before the map is built. As the map subsequently fills in, the home goal signal spreads through the graph — enabling direct homing even from locations never revisited. This precisely matches the mouse homing behavior after a single inbound traversal.
- **Efficient patrolling**: add habituation to point cells (sensitivity decays after each visit, recovers on timescale τ). Recently-visited locations produce weaker map output → gradient ascent on a uniform "neglect" goal signal now steers the agent toward unvisited regions. With β = 1.2, τ = 100 on the Rosenberg labyrinth, the endotaxis agent produces a perfect 252-step patrol that visits every end-node exactly once. Real mice sit at ε ≈ 1 (substantially better than random, below the perfect patrol).

**5. Relationship to successor representation.** The matrix `Y = (γ⁻¹I − A)⁻¹` is formally similar to the successor representation (Dayan 1993; Stachenfeld et al. 2017; Fang et al. 2023) — but the interpretation differs. In SR, γ is a **temporal discount factor** baked into the RL framework. In endotaxis, γ is a **neural gain** — a parameter of the circuit dynamics, not a statement about preferences over time horizons. The agent has no time horizon; it just wants the shortest path, and γ can be tuned to the graph's connectivity statistics.

**6. Distinguishing feature: no external action table.** Endotaxis does not tabulate available actions at each state. The agent simply tries whatever actions exist and picks the one that maximizes the goal signal. Information about the action space stays externalized in the environment, like in real chemotaxis. This "externalized cognition" simplifies the learning problem — the agent only needs one scalar function (the goal signal) rather than a full Q-value over state-action pairs.

**7. Predictions for biology.**
- **Place-field size gradient across cell types**: point cells smallest, map cells medium, goal cells very large (since goal cells pool over much of the environment). Consistent with Kjelstrup et al. (2008)'s 10× gradient along the hippocampal septotemporal axis. Goal-cell-like large place fields are reported in rat cortex (Hok et al. 2005).
- **Sudden place-field emergence**: when the agent first visits a salient location, the goal synapses potentiate via strong Hebbian coincidence → a place field appears in a single event. Matches Bittner et al. (2017)'s observation of sudden CA1 place-field formation via dendritic calcium plateaus.
- **Kenyon cell / mushroom body motif**: the "sparsely-selective large population → convergence onto small readout → Hebbian plasticity at the output" circuit motif is explicitly realized in the insect [[Mushroom Body]] (Kenyon cells → MBONs). Endotaxis proposes the mushroom body is doing spatial cognition via endotaxis in species that rely on it for navigation (bees, ants).

## Methods

- **Theory**: analytical derivation of the goal-signal-as-graph-distance relationship from the resolvent matrix; eigenvalue bound for stability.
- **Simulation**: ring graphs, binary-tree labyrinths (matching Rosenberg 2021), and Tower-of-Hanoi-style loopy graphs. Monte Carlo and closed-form Markov-chain evaluation of navigation performance.
- **Parameter sensitivity**: 3 parameters (gain γ, threshold θ for map-synapse learning, learning rate α for goal synapses). Performance is tolerant (10–20% slop); a single parameter set works across structurally diverse environments.
- **Code**: github.com/markus-meister/Endotaxis-2023

## Implications

**For the control thesis.** This paper is a concrete instantiation of the wiki's organizing principle. Chemotaxis is the ancient sensorimotor control loop — bacteria already have it. Endotaxis doesn't replace the controller; it *builds an internal generator of control signals* so the same loop can operate in environments without real chemical gradients, over targets that aren't odors, and at distances that exceed the sensory range. This is exactly the "memory/learning extend the reach of control" story, realized at the circuit level. The map cells extend reach over latent variables (graph structure); the goal cells extend reach over counterfactuals ("what signal would I get if I went there?"); the mode switch extends reach over multiple concurrent control objectives.

**For "simple rules, complex architecture".** Converges with [[li-2024-prediction-noise-reward|Li et al. (2024)]] and [[meister-2022-learning-fast-slow|Meister (2022)]]: the learning rules are simple and local (Hebbian throughout), the cells are plain linear rate neurons, and yet the circuit solves mapping, goal-learning, navigation, and patrolling. The computational work is done by the *architecture* (3-layer feedforward + recurrent map) and by the repurposing of an ancient module (chemotaxis). No new learning algorithm, no new neural machinery.

**For hippocampus vs. mushroom body.** The same computational motif (sparse place-like code → convergent readout with Hebbian plasticity) is proposed for both insect and vertebrate cognitive navigation. If correct, this is a deep homology — mushroom body and hippocampus solving the same computational problem with the same primitive, via independent or pre-bilaterian evolution.

**For evolution of intelligence.** The paper supports the view that cognitive navigation is not a qualitatively new capacity built from scratch but a repurposing of a pre-existing sensorimotor controller. The hard evolutionary work was done long before brains existed (chemotaxis in bacteria); cognitive extensions required only adding an internal signal-generation stage in front of the existing controller.

## Connections to Existing Knowledge

- **[[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]]**: endotaxis is the circuit-level proposal for the behavioral phenomena Rosenberg documented. Same lab, companion papers.
- **[[meister-2022-learning-fast-slow|Meister (2022)]]**: endotaxis relies entirely on the fast-local-Hebbian regime Meister argues for. The sparse point/map/goal hierarchy is exactly the kind of architecture that makes fast Hebbian learning work.
- **[[Hebbian Learning]]**: all three learning rules in endotaxis (map synapses, goal synapses, point-cell habituation) are strictly local coincidence detectors.
- **[[Place Cells]]**: the three cell types predict the observed place-field size gradient along the septotemporal axis of the hippocampus and the sudden single-event place-field formation mechanism.
- **[[Hippocampus]]**: endotaxis is a candidate computation for hippocampal spatial cognition.
- **[[Sparse Coding]]**: the mushroom-body motif (sparse Kenyon cells → dense MBONs via Hebbian convergence) is the cross-taxon instantiation of the sparse-code-enables-Hebbian-association principle.
- **[[li-2024-prediction-noise-reward|Li et al. (2024)]]**: both papers argue for emergent goal-directed behavior from simple local rules + architectural motifs; endotaxis adds spatial structure and an explicit cognitive map, while PaN generates reward-seeking without spatial structure.
- **[[Degeneracy]]**: the same endotaxis motif appearing independently in mushroom body and hippocampus is convergent computational structure despite different neural substrates.
- **Successor Representation** (Dayan 1993, Stachenfeld 2017, Fang 2023): formally similar mathematics with different interpretation (neural gain vs. temporal discount).

## Open Questions Raised

- Is endotaxis actually the computation used in the hippocampus? Direct tests would require recording point/map/goal-like populations during navigation and showing the predicted goal-signal gradient. The goal-cell place-field signature (very large field, sudden single-event emergence) is testable with current imaging.
- How does the mode switch work mechanistically? The paper treats it as given. The authors suggest anatomical circuit tracing — finding a module that receives convergent goal-signal inputs and outputs to the chemotaxis module — as the experimental entry point.
- Can endotaxis be extended to continuous environments (not just graph-structured ones)? Point cells with overlapping receptive fields would naturally generalize, but the monotonicity theorem is proved for discrete graphs.
- Endotaxis is "trial-and-error" at each decision — it samples available actions and picks the best. How does this compose with sequence-level planning? The paper notes this as a limitation and a direction for future work.
- How does endotaxis relate to [[Memory Consolidation]]? The map is acquired online during exploration — does it subsequently get consolidated to a long-term cortical substrate, and if so, how does the goal-signal machinery interact with that?
- The critical gain γ_c depends on graph topology (via λ_max(A)). Can neurons tune γ automatically based on the connectivity statistics they are experiencing? This would be necessary for an animal that moves between structurally different environments.
- What is the evolutionary relationship between the mushroom body and hippocampus as endotaxis substrates? Deep homology (pre-bilaterian origin) or convergent evolution?
