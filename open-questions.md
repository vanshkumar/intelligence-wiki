# Open Questions

Research gaps, unresolved debates, and questions to guide future source selection. Updated as sources are ingested — questions get added when a paper raises them, and marked resolved (with links) when answered.

These questions are organized by level but unified by the wiki's organizing principle: intelligence begins with closed-loop sensorimotor control, and learning/memory extend that control over longer timescales, more latent variables, and more counterfactual worlds.

---

## Control & Sensorimotor Foundations

- What is the minimal closed-loop sensorimotor system that exhibits learning? [[li-2024-prediction-noise-reward|Li et al. (2024)]] shows prediction + noise suffices for reward-seeking in a toy network — but what is the simplest *biological* system where this can be tested?
- How does the transition from reactive control (immediate sensorimotor loop) to model-based control (planning, counterfactual reasoning) happen across evolution and development? Is it a continuum or are there discrete architectural innovations?
- If genes encode behavior by constraining neurons' nonlinear feedback control algorithms (rather than specifying circuits), what are the specific molecular-to-dynamical mappings? Ion channel expression → membrane dynamics → network-level attractor structure is the rough chain, but the intermediate steps are poorly characterized.
- The [[Degeneracy|degeneracy]] observation — conserved macroscopic dynamics despite variable microscopic configurations ([[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt, 2019]]) — is predicted by a control-theoretic view of genes. Can this be made quantitative: given a distribution over neuronal parameters set by gene expression, what is the probability of the target macroscopic structure emerging?
- How do memory systems (hippocampal consolidation, cortical sparse codes) feed back into the sensorimotor loop? Is the right framing that memory *serves* control — building internal models that allow the loop to operate over longer horizons and more latent variables?

---

## Molecular & Cellular

- What are the fundamental molecular mechanisms of memory formation and storage?
- How do synaptic and non-synaptic plasticity mechanisms interact?
- What role does protein synthesis play in memory consolidation, and what triggers it?
- How exactly is calcium involved in synaptic plasticity? What are the specific molecular cascades from calcium influx to lasting synaptic change, and what determines whether a calcium signal produces LTP vs. LTD?
- Where does the membrane potential as an electrical circuit analogy break down? What phenomena require going beyond the RC circuit / Hodgkin-Huxley framework?
- What is the space of nonlinear dynamical systems that a single neuron can implement using its complement of ion channels? How much computational richness is available at the single-cell level before network effects?
  - *Partially addressed*: [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] show that dendritic branching with nonlinearities gives a single neuron the power of a multi-layer network (approaching a 2-layer FCNN). But this uses an abstract model (leaky ReLU); the full space of dynamics from biophysical ion channels in dendrites remains unexplored.

## Circuits & Systems

- How do different brain regions coordinate during learning?
- What determines whether a memory is consolidated into long-term storage or forgotten?
  - *Partially addressed*: [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] show that SWR-driven hippocampus→PFC spike timing during SWS falls within the STDP window, providing a candidate mechanism. But what determines which memories get replayed (and thus consolidated) vs. which are lost remains unknown.
- How does the hippocampus interact with cortical regions during systems consolidation?
  - *Partially addressed*: [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] demonstrate directional CA1→mPFC spike timing during SWS, driven by SWR events. This is direct single-cell-pair evidence for hippocampus-to-cortex communication during sleep. However, whether this timing actually induces plasticity (vs. merely falling in the right window) has not been shown causally.
- Is the travelling wave property of [[Theta Oscillations|hippocampal theta]] **causally necessary** for spatial behavior, or would synchronized theta work just as well? ([[lubenov-2009-theta-travelling-waves|Lubenov & Siapas, 2009]] — causal experiment not yet done)
- What is the computational advantage of segment over point spatial encoding in the [[Hippocampus]]? Does it support planning, prediction, or multi-scale spatial reasoning?
- When should travelling-wave structure in neural oscillations be interpreted as part of the computation vs. a geometric side effect of coordinated activity?

## Development & Plasticity

- What opens and closes critical periods for learning?
- How does adult neurogenesis contribute to learning and memory?
- How does the brain maintain stability while remaining plastic (the stability-plasticity dilemma)?

## Representations & Learning Speed
*(New — added from Meister 2022)*

- Does passive exposure to 2AFC task stimuli (without reinforcement) build [[Sparse Coding|sparse codes]] that accelerate subsequent reinforced learning? ([[meister-2022-learning-fast-slow|Meister, 2022]] — proposed but untested). [[reinert-2021-pfc-categorization|Reinert et al. (2021)]] show gradual emergence of category selectivity in mPFC during reinforced training, but never separate passive exposure from reinforced learning — the specific passive pre-exposure experiment remains undone.
- What are the specific unsupervised learning mechanisms that build sparse codes in cortex? How do they relate to [[Predictive Coding]]?
- How do neuromodulatory systems (dopamine, norepinephrine) interact with the sparse code framework — do they modulate which codes get built, which associations form on existing codes, or both?
- Are lab 2AFC tasks studying the brain's learning machinery, or mostly studying representation formation — a process that may be irrelevant to how the animal actually learns in the wild?
- Is the gradual emergence of category selectivity in [[Prefrontal Cortex|mPFC]] driven by slow building of upstream sensory representations, slow rule learning in PFC itself, or both? Simultaneous imaging of sensory cortex and PFC during learning would be needed to distinguish these. ([[reinert-2021-pfc-categorization|Reinert et al., 2021]])
- Why do Go-preferring and NoGo-preferring PFC neurons show asymmetric dynamics during rule switching (remapping vs replacement)? What determines which mechanism a neuron uses?

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
  - *Partially addressed*: [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] show that dendritic predictive plasticity rules (local compartmental mismatch × presynaptic rate) are analytically equivalent to backpropagation in the weak-feedback limit. The "algorithm" may be local prediction error minimization implemented by dendritic architecture.
- Does the brain implement something like predictive coding or free energy minimization?
  - *Partially addressed*: [[li-2024-prediction-noise-reward|Li et al. (2024)]] shows predictive coding can drive behavior (not just perception) when combined with noise, but the bottom-up prediction direction in PaN differs from classic top-down formulations.
  - *Substantially addressed*: [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] show that predictive coding and backpropagation are not competing theories — they are two descriptions of the same dendritic microcircuit. The apical dendrite computes a prediction error (top-down feedback minus lateral interneuron prediction), and this error is the backpropagated gradient. The remaining question is whether this holds in spiking networks at scale.
- How does the brain perform credit assignment across multiple synapses and time steps?
  - *Partially addressed*: [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] show that dendritic prediction errors at apical dendrites encode backpropagated gradients, with analytical proof in the weak-feedback limit. Continuous-time operation (no phases), 1.96% MNIST. [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] bring this to spiking biophysical fidelity and scale to CIFAR-10. Both address **structural** (spatial) credit assignment across layers. However, **temporal** credit assignment (delayed rewards, sequences) remains unaddressed — both mechanisms only handle immediate error signals.
  - *Flagged as limitation*: PaN has no mechanism for temporal credit assignment — only handles immediate sensory feedback ([[li-2024-prediction-noise-reward|Li et al. (2024)]]).
- What does it mean to "understand the brain"? What would a satisfying explanation look like — a predictive model, a compression of experimental data, an engineered system that reproduces behavior, or something else? How do we know when we've understood something vs. merely described it?
- What mathematical language is appropriate for describing brain computation? Is it dynamical systems, information theory, statistical mechanics, category theory, or something else — and does the answer depend on the level of description (single neuron vs. circuit vs. system)?
- What might a useful analog to Kolmogorov complexity look like in the brain? Is there a meaningful sense in which some neural representations or computations are "simpler" than others, and does the brain preferentially find low-complexity solutions?
- How does dopamine as reward prediction error solve temporal credit assignment? The RPE signal is global and scalar — how does the brain route it to the specific synapses that were causally responsible for the outcome, potentially many seconds earlier?
- Can universality class / distribution results from random matrix theory help us understand neural population dynamics? Do eigenvalue spectra of neural correlation matrices fall into known universality classes, and if so, what does that imply about the underlying dynamics?

## Evolution & Multi-Scale Organization

- How does DNA bridge the micro (local neuronal learning rules) to the macro (evolutionarily relevant behavior)? DNA encodes proteins, not circuits or behaviors — what are the intermediate layers of organization, and how constrained is the mapping from genome to neural architecture to behavioral repertoire?

## Dendritic Computation & Single-Neuron Power
*(New — added from Jones & Kording 2020)*

- What is the computational role of dendritic morphological diversity? Different neuron types have radically different dendritic trees — does this correspond to different computational specializations?
- How does the *k*-tree (raw computational power) framework interact with dendritic compartmentalization (Payeur, credit assignment)? Can a single neuron simultaneously exploit both multi-layer computation within branches AND feedforward/feedback separation across compartments?
- Does the brain optimize dendritic morphology during development for expected input statistics? Is branching pattern learned, genetically determined, or both?
- How does biologically structured sparsity (dendritic tree topology) compare to other sparsity patterns (random, pruned, lottery ticket) in computational efficiency?

## Hierarchical Learning & Credit Assignment
*(Updated with Greedy et al. 2022 — BurstCCN synthesis)*

- Does the burst-dependent credit assignment mechanism extend to **temporal** credit assignment (sequences, delayed rewards), or only spatial credit assignment across layers? ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]])
- Does a developmental period of "learning to do credit assignment" exist in mammalian cortex? [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] show feedback alignment converging over training epochs (weight update angle to backprop: ~65° → ~40°). This might correspond to critical period plasticity — an early period where the cortical hierarchy calibrates its feedback pathways before effective hierarchical learning can begin.
- What biological mechanism coordinates the forward and plateau phases that [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] require? Candidates include neuromodulatory gating (e.g., cholinergic bursts), oscillatory phase structuring (beta/gamma cycles), and SST interneuron disinhibition. [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] eliminate the phase requirement entirely via the self-predicting state — but if phases do exist in cortex, the question of their coordination mechanism remains.
- Can the self-predicting state ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. 2018]]) be detected experimentally? If apical dendrites are silent post-learning and noisy during learning, this should be measurable with dendritic calcium imaging. Zmarz & Keller (2016) and Attinger et al. (2017) provide initial support in mouse visual cortex, but the longitudinal trajectory (noisy → silent as learning converges) has not been demonstrated.
  - *Partially addressed*: [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] show that SD residuals (dendritic activity not predicted by somatic activity) contain task-relevant information during learning and are cell-specific. The 14-day trajectory shows P+ neurons maintaining activity while P- neurons decrease — consistent with selective error-driven shaping — but full convergence to a silent self-predicting state was not observed within the training window.
- Does the predictive-coding / credit-assignment unification ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. 2018]]) survive in spiking networks? The paper uses rate neurons; [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] use spiking neurons but with a burst-probability rather than prediction-error interpretation. Bridging these — spiking neurons with explicit dendritic prediction errors — would close the lineage.
  - *Partially addressed experimentally*: [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] show that dendritic signals encode error derivatives (more consistent with target propagation) rather than prediction errors per se. GCaMP imaging cannot distinguish burst vs. isolated spike contributions, so whether the SD residual reflects burst-rate modulation (as the computational lineage predicts) or a different dendritic signal type remains open.
- How sensitive is the Sacramento microcircuit to violations of one-to-one SST-to-pyramidal connectivity? The model assumes one interneuron per pyramidal neuron. Leinweber et al. (2017) show approximately targeted SST projections, but exact one-to-one is implausible. Does the mechanism degrade gracefully?
- Can the self-supervised variant of two-site learning ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]]'s Imax-style coherence-across-streams rule) be implemented with the full spiking/STP machinery of Payeur et al.? The 2001 paper proves the principle; the modern spiking implementation remains undone. This matters because most biological learning is unsupervised.
- What is the actual transfer function D = g(apical input, A) for dendritic calcium spike generation in vivo? The backprop implementation requires D ∝ A(1 - A) (sigmoid derivative), which is a strong biophysical assumption. The shape of the BAC firing response curve — particularly its saturating behavior — is incompletely characterized. ([[kording-konig-2001-two-integration-sites|Kording & Konig, 2001]])
- How does burst-dependent plasticity interact with neuromodulatory systems (dopamine, norepinephrine)? The model abstracts all neuromodulation into a gating term M(t) — what fills that role biologically?
- Can the mechanism support unsupervised learning, or does it require a supervised teaching signal? Could bursting + NMDA cooperativity + feedforward inhibition be adapted for unsupervised sequence learning?
- Does the STP polarization prediction hold across cortical areas — STD at feedforward synapses, STF at feedback synapses along the sensory hierarchy? Current evidence is mixed. ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]). [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] sharpen this prediction: the model requires **two** types of feedback connection with different STP (STF via interneurons, STD direct) converging on the same apical dendrites. Is this level of STP specificity actually present?
- BurstCCN with random feedback weights performs significantly worse than with W-Y symmetric weights on CIFAR-10 (~39% vs ~23%). Can biologically plausible feedback learning rules close this gap? This is the main remaining performance limitation of the dendritic credit assignment lineage. ([[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]])
- Can any model in the lineage be extended to **temporal** credit assignment (sequences, delayed rewards)? All five computational papers (Kording → Guerguiev → Sacramento → Payeur → Greedy) address only spatial (structural) credit assignment. Recurrent connections and temporal error signals are unaddressed. [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] validates spatial credit assignment experimentally but does not test temporal credit.
- Does the vectorized dendritic teaching signal ([[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]]) generalize beyond neurofeedback BCI to naturalistic learning? BCI artificially defines the neuron-to-outcome mapping — does the same cell-specific SD residual structure exist during sensory learning, motor learning, or navigation where causal roles are not experimenter-imposed?
- How do NDNF+ and SST+ interneurons interact in implementing credit assignment? The computational lineage assigns linearization and prediction roles to SST+; Francioni assigns a gating role to NDNF+ at L1. A dual-perturbation experiment (SST+ vs NDNF+ vs both) would disambiguate their contributions and test the proposed laminar division of labor.
- Can the SD residual be decomposed into burst-rate vs. isolated-spike contributions using voltage imaging or electrophysiology? GCaMP cannot distinguish these; the computational lineage specifically predicts burst-rate modulation as the credit signal carrier.

## Sleep & Memory Consolidation
*(New — added from Wierzynski et al. 2009)*

- Does the SWR-driven hippocampus→PFC spike timing during SWS **actually induce synaptic plasticity**, or does it merely fall within the STDP window without producing lasting change? Causal evidence (e.g., blocking SWR replay and measuring consolidation deficit) is needed. ([[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al., 2009]])
- What information is carried in SWR-driven hippocampal replay? Is it a faithful reinstatement of waking experience, a compressed/edited version, or a generative recombination? This determines whether consolidation is "copying" or "distilling."
- What explains the biphasic prefrontal response to hippocampal input — early excitation (0-100 ms) followed by late inhibition (100-200 ms)? Is the inhibitory phase a gating signal, a reset mechanism, or something else?
- Does hippocampal-prefrontal coupling strength change with learning? If SWR-driven consolidation builds cortical representations gradually ([[reinert-2021-pfc-categorization|Reinert et al., 2021]]), coupling should be stronger during active learning and weaker once consolidation is complete.
- What is the functional role of REM sleep in the two-stage model? Wierzynski shows hippocampal-prefrontal coupling is abolished during REM — but does REM perform cortical-internal reorganization (strengthening, pruning, integrating), and how?
- The 3 cell pairs with REM-correlated timing (out of 90) may be noise or may indicate a small subpopulation with a distinct consolidation role during REM. Is there a REM-specific hippocampal-cortical pathway?

## Cognitive Navigation & Endotaxis
*(New — added from Zhang et al. 2024)*

- Is [[Endotaxis]] actually the computation used in the hippocampus? The goal-cell signature (very large place field, sudden single-event emergence) is testable with current imaging. Are the three predicted cell populations (point, map, goal) dissociable in recordings?
- How is the mode switch — which selects among goal signals (food, water, home, neglect) and routes the chosen one to the chemotaxis module — implemented biologically? [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] treats it as given; circuit tracing to a module receiving convergent goal inputs and projecting to the taxis controller is the experimental entry point.
- Can endotaxis be extended to continuous (non-graph) environments? Point cells with overlapping receptive fields should generalize, but the monotonicity theorem is proved only for discrete graphs.
- The critical gain γ_c depends on graph topology via λ_max(A). Can neurons tune γ automatically based on environmental connectivity statistics, so the same circuit works across structurally different environments?
- Endotaxis is trial-and-error at each decision. How does it compose with sequence-level planning (chaining actions into motifs, internal forward models as in Kay et al. 2020 / Nyberg et al. 2022)? Is there a natural extension of the endotaxis circuit that supports prospective rollout?
- Is the [[Mushroom Body]] → [[Hippocampus]] motif correspondence **deep homology** (pre-bilaterian origin) or **convergent evolution**? Either way, what does the shared motif tell us about the optimality landscape of associative-learning architectures?
- The formal overlap between endotaxis and the [[Successor Representation]] suggests a single underlying "resolvent-of-connectivity" primitive that can be read out as value function or as goal gradient depending on downstream circuits. Is there biological evidence for both readouts coexisting?
- Does endotaxis interact with [[Memory Consolidation]] — is the learned map subsequently consolidated to cortical long-term storage, and if so, how does the goal-signal machinery persist or transfer?
- Bittner et al. (2017) observed sudden CA1 place-field formation via dendritic calcium plateaus over seconds-long windows. Is this the mechanism by which endotaxis goal cells write their synapses? The timescale of the plasticity rule endotaxis needs matches behavioral-time-scale plasticity observed experimentally.

## Ethology, Exploration & Sudden Insight
*(New — added from Rosenberg et al. 2021)*

- What is the neural substrate of the four local turning biases ([[rosenberg-2021-labyrinth-learning|Rosenberg et al. 2021]])? Are they implemented in a dedicated navigation circuit (entorhinal-hippocampal) or in a more general action-selection structure?
- What is the mechanism of **sudden insight**? Candidate accounts — attractor phase transitions, representational switching via sparse-code emergence, consolidation-driven reorganization, control-hierarchy threshold crossings — are not mutually exclusive, and none are yet experimentally distinguished.
- Can the cross-animal consistency of turning biases (SD ~0.03 across 19 mice) be traced to specific genes or developmental parameters? What is the control-theoretic mapping from gene expression to these four bias parameters? This is the sharpest available test of the genes→control→structure hypothesis.
- Do inbred vs. outbred mouse strains differ in the four bias parameters? Outbred strains would directly test how tightly the biases are genetically constrained.
- Why does exploration remain the dominant behavioral mode (~75–95%) even in rewarded animals after learning? Is it hedging, intrinsic reward, or that reward simply does not suppress the default mode?
- Is one-shot home-path learning dependent on hippocampal [[Place Cells|place cell]] formation during the inbound traversal, or does it rely primarily on path-integration machinery? Rotation-robust navigation favors the former but does not distinguish them.
- Does intrinsic exploration have a neuromodulatory signature (locus coeruleus / norepinephrine tone)? This connects the [[Explore-Exploit Tradeoff]] mechanism to the observed dominance of exploration in [[intrinsic-exploration|intrinsic exploration]].

## Computation Through Dynamics & Motor Cortex
*(New — added from Vyas et al. 2020)*

- What determines the intrinsic neural manifold? Is the ~10D subspace containing motor-cortex population variance primarily shaped by anatomical connectivity, cellular biophysics, slow developmental tuning, or all three? Manifold-constrained BCI learning (Sadtler 2014) makes the constraint concrete but leaves its substrate open. ([[vyas-2020-computation-through-dynamics|Vyas et al., 2020]])
- Are the motor-cortex CTD motifs (preparatory initial conditions, output-null preparation, rotational pattern generation, CIS) specific to motor cortex or instances of more general motifs? Rotations appear in speech cortex (Stavisky 2019) but not in SMA or muscles (Lara 2018a) — what predicts where the motif appears?
- Is null-space structure learned or given? Does the brain learn to place preparation in the null space of fixed readout weights `C`, or do `C` and cortical dynamics co-adapt?
- How widespread is the communication-subspace picture (Semedo 2019)? Does every inter-area connection factor cleanly into communication vs. private subspaces, analogous to output-null vs. output-potent in motor cortex?
- What is the biological implementation of contextual inputs in CTD models? Tonic thalamocortical input (Wang 2018) is one candidate; neuromodulation is another — are these distinct mechanisms or different labels for related signals?
- What is the relationship between fast within-repertoire learning (hours, Golub 2018) and slow off-manifold learning (days, Oby 2019)? Are these distinct mechanisms (synaptic tagging, consolidation) or a continuum? Does [[Memory Consolidation|SWR-driven consolidation]] mediate the slow, structural change?
- Can CTD be unified with credit-assignment accounts ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al., 2020]])? CTD describes what the dynamics *do*; credit-assignment describes how synapses get tuned to produce them — the two should compose but have not been worked out together.
- When brains and RNNs trained on the same task find the same computational scaffold via different strategies ([[brennan-2023-looper-computational-scaffold|Brennan 2023]]), what does this tell us about how to use RNNs as CTD hypothesis generators? Which RNN predictions should we take seriously as biological hypotheses and which should we treat as dataset-specific artifacts?
- Can the rotational motif in motor cortex be causally tested by perturbing the rotation directly (e.g., via patterned optogenetic input along the rotation axis)? The tools are becoming available; the critical falsification experiment for CTD as a causal model has not been done.

## Circuit-Behavior Mapping & State-Dependent Reconfiguration
*(New — added from Banerjee et al. 2023)*

- What other *C. elegans* sensorimotor circuits show life-stage-dependent reconfiguration? Is CO₂ chemotaxis an outlier, or is stage-dependent circuit identity the norm? ([[banerjee-2023-life-stage-chemosensation|Banerjee et al., 2023]])
- What is the molecular mechanism by which daf-2 insulin/IGF signaling gates AIB's recruitment into the dauer CO₂ circuit? Does it alter innexin composition (CHE-7 abundance or phosphorylation), receptor expression, or intrinsic excitability — or all three?
- Are there analogous state-dependent gap-junction reconfigurations in mammalian circuits? Electrical synapses are present throughout vertebrate nervous systems; whether they are similarly gated by systemic signals (insulin, cortisol, sex hormones) at the level of effective connectivity is largely unexplored.
- Does the same sensory neuron (BAG) carry different information in the two life stages, or does the downstream divergence transform a common signal differently? The reduced BAG response amplitude in dauers hints at the former, but calcium imaging resolution is insufficient to settle it.
- Is there a principled way to read off the effective connectome from a physiological state vector? Connectomics currently yields a static wiring diagram; a framework for computing the state-dependent active subset is missing.
- Does the [[Successor Representation]] / [[Endotaxis]] formal overlap generalize in the presence of circuit reconfiguration? If the same sensory gradient is routed through different interneurons in different states, does that correspond to different "value functions" implemented over the same anatomical substrate?
- How widespread is neuromodulation-via-electrical-synapse-recruitment as a mechanism? Classical neuromodulation (dopamine, serotonin, norepinephrine) operates on chemical synapse gain; Banerjee shows a systemic endocrine signal acting on electrical synapse composition. Is this a distinct class of neuromodulation or a widely distributed one that has been under-measured?
- Do analogous *intra-stage* state reconfigurations exist (feeding vs. sated, arousal state, circadian phase), or is the life-stage case special? Crustacean stomatogastric literature suggests the former; the Banerjee-level genetic precision has not been applied.

## Emergent Behavior & Autonomy
*(New — added from Li et al. 2024)*

- Can prediction + noise scale beyond toy environments to handle delayed rewards, high-dimensional sensory input, and aversive stimuli?
- What is the relationship between PaN's noise-driven exploration and norepinephrine/locus coeruleus modulation of neural gain?
- If reward-seeking is "free" (emerges from prediction + noise), what exactly are dopamine and explicit reward circuits *for*? Is their role primarily to bias which emergent goals get preferred (via learning rate modulation) rather than to define reward?
- How does PaN's mechanism relate to specific biological circuits? Is it relevant to any real neural system, or purely a proof of sufficiency?
