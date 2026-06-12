# 14 · Data Model & Field Dictionary

> The concrete answer to "what details do people actually need?" This lists every thing the system
> stores, the **fields it holds**, and **who needs each one** — field technician vs. office/admin vs.
> owner. Grounded in research of how real HVAC/plumbing/electrical operations run
> ([sources](#sources--confidence)).

It builds on the [object model spine](03-information-architecture.md) and follows the
[layered philosophy](12-system-layers.md): the **core fields below are the stable spine (Layer 1);
trade-specific details are configurable forms (Layer 3)** — never hard-coded columns. That split is
what lets one system serve HVAC today and a landscaper tomorrow without a rebuild.

**Who-needs-it key:** 🔧 Field technician · 🏢 Office / dispatch / admin · 👑 Owner · 🙋 Customer.
A field can serve several. "Captured by" notes who *enters* it.

---

## Quick answer: what does each person actually need?

Before the full dictionary, the short version of your question:

**The field technician (🔧) needs, on their phone:**
- Where am I going + what am I walking into: customer, address, **access notes (gate code, pets,
  hazards)**, the problem in their words, and this property's **history + equipment on file**.
- What to capture: **photos, voice notes, readings/measurements, the inspection checklist** for this
  job type — fast, few taps.
- What to sell & close: **line items from the pricebook, good/better/best options, signature,
  payment, next visit**.
- Compliance they're legally on the hook for: e.g. **EPA refrigerant log** (HVAC), permit numbers.

**The office/admin (🏢) needs, on the desktop:**
- The **customer account** (who pays) and its **properties** (where work happens) — two different
  things.
- **Scheduling & dispatch** data: appointment time, arrival window, duration, assigned tech,
  required skills, zone, status.
- The **catalog** (pricebook), **technician skills/availability**, **contracts/memberships**, and
  the **money chain** (estimate → invoice → payment).

**The owner (👑) needs:** the rolled-up numbers — revenue, balance due, tech utilization, close rate
— which are just the above, aggregated. Nothing separate.

Now the detail.

---

## The object map (with the two additions you asked about)

```
Organization
 └─ Customer (account / who pays) ───────────────┐
     ├─ Contact(s)                               │
     ├─ Service Agreement / Membership  ◀── CONTRACT (recurring revenue; generates Jobs)
     └─ Property / Location (where work happens)  │
         ├─ Equipment / Asset                     │
         └─ Project  ◀── multi-visit container (install/remodel)
             └─ Job (work order) ◀───────────────┘
                 ├─ Visit / Appointment
                 │   └─ Time Entry
                 ├─ Estimate → Line Items
                 ├─ Invoice  → Payment
                 ├─ Form Result / Readings   ◀── trade-specific, configurable
                 └─ Notes / Photos
 Catalog:  Pricebook Item · Job Type · Form          Team: User/Technician · Role · Skill
```

**Two things the research made clear are first-class, not just "a Job":**
- **Service Agreement / Membership** = the *contract*. A recurring plan that **generates Jobs** on a
  schedule (e.g. spring + fall tune-ups). The recurring-revenue engine. ([details](#8-service-agreement--membership-the-contract))
- **Project** = a container *above* Job for big multi-visit work (a system install, a remodel) with
  phases, multiple estimates, deposits/progress billing, and POs. ([details](#7-project-multi-visit-work))

---

## The entities & their fields

### 1. Customer (account — "who pays")
The billing-responsible party. **Distinct from where work happens** (that's Property).

| Field | Who | Notes |
|---|---|---|
| Customer ID | 🏢 | system-generated |
| Type: Residential / Commercial | 🏢👑 | drives workflow & reporting |
| Name (individual or company) | 🔧🏢 | |
| Billing address | 🏢 | who's financially responsible |
| Phone(s), Email(s) | 🔧🏢 | multiple |
| Payment terms | 🏢 | |
| Lead source / origin | 🏢👑 | marketing attribution |
| Tags / segments | 🏢 | |
| Communication preferences | 🏢🙋 | which auto-messages they get |
| Membership status | 🔧🏢 | active plan? (links to Contract) |
| **Account financials** (rollup): Lifetime revenue, Avg job total, Balance due, Credit available, Customer since | 👑🏢 | summary, computed |
| Custom fields, Notes | 🏢 | |

### 2. Contact
A person to reach. A customer can have several; a contact can be the **billing contact** and can map
to specific properties.

| Field | Who | Notes |
|---|---|---|
| Name, Role/title | 🔧🏢 | |
| Phone, Email | 🔧🏢 | |
| Billing contact? | 🏢 | pre-fills on quotes/invoices |
| Linked properties | 🏢 | |
| Per-contact comms preferences | 🏢🙋 | |

### 3. Property / Location ("where work happens")
Belongs to one Customer; a customer can have many. **Equipment lives here, not on the customer.**

| Field | Who | Notes |
|---|---|---|
| Service address | 🔧🏢 | distinct from billing address |
| Type: Residential / Commercial | 🔧🏢 | |
| Unit / suite (multi-unit support) | 🔧🏢 | property managers have many |
| **Access info**: gate/alarm codes, parking, on-site contact | 🔧 | *critical for the tech* — make structured, not buried in notes |
| **Hazards / pets** flag | 🔧 | safety, before arrival |
| Service history | 🔧🏢 | every past job at this location |
| Notes | 🔧🏢 | |

### 4. Equipment / Asset
Tied to the Property. The compounding-data moat — known on every return visit.

| Field | Who | Notes |
|---|---|---|
| Make / Manufacturer, Model, **Serial #** | 🔧🏢 | tech scans barcode to avoid typing |
| Equipment ID / asset tag | 🔧🏢 | |
| Install date, Age | 🔧🏢👑 | drives replacement opportunities |
| Warranty info / expiration | 🔧🏢 | |
| Location on site | 🔧 | "attic unit," "north panel" |
| Spec sheets / attachments | 🔧 | |
| **Readings/measurements** | 🔧 | trade-specific → stored as Form Results, not fixed columns ([§13](#13-form--readings-the-flexible-trade-specific-layer)) |

### 5. Job (work order) — the center of gravity
One unit of work at a property. The thing the tech runs.

| Field | Who | Notes |
|---|---|---|
| Work order # | 🔧🏢 | |
| Job Type | 🔧🏢 | preventive maint / repair / install / inspection — a configurable template |
| Priority | 🏢 | emergency vs standard |
| **Status** | 🔧🏢👑 | the lifecycle ([§Date/Status model](#datetime--status-model)) |
| Problem reported / reason for call | 🔧 | in the customer's words |
| Assigned technician(s) | 🔧🏢 | single or crew |
| Diagnosis / findings | 🔧 | captured on site |
| Work performed | 🔧 | |
| Parts/materials used (line items) | 🔧 | flow to invoice, decrement inventory |
| Labor time | 🔧 | start/stop |
| Photos / voice notes | 🔧 | |
| Maintenance recommendations | 🔧 | future work |
| Links: Property, Customer, (Project), (Agreement) | 🏢 | |

### 6. Visit / Appointment
A scheduled tech attendance. **A Job can have many Visits** (the multi-trip reality). This is the
scheduling unit.

| Field | Who | Notes |
|---|---|---|
| Scheduled date | 🔧🏢🙋 | |
| **Arrival window** (customer-facing) | 🔧🏢🙋 | e.g. 1–3pm — distinct from duration |
| Duration estimate | 🏢 | from Job Type |
| Assigned tech(s) / crew | 🔧🏢 | |
| Required skills / certs | 🏢 | unqualified techs can't be booked |
| Zone / route | 🏢 | drive-time, proximity |
| On-my-way / arrived / start / stop timestamps | 🔧🏢 | live status to the board |
| Visit status | 🔧🏢 | en route, on site, etc. |

### 7. Project (multi-visit work)
A container **above Job** for big jobs (system install, remodel). Use when work spans phases,
multiple estimates, and progress billing. Simple jobs skip this entirely.

| Field | Who | Notes |
|---|---|---|
| Project name / type | 🏢👑 | |
| Customer, Property | 🏢 | |
| Jobs (1..n) | 🔧🏢 | the project holds multiple jobs |
| **Phases** (e.g. rough-in → top-out → trim-out) | 🔧🏢 | with due dates & dependencies |
| Multiple estimates / change orders | 🏢🙋 | |
| Deposits / progress billing (AIA-style) | 🏢👑🙋 | pay over milestones |
| Purchase orders / materials | 🏢 | |
| Completion % / budget vs actual | 👑🏢 | real-time job costing |

### 8. Service Agreement / Membership (the contract)
The recurring plan. Has a **template** (the plan you sell) and an **instance** (one customer's
signed agreement). It **generates Visits/Jobs** on a schedule.

**Template (the plan definition) — 🏢 admin sets up:**
| Field | Notes |
|---|---|
| Plan name / tier | Silver/Gold/Platinum (good/better/best) |
| Term model | fixed-term (expires/renews) vs ongoing (until canceled) |
| Billing frequency | upfront / monthly / quarterly / semi-annual / annual |
| Recurring price | |
| Member benefits | % discount on repairs/parts, priority service |
| **Recurring services** | service type + # visits or cadence (e.g. 2 tune-ups/yr) |
| Revenue recognition | deferred vs immediate (accounting) |

**Instance (sold to a customer) — 🏢, visible 🔧👑:**
| Field | Who | Notes |
|---|---|---|
| Member (customer) | 🔧🏢 | |
| **Account manager** | 🏢🙋 | the person who owns the relationship (e.g. "Amy Smith") |
| Agreement sub-type | 🏢 | e.g. "HVAC Semi Annual" — a label/category on the plan |
| **Covered locations** | 🔧🏢 | one agreement can cover **multiple properties** (e.g. "4 covered locations") |
| **Covered property + equipment** | 🔧🏢 | which units (make/model/serial) are covered |
| **Term length + billing cadence** | 🏢👑 | e.g. "36 months – Quarterly" (confirmed by a real ServiceTitan agreement screen) |
| Coverage period (start → end) | 🏢🙋 | e.g. May 24 2024 → Sep 23 2025 |
| Start / end / activation date | 🏢 | e.g. 7/13/2020 → 7/30/2023 |
| Auto-renew | 🏢 | + card-on-file renewal protection |
| Status | 🔧🏢🙋 | active / expired / canceled / pending |
| **Billing model** | 🏢👑 | upfront · recurring · **Time of Service** (billed as each visit happens) |
| Billing amount & frequency | 🏢👑 | inherited, overridable |
| **Amount billed / remaining balance** | 🏢👑🙋 | e.g. $3,400 billed / $3,877.23 remaining |
| Included / **remaining visits** + next visit | 🔧🏢🙋 | e.g. "1 remaining · next Jul 1–Sep 30" |
| **Visit list** (named/numbered, e.g. Q1–Q4) | 🔧🏢🙋 | each links back to the agreement, with status (upcoming/completed), type, window, location |
| Priority/scheduling benefit | 🏢🙋 | |
| **Profitability / job costing** | 👑🏢 | budget vs actual across the agreement's life → see [§15](#15-job-costing--profitability-budget-vs-actual) |
| **Customer-visible in a portal** | 🙋 | status, upcoming visits, balance — "100% transparent" (see note below) |

> **The 🙋 marks matter here:** a service agreement is one of the few things the *customer* sees
> directly. ServiceTitan markets a customer portal where the customer checks their contract status,
> upcoming visits, and balance — *"give customers full visibility into their contracts"*
> ([reference screenshot](research/assets/servicetitan-service-agreements-customer-portal.jpeg)).
> That's your [transparency thesis](15-transparency-and-control.md) on the **customer** side, and it
> drives renewals. Our customer-facing surface ([no-download link](04-core-workflows.md)) should show
> the same: their agreement, what's covered, what's coming, what's owed.

### 9. Estimate / Quote
| Field | Who | Notes |
|---|---|---|
| Quote # | 🔧🏢 | |
| Line items: description, qty, unit price, **cost**, tax, type (service/material/labor) | 🔧🏢 | cost enables margin |
| **Options / tiers** (good/better/best) | 🔧🙋 | each with its own subtotal |
| Optional line items | 🙋 | customer can select/deselect |
| Status | 🔧🏢 | sent / approved (sold) / declined / signed |
| Deposit required | 🏢🙋 | % or fixed |
| **E-signature** | 🔧🙋 | editing an approved quote voids the signature |
| Validity / expiration, terms, disclaimer | 🏢🙋 | |
| Financing offer | 🙋 | on the total (minus deposit) |

### 10. Invoice
| Field | Who | Notes |
|---|---|---|
| Invoice #, type | 🏢 | |
| Invoice date, **due date**, completion date | 🏢👑 | |
| Links: Job/Project, source Estimate # | 🏢 | no re-keying |
| Line items, Customer PO | 🏢 | from approved work |
| Subtotal, tax, discount/member savings, **total** | 🏢👑🙋 | |
| Payments made, **remaining balance due** | 🏢👑 | |
| Payment terms, Status (open/paid) | 🏢 | |
| Progress-invoice variant | 🏢 | for Projects |
| Reminders schedule | 🏢 | |

### 11. Payment
| Field | Who | Notes |
|---|---|---|
| Amount | 🔧🏢👑 | |
| **Method**: card / ACH / cash / check / financing | 🔧🙋 | |
| Date, type | 🔧🏢 | |
| Deposit vs balance | 🏢 | |
| Tip | 🔧 | attributed to tech |
| Refund (full/partial) | 🏢 | audit-logged |
| Reconciliation link (→ QuickBooks/invoice) | 🏢 | idempotent |

### 12. Technician / Team (🏢 admin)
| Field | Who | Notes |
|---|---|---|
| Name, contact | 🏢 | |
| **Skills** (HVAC install, plumbing S&D…) | 🏢 | match tech ↔ job |
| **Certifications + expiry** | 🏢 | e.g. EPA cert; *verify expiry as a first-class field* |
| Working hours / shifts (regular/on-call/overnight) | 🏢 | |
| Availability / capacity | 🏢 | shifts − booked |
| Location / GPS (live) | 🏢 | trust-first, not surveillance |
| Pay / labor rate | 🏢👑 | timesheet / performance |
| Zone | 🏢 | |

### 13. Form / Readings (the flexible, trade-specific layer)
**This is where multi-industry flexibility lives.** Trade-specific data — HVAC superheat/subcooling/
static pressure/capacitor µF, electrical panel schedule/load calc, plumbing backflow/water pressure,
EPA refrigerant logs — are **configurable forms attached to Job Types and Equipment**, *not* fixed
columns on the Job.

| Field | Who | Notes |
|---|---|---|
| Form template (per Job Type) | 🏢 admin | the configurable bit |
| Fields: readings, checklist items, pass/fail, photos | 🔧 | rendered natively in the tech flow |
| Linked Job + Equipment | 🔧 | readings attach to the unit's history |
| Compliance fields (EPA 608: date, tech cert #, refrigerant type, lbs added/recovered, appliance ID, leak check) | 🔧 | legally required, retained 3 yrs (HVAC) |

> **Why this matters:** an HVAC "Maintenance" job type ships with a coil-inspection form; a landscaper
> later defines a "Spring Cleanup" form. Same engine, different config — the flexibility thesis made
> concrete. ([Layer 3](12-system-layers.md))

### 14. Pricebook Item & Job Type (🏢 admin — the catalog)
| Pricebook Item | Job Type |
|---|---|
| Name, code/part#/model | Name |
| Type: service / material | Default duration |
| Flat-rate vs hourly | Required skills/certs |
| Unit cost, markup %, unit price, margin | Default forms |
| Tax category | Default line items |
| Supplier / vendor | Default priority |

### 15. Job Costing / Profitability (budget vs actual)
Real-time profitability on a **Job, Project, or Service Agreement** — modeled from a live ServiceTitan
"Commercial Maintenance" agreement screen ([reference screenshot](research/assets/servicetitan-job-costing.jpeg)).
The market leader sells this as **"billing transparency"** and **"budget variance tracking"**, which
is a direct expression of your [transparency thesis](15-transparency-and-control.md), aimed at the owner.

**Shape:** for each category, four values — **Budget · Actuals · Variance · % of budget used.**

| Group | Categories (rows) | Unit |
|---|---|---|
| **Billed (revenue)** | Contract · Maintenance Revenue · Install Revenue · Service Revenue · **Total** | $ |
| **Expenses** | Labor Hours · Materials | **hours** (labor) and $ (materials) |

| Field | Who | Notes |
|---|---|---|
| Category | 👑🏢 | a revenue or expense line |
| Budget | 👑🏢 | the plan |
| Actuals | 👑🏢 | what really happened — **derived**, not typed |
| Variance | 👑🏢 | computed: Actuals − Budget (can be negative) |
| % of budget used | 👑🏢 | Actuals ÷ Budget; **can exceed 100%** (e.g. Materials 126% = over budget — flag it) |

> **For our model:** labor is tracked in **hours *and* dollars**; "Actuals" roll up from the real
> [Payments](#11-payment), [labor time](#5-job-work-order--the-center-of-gravity), and material costs
> already captured — so this view **reconciles to the penny** with the work behind it, rather than
> being a parallel spreadsheet. Over-budget categories are exactly what gets
> [surfaced early](15-transparency-and-control.md), not discovered at month-end.

---

## Date/time & status model (you mentioned date/time specifically)

There isn't one "date" — there are several, and conflating them is a classic mistake. The ones that
matter:

| Date/time | On | Meaning |
|---|---|---|
| Scheduled date + **arrival window** | Visit | when the customer expects someone (e.g. Thu 1–3pm) |
| Duration estimate | Visit (from Job Type) | how long it should take (internal) |
| On-my-way / Arrived / Start / Stop | Visit | live timestamps → the board & labor time |
| Completion date | Job | work finished |
| Due date | Invoice | when payment is owed |
| Term start / end / renewal | Service Agreement | the contract's life |
| Phase due dates | Project | milestone timeline |

**Job status lifecycle** (a sensible default; configurable per org):
```
Unscheduled → Scheduled → Dispatched → En route → On site → Completed → Invoiced → Closed
                                          (side states: On hold · Pending parts · Cancelled · Follow-up)
```
Status is set partly by the system, partly by the tech tapping through their job. It's what every
role reads at their own altitude ([IA](03-information-architecture.md)).

---

## How to use this

- **Build the spine first (Layer 1):** Customer, Contact, Property, Equipment, Job, Visit, Estimate,
  Invoice, Payment — the core fields above. These rarely change.
- **Treat readings & trade specifics as Forms (Layer 3):** never add an `hvac_superheat` column to
  the Job. Add it as a form field. This is the single most important modeling decision for
  flexibility.
- **Contracts and Projects are first-class** but not needed for the [Phase-1 wedge](08-roadmap.md) —
  the technician's single-Job flow doesn't require them. Add them in [Phase 3–4](08-roadmap.md).
- For the **quick-start slice**, you only need: Customer, Property, Equipment, Job, Visit, one Form,
  Estimate, Payment. Everything else layers on. ([System Layers quick-start](12-system-layers.md))

---

## Sources & confidence

Synthesized from three research streams across ServiceTitan, Jobber, Housecall Pro, FieldEdge,
Service Fusion, Microsoft Dynamics, EPA Section 608, and HVAC/plumbing/electrical work-order and
contract templates. Full source lists are in the research transcripts; key anchors:

- **Field/work-order & compliance:** ServiceTitan field mobile app & templates; EPA Section 608
  recordkeeping ([epa.gov/section608](https://www.epa.gov/section608/epas-refrigerant-management-program-questions-and-answers-section-608-certified)); HVAC diagnostic checklists (SafetyCulture, HVACSolver).
- **Customer/property/scheduling:** ServiceTitan [customer & location records](https://help.servicetitan.com/docs/customer-and-location-records-overview), [capacity planning](https://help.servicetitan.com/how-to/adjustable-capacity-planning-workflow); Jobber [client](https://help.getjobber.com/hc/en-us/articles/115009450867-Client-Basics) & [properties](https://help.getjobber.com/hc/en-us/articles/115010161128-Properties); Service Fusion dispatch.
- **Contracts/projects/billing:** ServiceTitan [memberships](https://help.servicetitan.com/docs/memberships), [projects](https://help.servicetitan.com/docs/manage-projects), [invoices](https://help.servicetitan.com/docs/invoice-walkthrough); Jobber [progress invoicing](https://help.getjobber.com/hc/en-us/articles/26297232277527-Progress-Invoicing); Housecall Pro [service plans](https://www.housecallpro.com/features/recurring-service-plans/) & [payments](https://www.housecallpro.com/features/payment/).

**Confidence:** Entity *structure* and field *concepts* are high-confidence (corroborated across
multiple vendors). **Exact field labels and status-enum strings vary by vendor** — normalize them in
our schema. Several vendor help/API pages blocked automated fetch (HTTP 403), so fields come from
cross-checked search summaries; before finalizing the database schema, confirm exact enums against a
live vendor API reference (e.g. ServiceTitan's developer portal) and validate the **technician
certification-expiry** field, which was implied but not explicitly named. Trade-specific items (EPA
logs, AIA progress billing) apply to HVAC/mechanical and construction-style work; lighter trades use
a subset.
