# The ARC Layered Model: A Layered Model for Modular Cognition and Explainable Intelligence

> **DRAFT v2 — 2026-11-06, for Joshua's review.**
> Built from the published paper (`ARC-Layered-Model-v1-as-pulled.md`) plus the
> conversation of 2026-11-06. Sections marked **[CHANGED]** are revisions;
> **[NEW]** are additions. Nothing here is settled until Joshua says so.

**Author: Joshua Wink**

---

## Abstract

As artificial intelligence systems grow in complexity and autonomy, the need for modular, transparent, and ethically grounded design becomes urgent. This paper introduces the **ARC Layered Model** — ARC standing for **Auditable Reasoning & Cognition** — a layered model for artificial cognition.

The ARC Layer Stack consists of seven refinement layers that transform raw signals into contextualized, explainable decisions. It is supplemented by **Salience Triage**, which governs what is retained; the **Trace Descent Path**, a post-hoc audit trail from final action back to first input; and **Reflexes**, layer-local fast paths. **[CHANGED]**

Two claims distinguish the model. First, its layers can be **exited early** — a signal may resolve before it reaches conscious reasoning, which is how a living organism survives and how an expert moves without deliberation. Second, the layers are separated by **vocabulary**: lower layers answer from a fixed set of options, and only the reasoning layer generates language that was not written in advance. That boundary is what makes auditability possible, and it is testable.

The model does not place moral judgment inside the machine. Layer 7 is where a **human being** takes responsibility for the decision — the system's obligation is to arrive there with the decision fully exposed. **[CHANGED]**

---

## 1. Introduction

**[CHANGED]** Modern AI systems are capable of remarkable feats — yet many still operate as opaque pipelines. They predict, recommend, or act without a structure that explains *how* or *why* a decision was made. This lack of modularity, traceability, and alignment poses not just technical risks, but ethical ones.

The immediate inspiration is the OSI networking model, which brought layered clarity to network communication. A cognitive model borrows its **shape** and refuses its **purpose**, and the difference matters.

OSI layers exist so that each can be replaced without disturbing the others. The abstraction is the goal: a layer above should not know how a layer below works. Layers in a nervous system exist for the opposite reason. They exist so that a signal can **stop early**. Touch something hot and the withdrawal begins before the signal has finished climbing to the brain; the local circuit resolves it. The layers are not insulation, they are **successive opportunities to act**.

That inversion is the thesis of this paper. A cognitive stack is not a stack of abstractions. It is a stack of **escalation points** — and the health of the system is measured by how seldom a signal has to go all the way up.

This is not an algorithm. It is not a training technique. It is a **layered model for cognition** — a framework that enables inspection, composition, and responsibility.

---

## 2. Overview of the ARC Layered Model

```
          [ Actuation Plane ]
                   ^
     [ Layer 7: Wisdom & Oversight ]   <- a human decides here
                   ^
     [ Layer 6: Reasoning ]
                   ^
     [ Layer 5: Context Management ]
                   ^
     [ Layer 4: Decision Model ]
                   ^
     [ Layer 3: Signal Processing ]
                   ^
     [ Layer 2: Normalization ]
                   ^
     [ Layer 1: Input ]
```

1. Input
2. Normalization
3. Signal Processing
4. Decision Model
5. Context Management
6. Reasoning & Interpretation
7. Wisdom & Oversight

This is not a rigid pipeline — it is a **model**. Layers communicate, can revisit earlier stages when ambiguity arises, and are shaped by cross-cutting forces: **time**, **trust**, **security**, **explainability**, and **human-in-the-loop**.

**[NEW] Three paths through the stack.** The same signal can take any of them:

- **Ascent** — upward refinement, layer by layer. The honest path, and the expensive one.
- **Descent** — the read-only audit back down through the logs, after the fact.
- **The shortcut** — a reflex resolving at whichever layer is competent to resolve it.

A mature system uses the shortcut most of the time. An immature system uses ascent for everything. **How a system matures is the story of its shortcuts.**

In this model:
- Data flows upward through increasing structure and meaning.
- **Actions** are committed post-cognition, via a dedicated **Actuation Plane**.
- **Salience Triage** governs what becomes memory, what becomes context, and what fades.
- The **Trace Descent Path** allows us to walk backward to explain any choice.

---

## 3. Perception: Sensors

**[NEW]** Before Layer 1 receives anything, something must detect it.

The organizing metaphor of this model is **the living organism**, and it is offered as evidence rather than decoration. Everything described here is drawn from how a body already works. That is the claim: the pattern is not invented for machines, it is observed in organisms and then made buildable.

A sensor reports a property of the world. A nerve reports softness, cold, pressure, stretch. These reports arrive **whether or not attention is on them** — you can set your attention on a texture afterward and find it remarkable, but the nerve was already reporting it. Sensation precedes attention.

Sensors in a cognitive system are equally arbitrary. Where a body has skin that reads pressure, a machine may have a sensor that reads ultraviolet, ionizing radiation, acoustic structure, magnetic field, or anything else inside — or deliberately beyond — the range a living organism experiences. The model does not privilege biological senses. It privileges the **structure** of sensing.

### 3.1 One sensor reports; two sensors measure

A single channel tells you *that* something is present. It does not tell you *where* it is.

With two sensors and a known separation, the relationship between their reports yields a quantity that exists in **neither report**. Two eyes give depth from disparity. Two ears give direction from time difference. In each case the pair produces information the individual channel never contained.

This is the model's strongest argument for composability, and it should be stated plainly:

> **Some information exists only at the level of the relationship between signals.**

It is also the reason a cognitive system should not be designed to receive a single stream. Depth is not a property of a picture. It is a property of a pair.

---

## 4. The Seven Layers

### Layer 1: Input

Receives unstructured signals from sensors and sources: logs, queries, audio, telemetry. It makes no assumptions about structure or meaning. Timestamping and basic metadata (source, modality) may occur here, but no filtering or transformation is applied.

The layer's value is that it is **unguarded**. What arrives is what happened.

### Layer 2: Normalization

**[CHANGED]** Transforms raw input into structured formats: tokens, typed events, embedding vectors. If normalization fails, error artifacts pass upward as well — not hidden.

The published version described this layer as format conversion. That undersells it. Two further duties belong here, and they are the reason Layer 2 is more than plumbing:

**Fusion.** Where two or more sensors observe the same scene, their reports are combined here into quantities no single channel carried — depth, direction, motion, material. Fusion is not the normalization of one signal. It is the construction of a new one, and it belongs at Layer 2 because it depends on the raw geometry of the channels, not on their meaning.

**Fidelity accounting.** A normalized signal must carry its own trustworthiness: resolution, provenance, freshness, confidence. A fused signal must carry how much of its confidence came from agreement between channels. Without this, every layer above silently inherits the errors below.

**[OPEN QUESTION for Joshua]** Whether fusion deserves its own named duty within Layer 2, or a layer of its own, is unsettled.

### Layer 3: Signal Processing

Filters and prioritizes normalized inputs. It scores relevance, detects anomaly, and routes by salience. This is where "what deserves attention?" is first asked.

**[NEW] Salience is a routing decision, not just a score.** A salience score that only gets recorded has done nothing. The score's purpose is to decide **which layer the signal stops at**. A signal above threshold continues; a signal that matches a known pattern resolves and never climbs. The efficiency of the entire stack is decided here, which is why Salience Triage (§8) is a cross-cutting concern rather than a step.

### Layer 4: Decision Model

**[CHANGED]** Applies rules, policies, or selectors to determine whether action should be taken — escalate, defer, await more data, act, or do nothing. It does not decide *how* to act; only *whether*, and *from a fixed set of options*.

**[NEW] The vocabulary rule.** This is the testable boundary between Layer 4 and Layer 6:

> **Layer 4 selects from a closed vocabulary. Layer 6 generates from an open one.**

Every option Layer 4 can choose was written before the signal arrived. Layer 6 produces language that was not anticipated — a summary, a hypothesis, a contradiction discovered mid-sentence. Point at any component and ask: *is its answer space fixed?* If yes, it is a decision model and it is auditable by construction. If no, it is reasoning, and its audit lives in its trace rather than its option list.

The practical consequence is a design pressure: **anything that can be pushed down into a closed-vocabulary decision becomes legible and cheap.** A decision that stays at Layer 6 is expensive twice — once in compute, and once in the audit.

**[NEW] Why now.** A decision model is only as useful as its decision function. Historically that function was either a hand-written rule or an LLM call, so anything richer than a threshold was either impossible to express or too expensive per event. A **decision model with a fixed label set** — sometimes called a system-one model — changes that economics. It selects an option, it does not write prose, it holds no tools, and it is cheap enough to invoke per signal.

That is what makes a genuinely populated Layer 4 practical. A decision model need not be a single threshold. It can be a selector over a written vocabulary: *in scope / out of scope / needs a human / cannot be undone*. The layer was always meant to be this. The model that fills it only recently became affordable.

### Layer 5: Context Management

Maintains temporal and identity continuity: session memory, user-specific data, historical relevance. Not yet interpretation, but **situation awareness**.

Context is **not a dump of prior data** — it is curated by Salience Triage, which decides what deserves to be remembered. The output is a memory-augmented frame of reference for the layers above.

### Layer 6: Reasoning & Interpretation

The core cognitive engine. Draws conclusions from structured input and temporal context using logic, inference, or learned models. It asks: *What does this mean? What follows? What contradicts?*

This is the layer with an **open vocabulary**, and the only layer where an unexpected answer is possible. Every other layer answers a question someone already knew to ask.

Output includes logical conclusions, predicted outcomes, summarized intent, and hypotheses — and it is **explainable by design**, because reasoning traces and justification chains are written to the Reasoning Trace Log as they form.

**[NEW] Layer 6 is where the funnel stays open.** The layers below converge; this one must not. A system that narrows too early produces well-audited behavior and cannot discover anything. The narrowing belongs at ascent, not at the door.

### Layer 7: Wisdom & Oversight

**[CHANGED — the largest revision. Read this first if only one section.]**

The published version said this layer "injects ethics and values, policy and constraints, mission relevance, and human-in-the-loop triggers," and that accountability "lives here."

The revised claim is narrower and, it is argued, more honest:

> **Layer 7 is not a component. It is a person.**

Oversight is not a function a system can perform on itself. It is an act of **discernment**, and discernment is a human burden. Ethics is not a solved domain from which a specification can be drawn. What is right and what is wrong is genuinely contested, and no amount of engineering converts that contest into a lookup. What resolves it — slowly, imperfectly, and with consequence — is a person reasoning it through, examining it, and taking responsibility for the answer.

This is a design commitment with teeth, and it produces three rules:

**1. The system cannot bear responsibility.** It can hold a decision, present it, and expose its whole derivation. It cannot own the outcome. Placing moral accountability on a system is not delegation, it is abandonment — the consequences still land on people, who then have no one to answer to.

**2. The system must make the decision easy to judge, not to accept.** Layer 7's requirement is not that the model decide well. It is that the human arrive at the decision with everything visible — the input, the context, the reasoning, the alternatives, and what happens if it is wrong. The Trace Descent Path is the mechanism. Its purpose is not transparency for its own sake; it is to let a person make a real judgment rather than a rubber stamp.

**3. Oversight inherits the obligation to be slow where it must be.** A decision that needs to be reasoned out must be allowed to be reasoned out. A system that asks for approval faster than a person can consider it has not created oversight; it has created a habit of consent.

**On tools at Layer 7.** A person making a moral judgment may use instruments — frameworks, precedents, advisors, and analytical aids of any kind. The model's position is that instruments inform the judgment without becoming it. A system trained to recognize moral character in a scenario, for instance, can be a useful lens: it says *this reads as a case of mercy, and here is why.* That is an aid to discernment. It is not discernment, and it must never be treated as the seat where the decision is made — because the moment an instrument's output is accepted as the verdict, the human has stopped judging and the responsibility has gone nowhere. **[See §12.]**

The consequence for the stack: Layer 7 is the layer the system **hands to**. It is a boundary, not an engine. Where a human has not been consulted, the highest layer the system may legitimately reach is Layer 6 — a conclusion, not a commitment.

---

## 5. Reflexes

**[CHANGED]** The published version defined reflexes as layer-local reactions to "local anomalies or safety thresholds," and every example in its table was a fault: overflow, malformed input, contradiction, conflict.

That framing is too narrow, and it misses the most important thing reflexes do.

A reflex is a **path through the stack that resolves before ascent completes.** Fault handling is one case. The others are at least as important:

**Withdrawal.** A hand leaves a hot surface before the signal reaches the brain — in a real nervous system the local circuit can initiate it without the message travelling all the way up. The system did not fail. It withdrew correctly and quickly. The reflex fired because the response was *right*, not because something *broke*.

**Competence.** A skilled hand shapes a form without the person deliberating over each movement. That is not a safeguard either. It is **muscle memory** — a resolution that has been reached so reliably, so many times, that the ascent is no longer necessary. The reasoning was done once. The reflex is what remains of it, compressed.

**Habituation.** The same mechanism in the other direction — a signal that has proven to carry nothing repeatedly stops climbing.

Together these give the model something the published version lacked: **a growth story.** A novice routes nearly everything to Layer 6. Expertise is the gradual relocation of judgement downward — not because the higher layers improved, but because the lower ones learned. The stack is not fixed in its proportions. It matures.

And it clarifies what a reflex is *not*: it is not the absence of thought. It is **thought, already had.** Compressed, in the same sense that a compression is a prior result reused.

**[NEW] The requirement this places on reflexes.** Because Layer 6 is the only layer with an open vocabulary, a reflex can only exist where a layer's answer space is closed. A shortcut requires a destination. This is why reflex and decision model are the same discipline viewed from two directions: one is how a decision gets made, the other is how it stops needing to be made.

**[NEW] A caution.** A reflex that fires when the world has changed is worse than no reflex at all, because it is fast and confident. Every reflex therefore owes: a record of what it fired on, and a way to be extinguished. Habituation is not a flaw to be designed out. It is the mechanism by which bad reflexes die.

---

## 6. Actuation Plane

The model is fundamentally cognitive. It stops at the boundary of internal deliberation. The **Actuation Plane** is the system's interface to the world — where judgment becomes commitment.

When Layer 7 produces an aligned, explainable decision, that output passes into actuation: an API call, a motion, a file write, a notification. The actuation itself is **not subject to reasoning**. It is executed, and its consequences become observable.

The plane is strictly downstream: it makes no decisions, but returns effects to be observed again via Layer 1. It is not a layer of cognition — it is the **effect surface**.

This preserves the separation between thought and deed, deliberation and execution, internal process and external impact.

Critically, actuation **must be logged**. The Actuation Log is part of the Trace Descent Path, so that any external effect can be traced to its origin.

---

## 7. Orthogonal Axes

The stack is vertical; these forces apply across all of it, and are not layers themselves.

**Time.** Inputs expire, memory decays, actions become invalid if delayed.

**Trust.** Inputs can be spoofed, reasoning can be probabilistic, sources have histories. Confidence and integrity propagate.

**Security.** Input validated, context access-controlled, actuation tamper-proof. Each layer guards its own perimeter.

**Explainability.** Every transformation, escalation, or discard is logged, justifiable, and reconstructable. A systemic property, designed in.

**Human-in-the-Loop.** Hooks wherever judgment is ethical or high-impact. **[CHANGED]** Under §4's revision this axis is not merely convenient — it is the mechanism by which Layer 7 exists at all.

---

## 8. Salience Triage

Not all information deserves equal attention.

```
    [Wisdom]        -> Ethical Significance
    [Reasoning]     -> Attention Weights
    [Context]       -> Memory Relevance
    [Decision]      -> Policy Fit
    [Signal]        -> Relevance Scores
    [Normalization] -> Format Validity
    [Input]         -> Filter: Noise, Spam
```

**Salience Triage** determines what is ignored, what is stored, what becomes context, and what is surfaced for reasoning or action. It may be implemented as rule-based filters, attention weights, human prioritization, or statistical anomaly detection.

**[NEW]** Its most consequential job is **routing**: deciding which layer a signal stops at. A triage policy that sends everything to Layer 6 is a system that thinks about everything and therefore thinks about nothing in particular. Triage is where efficiency and attention are the same decision.

Each triage decision is itself loggable and reversible, so missed signals can be recovered in post-hoc analysis. Without triage, systems drown. With it, cognition becomes sustainable and focused.

---

## 9. Immutable Storage Tiers

Every layer writes to its own **append-only** tier.

| Layer | Storage Tier | Purpose |
|-------|--------------|---------|
| L1 | Ingress Log | Raw input capture |
| L2 | Normalization Ledger | Transformations and fusion provenance |
| L3 | Signal Archive | Relevance scores and routing |
| L4 | Decision Journal | Which option, and why that vocabulary |
| L5 | Context Ledger | Memory and state frames |
| L6 | Reasoning Trace | Inference and logic chains |
| L7 | Oversight Ledger | The human decision, and its rationale |
| -> | Actuation Log | What was done, when, and why |

Each log is immutable. Higher layers may **read** lower logs, never write to them, preserving temporal and causal integrity.

**[CHANGED]** Two notes. The L2 tier must record **fusion provenance** — which channels agreed — or downstream trust cannot be reconstructed. And the L7 tier now records a *human* decision and its stated rationale, which is what makes the oversight real rather than nominal.

---

## 10. Trace Descent Path

To explain itself, a system walks the **Trace Descent Path** — from final decision back to origin.

```
    Oversight Ledger       <- Layer 7
        |
    Reasoning Trace        <- Layer 6
        |
    Context Ledger         <- Layer 5
        |
    Decision Journal       <- Layer 4
        |
    Signal Archive         <- Layer 3
        |
    Normalization Ledger   <- Layer 2
        |
    Ingress Log            <- Layer 1
```

From the Oversight Ledger:
1. What was the decision?
2. Why was it made?
3. What context was active?
4. What signal triggered it?
5. How was the input normalized?
6. What was originally received?

The path supports audits, ethical investigations, forensics, and introspection.

**[CHANGED]** Its purpose is sharper than "understanding." Given §4's revision, the descent exists so that **a person can take responsibility with their eyes open**. An audit that concludes "the system decided" has failed at its one job — it must terminate at a human being who can say *I see what it saw, and I am answering for this.*

**[NEW] The reflex path must be descendent too.** A shortcut that leaves no trace is unauditable by construction. Every reflex records what it fired on and where it exited, so the descent can follow a signal that never completed its ascent.

---

## 11. Limitations & Future Work

**[CHANGED]** Open areas, stated as research frontiers rather than defects:

- **Live feedback loops.** Adaptation during unfolding data, kept explainable.
- **Dynamic layer mutation.** Stacks that reconfigure for a domain — and whether reconfiguration can itself be audited.
- **Cross-agent models.** How Layer 5 memory and Layer 7 responsibility behave across a network of agents. If accountability cannot be delegated to one system, it certainly cannot be diluted across many.
- **Performance tradeoffs.** Full audit fidelity against speed.
- **Reflex acquisition and extinction.** What makes a shortcut trustworthy enough to earn, and what retires it.
- **Fusion and its limits.** Which relationships between channels genuinely create information, and which merely average.
- **Whether Layer 7 is a layer.** If oversight is a person, the stack may have six layers and a boundary. This draft keeps seven for continuity, and flags the question.

---

## 12. Appendix: Discussion, 2026-11-06

**[NEW]** Recorded because these are the reasons the revisions above exist.

**On the OSI parallel.** The value is the shape, not the rules. Networking layers abstract; cognitive layers escalate. One protects replaceability, the other protects the organism.

**On the body as evidence.** The model was arrived at by asking what networking's layering looks like for a person, then describing how a body works — reflex withdrawal, sensation before attention, two eyes for depth. The biology is not the limit of the model. It is the proof that the pattern is real.

**On decision models.** A selector with a fixed label set is what makes a populated Layer 4 affordable. The layer always wanted a real decision function; only now is one cheap enough to use per event.

**On moral instruments.** A system that reads a scenario through a fixed moral frame — for instance, one trained on Scripture and asked to describe a situation in terms of mercy, justice, or faithfulness — is a genuine aid to a human making a moral judgment. It is a tool that helps a person see more clearly.

It is not Layer 7. Layer 7 is the person. An instrument can improve a judgment and still never be the thing that bears it. Ethics is contested, discernment is difficult, and the resolution is arrived at by human beings reasoning it out — in prayer, in counsel, in conscience — and then living with what they chose.

The system's contribution is to make that choice visible and complete. The human's contribution is to make it, and to answer for it.

---

## 13. Conclusion

**[CHANGED]** The ARC Layered Model defines a layer of clarity for artificial intelligence.

By modeling cognition as a model rather than a black box, we gain modularity, explainability, responsibility, and alignment. We gain the ability to inspect cognition like a packet trace, and to constrain power by purpose.

But the deepest claim is not about transparency. It is about **where responsibility sits**. The stack refines, selects, reasons, and presents. It does not decide what is right. That remains with a person, who is not a component of the system but its reason for being auditable in the first place.

This model does not pretend to be final. It is **foundational** — a scaffolding to build better systems and ask better questions. It is an invitation to compose intelligence in layers, and in doing so to build systems that are not just capable, but trustworthy.

---

### Layer Index

| Layer | Name | Function |
|-------|------|----------|
| 1 | Input | Raw reception of unstructured data |
| 2 | Normalization | Format transformation, fusion, fidelity |
| 3 | Signal Processing | Filtering, salience scoring, routing |
| 4 | Decision Model | Selection from a closed vocabulary |
| 5 | Context Management | Memory, continuity, relevance |
| 6 | Reasoning & Interpretation | Open-vocabulary inference |
| 7 | Wisdom & Oversight | A human decides, and answers |

### Glossary

**Salience Triage**: what is remembered, ignored, routed, or surfaced.
**Trace Descent**: read-only traversal from a decision back to its origin.
**Actuation Plane**: the execution boundary — where cognition becomes commitment.
**Reflex**: a path that resolves before ascent completes; compressed prior reasoning.
**Closed vocabulary**: an answer space written before the signal arrived (Layer 4).
**Open vocabulary**: an answer space that includes answers nobody anticipated (Layer 6).
**Fusion**: combining channels to produce a quantity no single channel carried.
**Orthogonal Axes**: time, trust, security, explainability, human-in-the-loop.

---

*End of Draft*
