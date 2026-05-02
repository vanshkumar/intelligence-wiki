---
title: "Clone-structured graph representations enable flexible learning and vicarious evaluation of cognitive maps"
type: source
source_type: paper
authors:
  - "Dileep George"
  - "Rajeev V. Rikhye"
  - "Nishad Gothoskar"
  - "J. Swaroop Guntupalli"
  - "Antoine Dedieu"
  - "Miguel Lázaro-Gredilla"
year: 2021
doi: "10.1038/s41467-021-22559-5"
tags: [cognitive-map, hippocampus, hmm, graphical-models, place-cells, splitter-cells, schema, planning, replay]
date_ingested: 2026-05-01
key_finding: "A sparse over-complete HMM (clone-structured cognitive graph) trained by EM on (sensation, action) sequences explains spatial map formation from aliased observations, transitive inference across episodes, schema transfer, splitter cells / event-specific representations, place-cell remapping, replay, and hierarchical planning — all in a single model with exact message-passing inference."
---

## Overview

George et al. propose the **Clone-Structured Cognitive Graph (CSCG)**: a structured, sparse, over-complete hidden Markov model in which each observed symbol is emitted by multiple hidden states ("clones"). Transitions are between clones; emissions are deterministic blocks (each clone emits exactly one observation). The model is **action-augmented** — transitions are `P(z_{n+1} | z_n, a_n)` — and is trained with EM (Baum–Welch) on streams of (sensation, action) pairs. Inference and planning are sum-product / Viterbi message passing.

The paper's claim is that this single model explains a wide range of hippocampal phenomena that have previously required separate accounts: cognitive-map formation from aliased sensory data, transitive inference, transferable schemas, splitter cells / event-specific representations, the various forms of place-cell remapping, replay, and hierarchical planning. The authors propose a neuronal implementation in which each clone is a neuron, lateral connections implement the transition matrix, and sensory observations drive bottom-up input to all clones of that observation.

## Key Findings

### 1. Spatial maps from aliased sensory streams

A 6×8 room with only four unique colored sensory observations is traversed by an agent on a random walk. A first-order Markov model on the observations recovers nothing about the topology. A CSCG with 20 clones per observation, trained on 10,000 (action, observation) pairs, recovers the 2D spatial topology near-perfectly (Viterbi decoding gives 48 hidden states, the optimum for a 6×8 grid). The model can also learn from aliased observations *without* paired actions, though more weakly.

### 2. Transitive inference: stitching disjoint episodes

Two overlapping rooms (8×6 each, 15 unique observations, 3×3 overlap region plus a separate "confounder" patch in the first room that looks identical to the overlap but isn't connected to room 2) are explored on **separate** sequential random walks of 10,000 steps each. A single CSCG trained on both sequences correctly stitches them into a coherent global map: the overlap is merged, the confounder remains correctly unmerged. The model can then plan paths from room-1-only locations to room-2-only locations it has never traversed end-to-end — a clean transitive-inference demonstration.

### 3. Schema reuse

After training a CSCG on Room 1, the **transition matrix is frozen** and the emission matrix is re-initialized to random and re-trained on a few hundred (action, observation) pairs from a structurally identical Room 2 with different sensory observations. The model rapidly learns the new room — much faster than learning from scratch. This operationalizes Tolman / Bartlett "schema" transfer at the algorithmic level.

### 4. Splitter cells, event-specific representations, lap cells

In a figure-8 maze with two routes that share a central segment (Wood et al. 2000), CSCG learns **separate clones** for the shared segment depending on which route is being traversed. Activity of clones in this overlap segment reveals the route's identity — recapitulating the splitter-cell phenomenon. In a 4-lap looping rectangular track (Sun et al. 2019), CSCG learns lap-specific clones for the same observation, reproducing event-specific representations (ESR). In an overlapping odor-sequence task (Ginther et al. 2011), CSCG learns route-specific clones in the long shared middle segment.

### 5. Remapping as inference dynamics

Five rooms with the same 25 sensory observations arranged in different spatial configurations. A single CSCG is trained on random walks across all five rooms (room identity not provided). The clone activations during a 50-step walk show:

- **Partially trained** → activations overlap across rooms ≈ **global remapping** in inference terms
- **Fully trained** → clones cleanly partition by room, with some clones active in multiple rooms ≈ **partial remapping**
- **Fully trained, more uncertainty in inference** → smoothing causes shared clones with reduced firing rates ≈ **rate remapping**

Global / partial / rate remapping fall out as different operating points on the training × uncertainty surface of a single model.

### 6. Hierarchical planning via community detection

Community detection (InfoMap) on the learned CSCG transition matrix recovers room boundaries even when observations are aliased across rooms. In a 4×4 grid of rooms connected by corridors, two rounds of community detection recover a three-level hierarchy: clones → rooms → "hyper-rooms." Hierarchical planning at the highest level first reduces the search space dramatically.

### 7. Replay

Forward sampling from the learned graphical model produces sequences consistent with prior experience — the model's account of hippocampal replay. Two replay roles are proposed: (i) consolidation of trajectories via Viterbi training, and (ii) goal-directed evaluation ("vicarious trial and error" sensu Redish 2016).

## Methods

The CSCG is a structured cloned HMM:

- **Hidden states** `z_n ∈ {1, ..., H}` partition into `E` clone-blocks `C(j)` indexed by emitted observation `j`.
- **Emission matrix** is structured: `P(x_n = j | z_n = i) = 1` if `i ∈ C(j)`, else 0. This is the "cloning" structure.
- **Transition matrix** `T(i, j) = P(z_{n+1} = j | z_n = i, a_n)` is dense within and across clone-blocks.
- The deterministic emission collapses the forward-backward equations: only the sub-blocks of `T` corresponding to the observed emissions enter the recursion, giving computational savings over a generic HMM.

Training is EM/Baum–Welch with a small Dirichlet pseudocount κ for regularization (κ ≈ 10⁻²–10⁻³). Inference is exact belief propagation on the cloned chain. Planning is treated as inference: clamp current observation and goal observation/clone, run forward-backward to recover the action sequence.

The action-augmented form (Eq. 3 in the paper):
```
P(x_1, ..., x_N, a_1, ..., a_{N-1}) = Σ_{z_1, ..., z_N} P(z_1) Π_n P(z_{n+1} | a_n, z_n)
```

The same algorithm (BP) handles: prediction of next observation given action; inference of action given current and target observation; smoothing under noisy/missing observations; one-shot remapping after environmental change.

### Neurobiological implementation

Each clone = one neuron. Lateral connections between clones implement the transition matrix. All clones of an observation receive a common bottom-up "sensory" input. Clone activation = bottom-up input × lateral message (from prior clone activations through the transition matrix). The set of co-active clones at each time step represents the agent's belief over hidden states.

The authors argue, following standard HMM-message-passing-as-cortical-circuit proposals (Rao 2004, George & Hawkins 2009), that EM is *approximated* by spike-timing-dependent plasticity. This claim is asserted, not derived or simulated.

## Implications (paper's own)

- The hippocampus implements a **content-agnostic relational structure learner** rather than a memory index, a relational memory space, or a predictive map narrowly construed.
- Place-field remapping, splitter cells, ESRs, lap neurons, and chunking cells are all manifestations of a single mechanism (learning and inference dynamics in a cloned HMM), not separate phenomena.
- CSCGs subsume successor-representation models because they "lift" aliased observations into a hidden state space; pure SR over observations cannot represent context-dependent transitions.
- CSCGs offer cheaper exact inference than the Tolman-Eichenbaum Machine (Whittington et al. 2020), at the cost of less factorization between structural and sensory components.
- CSCGs may be a path to relational abstractions in artificial general intelligence.

## Thesis Bearing

**Bearing on [[control-thesis-ledger|the control thesis]]: mixed (primary support for P2; partial support for P1; weak / orthogonal to P5 and P6).**

The model is action-augmented and takes (sensation, action) streams as input — fitting the closed-loop sensorimotor framing at the I/O level. The agent's actions index the transition matrix; planning returns action sequences. As an account of "memory and learning extending control over latents and counterfactuals" (P2), CSCG is a strong constructive existence proof: a single learned object supports stitching disjoint episodes, transferring structure across environments, and planning over hierarchical abstractions.

That said, three caveats:

1. The agent in the experiments performs uniform random walks; the closed loop between learned CSCG and behavior is exercised only at test time (planning). The model is compatible with closed-loop control but does not require it for learning.
2. EM/Baum–Welch is a global learning algorithm with forward-backward passes over the whole sequence. The "approximated by STDP" claim is a hand-wave, not a derivation. As an account of substrate-local credit assignment (P5), CSCG sits on the wrong side of the [[credit-assignment-lineage|dendritic credit-assignment lineage]] — it is normative-algorithmic, not biophysical.
3. CSCG is structured message passing on a graphical model, not a [[Computation Through Dynamics|dynamical system]] in the CTD sense. It bears weakly on P6.

CSCG is also unapologetically representationalist: clones *are* the latent states, observations *are* aliased symbols, actions *are* reported by proprioception. This is in direct tension with [[brette-2018-coding-metaphor|Brette's (2018)]] critique of the symbol-grounding presupposition. Brette would push back that the (x, a) stream the model trains on is not what the brain has access to — it presupposes pre-grounded sensory categories and pre-labeled action tokens. A CSCG-style architecture might still be defensible from a [[subjective-physics|subjective-physics]] standpoint if the "observations" and "actions" are read as relational structure among co-varying signals rather than external referents, but the paper does not attempt this.

## Connections to Existing Knowledge

- **[[Cognitive Map]]** — CSCG is a graph + search account in the wiki's existing taxonomy. Distinguished from [[Endotaxis]] in that CSCG *learns the graph structure itself* (via EM over hidden states) and plans by message passing, whereas endotaxis assumes the graph and plans by gradient ascent on an internally generated signal. The two are complementary — endotaxis is the cheap reactive controller, CSCG is the structured planner.
- **[[Successor Representation]]** — explicit rival. The paper's argument is that SR over observations cannot disambiguate aliased states. CSCG lifts aliased observations into a hidden space and *then* the resolvent-of-connectivity structure operates. This is a real distinction: pure observation-level SR is a first-order Markov model over symbols and inherits all the failures the paper attributes to that.
- **[[Place Cells]]** — clones are predicted to manifest as place cells. The model gives a unified mechanism for ordinary place-cell tuning, splitter cells, ESRs, lap cells, and the various remapping phenomena. This places CSCG in direct competition with the [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis circuit-level account]] of place cells (point/map/goal cell types).
- **[[Hippocampus]]** — CA3 / CA1 proposed as substrate. The paper argues message-passing in cloned HMMs maps onto pyramidal-cell columns with shared bottom-up sensory drive and learned lateral connections.
- **[[Memory Consolidation]]** — replay framed as Viterbi sampling from the learned CSCG. Provides a structured-graphical-model account of replay distinct from the SWR-driven phenomenology in [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]].
- **[[Hebbian Learning]]** — the "EM ≈ STDP" claim slots into the wiki's running tension between locality and global error signals. CSCG sits with the [[free-energy-principle|FEP]] / [[Helmholtz Machine|Helmholtz]] / wake-sleep family rather than the dendritic credit-assignment family.
- **Tolman-Eichenbaum Machine (Whittington et al. 2020)** — referenced by the paper as a related but distinct model; not yet ingested in this wiki. TEM has cleaner factorization between structural and sensory components but only approximate inference; CSCG has exact inference but tighter coupling between structure and observation.
- **[[free-energy-principle|Free Energy Principle]] / [[Active Inference]]** — the paper notes that CSCG can be combined with active inference; the EM step corresponds to the M-step of variational EM, and the message passing corresponds to the E-step. Active inference adds priors over actions; CSCG as written has no such prior.
- **[[paradigm-pluralism-comp-neuro|Paradigm pluralism]]** — CSCG sits squarely in the **probabilistic / Bayesian-brain** paradigm cluster. It is normative at Marr's computational and algorithmic levels, hand-wavy at the implementational level. As such, the [[jonas-2017-microprocessor-critique|Jonas–Kording]] caution applies: even with full ground truth on a CSCG-implementing circuit, the standard analyses might or might not recover the algorithmic-level meaning.

## Open Questions Raised

- The "EM ≈ STDP" claim. Is there a local plasticity rule that implements EM on a cloned HMM with the right convergence properties? Or is the claim a placeholder for "some local learning rule will approximate this"?
- How does the brain pick the **number of clones per observation**? The model uses a constant number per emission for simplicity; biological plausibility likely requires growth or pruning.
- How does CSCG account for grid cells? The paper handwaves grid-cell-like properties as eigenvectors of the transition matrix and suggests grid output as just another sensory cue.
- Does CSCG-style learning happen *during* exploration (online EM, with growing transition-matrix evidence) or *during sleep* (batch EM consolidating accumulated experience)? The paper sketches an online variant but doesn't commit to a biological reading.
- Where does the **mode switch** for goal selection live in the CSCG framework? Endotaxis has a specific goal-selection signal; CSCG planning requires clamping the goal observation, but the source of that clamp is unspecified.
- CSCG vs. TEM head-to-head: which factorizations better predict observed neural representations in entorhinal cortex / hippocampus during structural transfer experiments?

## Sources

- George, D., Rikhye, R. V., Gothoskar, N., Guntupalli, J. S., Dedieu, A., & Lázaro-Gredilla, M. (2021). Clone-structured graph representations enable flexible learning and vicarious evaluation of cognitive maps. *Nature Communications*, 12, 2392. [DOI](https://doi.org/10.1038/s41467-021-22559-5)
- [PDF](../../raw/papers/george-2021.pdf)
