# Open Questions

Tracked unknowns and research gaps. Each entry is a single question with a status tag and references — not a literature summary. For the per-pillar evidence picture see [[control-thesis-ledger|the ledger]]; for sustained engagement with rivals see [[challenges-to-control-thesis|challenges to the control thesis]].

**Status tags**: `open` (no published evidence either way) · `partial` (some evidence; cleaner test needed) · `contested` (evidence cuts both ways) · `superseded` (resolved or made moot by later work).

---

## Control & sensorimotor foundations

- What is the minimal *biological* closed-loop sensorimotor system that exhibits learning? `open` Refs: [[li-2024-prediction-noise-reward|Li 2024]] (toy network sufficiency proof).
- Is the transition from reactive to model-based control continuous or discrete (across evolution and development)? `open`
- How do memory systems feed back into the sensorimotor loop — does memory *serve* control by extending its horizon? `open` (P2; foundational reframing question for the wiki)

## Genes → dynamics → behavior

- Given a distribution over neuronal parameters set by gene expression, what is the probability of the target macroscopic structure emerging? `open` — the quantitative form of P3. Refs: [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt 2019]], [[Degeneracy]].
- What are the molecular-to-dynamical mappings? Ion channel expression → membrane dynamics → network attractors is the rough chain; the intermediate steps are poorly characterized. `open`
- Can the four genetically-consistent local turning biases ([[rosenberg-2021-labyrinth-learning|Rosenberg 2021]]) be traced to specific genes? `open` — sharpest available test of genes→control→structure.
- Are there mammalian analogs of the *daf-2* life-stage circuit reconfiguration ([[banerjee-2023-life-stage-chemosensation|Banerjee 2023]]) — systemic endocrine signals gating effective electrical-synapse connectivity? `open`

## Molecular & cellular

- What triggers protein synthesis in memory consolidation? `open`
- What determines whether a calcium signal produces LTP vs. LTD? `open` — the molecular-cascade specificity is unsettled.
- What is the full nonlinear-dynamical-systems space a single neuron can implement using its ion channels? `partial` — [[jones-2020-dendritic-computation-power|Jones & Kording 2020]] addresses an abstract version; biophysical version remains.
- Where does the membrane-potential RC analogy break down? `open` — phenomena requiring beyond-HH frameworks.
- Are habituation, sensitization, and Pavlovian pairing reproducible in non-neural cells? `open` — extension of [[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]]'s spacing-effect demonstration.
- Is the cellular spacing effect causally relevant to animal memory or only mechanistically parallel? `partial` — Pagani et al. 2009 (SHP2 in *Drosophila*) closest existing causal link.

## Circuits & systems

- Does SWR-driven HPC→PFC spike timing during SWS *actually induce plasticity*, or merely fall in the STDP window? `open` Refs: [[wierzynski-2009-sleep-hpc-pfc|Wierzynski 2009]].
- What information is in SWR-driven hippocampal replay — faithful reinstatement, compressed edit, or generative recombination? `open`
- Is travelling-wave structure in [[Theta Oscillations|theta]] *causally* necessary for spatial behavior, or would synchronized theta suffice? `open` Refs: [[lubenov-2009-theta-travelling-waves|Lubenov 2009]].
- Is one-shot home-path learning ([[rosenberg-2021-labyrinth-learning|Rosenberg 2021]]) dependent on hippocampal place-cell formation during the inbound traversal, or path-integration alone? `open`
- What is the functional role of REM sleep in the two-stage consolidation model? `open`
- Are the four motor-cortex CTD motifs (preparatory ICs, output-null preparation, rotational dynamics, CIS) general or motor-specific? `partial` — rotations appear in speech cortex (Stavisky 2019), absent in SMA / muscles (Lara 2018a). Refs: [[vyas-2020-computation-through-dynamics|Vyas 2020]].
- Is null-space structure learned or given — does the brain learn to place preparation in the null space of fixed readouts, or do readouts and dynamics co-adapt? `open`

## Representations & learning speed

- Does passive exposure build sparse codes that accelerate later reinforced learning? `open` Refs: [[meister-2022-learning-fast-slow|Meister 2022]] (proposed); [[reinert-2021-pfc-categorization|Reinert 2021]] (does not isolate passive vs. reinforced).
- Is the gradual emergence of category selectivity in mPFC ([[reinert-2021-pfc-categorization|Reinert 2021]]) driven by upstream-sensory representation building or PFC rule learning? `open` — simultaneous imaging would distinguish.
- Why are Go-preferring vs. NoGo-preferring PFC neurons asymmetric during rule switches (remapping vs. replacement)? `open`
- Are lab 2AFC tasks studying learning machinery or representation formation? `open` — methodological worry about the relevance of trial-based paradigms to ethological learning. Refs: [[ethological-paradigms]].

## Credit assignment lineage

See [[credit-assignment-lineage|credit-assignment lineage]] for the consolidated open-questions section. Highlights:

- Does the lineage extend to *temporal* credit assignment (delayed rewards, sequences)? `open` — all six papers address only spatial / cross-layer credit.
- How does burst-dependent plasticity interact with neuromodulation? `open` — the M(t) gating term is unspecified.
- Are NDNF⁺ and SST⁺ interneurons complementary or competing in dendritic credit signals? `open` Refs: [[francioni-2026-vectorized-dendritic-signals|Francioni 2026]].
- Does the lineage's "error" signal (burst rate / plateau / apical voltage / Q-Y residual) compress to one biological variable, or are these distinct read-outs? `contested`
- Does dopamine RPE solve temporal credit assignment? How does a global scalar reach the specific synapses causally responsible? `open`

## Neural manifolds & dynamics

- What enforces the conserved manifold across individuals — connectivity topology, neuromodulatory state, dynamic regime, or all three? `open` Refs: [[brennan-2019-conserved-macroscopic-dynamics|Brennan & Proekt 2019]].
- Does manifold geometry change topologically (new loop) or parametrically (modified flow) during learning? `open`
- Does the manifold framework scale to higher-dimensional dynamics in larger nervous systems? `open` — current methods assume relatively low-dim structure.
- Why do biological systems consistently find general computational strategies while RNNs trained on the same tasks exploit dataset-specific statistics? `open` Refs: [[brennan-2023-looper-computational-scaffold|Brennan 2023]].
- Can computational scaffolds be compared formally across systems with a rigorous distance metric? `open`
- Can rotational dynamics be causally falsified by patterned optogenetic perturbation along the rotation axis? `open` — tools available; falsification experiment not done.

## Random networks, chaos, and the operating point

- Does cortex operate at the [[Edge of Chaos|edge of chaos]] (gJ ≈ 1)? Through what homeostatic mechanism is the operating point maintained? `open` Refs: [[sompolinsky-1988-chaos-random-networks|SCS 1988]].
- Is cortical trial-to-trial variability primarily deterministic chaos, channel noise, or a mixture? `contested`
- Is there a unified description that interpolates between SCS chaos and Brunel AI? `open` — conceptually the same phenomenon, no single framework derives both.
- Does cortex sit near an AI/SI boundary (allowing gamma/ripple excursions) or well inside AI (for robustness)? `open` Refs: [[brunel-1999-sparsely-connected-networks|Brunel 2000]].
- Can gamma and sharp-wave ripples really collapse onto a single phase diagram, or do they require cell-type-specific generators? `open`
- Does Wilson-Cowan **Theorem 4** (limit-cycle ↔ hysteresis interconvertibility under bias) hold in single cortical populations on physiological timescales? `open` — the formal kernel of context-dependent reconfiguration.
- Does the DMFT formalism extend to networks with plasticity (joint activity-connectivity dynamics)? `open` — would close a gap between circuit dynamics and learning.

## Inference, predictive coding, FEP

- Is the [[free-energy-principle|FEP]] empirically distinguishable from its rivals, or a unifying language? `contested` Refs: [[friston-2010-free-energy-principle|Friston 2010]].
- Does cortex actually adjust synaptic gain on prediction-error units in proportion to inverse error variance? `partial` — preliminary mouse V1 evidence; full test pending.
- Where do FEP's heritable phenotype-specific priors come from? `open` — the embodied analog of the constraint-discovery problem.
- Does the [[dark-room-problem|dark-room problem]] really not arise for pure perceptual [[rao-ballard-1999-predictive-coding|Rao-Ballard]]? Does adding action revive it? `contested`
- Are FEP and [[li-2024-prediction-noise-reward|PaN]] compatible (priors + noise) or alternative (priors vs. noise)? Can a single experiment distinguish them in vivo? `open`
- Are layer 2/3 pyramidal neurons specifically the prediction-error carriers in cortex? `partial` Refs: [[rao-ballard-1999-predictive-coding|Rao & Ballard 1999]]; mouse V1 work (Keller-Mrsic-Flogel 2018; Attinger 2017).
- Does hierarchical predictive coding scale to V2 / V4 / IT? `open`
- Does the constraint-discovery problem ([[jaynes-1957-maxent-statistical-mechanics|Jaynes 1957]]) admit a principled solution — a second-order MaxEnt over constraint sets? `open` — the deepest theoretical gap in the inference lineage.
- Is the brain running Helmholtz-style amortized inference (feed-forward + offline tuning) or CTD-style recurrent dynamics? Distinguishable predictions during recognition / imagination / sleep. `open`

## Subjective physics & representational claims

- What carries directed relational structure ("Paul drives car") in cortex? `open` — synchrony handles symmetric relations only. Refs: [[binding-problem]], [[brette-2018-coding-metaphor|Brette 2018]].
- Are generative models compatible with [[subjective-physics|subjective physics]], or genuinely alternative? Is there a sensorimotor reformulation predicting *consequences of actions* rather than *causes of inputs*? `open`
- Does the wiki's coding-flavored language (place cells "encode" location, V1 "encodes" orientation) survive Brette's critique under a strict correspondence-with-experimental-scope reading? `open` — methodological / conceptual.
- What does a "model that behaves" look like at cortical scale beyond the [[zhang-2024-endotaxis-neuromorphic-navigation|endotaxis]] insect-scale example? `open`

## Cognitive navigation, ethology, sudden insight

- Is endotaxis the actual hippocampal computation? Are the three predicted cell populations (point, map, goal) dissociable in recordings? `open` Refs: [[zhang-2024-endotaxis-neuromorphic-navigation|Zhang 2024]].
- How is the mode switch (selecting among goal signals and routing to the chemotaxis module) implemented biologically? `open`
- Is the [[Mushroom Body]] → [[Hippocampus]] motif correspondence deep homology or convergent evolution? `open`
- What is the mechanism of *sudden insight*? Candidates (attractor phase transitions, sparse-code emergence, consolidation-driven reorganization) are not mutually exclusive and are not yet experimentally distinguished. `open` Refs: [[rosenberg-2021-labyrinth-learning|Rosenberg 2021]].
- Why does exploration remain dominant (75–95%) even in rewarded animals after learning? `open` — hedging, intrinsic reward, or default-mode persistence?

## Hopfield, attractor memory, capacity

- What is the right asymmetric extension of the Hopfield network for sequence memory? `open` — symmetric Hopfield gets ~4-step sequences before breaking. Refs: [[hopfield-1982-collective-computational-abilities|Hopfield 1982]].
- Does cortex ever cross the spin-glass phase transition (α > α_c)? Failure mode would be retrieval of confabulated memories. `open` — possible signal in dementia / schizophrenia.
- Is CA3 closer to dense-quadratic Hopfield (0.138 N capacity) or modern (dense, exponential) Hopfield? `open` — connects to whether brain associative memory is fundamentally quadratic or super-quadratic.
- Does the sparse-coding capacity boost match the empirical sparseness of CA3 / mushroom-body codes? `open`
- Is replica symmetry broken in trained recurrent networks? Static analog of CTD-carved manifolds. `open` Refs: [[parisi-1979-replica-symmetry-breaking|Parisi 1979]].

## FORCE & trained chaotic networks

- What biologically plausible rule could approximate FORCE's millisecond-timescale plasticity requirement? `open` Refs: [[sussillo-abbott-2009-force-learning|Sussillo & Abbott 2009]].
- Does FORCE's three-architecture taxonomy map onto motor cortex + cerebellum / basal ganglia? `open`
- Is the operational edge of chaos (largest g where FORCE works, ~1.5) the same as the theoretical edge (gJ = 1)? Why does training benefit from being *inside* the chaotic regime? `open`
- Can FORCE-style training scale to closed-loop sensorimotor control with realistic feedback delays? `partial`

## Cellular cognition

- Why does suboptimal training *down-regulate* total CREB? `open` — homeostatic / interference protection? Refs: [[kukushkin-2024-massed-spaced-non-neural|Kukushkin 2024]].
- What kinetic parameters set the conserved 5–20 min optimal ITI? Chemistry-imposed or evolved? `open`
- Can CRE-luc cell protocols predict optimal training schedules in animals? `open` — would close cells→behavior pipeline.
- What is the formal factorization between cellular and circuit-level memory primitives? `open` — synapses give pairwise specificity; cellular cascades give temporal-pattern decoding. Which phenomena need which?

## Methodology & "what does it mean to understand?"

- Which neuroscience methods recover [[marrs-levels-of-analysis|Marr-level]] understanding when validated against ground-truth artificial systems? `open` Refs: [[jonas-2017-microprocessor-critique|Jonas & Kording 2017]].
- Is a microprocessor the right test bed? Stochasticity, cell-type heterogeneity, evolved bottom-up structure — does the brain differ in ways that make the analogy misleading? `contested`
- What does Lazebnik's "fix it" test look like in practice for cortical regions? Where do prosthetics succeed in the strong sense vs. the weak sense? `open`
- Where on the compressibility axis does the brain actually sit (between tic-tac-toe and Go)? `open` Refs: [[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]].
- What is the actual information content of the genome's brain-construction recipe (beyond ~6 × 10⁹ bits permissive)? `open`
- Can the [[principles-vs-parameters|principles-vs-parameters]] split be made empirically operational — measurement protocols that target the recipe rather than parameters? `partial` — Francioni 2026 is the cleanest existing example.

## Falsifying the wiki's thesis

- What specifically would falsify the wiki's organizing thesis ("intelligence begins with closed-loop sensorimotor control")? `open` — articulated in [[control-thesis-ledger|the ledger]] per pillar; needs ongoing maintenance.
- Does embodiment-agnostic AI (LLMs, transformer cognition without sensorimotor loops) constitute a counterexample to P1? `open` — the largest curation gap.
- Does V1 receptive-field development in dark-reared animals weaken the requirement for *active* sensorimotor coupling? `open` — wanted ingest.
- Does compositional / symbolic generalization (language) reduce to sensorimotor primitives, or escape them? `open`

## Wiki-meta

- Is the wiki's thesis a Lakatosian hard core, a Hacking style of reasoning, a Galisonian trading-zone vocabulary, or a Bourdieusian low-capital position? `open` — see [[historiographic-frameworks-comp-neuro|historiographic frameworks]]; multiple lenses apply.
- Does the wiki's coverage have a curation bias toward control-friendly sources? `open` — wanted ingests in the [[control-thesis-ledger|ledger]] are the proposed hedge.
- Should the wiki add an institutions / community-artifacts axis (Caltech CNS, Janelia, NEURON, COSYNE etc.)? `open` — meta-question about scope.
- When does an LLM-generated meta-survey count as a source vs. a pointer to sources? `open` — citation hygiene under [[chatgpt-2026-comp-neuro-kuhnian-review|the Kuhnian]] and [[chatgpt-2026-comp-neuro-kuhnian-historiography|historiography]] reports.

## Wanted primary-source ingests

Surfaced by historiography review as foundational gaps:

- Hebb 1949, *Organization of Behavior* — foundational for [[hebbian-learning|Hebbian learning]].
- Marr 1982, *Vision* — currently in the wiki only via secondary citations.
- Barlow 1961 chapter — primary for [[efficient-coding-hypothesis|efficient coding]].
- Rall 1964 — primary for [[dendritic-computation|dendritic theory]].
- McCulloch-Pitts 1943 — ancestor of connectionism.
- van Vreeswijk-Sompolinsky 1996 — conceptual primary for the AI state.
- Knill-Pouget 2004 — primary review for Bayesian brain.
- Boyden et al. 2005 — optogenetics methodology.
- Stokes 2015 *TICS*; Wolff 2017 *Nat Neurosci* — activity-silent working memory (genuine local anomaly within attractor accounts).
- Berke 2018; Engelhard 2019; da Silva 2018 — dopamine heterogeneity beyond scalar RPE.
- A major LLM / embodiment-agnostic AI critique — to discharge or sharpen P1.
- A major connectomics paper (e.g. *Drosophila* hemibrain) — to engage the connectomics paradigm on its own terms.
