# Index

Content catalog for the intelligence wiki. Organized by category. Each entry links to a wiki page with a one-line summary.

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — Local prediction + noise produces emergent reward-seeking behavior without a reward function (PaN algorithm)
- [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — Hippocampal theta oscillations are travelling waves, implying segment (not point) spatial encoding
- [[meister-2022-learning-fast-slow|Meister (2022)]] — 10,000× variation in learning rates explained by sparse neural codes, not task complexity
- [[gerstner-neuronal-dynamics-ch1|Neuronal Dynamics Ch. 1]] — Neuron models from LIF to conductance-based; shunting inhibition as divisive normalization
- [[gerstner-neuronal-dynamics-ch2|Neuronal Dynamics Ch. 2]] — Hodgkin-Huxley model, ion channel design space, star topology constraint, calcium-plasticity bridge
- [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]] — Conserved macroscopic dynamics predict future motor commands in *C. elegans* despite inter-individual neuron variability
- [[brennan-2023-looper-computational-scaffold|Brennan et al. (2023)]] — LOOPER extracts computational scaffolds from neural dynamics; same scaffold in monkey PFC and RNN despite different activity/strategy
- [[bennett-2023-history-intelligence-intro|A Brief History of Intelligence — Intro]] — Evolutionary decomposition as methodology; five breakthroughs framework; triune brain debunked
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — Burst-dependent plasticity + dendritic compartments + STP + inhibition ≈ backpropagation in spiking networks
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — Single neurons with dendritic trees can solve complex classification tasks; point neuron models underestimate computational power
- [[reinert-2021-pfc-categorization|Reinert et al. (2021)]] — Category-selective neurons in mouse mPFC emerge gradually during learning; flexible remapping during rule switches
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — Directional spike timing from hippocampus to PFC during SWS, driven by sharp-wave ripples; abolished during REM
- [[rosenberg-2021-labyrinth-learning|Rosenberg et al. (2021)]] — Overnight labyrinth exposes few-shot learning, sudden insight, one-shot home-path learning, and efficient exploration from 4 genetically-consistent local turning biases
- [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]] — Endotaxis: a 3-layer Hebbian circuit that computes a "virtual odor" (monotonic in graph distance) to repurpose the ancient chemotaxis module for cognitive navigation
- [[banerjee-2023-life-stage-chemosensation|Banerjee et al. (2023)]] — Same CO₂ cue, same valence, different microcircuits in *C. elegans* adults vs. dauer larvae; BAG–AIB gap junctions and daf-2 insulin signaling gate the reconfiguration
- [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]] — Review codifying the Computation Through Dynamics (CTD) framework; motor-cortex motifs (preparatory initial conditions, output-null preparation, rotational dynamics, line-attractor decisions, manifold-constrained BCI learning)
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — Three-compartment pyramidal neurons + SST interneurons learn via local dendritic prediction errors; analytically approximates backpropagation without separate phases; unifies predictive coding with credit assignment
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] — BurstCCN synthesis: Q-Y cancellation enables single-phase deep learning; combines burst multiplexing, STP type specificity, and homeostatic feedback; resolves phase and depth limitations; 1.84% MNIST, ~23% CIFAR-10
- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] — First spiking implementation of credit assignment with segregated dendritic compartments; plateau potentials carry feedback error; feedback alignment emerges during training; 3.28% MNIST
- [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]] — Two sites of synaptic integration (basal/apical dendrites) → two variables per neuron → backpropagation and self-supervised learning; conceptual seed of burst-dependent credit assignment
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] — First in vivo evidence: cell-specific SD residuals in L5 apical dendrites encode error derivatives during BCI learning; NDNF+ L1 interneuron perturbation abolishes vectorized signals and impairs learning
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — Sharp transition from silent fixed point to deterministic high-dimensional chaos at gain gJ = 1 in random asymmetric rate networks; solved exactly by dynamical mean-field theory; the substrate under CTD and the theoretical anchor of the edge-of-chaos framing
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — The Helmholtz Machine: variational lower bound (Helmholtz free energy = ELBO) with separate bottom-up recognition and top-down generative networks trained by the local wake-sleep delta rule; computational ancestor of VAEs, predictive coding, and the Free Energy Principle
- [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] — Analytical Fokker-Planck theory of sparsely connected E-I spiking networks; four generic regimes (SR, AR, AI, SI); fast oscillations (~1/2D, set by synaptic delay) and slow oscillations (set by membrane τ) emerge as Hopf bifurcations of the balanced state; maps gamma and sharp-wave ripples onto the same dynamical framework
- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — Two-variable mean-field E-I population model; three generic dynamical regimes (simple hysteresis, multiple hysteresis, limit cycles) selected by inequalities on four coupling strengths; Theorem 4: limit-cycle-capable populations must also exhibit hysteresis under different bias; foundational neural-mass model
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — FORCE learning: trains chaotic RNNs with intact feedback loops to produce complex coherent outputs by keeping error small throughout training; three architectures (readout feedback, separate feedback network, within-generator); chaos is beneficial with an operational "edge of chaos" at the largest g where FORCE still suppresses it; preparation as chaos suppression
- [[parisi-1979-replica-symmetry-breaking|Parisi (1979)]] — *Phys. Rev. Lett.* seed of hierarchical replica symmetry breaking: the order parameter for the SK mean-field spin glass is not a number but a function `q(x)` on `[0, 1]`; ultrametric organization of pure states; the static sibling of DMFT and the analytical foundation for Hopfield-network capacity calculations
- [[hopfield-1982-collective-computational-abilities|Hopfield (1982)]] — Founding paper of attractor neural networks: symmetric Hebbian-coupled binary neurons with asynchronous updates store `~0.15 N` patterns as fixed-point attractors of an energy function; emergent error correction, categorization, familiarity recognition, graceful forgetting; explicit identification with the Ising / spin-glass Hamiltonian; the bridge from neural networks to spin-glass physics
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — Founding paper of hierarchical predictive coding for cortex: feedback connections carry top-down predictions, feedforward connections carry residual errors; trained on natural images, recovers V1 simple-cell receptive fields and reinterprets endstopping and other extra-classical RF effects as residual-error signatures; disabling feedback eliminates extra-classical effects; the cortical instantiation of the Helmholtz-machine variational-inference framework and operational core of Friston's free-energy principle
- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — Founding paper of MaxEnt inference: statistical mechanics is a special case of statistical inference; the unique unbiased prior under expectation-value constraints maximizes Shannon entropy and gives the Boltzmann/canonical/grand-canonical distributions without ergodicity; provides the inference-theoretic foundation for predictive coding, free-energy minimization, sparse coding, and the Bayesian-brain program more broadly
- [[friston-2010-free-energy-principle|Friston (2010)]] — Canonical statement of the Free-Energy Principle as a unified brain theory: perception, action, and learning are gradient descents on the same variational free energy `F`; nine "global" brain theories (Bayesian brain, hierarchical predictive coding, efficient/infomax coding, cell-assembly / correlation theory, biased competition, neural Darwinism, optimal control, game theory, dynamical-systems accounts) emerge as special cases; canonical-microcircuit cortical implementation (forward errors, backward predictions, precision-weighted gradient); precision = synaptic gain = attention; resolves the dark-room problem via heritable phenotype-specific priors
- [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] — The massed-spaced learning effect reproduced in two non-neural human cell lines (SH-SY5Y, HEK293) using a CRE-luciferase reporter; four 3-min pulses of forskolin/TPA spaced by 10–20 min produce ~3.9× higher CREB-driven transcription at 24 h than a single equivalent massed pulse; ERK and CREB inhibition both block the effect; PKA encodes duration, PKC encodes event count. Memory's molecular substrate predates the nervous system — the temporal-pattern decoding and transcriptional consolidation that distinguish massed from spaced training live in conserved cellular signaling cascades, not in synapses or neural circuits per se
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — Methodological-philosophical thought experiment: standard systems-neuroscience analyses (connectomics, lesion studies, single-unit tuning, spike-word correlations, LFP / 1/f spectra, Granger causality, NMF dimensionality reduction) applied to a fully understood microprocessor (MOS 6502, full netlist, every transistor state simulable, three "behaviors": Donkey Kong, Space Invaders, Pitfall) produce results superficially similar to neural findings but do not recover computational understanding even with full ground truth. Frames "understanding" via [[marrs-levels-of-analysis|Marr's three levels]] and Lazebnik's "fix it" test; argues that data scarcity is not the bottleneck — methods are — and that ground-truth-anchored validation against engineered systems should be a precondition for trusting analytical methods on neural data
- [[brette-2018-coding-metaphor|Brette (2018)]] — Sustained philosophical critique of the [[neural-coding|neural coding metaphor]] as the basis for theories of brain function. Three-part argument: (1) tuning curves establish only context-dependent sensitivity, not "encoding" of properties (the Crick "overwise neuron" fallacy; ITD slope coding; V1 context-dependence; the unjustified linking proposition implicit in ideal observers); (2) codes carry Shannon information by reference to known external messages, but the brain has no external referent — the [[neural-coding|symbol grounding problem]] applied to neural representations; the *efficient-coding paradox* (a maximally efficient code is unreadable); (3) the linear/dominoes causal structure of codes is incongruent with the brain's circular dynamical-systems coupling to environment (the Paramecium "swimming neuron" example, the heart's rate-coding-of-running-speed under temporal-coordination life-criticality). Positive proposal: [[subjective-physics|subjective physics]] (information as relational structure among observables and actions), [[sensorimotor-contingencies|sensorimotor contingencies]] (O'Regan & Noë 2001), [[binding-problem|synchrony receptive fields]] (Brette 2012) as a representational primitive, and "models that behave" rather than encoder-decoder chimaeras. Companion to [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]] — methods don't recover Marr-level understanding, and the framework that interprets them is incoherent. Most explicit philosophical articulation in the literature of the wiki's organizing principle that intelligence begins with closed-loop sensorimotor control

## Concepts

- [[Neural Noise]] — Stochasticity in neural activity; functional roles including enabling exploration and destabilizing unrewarding states
- [[Explore-Exploit Tradeoff]] — The tension between exploiting known rewards and exploring uncertain alternatives
- [[Dark Room Problem]] — Objection to predictive coding: why doesn't the brain seek maximally predictable (boring) environments?
- [[Place Cells]] — Hippocampal neurons that fire at specific locations; place field size varies along septotemporal axis
- [[Sparse Coding]] — Representations where few neurons are active per stimulus; enables fast Hebbian associative learning by eliminating interference
- [[Degeneracy]] — Many-to-one mapping from microscopic neural configurations to macroscopic behavior; structurally different elements producing equivalent function
- [[Neural Manifolds]] — Low-dimensional surfaces in neural state space along which population activity evolves; the geometry of collective dynamics
- [[Credit Assignment]] — How neurons deep in a hierarchy determine which synapses to change; burst-dependent plasticity as a biological solution
- [[Dendritic Computation]] — Information processing within the dendritic tree; apical vs basal compartments separate feedforward from feedback
- [[Dopamine|Dopamine & Neuromodulation]] — Diffuse chemical signals that gate, bias, and steer learning; reward prediction error, three-factor rules
- [[Inhibitory Circuits]] — GABAergic interneuron types (PV+, SST+, VIP+) implementing gain control, sparse coding, and credit signal linearization
- [[Memory Consolidation]] — Hippocampus-to-cortex memory transfer during sleep via SWR-driven reactivation; SWS vs REM dissociation
- [[Sudden Insight]] — Discontinuous transitions in behavior during learning; challenges purely gradient-based accounts
- [[intrinsic-exploration|Intrinsic Exploration]] — Exploration as default behavioral mode, not a fraction traded off against exploitation
- [[ethological-paradigms|Ethological Paradigms]] — Naturalistic task designs that expose learning dynamics invisible in trial-based paradigms
- [[Cognitive Map]] — Internal representation of environmental structure supporting navigation to arbitrary goals; substrate for extending sensorimotor control over space
- [[Circuit-Behavior Mapping]] — Umbrella: the mapping between neural implementation and behavior is many-to-many; links degeneracy and context-dependent reconfiguration
- [[Context-Dependent Circuit Reconfiguration]] — Same substrate, different effective circuits depending on state; complement to degeneracy
- [[Preparatory Activity]] — Delay-period motor-cortex activity as initial condition for movement-period dynamics; substrate for motor adaptation
- [[Null Space Coding]] — Using the null space of a downstream readout to compute without driving action; output-null preparation, communication subspaces
- [[Helmholtz Machine]] — Hierarchical connectionist architecture with separate bottom-up recognition and top-down generative networks; trained by maximizing a variational lower bound on log-likelihood
- [[Variational Free Energy]] — Tractable upper bound on negative log-evidence (ELBO); formal backbone of variational inference, predictive coding, and active inference
- [[Excitation-Inhibition Balance]] — Regime where recurrent E and I nearly cancel, leaving fluctuation-driven low-rate irregular firing; the condition for the AI state and the gateway to emergent cortical oscillations
- [[Asynchronous Irregular State]] — AI: stationary global activity with Poisson-like low-rate single-cell firing; the dynamical operating point of waking cortex, generated by sparse random recurrence without external noise
- [[Hysteresis]] — Minimum dynamical structure for short-term memory: a bistable region where the active state is maintained after the stimulus is withdrawn; foundational WC / Hebb / Cragg-Temperley result
- [[spin-glass|Spin Glass]] — Disordered random-coupling magnetic system with frustration; the canonical instance of an exponentially many-attractor rugged energy landscape and the static counterpart of the SCS chaotic regime; foundational for Hopfield-network capacity theory
- [[energy-landscape|Energy Landscape]] — Scalar potential whose minima are attractors; the rugged-landscape picture for symmetric-coupling networks (Hopfield, spin glass), with caveats for asymmetric / driven systems where no Lyapunov function exists
- [[content-addressable-memory|Content-Addressable Memory]] — Memory retrieved by content rather than address; defined dynamically as flow toward locally stable points; the framing that turns associative memory into a dynamical-systems object
- [[natural-image-statistics|Natural Image Statistics]] — Regularities of natural visual input (1/f spectrum, long-range correlations along dominant orientations, sparse oriented features) that shape V1 receptive fields under multiple optimization criteria (sparse coding, ICA, predictive coding, efficient coding); the common cause behind V1's apparent universality
- [[efficient-coding-hypothesis|Efficient Coding Hypothesis]] — Sensory neurons organized to transmit information about input efficiently, removing natural-image redundancies subject to bandwidth/metabolic constraints; Attneave-Barlow-Linsker-Atick lineage; subsumed under FEP (Friston 2010) as the no-action / complexity-minus-accuracy reading of `F`
- [[spacing-effect|Spacing Effect]] — Distributed training produces stronger and more durable memory than the same total training applied massed; optimal non-zero ITI (5–20 min in many systems); decoded by PKA / PKC / ERK / CREB cascade kinetics; reproducible in non-neural human cells (Kukushkin 2024)
- [[subjective-physics|Subjective Physics]] — Brette's framework: information for an organism is the structure of relations among its sensor signals and actions, not Shannon correspondence to known external messages. Distinct from generative models (which describe causes-of-inputs) and from coding (which presumes external referents). The Martian iguana example. Resolves the symbol grounding problem by holding that nothing in the organism refers to anything external — what's internal are the lawful relations themselves
- [[binding-problem|Binding Problem]] — How the brain represents relations between features that belong to the same object, and between objects that stand in particular relations. Layer 1 (feature binding, von der Malsburg, Singer): synchrony, retinotopic-position-as-label, attention. Layer 2 (relational binding, Brette 2018): cell assemblies are bag-of-neurons that cannot represent directed relations like "Paul drives car"; even synchrony is symmetric and only marks symmetric relations

## Mechanisms

- [[Long-Term Potentiation|LTP / LTD]] — Sustained strengthening or weakening of synapses; the cellular basis of Hebbian learning
- [[Calcium Signaling]] — Ca²⁺ as bridge between electrical activity and lasting synaptic change; NMDA coincidence detection
- [[creb|CREB]] — cAMP response element-binding protein; transcription factor whose S133 phosphorylation gates the conversion of transient cellular events to lasting synaptic and molecular change; central to long-term memory across cell types from *Aplysia* to non-neural human cells
- [[Attractor Dynamics]] — Neural computation understood through stable states and transitions between them in dynamical systems
- [[Theta Oscillations]] — 4–10 Hz hippocampal rhythm; travelling wave structure enables segment encoding of space
- [[Phase Precession]] — Place cell firing shifts to earlier theta phases as animal traverses the field; converts position to spike timing code
- [[Divisive Normalization]] — Gain control via shunting inhibition; divides rather than subtracts, preserving discriminability across dynamic range
- [[Action Potential]] — All-or-nothing electrical pulse; HH model, ion channel design space, star topology constraint
- [[Rotational Dynamics]] — Motor-cortex population activity traces rotations during reaching; low-dimensional oscillator generates multiphasic muscle patterns
- [[Limit Cycle]] — Isolated closed orbit attractor in state space; the dynamical object underlying locomotion CPGs, cortical rotations, and rhythm generation more generally
- [[Wake-Sleep Algorithm]] — Two-phase local delta-rule learning for Helmholtz machines; wake trains generative weights against recognition samples, sleep trains recognition weights against generative hallucinations
- [[force-learning|FORCE Learning]] — First-Order Reduced and Controlled Error: trains chaotic RNNs by keeping error small throughout via RLS; three architectures; constructive existence proof that CTD trained dynamics can be carved from the SCS chaotic reservoir
- [[hopfield-network|Hopfield Network]] — Fully-connected recurrent network of binary neurons with symmetric Hebbian-stored couplings; energy function whose local minima are stored memories; capacity `α_c ≈ 0.138 N` (AGS via Parisi); founding model of attractor neural networks

## Theories

- [[Predictive Coding]] — Theory that the brain minimizes prediction errors between predicted and actual neural activity
- [[Active Inference]] — Extension of predictive coding to action; organisms minimize surprise of sensory observations
- [[Self-Supervised Behavior]] — Framework for agents whose goals emerge from internal dynamics without external reward (proposed by Li et al. 2024)
- [[Hebbian Learning]] — "Fire together, wire together" — local synaptic plasticity rule; fast but constrained by representation quality
- [[Endotaxis]] — Neuromorphic algorithm that repurposes chemotaxis for cognitive navigation via an internally computed "virtual odor" gradient
- [[Successor Representation]] — Predictive state representation encoding expected future occupancy; formally similar to endotaxis but with different interpretation
- [[Computation Through Dynamics]] — Framework: a neural population's job is to be a dynamical system whose temporal evolution *is* the computation; formalization of the dynamical-systems stance
- [[Edge of Chaos]] — Hypothesis that neural networks poised near the order-chaos transition achieve maximal computational capacity; theoretical anchor from Sompolinsky, Crisanti & Sommers (1988)
- [[Analysis-by-Synthesis]] — Perception as inversion of an internal generative model; root of predictive coding, active inference, and the Helmholtz machine lineage
- [[Wilson-Cowan Model]] — Two-variable mean-field E-I population model; three generic regimes (simple hysteresis, multiple hysteresis, limit cycles) selected by four coupling strengths; Theorem 4 on regime interconvertibility under bias
- [[maximum-entropy-principle|Maximum Entropy Principle]] — Jaynes's constructive criterion: given expectation-value constraints, the unique unbiased prior maximizes Shannon entropy; recovers Boltzmann/Gaussian/heavy-tailed distributions as special cases; the inference-theoretic foundation for predictive coding, free-energy minimization, and sparse/efficient coding
- [[free-energy-principle|Free Energy Principle]] — Friston's normative claim that biological systems must minimize variational free energy as a master imperative; perception, action, and learning are gradient descents on the same scalar; subsumes nine "global" brain theories under a single objective; defines the framework that [[active-inference|active inference]] operationalizes for embodied agents
- [[marrs-levels-of-analysis|Marr's Levels of Analysis]] — Three-level framework (computational, algorithmic, implementational) for analyzing information-processing systems; benchmark for "what does it mean to understand?" used by [[jonas-2017-microprocessor-critique|Jonas & Kording]] to argue current neuroscience methods recover the implementational level cleanly but rarely the algorithmic or computational level
- [[neural-coding|Neural Coding]] — The dominant 20th- and 21st-century framework for theorizing about how nervous systems represent information; encompasses single-unit tuning, population coding, Bayesian decoding, predictive coding, sparse/efficient coding, ideal observers. Three logically distinct senses (correspondence, representation, causality, after Perkel & Bullock 1968) — only the first is established by typical empirical results. Contested by [[brette-2018-coding-metaphor|Brette (2018)]] as the basis for theories of brain function while remaining valid as a measurement tool
- [[sensorimotor-contingencies|Sensorimotor Contingencies]] — O'Regan & Noë (2001) framework: perception is the practical mastery of how sensory inputs change as a function of action, not the construction of an internal picture. Vision as embodied skill, modal differences as different contingency structures, the dark-room problem dissolved rather than solved. Phenomenological / cognitive-science precursor to [[subjective-physics|subjective physics]]; foundational alternative to representationalist theories
- [[cellular-cognition|Cellular Cognition]] — Memory-like temporal pattern detection and transcriptional consolidation are properties of conserved cellular signaling cascades, not unique to neurons; the nervous system inherited memory primitives rather than inventing them; synapses contribute pairwise specificity, cellular cascades contribute temporal-pattern decoding

## Methods

- [[Dynamical Mean-Field Theory|DMFT]] — Analytical technique from spin-glass physics that reduces large random recurrent networks to a single self-consistent stochastic neuron in the N → ∞ limit; principal tool for theoretical claims about random RNN dynamics
- [[replica-method|Replica Method & RSB]] — Static sibling of DMFT for averaging the log-partition function over quenched disorder; Parisi's hierarchical RSB makes the order parameter a function `q(x)` on `[0,1]`; analytical machinery for Hopfield capacity, Gardner volumes, and generalization bounds
- [[Neural Mass Model]] — Mesoscopic modeling move: replace thousands of neurons in a local population with a small number of activity variables; basis of Wilson-Cowan, Jansen-Rit, DCM, and TVB

## Brain Regions

- [[Hippocampus]] — Medial temporal lobe structure critical for spatial navigation, episodic memory, and learning
- [[Prefrontal Cortex]] — Frontal cortex region for categorization, rule learning, decision-making, and cognitive flexibility
- [[Mushroom Body]] — Insect associative learning center; sparse→dense Hebbian convergence motif; candidate substrate for insect cognitive navigation via endotaxis
- [[C. elegans Chemotaxis Circuit]] — Compact CO₂-responsive sensorimotor circuit (BAG, AIY, AIB, RIG, AVE); clearest case of life-stage-dependent circuit reconfiguration
- [[Motor Cortex]] — M1 / PMd / SMA; foundational closed-loop controller; preparatory activity, output-null preparation, rotational pattern generation

## People

- [[Gabriel Kreiman]] — Harvard Medical School; computational neuroscience, prediction, emergent behavior
- [[Athanassios Siapas]] — Caltech; hippocampal circuits, oscillatory dynamics, sleep
- [[Markus Meister]] — Caltech; neural coding, retinal processing, learning rates and information theory
- [[Alexander Proekt]] — UPenn; neural dynamics, macroscopic dynamical models, *C. elegans*
- [[Ilenna Jones]] — UPenn; dendritic computation, single-neuron computational power
- [[Konrad Kording]] — UPenn; computational neuroscience, machine learning, neural data science; two-site integration framework (2001), dendritic computation
- [[Joao Sacramento]] — ETH Zurich (Neuroinformatics); dendritic microcircuits, predictive coding meets credit assignment
- [[Walter Senn]] — University of Bern; dendritic predictive plasticity framework, cortical learning theory
- [[Rui Ponte Costa]] — University of Bristol; cortical microcircuits, biologically plausible learning
- [[Will Greedy]] — University of Bristol (Costa group); BurstCCN single-phase deep learning synthesis
- [[Jordan Guerguiev]] — University of Toronto; first spiking segregated-dendrite credit assignment, burst-dependent plasticity
- [[Timothy Lillicrap]] — Google DeepMind; feedback alignment, biologically plausible deep learning
- [[Blake Richards]] — McGill / Mila; dendritic credit assignment, biologically plausible deep learning
- [[Yoshua Bengio]] — Mila / U Montreal; deep learning pioneer, target propagation, biologically plausible credit assignment
- [[Peter Konig]] — University of Osnabruck (formerly ETH Zurich); cortical dynamics, self-supervised learning, two-site integration framework
- [[Pieter Goltstein]] — Max Planck; prefrontal cortex, category learning, two-photon imaging
- [[Matthew Rosenberg]] — Caltech (Meister lab); ethological behavior, labyrinth navigation, unsupervised mouse behavior
- [[Tony Zhang]] — Caltech (Meister lab); computational neuroscience, endotaxis circuit model for cognitive navigation
- [[Elissa Hallem]] — UCLA; nematode chemosensation, host-seeking behavior, life-stage-dependent sensory circuits
- [[Paul Sternberg]] — Caltech; *C. elegans* genetics, developmental biology, neurogenetics
- [[Navonil Banerjee]] — UCLA (Hallem lab); *C. elegans* chemosensory circuit function across life stages
- [[Valerio Francioni]] — MIT (Harnett lab); first in vivo evidence for vectorized dendritic teaching signals
- [[Mark Harnett|Mark T. Harnett]] — MIT McGovern Institute; dendritic biophysics, cortical computation
- [[Krishna Shenoy]] — Stanford; motor cortex, BCI, dynamical-systems framing of motor control; senior author of the CTD review
- [[Saurabh Vyas]] — Columbia (Zuckerman); motor adaptation operates on preparatory dimensions; first author of the CTD review
- [[David Sussillo]] — Stanford / Google DeepMind; RNNs as models of neural population dynamics; fixed-point analysis methods
- [[Haim Sompolinsky]] — Hebrew University / Harvard; statistical physics of random networks, chaos transition, balanced E-I, associative memory
- [[Peter Dayan]] — Max Planck Tübingen; Bayesian brain, reinforcement learning theory, Helmholtz machine, TD-dopamine hypothesis
- [[Geoffrey Hinton]] — University of Toronto (Emeritus); Boltzmann machines, backpropagation, Helmholtz machine, deep belief networks, forward-forward algorithm
- [[Nicolas Brunel]] — Duke University (formerly ENS Paris, Chicago); analytical theory of balanced E-I spiking networks, cortical dynamics, mean-field / Fokker-Planck methods
- [[Hugh Wilson]] — York University, Toronto (Emeritus); mean-field neural population dynamics, vision, perception; co-author of the Wilson-Cowan model
- [[Jack Cowan]] — University of Chicago (Emeritus); neural mass modeling, neural field theory, statistical mechanics of cortex; co-author of the Wilson-Cowan model
- [[giorgio-parisi|Giorgio Parisi]] — Sapienza Rome; spin-glass theory, hierarchical replica symmetry breaking, disordered systems; 2021 Nobel laureate; methodological progenitor of associative-memory capacity theory
- [[john-hopfield|John Hopfield]] — Princeton (Emeritus) / Caltech / Bell Labs; attractor neural networks, content-addressable memory, kinetic proofreading, biophysics; 2024 Nobel laureate (with Hinton) for foundational neural-network discoveries
- [[rajesh-rao|Rajesh Rao]] — University of Washington (Hwang Endowed Professor); hierarchical predictive coding, brain-computer interfaces, Bayesian theories of cortex; co-author of Rao-Ballard 1999
- [[dana-ballard|Dana Ballard]] — UT Austin (Emeritus) / formerly Rochester; computer vision (Ballard's generalized Hough transform), active vision, embodied cognition, hierarchical predictive coding; co-author of Rao-Ballard 1999
- [[edwin-jaynes|E. T. Jaynes]] — Stanford / Washington University in St. Louis; theoretical physicist; reframed statistical mechanics as statistical inference via the maximum-entropy principle; Cox-Jaynes derivation of Bayesian probability theory; the inference-theoretic foundation underlying the Bayesian-brain program
- [[karl-friston|Karl Friston]] — UCL Wellcome Trust Centre for Neuroimaging; principal architect of the free-energy principle and active inference; SPM and DCM developer; canonical-microcircuit reading of cortex (forward errors, backward predictions, precision = synaptic gain = attention)
- [[nikolay-kukushkin|Nikolay V. Kukushkin]] — NYU (Liberal Studies; Center for Neural Science, Carew lab); molecular logic of memory formation; precision timing of ERK in long-term memory; cellular cognition framework
- [[thomas-carew|Thomas J. Carew]] — NYU Center for Neural Science; long-running *Aplysia* memory program; spaced vs massed long-term synaptic facilitation; signaling-cascade dynamics as memory mechanism; senior author of Kukushkin (2024)
- [[eric-jonas|Eric Jonas]] — University of Chicago (CS); statistical machine learning, probabilistic methods for science, methodology validated against ground-truth artificial systems; first author of the microprocessor critique
- [[romain-brette|Romain Brette]] — Sorbonne / INSERM / Institut de la Vision (Paris); computational and theoretical neuroscience, sound localization, spike-timing-based computation, philosophy of neuroscience; co-developer of the Brian neural simulator; sustained critic of the [[neural-coding|neural coding metaphor]] and architect of the [[subjective-physics|subjective physics]] framework as a positive alternative

## Analyses

- [[unified-picture-single-neuron-population-control|Unified picture: single-neuron biophysics + population dynamics for closed-loop control?]] — Partial unification. CTD + motor cortex on the population side; dendritic credit-assignment lineage on the single-neuron side; manifold-constrained learning as the cleanest junction; Wilson-Cowan/Brunel linking mesoscopic E-I parameters to attractor repertoire. Load-bearing gap: nobody has shown apical-dendrite events reshaping motor-cortex manifolds during adaptation.
