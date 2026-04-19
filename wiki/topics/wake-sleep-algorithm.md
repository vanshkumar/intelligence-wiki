---
title: "Wake-Sleep Algorithm"
type: mechanism
aliases: ["wake-sleep", "wake-sleep learning"]
tags: [learning-rule, credit-assignment, generative-model, sleep, local-learning]
source_count: 1
last_updated: 2026-04-18
level: circuit
---

Wake-sleep is a two-phase unsupervised learning algorithm for hierarchical stochastic networks. It trains a top-down **generative model** and a separate bottom-up **recognition model** using a purely local delta rule, without weight transport between the two networks. Introduced by [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] as the stochastic variant of the [[Helmholtz Machine]], it is one of the canonical biologically-plausible approaches to hierarchical credit assignment.

## The two phases

**Wake phase** (driven by real data):
1. A real input `d` is presented at the lowest layer.
2. Activities at successively higher layers are sampled from the bottom-up recognition model `Q(·|φ)` — each unit's probability of firing is `σ(Σ_i s_i^{ℓ−1} φ_{i,j})`, and a binary sample is drawn.
3. The **top-down generative weights θ** are updated (delta rule) to make the generative predictions `p_j^ℓ(θ, s^{ℓ+1})` match the sampled activities at each layer — i.e., θ learns to generate what the recognition model inferred.

**Sleep phase** (driven by the network's own hallucinations):
1. The recognition weights φ are turned off.
2. Starting at the top layer, activities are sampled from the generative model downward, producing a hallucinated input at the bottom layer. The true latent causes of this hallucinated input are known (the top-down samples).
3. The **bottom-up recognition weights φ** are updated (delta rule) to invert the generation — to map the hallucinated input back to its causes.

If both pathways use sigmoid activations, both phases use exactly the same local learning rule — the delta rule of Widrow & Stearns (1985). No weight transport, no non-local error signals, no iterative sampling at inference time.

## What wake-sleep is doing

Each phase improves one network against targets supplied by the other:

- Wake: generative weights learn to predict the activities the recognition model produces from real data.
- Sleep: recognition weights learn to produce the latent configurations the generative model would have used.

At the joint optimum, `Q_α = P_α` — the recognition distribution matches the true posterior of the generative model. However, wake-sleep does **not** descend a single cost function. The sleep phase's gradient is biased: it trains the recognition model on samples from the *generative* distribution rather than the *data* distribution, and it does not follow the correct gradient of the log-likelihood. In practice wake-sleep still converges on many problems, but this theoretical issue was later fixed by reweighted wake-sleep (Bornschein & Bengio 2014) and by stacked-RBM / DBN pretraining (Hinton et al. 2006).

## Biological interpretation

The algorithm's naming is suggestive: the "sleep" phase is a period of top-down generative activity with recognition pathways disengaged — not unlike dreaming. Wake-sleep predicts a normative functional role for offline generative cortical activity: **tuning the recognition pathway against self-generated samples**.

This fits with (but is distinct from) the other major account of sleep function in the wiki — SWR-driven replay during slow-wave sleep that transfers hippocampal traces to cortex ([[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. 2009]], [[Memory Consolidation]]). The two stories are compatible: SWS could instantiate wake-like consolidation (data-driven replay of real experience, tuning generative weights to capture it), and REM could instantiate the sleep phase (generative hallucination, tuning the recognition pathway). The mammalian two-stage sleep architecture has the right shape for a two-phase variational algorithm — though empirical evidence tying REM to recognition-pathway tuning specifically is still thin.

## Comparison with the dendritic credit-assignment lineage

Wake-sleep sits alongside the [[Credit Assignment|dendritic-compartment lineage]] ([[kording-konig-2001-two-integration-sites|Kording 2001]] → [[guerguiev-2017-segregated-dendrites|Guerguiev 2017]] → [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento 2018]] → [[payeur-2020-burst-dependent-credit-assignment|Payeur 2020]] → [[greedy-2022-single-phase-burstccn|Greedy 2022]] → [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]]) as a biologically-plausible alternative to backpropagation:

- **Wake-sleep**: separates forward and inverse computations in *time* (wake vs. sleep phases), uses two networks with independent weights.
- **Dendritic**: separates them in *space* (basal vs. apical compartments), uses one network with compartmentalized neurons; post-Sacramento variants achieve single-phase continuous learning.

A key disanalogy: wake-sleep requires the network to spend time hallucinating (sleep phase), during which it is not doing useful online inference. The dendritic lineage after Sacramento avoids this. On the other hand, wake-sleep has a natural fit with the biology of mammalian sleep that the dendritic lineage does not naturally claim.

## Limitations and extensions

- **Biased sleep gradient**: Reweighted wake-sleep (Bornschein & Bengio 2014) corrects this by importance-weighting sleep samples by their likelihood under the data distribution.
- **Factorial Q assumption**: Wake-sleep as presented assumes factorial recognition distributions at each layer. Structured variational methods (mixture of factorials, normalizing flows) relax this at the cost of more complex inference networks.
- **Discrete latents only in the original**: The original algorithm used binary stochastic units. Continuous-latent extensions (VAEs with reparameterization) superseded the delta-rule implementation for ML purposes, though the biological interpretation remains attached to wake-sleep.
- **No single objective**: This is the deepest theoretical limitation. It has not prevented wake-sleep from being useful, but it complicates convergence analysis.

## Sources

- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — introduces the algorithm in the stochastic [[Helmholtz Machine]].
