---
title: "A Kuhnian Historiography of Computational Neuroscience"
type: source
source_type: article
authors:
  - "ChatGPT (OpenAI deep research)"
year: 2026
tags: [philosophy-of-neuroscience, methodology, paradigms, kuhn, lakatos, historiography, sociology-of-science, meta-review]
date_ingested: 2026-04-30
key_finding: "A historiographic methodology for computational neuroscience that uses primary exemplars (papers, software, datasets) and community artifacts (training programs, conferences, journals, infrastructure, funding) as evidence; chronological scaffold from Lapicque (1907) to Blue Brain (2024); argues Kuhn fits well at the subcommunity level but requires complementary frameworks (Lakatos, Galison, Hacking, Bourdieu, Laudan) at the field level because comp neuro discontinuities are predominantly technology- and infrastructure-driven."
---

[Source PDF](../../raw/articles/computational-neuroscience-kuhnian-historiography.pdf)

## Provenance and how to read this source

This is an **LLM-generated deep research report** (ChatGPT, ~April 2026), the historiography sibling of [[chatgpt-2026-comp-neuro-kuhnian-review|the Kuhnian review report]] ingested earlier. Same provenance discipline applies: the report is a *meta-survey* and a *navigation document*, not a peer-reviewed primary source. The report's primary contribution to the wiki is its *methodological / historiographic strategy* and its *chronological scaffold* of primary exemplars and community artifacts — useful as a roadmap for which primary sources the wiki should ingest if it wants to follow up on any specific historical claim. Substantive empirical claims should be re-anchored against the cited primary literature before being treated as load-bearing.

The two ChatGPT 2026 reports overlap substantially (same nine-ish paradigm clusters, same Kuhnian framing, same crisis-vs-pluralism diagnosis) but differ in emphasis:
- The **review** ([[chatgpt-2026-comp-neuro-kuhnian-review|earlier ingest]]) inventories paradigms, anomalies, and crisis signals — its load-bearing contribution is the *meta-frame* (paradigm pluralism, captured in [[paradigm-pluralism-comp-neuro|paradigm-pluralism-comp-neuro]]).
- The **historiography** (this report) supplies a *methodology* for writing the field's history using primary exemplars + community artifacts as evidence, plus a *long chronological timeline* (1907–2024) with citation anchors, plus *alternative historiographic frameworks* beyond Kuhn (Lakatos research programmes, Galison trading zones, Hacking styles of reasoning, Bourdieu field theory, Laudan research traditions).

The historiography's main lift over the review is therefore: (i) the alternative-frameworks dimension (captured in [[historiographic-frameworks-comp-neuro|historiographic-frameworks-comp-neuro]]), (ii) the timeline as a primary-source ingest candidate list, and (iii) the institutional / sociological analysis of training, conferences, funding, and infrastructure as paradigm transmitters.

## Overview

The report develops a Kuhnian historiographic strategy for computational neuroscience that operationalizes Kuhn's categories (paradigm, normal science, anomaly, crisis, revolution, incommensurability, disciplinary matrix) as historically tractable indicators:

- **Exemplars** — canonical models and worked solutions (HH model, Rall dendritic theory, Hopfield network, Rao–Ballard).
- **Training mechanisms** — graduate programs (Caltech CNS PhD, Gatsby Unit), textbooks (*Theoretical Neuroscience*, *Spiking Neuron Models*), simulation toolchains (NEURON, GENESIS, NEST), summer schools.
- **Community standards** — what counts as explanation, acceptable idealization, and validation, codified in conference norms (CNS, COSYNE, NeurIPS) and journals (*Neural Computation*).

The narrative is structured as (a) periods of normal science (puzzle-solving within stable exemplar sets), (b) anomalies (persistent mismatches or methodological breakdowns), and (c) reconfigurations where new exemplars and standards reorganize practice. Six (rather than nine) candidate paradigms are surveyed:
1. **Conductance-based mechanistic modeling and simulation** (HH lineage, Rall dendritic theory, NEURON/GENESIS).
2. **Network dynamics and attractor computation** ([[hopfield-network|Hopfield 1982]], balanced-network theory 1996, spiking simulators).
3. **Neural coding and information-theoretic representation** (Barlow 1961 onward).
4. **Normative probabilistic inference and predictive processing** ([[rao-ballard-1999-predictive-coding|Rao–Ballard 1999]], [[free-energy-principle|Friston 2010]], Knill–Pouget 2004).
5. **Data-intensive statistical and ML neuroscience** (large-scale recording era, Neuropixels, NWB standards, Allen Observatory).
6. **Large-scale "digital brain" reconstruction / simulation neuroscience** (Blue Brain 2005–2024, Human Brain Project 2013–2023).

The report's key historiographic claim: Kuhn's framework fits *well* at the subcommunity level (where exemplars + training + standards are concretely identifiable), and fits *poorly* at the whole-field level because comp neuro is structurally interdisciplinary and has expanded predominantly through *instrumentation and infrastructure shifts* rather than through anomaly-driven theoretical revolutions in a single dominant paradigm.

## Key claims

### Historiographic methodology: evidence-first scaffold

A Kuhnian historiography of comp neuro should treat "paradigm" as a historically anchored package of (i) exemplars, (ii) training mechanisms, and (iii) community standards, and should narrate the field via primary citations rather than sweeping conceptual descriptions. The report's timeline table follows this discipline — every milestone is tied to a primary or official source (PubMed records, OA chapters, institutional history pages, archival paper PDFs).

The practical archival workflow is: (1) reconstruct shifting exemplars via cited papers and tools; (2) map community consolidation through conference programs, proceedings, and textbook editions; (3) document infrastructure and funding shifts through official initiative pages and standards documents; (4) only then use secondary historiography (e.g., philosophical analyses of explanation in computational neuroscience) to interpret how explanatory norms and field values changed.

### Chronological scaffold (selected milestones with primary anchors)

The report provides a citable timeline (verbatim selections, Lapicque → Blue Brain end-of-2024):

| Date | Milestone | Why it matters historiographically |
|---|---|---|
| 1907 | Lapicque introduces an early integrate-and-fire neuron model | Establishes an enduring exemplar of idealization; recurs across spiking models and inference models. |
| 1943 | McCulloch & Pitts, logical calculus model of neural activity | Seeds the "neuron-as-logical/computational element" lineage; conceptual ancestor of connectionism and ML-style paradigms. |
| 1948 | Wiener publishes *Cybernetics* | High-level disciplinary-matrix vocabulary (feedback, signals, communication) that unifies heterogeneous modeling traditions. |
| 1949 | Hebb publishes *The Organization of Behavior* | Stabilizes learning-as-synaptic-change as a guiding commitment later re-expressed in neural networks, plasticity rules, and RL. |
| 1952 | [[gerstner-neuronal-dynamics-ch2|Hodgkin & Huxley conductance-based action-potential model]] | Canonical mechanistic exemplar enabling decades of normal science in conductance-based modeling. |
| 1961 | Barlow's *Sensory Communication* chapter — efficient-coding lineage | Establishes a normative/information-theoretic tradition: explanation via optimality/information constraints rather than detailed mechanism. |
| 1964 | Rall's dendritic-tree theory | Foundational mathematical exemplar for compartmental modeling; central to simulation neuroscience. |
| 1976 | Neher & Sakmann, single-channel patch-clamp recording | Technology-driven expansion of what counts as "data" for mechanistic models; stabilizes normal science. |
| 1982 | Marr publishes *Vision* (levels of analysis) | Reshapes what "explanation" means in brain science. ([[marrs-levels-of-analysis|Marr's levels]]) |
| 1982 | [[hopfield-1982-collective-computational-abilities|Hopfield network]] | Establishes attractor-network exemplar supporting normal-science puzzle-solving in memory, optimization, and dynamics. |
| 1986 | Rumelhart, Hinton & Williams popularize backpropagation | Reboots learning-centered network paradigms; later becomes a focal *anomaly* site in biological-plausibility debates. |
| 1986 | Caltech CNS PhD program founded | Institutionalizes interdisciplinary training — critical for paradigm reproduction via shared exemplars and codebases. |
| 1987 | NeurIPS founded | Cross-field "trading zone" between neural networks and neuroscience. |
| 1988 | Sejnowski, Koch & Churchland publish "Computational Neuroscience" in *Science* | Programmatic synthesis explicitly noting *lack of large-scale theories* — key evidence about paradigm status. |
| 1988 | GENESIS simulation system development begins | Software as infrastructural exemplar embedding modeling-granularity and validation norms. |
| 1989 | *Neural Computation* journal begins publishing | Core venue consolidating theory + modeling + neural computation standards. |
| 1990 | Stanley Ogawa reports BOLD contrast (early fMRI lineage) | Whole-brain functional measurement; drives new model classes and statistical paradigms. |
| 1990 | Carver Mead, "Neuromorphic electronic systems" | Hardware-embodied computational paradigm feeding into modeling constraints. |
| 1992 | First CNS Meeting in San Francisco | Annual conference where puzzles, exemplars, and standards stabilize and are contested. |
| 1994 | NEST simulator first released | Tool for normal-science large-scale spiking simulation. |
| 1996 | [[brunel-1999-sparsely-connected-networks\|Balanced-network / asynchronous-irregular-state theory]] (van Vreeswijk & Sompolinsky 1996) becomes prominent | Exemplar shift in interpreting variability — from "noise" to "network regime." |
| 1997 | NEURON simulation environment described in canonical methods paper (Hines & Carnevale) | Codifies mechanistic modeling workflows and validation; embeds paradigmatic assumptions in software. |
| 1999 | [[rao-ballard-1999-predictive-coding\|Predictive coding formalization in visual cortex modeling (Rao & Ballard)]] | Helps consolidate predictive-processing paradigms reframing explanation as inference under generative models. |
| 2001–2002 | *Theoretical Neuroscience* (Dayan & Abbott) and *Spiking Neuron Models* (Gerstner & Kistler) consolidate field training | Textbooks as Kuhn's paradigm carriers — transmit exemplars + standards to new practitioners. |
| 2003 | Allen Institute founded | Institutional driver of data-centric paradigms and benchmark datasets. |
| 2004 | COSYNE begins | Epistemic venue tightening theory–data coupling. |
| 2005 | Optogenetics milestone (Boyden et al.) | Adds causal manipulation at scale; shifts what counts as explanatory adequacy (predict → intervene). |
| 2005 | INCF founded | Infrastructure for standards and interoperability; cross-lab normal science on shared data formats. |
| 2005–2024 | Blue Brain Project | Large-scale "digital reconstruction" research program testing whether detailed simulation is a central paradigm. |
| 2013–2023 | Human Brain Project (EU FET Flagship → EBRAINS) | Large-scale institutional attempt to reshape the field; case study for sociology-of-science analysis. |
| 2013–present | BRAIN Initiative (US) | Institutional and technological acceleration aligning with Kuhn's "outside the sciences" conditions. |
| 2014–present | NWB (Neurodata Without Borders) data standardization | Shift in disciplinary matrix: shared data languages become central exemplars for cumulative multi-site normal science. |
| 2017 | Neuropixels high-density silicon probes | Reconfigures feasible puzzles (population dynamics at scale); drives statistical/ML paradigms. |
| 2017–present | BICCN/BICAN cell-atlas programs | Reinforces data-driven paradigms; pressures standardization and integrative cross-modality modeling. |

The timeline is intended as an *evidence-first scaffold*. Many of these milestones are already in the wiki (Hodgkin–Huxley via [[gerstner-neuronal-dynamics-ch2|Gerstner Ch. 2]]; [[hopfield-1982-collective-computational-abilities|Hopfield 1982]]; [[rao-ballard-1999-predictive-coding|Rao–Ballard 1999]]; [[brunel-1999-sparsely-connected-networks|Brunel 1999/2000]]; [[wilson-cowan-1972-ei-populations|Wilson–Cowan 1972]]; [[friston-2010-free-energy-principle|Friston 2010]]; [[sompolinsky-1988-chaos-random-networks|SCS 1988]]). Several flagged as load-bearing exemplars are not yet ingested:
- **Lapicque 1907** (integrate-and-fire) — historical ancestor of LIF and spiking models.
- **McCulloch & Pitts 1943** — logical-calculus model; ancestor of connectionism.
- **Hebb 1949** — *Organization of Behavior*; the Hebb rule's primary source.
- **Barlow 1961** — *Sensory Communication* chapter; primary source for the [[efficient-coding-hypothesis|efficient-coding hypothesis]].
- **Rall 1964** — dendritic-tree theory; primary source for [[dendritic-computation|dendritic computation]].
- **Sejnowski, Koch & Churchland 1988** — *Science* article naming the field.
- **van Vreeswijk & Sompolinsky 1996** — balanced-network theory; primary source for the [[asynchronous-irregular-state|AI state]] before Brunel's analytical treatment.
- **Marr 1982** *Vision* — primary source for [[marrs-levels-of-analysis|Marr's levels]] (currently in the wiki only via secondary citations).
- **Rumelhart, Hinton & Williams 1986** (Nature) — backpropagation in neural networks.
- **Boyden et al. 2005** — optogenetics primary paper.
- **Hines & Carnevale 1997** — NEURON paper.
- **Knill & Pouget 2004** — Bayesian-coding-hypothesis review.

These are explicit ingest candidates the historiography surfaces.

### Where Kuhn fits well, where it requires modification

**Kuhn fits well** at the subcommunity level. The conductance-based modeling tradition has clear canonical exemplars (HH, Rall), tool-embedded practices (NEURON, GENESIS), and validation norms shaped by electrophysiology — a recognizable disciplinary matrix. Data-intensive comp neuro around high-density recording has infrastructural exemplars (Neuropixels), data standards (NWB), and statistical-modeling norms codified in methodological syntheses. Kuhn's emphasis on *education and textbooks* as paradigm transmitters maps cleanly onto comp neuro, where textbooks (*Theoretical Neuroscience*, *Spiking Neuron Models*) and software tutorials (NEURON, GENESIS, NEST documentation) often function as the most powerful vehicles for exemplar transmission. His treatment of *translation* and "going native" helps explain why cross-paradigm disputes hinge on learning a new formal language (probabilistic modeling, deep nets, new data-languages) rather than on pointwise empirical refutation.

**Kuhn fits poorly or requires modification** at the whole-field level. Comp neuro has frequently lacked the Kuhnian signature of a single dominant paradigm that suppresses fundamental controversy. Sejnowski, Koch & Churchland (1988) explicitly described the domain as lacking large-scale theories and as defined by problems and methods. This suggests either (i) a *pre-paradigmatic* condition (consistent with Masterman's observation of paradigm polysemy in Kuhn) or (ii) a field whose primary organizing structures are *infrastructural and methodological rather than theoretical*. Comp neuro's major discontinuities are often **technology- and infrastructure-driven** (recording, imaging, intervention, standardization), whereas SSR's canonical story emphasizes anomaly-to-crisis dynamics within relatively stable observational regimes. In a domain where new instruments change what can be observed and manipulated, "revolution" may be precipitated less by anomaly accumulation and more by shifts in feasible experimental/computational coupling, funding priorities, and data-sharing infrastructure.

### Alternative historiographic frameworks (key contribution)

Because comp neuro often hosts *coexisting* approaches (mechanistic, normative, statistical/ML, simulation-first), Kuhn benefits from complementary frameworks. The report inventories:

- **Imre Lakatos — research programmes**. Models science as competing programmes with *hard cores* (negative heuristic) and *protective belts* (positive heuristic of auxiliary hypotheses). Provides criteria for *progressive vs. degenerative* problemshifts without requiring a single paradigm monopoly. Captures the "pluralism + hybridization" pattern the [[chatgpt-2026-comp-neuro-kuhnian-review|review sibling]] identifies more naturally than strict Kuhn.
- **Larry Laudan — research traditions**. Accommodates persistent pluralism and treats *problem-solving success* as the unit of progress rather than paradigmatic replacement.
- **Peter Galison — trading zones**. Maps cross-field coordination via partial languages, tools, and local agreements — a precise fit for comp neuro's cross-disciplinary conferences (NeurIPS, COSYNE, CNS), shared software ecosystems (NEURON, NEST, NWB), and standardized data formats. Kuhnian incommensurability becomes tractable as *partial translation in a trading zone* rather than as wholesale untranslatability.
- **Ian Hacking — styles of reasoning**. Adds analytic depth for understanding why some modeling styles become dominant — the *style* (mechanistic-realist, normative-optimal, predictive-statistical) is itself a historically produced commitment that constrains what counts as a legitimate problem.
- **Pierre Bourdieu — field theory**. Adds sociological depth: institutional capital, funding, and prestige structures explain why certain paradigms become dominant even when alternative styles remain viable. Critical for understanding the rise of large-scale-data paradigms and the institutional-flagship era (Blue Brain, HBP, BRAIN Initiative).

These frameworks are not rivals to Kuhn but complements: Kuhn at the subcommunity level, Lakatos / Laudan at the multi-paradigm field level, Galison at the cross-paradigm coordination level, Hacking at the style level, Bourdieu at the institutional-power level. Captured in [[historiographic-frameworks-comp-neuro|historiographic-frameworks-comp-neuro]].

### Sociological / institutional drivers

Four drivers recur as paradigm-shaping in comp neuro:

1. **Interdisciplinary training institutions** (Caltech CNS PhD 1986; Gatsby Unit 1998; OCNS / Allen / Janelia training programs) act as *paradigm engines* — stabilizing exemplars (courses, codebases) and selecting for shared values about modeling practice.
2. **Conferences and journals** provide the social machinery of normal science: CNS Meeting (1992), OCNS, COSYNE (2004), NeurIPS (1987); *Neural Computation* (1989); these define what counts as a good puzzle, a satisfying solution, and legitimate evaluation standards.
3. **Funding regimes and big-science initiatives** (NSF CRCNS; NIH BRAIN Initiative 2013–present; EU Human Brain Project / EBRAINS 2013–2023) reshape the disciplinary matrix by prioritizing certain data types, scales, and infrastructures.
4. **Enabling technologies and data infrastructures** are unusually central to comp neuro: patch-clamp (1976), fMRI (BOLD 1990), optogenetics (2005), Neuropixels (2017), NWB standardization (2014–), INCF (2005). These redefine feasible puzzles and acceptable models — the *disciplinary matrix* by way of toolchains rather than theory.

This is the report's strongest case for why comp neuro requires non-Kuhnian frameworks at the field level: theoretical revolutions are rarer than instrumentation-driven reconfigurations of feasible normal science.

## Methods

Meta-analytic / bibliographic. The report cites ~150 primary sources and major reviews and uses Kuhn's *Structure of Scientific Revolutions* (and the 1965/1970 *Criticism and the Growth of Knowledge* debates, the 1969 Postscript, and Hoyningen-Huene's reconstruction) as the analytical scaffolding. Operational definitions:

- **Paradigm** = exemplars + training mechanisms + community standards (the Kuhnian "disciplinary matrix" specialization).
- **Anomaly** = persistent mismatch or methodological breakdown that resists alignment with professional expectation.
- **Crisis** = anomalies that "subvert the existing tradition of scientific practice."
- **Reconfiguration** = period where new exemplars and standards reorganize research practice (broader than full Kuhnian revolution; absorbs Lakatosian progressive problemshifts).

Bibliographic strategy emphasizes primary papers, official institutional pages, and journal/proceedings archives over secondary commentary. The report explicitly names this as an evidence-first historiographic discipline — citing primary exemplars and community artifacts as the loci of disciplinary-matrix commitments.

## Implications

For the wiki specifically:
- **Provides a methodology** for writing the wiki's own historical narrative around primary exemplars + community artifacts, complementary to the meta-frame in [[paradigm-pluralism-comp-neuro|paradigm pluralism]].
- **Surfaces specific primary-source ingest candidates** the wiki should consider (Hebb 1949, Barlow 1961, Rall 1964, McCulloch–Pitts 1943, Sejnowski–Koch–Churchland 1988, van Vreeswijk–Sompolinsky 1996, Marr 1982 *Vision* primary, Knill–Pouget 2004, Hines–Carnevale 1997, Boyden 2005). These are listed as open-question / future-ingest candidates.
- **Adds historiographic frameworks** beyond Kuhn (Lakatos, Galison, Hacking, Bourdieu, Laudan) to the wiki's methodological toolkit, captured in [[historiographic-frameworks-comp-neuro|historiographic-frameworks-comp-neuro]].
- **Supplies sociological / institutional analysis** the wiki had been treating implicitly — training programs, conferences, journals, funding, and infrastructure as paradigm transmitters and reshapers.
- **Sharpens the hedging** on the wiki's organizing thesis: under a Lakatosian reading, "intelligence begins with closed-loop sensorimotor control" is the *hard core* of the wiki's research programme, and the surrounding apparatus (CTD, dendritic credit assignment, [[cellular-cognition|cellular cognition]], the [[degeneracy|control-theoretic genes hypothesis]]) is the *protective belt*. Whether the programme is *progressive* (predicting novel facts) or *degenerative* (only accommodating existing facts via auxiliary hypotheses) is the right Lakatosian question to ask.

For computational neuroscience more broadly (per the report's own claim):
- Field histories should be written from primary exemplars + community artifacts, not from sweeping conceptual narratives.
- Discontinuities in the field's history are predominantly *infrastructural* (new instruments, new data formats, new shared toolchains) rather than *anomaly-driven* in Kuhn's classical sense.
- Kuhn at the subcommunity level + Lakatos / Galison / Hacking / Bourdieu at the field level is the right analytical pluralism.

## Connections to existing knowledge

- **[[paradigm-pluralism-comp-neuro|Paradigm Pluralism]]** ([[chatgpt-2026-comp-neuro-kuhnian-review|ChatGPT 2026 review sibling]]): same Kuhnian frame, extended by historiographic methodology. The historiography is the methodological underbelly of the review's diagnostic claims.
- **[[historiographic-frameworks-comp-neuro|Historiographic Frameworks for Comp Neuro]]**: the topic page that captures Lakatos / Galison / Hacking / Bourdieu / Laudan as alternatives or complements to Kuhn.
- **[[principles-vs-parameters|Principles vs Parameters]]** ([[lillicrap-kording-2019-understanding-neural-networks|Lillicrap & Kording 2019]]): the historiographic timeline shows that field-level discontinuities are predominantly *infrastructure-driven*; this is consistent with principles-vs-parameters in that the *recipe* (architecture, plasticity rules, developmental program) gets specified at the level of paradigms / research programmes / styles, while the *trained parameters* (specific theoretical commitments in any individual lab) are protected by the institutional capital surrounding that programme.
- **[[marrs-levels-of-analysis|Marr's Levels]]**: the report flags Marr 1982 *Vision* as a load-bearing primary source not yet directly ingested.
- **[[free-energy-principle|FEP]]** / **[[predictive-coding|predictive coding]]**: cited as paradigm 4 (normative probabilistic inference and predictive processing); historiographic anchors are Rao–Ballard 1999 (already in wiki), Knill–Pouget 2004 (not yet ingested), Friston 2010 (already in wiki).
- **[[hopfield-network|Hopfield Network]]** / **[[wilson-cowan-1972-ei-populations|Wilson–Cowan]]** / **[[brunel-1999-sparsely-connected-networks|Brunel]]** / **[[sompolinsky-1988-chaos-random-networks|SCS]]**: cited as canonical exemplars of the network-dynamics-and-attractor paradigm.
- **[[gerstner-neuronal-dynamics-ch2|Gerstner Ch. 2]]** for HH: the wiki currently has HH only via the textbook chapter; the historiography flags the Hodgkin & Huxley 1952 primary paper (J. Physiol.) as the canonical exemplar worth direct ingest.
- **[[efficient-coding-hypothesis|Efficient Coding Hypothesis]]**: the wiki has the hypothesis as a topic but not its primary source (Barlow 1961); the historiography flags this gap.
- **[[dendritic-computation|Dendritic Computation]]**: the wiki has the topic but not Rall 1964 as a primary source.
- **[[hebbian-learning|Hebbian Learning]]**: the wiki has the topic but not Hebb 1949 directly.

## Open questions raised

- **Which historiographic framework best fits the wiki's own thesis?** Under Kuhn, the wiki's "intelligence begins with closed-loop sensorimotor control" thesis is a paradigm-style commitment in tension with coding-frame paradigms. Under Lakatos, it is a *research programme* with the control thesis as the hard core, and the question becomes whether the surrounding theoretical apparatus generates *novel* predictions (progressive) or only accommodates existing data via auxiliary hypotheses (degenerative). Under Galison, the wiki itself is a *trading zone* coordinating sources from different paradigms via a partial common language. Under Hacking, the wiki commits to a specific *style of reasoning* (control-theoretic, dynamical-systems, sensorimotor). Under Bourdieu, the wiki is a low-institutional-capital outpost relative to the dominant DNN-as-brain-model and Bayesian-brain programs. These framings are not rivals — they are complementary lenses, and the wiki's hedging would benefit from being explicit about which lens it is using when.
- **Primary-source ingest candidates surfaced by the timeline.** Hebb 1949, Barlow 1961, Rall 1964, McCulloch–Pitts 1943, Sejnowski–Koch–Churchland 1988, van Vreeswijk–Sompolinsky 1996, Marr 1982 *Vision* primary, Knill–Pouget 2004, Hines–Carnevale 1997, Boyden et al. 2005 — each would close a "primary source not yet ingested" gap on an existing wiki topic. Worth prioritizing by which thread of the wiki's organizing thesis each best supports.
- **Are the sociological/institutional drivers properly tracked?** The wiki currently has individual-researcher pages and source pages; it has no systematic treatment of institutions (Caltech CNS, Gatsby, Salk, Janelia, Allen Institute) or community artifacts (CNS Meeting, COSYNE, NeurIPS, *Neural Computation*, NEURON, NEST, NWB). Whether to add an institutions/community-artifacts axis is a meta-question for the wiki's structure.
- **Is the field's history actually infrastructure-driven?** The historiography report's claim that comp neuro discontinuities are predominantly technology/infrastructure-driven rather than anomaly-driven is a strong empirical claim about the history. It deserves checking against the primary literature — particularly the 1986 backprop revival, the 1996 balanced-network reinterpretation, the 1999 predictive-coding consolidation, and the 2009–2013 dynamical-systems crystallization, which are partly theoretical reorganizations. The claim may be over-stated for the theory side and well-supported for the data/measurement side.
- **Single-citation hedging.** This is a single LLM-generated meta-survey; its operational definitions and the boundaries of its six paradigm clusters have not been independently vetted. The historiographic methodology it proposes (evidence-first scaffold via primary exemplars + community artifacts) is a sound discipline regardless of whether the report's specific synthesis is correct.

## Sources

- Self: ChatGPT (OpenAI deep research), "A Kuhnian Historiography of Computational Neuroscience," ~April 2026.
- Companion to [[chatgpt-2026-comp-neuro-kuhnian-review|the Kuhnian review report]] (same author, same date, overlapping bibliography). The review supplies the diagnostic / paradigm-mapping content; this report supplies the historiographic methodology and chronological scaffold.
- The article's bibliography (links collected on pages 16–18 of the source PDF) is the load-bearing contribution; primary sources should be consulted directly when specific historical claims are followed up in the wiki.
