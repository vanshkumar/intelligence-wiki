---
title: "What Does It Mean to Understand a Neural Network?"
type: source
source_type: paper
authors:
  - "Timothy P. Lillicrap"
  - "Konrad P. Kording"
year: 2019
doi: "10.48550/arXiv.1907.06374"
tags: [philosophy-of-neuroscience, what-is-understanding, compressibility, learning-rules, architecture, plasticity, methods-critique, marr-levels, nature-vs-nurture]
date_ingested: 2026-04-30
key_finding: "Trained neural networks are easier to understand at the level of the code that built them (architecture, loss function, learning rule) than at the level of the weights they end up with — and by analogy, neuroscience should focus on principles (anatomy, plasticity rules, development) rather than the trained parameters they produce, because human-level performance is unlikely to be compressible into a communicable mid-level model."
---

## Overview

Lillicrap & Kording (2019) is a six-page methodological essay that takes the [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] critique — that standard neuroscience methods do not recover [[marrs-levels-of-analysis|Marr-level]] understanding even with full ground truth — and supplies a constructive program: focus on the *principles* (architecture, loss function, learning rule, anatomy, plasticity) that generate a system rather than on the *parameters* (trained weights, connection strengths, representations) that embody its accumulated knowledge.

The argument turns on **compressibility**. A few hundred lines of PyTorch suffice to specify the recipe that builds AlexNet or AlphaGo; after training, the same systems are characterized by tens of millions of weights that no one — including the people who wrote the code — feels they understand. The asymmetry is not contingent. It reflects a structural fact about complex domains: the world contains incompressible knowledge (what balloons are, how sentences mean, what positions in Go are good), and any system performing well across such a world must embody that incompressibility in its parameters. The recipe stays compressible because the recipe specifies the *capacity to absorb* the world, not the world itself.

By analogy, the brain's parameters — synapse-by-synapse connection strengths, individual cell tuning, the millions of distinctions that adult humans encode about their world — are likely incompressible and probably uncommunicable in any short formal language. What *is* potentially compressible is the recipe biology uses to build a brain: the genome (upper-bounded at ~6 × 10⁹ bits, mostly non-coding, only ~20k coding genes), the developmental architecture, the cellular biophysics, and the plasticity rules. The paper's prescriptive payload: neuroscience should organize itself around the nature/nurture decomposition that machine learning practitioners use in practice — communicate the principles, hand the parameters off to the world.

[PDF](../../raw/papers/lillicrap-kording-2019.pdf)

## Key Findings

### The compressibility argument

The paper introduces compressibility through games. Tic-tac-toe has 255,168 possible games but admits a three-rule policy that achieves unbeatable play. Go has > 10¹⁰⁴⁸ games and admits no known compact valuation function — neural networks that play Go at superhuman level have hundreds of millions of weights and resist explanation by the humans who trained them. The rules of Go behavior are *heavy-tailed*: any short list of rules captures little of the relevant policy structure, and lossy compressions tend to sacrifice the very behavior that motivates the system.

Human-level performance across many domains is at the Go end of this axis, not the tic-tac-toe end. Adults know about thousands of object categories with megabytes of incompressible per-category knowledge (the balloon example: rubber/aluminum, kids/clowns, red in a famous song); humans hold ~1.5 MB of language-acquisition information (Mollica & Piantadosi 2019). The bulk of this information comes from the world, which is itself incompressible. The conclusion: there should be no compact mid-level description of a system that performs at human level across many domains, because the world such a system models is itself incompressible.

The paper situates this against ML distillation results: ImageNet classifiers can be compressed to ~100k parameters but not below in any human-readable way (Han et al. 2015; Hinton et al. 2015; Frosst & Hinton 2017; Zhou et al. 2018). The compressed networks remain opaque — *small* is not the same as *understandable*. Even MNIST networks, which solve a near-trivial task, do not admit a human-readable description after training.

### What understanding-by-current-methods misses

Lillicrap & Kording catalog the techniques deep learning practitioners use to look at trained networks: activation/derivative histograms (used mostly to diagnose vanishing/exploding gradients during training), sensitivity analysis, adversarial-example probing, feature visualization, unit ablation. None of these, the authors argue, would let a practitioner tell a useful story about how AlexNet, AlphaGo, or GPT2 actually decides anything. The methods diagnose engineering pathologies during construction; they do not deliver the kind of mid-level description that would let someone improve task performance through targeted intervention.

This is the deep-learning analogue of the [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]] result. There, standard neuroscience methods on the MOS 6502 (a system whose Marr-level structure we already know) recovered cell-type clusters, lesion-specific behavioral deficits, tuning curves, weak-pairwise / strong-global correlations, 1/f LFP spectra, and dimension-reduced latent components correlated with internal signals — all without recovering the chip's computational hierarchy. Here, deep-learning analysis methods on trained networks (a system whose code we wrote) recover diagnostic statistics without delivering the algorithmic-level account practitioners would actually use.

### Why the statistical-physics analogy fails

A common neuroscience hope is that a *mid-level* compact description should exist for the brain by analogy with statistical mechanics: the microscopic state of a gas is incommunicable (10²³ atoms in high-dimensional phase space) but the macroscopic state is captured by temperature, pressure, and a few thermodynamic variables. The hope is that some equivalent macroscopic description — a few latent variables, a low-dimensional dynamical system — could capture cortical computation.

Lillicrap & Kording argue this analogy fails for the regimes where neuroscience most wants it to work. Gas atoms are exchangeable and have effectively no memory; cells in the brain are unique (each with its own developmental trajectory, plasticity history, and connectivity context) and have memory that effectively goes back to the birth of the animal. A compact mid-level description requires the kind of homogeneity that statistical mechanics gets for free and brains do not have.

More fundamentally, the world the brain models is itself incompressible. A mid-level model that *worked* across the regimes of human behavior would have to be as compressible as the behaviors it explains — and the compressibility argument says those behaviors are not compressible. *Lossy* mid-level models for narrow domains (the cerebellar vestibulo-ocular reflex, where the world is simple) are reasonable to expect; mid-level models that work for vision, language, or planning are not.

### The principles/parameters decomposition

The paper's positive proposal is the same decomposition deep-learning papers tacitly use: communicate the *principles* (architecture, loss function, learning rule, optimization procedure, training data sources) and accept that the *parameters* (the weights that result from running the recipe on the world) cannot be communicated in any meaningful sense, only computed.

For neuroscience this maps onto:

- **Architecture** ↔ anatomy, large-scale connectivity, [[circuit-behavior-mapping|circuit motifs]], cell-type repertoire
- **Learning rule** ↔ synaptic plasticity rules ([[hebbian-learning|Hebbian]], STDP, three-factor, [[credit-assignment|credit-assignment]] mechanisms)
- **Loss function** ↔ behavioral objectives (homeostasis, reward, [[free-energy-principle|free energy]], [[predictive-coding|prediction error]])
- **Training data** ↔ the organism's lifetime of sensorimotor experience, which is what makes individual brains parametrically unique and parametrically uncommunicable

The paper notes that the genome upper-bounds the principles at ~6 × 10⁹ bits, mostly non-coding and redundant; only ~20k genes code anything, and most do not code information specifically for brains. This is sufficient to specify learning rules, architectures, and developmental programs but vastly insufficient to specify the trained synaptic state. The "nature" component is bounded; the "nurture" component is unbounded.

### Methodological prescription for neuroscience

The paper closes with a re-orientation of standard neuroscience programs around principles rather than parameters:

- **Behavior**: ask how learning *changes* action selection, not which actions are produced now.
- **Representation analysis**: ask which loss function, architecture, and learning rule would produce the measured representations — treat the representation as a fingerprint of the recipe, not an object of explanation in itself.
- **Connectomics**: focus on large-scale anatomy and circuit motifs (likely genetically specified) rather than individual neuron-to-neuron wiring (likely learned and idiosyncratic).
- **Optogenetics / perturbation**: target the signals that *carry* learning (reward prediction errors, third-factor signals, dendritic plateau potentials) rather than the signals that *implement* current computation.
- **Molecular**: focus on cascades that set up plasticity rather than cascades that implement moment-to-moment computation.

The paper's slogan: instead of asking *how the brain works*, ask *how the brain learns to work*.

## Methods

This is an essay, not an empirical paper. The argument proceeds by analogy and by literature review:

- **Compressibility**: tic-tac-toe vs. Go as illustrative endpoints; ImageNet/MNIST distillation literature (Han, Hinton, Frosst & Hinton, Zhou et al.) for empirical bounds on neural-network compression; estimates of human conceptual knowledge (Biederman 1987 for object categories; Mollica & Piantadosi 2019 for language).
- **Methods of understanding**: catalog of diagnostic techniques (activation histograms, sensitivity analysis, adversarial examples, feature visualization, unit ablation) and an argument that none deliver mid-level understanding.
- **Statistical-physics analogy and its breakdown**: by analogy with quantum mechanics → statistical mechanics; the disanalogy is cells-are-unique-and-have-long-memory.
- **Genome-bound argument**: ~6 × 10⁹ bits as an upper bound on the "nature" component, mostly non-coding, ~20k coding genes.

## Implications

### Direct alignment with the wiki's organizing thesis

The paper's principles/parameters decomposition is essentially a re-statement of this wiki's [[degeneracy|control-theoretic genes hypothesis]]: genes encode behavior not by specifying circuits directly but by modifying neurons' nonlinear feedback control algorithms, producing conserved macroscopic dynamical structures (limit-cycle attractors for locomotion, etc.) with high probability despite unique microscopic configurations. Lillicrap & Kording supply a complementary information-theoretic argument: the genome is compressible, the trained brain is not, and the genome's role is to specify the recipe that converts incompressible world into incompressible brain. The wiki's case for "intelligence begins with closed-loop sensorimotor control" gains a methodological partner: not only is sensorimotor control the substantive primitive, the principles that build sensorimotor controllers are also the appropriate target of neuroscientific explanation.

### Re-reading existing wiki sources

- **The dendritic credit-assignment lineage** ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]] → [[guerguiev-2017-segregated-dendrites|Guerguiev 2017]] → [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] → [[payeur-2020-burst-dependent-credit-assignment|Payeur 2020]] → [[greedy-2022-single-phase-burstccn|Greedy 2022]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) is exactly the kind of "principles" research the paper advocates: it studies the learning rule, not the trained representation. The paper provides the abstract justification for why this lineage is the right kind of neuroscience.
- **[[force-learning|FORCE learning]]** ([[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]]) likewise: the contribution is the learning rule and architecture (three FORCE variants for three plasticity-division-of-labor hypotheses), not particular trained networks.
- **The cellular cognition thread** ([[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]]): isolating the temporal-pattern-decoding kinetics of CREB-driven consolidation in non-neural human cells is principles-style research — the cascade is the recipe, the resulting transcription is the parameter.
- **[[predictive-coding|Predictive coding]] and [[free-energy-principle|FEP]]**: computational-level proposals that specify the *objective* (the loss function in Lillicrap-Kording's terms) rather than the trained generative model. Compatible with the paper's program insofar as they're principles-level, but the dark-room / constraint-discovery problems flagged in the wiki are exactly the *parameters* questions the paper says we should expect to be hard.

### Sharpening Marr's levels for trained systems

Lillicrap & Kording effectively argue that for systems that absorb the world's incompressibility, the *algorithmic level* of [[marrs-levels-of-analysis|Marr's framework]] cannot be communicated in a short formal language — it is the trained weights, and those weights resist any compression that preserves task performance. What *can* be communicated is:

1. The **computational level** (what problem? what objective?)
2. The **implementational level** (what hardware? what architecture? what plasticity rules?)
3. The **recipe** that converts the implementational substrate plus environmental input into a competent algorithm.

The standard Marr framework treats the algorithmic level as an autonomous object of explanation; this paper argues it cannot be that for trained systems performing at human level. The algorithm is what you get when you run the recipe on the world; it is not summarizable independent of either.

### Companion to the Brette and Jonas-Kording critiques

Together, three papers form a methodological triple:

- [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]]: standard neuroscience methods do not recover Marr-level understanding even with full ground truth.
- [[brette-2018-coding-metaphor|Brette 2018]]: the [[neural-coding|neural coding metaphor]] that interprets standard neuroscience results is structurally incoherent — algorithms have discrete temporal structure, brains are continuous-time dynamical systems, codes carry information by reference and not by use.
- **Lillicrap & Kording 2019** (this paper): even *with* better methods and a coherent framework, mid-level descriptions of trained systems are unlikely to exist; the appropriate target is the recipe, not the trained parameters.

The first two are negative arguments (methods fail; framework is wrong); the third is constructive (here is what to do instead). Together they recommend: build ground-truth-anchored validation of methods (Jonas-Kording), reframe theory as continuous-time sensorimotor dynamics rather than encoder/decoder chains (Brette), and target the principles that build brains rather than the trained brains themselves (Lillicrap-Kording).

### What the paper does not claim

- It does not claim parameters are *useless* objects of study — the point is that parameters are not communicable in a short formal language, not that they are uninteresting. Particular questions about particular parameters (where does *this* place cell come from? how does *this* attractor form?) remain valuable.
- It does not claim mid-level descriptions are *impossible* — it notes that history is full of "impossible" things that turned out to be possible, that simpler systems (the vestibulo-ocular reflex) admit lossy mid-level models, and that real brains may have features (modularity, approximate linearity, high noise) that make them more compressible than artificial networks.
- It does not equate the brain with a neural network. Plasticity is the load-bearing similarity; biophysical, evolutionary, and architectural differences are real but do not blunt the compressibility argument.

## Connections to Existing Knowledge

- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]: direct predecessor by the same second author. Lillicrap-Kording 2019 is the constructive sequel — Jonas-Kording showed methods fail to recover Marr-level understanding; this paper says we should expect that and reorganizes the program around principles instead.
- [[marrs-levels-of-analysis|Marr's Levels of Analysis]]: the framework whose algorithmic level the paper argues is uncommunicable for trained systems. The paper effectively splits Marr's framework into a communicable computational + implementational + recipe layer and an incommunicable trained-algorithm layer.
- [[brette-2018-coding-metaphor|Brette (2018)]]: philosophical companion. Brette critiques the framework that interprets neuroscience results; Lillicrap-Kording argue about the form of explanation those results could take. Compatible — both push toward dynamical / mechanistic / sensorimotor framings rather than encoder/decoder framings, and toward principles-level explanation.
- [[degeneracy|Degeneracy]]: the wiki's control-theoretic reading of degeneracy — genes specify principles (learning rules, dynamics, architecture), not microscopic circuits — is the biological correlate of Lillicrap-Kording's information-theoretic argument that the genome bounds the "nature" component.
- [[credit-assignment|Credit Assignment]]: the central problem of "how does the brain implement its learning rule" is exactly the principles-level research the paper advocates. The dendritic-credit-assignment lineage is the worked example.
- [[computation-through-dynamics|Computation Through Dynamics]]: the paper's compressibility argument tempers the strongest reading of CTD — that low-dimensional dynamical descriptions *are* the explanation. Under Lillicrap-Kording, low-dimensional dynamics are at best a lossy mid-level description that may work in narrow domains (motor control) but is unlikely to generalize to the cognitive regimes where the world is incompressible. Aligns with Jonas-Kording's NMF-on-the-chip caveat: dim-reduced components correlated with task variables are necessary but not sufficient.
- [[hebbian-learning|Hebbian Learning]] and [[force-learning|FORCE Learning]]: principles-level research programs. The paper's prescription endorses these as the appropriate target of explanation; their content is the recipe, not the trained network.
- [[konrad-kording|Konrad Kording]]: this is Kording's fourth paper in the wiki and the constructive bookend to his 2017 methodological critique. The methodology/philosophy thread now has a positive program.
- [[timothy-lillicrap|Timothy Lillicrap]]: bridges Lillicrap's feedback-alignment / dendritic-credit-assignment work (where his concrete contribution is precisely the kind of "learning rule as principle" research the paper advocates) with the methodological framing.

## Open Questions Raised

- **What is the appropriate compressibility benchmark for the brain?** The paper places the brain on a continuum between tic-tac-toe and Go but does not estimate where. Empirical work on the compressibility of trained ANNs (distillation) gives lower bounds for visual recognition (~100k parameters); is there an analogue for neural data?
- **Are there features that make brains more compressible than ANNs?** The paper flags strong modularity, approximate linearity, and high noise as candidate compressibility-helping features. Each is a research question on its own — how modular is cortex really, how much linear-approximation territory exists, and does noise compress the effective state space?
- **Can superhuman analyzers (future AI) understand systems humans cannot?** A speculative possibility the paper raises. If yes, the bound on understanding is on the analyzer, not on the system; if no, the bound is intrinsic.
- **What is the genome's actual information content for brain construction?** ~6 × 10⁹ bits is a permissive upper bound; tighter estimates would constrain how compressible the principles can be. Most coding genes are not brain-specific; non-coding regions may carry substantial regulatory information not yet quantified.
- **For [[computation-through-dynamics|CTD]]**: how much of explanatory weight rests on the recovered low-dimensional dynamics being a faithful summary, vs. on the trained-RNN sufficiency proof? Lillicrap-Kording's argument pushes toward sufficiency being load-bearing, in line with the [[jonas-2017-microprocessor-critique|Jonas-Kording 2017]] NMF caveat.
- **For [[predictive-coding|predictive coding]] / [[free-energy-principle|FEP]]**: is the constraint-discovery problem (which sufficient statistics get registered over evolutionary and developmental time) the principles question that connects FEP to the paper's program? The wiki's [[maximum-entropy-principle|MaxEnt]] reading suggests yes — the answer to "what should the brain do?" is settled at the computational level, but "what does it actually compute?" depends on the constraints, which are part of the recipe.
- **What does "fix the brain" look like under principles-only understanding?** Memory and sensory neuroprosthetics gesture at one operationalization; the paper's framing predicts they should focus on substituting principles (architecture, plasticity dynamics) rather than reproducing parameters.

## Sources

- Lillicrap, T. P. & Kording, K. P. (2019). What does it mean to understand a neural network? *arXiv preprint* arXiv:1907.06374. [PDF](../../raw/papers/lillicrap-kording-2019.pdf).
- Jonas, E. & Kording, K. P. (2017). Could a neuroscientist understand a microprocessor? *PLoS Computational Biology* 13(1):e1005268.
- Han, S., Mao, H. & Dally, W. J. (2015). Deep compression. *arXiv*:1510.00149.
- Hinton, G., Vinyals, O. & Dean, J. (2015). Distilling the knowledge in a neural network. *arXiv*:1503.02531.
- Mollica, F. & Piantadosi, S. T. (2019). Humans store about 1.5 megabytes of information during language acquisition. *Royal Society Open Science* 6(3):181393.
- Biederman, I. (1987). Recognition-by-components. *Psychological Review* 94(2):115.
