---
title: "Timothy P. Lillicrap"
type: person
tags: [credit-assignment, feedback-alignment, deep-learning, backpropagation, computational-neuroscience, philosophy-of-neuroscience]
affiliation: "Google DeepMind (formerly University College London)"
source_count: 2
last_updated: 2026-04-30
---

Computational neuroscientist and AI researcher; key figure in biologically plausible deep learning. Introduced **feedback alignment** (Lillicrap et al. 2016) — the discovery that random, fixed feedback weights can support learning because feedforward weights align to them during training. This finding is foundational for the entire dendritic credit assignment lineage: [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]], [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]], and [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] all rely on or demonstrate feedback alignment as the mechanism that relaxes the weight transport constraint.

Co-author on Guerguiev et al. (2017) and also showed that random synaptic feedback weights support error backpropagation in deep networks (Lillicrap et al. 2016, *Nature Communications*).

In a methodological-philosophical register, Lillicrap co-authored [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — the constructive sequel to [[jonas-2017-microprocessor-critique|Jonas & Kording (2017)]]. The paper supplies the [[principles-vs-parameters|principles-vs-parameters]] decomposition: trained neural networks (and by analogy brains) are compressible at the level of the recipe that builds them (architecture, learning rule, loss function) but not at the level of the trained weights, so neuroscience should target the recipe. This positions Lillicrap's own concrete research — feedback alignment as a learning *rule* — as a paradigmatic example of the principles-level work the paper advocates.

## Sources in Wiki

- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] — segregated dendrites for spiking credit assignment
- [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording (2019)]] — principles-vs-parameters; compressibility argument; methodological program
