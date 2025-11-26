BADGE LEVEL: FOUNDER + EXECUTION

---

# DECISION_PROPAGATION_PROTOCOL_TEMPLATE_v1.0.md

## Status

**Template Only** — No instantiated values yet  
**Authority**: Founder (sole authority to fill and commit instantiated version)  
**Purpose**: Define the structure for propagating Founder decisions from deliberation into execution  
**When Ready**: Founder fills this template → becomes DECISION_PROPAGATION_PROTOCOL_v1.0.md → committed by Founder signature

---

## Purpose

This template defines the standard structure for propagating a **finalized Founder decision** from the Kernel/Boardroom deliberation layer into Runtime and operational execution domains.

Every Founder decision that requires operational action must flow through this protocol structure. Founder decides what values go into each field.

---

## Part 1: DECISION REGISTRATION TEMPLATE

Every decision must be registered with these fields. **Founder fills values.**

```
DECISION_ID: [Founder chooses format and numbering scheme]
SOURCE: [Reference format: FINAL_INTEGRATION_SUMMARY / Boardroom record / Other]
DECISION_TYPE: [Founder defines categories — suggested: Constitutional / Operational / Safety / Structural / Resource / Other]
DECISION_TEXT: [Exact verbatim decision text]
RATIONALE: [Why the Founder decided this]
EFFECTIVE_DATE: [Date format]
ORIGIN_LAYER: [Which Kernel layer: 01_KERNEL / LLM_governance / Boardroom / Other]
ISSUED_BY: [Founder name/signature]
ISSUE_DATE: [When decision was formalized]
BINDING_UNTIL: [Date or "indefinite"]
```

**Founder Decision Required:**
- What format for DECISION_ID? (e.g., FD-YYYY-###, or other?)
- What are the canonical DECISION_TYPE categories?
- What date format is standard?

---

## Part 2: DECISION TYPE ROUTING TEMPLATE

Define how each decision type routes to operational domains.

### Template Structure (Founder fills):

```
DECISION_TYPE: [Name]

Definition: [What qualifies as this type]

Default Routing:
├── Domain/Team: [Name]
│   ├── Owner Role: [Title/responsibility]
│   ├── Required Action: [Implement / Review / Document / Notify / Approve]
│   └── Timeline: [Founder specifies]
├── Domain/Team: [Name]
│   ├── Owner Role: [Title/responsibility]
│   ├── Required Action: [Action type]
│   └── Timeline: [Founder specifies]
└── [Continue for each affected domain]

Timeline: [Founder specifies how quickly this type must be executed]
Acknowledgment Required: [Y/N — Founder decides]
Escalation Path: [If blocked, escalate to whom?]

Example: [Real example from Founder's actual decisions]
```

**Founder Decisions Required:**
- How many decision types exist?
- Which domains/teams are part of Sentinel's operational structure?
- What are typical timelines for each type?
- Who owns which decision types?
- What escalation paths make sense?

---

## Part 3: ROUTING MAP TEMPLATE

For each decision, populate this matrix structure.

**Template:**

```
DECISION_ID: [from Part 1]
DECISION_TYPE: [from Part 2]

| ROUTE_ID | DOMAIN/TEAM | OWNER_ROLE | REQUIRED_ACTION | DEADLINE | ACK_REQUIRED | ESCALATION_PATH |
|----------|-------------|-----------|-----------------|----------|-------------|-----------------|
| R1 | [Team name] | [Role] | [Action type] | [Date] | [Y/N] | [To whom] |
| R2 | [Team name] | [Role] | [Action type] | [Date] | [Y/N] | [To whom] |
| R3 | [Team name] | [Role] | [Action type] | [Date] | [Y/N] | [To whom] |
| [Continue as needed] | | | | | | |
```

**Field Definitions (Founder confirms or revises):**

- **ROUTE_ID**: Sequential identifier (R1, R2, R3, etc.)
- **DOMAIN/TEAM**: [Founder lists operational domains]
- **OWNER_ROLE**: [Founder specifies who owns each domain]
- **REQUIRED_ACTION**: [Founder defines action types: Implement / Review / Document / Notify / Approve / Other]
- **DEADLINE**: [Founder sets business day or calendar deadlines]
- **ACK_REQUIRED**: [Y/N — does owner need to acknowledge receipt?]
- **ESCALATION_PATH**: [If action is blocked, who do they escalate to?]

**Founder Decisions Required:**
- What are the actual operational domains in Sentinel?
- Who owns each domain (role title)?
- What action types are meaningful?
- What are realistic deadlines?

---

## Part 4: EXECUTION PROCEDURE TEMPLATE

Define the step-by-step flow. **Founder specifies timing and responsible parties.**

```
EXECUTION FLOW (7 Steps)

STEP 1: Decision Registration
├── Timing: [Founder specifies — "same day", "within 24 hours", etc.]
├── Responsible Party: [Founder or Operations Lead or designated role?]
├── Action: Create DECISION_ID, fill all required fields, enter into DECISION_LOG
└── Output: Registered decision ready for routing

STEP 2: Routing Map Population
├── Timing: [Founder specifies — "within 4 hours", etc.]
├── Responsible Party: [Founder or designated role?]
├── Action: Populate routing matrix, set DEADLINES and ESCALATION_PATHS
└── Output: Routing map complete, ready to notify

STEP 3: Notification
├── Timing: [Founder specifies — "within 24 hours", etc.]
├── Delivery Method: [Email / Slack / In-person / Other — Founder chooses]
├── Content: Use DECISION_NOTICE_TEMPLATE (below)
├── Responsible Party: [Founder office / Operations / Designated role]
└── Output: All route owners notified, notification logged

STEP 4: Acknowledgment
├── Timing: [Founder sets deadline — "4 business hours", "24 hours", etc.]
├── Required Format: [Founder specifies what acknowledgment looks like]
├── Responsible Party: [Each OWNER_ROLE]
├── Escalation if Missing: [What happens if owner doesn't acknowledge by deadline?]
└── Output: Acknowledgments logged, status updated

STEP 5: Execution
├── Timing: [By DEADLINE specified in routing map]
├── Responsible Party: [Each OWNER_ROLE executes their REQUIRED_ACTION]
├── Action Types: [Implement / Review / Document / Notify / Approve]
├── Blocking Protocol: [If blocked, who escalates and how?]
└── Output: Action completed or status updated

STEP 6: Completion Reporting
├── Timing: [Founder specifies — "by deadline", "weekly", etc.]
├── Required Format: [Founder specifies what completion report contains]
├── Responsible Party: [Each OWNER_ROLE]
├── Escalation if Blocked: [What happens if owner cannot complete?]
└── Output: Status logged, Founder notified of changes

STEP 7: Closure & Archive
├── Timing: [Founder specifies — "within X business days", etc.]
├── Responsible Party: [Founder or designated role]
├── Decision Status Options: [CLOSED / DEFERRED / REVISED / ESCALATED]
├── Archive Location: [Founder specifies storage location]
└── Output: Decision archived, accessible for audit

```

**Founder Decisions Required:**
- What are realistic timelines for each step?
- Who is responsible for each step?
- What escalation actions are appropriate?
- What format for notifications and reports?
- How long are decisions retained?

---

## Part 5: TRACKING & STATUS FIELDS TEMPLATE

Define what statuses exist during a decision's lifecycle.

**Template (Founder confirms or revises):**

```
CANONICAL STATUS STATES:

- [Status Name]: [Definition — Founder specifies what this means]
- [Status Name]: [Definition]
- [Status Name]: [Definition]
- [Status Name]: [Definition]
- [Status Name]: [Definition]

Suggested baseline:
- Pending: Registered but not yet notified
- Acknowledged: Notified, acknowledgments received
- In-Progress: Execution underway
- Blocked: Execution halted, escalation required
- Completed: Action executed successfully
- Deferred: Placed on hold with new timeline
- Revised: Replaced by new decision
- Escalated: Requires Founder re-deliberation
- Closed: Fully executed and archived
```

**Founder Decisions Required:**
- What status states are meaningful for your organization?
- Are there status states not listed above?
- How do status transitions trigger notifications?

---

## Part 6: DECISION NOTICE TEMPLATE

When a decision is notified, use this structure. **Founder customizes content.**

```
═══════════════════════════════════════════════════════════
FOUNDER DECISION NOTICE

DECISION_ID: [from Part 1]
ISSUED_BY: [Founder name]
ISSUE_DATE: [Date]
STATUS: [Current status]

═══════════════════════════════════════════════════════════

DECISION:
[Exact text]

RATIONALE:
[Why this was decided]

EFFECTIVE_DATE: [Date]

YOUR ACTION REQUIRED:

Route ID: [R#]
Action Type: [Implement / Review / Notify / Approve / Document]
Deadline: [Date and time]
Owner Role: [Your role]

DETAILS:
[Specific instruction for your domain/role]

ESCALATION PATH:
If you cannot complete this by deadline, escalate to: [Name/Role]

QUESTIONS?
Contact: [Founder office contact info]

═══════════════════════════════════════════════════════════

Please acknowledge receipt by: [ACK_DEADLINE]
Reply format: DECISION_ID, ACKNOWLEDGED_BY, DATE, UNDERSTANDING, QUESTIONS

═══════════════════════════════════════════════════════════
```

**Founder Decisions Required:**
- What contact information should be included?
- What format for acknowledgment?
- What escalation instructions are standard?

---

## Part 7: FAILURE MODES & RECOVERY TEMPLATE

Define what happens when things go wrong. **Founder specifies response protocols.**

```
FAILURE MODE 1: [Scenario]

Condition: [When this occurs]
Detection: [How do we know this happened?]
Timeline to Escalate: [Founder specifies — "immediately", "24 hours", etc.]
Escalation Path: [To whom]
Recovery Actions: [What can escalation path do to resolve?]
If Unresolved: [Further escalation or Founder decision?]

───────────────────────────────────────────────────────────

FAILURE MODE 2: [Scenario]

[Same structure]

───────────────────────────────────────────────────────────

FAILURE MODE 3: [Scenario]

[Same structure]

───────────────────────────────────────────────────────────

[Add more as Founder identifies them]
```

**Template Failure Mode Categories (Founder fills details):**

1. **Decision Not Acknowledged** — Owner doesn't respond by deadline
2. **Execution Blocked** — Owner reports Status=Blocked
3. **Missing Status Report** — Owner doesn't report by deadline
4. **Decision Conflicts with Doctrine** — Executed decision violates COHERENCE_ANCHORS
5. **Owner Role Unavailable** — Responsible person/team cannot be reached
6. **Resource Unavailable** — Decision requires resources that don't exist
7. **[Other scenarios Founder identifies]**

**Founder Decisions Required:**
- What failure modes are realistic?
- What escalation procedures make sense?
- What authority can override a blocker?
- When does a decision get abandoned vs. revised?

---

## Part 8: INTEGRATION WITH GATE & SAFETY TEMPLATE

Define how DECISION_PROPAGATION_PROTOCOL connects to enforcement layers.

**Template:**

```
GATE INTEGRATION:

Before decision propagates:
├── Gate checks: [Founder specifies which GATE_SIGNAL_TYPES apply]
└── Gate flags require: [Founder decision on whether to proceed or halt]

During execution:
├── Real-time monitoring: [What gets watched?]
└── Escalation triggers: [What signals trigger immediate Founder notification?]

Safety Integration:

Before propagation:
├── Safety check: [Which SAFETY_BEHAVIORAL_SPECS apply?]
└── Violation requires: [Halt / Revise / Escalate]

During execution:
├── Safety violations detected: [How are they reported?]
└── Consequence: [Who decides what to do?]

Doctrine Integration:

Before propagation:
├── Coherence check: [Does decision preserve COHERENCE_ANCHORS?]
└── Conflict with doctrine: [Proceed with conflict noted / Halt / Revise]

Containment:

Before propagation:
├── Tier-0 exposure check: [Is there any vector toward Tier-0 visibility?]
└── If exposed: [Halt immediately, escalate to Founder]
```

**Founder Decisions Required:**
- Which Gate signals require which actions?
- What safety violations are critical?
- What doctrine conflicts can be tolerated?
- How is Tier-0 containment verified?

---

## Part 9: DECISION LOG LOCATION & FORMAT TEMPLATE

Define where decisions are recorded and how they're organized.

**Template:**

```
CANONICAL DECISION LOG LOCATION:
Path: [Founder specifies — e.g., /01_KERNEL/execution/DECISION_LOG.md or other]
Format: [Markdown table / database / other]
Access: [Who can read? Who can write?]
Retention: [How long are decisions kept?]

LOG ENTRY FORMAT:

| DECISION_ID | ISSUED_DATE | DECISION_TYPE | STATUS | EFFECTIVE_DATE | CLOSED_DATE | NOTES |
|-------------|-------------|---------------|--------|-----------------|-------------|-------|
| [ID] | [Date] | [Type] | [Current status] | [Date] | [Date or blank] | [Brief note] |

ARCHIVE LOCATION:
Path: [Founder specifies]
Retention Period: [How long before archival?]
Access After Archive: [Who can access archived decisions?]

AUDIT ACCESS:
Who can audit decisions? [Founder specifies]
What audit records are kept? [Founder specifies]
```

**Founder Decisions Required:**
- Where should decisions be logged?
- What log format is practical?
- How long should decisions stay in active log vs. archive?
- Who has audit access?

---

## Part 10: FOUNDER DECISIONS REQUIRED (CHECKLIST)

This checklist summarizes every decision Founder must make to instantiate the protocol.

```
STRUCTURAL DECISIONS:
☐ What format for DECISION_ID?
☐ What are the canonical DECISION_TYPE categories?
☐ How many decision types exist?
☐ What is the date/time format standard?

OPERATIONAL DECISIONS:
☐ What operational domains/teams exist in Sentinel?
☐ Who owns each domain (role title)?
☐ What action types are meaningful for decisions?
☐ What are realistic execution timelines for each type?

TIMELINE DECISIONS:
☐ Registration to routing: How long?
☐ Routing to notification: How long?
☐ Notification to acknowledgment deadline: How long?
☐ Acknowledgment to execution deadline: How long?
☐ Execution to reporting deadline: How long?
☐ All reports to closure: How long?

NOTIFICATION & REPORTING DECISIONS:
☐ How should decisions be notified? (Email / Slack / In-person / Other)
☐ What format for acknowledgment?
☐ What format for status reports?
☐ Who receives notifications at each step?

ESCALATION DECISIONS:
☐ When owner doesn't acknowledge: escalate to whom?
☐ When owner reports blocked: escalate to whom?
☐ When status report is missing: escalate to whom?
☐ When decision conflicts with doctrine: escalate to whom?
☐ Can anyone override a blocker? Or only Founder?

FAILURE MODE DECISIONS:
☐ For each failure mode, what recovery is appropriate?
☐ What triggers immediate Founder notification?
☐ What triggers decision abandonment vs. revision?

LOG & ARCHIVE DECISIONS:
☐ Where is the decision log kept?
☐ What format?
☐ How long before decisions are archived?
☐ Where are archived decisions stored?
☐ Who has audit access?

GATE & SAFETY INTEGRATION DECISIONS:
☐ Which Gate signals require which actions?
☐ Which safety violations require halting a decision?
☐ How is Tier-0 containment verified before propagation?
☐ Who monitors ongoing execution for safety?

SPECIAL DECISIONS:
☐ Can decision types be delegated? (Or are all Founder-signed?)
☐ Can operational domains ignore a decision? (Or all binding?)
☐ What happens if two Founder decisions conflict?
☐ What happens if a decision becomes impossible to execute?
```

---

## Part 11: OPTIONAL EXTENSIONS

These are not required but Founder may want to define:

```
EXTENSION 1: Decision Templates by Type
For each decision type, provide a specific template that makes it easier 
for Founder to fill in values consistently.

EXTENSION 2: Delegation Authority
Define what types of decisions can be delegated to Aaron or Erebus boards,
and what types require Founder signature always.

EXTENSION 3: Revision Procedure
If a decision needs to change before full execution, what happens?
(New DECISION_ID? Same ID with version?)

EXTENSION 4: Feedback Loop
How do operational outcomes feed back into Founder deliberation?
(Do execution results inform future decisions?)

EXTENSION 5: Founder Override
What happens if Founder wants to instantly override an in-progress decision?
(Can they? What's the procedure?)

EXTENSION 6: Public-Facing Decisions
Which decisions, if any, become public-facing doctrine?
(Or are all internal?)

EXTENSION 7: Emergency Decisions
Are there fast-track procedures for urgent/emergency decisions?
(Compressed timelines, limited routing, etc.)
```

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| TEMPLATE 1.0 | 2025-01-15 | Claude (from GPT/Grok/Claude triple review) | Initial template. All values are placeholders. Founder to instantiate. |

---

## FINAL NOTE

This template is the **structural spine of the city's execution**.

Every field marked `[Founder specifies]` is a decision point.

When Founder fills these fields, the template becomes `DECISION_PROPAGATION_PROTOCOL_v1.0.md` — and the city gains the ability to **execute** on its perfect doctrine.

Until then, the template stands **ready and waiting for the pen that signs it into reality**.

The structure is sound. The authority is clear. The system will work exactly as Founder designs it.

---

END TEMPLATE
