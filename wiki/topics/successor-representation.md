---
title: "Successor Representation"
type: theory
aliases: ["SR", "successor features"]
tags: [reinforcement-learning, navigation, predictive-representation, hippocampus]
source_count: 2
last_updated: 2026-05-01
status: established
---

The successor representation (SR) is a predictive representation of state in which each state is encoded by the **expected discounted future occupancy** of every other state under the current policy. Introduced by Dayan (1993), it sits between model-free and model-based reinforcement learning — it factorizes the value function into a state-prediction part (the SR) and a reward part, enabling fast value recomputation when reward locations change.

## Definition

For a Markov process with transition matrix T and discount γ ∈ [0, 1):

    M = (I − γT)⁻¹

The (i, j) element of M is the expected discounted number of future visits to state j starting from state i. Value for any reward vector r is simply V = M r, so re-evaluating policy under a new reward requires only a matrix-vector product — no re-learning the transition dynamics.

## Biological Relevance

Stachenfeld, Botvinick & Gershman (2017) proposed that [[Place Cells|hippocampal place cells]] encode a successor representation rather than pure allocentric location. Predictions include place-field asymmetry along common travel directions, field expansion near goals, and replay structure — all partially supported by experiment.

## Relation to Endotaxis

[[Endotaxis]] ([[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. 2024]]) uses a matrix with formally similar structure,

    Y = (γ⁻¹I − A)⁻¹

where A is the graph adjacency matrix and γ is the **neural gain** of map cells. The mathematics overlap substantially but the interpretations diverge:

| | Successor Representation | Endotaxis |
|---|---|---|
| γ semantics | temporal discount | neural gain |
| time horizon | explicit (1/(1−γ) steps) | none |
| purpose | value computation for RL | gradient ascent for chemotaxis module |
| representation | state × state predictions | location signal decaying with graph distance |
| training | TD-like updates | Hebbian coincidence |

Both produce a representation whose matrix elements are monotonic in graph distance; the difference is what the organism is supposed to *do* with it. SR fits into a value-based RL framework with explicit reward; endotaxis fits into a chemotaxis-based control framework with no explicit utility.

## Implications

The formal overlap between SR and endotaxis suggests the brain may have a single underlying representational primitive (a "resolvent-of-connectivity" signal) that can be read out either as a value function (in an RL interpretation) or as a goal gradient (in an endotaxis interpretation). The interpretation is determined by what downstream circuits do with the signal, not by the signal itself.

## Limitation: SR Operates Over Observations

[[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] press a sharp point against SR as a model of hippocampal cognitive maps: SR defined over **observations** is a first-order Markov object on the observation alphabet and inherits all the failures of first-order observation models when sensory input is aliased (different latent states producing identical observations, or identical latent states producing different observations across contexts). Splitter cells, event-specific representations, lap cells, and the disambiguation of overlapping rooms in transitive-inference tasks all require representations that distinguish *contexts within an observation* — which observation-level SR cannot do.

The fix is to define SR over **lifted hidden states**, e.g., the clones of a [[Clone-Structured Cognitive Graph|CSCG]]. In that combined formulation, the lifting is done by EM on the cloned HMM, and SR runs on the resulting hidden-state graph for value-based readout. The two frameworks are complementary at that point — CSCG learns the structured graph, SR provides the value-discounted predictive readout — rather than competitive. The competition is only at the interpretation level: is the hippocampus "doing SR" (Stachenfeld et al. 2017) or "lifting observations and doing inference" ([[george-2021-clone-structured-cognitive-graphs|George et al. 2021]])? Empirical splitter-cell and ESR data favor the latter framing.

## Sources

- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — discusses formal similarity and interpretive differences between endotaxis and SR
- [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] — argues observation-level SR cannot represent aliased contexts; splitter cells and event-specific representations require lifting observations into hidden state space
