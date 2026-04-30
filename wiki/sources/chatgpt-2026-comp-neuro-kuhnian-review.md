---
title: "Computational Neuroscience Through a Kuhnian Lens"
type: source
source_type: article
authors:
  - "ChatGPT (OpenAI deep research)"
year: 2026
tags: [philosophy-of-neuroscience, methodology, paradigms, kuhn, marr-levels, meta-review]
date_ingested: 2026-04-30
key_finding: "Computational neuroscience is best read as a multi-paradigm field rather than a Kuhnian normal-science discipline; localized crisis signals exist (Bayesian optimality, DNN-as-brain-model, expectation suppression, dopamine heterogeneity, connectomics-to-understanding) but the field-wide pattern is proliferation plus hybridization, not revolution."
---

[Source PDF](../../raw/articles/computational-neuroscience-kuhnian-review.pdf)

## Provenance and how to read this source

This is an **LLM-generated deep research report** (ChatGPT, ~April 2026), not a peer-reviewed primary source. It synthesizes the published literature through Thomas Kuhn's framework (paradigms, normal science, anomalies, crisis, revolution) and reads as a meta-survey in the style of an academic review article.

The wiki ingests it as a **navigation document** — useful for its meta-frame and for its mapping of localized debates onto a unified Kuhnian vocabulary, *not* as an authority on any specific empirical claim. Wherever the report makes a substantive empirical claim, the citation it points to is the load-bearing source. Several of those citations (Hodgkin–Huxley, Wilson–Cowan, Hopfield, Rao–Ballard, [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]], [[brette-2018-coding-metaphor|Brette 2018]], [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]], [[vyas-2020-computation-through-dynamics|Vyas 2020]]) are already ingested independently; others (Marder on parameter degeneracy, Pouget–Wolpert–Körding–Ma on probabilistic population codes, Schultz on dopamine RPE, Sutton–Barto on RL, Sporns on connectomics, Friston on FEP) are in the wiki primarily through derivative or sibling sources rather than the originals.

The source page therefore serves two purposes: (i) it preserves the *meta-frame* the report contributes (paradigm pluralism, recurring local crises, hybridization as the normal-science move) on a page where the meta-frame can be linked from existing topic pages without contaminating those pages with an LLM survey's voice; (ii) it stands as an explicit pointer to the *primary sources* the wiki should ingest if it wants to follow up on any specific claim — the report's bibliography is its main load-bearing contribution. Single-citation hedging applies throughout: the report is the only source for the synthesis, and most synthesis claims have not been independently vetted against the primary literature for this wiki.

## Overview

The report applies Kuhn's framework — paradigms (shared exemplars + methods + standards), normal science (puzzle-solving), anomalies (persistent unresolved tensions), crisis (loss of confidence + proliferation of alternatives), and revolution (paradigm replacement) — to contemporary computational neuroscience. The headline diagnosis: the field does **not** look like a single Kuhnian paradigm undergoing revolution. It looks like a stable multi-paradigm ecology in which several partly incommensurable research programs coexist, each with its own canonical exemplars, standards of success, and characteristic anomalies.

Two adaptations of Kuhn's framework are flagged as necessary:
1. **Marr's levels** ([[marrs-levels-of-analysis|computational / algorithmic / implementational]]) make many paradigm "competitions" actually orthogonal — paradigms aiming at different levels are complementary, not rival.
2. **Inherited epistemic standards** differ across paradigms (biophysical realism, predictive accuracy on neural data, normative optimality, behavioral fit) — the same dataset can be a "success" by one standard and an "anomaly" by another, generating Kuhnian-style incommensurability.

Nine paradigm clusters are surveyed:
- **Single-neuron biophysics** (Hodgkin–Huxley lineage; conductance / compartmental models; NEURON simulation environment).
- **Rate-based networks** ([[wilson-cowan-1972-ei-populations|Wilson–Cowan]] lineage; mean-field ODE/PDE; nonlinear dynamics).
- **Spiking networks** (LIF / point-process / GLM models; STDP; spike statistics).
- **Bayesian brain / probabilistic coding** (ideal observers; PPCs; cue integration).
- **Predictive coding / processing** ([[rao-ballard-1999-predictive-coding|Rao–Ballard]] lineage; hierarchical generative models; [[free-energy-principle|free-energy]] formulations).
- **Deep learning / neural networks** (task-trained DNNs predicting neural responses; benchmarking platforms).
- **Reinforcement learning** (TD / dopamine RPE; model-free vs. model-based; computational psychiatry).
- **Dynamical systems / attractors** ([[hopfield-network|Hopfield]] / Shenoy / Sussillo / Stokes lineage; the ancestor of [[computation-through-dynamics|CTD]]).
- **Connectomics** (EM reconstructions; diffusion MRI; graph/network analyses; "more-data → understanding" as implicit promise).

Each paradigm has stable normal-science puzzle sets and major successes, *and* persistent local anomalies that do not cross over cleanly into other paradigms (because the standards differ).

## Key claims

### The field is multi-paradigm, not single-paradigm

Computational neuroscience does not operate under a shared dominant paradigm with shared success criteria. It operates as a confederation of paradigms with overlapping concerns and different evaluative standards. This is partly because the brain is a multi-scale adaptive system and different paradigms target different scales; partly because comp neuro inherits epistemic standards from disparate parent fields (physics, statistics, AI, psychophysics, electrophysiology). For Kuhn this is a *pre-paradigmatic or pluralistic* state, not a normal-science state with paradigm shifts.

The implication for "is the field in crisis?" is that the question is malformed. The field is not in crisis because the field is not a single paradigm. Specific paradigms have crisis signals; the *field* exhibits stable pluralism.

### Persistent local anomalies (paradigm-by-paradigm)

The report inventories well-documented anomalies that strike near the core of specific paradigms:
- **Single-neuron biophysics**: parameter degeneracy / identifiability — many parameter sets produce the same output (Marder's lab), and "sloppy" parameter sensitivities mean fitted detailed models do not uniquely identify mechanism.
- **Predictive coding**: empirical evidence that "expectation suppression" can dissociate from expectation manipulation (i.e., suppression effects can be dominated by bottom-up adaptation rather than top-down prediction); broad reviews showing inconsistent expectation-suppression evidence across contexts. This complicates the simplest "expectation always suppresses responses" reading.
- **Deep learning as brain model**: systematic behavioral mismatches between standard CNNs and human vision — texture bias, adversarial vulnerability — suggesting "neural predictivity" benchmarks may not entail explanatory adequacy.
- **Reinforcement learning**: dopamine encodes more than scalar reward prediction error (movement, salience, sensory/motor/cognitive variables); recent large-scale recordings show mixed selectivity inconsistent with a single scalar teaching signal.
- **Dynamical systems / attractor**: "activity-silent" working memory frameworks challenge persistent-activity attractor accounts — information may be carried in synaptic weights or hidden states rather than active representations.
- **Connectomics**: the "understanding gap" — even rich structural maps do not automatically yield mechanistic understanding under standard analyses, sharpened by [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]'s microprocessor critique.

Each anomaly is "persistent but local": it tends to prompt *boundary-setting* (the paradigm "works only in regime X") or *auxiliary hypotheses* (multi-factor dopamine theories, hybrid attractor + silent-state working memory, hierarchical-RL extensions) rather than wholesale abandonment.

### Localized crisis signals, not field-wide crisis

By Kuhn's criteria (persistent anomalies, loss of confidence in major venues, proliferation of alternatives), the report identifies several **localized** crisis signals:
- The Bayesian optimality program has faced explicit "just-so story" critiques and major reviews emphasizing that broad optimality claims can be virtually meaningless without explicit constraints (Bowers & Davis 2012; Rahnev & Denison 2018 BBS).
- The DNN-as-brain-model program has faced major target-article critiques in BBS-style venues (Bowers et al. 2023 *deep problems* paper).
- The connectomics / "more data + standard methods → understanding" optimism is explicitly problematized by [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]].
- The dopamine/RL program is patching rather than abandoning, with broadening accounts of dopamine signaling.
- The predictive-coding program faces a recurring tension between expectation and adaptation explanations of suppression effects.

But these localized crises do not aggregate into a field-wide crisis because **the field has no shared dominant paradigm whose loss would constitute one**. The pattern is *proliferation plus attempted synthesis* — benchmarking platforms, hybrid models, integrative-discipline calls (cognitive computational neuroscience) — rather than convergence onto a successor paradigm.

### Marr's levels and Kuhnian incommensurability

Many apparent paradigm conflicts are actually Marr-level mismatches: biophysical models target the implementational level; rate / spiking / dynamical-systems models target the algorithmic level; Bayesian / predictive-coding / RL models target the computational level (or claim algorithmic implementation of computational principles); deep learning sits ambiguously across algorithm and implementation. When two paradigms are not aimed at the same level, their disagreement is not a real disagreement.

But some disagreements *are* Kuhnian — they target the same level with different standards:
- **Rate vs. timing in neural codes**: same data, different "what counts as a code" commitments.
- **Bayesian optimality vs. constraint-based suboptimality**: same behavior, different "what counts as success" commitments.
- **Expectation-as-prediction vs. adaptation**: same suppression signature, different mechanistic primitives.
- **Predictive accuracy vs. explanatory adequacy**: same DNN benchmark performance, different "what counts as a successful brain model" commitments.
- **Structure-first connectomics vs. dynamics-first explanations**: same circuit, different "what is the explanatory primitive" commitments.

These are the load-bearing interparadigm conflicts the report identifies as genuinely Kuhnian.

### Resolution by hybridization, not replacement

The report's diagnosis is that the field's natural equilibrium is *stable pluralism* with hybridization as the dominant resolution move:
- Bayesian decoding × efficient coding → constraint-aware Bayesian models.
- Connectome × dynamical-systems modeling → connectome-informed dynamical models.
- Deep learning × benchmarking platforms × mechanistic constraints → integrated explanatory programs.
- Multi-factor dopamine accounts → expanded RL formalisms rather than abandonment.

This pattern resembles a *Lakatosian protective belt* (auxiliary hypotheses absorbing anomalies) more than a Kuhnian revolution, and is consistent with comp neuro being a multi-disciplinary research program in expansion rather than a paradigm in crisis.

## Methods

Meta-analytic / bibliographic. The article cites ~50 primary sources and major reviews across the surveyed paradigms and uses Kuhn's *Structure of Scientific Revolutions* as the analytical framework. Operational definitions used:
- A "paradigm" = a Kuhnian disciplinary matrix (exemplars + methods + standards).
- An "anomaly" = a persistent empirical/methodological tension prompting (i) ad hoc patches, (ii) explicit boundary-setting, or (iii) rise of alternative frameworks.
- A "crisis signal" = (a) persistence/centrality of anomalies + (b) explicit loss of confidence in major venues + (c) proliferation of rival frameworks or benchmarking regimes.

The bibliographic strategy mixes primary citations (Hodgkin–Huxley 1952; Hopfield 1982; Rao–Ballard 1999; Pouget et al. 2013; Friston 2010; Marder; Bowers et al. 2023; Jonas & Kording 2017) with major review citations (Vyas et al. 2020; Saxe, Nelli & Summerfield 2020; Sutton & Barto 2018; Kuhn 1962/1970; Stanford Encyclopedia entry on Kuhn).

## Implications

For the wiki specifically:
- **Provides a meta-frame** ([[paradigm-pluralism-comp-neuro|paradigm pluralism]]) under which existing methodological-philosophical pages ([[principles-vs-parameters|principles vs parameters]], [[marrs-levels-of-analysis|Marr's levels]], [[neural-coding|neural coding]], [[brette-2018-coding-metaphor|Brette]], [[jonas-2017-microprocessor-critique|Jonas–Kording]], [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap–Kording]]) can be read as voices in different paradigms with different standards rather than as competing claims about a single normal science.
- **Surfaces gaps** — paradigms the wiki underrepresents (connectomics as a research program; reinforcement learning as a paradigm with its own standards; deep learning as brain model with explicit critiques; activity-silent working memory) where future ingests of primary sources would be valuable.
- **Sharpens the wiki's hedging** — the wiki's organizing thesis (closed-loop sensorimotor control) is itself one paradigm-style commitment among several; the appropriate framing is that it is a *normative bet* on which paradigm best supports a biologically grounded route to understanding intelligence, not a settled fact of the field.
- **Calibrates the dynamical-systems / CTD thread** — the report identifies CTD as a paradigm in tension with both coding-style explanations (different explanatory primitive) and Bayesian / predictive-coding accounts (different commitment to explicit uncertainty representation). The wiki's CTD page should reflect that this is not a settled framework but a paradigm in a larger ecology.

For computational neuroscience more broadly (per the report's own claim):
- "Crisis" framings of the field are mostly miscategorizations. The field is not pre-revolutionary; it is multi-paradigm.
- The right question is which paradigm-pair *interfaces* are productive (e.g., dynamical-systems × connectomics; Bayesian × efficient coding; deep learning × benchmarking) and which are stuck on standards disputes.
- Methodological discipline (ground-truth-anchored validation, sufficiency proofs, falsifiability criteria within paradigms) matters more than paradigm choice per se.

## Connections to existing knowledge

- **[[principles-vs-parameters|Principles vs Parameters]]** ([[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]]): the report's "what counts as understanding?" thread runs through this page. The Kuhnian frame says different paradigms have different answers; the principles-vs-parameters frame says the answer for *trained systems* is the recipe, not the parameters. Compatible — the latter is one paradigm-level position within the former's pluralism.
- **[[marrs-levels-of-analysis|Marr's Levels]]**: the report's first adaptation of Kuhn explicitly invokes Marr to defuse some "paradigm conflicts" as level-mismatches. This connects directly to the wiki's existing use of Marr as the benchmark for understanding (via [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]]).
- **[[neural-coding|Neural Coding]]** + **[[brette-2018-coding-metaphor|Brette 2018]]**: the report frames the rate-vs-timing debate and the broader "what is a code?" debate as paradigmatic Kuhnian conflicts over standards. Brette's critique sits inside this — coding-style decomposition is one paradigm's commitment, not an established fact.
- **[[computation-through-dynamics|Computation Through Dynamics]]**: the report identifies CTD as both competitor and mediator — competitor to coding-style decomposition, mediator between mechanistic and behavioral targets. This nuances the wiki's existing CTD framing.
- **[[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]**: cited as a Kuhnian crisis signal for the connectomics paradigm specifically. The wiki already treats this paper as load-bearing for the principles-vs-parameters and methodological-skepticism threads.
- **[[predictive-coding|Predictive Coding]]** / **[[free-energy-principle|FEP]]**: cited as paradigms with localized crisis signals (expectation-suppression dissociations; falsifiability concerns). The wiki tracks both.
- **[[hopfield-network|Hopfield Network]]** / **[[wilson-cowan-1972-ei-populations|Wilson–Cowan]]**: cited as canonical exemplars of the dynamical-systems and rate-based-network paradigms respectively.

## Open questions raised

- Which paradigm-pair interfaces are most productive for the wiki's organizing thesis (closed-loop sensorimotor control)? The report's table suggests dynamical-systems × connectomics, RL × dopamine multi-factor accounts, and predictive coding × deep learning as the live frontiers.
- Is the report's "no field-wide crisis" diagnosis robust, or does the absence of a dominant paradigm itself constitute a *pre-paradigmatic* state that Kuhn would treat differently from mature normal science? The report nods at this but does not resolve it.
- Activity-silent working memory vs. persistent-activity attractor accounts — flagged by the report as a load-bearing local anomaly in the dynamical-systems paradigm but not currently in the wiki.
- Dopamine heterogeneity beyond scalar RPE — multiple primary sources cited (Berke 2018; Engelhard et al. 2019; da Silva et al. 2018) but no dedicated wiki page on the contemporary dopamine debate.
- Connectomics-as-paradigm — the wiki has [[jonas-2017-microprocessor-critique|Jonas & Kording]]'s critique but no dedicated treatment of the connectomics research program itself. Worth ingesting Sporns or a major connectome review.

## Sources

- Self: ChatGPT (OpenAI deep research), "Computational Neuroscience Through a Kuhnian Lens," ~April 2026, as a meta-survey article.
- Companion: [[chatgpt-2026-comp-neuro-kuhnian-historiography|ChatGPT (2026, historiography)]] — same author, same date, overlapping bibliography; supplies the historiographic methodology and chronological scaffold (1907–2024), plus alternative historiographic frameworks beyond Kuhn ([[historiographic-frameworks-comp-neuro|Lakatos / Galison / Hacking / Bourdieu / Laudan]]).
- The article's bibliography (links collected on pages 19–21 of the source PDF) is the load-bearing contribution; primary sources should be consulted directly when any specific claim is followed up in the wiki.
