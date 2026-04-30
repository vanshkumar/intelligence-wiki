---
title: "Sensorimotor Contingencies"
type: theory
aliases: ["sensorimotor account", "O'Regan-Noë theory", "enactive perception", "sensorimotor knowledge"]
tags: [perception, sensorimotor, action, ecological-psychology, enactivism, philosophy-of-mind, alternative-to-representationalism]
source_count: 1
last_updated: 2026-04-29
status: emerging
---

**Sensorimotor contingencies (SMCs)** are the lawful patterns of how sensory inputs change as a function of the perceiver's actions. The framework — articulated by O'Regan & Noë (2001) in "A Sensorimotor Account of Vision and Visual Consciousness" — proposes that perception is not the construction of an internal picture of the world but the *practical mastery of these contingencies*. To see is to know how visual sensations would change if you moved your eyes, head, or body in particular ways; to feel is to know how tactile sensations would change with hand movements; and so on.

Cited extensively in [[brette-2018-coding-metaphor|Brette (2018)]] as a foundational precursor for [[subjective-physics|subjective physics]] and as a key alternative to the representationalist framing of perception.

## The core claim

Perception is not a process of *building an internal model* from sensory signals; it is *engaging with sensorimotor contingencies* — knowing what the world will do in response to one's actions, and what the sensory consequences of one's actions will be. Vision is a kind of *bodily skill*, more like riding a bicycle than like reading a description.

Concrete examples:
- The "feel" of red is not a property of an internal red-token; it is the lawful pattern of how red-related sensations covary with eye movements over a red surface, with light changes, with surface curvature, with surrounding colors.
- The 3D shape of a cube is not constructed by inverting an image of the cube; it is the practical knowledge of how the visual array changes when you move around the cube.
- The persistence of an object behind an occluder is not an internal representation of "object continues to exist"; it is the contingency that head movements that look behind the occluder will reveal the object.

## Distinctive features

### No internal picture

The classical computational view of vision (Marr 1982; Bayesian brain) takes the goal of vision to be the construction of a 3D internal model from 2D retinal images. SMC denies this: there is no need for an internal picture, because the brain has access to the world through the practical loop of looking, moving, and updating. The "where" of an object is not represented in the brain; it is implicit in the contingency of how to look at it.

### Perception as embodied skill

SMC is part of the **enactivist** tradition (Varela, Thompson & Rosch 1991; Noë 2004; Thompson 2007). Perception is something the organism *does*, not something that *happens to* the organism. The body and the environment are not just inputs to a perceiving brain — they are part of the perceiving system.

### Modal differences as different contingency structures

SMC offers a distinctive answer to why different sensory modalities have different qualitative characters. Vision differs from touch differs from hearing because the *kinds of laws* that govern each modality's sensorimotor contingencies are different. Vision: as you move your eyes, parts of the visual field shift in laterally-coupled ways; the contingencies have a 2D-projection-from-3D-world structure. Touch: as you move your finger, sensations change with surface curvature and friction in different ways; the contingencies have a contact-mechanics structure. The *content* of perception is the structure of the contingencies, not a code over an abstract feature space.

## Relation to subjective physics

[[subjective-physics|Subjective physics]] (Brette 2016, 2018) generalizes and formalizes the SMC framework. Where O'Regan & Noë describe sensorimotor contingencies in qualitative phenomenological terms, Brette's subjective physics specifies them as *lawful relations among observables and action variables* — written explicitly as equations like `S_R(t) = S_L(t − Δ_B(p))` for the Martian iguana auditory case.

The two frameworks are mutually consistent and reinforcing:
- SMC is the phenomenological / cognitive-science formulation, focused on the experience of perceiving.
- Subjective physics is the mathematical / computational formulation, focused on the structure of organism-internal information.

## Relation to predictive coding and active inference

[[predictive-coding|Predictive coding]] and [[active-inference|active inference]] partly overlap with SMC — both treat perception as a kind of inference involving action — but Brette argues they remain in the coding frame:

- Predictive coding posits a generative model that maps internal latent variables to sensory observables. SMC denies that the latent variables are the right unit of analysis; the contingencies (relations among observables and actions) are.
- Active inference incorporates action but retains the generative-model framing: actions are selected to fulfill predicted sensory states. SMC takes actions to *define* the structure of perception, not to be tools for fulfilling predictions.

The dark-room problem ([[dark-room-problem]]) is a clean test case. Predictive coding faces the problem: if the brain minimizes prediction error, why doesn't it seek dark, predictable rooms? FEP resolves it via heritable phenotype-specific priors (the body has priors for being out exploring). SMC dissolves it: the question presupposes that perception is about minimizing some quantity *over* representations, but perception is not over representations; it is the engagement with sensorimotor contingencies. There is nothing to minimize.

## Relation to the wiki's organizing principle

SMC is one of the strongest pre-existing articulations of the wiki's organizing principle that intelligence begins with closed-loop sensorimotor control. The connection:

- The closed sensorimotor loop is the substrate; SMC says this is also the *content* of perception, not just its substrate.
- Memory and learning extend the contingencies into longer time horizons (knowing how my action will affect things tomorrow, not just now).
- Cognition extends contingencies to counterfactual worlds (knowing how my action would affect things if a different state held).
- Genes constrain neurons' nonlinear feedback control algorithms ([[degeneracy|degeneracy]]); SMC says these algorithms are exactly the substrate of perceptual contingencies.

The wiki's closed-loop framing is essentially SMC scaled up by other mechanisms (consolidation, sparse coding, dendritic credit assignment, etc.) without ever leaving the SMC frame.

## Critiques and limitations

- **Concrete neural implementation is underspecified.** SMC is stated at the cognitive-science level. Translating to neuroscience requires committing to specific representational primitives (synchrony receptive fields? attractor dynamics? generative models that operate on actions rather than causes?). Brette's [[subjective-physics|subjective physics]] is a step toward this but does not specify implementation.
- **Higher-level cognition (language, mathematics, mental simulation) is harder to fit.** SMC works well for embodied perception but the extension to abstract reasoning is open.
- **The framework is sometimes accused of "being non-explanatory"** because it deflates representational claims without offering a competing computational specification. Defenders respond that this is a feature: not all explanation is computational, and the SMC framework explicitly aims to redirect explanation toward embodied skill rather than internal computation.

## Sources

- [[brette-2018-coding-metaphor|Brette (2018)]] — cites O'Regan & Noë (2001) extensively as a foundational reference for the alternative to neural coding; explicitly names sensorimotor contingencies as the kind of information relevant to organisms.
- O'Regan, J. K. & Noë, A. (2001). A sensorimotor account of vision and visual consciousness. *Behavioral and Brain Sciences* 24:939–973. The founding paper.
- Noë, A. (2004). *Action in Perception*. MIT Press. Book-length development.
- Related work in the enactivist tradition: Varela, Thompson & Rosch (1991) *The Embodied Mind*; Thompson (2007) *Mind in Life*; Hutto & Myin (2013) *Radicalizing Enactivism*.
