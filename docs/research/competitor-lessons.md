# What We Learned From Competitors → How We Win

A plain-language, reviewable list. For each lesson: **what they do**, **where it breaks**, and
**our play** to overcome it. This is the "check it out later" version of the
[full research](market-and-competitors.md) and [pain points](user-pain-points.md), written to be
scanned, not studied.

Your goal in one line: **intuitive, quick & easy to get the job done, low maintenance, fast
communication.** Every play below serves that.

---

## The one big lesson

> **Every competitor trades power for simplicity — nobody has both.**
> ServiceTitan is powerful but heavy. Jobber/Housecall are simple but shallow. The AI startups are
> betting on AI answering the phone. **Our opening: be simple for the technician AND complete enough
> for the business, on one clean data spine.**

---

## How a job actually gets done (the loop they all share)

You weren't sure what "getting a job done" means in these tools. It's the same core loop everywhere
— we just make each step faster. (Full detail in [Core Workflows](../04-core-workflows.md).)

```
Customer calls/books → Office schedules & assigns a tech → Tech drives out (customer gets a
heads-up) → Tech diagnoses & quotes on site → Does the work → Takes payment before leaving →
Job closes → Owner sees the money
```

- **The office/desktop part:** booking, scheduling, dispatching, configuring, seeing reports.
- **The field/mobile part:** the tech running that job — arrive, capture, quote, do, get paid, close.
- The whole thing is **one Job moving through stages**. Competitors make this loop clunky in
  different places; we make it smooth end-to-end.

---

## Device split — your instinct, confirmed

| Device | Who | What it's for | Design bias |
|---|---|---|---|
| **Mobile** | Technician (everyday user) + the Customer's link | Quick capture, get paid, communicate — in the field, often no signal | Few taps, big targets, voice/camera over typing, **works offline** |
| **Desktop** | Admin, Dispatcher, Management | Run the day's board, configure the system, see the money | Dense, fast, lots on screen, keyboard shortcuts |
| **Both (glanceable)** | Owner | "How did we do today?" | Same data, simplified, phone or desktop |

**Yes:** desktop helps admin/management; mobile is for the tech's quick reporting and communication.
That's the right call and it's how the [IA](../03-information-architecture.md) is built.

---

## The lessons → our plays (the list)

### 1. They made the technician's app too complex
- **What happens:** ServiceTitan's app "matches the desktop with lots of screens" and slows field
  work; its redesign dropped to ~3.3★. Techs reject apps with too many taps.
- **Our play:** the **"under-30-second job"** — camera and voice first, typing last, each screen
  shows only what that tech needs. *(Serves: intuitive, quick & easy.)*

### 2. Their apps lose data with no signal
- **What happens:** ~1 in 5 jobs hit a dead zone; photos/notes/signatures "quietly evaporate," and
  ServiceTitan can even erase unsynced data.
- **Our play:** **genuinely offline-first with a zero-data-loss guarantee.** The phone is the source
  of truth; it syncs when signal returns. *(Serves: low maintenance, reliability.)*

### 3. They take months and thousands of dollars to set up
- **What happens:** ServiceTitan onboarding is 12–16 weeks and $5K–$50K; some shops "never get
  onboarded."
- **Our play:** **live and dispatching the same day**, self-serve, no implementation fee.
  *(Serves: low maintenance.)*

### 4. Their price creeps — add-ons and lock-in
- **What happens:** Housecall Pro's #1 complaint is "cost creep" (bill 2–9× the sticker); ServiceTitan
  has lock-in and $15K–$46K cancellation fees.
- **Our play:** **all-inclusive, transparent, month-to-month, easy to leave.** Honesty is the
  differentiator. *(Serves: trust, low maintenance.)*

### 5. They get shallow as you grow
- **What happens:** Jobber/Housecall users outgrow them past ~15–20 techs (reporting, automation too
  thin) and jump to ServiceTitan — a painful migration.
- **Our play:** **one platform that scales with the shop** so they never have to switch.
  *(Serves: low maintenance, longevity.)*

### 6. Their Android app is second-class
- **What happens:** Housecall Pro is 3.2★ on Android vs 4.5★ on iOS — crashes, slow loading.
- **Our play:** **Android quality parity** as a hard requirement, not an afterthought. Many techs
  carry cheap Android phones. *(Serves: intuitive, quick.)*

### 7. Their tracking feels like surveillance
- **What happens:** techs feel "constantly watched"; it hurts morale and makes the data worse.
- **Our play:** **trust-first design** — tracking that helps the tech and customer, never feels like
  a spy tool. *(Serves: adoption, communication.)*

### 8. Communication is an afterthought
- **What happens:** customers expect "where's my tech?" certainty (rideshare-grade) and most tools
  don't deliver; office↔field updates are slow or manual.
- **Our play:** **fast, built-in communication** — one-tap "on my way" with a live tracking link (no
  app download for the customer), and real-time field↔office status. *(Serves: quick communication —
  your explicit goal.)*

### 9. Double-booking and a stale board
- **What happens:** even premium tools double-book and show stale status; dispatchers lose trust in
  the board.
- **Our play:** a **dispatcher cockpit** that prevents conflicts before they happen and shows live,
  trustworthy status. *(Serves: quick & easy for the office.)*

### 10. AI is becoming table stakes, not a moat
- **What happens:** Avoca ($1B valuation), Netic, Swivl all push AI that answers calls and writes
  estimates.
- **Our play:** have a **credible AI story** (AI receptionist/booking, voice-to-structured notes),
  but win on the **experience + clean data** the AI runs on — not AI as a bolt-on. *(Serves:
  intuitive, future-proof.)*

---

## How this maps to your four goals

| Your goal | The plays that deliver it |
|---|---|
| **Intuitive experience** | #1 low-tap, #6 Android parity, #10 AI in the loop, the whole [design system](../design-system/README.md) |
| **Quick & easy to get job done** | #1 under-30-sec job, #9 fast dispatch, the smooth end-to-end loop |
| **Low maintenance** | #2 offline reliability, #3 same-day setup, #4 honest pricing, #5 scales with you |
| **Quick communication** | #8 on-my-way + live tracking + real-time field↔office, #7 trust-first |

---

## How to use this list

- **Review it** when you're weighing a feature: does it serve one of the four goals above? If not,
  it waits.
- **Check competitors out yourself** against this list — every claim links to its source in the
  [research report](market-and-competitors.md).
- It pairs with the [Pain Points Registry](user-pain-points.md) (what users hate) and the
  [PRD](../09-prd.md) (what we'll build to fix it).
