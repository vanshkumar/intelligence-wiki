# Open Questions

Research gaps, unresolved debates, and questions to guide future source selection. Updated as sources are ingested — questions get added when a paper raises them, and marked resolved (with links) when answered.

---

## Molecular & Cellular

- What are the fundamental molecular mechanisms of memory formation and storage?
- How do synaptic and non-synaptic plasticity mechanisms interact?
- What role does protein synthesis play in memory consolidation, and what triggers it?

## Circuits & Systems

- How do different brain regions coordinate during learning?
- What determines whether a memory is consolidated into long-term storage or forgotten?
- How does the hippocampus interact with cortical regions during systems consolidation?
- Is the travelling wave property of [[Theta Oscillations|hippocampal theta]] **causally necessary** for spatial behavior, or would synchronized theta work just as well? ([[lubenov-2009-theta-travelling-waves|Lubenov & Siapas, 2009]] — causal experiment not yet done)
- What is the computational advantage of segment over point spatial encoding in the [[Hippocampus]]? Does it support planning, prediction, or multi-scale spatial reasoning?
- When should travelling-wave structure in neural oscillations be interpreted as part of the computation vs. a geometric side effect of coordinated activity?

## Development & Plasticity

- What opens and closes critical periods for learning?
- How does adult neurogenesis contribute to learning and memory?
- How does the brain maintain stability while remaining plastic (the stability-plasticity dilemma)?

## Representations & Learning Speed
*(New — added from Meister 2022)*

- Does passive exposure to 2AFC task stimuli (without reinforcement) build [[Sparse Coding|sparse codes]] that accelerate subsequent reinforced learning? ([[meister-2022-learning-fast-slow|Meister, 2022]] — proposed but untested)
- What are the specific unsupervised learning mechanisms that build sparse codes in cortex? How do they relate to [[Predictive Coding]]?
- How do neuromodulatory systems (dopamine, norepinephrine) interact with the sparse code framework — do they modulate which codes get built, which associations form on existing codes, or both?
- Are lab 2AFC tasks studying the brain's learning machinery, or mostly studying representation formation — a process that may be irrelevant to how the animal actually learns in the wild?

## Neural Dynamics & Manifolds
*(New — added from Brennan & Proekt 2019)*

- Does the [[Neural Manifolds|manifold]] framework scale to organisms with more complex nervous systems? Higher-dimensional dynamics may require fundamentally different extraction methods. ([[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt, 2019]])
- What is the biological substrate of the conserved manifold? If individual neuron activations differ but dynamics are conserved, what physical properties enforce this constraint — is it connectivity topology, neuromodulatory state, or something else?
- How does the manifold change during learning? Does acquiring a new behavior correspond to a topological change (new loop) or a parametric change (modified flow)?
- What determines which neurons are informative for manifold reconstruction? Is there a principled way to identify the ~5% that suffice, or must it be done empirically?
- Does the 1D trajectory approximation (LOOPER) hold for open-ended tasks involving continuous interaction with changing environments, or only for trial-based classification? ([[brennan-2023-looper-computational-scaffold|Brennan et al., 2023]])
- Why do biological systems consistently find general computational strategies while RNNs trained on the same tasks exploit dataset-specific statistics? Is this a consequence of evolutionary selection pressure for generalization, or a structural property of biological networks? ([[brennan-2023-looper-computational-scaffold|Brennan et al., 2023]])
- Can computational scaffolds be compared formally across systems to quantify computational similarity — not just "same number of branches" but a rigorous distance metric?

## Computation & Theory

- What is the brain's "learning algorithm"? How does it compare to gradient descent and other artificial learning rules?
  - *Partially addressed*: [[li-2024-prediction-noise-reward|Li et al. (2024)]] shows local prediction + noise is sufficient for reward-seeking, suggesting the "algorithm" may be simpler than expected — but only demonstrated in toy environments.
- Does the brain implement something like predictive coding or free energy minimization?
  - *Partially addressed*: [[li-2024-prediction-noise-reward|Li et al. (2024)]] shows predictive coding can drive behavior (not just perception) when combined with noise, but the bottom-up prediction direction in PaN differs from classic top-down formulations.
- How does the brain perform credit assignment across multiple synapses and time steps?
  - *Flagged as limitation*: PaN has no mechanism for temporal credit assignment — only handles immediate sensory feedback ([[li-2024-prediction-noise-reward|Li et al. (2024)]]).

## Emergent Behavior & Autonomy
*(New — added from Li et al. 2024)*

- Can prediction + noise scale beyond toy environments to handle delayed rewards, high-dimensional sensory input, and aversive stimuli?
- What is the relationship between PaN's noise-driven exploration and norepinephrine/locus coeruleus modulation of neural gain?
- If reward-seeking is "free" (emerges from prediction + noise), what exactly are dopamine and explicit reward circuits *for*? Is their role primarily to bias which emergent goals get preferred (via learning rate modulation) rather than to define reward?
- How does PaN's mechanism relate to specific biological circuits? Is it relevant to any real neural system, or purely a proof of sufficiency?
