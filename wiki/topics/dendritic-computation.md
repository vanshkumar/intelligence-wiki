---
title: "Dendritic Computation"
type: concept
aliases: ["dendritic processing", "apical dendrites", "dendritic compartments"]
tags: [pyramidal-neurons, dendrites, computation, credit-assignment, calcium]
source_count: 7
last_updated: 2026-04-16
confidence: established
---

Dendritic computation refers to the information processing performed within the dendritic tree of a neuron, beyond simple summation of inputs at the soma. Pyramidal neurons in cortex have functionally distinct dendritic compartments that receive different classes of input and perform different computations, making the single neuron a more powerful computational unit than a simple point integrator.

## Compartmentalization in Pyramidal Neurons

Cortical pyramidal neurons have two major dendritic compartments:

- **Basal dendrites / perisomatic region**: Receive **feedforward (bottom-up)** input from lower cortical areas and thalamus. This is where the neuron integrates sensory-driven signals.
- **Apical dendrites**: Receive **feedback (top-down)** input from higher cortical areas and thalamic matrix neurons. This is where contextual, predictive, and error signals arrive.

This separation means a single neuron has access to both bottom-up evidence and top-down expectations, integrated in different compartments. [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]] first formalized the computational significance: with two integration sites, a neuron carries **two independent variables** — somatic activity (A) and apical dendritic burst rate (D) — enabling gradient-based learning that is structurally impossible for single-site point neurons. The interaction between compartments — particularly whether apical input triggers regenerative dendritic events — determines the neuron's output mode.

## Dendritic Regenerative Activity

Apical dendrites contain voltage-gated calcium channels (VGCCs) that can produce **dendritic calcium spikes** — regenerative events analogous to somatic action potentials but mediated by calcium rather than sodium. When apical input is strong enough, a calcium spike propagates toward the soma and can trigger a **burst** of somatic action potentials (high-frequency doublet or triplet, ISI < 16 ms).

This burst/spike distinction is computationally significant: [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] show that whether a neuron bursts or fires isolated spikes determines the **sign of synaptic plasticity** at its input synapses (burst → LTP, isolated spike → LTD). Top-down feedback therefore controls plasticity in lower areas by modulating burst probability — a mechanism for [[Credit Assignment]].

## Single Neurons as Multi-Layer Networks

Beyond compartmentalization, the branching structure of the dendritic tree itself provides computational power. [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] model a single neuron's dendrite as a sparse binary tree ANN (*k*-tree) where each dendritic branch node takes 2 inputs and applies a nonlinearity before passing its output toward the soma. This makes a single biological neuron internally equivalent to a multi-layer network — not a point integrator.

Key results:
- A single dendritic tree (1-tree) significantly outperforms a linear classifier (the point-neuron proxy) on binary image classification (MNIST: 92.2% vs 87.5%)
- When the same input is repeated across *k* subtrees — modeling **multi-synaptic boutons (MSBs)**, where the same presynaptic axon contacts the same dendrite at multiple points — performance monotonically increases and approaches a parameter-matched 2-layer fully connected network
- MSBs are biologically real: ~4 synapses per postsynaptic neuron, 11.5% MSBs in enriched environments, and **LTP increases MSBs 6-fold** (Toni et al. 1999)

This means learning doesn't just tune synaptic weights — it **replicates connections** across dendritic branches, directly increasing the neuron's computational capacity. The dendritic tree's branching structure is not just a wiring convenience; it is the substrate for nonlinear, multi-layer computation within a single cell.

## Escaping the Star Topology

The [[Action Potential|star topology constraint]] of single-compartment neuron models (all gating variables couple only through shared voltage) limits dynamical richness. Dendritic compartments provide an escape route: each compartment has its own local voltage, and the coupling between compartments adds degrees of freedom. This allows the neuron to perform computations — like separating feedforward from feedback signals — that a point neuron cannot.

## Role in Credit Assignment

The apical dendrite has been assigned three related but distinct functional interpretations across the credit assignment lineage:

1. **Carrier of the burst-rate learning signal** ([[kording-konig-2001-two-integration-sites|Kording & Konig, 2001]]): Apical input modulates burst rate D, which replaces the backpropagation error δ. STP multiplexing separates the burst signal (facilitating synapses) from the activity signal (depressing synapses).

2. **Plateau potential error carrier** ([[guerguiev-2017-segregated-dendrites|Guerguiev et al., 2017]]): The first spiking implementation. During plateau phases, the apical dendrite's temporally averaged voltage passes through a sigmoid nonlinearity to produce plateau potentials mimicking dendritic calcium spikes. The difference between plateau potentials in forward vs. target phases defines a local target for each hidden neuron. Electrotonic attenuation (g_A ≪ g_B) keeps apical input from corrupting feedforward processing during normal operation. Partial segregation suffices — consistent with experimental measurements.

3. **Site of prediction error computation** ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al., 2018]]): The apical compartment compares top-down feedback from higher areas with predictions generated by lateral SST interneurons. When interneurons cancel the feedback (self-predicting state), the apical compartment is silent. When they can't (novel teaching signal), the mismatch voltage is the backpropagated error. This makes the connection to [[Predictive Coding]] explicit: the prediction error *is* the credit signal.

4. **Controller of burst probability** ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al., 2020]]): Top-down feedback modulates burst probability via VGCCs and dendritic calcium spikes. SST+ interneurons linearize the response. Whether the neuron bursts or fires isolated spikes determines the sign of plasticity (burst → LTP, isolated spike → LTD).

5. **Dual-pathway cancellation site** ([[greedy-2022-single-phase-burstccn|Greedy et al., 2022]]): The apical dendrite receives **two** types of feedback — STF connections (Y, via interneurons) carrying burst rates and STD connections (Q, direct) carrying event rates. Q weights learn to cancel the baseline burst signal through Y, leaving only the error component. This achieves the self-predicting state without a separate interneuron population, and enables single-phase learning that scales to 9 layers.

6. **Experimentally measured SD residual** ([[francioni-2026-vectorized-dendritic-signals|Francioni et al., 2026]]): The first in vivo measurement. The **somato-dendritic (SD) residual** — the component of dendritic calcium activity not linearly predicted from somatic activity — is the experimental operationalization of the "independent dendritic variable" that all five computational models require. SD residuals encode error **derivatives** (not error magnitude), are cell-specific (sign depends on causal role: P+ amplified, P- attenuated during error reduction), and are causally necessary for learning (abolished by NDNF+ L1 interneuron activation). The linear soma-dendrite relationship (best fit by AIC) is consistent with SST+-mediated linearization. Notably, the perturbation targets **NDNF+ layer 1 interneurons** rather than SST+ Martinotti cells — L1 is where long-range cortico-cortical feedback terminates, suggesting a laminar division of labor: NDNF+ gates distal feedback input, SST+ linearizes and predicts at mid-apical sites.

All six share the fundamental insight that the apical dendrite separates feedforward representation from feedback teaching signals, and all produce learning rules that are local at the synapse but carry hierarchical information via the architecture.

## Sources

- [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]] — original formalization: two integration sites → two independent variables per neuron → gradient-based learning
- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] — first spiking implementation: plateau potentials in electrotonically segregated apical dendrites carry feedback error
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — apical dendrite as site of prediction error computation; comparison of top-down feedback vs. lateral interneuron predictions
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — apical dendrites as the substrate for top-down steering of plasticity via burst control
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] — apical dendrite as dual-pathway cancellation site: STF (Y) and STD (Q) feedback converge, Q learns to cancel Y baseline
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] — first in vivo measurement: SD residuals (dendritic activity not predicted by somatic activity) encode cell-specific error derivatives; NDNF+ L1 interneuron perturbation abolishes vectorized signals
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — dendritic trees as multi-layer networks; single neurons can solve complex classification tasks
