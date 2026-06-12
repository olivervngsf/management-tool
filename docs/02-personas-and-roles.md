# 02 · Personas & Roles

Five people touch the system. Design for each by name. The cardinal mistake in FSM is
designing one app and forcing everyone into it — the dispatcher's needs are the opposite of the
technician's, and both differ from the owner's. We build **one platform, role-tailored surfaces**.

---

## The five people

### 1. Maria — the Technician (the everyday user)

**Context:** In a truck or a crawlspace. One hand free. Gloves on. Phone in a mount or a pocket.
Spotty signal. Paid to fix things, not to do data entry. Has used apps that fought her and she
resents them.

**Jobs to be done:**
- Know where I'm going next and what I'm walking into before I knock.
- Capture what I found (photos, readings, notes) without typing an essay.
- Build a quote in front of the customer that looks professional and closes.
- Get paid before I leave.
- Close the job and move on without "finishing paperwork tonight."

**What she needs from the UI:** Big targets, thumb-reachable. Offline-first, always. Voice and
camera over keyboard. Zero ceremony. The app should feel like it respects her time and her trade.

**Failure mode to avoid:** Making her feel surveilled or treated as a data-entry clerk. Tone and
trust matter as much as function.

---

### 2. David — the Dispatcher / Office Coordinator (the power user)

**Context:** At a desk, two monitors, phone ringing. Juggling 8–15 techs across a city. The day
is a living puzzle: cancellations, emergencies, traffic, a tech calling in sick at 7:45am.

**Jobs to be done:**
- See the whole day at a glance and feel in control of it.
- Assign and re-assign jobs in seconds; drag, don't dig through menus.
- Know instantly who is free, who is running late, who is closest to the new emergency call.
- Reach any customer or tech in one tap.
- Keep promises: never double-book, never strand a customer in a window.

**What he needs from the UI:** Density, speed, keyboard shortcuts, real-time updates, a board that
reads like an instrument. This is the one place where *more information on screen* is the goal.

**Failure mode to avoid:** Hiding the board behind clicks. Latency. Anything that makes him doubt
the board reflects reality *right now*.

---

### 3. Sofia — the Owner / Operator (the decision-maker who pays)

**Context:** Started in the trade, now runs the business. Checks the phone between meetings and at
night. Cares about cash, capacity, and reputation. Will not build reports.

**Jobs to be done:**
- Are we making money today / this week? Where is revenue stuck?
- Is my team productive? Who's carrying the load, who needs help?
- Are customers happy? Any fires I need to put out?
- Is the business healthy enough to hire, buy a truck, take the loan?

**What she needs from the UI:** A truthful, glanceable home. Numbers she trusts that reconcile to
reality. Drill-down when she wants it, never required. Works on her phone first.

**Failure mode to avoid:** Vanity dashboards. Numbers that don't tie out destroy trust instantly.

---

### 4. Alex — the Administrator (the configurer)

**Context:** Office manager or ops lead. Sets the system up and keeps it running. Manages users,
price book, job types, forms, permissions, integrations.

**Jobs to be done:**
- Onboard and offboard staff; set who-can-do-what.
- Maintain the price book and the service catalog.
- Configure the system to match how *this* business actually works.
- Connect QuickBooks, the payment processor, the phone system.

**What they need from the UI:** Powerful, forgiving configuration. Clear permission models.
Bulk operations. Undo. Templates and sane defaults so setup is a day, not a month. This is where
multi-industry flexibility is exercised — Alex is the person who bends the tool to the trade.

**Failure mode to avoid:** Configuration so rigid it needs us, or so loose it breaks the techs'
experience downstream.

---

### 5. The Customer — the homeowner / property manager (the reason any of this exists)

**Context:** Has a broken AC in July. Anxious, wants certainty: when, who, how much. Compares this
experience to every consumer app they use.

**Jobs to be done:**
- Book or confirm an appointment without friction.
- Know who is coming and when — a real-time "your tech is 12 minutes away."
- Approve a quote and pay without hunting for a checkbook.
- Feel taken care of.

**What they need from the UI:** No app download required. A link that just works. Rideshare-grade
tracking. A clean quote they can approve with a tap. This experience is a growth engine — a
customer who loves it asks "what app do you use?" and tells their neighbor.

**Failure mode to avoid:** Forcing an account or download. Dead tracking links. Anything that feels
like 2010 enterprise software leaking out to the customer.

---

## Roles & permissions model

Personas describe *people*; roles describe *granted capability*. One person can hold multiple
roles (a working owner is often Owner + Technician + Admin). Roles are **composable permission
sets**, not fixed personas — this is essential for small shops where people wear many hats.

| Capability area | Technician | Dispatcher | Owner | Admin |
|---|---|---|---|---|
| View own schedule & jobs | ✅ | ✅ | ✅ | ✅ |
| View all schedules / the board | — | ✅ | ✅ | ✅ |
| Assign / reassign jobs | — | ✅ | ✅ | ✅ |
| Create estimates & take payment | ✅ | ✅ | ✅ | ✅ |
| See pricing / margin / cost | configurable | ✅ | ✅ | ✅ |
| Company financials & reports | — | partial | ✅ | ✅ |
| Manage users & permissions | — | — | ✅ | ✅ |
| Edit price book / job types | — | — | ✅ | ✅ |
| Integrations & billing | — | — | ✅ | ✅ |

**Design rules for permissions:**
- **Least privilege by default**, expand by grant. A new technician sees only their day.
- **Permissions are configurable per role, not just per built-in role.** Alex can create a
  "Senior Tech" role that sees cost but can't manage users.
- **Permission boundaries are invisible when respected.** A technician without pricing visibility
  should never see a greyed-out price field — the UI composes to what they *can* do, it doesn't
  tease what they can't.
- **Sensitive money/admin surfaces require explicit role**, and changes are audit-logged.

## The design implication

These five people justify the platform shape: a **focused mobile app** (Maria, and the
customer's link), a **dense desktop console** (David, Alex), and a **glanceable cross-device home**
(Sofia). The next document turns these needs into structure.
