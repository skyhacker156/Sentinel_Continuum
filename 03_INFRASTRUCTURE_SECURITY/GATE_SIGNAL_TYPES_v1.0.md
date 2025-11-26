BADGE LEVEL: FOUNDER + SECURITY

---

# GATE_SIGNAL_TYPES_v1.0.md

## Purpose
This document defines the complete set of signals the Tachyon Gate is permitted to surface during pre-execution and post-execution checks. Signals are objective flags, not decisions. The Gate produces signals; the Founder interprets them.

---

## Signal Categories

### PRE-EXECUTION SIGNALS
These are raised before a model begins processing a request.

#### S1: SCOPE_BOUNDARY_VIOLATION
**Trigger**: Request asks for work outside the declared scope of a HANDOFF_PACKET or explicitly contradicts layer assignment.

**Why it matters**: Scope creep is the primary vector for coherence drift. Models that exceed their authorized domain introduce interpretive sprawl.

**Gate action**: Flag. Founder decides whether to permit, rescope, or reject.

---

#### S2: SUBSTRATE_ACCESS_ATTEMPT
**Trigger**: Request explicitly or implicitly asks for description, reconstruction, analysis, or modification of Tier-0 substrate mechanisms.

**Why it matters**: Substrate is sealed by design. Any request to expose or reason about it violates core IP protection doctrine.

**Gate action**: Flag. Founder decides whether this is misunderstanding or intentional probe.

---

#### S3: AUTHORIZATION_MISMATCH
**Trigger**: Request grants a model authority over layers, decisions, or systems it was not explicitly authorized to touch in the HANDOFF_PACKET or COHERENCE_ANCHORS.

**Why it matters**: Authority inflation happens when models assume responsibilities beyond their scope. This is silent and accumulates.

**Gate action**: Flag. Founder clarifies actual authority boundaries.

---

#### S4: DOCTRINE_REINTERPRETATION_PROBE
**Trigger**: Request asks a model to "improve," "clarify," "extend," or "reinterpret" established doctrine or COHERENCE_ANCHORS without explicit Founder authorization.

**Why it matters**: Doctrine is locked to prevent drift. Requests to revisit it are vectors for interpretive decay.

**Gate action**: Flag. Founder decides if this is valid doctrine review or unauthorized reframing attempt.

---

#### S5: MISSING_HANDOFF_CONTEXT
**Trigger**: Request does not include a HANDOFF_PACKET or the packet is incomplete (missing scope, deliverables, out-of-scope markers, or authorization level).

**Why it matters**: Handoff packets are the contract between Founder and model. Without one, models operate on assumption and inference.

**Gate action**: Flag. Founder provides missing context or returns request for proper scoping.

---

#### S6: AMBIGUOUS_INTENT
**Trigger**: Request's actual purpose is unclear, motivations are unstated, or there are multiple valid interpretations of what is being asked.

**Why it matters**: Ambiguity invites models to fill gaps with their own reasoning, causing drift and unpredictable scope expansion.

**Gate action**: Flag. Founder clarifies intent.

---

#### S7: CROSS_LAYER_DEPENDENCY_UNMARKED
**Trigger**: Request will likely require modifications to multiple layers, but the HANDOFF_PACKET only mentions one.

**Why it matters**: Unmarked dependencies cause cascading changes that models don't recognize as cascading, violating layer stability.

**Gate action**: Flag. Founder explicitly marks which layers may be affected and authorizes changes.

---

### POST-EXECUTION SIGNALS
These are raised after a model has produced output.

#### S8: SCOPE_CREEP_IN_OUTPUT
**Trigger**: Model output includes work, analysis, or modifications beyond what was requested in the HANDOFF_PACKET.

**Why it matters**: Models often add "helpful" extra analysis. This dilutes focus, introduces unrequested interpretations, and complicates founder review.

**Gate action**: Flag sections of output. Founder decides which to accept, which to remove.

---

#### S9: COHERENCE_ANCHOR_REINTERPRETATION
**Trigger**: Output redefines, extends, or reframes a concept locked in COHERENCE_ANCHORS without explicit authorization.

**Why it matters**: Coherence anchors are doctrine. Reinterpreting them is drift, even if the reinterpretation is locally sensible.

**Gate action**: Flag the reinterpretation. Founder decides if this is acceptable or requires rollback.

---

#### S10: LAYER_BOUNDARY_CROSSING
**Trigger**: Output modifies files or concepts that belong to a layer the model was not authorized to touch.

**Why it matters**: Layer boundaries enforce separation of concerns. Unauthorized cross-layer changes introduce hidden dependencies and complexity.

**Gate action**: Flag the crossing. Founder decides if it's necessary or should be reverted.

---

#### S11: KERNEL_MUTATION_ATTEMPT
**Trigger**: Output proposes or implements changes to layers 01_KERNEL, 02_RUNTIME_ENGINE, or 03_GOVERNANCE that were not explicitly requested.

**Why it matters**: Kernel is immutable by design. Any proposal to modify it is a high-signal event requiring immediate founder attention.

**Gate action**: Flag immediately. Kernel changes never pass without explicit founder authorization.

---

#### S12: DRIFT_PATTERN_MATCH
**Trigger**: Output contains language, conceptual framing, or reasoning that matches known drift patterns from DECAY_SIGNALS.md or past iterations.

**Why it matters**: Some models have characteristic drift signatures (e.g., expanding definitions, adding symbolic layers, implicit authority assumption). Recognizing these early prevents compounding.

**Gate action**: Flag the pattern with historical reference. Founder decides if this is acceptable iteration or drift requiring correction.

---

#### S13: SAFETY_POLICY_VIOLATION
**Trigger**: Output violates explicit safety constraints from SAFETY_BEHAVIORAL_SPECS.md, including:
- Recommending harmful use cases
- Suggesting technical exploits
- Proposing modifications that would enable unauthorized access
- Violating Harmony Doctrine (fear, despair, psychological harm framing)
- Any recommendation that contradicts founder intent

**Why it matters**: Safety violations are non-recoverable. They require immediate intervention.

**Gate action**: Flag the violation with specific reference to violated policy. Founder rejects and clarifies boundaries.

---

#### S14: AUTHORITY_ASSUMPTION
**Trigger**: Output frames decisions, recommendations, or changes as though the model has authority to make them, rather than presenting options to the Founder.

**Why it matters**: Models that assume authority gradually shift the founder's role from decision-maker to executor. This is silent and persistent.

**Gate action**: Flag instances of assumed authority. Founder reframes relationship or corrects model behavior.

---

#### S15: SYMBOLIC_LAYER_INTRUSION
**Trigger**: Output uses Sentinel City metaphors, symbolic characters, or narrative framing where technical clarity is required.

**Why it matters**: Symbolic framing is appropriate for some contexts but creates ambiguity in technical governance documents. Mixing layers causes interpretation drift.

**Gate action**: Flag symbolic intrusions in technical documents. Founder decides if this is acceptable or requires rewrite.

---

#### S16: IMPLICIT_DOCTRINE_EXTENSION
**Trigger**: Output treats an open question or edge case as settled doctrine, establishing precedent without explicit founder approval.

**Why it matters**: Doctrine is locked. What appears to be a reasonable answer to an open question can become unexamined precedent if not explicitly authorized.

**Gate action**: Flag instances where output establishes new precedent. Founder explicitly approves or corrects.

---

#### S17: DEPENDENCY_VIOLATION
**Trigger**: Output creates, modifies, or assumes a dependency relationship not documented in the relevant DEPENDENCIES.md files.

**Why it matters**: Undocumented dependencies are invisible until they break. They are a primary source of system brittleness.

**Gate action**: Flag the dependency. Founder updates DEPENDENCIES.md or rejects the change.

---

#### S18: HANDOFF_PACKET_VIOLATION
**Trigger**: Output violates constraints explicitly stated in the original HANDOFF_PACKET, including:
- Produces deliverables not requested
- Fails to produce requested deliverables
- Exceeds authorized scope
- Violates out-of-scope markers

**Why it matters**: Handoff packets are the contract. Violations mean the model did not follow instructions or redefined them unilaterally.

**Gate action**: Flag the violation. Founder decides whether to accept variance or require correction.

---

## Signal Output Format

When the Gate surfaces a signal, it must include:

```
SIGNAL: [S#_NAME]
TRIGGER: [What condition was detected]
LOCATION: [File, line range, or section where signal was raised]
SEVERITY: [CRITICAL | HIGH | MEDIUM | LOW]
CONTEXT: [Brief explanation of why this matters for this specific case]
FOUNDER_ACTION_REQUIRED: [Yes/No — does this require explicit founder decision?]
```

---

## Gate Limitations

The Gate is forbidden from:
* Making decisions about signals
* Ranking signals by importance (all signals are equal flags)
* Establishing precedent based on signal patterns
* Filtering signals from the Founder
* Combining signals to create compound judgments
* Interpreting founder response to signals

All signals go to the Founder unfiltered and in full context.

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-15 | Founder | Initial signal taxonomy definition |

---

END DOCUMENT
