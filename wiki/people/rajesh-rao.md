---
title: "Rajesh Rao"
type: person
tags: [computational-neuroscience, predictive-coding, brain-computer-interfaces, machine-learning, vision]
affiliation: "University of Washington (Hwang Endowed Professor); Co-Director, Center for Neurotechnology"
source_count: 1
last_updated: 2026-04-27
---

Rajesh P. N. Rao is an Indian-American computational neuroscientist whose 1999 paper with [[dana-ballard|Dana Ballard]] ([[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]) established hierarchical [[predictive-coding|predictive coding]] as a leading theory of cortical computation. The paper proposed that cortico-cortical feedback connections carry top-down predictions of lower-level neural activity while feedforward connections carry the residual prediction errors — a structural hypothesis that gives a unified account of [[predictive-coding|predictive coding]] for the visual cortex and re-interprets the suite of "extra-classical" receptive-field effects (endstopping, surround suppression, orientation contrast, pop-out, contextual modulation) as the signature of error-detecting neurons in a network optimized for natural-image statistics.

Rao trained at the University of Rochester with [[dana-ballard|Dana Ballard]] (PhD, computer science, 1998) and was a Sloan Postdoctoral Fellow at the Salk Institute. He joined the University of Washington in 2000, where he co-directs the Center for Neurotechnology. His research has spanned three connected threads:

- **Predictive coding and Bayesian theories of cortex.** Beginning with the 1997 *Neural Computation* paper "Dynamic model of visual recognition predicts neural response properties in the visual cortex" (Rao & Ballard 1997, the Kalman-filter precursor to the 1999 paper) and continuing through later work on hierarchical Bayesian inference, attention, and active vision.
- **Brain-computer interfaces.** Rao's lab pioneered non-invasive BCIs based on EEG and ECoG, including direct brain-to-brain communication between humans (Stocco-Prat-Rao 2014) — early demonstrations of multi-brain coupling that have since matured into clinical trials.
- **Computational neuroscience textbooks and synthesis.** *Probabilistic Models of the Brain* (Rao, Olshausen & Lewicki, 2002) and *Bayesian Brain* (Doya, Ishii, Pouget & Rao, 2007) are major edited volumes in the Bayesian-brain lineage; *Brain-Computer Interfacing: An Introduction* (2013) is a textbook in the BCI area.

## Why he matters for this wiki

Rao's 1999 paper is one of the foundational sources for the [[predictive-coding|predictive coding]] framework that runs through much of the wiki. The Rao-Ballard architecture — feedback as predictions, feedforward as residuals, local Hebbian prediction-error learning — is the cortical instantiation of the [[helmholtz-machine|Helmholtz-machine]] variational-inference framework ([[dayan-hinton-1994-helmholtz-machine|Dayan-Hinton 1994]]) and the operational core of [[active-inference|Friston's free-energy principle]] in its original, perceptual form. It is also the conceptual ancestor of:

- The dendritic [[credit-assignment|credit-assignment]] lineage's prediction-error-as-credit-signal interpretation ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. 2018]]; [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. 2020]]).
- The [[li-2024-prediction-noise-reward|Li et al. (2024) PaN]] framework's extension of predictive coding from perception to closed-loop behavior.
- Modern proposals that cortical computation is fundamentally hierarchical-predictive (Keller-Mrsic-Flogel 2018; Bastos et al. 2012, "canonical microcircuits for predictive coding").

Under the wiki's [[overview|control-theoretic]] organizing principle, Rao's contribution is the perceptual half of the closed sensorimotor loop: the hierarchical generative model that allows the organism to act on inferred causes rather than raw sensation. Memory, attention, and learning extend the reach of this perceptual-control machinery over longer timescales and more abstract latent variables.

## Relevant Work in This Wiki

- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]] — "Predictive coding in the visual cortex: a functional interpretation of some extra-classical receptive-field effects." *Nature Neuroscience* **2**(1), 79–87. The founding paper of hierarchical predictive coding for cortex.

## Sources

- [[rao-ballard-1999-predictive-coding|Rao & Ballard (1999)]]
