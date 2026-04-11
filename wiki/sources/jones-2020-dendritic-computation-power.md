---
title: "Can Single Neurons Solve MNIST? The Computational Power of Biological Dendritic Trees"
type: source
source_type: paper
authors:
  - "Ilenna Simone Jones"
  - "Konrad Kording"
year: 2020
doi: "10.48550/arXiv.2009.01269"
tags: [dendrites, computation, pyramidal-neurons, sparse-coding, single-neuron, nonlinearity]
date_ingested: 2026-04-10
key_finding: "A single neuron with nonlinear dendritic branching (modeled as a sparse binary tree ANN) can solve complex classification tasks, approaching the performance of a 2-layer fully connected network — point neuron models severely underestimate single-neuron computational power."
---

## Overview

This paper quantifies the computational power of individual biological neurons by modeling their dendritic trees as trainable sparse binary tree ANNs (*k*-trees). The key insight: because dendrites impose nonlinearities on their inputs *before* summation at the soma, a single biological neuron is not a point integrator (McCulloch-Pitts / standard ANN unit) but rather an internal multi-layer network. The *k*-tree model — where *k* dendritic subtrees each receive the full input — shows that dendritic nonlinearity and repeated synaptic inputs together allow a single neuron to approach the classification performance of a parameter-matched 2-layer fully connected network on standard benchmarks (MNIST, CIFAR-10, etc.).

[PDF](../../raw/papers/jones-2020.pdf)

## Key Findings

### Point Neurons Underestimate Single-Neuron Computation

Standard neuron models (McCulloch-Pitts, Hodgkin-Huxley, ANN units) treat the neuron as a point: inputs are linearly summed, then passed through an output nonlinearity. But biological dendrites impose **nonlinearities before summation at the soma** — active properties like NMDA spikes, calcium spikes, and voltage-gated conductances mean that synaptic clustering on a dendritic branch produces supralinear summation. A single dendritic branch acts like a sigmoidal subunit (Poirazi et al. 2003), making the neuron internally a two-layer network.

Jones & Kording formalize this by building a *k*-tree: a sparse ANN with binary tree connectivity constraints where each hidden node takes exactly 2 inputs and applies a leaky ReLU nonlinearity. A 1-tree (single dendritic subtree) represents one soma-connected branch; a *k*-tree repeats this structure *k* times with the same input, modeling **multi-synaptic boutons (MSBs)** — the biological phenomenon where the same presynaptic axon contacts the same postsynaptic dendrite at multiple points.

### Dendritic Nonlinearity Beats Linear Classification

On binary classification tasks across 7 datasets, the 1-tree (single dendritic tree, ~500-6000 parameters depending on input size) significantly outperforms a linear discriminant classifier (proxy for a point neuron) on 6 of 7 tasks:

- MNIST: 92.2% vs 87.5% (p < 0.0001)
- FMNIST: 79.0% vs 67.5% (p < 0.0001)
- EMNIST: 85.2% vs 58.2% (p < 0.0001)
- CIFAR-10: 56.1% vs 52.5% (p < 0.0005)

The exception is USPS (smallest input, fewest parameters) — the 1-tree likely lacks sufficient complexity. This demonstrates that dendritic nonlinearity provides genuine computational power beyond what a linear model can achieve.

### Repeated Inputs Approach Fully Connected Network Performance

Increasing *k* (the number of repeated dendritic subtrees receiving the same input) monotonically improves performance across all tasks. Remarkably, the 32-tree — still representing a *single neuron* — approaches or matches a parameter-matched 2-layer fully connected network (FCNN):

| Task | 32-tree | FCNN | p-value |
|------|---------|------|---------|
| MNIST | 96.4% | 97.0% | 0.016 |
| FMNIST | 83.0% | 82.9% | 0.752 |
| EMNIST | 98.5% | 98.5% | 0.736 |
| CIFAR-10 | 57.8% | 56.5% | 0.034 |

On FMNIST, EMNIST, and USPS, the 32-tree matches the FCNN with no significant difference. On CIFAR-10, the 32-tree actually *exceeds* the FCNN (though FCNN training was unstable on this task).

### Multi-Synaptic Boutons Are Biologically Real

The repeated-input model is not just a theoretical device — MSBs are a known biological phenomenon:

- Electron microscopy shows ~4 presynaptic axon synapses per postsynaptic neuron on average (Kincaid et al. 1998)
- MSBs occur ~11.5% of the time in rats in enriched environments (Jones et al. 1997)
- **LTP increases MSBs 6-fold** (Toni et al. 1999) — learning actively builds repeated synaptic connections

This means the brain doesn't just strengthen existing connections during learning; it **replicates** them across dendritic branches, which in the *k*-tree framework directly increases the neuron's computational capacity.

### The *k*-Tree as a Structured Sparse Network

The *k*-tree is formally a special case of a sparse ANN — each node connects to exactly 2 inputs, which is far more constrained than random sparsity or pruned dense networks (cf. lottery ticket hypothesis, Frankle & Carbin 2019). Despite these severe constraints, the biologically structured sparsity performs surprisingly well. This suggests that the **tree topology** of real dendrites is not arbitrary but computationally advantageous.

## Methods

- **Model**: Sparse ANN with binary tree connectivity constraints, implemented in PyTorch. Leaky ReLU (slope 0.01) at hidden nodes, sigmoid at output. Sparsity maintained by a "freeze mask" zeroing gradients at non-tree connections.
- **Tasks**: Binary classification on 7 datasets (MNIST, Fashion-MNIST, EMNIST, Kuzushiji-MNIST, CIFAR-10, SVHN, USPS). For each dataset, the least linearly separable pair of classes was selected via LDA.
- **Controls**: LDA linear classifier (lower bound, point neuron proxy) and parameter-matched 2-layer FCNN (upper bound, dense network).
- **Training**: Adam optimizer, binary cross-entropy loss, early stopping after 60 epochs with no improvement, batch size 256. 10-fold cross-validation.
- **Parameter matching**: FCNN hidden layer size h = 2k ensures matched parameter count between *k*-tree and FCNN.

## Limitations

- **Input format**: 1D vectorized pixel input is not biologically plausible — real neurons receive structured input from specific presynaptic populations, not flattened images. Input ordering affects performance (random permutation decreases it).
- **Weight sign**: All weights are unconstrained real values. Biologically, inter-compartmental weights (analogous to axial resistances between dendritic compartments) should be positive-only.
- **No weight sharing or convolution**: The model doesn't use convolutional structure, limiting comparison to more powerful ANN architectures.
- **Binary classification only**: Real neurons participate in multi-class computations within larger circuits.

## Implications

### For the wiki's core question (how does the brain learn)

This paper reframes what "a neuron" is computationally. If a single neuron is internally a multi-layer network, then a network of such neurons is far more powerful than standard ANN models suggest. The finding that LTP increases MSBs means that **learning doesn't just tune connection strengths — it grows the internal architecture of individual neurons**, increasing their computational capacity. This adds another dimension to the "simple rules, complex architecture" theme: the architecture is not fixed but is itself shaped by learning.

### For dendritic computation

This complements [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] from a different angle. Payeur shows dendrites matter because they **separate feedforward from feedback** for [[Credit Assignment|credit assignment]] — a functional compartmentalization argument. Jones & Kording show dendrites matter because their **nonlinear branching structure** gives each neuron multi-layer computational power — a raw capacity argument. Both papers argue against point neuron models, but for different reasons: Payeur for the informational architecture, Jones for the computational capacity.

## Connections to Existing Knowledge

- **[[Dendritic Computation]]**: Directly extends — the *k*-tree is a formalization of what dendritic branching computes. Complements Payeur's compartmentalization argument with a capacity argument
- **[[Action Potential]]**: The [[Action Potential#The Star Topology Constraint|star topology constraint]] limits point neuron models; dendritic trees escape it by providing multiple independent nonlinear subunits before somatic integration
- **[[Sparse Coding]]**: The *k*-tree is formally a sparse network; biologically structured sparsity (tree topology) appears computationally advantageous compared to random sparsity
- **[[Hebbian Learning]]**: LTP doesn't just strengthen synapses — it replicates them (MSBs), which in this framework increases single-neuron computational power. Learning grows the architecture
- **[[Synapses]]**: MSBs (multiple synapses between the same pre/post pair) are a known feature of cortical connectivity, upregulated by LTP, with direct computational consequences

## Open Questions Raised

- What is the computational role of dendritic morphological diversity? Different neuron types have radically different dendritic trees — does this correspond to different computational specializations?
- How does the *k*-tree framework interact with dendritic compartmentalization (Payeur)? Can you have both multi-layer computation within branches AND feedforward/feedback separation across compartments?
- Does the brain optimize dendritic morphology during development to maximize computational capacity for expected input statistics? Is dendritic branching pattern learned or genetically determined?
- How does structured sparsity (biological tree topology) compare to other sparsity patterns (random, pruned, lottery ticket) in terms of computational efficiency?

## Sources

Jones & Kording (2020). arXiv preprint, 2009.01269.
