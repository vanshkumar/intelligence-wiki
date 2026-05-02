---
title: "Splitter Cells"
type: concept
aliases: ["route-dependent place cells", "trajectory-encoding place cells", "event-specific representations", "ESR", "lap cells", "chunking cells"]
tags: [hippocampus, place-cells, route-encoding, hippocampal-coding]
source_count: 1
last_updated: 2026-05-01
confidence: established
---

Splitter cells are hippocampal place cells whose firing on a shared physical segment of an environment **depends on the route the animal is taking** — past trajectory, future destination, or lap number — rather than on instantaneous sensory cues alone. They are the cleanest empirical case for the claim that the hippocampus represents *contextualized* spatial states, not just locations.

## Discovery and core finding

Wood, Dudchenko, Robitsek & Eichenbaum (2000) ran rats through a continuous T-maze in which left- and right-turn trials shared a long central stem. About two-thirds of CA1 place cells fired differentially on the stem depending on whether the rat had just come from a left- or right-turn trial — even though the sensory inputs and motor behavior on the stem were identical. The phenomenon has since been documented across mazes, species, and decades:

- Frank, Brown & Wilson (2000) — trajectory encoding in CA1 and entorhinal cortex
- Sun, Yang, Martin, Tonegawa (2019) — event-specific representations (ESR): distinct neural codes for repeated traversals of the same route on different laps; "chunking cells" that fire selectively on specific laps
- Ginther, Walsh & Ramus (2011) — overlapping odor sequences with route-specific responses
- Grieves, Wood & Dudchenko (2016) — place cells encode routes toward goals rather than physical locations

## Why they matter

Splitter cells dissociate **observed sensory state** from **inferred latent state**. On a shared stem, two trials produce identical sensory input but different population activity — so the population is representing something not present in the immediate input. This rules out theories on which place cells purely encode current sensory or proprioceptive state and forces theories that include past context, future intent, or both.

For the wiki's [[control-thesis-ledger|control thesis]], splitter cells are evidence that the hippocampal substrate represents *trajectories*, not just *positions* — which fits the framing of memory and learning as extending control over time. The substrate reaches forward and backward beyond the present moment.

## Mechanistic accounts

- **[[Clone-Structured Cognitive Graph|CSCG]]** ([[george-2021-clone-structured-cognitive-graphs|George et al. 2021]]) — splitter cells are different clones of the same observation. EM training on (sensation, action) streams allocates separate clones for the shared segment depending on the route. ESR and lap-cells fall out of the same mechanism. This is currently the most explicit unified algorithmic account of the splitter-cell zoo.
- **[[Successor Representation]]** (Stachenfeld et al. 2017) — predicts asymmetric place fields along common travel directions; partial account of splitter-like effects but doesn't naturally produce route-specific codes for fully aliased segments.
- **Path integration + context gating** — older proposals attribute splitter behavior to interaction between path-integration signals and contextual gating; biologically plausible but lacks a unified algorithmic story.
- **TEM** (Whittington et al. 2020) — also lifts observations into hidden structural states, predicting splitter-like phenomena; not yet ingested in this wiki.

## Relation to other place-cell phenomena

Splitter cells, **event-specific representations** (lap-specific firing for the same observation on a looping track), **chunking cells** (firing on specific lap ranges), and **prospective / retrospective coding** (firing predictive of future or past behavior on a shared segment) are increasingly read as a single phenomenon: hippocampal cells represent *latent contextual states* whose mapping to sensory observations is many-to-one.

In [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]]'s framing, this is just the cloning structure: one observation → many hidden states, with EM allocating clones to whatever contextual distinctions are needed to predict next observations.

## Sources

- [[george-2021-clone-structured-cognitive-graphs|George et al. (2021)]] — splitter cells, ESRs, and lap cells emerge from the same CSCG mechanism (cloning + EM)
