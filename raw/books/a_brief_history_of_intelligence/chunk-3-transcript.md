---
title: "Chunk 3"
source: "https://claude.ai/chat/7648e70d-f54c-45a3-a861-5b0183db9f2f"
author:
published:
created: 2026-04-10
description: "Claude conversation with 41 messages"
tags:
  - "clippings"
---
**You**

Let’s do chunk 3

---

**Claude**

Good, I've read the chunk. This section covers the emergence of neurons and their core properties — from the animal template (gastrulation + neurons + muscles) through Adrian's three discoveries (spikes, rate coding, adaptation), synaptic transmission, excitatory/inhibitory neurons, and nerve nets as the pre-brain architecture.

Since this is a non-textbook book, we'll do light carding — but first, let's make sure the key ideas are solid. Let me start with a few questions:

**1.** Bennett argues that gastrulation, neurons, and muscles are the three inseparable features that define animals and separate them from all other kingdoms of life. What's the functional story he tells for *why* these three co-evolved? What ecological pressure tied them together?

**2.** Adrian discovered three universal features of neurons. Can you walk me through the logical chain connecting them? Specifically: why does the first discovery (spikes) create a puzzle, how does the second (rate coding) solve it, and why does the second then create a *new* problem that requires the third (adaptation)?

**3.** What role do inhibitory neurons play, and how does Bennett frame their significance in terms of what kind of computation they enabled? He makes a specific claim about what was "new" vs. "not new" here — what is it?

---

**You**

1. Hmm neurons being needed for movement+perception for larger animals performing active hunting, muscles being needed for movement & digestion, and a stomach being needed to separate digestive enzymes from the rest of the animal?
2. Spikes created a puzzle because they are all identical so it was unclear how neurons transmit info, rate coding showed how it’s the rate of firing that contains info, and then it’s unclear how neurons represent super wide distributions of stimuli with a capped max firing rate (500hz?) which is solved by adaptation, ie adjusting representation resolution in response to stimuli
3. Inhibitory neurons allow animals to stop doing certain behaviors, eg stop moving/change direction.

---

**Claude**

Good start on all three, but each needs sharpening.

**On 1:** You've got the right pieces but the story isn't quite assembled. The stomach part — Bennett's emphasis isn't on separating enzymes from the animal's body, it's on a more basic problem: level-two multicellular life was too big to eat via phagotrophy (engulfing into a single cell), so animals invented internal digestion — trapping prey in a cavity. That's the gastrulation story. But the deeper question is: why do neurons and muscles *specifically* bind to this, when plants and fungi also eat other life and also sense and respond to their environment? What's the difference Bennett highlights?

**On 2:** The logical chain is right, and the 500 Hz cap is correct. But "adjusting representation resolution" is a bit vague. Can you be more precise about *what* adaptation actually does? Bennett makes a specific claim about what neurons end up encoding — absolute values or something else?

**On 3:** This is the one that needs the most work. You're describing a generic notion of inhibition. Bennett gives a very concrete example of *why* inhibitory neurons were needed — involving a coral polyp's mouth. What's the specific computational problem? And he makes a pointed claim about what was genuinely new about "do this, not that" logic in neurons vs. what already existed. What's the distinction?

---

**You**

1. Neurons are needed to sense when an animal is done eating and needs to expel waste. Muscles allow an animal to physically do the expulsion. Plants/fungi do external digestion so they don’t need this
2. Neurons encode relative strength of stimuli not absolute values. So they become less sensitive to stronger stimuli and vice versa
3. They were needed for a coral polyp to be able to close its mouth after prey had entered. The computational problem is that you would need a whole separate circuit to handle ‘close mouth’ instead of just turning off the ‘open mouth’ circuit?

---

**Claude**

**On 2:** Yes, that's it. Neurons encode relative changes in stimulus strength, not absolute values. The stronger the baseline stimulus, the more it takes to get a response — and conversely, neurons become more sensitive when stimuli are weak. That's how you solve the squishing problem without needing a bigger firing rate range.

**On 1:** The waste expulsion story isn't Bennett's argument. Plants and fungi also sense and respond to their environment — they orient toward light, grow toward food. So sensing and responding per se isn't what makes neurons necessary. Bennett's key distinction is something else entirely. Think about the *temporal* difference between how a plant responds to its environment and how a coral polyp catches prey. What's the word pair he keeps emphasizing?

**On 3:** You're closer but the geometry of the example is off. It's not about needing a separate circuit for closing vs. opening. Think about what has to happen *mechanically* even for a single action like opening the mouth — how many muscle groups are involved, and what must they do *simultaneously*? That's where the need for inhibition comes from. And then: what's Bennett's claim about whether this "do this, not that" logic was truly novel in evolution?

---

**You**

1. Ah active hunting requires making a sudden precise movement to catch some prey, which requires muscles and neurons. Plants are just “always on” comparatively
2. A lot of coordination is needed to open a mouth. So relaxing/contracting muscles properly requires inhibition. Hmm not sure about the novelty bit

---

**Claude**

**On 1:** You're almost there. "Sudden precise movement" captures it informally, but Bennett has a specific phrase he keeps returning to. The distinction between animals and plants/fungi isn't just speed or just precision — it's both. The word pair is **speed and specificity**. Plants orient toward the sun over hours to days; coral catches prey in seconds. Plant movement is clumsy and inexact; a coral polyp's catch-and-swallow reflex requires precise orchestration — grasping, opening the mouth, pulling in, closing — all with well-timed coordination of different muscle groups. Only the animal survival strategy of actively killing level-two multicellular life demanded *both* speed and specificity, and that's why animals have neurons and muscles while fungi (which also eat other life) don't.

**On 3:** Right — opening the mouth requires one set of muscles to contract *while another set simultaneously relaxes*. That's the concrete need for inhibition. Without inhibitory neurons, you can't enforce "contract these, relax those" at the same time.

On the novelty question: Bennett says "do this, not that" logic was **not new**. It already existed in the protein cascades of single cells. What *was* new is that this logic was recapitulated in the medium of neurons, which made it possible at the scale of level-three multicellular life. Same computational principle, new substrate, new scale.

Does that distinction make sense — same logic, different medium?

---

**You**

Yes

---

**Claude**

Good. A couple more things from this chunk before we card:

**4.** Bennett describes two levels of neural communication. What are they, and where does each operate?

**5.** The section ends by describing the nervous system architecture of early animals (and modern corals/jellyfish). What is it called, and how does it differ structurally from a brain? Why does this distinction matter for the story Bennett is building toward?

---

**You**

1. Within neurons - electrical. Between neurons - chemical signals across synapses
2. Hm don’t remember what it’s called, but I suppose the idea is small clusters of neurons in different places across the body. It’s different in that there’s no single centralized controller (a brain)

---

**Claude**

**On 4:** Exactly right.

**On 5:** The term is **nerve net** — a distributed web of independent neural circuits, each implementing its own independent reflexes. Your description of the structural difference is right: no centralization. Bennett's point is that this is the architecture that existed *before* breakthrough #1, which rewired nerve nets into brains. So the nerve net is the baseline — the "before" picture.

Alright, understanding is solid. This is a non-textbook book chapter, so we'll do light carding — key frameworks, surprising facts, and things that connect to your research interests. Let me propose cards:

```
Bennett argues neurons evolved for active hunting, not just sensing/responding, because only killing level-two multicellular life required {{c1::speed and specificity}} — the two properties that distinguish animal movement from plant/fungal responses.
```

```
Adrian's three discoveries about neurons, in logical order: {{c1::all-or-nothing spikes}} created the puzzle of how graded info is encoded, solved by {{c2::rate coding}}, which created the squishing problem (natural variables span a million-fold range but firing rate caps at ~{{c3::500}} Hz), solved by {{c4::adaptation}}.
```

```
Neural adaptation means neurons encode {{c1::relative changes in}} stimulus strength rather than {{c1::absolute values}} — they become less sensitive to strong baselines and more sensitive to weak ones.
```

```
Neural communication within a neuron is {{c1::electrical}}; across neurons (via synapses) it is {{c2::chemical}} (neurotransmitters).
```

```
Inhibitory neurons evolved because even simple reflexes (e.g., a coral polyp opening its mouth) require {{c1::one set of muscles to contract while another simultaneously relaxes}} — enforcing "do this, not that" logic.
```

```
"Do this, not that" logic was not new to neurons — it already existed in {{c1::protein cascades of single cells}}. What was new was implementing this logic at the scale of {{c2::level-three multicellular life}}.
```

```
Before brains, early animals had a {{c1::nerve net}}: a distributed web of {{c2::independent neural circuits}} each implementing their own independent reflexes.
```

How do those look?

---

**You**

anything around stomachs/internal digestion?

---

**Claude**

Good call. The gastrulation story is a core piece of this chapter.

```
Animals evolved {{c1::internal digestion (a stomach cavity)}} because level-two multicellular life was too large for {{c1::phagotrophy (engulfing into a single cell)}}, the previous strategy for eating other life.
```

```
The three inseparable features that bind all animals together and separate them from all other kingdoms of life are {{c1::gastrulation (stomach)}}, {{c2::neurons}}, and {{c3::muscles}}.
```

Want to add those?

---

**You**

yes sounds good

question: does bennett go into the \_order\_ of how these evolutionary changes come about? i mean the implied story i am getting is: \* level-2 multicellular organisms became level-3 at some point \* they were too big to eat single cells via phagotrophy so evolved internal digestion/stomachs to eat level-2 organisms \* notably they were \_not\_ mobile at this point - i assume just waited for level-2 organisms to float into their mouth? \* then at some point neurons+muscles co-evolved allowing them to actively hunt (eg coral polyp example)

---

**Claude**

Good question, and your reconstruction is reasonable, but I think it goes slightly beyond what Bennett actually claims here. A few things to note:

Bennett's key framing is that gastrulation, neurons, and muscles are **inseparable** — every animal that gastrulates also has neurons and muscles, and no non-animal does any of the three. He presents them as a package that defines the animal lineage, not as a clear temporal sequence where stomachs came first and neurons came later.

So the honest answer is: Bennett doesn't commit to a clean ordering in this chunk. He presents two competing hypotheses about the *form* of the earliest animals (gastrula-shaped creature vs. coral-like polyp), notes both are controversial, and doesn't resolve it.

Your intuition about passive feeding preceding active hunting is plausible — modern corals do exactly that (tentacles floating, waiting for prey to bump into them, then reflexively contracting). But that's a modern coral, not necessarily a temporal stage all animals passed through.

The thing Bennett *does* clearly argue is the **functional logic**: the animal niche of eating level-two life is what made all three necessary, and the specific demand for speed and specificity is what made neurons and muscles necessary (as opposed to the slower chemical signaling plants use). But whether stomachs preceded neurons by millions of years or they emerged together — he doesn't say.

Does that distinction matter for how you're thinking about this, or were you mainly checking whether you missed an explicit ordering?

---

**You**

ok thats fine. broadly what does the evolutionary literature say for the order in which these occurred? i am curious because i am thinking about \_how\_ the first neuron actually came about and i would think the order matters there

---

**Claude**

This is genuinely debated territory, but here's the rough picture:

The dominant view is that **cell specialization happened gradually** from an ancestral multicellular colony. The most popular hypothesis for neuron origins is that they evolved from **secretory cells** — cells that were already releasing chemical peptides to communicate locally with neighboring cells. These proto-neurons were doing chemical signaling before they were doing electrical signaling. The electrical part (action potentials) came as a speed upgrade on top of pre-existing chemical communication.

This fits a plausible ordering: multicellular colony → cell differentiation including secretory/sensory cells → some of those cells develop electrical excitability (proto-neurons) → coordination with contractile cells (proto-muscles) → all of this in the context of a body plan that includes a digestive cavity.

But the honest caveat: there's real disagreement. The ctenophore (comb jelly) problem complicates things — their neurons use very different molecular machinery than cnidarian/bilaterian neurons, which has led some to argue neurons evolved independently more than once. If true, that undermines any single clean ordering story.

The part most relevant to your research interest: the first neuron probably wasn't a sudden invention. It was likely a gradual co-option of existing chemical signaling machinery, with electrical excitability added for speed. The "neuron" is a speed hack on top of slower peptidergic communication that already existed.

Does that connect to what you were thinking about?

---

**You**

two questions: \* did other parts of ancient multicellular life also use electricity besides proto-neurons? basically is there any benefit to neurons doing chemical->electrical signal conversion beyond speed? \* is the bennett argument implicitly then that the electrical signaling \_speed\_ of neurons is really what was needed for active hunting? i mean all the logic (even inhibition) could be performed with chemical signaling pathways/proteins no?

---

**Claude**

Great questions. On both:

**On electricity beyond neurons:** Yes, electrical excitability is ancient and not unique to neurons. Plants have action potentials (Venus flytraps use them to snap shut). Even single-celled paramecia use voltage changes to reverse their swimming. So electrical signaling predates neurons.

Beyond speed, there's a second major benefit: **range**. Chemical diffusion degrades rapidly with distance — it scales with the square root of time, so it works fine for local cell-to-cell signaling but becomes useless across a macroscopic body. An electrical spike traveling down an axon can cross centimeters or meters with no signal degradation (the all-or-nothing property guarantees this). So for a large level-three organism that needs to coordinate distant muscle groups, chemical diffusion alone simply doesn't work.

**On Bennett's argument:** You're right that the logic itself could all be done chemically — and Bennett explicitly says so (protein cascades already did "do this, not that"). So what neurons added wasn't new *computation* but rather computation at a new **spatial and temporal scale**. Bennett emphasizes speed, but I think the full picture is speed *and* range. A coral polyp's catch-and-swallow reflex requires coordinating muscles across its whole body within seconds — that's a spatiotemporal coordination problem that chemical diffusion can't solve.

So neurons aren't a new kind of logic. They're a new communication medium that makes existing logic work at the scale of macroscopic bodies, fast enough for active hunting.

---

**You**

i see, so there are physical limits to chemical signaling pathways that make them not work for active hunting? is that actually true, there are no animals that use only chemical pathways for this?

---

**Claude**

As far as we know, no. Every animal with muscles also has neurons. There are no known animals that do fast coordinated movement via chemical signaling alone.

The closest counterpoint is **sponges** (Porifera) — they have no neurons at all, and they do have contractile cells that can slowly squeeze to push water through their body. But this is extremely slow, not coordinated across the body in any precise way, and not used for hunting. Sponges are filter feeders.

That said, I want to be precise about the claim. This is an **empirical observation**, not a proven physical impossibility. It's conceivable that some alternative biochemical architecture could achieve fast long-range coordination without electrical signaling. But evolution never found one (or if it did, it was outcompeted). The physics of chemical diffusion makes it very hard: diffusion time scales with the *square* of distance, so doubling the body size quadruples the communication delay. Electrical propagation along an axon doesn't have this problem.

So the honest framing is: the physics of diffusion creates a severe scaling barrier, and no known organism has overcome it for fast coordinated movement without neurons. That's strong evidence, but it's "no known counterexample" rather than "proven impossible."

---

**You**

I see. Worth making a card or two from this last bit of discussion. Suggest a couple based on salience to my research interests / the questions I asked here

---

**Claude**

```
Chemical diffusion time scales with the {{c1::square}} of distance, creating a severe barrier for fast coordination in macroscopic organisms. Electrical propagation along axons avoids this because {{c2::all-or-nothing spikes maintain signal integrity regardless of distance}}.
```

```
Neurons did not add new computational logic — {{c1::protein cascades in single cells}} already performed equivalent operations. What neurons added was a communication medium that made existing logic work at the {{c2::spatial and temporal scale}} required for macroscopic active hunting.
```

How are those?

---

**You**

Any animal with stomachs that doesn’t have neurons?

---

**Claude**

Not as far as we know. Bennett's claim that the triad is inseparable appears to hold. Sponges lack neurons but also lack a true digestive cavity — they filter-feed by passing water through channels. Placozoa (the simplest known animals) lack neurons, muscles, *and* a digestive cavity — they do external digestion by crawling over food and secreting enzymes underneath themselves, which is actually closer to the fungal strategy.

So the pattern is consistent: every known animal with a true stomach also has neurons and muscles. No exceptions.

---

**You**

Do these secretory cells / whatever chemical signaling cells we know about also do things like adaptation etc? Or I guess thy could solve the problem adaptation solves in a different way bc they don’t use all or nothing spikes

---

**Claude**

Exactly right that they don't face the squishing problem in the same form, since there's no rate code to squish into. But adaptation as a *general principle* — responding to relative changes rather than absolute values — is ancient and ubiquitous in biology, well predating neurons.

The classic example is **bacterial chemotaxis**. E. coli responds to *changes* in chemical concentration, not absolute concentration. If you put it in a uniform field of attractant, it adapts within seconds and stops responding. It only reacts to gradients — relative differences. The molecular mechanism is well understood: it involves methylation of receptors that resets their sensitivity baseline.

More broadly, **receptor desensitization** is everywhere in cell biology. G-protein coupled receptors (which predate neurons) down-regulate when chronically stimulated — receptors get internalized, downstream pathways saturate, etc. This is the same functional principle as neural adaptation (track relative changes, ignore stable baselines) implemented in purely chemical machinery.

So the computational principle "encode changes, not absolutes" appears to be a deep and very old solution to sensing in a world with huge dynamic range. Neurons inherited this principle and implemented it in the medium of firing rates, but it wasn't their invention.

---

**You**

Is there \_anything\_ specific computationally to neurons besides the speed/range bits?

---

**Claude**

This is the right question to push on. I think the honest answer is: at the level of individual computational primitives, **not really**. Thresholding, excitation, inhibition, adaptation, graded signal encoding — all exist in chemical signaling systems.

What *is* genuinely new is the **architecture** that neurons make possible. A neuron can receive inputs from thousands of other neurons and send to thousands more — massive fan-in and fan-out. Each of those connections (synapses) can be independently strong or weak. This creates a combinatorial space for computation that linear chemical cascades don't have. A protein signaling pathway is essentially a fixed chain; a neural network is a reconfigurable graph.

And then there's **synaptic plasticity** — the ability to modify individual connection strengths based on activity — which Bennett will get to in later chapters. This is arguably the really big deal. It's what makes neural networks *learnable*. Chemical systems have crude analogs (receptor up/down-regulation), but independently tunable pairwise connection weights across a massive network is a qualitatively different regime.

So: neurons didn't invent new computational primitives. They invented a new **network architecture** — many discrete units, high connectivity, independently modifiable weights — that, combined with speed and range, opened up a computational space that chemical cascades couldn't access.

This connects directly to your research interests — the question of what local learning rules *do* with that architecture is essentially the question of how the brain exploits the space neurons made possible.

---

**You**

Interesting. So there is no notion even of “local learning rules” in chemical signaling pathways?

---

**Claude**

There are things that *rhyme* with learning, but I think the answer is substantively no, for a specific structural reason.

A local learning rule like Hebbian plasticity requires three things: a **pairwise connection** between two specific units, **local access** to both units' activity states at that connection, and **modifiability** of that connection's strength based on their joint activity.

A synapse is exactly this structure — it's a physical locus where the presynaptic neuron's activity (spike → neurotransmitter release) and the postsynaptic neuron's activity (depolarization) are both locally available, and the synapse's strength can change based on their correlation.

Chemical signaling pathways don't have this. Receptor desensitization adjusts a single element's sensitivity — that's self-tuning, not relational learning. Gene regulatory networks can be modified epigenetically, but slowly and without pairwise activity-dependent specificity. The immune system does something learning-like (clonal selection), but that's population-level selection, not connection weight modification.

The fundamental issue is that **diffuse chemical signaling lacks a privileged structure where two specific cells' activity states converge**. Without that, you can't have "if A and B are active together, strengthen the link between them." You need something like a synapse for that.

So this might actually be the deepest computational novelty of neurons — not any single primitive, but the synapse as a substrate for pairwise, activity-dependent learning. Worth a card?

---

**You**

Yes, though look into how settled the literature is around these points first

---

**Claude**

Good push. Let me think about this honestly.

The core claim — that synapses uniquely provide a locus for pairwise activity-dependent plasticity — is the standard computational neuroscience framing, and it's broadly accepted. But there's at least one notable challenge to the strong version of the claim.

**Physarum polycephalum** (slime mold) has no neurons, but its tube network exhibits something structurally similar to Hebbian learning: tubes that carry more cytoplasmic flow thicken, tubes with less flow shrink. This is a local, activity-dependent modification of connection strength in a network — without any neurons or synapses. It's purely physical/biochemical. Physarum can solve mazes and approximate shortest-path networks this way.

So the strong claim "you need synapses for pairwise activity-dependent learning" has at least one counterexample in spirit. The weaker but more defensible claim is something like: neurons and synapses enable pairwise activity-dependent learning at a **speed, scale, and combinatorial richness** that no known chemical system matches. The same "speed and scale" story that applies to neurons generally.

The immunological synapse is another edge case — T-cells form structured contact points with antigen-presenting cells where signals from both sides are integrated. But this doesn't modify a persistent connection weight, so it's less analogous.

So I'd revise the card to something like:

```
The synapse may be the key computational novelty of neurons: a physical locus where {{c1::two specific cells' activity states converge}} and {{c2::connection strength can be modified based on their joint activity}}. Non-neural analogs exist (e.g., Physarum flow networks) but lack the {{c3::speed, scale, and combinatorial richness}} of synaptic networks.
```

Fair?

---

**You**

Do a deep review to accurately capture how settled the contents of this card are

---

**Claude**

The question is clear — I'll dive into a deep review of how well-supported the claim is that synapses are the key computational novelty of neurons, including the status of non-neural analogs like Physarum.

---

**You**

Do a deep review to accurately capture how settled the contents of the below cards that you suggested are

Chemical diffusion time scales with the {{c1::square}} of distance, creating a severe barrier for fast coordination in macroscopic organisms. Electrical propagation along axons avoids this because {{c2::all-or-nothing spikes maintain signal integrity regardless of distance}}.

Neurons did not add new computational logic — {{c1::protein cascades in single cells}} already performed equivalent operations. What neurons added was a communication medium that made existing logic work at the {{c2::spatial and temporal scale}} required for macroscopic active hunting.

The three inseparable features that bind all animals together and separate them from all other kingdoms of life are {{c1::gastrulation (stomach)}}, {{c2::neurons}}, and {{c3::muscles}}.

---

**Claude**

These are clear enough to research directly — let me dig in.

---

**You**

update the cards (chemical diffusion, synapse, computational logic, and inseparable features) that i had you do deep research on in my last two messages based on the results of the research (read it carefully)

---

**Claude**

Good — let me reread the key findings carefully for each.

**Chemical diffusion card** — The x² scaling is correct physics for free diffusion, but in biological tissue, degradation and uptake shift the effective regime to exponential decay. And electrical propagation works via active regeneration at nodes of Ranvier, not passive "signal integrity." Updated:

```
Free diffusion time scales with the {{c1::square}} of distance (t ~ x²/2D), but in biological tissue, enzymatic degradation and reuptake create {{c2::exponential}} spatial decay profiles, making the barrier even steeper at long range.
```

```
Electrical propagation along axons avoids diffusion scaling not through passive signal integrity but through {{c1::active regeneration}} — voltage-gated channels at {{c2::nodes of Ranvier}} regenerate the action potential from scratch at each node.
```

**Synapse card** — Pairwise activity-dependent plasticity is genuinely unique to synapses (Physarum is flow reinforcement, not Hebbian). But "speed, scale, and combinatorial richness" is not an established framing, and evolutionary biologists don't converge on plasticity alone as THE key innovation — it's part of a bundle. Updated:

```
The synapse is the only known biological structure where {{c1::two specific cells' activity states converge}} and {{c2::connection strength can be modified based on their joint activity}}. No non-neural system convincingly replicates this (Physarum tube adaptation responds to {{c3::local flow magnitude, not correlated activity of two connected nodes}}).
```

```
Evolutionary biologists identify a bundle of synaptic innovations — {{c1::speed}}, {{c2::spatial precision/directionality}}, {{c3::scalability beyond diffusion limits}}, and {{c4::activity-dependent plasticity}} — rather than any single property as the key novelty of neurons.
```

**Computational logic card** — Individual primitives (excitation, inhibition, thresholding, adaptation) are well-documented in unicellular organisms. But claiming neurons added "no new computational logic" overstates it — network-level computation, synaptic plasticity, and millisecond temporal coding are genuinely novel. Updated:

```
Individual computational primitives — excitation, inhibition, thresholding, adaptation, signal integration — all {{c1::predate neurons}} and exist in unicellular protein signaling networks (e.g., bacterial chemotaxis implements {{c2::perfect adaptation via integral feedback control}}).
```

```
What neurons genuinely added beyond ancient computational primitives was a new {{c1::network architecture}}: connected cells enabling recurrent dynamics, lateral inhibition, coincidence detection across spatially separated inputs, and {{c2::pairwise activity-dependent plasticity (learning)}}.
```

**Inseparable features card** — Bennett's triad is factually incorrect as stated. Sponges and placozoans are animals that lack all three. The triad describes Eumetazoa at best, not Metazoa. Updated:

```
Bennett claims gastrulation, neurons, and muscles are inseparable features defining all animals, but this is {{c1::falsified by sponges and placozoans}}, which are animals lacking all three. The triad more accurately describes {{c2::Eumetazoa (cnidarians + bilaterians)}}, not Metazoa.
```

```
Standard evolutionary biology defines animals (Metazoa) not by neurons/muscles/stomachs but by {{c1::multicellularity with collagen-based extracellular matrix}}, {{c2::unique cell junctions}}, and {{c3::blastula-stage embryonic development}}.
```

How do those look?

---

**Claude**

A Brief History Of Intelligence