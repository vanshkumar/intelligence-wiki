---
title: "Null Space Coding"
type: mechanism
aliases: ["output-null dimensions", "null space preparation", "communication subspaces"]
tags: [dynamical-systems, motor-cortex, linear-algebra, ctd, inter-area-communication]
source_count: 1
last_updated: 2026-04-14
level: systems
---

**Null space coding** is the use of the null space of a downstream readout to carry information that does not propagate to the downstream region. For a linear readout `y = Cx`, the null space of `C` is the set of states `x` for which `Cx = 0` — information lives in those states, but the readout is blind to it. This allows a circuit to compute internally without driving a downstream stage.

Introduced into systems neuroscience as the solution to an open puzzle about motor preparation: preparatory activity in motor cortex is large and tuned to upcoming movement, yet it does not produce movement. Kaufman et al. (2014) showed that preparatory activity is preferentially structured to lie in the null space of the motor-output readout to muscles — the **output-null subspace**. Movement begins when activity rotates from output-null into **output-potent** dimensions. Reviewed extensively in [[vyas-2020-computation-through-dynamics|Vyas et al. (2020)]].

## Why the Mechanism Matters

The general computational problem it solves: a circuit needs to compute something (prepare a movement, maintain a memory, integrate evidence) without the partial results of that computation driving action. Classical solutions — subthreshold activity, inhibitory gating — have well-known limitations:
- **Subthreshold**: activity must be small, limiting representational richness.
- **Inhibitory gating**: requires a separate mechanism to release the gate at the right time.

Null space coding does it with linear algebra: the computation happens along dimensions the readout cannot see. No amplitude limit, no gate — just a geometric arrangement of activity relative to readout weights.

## Evidence Across Cases

- **Motor preparation (Kaufman 2014, Elsayed 2016)**. Preparatory M1 / PMd activity is strongly biased toward output-null dimensions (muscle readout). Movement activity fills output-potent dimensions.
- **BCI flexibility (Stavisky 2017a)**. When the experimenter controls the output dimensions in a BCI, the brain isolates error-related signals in decoder-null dimensions. This is the clearest general test: whichever dimensions are currently the "output," the null space gets repurposed for accessory computation.
- **Optogenetic perturbation of ALM (Li 2016)**. After perturbation, preparatory activity in mouse anterior lateral motor cortex is restored along behaviorally relevant dimensions but not along non-informative dimensions. The restoration is selective to the dimensions that matter for the downstream readout.
- **Inter-area communication (Semedo 2019)**. Generalized to communication between brain regions: the **communication subspace** between two areas is a low-dimensional subspace of the sending area's activity that actually drives the receiving area. Activity orthogonal to this subspace stays in the sending area. The output-null / output-potent split in motor cortex is one instance of a broader principle.

## Relation to Manifolds and the CTD Framework

Null space coding complements [[Neural Manifolds|manifold structure]] and [[Computation Through Dynamics|CTD]] in the following way:
- **Manifolds** say where the population state actually goes (the low-dimensional subspace where variance concentrates).
- **Output-null / output-potent decomposition** says how that subspace is partitioned relative to a downstream readout.
- **CTD dynamics** govern the trajectory through the subspace, including the rotation from null into potent that initiates movement.

The same geometric move — partitioning the space by readout — also structures **BCI learning**: in Sadtler 2014 and Golub 2018 (see [[Neural Manifolds]]), perturbations that required off-manifold dynamics were learnable only slowly, consistent with the intrinsic manifold being a real constraint and learning having to work within its subspace structure.

## A Control-Theoretic Reading

Null space coding is a clean instance of a control-theoretic design principle: **separate internal state from actuation**. A good controller maintains richer internal state than it outputs; the mapping from state to output is intentionally lossy so that internal computation can proceed without commitment. Biology implements this lossy mapping with the geometry of readout weights rather than with a discrete gate.

This also reframes one interpretation of the closed-loop sensorimotor control framing of this wiki: the "control" in control-theoretic isn't the full population state but its projection through the readout. Most of the population's work lies in dimensions the actuator cannot see.

## Open Questions

- **Is null-space structure learned or given?** If the readout weights `C` are fixed early in development, the brain learns to place preparation in the null space. If `C` and the cortical dynamics co-adapt, the separation is an emergent property of joint optimization.
- **How general is the communication-subspace picture (Semedo 2019)?** Does every inter-area connection factor cleanly into communication vs. private subspaces?
- **What roles do non-output-potent *and* non-output-null dimensions play?** Some dimensions might not be null for the primary readout but also not potent — used for computation that neither drives the main output nor is strictly hidden from it.

## Sources

- [[vyas-2020-computation-through-dynamics|Vyas, Golub, Sussillo & Shenoy (2020)]] — review; Kaufman 2014, Elsayed 2016, Stavisky 2017a, Li 2016, Semedo 2019 cited for output-null preparation and communication subspaces.
