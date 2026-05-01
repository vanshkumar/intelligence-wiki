---
title: "Control Thesis Ledger"
type: exploration
tags: [meta, thesis, control, falsifiability]
date_created: 2026-05-01
prompted_by: "wiki cleanup; need a discipline scaffold to keep the organizing thesis testable rather than self-confirming"
---

The wiki's organizing thesis, decomposed into pillars, with supporting and resisting evidence per pillar, status, and would-be falsifiers. Updated on every ingest.

This page exists because a thesis with only supporting evidence is not a thesis — it is a brand. A pillar with no entries in the *resist / complicate* column is a red flag, not a victory. If a pillar has only support entries, the next ingest should look harder.

For sustained engagement with rival frameworks (as opposed to per-pillar bookkeeping), see [[challenges-to-control-thesis|challenges to the control thesis]].

---

## The claim

**The most biologically grounded route to understanding intelligence begins with closed-loop sensorimotor control.** Memory, learning, and cognition extend control over longer timescales, more latent variables, and more counterfactual worlds — they are not separate faculties.

**Working hypothesis on the evolutionary dimension.** Genes encode behavior not by specifying circuits directly but by constraining the nonlinear feedback-control algorithms that single neurons implement, producing microscopic [[Degeneracy|degeneracy]] with conserved macroscopic dynamical structures (e.g. limit-cycle attractors for locomotion).

Foundational triangulation: [[brette-2018-coding-metaphor|Brette (2018)]] (the philosophical articulation of closed-loop framing as a corrective to the coding metaphor); [[bennett-2023-history-intelligence-intro|Bennett (2023)]] (evolutionary decomposition methodology); [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] (the empirical anchor for microscopic-degeneracy / macroscopic-conservation).

---

## The pillars

| | Pillar | Status |
|---|---|---|
| **P1** | Closed-loop sensorimotor coupling is the developmental substrate from which higher cognition extends. | **emerging — under-tested** |
| **P2** | Memory and learning are extensions of control over time, latents, counterfactuals. | **emerging — partially supported** |
| **P3** | Genes encode behavior by constraining nonlinear feedback dynamics, yielding microscopic degeneracy + conserved macroscopic structure. | **emerging — analytical scaffold strong, biology thin** |
| **P4** | Inference (predictive coding, FEP, Helmholtz lineage) is one *side* of the control loop, not a separate faculty. | **contested — selection from the lineage, not a derivation** |
| **P5** | Credit assignment operates within the loop via dendritic / burst / neuromodulatory mechanisms — local to the substrate. | **well-supported — but the control framing is partly retrofit** |
| **P6** | Population dynamics (CTD, manifolds, attractors) are the level at which control is implemented; single-neuron biophysics constrains the substrate. | **emerging — strong correlative evidence, weak causal evidence** |

---

## P1 — Closed-loop sensorimotor coupling as developmental substrate

**Support**

- [[bennett-2023-history-intelligence-intro|Bennett (2023)]] — evolutionary decomposition methodology grounds higher cognition in successive elaborations of sensorimotor control; "five breakthroughs" framework places closed-loop control at the foundation.
- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — same CO₂ cue, opposite valences across *C. elegans* life stages, with daf-2 / BAG-AIB gap-junction reconfiguration. The behavioral output is loop-shaped at the substrate level, not abstracted away.
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — endotaxis algorithm explicitly repurposes the ancient chemotaxis sensorimotor module for cognitive navigation. Strongest demonstration of "higher cognition extends from a sensorimotor primitive."
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — macroscopic dynamics in *C. elegans* predict future motor commands; the control loop is the level at which behavior is conserved.
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — overnight labyrinth exposes few-shot learning emerging from a small set of genetically-consistent local turning biases. Higher behaviors emerge from sensorimotor primitives plus learning.
- [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] — motor cortex framed as a closed-loop controller; preparatory activity, output-null preparation, manifold-constrained learning are all loop-flavored.

**Resist / complicate**

- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — human knowledge spans thousands of object categories with megabytes of incompressible per-category content (the "balloons" example). Hard to reduce to sensorimotor primitives; either the reduction is correct but unintuitive, or sensorimotor coupling is *not the only* substrate from which cognition extends.
- [[reinert-2021-pfc-categorization|Reinert et al. (2021)]] — category-selective neurons in mPFC emerge during learning, with flexible remapping during rule switches. The category structure is *internal abstraction*, not directly grounded in motor control. Possible reading: control thesis must accommodate internal-only categorical operations, or P1 needs softening.
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — methodologically: even with full ground truth on a controller-style system (a CPU running games), standard analyses don't recover Marr-algorithmic understanding. Implication: empirical claims that a brain region "implements" sensorimotor control may be unfalsifiable with current methods.
- [[brette-2018-coding-metaphor|Brette (2018)]] — paradoxical entry: Brette is the philosophical *articulator* of closed-loop framing, but his critique implies that any specific implementation claim faces the symbol-grounding problem. He supports the *frame*; he resists *triumphalist* readings of any particular paper.

**Falsifiers**

- A clean demonstration that high-level cognition (compositional language, mathematical reasoning) develops normally in an organism deprived of sensorimotor coupling during a critical period.
- Embodiment-agnostic AI systems (large language models trained only on text) achieving human-level performance on tasks the thesis predicts require sensorimotor grounding. *Status: this is happening; the wiki has not yet ingested LLM literature, but the absence is itself a tell.*
- Visual receptive-field development that proceeds normally in dark-reared / sensory-deprived animals — would weaken the requirement for *active* sensorimotor coupling.

**Wanted ingests**

- Dark-reared animal visual development literature
- Mirror neurons / social learning
- Embodiment-agnostic AI: LLMs, transformer cognition
- Feral child / extreme deprivation cases (with appropriate skepticism)

---

## P2 — Memory and learning as extensions of control

**Support**

- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — directional HPC→PFC spike timing during SWS, abolished during REM. Memory consolidation has a temporal-control structure (replay-driven) — fits "extending control over time."
- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — hippocampal theta as travelling wave implies *segment* (not point) spatial encoding. The substrate represents extended trajectories, not snapshots — the right shape for control over space.
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — one-shot home-path learning, sudden insight; learning that operates on the loop's reach, not on isolated stimulus-response pairs.
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — explicitly extends chemotaxis (immediate control) into cognitive navigation (control over latent goal locations).
- [[meister-2022-learning-fast-slow|Meister (2022)]] — 10⁴-fold variation in learning rates explained by sparse codes; learning rate as a property of representational structure that determines how fast control can extend.
- [[bennett-2023-history-intelligence-intro|Bennett (2023)]] — historical decomposition of memory systems as successive control elaborations.

**Resist / complicate**

- [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] — the [[spacing-effect|spacing effect]] reproduces in non-neural human cell lines via PKA / PKC / ERK / CREB cascade kinetics. Memory's molecular substrate **predates the nervous system** and operates in cells that do not control behavior. Hard reading: memory primitives are *not* an extension of control; they're an inheritance from cellular signaling, repurposed by neurons. Soft reading: the kinetics are pre-existing, but their *deployment* in service of behavior is what makes them memory-as-control.
- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — content-addressable memory as fixed-point attractors of an energy function. Memory framed as **stable retrieval**, not as control. The Hopfield framing is an alternative organizing metaphor; the wiki's control reading must accommodate it.
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — trained parameters are heavy-tailed and incompressible; the structure of memory may not be cleanly reducible to "extended control." The world being modeled is itself incompressible, and so is the memory of it.
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — hierarchical RSB describes ultrametric organization of memory states in disordered systems; memory framed as static energy-landscape geometry, not dynamic control.

**Falsifiers**

- A memory phenomenon that is rich, durable, and behaviorally consequential but cannot be operationalized as extending control over time / latents / counterfactuals.
- A demonstration that semantic memory is acquired without any associated control-extension benefit.

**Wanted ingests**

- Episodic memory beyond rodent navigation paradigms
- Semantic memory in disembodied systems
- Cellular cognition follow-ups (does the molecular substrate scale to neural circuits?)

---

## P3 — Genes constrain dynamics, not circuits

**Support — analytical scaffold**

- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — three regimes selectable by four coupling-strength inequalities; **Theorem 4** (limit-cycle ↔ hysteresis interconvertibility under bias) is the formal kernel of "same substrate, different regime by tuning."
- [[brunel-1999-sparsely-connected-networks|Brunel (1999/2000)]] — four spiking regimes (SR, AR, AI, SI) selectable by (g, ν_ext); regime navigation without rewiring.
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — sharp regime transition at gain gJ = 1; dynamical mean-field theory establishes the substrate for [[edge-of-chaos|edge of chaos]].
- See aggregator: [[e-i-regimes|E-I regimes lineage]].

**Support — biology**

- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — macroscopic dynamics conserved across *C. elegans* individuals despite microscopic neuron variability. **The wiki's most direct empirical anchor for P3.**
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — computational scaffolds shared between monkey PFC and a trained RNN despite different activity / strategy. Independent demonstration of degeneracy at the scaffold level.
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — genetically-consistent behavioral biases (turn statistics, exploration patterns) across mice. Behavior is conserved at the macroscopic level.
- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — same gene (*daf-2*) controls life-stage circuit reconfiguration. Genes acting through neuromodulatory state to switch dynamical regime.
- [[bennett-2023-history-intelligence-intro|Bennett (2023)]] — methodological argument that evolutionary continuity sits at the dynamical-regime level, not the circuit level.

**Resist / complicate**

- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — capacity α_c ≈ 0.138N requires *specific* symmetric Hebbian coupling. Generic random coupling does not give Hopfield-style memory. P3 in its strongest form ("genes constrain mesoscopic parameters; specific micro-coupling does not matter") is in tension with the fact that some computations require specific structured coupling.
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — RSB requires a specific coupling-distribution structure; the ultrametric attractor organization is not robust to arbitrary parameter changes. Constraints on dynamics are *more specific* than gross macroscopic-parameter setting.
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — same mesoscopic dynamical signatures (1/f spectra, lesion tuning, NMF dimensions) can come from radically different programs. Microscopic degeneracy with macroscopic similarity is real, but does it map to *behavioral* similarity? The microprocessor critique suggests "same dynamics, different behavior" is also possible — undermining the inference from conserved dynamics to conserved function.
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — the genome (~6×10⁹ bits) upper-bounds the principles. But the trained synaptic state — shaped by an incompressible world — is *itself* incompressible. P3 says genes specify the recipe; Lillicrap-Kording agrees but emphasizes that recipe-level specification leaves enormous parameter degrees of freedom that the wiki may be underestimating.
- [[brette-2018-coding-metaphor|Brette (2018)]] — closed-loop sensorimotor framing supports *that* genes specify dynamics rather than codes, but Brette's symbol-grounding critique cuts at any claim that we can read a stable "function" off conserved dynamics.

**Falsifiers**

- A behaviorally identical organism with grossly different macroscopic dynamics (rules out P3's strong reading).
- A behaviorally divergent pair of organisms with identical macroscopic dynamics at the relevant timescale (rules out the inference from conserved dynamics to conserved function).
- Direct demonstration that fine microscopic detail (specific synaptic weight values, identified-cell connectivity) is required for a conserved behavior — would push P3 toward a circuit-specifying view.

**Wanted ingests**

- Epigenetics; trans-generational behavioral inheritance
- Specific gene-knockout studies showing dynamic-regime shifts
- Cross-species comparative dynamics where behavior is matched but circuits differ
- *C. elegans* connectome-vs-dynamics studies

---

## P4 — Inference is one side of the control loop

**Support**

- [[friston-2010-free-energy-principle|Friston (2010)]] — active inference adds action as a third minimizer of variational free energy `F`. The unification of perception + learning + action under one objective is Friston's distinctive move and the strongest case for P4.
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — predictive coding and credit assignment unified in a dendritic microcircuit; perception-as-inference and action-as-learning share substrate.

**Resist / complicate**

- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — MaxEnt is agnostic about action. The variational scaffold of inference does not require a control loop. **The lineage's foundation does not entail P4.**
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — Helmholtz machine designed for *unsupervised learning*, no action loop. Perception-only inference is sufficient for representation learning.
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — V1 receptive fields and extra-classical effects recovered from a perception-only predictive-coding model. **Inference works without action; this is the strongest "resist" entry for P4.**
- [[brette-2018-coding-metaphor|Brette (2018)]] — the latent-variable generative-model framing inherits the symbol-grounding problem. Even Friston's active inference, on Brette's reading, presupposes an internal representation of external causes — a presupposition the closed-loop / sensorimotor-contingencies framing rejects.
- See aggregator: [[inference-lineage|inference lineage]].

**Falsifiers**

- A clean demonstration that biological perception genuinely requires action coupling (would *strengthen* P4); current evidence (Rao-Ballard) is the other way.
- A predictive-coding model of cortex that is *inconsistent* with closed-loop control. *Status: most existing models are consistent with both readings; the dispute is about which is primary.*

**Wanted ingests**

- Comparison: visual learning in dark-reared / motorically-restricted animals
- Pure perceptual prediction without motor coupling (e.g. passive sensory receptive-field development)
- Active inference in specifically embodied agents vs. passive predictive coding in stationary observers

---

## P5 — Credit assignment is local to the substrate

**Support — the lineage is unusually clean here**

See aggregator: [[credit-assignment-lineage|credit-assignment lineage]].

- [[kording-konig-2001-two-integration-sites|Kording & König (2001)]] — two-compartment conceptual seed.
- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] — first spiking implementation; feedback alignment emerges.
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — phase elimination via SST-mediated prediction error; predictive-coding / credit-assignment unification.
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — biophysical scaling to ImageNet.
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] — single-phase, depth-scalable Q–Y cancellation.
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] — first in vivo evidence; cell-specific SD residuals encode error derivatives; NDNF⁺ perturbation abolishes learning.
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — single-neuron dendritic trees solve complex classification tasks; the substrate has the computational headroom for compartment-local credit.

**Resist / complicate**

- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — the credit assignment *recipe* is compressible (good for P5); but the *parameters* it produces are incompressible (a methodological caution against treating "P5 is supported" as "we now understand cortical learning").
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — even with full ground truth on dendritic compartments, current analytical methods may not recover the algorithmic-level meaning. The lineage shows what's *possible*; whether real cortex *uses* this mechanism is harder to confirm than it looks.
- **Internal tensions** (see lineage page): error magnitude vs. derivative; SST⁺ vs. NDNF⁺ interneuron division of labor; full-silence vs. partial-cancellation baselines. The mechanism is supported; specific implementational details disagree across the six papers.

**Note on framing.** Two of the six lineage papers (Sacramento, Greedy) explicitly use control-flavored language for the homeostatic baseline. The other four do not. The wiki's reading of "credit assignment within the loop" is consistent with the lineage but partially retrofit. P5 is the wiki's best-supported pillar at the *mechanism* level; the *control* gloss is a slightly weaker claim.

**Falsifiers**

- Demonstration that cortical learning operates through a non-local mechanism (e.g. weight transport via volume transmission in a way not captured by burst-multiplexing).
- Direct evidence that pyramidal apical dendrites do not compute prediction errors during in vivo learning.

**Wanted ingests**

- Temporal credit assignment (delayed rewards) in biology
- Neuromodulator–dendrite interaction (dopamine / acetylcholine gating of burst rules)
- Feedback weight learning mechanisms

---

## P6 — Population dynamics implement control; single-neuron biophysics constrains the substrate

**Support**

- [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] — motor-cortex motifs (preparatory initial conditions, output-null preparation, rotational dynamics, line-attractor decisions, manifold-constrained BCI learning) — the wiki's strongest direct evidence.
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — FORCE learning constructively shows that controlled dynamics can be carved from a chaotic substrate. Existence proof for the CTD picture.
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — macroscopic dynamics predict motor commands across individuals.
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — LOOPER scaffolds shared between PFC and RNN.
- [[reinert-2021-pfc-categorization|Reinert et al. (2021)]] — population-level category dynamics emerge during learning, with rule-switch remapping.
- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — attractor framing of collective computation; foundational scaffold (with caveats — symmetric coupling required).
- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]], [[brunel-1999-sparsely-connected-networks|Brunel (1999)]], [[sompolinsky-1988-chaos-random-networks|SCS (1988)]] — see [[e-i-regimes|E-I regimes lineage]] for the analytical substrate.
- [[gerstner-neuronal-dynamics-ch1|Gerstner Ch. 1]], [[gerstner-neuronal-dynamics-ch2|Gerstner Ch. 2]] — single-neuron biophysics constrains what populations can do (HH ion channels, shunting inhibition, star topology).

**Resist / complicate**

- [[brette-2018-coding-metaphor|Brette (2018)]] — population coding inherits the symbol-grounding problem. Population dynamics "implementing control" presupposes that population activity *represents* control variables; Brette argues this presupposition is incoherent. The wiki's strongest single resist entry — and the closest the wiki comes to engaging its own framing skeptically.
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — the standard population-analysis toolkit (NMF, rotational dynamics, manifold reduction) applied to a fully understood controller does not recover its algorithmic structure. **The methodological caution applies directly to P6.**
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — energy-landscape framing only valid for symmetric coupling; the rugged-landscape attractor picture (which underwrites Hopfield-style P6 reasoning) does not extend cleanly to driven asymmetric networks.
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — population dynamics may be a useful summary at the *principles* level but not faithful at the *parameters* level. P6 is consistent with this caveat but should not be over-read.

**Falsifiers**

- Demonstration that motor / decision behavior generated *without* the postulated population-dynamical motifs (e.g. by manipulations that disrupt manifold structure but leave behavior intact).
- An organism whose behavior tracks circuit-level details that no manifold-level summary can capture.

**Wanted ingests**

- Causal manipulations of manifold structure (e.g. closed-loop perturbations that target the null space)
- Cross-area dynamics integration (PFC + motor + sensory in unified frame)
- Explicit comparisons between manifold-based and non-manifold models on the same data

---

## Meta-frame: methodological humility

Two ingested LLM-generated meta-surveys urge complementary frameworks beyond Kuhn for reading the field. They do not bear directly on any pillar but constrain how confident the wiki should be in any pillar's status:

- [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT (2026, Kuhnian review)]] — comp neuro is multi-paradigm, not in revolution. The wiki's control thesis is one paradigm-style commitment, not field consensus. See [[paradigm-pluralism-comp-neuro|paradigm pluralism]].
- [[chatgpt-2026-comp-neuro-kuhnian-historiography|ChatGPT (2026, historiography)]] — recommends Lakatos / Laudan / Galison / Hacking / Bourdieu lenses. See [[historiographic-frameworks-comp-neuro|historiographic frameworks]].

Implication for this ledger: pillar statuses are **provisional reads**, not settled assessments. A pillar at "well-supported" status could be read as "well-supported within the dynamical-systems / control paradigm community; less load-bearing in the connectomics or normative-Bayesian communities."

---

## Wanted ingests, consolidated

**To test P1 (sensorimotor coupling as substrate):**
- Dark-reared / motorically-deprived sensory development
- Mirror neurons, social learning, imitation
- Embodiment-agnostic AI — large language models, transformer cognition without sensorimotor loops

**To test P2 (memory/learning as control extension):**
- Cellular cognition follow-ups (does the molecular substrate scale?)
- Semantic / episodic memory in non-action contexts

**To test P3 (genes → dynamics):**
- Epigenetics, trans-generational inheritance
- Specific gene-KO studies showing regime shifts
- Comparative connectome-vs-dynamics across closely related species

**To test P4 (inference as control's other side):**
- Pure perceptual prediction without motor coupling
- Sensorimotor-contingencies experimental literature (O'Regan-Noë successors)

**To test P5 (substrate-local credit assignment):**
- Temporal credit assignment in vivo
- Neuromodulator–dendrite interaction
- Feedback weight learning mechanisms

**To test P6 (population dynamics implement control):**
- Causal manipulations of manifold structure
- Non-manifold models compared on the same data

**To test the thesis as a whole:**
- Bayesian-brain / pure predictive-processing literature as a rival framework
- Symbolic / compositional generalization (language)

---

## Maintenance discipline

- Every ingest must add at least one entry to this ledger. If the source has no bearing on any pillar, note it under a "no bearing" line.
- Every ingest should ask explicitly: *where does this complicate the thesis?* before drafting the source page's Thesis Bearing section.
- A pillar with no resist entries gets flagged at the next lint pass.
- Pillar status should be updated when the balance of evidence shifts, not on routine ingests.
- The wanted-ingests list is the wiki's seek-list. New entries should be added when reading any source surfaces a discriminating gap.
