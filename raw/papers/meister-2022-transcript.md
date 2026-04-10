---
title: "Learning, fast and slow"
source: "https://claude.ai/chat/fd06ede6-b76c-48db-9b31-a6a05ffd6251"
author:
published:
created: 2026-04-10
description: "Claude conversation with 34 messages"
tags:
  - "clippings"
---
**Claude**

What's this paper covering, and how does it connect to what you've been working through?

---

**You**

Informal survey of learning rates of different animals across different tasks. Makes the point that often lab tasks aren’t relevant to animals real lives especially given their life spans, and so the “slow learning” we are studying there may not resemble real animal learning nor human like slow learning. Also notes that studying why some tasks are learned quickly vs slowly will probably teach us something about the brain.

---

**Claude**

Good. What's Meister's proposed explanation for *why* some tasks are fast and others slow? Not just the observation — the mechanism.

---

**You**

The neural code needed to represent and accomplish those tasks is something the animal is already intimately familiar with

---

**Claude**

More precise: what property of that neural code makes it ready for fast learning, and why does that property matter given the constraints on biological synaptic plasticity?

---

**You**

That neural code already has a sparse high dimensional representation of aspects relevant to the task so it can quickly classify between those aspects. Synaptic plasticity is relatively slow so building up a sparse high dim representation take a lot of time

---

**Claude**

Careful — synaptic plasticity itself isn't slow. Fear conditioning modifies synapses in one trial. The constraint is more specific. What exactly about biological plasticity makes the *representation* matter so much?

---

**You**

right. if there is a sparse high dimensional representation then the number of synapses that need to change is much smaller vs if there is not yet such a code?

---

**Claude**

That's part of it, but the deeper point is about what each synapse can *see*. What are the only variables a biological synapse has access to when deciding how to change?

---

**You**

pre and post synaptic activations (and neuromodulators). i guess the idea is that because the synaptic learning rules are mostly local, the representation matters a lot? don't quite see intuitively why tho

---

**Claude**

Right, you're circling it. Think about it concretely. Two stimuli, distributed code: stimulus A activates neurons {1, 3, 7}, stimulus B activates {1, 4, 7}. You want A→action1, B→action2. Hebbian learning strengthens synapses where pre and post fire together.

When you train A→action1, what happens to the synapses from neurons 1 and 7? And then what happens when stimulus B comes along?

---

**You**

1->3 and 3->7 strenghten in the case of A, and then 1->4 and 4->7 strengthen in the case of B. so 3 vs 4 are discriminative

---

**Claude**

You're mixing up the architecture. Go back to Meister's Figure 3: there are stimulus neurons (S) and action neurons (A), connected all-to-all with Hebbian synapses. So the synapses are from S-neurons to A-neurons.

Now: stimulus A activates S-neurons {1, 3, 7}. You pair it with action1, which activates A-neuron 1. What synapses get strengthened? And then stimulus B activates {1, 4, 7}, paired with action2 (A-neuron 2). What's the problem when you later present stimulus B?

---

**You**

1->A, 3->A, 7->A get strengthened. the issue is that 1 and 7 will point towards action-A when stimulus B is presented

---

**Claude**

Exactly. That's the interference problem. With a sparse code (one-hot), stimulus A only activates S-neuron 1, stimulus B only activates S-neuron 2 — no overlap, no interference, perfect recall after one shot.

So now connect it back: the constraint isn't that synapses are slow to change. It's that each synapse only sees local activity. With a distributed code, a single synapse participates in multiple associations and can't tell them apart. The synapse from neuron 1 can't know whether it fired because of stimulus A or B — it just sees "I fired, post fired, strengthen." Sparse codes avoid this entirely by ensuring each synapse only participates in one association.

Now the key question: where do these sparse codes come from? Meister gives two sources. What are they, and why does the second one create the slow-learning regime?

---

**You**

first is genetic (or early development). second is built up from plasticity throughout life, and it's slow because a whole new sparse distributed representation has to be built up

---

**Claude**

Right. And Meister adds a complementary psychological-level explanation too — the Bayesian prior argument. How does that account relate to the neural one? Are they independent explanations or does one underlie the other?

---

**You**

it underlies the neural code explanation – genetics/early development gives the brain priors, in the form of sparse distributed representations, for certain tasks/objects/etc

---

**Claude**

Meister actually argues the reverse direction: the neural explanation underlies the psychological one. The animal "not believing" the task contingency (low Bayesian prior) might *be* the fact that there's no sparse code for those events. No sparse representation → no efficient way to detect and reinforce that correlation → the contingency looks implausible from the brain's perspective.

Does that distinction matter, or is it just semantics?

---

**You**

distinction doesn't really matter, at least in the genetic/evolutionary case – kind of chicken and egg as to whether the sparse distributed code came first or whether figuring out what useful priors are came first. they're kind of the same thing over a long time span / in that context

i think the same is true in the early development / within life plasticity case as well

---

**Claude**

Fair point — the prior *is* the representation, viewed from different levels. Good.

Let me push on one more thing before we card. Meister makes a specific experimental prediction about slow-learning tasks. What is it, and why would it be a strong test of his framework?

---

**You**

don't quite recall, but i suspect it's something like – slow learning tasks that closely mimic something an animal actually has to do in the wild will be learned more rapidly? i guess in that case it's probably more just a fast learning task tho

---

**Claude**

Different prediction. He says: expose the animal to the abstract stimuli and actions from a slow 2AFC task *without* any reinforcement contingencies — just let it experience them freely for weeks. Then add the contingencies. His prediction: (1) concept cells specific to those task events should emerge during exposure, and (2) the task should then be learned much faster.

Why is this a strong test? What would it rule out if confirmed?

---

**You**

ah right. if this is confirmed it would tell us that the reinforcement/reward part of 2AFC doesn't actually speed up creating of the representation/ the learning (or at least would tell us exactly how much it does do so )

make sure you invoke the anki-cards skill for making the actual cards

---

**Claude**

Close but sharper: the prediction specifically tests whether the bottleneck in slow learning is *building the sparse representation* (unsupervised) versus *forming the stimulus-action association* (reinforcement-dependent). If the task is learned fast after passive exposure, the bottleneck was representation, not association. That's the core claim — association via Hebbian learning is fast once the code is right; the slow part is getting the code right.

OK, I think you've got the key concepts. Let me read the card skill and then we'll draft.

---

**You**

looks good

---

**Claude**

13 cards. This paper connects nicely to your genome-encoding-cost-functions insight — the sparse code *is* the prior, and evolution invests complexity into building the right representations rather than the learning algorithm itself.

---

**You**

Hmm this is written confusingly - “which one” is odd in the answer

---

**Claude**

You're right. How about:

```
Q: Why does a distributed (non-sparse) neural code cause interference under Hebbian learning?
A: Overlapping activations mean a single synapse gets strengthened by multiple unrelated associations
```

---

**You**

Animal can’t learn a sparse code in a supervised (reinforced) way in its lifetime per meister?

---

**Claude**

Not quite. Animals in slow 2AFC tasks *do* eventually learn with reinforcement — it just takes thousands of trials. Meister's claim is that the representation-building part *can* happen unsupervised, not that it *can't* happen with reinforcement. His prediction is that passive exposure should be sufficient for the representation, making subsequent reinforced learning fast. But he doesn't rule out that reinforcement also contributes to shaping the code — the experiment would help tease apart the two contributions.

---

**You**

Specifically in the context of the card - it says genetics or unsupervised learning

---

**Claude**

Good catch. The card should say:

```
Q: What are the two sources of sparse codes Meister emphasizes?
A: Genetic/evolutionary hardwiring, and unsupervised learning from lifetime experience
```

Adding "emphasizes" makes it clear these are the two he highlights, not an exhaustive list. He's silent on whether reinforcement also shapes representations — that's partly what his proposed experiment would test.

---

**Claude**

How Do We Learn?