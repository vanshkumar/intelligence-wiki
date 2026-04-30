---
title: "The Free-Energy Principle: A Unified Brain Theory?"
type: source
source_type: paper
authors:
  - "Karl Friston"
year: 2010
doi: "10.1038/nrn2787"
tags: [free-energy-principle, active-inference, predictive-coding, bayesian-brain, efficient-coding, hebbian-learning, attention, optimal-control, dynamical-systems]
date_ingested: 2026-04-28
key_finding: "A single objective — minimizing variational free energy on sensations and their causes — subsumes the Bayesian brain, predictive coding, hierarchical inference, efficient/infomax coding, Hebbian cell-assembly learning, biased-competition attention, neural Darwinism, optimal control, and dynamical-systems accounts of cortex; perception, action, and learning are gradient descents on the same scalar."
---

[PDF](../../raw/papers/friston-2010.pdf)

## Overview

Friston's *Nature Reviews Neuroscience* review consolidates the **free-energy principle (FEP)** as a candidate unified brain theory. The thesis: any self-organizing system that remains at non-equilibrium steady state with its environment must minimize a variational upper bound on the *surprise* (negative log evidence) of its sensory exchange with that environment. Surprise itself is intractable, but variational free energy `F` — a function of internal brain states and sensations — is computable, bounds surprise from above, and is therefore the right substitute objective. Three things change `F`: **perception** (changes internal states / the recognition density), **action** (changes the sensory data that get sampled), and **learning** (changes the parameters of the generative model). Each of perception, action, and learning is a gradient descent on the same scalar.

The review's distinctive move is not to introduce the principle (Friston had developed it in technical papers across 2005–2009) but to **deconstruct rival "global" brain theories** — the [[analysis-by-synthesis|Bayesian brain]], hierarchical [[predictive-coding|predictive coding]], the [[efficient-coding-hypothesis|efficient/infomax]] principle, [[hebbian-learning|cell-assembly]] / correlation theory, biased-competition / attention, neural Darwinism, optimal control and reinforcement learning, game theory — and show that each emerges as a special case of FEP optimization under a different read of the same `F`. The recurring claim: every theory that has been called a unified brain theory implicitly optimizes "value" (or its complement, surprise / prediction error / expected cost), and FEP is the principle that makes the unification formal.

## Key Findings

### The free-energy principle proper

- **Self-organizing systems must occupy a small region of state space (low entropy of sensory states), so they must avoid surprising states.** Surprise `−log p(s̃|m)` cannot be evaluated directly because `p(s̃|m)` requires marginalizing over hidden environmental causes. Free energy `F(s̃, μ) = ⟨ln q(ϑ|μ) − ln p(s̃, ϑ|m)⟩_q` is an upper bound on surprise that depends only on (i) sensory states `s̃` and (ii) internal states `μ` encoding a recognition density `q(ϑ|μ)` over hidden causes `ϑ`.
- **Minimizing `F` does two jobs simultaneously.** As `F` = surprise + KL divergence between recognition and true posterior, minimizing `F` w.r.t. internal states `μ` makes the recognition density approximate the conditional density (perceptual inference / [[analysis-by-synthesis]]) and tightens the bound on surprise. Minimizing `F` w.r.t. action `a` selectively samples sensory data consistent with the recognition density — the [[active-inference]] reading.
- **Three formulations of `F`.** (i) Energy minus entropy (statistical-thermodynamic form) — connects to free energy in physics. (ii) Surprise plus divergence — makes the link to Bayesian inference explicit. (iii) Complexity minus accuracy (model-comparison form, after Bishop) — clarifies that minimizing `F` balances how well the recognition density predicts data against how complex the recognition density is. Box 1 of the paper lays out all three; the equivalence is exact and gives FEP its multiple readings.

### Hierarchical message passing as the cortical implementation

- **The "canonical microcircuit" reading (Box 2).** Neuronal activity `μ^(i)` at cortical level `i` encodes conditional expectations of hidden states; activity `ξ^(i)` encodes precision-weighted prediction errors. Forward connections between cortical areas convey prediction errors (superficial pyramidal cells); backward connections convey predictions (deep pyramidal cells). The two equations
  
  `μ̇^(i) = D μ^(i) − ∂_μ̃ ε^(i)ᵀ ξ^(i) − ξ^(i+1)`
  
  `ξ^(i) = Π^(i) (μ̃^(i) − g^(i)(μ̃^(i+1)))` (with analogous equation for state errors)
  
  describe respectively **recognition dynamics** (gradient descent on `F` over expectations) and **prediction error formation**. Synaptic plasticity `θ̇ = −∂_θ ε^Tξ` is a gradient descent on `F` over generative parameters and turns out to be **formally identical to a Hebbian rule** — cell assemblies are what FEP-driven plasticity produces.
- **Asymmetric forward / backward connections** — predicted by FEP and observed in real cortex (forward = driving, backward = modulatory) — fall out of the reciprocal exchange of prediction errors and predictions, and match Adaptive Resonance Theory's resonance picture in form.
- **Precision = synaptic gain = attention.** The precision matrices `Π^(i)` (inverse covariance of prediction errors at level `i`) modulate the impact of error units on conditional expectations. Optimizing precision corresponds to **synaptic gain control**, and links FEP directly to biased-competition / attentional gain models (Desimone-Duncan, Reynolds-Heeger), neuromodulator ([[dopamine|dopamine, ACh]]) function, and synchrony as a precision-encoding mechanism. This is the cleanest concrete neural prediction the review makes: attention is the optimization of precision, and precision is implemented as gain modulation on prediction-error units.

### Subsumption of rival theories

- **[[analysis-by-synthesis|Bayesian brain]] (Knill, Pouget, Lee-Mumford, Kersten-Mamassian-Yuille).** Identical to FEP under the reading that the brain encodes a recognition density that approximates the posterior. FEP adds the variational machinery that makes this trainable in continuous-time hierarchical models.
- **[[predictive-coding|Hierarchical predictive coding]] ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]], Mumford 1992).** A direct implementation of FEP under Gaussian noise assumptions. The Rao-Ballard objective is a Gaussian-specialized variational free energy with explicit precision-weighting `(1/σ², 1/σ²_td)` of prediction errors at each level.
- **[[efficient-coding-hypothesis|Efficient / infomax coding]] (Barlow 1961, Linsker 1988, Atick 1992; Bell & Sejnowski 1995, Olshausen & Field 1996, Simoncelli & Olshausen 2001).** FEP recovers infomax as the special case where action is absent: maximizing mutual information between sensory states and conditional expectations is equivalent to minimizing complexity − accuracy (the third formulation of `F`). The empirical priors implied by [[sparse-coding|sparse coding]] (heavy-tailed / kurtotic) are MaxEnt priors registering an additional constraint; FEP is then `infomax + a Jaynesian sparsity constraint`.
- **[[hebbian-learning|Cell-assembly / correlation theory]] (Hebb 1949, von der Malsburg 1973, Singer-Gray 1995).** Synaptic plasticity that descends `F` is formally Hebbian: when the parameters of a generative-model expectation are mixed with presynaptic predictions and postsynaptic prediction errors are highly correlated, weights grow to suppress error. The "extra" content of correlation theory beyond Hebb — synchrony as the carrier — maps onto FEP's precision encoding (synchronous presynaptic input lowers postsynaptic time constants and increases gain).
- **Biased competition / attention (Desimone & Duncan 1995, Reynolds & Heeger 2009).** Attention = optimization of precision = optimization of synaptic gain on prediction-error units. Neuromodulators (dopamine, acetylcholine, NA) encode the precision/saliency of prediction errors; this links FEP to the [[divisive-normalization|Reynolds-Heeger normalization]] account of attention and to the divisive-normalization computational primitive that survives across modalities and species.
- **Neural Darwinism (Edelman 1989; Friston, Tononi et al. 1994).** Innate value is a prior expectation about which sensory states the agent will visit. Selective processes within an individual's brain (synaptic selection by experience-dependent reentrant signaling) correspond to the same gradient on `F` over generative parameters; selection over evolutionary timescales fixes the priors that selection over developmental timescales tunes.
- **Optimal control / reinforcement learning (Sutton-Barto, Watkins, Schultz, Daw-Doya).** Value is the negative surprise of a state under the agent's prior expectations. The Bellman equation is the dynamic-programming statement of consistency between value and expected next-state value; FEP recasts it as the agent's prior about its own state-occupancy distribution. **Reward is not exogenous** in FEP — it is the expression of a heritable prior about which states the phenotype expects to occupy. Free-energy minimization upper-bounds expected cost, so FEP is consistent with optimal control without taking value/cost as primitive.
- **Game theory / behavioral economics.** Optimal decisions under uncertainty (Bayesian decision theory) are decisions that minimize expected cost; FEP again upper-bounds this by free energy. Game-theoretic notions of equilibrium fall out of joint optimization of free energies across interacting agents.
- **Dynamical-systems / [[attractor-dynamics|attractor-based]] accounts (Friston 1997, Tsuda 2001, Rabinovich 2008, Freeman, Maturana-Varela's autopoiesis).** Priors expressed as cost functions on hidden-state motion induce attractors in the state space the agent occupies. Itinerant / metastable / winner-less-competition dynamics are the multi-attractor correlate of priors over state-trajectories; the [[explore-exploit-tradeoff|exploration / exploitation tension]] becomes the dynamical question of whether the agent's priors induce stable fixed points or itinerant orbits. Figure 3's mountain-car example demonstrates this concretely: a destabilizing prior (negative friction in the cost function) forces the car to leave its starting basin and discover the goal attractor.

### The cued reaching example (Figure 2)

The clearest concrete demonstration in the review. A two-jointed arm with proprioceptive and visual sensory channels has a generative model whose hidden states represent target location and joint angles, with a prior that includes an "elastic band" coupling the fingertip to the cued target. Recognition dynamics infer hidden states; action minimizes free energy by reducing visual and proprioceptive prediction errors; the elastic-band prior makes the fingertip drift toward the target without an explicit cost-of-error or trajectory plan. Figure 2 shows the trajectory emerging from minimization of `F` alone, without a separate motor planner. This is FEP's proposed unification of motor control with perception: motor commands are the expressions of priors that, when minimized, the body fulfills. Computational motor control (Wolpert & Kawato, Todorov) becomes a special case where the priors encode trajectory cost rather than goal location.

### The dark-room problem and priors

Friston's response to the [[dark-room-problem|dark-room objection]] is built into FEP from the start: agents avoid surprising states, and the set of unsurprising states for an organism is determined by *its phenotype's priors*, which are themselves heritable / specified by natural selection. A fish in a dark room is surprising (its phenotype expects water); a mole in a lit room is surprising (its phenotype expects darkness). The framework therefore does not predict that any agent will seek a dark room — it predicts that each phenotype seeks the states its priors expect, and these priors have been selected to match the niche the phenotype occupies.

This is the place where FEP is most often misread as either trivial ("of course agents prefer expected states") or vacuous ("priors do all the work"). The review's response, sharpened in later work, is that the priors are **constrained** — they must be consistent with the phenotype's survival, which makes the prior-discovery problem the deep open question, and the same one [[jaynes-1957-maxent-statistical-mechanics|Jaynes]] flagged for MaxEnt: which sufficient statistics should the prior register?

## Methods

A review article — no original empirical or simulation results, but it presents:
- Box 1: the formal definition of variational free energy and the three equivalent re-expressions.
- Box 2: a candidate cortical message-passing scheme (forward errors, backward predictions, synaptic plasticity rule) for hierarchical Gaussian models, drawn from Friston (2008) *PLoS Comput. Biol.* "Hierarchical Models in the Brain."
- Figure 1: a birdsong-recognition simulation (perceptual inference + categorization via a Lorenz-attractor generative model).
- Figure 2: the cued-reaching simulation (action emerges from FEP minimization with goal-location priors).
- Figure 3: the mountain-car problem solved by destabilizing priors (negative friction in the cost function).
- Figure 4: a "tree" linking FEP to nine other "global" brain theories with the variable being optimized in each.

## Implications

### For the wiki's organizing thesis

FEP is the most ambitious unification of perception, action, and learning under a single objective in modern theoretical neuroscience. Its formal commitment to **the same scalar `F` being minimized over recognition, generative, and action variables** is the closest existing framework to the wiki's organizing thesis (closed-loop sensorimotor control as the primary substrate). The cued-reaching example (Figure 2) is the FEP statement of that thesis: action is not a separate module but an additional variable that the agent uses to reduce the same surprise that perception and learning reduce.

The two ways FEP **falls short** of the wiki's thesis are well documented:
1. **Architecture.** Most active-inference implementations require modular architecture (separate components for prior specification, action selection, planning) — undermining the "emergence from simple rules" character that [[li-2024-prediction-noise-reward|PaN]] and other minimalist closed-loop accounts achieve. PaN replaces FEP's prior + recognition + action triad with prediction + noise, getting closed-loop control for free from instability of the dark-room state.
2. **Constraint-discovery.** FEP says the agent has priors and minimizes free energy under them; it does not say where the priors come from. The deep open question — which constraints natural selection registers in the genome that then constrain the developmental construction of the cortex's generative model — sits *outside* FEP. The control-theoretic reading of [[Degeneracy]] in this wiki is one specific answer (genes specify nonlinear feedback control algorithms whose limit-cycle attractors are conserved despite microscopic configuration), but FEP itself is silent on it.

### For predictive coding and the Helmholtz lineage

FEP is the **explicit generalization** of the [[helmholtz-machine|Helmholtz machine]] / [[rao-ballard-1999-predictive-coding|Rao-Ballard]] objective to embodied agents. The Helmholtz machine optimizes free energy over recognition (φ) and generative (θ) parameters; Rao-Ballard adds online gradient-descent dynamics in continuous time on the recognition variables; Friston adds **action** as a third variable that minimizes the same objective by changing the data the agent samples. This three-way unification is FEP's distinctive contribution.

Mechanistically, FEP inherits the Helmholtz separation of recognition (forward, prediction-error-carrying) and generative (backward, prediction-carrying) pathways; this is the canonical-microcircuit reading. The dendritic-microcircuit lineage ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] etc.) provides one biophysical implementation of the prediction-error / prediction split as an apical-vs-basal compartment split within single neurons. FEP is thus consistent with both the Helmholtz wake-sleep lineage and the dendritic credit-assignment lineage; whether the brain actually implements `F`-minimization through wake-sleep, dendritic compartments, or some combination is an open empirical question.

### For attention and neuromodulation

The cleanest concrete neural prediction in the review: **precision = synaptic gain on prediction-error units = attentional modulation = neuromodulator action**. This converts the otherwise-fuzzy hand-wave "dopamine encodes uncertainty" into the formal claim that dopamine (and ACh, NA) modulates the gain of specific cell populations carrying prediction errors, with the gain set to match the inverse variance of the error. The downstream literature (Yu & Dayan 2005 on ACh and NA; Friston 2009 on dopamine and precision; Adams-Stephan-Brown 2013 on positive symptoms of schizophrenia as aberrant precision) builds directly on this framing.

### For the dark-room problem

FEP's resolution of the [[dark-room-problem|dark-room objection]] — agents seek phenotype-expected states, not maximally predictable states — passes the buck to the prior-discovery problem. This is the deeper of the two routes to the same problem, the other being [[li-2024-prediction-noise-reward|PaN's]] noise-induced instability of the zero-signal state. The two are not exclusive: priors set the attractor landscape, noise prevents collapse to trivial fixed points within it.

## Connections to Existing Knowledge

### Predecessors

- **[[helmholtz-machine|Helmholtz Machine]] ([[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel 1994]])** introduced variational free energy as the objective for unsupervised connectionist learning. FEP is the embodied / continuous-time generalization. The Helmholtz free energy and Friston's `F` are the same object; the Helmholtz machine optimizes it offline by [[wake-sleep-algorithm|wake-sleep]], FEP optimizes it online by gradient descent.
- **[[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]]** specialized the Helmholtz framework to continuous Gaussian latents and online gradient dynamics for vision. The Rao-Ballard objective with explicit precision-weighting `(1/σ², 1/σ²_td)` is a Gaussian-special case of FEP. The "predictive coding" community's instantiation of FEP is essentially Rao-Ballard with one extra degree of freedom (action).
- **[[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]** placed Bayesian inference on a variational footing. FEP is the local-recognition specialization of MaxEnt inference applied to a generative model with hidden causes and (in the embodied case) actions. The dark-room objection inherits its sharpened form from MaxEnt: which constraints does the system register?
- **Hebb (1949), von der Malsburg (1973)** for the cell-assembly / correlation-theory thread: Friston's plasticity rule reduces to Hebbian learning when the activity term is mixed with a presynaptic prediction.

### Companion / sibling frameworks

- **[[active-inference|Active Inference]]** is FEP applied to embodied agents. The active-inference page should cite Friston 2010 as the principal source for the framework, with the [[helmholtz-machine|Helmholtz-machine]] and [[rao-ballard-1999-predictive-coding|Rao-Ballard]] as the predecessors.
- **[[predictive-coding|Predictive Coding]]** is the perceptual restriction of FEP. With Gaussian noise, the predictive-coding objective is exactly FEP's free energy; the difference is whether action is allowed as an additional variable.
- **[[variational-free-energy|Variational Free Energy]]** is the mathematical object FEP minimizes. The same object as the ELBO in VAEs and the Helmholtz free energy in connectionist generative learning; FEP is the principled commitment to optimizing it across recognition, generative, and action variables.
- **[[analysis-by-synthesis|Analysis-by-Synthesis]]** is the conceptual root: FEP is the embodied / continuous-time / variational specialization of the Helmholtzian view that perception is inversion of an internal generative model.

### Downstream / contrasted

- **[[li-2024-prediction-noise-reward|Li et al. (2024) PaN]]** is positioned (by its authors) explicitly *against* active inference: closed-loop reward-seeking from local prediction + noise without priors, without an action-selection module, without optimization toward Bayes-optimality. The contrast sharpens what FEP commits to (priors) and what PaN replaces those commitments with (noise-induced instability).
- **The [[credit-assignment|dendritic credit-assignment]] lineage** (Sacramento 2018, Payeur 2020, Greedy 2022, Francioni 2026) provides an alternative biological implementation of the prediction-error / prediction split that FEP requires. Whether dendritic predictive plasticity is a biophysical implementation of FEP's gradient on `F`, or a parallel framework, remains an open question.
- **[[computation-through-dynamics|Computation Through Dynamics]] / [[force-learning|FORCE]]** lineage takes a different stance: trained recurrent dynamics carve task-relevant trajectories out of a chaotic reservoir. FEP commits to a *generative model* and a *recognition density*, both of which CTD work generally avoids. Reconciling the two — is CTD-style trained dynamics a special case of FEP minimization with the right prior, or a categorically different framework? — is open.

## Open Questions Raised

1. **Where do the priors come from?** FEP says agents minimize free energy under heritable priors but does not specify the prior-discovery process. This is the deep open question — analogous to the constraint-discovery problem in MaxEnt — and is the place where the wiki's control-theoretic reading of [[Degeneracy]] (genes shape feedback control algorithms; conserved limit-cycle attractors emerge) and FEP's "natural selection sets the priors" answer are competing or complementary stances. Which is correct?
2. **Does the brain actually compute `F` in any concrete sense?** FEP is consistent with multiple biophysical implementations (wake-sleep / Helmholtz / dendritic predictive plasticity). What experimental signature would discriminate them? The cleanest candidate is the precision = synaptic gain mapping — does cortex actually adjust gain on superficial pyramidal cells in proportion to inverse error variance? Recent mouse-V1 work (Keller-Mrsic-Flogel 2018) provides preliminary support but hasn't tested the precision-as-gain claim directly.
3. **Is the "tree of theories" subsumption real or aspirational?** Each theory's correspondence to FEP under different reads of `F` is mathematically defensible, but the biological commitments differ. Is FEP the actual unifying principle of cortex, or a unifying *language* for re-describing existing theories without making predictions distinguishable from them?
4. **How does FEP scale with the constraint-discovery problem?** A real organism's prior is structured (objects, faces, conspecifics, danger). The hierarchical generative models that FEP requires must therefore be structured / compositional. How much of this structure is genetically specified vs. developmentally constructed? Neural Darwinism and FEP both invoke selection but at different timescales — unresolved.
5. **Is the precision = attention claim experimentally distinguishable from gain-modulation accounts that predate FEP** (Reynolds-Chelazzi-Desimone 1999, Reynolds-Heeger 2009)? FEP frames attention as variational optimization; the gain-modulation accounts frame it as biased competition. Empirical signatures may overlap.
6. **Mountain-car-style "destabilizing priors" as the FEP answer to exploration** — does this generalize to real-world animals with rich sensory niches? Or do destabilizing priors collapse into the same kind of ad-hoc engineering that FEP was meant to dispense with?
7. **How does FEP relate to [[computation-through-dynamics|Computation Through Dynamics]]?** CTD-style trained recurrent dynamics — fixed points, line attractors, rotational dynamics — could in principle be derived as FEP minimizers under the right priors on hidden-state trajectories. But the CTD framework is largely silent on generative models; it works with stimulus → activity → behavior mappings. Is there a real reconciliation, or do FEP and CTD operate in different conceptual layers?
8. **The dark-room resolution via priors hides the deeper question.** If priors are heritable and selected, then FEP's claim to be a "principle" of intelligence reduces to a claim about evolutionary adaptation. The interesting work is in the prior-discovery process, which FEP off-loads to natural selection. This is consistent with the wiki's evolutionary thesis (genes encode behavior by shaping nonlinear feedback control algorithms) but undercuts FEP's claim to be the *single* unifying principle.

## Sources Cited Forward

This source is the principal citation for [[free-energy-principle|the Free-Energy Principle]] as a framework, [[active-inference|Active Inference]] (it is the canonical FEP review for the active-inference framing), and is a major secondary citation for [[predictive-coding|Predictive Coding]] (FEP's recasting), [[variational-free-energy|Variational Free Energy]] (FEP's commitment to it as objective), [[hebbian-learning|Hebbian Learning]] (Hebbian rule from gradient on `F`), [[efficient-coding-hypothesis|Efficient/Infomax Coding]] (FEP recovers it as a special case), [[natural-image-statistics|Natural Image Statistics]] (FEP as the unifying lens across optimization criteria), [[dark-room-problem|Dark Room Problem]] (priors as the resolution), [[attractor-dynamics|Attractor Dynamics]] (priors-as-cost-functions induce attractors), and [[divisive-normalization|Divisive Normalization]] (precision-weighted attentional gain).

## See Also

- [[karl-friston|Karl Friston]] — author
- [[free-energy-principle|Free Energy Principle]] — primary concept page
- [[active-inference|Active Inference]] — framework page
- [[variational-free-energy|Variational Free Energy]] — mathematical object
- [[predictive-coding|Predictive Coding]] — perceptual restriction
- [[helmholtz-machine|Helmholtz Machine]] — predecessor
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — predecessor
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — predecessor
- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — inference-theoretic foundation
- [[dark-room-problem|Dark Room Problem]] — the standard objection
- [[efficient-coding-hypothesis|Efficient Coding Hypothesis]] — subsumed under FEP
