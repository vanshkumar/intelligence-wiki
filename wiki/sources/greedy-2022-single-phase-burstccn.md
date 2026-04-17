---
title: "Single-Phase Deep Learning in Cortico-Cortical Networks"
type: source
source_type: paper
authors:
  - "Will Greedy"
  - "Heng Wei Zhu"
  - "Joseph Pemberton"
  - "Jack Mellor"
  - "Rui Ponte Costa"
year: 2022
doi: "10.48550/arXiv.2206.11769"
tags: [credit-assignment, dendrites, backpropagation, bursting, STP, cortical-microcircuit, single-phase, feedback-alignment]
date_ingested: 2026-04-17
key_finding: "BurstCCN combines burst ensemble multiplexing, connection-type-specific STP, and a novel learned Q feedback pathway to achieve single-phase deep learning that approximates backpropagation, scales to 9 layers, and reaches 1.84% MNIST / ~23% CIFAR-10 — resolving the phase and depth limitations of prior dendritic credit assignment models."
---

## Overview

BurstCCN (Bursting Cortico-Cortical Network) is a synthesis model that unifies the best features of the prior [[Credit Assignment]] lineage — burst-dependent plasticity from [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]'s Burstprop, the self-predicting state concept from [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]'s EDN, and the segregated dendrite architecture from [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]]. The key innovation is a **novel Q feedback pathway** — a set of STD (short-term depressing) connections from dendrite-targeting interneurons to apical dendrites that learn to cancel baseline burst activity, enabling single-phase learning without alternating forward/backward phases.

The paper demonstrates three versions of BurstCCN (spiking, continuous-time rate, discrete-time rate), showing single-phase learning, backprop approximation, and scaling to complex image classification (MNIST, CIFAR-10). It resolves the two remaining limitations of previous models: [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]]'s phase requirement and [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]'s EDN depth-scaling failure.

[PDF](../../raw/papers/greedy-2022.pdf)

## Key Findings

### Architecture: Three Connection Types

BurstCCN distinguishes three types of inter-layer connections, each with specific STP:

1. **W (feedforward)** — STD connections from layer l−1 to layer l. Transmit **event rates** (the feedforward signal). Because STD filters out bursts and passes tonic firing, these connections carry only the bottom-up representation, equivalent to a standard feedforward ANN.

2. **Y (feedback, STF)** — Short-term facilitating connections from layer l to layer l−1. Interpreted as SST+ dendrite-targeting interneuron projections. Transmit **burst rates** backward — these carry the error signal. STF selectively passes high-frequency bursting while filtering out tonic spiking.

3. **Q (feedback, STD)** — A novel set of STD connections from layer l to layer l−1, also targeting apical dendrites. Transmit **event rates** backward. Their role: cancel the baseline burst activity at apical dendrites so that only the error-carrying component (from Y) remains.

The distinction between Y and Q is the central innovation. Both project to apical dendrites, but they carry different signals due to their different STP types (STF vs STD).

### The Q-Y Cancellation Mechanism

When no teaching signal is present at the output:
- Y connections carry burst rates backward (containing both baseline bursting and any error signal)
- Q connections carry event rates backward
- A homeostatic learning rule drives Q weights to silence apical dendrites:

  **ΔQ_l = −η^(Q) u_l e_{l+1}^T**

  This rule pushes Q toward the **Q-Y symmetric state**: Q_l = p_l^0 Y_l, where p_l^0 is the baseline burst probability. At this point, the event-rate signal through Q exactly cancels the baseline burst-rate signal through Y, leaving apical dendrites at rest.

When a teaching signal IS present:
- The output error changes burst probabilities at the output layer
- This change propagates backward through Y (as a burst-rate deviation from baseline)
- Q cannot cancel this deviation because it only carries event rates, which are unaffected by the teaching signal
- The remaining apical signal is the **error** — the burst probability deviation from baseline

This is functionally analogous to Sacramento's self-predicting SST interneurons, but achieved through learned feedback weights with different STP types rather than a separate interneuron population.

### Burst-Dependent Plasticity Rule

Feedforward weight updates follow:

**ΔW_l = η_l^(W) (p_l − p_l^0) ⊙ e_l · e_{l-1}^T**

where p_l is burst probability, p_l^0 is the constant baseline (predefined, not a moving average), e_l is event rate, and ⊙ is element-wise multiplication. The change in burst probability from baseline, (p_l − p_l^0), is the signed error signal: positive → LTP, negative → LTD, scaled by event rate.

Key difference from Burstprop: Burstprop uses a **moving average** p̄ as the baseline, which requires a prediction phase without teaching signals to establish. BurstCCN uses a **constant** baseline p^0 and relies on Q cancellation to remove non-error burst activity, enabling true single-phase operation.

### Single-Phase Learning

The critical test: XOR classification. Burstprop requires two phases (prediction, then teaching) and fails in single-phase mode because its moving average p̄ is corrupted by the continuous teaching signal. BurstCCN succeeds in single-phase mode because Q cancellation provides a clean baseline regardless of whether a teaching signal is present.

The continuous-time BurstCCN also learns a dynamic nonlinear regression task (three sinusoidal inputs → nonlinear target) with continuously changing inputs and targets — no fixed stimulus presentations needed.

### Analytical Approximation to Backpropagation

In the weak-feedback limit (small apical potentials u_l), the change in burst rate at hidden layer l satisfies:

**δb_l = f'(v_l) ⊙ (−Y_l) δb_{l+1} + O(u_l^3)**

This is the backprop recurrence relation. The feedforward weight update becomes:

**ΔW_l^BurstCCN = η_l^(W) δb_l e_{l-1}^T ≈ −η_l^(W) (∂E^task/∂v_l) e_{l-1}^T = ΔW_l^backprop**

provided feedback weights are in the W-Y symmetric state (Y_l = −W_{l+1}^T). With random feedback weights, the model approximates feedback alignment instead.

### Results

**MNIST** (5-layer, 784-500-500-500-10):
- BurstCCN: **1.84 ± 0.01%** (random feedback)
- BurstCCN (Q-Y symmetric): comparable
- Burstprop: 1.75 ± 0.01%
- EDN (Sacramento): 10.65 ± 0.09%
- Standard ANN: 1.84 ± 0.01%

**Depth scaling** (MNIST, 2-9 hidden layers):
- BurstCCN and Burstprop maintain performance through 9 layers
- EDN shows substantial decay with depth — error signals degrade through many layers

**CIFAR-10** (3 conv + FC + output):
- BurstCCN (W-Y symmetric): **22.92 ± 0.03%** — comparable to ANN (22.62%) and Burstprop (24.15%)
- BurstCCN (random feedback): **38.99 ± 0.18%** — similar to ANN (36.30%) and Burstprop (41.32%) with random feedback

**Q-Y alignment**: As Q weights converge via the homeostatic rule, apical potentials shrink and weight updates align more closely with backprop gradients (from ~90° toward ~20-30°).

## Methods

- **Spiking BurstCCN**: Two-compartment neurons (soma + apical), Poisson spike generation, bursts defined as ISI < 16ms, ensemble-level burst probability p = b/e
- **Continuous-time rate BurstCCN**: Conductance-based ODEs for somatic and apical voltages (see SM)
- **Discrete-time rate BurstCCN**: Simplified fixed-point computation for image classification; STD on W means only event rates propagate forward; STF on Y means only burst rates propagate backward
- **CIFAR-10**: 3 convolutional layers (32, 64, 128 filters) + 1 FC hidden + output; mini-batch training

## Implications

### Synthesis of the Credit Assignment Lineage

BurstCCN resolves both remaining limitations of the prior dendritic credit assignment models:

| Limitation | Source | BurstCCN Solution |
|-----------|--------|-------------------|
| Multi-phase learning | [[guerguiev-2017-segregated-dendrites\|Guerguiev 2017]] (forward/plateau phases) | Q cancellation provides continuous baseline |
| Phase dependence of baseline | Burstprop's moving average p̄ corrupted by continuous teaching | Constant p^0 + learned Q weights |
| Depth scaling failure | [[sacramento-2018-dendritic-microcircuits-backprop\|Sacramento 2018]] EDN degrades with depth | STP-based multiplexing maintains error fidelity |

The model achieves this by combining elements from across the lineage:
- **From [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]]**: Two-site architecture, STP multiplexing
- **From [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]]**: Segregated dendritic compartments, feedback alignment
- **From [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]**: Self-predicting state concept (realized here as Q-Y cancellation instead of SST interneurons)
- **From [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]**: Burst ensemble multiplexing, burst-dependent plasticity rule, STP type specificity

### Biological Predictions

1. **STP type specificity on feedback connections**: STD on cortico-cortical feedback projections to pyramidal cells (the Q pathway); STF on feedback via dendrite-targeting SST+ interneurons (the Y pathway). Evidence: SST interneurons receive STF top-down connections while direct pyramidal-to-pyramidal projections exhibit STD (Urban-Ciecko & Barth 2016; experimental STP data in cortical feedback).

2. **Disrupting SST+ STF connections impairs learning**: Manipulations of interneurons with STF connections should disrupt burst decoding from the layer above, impairing credit assignment.

3. **Burst variance correlates with error magnitude**: The variance in bursting activity and the distal dendritic potentials should correlate with the severity of errors during learning.

### Connection to the Control Thesis

The Q-Y cancellation mechanism implements a specific form of homeostatic control: the system actively maintains a quiescent apical state as its equilibrium, and deviations from this equilibrium (errors) drive corrective updates. This is the same principle as Sacramento's self-predicting state — the default is "all predictions satisfied" and learning is triggered by perturbation. The control system maintains its own calibration (via Q weight learning) while simultaneously learning the task (via W weight updates).

## Connections to Existing Knowledge

- **[[Credit Assignment]]**: The synthesis model that resolves the phase and depth limitations of the entire Kording → Guerguiev → Sacramento → Payeur lineage. First model to combine single-phase learning, depth scaling, and biological features (bursting, STP, interneurons).
- **[[Dendritic Computation]]**: Uses the same basal/apical segregation but adds a specific functional prediction: two types of feedback connection (STF via interneurons, STD direct) converging on apical dendrites with opposing roles.
- **[[Synapses]]**: Makes the most specific STP predictions in the lineage — three connection types with three STP profiles (STD feedforward, STF feedback via interneurons, STD feedback direct), each with a precise computational role.
- **[[Inhibitory Circuits]]**: SST+ dendrite-targeting interneurons are proposed as the biological substrate of the Y pathway (STF feedback carrying burst/error signals). The Q pathway may correspond to direct cortico-cortical feedback projections with STD.
- **[[Hebbian Learning]]**: Plasticity rule is local: burst probability deviation × event rate × presynaptic event rate. Q weight learning is a homeostatic variant — drives apical dendrites to rest.
- **[[Predictive Coding]]**: The Q-Y cancellation is functionally equivalent to Sacramento's self-predicting state: a learned pathway that cancels expected feedback, leaving only the error (unexpected) component. Different implementation, same computational principle.
- **[[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]]**: Experimental validation — SD residuals (dendritic activity not predicted by somatic activity) are the in vivo counterpart of the error component that remains after Q-Y cancellation. The cell-specific sign of SD residuals during error reduction matches BurstCCN's prediction that the error signal is vectorized (neuron-specific), not scalar.

## Open Questions Raised

- The model requires distinct STP types (STF vs STD) on two classes of feedback connection to the same dendritic compartment. Is this level of STP specificity actually present in cortical feedback? The evidence for STF on SST+ interneuron connections is encouraging but incomplete.
- BurstCCN with random feedback weights (feedback alignment) performs significantly worse than with W-Y symmetric weights on CIFAR-10 (~39% vs ~23%). Can biologically plausible feedback learning rules close this gap? The authors acknowledge this as the main remaining limitation.
- The constant baseline p^0 is assumed to be the same for all neurons in a layer. How sensitive is the model to heterogeneous baselines, as would exist in real cortex?
- Can BurstCCN be extended to temporal credit assignment? The current model handles spatial (structural) credit assignment only. Recurrent connections and temporal error signals are not addressed.
- Does the Q-Y cancellation mechanism interact with [[Memory Consolidation|sleep-dependent consolidation]]? The Q weights must be maintained in alignment with changing W and Y weights — does this calibration happen during sleep?

## Sources

Greedy, W., Zhu, H.W., Pemberton, J., Mellor, J. & Costa, R.P. (2022). Single-phase deep learning in cortico-cortical networks. Preprint, arXiv:2206.11769.
