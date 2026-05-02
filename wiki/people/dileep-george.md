---
title: "Dileep George"
type: person
tags: [graphical-models, hippocampus, cognitive-maps, probabilistic-ai, vicarious]
affiliation: "Google DeepMind (formerly Vicarious AI co-founder; Numenta)"
source_count: 1
last_updated: 2026-05-01
---

Dileep George is a computational neuroscientist and AI researcher whose work centers on hierarchical probabilistic graphical models as architectures for cortical computation. Co-founder (with Scott Phoenix) of Vicarious AI; previously co-founder of Numenta with Jeff Hawkins. Now at Google DeepMind. PhD from Stanford under Bruno Olshausen.

George's research program is a sustained pursuit of one architectural commitment: that cortical computation is best understood as **structured message passing on hierarchical probabilistic models**, in the lineage of HTM (Numenta), the Recursive Cortical Network (George et al. 2017 *Science* — solving CAPTCHAs with strong generalization from few examples), and CSCGs ([[george-2021-clone-structured-cognitive-graphs|George et al. 2021]]). The work consistently bets on inference algorithms with explicit graphical-model semantics rather than on dense connectionist architectures.

The CSCG paper extends this program to the hippocampus: a single clone-structured HMM trained by EM on (sensation, action) streams is offered as a unified mechanism for cognitive-map formation, transitive inference, schemas, splitter cells, place-cell remapping, replay, and hierarchical planning. The neuronal implementation maps clones to neurons and the transition matrix to lateral connectivity, with the EM algorithm hand-waved as approximated by [[Long-Term Potentiation|STDP]].

## Sources

- [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] — CSCGs as unified model of hippocampal cognitive-map function
