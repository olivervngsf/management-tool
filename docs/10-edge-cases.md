# 10 · User Edge Cases

Happy paths are easy; field service lives in the exceptions. This catalog enumerates the hard
real-world cases each [core flow](04-core-workflows.md) must handle gracefully. It is a design and
QA checklist: a flow isn't "done" until its edge cases here have a defined behavior. The research
is blunt about this — incumbents *lose data* and *double-book* precisely because they handle the
edges poorly ([research §6](research/market-and-competitors.md)).

Each case lists the **situation**, the **required behavior**, and the **principle** it protects
(see [Design Principles](05-design-principles.md)).

---

## A. Offline & sync (the defining hard problem)

> ~20% of jobs happen in dead zones. Incumbents silently lose photos, notes, and signatures — even
> erase unsynced data. Our **zero-data-loss guarantee** lives or dies here.

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| A1 | Tech runs an entire job with **no signal** (basement, rural) | Every step works locally; UI never blocks on network; clear "saved on device, will sync" state | Offline-first, Trust |
| A2 | App **killed / phone dies** mid-job with unsynced work | Nothing lost — local writes are durable; on relaunch, work is intact and sync resumes | Forgiving, Trust |
| A3 | Signal returns; **queued changes flush** | Background sync with retry/backoff; user sees honest progress, not a blocking spinner | Speed, Trust |
| A4 | **Conflict:** office edited the job (reassigned, price changed) while tech was offline editing the same job | Field observations/captures (photos, notes, readings, signature) **always win** — the tech was there. Server-authoritative data (assignment, pricebook) flows down and is surfaced, not silently overwritten. Never a silent clobber | Trust |
| A5 | **Payment captured offline** | Capture *intent* offline; the charge is confirmed server-side on reconnect and only then shown as "Paid." Never show paid on an unconfirmed charge | Trust (money) |
| A6 | Two techs edit the **same shared property** offline | Merge non-conflicting fields; flag true conflicts for human resolution, never auto-discard | Forgiving |
| A7 | Large **photo/video backlog** on a slow connection | Upload opportunistically, compress, resumable; job can close before media finishes uploading | Speed |
| A8 | Device **storage full** / sync repeatedly failing | Visible, honest warning with a clear remedy; never fail silently | Trust |

---

## B. Scheduling & dispatch

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| B1 | Dispatcher tries to **double-book** a tech | Prevent at the point of action — conflict is visible *before* confirm, not after | Trust, Dispatcher cockpit |
| B2 | **7:45am emergency** must be slotted | Surface closest available, qualified techs ranked; one-gesture re-slot; affected customers auto-notified of new windows | Speed |
| B3 | Job assigned to a tech **lacking required skill/cert** (e.g., EPA refrigerant) | Warn clearly; allow override with a reason (don't hard-block — the office knows its team) | Humane, Forgiving |
| B4 | **Drive time impossible** between back-to-back jobs | Flag the infeasible gap; suggest a fix | Trust |
| B5 | Tech **calls in sick**; their day must be redistributed | Bulk-reassign that day's visits; preserve customer windows where possible; notify | Speed |
| B6 | Customer **reschedules / cancels** late | One-tap reschedule; freed slot returns to the board; cancellation policy/fee configurable | Forgiving |
| B7 | **Recurring/maintenance** job auto-generates onto an already-full day | Generate as unassigned in the queue, never silently double-book | Trust |
| B8 | Appointment is a **wide arrival window** (1–3pm) vs. a fixed time | Model both; the board and the customer link show the right one | Clarity |
| B9 | **Multi-tech job** (install needing 2 people) | Assign a crew to one Visit; status and time roll up correctly | Clarity |

---

## C. The job itself (multi-visit, scope changes)

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| C1 | Job needs a **second trip** (part on order) | Spawn next Visit in two taps **without closing the Job**; Job stays open across trips | Clarity (Job≠Visit) |
| C2 | **Scope grows** on site (found a second problem) | Add line items / a second option mid-job; estimate and invoice update; re-signature if needed | Forgiving |
| C3 | Customer **declines all work** after diagnosis | Capture a diagnostic/trip fee per config; close as "no work done," not an error state | Humane |
| C4 | Tech **arrives, no one home** (no-show) | One-tap "customer not home"; trip fee per policy; reschedule flow; timestamped + photo proof | Trust |
| C5 | **Wrong address / can't access** (locked gate, wrong unit) | Capture reason; quick path to call customer/office; doesn't strand the day | Humane |
| C6 | Job **reopened after close** (callback, warranty) | Reopen links to original Job/Property history; warranty status visible; doesn't duplicate the record | Trust, data history |
| C7 | **Equipment not on file** the first time | Add equipment to the Property in seconds; it's there for every future visit (the compounding-data moat) | Clarity |

---

## D. Money & payments

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| D1 | **Partial payment / deposit** on a big install | First-class: deposits, progress payments, balance due tracked; invoice reflects remaining balance | Trust (money) |
| D2 | **Card declined** in front of the customer | Calm, non-embarrassing retry; offer alternate method (ACH, cash, check, "pay by link later") | Humane |
| D3 | **Cash / check** taken | Record without processing; reconciles into the day's totals | Trust |
| D4 | **Refund / partial refund / dispute** | Supported, audit-logged, reflected in owner's numbers and the accounting sync | Trust |
| D5 | **Tip** added by customer | First-class; attributed to the tech | Clarity |
| D6 | **Tax / surcharge** varies by jurisdiction or item | Configurable tax rules; correct per line item; reconciles exactly | Trust (money) |
| D7 | Owner's **"today's revenue" must tie out** to the invoices behind it | It's the same data aggregated, never a parallel report; reconciles to the penny | Trust |
| D8 | **QuickBooks sync** hiccup (the documented Jobber pain) | Idempotent, one-directional; failures are visible and retryable, never silent double-posts | Trust |

---

## E. Roles, permissions & multi-hat users

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| E1 | **Working owner** is Owner + Technician + Admin at once | Roles compose; one login, surfaces blend to total capability | Consistency |
| E2 | Tech **without pricing visibility** opens a job | UI **composes to capability** — no greyed-out teasing of forbidden fields | Humane, Clarity |
| E3 | **New hire**, day one, no training | Sees only their day; completes first job with zero training (a measurable bar) | Learnable |
| E4 | Admin builds a **custom role** ("Senior Tech sees cost, can't manage users") | Permissions configurable per role, not just built-ins | Flexibility |
| E5 | **Offboarding** a tech mid-day with open jobs | Reassign their work; revoke access; their historical records remain intact | Trust |
| E6 | Sensitive financial/admin surface accessed | Requires explicit role; change is audit-logged | Trust |

---

## F. Multi-industry / configuration

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| F1 | A **non-HVAC trade** (cleaning, landscaping) onboards | Configurable JobTypes/Forms/Pricebook adapt vocabulary and fields — no core code change | Flexibility |
| F2 | Trade-specific **form** (coil inspection vs. spring cleanup checklist) | Forms attach to JobTypes; render natively in the tech flow | Flexibility |
| F3 | A shop runs **multiple trades** under one roof | Job types coexist; a tech can be qualified across trades | Flexibility |
| F4 | Business has **multiple locations / dispatch hubs** | Data scopes to location; org-level roll-up for the owner | Clarity |

---

## G. Customer-facing experience

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| G1 | Customer **won't download an app** | Everything works from a link — no download, no forced account | Humane (growth) |
| G2 | **Tracking link** while tech is en route | Rideshare-grade live ETA; degrades gracefully if location is briefly unavailable | Trust |
| G3 | Customer **approves a quote option** from the link | Approval flows straight to the invoice; no re-keying | Speed |
| G4 | Customer **speaks another language** / accessibility needs | Localizable customer touchpoints; WCAG 2.2 AA | Accessible |
| G5 | **Notifications** must not spam | Sensible defaults, customer can opt down; branded to the *business*, not us | Humane |

---

## H. Data integrity & trust backstops

| # | Situation | Required behavior | Principle |
|---|---|---|---|
| H1 | **Migration in** from spreadsheets/QuickBooks/a competitor | Effortless import (the #1 switching risk in the research); customers/properties/pricebook map cleanly | Lowers switching cost |
| H2 | **Migration out** (customer wants to leave) | Easy export — no hostage-taking; this *builds* trust with a skeptical buyer | Trust |
| H3 | Accidental **destructive action** (delete a customer/job) | Undo / soft-delete; irreversible actions gated and rare | Forgiving |
| H4 | **Audit:** who changed this price / status / assignment | History is captured and viewable on the object's timeline | Trust |
| H5 | **Duplicate customer/property** created | Detect and offer merge; never silently fork history | Trust |

---

## How to use this catalog

- **Design:** every screen spec references the edge cases in its flow and states the behavior.
- **PRD:** acceptance criteria in the [PRD](09-prd.md) are written against these cases, not just the
  happy path.
- **QA:** this is the field-conditions test matrix. The offline section (A) and money section (D)
  are the highest-severity — they are where trust is won or permanently lost.

If we handle these gracefully where incumbents don't, the product *feels* world-class precisely in
the moments that matter most to a stressed person in the field.
