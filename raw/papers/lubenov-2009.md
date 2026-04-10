---
title: "Hippocampal theta oscillations are travelling waves"
source: "https://claude.ai/chat/a1c85fdc-e503-4f0e-bad2-fc6bb4ac3eba"
author:
published:
created: 2026-04-10
description: "Claude conversation with 40 messages"
tags:
  - "clippings"
---
**Claude**

What's this paper about, and what drew you to it in the context of your research questions?

---

**You**

it shows that rather than theta oscillations (which are 4-10hz oscillations visible in the local field potential of the hippocampus) being synchronized across the whole hippocampus they are instead traveling waves going from one end to the other. the implication is that the hippocampus represents a line segment in physical space rather than a single point using theta oscillations. it's relevant because it's an example of a dynamical system in a population of neurons representing real info, not just being some correlative artifact (though i guess they didn't conclusively prove that in this paper either)

---

**Claude**

Good orientation. A few things to push on:

1. You said they didn't conclusively prove the travelling wave carries real information rather than being epiphenomenal. What would it take to prove that? What kind of experiment distinguishes "this wave pattern is computational" from "this wave pattern is a side effect of anatomy"?
2. The key methodological move in this paper is recording from stratum oriens specifically. Why? What problem does that solve, and what would go wrong if they recorded from stratum radiatum instead?

---

**You**

1. hmm perhaps a BCI-like experiment where the wave is computed and displayed live on the linear track the rat is on, and then the rat has to maybe turn 180 degrees without changing the line segment that's displayed from the wave (ie ABCD where A is behind the rat, and the rat basically has to turn to look at A to get some food without it turning around resulting in A switching to D's original position) – if this is impossible it provides evidence that A = behind you. you could do the same for BCD as well. you could also perhaps do an experiment where you disrupt the theta oscillation in some way and see if the rat gets disoriented? that's less direct tho.
2. not sure, i'm not really familiar with the anatomy here

---

**Claude**

On 1 — your disruption idea is actually the more powerful one. The BCI experiment is creative but it's testing what the wave *encodes*, not whether it's *used*. The cleanest test: disrupt the travelling wave property specifically — make theta synchronous across the hippocampus while preserving theta power and frequency — and see if spatial behavior degrades. That dissociates "theta matters" (already known) from "the wave structure of theta matters." Hard to do, but that's the logic.

On 2 — this is actually the key methodological insight of the whole paper, so let's get it. The problem: theta phase changes dramatically with depth. There's a phase reversal near the pyramidal cell layer, and a steep phase gradient through stratum radiatum. So if you put two electrodes at different lateral positions but at slightly different depths in radiatum, the phase difference you measure could be a depth artifact, not a lateral travelling wave. Stratum oriens solves this because theta phase is essentially constant across ~400μm of depth there. Small depth errors between electrodes don't contaminate your lateral phase measurements.

Does that click? Can you restate why the depth-invariance property is essential for their claim?

---

**You**

i see. yes it allows for electrode depth placement error to not be a confound when calculating the phase of theta at two points along the hippocampus. it lets you isolate how the phase of theta actually changes thru the hippocampus

---

**Claude**

Exactly. Now let's get into the core result. They find the phase gradient is ~21°/mm, propagating roughly along the septotemporal axis at ~80-107 mm/s with a wavelength of ~11-15mm.

What does it mean that the wavelength is "commensurate with the long hippocampal axis"? Why do they call that out specifically?

---

**You**

it means the direction of travel of the wave aligns with the septotemporal axis?

---

**Claude**

Not quite. Direction is a separate point (and yes, it's roughly septotemporal). "Commensurate" means the wavelength (~12-15mm) is comparable to the physical length of the hippocampus (~12-14mm in rat).

Why does that matter? Think about what it would mean if the wavelength were, say, 100mm — much longer than the hippocampus. Or 2mm — much shorter.

---

**You**

ah, it means that the wave goes through a single period as it travels down the hippocampus, so it repeats only one time, ie the phase of theta at each spot in the hippocampus can uniquely identify it so it is likely representing one unique location/point on the line segment that's being encoded

---

**Claude**

That's it. One wavelength ≈ one hippocampus length means each septotemporal position gets a unique phase — no ambiguity. If the wavelength were much shorter, multiple positions would share the same phase and the topographic map would be degenerate.

Let me draft cards for what we've covered so far.

**Card Drafts**

```
Q: In Lubenov & Siapas 2009, why did the authors record from stratum oriens specifically to study lateral theta phase organization?
A: Theta phase is depth-invariant there (~400μm), so small electrode depth errors don't contaminate lateral phase measurements.

Q: What is the approximate propagation speed of hippocampal theta travelling waves (Lubenov & Siapas 2009)?
A: ~80–107 mm/s

Q: What is the approximate spatial wavelength of hippocampal theta travelling waves?
A: ~11–15 mm

Q: Why is it functionally significant that the theta travelling wave's wavelength is commensurate with the hippocampus length?
A: Each septotemporal position gets a unique phase — no ambiguity in the topographic map.

Q: What direction do hippocampal theta travelling waves predominantly propagate?
A: Along the septotemporal axis (septal → temporal).

Q: In the Lubenov & Siapas setup, what would confound lateral phase measurements if recordings were made in stratum radiatum instead of stratum oriens?
A: The steep theta phase gradient with depth in radiatum — small depth errors between electrodes would mimic lateral phase differences.
```

Now let's move to Figure 6 — the core functional argument. What's their logic connecting travelling waves to the representation of a spatial segment rather than a point?

---

**You**

their example is a series of concentric circles ABCD where A is centered behind and D is in front of the rat. at a particular point in the wave's propagation, say early on, neurons associated with each of A B C D fire, but the combination of that particular theta phase + A/B/C/D uniquely identifies the point. so eg early theta + A means we are at the center of A, early theta + B means we are not at the center of B and instead to the left, same for C/D except more and more to the left of centers of C/D respectively

---

**Claude**

You're describing phase precession — that's the right ingredient. But I think you're conflating two things. Phase precession happens at a single septotemporal level. The question Figure 6 is really asking is: what happens when you combine phase precession with the sync vs. travelling wave distinction *across* septotemporal levels?

Here's the key question: at a single instant in time, under synchronized theta, every septotemporal level is at the same phase. Under a travelling wave, each level is at a different phase. Given phase precession, what does that difference imply about what's represented at that instant?

---

**You**

hmm for "phase precession happens at a single septotemporal level", in which direction is the phase precession occurring there? orthogonal to the septotemporal axis?

under synchronized theta, you can use the phase precession to represent movement but each septotemporal level represent the same point. vs if it's a traveling wave each septotemporal level can represent a different point on a line segment using the theta phase.

---

**Claude**

Right. Phase precession is a relationship between a neuron's firing phase and the rat's position within that neuron's place field — it's about physical movement through space, not a spatial axis on the hippocampus.

And yes, your second paragraph nails it. Synchronized theta → every septotemporal level is at the same phase → phase precession maps them all to the same point in space → hippocampal output encodes a point. Travelling wave → each septotemporal level is at a different phase → phase precession maps each to a different point → hippocampal output encodes a segment.

One more piece makes this richer: place field size increases along the septotemporal axis (small fields septally, large temporally). What does that add to the picture?

---

**You**

hmm i don't quite understand "Phase precession happens at a single septotemporal level" – the precession happens over time as the rat moves right. so the idea is that all the neurons at a single septotemporal level (which i am taking to mean a slice of the hippocampus so that all neurons have the same value in the septotemporal direction) have ~ the same place field? and then as the rat moves all of them precess to encode that movement?

place field size increasing means.. perhaps the animal has a richer representation of its location in front of itself?

---

**Claude**

Good catch, let me be more precise. At a single septotemporal level, neurons don't share one place field — they have place fields at many different locations, but of similar *size*. Only the subset whose fields overlap the rat's current position fire at any moment. Phase precession means each of those active neurons fires at a phase determined by how far the rat has progressed through *its* field.

So "phase precession at a septotemporal level" means: the active neurons at that level collectively trace out a segment of space within one theta cycle, via their phase-position relationships.

The travelling wave then staggers *when* each septotemporal level hits a given phase. So different levels are reading out different portions of their local spatial segments at each instant.

On place field size — it's simpler than a directional thing. Septal = small fields (fine resolution), temporal = large fields (coarse resolution). Combined with the travelling wave, within each theta cycle the hippocampal output sweeps from fine to coarse spatial resolution. Does that land?

---

**You**

so to be clear about all the dimensions a particular hippocampal neuron has: \* place field location (center of its place field) \* place field size (how big the place field is) – septotemporal level roughly encodes this \* phase precession (how far within a single theta period the neuron's max firing rate is) – encodes how far the rat has progressed through its field

i think i get all those but i don't see how the traveling wave part plays into this now. it feels like the phase precession already uses the "where within a theta period you are" dimension so that can't be reused by the traveling wave?

---

**Claude**

This is exactly the right confusion to have. The resolution: phase precession is defined relative to the **local** theta oscillation at that neuron's location. The travelling wave means the local theta phase is different at each septotemporal level at the same instant.

So at time t, septal neurons see local phase 90°, mid-hippocampus sees 180°, temporal sees 270° (say). Each level's neurons fire according to phase precession relative to *their own* local phase. Since each level is at a different local phase at the same instant, each level is reading out a different point in its phase-precession sequence — i.e., a different position in space.

Under synchronized theta, all levels see the same local phase at time t, so all levels read out the same position.

Does the local vs. global distinction resolve it?

---

**You**

ah i see that makes sense

write out the time zone analogy just to make this fully clear

---

**Claude**

It's noon in New York, 11am in Chicago, 10am in Denver, 9am in LA. Everyone is doing their "noon activity" at different clock times — NYC is at lunch while LA is still in morning meetings.

Same thing: septal hippocampus is at theta phase 270° while temporal is at 90°. Each level does its "270° activity" (fire neurons whose fields are centered behind the rat, say) at different moments. So at any instant, septal is representing one location and temporal is representing a different one — a segment of space is laid out across the hippocampus, just like "right now" corresponds to different local times across the country.

Synchronized theta would be like the whole country sharing one time zone — everyone does lunch simultaneously, and you only get one location represented at a time.

**Card Drafts**

```
Q: Phase precession relates a neuron's firing phase to position within its place field. In a travelling theta wave, is this phase measured relative to a global or local reference?
A: Local theta at that neuron's septotemporal level.

Q: Why does synchronized theta imply the hippocampus encodes a point in space, while a travelling wave implies a segment?
A: Synchronized: all septotemporal levels share the same local theta phase, so phase precession maps them to the same position. Travelling wave: each level has a different local phase, mapping each to a different position.

Q: Place field size increases along which hippocampal axis?
A: Septotemporal (small fields septally, large temporally).

Q: What does the combination of the theta travelling wave and the septotemporal place-field-size gradient imply about hippocampal output within a theta cycle?
A: Output sweeps from fine to coarse spatial resolution.
```

Now — the paper proposes three possible mechanisms for generating the travelling wave. Can you recall or reconstruct what they are?

---

**You**

direct creation via an oscillator (medial septum?) many weakly coupled oscillators (don't quite understand the mechanism here but that's fine – maybe it's the intrinsic oscillation of the hippocampus?) don't recall the third

---

**Claude**

Third is propagation of activity through an excitable network — specifically CA3, where in disinhibited slices, pulses propagate the full 10mm length at 0.1–0.15 m/s, matching the observed wave speed and direction.

On the coupled oscillators: entorhinal cortex neurons have intrinsic oscillation frequencies in the theta range, and those frequencies decrease along the dorsoventral axis. A gradient of natural frequencies in coupled oscillators naturally produces a travelling wave — the faster oscillators lead in phase and the wave propagates from fast to slow. Same principle may apply within CA1 itself.

The authors' point is that all three mechanisms likely contribute, and the whole system is a feedback loop, not feedforward.

**Card Drafts**

```
Q: What are the three mechanisms proposed for generating hippocampal theta travelling waves (Lubenov & Siapas 2009)? (1 of 3): delayed excitation from a single oscillator
A: Medial septum, whose projections are topographically organized along the septotemporal axis with different transmission delays.

Q: What are the three mechanisms proposed for generating hippocampal theta travelling waves? (2 of 3): propagation in an excitable network
A: CA3 recurrent network — pulses propagate its full length at ~0.1–0.15 m/s, matching observed wave speed.

Q: What are the three mechanisms proposed for generating hippocampal theta travelling waves? (3 of 3): frequency gradient in coupled oscillators
A: Entorhinal cortex neurons have intrinsic theta-range frequencies that decrease dorso-ventrally, so faster oscillators lead in phase.

Q: When I see a gradient of natural frequencies in a network of weakly coupled oscillators, I should consider...
A: Travelling wave emergence (fast → slow).
```

Anything else in this paper you want to dig into, or should we do a final review pass on all the card drafts?

---

**You**

reread the project instructions, especially the parts relevant to anki card generation, and re-generate the sets of anki cards from scratch (throw out the current cards)

---

**Claude**

```
Q: In Lubenov & Siapas 2009, why were recordings made in stratum oriens rather than stratum radiatum?
A: Theta phase is depth-invariant there (~400μm).

Q: What problem would stratum radiatum recordings introduce for measuring lateral theta phase differences?
A: Depth errors mimic lateral phase differences.

Q: Approximate propagation speed of hippocampal theta travelling waves?
A: ~80–107 mm/s

Q: Approximate spatial wavelength of hippocampal theta travelling waves?
A: ~11–15 mm

Q: Dominant propagation direction of hippocampal theta travelling waves?
A: Septal → temporal

Q: Why is it significant that the theta wave's spatial wavelength ≈ hippocampus length?
A: Each septotemporal position gets a unique phase.

Q: Phase precession: a neuron's firing phase is measured relative to what?
A: Its local theta oscillation.

Q: Under synchronized theta, the hippocampus instantaneously encodes a ___ in space. Under a travelling wave, a ___.
A: Point; segment.

Q: Why does a travelling wave produce segment encoding? (given phase precession)
A: Different septotemporal levels are at different local phases simultaneously.

Q: How does place field size vary along the septotemporal axis?
A: Increases (small septal, large temporal).

Q: Theta travelling wave + septotemporal place-field-size gradient → what property of hippocampal output within a cycle?
A: Sweeps fine → coarse spatial resolution.

Q: Mechanism 1 for theta travelling waves: delayed excitation from a single oscillator. Which structure?
A: Medial septum.

Q: Mechanism 2 for theta travelling waves: propagation in an excitable network. Which structure?
A: CA3 recurrent network.

Q: Mechanism 3 for theta travelling waves: frequency gradient in coupled oscillators. Which structure?
A: Entorhinal cortex.

Q: Why does a frequency gradient in coupled oscillators produce a travelling wave?
A: Faster oscillators lead in phase; wave propagates fast → slow.

Q: When I see a gradient of natural frequencies in weakly coupled oscillators, I should consider...
A: Travelling wave emergence.
```

---

**You**

has anyone done this experiment where theta waves were synchronized experimentally across the hippocampus to see if the animal was no longer able to navigate a linear track?

---

**Claude**

I didn't find the specific experiment you're describing — selectively converting the travelling wave into synchronous theta while preserving other properties. The closest work involves disru [eLife](https://elifesciences.org/reviewed-preprints/109375v1) pting theta-timescale coordination via medial septum manipulations (cooling to reduce frequency, entraining at abnormal frequencies, or scrambling theta), which impairs spatial task performance. But those experiments disrupt theta itself, not specifically the travelling wave property. They can't distinguish "theta matters" from "the wave structure of theta matters."

A 2017 theoretical paper explored how the travelling wave is actually *necessary* for maintaining a consistent phase code across the hippocampus, given that place field sizes vary along the septotemporal axis. The travelling wave imposes location-specific phase offsets that compensate for different precession rates. [Nature](https://www.nature.com/articles/s41598-017-08053-3) That's a theoretical prediction of what would break — but still not the direct causal experiment.

So as far as I can tell, the clean experiment — make theta synchronous while preserving power/frequency, test spatial behavior — hasn't been done. It's technically very hard: you'd need to independently control theta phase at multiple septotemporal levels simultaneously. Optogenetics can entrain theta at one frequency, but imposing zero phase lag across the whole hippocampus while keeping everything else constant is a different challenge entirely.

---

**You**

i see. what followups have broadly been done on the original paper here?

---

**Claude**

The main followup threads:

**Replication and extension along the full axis:** Patel et al. (2012) confirmed travelling theta waves along the entire septotemporal axis of the hippocampus [Nature](https://www.nature.com/articles/s41598-017-08053-3), addressing the original paper's caveat that they only recorded from the septal third.

**Confirmed in humans:** Zhang & Jacobs (2015) used multielectrode recordings from neurosurgical patients and found that human hippocampal theta oscillations are also travelling waves, propagating posterior-to-anterior (the human equivalent of septal-to-temporal given evolutionary rotation). They also found the waves appear at a broader frequency range than in rodents. [Journal of Neuroscience](https://www.jneurosci.org/content/35/36/12477)

**Extended to entorhinal cortex:** A 2020 eLife paper showed that the medial entorhinal cortex also activates as a travelling wave [eLife](https://elifesciences.org/articles/52289), confirming the original paper's prediction that the wave wouldn't be confined to CA1.

**Theoretical work on phase code consistency:** A 2017 paper showed mathematically that the travelling wave is actually *necessary* for maintaining a consistent relationship between spatial distance and theta phase differences across the hippocampus, because place field widths vary along the septotemporal axis. [Nature](https://www.nature.com/articles/s41598-017-08053-3)

**Broader travelling wave framework:** A 2018 Nature Reviews Neuroscience article placed the hippocampal result in a broader context of cortical travelling waves found across sensory, motor, and cognitive systems. [Nature](https://www.nature.com/articles/nrn.2018.20?error=cookies_not_supported&code=363e97e3-76a9-4e20-832a-0841e841c5b1)

So the basic finding has been robustly confirmed and extended. The causal experiment — specifically disrupting the wave property while preserving theta — remains undone.

---

**You**

what about in c elegans? any evidence of traveling waves

---

**Claude**

The situation in C. elegans is fundamentally different. The "travelling wave" in C. elegans is the **locomotor body wave** — the sinusoidal bending pattern that propagates head-to-tail for forward movement. This is a motor output, not an information-encoding oscillation like hippocampal theta.

Key findings relevant to your question:

Spontaneous subthreshold oscillations have NOT been confirmed in C. elegans. [eLife](https://elifesciences.org/articles/99904) So there's no analogue of hippocampal theta — no brain-wide oscillation that could be a travelling wave in the Lubenov & Siapas sense.

What *has* been found about C. elegans locomotor waves is interesting in its own right though. Multiple sections of the forward locomotor circuit can independently generate rhythms — distributed rhythm generators rather than a single head oscillator. [PubMed Central](https://pmc.ncbi.nlm.nih.gov/articles/PMC5780042/) Motor neurons function as oscillators, and descending interneuron inputs plus proprioceptive coupling work together to propagate bending waves along the body. [PNAS](https://www.pnas.org/doi/10.1073/pnas.1717022115)

So the C. elegans wave uses two of the three mechanisms from the Lubenov paper: excitable network propagation (proprioceptive coupling along the body) and coupled oscillators (distributed motor neuron oscillators). But it's serving a completely different function — generating movement rather than encoding spatial information.

The deeper question for your research: C. elegans has 302 neurons and no hippocampus. Is there a minimal system size below which travelling-wave-as-information-encoding doesn't emerge? Or is it that without a spatial map to encode, the question doesn't apply?

---

**You**

another way to think about it – is there a microcircuit that is "hippocampus-like" in c elegans? it may not use traveling waves in the same way but the same kind of oscillations could play an interesting analogous role for encoding associative and non-associative memories

---

**Claude**

There's no single "hippocampus-like" microcircuit in C. elegans, but the memory architecture is really interesting and quite different from what you might expect.

The key finding: C. elegans can form both short-term and long-term associative memories, and these are stored in different parts of the network. Short-term memories are primarily coded in sensory neurons, while long-term memories are relegated to inner layers (interneurons), allowing the sensory system to resume innate functionality. [eLife](https://elifesciences.org/articles/74434) That's a striking organizational principle — STM and LTM aren't just different durations of the same thing, they live in different circuit layers.

The molecular machinery is conserved: NMDA receptors (nmr-1) are required for both STM and LTM, while CREB (crh-1) is required only for LTM [NCBI](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3187929/) — same as in mammals. The NMDA receptor is expressed in only six pairs of interneurons (AVA, AVD, ADE, RIM, AVG, PVC). [NCBI](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3187929/) So those interneurons are your closest thing to a "hippocampal" node — they're the convergence point where association happens.

Individual sensory neurons can code either the conditioned stimulus identity or the experience valence, and interneurons integrate these to modulate behavior. [eLife](https://elifesciences.org/articles/74434) This parallels the mammalian division where the hippocampus handles context, amygdala handles valence, and sensory cortex provides stimulus information — but compressed into ~6 interneurons.

One wild result: associative memories in C. elegans can be transmitted to F1 progeny through sperm, involving histone methylation and small RNA pathways. [Nature](https://www.nature.com/articles/s41467-023-39804-8) That's transgenerational inheritance of learned associations — no hippocampus needed.

The answer to your original question: the oscillation-based encoding strategy of the hippocampus doesn't have a clear C. elegans analogue. C. elegans memory is more about changing synaptic weights and receptor expression in identified neurons. It's local learning rules all the way down — no global clock needed when your entire network is 302 neurons. The interesting connection to your research: the *molecular* learning rules (NMDA-dependent plasticity, CREB-dependent consolidation) are conserved, but the *computational architecture* that deploys them is radically different.

---

**You**

hmm, how are short term memories consolidated from sensory neurons to interneurons? this uses local learning rules?

---

**Claude**

This is where it gets really concrete and relevant to your research questions. The picture emerging is:

**STM lives in sensory neurons** as changes in their response properties — things like altered calcium dynamics in AWC when it detects butanone. This is cell-autonomous plasticity: the sensory neuron itself changes how it responds. The local learning rules here are molecular: receptor trafficking, DAG signaling, calcium sensor modulation.

**LTM consolidation to interneurons** involves a specific mechanism that's been worked out in detail for olfactory memory. Sleep is required to consolidate odor memory. Memory consolidation requires the AIY interneurons (but not for acquisition). In worms that consolidate memory, both sleep and odor conditioning are required to diminish inhibitory synaptic connections between AWC sensory neurons and AIY interneurons. [Cell Press](https://www.cell.com/cell/pdf/S0092-8674\(23\)00525-1.pdf) So consolidation literally involves remodeling of specific synapses — measured with fluorescent synaptic markers in a living animal.

Enhanced Gαq signaling in the AWC sensory neuron non-cell-autonomously induces CREB activity in AIM interneurons, which then transcribes long-term memory genes to consolidate the memory. [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S1074742714001385) So the sensory neuron signals to the interneuron to trigger its own consolidation — it's not a top-down process.

Immediately after conditioning and up to 15 minutes post-conditioning, memory is independent of transcription, translation, or the activity of the primary sensory neurons. [Cell Press](https://www.cell.com/iscience/fulltext/S2589-0042\(24\)02372-1) This suggests there's an initial trace that's neither in sensory neurons nor dependent on gene expression — possibly residing in network activity or transient molecular states.

The consolidation timeline: distinct memory phases with clear transition points [Cell Press](https://www.cell.com/iscience/fulltext/S2589-0042\(24\)02372-1) — an early transcription/translation-independent phase, then sensory-neuron-dependent maintenance, then CREB-dependent consolidation into interneurons requiring sleep.

To your question about local learning rules: yes, this is local rules all the way. The AWC neuron's Gαq pathway detects the coincidence of odor + food, changes its own response (STM), and also sends a signal to downstream interneurons that triggers CREB-dependent gene expression there (LTM). No global controller orchestrates the transfer. The "consolidation" is an emergent consequence of local signaling between connected neurons — the sensory neuron essentially instructs its postsynaptic partner to make the change permanent.

This connects directly to your research on how local learning rules generate system-level plasticity. The C. elegans case is about as clean an example as exists: identified neurons, known synapses, specific molecular pathways, and you can watch the synapses physically remodel.

---

**You**

back to establishing causality of the traveling wave property being computationally key – what work has been done here?

---

**Claude**

The short answer: nobody has causally tested the travelling wave property specifically. What exists is a set of experiments that establish causality for theta's *temporal structure* but not its *spatial propagation structure*.

The closest work:

**Theta scrambling** (Etter et al. 2023): Optogenetic frequency scrambling of hippocampal theta abolished the oscillation's regularity, which impaired working memory while surprisingly leaving spatial codes (place fields) intact. [Nature](https://www.nature.com/articles/s41467-023-35825-5) This tells you theta's temporal regularity matters for memory but doesn't touch the travelling wave question.

**Phase-specific closed-loop inhibition** (Siegle & Wilson 2014): Closed-loop optogenetic inhibition of CA1 at specific theta phases causally demonstrated that peak vs. trough of theta serve different functions — peak inhibition improved navigation with external cues, trough inhibition improved navigation with internal cues. [Neuron](https://www.cell.com/neuron/fulltext/S0896-6273\(15\)00258-5) This shows theta phase is computationally meaningful, but the manipulation was at a single hippocampal location, not across the septotemporal axis.

**Phase precession causality** (2023): Optogenetic stimulation replicating theta phase precession patterns produced stronger sharp-wave ripple reactivation and more stable place fields than random-phase stimulation. [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S258900422301310X) This establishes that the phase-position relationship (phase precession) is causally important for memory consolidation — a necessary prerequisite for the travelling wave to matter.

**Entorhinal input manipulation** (2025): Inhibiting entorhinal layer III inputs to CA1 impaired phase precession slope and range but surprisingly strengthened theta sequences, suggesting these are dissociable and depend on circuit-level dynamics across the trisynaptic circuit. [Nature](https://www.nature.com/articles/s41467-025-61453-2)

The gap remains exactly where we identified it earlier: you'd need to impose synchronous theta across the septotemporal axis while preserving local theta properties — frequency, power, phase precession at each site. While MS inputs could theoretically control hippocampal temporal codes directly, causal evidence is still lacking. [Nature](https://www.nature.com/articles/s41467-023-35825-5) The technical barrier is that existing optogenetic approaches entrain theta from a single source (medial septum), which naturally produces a travelling wave via the same anatomical delays that generate it normally. To *remove* the wave while keeping theta, you'd need independent phase control at multiple septotemporal sites simultaneously — a qualitatively harder experiment than anything done so far.

So the state of the field: theta matters (established), theta phase matters (established), phase precession matters (established), but whether the *spatial propagation* of theta across the hippocampus is computationally necessary remains an open question. The theoretical work (2017 paper on phase code consistency) provides the strongest argument that it should matter.

---

**You**

When should travelling-wave structure be interpreted as part of the computation, rather than just a geometric description of coordinated activity?

how would Siapas respond to this, especially given the original paper was written in 2009 and a lot has happened since?

---

**Claude**

Good question. Let me think about what the strongest version of Siapas's position would be, given what's accumulated since 2009.

He'd probably push back on the framing itself. The distinction between "part of the computation" and "geometric description of coordinated activity" assumes these are separable — but the whole point of the Computation Through Dynamics framework (which you know well) is that the geometry *is* the computation. A travelling wave is a specific dynamical regime that constrains which patterns of co-activation are possible at each instant. That constraint is the computation.

More concretely, he'd likely argue: the travelling wave isn't a description layered *on top of* the real computation. It's the mechanism by which the hippocampus achieves topographic mapping of space onto its anatomy at each instant. Without the wave, you don't get the segment representation — you get a point. That's a different computation, not the same computation described differently.

He'd point to the converging evidence: the wave is present whenever theta is present, it's consistent across animals, the wavelength matches the hippocampal length (not an accident — it's the regime that gives unique phase assignment), it's confirmed in humans and entorhinal cortex, and the 2017 theoretical work shows it's *necessary* for maintaining a consistent phase code given variable place field sizes. The system appears tuned to produce exactly this wave.

The strongest version of his argument against the "just geometry" interpretation: if you could make theta synchronous (removing the wave), the phase precession code would break across septotemporal levels — neurons at different levels would no longer maintain consistent spatial relationships via their phase differences. That's a prediction, not yet tested, but it follows directly from the architecture.

Where he'd probably be honest about limits: the causal experiment hasn't been done. And there's a deeper question about whether the hippocampus *needs* to represent a segment rather than a point — maybe a point representation would work fine for navigation and the segment is epiphenomenal. That's harder to argue against without the behavioral manipulation.

What's your intuition? Do you think there's a meaningful distinction between "the geometry is the computation" and "the geometry is a side effect of the wiring"?

---

**Claude**

How Do We Learn?