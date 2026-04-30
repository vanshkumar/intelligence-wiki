---
title: "Paradigm Pluralism in Computational Neuroscience"
type: concept
aliases: ["multi-paradigm computational neuroscience", "Kuhnian frame for comp neuro", "incommensurable standards in neuroscience", "paradigm ecology"]
tags: [philosophy-of-neuroscience, methodology, kuhn, marr-levels, what-is-understanding, paradigms]
source_count: 2
last_updated: 2026-04-30
confidence: emerging
---

A meta-methodological frame for reading computational neuroscience as a confederation of partly incommensurable paradigms with different exemplars, methods, and standards of success — rather than as a single Kuhnian "normal science" with a dominant paradigm undergoing puzzle-solving (and occasional revolution). Articulated explicitly in [[chatgpt-2026-comp-neuro-kuhnian-review|the ChatGPT 2026 Kuhnian review]]; consistent with positions implicit in [[principles-vs-parameters|Lillicrap & Kording 2019]], [[brette-2018-coding-metaphor|Brette 2018]], and [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]].

## The claim

Kuhn's framework distinguishes:
- **Paradigms** — shared exemplars + methods + standards.
- **Normal science** — puzzle-solving within those standards.
- **Anomalies** — persistent puzzles the paradigm cannot absorb.
- **Crisis** — loss of confidence in a dominant paradigm + proliferation of alternatives.
- **Revolution** — replacement of one paradigm by another with different standards.

Applied to computational neuroscience, the diagnosis is that the field does **not** look like a single paradigm doing normal science. It looks like a stable multi-paradigm ecology. The paradigm clusters — single-neuron biophysics, rate-based networks, spiking networks, Bayesian/probabilistic coding, predictive coding, deep learning, reinforcement learning, dynamical systems / attractors, connectomics — each have:
- canonical exemplars (Hodgkin–Huxley; [[wilson-cowan-1972-ei-populations|Wilson–Cowan]]; [[hopfield-network|Hopfield]]; Bayesian ideal observers; [[rao-ballard-1999-predictive-coding|Rao–Ballard]]; task-trained DNNs; TD learning; [[computation-through-dynamics|CTD]]; the connectome);
- characteristic methods;
- inherited evaluative standards (biophysical realism; predictive accuracy on neural data; normative optimality; behavioral fit; engineering performance);
- and persistent local anomalies.

Crucially, the *standards* differ across paradigms. The same dataset can be a "success" by predictive-accuracy standards (deep learning) and an "anomaly" by explanatory-adequacy standards (cognitive psychophysics). This is Kuhnian incommensurability — paradigms talking past each other because they aim at different things.

## Two adaptations of Kuhn for comp neuro

**1. Multi-level structure (Marr)**. [[marrs-levels-of-analysis|Marr's three levels]] (computational / algorithmic / implementational) defuse some apparent paradigm conflicts by showing the paradigms target different levels of the same phenomenon. Biophysics targets implementation; rate / spiking / dynamical-systems models target algorithm; Bayesian / predictive-coding / RL accounts target computation (or claim algorithmic implementation of computational principles). Two paradigms not aimed at the same level are complementary, not rival.

**2. Inherited epistemic standards**. Computational neuroscience inherits standards from physics (analytical tractability, parsimony), statistics (predictive validation, uncertainty quantification), AI (benchmark performance), psychology (behavioral fit), and electrophysiology (biophysical realism). These standards are not always compatible. A paradigm grounded in one parent field's standards will treat data differently than a paradigm grounded in another's — this is structural, not ideological.

## Persistent local anomalies (paradigm-by-paradigm)

The pattern flagged by the [[chatgpt-2026-comp-neuro-kuhnian-review|review]] is that each paradigm has anomalies that strike near its core but do not propagate cleanly to other paradigms (because the standards differ):
- **Single-neuron biophysics**: parameter [[degeneracy|degeneracy]] / identifiability — many parameter sets produce the same output (Marder); "sloppy" sensitivities mean fitting does not uniquely identify mechanism.
- **Predictive coding**: expectation-suppression dissociations — suppression effects in some contexts are dominated by bottom-up adaptation rather than top-down expectation; broad reviews show inconsistent expectation-suppression evidence across contexts.
- **Deep learning as brain model**: behavioral mismatches (texture bias, adversarial vulnerability) suggest "neural predictivity" benchmarks may not entail explanatory adequacy.
- **Reinforcement learning**: dopamine encodes more than scalar reward prediction error (movement, salience, mixed selectivity), challenging a single-scalar teaching-signal account.
- **Dynamical systems / attractor**: "activity-silent" working memory frameworks challenge persistent-activity attractor accounts.
- **Connectomics**: the [[jonas-2017-microprocessor-critique|"understanding gap"]] — even rich structural maps do not yield mechanistic understanding under standard analyses.

Each anomaly tends to prompt **boundary-setting** ("works only in regime X") or **auxiliary hypotheses** (multi-factor dopamine, hybrid attractor + silent-state working memory, hierarchical RL extensions) rather than wholesale abandonment.

## Localized crisis signals, no field-wide crisis

By Kuhn's criteria, several localized crisis signals are visible:
- The Bayesian optimality program faces explicit "just-so story" critiques (Bowers & Davis 2012; Rahnev & Denison 2018 BBS) and major reviews emphasizing that broad optimality claims can be virtually meaningless without explicit constraints.
- The DNN-as-brain-model program faces target-article critiques (Bowers et al. 2023 BBS *deep problems* paper).
- The connectomics / "more data + standard methods → understanding" optimism is explicitly problematized by [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]].
- The dopamine/RL program is patching rather than abandoning, with broadening multi-factor accounts.
- The predictive-coding program faces the recurring expectation-vs.-adaptation tension.

But these do not aggregate into a *field-wide* crisis because the field has no shared dominant paradigm whose loss would constitute one. The aggregate pattern since the 2010s is **proliferation plus attempted synthesis** — benchmarking platforms, hybrid models, integrative-discipline calls (cognitive computational neuroscience) — consistent with field expansion rather than Kuhnian revolution.

## Genuinely Kuhnian conflicts (level-aligned, standards-divergent)

When two paradigms target the same level but bring different standards, the disagreement is paradigmatic in Kuhn's sense:
- **Rate vs. timing in [[neural-coding|neural codes]]** — same data, different "what counts as a code" commitments.
- **Bayesian optimality vs. constraint-based suboptimality** — same behavior, different "what counts as success" commitments.
- **Expectation-as-prediction vs. adaptation** — same suppression signature, different mechanistic primitives.
- **Predictive accuracy vs. explanatory adequacy** in DNN-as-brain-model — same benchmark performance, different "what counts as a successful brain model" commitments.
- **Structure-first connectomics vs. dynamics-first explanations** — same circuit, different "what is the explanatory primitive" commitments.

These are the load-bearing interparadigm conflicts that resist resolution by appeal to data alone, because data are interpreted differently under different standards.

## Resolution by hybridization

The dominant resolution move in the field is hybridization rather than replacement:
- Bayesian decoding × efficient coding → constraint-aware Bayesian models.
- Connectome × dynamical-systems modeling → connectome-informed dynamical models (e.g., dynamical models of *Drosophila* connectomes).
- Deep learning × benchmarking platforms × mechanistic constraints → integrated explanatory programs.
- Multi-factor dopamine accounts → expanded RL formalisms rather than abandonment.

This pattern resembles a *Lakatosian protective belt* (auxiliary hypotheses absorbing anomalies) more than a Kuhnian revolution, and is consistent with comp neuro being a multi-disciplinary research program in expansion.

## Relation to other methodological positions

- **[[principles-vs-parameters|Principles vs Parameters]]** ([[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]]): a paradigm-level commitment to *what neuroscience can communicate* — the recipe, not the trained parameters. Sits inside paradigm pluralism as one substantive answer to the "what counts as understanding?" question.
- **[[jonas-2017-microprocessor-critique|Jonas & Kording 2017]]**: a *crisis signal* for the connectomics paradigm specifically — standard methods do not recover [[marrs-levels-of-analysis|Marr-level]] understanding even with full ground truth on a known engineered system.
- **[[brette-2018-coding-metaphor|Brette 2018]]**: a deep critique of one paradigm's *foundational metaphor* (coding). Within the Kuhnian frame, this is an interparadigm conflict between coding-style and dynamical-systems / sensorimotor-contingencies frames over what the explanatory primitive should be.
- **[[historiographic-frameworks-comp-neuro|Historiographic Frameworks]]** ([[chatgpt-2026-comp-neuro-kuhnian-historiography|ChatGPT 2026 historiography sibling]]): the post-Kuhnian frameworks (Lakatos research programmes, Galison trading zones, Hacking styles of reasoning, Bourdieu field theory, Laudan research traditions) that pick up where Kuhn falls short at the whole-field level. Comp neuro's discontinuities are predominantly technology/infrastructure-driven rather than anomaly-driven, which Kuhn handles awkwardly and the alternative frameworks handle directly.
- **[[free-energy-principle|FEP]]** / **[[predictive-coding|predictive coding]]**: the [[chatgpt-2026-comp-neuro-kuhnian-review|review]] flags FEP as a candidate "unifying paradigm" that has not actually unified the field — its falsifiability is contested, and it coexists rather than replaces.
- **[[computation-through-dynamics|CTD]]**: identified as both competitor and mediator — competitor to coding-style decomposition, mediator between mechanistic and behavioral targets via shared mathematical language.

## Implication for the wiki

The wiki's organizing thesis (closed-loop sensorimotor control) is itself a paradigm-style commitment — a *normative bet* on which paradigm best supports a biologically grounded route to understanding intelligence. It is not a settled fact of the field. The Kuhnian frame recommends:
- Treating the wiki's commitments (the [[degeneracy|control-theoretic genes hypothesis]], CTD, sensorimotor primitives, predictive coding read as a perceptual subsystem of a control loop) as paradigm-internal positions, not as field consensus.
- Reading sources from rival paradigms (pure coding-frame, optimality-frame, structure-first connectomics) on their own terms while flagging where their standards differ.
- Looking for productive *paradigm-pair interfaces* (CTD × connectomics; predictive coding × CTD; multi-factor dopamine × CTD) rather than expecting wholesale resolution.

## Caveats

The frame itself is contestable. A strict Kuhnian could argue that the absence of a dominant paradigm is not pluralism but a *pre-paradigmatic* state, in which case the field is awaiting (rather than past) its first paradigm. A Lakatosian could argue that what looks like multi-paradigm pluralism is actually a research program with a stable hard core (computation as the brain's job description) and a protective belt of swappable auxiliary hypotheses. A Feyerabendian could argue paradigm pluralism is the right end-state for *all* mature science. The frame here treats Kuhn pragmatically as a vocabulary for surfacing standards-disputes rather than as a settled philosophy of science.

The single source it rests on — the [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT 2026 Kuhnian review]] — is itself an LLM-generated meta-survey, not peer-reviewed primary literature. The frame is a *useful map*, not a vetted scholarly position.

## Sources

- [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT (2026, review)]] — articulates the multi-paradigm reading of computational neuroscience using Kuhn's framework; surveys nine paradigm clusters with their canonical exemplars and persistent local anomalies; argues for stable pluralism with hybridization as the dominant resolution move rather than field-wide crisis or paradigm revolution.
- [[chatgpt-2026-comp-neuro-kuhnian-historiography|ChatGPT (2026, historiography)]] — companion meta-survey supplying the historiographic methodology and chronological scaffold; argues Kuhn fits well at the subcommunity level but requires complementary frameworks ([[historiographic-frameworks-comp-neuro|Lakatos / Galison / Hacking / Bourdieu / Laudan]]) at the whole-field level because comp neuro's discontinuities are predominantly technology and infrastructure driven.
