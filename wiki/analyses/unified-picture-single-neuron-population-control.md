---
title: "Is there a unified picture of single-neuron biophysics and population dynamics for closed-loop sensorimotor control?"
type: exploration
tags: [dendritic-computation, population-dynamics, motor-control, ctd, credit-assignment, manifolds, control-thesis]
date_created: 2026-04-21
prompted_by: "user query"
---

## The question

Is there a unified picture of what individual neurons do (e.g. [[Dendritic Computation|dendritic computation]], and more generally biophysics) *and* what populations do, specifically for closed-loop sensorimotor control — the production of movement?

## Short answer

A **partial** unified picture. Two well-developed threads converge at a few specific junctions but have not fully merged. The load-bearing bridge — how single-neuron dendritic events sculpt the low-dimensional dynamics motor cortex uses — is mostly conjectural, with [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] as the first experimental toehold.

## The two threads

### Thread 1 — population level (sensorimotor control)

[[Computation Through Dynamics|CTD]] is the formal language. A neural population's state `x(t) ∈ ℝ^N` evolves according to `dx/dt = f(x, u)`, and the closed loop in [[Motor Cortex]] maps onto canonical motifs ([[vyas-2020-computation-through-dynamics|Vyas et al. 2020]]):

- **Prepare** — [[Preparatory Activity|delay-period activity]] in PMd sets the initial condition.
- **Hide from actuator** — [[Null Space Coding|output-null coding]]: preparation lives in the null space of the muscle readout.
- **Move** — [[Rotational Dynamics|rotational pattern generation]] in M1: a low-dimensional oscillator *generates* (not represents) multiphasic muscle activity.
- **Transition** — a condition-invariant signal (CIS) shifts the population from preparation to movement-generation regions of state space.
- **Maintain context / update** — SMA low-divergence trajectories; adaptation operates on preparatory dimensions.

The intrinsic [[Neural Manifolds|manifold]] on which these dynamics live is the **control-theoretic repertoire** that connectivity and cellular biophysics make accessible.

### Thread 2 — single-neuron level (biophysics)

Pyramidal neurons in cortex are not point integrators. They carry **two independent variables per cell** via basal/apical compartmentalization ([[kording-konig-2001-two-integration-sites|Kording & Konig 2001]]):

- **Basal dendrites** receive feedforward input.
- **Apical dendrites** receive top-down feedback; VGCCs there produce regenerative calcium spikes, and calcium spikes drive somatic bursts.
- **Bursts gate plasticity sign** — burst → LTP, isolated spike → LTD ([[payeur-2020-burst-dependent-credit-assignment|Payeur et al. 2020]]) — so top-down feedback steers [[Credit Assignment]] in lower areas.
- **SST+ / NDNF+ interneurons** linearize and predict the feedback, so the apical dendrite computes a *prediction error* ([[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. 2018]], [[francioni-2026-vectorized-dendritic-signals|Francioni et al. 2026]]).

Separately, [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] show the dendritic tree itself is a multi-layer network, and LTP grows multi-synaptic boutons 6×, so the single neuron's computational capacity is both nontrivial and *learning-reshapeable* — learning modifies the cell's internal architecture, not just its weights.

## Where the threads meet

### 1. Manifold-constrained learning as the cleanest junction

The Sadtler/Golub/Oby BCI experiments in monkey motor cortex are the strongest empirical bridge:

- **Sadtler 2014**: within-manifold BCI perturbations are learned in hours; off-manifold perturbations take days or fail.
- **Golub 2018**: within-manifold learning proceeds by **neural reassociation** — re-using existing dynamical states in new pairings.
- **Oby 2019**: multi-day training eventually accesses off-manifold states, revealing multiple learning mechanisms at different timescales.

Interpretation: the manifold is shaped by biophysics and connectivity; fast learning operates inside it without changing synaptic weights much; slow structural change reshapes it. [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] is the first in vivo evidence that cell-specific dendritic SD residuals carry the learning signal *during a BCI task* — directly tying apical-dendrite credit assignment to motor-cortex manifold learning. NDNF+ L1 interneuron activation abolishes both the vectorized dendritic signal and the learning.

### 2. Mesoscopic → microscopic via E-I parameters

[[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] Theorem 4: any E-I population capable of a [[Limit Cycle|limit cycle]] under some bias must also exhibit [[Hysteresis|hysteresis]] under some other bias. One genetically-specified substrate expresses **multiple dynamical regimes** — rhythm generation *and* persistent activity — as neuromodulatory or attentional inputs shift it across parameter boundaries.

[[brunel-1999-sparsely-connected-networks|Brunel (2000)]] does the spiking analogue: the [[Asynchronous Irregular State|AI state]] is the substrate, gamma and sharp-wave ripples are Hopf bifurcations of the same balanced network, selectable by the `(g, ν_ext)` operating point.

This is the control-theoretic reading of [[Degeneracy]] in explicit form: genes set aggregate E-I coupling parameters; macroscopic attractors (limit cycles for locomotion, rotations for reaching, bistability for working memory) emerge with high probability; the microscopic wiring realizing them is free to vary.

### 3. The chaotic / AI reservoir as raw material

[[sompolinsky-1988-chaos-random-networks|SCS 1988]] (rate) and [[brunel-1999-sparsely-connected-networks|Brunel]] (spiking) establish what untrained recurrent networks generically do: silent below a critical coupling, deterministic high-dimensional chaos (or AI irregularity) above it. CTD-style trained dynamics — rotations, line attractors, preparatory states — are carved out of this reservoir by training. Near-critical operation ([[Edge of Chaos]]) gives long memory and high input sensitivity, the ingredients a control system needs.

[[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] provide the constructive existence proof that carving actually works: [[force-learning|FORCE learning]] trains chaotic recurrent networks (g = 1.5) to produce arbitrary coherent outputs — including human motion-capture running and walking — by modifying only readout or feedback weights while leaving the recurrent connectivity random. The in-silico trained manifold (~8 output-relevant PCs, ~50 uniquely-determined) is the mechanistic counterpart of the empirical ~10D monkey motor-cortex manifold. FORCE also gives a dynamical reading of preparation: a one-shot non-periodic sequence requires an input that quenches chaos into a prepared fixed point, mirroring the drop in motor-cortex neural variability at movement onset (Churchland et al. 2006).

## Where it is *not* yet unified

### The dendritic lineage is mostly tested on static classification

The credit-assignment lineage (Kording 2001 → Guerguiev 2017 → Sacramento 2018 → Payeur 2020 → Greedy 2022 → Francioni 2026) evaluates against MNIST and CIFAR. Francioni's BCI experiment is the first closed-loop neural substrate, and even it is a neurofeedback task, not a reaching or grasping task. Whether burst-dependent plasticity scales to the temporal-credit-assignment demands of motor control over hundreds of milliseconds is untested.

### The missing hinge

**No one has yet shown how burst-dependent plasticity at individual apical dendrites reshapes motor-cortex rotational manifolds during motor adaptation.** This is the hinge. Force-field and visuomotor-rotation adaptation experiments (Vyas 2018, Perich 2018, Sheahan 2016) show that adaptation shifts preparatory states; the dendritic lineage shows how individual-neuron weight updates could be computed; nobody has tied the two together at the level of dendritic events during the intertrial interval predicting shifts in preparatory state on the next trial.

### CTD is black-box about `f`

CTD treats the vector field `f(x, u)` as a black-box dynamical system to be analyzed by fixed-point finding and linearization. The dendritic-computation literature specifies what individual neurons compute. A formal derivation from "compartmentalized pyramidal neurons + SST/NDNF+ interneurons + STP + Dale's law" to a specific class of `f` that *produces rotational dynamics* is largely absent. The existing mesoscopic models (Wilson-Cowan, Jansen-Rit, balanced-E-I field theories) use point-neuron or rate abstractions and do not carry the compartmental structure forward.

### Two different notions of "manifold"

CTD's intrinsic manifold is the subspace of population states that the trained circuit actually visits. The dendritic literature's "capacity" is about how many classifications a single neuron or small network can solve. It is not obvious how single-neuron dendritic capacity translates into the dimensionality or geometry of the population manifold. The question "does richer dendritic computation produce a higher-dimensional or better-shaped control manifold?" has not been asked cleanly.

## Verdict

The unified picture exists in **sketch**:

> Biophysics (dendritic compartments, E-I balance, intrinsic excitability) shapes the manifold. CTD describes the flow on it. Dendritic credit assignment updates the weights when the manifold needs reshaping. Genes tune E-I parameters; macroscopic attractors emerge with high probability despite microscopic degeneracy. Sleep-dependent consolidation ([[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. 2009]]) operates the slow structural channel. The Helmholtz-machine lineage ([[dayan-hinton-1994-helmholtz-machine|Dayan et al. 1994]]) supplies the perceptual half of the loop.

But the **load-bearing connection** — single-neuron dendritic events → low-dimensional control dynamics — is conjectural. [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] is the first experimental toehold. Filling this gap is the central empirical and theoretical project the wiki is watching for.

## Bearing on the control thesis

What the literature *establishes* (with citations to source pages, not to this analysis):
- CTD-style low-dimensional dynamics describe motor-cortex behavior during preparation and movement at the population level.
- Burst-dependent dendritic plasticity approximates backpropagation in spiking networks at competitive accuracy and depth (in silico).
- Mesoscopic E-I parameters select among silent / oscillatory / chaotic / AI / SI dynamical regimes in mean-field models.
- Manifold-constrained BCI learning operates faster within the manifold than off it.

What the wiki *interprets* as evidence for the [[control-thesis-ledger|control thesis]] (this is a reading, not a derivation from any single paper):
- That the population-level CTD motifs *implement* control rather than merely correlating with it.
- That dendritic credit assignment *tunes the same loop* the population dynamics implement.
- That the regime-selection picture from E-I theory *is* the mechanism by which "genes constrain dynamics, not circuits."
- That fast (within-manifold) and slow (off-manifold) learning are *one system* operating at two timescales of the same loop.

Each of these readings is plausible and the wiki commits to them as working hypotheses; none is forced by the cited papers individually. The interpretive load belongs in the [[control-thesis-ledger|ledger]] (pillars P5 and P6) and in [[challenges-to-control-thesis|challenges to the control thesis]] (where [[brette-2018-coding-metaphor|Brette 2018]] and [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]] articulate why these readings are not free).

**The load-bearing empirical gap remains: nobody has shown how dendritic events on trial *n* predict manifold shifts on trial *n+1* during real motor adaptation.** [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] is the closest existing toehold — and is a neurofeedback BCI task, not natural reaching. Closing this gap is the central empirical project the wiki is watching for.

## Sources

- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — CTD as a named framework and catalog of motor-cortex motifs.
- [[sompolinsky-1988-chaos-random-networks|Sompolinsky, Crisanti & Sommers (1988)]] — chaos transition in random asymmetric rate networks.
- [[brunel-1999-sparsely-connected-networks|Brunel (2000)]] — Fokker-Planck theory of sparsely connected E-I spiking networks.
- [[wilson-cowan-1972-ei-populations|Wilson & Cowan (1972)]] — two-variable mean-field E-I population model; Theorem 4.
- [[kording-konig-2001-two-integration-sites|Kording & Konig (2001)]] — two integration sites → two independent variables per neuron.
- [[guerguiev-2017-segregated-dendrites|Guerguiev et al. (2017)]] — first spiking credit assignment with segregated dendrites.
- [[sacramento-2018-dendritic-microcircuits-backprop|Sacramento et al. (2018)]] — apical dendrite as prediction-error site; unifies PC with credit assignment.
- [[payeur-2020-burst-dependent-credit-assignment|Payeur et al. (2020)]] — burst-dependent plasticity + STP + inhibition ≈ backpropagation.
- [[greedy-2022-single-phase-burstccn|Greedy et al. (2022)]] — BurstCCN single-phase synthesis.
- [[francioni-2026-vectorized-dendritic-signals|Francioni et al. (2026)]] — first in vivo evidence of vectorized dendritic teaching signals during BCI learning.
- [[jones-2020-dendritic-computation-power|Jones & Kording (2020)]] — dendritic trees as multi-layer networks; MSBs as learning-reshapeable architecture.
- [[dayan-hinton-1994-helmholtz-machine|Dayan, Hinton, Neal & Zemel (1994)]] — the Helmholtz machine; perceptual half of the loop.
- [[wierzynski-2009-sleep-hpc-pfc|Wierzynski et al. (2009)]] — SWR-driven hippocampal-cortical coupling during SWS.
- [[sussillo-abbott-2009-force-learning|Sussillo & Abbott (2009)]] — FORCE learning as the constructive proof that trained motor-output dynamics can be carved out of the SCS chaotic reservoir; preparation-as-chaos-suppression; three architectures (readout feedback, separate feedback network, within-generator) as hypotheses for motor-cortex / cerebellum / basal-ganglia division of labor.
