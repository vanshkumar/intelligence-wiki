---
title: "Learning, Fast and Slow"
type: source
source_type: paper
authors:
  - "Markus Meister"
year: 2022
doi: "10.1016/j.conb.2022.102555"
tags: [learning-rate, sparse-coding, hebbian-learning, associative-learning, neural-representations, information-theory]
date_ingested: 2026-04-10
key_finding: "The 10,000× difference in learning rates across tasks is explained by whether the animal already has sparse, high-dimensional neural codes for the relevant stimuli — not by task complexity."
---

## Overview

This review surveys learning rates across animal species and tasks, revealing a striking 4-order-of-magnitude range: from ~1 bit/trial (fear conditioning, Bruce effect, food aversion) to ~10⁻⁴ bits/trial (laboratory 2AFC tasks). Meister argues that the critical variable is **not** task complexity but whether the animal already possesses a [[Sparse Coding|sparse, high-dimensional neural representation]] of the relevant events. Fast learning occurs when the right code exists (genetically or from prior experience); slow learning is bottlenecked by the need to build that code from scratch.

The paper connects a neural-level explanation (sparse codes enable efficient [[Hebbian Learning]]) to a psychological-level explanation (Bayesian priors determine what contingencies seem plausible), arguing these are the same thing viewed at different levels: the sparse code **is** the prior.

[PDF](../../raw/papers/meister-2022.pdf) | [Transcript](../../raw/papers/meister-2022-transcript.md)

## Key Findings

**1. Learning rates span 4 orders of magnitude.** Figure 1 plots bits learned vs. number of reinforced trials across species and tasks. The fastest learners (fear conditioning, Bruce effect, food aversion) extract ~1 bit per experience. The slowest (visual/touch 2AFC in rodents) extract ~10⁻⁴ bits per trial. This range exists even within the same species performing tasks of similar logical complexity.

**2. Task complexity doesn't explain the difference.** Simple 2AFC tasks (2 stimuli, 2 actions, 1 bit of complexity) are among the slowest to learn. Complex tasks like maze navigation (9+ bits) are learned orders of magnitude faster. The determining variable is not structural complexity but whether the task falls within the animal's natural behavioral repertoire.

**3. Sparse codes enable fast Hebbian learning.** The core neural argument:
- Biological synapses modify based only on **local** information: pre-synaptic activity, post-synaptic activity, and neuromodulatory signals
- With **distributed (non-sparse) codes**, multiple stimuli activate overlapping sets of neurons. A synapse strengthened for one association gets corrupted by another — the **interference problem**. The synapse from a shared neuron can't distinguish which stimulus caused it to fire.
- With **sparse codes** (ideally one-hot), each stimulus activates a unique set of neurons. No overlap means no interference. A single Hebbian exposure is sufficient to form a correct association.
- Therefore: fast learning requires that a sparse code for the relevant stimuli already exists. The association step itself is fast; the bottleneck is the representation.

**4. Two sources of sparse codes:**
- **Genetic/evolutionary hardwiring** — evolution has pre-built sparse representations for ecologically critical events (predators, mates, food, spatial landmarks). These support fast, often one-shot learning.
- **Unsupervised learning from lifetime experience** — the visual system progressively builds sparse codes through exposure: retinal → thalamic → cortical processing stages, each expanding dimensionality and increasing sparseness. This is slow but eventually enables fast associative learning for experienced stimuli.

**5. The Bayesian prior IS the sparse code.** At the psychological level, slow learning on implausible contingencies (e.g., "whisker touch → lick left for juice") can be framed as the animal requiring overwhelming evidence to overcome a low prior. Meister argues this psychological explanation and the neural explanation are the same thing: lacking a sparse code for those events means the animal's brain literally cannot efficiently detect and reinforce the correlation — which manifests as the contingency seeming "implausible."

**6. Experimental prediction.** Expose animals to the abstract stimuli and actions of a slow 2AFC task **without reinforcement** for an extended period. Prediction: (1) concept cells specific to those task events should emerge during passive exposure, and (2) subsequent reinforced learning should be much faster. This would demonstrate that the bottleneck is building the representation (unsupervised), not forming the association (reinforcement-dependent).

## Methods

Meister uses **information theory** to create a common currency for comparing learning across tasks:
- Task complexity C = log₂(mⁿ) bits, where m states and n actions
- Learning L = H_before − H_after (reduction in entropy about the correct mapping)
- For 2AFC: L = 2(1 + p_aft·log₂(p_aft) + (1−p_aft)·log₂(1−p_aft)) bits, where p_aft is post-training accuracy
- This framework generalizes to continuous action distributions using KL divergence

## Implications

**For understanding biological learning:**
- The "learning algorithm" (Hebbian plasticity) is not the bottleneck — it's fast. The bottleneck is the **representation**. This reframes the study of learning: instead of asking "how do synapses learn?", ask "how do the right representations emerge?"
- Lab tasks that take thousands of trials may be studying representation formation, not the animal's natural learning mechanisms. These circuits may have little to do with how the animal actually learns in the wild.

**For evolutionary investments:**
- Evolution invested heavily in building sparse codes for ecologically relevant events — the sensory processing hierarchy (retina → cortex) is a massive unsupervised feature extraction pipeline that creates the representations needed for fast learning.
- This aligns with [[li-2024-prediction-noise-reward|Li et al. (2024)]]: the learning rules themselves may be simple; the complexity is in the architecture that produces the right representations and the neuromodulatory systems that bias which associations form.

**For experimental design:**
- Meister argues the field should redirect effort from the "lower right" of Figure 1 (slow lab tasks) toward the "upper left" (fast, naturalistic learning). The fast regime is where the brain's actual learning machinery is most visible, uncontaminated by the confound of representation building.

## Connections to Existing Knowledge

- **[[Hebbian Learning]]**: Meister's framework depends on Hebbian plasticity being fast but local — the locality constraint is what makes the representation matter so much.
- **[[Sparse Coding]]**: The central concept of the paper. Sparse, high-dimensional representations solve the interference problem and enable one-shot associative learning.
- **[[li-2024-prediction-noise-reward|Li et al. (2024)]]**: Both papers converge on the idea that the learning rules are simple and that the complexity is elsewhere — PaN in the architecture + noise, Meister in the representations. Together they suggest evolution's investments were in building the right codes and control systems, not the learning algorithm itself.
- **[[Predictive Coding]]**: The visual cortex's progressive construction of sparse codes through hierarchical processing is consistent with predictive coding accounts of sensory processing.
- **[[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]]**: Provides a complementary contribution to the slow timescale of mammalian learning. Meister attributes slow lab-learning to **representation building** (slow construction of sparse codes). Kukushkin shows that even at the *non-synaptic*, single-cell level, transcriptional consolidation has 24-h kinetics — a genuinely *molecular* slowness that is independent of representation. Both contributions to slow learning may be at work; Meister's representational story is not displaced, but is now one of two factors rather than the only factor.

## Open Questions Raised

- Can the information-theoretic framework be extended to capture representational learning (not just associative learning)?
- What are the specific unsupervised learning mechanisms that build sparse codes in cortex?
- Does the passive exposure prediction hold? Would pre-exposure to 2AFC stimuli produce concept cells and speed subsequent learning?
- How do neuromodulatory systems (dopamine, norepinephrine) interact with the sparse code framework — do they modulate which codes get built, or which associations form on existing codes, or both?
