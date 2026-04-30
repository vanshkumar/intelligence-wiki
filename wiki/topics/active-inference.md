---
title: "Active Inference"
type: theory
aliases: ["active inference framework"]
tags: [predictive-coding, free-energy, perception, action, bayesian, maximum-entropy]
source_count: 6
last_updated: 2026-04-29
status: emerging
---

Active inference is a theoretical framework proposing that living organisms follow a single imperative: **minimizing the surprise of their sensory observations**. It extends [[Predictive Coding]] from perception to action — when there's a discrepancy between prediction and observation, the organism can either change its beliefs (update internal model) or change the world (take an action that produces input matching its prediction).

Active inference is the closest existing theoretical framework to a control-first view of intelligence: it treats perception and action as two sides of the same closed-loop process. However, its implementations tend to require modular architecture (separate components for planning, action selection, etc.), which limits the "emergent from simple rules" character that [[li-2024-prediction-noise-reward|PaN]] demonstrates. PaN achieves closed-loop control behavior from simpler ingredients — local prediction + noise — without the additional apparatus active inference typically requires.

## Relation to Predictive Coding

Active inference is often described as the action-oriented extension of predictive coding. Where predictive coding explains perception (updating beliefs to match sensory input), active inference explains behavior (acting on the world to make sensory input match beliefs).

The framework is closely associated with [[karl-friston|Karl Friston]]'s [[free-energy-principle|free-energy principle]] (FEP), which casts perception, action, *and* learning as gradient descents on the same variational free energy. [[friston-2010-free-energy-principle|Friston (2010)]] is the canonical statement of active inference inside FEP as a unified brain theory: minimize `F` over recognition variables (perception), action (control), and generative parameters (learning) — three gradient descents on the same scalar.

## Historical root: the Helmholtz machine

Active inference's formal backbone — variational [[Variational Free Energy|free energy]] as an upper bound on negative log-evidence — was introduced into connectionist learning by [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] as the **Helmholtz free energy** in the [[Helmholtz Machine]]. The Helmholtz machine addresses perception and learning (minimize `F` with respect to activation and weight variables); active inference adds **action** as a third variable the agent can use to further reduce `F` by changing its own sensory distribution. The three-way unification — perception = minimize F over activations, learning = minimize F over weights, action = minimize F over controls — is Friston's extension of the Helmholtz variational framework. See [[Analysis-by-Synthesis]] for the broader intellectual lineage.

## Inference-theoretic foundation: MaxEnt

Active inference inherits its variational form — `⟨E⟩_Q − H[Q]`, an upper bound on negative log-evidence — from the general [[maximum-entropy-principle|maximum-entropy]] inference framework of [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]. In Jaynes's framework, the "implicit prior" is the MaxEnt distribution under whatever constraints (sufficient statistics) the system has registered; free-energy minimization is the local-recognition specialization to a generative model with hidden causes and (in active inference) actions. This matters for the dark-room and exploration objections: from the MaxEnt angle, an agent that registers richer constraints over time has a *higher*-entropy prior, not a lower one. The dark-room agent has impoverished its constraint set — the opposite of what a constraint-extending intelligence does. The constraint-discovery problem (which sufficient statistics to register over evolutionary and developmental time) is not addressed by free-energy minimization alone and represents the deep open question that active inference inherits unresolved from its Jaynesian roots.

## Criticisms

- **Computational cost**: Active inference models require components with separate roles and are computationally expensive to implement
- **Difficulty of understanding**: Critics note these models can be hard to build or understand (Biehl et al., 2021)
- **Not emergent**: Most active inference models do not operate on emergent principles — they have separate modules for action selection, planning, etc., which undermines claims of biological plausibility
- **Scalability**: Scaling active inference models remains an ongoing challenge
- **Noise assumptions**: Active inference and the free energy principle assume that internal noise can be **averaged over** to arrive at long-term behavior. PaN challenges this by showing that noise is **necessary** and cannot be averaged away.

## Critique: still in the coding frame ([[brette-2018-coding-metaphor|Brette 2018]])

Active inference partially addresses Brette's circular-causality critique of static [[neural-coding|coding]] frameworks — perception, action, and learning are all driven by the same scalar `F`, and action is in the loop rather than tacked on after a perceptual encoder. But Brette argues active inference still operates within the coding metaphor in two important senses:

- **The generative model retains the latent-cause framing.** `F` is defined over a generative model `p(o, s)` that maps hidden states to observables. Agents act to fulfill predictions about preferred sensory states. The hidden states `s` face the same [[neural-coding|symbol grounding problem]] that Brette diagnoses for predictive coding: how does the organism know what its `s` refers to? Active inference points to heritable phenotype-specific priors as the source — but this re-locates rather than dissolves the question.
- **Action is in the service of an internal generative model**, not a primitive of subjective physics. In [[subjective-physics|subjective physics]] / [[sensorimotor-contingencies|sensorimotor contingencies]], action *defines* the lawful structure that perception engages with — perception is engagement with the contingencies that actions reveal. In active inference, action is a tool for fulfilling predictions of a pre-existing generative model. The two readings are subtly but importantly different about what role action plays.

What survives Brette's critique: the *coupled-loop dynamical-systems* aspect of active inference is consistent with subjective physics. Models that compute action and perception as gradient flows on a shared scalar are categorically the right kind of structure (vs. a perceptual encoder feeding a separate decision-making module). The contested move is the specific *generative-model* parameterization of that scalar.

The empirical signature that would distinguish the two readings: in subjective physics, the lawful relations between observables and actions are direct objects of learning; in generative-model active inference, only the latents-to-observables mapping is. A direct empirical test of this distinction has not been done.

## Contrast with PaN

[[li-2024-prediction-noise-reward|Li et al. (2024)]] shares active inference's idea that actions minimize predictive errors, but differs in key ways:
- PaN does **not** aim to explain or generate Bayes-optimal behavior
- PaN does **not** optimize with respect to any predefined utility function
- PaN's continuous noise injection **prevents** optimality and is **necessary** for its key behaviors
- PaN operates on emergent principles with no separate modules

## Sources

- [[friston-2010-free-energy-principle|Friston (2010)]] — the canonical review. Establishes active inference as the embodied instantiation of the free-energy principle: action minimizes `F` by selecting sensory data consistent with the recognition density. Lays out the three readings of `F`, the canonical-microcircuit hierarchical message-passing implementation, the precision = synaptic gain = attention identification, and the resolution of the dark-room problem via heritable phenotype-specific priors. Subsumes nine "global" brain theories (Bayesian brain, hierarchical predictive coding, efficient/infomax coding, cell-assembly / correlation theory, biased competition, neural Darwinism, optimal control, game theory, dynamical-systems accounts) under FEP.
- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — positions PaN as distinct from active inference
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — introduces the variational [[Variational Free Energy|free energy]] that active inference later generalized to embodied agents
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — the perceptual-only predecessor to active inference. Friston's free-energy principle generalizes the Rao-Ballard objective from perceptual inference (update beliefs to match sensations) to embodied control (also act to make sensations match beliefs). The Rao-Ballard precision-weighting of prediction errors `(1/σ², 1/σ²_td)` is the same precision concept that Friston later recasts as attentional modulation
- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — the inference-theoretic foundation. Establishes that the `⟨E⟩ − H` variational form is the Lagrangian for MaxEnt inference; active inference is the embodied / recurrent specialization. Sharpens the dark-room objection: constraint-extending agents have *higher*-entropy priors than constraint-impoverishing ones
- [[brette-2018-coding-metaphor|Brette (2018)]] — critique: active inference partially addresses the static-coding problem (circular causality, action-in-the-loop) but retains the generative-model framing and so inherits the [[neural-coding|symbol grounding problem]]. Action in active inference fulfills generative-model predictions; in [[subjective-physics|subjective physics]] / [[sensorimotor-contingencies|sensorimotor contingencies]], action defines the lawful structure that perception engages with. The coupled-loop dynamical-systems aspect of active inference survives reinterpretation; the generative-model parameterization is contested.
