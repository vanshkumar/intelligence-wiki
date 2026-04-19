---
title: "Inhibitory Circuits"
type: concept
aliases: ["inhibition", "interneurons", "inhibitory interneurons", "GABAergic", "PV+ interneurons", "SST+ interneurons"]
tags: [inhibition, interneurons, GABA, computation, microcircuit]
source_count: 7
last_updated: 2026-04-18
confidence: established
---

Inhibitory circuits — networks of GABAergic interneurons — perform essential computational functions in cortical and subcortical circuits. Far from simply suppressing activity, different interneuron types implement distinct computations: gain control, competitive selection, signal linearization, and temporal structuring. Individual computational primitives like inhibition predate neurons ([[bennett-2023-history-intelligence-ch1|Bennett, 2023]]), but the diversity of interneuron types and their precise targeting of different cellular compartments is a distinctly neural innovation.

## Interneuron Types and Their Computational Roles

Different interneuron classes target different compartments of pyramidal neurons, implementing different computations:

### Parvalbumin-positive (PV+) — Perisomatic Inhibition

PV+ basket cells target the soma and proximal dendrites of pyramidal neurons. They provide fast, powerful inhibition that controls the **timing and rate** of pyramidal cell output. PV+ inhibition implements:
- **[[Divisive Normalization]]**: Shunting inhibition at the soma divides (rather than subtracts) the neuron's response by population activity, preserving discriminability across dynamic range ([[gerstner-neuronal-dynamics-ch1|Gerstner et al., Ch. 1]])
- **Winner-take-all dynamics** for [[Sparse Coding]]: strongly driven neurons suppress weakly driven ones through lateral PV+ inhibition, concentrating activity in a few neurons per stimulus
- **Gamma oscillations**: PV+ networks generate fast (~30-80 Hz) oscillations that temporally structure cortical computation

### Somatostatin-positive (SST+) — Dendritic Inhibition

SST+ (Martinotti) cells target the **apical dendrites** of pyramidal neurons. This compartment-specific targeting has direct implications for [[Credit Assignment]], with two distinct computational roles proposed:

**Prediction and cancellation of top-down feedback** ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al., 2018]]): SST interneurons receive lateral input from same-layer pyramidal cells and project back to pyramidal apical dendrites. They learn to predict and cancel the top-down feedback, establishing a **self-predicting state** where apical compartments are silent. When the prediction fails (novel teaching signal), the mismatch at the apical dendrite is a prediction error that drives learning. The interneuron-to-pyramidal apical learning rule is a dendritic variant of homeostatic inhibitory plasticity (Vogels et al. 2011) — apical synapses adjust until the apical voltage reaches rest. This is consistent with monosynaptic input mapping showing that SST cells receive top-down projections (Leinweber et al. 2017).

**Linearization of burst probability** ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al., 2020]]): SST+ interneurons targeting apical dendrites keep burst probabilities in a linear operating range, preventing saturation of the credit signal. Without this linearization, the burst probability would saturate at high feedback input, distorting the credit signal. This is a computational necessity for the burst-dependent mechanism to approximate backpropagation gradients.

**Error signal carrier via STF connections** ([[greedy-2022-single-phase-burstccn|Greedy et al., 2022]]): In BurstCCN, SST+ dendrite-targeting interneurons are the biological substrate of the **Y pathway** — STF (short-term facilitating) feedback connections that carry burst rates backward. Because STF selectively transmits bursts, these connections decode the error signal from higher areas. A separate Q pathway (STD, possibly direct cortico-cortical projections) cancels the baseline burst signal at apical dendrites, leaving only the error. The prediction: disrupting SST+ STF connections should impair burst decoding and obstruct learning in the layer below.

These three roles are complementary rather than contradictory — prediction/cancellation describes what SST interneurons compute (Sacramento), linearization describes the operating regime they maintain (Payeur), and STF error transmission describes the signal they carry (BurstCCN). All predict that manipulating SST+ apical-targeting interneurons should impair hierarchical credit assignment and disrupt learning.

### NDNF+ — Layer 1 Gating of Distal Dendritic Input

NDNF+ interneurons reside in cortical **layer 1** and inhibit the distal apical tuft of pyramidal neurons — the compartment where long-range cortico-cortical feedback arrives. [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] demonstrate that optogenetic activation of NDNF+ L1 interneurons abolishes **vectorized dendritic error signals** (cell-specific SD residuals encoding error derivatives) and impairs learning in a neurofeedback BCI task. This is the first causal evidence that a specific interneuron type gates the dendritic teaching signals predicted by the credit assignment lineage.

NDNF+ interneurons complement SST+ Martinotti cells in a proposed **laminar division of labor**: SST+ cells target mid-apical dendrites and may implement linearization ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al., 2020]]) and prediction/cancellation ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al., 2018]]), while NDNF+ cells gate the distal tuft where top-down feedback input terminates. Disrupting either should impair credit assignment, but through different mechanisms — NDNF+ by blocking the arrival of the teaching signal, SST+ by corrupting its processing.

### VIP+ — Disinhibition

VIP+ interneurons primarily inhibit other interneurons (especially SST+ cells), producing **disinhibition** of pyramidal neurons. This creates a circuit motif where activating VIP+ cells releases pyramidal neurons from SST+ inhibition, potentially gating plasticity or switching between processing modes. VIP+ circuits are less well-characterized in the wiki's current sources but are increasingly recognized as important for attentional gating and learning.

## Inhibition Dominates Network-Level Dynamics

Beyond compartment-specific roles for individual neurons, inhibition is the dominant driver of cortical network-level dynamics. [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] showed analytically that a sparsely connected excitatory-inhibitory spiking network has four generic regimes (SR, AR, [[Asynchronous Irregular State|AI]], SI) separated by Hopf and saddle-node bifurcations — and the *inhibition-dominated* regime (g > 4, where g is the relative strength of recurrent inhibition to recurrent excitation) is where cortex-like irregular, low-rate, weakly-correlated activity emerges. Both cortical oscillation families — **fast oscillations** (~100–200 Hz, matching sharp-wave ripples, frequency ≈ 1/2D set by synaptic delay) and **slow oscillations** (~20–60 Hz, matching gamma, frequency set by membrane τ) — appear on Hopf bifurcation lines of this inhibition-dominated state. The oscillations are generated primarily by the inhibitory population; excitation is the perturbation that sets the operating point.

This elevates the role of inhibition from "gain control and compartment-specific computation" to **the parameter that sets the operating regime of the whole network**. The same anatomical circuit can express quiescent, asynchronous-irregular, gamma-oscillatory, or ripple-oscillatory dynamics depending on the balance `g` and external drive — and inhibition is what tunes `g`. Neuromodulation of inhibitory interneurons (e.g., VIP+ disinhibition, acetylcholine on PV+ cells) can thus switch between regimes without rewiring.

## Inhibition as a Computational Primitive

[[bennett-2023-history-intelligence-ch1|Bennett (2023)]] notes that inhibition as a signaling mechanism predates neurons — unicellular organisms use inhibitory chemical signals. What neurons added was the **spatial precision** and **cell-type diversity** of inhibition: different interneuron types targeting different compartments of the same postsynaptic neuron to implement different computations simultaneously.

## Sources

- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — SST interneurons predict and cancel top-down feedback, establishing self-predicting state for credit assignment
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — SST+ interneurons linearize burst probability for credit assignment
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] — SST+ as STF error-signal carriers (Y pathway) in BurstCCN
- [[gerstner-neuronal-dynamics-ch1|Gerstner et al., Neuronal Dynamics Ch. 1]] — shunting inhibition as divisive normalization
- [[bennett-2023-history-intelligence-ch1|Bennett (2023), Ch. 1]] — inhibition as a pre-neural computational primitive
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] — NDNF+ L1 interneuron activation abolishes vectorized dendritic error signals and impairs learning
- [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] — inhibition-dominated (g > 4) regime is where AI activity and both cortical oscillation families (gamma, sharp-wave ripples) emerge; oscillations are carried primarily by the inhibitory population
