# 01 · Product Strategy

> Grounded in [Market & Competitive Research](research/market-and-competitors.md) (June 2026).
> Specific competitor numbers below are sourced and cross-checked there.

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

### The numbers that justify the bet

The [research](research/market-and-competitors.md) makes the opportunity concrete:

- **Market:** FSM software is **~$5–6.5B (2025–26)** growing to **~$9.5–13.8B by 2030–34** (~10–13%
  CAGR), atop a **~$1.5T** annual trades-services TAM.
- **The wide-open door:** **~45%** of trades businesses still run on **pen-and-paper or
  spreadsheets**, and **~56%** use no purpose-built FSM software — QuickBooks is the default
  "system." Most of the market is not a competitor's customer; it's un-digitized.
- **The "missing middle":** ~80% of field-service businesses are too big for consumer tools and too
  small for ServiceTitan — under-served by design.
- **Tailwinds:** an acute skilled-trades labor shortage (~$1T economic risk) pushes shops to do more
  with fewer people via software; PE roll-ups and ServiceTitan's 2024 IPO have validated the
  category and the spend.

### The competitive map, and the seam each leaves

| Player | Owns | The seam they leave |
|---|---|---|
| **ServiceTitan** | Enterprise (20+ techs); "operating system for the trades" | 12–16 wk / **$5K–$50K** onboarding, $245–500/tech/mo, lock-in with steep ETFs, and a **mobile app that regressed to ~3.3★** with weak offline — its most consistent complaint |
| **Jobber** | SMB ops, loved for ease of use (100k+ customers) | Per-seat cost creep; **too shallow past ~15–20 techs** |
| **Housecall Pro** | SMB growth tools, fast setup | **Add-on cost creep is its #1 complaint** (~9× advertised price at 5 techs); **3.2★ Android** app |
| **Swivl + AI wave** (Avoca $1B val, Netic, Quantra) | The AI-native angle — mostly **AI voice/agents on inbound calls** | Thin on the *field experience + data spine*; AI bolted to the call, not woven into the daily loop |

The seams line up: **mobile/offline failure and data-entry friction** are the biggest, best-
evidenced gaps — and they are exactly the technician's daily loop, which is our wedge. Meanwhile AI
voice/booking is becoming **table stakes** (Avoca/Netic), so it's a *must-have*, not our
differentiator; our edge is the experience and data spine the AI runs on.

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

## Business & pricing model (research-backed)

Pricing is a **strategic weapon**, not an afterthought — the two loudest complaints across the
category are **add-on cost creep** (Housecall Pro's #1 gripe; ServiceTitan too) and **lock-in /
termination fees** (ServiceTitan ETFs of $15K–$46K are documented). We position as the clean inverse.

**Principles:**
- **Per-seat, role-weighted.** Technician seats priced low (drive adoption — the wedge); office/
  admin/owner seats priced higher (where the willingness-to-pay sits). Undercuts ServiceTitan's
  $245–500/tech/mo while monetizing the office.
- **All-inclusive, no add-on creep.** Core platform features are *in the plan*. We do not nickel-
  and-dime dispatch, marketing basics, or the customer experience as "Pro" modules. This directly
  attacks the most-cited pricing complaint in the market.
- **No lock-in, no implementation fee.** Month-to-month, self-serve, day-not-quarter onboarding —
  the inverse of ServiceTitan's $5K–$50K / 12–16-week setup, which is its single biggest adoption
  barrier. Easy migration in *and* out builds the trust a conservative buyer base demands.
- **Transparent, published pricing.** ServiceTitan hides pricing behind a sales demo; we publish it.
  Transparency is itself a differentiator with a skeptical, word-of-mouth-driven buyer.
- **Payments as the second revenue line and retention moat.** Margin on in-app card/ACH capture
  (benchmark ~2.9% + 30¢ cards / ~1% ACH, matching the SMB market). Once the money flows through
  the product, the product is load-bearing — and payments are where incumbent stickiness actually
  lives, not the core app.

**Why this is defensible against the AI wave:** competitors like Swivl go free + usage and the
VC-backed AI players (Avoca, Netic) may subsidize aggressively. We don't win the race to $0 — we win
on the experience and the embedded-payments economics, priced honestly in between Swivl's free tier
and ServiceTitan's enterprise toll.

## The single most important bet

If we are right about one thing, it is this: **in this category, the team that wins the
technician's daily loyalty wins the account.** Every prioritization call in
[the roadmap](08-roadmap.md) flows from that bet.
