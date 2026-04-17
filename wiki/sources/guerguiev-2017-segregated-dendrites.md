---
title: "Towards Deep Learning with Segregated Dendrites"
type: source
source_type: paper
authors:
  - "Jordan Guerguiev"
  - "Timothy P. Lillicrap"
  - "Blake A. Richards"
year: 2017
doi: "10.48550/arXiv.1610.00161"
tags: [credit-assignment, dendrites, backpropagation, deep-learning, pyramidal-neurons, spiking, feedback-alignment, plateau-potentials]
date_ingested: 2026-04-16
key_finding: "Spiking neurons with electrotonically segregated basal and apical dendritic compartments can coordinate learning across layers using local targets derived from plateau potentials, achieving deep learning on MNIST (3.28% error) with random feedback weights and no weight transport."
---

## Overview

This paper demonstrates the first **spiking neural network** implementation of deep learning using segregated dendritic compartments. Hidden layer neurons have three compartments — soma, basal dendrites (feedforward input), and apical dendrites (feedback from higher layers). During alternating "transmit" and "plateau" phases, the apical compartment produces plateau potentials that encode feedback information. The difference between plateau potentials in the two phases provides a local target for each hidden neuron, enabling [[Credit Assignment]] without weight transport.

The key biological insight motivating the work: in neocortical pyramidal neurons, feedforward sensory information and top-down feedback arrive at electrotonically distinct dendritic compartments (basal vs. distal apical), and the distal apical dendrite communicates with the soma via active calcium plateau potentials rather than passive current spread. This segregation provides the physical substrate for separating feedforward representations from feedback teaching signals.

[PDF](../../raw/papers/guerguiev-2017.pdf)

## Key Findings

### Architecture and Neuron Model

Hidden layer neurons have three voltage variables:
- **C_i(t)** — somatic voltage, integrating basal and apical inputs:
  dC_i/dt = −g_L C_i + g_B(B_i − C_i) + g_A(A_i − C_i)
- **B_i(t)** — basal compartment voltage, receiving feedforward input via W^0
- **A_i(t)** — apical compartment voltage, receiving feedback from output layer via random weight matrix Y

The somatic compartment generates Poisson spikes at rate λ_max σ(C_i). The critical design parameter is **g_A** — the conductance coupling apical dendrites to soma. When g_A is low (electrotonic segregation), apical input influences the soma weakly during normal operation but can drive plateau potentials during the target phase.

### Two-Phase Operation

The network alternates between two phases:

1. **Forward/transmit phase** (t_0 to t_1): An image is presented to the input layer. Hidden layer neurons spike based primarily on basal (feedforward) input. Output neurons spike freely. Apical input has minimal effect on somatic firing due to electrotonic attenuation.

2. **Target/plateau phase** (t_1 to t_2): The same image continues to drive the input, but now the output layer also receives "teaching signals" — excitatory and inhibitory conductances that push output neuron voltages toward the correct class label. During this phase, apical voltages are temporally averaged and passed through a sigmoid nonlinearity to produce **plateau potentials** (α):

   α_i^f = σ(∫ A_i dt during forward phase)
   α_i^t = σ(∫ A_i dt during target phase)

These plateau potentials mimic the calcium spike / plateau potential events observed in pyramidal neuron apical dendrites (Larkum et al. 1999, 2009), which involve temporal averaging over ~20-30 ms followed by a nonlinear threshold.

### Local Targets from Plateau Differences

The hidden layer target rate of fire is defined as:

**λ̂_i^C = average forward firing rate + α_i^t − α_i^f**

The plateau difference (α^t − α^f) captures how the output layer's teaching signal changes the feedback arriving at the hidden neuron's apical dendrite. If the teaching signal increases feedback to neuron i, its target rate goes up; if feedback decreases, target rate goes down. This is a **local** signal — each hidden neuron computes its own target from its own apical voltage.

Local error functions are then defined for each layer:
- Output: L^1 = ||λ̂^U − λ_max σ(average forward somatic voltages)||²
- Hidden: L^0 = ||λ̂^C − λ_max σ(average forward somatic voltages)||²

Weight updates follow local gradient descent on these errors.

### Credit Assignment Without Weight Transport

The paper proves (Theorem 1) that reducing the hidden layer error L^0 will also reduce the output layer error L^1, provided:
1. Output layer error is sufficiently small
2. Feedforward (W^1) and feedback (Y) weight matrices produce forward and backward transformations that are approximate inverses of each other

This second condition is **not assumed** — it **emerges during training** via feedback alignment (Lillicrap et al. 2016). During the first epoch, W^1 and Y start random and uncorrelated, but they rapidly align so that their forward and backward functions become approximate inverses. The network is literally *learning to do credit assignment*.

### Results

**MNIST classification**:
- One hidden layer (784-500-10): **3.28% test error** by epoch 60, vs ~4.1% for a single-layer network
- Two hidden layers (784-500-500-10): **2.75% test error** — demonstrating genuine deep learning benefit from additional layers

**Deep learning signatures**:
- t-SNE visualization of hidden layer activity shows progressively more abstract, category-separated representations in deeper layers
- Two-digit clusters in the first hidden layer; single well-separated clusters per category in the second
- Receptive fields in hidden layer qualitatively match backprop-trained networks (oriented edges, strokes)

**Weight update alignment to backprop**:
- Weight update angle to backprop starts at ~65° (near orthogonal) and drops to ~40° during training
- With exact spike rates propagated (instead of spiking noise), angle drops to ~35°
- Confirms the network approximates backpropagation, with spiking noise as the main source of deviation

**Feedback weight conditions**:
- **Sparse random weights** work if magnitudes are scaled up (~5×) to compensate for the 80% zero entries
- **Symmetric weights** (Y = W^{1T}) improve learning slightly (3.7% → 3.6% by epoch 60)
- **Noisy symmetric weights** (Y = W^{1T} + noise) impair learning — because Y can never align with the changing W^1. This reveals that alignment is a **dynamic process**: Y must either be fixed (so W^1 aligns to it) or track W^1. A noisy moving target prevents convergence.

**Partial apical attenuation suffices**:
- Total segregation (g_A = 0) works but isn't necessary
- g_A = 0.05 (apical gets 12× less coupling to soma than basal, g_B = 0.6) works well
- g_A = g_B = 0.6 (no segregation) significantly impairs learning
- Consistent with experimental measurements of apical attenuation (Larkum et al. 1999, 2009)

## Methods

- **Spiking simulation**: Poisson spike generation from somatic voltage; weighted sums of postsynaptic potentials at dendritic compartments
- **Phases**: Stochastic timing — plateau intervals between 50-60 ms, randomly sampled from inverse Gaussian distribution
- **Training**: Online, one image at a time, 60,000 MNIST images per epoch
- **Output teaching**: Excitatory conductances to correct-class output neuron, inhibitory to others

## Implications

### Position in the Credit Assignment Lineage

Guerguiev et al. (2017) is the **first spiking implementation** of credit assignment via segregated dendrites. It occupies a specific position in the lineage:

| Feature | Kording & Konig (2001) | Guerguiev et al. (2017) | Sacramento et al. (2018) | Payeur et al. (2020) |
|---------|----------------------|------------------------|------------------------|---------------------|
| Neuron model | Rate, two variables | Spiking, three compartments | Rate, three compartments | Spiking, two compartments |
| Phases | Not addressed | Yes (forward/plateau) | **None** (continuous) | None (continuous) |
| Error representation | Burst rate D | Plateau potential difference | Apical prediction error | Burst probability deviation |
| Feedback weights | Symmetric assumed | Random (alignment emerges) | Random or learned | Learned |
| Interneurons | None | None | SST predict/cancel | SST linearize |
| Scale | X-OR | MNIST (3.28%) | MNIST (1.96%) | CIFAR-10, ImageNet |

The two-phase requirement is the main biological limitation that subsequent work addresses. [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] remove it by introducing SST interneurons that continuously predict and cancel top-down feedback (the self-predicting state). [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] remove it by using the burst/spike distinction as a continuous multiplexing mechanism.

### Feedback Alignment as a Developmental Process

The paper's most striking finding for biological plausibility is that the network **learns to do credit assignment** — it doesn't start with it. During early training, weight updates are nearly orthogonal to what backprop prescribes. Over epochs, feedforward and feedback weight matrices align, and updates converge toward the backprop gradient. This suggests that early postnatal development might involve a period where the cortical microcircuit is calibrating its feedback pathways — learning how to learn — before effective hierarchical learning can begin. The self-predicting state of [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] makes this explicit: the lateral microcircuit must first learn to predict top-down feedback before errors can be computed.

### Plateau Potentials as Error Carriers

The paper reframes apical plateau potentials — well-documented electrophysiological events driven by VGCC-mediated calcium spikes in distal dendrites — as carriers of feedback error information. The temporal averaging + nonlinearity that defines plateau potentials in the model is motivated by the biophysics: calcium spike generation in the apical shaft involves integration over ~20-30 ms windows followed by a regenerative threshold (Larkum et al. 1999). Bittner et al. (2015) showed that such plateau potentials can guide plasticity in vivo.

## Connections to Existing Knowledge

- **[[Credit Assignment]]**: First spiking demonstration that segregated dendrites enable hierarchical credit assignment with random feedback weights. Bridges the conceptual framework of [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]] to the later continuous-time implementations.
- **[[Dendritic Computation]]**: Exploits the same basal/apical segregation as the full lineage, but with a specific biophysical mechanism (plateau potentials from temporal averaging + sigmoid) rather than burst rate (Kording) or prediction errors (Sacramento).
- **[[Hebbian Learning]]**: Weight updates are local gradient descent on local error functions — each synapse sees only its own pre/post variables. The local target incorporates feedback information via the plateau potential, enriching the local rule with hierarchical credit.
- **[[Action Potential]]**: Uses spiking neurons (Poisson process driven by somatic voltage), unlike the rate models of Kording and Sacramento. The plateau potential mechanism specifically mimics dendritic calcium spike events.
- **[[Predictive Coding]]**: The two-phase operation can be interpreted as a crude prediction-error scheme: the forward phase generates a prediction, the target phase delivers the actual outcome, and the difference drives learning. Sacramento (2018) makes this continuous and explicit.

## Open Questions Raised

- Can the two-phase requirement be eliminated while retaining spiking neurons? Sacramento (2018) eliminates phases but uses rate neurons; Payeur (2020) uses spiking neurons without phases but with a different mechanism (burst/spike). A spiking model with continuous dendritic prediction errors — combining Sacramento's no-phase property with Guerguiev's spiking — has not been demonstrated.
- How should feedback weights be structured in cortex? Sparse random weights work in the model if scaled, but is there a biologically optimal sparsity/magnitude combination? Does cortical feedback connectivity follow such a pattern?
- The model requires a mechanism for coordinating forward and plateau phases across the network. Neuromodulatory signals, oscillatory gating, and SST interneuron disinhibition are all candidates. Which one does the brain use, if any?
- Does a developmental period of "learning to do credit assignment" (feedback alignment convergence) exist in mammalian cortex? This might correspond to critical period plasticity in sensory cortices.

## Sources

Guerguiev, J., Lillicrap, T.P. & Richards, B.A. (2017). Towards deep learning with segregated dendrites. *eLife*, 6:e22901.
