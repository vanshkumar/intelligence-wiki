---
title: "Vectorized Instructive Signals in Cortical Dendrites"
type: source
source_type: paper
authors:
  - "Valerio Francioni"
  - "Victor D. Tang"
  - "Enrique H. S. Toloza"
  - "Zhengyuan Ding"
  - "Nathan J. Brown"
  - "Mark T. Harnett"
year: 2026
doi: "10.1038/s41586-026-01990-7"
tags: [dendritic-computation, credit-assignment, calcium-imaging, BCI, inhibitory-circuits, layer-1, NDNF]
date_ingested: 2026-04-16
key_finding: "Distal apical dendrites of L5 pyramidal neurons carry cell-specific instructive signals (SD residuals) encoding error derivatives — the first in vivo experimental evidence for vectorized dendritic teaching signals predicted by the computational credit assignment lineage"
---

## Overview

[PDF](../../raw/papers/francioni-2026.pdf)

This paper provides the first **in vivo experimental evidence** that distal apical dendrites carry cell-specific instructive signals during learning — the biological counterpart to the teaching signals predicted by the computational [[Credit Assignment]] lineage (Kording 2001 → Guerguiev 2017 → Sacramento 2018 → Payeur 2020 → Greedy 2022). Using simultaneous two-photon calcium imaging of layer 5 pyramidal neuron somas and their corresponding distal apical dendrites in mouse retrosplenial cortex (RSC) during a neurofeedback BCI task, Francioni et al. isolate a dendritic signal component — the **somato-dendritic (SD) residual** — that is not predicted by somatic activity. This residual encodes task-relevant variables (reward, error), is cell-specific (sign depends on each neuron's causal role in the task), and is necessary for learning (disrupting it via NDNF+ layer 1 interneuron activation abolishes vectorized error signals and impairs task acquisition).

## Key Findings

### SD residuals: isolating the dendritic teaching signal

The core methodological innovation is the **SD residual** — the component of dendritic GCaMP activity that cannot be linearly predicted from somatic activity, computed using surrounding network activity as the predictor (not the neuron's own soma, to avoid circularity). The soma-dendrite relationship is best described by a **linear** model (lowest AIC), consistent with the linearization role proposed for SST+ interneurons by [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]].

SD residuals are not noise: they are **correlated with task variables** (reward, error magnitude, error direction) and can be decoded from the population vector, demonstrating that dendrites carry structured information beyond what the soma represents.

### Vectorized, cell-specific signals

Neurons are classified by their causal role in the BCI task:
- **P+ neurons**: activity drives the visual stimulus toward the target orientation
- **P- neurons**: activity drives the stimulus away from the target

During **error reduction epochs** (when the animal is correcting errors), P+ neuron dendrites are relatively **amplified** (positive SD residual) while P- neuron dendrites are relatively **attenuated** (negative SD residual). This is a **cell-specific, signed** teaching signal — exactly the "vectorized" instructive signal the computational lineage requires. A scalar global signal (like dopamine RPE) would affect all neurons equally; what Francioni observes is a signal whose sign depends on each neuron's causal contribution.

### Error derivatives, not errors

SD residuals correlate with the **derivative** of the error signal (rate of change of stimulus angle) rather than with error magnitude per se. This is more consistent with **target propagation** (telling each neuron where to go) than with classical backpropagation (telling each neuron how wrong it is). This nuance does not invalidate the computational lineage — the models show that various local error representations can implement gradient-based learning — but it does constrain which specific computation the dendrites perform.

### NDNF+ layer 1 interneuron perturbation

Optogenetic activation of **NDNF+ interneurons** in cortical layer 1 — which inhibit the distal apical tuft of L5 pyramidal neurons — abolishes the vectorized SD residual pattern and impairs learning. This demonstrates that the dendritic teaching signal is **causally necessary** for task acquisition. NDNF+ interneurons are a new cell type in the credit assignment story: the computational lineage emphasized SST+ Martinotti cells targeting apical dendrites, but Francioni shows that L1 NDNF+ cells, which gate distal dendritic input from above, are equally critical.

### Anaesthesia preferentially suppresses dendritic signals

Under isoflurane anaesthesia, dendritic activity is preferentially reduced relative to somatic activity, shrinking SD residuals. This is consistent with the dendritic channel requiring active network state — top-down feedback (the proposed source of the teaching signal) is suppressed by anaesthesia before feedforward drive is.

### P+ neurons increase activity, P- neurons decrease over learning

Over 14 days of training, P+ neurons maintain or increase their calcium transient frequency while P- neurons decrease theirs. This is the expected learning outcome if the dendritic teaching signals are driving appropriate plasticity: neurons that help are strengthened, neurons that hinder are suppressed.

## Methods

- **Species/preparation**: Mice, layer 5 pyramidal neurons in retrosplenial cortex (RSC)
- **Task**: Neurofeedback BCI — mice learn to rotate a visual grating by modulating the activity of ~8 imaged neurons. No motor action required; the neural activity directly controls the visual stimulus.
- **Imaging**: Simultaneous two-photon calcium imaging (GCaMP7f) of somas (proximal trunk as proxy) and distal apical dendrites in two planes ~500 μm apart, at 30 Hz per plane. Same neurons tracked chronically across 14 days.
- **SD residual computation**: For each coincident soma-dendrite calcium event, the spike-inferred activity of all other neurons in the field of view is used to predict dendritic magnitude from somatic magnitude via linear regression. The residual is the SD residual.
- **P+/P- classification**: Based on the sign of each neuron's BCI weight (defined by the decoder mapping neural activity to stimulus rotation). P+ neurons push toward the target; P- push away.
- **Perturbation**: Optogenetic activation of NDNF-Cre-expressing L1 interneurons via ChRimson, delivered on alternating days during closed-loop BCI.
- **Analysis**: SVM decoders, Pearson correlation with task variables, two-way repeated measures ANOVA across days and conditions. All analysis in MATLAB 2020a.

## Implications

### Experimental closure of the computational lineage

This paper bridges **20+ years** of theoretical work (Kording 2001 through Greedy 2022) to experimental reality. The five computational papers predicted that apical dendrites carry cell-specific teaching signals that implement hierarchical credit assignment. Francioni provides the first direct in vivo measurement of such signals. The lineage is now: conceptual insight (Kording) → spiking proof of concept (Guerguiev) → analytical theory (Sacramento) → biophysical maturity (Payeur) → full synthesis (Greedy) → **experimental validation (Francioni)**.

### NDNF+ interneurons as a new player

The computational lineage focused on SST+ Martinotti cells as the key inhibitory partner. Francioni shows that **NDNF+ layer 1 interneurons** — a distinct cell type gating distal dendritic input — are necessary for the teaching signal. This is complementary, not contradictory: SST+ cells may handle mid-apical linearization and prediction (as modeled), while NDNF+ cells gate the distal tuft where cortico-cortical feedback arrives. The laminar specificity matters — L1 is where long-range feedback projections terminate.

### Constraints on the error representation

The finding that SD residuals encode error **derivatives** rather than error magnitudes constrains but does not disqualify the computational models. Sacramento's framework computes prediction errors (consistent with error), while target propagation computes targets (consistent with derivatives). Payeur's burst-dependent mechanism is agnostic — it requires only that burst probability carries the credit signal, which could represent either. The experimental data push slightly toward target propagation.

## Connections to Existing Knowledge

- **[[Credit Assignment]]**: Experimental validation of the central prediction of the dendritic credit assignment lineage — cell-specific teaching signals in apical dendrites
- **[[Dendritic Computation]]**: SD residuals operationalize the "independent dendritic variable" that all five computational papers require. The linear soma-dendrite relationship supports SST+-mediated linearization ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al., 2020]])
- **[[Inhibitory Circuits]]**: Introduces NDNF+ L1 interneurons as a fourth key interneuron type for credit assignment, complementing PV+, SST+, and VIP+ roles
- **[[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]**: The self-predicting state predicts that dendritic signals should be noisy during learning and silent post-learning; Francioni's 14-day trajectory is consistent but doesn't reach full convergence
- **[[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]]**: BurstCCN's Q-Y cancellation predicts that baseline dendritic activity should be cancelled, leaving only error-related residuals — exactly what the SD residual captures

## Open Questions Raised

- Do SD residuals correspond to burst-rate modulation (as the computational lineage predicts), or to a different dendritic signal type? GCaMP imaging cannot distinguish bursts from isolated spikes.
- Is the NDNF+ perturbation effect specific to gating feedback, or does it non-specifically suppress all dendritic activity? The experiment shows abolition of vectorized signals, but whether NDNF+ activation specifically blocks top-down input vs. generally hyperpolarizing the apical tuft is undetermined.
- Does the SD residual pattern generalize beyond BCI tasks to naturalistic learning? BCI is an unusual task where the mapping between neural activity and outcome is artificially defined — does the same cell-specific dendritic signal structure exist during sensory learning, motor learning, or navigation?
- How do NDNF+ and SST+ interneurons interact? The computational lineage assigns linearization and prediction roles to SST+; Francioni assigns a gating role to NDNF+. A dual-perturbation experiment (SST+ vs NDNF+ vs both) would disambiguate their contributions.
- Can the error-derivative (vs error) distinction be confirmed with higher-temporal-resolution methods (e.g., voltage imaging)?
