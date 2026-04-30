---
title: "Subjective Physics"
type: concept
aliases: ["sensory laws", "organism-internal physics", "internal model of relations", "Brette's subjective physics"]
tags: [sensorimotor, perception, internal-model, ecological-psychology, gibson, philosophy-of-neuroscience, alternative-to-coding]
source_count: 1
last_updated: 2026-04-29
confidence: emerging
---

**Subjective physics** is [[romain-brette|Brette]]'s framework for the kind of information actually relevant to a living organism. The proposal: information for an organism is not Shannon correspondence to known external messages — it is the *invariant structure of relations among its sensor signals and its actions*. The organism builds an internal model of these lawful relations; the model is what perception and action operate on. Introduced in Brette (2016) and developed in [[brette-2018-coding-metaphor|Brette (2018)]].

The framework is a positive alternative to the [[neural-coding|neural coding]] metaphor. Where coding treats neural activity as *messages about the world* that the brain *decodes*, subjective physics treats neural activity as *participants in lawful relations* among observables that the organism can manipulate via action.

## Core proposal

Information, for an organism, has the form of a *law*:

```
if action A, then observable B
if observable A, then observable B follows
if action A in context B, then observable C
```

Such laws are **observable from inside the organism** — the organism can detect that, whenever it performs action A, observable B occurs. No external referent is required. The organism does not need to know what *causes* the law (an external state of the world); it only needs to know that the law holds. Brette calls this **information by structure**, in contrast to Shannon's **information by reference**.

This addresses the **symbol grounding problem** (Harnad 1990) for neural representations. Coding-style theories assume that neural activity refers to external properties (orientation, location, cause), but offer no account of how the brain *knows* what its activity refers to. Subjective physics resolves the problem by holding that nothing in the organism refers to anything external; what's internal are the relations themselves, which the organism can verify through its own actions and observations.

## Antecedents

- **Gibson's ecological optics** (1986). Perception extracts *invariants* from the optic flow — properties of the sensory array that remain stable under changes of viewpoint, lighting, motion. Gibson's invariants are exactly the sensory laws Brette formalizes.
- **O'Regan & Noë's [[sensorimotor-contingencies|sensorimotor contingencies]]** (2001). Vision is the practical mastery of how visual sensations covary with eye, head, and body movement. The "feel" of red is the lawful pattern of how that sensory quality changes as you move. Subjective physics extends this from vision to every modality and from contingencies to a more general algebra of sensory laws.
- **Rosen's anticipatory systems** (1985). Biological organisms contain internal models of the world that allow them to anticipate states. Rosen specifies the model in terms of relations between observables (rather than mappings from latent causes to observables), which is exactly Brette's proposal.
- **Maturana & Varela autopoiesis** — biological cognition is the self-organization of an organism's own sensor-effector loop. Subjective physics fits this conception of cognition as inherently organism-defined rather than world-correspondent.
- **Powers' Perceptual Control Theory** (1973) and Ahissar & Assa's "perception as closed-loop convergence" (2016) — perception as the operation of a control loop on sensory variables, with the variables themselves defined by their role in the loop.

## The Martian iguana

Brette's canonical example (adapted from Dennett 1978):

A blind iguana sits in a fixed position. A frog produces sounds at varying distances. The two sounds at the iguana's ears obey a sensory law:

```
S_R(t) = S_L(t − Δ)   for all t
```

where Δ is the (unknown to the iguana) interaural time difference. The iguana can detect this lawful relation directly from its sensory signals — it does not need to know that Δ corresponds to the frog's position. To an external observer, Δ varies lawfully with position; to the iguana, Δ is just an observable.

So far the iguana cannot *localize* the sound. The lawful relation is intrinsic to the sensory flow but does not connect to anything the iguana can do.

Now allow the iguana to turn its head, and let p be the proprioceptive signal indicating head position. The iguana then observes a richer law:

```
S_R(t) = S_L(t − Δ_B(p))   for all t and p
```

That is: the interaural delay depends on head position in a specific lawful way. **This relation defines what the frog's position is for the iguana.** Not as an external property the iguana represents, but as an *internal manipulation*: to predict what would happen if it turned its head, the iguana applies its sensorimotor model. To "localize the sound" means to compute a counterfactual within the model — not to extract a coded variable from the auditory periphery.

The iguana's *spatial perception* lives in the manipulability of the lawful relation, not in any individual neural response.

## Distinct from generative models

Brette explicitly contrasts subjective physics with generative models in [[predictive-coding|predictive coding]] and the [[free-energy-principle|free-energy principle]].

A **generative model** maps internal latent variables to observables: `Y = f(X) + noise`, where X is a hidden cause and Y is the observation. Inference inverts the mapping. Examples: Olshausen-Field sparse coding (X = sparse latents, Y = image); Rao-Ballard predictive coding (X = top-down latents, Y = bottom-up sensory inputs); Helmholtz machine (X = generative latents, Y = data).

A **subjective-physics model** describes lawful relations among observables (and actions): `B = f(A, action_state)`, where A and B are both directly observable. There are no hidden causes; the model is *over* the sensory + action manifold itself.

The difference matters:
- Generative models are *parametric descriptions* of input statistics — useful as compression devices but unhelpful for organisms because the latents lack grounded meaning. (A Fourier transform "encodes" an image, but the Fourier coefficients do not refer to anything the organism does.)
- Subjective-physics models are *manipulable* — by selecting an action, the organism predicts the consequent observable. The model is part of a controller, not a perceptual encoder.

This is also where Brette parts ways with the [[active-inference|active inference]] reading of action. Active inference incorporates action into the FEP framework but retains the generative-model framing: action is selected to fulfill predictions of preferred sensory states. Brette would argue this still treats actions as constraints on a generative model, not as primitives that define the lawful structure of subjective physics.

## Implementation hints

Brette is largely silent on neural implementation, but the [[binding-problem|synchrony receptive field]] framework (Brette 2012; Laudanski 2014; Goodman & Brette 2010) is the closest existing proposal. A group of neurons whose receptive fields produce equal output for some set of stimuli defines a *synchrony receptive field* — the set of stimuli that elicit synchronous responses. Synchrony in this group then **directly indicates** that a sensory law holds (e.g., `S_L(t) = S_R(t − d)` for the Jeffress 1948 ITD model).

The representational primitive is therefore *not* the firing rate of a neuron tuned to a stimulus parameter, but the *synchronous coactivation of a group of neurons* that marks the holding of a sensory law. This is closer to a logical or relational primitive than to a coded value. See [[binding-problem]] for the limits of synchrony as a representational substrate (it is symmetric, so cannot directly encode directed relations).

## Relation to the wiki's organizing principle

Subjective physics is the most explicit positive articulation in the literature of the framework the wiki has adopted as its organizing principle. The thesis "intelligence begins with closed-loop sensorimotor control" plus subjective physics gives:

- **Information** for the organism = lawful relations among sensors and actions
- **Perception** = practical mastery of those laws (sensorimotor contingencies)
- **Action selection** = manipulation of the internal sensorimotor model to predict counterfactual consequences
- **Learning** = updating the laws as experience reveals new structure
- **Memory** = persistence of learned laws across time
- **Cognition** = extension of the model over longer timescales, more variables, more counterfactual worlds

The architecture that produces this — neurons tuned by genes, feedback control implemented in dendrites, manifolds and attractors that constrain dynamics, dopaminergic and other neuromodulators that bias plasticity — is the substrate the rest of the wiki catalogs.

## Open questions

- **Concrete instantiation in cortex.** Subjective physics specifies what *kind* of model the brain has but is largely silent on how it is implemented in cortical microcircuits. Synchrony receptive fields are a candidate primitive but only for symmetric (equality-flavored) relations. What carries directed and structured relations remains open.
- **Compatibility with hierarchical credit assignment.** The dendritic credit-assignment lineage ([[credit-assignment]]) is internally framed in supervised-learning / predictive-coding terms. A subjective-physics reading would derive the apical-dendrite teaching signal from sensorimotor mismatch (predicted vs. observed consequences of action), but the formal mapping has not been worked out.
- **Generative models as tools vs. as organism-internal representations.** Generative models are extraordinarily useful machinery in machine learning. The question is whether the brain *uses* them as inverse-inference tools (as predictive coding claims) or whether the brain only manipulates lawful relations. Whether these views make distinguishable empirical predictions is unclear.
- **Scaling.** The Martian iguana example involves three observables (S_L, S_R, p). Real perception involves many more, and many of the relations are higher-order (depend on combinations of variables). Whether subjective physics can carry over to high-dimensional sensorimotor manifolds without re-introducing coding-style intermediate representations is open.

## Sources

- [[brette-2018-coding-metaphor|Brette (2018)]] — develops subjective physics as the positive alternative to coding; introduces the Martian iguana example; argues it resolves the symbol grounding problem and provides the form of information actually relevant to organisms.
- Brette, R. (2016). Subjective Physics. In *Closed Loop Neuroscience* (El Hady, A., ed.), pp. 146–170. Academic Press. The original chapter-length statement of the framework, referenced in the 2018 paper.
