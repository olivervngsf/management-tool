# 01 · Product Strategy

## The market in one breath

Service businesses — HVAC, plumbing, electrical, and the dozens of trades adjacent to them —
run on coordination: getting the right person, with the right parts, to the right address, at
the right time, and getting paid for it cleanly. The software that runs this is called Field
Service Management (FSM). It is a large, proven, and surprisingly under-loved market.

- **ServiceTitan** — the enterprise standard. Powerful, deep, expensive, and famously heavy to
  learn. Optimized for large shops with dedicated office staff.
- **Jobber / Housecall Pro** — the SMB standard. Approachable, faster to adopt, but thinner as a
  business grows and not built mobile-first for the technician's reality.
- **Swivl and the new wave** — betting that AI and a cleaner UX can unseat the incumbents.

The pattern: power and polish are inversely correlated in this category. We intend to break that
trade-off.

## Our wedge: experience as the product

Most FSM tools are databases with forms bolted on. We treat the **moment-to-moment experience**
as the product surface that wins or loses the deal:

1. **The technician actually likes the app.** Adoption in this category dies at the technician.
   If the person in the field finds the app slow, fiddly, or condescending, they route around it,
   data rots, and the business stops trusting the system. We win the technician first.
2. **The dispatcher runs the day without thinking about the tool.** The dispatch board is a
   real-time instrument. It should feel like a pro audio console — dense, fast, legible under
   pressure — not a spreadsheet.
3. **The owner sees the truth, fast.** Where is the money, where is it stuck, which tech is
   carrying the team. One glance, no report-building.

## Positioning statement

> For growing service businesses who are outgrowing spreadsheets and underwhelmed by clunky
> incumbents, **Fieldwork** is the field service platform that field teams genuinely enjoy using
> and owners can run the whole business on — because it pairs the depth of an enterprise tool
> with the craft of a consumer product.

## How we win (and where we refuse to compete on day one)

**We compete on:**
- Interaction quality and speed (Apple-grade, mobile-first).
- Time-to-value: a shop is live and dispatching the same day.
- Configurability without consultants: roles, job types, and forms adapt to the trade.
- A customer-facing experience that makes the *end customer* prefer businesses on Fieldwork.

**We deliberately do not win on (yet):**
- Deep accounting (we integrate with QuickBooks/Xero, we are not a GL).
- Marketing automation suites, call-center telephony, or fleet telematics — partner, don't build.
- Enterprise franchise/multi-location consolidation — that is a later-stage motion.

Saying no here is the strategy. The incumbents are wide; we go deep on the daily loop first.

## Multi-industry flexibility — a design constraint, not a feature

The first vertical is HVAC / plumbing / electrical because those workflows are the richest and
best understood: dispatch, diagnosis, estimate, parts, multi-visit jobs, and invoicing all show
up. But the *core primitives are industry-agnostic* and must stay that way:

- **Customer → Property → Job → Visit → Line Items → Invoice → Payment** is universal.
- What changes per industry is **vocabulary, forms, and job types** — not the spine.
- Rule: no trade-specific concept is hard-coded into the core. "Refrigerant charge" is a
  *configurable line item template*, not a database column. This is what lets a cleaning company,
  a landscaper, or an appliance-repair shop adopt us later with a configuration change, not a
  rebuild. See [Information Architecture](03-information-architecture.md).

## What "world class" means here, measurably

A vague aspiration becomes a bar only when it has numbers. Our quality bar:

- **Speed:** any primary action (open a job, add a line item, start a timer) responds in
  < 100 ms perceived; cold app launch to usable in < 2 s.
- **Offline:** a technician can run an entire job — photos, notes, signature, payment capture
  intent — with zero connectivity, and it syncs cleanly when signal returns.
- **Learnability:** a new technician completes their first job in the app with no training.
- **Density without clutter:** the dispatch board shows a full day for a 12-tech shop on one
  screen, readable at a glance.
- **Trust:** the owner's "today" number reconciles to the penny with the invoices behind it.

## Business model (orienting, not committed)

Per-seat SaaS with role-based pricing (technician seats priced lower than office/admin seats),
plus payment processing margin on in-app card/ACH capture. Payments are both a revenue line and a
retention moat — once the money flows through the product, the product is load-bearing.

## The single most important bet

If we are right about one thing, it is this: **in this category, the team that wins the
technician's daily loyalty wins the account.** Every prioritization call in
[the roadmap](08-roadmap.md) flows from that bet.
