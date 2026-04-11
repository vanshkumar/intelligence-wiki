---
title: "State-Dependent Spike Timing Relationships Between Hippocampal and Prefrontal Circuits During Sleep"
type: source
source_type: paper
authors:
  - "Casimir M. Wierzynski"
  - "Evgueniy V. Lubenov"
  - "Ming Gu"
  - "Athanassios G. Siapas"
year: 2009
doi: "10.1016/j.neuron.2009.01.011"
tags: [sleep, hippocampus, prefrontal-cortex, memory-consolidation, sharp-wave-ripples, SWS, REM, spike-timing, plasticity]
date_ingested: 2026-04-11
key_finding: "During slow-wave sleep, prefrontal cortex cells fire consistently within 0-100 ms after hippocampal CA1 cells, driven by sharp-wave/ripple events. These interactions are nearly abolished during REM sleep, suggesting SWR events are an atomic unit of hippocampal-prefrontal communication for memory consolidation."
---

## Overview

This paper establishes that hippocampal and prefrontal circuits interact with precise, directional spike timing during sleep — but only during slow-wave sleep (SWS), not REM. Using chronic multi-tetrode recordings from CA1 and mPFC in freely sleeping rats, the authors show that individual prefrontal cells fire consistently 0-100 ms after hippocampal cells, with the timing driven by hippocampal sharp-wave/ripple (SWR) events. This timing falls within the window for spike-timing-dependent plasticity, providing single-cell-pair evidence for a mechanism of hippocampus-to-cortex memory transfer during sleep. The near-complete abolition of these correlations during REM sleep suggests fundamentally different hippocampal-cortical interactions across sleep stages.

[PDF](../../raw/papers/wierzynski-2009.pdf)

## Key Findings

### Directional Spike Timing: Hippocampus Leads Prefrontal Cortex

Cross-covariance analysis of all simultaneously recorded mPFC-CA1 cell pairs (2779 total, from 219 CA1 and 76 mPFC cells) during SWS revealed:

- **11% of pairs** (304/2779) showed significant correlations during SWS (false discovery rate 1%)
- **70% directional bias**: prefrontal cells tended to fire *after* hippocampal cells (p < 10⁻¹¹)
- **Average lag of 36 ms** (s.e. = 12 ms), with peak lags concentrated in the 0-100 ms range (39% of pairs, p < 10⁻²¹)
- Interactions were **distributed** across cells in both regions — not driven by a small number of highly interacting neurons. Median interaction rates: 10% for hippocampal cells, 7% for prefrontal cells.

The 0-100 ms timing is significant because it falls within the window for [[Long-Term Potentiation|spike-timing-dependent plasticity]] — the pre→post ordering (hippocampus before PFC) would favor LTP at hippocampal-to-prefrontal [[Synapses|synapses]]. Combined with known monosynaptic excitatory projections from CA1 to mPFC, this satisfies two major requirements for activity-dependent plasticity: synaptic contact and consistent spike timing.

### Sharp-Wave/Ripple Events Drive the Interactions

The hippocampal-prefrontal timing correlations during SWS are driven by SWR events:

- Restricting analysis to spikes within ±250 ms of SWR centers: 141/304 significantly correlated pairs retained significance
- Only 32/304 showed significant correlations when SWR-driven spikes were *excluded*
- 78% of correlated pairs (with 0-100 ms peak lags) were also correlated during SWR-restricted analysis, vs only 14% when SWR events were excluded

SWR events thus serve as an **atomic unit** of hippocampal-prefrontal communication during SWS — the directional spike timing relationships are organized around these discrete population events.

### Near-Complete Abolition During REM Sleep

The most striking result: hippocampal-prefrontal timing correlations that are robust during SWS are **nearly abolished during REM sleep**.

- Only **3 of 304** SWS-correlated cell pairs also showed significant correlations in REM
- Only **19 of 2779** total pairs showed any significant correlation during REM
- This was not due to differences in firing rates (similar between SWS and REM) or recording duration artifacts (verified by subsampling SWS to match REM duration)
- The number of prefrontal spikes within 0-100 ms of a CA1 spike was significantly higher in SWS compared to REM (p < 10⁻¹⁵)

The two brain areas effectively **decouple** during REM. This dissociation is a major constraint on theories of memory consolidation during sleep.

### Biphasic Prefrontal Response to Hippocampal Bursts

The prefrontal response to hippocampal activity is nonlinear and depends on burst strength:

- **Weak hippocampal bursts** → single-peaked, short-latency (~10 ms) prefrontal response from a few strongly correlated cell pairs
- **Strong hippocampal bursts** → biphasic response: short-latency peak + secondary peak at ~100 ms, with increased spindle-band (7-15 Hz) activity in prefrontal LFPs

The secondary 100 ms peak is not simply a delayed version of the first — it emerges from spindle-band activity within cortical or cortico-thalamic circuits, triggered by the hippocampal drive. The aggregate cross-covariance of all 2779 pairs (not just the 304 significant ones) shows the 100 ms peak clearly, indicating it arises from many individually weak but collectively coherent interactions.

This biphasic structure means SWR events don't just transfer a single spike pattern — stronger bursts recruit additional cortical processing through spindle-mediated mechanisms.

## Methods

- **Subjects**: 3 male Long-Evans rats (350-450g)
- **Recording**: Chronic multi-tetrode recordings — 12 tetrodes targeting dorsal CA1, 12 targeting prelimbic/infralimbic mPFC. Simultaneous recording during extended natural sleep sessions (mean 222 ± 19 min per session)
- **Sleep staging**: SWS vs REM classified by muscle tone, theta/delta power ratio, and theta power
- **Analysis**: Cross-covariance computed as standardized raw spike counts in 10 ms bins. False discovery rate controlled at q = 0.01 across all pairs. SWR events identified by ripple band (80-250 Hz) power threshold.
- **Context**: All recordings performed after spatial tasks (linear track, T-maze), so hippocampal-prefrontal interactions reflect post-learning consolidation

## Implications

### For memory consolidation

This paper provides single-cell-pair evidence for the predominant model of systems consolidation: hippocampal memories are gradually transferred to neocortex through repeated reactivation during SWS. The directional timing (hippocampus → PFC, within the plasticity window), the SWR-driven organization, and the state dependence (SWS only) all support this model.

The SWS/REM dissociation suggests a **two-stage model**: SWS handles hippocampus-to-cortex transfer (directional, SWR-driven, plasticity-compatible timing), while REM may serve internal cortical reorganization without hippocampal-cortical coupling. The authors note this may explain why dreams (associated with REM) are largely forgotten — [[Prefrontal Cortex|PFC]] is not receiving structured hippocampal input during REM.

### For the hippocampal-prefrontal pathway

Combined with [[reinert-2021-pfc-categorization|Reinert et al. (2021)]], which shows gradual emergence of category representations in mPFC during learning, this paper suggests a mechanism: hippocampal SWR-driven spike timing during sleep could progressively build and refine PFC representations through repeated, plasticity-compatible reactivation. The gradual timescale of representation building in PFC (weeks) is consistent with consolidation requiring many sleep cycles.

## Connections to Existing Knowledge

- **[[Hippocampus]]**: SWR events as the vehicle for hippocampal output during sleep; hippocampus leads the interaction directionally
- **[[Prefrontal Cortex]]**: PFC as the recipient of hippocampal memory transfer during SWS; biphasic response structure suggests complex cortical processing of hippocampal input
- **[[Long-Term Potentiation]]**: The 0-100 ms hippocampus→PFC timing falls within the STDP window for LTP at hippocampal-to-prefrontal synapses
- **[[Theta Oscillations]]**: Complements [[lubenov-2009-theta-travelling-waves|Lubenov & Siapas (2009)]] — theta structures hippocampal activity during waking behavior, SWR structures it during sleep. Same circuit, different oscillatory modes for different computational needs
- **[[Athanassios Siapas]]**: From the same lab; extends the Siapas group's work from waking oscillatory dynamics to sleep consolidation mechanisms

## Open Questions Raised

- Does the SWR-driven hippocampal-prefrontal spike timing actually induce synaptic plasticity in PFC? The timing is compatible with STDP, but causal evidence is lacking.
- What information content do the SWR-driven hippocampal-prefrontal interactions carry? Are they replaying specific spatial trajectories or task-relevant sequences?
- What is the functional role of the biphasic (10 ms + 100 ms) prefrontal response? Does the spindle-mediated second peak serve a different computational purpose than the direct first peak?
- Are the 3/304 pairs that show REM correlations functionally special? Could they represent a rare but important REM-specific consolidation mechanism?
- Does the hippocampal-prefrontal coupling during SWS change across learning — do more pairs become correlated as the animal learns more about its environment?

## Sources

Wierzynski et al. (2009). *Neuron*, 61(4), 587–596.
