---
title: "Variational Free Energy"
type: concept
aliases: ["Helmholtz free energy", "ELBO", "evidence lower bound", "negative free energy"]
tags: [variational-inference, information-theory, generative-model, predictive-coding, free-energy-principle]
source_count: 1
last_updated: 2026-04-18
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

Friston's Free Energy Principle treats variational free energy as a candidate master quantity for cortical dynamics: neurons' activity and synapses are described as implementing gradient descent on `F` over both recognition (activation) and generative (weight) variables, with action added as a third variable that the agent can use to further reduce `F` by changing its own sensory distribution. In this framing:
- perception = minimize F w.r.t. recognition (activation) variables,
- learning = minimize F w.r.t. generative (weight) variables,
- action = minimize F w.r.t. action (control) variables.

This is the natural home for the wiki's control thesis: the same scalar loss unifies inference, learning, and action. The Helmholtz machine addresses the first two; [[Active Inference]] completes the triad.

## Relationship to other quantities

- **Evidence Lower Bound (ELBO) in VAEs**: `ELBO = −F`. Different sign convention, identical content.
- **Cross-entropy loss in a deep autoencoder**: the generative part of `F` (expected energy) is a cross-entropy; the recognition part (entropy of Q) is a regularizer. In a deterministic autoencoder with point estimates of latents, the entropy term vanishes and you are left with reconstruction loss.
- **KL[Q ‖ P] interpretation**: the gap between `log p(d|θ)` and the bound. Small for factorial posteriors, large when the true posterior has strong correlations the factorial Q can't represent.
- **Prediction error**: in the [[Predictive Coding|predictive-coding]] formulation, the expected-energy part of `F` reduces to a weighted sum of squared prediction errors plus log-precision terms. Minimizing `F` is then *exactly* predictive-coding learning.

## Biological plausibility

`F` is local in the sense that its gradient with respect to each weight depends only on the pre- and post-synaptic activities of that weight — no weight transport, no non-local error signals. This is why the Helmholtz machine ([[dayan-hinton-1994-helmholtz-machine|Dayan et al. 1994]]) and its descendants are attractive as candidate cortical learning algorithms. Whether cortex actually computes `F` or its gradient in any concrete sense is an open empirical question — the [[Credit Assignment|dendritic-compartment lineage]] provides one biophysical candidate for its implementation, [[Wake-Sleep Algorithm|wake-sleep]] provides another.

## Sources

- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — introduces the Helmholtz free energy as the objective for connectionist generative learning; equation 5 gives the central variational identity.
