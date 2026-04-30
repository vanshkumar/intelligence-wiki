---
title: "Binding Problem"
type: concept
aliases: ["binding", "feature binding", "structure problem", "relational binding", "von der Malsburg's binding problem"]
tags: [representation, perception, cell-assembly, synchrony, structured-representation, philosophy-of-neuroscience]
source_count: 1
last_updated: 2026-04-29
confidence: contested
---

The **binding problem** is the question of how the brain represents the *relations* between features that belong to the same object, and between objects that stand in particular relations to each other. The problem is structured in (at least) two layers:

1. **Feature binding**: how do features belonging to the same object (red, round, moving leftward, in the upper-right) get associated? (von der Malsburg 1981, 1999.)
2. **Relational binding**: how does the brain represent that *Paul drives the car* — including the directed relation *drives*, with Paul as the agent and the car as the patient? (Brette 2018; classical structured-representation arguments in cognitive science.)

Layer 1 is the classical formulation and has multiple proposed solutions. Layer 2 is sharpened by [[brette-2018-coding-metaphor|Brette (2018)]] and is much harder; existing solutions are incomplete or speculative.

## Layer 1: Feature binding

### The problem

In hierarchical feature-detection models of cortex (Hubel & Wiesel, Riesenhuber & Poggio, deep CNNs), features are represented by the activity of feature-tuned neurons. A scene with multiple objects activates many feature detectors simultaneously. How does the brain know which features belong to which object?

The naïve answer — "the active features all belong to one combined object" — fails when there are multiple objects. If scene A contains a red square and a blue circle, and scene B contains a red circle and a blue square, the same set of feature detectors is active in both cases. The activity pattern alone does not specify the bindings.

This is sometimes called the **superposition catastrophe** (von der Malsburg 1999): if multiple objects' feature representations are simultaneously active, they fuse into an unparseable combined representation.

### Proposed solutions

**Synchrony binding** (Singer 1999; von der Malsburg 1999). Features belonging to the same object fire synchronously; features belonging to different objects fire asynchronously. Synchrony is detected by temporal coincidence at downstream coincidence detectors (e.g., thresholded summation over short windows).

- Empirical support: gamma-band synchronization correlates with attention and grouping (Gray & Singer 1989; Engel & Singer 2001). Selective synchronization in auditory binding (Lakatos et al. 2008).
- Critique (Merker 2013, Shadlen & Movshon 1999): synchrony's causal role is contested. Whether downstream readers can reliably extract the synchrony signal is unclear; whether synchrony's correlation with grouping is constitutive or epiphenomenal is unclear.

**Retinotopic-position-as-label** (Kawato 1997). Feature neurons encode not just the feature but the conjunction of feature × retinotopic position. Two simultaneous objects at different positions are then represented by activity patterns that don't superpose. This solves the catastrophe by making position part of the feature code.

- Limitation: works only for retinotopic features; doesn't generalize to abstract or amodal features.

**Attention-based binding** (Treisman 1996). A spotlight of attention sequentially binds features at one location at a time. Binding is achieved by *temporal sequencing of attention*, not by simultaneous neural mechanisms.

- Limitation: serializes binding; doesn't fit the apparent parallelism of perception in cluttered scenes.

**Ricci, Kim & Serre (2018)**: connectionist models designed to detect simple relations between shapes (e.g., same-vs-different) systematically fail when not specifically trained on the relation. This is empirical evidence that feature-detector architectures alone don't solve binding.

## Layer 2: Relational binding

[[brette-2018-coding-metaphor|Brette (2018)]] sharpens the problem in a way that exposes deeper limitations. Even if feature binding is solved, the resulting [[neural-coding|cell assembly]] (the union of feature-bound subassemblies) does not represent **directed relations** between objects.

### The Paul-drives-car example

Consider the visual scene: "Paul is wearing a new shirt, driving a car." A complete representation must include:
- The assembly for Paul.
- The assembly for the shirt.
- The assembly for the car.
- The relation *wears*, with Paul as subject and shirt as object.
- The relation *drives*, with Paul as subject and car as object.

A cell-assembly representation — the union of all activated assemblies — is a *bag of neurons*. It lacks the structural ingredients (labels on edges, argument-position information, directed connections between nodes) needed to encode "Paul drives the car" rather than "the car drives Paul."

Mathematically: a cell assembly is a *subset of neurons*, isomorphic to an unstructured set or a bag. A relational scene is a *labeled directed graph*. The mapping from one to the other is not a recoverable embedding.

### Why synchrony doesn't fix this

Synchrony is symmetric. If neurons A, B fire synchronously, the relation encoded is "A and B go together" — there is no inherent asymmetry to mark "A is the subject and B is the object." For symmetric relations (parallel-to, equal-to, simultaneously-with) synchrony works. For directed relations (drives, hits, contains) it does not.

This is the residual binding problem after the simpler form is solved. Even if synchrony solves feature binding (an open question), it does not solve relational binding.

### Synchrony receptive fields

Brette's own [[subjective-physics|subjective physics]] line of work proposes [[subjective-physics|synchrony receptive fields]] (Brette 2012; Laudanski 2014; Goodman & Brette 2010) as a more powerful primitive: a group of neurons whose receptive fields produce equal output for some set of stimuli defines the *synchrony receptive field* — the set of stimuli that elicit synchronous responses. This generalizes binding to *the holding of a sensory law*: synchrony marks `S_L(t) = S_R(t − d)` (Jeffress 1948 ITD model) or `f(N_A(S)) = f(N_B(S))` for arbitrary feature relations.

Synchrony receptive fields can carry sensory laws — invariant relational structure — which is an advance over simple cell-assembly bag-of-neurons representations. But they remain symmetric (synchrony is a symmetric relation), so they cannot directly carry directed relational content. A separate mechanism is needed for directed relations.

### Neural syntax (Buzsáki 2010)

A speculative proposal: the *temporal sequence of activation* of cell assemblies could encode argument structure analogously to word order in sentences. "Paul drives car" would correspond to assembly sequence *Paul → drives → car* (sequenced in time within a relevant time window like a theta cycle). This would require:
- Reliable temporal ordering of assembly activation
- Downstream readers that interpret order as relational structure
- Mechanisms for embedded structure (parentheses, recursion)

The proposal is conceptually clean but lacks specific empirical support beyond suggestive observations of replay-like sequences in hippocampus. Whether neural syntax can carry the kind of structured representations cognitive scientists argue for remains open.

## Status in this wiki

Brette's relational-binding sharpening of the problem is a key challenge for several frameworks the wiki tracks:

- **[[neural-coding|Neural coding]]** in its standard form (rate codes, population codes, decoders) provides no mechanism for relational binding. This is one of Brette's load-bearing critiques.
- **[[helmholtz-machine|Helmholtz machine]]** and other generative-model frameworks can in principle encode relational structure in their latent variables, but typically don't — most VAE-style implementations represent scenes as flat feature vectors.
- **[[predictive-coding|Predictive coding]]** in its hierarchical form encodes scene structure in higher-level latent activations, but again, the typical implementation is flat.
- **[[subjective-physics|Subjective physics]]** offers a partial solution via synchrony receptive fields for symmetric relations but does not address directed relations.
- **[[hopfield-network|Hopfield networks]]** and other [[content-addressable-memory|attractor memories]] are subject to the bag-of-neurons critique exactly: stored memories are subsets of neurons, not labeled graphs.
- **[[place-cells|Place cells]] and [[cognitive-map|cognitive maps]]** face the relational version: a cognitive map of a maze is not just a set of place activations but a labeled graph (this junction connects to that one in this direction). The [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis circuit]] partially addresses this with adjacency-matrix learning in map-cell connections.

## Open questions

- **What is the right primitive for directed relational structure?** Synchrony works for symmetric, neural syntax is speculative. Tensor-product representations (Smolensky 1990) and complex-valued neural networks (Plate 1995) are computationally adequate but lack neural plausibility.
- **Does the brain solve this problem at all?** Some authors (e.g., Edelman 1987) argue the binding problem is a pseudo-problem, an artifact of the localist representation assumption. Distributed representations with population coding may suffice if we don't require localist binding.
- **How do hierarchical predictive-coding latents handle relational structure?** A scene-level latent could in principle code "Paul drives car" as a single high-level category, but this requires the scene's relational structure to be in the *training distribution* of the generative model. Generalization to novel relational compositions is the open problem.
- **What does the binding problem look like in sensorimotor framing?** [[sensorimotor-contingencies|SMC]] suggests perception is engagement with sensorimotor contingencies, not assembly of internal representations. In this framing, the question becomes: what makes the contingency "Paul drives car" different from "car drives Paul"? Probably the answer involves the action-affordance structure differing — but this needs to be made explicit.

## Sources

- [[brette-2018-coding-metaphor|Brette (2018)]] — sharpens the binding problem from feature binding to relational binding (the Paul-drives-car example); critiques cell-assembly representations as bag-of-neurons; reviews synchrony binding, retinotopic-label binding, and synchrony receptive fields; flags neural syntax as a speculative direction.
- von der Malsburg, C. (1999). The what and why of binding: the modeler's perspective. *Neuron* 24:95–104.
- Singer, W. (1999). Neuronal synchrony: a versatile code for the definition of relations? *Neuron* 24:49–65.
- Treisman, A. (1996). The binding problem. *Curr. Opin. Neurobiol.* 6:171–178.
- Kawato, M. (1997). Bidirectional Theory Approach to Consciousness. In *Cognition, Computation, and Consciousness*. Oxford University Press.
- Buzsáki, G. (2010). Neural syntax: cell assemblies, synapsembles, and readers. *Neuron* 68:362–385.
- Ricci, M., Kim, J. & Serre, T. (2018). Same-different problems strain convolutional neural networks. arXiv:1802.03390.
