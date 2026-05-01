# Overview

This page is the wiki's argument — what it currently claims, where the claims rest, and where they are under tension. It is *not* a catalog of pages; that lives in [[index|index.md]]. It is *not* an exhaustive bibliography; the per-pillar evidence ledger does that work in [[control-thesis-ledger|wiki/analyses/control-thesis-ledger.md]].

The intent: keep this page short enough to read end-to-end, organized so the thesis is visible as a structure of testable pillars rather than a collection of source-by-source endorsements. The lineage walkthroughs that used to live here have been extracted to [[credit-assignment-lineage|credit-assignment lineage]], [[e-i-regimes|E-I regimes lineage]], and [[inference-lineage|inference lineage]]. Active resistance to the thesis lives at [[challenges-to-control-thesis|challenges to the control thesis]].

---

## The working thesis

**The most biologically grounded route to understanding intelligence begins with closed-loop sensorimotor control.** Memory, learning, and cognition are extensions of that control over longer timescales, more latent variables, and more counterfactual worlds — not separate faculties.

**Working hypothesis on the evolutionary dimension.** Genes encode behavior not by specifying circuits directly but by constraining the nonlinear feedback-control algorithms that single neurons implement, producing microscopic [[Degeneracy|degeneracy]] with conserved macroscopic dynamical structures. This is a control-theoretic reading of degeneracy.

The thesis is a **lens, not an axiom**. The wiki is maintained to test and refine it. Sources that resist the thesis are as valuable as those that support it; the [[control-thesis-ledger|ledger]] has a mandatory resist column on every pillar.

Foundational triangulation: [[brette-2018-coding-metaphor|Brette (2018)]] for the philosophical articulation of closed-loop framing as corrective to the coding metaphor; [[bennett-2023-history-intelligence-intro|Bennett (2023)]] for evolutionary decomposition methodology; [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] for the empirical anchor of microscopic-degeneracy / macroscopic-conservation.

---

## The pillars

The thesis decomposes into six sub-claims. Each pillar has a status, primary evidence, primary resistance, and a falsifier in the [[control-thesis-ledger|ledger]].

### P1 — Closed-loop sensorimotor coupling is the developmental substrate from which higher cognition extends.

*Status: emerging — under-tested.* The strongest evidence is comparative ([[bennett-2023-history-intelligence-intro|Bennett 2023]] for the methodology; [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang 2024]] for chemotaxis-as-substrate-for-cognitive-navigation; [[banerjee-2023-life-stage-chemosensation|Banerjee 2023]] for life-stage circuit reconfiguration). The pillar is genuinely under-tested against embodiment-agnostic alternatives; large language models and dark-rearing literature are the wanted ingests that would either sharpen or weaken it.

### P2 — Memory and learning extend control over time, latents, and counterfactuals.

*Status: emerging — partially supported.* [[wierzynski-2009-sleep-hpc-pfc|Wierzynski 2009]] (replay-driven HPC→PFC consolidation) and [[rosenberg-2021-labyrinth-learning|Rosenberg 2021]] (one-shot home-path learning) shape memory in ways consistent with control extension. [[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]] is the sharpest complication: memory primitives exist in non-neural cells that have no behavior to control. The wiki's working reconciliation (cellular kinetics are inherited primitives put to use in the loop) is plausible but is not forced by the data.

### P3 — Genes constrain dynamics, not circuits.

*Status: emerging — analytical scaffold strong, biology thin.* The [[e-i-regimes|E-I regimes lineage]] (Wilson-Cowan → SCS → Brunel) supplies the analytical substrate: a single network expresses many dynamical regimes selectable by mesoscopic parameters. [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt 2019]] is the most direct biological anchor (macroscopic dynamics conserved across individuals despite microscopic neuron variability). The pillar is under-tested at the level of specific gene→dynamic-regime causal links; epigenetics and trans-generational inheritance are unrepresented in the wiki and would discriminate.

### P4 — Inference is one side of the control loop.

*Status: contested — selection from the lineage, not a derivation.* The [[inference-lineage|inference lineage]] (Jaynes → Helmholtz machine → Rao-Ballard → Friston) supplies a variational scaffold but does not entail closed-loop control. [[rao-ballard-1999-predictive-coding|Rao-Ballard 1999]] specifically shows that perceptual inference works without action. Only [[friston-2010-free-energy-principle|Friston 2010]] adds action as a third minimizer of `F` — and this is Friston's distinctive move, not entailed by the variational scaffold. The wiki's read of P4 is a *strong choice* among readings, not a derivation. P4 is the pillar most at risk of being top-down framing.

### P5 — Credit assignment operates within the loop, local to the substrate.

*Status: well-supported (mechanism); the control framing is partly retrofit.* The [[credit-assignment-lineage|credit-assignment lineage]] (Kording-König 2001 → Guerguiev 2017 → Sacramento 2018 → Payeur 2020 → Greedy 2022 → Francioni 2026) is the wiki's cleanest mechanistic program. Compartmentalized dendritic credit, burst-multiplexed STP, and inhibitory linearization implement a backprop-approximation in spiking networks at competitive depth and accuracy, with first in vivo confirmation in [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]. The control gloss (homeostatic baseline as servo equilibrium) is explicit in two of the six papers, retrofit in the other four.

### P6 — Population dynamics implement control; single-neuron biophysics constrains the substrate.

*Status: emerging — strong correlative evidence, weak causal evidence.* [[vyas-2020-computation-through-dynamics|Vyas 2020]] codifies motor-cortex motifs (preparatory ICs, output-null preparation, rotational dynamics, manifold-constrained learning); [[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]] gives the constructive existence proof (controlled dynamics carved from a chaotic substrate). [[brette-2018-coding-metaphor|Brette 2018]] is the strongest single resist entry: population dynamics "implementing control" inherits the symbol-grounding problem if read representationally. The wiki has not resolved how strongly to commit to representational language; this is a load-bearing assumption.

---

## Active tensions

The wiki has internal disagreements — mostly carried by the ingest sources rather than imposed by the wiki's framing. Calling them out keeps them visible.

- **Rate vs. timing as the primary code.** [[brunel-1999-sparsely-connected-networks|Brunel]] and the rate-modeling tradition vs. spike-timing accounts (phase precession, burst codes). Cuts across P5 and P6.
- **Credit assignment as backprop-approximation vs. genuinely local rule.** [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] proves analytical equivalence under weak feedback; [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]] finds error *derivatives* not magnitudes (favoring target propagation). Mechanism is supported; specific implementational details disagree across the lineage.
- **Predictive coding as inference primitive vs. control's other side.** P4's contested status; [[rao-ballard-1999-predictive-coding|Rao-Ballard]] vs. [[friston-2010-free-energy-principle|Friston]] readings.
- **Memory as substrate-general vs. synaptic-specific.** [[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]] vs. the neural-circuit memory literature. Cuts directly at P2.
- **Population dynamics as faithful summary vs. coding-metaphor inheritor.** [[brette-2018-coding-metaphor|Brette 2018]] vs. the [[computation-through-dynamics|CTD]] / manifold tradition.
- **Methodological: can analyses recover algorithmic understanding at all?** [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]] and [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]] urge methodological humility across all pillars.
- **Meta: is the thesis a paradigm commitment or field consensus?** [[chatgpt-2026-comp-neuro-kuhnian-review|the Kuhnian review]] and [[paradigm-pluralism-comp-neuro|paradigm pluralism]] suggest the former. The wiki should be read as one paradigm-style commitment among several, not as a settled view.

---

## What's missing

Curation gaps that bear directly on the thesis. Listed in the [[control-thesis-ledger|ledger]] under wanted ingests; flagged here because each is load-bearing.

- **Embodiment-agnostic AI** (LLMs, transformer cognition without sensorimotor loops). Tests P1 directly. Currently the wiki's largest gap.
- **Dark-rearing / sensory-deprivation visual development.** Tests whether closed-loop coupling is *required* for representational development.
- **Mirror neurons, social learning, imitation.** Stress-tests P1 by introducing a non-individual sensorimotor source.
- **Epigenetics, trans-generational inheritance.** Stress-tests P3's gene→dynamics claim.
- **Symbolic / compositional generalization (language).** Tests whether P2's "extension of control" framing accommodates productive compositionality.
- **Pure perceptual prediction without motor coupling.** Tests P4's "inference as control's other side."
- **Causal manipulations of manifold structure.** Tests P6's implementational claim.
- **Bayesian-brain / pure predictive-processing literature as a rival framework.** Tests the thesis as a whole.

---

## How to read this wiki

- **Catalog of what exists**: [[index|index.md]].
- **Per-pillar evidence and falsifiers**: [[control-thesis-ledger|wiki/analyses/control-thesis-ledger.md]].
- **Sustained engagement with rivals**: [[challenges-to-control-thesis|wiki/analyses/challenges-to-control-thesis.md]].
- **Open questions**: [[open-questions]].
- **Lineage walkthroughs**: [[credit-assignment-lineage]], [[e-i-regimes]], [[inference-lineage]].
- **Single-neuron ↔ population synthesis**: [[unified-picture-single-neuron-population-control]].
- **Activity log**: [[log]].

A good way to read the wiki critically: pick a pillar from the ledger, read its support and resist columns, then read the falsifier and ask *would I notice this falsifier in current data?* If the answer is no, the pillar is under-tested.
