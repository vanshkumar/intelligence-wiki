---
title: "Calcium Signaling"
type: mechanism
aliases: ["calcium", "Ca2+", "calcium dynamics", "calcium influx", "NMDA receptor"]
tags: [calcium, plasticity, ion-channels, coincidence-detection, molecular]
source_count: 2
last_updated: 2026-04-11
level: molecular
---

Calcium (Ca²⁺) is the central molecular signal bridging electrical activity and lasting synaptic change. It serves dual roles in neural computation: as a **transient state variable** (mediating adaptation and excitability changes that vanish when calcium is pumped out) and as a **trigger for lasting plasticity** (initiating self-sustaining downstream cascades that persist after calcium is removed). The same ion, the same concentration-sensing logic — but genetically encoded downstream readers determine whether the effect is transient or lasting.

## NMDA Receptor as Coincidence Detector

The NMDA receptor is the key molecular device implementing [[Hebbian Learning|Hebbian coincidence detection]] ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]). It requires **both**:
1. **Pre-synaptic glutamate release** — binds the receptor
2. **Post-synaptic depolarization** — relieves the voltage-dependent Mg²⁺ block

Only when both conditions are met does the channel open and pass calcium. This makes the NMDA receptor a molecular AND gate for correlated pre/post activity — the biophysical implementation of "neurons that fire together wire together."

## Calcium and Plasticity Direction

The magnitude and temporal profile of calcium influx determines the direction of [[Long-Term Potentiation|synaptic plasticity]]:
- **Large, rapid calcium transients** → activate CaMKII and related kinases → LTP
- **Smaller, prolonged calcium elevations** → activate calcineurin and related phosphatases → LTD

This is the **calcium control hypothesis** — a single ionic signal produces opposite outcomes depending on its temporal dynamics.

## Calcium-as-State vs. Calcium-as-Trigger

A critical distinction ([[gerstner-neuronal-dynamics-ch2|Gerstner et al., Ch. 2]]):

**Calcium-as-state-variable**: Calcium accumulates during spiking and activates calcium-dependent K⁺ channels (I_K[Ca]), producing [[Neural Adaptation|spike-frequency adaptation]]. When calcium is pumped out, the effect vanishes. Here calcium IS the memory — transient, activity-dependent, and fully reversible.

**Calcium-as-trigger**: Calcium influx through NMDA receptors initiates self-sustaining downstream changes — CaMKII autophosphorylation, AMPA receptor trafficking, structural synaptic modification — that persist after calcium is removed. Here calcium triggers a state transition that outlasts the signal itself. This is how a transient electrical event (correlated firing) produces a lasting structural change (modified synapse).

The difference lies not in the calcium signal but in the **genetically encoded downstream readers** — the proteins that detect calcium concentration and decide whether to produce a transient or lasting response. This is one mechanism by which DNA bridges evolutionary timescales to moment-to-moment learning rules.

## Dendritic Calcium Spikes

Beyond its role at synapses, calcium mediates regenerative events in [[Dendritic Computation|dendrites]]. Voltage-gated calcium channels (VGCCs) in apical dendrites can produce **dendritic calcium spikes** — regenerative events analogous to somatic [[Action Potential|action potentials]] but mediated by calcium rather than sodium. These calcium spikes propagate toward the soma and can trigger bursts of somatic action potentials ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]). Top-down feedback controls whether these dendritic calcium spikes occur, making calcium the physical medium through which higher cortical areas steer plasticity in lower areas for [[Credit Assignment]].

## Sources

- [[gerstner-neuronal-dynamics-ch2|Gerstner et al., Neuronal Dynamics Ch. 2]] — NMDA coincidence detection, calcium control hypothesis, calcium-as-state vs calcium-as-trigger
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — dendritic calcium spikes via VGCCs as substrate for top-down burst control
