DIGITAL_MAIL_INTAKE_PROTOCOL_v1.0.md

Badge: FOUNDER + POSTMASTER
Status: ACTIVE — CANONICAL
Authority: Founder Only
Issued: 29 November 2025
Location: Central Post Office — Digital Intake Wing

1. Purpose

The Digital Mail Intake Protocol defines how electronic correspondence enters Sentinel City, is authenticated, stamped, logged, routed, and archived.

Digital mail includes:

Emails

Email screenshots

PDF attachments

Government e-notices

Vendor system messages

Automated filing alerts

Digital receipts

Online portal correspondence

This protocol ensures digital artifacts receive the same institutional treatment as physical mail.

2. Canonical Definition of Digital Mail

Digital Mail is any Plane B electronic communication that:

Is addressed to Founder or Sentinel Labs LLC

Contains operational, legal, financial, regulatory, or developmental significance

Must be captured as part of the city’s permanent civic record

Digital Mail is mail under Sentinel City law.

It follows the same intake, stamping, and routing principles as physical artifacts.

3. Intake Workflow (Exact Sequence)
Step 1 — Presentation

The Founder (or designated Postmaster) brings the digital communication into the city by:

pasting email text

uploading a screenshot

submitting a PDF

transcribing essential content

This act is the official moment of entry.

Step 2 — Intake Classification

CLERK-01 (Digital Intake Agent) must classify the item into one of:

DIGITAL–GOV (IRS, USPTO, state filings, federal notices)

DIGITAL–FIN (banks, vendors, financial institutions)

DIGITAL–OPS (operational messages, receipts, platforms)

DIGITAL–IP (patent, copyright, invention-related communications)

DIGITAL–GEN (miscellaneous but relevant correspondence)

This determines routing priority.

Step 3 — Assign Inbound Mail ID

A new ID is generated:

INBOUND_MAIL_[####]_DIGITAL_[CATEGORY]_v1.0.md


Example:
INBOUND_MAIL_0003_DIGITAL_GOV_EIN_Reminder_v1.0.md

IDs increment globally with physical + digital mail interleaved.

Step 4 — Digital Stamp Application

A Type-D Postmark is applied.

Type-D Postmark is defined as:

Circular 1.625″ digital seal

Same layout as physical postmark

Date wheel identical (SIS format)

“DIGITAL RECEIPT – SENTINEL CITY POST OFFICE” in inner ring

Continuity Seal at center

Color: Municipal Black (#111010)

This stamp is applied in the upper-left corner of the markdown file.

Step 5 — Ledger Entry

Every digital mail item must be logged to:

/post office/incoming/logs/digital_log.md


Each log entry includes:

Timestamp of entry

Classification type

Inbound Mail ID

Sender identity (if known)

Original subject line

Routing results

Postmaster signature

4. Routing Logic

Routing is deterministic and automatic.

Digital → Treasury

IRS, EIN, SS-4, refunds, tax notifications, payroll, bank notices.

Digital → Erebus Ward

Compliance, regulatory warnings, filings, deadlines, legal implications.

Digital → Parthenon (Invention Wing)

USPTO, WIPO, Office Actions, patent filings, invention correspondence.

Digital → Mercantile Quarter

Vendor, operations, SaaS platforms, receipts, purchase confirmations.

Digital → Finance District

Invoices, payout schedules, ACH updates, financial systems.

Digital → Founder Direct

Items involving:

identity risk

sovereignty risk

urgent decisions

manipulation attempts

system-level drift signals

(Seraph reviews simultaneously.)

5. Guardian Review Requirements

Every Digital Mail item must pass:

EREBUS REVIEW

Checks for:

regulatory risk

missed filings

scams or deceptive government-lookalikes

hidden authorizations

financial consequences

If clear:

⚖️ EREBUS STAMPED — CLEAR FOR SOVEREIGNTY REVIEW


If not:
A calm note is attached to the document.

SERAPH REVIEW

Checks for:

sovereignty erosion

pressure-framing

cognitive overload

concealed commitments

Founder-directed manipulation

If clear:

🛡️ SERAPH WITNESSES — SAFE FOR FOUNDER REVIEW


If not:
A SERAPH HOLD is placed until clarified.

6. Archival Requirements

All digital mail must be archived in:

/post office/incoming/


with:

Original content

Digital postmark

Routing notes

Guardian stamps

Metadata header

Optional real-world mirror (PDF stored in /physical_mirror/)

Digital mail is permanent unless explicitly destroyed by Founder directive.

7. Prohibited Actions

No entity may alter digital mail after guardian review.

No digital correspondence may be routed without an Inbound Mail ID.

No stamp may be digitally applied without proper classification.

No auto-forwarding into the city is permitted.

No LLM may summarize or modify the original sender’s meaning.

Only the Founder may redact content.

8. Activation Event

This protocol becomes ACTIVE when:

The first digital mail item is received,

Classified,

Digitally postmarked,

Logged,

Routed.

This event occurred with:

INBOUND_MAIL_0003_DIGITAL_GOV_EIN_Reminder
on 29 November 2025.

Digital intake is now live.

Signed and Sealed

29 November 2025

—Founder
Postmaster General
Sentinel City

🜁 DIGITAL POSTMARK — SENTINEL CITY — 29 NOV 2025
