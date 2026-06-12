# User Pain Points Registry

A living catalog of the real pains FSM users feel, drawn from the
[market & competitive research](market-and-competitors.md) (G2/Capterra/Trustpilot/Reddit synthesis,
app-store reviews, ServiceTitan Community). Each pain is an **opportunity**: it maps to a
differentiation bet in the [strategy](../01-product-strategy.md), a requirement in the
[PRD](../09-prd.md), and/or an edge case in [doc 10](../10-edge-cases.md).

**How to read severity:** `Frequency` = how often it shows up in reviews/forums; `Severity` = how
much it drives churn or blocks adoption. **P0** = trust-destroying / deal-breaking, **P1** = major
friction, **P2** = annoyance. Personas per [doc 02](../02-personas-and-roles.md): Tech (Maria),
Dispatch (David), Owner (Sofia), Admin (Alex), Customer.

> This is a registry, not prose — add rows as new evidence arrives. Keep `Our response` honest:
> "not yet" is a valid status.

---

## Severity summary

| Severity | Count | The headline pains |
|---|---|---|
| **P0** | 6 | Offline data loss, payment trust, double-booking, onboarding wall, today's-number doesn't tie out, switching/migration |
| **P1** | 9 | Too many taps, Android performance, cost creep, lock-in/ETFs, learning curve, surveillance morale, sync failures, stale board, app crashes |
| **P2** | 5 | Update regressions, support latency, reporting rigidity, notification spam, duplicate records |

---

## 1. Technician (Maria) — the wedge

| ID | Pain | Sev | Freq | Evidence (source) | Our response |
|---|---|---|---|---|---|
| PP-T1 | **Offline data loss** — photos, notes, signatures "quietly evaporate" in dead zones; ST can erase unsynced data | **P0** | High | ~20% of jobs hit no signal; ST "Download Pricebook" wipes unsaved changes ([ST Community](https://community.servicetitan.com/t5/Mobile/Offline-Synching-Issues/m-p/24503), [wednesday.is](https://mobile.wednesday.is/writing/offline-sync-mobile-apps-field-teams-dead-zones-2026)) | **Zero-data-loss offline-first** — [PRD R1.11/NFR1](../09-prd.md), [edges A1–A8](../10-edge-cases.md) |
| PP-T2 | **Too many taps / data-entry burden** — "so many screens and options that slow down field work"; techs carry paper as backup | **P1** | High | ST app redesign "more complex," dropped to ~3.3★; "a tech should start a form in <30s" ([getonecrew](https://www.getonecrew.com/post/servicetitan-reviews), [repair-crm](https://www.repair-crm.com/2026/05/30/digital-forms-for-service-technicians-a-2026-guide-for-small-field-teams)) | **"Under-30-second job"** — camera/voice-first, role-composed screens ([PRD R1.5](../09-prd.md)) |
| PP-T3 | **App crashes / freezes mid-job**, losing work; battery drain | **P1** | High | crashes during invoice creation, photo-upload failures ([contractortoolstack](https://contractortoolstack.com/software/housecall-pro/)) | Durable local writes survive app kill ([edge A2](../10-edge-cases.md)) |
| PP-T4 | **Android is a second-class citizen** — slow, crashy vs. iOS | **P1** | Med | HCP **3.2★ Android vs 4.5★ iOS** ([rivetops](https://www.rivetops.io/jobber-vs-housecall-pro)) | **Android quality parity** as an explicit NFR9 ([PRD](../09-prd.md)) |
| PP-T5 | **Feels surveilled** — GPS used for discipline, "constant surveillance"; hurts morale *and* data quality | **P1** | Med | 23% of monitored workers feel watched; tracking "breeds resentment" ([fieldservicely](https://www.fieldservicely.com/blog/how-to-track-field-employees-without-micromanaging), [memtime](https://www.memtime.com/blog/is-time-tracking-micromanagement)) | **Trust-first, not surveillance-first** design ([strategy](../01-product-strategy.md), [edge E*](../10-edge-cases.md)) |
| PP-T6 | **Updates make it slower** — regressions erode a working tool | **P2** | Med | "Every time there's an update, it seems to slow down" ([getonecrew](https://www.getonecrew.com/post/servicetitan-reviews)) | Performance as a gated NFR2; no regressions ship |

## 2. Dispatcher (David)

| ID | Pain | Sev | Freq | Evidence | Our response |
|---|---|---|---|---|---|
| PP-D1 | **Double-booking** — "one of the most frustrating challenges," worsens as shops scale | **P0** | High | causes "customer dissatisfaction, tech burnout, revenue loss" ([fieldproxy](https://www.fieldproxy.ai/blog/fix-double-booking-issues-service-scheduling-guide)) | **Conflict prevented at point of action** ([PRD R2.3](../09-prd.md), [edge B1](../10-edge-cases.md)) |
| PP-D2 | **Stale / unreliable real-time state** — even ST's board: location needs Services on, long-horizon jobs don't show, only validated addresses map | **P1** | Med | ([ST dispatch FAQ](https://help.servicetitan.com/docs/dispatch-board-faq)) | Trustworthy live status < 1s ([PRD R2.1/NFR3](../09-prd.md)) |
| PP-D3 | **Slow re-slotting under pressure** (emergencies, sick calls) | **P1** | Med | manual scheduling, poor comms cited as root cause ([buildops](https://buildops.com/resources/field-service-dispatching-guide/)) | One-gesture emergency re-slot + bulk reassign ([PRD R2.4](../09-prd.md), [edges B2/B5](../10-edge-cases.md)) |

## 3. Owner (Sofia)

| ID | Pain | Sev | Freq | Evidence | Our response |
|---|---|---|---|---|---|
| PP-O1 | **Paying for features they never use** — "$25K–35K/yr on features they never touch" | **P1** | High | ([fieldcamp](https://fieldcamp.ai/reviews/servicetitan/)) | All-inclusive pricing, no Pro-module maze ([strategy pricing](../01-product-strategy.md)) |
| PP-O2 | **Numbers they can't trust** — needs today's revenue to reconcile, not a vanity dashboard | **P0** | Med | trust is the asset in operational SW ([design principle 8](../05-design-principles.md)) | Owner's Home == sum of confirmed payments, $0.00 variance ([PRD R3.3](../09-prd.md), [edge D7](../10-edge-cases.md)) |
| PP-O3 | **QuickBooks sync breaks**, causing manual fixes | **P1** | Med | "unreliable accounting-sync causing manual fixes" ([checkthat Jobber](https://checkthat.ai/brands/jobber/reviews)) | Idempotent one-way sync, visible/retryable ([PRD R3.4](../09-prd.md), [edge D8](../10-edge-cases.md)) |

## 4. Buyer / Admin (Alex) — adoption & commercial

| ID | Pain | Sev | Freq | Evidence | Our response |
|---|---|---|---|---|---|
| PP-B1 | **Onboarding wall** — ST's 12–16 wk, $5K–$50K setup; "never onboarded despite paying for a year" | **P0** | High | "infeasible for a 10-person shop in busy season" ([fieldcamp](https://fieldcamp.ai/reviews/servicetitan/), [missing-middle](https://fieldcamp.medium.com/the-missing-middle-why-80-of-field-service-businesses-are-underserved-0978a3fe40c3)) | **Live same day**, no fee, self-serve ([PRD G5](../09-prd.md)) |
| PP-B2 | **Cost creep from add-ons** — HCP's #1 complaint; bill 2–9× the advertised entry | **P1** | High | 5-tech setup ≈ $1,600/mo ([projul](https://projul.com/blog/housecall-pro-pricing-analysis-2026/)) | Bundled, transparent pricing ([strategy](../01-product-strategy.md)) |
| PP-B3 | **Lock-in & termination fees** — documented ETFs $15K–$46K; cancel friction | **P0** | Med | ([fieldcamp](https://fieldcamp.ai/reviews/servicetitan/), Trustpilot ~2.9 HCP) | Month-to-month, no ETF, **easy export** ([PRD NFR8](../09-prd.md), [edge H2](../10-edge-cases.md)) |
| PP-B4 | **Steep learning curve** — "overwhelming," staff "scared to dive in" | **P1** | High | ST's #1 weakness on G2 ([G2](https://www.g2.com/products/ServiceTitan/reviews)) | Progressive disclosure; first job, no training ([PRD G2](../09-prd.md)) |
| PP-B5 | **Switching cost / data gravity** — migrating history/pricebook is the thing that traps people | **P0** | High | top switching risk ([research §7](market-and-competitors.md)) | **Effortless import** ([PRD NFR8](../09-prd.md), [edge H1](../10-edge-cases.md)) |
| PP-B6 | **Slow support** — long waits, unresolved escalations (both ST and HCP polarizing) | **P2** | Med | ([getonecrew](https://www.getonecrew.com/post/servicetitan-reviews), [checkthat HCP](https://checkthat.ai/brands/housecall-pro/reviews)) | Not a product feature — a service-design commitment to track post-launch |
| PP-B7 | **Reporting too rigid / shallow** — limited templates (ST); outgrown past ~15–20 techs (Jobber/HCP) | **P2** | Med | ([capterra](https://www.capterra.com/p/150053/ServiceTitan/), [getonecrew Jobber](https://www.getonecrew.com/post/jobber-reviews)) | Deferred to R5 reporting depth ([PRD](../09-prd.md)) — *not yet* |

## 5. Customer (homeowner)

| ID | Pain | Sev | Freq | Evidence | Our response |
|---|---|---|---|---|---|
| PP-C1 | **Forced app download / account** to interact | **P1** | Med | self-service is "table stakes" ([servicepower](https://www.servicepower.com/blog/field-service-and-the-age-of-consumer-self-service)) | Link-based, no download ([PRD R2.5](../09-prd.md), [edge G1](../10-edge-cases.md)) |
| PP-C2 | **No real-time "where's my tech"** certainty | **P1** | Med | customers expect rideshare-grade tracking ([servicepower](https://www.servicepower.com/blog/field-service-and-the-age-of-consumer-self-service)) | On-my-way live tracking link ([PRD R2.5](../09-prd.md), [edge G2](../10-edge-cases.md)) |
| PP-C3 | **Notification spam** | **P2** | Low | (general FSM UX) | Sensible defaults, opt-down, business-branded ([edge G5](../10-edge-cases.md)) |

---

## Coverage check — does the product answer the worst pains?

Every **P0** has a committed response:

| P0 pain | Addressed by |
|---|---|
| PP-T1 Offline data loss | R1.11 / NFR1, edges A1–A8 |
| PP-D1 Double-booking | R2.3, edge B1 |
| PP-O2 Untrustworthy numbers | R3.3, edge D7 |
| PP-B1 Onboarding wall | G5, same-day live |
| PP-B3 Lock-in / ETFs | NFR8, easy export, no-contract pricing |
| PP-B5 Switching cost | NFR8, effortless import |

**Gaps we're consciously not solving yet (P2):** deep reporting (PP-B7) and support latency (PP-B6)
are post-PMF / service-design, not Phase 1–3 — recorded here so they aren't forgotten.

## Maintenance

- Add a row whenever new evidence (a review, a sales call, a design-partner interview) surfaces a
  pain — with a source.
- When a pain's response ships, link the release and move it to a "resolved" view.
- Re-score severity from real customer data once we have design partners; today's scores are
  research-derived.
