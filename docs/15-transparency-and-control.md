# 15 · Transparency, Status & Staying in Control

> The promise: **nobody is ever in the dark, and the human is always in charge.** Everyone knows
> what's happening (time, status, money) at their own altitude; problems surface **early — before
> they go out of scope or it's too late**; and people stay in control of every decision.

This is the human-facing companion to the [AI Operating Model](13-ai-operating-model.md) (which
handles the AI side of the same values) and it builds on the [status model](14-data-model.md) and
[core flows](04-core-workflows.md). It captures a theme that runs through everything: **trust is
built by visibility and control, not by automation.**

---

## 1. Everyone knows the time & status (shared, at the right altitude)

A single source of truth for "what's going on," shown differently to each person — never a separate
version that can drift.

| Who | What they see | When |
|---|---|---|
| 🔧 **Technician** | their day, the current job, their next stop, time on site | live, on the phone |
| 🏢 **Office / dispatch** | the whole board — every tech's status, who's late, what's unassigned | live, < 1s after a field action |
| 👑 **Owner** | the rolled-up day — jobs done vs scheduled, money in, anything at risk | glanceable |
| 🙋 **Customer** | their appointment, the on-my-way ETA, what's approved | their tracking link |

**Rules:**
- **Status is honest and current.** It reflects reality *now*, including sync state when offline
  ("saved on device, will send") — never a comforting lie. ([Trust principle](05-design-principles.md))
- **One status, many views.** The owner's "in progress" and the customer's "your tech is 12 min
  away" are the *same fact* at different altitudes. ([IA](03-information-architecture.md))
- **Time is explicit.** Arrival window, on-site time, expected duration, and "running long" are all
  visible — so nobody guesses. ([Date/status model](14-data-model.md))

### Location & tracking — the bright line (yes, we track; no, we don't surveil)

We **do** track tech location and show people on a map — every FSM tool does, and it's
[table stakes](research/table-stakes.md): the dispatcher needs to send the *closest qualified* tech,
the customer needs a real "12 minutes away," and routes need optimizing. The board shows tech status;
the customer link shows the on-my-way ETA. **Trust-first does not mean no GPS.**

The difference from a surveillance tool like [Hubstaff](research/market-and-competitors.md) is
**purpose, transparency, and respect** — the same data, used differently:

| Operational tracking — **what we do** ✅ | Surveillance — **what we refuse** 🚫 |
|---|---|
| Location → dispatch the closest tech, give the customer an ETA, optimize routes | Location → discipline, "gotcha" reports, watching breaks |
| Tracked **on the clock / en route**, tied to the job | Tracked all day, on breaks, off-shift |
| **Transparent:** the tech sees exactly what's shared and with whom ([disclosure rules](13-ai-operating-model.md)) | Hidden monitoring the worker can't see |
| **The tech sees their own data**; it helps them | Data weaponized against the worker |
| Job status, GPS for routing/ETA | **No** screenshots, keystroke/app/URL monitoring, or webcam |

**The rule:** *tracking must serve the tech and the customer, never spy on the tech.* Location is a
tool for getting the right person there fast and keeping the customer informed — it is never a
management cudgel. (And the [private personal layer](16-notes-and-reflection.md) is always off-limits
to tracking entirely.) That's how a NEED (GPS on a map) and our trust-first promise both hold true.
The full mechanics — location follows the *job* not the person, on at "On my way," off at "Arrived" —
are designed in [Location & Privacy Design](18-location-privacy-design.md).

---

## 2. The One-Line Report (the signature habit)

The lightweight pulse you asked for: **the field always sends a short, plain update to the office —
so the office knows what's happening before it's too late.** Small, frequent, low-effort.

**What it is:** a one-sentence status the technician sends (or confirms) at the key beats of a job —
not a form, not paperwork. A heartbeat the office can scan.

```
  7:58  "On my way to the Reyes job."                         (auto from "On my way")
  8:21  "On site. Older unit than expected — taking a look."   (one tap + 4 words)
  8:50  "Found a cracked heat exchanger. Quoting replacement." ⚠ concern flagged
  9:30  "Customer approved Gold option. Starting now."
 10:40  "Done. Paid by card. Recommended a return for the vent." ✅
```

**How it stays effortless (so it actually happens):**
- **Mostly automatic.** Status taps the tech already makes ("On my way," "Arrived," "Paid") *become*
  the report — no extra step.
- **One line to add color.** When there's something to say, it's a single sentence — typed in a
  moment or spoken (voice→text). [AI can draft it](13-ai-operating-model.md) from the job state; the
  tech confirms. Never a wall of fields.
- **Flows to the right people**, governed by [disclosure rules](13-ai-operating-model.md) — the
  office sees operational detail; the customer sees only what's meant for them.

**Why it matters:** the office gets a continuous, low-cost picture of the day. A dispatcher scanning
ten one-liners *feels* the day and catches the one that says "taking longer than expected" — **before**
it becomes an angry customer call. It's the cheapest possible early-warning system, and it keeps the
field and office on the same page without meetings or phone tag.

---

## 3. Raise the concern early — before it's out of scope or too late

The whole point of the pulse above is **catching trouble while it's still small.** Two senses,
working together:

**A. The human flags it.** The technician can raise a concern in one tap from the job — "this is
bigger than quoted," "part won't arrive in time," "customer is unhappy." It goes up immediately,
visibly, with context. Raising a concern is *encouraged and easy*, never a hassle or a black mark.

**B. The system watches for it.** [AI operational awareness](13-ai-operating-model.md) quietly
notices the early signs and surfaces them to the right human:
- **Out-of-scope, early:** work is growing past the approved estimate → flag to re-quote *now*, not
  at invoice time when it's a fight. "This job is trending 40% over the estimate — re-quote?"
- **Running late:** a visit will blow its window → tell dispatch *before* the customer calls.
- **Blocked / waiting:** a part is late from a supplier → surface it so the customer can be told
  proactively. ([the late-partner case](13-ai-operating-model.md))
- **Off-plan:** a project phase slipping its milestone → raised to the owner/PM while there's time to
  act.

**The principle:** *surface early, decide deliberately.* The system's job is to **notice and tell the
right person in time** — never to quietly fix it and hope. A small heads-up at 9am beats a crisis at
5pm. Out-of-scope work gets re-approved, not absorbed; late parts get communicated, not discovered.

---

## 4. Financial transparency (contracts, how people pay, no surprises)

Money is where trust is won or lost, so it's the most transparent thing in the system.

**The customer always knows what they owe and how to pay:**
- The **estimate** shows clear options and prices up front; approving is a tap.
- **How to pay is easy and open:** card (incl. tap-to-pay), ACH, cash, check, or financing — the
  customer picks. A receipt goes out instantly. ([Payment fields](14-data-model.md))
- **No hidden fees.** What's quoted is what's charged; changes are re-approved, not slipped in
  (§3 out-of-scope).

**Contracts (service agreements / memberships) are transparent:**
- The plan states plainly what's covered, what it costs, **how often it bills** (monthly / quarterly
  / annual), the benefits, and when it renews. ([Contract fields](14-data-model.md))
- The customer and the office both see status, remaining visits, and the next billing date — no
  mystery charges.

**The office and owner see the truth, reconciled:**
- Balance due, payments made, deposits, AR — all visible and **reconciling to the penny** against the
  invoices behind them ([Owner's Home](09-prd.md), [Trust principle](05-design-principles.md)).
- Every payment, refund, and discount is logged and traceable.

**Full transparency with the system itself:** when AI fills a price or drafts an invoice, you can see
*where it came from* (provenance), and a human approves before any money moves ([the gate](13-ai-operating-model.md)).
Nothing about money is a black box.

---

## 5. Users stay in control

The thread tying it all together — and a deliberate stance against the "let the AI run it" wave:

- **The human decides; the system assists.** AI prepares, suggests, and warns; a person chooses and
  approves. Accountability never leaves the human. ([Autonomy ladder](13-ai-operating-model.md))
- **The gate is theirs.** Nothing touching money or the customer happens without a human pressing the
  button — and the record shows who.
- **Everything is visible and reversible.** No silent actions; undo everywhere. Control means you can
  always see what happened and walk it back.
- **They set the rules.** Admins configure what AI may do and what's shared; the system operates
  inside those guardrails and never moves the fence. ([Guardrails](13-ai-operating-model.md))

> **Control isn't a feature you add — it's the absence of surprises.** People stay in control because
> they always know what's happening, they hear about problems early, and nothing important happens
> without them. That is the trust this product is built to earn.

---

## How this shows up in the product (so it's not just words)

| Promise | Where it lives |
|---|---|
| Shared, honest status | the board, the job screen, the owner home, the customer link |
| The One-Line Report | auto-generated from status taps + one-line add; flows to the office |
| Early concern-raising | one-tap "raise concern" + AI off-plan/out-of-scope/late detection |
| Financial transparency | clear estimates, open payment options, plain-language contracts, reconciled owner numbers |
| Staying in control | the human gate, provenance, undo, admin-set guardrails |

These become concrete requirements in the [PRD](09-prd.md) (status & notifications in R1–R2, the
money path in R3) and are held to account by the [design principles](05-design-principles.md) —
especially Trust (#8) and Humane tone (#10).
