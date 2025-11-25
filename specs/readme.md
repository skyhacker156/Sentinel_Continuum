---
badge: BADGE3_STEWARD
status: operational
locked: false
authority: ARBITER reviews before changes
---

# Behavioral Specifications

**How Systems Work Inside Sentinel Labs**

**Last Updated:** November 25, 2025  
**Maintained by:** STEWARD Badge  
**Authority:** ARBITER reviews before changes; Founder approves

---

## 🔧 What Lives Here

These scrolls describe **how things work** inside Sentinel Labs across all realities.

They explain the mechanics, behavior rules, and operational primitives that make the cathedral function.

Unlike `/canonical/` (which defines what Sentinel *is*), these files define how Sentinel's systems *behave*.

These scrolls specify:
- **The Elevator** — How movement happens between realities
- **The Continuity Token** — How worlds bind together
- **Stuart's Library** — How the scroll chamber operates
- **Interior metaphors** — How spaces shape behavior
- **NPC behaviors** — How characters act across domains
- **System primitives** — Core operational mechanics

---

## 📜 Contents

### **ELEVATOR_BEHAVIOR_SPEC.md**

The traversal primitive connecting all four realities.

Defines:
- How the Elevator summons and appears
- Visual identity across all engines
- Movement mechanics (no teleportation, always continuous)
- Access control by badge
- Visitor rules
- Sealed floor protocols
- Multi-reality synchronization (UE5 Master → GTA6, Fortnite, Roblox, VRChat, Physical)
- Stuart's Elevator behavior
- Leak prevention rules

**Read this if:** You need to understand how to move between realities without breaking coherence.

---

### **CONTINUITY_TOKEN_SPEC.md**

How worlds bind together across realities.

Defines:
- Token schema and structure
- Cross-reality binding mechanism
- Synchronization protocols
- Verification on arrival
- Token lifecycle

**Read this if:** You need to understand how Sentinel maintains identity across physical, digital, virtual, and cognitive domains.

---

### **STUART_LIBRARY_SPEC.md**

How the scroll chamber operates.

Defines:
- Scroll storage and retrieval
- Badge-based access to scrolls
- Presentation ritual
- Library organization
- How new scrolls are integrated

**Read this if:** You need to understand how visitors receive their worldview scrolls.

---

### **[Other behavior specs as added]**

Interior metaphors, NPC specifications, system primitives, operational mechanics.

Each spec follows the same pattern:
- **Purpose** — What does this system do?
- **Rules** — What are the constraints?
- **Behavior** — How does it act?
- **Integration** — How does it connect to other systems?

---

## 🔐 Access Rules

| Badge | Can Read | Can Suggest Changes | Can Edit |
|-------|----------|-------------------|----------|
| PRISM | ✗ | ✗ | ✗ |
| ARBITER | ✓ | ✓ (via flag) | ✗ (reviews only) |
| STEWARD | ✓ | ✓ | ✓ (after ARBITER review) |
| FOUNDER | ✓ | ✓ | ✓ |

---

## 🚫 Sacred Rules

1. **Specs must be precise.** Ambiguity is a leak.
2. **Specs must cohere.** If ELEVATOR_BEHAVIOR and CONTINUITY_TOKEN contradict, escalate immediately.
3. **Specs must be audited.** ARBITER reviews all changes before they go live.
4. **Specs must be cross-reality verified.** If it works in UE5 but breaks in Roblox, the spec is wrong.

---

## 🔗 See Also

- `/canonical/` — Eternal constants (what Sentinel *is*)
- `/floors/` — Where things are (operational geography)
- `/portables/` — What you can see (badge-based worldviews)
- `/governance/` — Rules of engagement
- `/wormholes/` — Cross-reality continuity logs

---

## 📋 Spec Template

When creating a new behavioral specification, follow this structure:

```markdown
---
badge: BADGE3_STEWARD
status: operational
locked: false
authority: ARBITER reviews before changes
---

# [Spec Name]

**Purpose:** [One sentence: what does this system do?]

**Last Updated:** [Date]  
**Maintained by:** STEWARD Badge  
**Authority:** ARBITER reviews; Founder approves

---

## 1. PURPOSE
[What is this system for?]

---

## 2. RULES
[What are the constraints and limitations?]

---

## 3. BEHAVIOR
[How does this system act across all realities?]

---

## 4. INTEGRATION
[How does this connect to other systems?]

---

## 5. LEAK PREVENTION
[What should never be revealed about the internals?]

---

**See also:** [Related specs and canonical files]
```

---

**These scrolls make the cathedral function.**

**They describe the machinery beneath the marble.**

**They must be precise, audited, and true.**
