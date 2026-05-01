---
title: "Challenges to the Control Thesis"
type: exploration
tags: [meta, thesis, critique, rival-frameworks]
date_created: 2026-05-01
prompted_by: "wiki cleanup; sources that resist the control thesis are present in the wiki but not foregrounded; this page gives them a home"
---

The wiki's organizing thesis treats intelligence as fundamentally rooted in closed-loop sensorimotor control. This page is the dedicated home for arguments and evidence that *resist* that framing — methodological challenges, rival philosophical commitments, embodiment-agnostic counterexamples, and bottom-up developmental phenomena that don't obviously reduce to control.

This page complements [[control-thesis-ledger|the ledger]] (which scores per-pillar evidence) by engaging rival frameworks at length. The goal is not to defeat the thesis — the wiki retains it as an organizing lens — but to keep the lens honest by giving its sharpest critics room to be wrong on their own terms rather than being paraphrased away.

The wiki's working rule: **if a new ingest resists the thesis in a sustained way, it should land here, not in a footnote.** A source that complicates a single pillar goes in the ledger; a source that engages the framework as a whole goes here.

---

## 1. The methodological challenge

### Jonas & Kording (2017): the microprocessor critique

[[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] applied standard systems-neuroscience methods (connectomics, lesion studies, single-unit tuning, NMF, Granger causality) to a fully understood microprocessor running games. The methods did not recover the chip's algorithmic-level organization, even with full ground truth and the ability to simulate every transistor.

**The challenge to the control thesis.** Any claim of the form "this brain region implements closed-loop control of X" rests on inferential moves the microprocessor critique calls into question. If we cannot recover algorithmic structure from a system we fully understand, the inference from observed neural dynamics to "the brain is doing closed-loop control" is methodologically underdetermined.

**Why this is not a disqualification.** Jonas & Kording is methodological pessimism about *current* analytical techniques, not a metaphysical claim that brains aren't doing what we think they are. The wiki's response should be to demand higher evidentiary standards for control-theoretic claims — specifically:
- Causal manipulations of the postulated control variables, not just correlative observations.
- Explicit comparison against non-control models on the same data.
- Ground-truth-anchored validation against engineered systems before applying analytical methods to neural data.

The wiki's [[unified-picture-single-neuron-population-control|unified-picture analysis]] partially heeds this: its load-bearing gap ("nobody has shown apical-dendrite events reshaping motor-cortex manifolds during adaptation") is a causal, control-relevant gap, not a correlative one.

---

## 2. The representational challenge

### Brette (2018): the coding metaphor as incoherent foundation

[[brette-2018-coding-metaphor|Brette (2018)]] argues that the [[neural-coding|neural coding metaphor]] is incoherent at the level of theories of brain function (though valid as a measurement tool). Three sub-arguments:

1. Tuning curves establish only context-dependent sensitivity, not "encoding" of properties (the Crick "overwise neuron" fallacy).
2. Codes carry Shannon information by reference to known external messages, but the brain has no external referent — the symbol-grounding problem applied to neural representations. The "efficient coding paradox": a maximally efficient code is unreadable.
3. The linear / dominoes causal structure of codes is incongruent with the brain's circular dynamical-systems coupling to environment.

**The challenge to the control thesis — paradoxical.** Brette's positive proposal ([[subjective-physics|subjective physics]]; [[sensorimotor-contingencies|sensorimotor contingencies]]; "models that behave") is the philosophical articulation of closed-loop framing. He is the wiki's most explicit ally on the framing question.

But Brette's critique cuts at *triumphalist* readings of any specific paper. Population dynamics "implementing control" presupposes that population activity *represents* control variables. The closed-loop / subjective-physics framing rejects representation altogether: nothing in the organism refers to anything external; what's internal are the lawful relations themselves.

**This is a serious tension within the wiki.** The control thesis as stated assumes some version of representation (genes encode dynamics; neural populations implement control; predictions are about external states). Brette's strict subjective-physics reading would refuse this entire vocabulary. The wiki has not yet resolved whether to:

- (a) Adopt the strict subjective-physics framing — abandon "encoding," "representing," "predicting" as theoretical primitives, treat them only as heuristics for the modeler.
- (b) Retain a moderate-representational reading — neural variables stand in lawful relation to organism-relevant variables, and we use "encoding" / "predicting" as shorthand for those lawful relations, not for symbolic correspondence.
- (c) Bracket the question — pursue control-theoretic mechanisms without committing on the representational ontology.

The wiki's working position has been (b) by default; this is worth flagging as a load-bearing assumption.

---

## 3. Embodiment-agnostic intelligence

### Large language models and transformer cognition

The wiki has not yet ingested LLM literature. **This is itself the largest gap, and surfacing it as a challenge is more important than resolving it.**

The phenomenon: large transformer models trained only on text exhibit cognitive performance on tasks the control thesis predicts should require sensorimotor grounding (commonsense reasoning, analogy, mathematical problem-solving, programming). They have no closed-loop coupling to a physical environment during training and limited closed-loop coupling during deployment.

**Possible readings:**

1. **Defensive** — LLMs aren't really doing what their performance suggests. They are pattern-matchers without true understanding; the control thesis is silent on them. *Risk: this reading is becoming harder to maintain as model capabilities scale.*

2. **Concession** — sensorimotor coupling is sufficient but not necessary for intelligence. The thesis would need to be weakened: *closed-loop control is one route to intelligence; large-corpus statistical learning is another.* This is a substantial retreat from the thesis as stated.

3. **Extension** — the closed loop is implicit in training. LLMs are trained on text produced by embodied humans, so the sensorimotor structure of human experience is *encoded* in the training distribution. The model inherits the loop's regularities at one remove. *This is a real argument, but it requires defending: how exactly does the regularity transfer? Does it transfer fully?*

4. **Loop-at-deployment** — even if LLM training is loop-free, their deployment in agentic settings (with tool use, memory, environmental feedback) reintroduces the loop. The wiki should engage agentic AI literature as a *partial* test of the thesis.

The honest position: **the wiki should ingest at least one major LLM paper and one major embodiment-agnostic AI critique** before being able to take a serious position. The current absence is a curation gap.

---

## 4. Bottom-up sensory development

### Receptive-field development without strong sensorimotor coupling

V1 receptive-field properties (orientation tuning, simple/complex cell structure) develop in dark-reared animals to a substantial degree, and recover with even brief visual exposure that does not require sustained motor engagement. Multiple lines of evidence (Hubel-Wiesel critical-period work and follow-ups) suggest that representation formation is *not* fully gated by closed-loop sensorimotor coupling.

**The challenge to the control thesis.** P1 (sensorimotor coupling as developmental substrate) needs to accommodate findings that representational development proceeds with passive sensory exposure plus genetically specified circuit constraints, without obligate motor coupling.

**Possible reconciliations:**
- Sensorimotor coupling is the *organizing* principle for cognition broadly, but specific representational scaffolds (V1 RFs) develop on a more autonomous schedule.
- Dark-rearing is not actually motorically deprived — animals still move, vestibular input still occurs, eye movements happen. The "closed loop" may be subtler than visual scene-action coupling.
- Genes specify the *initial* circuit dynamics directly (Rao-Ballard's natural-image-statistics learning operating on a genetically pre-shaped substrate), and sensorimotor coupling tunes from there.

**Status:** the wiki has not ingested primary dark-rearing literature. This is a wanted ingest in the ledger.

---

## 5. Symbolic and compositional generalization

The Fodor-style challenge: human language exhibits productive, compositional generalization that does not obviously reduce to sensorimotor contingencies. Speakers produce and understand sentences they have never encountered, applying compositional rules that operate on abstract syntactic categories.

If compositional generalization is a primary feature of human intelligence, and if it does not reduce to sensorimotor primitives, then the control thesis is at best incomplete.

**Counter-readings within the wiki's framing:**
- Compositional language is grounded *eventually* in sensorimotor primitives but operates many levels of abstraction above them. The thesis predicts continuity, not direct reducibility.
- Recent embodied-cognition work (and the [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis]] paradigm of repurposing primitive sensorimotor algorithms for cognitive uses) is the wiki's preferred reconciliation: language extends control over abstract latents the way endotaxis extends chemotaxis over space.
- LLMs (see §3) demonstrate compositional generalization without a sensorimotor history. This either undermines the reconciliation or supports the "loop is implicit in training data" reading.

The wiki has no dedicated page on language; this is a gap.

---

## 6. Cellular cognition predates the nervous system

### Kukushkin et al. (2024): memory-like primitives in non-neural cells

[[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] reproduces the [[spacing-effect|spacing effect]] in non-neural human cell lines using PKA / PKC / ERK / CREB cascade kinetics. Memory's molecular substrate predates neurons and operates in cells that do not control behavior in any obvious sense.

**The challenge to the control thesis.** P2 (memory as extension of control) is harder to maintain if memory primitives exist in cells that have no behavior to control. Two readings:

- **Soft.** The cellular kinetics are pre-existing primitives; *deployment in service of behavior* is what makes them memory-as-control. Neurons inherited the kinetics and put them to use in the loop. The thesis survives at the integrative level.
- **Hard.** Memory is a substrate-general property of cellular signaling, not specifically a control extension. The control thesis over-localizes a phenomenon that is widely distributed at the cellular level.

The wiki has tilted toward the soft reading. The hard reading remains live and the [[cellular-cognition|cellular cognition]] page is the place to track it.

---

## 7. Open invitation

This page is where new contradictions land. When an ingest engages a rival framework at length, or when a finding resists the thesis as a whole (not just one pillar), it belongs here. Add sections rather than arguing a finding away.

The wiki's discipline: a thesis kept honest by adversarial engagement is more valuable than a thesis defended by curatorial filtering. If this page grows large, the thesis is being pressure-tested — that is the desired state.

---

## Sources

- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]
- [[brette-2018-coding-metaphor|Brette (2018)]]
- [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]]
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — informs §1 (methodology) and §3 (LLMs) indirectly

## Related

- [[control-thesis-ledger|Control thesis ledger]] — per-pillar evidence ledger
- [[Dark Room Problem]] — a specific narrow challenge to predictive processing
- [[neural-coding|Neural coding (the metaphor)]] — Brette's primary target
- [[subjective-physics|Subjective physics]] — Brette's positive alternative
- [[paradigm-pluralism-comp-neuro|Paradigm pluralism]] — meta-frame for reading the wiki itself
