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

## Mechanisms

- [[Long-Term Potentiation|LTP / LTD]] — Sustained strengthening or weakening of synapses; the cellular basis of Hebbian learning
- [[Calcium Signaling]] — Ca²⁺ as bridge between electrical activity and lasting synaptic change; NMDA coincidence detection
- [[Attractor Dynamics]] — Neural computation understood through stable states and transitions between them in dynamical systems
- [[Theta Oscillations]] — 4–10 Hz hippocampal rhythm; travelling wave structure enables segment encoding of space
- [[Phase Precession]] — Place cell firing shifts to earlier theta phases as animal traverses the field; converts position to spike timing code
- [[Divisive Normalization]] — Gain control via shunting inhibition; divides rather than subtracts, preserving discriminability across dynamic range
- [[Action Potential]] — All-or-nothing electrical pulse; HH model, ion channel design space, star topology constraint
- [[Rotational Dynamics]] — Motor-cortex population activity traces rotations during reaching; low-dimensional oscillator generates multiphasic muscle patterns
- [[Limit Cycle]] — Isolated closed orbit attractor in state space; the dynamical object underlying locomotion CPGs, cortical rotations, and rhythm generation more generally
- [[Wake-Sleep Algorithm]] — Two-phase local delta-rule learning for Helmholtz machines; wake trains generative weights against recognition samples, sleep trains recognition weights against generative hallucinations
- [[force-learning|FORCE Learning]] — First-Order Reduced and Controlled Error: trains chaotic RNNs by keeping error small throughout via RLS; three architectures; constructive existence proof that CTD trained dynamics can be carved from the SCS chaotic reservoir

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

## Methods

- [[Dynamical Mean-Field Theory|DMFT]] — Analytical technique from spin-glass physics that reduces large random recurrent networks to a single self-consistent stochastic neuron in the N → ∞ limit; principal tool for theoretical claims about random RNN dynamics
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

## Analyses

- [[unified-picture-single-neuron-population-control|Unified picture: single-neuron biophysics + population dynamics for closed-loop control?]] — Partial unification. CTD + motor cortex on the population side; dendritic credit-assignment lineage on the single-neuron side; manifold-constrained learning as the cleanest junction; Wilson-Cowan/Brunel linking mesoscopic E-I parameters to attractor repertoire. Load-bearing gap: nobody has shown apical-dendrite events reshaping motor-cortex manifolds during adaptation.
