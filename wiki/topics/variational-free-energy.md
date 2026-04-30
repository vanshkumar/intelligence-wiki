---
title: "Variational Free Energy"
type: concept
aliases: ["Helmholtz free energy", "ELBO", "evidence lower bound", "negative free energy"]
tags: [variational-inference, information-theory, generative-model, predictive-coding, free-energy-principle, maximum-entropy]
source_count: 4
last_updated: 2026-04-28
confidence: established
---

Variational free energy is a tractable upper bound on the negative log-likelihood of observed data under a generative model. Minimizing it simultaneously (a) fits the generative model to the data and (b) tightens an approximate posterior toward the true posterior over hidden causes. It is the formal backbone of [[Analysis-by-Synthesis|analysis-by-synthesis]] as implemented in the [[Helmholtz Machine]], of hierarchical [[Predictive Coding]], and of Friston's Free Energy Principle and [[Active Inference]].

Introduced into connectionist learning by [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] under the name *Helmholtz free energy*; subsequently adopted (with equivalent algebra, different notation) as the **Evidence Lower Bound (ELBO)** in variational autoencoders.

## Definition

Given a generative model with parameters θ, observed data `d`, and hidden causes `α`:

- log-likelihood: `log p(d|θ) = log Σ_α p(α|θ) p(d|α, θ)` — intractable for rich models.
- Energy of explanation α: `E_α(θ, d) = −log p(α|θ) p(d|α, θ)`.
- For any recognition distribution `Q(α)` (typically factorial and parameterized by a separate recognition network with weights φ):

`F(d; θ, Q) = Σ_α Q_α E_α − H[Q]` (expected energy minus entropy)

where `H[Q] = −Σ_α Q_α log Q_α`.

The central identity:

`log p(d|θ) = −F(d; θ, Q) + KL[Q(α) ‖ P(α|d, θ)]`

Since `KL ≥ 0`, `−F(d; θ, Q)` is a **lower bound on the log-likelihood**, tight iff `Q = P` (the true posterior). Equivalently, `F` is an **upper bound on the negative log-likelihood**.

## Why it is tractable

Three properties make `F` easy to compute even when `log p(d|θ)` is not:

1. **No sum over α in the computation of `F`**: because `E_α` is evaluated at a particular sample of the latents, and the expectation is under `Q` (which is chosen to factorize), `F` can be computed in time linear in the network depth and unit count.
2. **Factorial Q**: for `h` binary units per layer, `Q` is specified by `h` numbers per layer, not `2^h − 1`.
3. **Differentiable with respect to both θ and φ**: gradient descent updates both the generative parameters and the parameters of the recognition model that produces Q.

## Two simultaneous jobs

Optimizing `−F(θ, φ)` by gradient ascent does two things at once:

1. **Fits the generative model**: increasing `log p(d|θ)` (the thing we actually care about).
2. **Tightens the posterior approximation**: decreasing `KL[Q ‖ P]` (making recognition more accurate).

There is a subtle third effect: because both `log p(d|θ)` and `KL[Q ‖ P]` depend on θ, the bound encourages the generative model to **re-shape itself so that its true posterior is close to something representable by the restricted class of Q** — i.e., the network prefers generative models whose posteriors can be well-approximated by its recognition network. This is sometimes called the "representability" or "amortization" pressure.

## Algebraic forms

The paper gives several useful rewrites. For factorial Q and Bernoulli generative units, the per-unit contribution to `F` is:

`KL[q, p] = q log(q/p) + (1 − q) log((1 − q)/(1 − p))`

summed over all units and layers. This is exactly the cross-entropy used in modern VAE training.

## In the Free Energy Principle

[[karl-friston|Friston]]'s [[free-energy-principle|Free Energy Principle]] (canonical review: [[friston-2010-free-energy-principle|Friston 2010]]) treats variational free energy as a candidate master quantity for cortical dynamics: neurons' activity and synapses are described as implementing gradient descent on `F` over both recognition (activation) and generative (weight) variables, with action added as a third variable that the agent can use to further reduce `F` by changing its own sensory distribution. In this framing:
- perception = minimize F w.r.t. recognition (activation) variables,
- learning = minimize F w.r.t. generative (weight) variables,
- action = minimize F w.r.t. action (control) variables.

This is the natural home for the wiki's control thesis: the same scalar loss unifies inference, learning, and action. The Helmholtz machine addresses the first two; [[Active Inference]] completes the triad.

[[friston-2010-free-energy-principle|Friston (2010)]] sharpens the framing by giving three equivalent re-expressions of `F`: (i) energy minus entropy (statistical-thermodynamic form), (ii) surprise plus KL between recognition and posterior (Bayesian form), and (iii) complexity minus accuracy (model-comparison form). The third form is what links FEP to the [[efficient-coding-hypothesis|efficient/infomax]] principle: maximizing accuracy under a complexity bound is mutual-information maximization. The same `F`, three readings, three families of "rival" theories that fall out as special cases.

## Free energy as a MaxEnt Lagrangian

`F` is the Lagrangian whose stationary points are [[maximum-entropy-principle|maximum-entropy]] distributions. The variational problem "maximize `H[Q]` subject to a constraint on `⟨E⟩_Q`" — the form Jaynes (1957) uses to derive the canonical, grand-canonical, and pressure ensembles of statistical mechanics from inference principles — is exactly the variational problem of `F`-minimization (with `−H[Q]` minimized and `⟨E⟩_Q` constrained to match the data likelihood). Free-energy minimization is, in its general form, [[jaynes-1957-maxent-statistical-mechanics|MaxEnt inference]]: at the optimum, `Q` is the maximally noncommittal distribution consistent with the constraint imposed by the energy term. This identification matters because it places the free-energy framework on inference-theoretic foundations — there is nothing specifically neural about the objective; whatever cortex does that resembles `F`-minimization is, formally, MaxEnt inference under whichever constraints the cortex has registered (typically encoded by the energy landscape of its generative model).

## Relationship to other quantities

- **Evidence Lower Bound (ELBO) in VAEs**: `ELBO = −F`. Different sign convention, identical content.
- **Cross-entropy loss in a deep autoencoder**: the generative part of `F` (expected energy) is a cross-entropy; the recognition part (entropy of Q) is a regularizer. In a deterministic autoencoder with point estimates of latents, the entropy term vanishes and you are left with reconstruction loss.
- **KL[Q ‖ P] interpretation**: the gap between `log p(d|θ)` and the bound. Small for factorial posteriors, large when the true posterior has strong correlations the factorial Q can't represent.
- **Prediction error**: in the [[Predictive Coding|predictive-coding]] formulation, the expected-energy part of `F` reduces to a weighted sum of squared prediction errors plus log-precision terms. Minimizing `F` is then *exactly* predictive-coding learning.

## Biological plausibility

`F` is local in the sense that its gradient with respect to each weight depends only on the pre- and post-synaptic activities of that weight — no weight transport, no non-local error signals. This is why the Helmholtz machine ([[dayan-hinton-1994-helmholtz-machine|Dayan et al. 1994]]) and its descendants are attractive as candidate cortical learning algorithms. Whether cortex actually computes `F` or its gradient in any concrete sense is an open empirical question — the [[Credit Assignment|dendritic-compartment lineage]] provides one biophysical candidate for its implementation, [[Wake-Sleep Algorithm|wake-sleep]] provides another.

## Sources

- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — introduces the Helmholtz free energy as the objective for connectionist generative learning; equation 5 gives the central variational identity.
- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — specializes the variational-inference framework to continuous Gaussian latents in a hierarchical visual generative model. The optimization objective `E = (1/σ²)‖I − f(Ur)‖² + (1/σ²_td)‖r − r^td‖² + g(r) + h(U)` is a Gaussian-specialized variational free energy with explicit precision-weighting `(1/σ², 1/σ²_td)` of the prediction errors at each level — the precision-weighting that becomes central in Friston's later free-energy formulation of attention and salience.
- [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]] — establishes that the variational form `⟨E⟩ − H` is the Lagrangian for [[maximum-entropy-principle|MaxEnt]] inference. Free-energy minimization is therefore not idiosyncratic to neuroscience but the local-recognition specialization of the general MaxEnt inference framework Jaynes derived for statistical mechanics.
- [[friston-2010-free-energy-principle|Friston (2010)]] — the canonical review establishing variational free energy as the master quantity behind a [[free-energy-principle|unified brain theory]]. Gives the three equivalent re-expressions of `F` (energy − entropy; surprise + KL; complexity − accuracy), the canonical-microcircuit message-passing implementation (Box 2: forward errors, backward predictions, precision-weighted gradient on `F`), and the active-inference extension where action is a third variable minimizing `F`.
