---
title: "Credit Assignment Lineage: From Two-Site Integration to In Vivo Vectorized Signals"
type: theory
aliases: ["dendritic credit assignment lineage", "burst credit assignment lineage"]
tags: [credit-assignment, dendritic-computation, learning-rule, plasticity]
source_count: 6
last_updated: 2026-05-01
status: emerging
---

The 25-year arc from a structural conjecture about pyramidal-neuron compartments to direct in vivo measurement of cell-specific dendritic teaching signals. Six papers, each closing a gap left by the previous: rate concept → spiking implementation → phase elimination → biophysical maturity → depth scaling → empirical confirmation.

The lineage is the wiki's clearest example of a coherent mechanistic program. It is not the wiki's clearest example of *thesis-relevant* research — the connection to closed-loop control is uneven across the six papers and is in some places retrofit. See *Bearing on the control thesis* below for an honest reckoning.

## The motivating problem

Backpropagation requires non-local information at each synapse: the post-synaptic activity must be combined with a downstream error signal computed from much later layers. Real synapses see only their own pre- and post-synaptic activity. The credit-assignment problem is: how could biological neurons approximate backprop using only local signals?

The lineage's shared answer: **two compartments per pyramidal neuron — basal (feedforward) and apical (feedback) — provide two locally accessible variables, and a non-linear interaction (bursts, plateau potentials, Ca²⁺ spikes) lets one compartment carry an error-like signal without contaminating the other**.

## The six-paper arc

### 1. Kording & König (2001) — the conceptual seed

[[kording-konig-2001-two-integration-sites|Kording & König (2001)]] argued formally that two integration sites give pyramidal neurons two independent variables per neuron, separating feedforward activity from a learning signal. They proposed that **bursts** carry the second variable and that **short-term plasticity (STP)** can multiplex burst vs. tonic spike codes on the same axon (facilitating synapses follow bursts; depressing synapses follow tonic spikes). Demonstrated XOR learning under burst-gated plasticity ΔW_basal ∝ D_post · A_pre.

The structural insight is the foundation. Almost every later paper inherits the apical/basal split.

### 2. Guerguiev, Lillicrap & Richards (2017) — first spiking implementation

[[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] gave the first spiking realization. Two-phase operation (forward phase, then plateau phase) separated feedforward from feedback. Plateau potentials encoded the local target via temporal averaging; the difference α^t − α^f served as a teaching signal. Crucially, **feedback alignment emerged during training** — the network learns to route credit, weight transport not required. MNIST: 3.28%.

Phase requirement is the lineage's first awkwardness. Real cortex does not obviously segregate forward and feedback phases in time.

### 3. Sacramento, Costa, Bengio & Senn (2018) — phase elimination via prediction error

[[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] removed phases. SST interneurons continuously predict and cancel top-down feedback; the **self-predicting state** is the network's homeostatic equilibrium. When predictions fail, apical voltage deflection equals the prediction error and approximates the backprop gradient analytically (in the weak-feedback limit). Three connection types, three local plasticity rules. MNIST: 1.96%. The paper unifies [[predictive-coding|predictive coding]] (errors are deviations from a self-predicted equilibrium) with [[credit-assignment|credit assignment]] (those deviations *are* the gradient).

### 4. Payeur, Guerguiev, Zenke, Richards & Naud (2020) — biophysical maturity

[[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] implemented the rule with explicit voltage-gated Ca²⁺ channels, dendritic Ca²⁺ spikes, and SST⁺ linearization of the apical–burst relationship. Plasticity rule: dw/dt ∝ (B_i − P̄_i) · E_i · Ẽ_j (burst probability deviation from an adaptive threshold). STP type-specificity carries the signals separately: feedforward STD transmits event rate; feedback STF transmits burst rate. Scaled to CIFAR-10 (20.1% error) and ImageNet (56.1% top-5). Three falsifiable predictions: STP polarization by pathway, correlation of burst variance with learning rate, disruption by apical inhibition.

### 5. Greedy, Zhu, Pemberton, Mellor & Costa (2022) — single-phase, depth-scalable

[[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] resolved the two remaining issues — Sacramento's depth ceiling (~2–3 layers) and any residual phase-dependence — with the **Q–Y cancellation mechanism**. A homeostatic Q pathway (STD feedback) learns to cancel the baseline burst activity carried by the Y pathway. In the symmetric Q–Y state, baseline is silent and any deviation is pure error. Single phase, 9-layer depth, MNIST 1.84%, CIFAR-10 22.92%. Backprop approximation: δb_l ≈ f'(v_l) ⊙ (−Y_l) δb_{l+1}.

### 6. Francioni et al. (2026) — first in vivo evidence

[[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] measured cell-specific teaching signals in L5 apical dendrites during BCI learning. The **SD residual** (dendritic activity not predicted by surrounding somatic activity) tracks reward, error magnitude, and crucially, **error direction**: P+ neurons (those whose increased activity reduces error) show positive residuals; P− neurons show negative residuals. NDNF⁺ layer 1 interneuron perturbation abolishes the residuals and impairs learning. The soma–dendrite relationship is linear (lowest AIC), consistent with SST⁺ linearization. Twenty-five years after Kording's structural conjecture, the cell-specific dendritic teaching signal is observable.

## What the lineage establishes

- Pyramidal compartmentalization plus burst-multiplexed STP plus targeted inhibition is **sufficient** to approximate backpropagation in spiking networks at competitive accuracy and depth.
- The basic architecture (apical = feedback / error, basal = feedforward / activity) is **empirically supported in vivo** for at least one task (BCI motor learning) and one cell type (L5 cortical pyramidal).
- The mechanism unifies [[predictive-coding|predictive coding]] and [[credit-assignment|credit assignment]]: the same apical signal that represents prediction error also drives the local plasticity rule.
- A homeostatic baseline (self-predicting state in Sacramento; Q–Y cancellation in Greedy; NDNF⁺-mediated baseline in Francioni) is the dynamical equilibrium from which deviations drive learning. This is the strongest control-flavored claim the lineage supports.

## Honest tensions within the lineage

1. **Error magnitude vs. error derivative.** Sacramento, Payeur, and Greedy assume errors / gradients. Francioni finds SD residuals correlate with error *derivatives*, not error magnitudes. This favors target propagation over pure backprop and is not a small detail — it changes which of the theoretical models maps cleanly onto cortex.

2. **Which interneuron type carries the cancellation.** Sacramento and Payeur emphasize SST⁺ Martinotti cells. Francioni's perturbation evidence implicates NDNF⁺ layer-1 interneurons. The roles may be complementary (NDNF⁺ gates distal apical input; SST⁺ linearizes mid-apical), but no current model integrates both cleanly.

3. **Convergence to silent baseline.** Sacramento's self-predicting state is silent at equilibrium. Greedy's Q–Y mechanism produces partial cancellation. Francioni observes that P+ and P− neurons do *not* reach silence even after 14 days of training. The Greedy/partial-cancellation model fits the in vivo data better than Sacramento's full-silence model.

4. **Depth scaling.** Sacramento's continuous-voltage approach degrades past 2–3 layers; Payeur's and Greedy's discrete-burst approaches scale to 9. Whether this reflects a fundamental advantage of burst encoding for deep credit assignment, or an artifact of the weak-feedback approximation, is unresolved.

5. **Error-carrier consensus is illusory.** Each paper's "error signal" is operationally defined differently: burst rate, plateau potential difference, apical voltage, burst-probability deviation, post-Q residual. These are not the same biological variable. They might compress to a single underlying quantity, or they might be different read-outs of distinct apical computations. This matters because in vivo measurement (Francioni) sees the dendritic Ca²⁺ signal, not any of the model-specific abstractions.

## Bearing on the control thesis

Mixed, and worth being honest about. The lineage's architectural commitments (compartments, bursts, STP, inhibitory linearization) do not require a closed-loop framing — they're motivated by approximating gradient descent, not by servo control. Two of the six papers (Sacramento, Greedy) frame their homeostatic baseline in explicitly control-flavored language; the other four do not. The wiki has at times read the homeostatic equilibrium as the substrate-level signature of control, but this is the wiki's reading, not a direct claim of the underlying papers.

What the lineage *does* support, modestly: credit assignment in cortex is **local to the substrate** (dendritic, burst-mediated, neuromodulator-gated), which is consistent with — but does not entail — a closed-loop view in which learning operates within the same dynamical loop that produces behavior. See ledger pillar P5 for the full bookkeeping.

## Key gaps after Francioni 2026

- **Temporal credit assignment.** The lineage addresses spatial (cross-layer) credit. Delayed rewards and temporally extended sequences are unaddressed.
- **Neuromodulation.** A global gating signal M(t) is abstracted across the lineage; how dopamine / acetylcholine / noradrenaline interact with local burst-dependent rules is not specified.
- **Feedback weight learning.** The strong CIFAR-10 and ImageNet results require *learned* feedback weights (Y), not random aligned ones. The biological mechanism for learning Y is not fully worked out.
- **NDNF⁺ vs. SST⁺ division of labor.** Open empirical question, raised sharply by Francioni.
- **Unsupervised / self-supervised variants.** Only Kording explored mutual-information-style self-supervision. Whether modern spiking models support unsupervised learning is open.

## Sources

- [[kording-konig-2001-two-integration-sites|Kording & König (2001)]]
- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]]
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]]
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]]
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]]
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]]

## Related

- [[Credit Assignment]] — the broader concept page
- [[Dendritic Computation]] — the substrate
- [[Inhibitory Circuits]] — SST⁺, NDNF⁺ roles
- [[Predictive Coding]] — unification with credit assignment
- [[control-thesis-ledger|Control thesis ledger]] (pillar P5) — bearing
