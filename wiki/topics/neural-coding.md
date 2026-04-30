---
title: "Neural Coding"
type: theory
aliases: ["neural code", "coding metaphor", "encoding and decoding", "sensory coding"]
tags: [representation, information-theory, perception, coding, philosophy-of-neuroscience, contested-framework]
source_count: 2
last_updated: 2026-04-29
status: contested
---

**Neural coding** is the dominant framework in 20th- and 21st-century systems neuroscience for theorizing about how nervous systems represent information. In its standard form, sensory or task-relevant variables (orientation, sound location, value, decision, identity) are taken to be *encoded* by neural activity — typically by firing rates, spike timing patterns, or population-level state vectors — and *decoded* by downstream computations or by an external observer (the experimenter or an "ideal observer" model). The framework subsumes single-unit tuning curves, population coding, Bayesian decoding, predictive coding, sparse/efficient coding, and the broader Bayesian-brain program.

[[brette-2018-coding-metaphor|Brette (2018)]] gives the most systematic articulation of the framework — and the most sustained critique of it — in the contemporary literature. Following Perkel & Bullock (1968), the metaphor carries three logically distinct senses, only the first of which is established by typical empirical results:

1. **Correspondence (technical)** — a statistical correspondence between a stimulus parameter and an observable derived from neural activity. Established by tuning-curve experiments, decoding analyses, and information-theoretic measurements.
2. **Representation** — the neural code is a *message* about an external property, with the brain as *reader*.
3. **Causality** — the encoded message has *causal powers* in the brain; downstream computations operate on it.

The technical sense does not entail the representational or causal senses. Brette argues that the typical move from technical to representational claims constitutes an unjustified semantic drift — and that the field's theories rest on this drift rather than on the technical results themselves.

## The framework

### Single-neuron coding

Originated with Adrian's discovery (1920s) that sensory afferents fire spikes whose rate varies systematically with stimulus intensity. Generalized to "tuning curves" — plots of firing rate versus a stimulus parameter, exemplified by Hubel & Wiesel's (1962) orientation tuning in V1, O'Keefe's (1971) place fields in hippocampus, Quiroga's (2005) "concept cells" in MTL. The standard interpretation is that each cell *encodes* the parameter to which it is tuned.

### Population coding

Many cells are required to disambiguate stimuli that single cells cannot resolve. Population codes (Pouget et al. 2003; Jazayeri & Movshon 2006; Knill & Pouget 2004) treat the activity of an ensemble as encoding a probability distribution over stimulus parameters. Decoding extracts a single value (e.g., the maximum likelihood estimate) or the full distribution. The Bayesian brain hypothesis is the strongest version: neural populations represent posterior distributions over latent variables and update them via inference.

### Information-theoretic coding

Shannon (1948) information theory provides a measurement framework — mutual information between stimulus and neural response quantifies how much one observable carries about another. Barlow's (1961) efficient coding hypothesis proposed that sensory neurons are organized to maximize information transmission about natural stimuli subject to bandwidth and metabolic constraints. Olshausen & Field's (1996) sparse coding result derives V1-like receptive fields by minimizing description length over natural images. See [[efficient-coding-hypothesis|efficient coding]] and [[sparse-coding|sparse coding]].

### Predictive and generative coding

Hierarchical predictive coding ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]) proposes that neural activity encodes the latent variables of a generative model that maps causes → observables. Top-down connections carry predictions; bottom-up connections carry residual errors. Friston's [[free-energy-principle|free-energy principle]] generalizes this to a unified objective for perception, learning, and action. Both inherit the framing that neural activity *represents* hidden causes of sensory inputs.

### Cell assemblies and engrams

Hebb's (1949) cell assembly hypothesis holds that memories and percepts are encoded by sub-populations of co-activated neurons. Tonegawa-style engram cells (Tonegawa et al. 2015) operationalize this: optogenetically reactivating an engram cell assembly elicits the corresponding memory. The framework treats percepts as *which* assembly is active, not *what relations* hold among assemblies — a critical limitation for representing structured scenes (see [[binding-problem]]).

### Decoders and ideal observers

Decoding analyses (Macmillan & Creelman 2005; Quian Quiroga & Panzeri 2009) build statistical models that map observed neural activity to predicted stimulus parameters. *Ideal observers* are decoders that make optimal use of the experimenter's information about stimulus presentations. Behavioral comparisons (e.g., Skottun 1998 on ITD discrimination) compare the accuracy of an ideal observer reading single-neuron activity to the accuracy of behavioral discrimination — the implicit conclusion being that, since they match, single neurons "carry enough information" to support the behavior.

## Critique

[[brette-2018-coding-metaphor|Brette (2018)]] is the most thorough articulation of the critique. Three load-bearing arguments:

### Representational power is weaker than implied (context-dependence of tuning)

Tuning curves establish *sensitivity* to a stimulus parameter when other parameters are held fixed — they do not establish that the cell *carries information about* that parameter in any other context. The cone-wavelength example (Crick 1979's "fallacy of the overwise neuron"): a cone's response to monochromatic light at fixed intensity varies with wavelength, so it "encodes wavelength" in the technical sense — yet animals with single-cone retinas are color-blind, because the same cone response is consistent with many wavelength-intensity combinations. Wavelength is encoded only by the *relative* activity of cones with different tunings.

The same point generalizes to V1 orientation tuning (Bolz & Gilbert 1986; Gilbert & Li 2013; Pakan et al. 2018; Chanauria et al. 2018 — tuning depends on surround, on task, on locomotion, on prior auditory stimuli), to MSO/IC ITD tuning (Brette 2010, 2018; Goodman et al. 2013 — single-neuron ITD selectivity is ambiguous when sound spectrum is unknown; population heterogeneity is required), and to Bayesian-brain readouts of population codes ([[brette-2018-coding-metaphor|Brette 2018]] §2.3.2: a context-free linear-log-likelihood readout requires that tuning curves be context-free, but they are not).

The deep problem: *context cannot be incorporated by extending the code to represent more parameters*, because context defines what the parameters *are* (the orientation *of a bar* requires that there is a bar; without an object, "orientation" has no referent). Coding presupposes object-formation; it does not deliver it.

### Codes carry information by reference, not by structure

Shannon information is *correspondence to a known external message*. The experimenter has access to the stimulus and so can compute the information neural activity carries about it. The brain has only the neural activity; it does not know what the activity refers to. This is the **symbol grounding problem** (Harnad 1990) applied to neural representations.

The **efficient-coding paradox**: if a code maximally compresses input, the encoded messages are indistinguishable from random noise without the decoding key — so a perfectly efficient code is *unreadable* by any reader who only sees the code. The notion of information implied by efficient-coding theories is information accessible to an external observer (the experimenter or evolution), not to the organism.

The **right notion of information** for an organism is the *invariant structure of relations among its sensor signals and actions* — Gibson's (1986) ecological invariants, O'Regan & Noë's (2001) [[sensorimotor-contingencies|sensorimotor contingencies]], Brette's [[subjective-physics|subjective physics]]. Information lives in *laws*: "if I do action A, then sensory property B happens"; "if sensory property A happens, then property B tends to follow." This is **information by structure**, not by reference.

### Causal structure is incongruent with the brain's

Coding describes brain function as a linear chain (encode → transform → decode → effector — "dominoes" in Brette's analogy, Fig. 10). The brain's actual causal structure is circular: a distributed dynamical system mutually coupled to itself and to the environment ("tent"). The two structures are categorically different, not connected by adding more steps to the chain.

Coding variables (firing rate averaged over a window, BOLD signal, trial-averaged spike count) are aggregate observables, not state variables of the brain's dynamical system. State variables are membrane potentials, ion-channel states, neurotransmitter concentrations. *Spikes* — being discrete events — have causal effects (synaptic release, postsynaptic potentials, downstream spikes), but they are not state variables either; they are *transitions* in state space. The "neural code" reifies aggregates that are not part of the causal structure.

Worked examples:
- **The Paramecium "swimming neuron"**: a single excitable cell encodes chemical concentration in spikes (technical sense). A coding-view analysis would conclude that the cell's tuning is set by efficient input transmission. A sensorimotor analysis would conclude that the cell's tuning is set by the closed control loop that produces effective chemotaxis. The two analyses make different empirical predictions about the cell's response properties.
- **Cardiac excitable cells**: rate-coding analysis would conclude the heart "uses a rate code" for running speed. Yet the synchrony of atrial vs. ventricular contraction is life-critical. The temporal coordination matters causally; the rate-coding analysis would correctly characterize input-output sensitivity but completely miss the causal structure that matters for function.

## What survives

Brette's argument does not deny information theory's value as a *measurement tool*. Statistical correspondences between stimuli and neural activity remain real and quantifiable. What he denies is that those correspondences support claims about *what the brain represents*. Information theory in a sensorimotor framework would play the role spectroscopy plays in astronomy — a measurement instrument, not a framework for theory.

Some specific coding frameworks survive Brette's critique relatively intact in their *mechanistic* form, even when their *representational* form is challenged:

- **Sparse coding** as a description of dictionary-learning algorithms in cortex ([[sparse-coding|sparse coding]]) survives as a mechanistic claim about plasticity. The representational reading (sparse codes "represent" the latent causes of inputs) is the contested part.
- **Predictive coding** as a description of cortical microcircuits ([[predictive-coding|predictive coding]]; [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]]) survives as a *credit-assignment* mechanism. The representational reading (apical-dendrite signals "represent" prediction errors over latent causes) is the contested part.
- **The dendritic credit-assignment lineage** ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) is internally framed in coding terms but its biology — apical compartments as gated signaling pathways carrying residual mismatch — admits a sensorimotor reading where the apical signal is residual sensorimotor error. The mechanism survives reinterpretation; the framing changes.

## The rate-vs-timing dispute as Kuhnian

The long-running rate-vs-timing debate ([[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT 2026]]) is Kuhnian in a specific sense: the two camps treat the *same* spike-train data with different commitments about what the explanatory primitive is. Rate-centric paradigms treat irregularity as a feature (stochastic computation, distributional codes); timing-centric paradigms treat millisecond reliability under fluctuating inputs as evidence for temporally structured computation. The dispute shifts which puzzles are legitimate and which results count as anomalies — Kuhn's hallmark of standards-divergent conflict. Brette's critique sits inside this: the coding-metaphor critique is a paradigm-level move that questions whether *either* rate or timing readings get the explanatory primitive right, and recommends [[paradigm-pluralism-comp-neuro|paradigm-aware]] reinterpretation rather than adjudication within the coding frame.

## Status in this wiki

The wiki uses coding-flavored language ("place cells encode location," "PFC encodes the categorization rule," "V1 encodes orientation") because this is the standard vocabulary of the literature it summarizes. Following Brette, these claims should be read as *correspondence claims with experimental scope* — under the conditions of the experiment, neural activity statistically corresponds to the named variable — without inheriting the representational and causal entailments. The wiki's organizing principle (intelligence begins with closed-loop sensorimotor control) is essentially a constructive version of Brette's negative argument; the negative and positive halves are mutually supporting.

## Sources

- [[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT (2026)]] — frames the rate-vs-timing debate (and the broader "what is a code?" debate) as Kuhnian standards-divergent conflicts; locates the coding metaphor as one paradigm's foundational commitment within a [[paradigm-pluralism-comp-neuro|multi-paradigm comp-neuro ecology]].
- [[brette-2018-coding-metaphor|Brette (2018)]] — sustained philosophical critique of the coding metaphor, including the three-sense decomposition (correspondence, representation, causality), the worked examples (cone wavelength, ITD slope coding, V1 context-dependence, ideal observers, cell assemblies, Paramecium, heart, dominoes-vs-tent), and the positive proposal (subjective physics, sensorimotor contingencies, synchrony receptive fields, models that behave).
