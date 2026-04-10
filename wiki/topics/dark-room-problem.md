---
title: "Dark Room Problem"
type: concept
aliases: ["dark room objection"]
tags: [predictive-coding, active-inference, philosophy]
source_count: 1
last_updated: 2026-04-10
confidence: established
---

The dark room problem is a well-known objection to [[Predictive Coding]] and prediction error minimization theories of the brain: if the brain's goal is to minimize prediction error, why doesn't it simply seek out maximally predictable environments — sitting in a dark room doing nothing, where prediction error is always zero?

## The Problem

Any agent that minimizes prediction error has a trivial solution available: reduce activity to zero, or stay in an environment where nothing happens. This achieves zero prediction error with no effort. Yet real organisms actively explore, seek novelty, and engage with complex, unpredictable environments.

## Proposed Solutions

**Active inference**: Actions are themselves a way to minimize prediction error — the agent changes the world to match its predictions rather than just updating beliefs. However, this requires additional components (prior preferences, curiosity drives, or separate action selection modules), which means the agent isn't operating purely on prediction error minimization.

**PaN (Prediction and Noise)**: [[li-2024-prediction-noise-reward|Li et al. (2024)]] proposes that [[Neural Noise]] solves the dark room problem without additional components. The key insight: the dark room (zero-signal state) is **unstable under noise** because all fixed points lie on the decision boundary. Noise kicks the network out of the dark room, and rewarding states are stable attractors that resist perturbation. The agent doesn't *choose* to leave the dark room — it *can't stay* there because noise keeps destabilizing it.

This is a notably parsimonious solution: it requires no curiosity drive, no prior preferences, no separate action module — just the noise that's already inherent in any biological neural system.

## Sources

- [[li-2024-prediction-noise-reward|Li et al. (2024)]] — noise as a solution to the dark room problem
