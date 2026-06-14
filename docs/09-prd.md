# 09 · Product Requirements Document (PRD)

**Product:** Fieldwork — field service management for the trades
**Status:** Foundation / pre-build · **Last updated:** 2026-06-13
**Owner:** Product · **Source of truth for:** scope, requirements, acceptance criteria, metrics

> This PRD operationalizes the [Strategy](01-product-strategy.md), grounded in
> [Research](research/market-and-competitors.md), and built on the [IA](03-information-architecture.md),
> [Flows](04-core-workflows.md), [Edge Cases](10-edge-cases.md), and [Design Principles](05-design-principles.md).
> It scopes **Phase 1–3** (the wedge through the money path) in requirement-level detail; later
> phases are summarized. Requirements use **MoSCoW** (Must / Should / Could / Won't-yet) and each
> Must has acceptance criteria.
>
> **2026-06-13 update:** absorbs the [AI Operating Model](13-ai-operating-model.md),
> [Transparency & Control](15-transparency-and-control.md), [Notes & Reflection](16-notes-and-reflection.md),
> and the [Data Model](14-data-model.md) — adding requirements for the One-Line Report, the personal
> reflection layer, the AI gate/transparency, job costing, contracts & the customer portal, and the
> configuration layer. New requirements name their [UX backlog](ux-ui-review.md) gap (G15–G29) for
> design traceability.

---

## 1. Problem & opportunity

Service businesses run on coordination, but the software that runs them forces a trade-off between
power and usability. **~45% of trades shops still use pen-and-paper/spreadsheets and ~56% use no
FSM software** ([research §2](research/market-and-competitors.md)). Incumbents leave clear seams:
ServiceTitan is powerful but heavy (12–16 wk, $5K–$50K onboarding; mobile app regressed to ~3.3★);
Jobber/Housecall Pro are loved but get expensive and shallow at scale; and a well-funded AI wave is
making AI call-handling table stakes. The best-evidenced unmet needs are **mobile/offline failure**
and **data-entry friction** — i.e., the technician's daily loop.

**Opportunity:** win the technician's daily loyalty with a genuinely offline-first, radically
low-friction, Apple-grade experience — then expand to the dispatcher and owner on one data spine,
priced honestly and configurable across trades.

## 2. Goals & non-goals

**Goals**
- G1. A technician runs an entire job end-to-end on a phone, **fully offline**, with zero data loss.
- G2. A new technician completes their first job **with no training**.
- G3. A dispatcher runs a full day for a 10+ tech shop from one live board.
- G4. An owner sees a **today's-revenue number that reconciles to the penny**.
- G5. A shop is **live and dispatching the same day** — no implementation project, no fee.
- G6. The core flexes to a **second trade via configuration**, not code.

**Non-goals (now)** — per strategy's deliberate "no":
- Deep accounting/GL (we integrate with QuickBooks/Xero).
- Full marketing-automation suite, fleet telematics (partner, don't build).
- Telephony **rails** (partner, Twilio-style) — but we *do* build the **Leads & Communications**
  experience (lead pipeline + unified calls/texts/voicemail inbox) on top.
- Enterprise multi-franchise consolidation.
- Native Swift/Kotlin rewrites (Expo carries us past PMF).

## 3. Success metrics — "what success looks like"

**North-star: Technician daily active use > 90%** of assigned techs. If the field user won't use it,
nothing downstream matters ([strategy](01-product-strategy.md)). Everything below ladders to it.

Metrics are grouped so you can see success at a glance — each is **leading** (predicts) or **lagging**
(confirms). Targets are starting bars to refine with real shops.

**① Adoption & retention — the wedge (the most important group)**
| Metric | Target | L/L |
|---|---|---|
| Technician daily active use (of assigned techs) | **> 90%** | lagging |
| New tech completes first job **without training** | ≥ 95% | leading |
| Technician satisfaction / NPS | > 50 (strong) | lagging |
| Shop (logo) gross retention | > 90%/yr | lagging |
| Time-to-first-dispatch for a new shop | < 1 day | leading |

**② Experience & speed (do they *feel* it?)**
| Metric | Target | L/L |
|---|---|---|
| Perceived primary-action latency | < 100 ms | leading |
| Cold launch → usable | < 2 s | leading |
| **Time to complete a core job-to-be-done** | **< 30 seconds** | leading |
| App rating — **iOS *and* Android** | ≥ 4.5★ both (no Android gap) | lagging |

> **Note — the 30-second rule:** a *job-to-be-done* is one discrete task the user came to do —
> capture a note/photo, add a line item, send a One-Line Report, take a payment step. **Each must be
> completable in under 30 seconds.** Measure real time from intent → done (not taps), on a phone,
> with gloves, on a mediocre connection. If a task can't be done in 30s, it's a design defect —
> simplify it (fewer fields, voice/photo over typing, smart defaults, AI write-it-fills). This is the
> "under-30-second job" as a hard target; it governs R1.5 and the whole technician loop.

**③ Reliability & trust (does it just work?)**
| Metric | Target | L/L |
|---|---|---|
| Offline job completion (no signal) | 100% of [Flow 1](04-core-workflows.md) | leading |
| **Data-loss incidents** | **0** | lagging |
| Sync success rate | > 99.5% | leading |
| Board update propagation (field → dispatcher) | < 1 s | leading |

**④ Money correctness & impact**
| Metric | Target | L/L |
|---|---|---|
| Today's-revenue reconciliation error | **$0.00** | lagging |
| Invoices paid **on-site** (no AR chase) | rising % | lagging |
| Days-sales-outstanding (AR) for the shop | falling | lagging |

**⑤ Transparency & communication (your stated goal)**
| Metric | Target | L/L |
|---|---|---|
| Jobs with a One-Line Report pulse | > 95% | leading |
| Out-of-scope work caught **before** invoice | rising % | leading |
| Customer on-my-way / portal link open rate | high | lagging |

**⑥ AI — trust-first**
| Metric | Target | L/L |
|---|---|---|
| AI-filled fields accepted (after human review) | high, with edits welcome | leading |
| Admin time saved per job (less data entry) | rising | lagging |
| Money/customer actions that were human-approved | **100%** (gate adherence) | lagging |

**⑦ Flexibility & growth (the flywheel)**
| Metric | Target | L/L |
|---|---|---|
| 2nd vertical onboarded **by config, no code** | achievable | leading |
| New shops arriving via **word-of-mouth/referral** | rising % | lagging |
| Expansion (seats / agreements per shop over time) | rising | lagging |

> **How to read it:** watch the **leading** metrics weekly (they tell you early if you're winning);
> the **lagging** metrics (retention, NPS, referral, reconciliation) are the proof. The single number
> that matters most early is **technician daily use** — get that, and the rest follows.

## 4. Users & roles

See [Personas & Roles](02-personas-and-roles.md): Maria (Technician), David (Dispatcher), Sofia
(Owner), Alex (Admin), and the Customer. Permissions are **composable roles, least-privilege by
default**; the UI **composes to capability** (no greyed-out teasing).

## 5. Scope by release

| Release | Theme | Flows | Doc |
|---|---|---|---|
| **R1** | The Technician's Job (the wedge) | [Flow 1](04-core-workflows.md) | Phase 1 |
| **R2** | The Dispatcher's Board | [Flows 2–3](04-core-workflows.md) | Phase 2 |
| **R3** | The Money Path + Owner's Home | [Flow 4](04-core-workflows.md) | Phase 3 |
| **R4** | Configurability & multi-industry | — | Phase 4 |
| **R5** | Scale & polish → GA | — | Phase 5 |

---

## 6. Requirements

Format: **[ID] (MoSCoW)** requirement → *Acceptance criteria.* Edge-case IDs reference
[doc 10](10-edge-cases.md).

### R1 — The Technician's Job *(MVP, offline-first)*

**Today & job list**
- **R1.1 (Must)** Tech sees a chronological "Today" list of their visits, current job pinned.
  *AC: opens in < 2s cold; reflects last sync; works offline showing last-synced data (A1).*
- **R1.2 (Must)** Tech opens a Job and sees, above the fold: customer, problem in their words,
  property history, equipment on file, access notes.
  *AC: all visible without scrolling on a standard phone; available offline.*

**Status & travel**
- **R1.3 (Must)** One-tap "On my way" → starts travel time entry, notifies customer with tracking
  link, updates the board.
  *AC: single tap; queues offline and fires on reconnect (A3); board reflects within 1s when online.*
- **R1.4 (Must)** One-tap "Arrived" (geofence-suggested) and "Start/Stop work" timer.
  *AC: timer is durable across app kill/phone death (A2).*

**Capture**
- **R1.5 (Must)** Capture photos, voice-to-text notes, and JobType form fields with minimal taps.
  *AC: start a capture in < 30s ("under-30-second job"); camera/voice are first-class; typing
  optional; all attach to the Property and survive offline (A1, C7).*
- **R1.6 (Should)** Add/confirm equipment on the Property if not on file.
  *AC: persists to Property for future visits (C7).*

**Quote in the room**
- **R1.7 (Must)** Build an estimate from the pricebook with good/better/best options; present and
  capture signature on the phone.
  *AC: line items priced from pricebook; pricing visibility respects role (E2); signature captured
  offline; scope can grow mid-job (C2).*

**Materials & labor**
- **R1.8 (Must)** Add materials used (flow to invoice) and track labor time.
  *AC: works offline; decrements inventory when inventory is enabled.*

**Payment**
- **R1.9 (Must)** Collect payment: card (Tap to Pay), ACH, or record cash/check; instant receipt.
  *AC: charge confirmed server-side before showing "Paid" (A5, D1–D3); decline handled calmly with
  alternates (D2); receipt sent on reconnect if offline.*

**Close & multi-visit**
- **R1.10 (Must)** Review, final signature, mark done; or spawn a return Visit without closing the
  Job.
  *AC: Job stays open across Visits (C1); no-show/declined-work handled as valid outcomes (C3, C4).*

**Offline backbone (cross-cutting Must for all R1)**
- **R1.11 (Must)** Every R1 action works with zero connectivity and syncs cleanly on reconnect with
  honest sync status and **zero data loss**.
  *AC: full Flow 1 completed in airplane mode; conflicts resolve field-wins for captures (A4);
  nothing lost on app kill / dead battery / storage pressure (A2, A8).*

**AI assist — write-it-fills + the gate** ([AI Operating Model](13-ai-operating-model.md))
- **R1.12 (Must)** Tech speaks/types a sentence; AI fills structured fields (problem, diagnosis,
  work, materials, follow-up), each showing **provenance**, before the tech confirms. *(UX: G17, G29)*
  *AC: every AI-filled value shows its source (✓ from your note / ⚠ confirm); low-confidence items
  are flagged, never auto-committed; works toward the "under-30-second job" (R1.5).*
- **R1.13 (Must)** A **human gate** precedes any committed, sent, or charged action; AI never acts
  autonomously on money/customer/irreversible steps. *(UX: G18)*
  *AC: gate states plain-language summary ("this will charge $240, email a receipt"); one-tap
  approve/edit; approval logged with who/when (H4); nothing on the [autonomy ladder](13-ai-operating-model.md)
  above the configured level executes without it.*

**The One-Line Report (status pulse — tech side)** ([Transparency](15-transparency-and-control.md))
- **R1.14 (Must)** Status taps the tech already makes (on-my-way/arrived/paid) **auto-generate** a
  one-line update to the office; the tech can add one spoken/typed sentence. *(UX: G15)*
  *AC: no extra step for the auto lines; optional add ≤ 1 sentence via voice→text; queues offline,
  sends on reconnect (A3).*

**Personal notes & reflection (the private layer)** ([Notes & Reflection](16-notes-and-reflection.md))
- **R1.15 (Should)** Each user has a **private-by-default** personal notes space, plus a clear
  3-level visibility choice (operational / team / private) when writing. *(UX: G16)*
  *AC: private notes are never visible to managers/admins and cannot be exposed by an admin setting;
  the active visibility is always labeled; sharing a note is one deliberate action (NFR12).*

### R2 — The Dispatcher's Board

- **R2.1 (Must)** Live board: techs × time, jobs as cards, unassigned queue.
  *AC: full day for 10+ techs readable on one screen; updates from field < 1s.*
- **R2.2 (Must)** Drag-or-keyboard assign/reassign in < 2s, no dialog.
  *AC: routine assignment requires no modal.*
- **R2.3 (Must)** Prevent double-booking at point of action; warn on skill/cert mismatch and
  impossible drive time (override-with-reason).
  *AC: conflict visible before confirm (B1, B3, B4).*
- **R2.4 (Must)** Emergency re-slot: surface closest qualified available techs; one-gesture reassign;
  auto-notify affected customers of new windows.
  *AC: the 7:45am scenario completes in one flow (B2); sick-day bulk reassign supported (B5).*
- **R2.5 (Must)** Customer notifications: confirmation + on-my-way live tracking link (no download).
  *AC: link works without an account; ETA degrades gracefully (G1, G2).*
- **R2.6 (Should)** Command palette (`⌘K`) to jump to any object/action.
- **R2.7 (Must)** Booking intake: office creates a job in a few fields; customer/property
  auto-complete from history.
  *AC: wide-window and fixed-time appointments both modeled (B8); multi-tech crews supported (B9).*

**Awareness & early warning** ([Transparency §2–3](15-transparency-and-control.md))
- **R2.8 (Must)** Office sees a live **stream of One-Line Reports** and can scan the day at a glance.
  *(UX: G15)*
  *AC: chronological, per-tech; concern-flagged (⚠) lines surface to the top; read/unread states.*
- **R2.9 (Must)** **Raise a concern** in one tap (tech) **and** AI **operational-awareness** alerts
  (running late, blocked/late part, trending out-of-scope) surface to the right person *early*.
  *(UX: G21, G27)*
  *AC: concern goes up immediately with context; out-of-scope is flagged *before* invoice time (links
  to D-series money cases); late-window flagged before the customer calls (B-series).*
- **R2.10 (Should)** AI **receptionist/booking** proposes a booking from an inbound call/text; a
  human approves at the gate (L2). *(UX: G18; [AI model](13-ai-operating-model.md))*
  *AC: proposed booking lands in the same Job object; office confirms before it hits the board.*

### R3 — The Money Path + Owner's Home

- **R3.1 (Must)** Approved estimate **becomes** the invoice — no re-keying.
  *AC: zero manual line-item re-entry; customer can approve from the link (G3).*
- **R3.2 (Must)** Deposits, partial/progress payments, tips, refunds, configurable tax.
  *AC: balance-due tracked; refunds audit-logged and reflected everywhere (D1, D4, D5, D6).*
- **R3.3 (Must)** Owner's Home: today's revenue, jobs done vs. scheduled, team status — same data,
  reconciling to the penny.
  *AC: revenue == sum of confirmed payments, $0.00 variance (D7); works on phone and desktop.*
- **R3.4 (Must)** QuickBooks/Xero sync — one-directional, idempotent.
  *AC: no double-posts; failures visible and retryable (D8).*
- **R3.5 (Should)** Online self-service booking into the same Job object.

**Transparency, contracts & job costing** ([Data Model](14-data-model.md), [Transparency §4](15-transparency-and-control.md))
- **R3.6 (Must)** **Financial transparency:** clear up-front estimate options; open payment choice
  (card/ACH/cash/check/financing); plain-language contracts (what's covered, cadence, renewal); no
  hidden fees — out-of-scope work is re-approved, not slipped in.
  *AC: customer always sees what they owe and how to pay; changes re-approved (links R2.9, D-series).*
- **R3.7 (Should)** **Job costing / profitability** on a Job/Project/Agreement: budget vs actual vs
  variance vs % used, with over-budget flagged; actuals **derived** from real payments/labor/materials.
  *(UX: G22; [data §15](14-data-model.md))*
  *AC: reconciles to the penny with backing data (D7); drill-down to the line items behind a number.*
- **R3.8 (Should)** **Customer self-service portal** (no download): the customer sees their agreement
  status, upcoming/past visits, balance, and can pay. *(UX: G23)*
  *AC: token-link access, no forced account (G1); contract/visit/balance match the office to the penny;
  WCAG 2.2 AA.*

### R4 / R5 — summarized

- **R4 (Configurability & the config layer):** the admin **configuration surface** *(UX: G26)* —
  JobType builder, no-code **Form builder** (trade-specific readings/checklists, incl. compliance
  like EPA logs), composable role/permission matrix (E4), and the **AI guardrail setup + Capability
  Charter** *(UX: G20; [AI model](13-ai-operating-model.md))*. Plus: **Service Agreements / memberships**
  engine that generates recurring visits (B7), **Projects** (multi-visit, phases, progress billing,
  POs) *(UX: G24, G25; [data §7–8](14-data-model.md))*, onboard a 2nd vertical by config (F1–F3),
  multi-location scoping (F4).
- **R5 (Scale & polish):** reporting depth, inventory/truck stock, **audit-log/accountability view**
  *(UX: G28)*, WCAG 2.2 AA audit, performance hardening to the NFR bar, reliability/observability,
  payments security/compliance baseline.

---

## 7. Non-functional requirements

| # | Requirement | Target |
|---|---|---|
| NFR1 | Offline-first technician app | 100% of Flow 1 offline; zero data loss; conflict-aware sync |
| NFR2 | Performance | < 100ms perceived primary actions; < 2s cold launch; optimistic UI |
| NFR3 | Real-time | field action → dispatcher board < 1s |
| NFR4 | Accessibility | WCAG 2.2 AA; full Dynamic Type; VoiceOver/TalkBack; color never sole signal |
| NFR5 | Cross-platform parity | shared tokens; native-right rendering on web & mobile ([DS](design-system/README.md)) |
| NFR6 | Security & tenancy | multi-tenant row-level isolation; permissions enforced server-side; audit log (H4) |
| NFR7 | Financial correctness | payments confirmed server-side; reconciles to the penny |
| NFR8 | Data portability | effortless import **and** export (H1, H2) — a trust + anti-lock-in requirement |
| NFR9 | Android quality parity | match iOS quality/perf (attacks the 3.2★ Android gap from research) |
| NFR10 | AI accountability & control | human gate on money/customer/irreversible; **nothing autonomous** there; every AI action reversible + audit-logged ([AI model](13-ai-operating-model.md)) |
| NFR11 | AI transparency | every AI-filled value shows **provenance + confidence**; no silent AI actions |
| NFR12 | Personal-layer privacy | personal reflection is **private by default**; admins **cannot** override; sharing is user-initiated ([d16](16-notes-and-reflection.md)) |
| NFR13 | AI stability & guardrails | AI acts only inside admin-set guardrails, **never changes its own rules**, makes **no random changes**; behavior predictable |
| NFR14 | Screen-state completeness | every screen defines all 7 states (default/empty/loading/error/offline-syncing/no-permission/success) — see the [State Catalog](17-screen-states.md) |
| NFR15 | Mobile-friendly & responsive | **mobile-first**, fluid across phone → tablet → desktop breakpoints; tech surfaces thumb-reachable, targets ≥ 44pt; customer portal fully responsive; defined breakpoints & grid ([UX G9](ux-ui-review.md)) |

## 8. Dependencies & integrations

Per [Architecture](07-technical-architecture.md): payments (Stripe / Tap to Pay), accounting
(QuickBooks/Xero), SMS/email (notifications + tracking link), maps/routing (tracking + dispatch
proximity). Each sits behind an interface in `packages/core` for swappability.

## 9. Risks & mitigations (from research §7)

| Risk | Mitigation |
|---|---|
| Switching cost / data gravity | Make import effortless (NFR8, H1); same-day onboarding (G5) |
| Simplicity vs. depth tension (what bloated ServiceTitan) | Progressive disclosure; role-composed UI; ruthless non-goals |
| Offline-first is hard | First-class engineering phase, not a late add-on (R1.11, NFR1) |
| Conservative, skeptical buyers | Transparent pricing, easy export, no lock-in; technician-first proof |
| AI wave makes voice table stakes | Ship a credible AI receptionist/booking; differentiate on experience + data spine |
| Payments moat | Embed payments early (R1.9) as revenue + retention |
| Breadth dilutes depth | Anchor depth in HVAC/plumbing/electrical first; expand by config only when core is loved |

## 10. Open questions

- ~~**AI scope for R1–R3**~~ — **Resolved** in the [AI Operating Model](13-ai-operating-model.md):
  write-it-fills (voice/text→structured) ships in R1; AI receptionist/booking in R2; AI invoice
  draft + out-of-scope detection in R3 — all gated by the autonomy ladder (nothing touching money or
  the customer is ever autonomous; a human approves at the last gate).
- **Pricing specifics:** exact per-seat tiers and payment margin — to be set against the
  [strategy's pricing principles](01-product-strategy.md) with live cost data.
- **Inventory depth in R1** vs. deferring full truck-stock to R4.
- **First design partner shop** to run R1 live (the Phase-1 exit gate).
- **Gate density vs. friction:** how many AI confirmation gates before they stop feeling like time
  saved? Tune the [autonomy ladder](13-ai-operating-model.md) with design partners (NFR10 vs speed).
- **Metric baselines:** the §3 targets are starting bars; calibrate against real shop data once a
  design partner is live.

## 11. Out of scope (explicit "Won't-yet")

GL/accounting, marketing-automation suite, telephony/call-center, fleet telematics, franchise
consolidation, native rewrites, a public plugin marketplace. Saying no here *is* the strategy.
