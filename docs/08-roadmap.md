# 08 · Roadmap

Sequenced by the central bet: **win the technician's daily loop first**
([Product Strategy](01-product-strategy.md)). Each phase delivers a coherent, demoable slice of the
[five core flows](04-core-workflows.md) — never half-built horizontal layers. We always have
something real to put in front of a shop.

Timeframes are relative and deliberately loose; the *order* is the commitment.

---

## Phase 0 — Foundation *(this repository)*

**Goal:** a team can align and start building without re-litigating direction.

- ✅ Product strategy, personas, IA, core workflows, design principles.
- ✅ Design system foundation + token source of truth.
- ✅ Technical architecture target.
- ⏭️ Next: monorepo scaffold, `tokens` + `ui` packages, and a clickable prototype of **Flow 1
  (technician job)** and the **dispatch board**.

**Exit criteria:** the prototype makes a shop owner say "yes, that's what my techs would actually
use."

---

## Phase 1 — The Technician's Job (the wedge) · *MVP*

**Goal:** one technician can run a real job end to end on their phone. This is the smallest thing
that is genuinely valuable and the hardest thing to fake — so we build it first.

- Mobile app: Today list → Job screen → arrive → capture (photo/voice/notes) → close.
- Estimate builder with good/better/best, in-room signature.
- Payment capture (Tap to Pay + record cash/check) with instant receipt.
- **Offline-first from day one** — not retrofitted (see [Architecture](07-technical-architecture.md)).
- Minimal office web: create a job, assign it to a tech, see it close.

**Exit criteria:** a friendly real shop runs live jobs through it for a week and prefers it to
paper. *Technician NPS is the metric that matters — not feature count.*

---

## Phase 2 — The Dispatcher's Board (run the day)

**Goal:** an office can run a full day for a multi-tech shop.

- The dispatch board: techs × time, drag-to-assign, live field status, unassigned queue.
- Conflict / skill / drive-time warnings; the 7:45am-emergency re-slot flow.
- Real-time sync field → board (< 1s).
- Customer notifications: confirmation + **on-my-way live tracking link** (the delight feature).
- Command palette (`⌘K`) on desktop.

**Exit criteria:** a 10-tech shop runs an entire week off the board with no spreadsheets.

---

## Phase 3 — The Money Path (get paid, see the truth)

**Goal:** the business runs its finances in Fieldwork and trusts the numbers.

- Estimate → Invoice → Payment fully connected, no re-keying; deposits, partials, tips.
- QuickBooks / Xero sync (one-directional, idempotent).
- The Owner's Home: today's revenue, jobs done vs. scheduled, team status — reconciling to the
  penny.
- Online booking from a link (self-serve into the same Job object).

**Exit criteria:** an owner checks the app instead of calling the office to ask "how'd we do today?"
— and the number is right.

---

## Phase 4 — Configurability & Multi-Industry (open the aperture)

**Goal:** prove the flexibility thesis — onboard a non-HVAC trade with configuration, not code.

- Admin surfaces: configurable JobTypes, Forms, Price Book, and the composable role/permission
  builder ([Personas](02-personas-and-roles.md)).
- Recurring / maintenance-plan engine (the shoulder-season revenue driver).
- A second vertical onboarded end-to-end (e.g. electrical or appliance repair) purely via config.

**Exit criteria:** a shop in a different trade self-onboards and runs a real job without us writing
trade-specific code.

---

## Phase 5 — Scale & Polish (toward GA)

**Goal:** ready for many shops, not a few friendly ones.

- Reporting depth, inventory/truck stock, team performance, payroll-relevant time data.
- Performance hardening to the [non-functional bar](07-technical-architecture.md).
- Accessibility audit to WCAG 2.2 AA across both apps.
- Reliability, observability, on-call, and the security/compliance baseline for handling payments.

**Exit criteria:** the [strategy's measurable "world class" bar](01-product-strategy.md) is met,
verified, on real shops at real volume.

---

## How we sequence within every phase

1. **Flow before feature.** Ship a complete thin slice of a journey, then deepen it.
2. **Technician-acceptance gates everything.** If the field user won't use it, no downstream
   feature matters.
3. **Design-review against the [ten principles](05-design-principles.md)** before any screen
   ships — quality is a gate, not a later pass.
4. **Offline and money correctness are never "phase 2 of a feature"** — they're built in from the
   first line, because both are rewrites if bolted on.

---

## The one metric per phase

| Phase | The number that tells us it worked |
|---|---|
| 1 | Technician NPS / daily active use by real techs |
| 2 | A multi-tech shop runs a full week off the board |
| 3 | Owner-trusted daily revenue that reconciles exactly |
| 4 | A non-HVAC shop self-onboards via config alone |
| 5 | The measurable world-class bar, met at volume |

Everything ladders back to the central bet. If a proposed feature doesn't move the current phase's
number, it waits.
