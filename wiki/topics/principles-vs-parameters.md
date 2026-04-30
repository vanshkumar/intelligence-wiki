---
title: "Principles vs Parameters"
type: concept
aliases: ["nature vs nurture decomposition", "compressibility of trained networks", "principles/parameters split", "recipe vs trained-state"]
tags: [philosophy-of-neuroscience, methodology, what-is-understanding, compressibility, learning-rules, marr-levels]
source_count: 2
last_updated: 2026-04-30
confidence: emerging
---

A methodological frame, articulated most explicitly by [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]], that splits any learned system into two layers with different epistemic statuses:

- **Principles** — the *recipe* that produces the system. For artificial networks: architecture, loss function, learning rule, optimizer, training data sources. For brains: anatomy, connectivity motifs, [[hebbian-learning|plasticity rules]], developmental program, [[credit-assignment|credit-assignment]] machinery, the [[degeneracy|gene-encoded constraints]] that shape neuronal control algorithms.
- **Parameters** — the *trained state* the recipe produces when run on the world. For artificial networks: the millions to billions of weights after training. For brains: synapse-by-synapse connection strengths, individual cell tuning, the accumulated experiential structure of an adult cortex.

The claim is that the two layers have *fundamentally different compressibilities*. Principles can be written down — a few pages of code or a small set of biophysical and developmental rules. Parameters are heavy-tailed, idiosyncratic, and shaped by an incompressible world; they cannot be compressed into a short formal language without sacrificing the very task performance that motivates them.

## The compressibility argument

The motivating contrast is two games. **Tic-tac-toe** has 255,168 possible games and admits a three-rule policy that achieves unbeatable play; the rule set is fully informative and the policy is communicable. **Go** has > 10¹⁰⁴⁸ games and admits no known compact valuation; neural networks that play it at superhuman level have hundreds of millions of weights and resist explanation. The rules of Go behavior are heavy-tailed: any short list of rules captures little of the relevant policy structure, and lossy compressions sacrifice task performance.

Human-level performance across many domains lives at the Go end of this axis. Adults know thousands of object categories with megabytes of incompressible knowledge per category (the canonical example: balloons are made of rubber or aluminum foil, often held by kids or clowns, are red in a famous song); humans hold ~1.5 MB of information from language acquisition (Mollica & Piantadosi 2019). Most of this information comes from the world, which is itself incompressible — and a competent agent's parameters must reflect that incompressibility.

The principles, by contrast, can be bounded. The genome is upper-bounded at ~6 × 10⁹ bits, mostly non-coding and redundant; only ~20k coding genes exist, most not specifically brain-related. Whatever the biological recipe is, it fits into this budget. The principles/parameters split is therefore not symmetric — the principles are bounded by a small information budget, the parameters by the world.

## Relation to Marr's levels

The split adjusts [[marrs-levels-of-analysis|Marr's framework]] for systems that absorb the world's incompressibility. Standard Marr treats the algorithmic level as an autonomous object of explanation. Under principles-vs-parameters, the algorithmic level for a trained system *is* the parameter set together with the architecture that operates on it; it is not separately summarizable in a short formal language. What can be communicated is:

1. **Computational level** — the problem the system solves (the loss function, the objective).
2. **Implementational level** — the substrate (cell types, connectivity motifs, biophysics; or transistors and gates).
3. **Recipe** — the principles that convert (1) running on (2) into a competent algorithm: architecture, learning rule, developmental program.

The trained algorithm is then an *output* of the recipe, not a layer of explanation in its own right. This recasts the goal of neuroscience: not "specify the algorithm cortex implements" but "specify the principles that build cortex's algorithms, given a particular environment."

## Methodological prescriptions

The frame reorganizes standard neuroscience programs:

- **Connectomics** — focus on large-scale anatomy and [[circuit-behavior-mapping|circuit motifs]] (likely genetically specified, hence part of the principles) rather than which-exact-neuron-connects-to-which-exact-neuron (likely learned, hence parameters).
- **Plasticity research** — central to the principles agenda. The dendritic credit-assignment lineage ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]] → [[guerguiev-2017-segregated-dendrites|Guerguiev 2017]] → [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] → [[payeur-2020-burst-dependent-credit-assignment|Payeur 2020]] → [[greedy-2022-single-phase-burstccn|Greedy 2022]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) is exactly the kind of research the frame advocates: the contribution is the learning rule, not any particular trained representation.
- **Optogenetics / perturbation** — target signals that *carry* learning (reward prediction errors, third-factor signals, dendritic plateau potentials) rather than signals that *implement* current computation.
- **Behavior** — ask how learning *changes* action selection, not which actions are produced now.
- **Representations** — treat measured representations as fingerprints of the underlying recipe (loss function + architecture + learning rule), not as objects of explanation in themselves.
- **Molecular** — focus on cascades that *set up* plasticity ([[creb|CREB]], synaptic-tagging machinery; see [[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]]) rather than cascades that implement moment-to-moment computation.

## Why the statistical-physics analogy fails for parameters

A common rejoinder is that statistical mechanics gives compact mid-level descriptions of microscopically incompressible systems — temperature and pressure summarize 10²³ atoms — so by analogy a mid-level description should exist for the brain. Lillicrap & Kording argue the analogy fails for the regimes neuroscience cares about: gas atoms are exchangeable and effectively memoryless, while cortical cells are unique (each with its own developmental trajectory and plasticity history) and have memory going back to the birth of the animal. A compact mid-level description requires homogeneity that statistical mechanics gets for free and brains do not have.

More fundamentally, a mid-level model that *worked* across the regimes of human behavior would have to be as compressible as the behaviors it explains. For domains where the world is genuinely simple (the cerebellar vestibulo-ocular reflex), lossy mid-level models are reasonable. For vision, language, planning, or sensorimotor flexibility, they are not.

## Relation to the wiki's organizing thesis

The principles/parameters split is the information-theoretic complement of the wiki's [[degeneracy|control-theoretic genes hypothesis]]: genes encode behavior not by specifying microscopic circuits but by modifying neurons' nonlinear feedback control algorithms, producing conserved macroscopic dynamical structures (limit-cycle attractors for locomotion, etc.) with high probability despite unique microscopic configurations. The macroscopic dynamical structure *is* the principle; the microscopic configuration *is* the parameter.

For closed-loop sensorimotor control, this means the appropriate target of explanation is *the controller-building recipe* — how a genome plus a developmental environment plus an organism's interactions with the world yields a competent controller — not the specific synaptic state the recipe produces in any individual brain. The wiki's progression from immediate reactive control to longer-horizon planning and abstraction is then a progression in *what kinds of recipes get built*, not a progression in what kinds of algorithms run on top of fixed substrates.

## Relation to other methodological positions

- **[[paradigm-pluralism-comp-neuro|Paradigm pluralism]]** ([[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT 2026]]): the wider Kuhnian reading positions principles-vs-parameters as a paradigm-level commitment about *what neuroscience can communicate* (the recipe, not the trained parameters), among several rival commitments. Lillicrap-Kording's frame is one substantive answer to the "what counts as understanding?" question; the Kuhnian view says different paradigms (biophysical-realism, predictive-accuracy, normative-optimality, behavioral-fit) give incompatible answers because their standards differ.
- **[[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]**: the negative version of the same argument. Standard neuroscience methods on the MOS 6502 do not recover [[marrs-levels-of-analysis|Marr-level]] understanding even with full ground truth; the parameters resist analysis even when known. Principles-vs-parameters provides the constructive interpretation: of course the parameters resist analysis — they should — but the chip's principles (instruction set, decoder, ALU design) *are* communicable, and the analogous neural recipe is what to target.
- **[[brette-2018-coding-metaphor|Brette (2018)]]**: critiques the [[neural-coding|coding metaphor]] that interprets neural data as encoder/decoder chains. Compatible with principles-vs-parameters — both push toward dynamical / mechanistic / sensorimotor framings — but Brette's critique is at the level of how to interpret what we measure, while Lillicrap-Kording is at the level of what to target measuring. Together they recommend: stop interpreting parameters as codes, start targeting the principles that produce them.
- **[[free-energy-principle|FEP]] and [[predictive-coding|predictive coding]]**: principles-level theories — they specify computational-level objectives and implementational architectures, leaving the trained generative model as a parameter that emerges from running the principles on the world. The dark-room / constraint-discovery problems are exactly the parameters questions the frame predicts will be hard.
- **[[computation-through-dynamics|Computation Through Dynamics]]**: the principles-vs-parameters frame is in tension with the strongest reading of CTD — that low-dimensional dynamics *are* the explanation. CTD's defense is the trained-RNN sufficiency proof: if a randomly-initialized network trained on the same task develops the same dynamics, the dynamics are a property of the recipe (architecture + loss + training data), not of any particular trained instantiation. The sufficiency move is what makes CTD compatible with the frame.

## Caveats

The frame should not be read as claiming parameters are uninteresting. Particular questions about particular parameters — where does *this* place cell come from, how does *this* attractor form — remain valuable. The claim is that parameters are not communicable in a short formal language, not that they are unworth studying. Lossy mid-level descriptions for narrow domains can also be reasonable goals.

Nor does the frame claim mid-level descriptions are *impossible*. History contains examples of "impossible" reductions that succeeded; brains may have features (modularity, approximate linearity, high noise) that make them more compressible than ImageNet classifiers; superhuman analyzers might find reductions humans cannot. The claim is that the default expectation should be compressed-recipe, incompressible-parameters, and that experimental and theoretical effort should be allocated accordingly.

## Sources

- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — articulates the principles/parameters decomposition; argues from compressibility that mid-level descriptions of trained systems performing across the world's full complexity should not be expected to exist; reorganizes neuroscience programs around the principles layer.
- [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT (2026)]] — locates principles-vs-parameters within a broader [[paradigm-pluralism-comp-neuro|Kuhnian-pluralist]] reading of comp neuro; treats it as one paradigm-level position on "what counts as understanding" among several with different evaluative standards.
