---
title: "Preparatory Activity"
type: concept
aliases: ["motor preparation", "delay-period activity", "initial condition hypothesis"]
tags: [motor-cortex, dynamical-systems, ctd, initial-conditions]
source_count: 2
last_updated: 2026-04-22
confidence: established
---

**Preparatory activity** is the neural activity during the delay period between cue and movement in instructed-delay motor tasks. In [[Computation Through Dynamics|CTD]] framing, this activity is the **initial condition** that seeds the movement-period dynamics: where the population state sits at the go cue determines the trajectory it then traces through state space to produce muscle activity.

Reviewed in [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]]; the canonical empirical and modeling work is from Churchland, Shenoy, Kaufman, Ames and collaborators over 2006–2020.

## The Initial-Condition Hypothesis

Two competing framings for what preparatory activity is:

1. **Representational**: prep activity is a subthreshold version of movement-period activity — the same representation, below the threshold for triggering movement.
2. **Initial-condition (CTD)**: prep activity sets up an initial state in a dynamical system; movement-period dynamics evolve from that state, governed by local circuit dynamics plus inputs from other regions.

The initial-condition hypothesis is favored empirically ([[vyas-2020-computation-through-dynamics|Vyas et al. 2020]] review the evidence). Key results:

- **Different reaches, different preparatory states.** Preparatory activity is tuned to upcoming movement direction, distance, and speed (Churchland, Santhanam, Messier & Kaletka). Qualitatively similar movements have similar preparatory states.
- **Preparation-time benefits.** More delay ⟹ faster reaction times. The initial-condition hypothesis predicts this: a better-positioned initial state requires less time to evolve into movement (Afshar 2011, Ames 2014).
- **Intracortical microstimulation during preparation causes reaction-time penalty** (Churchland & Shenoy 2007a), consistent with perturbing the initial condition.
- **Preparation is not always required.** Ames et al. (2014) showed that movements with no delay bypass the preparation process, but downstream population response is largely conserved — the process can be compressed if necessary.
- **Discrete attractor dynamics underlie preparation** (Inagaki et al. 2019). In mouse ALM, delay-period activity moves toward stable fixed points corresponding to movement directions, and optogenetic perturbation either collapses back to the fixed point (robust) or "hops" to the other fixed point (producing incorrect actions).

## Output-Null Structure

The puzzle: preparatory activity is large and movement-tuned. Why doesn't it cause movement?

Answer: preparation is structured to lie in the **null space** of the motor-output readout. See [[Null Space Coding]]. Activity along output-null dimensions is behaviorally informative without driving muscles; movement begins when activity rotates from null into output-potent dimensions (Kaufman 2014, Elsayed 2016, Stavisky 2017a, Li 2016).

## Preparation as Chaos Suppression

[[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] propose a specific dynamical reading of what preparation *is*. To produce a one-shot (non-periodic) sequence in a [[force-learning|FORCE]]-trained recurrent network, the network must be brought to a fixed point before the sequence starts — an auxiliary readout provides a constant input that induces this fixed point, quenching the chaotic activity that otherwise dominates the spontaneous network. Sussillo & Abbott connect this directly to Churchland et al. (2006): the sharp drop in neural variability in motor and premotor cortex just before movement has exactly this character — a chaotic state being quenched into a prepared initial condition from which the movement trajectory then evolves. Preparation, in this reading, is literally **chaos suppression**, and the prepared initial condition is the stable fixed point that FORCE's auxiliary readout induces.

This dovetails with the Inagaki et al. (2019) observation of discrete attractor dynamics in mouse ALM: preparation moves the state toward stable fixed points, and perturbations either return to the fixed point or hop to a different one.

## Role in Motor Adaptation

[[vyas-2020-computation-through-dynamics|Vyas et al.]] highlight a striking result: **motor adaptation operates on preparatory dimensions, not movement-period dimensions**.

- In visuomotor rotation (VMR) learning, preparatory states shift across trials to align with the anti-VMR direction, matching the timescale of behavioral adaptation (Vyas et al. 2018).
- Disrupting preparatory state via microstimulation does not affect the stimulated trial's movement but disrupts the *trial-by-trial update* on subsequent trials (Vyas et al. 2020).
- The preparatory subspace is shared between overt reaching and covert BCI contexts, and adaptation transfers between them (Vyas et al. 2018).

Interpretation: learning repositions the initial condition rather than retuning movement-period dynamics. The "learning algorithm" in motor adaptation is implemented at the level of where the trajectory starts, not how it unfolds.

## Relation to the Control Thesis

Preparatory activity is the clearest case in the wiki of the control-theoretic primitive: **the initial condition of a closed-loop sensorimotor controller is itself a computed object**. The prepare → move → sense feedback → update loop is the foundational pattern this wiki treats as the basis of intelligence, and preparation is where upstream context and task rules are integrated into the form the movement dynamics can act on. Adaptation-via-preparation ([[vyas-2020-computation-through-dynamics|Vyas 2020]]) extends the same logic over longer timescales — initial-condition updating is a general mechanism for learning, not a motor-specific trick.

## Sources

- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — review and formalization of the initial-condition hypothesis under CTD; motor adaptation as preparatory-state updating.
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — preparation as chaos suppression: FORCE one-shot-sequence training requires a fixed-point-inducing input before the sequence; directly connects to the Churchland et al. (2006) drop in neural variability at movement onset.
