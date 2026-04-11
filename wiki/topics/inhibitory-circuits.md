---
title: "Inhibitory Circuits"
type: concept
aliases: ["inhibition", "interneurons", "inhibitory interneurons", "GABAergic", "PV+ interneurons", "SST+ interneurons"]
tags: [inhibition, interneurons, GABA, computation, microcircuit]
source_count: 3
last_updated: 2026-04-11
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

SST+ (Martinotti) cells target the **apical dendrites** of pyramidal neurons. This compartment-specific targeting has direct implications for [[Credit Assignment]]:

[[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] show that SST+ interneurons targeting apical dendrites **linearize** the burst probability response of pyramidal neurons. Without this linearization, the burst probability would saturate at high feedback input, distorting the credit signal. SST+ inhibition keeps burst probabilities in a linear operating range, ensuring that the top-down teaching signal is faithfully transmitted. This is a computational necessity for the burst-dependent credit assignment mechanism to approximate backpropagation gradients.

The prediction: manipulating SST+ interneurons that target apical dendrites should impair hierarchical credit assignment and disrupt learning in cortical circuits.

### VIP+ — Disinhibition

VIP+ interneurons primarily inhibit other interneurons (especially SST+ cells), producing **disinhibition** of pyramidal neurons. This creates a circuit motif where activating VIP+ cells releases pyramidal neurons from SST+ inhibition, potentially gating plasticity or switching between processing modes. VIP+ circuits are less well-characterized in the wiki's current sources but are increasingly recognized as important for attentional gating and learning.

## Inhibition as a Computational Primitive

[[bennett-2023-history-intelligence-ch1|Bennett (2023)]] notes that inhibition as a signaling mechanism predates neurons — unicellular organisms use inhibitory chemical signals. What neurons added was the **spatial precision** and **cell-type diversity** of inhibition: different interneuron types targeting different compartments of the same postsynaptic neuron to implement different computations simultaneously.

## Sources

- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — SST+ interneurons linearize burst probability for credit assignment
- [[gerstner-neuronal-dynamics-ch1|Gerstner et al., Neuronal Dynamics Ch. 1]] — shunting inhibition as divisive normalization
- [[bennett-2023-history-intelligence-ch1|Bennett (2023), Ch. 1]] — inhibition as a pre-neural computational primitive
