---
title: "Is coding a relevant metaphor for the brain?"
type: source
source_type: paper
authors:
  - "Romain Brette"
year: 2018
doi: "10.1101/168237"
tags: [neural-coding, philosophy-of-neuroscience, sensorimotor, ideal-observer, linking-proposition, symbol-grounding, circular-causality, sensorimotor-contingencies, subjective-physics, action-potential, binding-problem, ethological]
date_ingested: 2026-04-29
key_finding: "The neural coding metaphor — encoding/decoding, codes, ideal observers, Bayesian decoders — is a misleading framework for theorizing about brain function: codes have weaker representational power than implied (context-dependent tuning), they convey only Shannon information by reference to known external messages (which the brain has no access to), and their linear/dominoes causal structure is incongruent with the brain's circular dynamical-systems coupling to the environment. Spikes are timed actions, not hieroglyphs to be decoded."
---

## Overview

Brette (2018) is the most thorough sustained critique of the *neural coding metaphor* in the contemporary neuroscience literature. The paper argues that "neural coding" — the framework in which sensory signals are *encoded* into neural activity, *decoded* by downstream circuits, and *read* by an ideal observer — is misleading as a basis for theories of brain function. The argument is structured in three parts, each addressing a distinct sense of the metaphor identified by Perkel & Bullock (1968):

1. **Correspondence (Section 2)**: When the neural coding literature claims that a neuron "encodes" a stimulus property (orientation, sound location, faces), the proposition is far weaker than commonly implied. The "code" depends on the experimental design — what other stimulus dimensions are held fixed, what task the animal is doing, what context the recordings are in. Tuning curves are not context-free symbols. The "overwise neuron" fallacy (Crick 1979) treats single-unit selectivity as if it carried general information; in reality, it is sensitivity to a specific experimentally-controlled parameter, not "information about" that parameter in the world.
2. **Representation (Section 3)**: The coding metaphor implicitly invokes Shannon information — a correspondence between message and code that an external observer can decode. But Shannon information is *information by reference* to a known external message; the brain has only neural activity and no privileged access to "the message." The right form of information for an organism is not Shannon correspondence but the *structured relations among observables and actions* — Gibson's invariants, O'Regan & Noë's [[sensorimotor-contingencies|sensorimotor contingencies]], and Brette's own [[subjective-physics|subjective physics]] framework. The Martian iguana thought experiment makes this concrete.
3. **Causality (Section 4)**: The coding metaphor structures brain function as a linear chain (encoding → decoding → effector — "dominoes"). But the brain is a *circular dynamical system* coupled to the environment ("tent"). Coding variables are aggregate observables (firing probabilities, BOLD, trial-averaged spike counts) without causal powers; only spike events have them. The temporal abstraction inherent in coding — measuring activity over windows tied to experimental onsets — is incongruent with the millisecond, ongoing causal structure of cortical dynamics.

Brette's positive proposal is to abandon coding as the central organizing metaphor and embrace the brain as a coupled dynamical system whose fundamental computational primitives are *timed actions* (spikes) and *relational sensorimotor models*. Action potentials are *potentials that produce actions*, not symbols to be decoded.

For this wiki, Brette (2018) is uniquely load-bearing on the organizing principle. The wiki's thesis — that intelligence begins with closed-loop sensorimotor control — is essentially a constructive version of Brette's negative argument. Brette dismantles the coding view; the organizing principle is a candidate replacement.

[PDF](../../raw/papers/brette-2018.pdf)

## Key Findings

### The three senses of the coding metaphor

Brette draws on Lakoff & Johnson (1980) — metaphors are not neutral; they shape conceptual systems. Following Perkel & Bullock (1968), the neural coding metaphor carries three senses:

- **Correspondence** (technical): a statistical correspondence between a stimulus property (in the experimentally-controlled domain) and a coding variable extracted from neural activity (e.g., firing rate). Information theory (Shannon 1948) formalizes this.
- **Representation**: the neural code is a *message* about an external property, with the brain as *reader*.
- **Causality**: the encoded message has *causal powers* in the brain; downstream computations operate on the encoded representation.

Most technical results — tuning curves, decoding accuracies, mutual information measurements — establish only the first sense. But theories of brain function silently inherit the second and third senses, treating tuning curves and decoded signals as if they were symbols the brain manipulates. Brette's program is to show that this inheritance is unjustified — the technical sense does not entail either of the other two.

### Section 2: tuning curves don't license the inferences they're typically used for

**The cone wavelength example (Crick 1979 "fallacy of the overwise neuron")**: A cone responds to light with an amplitude that varies systematically with wavelength — so it "encodes wavelength" in the technical sense. But humans with single-cone retinas (or analogous animals) are color-blind. Why? Because the cone's response depends *also* on light intensity. The cone is sensitive to wavelength only when intensity is held fixed. In any natural setting where both vary, the cone does not in fact encode wavelength. Wavelength is encoded only by the *relative* activity of cones with different tunings (Fig. 2D). The "encodes wavelength" claim is a property of the experimental design (held-fixed intensity), not of the neuron.

**Generalization**: Tuning curve experiments establish that a neuron is *sensitive* to some stimulus parameter (responsiveness varies with the parameter when other things are held fixed). They do not establish that the neuron *carries information about* that parameter in any other context. The semantic drift from "sensitive to" to "carries information about" to "represents" is the load-bearing fallacy.

**Sound localization (ITD)**: Neurons in MSO and IC have ITD tuning curves with steep slopes around relevant ITD values ("slope coding," Harper & McAlpine 2004). A neuron's spike count carries information about ITD — but only conditional on knowing other parameters of the sound (frequency, intensity, level). With unknown sounds, the same spike count is consistent with very different ITDs. Heterogeneous tunings across the population resolve the ambiguity, but only by combining information across neurons — and this is fundamentally not what slope coding entails (Goodman & Brette 2010; Goodman et al. 2013).

**The ideal observer critique (Skottun 1998, Shackleton 2003)**: Studies that compare single-neuron sensitivity to behavioral discrimination and conclude "neurons are sufficient to support the behavior" use an *ideal observer*: a hypothetical decoder that knows the experimental design (what stimuli were presented, when, with what timing window) and reads neural activity accordingly. Such a decoder is "ideal" in that it makes maximally efficient use of the *experimenter's* information — including stimulus identity, presentation timing, and the choice of relevant time windows. But this is information the brain does not have. The conclusion that neural activity is "sufficient" therefore depends on an unjustified linking proposition (Teller 1984): that the brain reads the code the same way the experimenter does.

**Visual cortex tuning is task-dependent**: Hubel-Wiesel-style orientation selectivity in V1 has long been the canonical example of "encoding orientation." But V1 tuning depends on the surround (Bolz & Gilbert 1986), on what the animal is doing (Gilbert & Li 2013), on locomotion (Pakan et al. 2018), on prior auditory stimuli (Chanauria et al. 2018). A coding theory that treats orientation tuning as a context-free symbol is therefore systematically wrong about what V1 cells do across natural conditions.

### Section 3: codes are information by reference, but organisms need information by structure

**The setup**: The Bayesian brain hypothesis (Knill & Pouget 2004), predictive coding ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]), the [[free-energy-principle|free-energy principle]] (Friston 2009, [[friston-2010-free-energy-principle|Friston 2010]]), and information-theoretic accounts of efficient coding (Barlow 1961; [[natural-image-statistics|Olshausen & Field 1996]]) all assume that neural activity *represents* properties of the world — stimulus parameters, generative-model latent variables, "causes" of sensory inputs. The brain manipulates these representations to perform inference and guide behavior.

**The symbol grounding problem (Harnad 1990)**: How does the brain know what its neural activity refers to? Shannon information requires a *known external referent*: the value of a code is determined by the message it corresponds to. The experimenter has access to the message (they presented the stimulus). The brain does not.

**The efficient-coding paradox**: Suppose a neural population encodes sensory inputs as efficiently as possible (Barlow 1961; [[natural-image-statistics|Olshausen & Field 2004]]) — all redundancy removed. Then the encoded messages are *indistinguishable from random noise* without the decoding key, which only the input statistics provide. So a perfectly efficient code would be *unreadable* by any reader who only sees the code. The notion of information implied by efficient-coding theories is information by reference to the inputs — a kind of information accessible only to an external observer (the experimenter, or evolution). It is not the right kind of information for the organism.

**Brette's alternative: information as relational structure**. The right notion of information for an organism is the *invariant structure* of its sensory signals as a function of its actions — Gibson's (1986) ecological optics, O'Regan & Noë's (2001) [[sensorimotor-contingencies|sensorimotor account of vision]], Rosen's (1985) anticipatory systems, Maturana & Varela's autopoiesis. Information lives in *laws*: "if I do action A, then sensory property B happens"; "if sensory property B happens, then sensory property A also tends to happen." This is **information by structure**, not by reference. The wiki page [[subjective-physics]] develops this framework.

**The Martian iguana thought experiment** (adapted from Brette 2016, Dennett 1978):

- A blind iguana fixed in place hears sounds from a frog at varying distances. The two sounds at the iguana's ears obey a sensory law: `S_R(t) = S_L(t − Δ)`, where Δ is the interaural delay. The iguana can detect this lawful relation directly — it doesn't need to know what causes it. To an external observer Δ varies lawfully with the frog's position, but to the iguana, Δ is just an observable, not "the frog's location."
- Now allow the iguana to turn its head. It then observes that Δ varies lawfully with proprioceptive head position p: `S_R(t) = S_L(t − Δ_B(p))` for all p. **This relation is what defines the frog's position for the iguana** — not as an external property, but as a manipulation of an internal sensorimotor model. To predict what would happen if it turned its head a particular way, the iguana applies its model. "Localizing the sound" is computing a counterfactual within the sensorimotor model, not extracting a coding variable from the auditory periphery.

**Critique of predictive coding and the FEP** (Section 3.4): [[predictive-coding|Predictive coding]] proposes that neural activity encodes "internal variables that describe the external world" via a generative model that maps causes → observables. Brette's objection: a generative model is a *parametric description* of input statistics (like a Fourier transform), not a relational structure. The "causes" are coding variables; their semantics is fixed by the form of the generative model, not by anything the organism does. Calling these latents "causes" is a metaphorical extension of the strict-technical sense of cause (one event producing another), not the sense of "causes in the world that the organism interacts with." The same critique applies to the [[free-energy-principle|free-energy principle]] insofar as it inherits the generative-model framing.

**Critique of cell assemblies and engrams** (Section 3.5): Tonegawa-style memory engrams treat percepts as activations of cell-assembly subsets. But cell assemblies are unstructured "bags of neurons" — they cannot represent *relations* between objects. The visual scene "Paul, wearing a new shirt, drives a car" requires representing not only the assemblies for Paul, shirt, car, but the relations *wears* and *drives* with their argument structure. A subset of activated neurons cannot encode a labeled directed graph. This is the [[binding-problem|binding problem]] (von der Malsburg 1999) sharpened from a perceptual to a representational form.

Proposed solutions are partial:
- **Synchrony binding** (Singer 1999, von der Malsburg 1999): synchronously firing neurons share an object label. But synchrony is symmetric — it can mark *which features go together*, not *what relation they stand in*. "Paul drives car" and "car drives Paul" cannot be distinguished by synchrony alone.
- **Synchrony receptive fields** (Brette 2012): groups of neurons whose receptive fields produce equal output define a *synchrony receptive field* — the set of stimuli that elicit synchronous responses. This represents a sensory law (e.g., the Jeffress 1948 ITD model: synchrony marks `S_L(t) = S_R(t − d)`). Generalizes binding to lawful relations between observables.
- **Neural syntax** (Buzsáki 2010): the temporal sequence of activation could encode argument structure analogous to word order. Speculative.

### Section 4: coding's causal structure is incongruent with the brain's

**The dualistic structure of coding**: The coding metaphor partitions brain function into *encoding* (world → neural activity) and *decoding* (neural activity → behavior or further computation). These two components are causally independent — encoding can be studied without reference to behavior, and decoding can be modeled by an ideal observer that ignores the brain's mechanisms. Brette argues this dualism is structurally Cartesian: the encoded representation occupies the role Descartes assigned to mental content, and the decoder occupies the role of mind reading body.

**The Paramecium "swimming neuron"**: A unicellular organism uses voltage-gated calcium channels to spike when chemoreceptors detect concentration drops, triggering ciliary direction reversal (Eckert 1972). It performs chemotaxis. Two readings of the same system:
- *Coding view*: The cell encodes concentration in spikes; if it transmits chemical-environment information efficiently to "downstream" computation, evolution should tune coding to maximize Shannon information about concentration (efficient coding hypothesis).
- *Sensorimotor view*: The cell's firing implements a control law that, given the chemical environment and the cell's own actions, leads to food. The relevant tuning is to the *behavior of the loop*, not to the input statistics.

The two views make different empirical predictions about the cell's response properties. The coding view treats the cell as an encoder disconnected from its actions; the sensorimotor view treats encoding as inseparable from the behavior it produces. Real organisms behave according to the second view, but the field's analytical tools produce results consistent with the first.

**The heart example**: Cardiac excitable cells have firing rate that varies with running speed — they "encode" running speed in the technical sense. Standard rate-vs-timing analysis would conclude:
1. Firing rate is sensitive to the stimulus (running speed).
2. Cells fire regularly.
3. Spike timing is not reproducible across trials (the heart beats whenever it is ready).
4. Spike timing carries no additional information about the stimulus beyond the rate.

So a coding analysis would conclude *the heart uses a rate code*. Yet the temporal coordination of cardiac spikes — atria simultaneous, ventricles simultaneous, atria-then-ventricles — is *life-critical*. Synchrony within chambers and phase difference between chambers determines whether the pump works. The rate-coding analysis, applied to the heart, would correctly characterize the input-output sensitivity but completely miss the causal structure that matters for function. Brette argues this is exactly what happens when rate-coding analysis is applied to the brain.

**The dominoes vs. tent argument** (Fig. 10): Coding describes brain function as a linear chain of transformations, like falling dominoes — each step has a definite input and output, and time is a discrete sequence of code-to-code transitions. The brain's actual causal structure is more like a tent — a distributed, mutually-supporting network where every element is coupled to every other and to the environment. The two structures cannot be reconciled by adding stages to the chain; they are categorically different. Algorithmic descriptions (encode, transform, decode, output) have temporal structure that is internal to the algorithm, not the physical system. Dynamical systems, in general, cannot be mapped onto algorithmic descriptions (van Gelder 1995).

**Causal powers of coding variables**: Aggregate observables (firing rate averaged over a window, BOLD signal, trial-averaged spike counts) are not state variables of the brain's dynamical system. State variables are membrane potentials, ion-channel states, neurotransmitter concentrations. Spikes — being discrete events — have causal effect (they trigger synaptic release, postsynaptic potentials, downstream spikes), but they are not state variables either; they are *transitions* in the state space. The "neural code" reifies aggregates that are not part of the causal structure of the system that produces them.

A trial-averaged firing rate of a Jennifer Aniston cell (Quiroga et al. 2005) does not exist on any single trial — it is a property only of an ensemble of trials defined by the experimenter. Yet causal effects must be attributed to events that *actually occur*, not to averages over alternative trials that did not. A coding variable that requires trial-averaging to be defined cannot have causal powers in the brain. The same applies to coding variables defined by spatial averaging (population rates) or by long temporal windows that exceed the timescale at which downstream neurons influence each other.

### Positive proposal: models that behave

Brette's constructive view is that brain function should be modeled as full *sensorimotor systems* — "models that behave" (Gomez-Marin 2017). The unit of analysis is the closed loop: sensory transduction, neural dynamics, motor output, environmental feedback. The relevant theoretical objects are:

- **Sensory laws** (invariants in the sensory flow — see [[subjective-physics]])
- **Sensorimotor contingencies** (lawful covariation between actions and sensory consequences — see [[sensorimotor-contingencies]])
- **Internal models of relations** (rather than generative models of causes)
- **Spikes as timed actions** (not symbols)
- **Synchrony receptive fields** as a representational primitive that can carry relational structure (rather than firing-rate codes that cannot)

Action potentials are *potentials that produce actions*. They are events in time, with causal powers, that mediate coupling between dynamical units.

## Methods

This is a theoretical/philosophical paper rather than an experimental one. The argumentative methods are:

- **Conceptual analysis** of the metaphor (Lakoff & Johnson 1980): which sense of "coding" is established by which kind of empirical result, and which inferences are licensed.
- **Worked examples**: cone wavelength encoding (Section 2.1), MSO/IC ITD tuning (2.2–2.3.1), V1 visual coding (2.3.2), Jeffress model and synchrony receptive fields (3.5), Martian iguana sensorimotor inference (3.3), Paramecium chemotaxis (4.1), cardiac excitable cells (4.2), Jennifer Aniston cells and BOLD (4.3).
- **Reference to existing critiques**: Crick's "overwise neuron" fallacy (1979); Skinner via Chomsky (1959) on metaphoric extension of technical vocabulary; Cisek (1999) on the Cartesian heritage of computationalism; van Gelder (1995) on the dynamical hypothesis; Gomez-Marin (2017) on models that behave.
- **Critique of linking propositions** (Teller 1984): identifying the implicit assumption that the brain's relation to neural activity matches the experimenter's.

## Implications

### For the wiki's organizing principle

Brette (2018) is the most explicit philosophical articulation in the literature of the wiki's working thesis: *intelligence begins with closed-loop sensorimotor control, and learning, memory, and cognition are extensions of that control rather than separate symbolic faculties*. Where the wiki's thesis is constructive, Brette's argument is the corresponding negative claim — that the dominant alternative framework (neural coding) is incoherent as a basis for theories of brain function. The two halves are mutually supporting.

Specific commitments inherited:
- The substrate for intelligence is the closed sensorimotor loop, not a perceptual encoder feeding a cognitive symbol manipulator.
- Information for the organism is *relational structure among observables and actions* (Gibson, O'Regan-Noë, [[subjective-physics|subjective physics]]).
- Spikes are *timed actions*, not symbols. Action potentials produce actions.
- Cognitive functions (working memory, attention, planning) are extensions of the basic loop's reach (cf. [[memory-consolidation]], [[sparse-coding|sparse codes that extend latent-variable reach]], [[computation-through-dynamics|trained dynamics that extend control]]) rather than separate computations on stored representations.

### For specific frameworks in the wiki

**Compatible / sympathetic**:
- [[computation-through-dynamics|Computation Through Dynamics]] — Brette would be largely sympathetic. CTD treats neural populations as dynamical systems whose evolution *is* the computation, not as substrates for codes. The trained-RNN hypothesis-generator workflow is consistent with the systemic view. CTD's main residual coding-flavored move is the use of "task variables" as coding targets (e.g., line-attractor decisions integrating sensory evidence into a choice axis), which Brette would argue still over-attributes coding semantics to dynamical structure.
- [[self-supervised-behavior|self-supervised behavior]] / [[li-2024-prediction-noise-reward|Li et al. (2024)]] — fits Brette's frame: emergent goal-seeking from local dynamics + noise, no external reward signal, no encode/decode dualism.
- [[ethological-paradigms|Ethological paradigms]] / [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — directly aligned: trial-based 2AFC paradigms maximize the conditions under which coding analyses look most plausible (everything else held fixed); naturalistic paradigms expose context-dependence and behavioral degeneracy that coding cannot accommodate.
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]], [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — sympathetic: macroscopic dynamics conserved despite microscopic variation, computational scaffolds that capture branching/merging of trajectories rather than stimulus-coded variables.
- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — directly compatible with the heart example: the same anatomy implements different effective circuits depending on state; the "code" reified across states would miss the state-dependent reconfiguration.
- [[circuit-behavior-mapping|Circuit-behavior mapping]] — Brette deepens the umbrella: the mapping isn't just many-to-many, it's a closed loop with the environment.

**Critically engaged**:
- [[predictive-coding|Predictive coding]] (Rao-Ballard) — Brette explicitly critiques this as still-coding, with generative models as parametric input descriptions rather than relational structures. The kurtotic-prior simulation that recovers V1 receptive fields ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]) is technically valid but interpretively over-extended.
- [[free-energy-principle|Free energy principle]] / [[active-inference|active inference]] (Friston) — closer to Brette's view because action is in the loop, but Brette argues the FEP retains the generative-model framing and so inherits the symbol-grounding problem. The dark-room resolution via heritable phenotype-specific priors does not address the deeper issue that priors are still structured as causes-of-observables, not as relations-among-observables.
- [[helmholtz-machine|Helmholtz machine]] / [[analysis-by-synthesis|analysis-by-synthesis]] — direct ancestor of the framework Brette critiques. The wake-sleep separation enforces the encoder/decoder dualism Brette argues against.
- [[sparse-coding|Sparse coding]] / [[efficient-coding-hypothesis|efficient coding]] — efficient codes are unreadable (the efficient-coding paradox in Section 3.1); this is the cleanest explicit critique of efficient coding in the literature.
- Bayesian brain (Knill & Pouget 2004; Pouget et al. 2003; Jazayeri & Movshon 2006) — direct critique: context-free tuning curves are an artifact of experimental design.
- Ideal observers (Macmillan & Creelman 2005; Skottun 1998; Shackleton 2003) — critiqued via the linking-proposition argument (Teller 1984).
- Cell assembly / engram (Tonegawa et al. 2015) — bag-of-neurons can't represent relations.

### For the wiki's empirical commitments

The empirical evidence the wiki adduces for closed-loop sensorimotor control as foundational — [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis circuits that repurpose chemotaxis]], [[sussillo-abbott-2009-force-learning|FORCE learning]] that carves trained dynamics from chaotic substrates, [[francioni-2026-vectorized-dendritic-signals|in-vivo vectorized dendritic teaching signals]] — is largely compatible with Brette's framing. The dendritic credit-assignment lineage ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]] → Francioni 2026) is interestingly orthogonal: it is internally framed as a credit-assignment mechanism for hierarchical predictive coding, but its biological substrate (apical dendrites as gated signaling pathways) is consistent with a sensorimotor-control reading where the apical signal carries the residual mismatch between intended and observed sensorimotor consequences.

### Methodological prescriptions

- **Build "models that behave"** — full sensorimotor loops including sensors, neural dynamics, body, and environment. Models of perceptual subsystems disconnected from action are *chimaeras* (Brette's term): a neural model attached at one end to an artificial encoder (stimulus → neural activity), at the other end to an artificial decoder (neural activity → behavior). The disconnections from real sensors and real actions are where coding-style assumptions silently enter.
- **Constrain the model with neural recordings**, but don't make neural activity the *output* of the model. The output is behavior. Neural activity is a constraint on the model's internal state.
- **Treat spikes as timed events with causal powers**, not as samples of a continuous coding variable.
- **Stop comparing single-neuron activity to behavior via ideal observers**. The comparison requires a linking proposition that has never been justified.

### What changes for theory-building

Brette's view does not preclude using information-theoretic tools — they remain valid as statistical analyses of observed correspondences. What he denies is that those correspondences support claims about *what the brain represents*. A complete theory of brain function will use information theory in the same role that astronomy uses spectroscopy: as a measurement tool, not as the framework for theory.

For wiki entries that use coding language ("place cells encode location," "V1 encodes orientation," "PFC encodes the categorization rule"), Brette's argument suggests reading these as *correspondence claims with experimental scope* — that under the conditions of the experiment, neural activity statistically corresponds to the named variable — without inheriting the representational and causal entailments. The dendritic credit-assignment lineage's "predictive coding as credit assignment" reading similarly survives Brette's critique as a *mechanistic* description of plasticity, even if its representational interpretation is contested.

## Connections to Existing Knowledge

- [[neural-coding|Neural Coding]] — the umbrella concept Brette critiques. The page captures both the framework and the major critiques (this paper foremost).
- [[subjective-physics|Subjective Physics]] — Brette's positive alternative. Information as relations among observables and actions; sensory laws as the units of organism-internal physics.
- [[sensorimotor-contingencies|Sensorimotor Contingencies]] — O'Regan & Noë (2001), the antecedent framework Brette draws on. Vision as the practical mastery of sensorimotor laws, not the construction of an internal picture.
- [[binding-problem|Binding Problem]] — von der Malsburg, Singer, Brette. Why cell assemblies cannot represent relational structure; the synchrony solutions and their limits.
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — the methodological-philosophical companion. Jonas-Kording: standard analyses don't recover Marr-level understanding even with ground truth. Brette: even when those analyses converge cleanly, the metaphor that gives them representational meaning is incoherent. Together they form a two-front critique: methods don't work, and even if they did, the framework that interprets them is wrong.
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — the constructive third leg of the methodological-philosophical triad. Brette: the coding framework that interprets parameters is incoherent. Jonas-Kording: standard methods do not recover Marr-level understanding from parameters. Lillicrap-Kording: parameters are not communicable in any short formal language because the world they encode is incompressible — so neuroscience should target the *recipe* (architecture, plasticity, developmental program) rather than the trained parameters. Brette's continuous-time-dynamical-systems framing of the algorithmic level is compatible: the dynamics are part of the recipe, not part of the parameters. See [[principles-vs-parameters|principles-vs-parameters]] for the integrated frame.
- [[predictive-coding|Predictive Coding]], [[active-inference|Active Inference]], [[free-energy-principle|Free Energy Principle]], [[helmholtz-machine|Helmholtz Machine]], [[analysis-by-synthesis|Analysis-by-Synthesis]] — the main targets of the representational critique.
- [[sparse-coding|Sparse Coding]], [[efficient-coding-hypothesis|Efficient Coding Hypothesis]] — the targets of the efficient-coding paradox.
- [[computation-through-dynamics|Computation Through Dynamics]] — sympathetic, treats populations as dynamical systems rather than codes.
- [[ethological-paradigms|Ethological Paradigms]] — Brette's critique of trial-based-paradigms-as-coding-experiments aligns with the wiki's ethological thread.
- [[self-supervised-behavior|Self-Supervised Behavior]] — emergent goal-seeking without external reward signals fits Brette's frame.
- [[circuit-behavior-mapping|Circuit-Behavior Mapping]] — Brette deepens the many-to-many mapping into a closed loop with the environment.
- [[place-cells|Place Cells]], [[hippocampus|Hippocampus]], [[motor-cortex|Motor Cortex]], [[prefrontal-cortex|Prefrontal Cortex]] — phenomena typically described in coding terms; Brette's view recontextualizes them as components of sensorimotor loops.

## Open Questions Raised

- **What does a "model that behaves" look like, concretely, for a cortical region?** Brette's prescription is principled but not algorithmic. The endotaxis circuit ([[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. 2024]]) is one example of a sensorimotor-loop model that includes the controller (chemotaxis), the internal signal generator (map cells, goal cells), and the action module. What does the analogous specification look like for vision? Audition? Decision-making? The literature has plenty of "encoder" and "decoder" submodels but few full closed loops at cortical scale.
- **Can synchrony receptive fields scale to structured representations?** Brette's earlier work (Brette 2012; Laudanski 2014; Goodman & Brette 2010) develops synchrony receptive fields as a representational primitive that captures sensory laws (e.g., Jeffress ITD model, pitch perception). But synchrony is a symmetric relation, so it cannot represent directed relations like "Paul drives car." Whether richer temporal structures (sequences, polychrony) can carry directed relational content remains open.
- **How does Brette's view interact with the dendritic credit-assignment lineage?** The dendritic lineage ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) explicitly frames apical-dendrite signals as *credit signals* in a hierarchical predictive-coding framework. A sensorimotor reading would interpret the same biology as a mechanism for routing residual sensorimotor mismatch into local plasticity, *without* the predictive-coding semantic commitments. The mechanism survives reinterpretation but the framing changes substantially. Whether the two readings make distinguishable empirical predictions is unclear.
- **What is the role of generative models in a sensorimotor framework?** Brette argues generative models map causes to observables, not relations among observables. But generative models are extraordinarily useful in machine learning and cognitive science. Is there a sensorimotor-friendly reformulation in which generative models are tools for *predicting consequences of actions* rather than for *inferring causes of inputs*? The distinction matters: in the first case, the generative model is part of the controller; in the second, it is a separable perceptual encoder.
- **Where do attractor dynamics and CTD-style trained motifs fit?** Brette explicitly endorses the dynamical-systems view but is silent on attractor structure as such. CTD-style trained dynamics in motor cortex (rotations, line attractors, output-null preparation) are dynamical-systems-flavored explanations that nonetheless use task-variable coding language. The reconciliation is presumably that the *dynamics* are real but the *coding* descriptions are scaffolding, not load-bearing — but this needs to be made explicit.
- **How should learning be theorized within the sensorimotor framework?** Hebbian plasticity is straightforwardly compatible — local rules that strengthen co-activated synapses are fully sensorimotor. Hierarchical credit assignment is more contested: the supervised-learning reading of hierarchical learning ([[payeur-2020-burst-dependent-credit-assignment|Payeur 2020]], [[greedy-2022-single-phase-burstccn|Greedy 2022]]) needs an external target signal. A sensorimotor reading would derive the target from sensorimotor mismatch (intended vs. observed action consequences), but the algorithmic specification is open.

## Sources

- Brette, R. (2018). Is coding a relevant metaphor for the brain? *bioRxiv* preprint 168237 (July 2018 version). DOI: [10.1101/168237](https://doi.org/10.1101/168237). Subsequently published with revisions in *Behavioral and Brain Sciences* 42:e215 (2019).
- Antecedent works: Brette (2010, 2012, 2015, 2016) on auditory coding, computing with neural synchrony, philosophy of the spike, and subjective physics.
- Foundational references for the alternative framework: Gibson (1986); O'Regan & Noë (2001); Maturana & Varela; Rosen (1985); Chomsky (1959); Lakoff & Johnson (1980); van Gelder (1995); Gomez-Marin (2017).
- Targets of critique: Perkel & Bullock (1968); Barlow (1961); Olshausen & Field (2004); Knill & Pouget (2004); Pouget et al. (2003); Jazayeri & Movshon (2006); Friston (2009, 2010); Rao & Ballard (1999); Tonegawa et al. (2015); Skottun (1998); Shackleton et al. (2003); Harper & McAlpine (2004); Quiroga et al. (2005).
