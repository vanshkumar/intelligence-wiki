---
title: "Clone-Structured Cognitive Graph"
type: concept
aliases: ["CSCG", "cloned HMM", "clone-structured HMM", "action-augmented cloned HMM"]
tags: [cognitive-map, hippocampus, hmm, graphical-models, planning, schema, splitter-cells]
source_count: 1
last_updated: 2026-05-01
confidence: emerging
---

A clone-structured cognitive graph (CSCG) is a sparse over-complete hidden Markov model in which each observed symbol is emitted by multiple hidden states ("clones"), with deterministic block-structured emissions and dense action-conditioned transitions. Introduced by [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] as a unified model of hippocampal cognitive-map function, the CSCG lifts aliased sensory observations into a hidden state space that supports transitive inference, schema transfer, hierarchical planning, and a wide range of place-cell phenomena under one mechanism.

## Structure

- **Hidden states** `z ∈ {1, ..., H}` partitioned into `E` clone-blocks `C(j)`, one block per emission symbol
- **Emission matrix** is deterministic: `P(x = j | z = i) = 1` if `i ∈ C(j)`, else 0 (the "cloning" structure)
- **Transition matrix** `T(i, j) = P(z' = j | z = i, a)` indexed by both prior state and action
- **Joint** `P(x_{1:N}, a_{1:N-1}) = Σ_z P(z_1) Π_n P(z_{n+1} | z_n, a_n)` with the emission collapse making forward-backward operate on small blocks of `T`

The cloning structure is what distinguishes CSCG from a generic HMM: the deterministic block emissions create a sparse computational shortcut and an interpretable representation in which each clone "stands for" a particular context in which a sensory observation occurs.

## What CSCG buys you

The model's claim is that one parameterization explains a long list of hippocampal phenomena that have previously required separate accounts:

- **Cognitive map from aliased input** — random walk in a 6×8 room with 4 unique colors recovers the 2D topology
- **Transitive inference** — disjoint episodes in two overlapping rooms get stitched into a single coherent map; planning works between locations never traversed end-to-end
- **Schemas / structural transfer** — freeze the transition matrix, re-train the emission matrix on a structurally identical room with new observations → fast acquisition
- **[[Splitter Cells]]** — different clones for shared physical locations in different routes (Wood et al. 2000)
- **Event-specific representations / lap cells** — different clones for the same observation in different laps (Sun et al. 2019)
- **Place-cell remapping** — global / partial / rate remapping fall out as different operating points on the (training × inference uncertainty) surface of a single CSCG trained across multiple environments
- **Hierarchical planning** — community detection on the learned transition matrix recovers nested modular structure for cheaper planning
- **Replay** — sampled trajectories from the model

## Inference and Planning

All queries reduce to message passing on the cloned chain:
- **Prediction**: forward sum-product
- **Smoothing / belief estimation**: forward + backward
- **Planning**: clamp current observation/clone and target; run forward-backward to recover the action sequence (planning as inference)
- **Most-likely path**: Viterbi
- **Replay**: forward sampling

Exact inference is tractable because the deterministic emissions reduce per-step computation to small `T` sub-blocks rather than full `H × H` operations.

## Learning

EM (Baum–Welch) on (sensation, action) sequences. A small Dirichlet pseudocount κ regularizes the transition matrix. Online and adaptive variants are sketched in the methods. The authors claim EM is "approximated by [[Long-Term Potentiation|spike-timing-dependent plasticity]]" but do not derive or simulate this — it is a placeholder for "some local rule should work."

## Proposed Neuronal Implementation

- **Each clone = one neuron**
- **Bottom-up sensory input**: all clones of a given observation receive a common input from that observation
- **Lateral connections** between clones implement the action-conditioned transition matrix
- **Activation**: bottom-up input × lateral message from previous timestep's clone activity
- **Population at time t**: the agent's belief over hidden states

This places CSCG in the [[paradigm-pluralism-comp-neuro|probabilistic / Bayesian-brain]] paradigm cluster, with [[Helmholtz Machine|Helmholtz machines]], [[free-energy-principle|FEP]], and the Tolman-Eichenbaum Machine (Whittington et al. 2020, not yet ingested). It is normative at Marr's computational and algorithmic levels, hand-wavy at the implementational level.

## Distinguishing CSCG From Rivals

| | CSCG | [[Successor Representation\|SR]] | [[Endotaxis]] | TEM (Whittington 2020) |
|---|---|---|---|---|
| Lifts aliased observations? | yes | no (operates on observations) | no (assumes graph) | yes |
| Inference | exact BP | matrix inversion | gradient ascent | approximate |
| Planning | inference (BP) | value × reward | gradient ascent on virtual odor | inference |
| Learns the graph? | yes (EM) | TD on observations | Hebbian on adjacency | gradient |
| Action-conditioned? | yes | implicit (policy in T) | yes | yes |
| Structure / sensory factorization | tight (clones tied to observations) | none | tight | clean |

CSCG and SR diverge because SR over observations cannot disambiguate aliased states; SR could in principle be defined over CSCG hidden states, in which case the two converge in the planning step but differ in *what they store*. CSCG and endotaxis are complementary — endotaxis is a cheap reactive controller assuming a learned graph; CSCG learns the graph by message passing. CSCG and TEM (Whittington et al. 2020, not yet ingested) are the closest rivals: both lift observations into hidden structure; TEM has cleaner factorization of structural and sensory components but only approximate inference, while CSCG has exact inference at the cost of tighter coupling between structure and emission.

## Tensions

- **Substrate-local credit assignment.** The [[credit-assignment-lineage|dendritic credit-assignment lineage]] argues that biologically plausible learning requires local plasticity rules with carefully designed feedback signals. EM/Baum–Welch is a global forward-backward algorithm; the "STDP approximation" is asserted, not derived. CSCG sits on the wrong side of this lineage.
- **Coding presupposition.** [[brette-2018-coding-metaphor|Brette (2018)]] argues that the brain has no external referent for "observation" or "action" symbols. CSCG presupposes pre-grounded sensory categories and pre-labeled action tokens — exactly the assumption Brette challenges. A defense is possible if observations and actions are read as relational structure among co-varying signals (the [[subjective-physics|subjective-physics]] reading), but the paper does not attempt this.
- **Dynamics vs. message passing.** CSCG is structured belief propagation, not a dynamical system in the [[Computation Through Dynamics|CTD]] sense. Whether real cortical / hippocampal computation is better modeled as message passing on a graphical model or as dynamics on a manifold is a live disagreement between paradigm clusters.

## Sources

- [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] — introduces CSCG; demonstrates spatial map formation, transitive inference, schemas, splitter cells, ESR, remapping, hierarchical planning, replay in a single model
