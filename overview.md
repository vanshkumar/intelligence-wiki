# Overview

This wiki explores a central question in neuroscience: **how does the brain learn?**

The scope spans the biological mechanisms that allow nervous systems to acquire, store, and retrieve information — from molecular events at individual synapses to large-scale circuit dynamics that support cognition. Key areas include:

- **Synaptic plasticity** — the molecular and cellular mechanisms by which connections between neurons strengthen or weaken
- **Memory systems** — how different types of memory (working, episodic, procedural, semantic) are formed, consolidated, and retrieved
- **Neural circuits** — how interconnected brain regions coordinate to support learning
- **Development** — how the brain's learning capacity emerges, including critical periods, pruning, and neurogenesis
- **Cognitive processes** — attention, metacognition, transfer, and abstraction as they relate to learning

---

## Emerging Themes

### Local rules can produce emergent reward-seeking

[[li-2024-prediction-noise-reward|Li et al. (2024)]] demonstrates that two simple ingredients — local [[Predictive Coding|predictive updates]] and [[Neural Noise|internal noise]] — are sufficient for neural networks to exhibit flexible reward-seeking behavior. Networks autonomously explore and exploit, adapt to environmental changes, and form task preferences, all without an external reward function. The mechanism relies on [[Attractor Dynamics]]: rewarding states are stable attractors under noise, while unrewarding states are unstable.

This has implications for understanding what evolution invested in. If basic reward-seeking is "free" once neurons do local prediction and have intrinsic noise (biophysically unavoidable), then evolution's investment was not in inventing goal-directed behavior but in machinery to **shape and control** it — steering subsystems, neuromodulation, specialized architectures. The role of dopamine may be more subtle than standard RL assumes: not defining what's rewarding, but biasing *which* emergent goals get preferred through learning rate modulation.

Key open question: can this minimal mechanism scale beyond toy environments to handle the challenges real organisms face (delayed rewards, high-dimensional sensory input, aversive stimuli)?

### Oscillatory structure encodes spatial information

[[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] showed that [[Theta Oscillations]] in the [[Hippocampus]] are not synchronized — they are **travelling waves** propagating along the septotemporal axis. Combined with [[Phase Precession]] (spike timing shifting with position within a place field), this means the hippocampus instantaneously encodes a **segment** of space, not a point. The wave's wavelength matches the hippocampal length, giving each septotemporal position a unique phase.

This is an example of "the geometry *is* the computation" — the travelling wave isn't a description layered on top of the real computation, but the mechanism by which the hippocampus achieves its topographic spatial mapping. The [[Place Cells|place field]] size gradient along the septotemporal axis (small septal, large temporal) adds a resolution dimension: within each theta cycle, hippocampal output sweeps from fine to coarse spatial resolution.

Key open question: is the travelling wave property **causally necessary** for spatial behavior? The experiment — imposing synchronous theta while preserving frequency and power — has not yet been done.

### The bottleneck is the representation, not the learning rule

[[meister-2022-learning-fast-slow|Meister (2022)]] surveys learning rates across species and tasks, finding a 10,000× range — from one-shot fear conditioning to tens of thousands of trials for laboratory 2AFC tasks. The critical variable is not task complexity but whether the animal already has a [[Sparse Coding|sparse, high-dimensional neural code]] for the relevant events.

[[Hebbian Learning]] is **fast** — synapses can modify in a single trial. But Hebbian plasticity is **local** — each synapse only sees its own pre/post activity. With distributed (non-sparse) codes, this locality causes interference: shared neurons can't distinguish which stimulus caused them to fire. Sparse codes eliminate this problem by ensuring each synapse participates in at most one association.

This converges with [[li-2024-prediction-noise-reward|Li et al. (2024)]] on a broader theme: **the learning rules themselves are simple; evolution's investment was elsewhere.** PaN shows simple prediction + noise gives you reward-seeking for free. Meister shows simple Hebbian plasticity gives you fast associative learning — *if* the right representations exist. Both papers redirect attention from the learning algorithm to the architecture, representations, and control systems that enable it.

Two sources of sparse codes: (1) genetic/evolutionary hardwiring for ecologically critical events, and (2) unsupervised learning from lifetime experience (the cortical hierarchy progressively sparsifies representations). Meister proposes that the Bayesian prior **is** the sparse code — lacking a code for a contingency is what makes it seem implausible.

Key open question: does passive exposure to task stimuli (without reinforcement) build sparse codes that accelerate subsequent learning? This would directly test whether the bottleneck is representational.

### The right level of description is macroscopic dynamics, not individual neurons

[[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] demonstrate that even in *C. elegans* — the simplest model nervous system, with a fully mapped connectome and genetically identical animals — individual neuron activation patterns differ consistently across worms performing the same behavior. Averaging neuron activity across individuals destroys behaviorally relevant information.

Yet the **macroscopic dynamics** are conserved: the system traces cyclic loops through a low-dimensional [[Neural Manifolds|manifold]] parameterized by just two variables (phase and loop identity). This manifold, built from ~5% of neurons, predicts behavioral switches up to 30 seconds ahead and generalizes across animals observed years apart.

This is [[Degeneracy]]: many microscopic configurations → same macroscopic function. Evolution selects on behavior, not on individual neuron activation, so there is no pressure for microscopic consistency. The implication reinforces the emerging theme from multiple sources: **the learning rules and computational primitives are simple; the magic is in the collective organization** — whether that's the architecture (Bennett), the representations ([[meister-2022-learning-fast-slow|Meister]]), or the dynamics (Brennan & Proekt).

The [[Attractor Dynamics|attractor]] framework connects across scales: [[li-2024-prediction-noise-reward|Li et al. (2024)]] shows attractors organizing reward-seeking behavior in a toy model; Brennan & Proekt show limit cycle attractors organizing motor behavior in a real nervous system. In both cases, [[Neural Noise|noise]] plays a functional role — destabilizing unrewarding states in PaN, driving behavioral transitions at manifold merge points in *C. elegans*.

[[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] push this further with LOOPER, which extracts **computational scaffolds** — graphs of branching and merging 1D trajectories that directly reveal what information a system stores and when it makes decisions. The key demonstration: a monkey PFC and an RNN trained on the same working memory task produce the same computational scaffold despite completely different neuronal activity. But the two systems employ different strategies — the monkey learns the general algorithm, the RNN exploits dataset statistics and fails on specific novel stimuli that the scaffold predicts. This extends [[Degeneracy]] from "same dynamics despite different neuron activations" to "same computational structure despite different architectures entirely." It also suggests biological systems are under selection pressure for generalization in a way artificial networks are not.
