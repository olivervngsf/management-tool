# 09 · Product Requirements Document (PRD)

**Product:** Fieldwork — field service management for the trades
**Status:** Foundation / pre-build · **Last updated:** 2026-06-12
**Owner:** Product · **Source of truth for:** scope, requirements, acceptance criteria, metrics

> This PRD operationalizes the [Strategy](01-product-strategy.md), grounded in
> [Research](research/market-and-competitors.md), and built on the [IA](03-information-architecture.md),
> [Flows](04-core-workflows.md), [Edge Cases](10-edge-cases.md), and [Design Principles](05-design-principles.md).
> It scopes **Phase 1–3** (the wedge through the money path) in requirement-level detail; later
> phases are summarized. Requirements use **MoSCoW** (Must / Should / Could / Won't-yet) and each
> Must has acceptance criteria.

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
- Full marketing-automation suite, call-center telephony, fleet telematics (partner, don't build).
- Enterprise multi-franchise consolidation.
- Native Swift/Kotlin rewrites (Expo carries us past PMF).

## 3. Success metrics

| Metric | Target | Tied to |
|---|---|---|
| Technician daily active use (of assigned techs) | > 90% | Wedge / G1–G2 |
| Offline job completion (no signal) | 100% of [Flow 1](04-core-workflows.md) | G1 |
| Perceived primary-action latency | < 100 ms | Speed principle |
| Cold launch → usable | < 2 s | Speed |
| New-tech first job without training | ≥ 95% succeed | G2 |
| Time-to-first-dispatch for a new shop | < 1 day | G5 |
| Today's-revenue reconciliation error | $0.00 | G4 |
| Board update propagation (field → dispatcher) | < 1 s | G3 |
| Second-vertical onboarding without code | achievable | G6 |

The **north-star is technician adoption** — if the field user won't use it, nothing downstream
matters ([strategy](01-product-strategy.md)).

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

### R4 / R5 — summarized

- **R4 (Configurability):** admin-configurable JobTypes, Forms, Pricebook; composable role builder
  (E4); recurring/maintenance-plan engine (B7); onboard a 2nd vertical by config (F1–F3); multi-
  location scoping (F4).
- **R5 (Scale & polish):** reporting depth, inventory/truck stock, WCAG 2.2 AA audit, performance
  hardening to the NFR bar, reliability/observability, payments security/compliance baseline.

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

## 11. Out of scope (explicit "Won't-yet")

GL/accounting, marketing-automation suite, telephony/call-center, fleet telematics, franchise
consolidation, native rewrites, a public plugin marketplace. Saying no here *is* the strategy.
