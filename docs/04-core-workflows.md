# 04 · Core Workflows

Strategy and IA become real in flows. This document specifies the handful of end-to-end journeys
that the whole product must nail. If these feel effortless, we win; everything else is supporting
cast.

The spine of the business is the **Job Lifecycle**. Every role touches it from a different angle.

---

## The Job Lifecycle (state machine)

```
   ┌─────────┐   booked    ┌───────────┐  assigned  ┌───────────┐
   │  LEAD   │ ──────────▶ │ SCHEDULED │ ─────────▶ │ DISPATCHED │
   └─────────┘             └───────────┘            └─────┬──────┘
                                                          │ tech taps "On my way"
                                                          ▼
   ┌──────────┐   paid     ┌──────────┐  work done  ┌──────────┐
   │  CLOSED  │ ◀───────── │ INVOICED │ ◀────────── │ ON SITE  │
   └──────────┘            └──────────┘             └────┬─────┘
        ▲                                                │ (may spawn another Visit)
        └──────────── multi-visit jobs loop back ────────┘
```

A Job can hold multiple Visits; the Job stays open across trips and only closes when the work and
the money are both done. State is explicit and visible to every role at the right altitude.

---

## Flow 1 — The Technician's Job (the most important flow in the product)

This is Maria's loop and the single screen we obsess over. It must work **fully offline**.

**1. Heads-up (before the door).** Open the Job. Above the fold: customer name, the problem in
their words, this property's history ("we replaced the capacitor 14 months ago"), equipment on
file, and access notes ("gate code 4827, dog is friendly"). Maria knows what she's walking into.

**2. On my way.** One tap. This: notifies the customer with a live tracking link, starts the
travel time entry, and updates the board so David sees movement. The customer's anxiety drops; the
office stays informed; Maria did one thing.

**3. Arrive & diagnose.** Tap "Arrived" (geofence-suggested). Capture findings the fast way:
camera first, voice-to-text notes, tap-to-fill from the job type's inspection form. Typing is the
last resort, never the default. Photos attach to the Property, building its history.

**4. Quote in the room.** Build an estimate from the price book in seconds. Offer **good / better /
best** options (a proven trades-sales pattern — e.g., repair vs. repair-plus-tune-up vs. replace).
Present it on the phone, hand it to the customer, get a signature right there. Pricing visibility
respects Maria's role (see [Personas](02-personas-and-roles.md)).

**5. Do the work, log materials.** Add the parts actually used; they flow to the invoice and
decrement inventory. Timer tracks labor. All of this works with no signal.

**6. Collect payment.** Tap to pay — card (tap-to-pay on the phone), ACH, or record cash/check.
Receipt texted/emailed instantly. *Getting paid on site is the highest-leverage moment in the whole
business* — it eliminates the accounts-receivable black hole that strangles service shops.

**7. Close out.** Review, capture a final signature, mark done. If a return trip is needed, spawn
the next Visit in two taps without closing the Job. Maria drives away with nothing left to do
tonight.

**Offline note:** every step above queues locally and syncs when signal returns, with clear,
non-alarming sync status. Conflict resolution favors the field (the tech on site is the source of
truth for what happened). See [Technical Architecture](07-technical-architecture.md).

---

## Flow 2 — The Dispatcher's Day (running the board)

David's loop on the desktop console.

**Morning:** the board shows every tech as a lane, the day as a timeline, jobs as cards. Unassigned
jobs sit in a queue on the side. He drags cards onto techs; the system warns on conflicts, skill
mismatch (a job needing EPA certification onto a tech who lacks it), or an impossible drive time.

**The 7:45am emergency** (the scenario that defines a dispatch tool): a no-cooling call lands in
July. David needs the *closest available, qualified* tech. The board surfaces candidates ranked by
proximity and current status. One drag re-slots the day; affected customers are auto-notified of new
windows. What used to be ten phone calls is one gesture.

**All day:** live status flows in from the field — on-my-way, arrived, running long. The board is
never stale. David's job is exception-handling, and the UI puts exceptions (late, stuck,
unassigned, at-risk window) at the top, calm until something needs him.

**Design bar:** every routine assignment is drag-or-keyboard, < 2 seconds, no dialog. The board is
an instrument, not a form.

---

## Flow 3 — Booking → Scheduled (how work enters the system)

Work arrives three ways; all land as the same Job object:

1. **Phone call** → office creates the Job and a Visit in a few fields, customer/property
   auto-completing from history.
2. **Online booking** → the customer self-serves from a link (no app), picks a service and a real
   open window from live availability. Lands as a Lead/Scheduled job for the office to confirm.
3. **Recurring / maintenance plan** → membership agreements auto-generate Jobs on a schedule
   (the recurring-revenue engine that keeps techs busy in shoulder season).

Whatever the door, it's one object model downstream — no special-casing.

---

## Flow 4 — Estimate → Invoice → Paid → Reconciled (the money path)

The path that must reconcile to the penny:

```
Estimate (options)  →  customer approves  →  approved items become Invoice line items
   →  Payment captured (field or office)  →  Job closes  →  syncs to QuickBooks/Xero
```

**Non-negotiables:**
- No re-keying. An approved estimate *becomes* the invoice; nobody retypes line items.
- The owner's "today's revenue" is the sum of these payments — same data, not a parallel report.
- Partial payments, deposits, and tips are first-class (deposits on installs are standard in HVAC).
- Accounting sync is one-directional and idempotent; the GL is downstream, never the source of UI
  truth.

---

## Flow 5 — The Customer's Experience (the growth flow)

No download, all link-based, consumer-grade:

1. **Confirmation** — "You're booked Thursday 1–3pm with Anytown HVAC."
2. **On-my-way** — live map, tech name, photo, ETA. Rideshare-grade. This single feature generates
   more delight (and word-of-mouth) than any internal feature.
3. **Approve & pay** — review the quote, approve an option, pay, all from the link.
4. **Aftercare** — receipt, service summary, a nudge for a review, an invitation to a maintenance
   plan.

Every touch is branded to *the service business*, not to us. We make our customers look world-class
to *their* customers. That is the referral engine.

---

## How the flows interlock

```
   Customer books ──▶ Dispatcher schedules ──▶ Technician executes ──▶ Money flows ──▶ Owner sees truth
        (Flow 3)          (Flow 2)                 (Flow 1)             (Flow 4)         (Home / 03)
        └──────────────── Customer experience (Flow 5) wraps the whole arc ───────────────┘
```

Five flows, one Job object moving through them. Build these five well before building anything
else — they are the product. Everything in the [Roadmap](08-roadmap.md) is sequenced to make these
flows real in priority order.
