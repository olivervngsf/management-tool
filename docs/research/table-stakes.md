# Table Stakes — the must-have foundation

The **needs, not wants.** These are the capabilities every credible FSM product has and every shop
expects. They don't *win* the deal — they're the price of entry. Missing any one *loses* the deal.
This separates the **foundation we must build** (here) from the **differentiators that win**
([how we win](competitor-lessons.md), [strategy](../01-product-strategy.md)).

Each row carries **metadata = evidence it's a real need**: which competitors all ship it (universal
presence = table stakes), plus market/usage data from the [research](market-and-competitors.md).
Sources are cited; competitor coverage is from the [competitor profiles](market-and-competitors.md).

**Legend:** ✅ has it · ST = ServiceTitan · J = Jobber · HCP = Housecall Pro · SW = Swivl.

---

## The foundation (NEED — must-have to be credible)

| # | Capability | Evidence it's a real need (metadata) | ST | J | HCP | SW | Our coverage |
|---|---|---|:--:|:--:|:--:|:--:|---|
| 1 | **Scheduling & dispatch** | Core of every FSM product; the reason the category exists ("the right person to the right address at the right time") | ✅ | ✅ | ✅ | ✅ | [Board B1](../build-backlog.md), [PRD R2](../09-prd.md) |
| 2 | **Technician mobile app** | The field tool; mobile-first is "the dividing line between apps that succeed and fail" ([trends](market-and-competitors.md)) | ✅ | ✅ | ✅ | ✅ | [A-flows](../build-backlog.md), [PRD R1](../09-prd.md) |
| 3 | **Customer / CRM records** (customer → property → equipment + history) | Universal; the system of record. Property/equipment history is standard in ST/Jobber/FieldEdge | ✅ | ✅ | ✅ | ✅ | [data §1–4](../14-data-model.md) |
| 4 | **Job / work order management** | The unit of work; every tool's spine | ✅ | ✅ | ✅ | ✅ | [data §5–6](../14-data-model.md) |
| 5 | **Estimates / quotes** (multi-option) | All four ship good/better/best quoting; "send proposals in hours not days" is a headline feature | ✅ | ✅ | ✅ | ✅ | [data §9](../14-data-model.md), proto ✅ |
| 6 | **Invoicing** | Universal; the bill. Customer "Invoices Hub" w/ online pay is marketed by ST | ✅ | ✅ | ✅ | ✅ | [data §10](../14-data-model.md), proto ✅ |
| 7 | **Integrated payments** (card + ACH) | Embedded, on-site card payment is now "standard… a core differentiator" ([trends](market-and-competitors.md)); ~2.9%+30¢ / 1% ACH across the market | ✅ | ✅ | ✅ | ✅ | [PRD R1.9](../09-prd.md), proto ✅ |
| 8 | **Online booking / self-scheduling** | Self-service portals (book, track, pay) are explicitly **"table stakes"** ([servicepower](https://www.servicepower.com/blog/field-service-and-the-age-of-consumer-self-service)) | ✅ | ✅ | ✅ | ✅ | [D3](../build-backlog.md), PRD R3.5 |
| 9 | **Customer notifications** (confirm, reminder, on-my-way) | Customers expect "on-demand scheduling, real-time tracking, proactive updates" — the "Amazon experience" ([trends](market-and-competitors.md)) | ✅ | ✅ | ✅ | ✅ | [D1](../build-backlog.md), PRD R2.5 |
| 10 | **Price book** (services/materials, flat-rate) | Universal; flat-rate pricing is standard in the trades (ST/Jobber) | ✅ | ✅ | ✅ | ✅ | [data §14](../14-data-model.md) |
| 11 | **Accounting sync** (QuickBooks/Xero) | QuickBooks holds **~62%** of accounting share, construction its **#1** vertical ([electroiq](https://electroiq.com/stats/quickbooks-statistics/)); all four integrate it | ✅ | ✅ | ✅ | ✅ | [E3](../build-backlog.md), PRD R3.4 |
| 12 | **Photos / attachments / notes** | Universal field capture; multi-photo + notes in all field apps | ✅ | ✅ | ✅ | ✅ | [PRD R1.5](../09-prd.md), proto ✅ |
| 13 | **Reporting / dashboard** | Owners need revenue/jobs/utilization at a glance; standard in all | ✅ | ✅ | ✅ | ✅ | [C1](../build-backlog.md), proto ✅ |
| 14 | **Service agreements / memberships** (recurring) | The recurring-revenue engine; ST/HCP/Jobber/FieldEdge all ship it; keeps techs busy in shoulder season | ✅ | ✅ | ✅ | ◻ | [data §8](../14-data-model.md), F1 |
| 15 | **Offline-capable mobile** | ~20% of jobs hit dead zones; "offline-first design… the dividing line" ([trends](market-and-competitors.md)) — *everyone claims it; few do it well* | ~ | ~ | ~ | ~ | **[I1](../build-backlog.md) — our differentiator too** |
| 16 | **Multi-user roles / permissions** | Office vs field vs owner access; standard | ✅ | ✅ | ✅ | ✅ | [personas](../02-personas-and-roles.md), PRD NFR6 |
| 17 | **Customer self-service portal** | One hub for jobs/invoices/proposals/agreements; ST markets "100% transparent" | ✅ | ~ | ~ | ◻ | [D2](../build-backlog.md), proto ✅ |
| 18 | **GPS location / map / routing** | Dispatch needs the *closest* tech, customers need real ETAs, routes need optimizing; all FSM tools show techs on a map | ✅ | ✅ | ✅ | ✅ | [Board B1](../build-backlog.md) + the [tracking bright line](../15-transparency-and-control.md) |

`~` = present but weak/partial (the opening we exploit).

> **Note on GPS (row 18):** tracking location *is* table stakes — trust-first does **not** mean no
> GPS. We track to dispatch and inform the customer, **transparently and purpose-bound**, never to
> surveil the tech (the [bright line](../15-transparency-and-control.md) vs. Hubstaff).

---

## What the metadata is telling us

1. **Universal presence = the real signal.** When ServiceTitan, Jobber, Housecall Pro *and* Swivl all
   ship a capability, that's the market saying "shops won't buy without this." Rows 1–14, 16 are
   ✅ across the board — those are non-negotiable.
2. **External evidence backs it up** where we have it: online booking ("table stakes"), embedded
   payments ("standard… core differentiator"), QuickBooks (62% share / #1 vertical), offline ("the
   dividing line"). These aren't our opinion — they're sourced.
3. **Two rows are both NEED *and* WIN.** Offline (#15) and the customer portal (#17) are table stakes
   that everyone does *weakly* (`~`). We must have them to compete **and** doing them *well* is how we
   differentiate. Build them as foundation, polish them as moats.

---

## The line: NEED (foundation) vs WANT (how we win)

| NEED — must have (this doc) | WANT — wins the deal ([differentiators](competitor-lessons.md)) |
|---|---|
| Scheduling, dispatch, mobile app, CRM, jobs | **Genuine zero-data-loss offline** (not "offline-ish") |
| Estimates, invoicing, payments, price book | **AI write-it-fills** + the human gate |
| Online booking, notifications, QuickBooks | **Trust-first private layer** (anti-surveillance) |
| Reporting, memberships, roles, portal | **Transparency** (one-line report, job costing visible) |
| Photos/notes, multi-user | **Compact, Apple-grade UX · honest pricing · same-day onboarding** |

> **Strategy in one line:** match the left column to get in the game; win on the right column. A
> beautiful app that can't take a payment or sync to QuickBooks isn't a contender — so we build the
> foundation first, then let the differentiators carry the win.

---

## Coverage status (are we covering the foundation?)

Of the 17 needs: **most are already reflected** in the [data model](../14-data-model.md),
[PRD](../09-prd.md), and [build backlog](../build-backlog.md); several are already in the
[prototype](../prototype/fieldwork-prototype.html) (estimate, invoice, payment, portal, reporting).
The ones still to design/build are flagged in the [build backlog](../build-backlog.md) — notably
online booking (D3), memberships (F1), and the accounting sync (E3).

**Use this as the readiness checklist:** we are not "competitive" until every NEED row is real. The
differentiators don't substitute for the foundation — they sit on top of it.
