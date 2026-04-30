---
title: "Predictive Coding"
type: theory
aliases: ["prediction error minimization", "predictive processing"]
tags: [learning-rule, prediction, cortex, perception]
source_count: 8
last_updated: 2026-04-29
status: established
---

Predictive coding is a theory of neural computation proposing that the brain continuously generates predictions about its sensory input and updates its internal model by minimizing **prediction errors** — the discrepancy between predicted and actual neural activity. When embedded in a closed sensorimotor loop (as in [[li-2024-prediction-noise-reward|PaN]]), prediction is not just a perceptual mechanism but the core operation of a control system — the organism predicts, acts, and updates, with prediction error driving both model refinement and action selection.

## Core Idea

In a predictive coding network, each layer maintains a prediction of what the layer it connects to should look like. Prediction errors (the difference between predicted and actual activity) drive learning: both neural activities and synaptic weights update to reduce these errors. All updates are **local** — each neuron only needs information available at its own synapse.

## Prediction Direction

A key architectural distinction exists between two formulations:

**Top-down predictive coding** ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]): Higher, more abstract layers predict lower, more sensory layers. Predictions flow downward, prediction errors flow upward. The energy function has the form:

$$E = \frac{1}{2}(x_0 - s)^2 + \frac{1}{2}\sum_{l=0}^{L-2}(x_l - f(V_l \, x_{l+1}))^2$$

This implies the brain has a **generative model** — abstract representations at the top reconstruct sensory data at the bottom. Requires separate top-down and bottom-up connection pathways.

**Bottom-up predictive coding** (Bogacz et al.): Lower layers predict upper layers through feedforward weights. The energy function has the form:

$$E = \frac{1}{2}(s - x_0)^2 + \frac{1}{2}\sum_{l=1}^{L-1}(x_l - \text{Relu}(W_{l-1} x_{l-1}))^2$$

Architecturally simpler — one set of weights, computation flows bottom-up. Used by the PaN algorithm in [[li-2024-prediction-noise-reward|Li et al. (2024)]].

The real brain likely uses **both directions** simultaneously — the cortex has massive reciprocal connectivity. However, bidirectional models are harder to analyze because convergence requires the whole system to settle into a consistent state.

## Variants

- **Base Predictive Coding (PC)**: Activities run to convergence, then weights update. Requires an external signal to switch between phases.
- **Monte Carlo Predictive Coding (MCPC)**: Adds noise to activity updates. Can infer posterior distributions over latent variables. Explains stimulus-onset reduction in neural variability observed experimentally.
- **Incremental Predictive Coding (iPC)**: Couples activity and weight updates in alternation every timestep, eliminating the need for a convergence signal. Faster than PC with convergence guarantees.
- **PaN (Prediction and Noise)**: Combines MCPC's noise injection (extended to weights) with iPC's coupled updates. Operates in a closed loop with an environment, producing emergent reward-seeking behavior.

## The Rao-Ballard Cortical Model

[[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] is the canonical cortical instantiation of predictive coding. Their model has become the reference architecture against which subsequent predictive-coding proposals are compared. Key elements:

- **Continuous-latent linear-Gaussian generative model.** Image `I = f(Ur) + n` at the lowest level; recursively `r = f(U^h r^h) + n^td` at higher levels. `U` is a matrix of basis vectors; `r` is the cause vector (model neuron activities); `f` is `tanh` or identity.
- **Free-energy / negative-log-posterior objective.** `E = (1/σ²) ‖I − f(Ur)‖² + (1/σ²_td) ‖r − r^td‖² + g(r) + h(U)`, where `g(r)` and `h(U)` are negative-log priors. The two prediction-error terms are weighted by inverse noise variances — the **precision-weighting** that becomes central in Friston's later free-energy formulation.
- **Activity dynamics.** Gradient descent on `E`: `dr/dt ∝ U^T (I − f(Ur)) + (r^td − r) − ½ g'(r)`. Each model neuron integrates a feedforward residual (the part of the input the current estimate doesn't predict), a top-down residual (mismatch between higher-level prediction and current estimate), and a prior decay term.
- **Synaptic learning rule.** Slower-timescale Hebbian rule: `dU/dt ∝ (I − f(Ur)) r^T − λU`. The post-synaptic factor is the **residual prediction error**; the pre-synaptic factor is the activity. This is structurally Hebbian but with a residual-error post-synaptic signal — the same architectural pattern as [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento]] dendritic predictive plasticity, [[dayan-hinton-1994-helmholtz-machine|wake-sleep]] delta-rule learning, and [[sparse-coding|sparse-coding]] dictionary learning.
- **Lateral-interaction equivalent.** For linear `f`, the dynamics can be rewritten with explicit lateral inhibition `Wr` where `W = U^T U`. Predictive feedback can be physically realized either by V2 → V1 cortico-cortical feedback or by V1 horizontal lateral connections — the two are formally equivalent in the linear case. This is also the model's bridge to [[divisive-normalization|divisive normalization]]: repeated subtraction of neighboring activities produces a net effect approximating divisive scaling.

### Empirical predictions

The model was *trained on natural images* and tested against V1 physiology with two principal results:

1. **Simple-cell-like RFs emerge from training.** Level-1 basis vectors after several thousand natural-image patches resemble localized oriented Gabor / DoG filters — the canonical Hubel-Wiesel V1 simple-cell signature. With a kurtotic prior `g(r) = α Σ log(1 + r_i²)`, the wavelet-like RFs of [[sparse-coding|Olshausen-Field 1996]] are recovered exactly inside the hierarchical predictive framework. The simple-cell RFs are a parameter-free emergent property of the training, not a built-in feature detector.
2. **Endstopping and other extra-classical effects emerge as residual-error signatures.** The level-1 *error-detecting* neurons (those carrying `(r − r^td)` to level 2) show endstopping: strong response to a short bar in their RF, suppression when the bar extends into the surround. The mechanism: in [[natural-image-statistics|natural images]], oriented structures tend to extend over `±50` pixels along their dominant orientation (autocorrelation analysis in Fig. 4 of the paper). A long bar can therefore be predicted from the surround context by level 2; a short bar cannot. The endstopped neuron is silent when the input is *typical* of natural-image statistics and fires when it is atypical.

The same framework reproduces orientation-contrast suppression / facilitation, pop-out (single odd-orientation bar in a homogeneous field of orthogonally-oriented bars), and tonic-phase contextual modulation matching Zipser-Lamme-Schiller (1996). All emerge from a single optimization principle (minimize prediction error against natural-image statistics) without separate mechanisms for each effect.

### The feedback-inactivation prediction

The cleanest causal test of the framework: removing the level-2 → level-1 feedback in the model **eliminates endstopping in 82% of model error-detecting neurons**. This matches the cat-striate finding of Bolz & Gilbert (1986) — inactivating layer 6 (the source of feedback to V1) eliminates endstopping — and the Sandell & Schiller (1982) result that cooling V2 dramatically affects layer-6 V1 responses, and the Hupé et al. (1998) figure-ground result.

The cell-type-level prediction is that **layer 2/3 pyramidal neurons** (the source of feedforward axons to higher areas) carry the residual prediction error `(r − r^td)`. This was the most actionable concrete prediction of the paper and has motivated decades of subsequent layer-resolved cortical recording — culminating in mouse V1 work (Keller-Mrsic-Flogel 2018; Attinger 2017; Zmarz & Keller 2016) that has begun to provide direct evidence for prediction-error-like signals in superficial pyramidal cells.

## The Dark Room Problem

A fundamental challenge for predictive coding as a theory of behavior: if the brain minimizes prediction error, the easiest solution is to seek out maximally predictable environments — sitting in a dark room doing nothing. See [[Dark Room Problem]].

## Relationship to Neural Adaptation

Predictive coding at the network level is structurally similar to [[Neural Adaptation]] at the single-neuron level — both encode deviations from an expected baseline rather than absolute values. Adaptation adjusts a neuron's input-output mapping based on recent stimulus history; predictive coding adjusts a layer's representation based on predictions from other layers. The burst-dependent plasticity threshold P̄ in [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] is formally analogous to adaptation — learning is driven by deviations of burst probability from a slowly moving average, not by absolute burst rate.

## Predictive Coding as Credit Assignment

[[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] provide the strongest bridge between predictive coding and [[Credit Assignment]] in the wiki. In their dendritic microcircuit model, each cortical layer contains pyramidal neurons (three compartments: soma, basal, apical) and lateral SST interneurons. The interneurons learn to predict and cancel top-down feedback at the apical dendrite, establishing a **self-predicting state** where apical compartments are silent. When a novel teaching signal arrives at the output, interneurons can't explain it away → prediction errors appear at apical dendrites → these errors propagate backward through the network.

The key result: in the weak-feedback limit, the apical prediction error at layer k is exactly the backpropagated error — the output error multiplied by the chain of derivative and weight matrices. **Predictive coding and backpropagation are not competing theories; they are two descriptions of the same dendritic microcircuit.** The prediction error *is* the credit signal.

This unification has a concrete architectural interpretation: the top-down pathway carries the "actual" feedback signal, the lateral (SST interneuron) pathway carries the "predicted" feedback signal, and the apical compartment computes their difference. All plasticity rules are local dendritic prediction error rules of the form dw/dt = η[φ(u) − φ(v)]r, belonging to the dendritic predictive plasticity family (Urbanczik & Senn 2014).

## Inference-theoretic foundation

The predictive-coding energy function is, formally, the negative log of a Bayesian posterior — prediction-error terms come from the data likelihood, prior terms `g(r)` and `h(U)` from prior beliefs about activities and weights. The choice of `g` is the choice of prior, and in the Jaynesian view ([[jaynes-1957-maxent-statistical-mechanics|Jaynes 1957]]; [[maximum-entropy-principle|MaxEnt principle]]) priors are determined by which sufficient statistics the system has registered: a Gaussian `g(r) = α Σ r_i²` is the [[maximum-entropy-principle|MaxEnt]] prior under a variance constraint; a kurtotic `g(r) = α Σ log(1 + r_i²)` is the MaxEnt prior under a kurtosis-like constraint, which produces sparse codes. Predictive coding is therefore not an idiosyncratic objective but the MAP-inference specialization of MaxEnt inference applied to a hierarchical generative model — the choice of `g` is the choice of which constraint set the prior is registering.

## Historical Lineage: Helmholtz Machine → Rao-Ballard → Free-Energy Principle

Hierarchical predictive coding descends directly from the [[Helmholtz Machine]] of [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]], which first cast unsupervised learning as variational inference in a network with separate top-down (generative) and bottom-up (recognition) pathways. The [[Variational Free Energy|Helmholtz free energy]] they introduced — `F = Σ Q E − H[Q]` — becomes the predictive-coding energy function when the generative model is linear-Gaussian and the recognition distribution is Gaussian at each layer. [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] is the **continuous-latent, vision-specific specialization** of the Helmholtz framework: where Dayan-Hinton 1994 used discrete binary latents and offline wake-sleep training, Rao-Ballard use continuous Gaussian latents and online gradient-descent dynamics, applied directly to natural-image input. [[karl-friston|Friston]]'s [[free-energy-principle|free-energy principle]] ([[friston-2010-free-energy-principle|Friston 2010]]; [[Active Inference]]) further generalizes the Rao-Ballard objective to embodied action — perception minimizes `F` over recognition variables, action minimizes `F` over control variables, learning minimizes `F` over generative parameters. [[friston-2010-free-energy-principle|Friston (2010)]] also makes explicit the canonical-microcircuit reading: superficial pyramidal cells carry prediction errors, deep pyramidal cells carry predictions, and the precision matrices that weight prediction errors are interpreted as synaptic gain — the link between predictive coding, attention, and neuromodulation.

The two architectural commitments that survive the lineage intact are:
- **Separate recognition and generative pathways** with independent weights — the top-down pathway predicts, the bottom-up pathway infers, and the two are not forced to be transposes of each other (as in Boltzmann machines).
- **Local prediction-error learning** — all updates depend only on pre- and post-synaptic activity at each synapse, with the error signal computed from the mismatch between top-down prediction and bottom-up signal.

See [[Analysis-by-Synthesis]] for the broader philosophical and historical context.

## Critique: predictive coding still operates within the coding metaphor

[[brette-2018-coding-metaphor|Brette (2018)]] critiques predictive coding (and the broader [[free-energy-principle|FEP]] family) as still operating within the [[neural-coding|coding metaphor]] despite its dynamical and active components. The argument:

- A generative model `Y = f(X) + noise` maps internal latent variables `X` (the "causes") to observables `Y` (sensory inputs). This is a *parametric description of input statistics* — formally analogous to a Fourier transform or any other compression scheme. The latents are fixed by the form of the generative model, not by anything the organism does.
- Calling the latents *causes* of sensory inputs is a metaphorical extension of the strict-technical sense of cause (one event producing another). The Rao-Ballard latents are not causes in the world the organism interacts with; they are coding variables in the model.
- The organism faces the [[neural-coding|symbol grounding problem]] (Harnad 1990): how does it know what its latents refer to? Predictive coding offers no answer; the latents acquire meaning only via the experimenter's setup of the generative model.
- The right notion of information for an organism, Brette argues, is [[subjective-physics|relations among observables and actions]] — Gibson's invariants, [[sensorimotor-contingencies|O'Regan & Noë's sensorimotor contingencies]] — not generative-model latents.

What survives the critique is the *mechanistic* content of predictive coding: the cortical microcircuit (top-down predictions, bottom-up errors, precision-weighted gradient on `F`) is a coherent description of dendrites, synapses, and inhibitory interneurons that may be correct as biology even if its representational interpretation is contested. The dendritic credit-assignment lineage ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) is the cleanest example: the apical-compartment teaching signal can be read either as "prediction error over latent causes" (Rao-Ballard / FEP framing) or as "residual sensorimotor mismatch routed for local plasticity" (subjective-physics framing). The biology is the same; the framing changes substantially.

The Rao-Ballard *technical* result — that fitting a sparse linear-Gaussian generative model to natural images recovers Gabor-like receptive fields — also survives intact. What's contested is the *interpretation* that V1 is therefore *encoding* the latent causes of natural images, rather than merely *correlating* with statistics that happen to be informative about a class of stimuli.

## Biological Plausibility

Predictive coding is considered more biologically plausible than backpropagation because:
- All updates are local (no need to propagate errors through the full network)
- It naturally accounts for top-down influences on perception
- The prediction error signals map onto known neural response properties
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] show that dendritic prediction errors in mouse visual cortex (Zmarz & Keller 2016, Attinger et al. 2017) are consistent with the self-predicting microcircuit framework

## Sources

- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — the canonical cortical instantiation of predictive coding. Hierarchical generative model with continuous Gaussian latents; feedback carries top-down predictions, feedforward carries residual prediction errors; Hebbian learning of basis vectors; recovers V1 simple-cell receptive fields from natural-image training; explains endstopping and other extra-classical RF effects as residual-error signatures; predicts that disabling top-down feedback eliminates extra-classical effects.
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — historical root: the [[Helmholtz Machine]] introduces variational free-energy learning with separate top-down generative and bottom-up recognition pathways. Rao-Ballard 1999 is the continuous-latent specialization of this framework.
- [[friston-2010-free-energy-principle|Friston (2010)]] — generalizes hierarchical predictive coding to embodied agents under the [[free-energy-principle|free-energy principle]]. Predictive coding becomes the perceptual restriction of FEP under Gaussian noise; the canonical-microcircuit message-passing reading (forward errors / backward predictions / precision-weighted gradient) is the cortical implementation. Identifies precision-weighting with synaptic gain and with attention — the link between predictive coding and neuromodulator function.
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — unifies predictive coding and backpropagation: apical dendritic prediction errors (top-down minus lateral prediction) are analytically equivalent to backpropagated gradients. Realizes the Rao-Ballard prediction-error coding scheme at the dendritic-microcircuit level.
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst probability deviation from adaptive baseline as prediction-error-like signal.
- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — extends predictive coding to closed-loop behavior via PaN (a bottom-up rather than top-down formulation).
- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — supplies the inference-theoretic foundation. The activity prior `g(r)` in predictive-coding energy functions is a [[maximum-entropy-principle|MaxEnt]] prior under whichever constraints the system has registered: Gaussian under variance, heavy-tailed (sparse-coding) under kurtosis. Predictive coding is MAP inference under MaxEnt-shaped priors.
- [[brette-2018-coding-metaphor|Brette (2018)]] — critique: predictive coding's generative model is a parametric description of input statistics (analogous to a Fourier transform), not a relational structure; the latents face the [[neural-coding|symbol grounding problem]]; the right form of information for an organism is [[subjective-physics|relations among observables and actions]], not generative-model latents. The mechanistic content (cortical microcircuit, dendritic apical-compartment teaching signals) survives reinterpretation under a sensorimotor framing; the representational content is contested.
