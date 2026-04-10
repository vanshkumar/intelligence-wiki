---
title: "Chapter 1"
source: "https://claude.ai/chat/2c9e126e-4640-47cb-beab-e937c7db9912"
author:
published:
created: 2026-04-10
description: "Claude conversation with 25 messages"
tags:
  - "clippings"
---
**You**

the project files contain a textbook split into chapters. let's start with chapter 1.

---

**Claude**

The PDF didn't render as text directly. Let me extract it properly.

---

**You**

1. membrane potential is the potential difference between the inside and outside of the cell (separated by the cell membrane). at rest means there are ions/charge built up on one side vs the other (= resting potential) that want to flow one way but don't for some reason (counteracted by active ion pumps, concentration gradient, etc)
2. resting potential = battery, membrane = capacitor, the resistor represents the conductance/resistance of the membrane (how much it lets ions through)
3. tau\_m du/dt = -(u(t) - u\_rest) + RI(t). the sign of u(t)-u\_rest is negative because the potential wants to return back to its resting value. RI(t) sign is positive because that is the driving input current that pushes the membrane potential away from rest
4. it's called leaky because incoming current "leaks" out constnatly as the membrane potential decays exponentially to rest in the absence of current. if there were no leak then... i guess the membrane potential would just shoot off to infinity with any constant nonzero input current

---

**Claude**

Solid across the board. A few refinements:

On (1) — good. The chapter just takes the resting potential (~-65mV) as given and inserts a battery to account for it. The ionic mechanisms behind it come in Chapter 2.

On (4) — your intuition is right but let's sharpen it. If R → ∞, what happens to τ\_m = RC? And what does the differential equation reduce to? Write it out explicitly — the resulting object has a standard name that contrasts with "leaky integrator."

**Next round, going deeper into the math:**

1. The chapter derives the "free solution" (Eq. 1.6) — exponential decay from an initial condition with no input. Then it considers a constant current pulse of duration Δ and derives Eq. (1.7). Explain in your own words why, if the current never stopped, the membrane potential would approach u\_rest + RI\_0. Don't just say "steady state" — explain it in terms of what's happening to the two currents (resistive and capacitive) in the circuit.
2. The Dirac delta section is important. The chapter takes a current pulse of amplitude I\_0 = q/Δ and lets Δ → 0. Why does the voltage deflection at the end of the pulse stay the same regardless of how short we make the pulse? What's the physical content of this result?
3. What are the two components of the leaky integrate-and-fire model? (Not the circuit components — the two conceptual/mathematical pieces that together define the model's dynamics.)

---

**You**

1. ah yea diff eq becomes du/dt = I(t)/C, so fully driven by the input current
2. capacitor would fill up so only curernt would be thru the resistor hence potential would be battery (u\_rest) + RI\_0
3. the voltage effect stays the same regarldess of how short we make it because the delta\_t bit cancels. the phsyical content is that the voltage effect of a current pulse depends on the total charge delivered, not the time within which it is delivered (for times much shorter than tau\_m)
4. leaky integration part: incoming presynaptic spikes are instantanesous charge increases that linearly sum, while the membrane potential also has an ongoing exponential decay back to rest. fire part: once voltage crosses a threshold, an action potential fires – the form of the action potential isn't represented, it's just a dirac delta at the firing time. after that the membrane potential resets immediately to a value below the resting potential

---

**Claude**

Good. Two corrections:

On the R → ∞ point: yes, du/dt = I(t)/C. This is a **perfect integrator** — it accumulates charge forever with no decay. That's the contrast: leaky integrator vs. perfect integrator. And τ\_m = RC → ∞ means the decay timescale becomes infinite, which is exactly "no decay."

On (4): small but important precision issue. The chapter specifies u\_r < ϑ (reset below threshold), not necessarily below u\_rest. In Fig. 1.9a they happen to set u\_r = u\_rest, but that's a choice. Also, the "integration" part isn't specific to instantaneous delta-function inputs — it's the linear ODE integrating any input current I(t), whether that's an experimenter's injected current, synaptic currents, or whatever. The delta-function representation of spikes is a separate modeling choice.

**Pushing further into the key mathematical ideas:**

1. The chapter presents two equivalent "pictures" of the LIF model: the differential equation picture (Eq. 1.5 + threshold + reset) and the filter/convolution picture (Eq. 1.22). In the filter picture, what do the two filters η and κ each represent, and what are they each convolved with?
2. Why does convolution with κ turn into simple multiplication in the Fourier domain? Don't just state the convolution theorem — explain the calculation step that makes it work (hint: it's a change of variables).
3. What is the physical meaning of |κ̂(ω)| decreasing as 1/ω at high frequencies?

---

**You**

Hmm I skipped the starred advanced sections (as recommended on first time thru the book), not sure if these are in there?

---

**Claude**

Fair enough — sections 1.3.4, 1.3.5, and 1.3.6 are all starred. We can come back to those when you're ready. Let's stay with the non-starred material.

We've covered the RC circuit, the ODE, free solution, delta function, and the two components of the LIF model. Let me ask about the rest:

1. The chapter describes linear summation of PSPs (Eq. 1.2) — multiple presynaptic spikes add up linearly. Under what condition does this linearity break down, and what happens when it does?
2. Section 1.4 catalogs several limitations of the basic LIF model. Pick the one you think is most important for your research interests (local learning rules, plasticity, behavior) and explain what the limitation is and why it matters.
3. The adaptive threshold model (Eq. 1.34) is presented as a fix for one of these limitations. In your own words, what does that equation say? What's the dynamics of ϑ(t)?

---

**You**

1. breaks down when there is an ongoing/recent action potential, in which case all the ion channels are in use so presynaptic spikes have no effect
2. shunting inhibition is a very nonlinear behavior where just a few inhibitory inputs can erase the input from a ton of excitatory synaphses. this seems like it could be a crucial mechanism whereby the choice of whether a neuron fires or not could be switched between on/off rapidly
3. the firing threshold itself has an exponential relaxation in the absence of input + increase by some degree in the case of input (spikes), which models adaptation

---

**Claude**

Good, but let me tighten each one.

On (8): You're describing the refractory period / conductance changes after a spike (section 1.4.3), which is one reason linearity breaks down. But the chapter's main point is simpler — linearity breaks down when the summed PSPs push the membrane potential to threshold ϑ, triggering the action potential. That's the fundamental nonlinearity of the neuron: linear integration below threshold, then a qualitatively different event (spike) at threshold. The conductance change story is a secondary, more subtle nonlinearity.

On (9): Good observation about shunting inhibition. One precision fix: the chapter explains it through reversal potentials. The PSC amplitude is proportional to (u₀ - E\_syn). For inhibitory synapses, E\_syn is close to u\_rest, so when the neuron is near rest, inhibitory input does almost nothing to the voltage — but it massively increases local conductance, which divides (shunts) excitatory currents. It's a multiplicative/divisive operation, not additive. That's what makes it so powerful and so different from the linear picture.

On (10): Right idea, but be precise about what "input" means here. The threshold ϑ(t) doesn't increase from external input — it increases by a fixed amount θ each time *the neuron itself fires*. Between spikes, it relaxes back to ϑ₀. So neurons that fire rapidly accumulate a higher threshold, making the next spike harder to trigger. That's adaptation.

I think we've covered the chapter well. Are you ready for cards, or do you want to dig into anything further first?

---

**You**

on the shunting point - the idea is that increasing local conductance allows the potential that is built up from a ton of other excitatory synapses (ions) a pathway to exit the cell & thereby decrease the potential? and it's a division because a 2x increase in local conductance will halve the amount of remaining potential?

---

**Claude**

Close but not quite. The mechanism isn't about draining charge that's already built up — it's about diverting incoming excitatory current before it can charge the membrane.

Think back to the RC circuit. In steady state, all current flows through resistors (capacitor is fully charged). If you add another resistor in parallel (which is what opening inhibitory channels does), the total resistance drops. Now the same excitatory current produces a smaller voltage deflection because V = I × R\_total and R\_total just got smaller.

The division comes from the steady-state voltage being a conductance-weighted average of reversal potentials:

u = (g\_exc · E\_exc + g\_inh · E\_inh + g\_leak · E\_leak) / (g\_exc + g\_inh + g\_leak)

Adding g\_inh increases the denominator. That's the division — the excitatory contribution gets divided by a larger total conductance. And because E\_inh ≈ E\_leak ≈ u\_rest, the inhibitory conductance barely changes the numerator. It acts almost purely on the denominator.

So it's not "letting built-up charge escape." It's "making it harder for new excitatory current to build up voltage in the first place." A current divider, not a drain.

Does that distinction land? If so, we can move to cards.

---

**You**

ok so \* inhibitory synapses increase local conductance (lower resistance) \* any incoming excitatory synapses then have a higher conductance to deal with, which means that the potential they are able to build up is less because V = IR, so basically the current cause by an excitatory synapse is decreases

that makes sense mathematically.. but physically speaking what's happening? say membrane potential is roughly at rest after a few inhibitory synapses have come in. so excitatory synapses will cause a positive current because reversal potential is ~0. physically, excitatory synapses will release some transmitter to cause some ion channels to open up & allow say sodium ions to flow into the cell. won't the increase in local conductance that the inhibotry synapses caused result in \_even more\_ sodium ions flowing into the cell because the conductance is higher/resistance is lower? i guess the way that could not be the case is via the reversal potential of these inihibitory synapses which is like -75mv. so because \_specifically\_ the inihibotry synapse specific ion channels are open, they cause a negative current (sodium ions to flow out) which allows a separate path for the incoming sodium ions from the excitatory syanpse ion channels to flow out. i still don't quite see why this is a division.. i guess the idea is if you double the conducitivity of these inhiibtory syanpse ion channels, they will take away half the excitatory synapse current? i think i am missing some key intuition here

---

**Claude**

You're asking exactly the right question. Let me untangle the physical picture.

First, an ion species correction: inhibitory synapses typically open chloride (Cl⁻) or potassium (K⁺) channels, not sodium. Excitatory synapses open channels permeable to Na⁺ (and some K⁺). So these are different channels carrying different ions.

Now the physical picture. Imagine the membrane is near rest (-65mV) with a bunch of inhibitory Cl⁻ channels open (E\_inh ≈ -75mV):

1. Excitatory synapse opens → Na⁺ flows in → membrane starts to depolarize slightly, say toward -60mV
2. Now the voltage (-60mV) is further from E\_inh (-75mV) than it was before. The driving force across those open inhibitory channels just increased — so Cl⁻ flows in (or K⁺ flows out), opposing the depolarization
3. The more the excitatory input tries to depolarize, the harder the inhibitory channels push back

It's a negative feedback loop. The inhibitory channels act like a conductance clamp near E\_inh. They don't do much at rest (small driving force), but they actively resist any attempt to move the voltage away from E\_inh.

The division: think of the excitatory Na⁺ current flowing in. That current has to go somewhere — some of it charges the membrane capacitor (which is what actually changes the voltage), and some of it flows right back out through the open inhibitory channels. More open inhibitory channels = more of the excitatory current gets shunted out before it ever charges the membrane. The voltage change is roughly I\_exc / g\_total, and g\_total includes g\_inh. That's the division.

Does the current-divider picture make sense now?

---

**You**

hmm, but what's actually happening physically with the "current" if what's coming in is sodium ions and what's going out is a different kind of ion

---

**Claude**

The capacitor doesn't care about ion identity. It only sees net charge on the membrane.

Na⁺ flows in through excitatory channels → positive charge added to the inside of the membrane. K⁺ flows out through inhibitory channels → positive charge removed from the inside of the membrane. From the capacitor's perspective, these are just positive and negative currents. C dV/dt = net current = I\_in - I\_out.

So physically: Na⁺ enters, tries to charge the membrane positive. Simultaneously, K⁺ leaves (or Cl⁻ enters), removing positive charge (or adding negative charge) from the inside. The membrane voltage only changes according to the *net* charge accumulation on the capacitor, regardless of which ions carried it.

That's why the circuit model works despite multiple ion species. Current is charge per unit time. A Na⁺ ion crossing inward contributes exactly +1 elementary charge. A K⁺ ion crossing outward removes exactly +1 elementary charge. The membrane doesn't know the difference.

The division then follows straightforwardly: more open inhibitory channels → more K⁺/Cl⁻ current opposing the Na⁺ current → less net current reaching the capacitor → less voltage change. And the opposing current scales with conductance, giving you the division.

---

**You**

i see, ok make sense

want to think about what would be useful to internalize here before generating cards – i suspect it's more on the qualitative side of things? but some of these equations are fairly basic so internalizing them would be good too

clearly i am also lacking some intuition around what's going on here so building that via cards would be quite useful

---

**Claude**

Good instinct to filter before generating. Let me help you think about what's actually worth internalizing here.

**Probably worth carding:**

- The RC circuit ↔ membrane correspondence (you'll reference this constantly)
- The ODE itself and what each term means physically
- Exponential relaxation as the free solution — you flagged this in Chapter 2 as a universal pattern, so anchoring it here where it first appears is valuable
- Perfect integrator vs leaky integrator (what leak buys you)
- Shunting inhibition as conductance-based division, not additive subtraction — this is genuinely non-obvious and you just worked hard to understand it
- The fundamental nonlinearity: linear below threshold, qualitative event at threshold
- Adaptation via dynamic threshold — this connects directly to neural coding questions

**Probably not worth carding:**

- Anatomy (dendrites/soma/axon) — obvious to you
- Spike train definition as sum of deltas — notation you won't forget
- Fourier / filter sections — skipped, revisit later

**Borderline:**

- The delta function argument (voltage depends on total charge, not pulse shape) — is this obvious to you from your math background, or did it sharpen something?

What's your sense? Anything you'd add or cut?

---

**You**

yes sounds good. again, i want to be building intuition with these cards so some cards along the lines of "if this happens then what will happen" would be useful

---

**Claude**

Good — "if X then what" cards are exactly the salience/behavioral prompts that close the gap between knowing a fact and having it occur to you. Let me generate the set.

```
The cell membrane acts like a {{c1::capacitor}} because it is a thin insulator separating two conducting solutions, allowing charge to build up on either side
```

```
The cell membrane acts like a {{c1::resistor (with finite leak resistance)}} because the insulator is imperfect — ions slowly leak through via ion channels
```

```
The resting potential in the LIF circuit model is represented by a {{c1::battery}} in series with the membrane resistance
```

```
The passive membrane equation: τ_m (du/dt) = {{c1::−(u − u_rest) + RI(t)}}
```

```
In the passive membrane equation, the term −(u − u_rest) represents {{c1::the leak current through the membrane resistance, which always drives the potential back toward rest}}
```

```
In the passive membrane equation, τ_m = {{c1::RC}}, where R is the membrane resistance and C is the membrane capacitance
```

```
A typical membrane time constant τ_m is on the order of {{c1::10 ms}}, which is {{c2::~10x longer}} than the duration of an action potential (~1 ms)
```

```
If you inject current into a neuron and then stop, the membrane potential returns to rest via {{c1::exponential decay with time constant τ_m}}: u(t) − u_rest = Δu · exp(−t/τ_m)
```

```
If the membrane resistance R → ∞ (no leak), the passive membrane equation becomes {{c1::du/dt = I(t)/C}}, which is a {{c2::perfect integrator}} — it accumulates charge indefinitely with no decay
```

```
If you apply a constant current I_0 to a passive membrane forever, the steady-state voltage is {{c1::u_rest + RI_0}}, because in steady state {{c2::du/dt = 0, so all current flows through the resistor and none charges the capacitor}}
```

```
If you deliver a very short current pulse (Δ ≪ τ_m), the resulting voltage deflection depends on {{c1::the total charge q delivered (= I_0 · Δ)}}, not on the pulse duration or amplitude separately
```

```
The two components that define the leaky integrate-and-fire model are: (1) {{c1::the linear ODE describing membrane voltage evolution (passive membrane equation)}} and (2) {{c2::a threshold ϑ with immediate reset to u_r after firing}}
```

```
In the LIF model, when u(t) reaches the threshold ϑ, the spike itself is {{c1::not explicitly modeled}} — it is treated as a point event (delta function), and the voltage is immediately reset to u_r
```

```
If a neuron is integrating excitatory PSPs that sum linearly, this linearity breaks down when {{c1::the membrane potential reaches the firing threshold ϑ, triggering an action potential — a qualitatively different event}}
```

```
The fundamental nonlinearity of a spiking neuron: {{c1::linear integration}} below threshold, {{c2::a qualitative all-or-nothing event (spike)}} at threshold
```

```
If an inhibitory synapse opens ion channels near a neuron at rest, the immediate effect on membrane potential is {{c1::very small}}, because {{c2::the reversal potential of inhibitory synapses (E_inh ≈ −75mV) is close to the resting potential (≈ −65mV), so the driving force is small}}
```

```
Shunting inhibition works by {{c1::increasing membrane conductance (lowering resistance)}}, which causes excitatory currents to be {{c2::divided by a larger total conductance}}, reducing the voltage change they can produce
```

```
Shunting inhibition is a {{c1::divisive/multiplicative}} operation on excitatory input, not an {{c2::additive/subtractive}} one
```

```
Physically, shunting inhibition works because excitatory Na+ flowing in is opposed by {{c1::K+ flowing out (or Cl− flowing in) through open inhibitory channels}}, and the membrane capacitor only sees {{c2::net charge}}, regardless of ion species
```

```
If a neuron's membrane is depolarized above E_inh with many inhibitory channels open, and excitatory input tries to depolarize it further, the inhibitory channels {{c1::push back harder}} because {{c2::the driving force (u − E_inh) across those channels increases, creating a negative feedback loop}}
```

```
When I see a conductance-based synapse model, I should remember that the postsynaptic current depends on {{c1::the difference between membrane potential and the synapse's reversal potential}}, making the response state-dependent rather than fixed
```

```
Adaptation in the LIF model can be captured by making the firing threshold {{c1::dynamic}}: it increases by a fixed amount θ after each spike and relaxes exponentially back to ϑ_0 with time constant {{c2::τ_adapt (hundreds of ms)}}
```

```
If a neuron fires several spikes in rapid succession, the adaptive threshold mechanism causes {{c1::the threshold to accumulate upward, making each successive spike harder to trigger}}, which produces {{c2::increasing interspike intervals until a steady firing rate is reached}}
```

```
The simple LIF model cannot capture adaptation because {{c1::the reset erases all memory — each spike starts the integration fresh from u_r, with no trace of previous spikes}}
```

```
When I see a neuron model, I should ask: does it have {{c1::memory beyond the most recent spike}}? If not, it cannot capture {{c2::adaptation, bursting, or any multi-spike phenomenon}}
```

---

**You**

i updated the project instructions significantly, especially around how cards should be made. consider the full context of this conversation and the new instructions, and regenerate cards from scratch for me.

---

**Claude**

Let me re-read the instructions carefully.

```
Q: In the LIF circuit model, what physical property of the membrane does the capacitor represent?
A: Charge storage across the insulating membrane

Q: In the LIF circuit model, what physical property of the membrane does the resistor represent?
A: Ion leakage through the membrane

Q: In the LIF circuit model, what does the battery represent?
A: The resting potential

Q: What is the passive membrane equation?
A: τ_m (du/dt) = −(u − u_rest) + RI(t)

Q: In the passive membrane equation, why is the sign of (u − u_rest) negative?
A: It's a restoring force — drives voltage back toward rest

Q: In the passive membrane equation, what is τ_m in terms of circuit components?
A: RC

Q: What is the order of magnitude of a typical membrane time constant τ_m?
A: ~10 ms

Q: If you stop injecting current into a passive membrane, what does the voltage do?
A: Exponential decay to u_rest with time constant τ_m

Q: If the membrane had no leak (R → ∞), what would the passive membrane equation become?
A: du/dt = I(t)/C — a perfect integrator

Q: Why can't a perfect integrator (no leak) be a good neuron model on its own?
A: It accumulates charge indefinitely with no decay

Q: A constant current I_0 is applied to a passive membrane forever. What is the steady-state voltage?
A: u_rest + RI_0

Q: Why does steady-state voltage under constant current equal u_rest + RI_0? (Think about the capacitor.)
A: du/dt = 0, so no current charges the capacitor — all current flows through R

Q: You deliver a very short current pulse (Δ ≪ τ_m) to a passive membrane. What determines the voltage deflection?
A: Total charge delivered (q = I_0 · Δ), not pulse shape

Q: What are the two components that define the LIF model? (1 of 2): the subthreshold dynamics
A: Linear ODE for membrane voltage (passive membrane equation)

Q: What are the two components that define the LIF model? (2 of 2): the spiking mechanism
A: Threshold ϑ with immediate reset to u_r

Q: In the LIF model, is the shape of the action potential explicitly modeled?
A: No — it's a point event; voltage resets instantly

Q: A neuron sums excitatory PSPs linearly. When does this linearity break down?
A: When voltage reaches threshold — triggering a qualitatively different event (spike)

Q: An inhibitory synapse opens channels on a neuron near rest. Why is the voltage effect small?
A: E_inh (≈ −75mV) is close to u_rest (≈ −65mV), so driving force is small

Q: How does shunting inhibition reduce the effect of excitatory input?
A: Increases total membrane conductance, dividing excitatory current's voltage effect

Q: Is shunting inhibition additive or divisive?
A: Divisive

Q: Physically, why does the membrane capacitor not distinguish between Na+ entering and K+ leaving?
A: It only sees net charge, regardless of ion species

Q: Many inhibitory channels are open and excitatory input tries to depolarize the membrane. What happens at the inhibitory channels?
A: Their driving force (u − E_inh) increases, so they push back harder — negative feedback

Q: What does the adaptive threshold equation do after each spike?
A: Increases ϑ by a fixed amount θ

Q: What does the adaptive threshold do between spikes?
A: Relaxes exponentially back to ϑ_0 with time constant τ_adapt (~hundreds of ms)

Q: A neuron fires several spikes rapidly under the adaptive threshold model. What happens to the interspike intervals?
A: They increase — each spike is harder to trigger

Q: Why can't the simple LIF model (without adaptation) capture increasing interspike intervals?
A: Reset erases all memory — each spike restarts integration fresh from u_r

Q: When I see a neuron model, I should ask: does it have memory beyond the most recent spike? If not, it cannot capture...
A: Adaptation, bursting, or any multi-spike phenomenon

Q: When I see a conductance-based synapse, I should remember that the postsynaptic current depends on...
A: (u − E_syn) — making the response state-dependent, not fixed
```

---

**You**

Anki-compatible mathjax for the equations/variables please

---

**Claude**

```
Q: In the LIF circuit model, what physical property of the membrane does the capacitor represent?
A: Charge storage across the insulating membrane

Q: In the LIF circuit model, what physical property of the membrane does the resistor represent?
A: Ion leakage through the membrane

Q: In the LIF circuit model, what does the battery represent?
A: The resting potential

Q: What is the passive membrane equation?
A: \(\tau_m \frac{du}{dt} = -(u - u_{\text{rest}}) + RI(t)\)

Q: In the passive membrane equation, why is the sign of \((u - u_{\text{rest}})\) negative?
A: It's a restoring force — drives voltage back toward rest

Q: In the passive membrane equation, what is \(\tau_m\) in terms of circuit components?
A: \(RC\)

Q: What is the order of magnitude of a typical membrane time constant \(\tau_m\)?
A: ~10 ms

Q: If you stop injecting current into a passive membrane, what does the voltage do?
A: Exponential decay to \(u_{\text{rest}}\) with time constant \(\tau_m\)

Q: If the membrane had no leak (\(R \to \infty\)), what would the passive membrane equation become?
A: \(du/dt = I(t)/C\) — a perfect integrator

Q: Why can't a perfect integrator (no leak) be a good neuron model on its own?
A: It accumulates charge indefinitely with no decay

Q: A constant current \(I_0\) is applied to a passive membrane forever. What is the steady-state voltage?
A: \(u_{\text{rest}} + RI_0\)

Q: Why does steady-state voltage under constant current equal \(u_{\text{rest}} + RI_0\)? (Think about the capacitor.)
A: \(du/dt = 0\), so no current charges the capacitor — all current flows through \(R\)

Q: You deliver a very short current pulse (\(\Delta \ll \tau_m\)) to a passive membrane. What determines the voltage deflection?
A: Total charge delivered (\(q = I_0 \cdot \Delta\)), not pulse shape

Q: What are the two components that define the LIF model? (1 of 2): the subthreshold dynamics
A: Linear ODE for membrane voltage (passive membrane equation)

Q: What are the two components that define the LIF model? (2 of 2): the spiking mechanism
A: Threshold \(\vartheta\) with immediate reset to \(u_r\)

Q: In the LIF model, is the shape of the action potential explicitly modeled?
A: No — it's a point event; voltage resets instantly

Q: A neuron sums excitatory PSPs linearly. When does this linearity break down?
A: When voltage reaches threshold — triggering a qualitatively different event (spike)

Q: An inhibitory synapse opens channels on a neuron near rest. Why is the voltage effect small?
A: \(E_{\text{inh}} \approx -75\text{mV}\) is close to \(u_{\text{rest}} \approx -65\text{mV}\), so driving force is small

Q: How does shunting inhibition reduce the effect of excitatory input?
A: Increases total membrane conductance, dividing excitatory current's voltage effect

Q: Is shunting inhibition additive or divisive?
A: Divisive

Q: Physically, why does the membrane capacitor not distinguish between Na⁺ entering and K⁺ leaving?
A: It only sees net charge, regardless of ion species

Q: Many inhibitory channels are open and excitatory input tries to depolarize the membrane. What happens at the inhibitory channels?
A: Their driving force \((u - E_{\text{inh}})\) increases, so they push back harder — negative feedback

Q: What does the adaptive threshold equation do after each spike?
A: Increases \(\vartheta\) by a fixed amount \(\theta\)

Q: What does the adaptive threshold do between spikes?
A: Relaxes exponentially back to \(\vartheta_0\) with time constant \(\tau_{\text{adapt}}\) (~hundreds of ms)

Q: A neuron fires several spikes rapidly under the adaptive threshold model. What happens to the interspike intervals?
A: They increase — each spike is harder to trigger

Q: Why can't the simple LIF model (without adaptation) capture increasing interspike intervals?
A: Reset erases all memory — each spike restarts integration fresh from \(u_r\)

Q: When I see a neuron model, I should ask: does it have memory beyond the most recent spike? If not, it cannot capture...
A: Adaptation, bursting, or any multi-spike phenomenon

Q: When I see a conductance-based synapse, I should remember that the postsynaptic current depends on...
A: \((u - E_{\text{syn}})\) — making the response state-dependent, not fixed
```

---

**Claude**

Neuronal Dynamics