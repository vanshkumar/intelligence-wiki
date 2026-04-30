---
title: "Free Energy Principle"
type: theory
aliases: ["FEP", "free-energy principle", "Friston's free-energy principle"]
tags: [free-energy, variational-inference, active-inference, predictive-coding, bayesian-brain, unified-theory]
source_count: 2
last_updated: 2026-04-29
status: emerging
---

The **free-energy principle (FEP)** is the claim, articulated by [[karl-friston|Karl Friston]], that any self-organizing system that remains at non-equilibrium steady state with its environment must — to maintain that steady state in the face of fluctuations — minimize a variational upper bound on the *surprise* (negative log evidence) of its sensory exchange with the environment. Surprise is intractable; [[variational-free-energy|variational free energy]] `F` is computable, bounds surprise from above, and is therefore the right substitute objective. The principle's distinctive commitment is that **perception, action, and learning are gradient descents on the same scalar** `F`, taken with respect to recognition (internal-state), action (control-signal), and generative (parameter) variables respectively.

The 2010 *Nature Reviews Neuroscience* review ([[friston-2010-free-energy-principle|Friston 2010]]) is the canonical statement of FEP as a candidate *unified* brain theory: it argues that nine independently-developed "global" brain theories — the Bayesian brain, hierarchical predictive coding, [[efficient-coding-hypothesis|efficient/infomax]] coding, [[hebbian-learning|cell-assembly / correlation theory]], biased-competition / attention, neural Darwinism, optimal control / reinforcement learning, game theory, and dynamical-systems / attractor accounts — are each special cases of FEP optimization under a different read of the same `F`.

## What FEP is, and what it isn't

**FEP is a principle, not a model.** It says nothing about *which* generative model the brain has, *how* it implements `F`-minimization neurally, or *which* priors have been registered. Models that instantiate FEP — hierarchical [[predictive-coding|predictive coders]], the [[helmholtz-machine|Helmholtz machine]], [[active-inference|active-inference]] agents — are FEP's biological commitments; FEP itself is the prior commitment to optimizing variational free energy as the master objective.

**FEP ≠ variational free energy ≠ active inference.**

| | What it is |
|---|---|
| [[variational-free-energy\|Variational free energy]] | The scalar mathematical object: an upper bound on negative log evidence, equivalent to the ELBO. |
| **Free-Energy Principle** | The *normative claim* that biological systems must minimize this scalar to persist as systems. |
| [[active-inference\|Active Inference]] | The framework that operationalizes FEP for embodied agents — adding action as the third variable that minimizes `F`. |

## The three readings of `F` that FEP exploits

Friston (2010) shows that `F` admits three equivalent re-expressions:

- **`F = ⟨E⟩_q − H[q]`** (energy minus entropy). The statistical-thermodynamic form. Connects FEP to physics; `F` is literally a free energy.
- **`F = surprise + KL[q ‖ p_posterior]`** (Bayesian form). Minimizing `F` simultaneously (i) tightens the bound on surprise and (ii) makes the recognition density `q` approximate the true posterior. This is the [[analysis-by-synthesis|analysis-by-synthesis]] reading.
- **`F = complexity − accuracy`** (model-comparison form). Decomposes `F` as the KL between recognition and prior densities (complexity) minus the expected log-likelihood (accuracy). This is the form that connects FEP to the [[efficient-coding-hypothesis|efficient/infomax]] principle.

The tree of theories FEP subsumes uses these three readings — different rivals are seen as optimizing different decompositions of the same `F`.

## Three variables, one objective

FEP's distinctive commitment beyond [[variational-free-energy|variational free energy]] as a perceptual learning objective (the Helmholtz machine's commitment) is that **action is also a variable** that minimizes `F`:

- **Perception** — minimize `F` w.r.t. internal states `μ` (recognition). Corresponds to inferring hidden causes of sensations; the [[predictive-coding|predictive-coding]] reading.
- **Action** — minimize `F` w.r.t. action `a` (control). Corresponds to selectively sampling sensory data that match the recognition density; the [[active-inference|active-inference]] reading.
- **Learning** — minimize `F` w.r.t. generative parameters `θ` (synaptic weights). Corresponds to updating the brain's generative model; reduces to [[hebbian-learning|Hebbian]] gradient descent under the canonical microcircuit assumptions.

The unification is what makes FEP ambitious: a single scalar, three gradient descents on it, no separate modules.

## How FEP subsumes nine "global" brain theories

This is the deconstructive backbone of [[friston-2010-free-energy-principle|Friston (2010)]]:

| Theory | What it optimizes | FEP reading |
|---|---|---|
| Bayesian brain ([[analysis-by-synthesis\|analysis-by-synthesis]], Knill-Pouget) | Posterior over hidden causes | Recognition density `q` approximates posterior; minimize `F` over `μ`. |
| Hierarchical [[predictive-coding\|predictive coding]] ([[rao-ballard-1999-predictive-coding\|Rao-Ballard 1999]]) | Sum of squared prediction errors at each level | Gaussian-special case of `F`; explicit precision-weighting `(1/σ², 1/σ²_td)`. |
| [[efficient-coding-hypothesis\|Efficient / infomax]] coding (Barlow, Linsker, Atick) | Mutual information between input and representation | `F = complexity − accuracy`; maximizing accuracy ≈ maximizing mutual information when complexity is bounded. |
| [[hebbian-learning\|Cell assembly / correlation]] (Hebb, von der Malsburg, Singer) | Coincident activity strengthens synapses | Gradient descent on `F` over weights yields Hebbian rule with prediction-error postsynaptic factor. |
| Biased competition / attention (Desimone-Duncan, Reynolds-Heeger) | Selective gain on attended representations | Optimizing precision (inverse error variance) ≈ optimizing synaptic gain on prediction-error units. |
| Neural Darwinism (Edelman) | Selection of neuronal groups by experience | Plasticity gradient on `F` over `θ`; selection over evolutionary timescales fixes the priors selection over developmental timescales tunes. |
| Optimal control / RL (Sutton-Barto, Watkins) | Expected cumulative reward / value | Value = negative surprise under prior expectations about state occupancy; `F` upper-bounds expected cost. |
| Game theory / decision theory (Camerer, von Neumann) | Expected utility | Optimal decisions minimize expected cost; FEP upper-bounds it. |
| Dynamical-systems / attractor accounts (Tsuda, Rabinovich, Freeman, Maturana-Varela) | Itinerant / metastable trajectories | Priors as cost functions on hidden-state motion induce attractors; itinerant dynamics correspond to priors over state-trajectories. |

The unification is mathematically defensible — each correspondence is exact under stated assumptions — but the biological commitments differ. Whether FEP is the *actual* unifying principle of cortex or a unifying *language* for re-describing existing theories is an open question (see Open Issues below).

## The cortical implementation: hierarchical message passing

FEP's most concrete neural commitment (Box 2 of [[friston-2010-free-energy-principle|Friston 2010]]; Bastos et al. 2012; descendants of [[rao-ballard-1999-predictive-coding|Rao-Ballard]]):

- **Superficial pyramidal cells** carry **prediction errors** `ξ^(i) = Π^(i)(μ̃^(i) − g^(i)(μ̃^(i+1)))` to higher cortical levels via forward connections. The activity of these cells is *what gets reduced* by optimization.
- **Deep pyramidal cells** carry **predictions** `g^(i)(μ̃^(i+1))` to lower cortical levels via backward connections.
- **Recognition dynamics** at each level: `μ̇^(i) = D μ^(i) − ∂_μ̃ ε^(i)ᵀ ξ^(i) − ξ^(i+1)`. Each cortical column performs gradient descent on `F` over its expectation.
- **Synaptic plasticity**: `θ̇ = −∂_θ ε^Tξ`, formally identical to a Hebbian rule with prediction-error post-synaptic signal. Weights grow when presynaptic prediction and postsynaptic prediction error are correlated.
- **Precision matrices `Π^(i)`** encode inverse error variance and modulate the impact of error units on conditional expectations. Precision optimization corresponds to **synaptic gain control** — and this is the single cleanest neural prediction in the framework: attention is the optimization of precision, implemented as gain modulation on prediction-error units.

The asymmetric forward/backward cortical connectivity (forward = driving glutamatergic; backward = modulatory) is *predicted* by FEP rather than postulated.

## Precision and attention

Friston's identification of precision (inverse variance of prediction errors) with synaptic gain on prediction-error units is FEP's most concrete and most testable neural commitment. It connects FEP to:

- **Neuromodulator function.** Dopamine encodes the precision of reward-related prediction errors; acetylcholine and noradrenaline encode contextual uncertainty more broadly. Friston (2009), Yu & Dayan (2005), and downstream work make this concrete.
- **Biased-competition / [[divisive-normalization|normalization]] accounts of attention.** Reynolds-Heeger normalization can be derived as the optimal gain-control mechanism under FEP's precision-weighting.
- **Synchrony as a precision carrier.** Synchronous presynaptic input lowers postsynaptic time constants and increases gain — a biophysical implementation of precision modulation.
- **Aberrant precision in disorders.** Adams-Stephan-Brown 2013 read positive symptoms of schizophrenia as aberrant precision in prediction-error pathways.

## The dark-room resolution and the constraint-discovery problem

The standard objection to surprise-minimization frameworks — the [[dark-room-problem|dark-room problem]] — is that an agent that minimizes prediction error has a trivial solution available: sit in a dark room. FEP's response, built into the framework: agents avoid surprising states, but the set of unsurprising states for an organism is determined by **its phenotype's priors**, which are themselves heritable / specified by natural selection. A fish in a dark room is surprising (its phenotype expects water); a mole in a lit room is surprising (its phenotype expects darkness).

This response is correct but passes the buck: it relocates the substantive question from "why does the agent move" to "where do the priors come from." This is the **constraint-discovery problem** — the same one [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] flagged for [[maximum-entropy-principle|MaxEnt]] inference, transposed into the embodied / evolutionary setting. FEP says agents minimize free energy under the priors they have; it does not say where those priors come from. The wiki's control-theoretic reading of [[Degeneracy]] (genes shape nonlinear feedback control algorithms; conserved limit-cycle attractors emerge despite microscopic configuration) is one specific answer; FEP itself is silent on it.

## Relation to the wiki's organizing thesis

FEP is the closest existing framework to the wiki's organizing thesis — closed-loop sensorimotor control as the primary substrate of intelligence — and the most ambitious attempt at unifying perception, action, and learning under a single objective. Its formal commitment to the same scalar `F` being minimized over recognition, action, and generative variables matches the thesis's core move (action is not a separate module).

Two ways FEP falls short of the thesis:

1. **Architecture.** Most active-inference implementations require modular structure (separate components for prior specification, recognition, action selection). [[li-2024-prediction-noise-reward|PaN]] (Li et al. 2024) replaces FEP's prior + recognition + action triad with prediction + noise, getting closed-loop reward-seeking behavior from instability of the dark-room state without a planner.
2. **Constraint-discovery.** FEP delegates the prior-specification problem to natural selection without further specification. The control-theoretic reading of degeneracy in this wiki — that genes specify nonlinear feedback control algorithms whose conserved macroscopic dynamics produce species-typical behavior with high probability despite unique microscopic configurations — is a candidate answer; FEP does not commit to it.

## Open issues

- **Is FEP empirically distinguishable from its rival frameworks?** Each correspondence in the "tree of theories" is mathematically exact under stated assumptions, but if every other framework can be re-described as a special case of FEP, what unique predictions does FEP make? Critics (e.g., Colombo & Wright 2018) have argued FEP is unfalsifiable as currently stated.
- **The precision = synaptic gain claim** is the most concrete neural prediction. Direct experimental verification — does cortex actually adjust gain on superficial pyramidal cells in proportion to inverse error variance? — has been pursued in mouse V1 (Keller-Mrsic-Flogel 2018; Attinger 2017) but the precision-as-gain claim has not been directly tested.
- **How does FEP relate to [[computation-through-dynamics|Computation Through Dynamics]]?** CTD-style trained recurrent dynamics could in principle be derived as FEP minimizers under priors on hidden-state trajectories. But CTD is largely silent on generative models. Reconciling the two — or showing they're fundamentally different conceptual layers — is open.
- **Does FEP scale with the constraint-discovery problem?** Real organisms have structured priors (objects, faces, conspecifics, danger). The hierarchical generative models FEP requires must therefore be structured / compositional. How much is genetically specified vs. developmentally constructed? FEP and Neural Darwinism both invoke selection but at different timescales; the integration is unclear.
- **The dark-room resolution via priors hides the deeper question.** If priors are heritable and selected, FEP's claim to be a "principle" of intelligence reduces to a claim about evolutionary adaptation. The interesting work is in the prior-discovery process, which FEP off-loads to natural selection.

## Critique: FEP inherits the coding metaphor

[[brette-2018-coding-metaphor|Brette (2018)]] critiques FEP as still operating within the [[neural-coding|coding metaphor]] despite its dynamical-systems and embodied components. The structural argument:

- FEP is defined over a generative model `p(o, s)` where `s` are hidden states and `o` are observables. The recognition density `q(s)` is updated to approximate the posterior `p(s|o)` under the model.
- The hidden states `s` are *coding variables* in the sense Brette critiques: they map causes-of-observables to observables, exactly the parametric description that he argues is the wrong unit of analysis. The right unit is *relations among observables and actions* ([[subjective-physics|subjective physics]]) — relations the organism can directly verify, without latent intermediates.
- FEP-as-unification still requires that the brain "represent" the latents `s`. This re-imports the [[neural-coding|symbol grounding problem]] — how does the brain know what its `s` refer to? — at the principle level.
- FEP's dark-room resolution via heritable phenotype-specific priors is structurally consistent with subjective physics (the priors *are* the lawful structure the organism inherits), but FEP frames the priors as constraints on a generative model rather than as direct relational structure. The framings differ; the predictions might or might not.

What survives the critique:
- The *formal* claim that a single scalar drives perception, learning, and action is structurally compatible with subjective physics. A sensorimotor formulation could in principle be cast as gradient descent on a scalar defined over the lawful structure of sensorimotor relations rather than over generative-model latents.
- The *empirical* claims about cortical microcircuits (forward errors, backward predictions, precision-weighted gradients on `F`) survive as biological observations about cortical signaling that admit either reading.
- The dark-room resolution survives — but Brette would diagnose the problem differently: it isn't that priors prevent agents from seeking dark rooms; it's that "seek dark rooms" requires the kind of disembodied inference framework that subjective physics rejects to begin with.

What's most contested:
- The status of "principle". Brette would argue FEP, like neural coding, is a productive technical framework but not the right framework for theory. The unification under `F` is mathematically real but philosophically less load-bearing than the FEP literature suggests, because it operates within a metaphor whose grounding is the contested question.

## Relationship to other concepts

- **[[variational-free-energy|Variational Free Energy]]** — the mathematical object FEP minimizes; the same object as the ELBO and the Helmholtz free energy.
- **[[active-inference|Active Inference]]** — the embodied / motor instantiation of FEP. Active inference *is* FEP applied to agents that act; FEP is the principle, active inference is the framework.
- **[[predictive-coding|Predictive Coding]]** — the perceptual restriction of FEP under Gaussian noise assumptions.
- **[[helmholtz-machine|Helmholtz Machine]]** — predecessor; FEP generalizes the Helmholtz objective to embodied agents.
- **[[analysis-by-synthesis|Analysis-by-Synthesis]]** — conceptual root; FEP is the embodied / continuous-time / variational specialization.
- **[[maximum-entropy-principle|Maximum Entropy Principle]]** — inference-theoretic foundation; `F` is the Lagrangian whose stationary points are MaxEnt distributions. FEP is the embodied specialization of MaxEnt inference.
- **[[efficient-coding-hypothesis|Efficient Coding Hypothesis]]** — subsumed under FEP's complexity-minus-accuracy reading.
- **[[hebbian-learning|Hebbian Learning]]** — gradient on `F` over weights yields a Hebbian rule with prediction-error post-synaptic signal.
- **[[dark-room-problem|Dark Room Problem]]** — FEP's resolution via heritable priors; relocates the substantive question to constraint-discovery.
- **[[divisive-normalization|Divisive Normalization]]** — Reynolds-Heeger normalization can be derived as the FEP-optimal gain-control mechanism.
- **[[attractor-dynamics|Attractor Dynamics]]** — priors as cost functions on hidden-state motion induce attractors; FEP frames itinerant / metastable dynamics as priors over state-trajectories.
- **[[neural-coding|Neural Coding]]** — FEP inherits the coding-metaphor framing critiqued by [[brette-2018-coding-metaphor|Brette (2018)]]: hidden states `s` are coding variables; the [[neural-coding|symbol grounding problem]] applies. [[subjective-physics|Subjective physics]] is a candidate alternative framing of the same dynamical structure.

## Sources

- [[friston-2010-free-energy-principle|Friston (2010)]] — "The free-energy principle: a unified brain theory?" *Nature Reviews Neuroscience.* The canonical review. Establishes FEP as the variational principle behind nine independently-developed brain theories; presents the three readings of `F`; lays out the canonical-microcircuit hierarchical message-passing implementation; identifies precision with synaptic gain and with attention; resolves the dark-room problem via heritable priors.
- [[brette-2018-coding-metaphor|Brette (2018)]] — critique: FEP retains the coding-metaphor framing (hidden states as coding variables, generative model as parametric input description); inherits the [[neural-coding|symbol grounding problem]]. The unification of perception, learning, and action under a single scalar survives reinterpretation in [[subjective-physics|subjective physics]] terms; the generative-model parameterization is what's contested.
