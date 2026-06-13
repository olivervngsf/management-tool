# Build Backlog — Flows to Prioritize

The menu of buildable flows across the whole product, so you can rank them. Grounded in the
[core workflows](04-core-workflows.md), [PRD](09-prd.md), [data model](14-data-model.md), and the
[pain points](research/user-pain-points.md).

**Legend** — Status: ✅ in the [prototype](prototype/fieldwork-prototype.html) · 🔲 not yet ·
🧱 platform (engineering, not a screen). Value: ⭐⭐⭐ high → ⭐ lower. Effort: **S** small ·
**M** medium · **L** large. "Kills" = the pain it removes ([registry](research/user-pain-points.md)).

---

## A · Technician loop — the wedge (win here first)
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| A1 Today / my day | chronological visits, current job pinned | — | ✅ | ⭐⭐⭐ | S |
| A2 Job heads-up + status | who/what/history/equipment/access; on-my-way → arrived → start | — | ✅ | ⭐⭐⭐ | M |
| A3 Capture (AI write-it-fills) | speak → AI fills fields w/ provenance; photo/voice | PP-T2 | ✅ | ⭐⭐⭐ | M |
| A4 Proposal / estimate | good/better/best, photos, Sign & Accept | — | ✅ | ⭐⭐⭐ | M |
| A5 Payment / collect | tap-to-pay/ACH/cash/check; confirm-then-Paid | PP-T1 | ✅ | ⭐⭐⭐ | M |
| A6 Close-out + multi-visit | review, sign, mark done, spawn return visit | — | 🔲 | ⭐⭐ | S |
| A7 One-Line Report | status pulse to office (auto + 1 line) | — | ✅ | ⭐⭐⭐ | S |
| A8 Me — private notes/reflection | private-by-default journal + growth | PP-T5 | ✅ | ⭐⭐ | S |
| A9 Customer/property search & history | look up any property + its past jobs | — | 🔲 | ⭐⭐ | M |
| A10 Equipment & inspection forms | per-unit readings/checklists (EPA, etc.) | — | 🔲 | ⭐⭐ | M |

## B · Office / dispatch
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| B1 Dispatch board | techs × time, drag-assign, live status | PP-D2 | ✅ | ⭐⭐⭐ | L |
| B2 Conflict prevention | block double-book / skill / drive-time | PP-D1 | 🔲(shown) | ⭐⭐⭐ | M |
| B3 Emergency re-slot | closest qualified tech, one-gesture, auto-notify | PP-D3 | 🔲 | ⭐⭐⭐ | M |
| B4 Booking intake | create a job from a call in a few fields | — | 🔲 | ⭐⭐ | M |
| B5 Live report stream + concern alerts | scan the day; ⚠ surfaced early | — | ✅(feed) | ⭐⭐ | M |
| B6 Schedule / calendar views | week/day calendar | — | 🔲 | ⭐ | M |
| B7 Command palette (⌘K) | jump to anything | — | 🔲 | ⭐ | S |

## C · Owner
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| C1 Owner home | glanceable revenue/jobs/team/needs-you | PP-O2 | ✅ | ⭐⭐⭐ | M |
| C2 Job costing / profitability | budget vs actual, over-budget flagged | PP-O2 | ✅ | ⭐⭐ | M |
| C3 Reports (depth) | configurable reporting | PP-B7 | 🔲 | ⭐ | L |

## D · Customer-facing
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| D1 On-my-way tracking link | rideshare-grade ETA, no download | PP-C2 | ✅ | ⭐⭐⭐ | M |
| D2 Customer portal | agreement, visits, balance, pay | PP-C1 | ✅ | ⭐⭐ | M |
| D3 Online self-booking | customer books from live availability | — | 🔲 | ⭐⭐ | M |
| D4 Approve proposal & pay from link | sign + pay remotely | — | 🔲 | ⭐⭐ | M |

## E · Money path
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| E1 Estimate → Invoice → Payment | no re-keying; approved work becomes invoice | — | 🔲 | ⭐⭐⭐ | M |
| E2 Deposits / progress / tips / refunds | first-class money cases | — | 🔲 | ⭐⭐ | M |
| E3 QuickBooks / Xero sync | one-way, idempotent | PP-O3 | 🔲(shown) | ⭐⭐ | L |
| E4 Financing | offer financing on the total | — | 🔲 | ⭐ | M |

## F · Contracts & projects
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| F1 Service agreements / memberships | recurring plan that auto-generates visits | — | 🔲 | ⭐⭐⭐ | L |
| F2 Recurring/maintenance engine | seasonal tune-ups on schedule | — | 🔲 | ⭐⭐ | L |
| F3 Projects (multi-visit) | phases, change orders, progress billing, POs | — | 🔲 | ⭐⭐ | L |

## G · Admin / configuration (makes flexibility real)
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| G1 Onboarding / first-run | live same day, empty states | PP-B1 | 🔲 | ⭐⭐⭐ | M |
| G2 Data import / migration | bring history/pricebook in painlessly | PP-B5 | 🔲 | ⭐⭐⭐ | L |
| G3 JobType builder | configure job types per trade | — | 🔲 | ⭐⭐ | M |
| G4 Form builder (no-code) | trade-specific readings/checklists | — | 🔲 | ⭐⭐ | L |
| G5 Price book management | services/materials, cost/markup | — | 🔲 | ⭐⭐ | M |
| G6 Roles & permissions builder | composable roles | — | 🔲 | ⭐ | M |
| G7 AI guardrails + Capability Charter | set/show what AI may do | — | 🔲 | ⭐⭐ | M |

## H · AI
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| H1 Write-it-fills | (in A3) NL → structured | PP-T2 | ✅ | ⭐⭐⭐ | M |
| H2 AI receptionist / booking | answers calls/texts, proposes booking | — | 🔲 | ⭐⭐ | L |
| H3 Operational awareness | off-plan/late/out-of-scope early warning | — | 🔲(feed) | ⭐⭐ | M |
| H4 AI invoice draft | draft invoice from approved work | — | 🔲 | ⭐⭐ | M |
| H5 Owner Q&A over data | "how did we do today?" | — | 🔲 | ⭐ | M |

## I · Platform (cross-cutting — under everything)
| Flow | What it delivers | Kills | Status | Value | Effort |
|---|---|---|---|---|---|
| I1 Offline-first sync engine | zero-data-loss local-first | PP-T1, PP-T3 | 🧱 | ⭐⭐⭐ | L |
| I2 Auth + multi-tenancy | accounts, orgs, isolation | — | 🧱 | ⭐⭐⭐ | M |
| I3 Design-token pipeline | tokens → web + mobile | — | 🧱 | ⭐⭐ | S |
| I4 Notifications | push/SMS/email | PP-C3 | 🧱 | ⭐⭐ | M |
| I5 Audit log | who/what/when/why | — | 🧱 | ⭐⭐ | M |

---

## Recommended order (you can override)

**Wave 1 — the wedge, made real (build to ship to one shop):**
A1–A8 as *working code* on **I1 (offline) + I2 (auth) + I3 (tokens)**. This is the technician's
whole day, offline, and it's the thing that wins the first user. ([Phase 1](08-roadmap.md))

**Wave 2 — run the office:** B1 board, B2 conflict, B3 re-slot, B4 booking, D1 tracking, B5 alerts.

**Wave 3 — the money & the owner:** E1 estimate→invoice→payment, E2 money cases, C1 owner home,
C2 job costing, E3 QuickBooks.

**Wave 4 — flexibility & growth:** G1 onboarding, G2 import, G3–G7 config, F1 agreements, D2 portal,
D3 booking, F3 projects.

**Wave 5 — depth & scale:** C3 reports, H2 receptionist, F2 recurring engine, the rest of AI, I5 audit.

> **The rule:** Wave 1 before anything else — the technician loop is the wedge; everything else
> assumes a shop already loves the field app.

---

## How to prioritize (pick your way)

- **Fastest to a demo a shop reacts to →** deepen A-flows + add D1 (tracking) and G1 (onboarding).
- **Fastest to real revenue/stickiness →** E-flows (money) + E3 (QuickBooks).
- **Biggest differentiator →** I1 (true offline) + A3/H1 (AI write-it-fills) + A8 (trust/privacy).
- **Broadest market reach →** G-flows (configuration = more trades).

**Tell me your top 3 flows** and I'll build/deepen them next (as prototype screens now, or as the
first real code when you're ready).
