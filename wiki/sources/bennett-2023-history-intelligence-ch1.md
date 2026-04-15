---
title: "A Brief History of Intelligence — Chapter 1: The World Before Brains"
type: source
source_type: book
authors:
  - "Max Bennett"
year: 2023
doi: ""
tags: [evolution, neurons, synapses, nerve-nets, adaptation, rate-coding, brain-evolution]
date_ingested: 2026-04-10
key_finding: "Neurons didn't invent new computational primitives — they provided a network architecture (especially synapses enabling pairwise activity-dependent plasticity) at the speed and spatial scale required for macroscopic active hunting."
---

## Overview

Chapter 1 traces the world before brains — from abiogenesis through the evolution of neurons and the first nerve nets. [[Max Bennett]] establishes what neurons are, why they evolved, and what they genuinely added to biological computation. The core argument: neurons are a **medium**, not a message. Every computational primitive they implement (excitation, inhibition, thresholding, adaptation) already existed in unicellular organisms. What neurons added was a **network architecture** — massive fan-in/fan-out, reconfigurable graph structure, and crucially, [[Synapses|pairwise activity-dependent plasticity]] — at the speed and spatial scale required for macroscopic active hunting.

[PDF Ch.1a](../../raw/books/a_brief_history_of_intelligence/chunk-2.pdf) | [PDF Ch.1b](../../raw/books/a_brief_history_of_intelligence/chunk-3.pdf) | [Ch.1a Transcript](../../raw/books/a_brief_history_of_intelligence/chunk-2-transcript.md) | [Ch.1b Transcript](../../raw/books/a_brief_history_of_intelligence/chunk-3-transcript.md)

## Key Findings

### From Abiogenesis to the Need for Neurons

**Protein synthesis** enabled two categories of proteins that constitute primitive intelligence:
- **Movement proteins** (molecular motors) — comparable to boat propellers
- **Perception proteins** (receptors) — detect temperature, light, chemicals

Together these gave bacteria the ability to swim toward favorable conditions and away from threats.

**The Great Oxygenation Event** (~2.4 Gya): Cyanobacteria evolved photosynthesis, flooding Earth with oxygen. Aerobic respiration is ~15× more efficient than anaerobic, making active hunting energetically viable for the first time and launching the predator-prey arms race that drove brain evolution.

**Three levels of pre-brain life** (organized by size and mobility, not kingdom):
1. Single-celled organisms
2. Small multicellular organisms (mobile via cellular propellers, could engulf single-celled life)
3. Large multicellular organisms (too big for cellular propellers, immobile)

### Why Only Animals Evolved Neurons

Both fungi and animals are respiratory eukaryotes that eat other life. The split:
- **Fungi**: external digestion (secrete enzymes, absorb nutrients, wait for things to die)
- **Animals**: internal digestion (active hunting, trap food in a gut cavity)

Only the animal strategy of hunting level-2 multicellular life required real-time sensing and coordinated movement at macroscopic scale — hence neurons. **The harder strategy drives innovation**: fungi outweigh animals 6:1 by biomass but never needed neurons.

### Neuron Universality

All neurons, from jellyfish to humans, are fundamentally identical in their basic operation. Evolution locked in the neuron's form ~600+ million years ago and has only rewired since then. Intelligence differences between species come entirely from **wiring** — connectivity, plasticity rules, and architecture — not from the computational unit itself.

### Adrian's Three Discoveries

Edgar Adrian established three universal features of neurons:
1. **All-or-nothing spikes** — neurons fire discrete [[Action Potential|action potentials]], not continuous signals
2. **Rate coding** — information encoded in firing rate (heavier weight → more spikes per second)
3. **[[Neural Adaptation]]** — neurons constantly remap the stimulus-to-firing-rate relationship, encoding relative changes rather than absolute values. Solves the dynamic range problem: natural variables span a million-fold range but firing rate caps at ~500 Hz.

### The Synapse as the Key Novelty

The transcript discussion pushed well beyond Bennett's text on the question of what neurons genuinely added. The conclusion:

Individual computational primitives all predate neurons:
- **Excitation** — exists in bacterial signaling cascades
- **Inhibition** — exists in protein regulatory networks
- **Thresholding** — exists in bistable molecular switches
- **Adaptation** — exists in bacterial chemotaxis

The [[Synapses|synapse]] is the genuinely novel structure: the only known biological substrate where **two specific cells' activity states converge and connection strength can be modified based on their joint activity**. Non-neural analogs were examined (e.g., Physarum slime mold flow networks) and found to lack true pairwise activity-dependent plasticity — Physarum responds to local flow magnitude, not correlated activity of two connected nodes.

This makes the synapse the physical prerequisite for [[Hebbian Learning]]. Without it, there's no structure for implementing "fire together, wire together."

### Neurons as Speed/Range Upgrade

Chemical diffusion scales poorly with distance (square of distance, plus enzymatic degradation in biological tissue). Electrical propagation via [[Action Potential|action potentials]] uses active regeneration at nodes of Ranvier, maintaining signal integrity over macroscopic distances. Neurons solved the **engineering problem** of coordinating a large multicellular body in real time.

### Nerve Nets

Before brains, animals had **nerve nets**: distributed webs of independent neural circuits, each implementing independent reflexes. Corals and jellyfish still have this architecture. There is no central coordination — each reflex arc operates independently. The first breakthrough in brain evolution was centralizing nerve nets into brains.

## Implications

**For the wiki's core question (how does the brain learn):**
- The neuron is a fixed, universal unit — all the magic is in connectivity and plasticity. This frames the centrality of [[Hebbian Learning]], [[Sparse Coding]], and architectural organization.
- The synapse is the critical innovation for learning: pairwise activity-dependent modification of connection strength is unique to neural systems and is the substrate for all associative learning.
- Computational primitives are older than neurons. What neurons added was the **network architecture** and **communication medium** that enabled these primitives to operate at macroscopic scale.

**For understanding evolution's investments:**
- Converges with [[meister-2022-learning-fast-slow|Meister (2022)]] and [[li-2024-prediction-noise-reward|Li et al. (2024)]]: the basic learning rules are simple; evolution invested in architecture, representations, and control systems.
- The "harder strategy drives innovation" pattern (fungi vs. animals) suggests that selection pressure from the predator-prey arms race was the primary driver of neural evolution.

## Connections to Existing Knowledge

- **[[Synapses]]**: Identified as the key computational novelty of neurons — the physical substrate for [[Hebbian Learning]]
- **[[Hebbian Learning]]**: Cannot exist without the synapse's pairwise activity-dependent plasticity
- **[[Action Potential]]**: Adrian's spike discovery; Bennett emphasizes all-or-nothing nature and rate coding
- **[[Neural Adaptation]]**: Adrian's third discovery; encoding relative changes rather than absolute values
- **[[Sparse Coding]]**: Inhibition (discovered by Eccles) enables the competitive dynamics that produce sparse representations
- **[[Neural Noise]]**: Stochastic channel behavior is universal across the fixed neuronal unit
- **[[Predictive Coding]]**: Adaptation (encoding deviations from baseline) is conceptually related to prediction error

## Open Questions Raised

- Is there any pre-neural system with true pairwise activity-dependent plasticity, or is the synapse genuinely unique?
- How did nerve nets become centralized brains? What selection pressures drove centralization? (Breakthrough #1, to be covered in later chapters)
- What are the Five Breakthroughs specifically? (later chapters)

## Sources

Popular science book, Chapters 1a-1b. Bennett's claims were partially verified against primary literature in the transcripts: the "animal template" (gastrulation/neurons/muscles) describes Eumetazoa not all Metazoa; electrical propagation uses active regeneration not passive signal integrity.
