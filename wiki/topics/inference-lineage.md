---
title: "Inference Lineage: From MaxEnt to the Free Energy Principle"
type: theory
aliases: ["variational inference lineage", "free energy lineage"]
tags: [inference, bayesian-brain, predictive-coding, free-energy, helmholtz]
source_count: 4
last_updated: 2026-05-01
status: emerging
---

The lineage from Jaynes's MaxEnt principle (1957) through to Friston's Free Energy Principle (2010) is the wiki's clearest example of a normative theoretical program: a single variational objective, progressively elaborated, claimed to subsume perception, learning, and (eventually) action.

This page tracks what the lineage *establishes* versus what it *normatively asserts*, and is honest about whether the wiki's reading of inference as "one side of the control loop" is derived from these papers or grafted onto them.

## The arc

**[[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]** — MaxEnt as the unique unbiased prior under expectation-value constraints. The variational form `H[p]` subject to `⟨f_k⟩` constraints recovers Boltzmann / Gaussian / canonical distributions without ergodicity. Statistical mechanics is statistical inference; the variational scaffold of everything downstream.

**[[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]]** — Made variational inference *learnable in neural networks*. Separated **recognition network Q** (bottom-up, amortized posterior) and **generative network P** (top-down). Trained jointly by maximizing the variational lower bound on log-likelihood — the negative Helmholtz free energy `F = ⟨E⟩_Q − H[Q]`. Wake-sleep algorithm: two local-learning phases (wake learns generative weights against recognition samples; sleep learns recognition weights against generative hallucinations). Computational ancestor of VAEs, predictive coding, and active inference.

**[[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]]** — Cortical instantiation. Continuous latents and linear-Gaussian generative models in a hierarchy; feedback carries top-down predictions, feedforward carries residual errors `(r − r^td)`. **Online** gradient dynamics (no offline phase). Trained on natural images, recovers V1 simple-cell receptive fields parameter-free. Reinterprets endstopping and other extra-classical-RF effects as residual-error signatures; predicts that disabling feedback eliminates these effects (matches Bolz & Gilbert 1986). Introduces explicit precision weighting `1/σ²` of the two error streams.

**[[friston-2010-free-energy-principle|Friston (2010)]]** — Unification. Any self-organizing non-equilibrium-steady-state system must minimize variational free energy `F`. The same `F` is minimized over recognition variables (perception), generative parameters (learning), **and action variables (control)** — the three-way unification is Friston's distinctive move. Nine "global" brain theories emerge as special cases. Canonical-microcircuit reading: superficial pyramidal cells carry precision-weighted prediction errors upward; deep pyramidal cells carry predictions downward. **Precision = synaptic gain = attention = neuromodulation** — the most concrete neural prediction. Dark-room problem resolved via heritable phenotype-specific priors.

## What the lineage establishes

1. The variational objective `⟨E⟩_Q − H[Q]` is the canonical form for inference under partial information (Jaynes). Both Bayesian and frequentist inference reduce to it under the right reading.
2. The objective is learnable in hierarchical neural networks when recognition is amortized and updates are local (Dayan-Hinton, Rao-Ballard).
3. Under Gaussian specializations, the framework predicts cortical microcircuit structure, prediction-error signaling, and the causal dependence of extra-classical effects on feedback (Rao-Ballard).
4. Action joins perception and learning under a single scalar (Friston), giving a normatively unified read of brain function — *whether or not* this is what real brains compute biophysically.

## What is normative-only

- That cortex *actually computes* variational free energy in any concrete biophysical sense. The framework is consistent with multiple implementations (wake-sleep, dendritic prediction-error plasticity, recurrent settling). No definitive empirical proof exists.
- That precision modulation = synaptic gain = attention. The most testable claim. Keller & Mrsic-Flogel (2018, not yet ingested) provides preliminary support; the full mapping is unverified.
- That the dark-room is "solved" by heritable priors. Logically consistent but pushes the constraint-discovery problem onto natural selection — silent on how priors are actually constructed.

## Honest tensions across the four papers

1. **Does Jaynes's MaxEnt require a generative model?** No. Jaynes works with constraints `⟨f_k⟩` on a distribution; he posits no `p(data | causes)`. The generative-model framing enters with Dayan-Hinton and becomes central thereafter. A system could do MaxEnt inference over observed statistics without ever learning a forward model of causes-to-observables. This is a genuine architectural choice, not a derivation.

2. **Empirical-Bayes (Rao-Ballard) vs. full variational (Friston).** Rao-Ballard is MAP inference over a fixed prior `g(r)` learned via the update rule. Friston's framework allows the recognition density itself to be a variable (`μ` parameters). Often glossed over, formally distinct. Rao-Ballard fixes Gaussian; Friston permits arbitrary expressiveness. Not a contradiction but a design commitment.

3. **Wake-sleep vs. online dendritic prediction-error.** The Helmholtz machine's offline two-phase learning competes with Rao-Ballard's continuous online dynamics. Real cortex almost certainly uses both — the question is when. The dendritic credit-assignment lineage ([[credit-assignment-lineage]]) supplies a candidate biological substrate for the online variant; whether REM sleep actually serves the wake-sleep role is speculative.

4. **Is FEP unfalsifiable?** If every existing theory fits as a special case of `F`, what observations *would* falsify FEP itself? Friston's escape: the canonical-microcircuit predictions (precision = gain; superficial-pyramidal error units; feedback-dependent extra-classical effects) are testable. But the "unified theory" framing risks overshadowing the concrete predictions, making FEP seem like philosophical re-labeling.

5. **Constraint discovery is not solved by any of them.** Jaynes assumes constraints are given (by measurement). Helmholtz / Rao-Ballard learn from data starting from an isotropic prior. Friston defers to natural selection. None addresses *how* an organism decides which sufficient statistics to track. This is the lineage's deepest gap.

## Bearing on the control thesis — does inference require control?

**Honest answer: no, not intrinsically.**

The wiki's organizing thesis treats inference as "one side of the control loop." This reading is *compatible with* the lineage but not *derivable from* it.

- Jaynes's MaxEnt is agnostic about action.
- The Helmholtz machine was designed for unsupervised learning, with no action loop at all.
- Rao-Ballard's V1 model is perception-only; the framework recovers cortical structure without invoking embodied control.
- Only Friston's FEP adds action as a third minimizer of `F`. **This is Friston's distinctive move, not entailed by the variational scaffold.**

The control reading is therefore a **selection** from FEP, not a derivation. A perception-only agent that never acts satisfies FEP; it just won't survive in a dynamic environment. Natural selection (presumably) won't build it — but that's an evolutionary argument, not a mathematical one.

What the lineage does support: *if* you commit to embodied agents minimizing `F` over both internal states and actions, you get a single objective that subsumes perception, learning, and control. That's a strong normative claim, not a weak one. But the framework does not *force* this commitment.

The wiki should treat inference as **partially aligned** with the control thesis — strongly aligned at the active-inference (Friston) end, less aligned at the perception-only (Helmholtz, Rao-Ballard) end, agnostic at the Jaynes end. See ledger pillar P4 for full bookkeeping. Brette's [[brette-2018-coding-metaphor|critique of the coding metaphor]] applies to this lineage — the latent-variable generative-model framing inherits the symbol-grounding problem and is one of the wiki's clearest open tensions.

## Sources

- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]]
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]]
- [[friston-2010-free-energy-principle|Friston (2010)]]

## Related

- [[Maximum Entropy Principle]]
- [[Helmholtz Machine]]
- [[Predictive Coding]]
- [[Free Energy Principle]]
- [[Active Inference]]
- [[Variational Free Energy]]
- [[Analysis-by-Synthesis]]
- [[Wake-Sleep Algorithm]]
- [[Dark Room Problem]]
- [[brette-2018-coding-metaphor|Brette (2018) — coding-metaphor critique]]
- [[control-thesis-ledger|Control thesis ledger]] (pillar P4)
