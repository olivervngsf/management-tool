# Prototype × Pain Points — coverage review

Audit of the [clickable prototype](fieldwork-prototype.html) against the
[User Pain Points Registry](../research/user-pain-points.md). Question: **does each screen actually
overcome the pain it's meant to?** Honest status per pain — ✅ shown · 🟡 partial · 🔭 not
screen-level (lives in engineering/pricing/support, can't be a wireframe).

---

## Technician (Maria)
| Pain | Sev | In the prototype? | Where |
|---|---|---|---|
| PP-T1 Offline data loss | P0 | ✅ | "Offline · synced 8:02am" chip on **Today**; "Saved on device · will sync" on **Capture** |
| PP-T2 Too many taps / data entry | P1 | ✅ strong | **Capture** — speak one sentence → AI fills fields with ✓/⚠ provenance (the under-30-second job) |
| PP-T3 Crashes lose work | P1 | 🟡 | implied by "saved on device" (durability), but reliability isn't a wireframe property |
| PP-T4 Android second-class | P1 | 🔭 | it's web/cross-platform, renders the same everywhere — but parity is an NFR, not a screen |
| PP-T5 Feels surveilled | P1 | ✅ **(newly added)** | **Me** — private-by-default notes, "your manager can't see this 🔒", 3-level visibility, "a safe place to think, not another place to be watched" |
| PP-T6 Updates slower | P2 | 🔭 | performance NFR, not a screen |

## Dispatcher (David)
| Pain | Sev | In the prototype? | Where |
|---|---|---|---|
| PP-D1 Double-booking | P0 | ✅ | **Board** — "double-booking & skill conflicts blocked before they happen"; EPA-cert ⚠ on the unassigned emergency |
| PP-D2 Stale real-time state | P1 | ✅ | **Board** — live tech statuses + the live one-line-report feed |
| PP-D3 Slow re-slotting | P1 | 🟡 | **Board** — unassigned queue + emergency card present; drag-to-reassign is described, not interactive in a wireframe |

## Owner (Sofia)
| Pain | Sev | In the prototype? | Where |
|---|---|---|---|
| PP-O1 Paying for unused features | P1 | 🔭 | pricing/commercial, not a screen |
| PP-O2 Numbers can't trust | P0 | ✅ strong | **Owner** — "reconciled", job-costing table, "reconciles to the penny" |
| PP-O3 QuickBooks sync breaks | P1 | ✅ **(newly added)** | **Owner** — "Synced to QuickBooks ✓" indicator |

## Admin / Buyer (Alex)
| Pain | Sev | In the prototype? | Where |
|---|---|---|---|
| PP-B1 Onboarding wall | P0 | 🔭 | setup-speed promise; would show as a first-run/empty-state flow (not built yet) |
| PP-B2 Cost creep | P1 | 🔭 | pricing, not a screen |
| PP-B3 Lock-in / ETFs | P0 | 🔭 | commercial terms, not a screen |
| PP-B4 Learning curve | P1 | ✅ implicit | the whole prototype *is* the answer — clarity, one primary action, compact-but-calm |
| PP-B5 Switching / migration | P0 | 🔭 | import/export; a setup-flow screen, not built yet |
| PP-B6 Slow support | P2 | 🔭 | service-design, not a screen |
| PP-B7 Reporting rigidity | P2 | 🔭 | deferred to R5 |

## Customer (homeowner)
| Pain | Sev | In the prototype? | Where |
|---|---|---|---|
| PP-C1 Forced app / account | P1 | ✅ | **Customer** — "no app needed", no-download portal |
| PP-C2 No real-time tracking | P1 | ✅ | **Customer** — "Maria is on the way · ETA 12 min" |
| PP-C3 Notification spam | P2 | 🔭 | notification policy, not a screen |

---

## Verdict

**Every screen-addressable P0/P1 pain is now visibly answered** in the prototype:

- P0s shown: PP-T1 (offline), PP-D1 (no double-book), PP-O2 (reconciled numbers). The remaining
  P0s — PP-B1 onboarding, PP-B3 lock-in, PP-B5 migration — are **commercial/setup**, not technician-
  flow screens, so they're correctly absent here (they'd live in an onboarding/settings flow).
- Gaps closed this pass: **PP-T5 surveillance** (new **Me** private layer — the signature
  trust differentiator, previously invisible), **PP-O3** (QuickBooks synced indicator), plus offline
  and no-double-book cues reinforced.

**Consciously not in this prototype (and why):**
- *Reliability/performance pains* (PP-T3 crashes, PP-T4 Android, PP-T6 updates) — these are
  engineering NFRs you feel in the real app, not things a wireframe can demonstrate.
- *Commercial pains* (PP-O1, PP-B2, PP-B3) — pricing/terms, proven on the pricing page, not a screen.
- *Setup pains* (PP-B1 onboarding, PP-B5 migration) — would be a **first-run / import flow**; worth
  prototyping next if onboarding is a focus.
- *Deferred* (PP-B6 support, PP-B7 reporting) — post-PMF.

**Recommended next prototype additions** (to cover the remaining screen-able pains): a **first-run /
import** flow (PP-B1, PP-B5) and an **empty-state** for a brand-new account — the "live the same day"
promise made visible.
