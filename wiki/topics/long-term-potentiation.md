---
title: "Long-Term Potentiation and Depression"
type: mechanism
aliases: ["LTP", "LTD", "long-term potentiation", "long-term depression", "synaptic potentiation", "late-phase LTP", "L-LTP"]
tags: [plasticity, synapse, learning, calcium, glutamate, creb, transcription]
source_count: 6
last_updated: 2026-04-28
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

## Late-Phase LTP and Transcriptional Consolidation

Early-phase LTP (E-LTP) is protein-synthesis-independent and decays within hours; late-phase LTP (L-LTP) requires new transcription and translation and persists for days to weeks. The transition from E-LTP to L-LTP is gated by the **[[creb|CREB]] cascade**: calcium influx → CaMKII / PKA / PKC / ERK activation → CREB phosphorylation at S133 → CRE-bound CREB drives transcription of immediate-early genes → IEG products produce structural synaptic modifications.

[[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] demonstrates that the consolidation half of this cascade — kinase activation, CREB phosphorylation, and CRE-dependent transcription — operates with the same temporal dynamics in non-neural human cell lines (SH-SY5Y, HEK293) as in *Aplysia* sensory neurons. This locates the **transcriptional consolidation step** at the cellular level rather than at the synapse: synapses contribute the pairwise specificity (which connection changes), but the cascade that decides whether a lasting change happens given the temporal pattern is broadly conserved across cell types. The [[spacing-effect|spacing effect]] in late-phase LTP therefore inherits the optimal-ITI dynamics of the cellular cascade — a 5–20-min optimal ITI in many systems is consistent with the cascade's intrinsic time constants.

## Role in Memory Consolidation

During slow-wave sleep, [[Hippocampus|hippocampal]] CA1 cells fire 0-100 ms before [[Prefrontal Cortex|mPFC]] cells in sharp-wave/ripple-driven bursts ([[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al., 2009]]). This hippocampus→PFC timing falls squarely within the STDP window, with the pre→post ordering that would favor LTP at hippocampal-to-prefrontal synapses. Repeated SWR-driven reactivation across many sleep cycles could progressively strengthen these connections, providing a cellular mechanism for [[Memory Consolidation|systems consolidation]].

## Sources

- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — calcium-plasticity bridge, NMDA as coincidence detector
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst/spike distinction determines LTP vs LTD; credit assignment via dendritic modulation of burst probability
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — LTP-induced MSBs increase single-neuron computational capacity
- [[meister-2022-learning-fast-slow|Meister (2022)]] — LTP is fast; the bottleneck for learning is the representation, not the plasticity mechanism
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — hippocampus→PFC spike timing during SWS falls within the STDP window for LTP
- [[kukushkin-2024-massed-spaced-non-neural|Kukushkin et al. (2024)]] — the [[creb|CREB]] cascade that gates late-phase LTP operates with the same temporal dynamics in non-neural human cells; transcriptional consolidation is a cellular-level process that the synapse adds pairwise specificity to. The [[spacing-effect|spacing effect]] in late-phase LTP inherits the optimal-ITI dynamics of the cellular cascade.
