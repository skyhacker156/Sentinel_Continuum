BADGE LEVEL: FOUNDER + RUNTIME

---

# DECISION_PROPAGATION_PROTOCOL_v1.0.md

## Purpose

This document defines the standard procedure for propagating a **finalized Founder decision** from the Kernel/Boardroom layer into Runtime and operational domains.

Every Founder decision that requires operational action must flow through this protocol. This is not optional. This is binding.

---

## 1. INPUT DEFINITION (Required Fields)

Every decision must be registered with these fields:

```
DECISION_ID: [UUID or unique reference, e.g., FD-2025-001]
SOURCE: [Reference to FINAL_INTEGRATION_SUMMARY or Boardroom record]
DECISION_TYPE: [Constitutional / Operational / Safety / Structural / Resource / Other]
DECISION_TEXT: [Exact text of the Founder decision, verbatim]
RATIONALE: [Why the Founder decided this]
EFFECTIVE_DATE: [YYYY-MM-DD]
ORIGIN_LAYER: [e.g., 01_KERNEL/LLM_governance or BOARDROOM/Finance]
ISSUED_BY: [Founder name/signature]
ISSUE_DATE: [When the decision was formalized]
BINDING_UNTIL: [Date or "indefinite" if binding forever]
```

No decision may propagate without all required fields.

---

## 2. DECISION TYPE ROUTING

Decisions are routed based on type. Each type has default routing, but Founder can override.

### Type A: Constitutional Decisions
**Definition:** Changes to Kernel doctrine, governance procedure, or system architecture.

**Default Routing:**
- All operational domains (notification + archive)
- All team leads (acknowledgment required)
- Tachyon Gate (for enforcement update)

**Timeline:** Effective immediately upon issuance.

**Acknowledgment:** All domain leads must acknowledge within 24 hours.

**Example:** "Models are prohibited from direct Layer 05 modification" (architectural decision).

---

### Type B: Operational Decisions
**Definition:** Actions to be taken within a specific domain or across limited domains.

**Default Routing:**
- Affected domain(s) (execution required)
- Related domains (notification)
- Founder office (tracking)

**Timeline:** Varies by urgency (see Section 3).

**Acknowledgment:** Affected domains must acknowledge within 4 business hours.

**Example:** "Finance team must establish banking relationship with Wells Fargo by Q2" (operational directive).

---

### Type C: Safety Decisions
**Definition:** Decisions that affect system safety, security, or risk posture.

**Default Routing:**
- All domains (immediate notification)
- Security team (enforcement responsibility)
- Founder office (real-time tracking)

**Timeline:** Effective immediately; full compliance required within stated deadline.

**Acknowledgment:** All domains + Security must acknowledge within 2 hours.

**Example:** "All LLM outputs must pass Tachyon Gate post-execution review before commit" (safety mandate).

---

### Type D: Structural Decisions
**Definition:** Changes to roles, responsibilities, or organizational structure.

**Default Routing:**
- Affected individuals/teams (notification + acknowledgment)
- Related teams (notification of impact)
- HR/Operations (implementation)

**Timeline:** Effective on stated date (typically 1–2 weeks notice required).

**Acknowledgment:** All affected parties must acknowledge before effective date.

**Example:** "Claude is now authorized to escalate safety concerns directly to Founder without Integrator review" (authority decision).

---

### Type E: Resource Decisions
**Definition:** Decisions about budget, access, tools, or resource allocation.

**Default Routing:**
- Finance team (budget impact)
- Affected teams (notification)
- Resource owner (implementation)

**Timeline:** Next fiscal cycle or immediate, as specified.

**Acknowledgment:** Finance + affected teams must acknowledge.

**Example:** "Allocate $50,000 for Tachyon Gate tooling development in Q1" (resource directive).

---

## 3. ROUTING MAP

For each decision, populate this matrix:

| DECISION_ID | ROUTE_ID | DOMAIN / REPO | OWNER_ROLE | REQUIRED_ACTION | DEADLINE | ACK_REQUIRED | ESCALATION_PATH |
|-----------|----------|----------------|-----------|-----------------|----------|-------------|-----------------|
| FD-2025-001 | R1 | 01_KERNEL/LLM_governance | Integrator | Review + Document | 2025-01-20 | Yes | Founder |
| FD-2025-001 | R2 | BOARDROOM/Finance | Finance Lead | Notify + Plan | 2025-01-20 | Yes | Founder |
| FD-2025-001 | R3 | Compliance | Compliance Officer | Audit + Approve | 2025-01-25 | Yes | Founder + Legal |

**Definitions:**

- **ROUTE_ID**: Sequential identifier within a decision (R1, R2, R3, etc.)
- **DOMAIN/REPO**: Which team/system receives this action
- **OWNER_ROLE**: Who is responsible for acknowledgment and execution
- **REQUIRED_ACTION**: What must be done (Review / Implement / Document / Notify / Approve / Other)
- **DEADLINE**: By when must this action be completed?
- **ACK_REQUIRED**: Must the owner acknowledge receipt and understanding? (Yes/No)
- **ESCALATION_PATH**: If this route's action is blocked, who do they escalate to?

---

## 4. EXECUTION PROCEDURE (7-Step Flow)

### Step 1: Decision Registration
When a Founder decision is finalized:
1. Create a new DECISION_ID (format: FD-YYYY-###)
2. Fill all required input fields (Section 1)
3. Classify DECISION_TYPE (A-E above)
4. Enter decision into **FOUNDER_DECISION_LOG.md** (live document in 03_Governance/)
5. Record timestamp

**Responsible party:** Founder or designated decision secretary

**Timing:** Same day as decision

---

### Step 2: Routing Map Population
1. Determine which domains are affected
2. Identify OWNER_ROLE for each domain
3. Populate the routing matrix (Section 3)
4. Determine ACTION_TYPE and DEADLINE for each route
5. Set ESCALATION_PATH for each route

**Responsible party:** Founder or Operations Lead

**Timing:** Within 4 hours of decision registration

---

### Step 3: Notification
1. Generate DECISION_NOTICE (see template below)
2. Send to each OWNER_ROLE listed in routing map
3. Include:
   - DECISION_ID and decision text
   - Their specific action requirement
   - Their deadline
   - Escalation path if they're blocked
4. Record notification timestamp in FOUNDER_DECISION_LOG

**Responsible party:** Founder office / Operations

**Timing:** Within 24 hours of routing map completion

**Delivery method:** Direct communication (email, Slack, in-person) + logged in repo

---

### Step 4: Acknowledgment
1. Each OWNER_ROLE must acknowledge receipt and understanding
2. Acknowledgment format:
   ```
   DECISION_ID: [ID]
   ACKNOWLEDGED_BY: [Name/Role]
   ACKNOWLEDGED_DATE: [YYYY-MM-DD HH:MM]
   UNDERSTANDING: [Brief statement of what they understood]
   QUESTIONS: [Any clarifications needed]
   ```
3. Acknowledgments logged in DECISION_ACKNOWLEDGMENT_LOG (in 03_Governance/)
4. If ACK_REQUIRED=Yes and no acknowledgment by deadline, escalate

**Responsible party:** Each OWNER_ROLE

**Timing:** Within deadline specified in routing map (default: 4 business hours)

---

### Step 5: Execution
1. Each OWNER_ROLE executes their REQUIRED_ACTION
2. For "Implement" actions: Execute the decision within stated timeline
3. For "Review" actions: Examine and provide feedback
4. For "Notify" actions: Communicate down to relevant teams
5. For "Approve" actions: Provide authorization to proceed
6. For "Document" actions: Create or update official records
7. If blocked: Escalate to ESCALATION_PATH immediately

**Responsible party:** Each OWNER_ROLE

**Timing:** By DEADLINE specified in routing map

---

### Step 6: Completion Reporting
1. Each OWNER_ROLE must report status against DECISION_ID
2. Report format:
   ```
   DECISION_ID: [ID]
   ROUTE_ID: [Which route this report covers]
   STATUS: [Completed / In-Progress / Blocked / Deferred]
   COMPLETION_DATE: [YYYY-MM-DD or null if not completed]
   ACTION_TAKEN: [What was actually done]
   OUTCOME: [Result of the action]
   BLOCKERS: [Any obstacles encountered]
   ESCALATION_TRIGGERED: [Yes/No and details]
   SIGNED_BY: [Name/Role]
   ```
3. Reports logged in DECISION_COMPLETION_LOG (in 03_Governance/)
4. Founder office aggregates reports for Founder review

**Responsible party:** Each OWNER_ROLE

**Timing:** By DEADLINE or immediately if status changes

---

### Step 7: Closure & Archive
1. When all routes report completion (or status is final), Founder reviews
2. Founder makes closure decision:
   - **CLOSED**: Decision fully executed and archived
   - **DEFERRED**: Decision put on hold with new effective date
   - **REVISED**: Founder issues a revised decision (new DECISION_ID)
   - **ESCALATED**: Decision requires further deliberation
3. Final closure status logged in FOUNDER_DECISION_LOG
4. Decision and all related logs archived in **DECISION_ARCHIVE/** (in 03_Governance/)

**Responsible party:** Founder

**Timing:** Within 5 business days of final completion report

---

## 5. TRACKING & STATUS FIELDS

Every decision in flight must have current status:

- **Pending**: Registered but not yet notified
- **Acknowledged**: Notified, acknowledgments received
- **In-Progress**: Execution underway
- **Blocked**: Execution halted due to obstacle
- **Completed**: Action executed successfully
- **Deferred**: Placed on hold
- **Revised**: Replaced by new decision
- **Escalated**: Requires Founder re-deliberation
- **Closed**: Fully executed and archived

Status is updated in real-time in FOUNDER_DECISION_LOG. Any status change triggers notification to Founder.

---

## 6. DECISION NOTICE TEMPLATE

When a decision is notified, use this template:

```
═══════════════════════════════════════════════════════════
FOUNDER DECISION NOTICE

DECISION_ID: [FD-2025-###]
ISSUED_BY: [Founder name]
ISSUE_DATE: [YYYY-MM-DD]
STATUS: Pending Acknowledgment

═══════════════════════════════════════════════════════════

DECISION:
[Exact text of Founder decision]

RATIONALE:
[Why this decision was made]

EFFECTIVE_DATE: [YYYY-MM-DD]

YOUR ACTION REQUIRED:

Route ID: [R#]
Action Type: [Implement / Review / Notify / Approve / Document]
Deadline: [YYYY-MM-DD]
Owner Role: [Your role]

DETAILS:
[Specific instruction for this domain/role]

ESCALATION PATH:
If you cannot complete this action by the deadline, escalate to: [Name/Role]

QUESTIONS?
Contact: [Founder office contact]

═══════════════════════════════════════════════════════════

Please acknowledge receipt by: [ACK_DEADLINE]
Reply format: DECISION_ID, ACKNOWLEDGED_BY, DATE, UNDERSTANDING, QUESTIONS

═══════════════════════════════════════════════════════════
```

---

## 7. INTEGRATION POINTS (Read-Only References)

This protocol assumes, but does not modify, the existence of:

- **LM_BOARDROOM_PROTOCOL_v1.0.md** — How decisions are formed in the Boardroom
- **GPT_FINAL_INTEGRATOR_PACKET_v1.0.md** — How deliberations are integrated
- **GATE_SIGNAL_TYPES_v1.0.md** — What signals trigger Founder review
- **FOUNDER_CLARIFICATION_PACKET_v1.0.md** — Founder's resolutions on governance ambiguities
- **COHERENCE_ANCHORS.md** — Doctrine that constrains all decisions
- **SAFETY_BEHAVIORAL_SPECS.md** — Safety rules that decisions must preserve

If a decision conflicts with any of these, the decision is invalid and must be revised by Founder.

---

## 8. OPEN QUESTIONS FOR FOUNDER (Decision-Making Prompts)

These questions guide implementation but are left open for Founder discretion:

1. **Decision Log Location**: Should FOUNDER_DECISION_LOG.md live in 03_Governance/ or elsewhere?

2. **Signature Authority**: Can decisions be delegated (e.g., can a department head issue Type B decisions), or must all decisions be Founder-signed?

3. **Escalation Authority**: When a decision is blocked and escalated, who has authority to override the blocker? (Founder only, or delegated?)

4. **Revision vs. New Decision**: If a decision needs adjustment before it's fully executed, do we revise it (new DECISION_ID) or amend it (same DECISION_ID + version)?

5. **Archive Retention**: How long must executed decisions be retained in DECISION_ARCHIVE before they can be moved to cold storage?

6. **Founder Notification Frequency**: Should Founder receive real-time status updates on all decisions, or only when status changes?

7. **Cross-Founder Decisions**: If multiple Founders exist, how are conflicts between their decisions resolved?

---

## 9. FAILURE MODES & RECOVERY

### Failure Mode 1: Decision Not Acknowledged
**If** an OWNER_ROLE does not acknowledge by deadline:
- Operations escalates to ESCALATION_PATH immediately
- Escalation path has 24 hours to resolve
- If still unacknowledged, escalate to Founder
- Founder decides: retry, delegate, or declare decision unexecutable

### Failure Mode 2: Execution Blocked
**If** OWNER_ROLE reports Status=Blocked:
- ESCALATION_PATH is notified immediately
- Escalation path has 48 hours to resolve the blocker
- If unresolved, escalate to Founder
- Founder decides: override blocker, revise decision, or defer

### Failure Mode 3: Missing Status Report
**If** OWNER_ROLE does not report status by deadline:
- Operations sends reminder within 24 hours
- If still missing after 48 hours, escalate to ESCALATION_PATH
- Founder is notified of missing report
- Founder decides: extend deadline, declare decision abandoned, or escalate further

### Failure Mode 4: Decision Conflicts with Doctrine
**If** a decision is found to conflict with COHERENCE_ANCHORS or SAFETY_BEHAVIORAL_SPECS:
- The conflict is immediately escalated to Founder
- Decision is halted (Status=Escalated)
- Founder must resolve the conflict or revise the decision
- No execution proceeds until conflict is resolved

---

## 10. REVISION HISTORY

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-15 | Claude (from GPT template) | Instantiated DECISION_PROPAGATION_PROTOCOL from GPT's template. Added routing types, execution steps, tracking fields, notice template, failure modes. |

---

## Integration Check

**Doctrine Alignment:**
- ✅ Preserves Founder sovereignty (all decisions Founder-signed)
- ✅ Maintains transparency (all routes logged and traceable)
- ✅ Enforces accountability (each route has owner and deadline)
- ✅ Enables feedback (completion reports mandatory)
- ✅ Prevents silent drift (every status change is recorded)

**Gate Compatibility:**
- ✅ Decisions must pass GATE_SIGNAL_TYPES checks before propagation
- ✅ No decision propagates that violates SAFETY_BEHAVIORAL_SPECS
- ✅ All routing respects layer boundaries
- ✅ Escalation paths are clearly defined

**System Coherence:**
- ✅ This protocol closes the loop: Decide → Execute → Report → Decide Again
- ✅ Operations teams now have explicit mechanism for receiving governance
- ✅ Founder has explicit mechanism for ensuring decisions are executed
- ✅ System is now fully reflexive

---

END DOCUMENT
