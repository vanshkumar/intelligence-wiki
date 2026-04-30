---
title: "Karl Friston"
type: person
tags: [computational-neuroscience, free-energy-principle, active-inference, predictive-coding, bayesian-brain, neuroimaging]
affiliation: "Wellcome Trust Centre for Neuroimaging, University College London"
source_count: 1
last_updated: 2026-04-28
---

Karl Friston is a theoretical neuroscientist at the Wellcome Trust Centre for Neuroimaging, UCL. He is the principal architect of the **free-energy principle (FEP)** and **active inference** as a unified normative framework for perception, action, and learning, and the developer of statistical parametric mapping (SPM) and dynamic causal modelling (DCM) — the analytical machinery that has shaped a generation of fMRI and EEG/MEG studies.

## Themes in his work relevant to this wiki

- **The [[Free Energy Principle|free-energy principle]] (FEP).** A claim that any self-organizing system at non-equilibrium steady state with its environment must minimize a variational upper bound on the surprise of its sensory exchange. Perception, action, and learning are gradient descents on the same scalar — variational free energy — over recognition, action, and generative-model parameters respectively. The 2010 *Nature Reviews Neuroscience* review ([[friston-2010-free-energy-principle|Friston 2010]]) is the canonical statement of FEP as a *unified* brain theory; technical foundations are in Friston (2005–2009).
- **[[Active Inference]].** The embodied / continuous-time / motor extension of variational inference: agents act on their environment to make their sensations match their predictions. Generalizes the [[helmholtz-machine|Helmholtz machine]] (perception + learning) by adding action as a third variable that minimizes the same free energy objective.
- **Hierarchical [[Predictive Coding|predictive coding]] as the cortical implementation of FEP.** Friston has spelled out (Friston 2005, 2008; Bastos et al. 2012) how cortical microcircuits — superficial pyramidal cells carrying prediction errors, deep pyramidal cells carrying predictions, with precision-weighting via inverse-variance gain modulation — implement gradient descent on free energy.
- **Precision = synaptic gain = attention.** Friston's reading of attention as the optimization of inverse-variance weights on prediction-error units links FEP to biased-competition (Desimone-Duncan 1995) and [[divisive-normalization|Reynolds-Heeger normalization]] models of attention, and to neuromodulator function (dopamine encoding precision; ACh/NA encoding contextual uncertainty).
- **Statistical parametric mapping (SPM).** The widely-used software framework for analyzing brain-imaging data — the methodology under most modern fMRI and EEG/MEG group analyses.
- **Dynamic causal modelling (DCM).** A Bayesian framework for inferring effective connectivity between brain regions from neuroimaging data; an early concrete application of variational inference to neural data.

## Position relative to other lineages in this wiki

- **Helmholtz lineage.** Friston is the embodied / online-dynamics extension of [[dayan-hinton-1994-helmholtz-machine|Dayan-Hinton-Neal-Zemel (1994)]]'s Helmholtz machine. Where Dayan-Hinton optimize free energy over discrete latents and weights via offline wake-sleep, Friston commits to continuous-time gradient dynamics over recognition, weights, and action.
- **Predictive-coding lineage.** Friston generalizes [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]]'s perceptual-only hierarchical predictive coder to embodied agents. The Rao-Ballard precision-weighting `(1/σ², 1/σ²_td)` is the same precision concept that Friston later reads as attentional gain.
- **MaxEnt foundation.** FEP inherits its variational form from [[jaynes-1957-maxent-statistical-mechanics|Jaynes (1957)]]'s MaxEnt inference framework; Friston's `F` is the Lagrangian whose stationary points are MaxEnt posteriors over hidden causes.
- **Critics / alternatives.** [[li-2024-prediction-noise-reward|Li et al. (2024) PaN]] is positioned explicitly against active inference, getting closed-loop reward-seeking behavior from local prediction + noise without priors or modular planners. [[computation-through-dynamics|Computation Through Dynamics]] avoids the generative-model commitment FEP requires.

## Sources in this wiki

- [[friston-2010-free-energy-principle|Friston (2010)]] — "The free-energy principle: a unified brain theory?" *Nature Reviews Neuroscience.* The canonical review unifying nine "global" brain theories under FEP.
