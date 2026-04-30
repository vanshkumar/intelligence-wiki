---
title: "Konrad Kording"
type: person
tags: [computational-neuroscience, machine-learning, dendrites, neural-data-science, methods-validation, philosophy-of-neuroscience]
affiliation: "University of Pennsylvania (Departments of Neuroscience and Bioengineering)"
source_count: 4
last_updated: 2026-04-30
---

Computational neuroscientist working at the intersection of neuroscience and machine learning. Leads the Kording Lab at UPenn, applying data science and ML methods to understand neural computation. Earlier work at ETH Zurich (with [[Peter Konig]]) established foundational ideas about dendritic compartments as substrates for learning. Recent work increasingly engages with the philosophy of how neuroscientific methods should be validated against ground-truth-known artificial systems.

## Key Contributions in This Wiki

- Co-proposed the two-site synaptic integration framework: basal/apical dendritic compartments provide two independent variables per neuron, enabling backpropagation and self-supervised learning in cortical networks ([[kording-konig-2001-two-integration-sites|Kording & Konig, 2001]]). This is the conceptual seed of the burst-dependent credit assignment lineage
- Co-demonstrated that dendritic tree structure gives single biological neurons multi-layer computational power, far exceeding point neuron models ([[jones-2020-dendritic-computation-power|Jones & Kording, 2020]])
- Co-authored the methodological-philosophical thought experiment ([[jonas-2017-microprocessor-critique|Jonas & Kording, 2017]]) — applied standard systems-neuroscience analyses to a fully understood microprocessor (MOS 6502) and demonstrated that they do not recover computational understanding even with full access to every wire, every transistor, and the complete connectome. The paper provides a methodological warning against the assumption that data scarcity is the bottleneck and a constructive case for [[marrs-levels-of-analysis|Marr-levels-anchored]] validation of analytical methods
- Co-authored the constructive sequel ([[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording, 2019]]) — supplies the [[principles-vs-parameters|principles-vs-parameters]] decomposition. Where Jonas & Kording (2017) showed that standard methods do not recover Marr-level understanding even with ground truth, Lillicrap & Kording (2019) argue we should *expect* that — trained networks (and brains) are compressible at the level of the recipe that builds them but not at the level of the parameters they end up with — and reorganize the neuroscience program around the recipe (architecture, plasticity rules, developmental program) instead of the parameters (synaptic state, individual cell tuning)

## Sources

- [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]]
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]]
- [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]]
