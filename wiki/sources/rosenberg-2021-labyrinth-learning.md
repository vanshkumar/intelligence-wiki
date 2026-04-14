---
title: "Mice in a Labyrinth Show Rapid Learning, Sudden Insight, and Efficient Exploration"
type: source
source_type: paper
authors:
  - "Matthew Rosenberg"
  - "Tony Zhang"
  - "Pietro Perona"
  - "Markus Meister"
year: 2021
doi: "10.7554/eLife.66175"
tags: [learning-rate, exploration, sudden-insight, ethology, navigation, one-shot-learning]
date_ingested: 2026-04-13
key_finding: "Mice freely exploring a complex labyrinth overnight exhibit few-shot reward learning (~10 trials), one-shot home-path learning, sudden insight transitions, and efficient exploration governed largely by 4 local turning biases that are strikingly consistent across animals."
---

## Overview

Rosenberg, Zhang, Perona & Meister (2021) report what happens when mice are placed into a 6-level binary-tree labyrinth (64 end-nodes, ~1.5 m on a side) overnight, with no human interference, no training protocol, and no hand-scoring. Automated tracking yields ~10⁴ decisions per animal per night. The paper's central argument, paralleling [[meister-2022-learning-fast-slow|Meister (2022)]], is that laboratory 2AFC paradigms systematically under-report what rodents can actually do — when allowed to behave naturally in a complex environment, mice learn far more, far faster, and with behavioral dynamics (sudden insight, one-shot escape learning, intrinsic exploration) that trial-based tasks obscure entirely.

[PDF](../../raw/papers/rosenberg-2021.pdf)

## Key Findings

**1. Few-shot reward learning.** Water-deprived mice discover a single rewarded end-node and converge on reliable navigation to it after ~10 reward experiences (the learning curve from random-walk baseline to asymptotic direct paths decays with time constant 10.1 rewards). This is orders of magnitude faster than visual/tactile 2AFC tasks.

**2. Sudden insight.** Behavioral change is discontinuous: long direct reward-paths appear abruptly in single animals' trajectories, rather than emerging via gradual smoothing of a curve. The population-averaged learning curve is smooth, but individual animals show step-like transitions — an observation that is incompatible with a purely gradient-based narrative of reward learning.

**3. One-shot home-path learning.** After a single traversal of any maze path, mice can return to the entry point from arbitrary novel locations. Escape paths are essentially direct (few errors) on the first attempt. This is a concrete instance of one-shot learning in spatial navigation.

**4. Navigation is map-based, not odor-based.** Rotating the maze between sessions does not disrupt navigation performance, ruling out local chemosensory cues and implicating an internal spatial representation.

**5. Efficient exploration from 4 local rules.** Exploration efficiency (end-nodes visited vs. decisions taken) is ~2× that of a random walk. A Markov model with just **four local turning biases** — P_SF (streak-forward), P_SA (streak-away-from-center), P_BF (bounce-forward), P_BS (bounce-streak) — captures roughly 60% of the efficiency gain over random walks. The biases are:
   - *Streak/switch bias*: a tendency to alternate left/right turns (streak) rather than repeat
   - *Forward bias at T-junctions*: preference to continue rather than reverse
   - *Outward bias*: preference for nodes away from the maze center
   - A systematic preference for outer end-nodes emerges directly from these local rules

**6. Biases are consistent across animals.** Across 19 mice, the four bias parameters have standard deviations of ~0.03 — remarkably tight. This cross-animal consistency strongly suggests a genetic/developmental substrate for the local decision rules that produce efficient exploration, rather than learning-by-experience.

**7. Exploration is the dominant behavioral mode.** Even in water-rewarded mice, after learning, ~75–95% of time is spent exploring (not drinking, not leaving). In *unrewarded* mice, exploration persists at similar rates throughout the session. Exploration is not instrumental to reward; it is the default behavioral state.

**8. Information-theoretic analysis of decisions.** The prior entropy of a random walk at a T-junction is 1.585 bits (3 outcomes); mice reduce this to 1.237 bits using local context (prior turn direction). This is a modest per-decision reduction but compounds across ~2000 decisions/hour.

**9. Decision rate ~1000× higher than 2AFC.** Mice make ~2000 decisions per hour in the labyrinth vs. ~100 per hour in typical 2AFC setups. The *information per decision* may be similar, but the raw throughput of a naturalistic task makes the learning machinery visible at timescales that trial-based paradigms cannot resolve.

## Methods

- **Apparatus**: 6-level symmetric binary-tree maze, opaque walls, single entry connecting to home cage. 64 end-nodes. Overnight unsupervised sessions.
- **Tracking**: automated video + pose estimation; every decision at every junction recorded.
- **Conditions**: unrewarded exploration, water-rewarded (single fixed end-node), maze rotation controls.
- **Analysis**: information-theoretic decomposition of decisions; Markov models of increasing order; 4-parameter local-bias model fit to exploration trajectories.

## Implications

**For the organizing principle of this wiki.** The paper is a direct empirical instantiation of the control-first view:

- **Genes→control→structure**: cross-animal consistency of turning biases (SD ~0.03) is exactly what a control-theoretic reading of [[Degeneracy]] predicts at the behavioral level. Genes constrain local decision rules at each T-junction; efficient global exploration emerges as a high-probability consequence, without any global map or inherited circuit specifying "visit all 64 nodes." This extends [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt (2019)]]'s degeneracy observation from *C. elegans* dynamics to mammalian behavior: consistent macroscopic structure, presumably variable microscopic implementation.

- **Sensorimotor loop first**: exploration is dominant even without reward. The closed sensorimotor loop (sense → decide → move → update) is the organism's default operation; reward biases it but is not required to initiate it. This supports the framing in [[self-supervised-behavior|self-supervised behavior]] — goals emerge from the dynamics of the loop, not from an externally supplied utility function.

**For the learning-rate debate.** Directly extends [[meister-2022-learning-fast-slow|Meister (2022)]]'s critique of 2AFC: when the task falls within the animal's natural repertoire (navigate a maze, find water, return home), learning is fast and rich. The 10,000× range Meister identified is here made concrete — the same species, same lab, same time period, different paradigm, 1000× different decision rate.

**For models of exploration.** Efficient exploration does not require a global map, reward signal, or explicit information-gain calculation. Four local biases suffice for ~60% of the efficiency — suggesting that many lab "exploration strategies" modeled via softmax/ε-greedy/UCB are over-engineered relative to what real animals do.

**For sudden insight.** Discontinuous behavioral transitions challenge pure gradient-descent models of reward learning. The mechanism is not addressed in this paper, but the empirical signature is clean.

## Connections to Existing Knowledge

- **[[meister-2022-learning-fast-slow|Meister (2022)]]**: same lab; Rosenberg is the empirical paper, Meister 2022 is the review. The labyrinth is the concrete "upper-left of Figure 1" task.
- **[[Degeneracy]]**: cross-animal consistency of turning biases is behavioral-level evidence for the genes→control→structure hypothesis that explains microscopic variability with macroscopic conservation.
- **[[self-supervised-behavior|Self-Supervised Behavior]]**: dominant exploration without reward matches the SSB claim that goal-directed behavior emerges from loop dynamics rather than from external objectives. Rosenberg provides the strongest ethological support for this claim to date.
- **[[Explore-Exploit Tradeoff]]**: the Rosenberg data suggest exploration is not a fraction of behavior traded off against exploitation, but the default mode that exploitation episodically interrupts.
- **[[li-2024-prediction-noise-reward|Li et al. (2024)]] (PaN)**: PaN's attractor-based explore/exploit switching is a candidate mechanism for the bimodal behavioral states Rosenberg observes (explore / drink / leave).
- **[[zhang-2024-endotaxis-neuromorphic-navigation|Zhang et al. (2024)]]**: the mechanistic companion paper from the same lab. Endotaxis is the circuit-level proposal that quantitatively accounts for all three Rosenberg behaviors (one-shot homing, few-shot reward learning, efficient patrolling) with a single Hebbian circuit.
- **Weber et al. (2013)** (cited in Rosenberg, not yet ingested): genetic basis of burrow-structure differences in *Peromyscus* mice — a precedent for the genes-encode-behavioral-structure claim that would complement the labyrinth findings.

## Open Questions Raised

- What is the neural substrate of the four local turning biases? Are they implemented in a dedicated navigation circuit (e.g., entorhinal–hippocampal), or in a more general action-selection structure?
- Sudden insight: what is the transition mechanism? Is this a phase transition in an attractor landscape, consolidation-driven representational switching, or something else?
- Is one-shot home-path learning a consequence of [[Hippocampus|hippocampal]] [[Place Cells|place-cell]] formation during the inbound traversal, or does it rely on path integration machinery? Rotation-robust navigation suggests the former.
- Can the cross-animal bias consistency (SD ~0.03) be traced to specific genes or developmental parameters? What is the control-theoretic mapping from gene expression to these four bias parameters?
- Do inbred vs. outbred mouse strains differ in the bias parameters? Outbred strains would test the genetic-constraint hypothesis directly.
- Does the dominance of exploration (even in unrewarded animals) have a neuromodulatory signature? Locus coeruleus / norepinephrine tone is a candidate.
