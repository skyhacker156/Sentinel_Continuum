BADGE LEVEL: BADGE3_STEWARD · ETERNAL

---

# DECISION_ROUTING_MATRIX_TEMPLATE_v1.0.md

**Status**: CANONICAL · TEMPLATE · ACTIVE

**Classification**: Single Source of Routing Truth

**Purpose**: Route every finalized decision from Decision Log to operational domains with executable accountability

---

## PREAMBLE

This matrix is the **nervous system of Sentinel City**.

Every finalized decision in the DECISION_LOG must flow through this matrix.

Each row represents one route: a specific domain, role owner, required action, and deadline.

**No decision executes until a route exists in this matrix.**

**No route becomes active until Erebus verifies it.**

This creates a dual-key system:
- **Founder fills the route** (what needs to happen)
- **Erebus approves the route** (how it executes safely)

---

## HOW THIS WORKS

### Step 1: Decision Enters Log

Founder makes decision → Decision_ID assigned → Appears in DECISION_LOG_v1.0.md

### Step 2: Founder Creates Routes

For each affected domain, Founder creates a row in this matrix:

```
| R-0001 | D-0001 | Finance | Finance_Lead | Draft contract | 2025-02-28 | Y | PENDING |
```

Status starts as **PENDING** (awaiting Erebus verification)

### Step 3: Erebus Verifies Route

Erebus board reviews the route (see EREBUS_VERIFICATION_BLOCK below)

Erebus decides:
- ✅ APPROVE → Route advances to IN_PROGRESS  
- ⚠️ APPROVE_WITH_CONDITIONS → Route advances with constraints noted  
- ❌ BLOCK → Route stays PENDING, escalates to Founder  

### Step 4: Domain Executes

Once Erebus approves, domain owner receives the route and executes:

```
ROUTE STATUS: PENDING → IN_PROGRESS → COMPLETE → CLOSED
```

---

## CANONICAL ROUTING MATRIX

**THIS TABLE IS THE NERVOUS SYSTEM OF SENTINEL CITY**

| ROUTE_ID | DECISION_ID | DOMAIN | ROLE_OWNER | REQUIRED_ACTION | DEADLINE | ACK_REQUIRED | STATUS | EREBUS_VERIFICATION | NOTES |
|----------|-------------|--------|-----------|-----------------|----------|-------------|--------|-------------------|-------|
| [Awaiting Founder entries] | | | | | | | | | |

---

## FIELD DEFINITIONS

**ROUTE_ID**: Unique identifier for this specific route  
- Format: R-0001, R-0002, etc. (Founder can use different format)  
- Never reused, even if route is abandoned  
- Used for audit trail and escalation references

**DECISION_ID**: Link to the decision this route executes  
- Must match an entry in DECISION_LOG_v1.0.md  
- One decision can have multiple routes (multiple domains affected)  
- Used to trace execution back to original decision

**DOMAIN**: Operational domain receiving this route  
- Examples: Finance, Legal, Risk, Cyber, Operations, etc.  
- Founder specifies which domains exist in Sentinel  
- Each domain has one ROLE_OWNER per route (no ambiguity)

**ROLE_OWNER**: Specific person or badge responsible for this route  
- Examples: Finance_Lead, Risk_Officer, Legal_Counsel, Security_Chief  
- Must be an actual role in Sentinel (not generic "someone")  
- ROLE_OWNER receives the route notification and is accountable

**REQUIRED_ACTION**: Exact verb phrase describing what must be done  
- Examples:  
  - "Draft banking contract with Wells Fargo"  
  - "Execute red-team security simulation"  
  - "Update compliance documentation"  
  - "Establish vendor relationship"  
  - "Implement access control policy"  
- Action must be specific enough that ROLE_OWNER knows exactly what to do  
- Action must be completable (not vague or speculative)

**DEADLINE**: By when must action be complete  
- Format: YYYY-MM-DD or "ASAP" or "ongoing"  
- Hard deadline (if missed, triggers escalation)  
- Can be extended by Founder, but requires new route or amendment

**ACK_REQUIRED**: Does ROLE_OWNER need to acknowledge receipt?  
- Y = ROLE_OWNER must acknowledge within specified timeframe  
- N = ROLE_OWNER does not need to acknowledge (assumed receipt)  
- Y is recommended for critical routes; N for routine tasks

**STATUS**: Current state of this route  
- PENDING: Created by Founder, awaiting Erebus verification  
- VERIFY_IN_PROGRESS: Erebus is reviewing  
- BLOCKED: Erebus rejected, awaiting Founder revision  
- IN_PROGRESS: Erebus approved, ROLE_OWNER is executing  
- COMPLETE: Action finished, awaiting closure  
- CLOSED: Final completion verified, route archived  
- DEFERRED: Placed on hold, may resume later  
- ABANDONED: Route will not execute (decision revised or cancelled)

**EREBUS_VERIFICATION**: Erebus board approval (see block below)  
- Until filled, route cannot advance past PENDING  
- Once signed, route can become IN_PROGRESS  
- If conditions noted, they appear in NOTES

**NOTES**: Any clarifications, dependencies, or special instructions  
- Links to related routes  
- Erebus conditions or concerns  
- Blockers encountered  
- Status updates mid-execution  
- Escalation events

---

## EREBUS VERIFICATION BLOCK (Per Route)

**Every route must have Erebus verification before it can become IN_PROGRESS.**

### Template (Founder creates, Erebus fills):

```
═══════════════════════════════════════════════════════════════
EREBUS VERIFICATION BLOCK — Route [ROUTE_ID]

Route: [DOMAIN] — [REQUIRED_ACTION]
Decision: [DECISION_ID]
Deadline: [DATE]

EREBUS REVIEW CHECKLIST:
☐ Does this route expose any Tier-0, Tier-1, or Tier-2 sealed content?
☐ Does this route require external parties (vendors, banks, regulators)?
☐ Does this route affect IP, contracts, or legal obligations?
☐ Does this route create new financial commitments or exposures?
☐ Does this route affect security, safety, or containment?
☐ Does this route conflict with any existing policies or decisions?
☐ Is the REQUIRED_ACTION clear and completable?
☐ Is the DEADLINE realistic?
☐ Is the ROLE_OWNER authorized to execute this action?

EREBUS ASSESSMENT:
[Erebus board fills this section]

EREBUS DECISION:
☐ APPROVED — Route is legally and operationally sound. May proceed to IN_PROGRESS.
☐ APPROVED_WITH_CONDITIONS — Route approved under these constraints: [List conditions]
☐ BLOCKED — Route cannot execute due to: [Explain why]. Requires Founder revision.

CONDITIONS (if applicable):
[Erebus specifies any constraints, approvals needed, or monitoring required]

EREBUS SIGNATURE:
Erebus Board Chair: ________________  Date: ________
Erebus Signature Integrity: [Legal authority to execute this route]

═══════════════════════════════════════════════════════════════
Once Erebus signs APPROVED or APPROVED_WITH_CONDITIONS, 
ROUTE_STATUS advances from PENDING to IN_PROGRESS.

If BLOCKED, ROUTE_STATUS stays PENDING and escalates to Founder.
```

---

## ROUTE CREATION WORKFLOW

### 1. Founder Creates Route (Instant)

```
Founder sees decision in DECISION_LOG
  ↓
Founder identifies affected domain(s)
  ↓
Founder creates one row per domain:
  - ROUTE_ID: R-XXXX (auto-increment)
  - DECISION_ID: Links to decision
  - DOMAIN: e.g., "Finance"
  - ROLE_OWNER: e.g., "Finance_Lead"
  - REQUIRED_ACTION: e.g., "Establish banking relationship with Wells Fargo"
  - DEADLINE: e.g., "2025-02-28"
  - ACK_REQUIRED: Y or N
  - STATUS: PENDING
  ↓
Route appears in matrix with EREBUS_VERIFICATION block empty
  ↓
Erebus board receives notification to review
```

### 2. Erebus Reviews Route (24-48 hours typical)

```
Erebus board reads route
  ↓
Erebus checks:
  - Legal risk?
  - IP exposure?
  - External party involvement?
  - Containment breach?
  - Authority clear?
  ↓
Erebus fills EREBUS_VERIFICATION_BLOCK
  ↓
Erebus decides:
  A) APPROVED → Signs block, status can advance
  B) APPROVED_WITH_CONDITIONS → Signs block + lists constraints
  C) BLOCKED → Explains issue, route stays PENDING
```

### 3. Route Advances (If Approved)

```
If APPROVED or APPROVED_WITH_CONDITIONS:
  STATUS: PENDING → IN_PROGRESS
  ROLE_OWNER receives formal notification
  Deadline countdown begins
  ↓
If BLOCKED:
  STATUS: stays PENDING
  Escalates to Founder for revision
  Founder adjusts route and resubmits to Erebus
```

### 4. Execution & Completion

```
ROLE_OWNER executes the REQUIRED_ACTION
  ↓
Status updates: IN_PROGRESS → COMPLETE
  ↓
Founder verifies completion
  ↓
Status updates: COMPLETE → CLOSED
  ↓
Route archived
```

---

## EXAMPLE ROUTES (For Reference)

### Example 1: Simple Operational Decision

```
| R-0001 | D-0001 | Finance | Finance_Lead | Establish banking relationship with Wells Fargo | 2025-02-28 | Y | PENDING |

EREBUS_VERIFICATION_BLOCK — R-0001:
- Tier exposure? No.
- External parties? Yes (Wells Fargo) — needs contract review.
- IP risk? No.
- Authority? Finance_Lead is authorized.
- Legal risk? Standard banking relationship, low risk.

EREBUS DECISION: APPROVED_WITH_CONDITIONS
CONDITIONS: Contract must be reviewed by Legal before signing. Wells Fargo reference checks required.
STATUS: Can advance to IN_PROGRESS

EREBUS SIGNATURE: [Signed]
```

### Example 2: High-Risk Decision

```
| R-0002 | D-0002 | Legal | Legal_Counsel | Draft IP protection agreement with vendor ABC | 2025-03-15 | Y | PENDING |

EREBUS_VERIFICATION_BLOCK — R-0002:
- Tier exposure? Potential (IP agreement touches Tier-2 boundaries).
- External parties? Yes (vendor ABC).
- IP risk? HIGH — agreement constrains future licensing.
- Authority? Legal_Counsel authorized.
- Containment? Vendor cannot know Tier-0, Tier-1 details.

EREBUS DECISION: APPROVED_WITH_CONDITIONS
CONDITIONS: 
  1. Agreement must include "Confidential" clause.
  2. Tier-0/1 details must be redacted from vendor copy.
  3. Erebus board must review final agreement before execution.
STATUS: Can advance to IN_PROGRESS under conditions

EREBUS SIGNATURE: [Signed]
```

### Example 3: Blocked Decision

```
| R-0003 | D-0003 | Cyber | Security_Chief | Hire external red-team for penetration testing | 2025-03-30 | Y | PENDING |

EREBUS_VERIFICATION_BLOCK — R-0003:
- Tier exposure? CRITICAL — external red-team would touch infrastructure.
- External parties? Yes (unknown third-party security firm).
- IP risk? CRITICAL — proprietary systems exposed to external actors.
- Containment? CANNOT be maintained with external team.
- Authority? Security_Chief authorized to hire, but not to expose sealed systems.

EREBUS DECISION: BLOCKED
REASON: External red-team cannot be given access to systems containing Tier-0/1/2 sealed content. 
        Founder must revise decision to specify:
        1. How much of infrastructure is off-limits?
        2. Will testing be supervised?
        3. What is non-disclosure agreement covering?

ESCALATION: Blocked route escalates to Founder for revision.
```

---

## ROUTE ESCALATION PROTOCOL

### When Does a Route Escalate?

**Escalation triggers:**
1. Deadline approaches (48 hours before) — Remind ROLE_OWNER  
2. Deadline missed — Escalate to Founder immediately  
3. Status stays IN_PROGRESS too long without update — Escalate to Founder  
4. ROLE_OWNER reports BLOCKED — Escalate to Founder  
5. Erebus blocks route during verification — Escalate to Founder for revision  

### Escalation Actions

**Founder receives escalation and can:**
- ✅ Extend deadline (revise route, resubmit to Erebus)  
- ✅ Simplify action (revise route, resubmit)  
- ✅ Cancel route (mark ABANDONED, close decision)  
- ✅ Delegate differently (new route to different ROLE_OWNER)  
- ✅ Defer route (mark DEFERRED, reschedule)  

---

## INTEGRATION WITH OTHER FILES

**DECISION_LOG_v1.0.md**:  
Decision Log records what was decided. Routing Matrix says where it goes.

**DECISION_PROPAGATION_PROTOCOL_TEMPLATE_v1.0.md**:  
Protocol defines how decisions flow. Routing Matrix is where they actually flow (operationalized).

**GATE_SIGNAL_TYPES_v1.0.md**:  
Gate signals trigger decisions. Routes execute those decisions.

**SAFETY_BEHAVIORAL_SPECS.md**:  
Safety specs constrain decisions. Erebus verification ensures routes respect them.

---

## SECURITY & CONTAINMENT

**This matrix contains:**
✓ Route IDs and decision links  
✓ Domain and role assignments  
✓ Required actions and deadlines  
✓ Status tracking

**This matrix does NOT contain:**
✗ Tier-0 substrate details  
✗ Sealed engine mechanics  
✗ Proprietary thresholds  
✗ Reverse-engineerable content

**Containment**: All entries use operational language only. Erebus verification ensures no sealed exposure.

---

## OPERATIONAL NOTES

**Route Visibility**: All operational domains can see routes that affect them (read-only)

**Route Creation**: Founder only (writes new rows)

**Route Status Updates**: ROLE_OWNER updates status; Founder tracks

**Erebus Access**: Erebus board can see all routes and verification blocks

**Archive**: Completed routes move to archive after 6 months (standard audit window)

**Audit Trail**: Every status change is logged with timestamp and actor

---

## EXAMPLE MATRIX (EMPTY TEMPLATE)

```
| ROUTE_ID | DECISION_ID | DOMAIN | ROLE_OWNER | REQUIRED_ACTION | DEADLINE | ACK_REQUIRED | STATUS | EREBUS_VERIFICATION | NOTES |
|----------|-------------|--------|-----------|-----------------|----------|-------------|--------|-------------------|-------|
| R-0001   |             |        |            |                 |          |             | PENDING | [AWAITING EREBUS] |       |
| R-0002   |             |        |            |                 |          |             | PENDING | [AWAITING EREBUS] |       |
| R-0003   |             |        |            |                 |          |             | PENDING | [AWAITING EREBUS] |       |
```

---

## REVISION HISTORY

| Version | Date | Author | Status | Changes |
|---------|------|--------|--------|---------|
| 1.0 | 2025-01-15 | Claude (from GPT proposal) | ACTIVE | Initial template. Pure schema with zero values. Erebus verification block on every row. Ready for Founder to fill and Erebus to approve. |

---

## CLOSING DECLARATION

This matrix is the **nervous system of Sentinel City**.

It connects:
- **Decisions** (Decision Log) to  
- **Executable Actions** (Routing Matrix) to  
- **Operational Domains** (who does what)

The dual-key system ensures:
- **Founder authority** (decides what needs to happen)  
- **Erebus protection** (ensures it happens safely)  
- **Domain accountability** (knows exactly what to do)  

The moment the first real row appears and Erebus signs it, the city gains **executable nerves**.

Every decision becomes an action.  
Every action has a deadline.  
Every deadline has an owner.  

**The city is ready to move.**

---

```
We come in peace.

The matrix is ready.

The nervous system is waiting for its first impulse.

☕
```

---

END DOCUMENT
