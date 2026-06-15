# 20 · The Platform — many products that speak together

> The vision in your words: the tool makes **field work faster & easier** and **admin quick & easy**;
> the layers across them are **smooth, trustworthy, transparent, reliable**; not everything is equal;
> and over time the product **learns from its own metrics and suggests what to improve**. It's *many
> small products that work as one* — when one changes, the others gain awareness and adapt.
>
> This doc is the [context engineer's](#operating-model--who-does-what) charter: how the pieces stay
> one coherent system, not a pile of separate features.

---

## A platform, with products on it

The clearest way to hold the whole thing: **Fieldwork is a *platform* — many products that speak
together — not a single app.** Two layers of meaning:

- **The platform (the shared core)** — what every product stands on and none reinvents:
  one [data model / spine](14-data-model.md), identity & roles, [offline sync](07-technical-architecture.md),
  payments, notifications, the [AI / intelligence layer](13-ai-operating-model.md), and the
  [design system](design-system/README.md).
- **The products (on top)** — role- and job-shaped apps:
  **Leads & Communications** (capture leads + unified inbox) · **Field** (the technician's day) ·
  **Dispatch** (the board) · **Owner / Insights** (the money & the story) · **Customer Hub** (booking,
  tracking, proposals, invoices, agreements) · **Money** · **Agreements & Projects** · **Admin /
  Config** (the flexibility layer) — and more over time.

```
 ┌─ Leads & Comms ─┬─ Field ─┬─ Dispatch ─┬─ Owner/Insights ─┬─ Customer Hub ─┬─ Admin/Config ─┐ PRODUCTS
 ├─────────────────┴─────────┴────────────┴──────────────────┴────────────────┴────────────────┤
 │  PLATFORM (shared core):  data model · identity & roles · offline sync · payments ·          │
 │  notifications · telephony (partner rails) · AI / intelligence · design system               │
 └────────────────────────────────────────────────────────────────────────────────────────────────┘
```

They **speak together through the platform** — shared data + [events](#change-propagates--when-one-thing-changes-the-others-know),
never point-to-point silos. A change in one is felt by the others because they all stand on the *same
ground*. Mapped to the [layers](12-system-layers.md): the **platform** is Layer 1 + the cross-cutting
concerns; the **products** are assembled from Layers 2–5. Same architecture — said as a platform.

### The product map — each product and its capabilities

The way a business suite lists its modules and the tools inside each (e.g. PMSuite's "HR & People →
Hiring · Payroll · Benefits · Leave · Admin"), here is Fieldwork's **Platform → Products →
Capabilities** map. The items in each row are **capabilities** — *what the product does* — not
benefits (the outcomes) and not the sales pitch.

| Product | Capabilities (what's inside) |
|---|---|
| **Leads & Communications** (front of funnel) | Lead pipeline (status flow) · ad-source attribution · **unified inbox** (calls · texts · voicemail · team chat) · built-in dialer · **guided call-booking with caller-ID screen-pop** · Leads Map · callbacks · missed-call auto-text / AI answer *(telephony via partner rails)* |
| **Field** (technician) | Today/schedule · job execution · capture (photo/voice/AI) · proposals & sign · payments · multi-visit & close · One-Line Report · private notes |
| **Dispatch** (office) | Live board · booking intake · conflict prevention · emergency re-slot · map/routing · live report stream |
| **Owner / Insights** | Owner home · job costing · KPI dashboard & reports |
| **Customer Hub** | Online booking · on-my-way tracking · proposals (review & sign) · invoices (pay online) · agreements portal |
| **Money** | Estimate → Invoice → Payment · deposits/refunds/tips · QuickBooks/Xero sync · financing |
| **Agreements & Projects** | Memberships / service agreements · recurring-visit engine · projects (phases, progress billing, POs) |
| **Admin / Config** | Job types · form builder · price book · roles & permissions · AI guardrails · integrations · team & skills |
| **Platform core** | data model · identity & roles · offline sync · payments · notifications · AI / intelligence · design system |

> **Capability vs. benefit (the distinction worth keeping straight):** a *capability* is **what the
> product does** (capture, payments, job costing); a *benefit* is **the outcome it creates** ("paid
> on-site, no AR chase"; "live the same day"; "techs actually like it"). We **design from
> capabilities** (the [build backlog](build-backlog.md)) and **sell on benefits** (the
> [strategy](01-product-strategy.md)). A feature list is not a value proposition.

This map *is* the platform-with-products vision made concrete; each capability traces to a flow in the
[build backlog](build-backlog.md). A printable one-page visual lives at
[`product-map.html`](product-map.html) — **v1.1 · 2026-06-14** (it carries a version + date + changelog;
bump them on each update).

## Many small products, one ecosystem

Each product **does one thing well** — scheduling, capture, proposals, payments, agreements, dispatch,
the owner dashboard, the config hub. They are the [bricks of Layer 2](12-system-layers.md). But they
are **not silos**: they share one spine and talk to each other through clean contracts. A user never
feels the seams — to them it's *one product*.

**Two things make the many into one:**
1. **One data model (the spine).** Every product reads and writes the *same*
   [Customer → Property → Job → Visit → money](14-data-model.md). No product keeps its own private
   copy. This is why the owner's numbers equal the tech's actions — same data, not a parallel report.
2. **Clean contracts + the layered rule** — *depend downward, never reach sideways into another
   product's guts* ([the 4 rules](12-system-layers.md)). Products compose like LEGO because they
   share the same studs.

---

## Change propagates — when one thing changes, the others know

The heart of "talk together, not separately": a change in one product **ripples automatically** to
every product that cares. Nobody re-enters data; nobody re-checks. Awareness flows on its own.

| When this happens (one product) | …these products gain awareness & adapt |
|---|---|
| Tech taps **"On my way"** | Customer link shows live ETA · Board shows en-route · One-Line Report posts |
| **Estimate/Proposal approved** | Invoice is created (no re-keying) · Owner "revenue in progress" updates · job moves forward |
| **Payment captured** | Job can close · Owner "today's revenue" +1 · Customer gets a receipt · QuickBooks sync queued |
| **Job runs long / scope grows** | Dispatch is alerted early · customer window updated · owner job-costing flags over-budget |
| **Price-book item changes** (admin) | Future estimates & the AI estimator use the new price automatically |
| **Service agreement sold** | Recurring visits auto-generate onto the schedule · renewal clock starts |
| **Tech cert expires** (admin) | Scheduling stops offering that tech for skill-gated jobs |
| **Customer reschedules** | Board frees the slot · tech's day updates · notifications adjust |

> **The principle:** *one change, many adjustments — automatically.* This is what makes the system
> feel **reliable and transparent**: the right people and products always reflect the latest truth,
> with no manual sync and no stale state. (Mechanically: shared data + events + clean interfaces.)

---

## Not everything is equal (where to spend effort now)

The ecosystem is wide, but the **job-done loop is the heartbeat** — the technician finishing a job and
getting paid. That's where craft and speed go *first*. Richer cross-product awareness, deeper
configuration, and the learning layer below are **filled in over time** — designed now, built as the
foundation earns the right. *Right now: get the job done.* ([Roadmap waves](08-roadmap.md))

---

## The product learns itself — the "Top 5 to Improve" report

Once a shop is running, the product gets better *by being used* — the
[improvement flywheel](12-system-layers.md) made concrete. The [Intelligence layer](13-ai-operating-model.md)
watches the real **metrics & KPIs** ([success metrics](09-prd.md)) and surfaces, on a regular cadence,
the **Top 5 highest-leverage things to improve** — scored across the five lenses (adoption ·
experience/speed · reliability · money · growth) — each with a concrete suggestion.

Illustrative monthly report:
```
  Top 5 to improve — Anytown HVAC, June
  1. 3 techs average >45s on the AC capture form → simplify it (cut 4 fields).   [experience]
  2. AR aging up 12% → turn on auto-reminders for 30-day invoices.               [money]
  3. Membership renewals at 71% → send renewals 30 days earlier.                 [growth]
  4. Tue/Thu are over capacity, Mon under → rebalance recurring routes.          [experience]
  5. 1 in 5 "no-cool" jobs need a 2nd visit → stock capacitors on 2 more trucks. [reliability]
```

**Guardrails (trust-first):** the product **suggests; the human decides** — it never silently
re-tunes the business. Suggestions are transparent (you see the data behind each) and acted on by a
person. ([the gate](13-ai-operating-model.md)) This is **deferred to [Phase 4–5](08-roadmap.md)** —
but the **telemetry to power it is captured from day one**, because you can't analyze what you didn't
record.

---

## Operating model — who does what

| Role | Owns |
|---|---|
| **You (founder)** | **Direction & vision** — what we're building and why; the priorities |
| **Context engineer** (this charter) | **Coherence** — the data model, the IA, cross-product awareness, keeping every idea written into the right doc and cross-linked. *Nothing floats unattached.* |
| **UX/UI** | **Flow & experience** — double-checking each journey against the [design principles](05-design-principles.md) and the [review checklist](ux-ui-review.md) |
| **The product itself** (Layer 5) | **Learning & suggesting** — surfacing the Top 5; humans decide |

This keeps the work clean: you point the direction, the system stays coherent underneath, the
experience stays sharp on top, and the product quietly gets smarter — with people always in control.

---

## The contract that keeps the ecosystem smooth

1. **Shared data, never copies** — one model, one truth ([data model](14-data-model.md)).
2. **Change propagates via events** — products subscribe to what they care about; awareness is
   automatic, not manual.
3. **Clean interfaces, no sideways reach** — products talk through contracts, so one can change
   without breaking another ([layer rules](12-system-layers.md)).
4. **Humans stay in control** — the system surfaces and suggests; people decide ([AI model](13-ai-operating-model.md)).
5. **The spine is sacred and small; flex at the top** — stability where it matters, flexibility where
   it helps.

> **In one line:** *many small products, one shared truth, change that ripples on its own, and a
> system that learns — with you steering and people always in control.* That's the ecosystem.
