---
title: "Long-Term Potentiation and Depression"
type: mechanism
aliases: ["LTP", "LTD", "long-term potentiation", "long-term depression", "synaptic potentiation"]
tags: [plasticity, synapse, learning, calcium, glutamate]
source_count: 5
last_updated: 2026-04-11
level: cellular
---

Long-term potentiation (LTP) is a sustained strengthening of synaptic transmission following correlated pre- and post-synaptic activity. Long-term depression (LTD) is the converse — a sustained weakening following uncorrelated or low-frequency activity. Together, LTP and LTD are the primary cellular mechanisms underlying [[Hebbian Learning]] and are the physical substrate by which experience modifies neural circuits.

## Induction

LTP at excitatory synapses typically requires:
1. **Pre-synaptic glutamate release** — activates AMPA and NMDA receptors
2. **Post-synaptic depolarization** — relieves the Mg²⁺ block of the NMDA receptor
3. **Calcium influx through NMDA receptors** — the NMDA receptor acts as a molecular coincidence detector for correlated pre/post activity ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]])

The critical variable is the magnitude and duration of the [[Calcium Signaling|calcium signal]]: large, rapid calcium transients favor LTP; smaller, prolonged calcium elevations favor LTD. This is the **calcium control hypothesis** — the same ion, through different temporal patterns, produces opposite plasticity outcomes.

## Expression

The calcium-as-trigger mechanism is what makes LTP lasting ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]): calcium influx initiates self-sustaining downstream cascades — CaMKII autophosphorylation, AMPA receptor trafficking to the synapse, and eventually structural synaptic modification — that persist after calcium is removed. Genetically encoded downstream proteins determine whether a calcium signal produces transient or lasting change. This is how DNA bridges evolutionary timescales to learning rules.

## Frequency Dependence

A well-established experimental finding: high-frequency stimulation produces LTP, low-frequency stimulation produces LTD. [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] reinterpret this through the burst/spike distinction — high-frequency bursts in pyramidal neurons drive LTP at the neuron's input [[Synapses|synapses]], while isolated spikes drive LTD. The sign of plasticity is controlled by top-down feedback via [[Dendritic Computation|apical dendrites]], which modulates burst probability.

## Beyond Weight Tuning: LTP Grows Architecture

LTP doesn't only strengthen existing connections — it can **replicate** them. Multi-synaptic boutons (MSBs), where the same presynaptic axon contacts the same postsynaptic dendrite at multiple points, increase 6-fold after LTP induction (Toni et al. 1999). [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] show that these repeated inputs across dendritic branches directly increase a neuron's computational capacity. Learning thus reshapes the computational architecture, not just the parameters.

## Role in Credit Assignment

In the burst-dependent [[Credit Assignment]] framework ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]):
- **Burst → LTP**: Top-down feedback triggers dendritic calcium spikes, causing the neuron to burst. Burst events above the adaptive threshold P̄ strengthen feedforward synapses.
- **Isolated spike → LTD**: Without top-down support, isolated spikes below the threshold weaken feedforward synapses.
- The adaptive threshold P̄ ensures the system responds to *changes* in burst probability, not absolute levels — formally analogous to [[Neural Adaptation]].

## Role in Memory Consolidation

During slow-wave sleep, [[Hippocampus|hippocampal]] CA1 cells fire 0-100 ms before [[Prefrontal Cortex|mPFC]] cells in sharp-wave/ripple-driven bursts ([[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al., 2009]]). This hippocampus→PFC timing falls squarely within the STDP window, with the pre→post ordering that would favor LTP at hippocampal-to-prefrontal synapses. Repeated SWR-driven reactivation across many sleep cycles could progressively strengthen these connections, providing a cellular mechanism for [[Memory Consolidation|systems consolidation]].

## Sources

- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — calcium-plasticity bridge, NMDA as coincidence detector
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst/spike distinction determines LTP vs LTD; credit assignment via dendritic modulation of burst probability
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — LTP-induced MSBs increase single-neuron computational capacity
- [[meister-2022-learning-fast-slow|Meister (2022)]] — LTP is fast; the bottleneck for learning is the representation, not the plasticity mechanism
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — hippocampus→PFC spike timing during SWS falls within the STDP window for LTP
