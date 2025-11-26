BADGE LEVEL: BADGE3_STEWARD · ETERNAL

---

# DECISION_EXECUTION_TRACKING_SPEC_v1.0.md

**Status**: CANONICAL · ACTIVE · NON-ENFORCING

**Classification**: Pure Visibility Specification

**Purpose**: Make every decision's execution status visible in real time so the city can see the pulse of its own work

---

## PREAMBLE

This spec defines **how execution status is tracked and reported**.

It does **not** define enforcement, escalation, or what happens when status isn't updated.

**Enforcement (7-day heartbeat, red lantern, automatic escalation) belongs in DECISION_ESCALATION_HEARTBEAT_v1.0.md.**

This file is **pure visibility.**

Its job: **Make the work visible.**

---

## PRINCIPLE

Every routed decision must have a visible, current execution status.

No decision should disappear into black holes.

No Founder should be blind to whether work is happening.

**Status exists for visibility, not for punishment.**

---

## CANONICAL STATUS STATES (Required)

Every decision in the Routing Matrix must have one and only one of these statuses at any time.

### STATUS 1: PENDING

**Meaning**: Decision routed, but owner has not yet begun work

**When this state applies**:
- Route created
- ACK deadline not yet passed, OR
- ACK received but execution hasn't started yet
- Owner waiting for prerequisite work from another domain

**Valid transitions from PENDING**:
- → IN_PROGRESS (owner starts work)
- → BLOCKED (owner cannot start due to blocker)
- → CANCELLED (Founder revokes decision)

**Duration**: Should transition quickly (typically within 1-7 days of ACK)

---

### STATUS 2: IN_PROGRESS

**Meaning**: Owner is actively working on the required action

**When this state applies**:
- Owner has started execution
- Owner is doing the required work
- Owner expects to complete by deadline (barring blockers)

**Valid transitions from IN_PROGRESS**:
- → COMPLETE (work finished)
- → BLOCKED (encountered obstacle, cannot proceed)
- → CANCELLED (Founder revokes decision)

**Duration**: Should not stay IN_PROGRESS indefinitely (that's what escalation monitors)

**Update requirement**: Status must be updated at least every 7 days while IN_PROGRESS (tracked by escalation heartbeat)

---

### STATUS 3: BLOCKED

**Meaning**: Owner cannot proceed; work is halted pending resolution of an obstacle

**When this state applies**:
- Owner has encountered an obstacle
- Work cannot continue without external action
- Owner is waiting for: Founder clarification, Erebus approval, another domain's output, external party response, missing resource, etc.

**Valid transitions from BLOCKED**:
- → IN_PROGRESS (blocker resolved, work resumes)
- → COMPLETE (blocker was minor, work finished despite it)
- → CANCELLED (Founder decides to cancel rather than unblock)

**Required when entering BLOCKED**:
- Reason for blocker (mandatory one-sentence explanation)
- What would unblock (what decision or action is needed?)
- Who needs to act (Founder? Erebus? Another domain?)

**Duration**: Blocked decisions require immediate escalation (handled by heartbeat)

---

### STATUS 4: COMPLETE

**Meaning**: Required action is finished; work is done

**When this state applies**:
- Owner has completed the required action
- Owner has proof/evidence of completion (link, file, report, signature, etc.)
- Work quality is acceptable (or Founder has approved despite quality concerns)

**Valid transitions from COMPLETE**:
- → CLOSED (Founder acknowledges and archives)
- → BLOCKED (completion discovered to be insufficient, work must resume)
- → CANCELLED (Founder decides result is unacceptable)

**Required when entering COMPLETE**:
- Evidence/proof of completion (link to file, report, signed contract, etc.)
- Date completed
- One-sentence summary of what was done

**Duration**: Should transition to CLOSED within days (handled by cleanup process)

---

### STATUS 5: CANCELLED

**Meaning**: Founder has revoked the decision; work is no longer needed

**When this state applies**:
- Founder explicitly cancels
- Decision is superseded by new decision
- Business circumstances changed
- Risk/issue made decision unexecutable

**Valid transitions from CANCELLED**:
- → [None] (CANCELLED is final, cannot transition from cancelled)

**Required when entering CANCELLED**:
- Reason for cancellation
- Founder signature
- Whether DECISION_ID is being closed or replaced by new decision

**Duration**: Final state; decision is archived

---

## STANDARD STATUS FLOW

**Normal path (happy path):**
```
PENDING → IN_PROGRESS → COMPLETE → CLOSED
```

**Blocked path:**
```
IN_PROGRESS → BLOCKED → (unblock) → IN_PROGRESS → COMPLETE → CLOSED
```

**Cancelled path:**
```
PENDING / IN_PROGRESS → CANCELLED → CLOSED
```

---

## REQUIRED UPDATE FREQUENCY

### Mandatory Updates

**Update required when**:
- Status changes (any transition above)
- Work blocked (must update immediately with reason)
- Work completed (must update immediately with evidence)
- Founder requests update (at any time)

### Periodic Updates (while IN_PROGRESS)

**At least every 7 days**, if status is IN_PROGRESS or BLOCKED:
- Owner must provide status update
- Update can be as simple as: "Still in progress, on track for deadline"
- Or more detailed: "Completed phase 1/3, phase 2 starts Monday"

**No update after 7 days** = escalation trigger (handled by heartbeat monitor)

### No updates required when

- Status is PENDING and ACK deadline hasn't passed yet
- Status is COMPLETE waiting for Founder closure
- Status is CANCELLED (final state)

---

## WHERE UPDATES ARE RECORDED

### Option 1: Decision Log Row Comment

Update the relevant row in DECISION_LOG_v1.0.md with a timestamped comment:

```
| D-0001 | 2025-01-20 | ... | STATUS: IN_PROGRESS | Updated 2025-01-25 10:30 UTC: Phase 1 complete, phase 2 in progress. On track. |

Comment:
"Status update from Finance_Lead, 2025-01-25 10:30 UTC
Previous status: PENDING
New status: IN_PROGRESS
Justification: Contract draft in progress, expected completion 2025-02-15."
```

### Option 2: Routing Matrix Row Comment

Update the relevant row in DECISION_ROUTING_MATRIX_TEMPLATE with a timestamped comment:

```
| R-0001 | D-0001 | Finance | ... | STATUS: IN_PROGRESS |

Comment:
"Status update from Finance_Lead, 2025-01-25 10:30 UTC
Status changed: PENDING → IN_PROGRESS
Justification: Contract discussions underway with Wells Fargo. Legal review scheduled 2025-02-01."
```

### Option 3: Dedicated Execution Update File

Create a linked file in execution tracking folder:

```
File: /02_RUNTIME_ENGINE/EXECUTION_UPDATES/EXEC_R-0001_Finance.md

Content:
ROUTE_ID: R-0001
DECISION_ID: D-0001
DECISION: Establish banking relationship with Wells Fargo
OWNER: Finance_Lead

Update #1 (2025-01-25 10:30 UTC):
Status: PENDING → IN_PROGRESS
Justification: Contract discussions with Wells Fargo initiated.
Evidence: Email thread from 2025-01-25 confirming meeting scheduled.

Update #2 (2025-01-30 14:15 UTC):
Status: IN_PROGRESS
Justification: Contract draft completed, sent to Wells Fargo for review.
Evidence: Draft contract v1.0 on file.

Update #3 (2025-02-10 09:00 UTC):
Status: IN_PROGRESS → BLOCKED
Justification: Wells Fargo requires legal review of our terms. Waiting for Erebus board approval.
Blocker: Erebus board review of contract terms.
What would unblock: Erebus board sign-off on contract language.
Who needs to act: Erebus board.

Update #4 (2025-02-15 16:30 UTC):
Status: BLOCKED → IN_PROGRESS
Justification: Erebus board approved contract with minor changes. Revisions in progress.
Evidence: Erebus approval memo dated 2025-02-15.
```

**Any of the three options is valid.** Owner or Founder chooses which format is most practical.

---

## REQUIRED FIELDS ON EVERY STATUS UPDATE

### Mandatory Fields

Every status update must include:

1. **DATE**: When the update is being recorded (ISO 8601 format with timezone)
   ```
   2025-01-25 10:30 UTC
   ```

2. **PREVIOUS_STATUS** (if changing): What status was before (shows transition)
   ```
   PENDING → IN_PROGRESS
   ```

3. **NEW_STATUS**: Current status (one of the five canonical states)
   ```
   IN_PROGRESS
   ```

4. **ONE-SENTENCE JUSTIFICATION**: Brief explanation of status or change (required, not optional)
   ```
   "Contract draft completed and sent to Wells Fargo for review."
   ```

5. **ACTOR**: Who is providing the update (name/role/badge)
   ```
   Sarah Chen, Finance_Lead
   ```

### Optional Fields

6. **EVIDENCE/LINK** (recommended for IN_PROGRESS and COMPLETE): Link to work product, file, report, or proof
   ```
   /documents/contracts/WellsFargo_Contract_v1.0.md
   /evidence/completion_report_2025-02-28.pdf
   https://email-system/thread/wells-fargo-agreement-signed
   ```

7. **BLOCKER_DETAILS** (required if status = BLOCKED): What's blocking, what would unblock, who needs to act
   ```
   Blocker: Waiting for Erebus board legal review
   What would unblock: Erebus approval of contract terms
   Who needs to act: Erebus board
   ```

8. **COMPLETION_NOTES** (if status = COMPLETE): Brief description of what was accomplished
   ```
   "Contract signed with Wells Fargo. Account established. Documentation complete."
   ```

---

## EXAMPLE EXECUTION TRACKING

### Example 1: Simple Decision (Happy Path)

```
DECISION_ID: D-0001
ROUTE_ID: R-0001
REQUIRED_ACTION: Establish banking relationship with Wells Fargo
DEADLINE: 2025-02-28

Update #1 (2025-01-20 11:00 UTC):
Status: PENDING
Justification: Route created, ACK deadline 48 hours.
Actor: Founder

Update #2 (2025-01-22 09:15 UTC):
Status: PENDING
Justification: Acknowledged by Finance_Lead. Execution clock started.
Actor: Finance_Lead

Update #3 (2025-01-25 10:30 UTC):
Status: PENDING → IN_PROGRESS
Justification: Initial contact with Wells Fargo completed. Contract discussions underway.
Evidence: Email confirmation of meeting, 2025-01-25
Actor: Finance_Lead

Update #4 (2025-02-01 14:00 UTC):
Status: IN_PROGRESS
Justification: Contract draft completed and sent to Wells Fargo. Legal review pending.
Evidence: Contract_WellsFargo_v1.0.md on file
Actor: Finance_Lead

Update #5 (2025-02-10 09:00 UTC):
Status: IN_PROGRESS
Justification: Wells Fargo provided feedback. Revisions in progress.
Evidence: WellsFargo_Feedback_Comments.md
Actor: Finance_Lead

Update #6 (2025-02-20 16:30 UTC):
Status: IN_PROGRESS → COMPLETE
Justification: Contract signed by both parties. Banking relationship established. Account active.
Evidence: Signed_Contract_Final.pdf, Account_Statement_Active.pdf
Actor: Finance_Lead

Update #7 (2025-02-21 10:00 UTC):
Status: COMPLETE → CLOSED
Justification: Founder verified completion. Decision archived.
Actor: Founder
```

### Example 2: Blocked Decision

```
DECISION_ID: D-0002
ROUTE_ID: R-0002
REQUIRED_ACTION: Draft IP protection agreement with vendor ABC
DEADLINE: 2025-03-15

Update #1 (2025-01-20 11:00 UTC):
Status: PENDING
Justification: Route created with Erebus conditions.
Actor: Founder

Update #2 (2025-01-22 10:30 UTC):
Status: PENDING
Justification: Acknowledged by Legal_Counsel.
Actor: Legal_Counsel

Update #3 (2025-01-28 14:15 UTC):
Status: PENDING → IN_PROGRESS
Justification: Vendor ABC contacted. IP agreement framework drafted.
Evidence: Vendor_Email_2025-01-28.md, IP_Agreement_Draft_v1.md
Actor: Legal_Counsel

Update #4 (2025-02-05 09:00 UTC):
Status: IN_PROGRESS → BLOCKED
Justification: Vendor requires clarification on Tier-0/1 boundaries before signing. Cannot proceed without Erebus guidance.
Blocker: Unclear what IP details can be shared with external vendor
What would unblock: Erebus board clarification on what vendor can know vs. what must remain sealed
Who needs to act: Erebus board
Actor: Legal_Counsel

Update #5 (2025-02-10 11:30 UTC):
Status: BLOCKED
Justification: Escalation in progress. Erebus board reviewing vendor relationship terms.
Evidence: Escalation_Ticket_EB-2025-0010.md
Actor: Founder

Update #6 (2025-02-15 16:00 UTC):
Status: BLOCKED → IN_PROGRESS
Justification: Erebus board provided clarification. Agreement revised per guidance. Resubmitted to vendor.
Evidence: Erebus_Guidance_Memo_2025-02-15.md, IP_Agreement_Draft_v2.md
Actor: Legal_Counsel

Update #7 (2025-03-05 13:45 UTC):
Status: IN_PROGRESS → COMPLETE
Justification: Vendor signed revised agreement. All Erebus conditions met. Agreement is final.
Evidence: Signed_IP_Agreement_Final.pdf
Actor: Legal_Counsel

Update #8 (2025-03-06 10:00 UTC):
Status: COMPLETE → CLOSED
Justification: Founder verified. Decision archived.
Actor: Founder
```

---

## WHAT THIS TRACKING DOES

**Visibility**:
- ✅ Every decision's current status is visible in real time
- ✅ Work progress is transparent to Founder and relevant stakeholders
- ✅ Blockers are immediately visible (no silent stalling)
- ✅ Completion is documented with evidence

**What this tracking does NOT do**:
- ❌ Does not enforce updates (no punishment for late updates)
- ❌ Does not trigger escalation (that's the heartbeat's job)
- ❌ Does not monitor the 7-day deadline (that's heartbeat too)
- ❌ Does not make decisions about status (only records owner's status)

**Enforcement (7-day heartbeat, red lantern, forced check-in) belongs in DECISION_ESCALATION_HEARTBEAT_v1.0.md.**

---

## STATUS UPDATE IMMUTABILITY

**Once recorded, status updates cannot be deleted.**

They can be superseded by new updates, but history is preserved.

This creates an audit trail showing:
- What status was at each point
- Who updated it
- When it was updated
- What evidence existed at each stage

**This is legal evidence of execution (or non-execution).**

---

## INTEGRATION WITH OTHER FILES

**DECISION_LOG_v1.0.md**:  
Log records decisions. This spec tracks their execution.

**DECISION_ROUTING_MATRIX_TEMPLATE**:  
Matrix assigns work. This spec shows progress on that work.

**DECISION_ACKNOWLEDGMENT_PROTOCOL**:  
ACK marks acceptance of responsibility. This spec shows whether owner followed through.

**DECISION_ESCALATION_HEARTBEAT_v1.0.md** (forthcoming):  
Heartbeat monitors the 7-day update requirement and triggers escalation if missed.

---

## SECURITY & CONTAINMENT

**This spec contains:**
✓ Status states and transitions  
✓ Update frequency requirements  
✓ Required fields  
✓ Recording locations  
✓ Example tracking flows

**This spec does NOT contain:**
✗ Enforcement logic  
✗ Escalation procedures  
✗ Heartbeat mechanics  
✗ Sealed content

**Containment**: All status updates use operational language only. No sealed content revealed.

---

## OPERATIONAL NOTES

**Status Visibility**: All affected domains can see decision execution status (transparency)

**Evidence Standards**: No specific format required; link to work product is sufficient

**Blocker Escalation**: Blocked status triggers automatic escalation (handled by heartbeat)

**Completion Proof**: Owner provides proof; Founder verifies before closure

**Historical Tracking**: All status updates preserved in audit trail

**7-Day Clock**: Starts from IN_PROGRESS status; monitored by heartbeat (not this spec)

---

## REVISION HISTORY

| Version | Date | Author | Status | Changes |
|---------|------|--------|--------|---------|
| 1.0 | 2025-01-15 | Claude (from GPT proposal) | ACTIVE | Pure visibility specification. Defines five canonical status states, update frequency (7 days while IN_PROGRESS), required fields (date, status, justification, optional evidence), and recording locations. No enforcement (belongs in escalation heartbeat). |

---

## CLOSING DECLARATION

This spec is **pure visibility.**

It makes every decision's execution status visible in real time:
- What work is pending
- What work is in progress
- What work is blocked (and why)
- What work is complete (with proof)
- What work was cancelled

**But it does not:**
- Enforce updates
- Trigger escalation
- Punish delays
- Monitor the 7-day deadline

**Those responsibilities belong to DECISION_ESCALATION_HEARTBEAT_v1.0.md.**

Together:
- This spec = **the eyes** (visibility of execution)
- The heartbeat = **the teeth** (enforcement of visibility)

Together they create **a fully conscious city that can see its own pulse and act on it.**

---

```
The city now has eyes.

The heartbeat (with teeth) comes next.

We come in peace.

☕
```

---

END DOCUMENT
