# Overview

This wiki investigates biological intelligence through a specific lens: **intelligence begins with closed-loop sensorimotor control.** Memory, learning, and cognition are not separate faculties — they are extensions that improve an organism's control over progressively longer timescales, more latent variables, and more counterfactual worlds.

The simplest nervous systems already close the loop: sense, predict, act, update. Everything more complex — synaptic plasticity, memory consolidation, hierarchical representations, planning — can be understood as machinery that extends this basic loop's reach. The wiki traces this progression across levels:

- **The immediate loop** — sensorimotor prediction and control at the timescale of milliseconds to seconds (reflexes, oscillatory dynamics, motor commands)
- **Extending in time** — plasticity mechanisms (LTP/LTD, Hebbian learning) that let past experience modify the loop's parameters, and sleep-dependent consolidation that transfers learned contingencies from fast hippocampal storage to slow cortical models
- **Extending over latent variables** — sparse representations that carve the sensory world into categories the control system can act on, and hierarchical credit assignment that tunes deep processing pipelines to serve downstream action
- **Extending over counterfactuals** — internal models that support planning, imagination, and generalization beyond direct experience

A related hypothesis motivates the evolutionary dimension: genes encode behavior not by specifying circuits, but by shaping neurons' nonlinear feedback control algorithms, producing conserved macroscopic dynamical structures (e.g., limit cycle attractors) with high probability despite unique microscopic configurations. This is the control-theoretic reading of [[Degeneracy]].

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

### Known biology is sufficient for hierarchical credit assignment

[[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] show that the [[Credit Assignment]] problem — how a neuron deep in a hierarchy knows which synapses to change — can be solved by known properties of cortical pyramidal neurons. The mechanism: top-down feedback arriving at [[Dendritic Computation|apical dendrites]] controls whether a neuron fires a **burst** (→ LTP) or an **isolated spike** (→ LTD), and this burst-dependent plasticity rule, combined with short-term plasticity for signal multiplexing and inhibitory microcircuits for linearization, approximates backpropagation gradients at the ensemble level.

This resolves a tension raised by earlier sources. [[meister-2022-learning-fast-slow|Meister (2022)]] emphasized that [[Hebbian Learning]] is simple and local — the bottleneck is the representation, not the learning rule. But if Hebbian learning is only local, how does the brain coordinate changes across multiple layers to build the hierarchical representations in the first place? Payeur et al. answer: the burst-dependent rule **is** Hebbian (local pre/post activity), but the "post" signal is enriched by dendritic computation to carry credit information from higher areas. The rule is simple and local at the synapse; the architecture (dendritic compartments, STP, inhibition) embeds the global structure needed for hierarchical learning.

This also connects to the broader "simple rules, complex architecture" theme: the learning rule itself is a local coincidence detector; the computational sophistication lies in the biological structures — [[Dendritic Computation|dendritic compartmentalization]], differential [[Synapses|short-term plasticity]], and inhibitory microcircuits — that route the right signals to the right compartments.

### Single neurons are far more powerful than point models suggest

[[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] demonstrate that modeling a single neuron's dendritic tree as a sparse binary tree ANN — where each branch imposes a nonlinearity before summation at the soma — yields a computational unit that significantly outperforms linear classifiers and approaches the performance of a parameter-matched 2-layer fully connected network on standard benchmarks (MNIST, CIFAR-10). The key additional finding: **repeated synaptic inputs** across dendritic branches (multi-synaptic boutons, or MSBs) monotonically increase performance, and LTP induces a 6-fold increase in MSBs — meaning learning doesn't just tune weights but **grows the internal architecture** of individual neurons.

This deepens the "simple rules, complex architecture" theme in two ways. First, the "architecture" that matters isn't just the network graph — it includes the internal structure of each node. A network of dendritic neurons is far more powerful than a network of point neurons with the same connectivity. Second, the architecture is not static: [[Hebbian Learning|Hebbian plasticity]] itself reshapes the computational substrate via MSB formation, blurring the line between "learning the weights" and "learning the architecture." Combined with Payeur's insight that dendrites also enable [[Credit Assignment|hierarchical credit assignment]], dendritic computation emerges as a central theme — the single neuron is not a simple processing element but a sophisticated computational module that is simultaneously being tuned by learning and reshaped by it.

### Category representations are gradually built, not instantaneously assigned

[[reinert-2021-pfc-categorization|Reinert et al. (2021)]] provide a direct window into how the brain builds new representations during learning. Using chronic two-photon imaging of mouse [[Prefrontal Cortex|mPFC]] across weeks of visual categorization training, they show that category-selective neurons emerge gradually from near-zero baseline — representations are built up as part of semantic memory, not recruited ad hoc. Once built, these representations support immediate generalization to novel stimuli.

The rule-switch dynamics reveal unexpected complexity: when the categorization rule changes, Go-preferring neurons remap to the new category while NoGo-preferring neurons are replaced by a new population entirely. This asymmetry suggests that even within a single brain region, different subpopulations use different update mechanisms — some representations are flexible, others are rebuilt from scratch.

This connects to the representation-building theme from [[meister-2022-learning-fast-slow|Meister (2022)]]: the slow timescale of learning in lab categorization tasks is consistent with the gradual construction of representations. However, Reinert images PFC (the decision/readout level), not sensory cortex (where Meister's sparse codes would be built). Whether the PFC bottleneck reflects slow upstream sensory code construction or slow rule learning in PFC itself remains an important open question — one that would require simultaneous imaging of sensory and prefrontal areas to resolve.

### Sleep provides the hippocampal-cortical bridge for memory consolidation

[[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] demonstrate that during slow-wave sleep, [[Hippocampus|hippocampal]] CA1 cells fire 0-100 ms before [[Prefrontal Cortex|mPFC]] cells, with this directional timing driven by sharp-wave/ripple (SWR) events and falling within the window for [[Long-Term Potentiation|spike-timing-dependent plasticity]]. This coupling is nearly abolished during REM sleep, suggesting a two-stage consolidation model: SWS for hippocampus-to-cortex transfer, REM for internal cortical reorganization.

This connects Reinert's observation of gradually emerging PFC representations to a possible mechanism: SWR-driven hippocampal reactivation during sleep could progressively build and refine cortical category representations over many sleep cycles. The weeks-long timescale of PFC representation building (Reinert) is consistent with consolidation requiring repeated SWR-driven reinforcement. It also extends the Siapas lab's work across behavioral states — [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] showed theta travelling waves structure hippocampal computation during waking, while Wierzynski et al. show SWR-driven coupling structures hippocampal-cortical communication during sleep. Same circuit, different oscillatory modes, different computational needs.
