---
title: "Action Potential"
type: mechanism
aliases: ["spike", "nerve impulse", "AP"]
tags: [biophysics, ion-channels, hodgkin-huxley, neuron, electrical-signaling]
source_count: 2
last_updated: 2026-04-10
level: cellular
---

The action potential is the all-or-nothing electrical pulse by which neurons communicate over long distances. It is the fundamental unit of neural signaling — discovered by Edgar Adrian to be discrete (not graded), with information encoded in firing rate rather than pulse amplitude.

## Biophysical Mechanism (Hodgkin-Huxley)

The action potential arises from **voltage-dependent ion channel conductances** creating positive and negative feedback loops with different timescales ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]):

**Upstroke:** Depolarization opens Na⁺ channels (fast activation, gating variable m). Na⁺ influx further depolarizes the membrane → more Na⁺ channels open. This positive feedback drives a rapid voltage rise.

**Termination:** Two slower negative feedback processes catch up:
- Na⁺ inactivation (h) — shuts down the same Na⁺ channels that drove the upstroke
- K⁺ activation (n) — opens K⁺ channels, driving repolarization via K⁺ efflux

**Afterhyperpolarization:** K⁺ channels remain open briefly after Na⁺ channels close, hyperpolarizing the membrane below rest. Creates the **refractory period** during which a new spike cannot be initiated.

The entire sequence depends on **timescale separation**: if all gating variables equilibrated instantly, the system would reduce to a 1D equation du/dt = F(u), capable only of monotonic approaches to fixed points — no spikes possible. All interesting neural dynamics arise from variables being out of equilibrium.

## The Ion Channel Design Space

Beyond the basic Na⁺/K⁺ spike mechanism, neurons express a diverse complement of ion channels that extend their computational repertoire. Each channel adds a gating variable characterized by its voltage sensitivity and kinetic timescale:

- **I_M** (slow K⁺) — spike-frequency adaptation: firing rate decreases during sustained input
- **I_h** (hyperpolarization-activated) — subthreshold oscillations, sag potential. Contributes to [[Theta Oscillations]] and intrinsic rhythmicity
- **I_T** (low-threshold Ca²⁺) — postinhibitory rebound: spiking after release from inhibition. Key mechanism in thalamic relay and hippocampal circuits
- **I_K[Ca]** (calcium-dependent K⁺) — adaptation gated by intracellular calcium, providing a non-voltage pathway for controlling excitability

### Type I vs. Type II Excitability

Different ion channel complements produce qualitatively different encoding:
- **Type I**: Continuous frequency-current curve; can fire at arbitrarily low rates; encodes graded input
- **Type II**: Discontinuous curve; jumps to a finite frequency at threshold; better for detecting input presence

A ~20 mV shift in Na⁺ inactivation can switch between types — small parametric changes, qualitative computational differences.

## The Star Topology Constraint

In single-compartment neuron models, all gating variables couple only through the shared voltage variable — a **star topology**. This bottleneck limits dynamical richness regardless of how many channels are added. Real neurons escape via:
1. **Spatial structure** — dendritic compartments with local voltages
2. **Non-voltage state variables** — calcium concentration, second messengers

Both escape routes are where **plasticity mechanisms** operate: calcium signaling through NMDA receptors is the coincidence detector for [[Hebbian Learning]], and dendritic computation shapes what signals reach the soma.

## Role in Neural Communication

Action potentials solve the **distance problem** of neural signaling. Chemical diffusion scales poorly with distance (square of distance, plus enzymatic degradation in biological tissue). Electrical propagation via action potentials uses active regeneration at nodes of Ranvier, maintaining signal integrity over macroscopic distances ([[bennett-2023-history-intelligence|Bennett, 2023]]).

Adrian's three key discoveries about action potentials:
1. **All-or-nothing** — discrete pulses, not continuous signals
2. **Rate coding** — information in firing frequency
3. **Adaptation** — neurons remap stimulus-to-rate dynamically, encoding relative changes rather than absolute values

## Sources

- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — Hodgkin-Huxley model, ion channel design space, star topology
- [[gerstner-neuronal-dynamics-ch1|Gerstner et al., Neuronal Dynamics Ch. 1]] — LIF model as simplified action potential mechanism
