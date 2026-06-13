# 17 · Screen-State Catalog

> Closes UX gap **G3**. For every critical screen, this defines the **seven states** it must handle —
> so no screen ever shows a blank void, a dead spinner, or a lie. States are where field apps win or
> fail ([the incumbents lose data and stall here](research/user-pain-points.md)).

This is the bridge between the [edge cases](10-edge-cases.md) (what *situations* happen) and the
[design principles](05-design-principles.md) (how each should *feel*). It also satisfies PRD
**NFR14** (screen-state completeness) and feeds the [design-review checklist](ux-ui-review.md).

---

## The seven canonical states (and how each should feel)

Every screen must answer all seven. The global treatment (apply unless a screen overrides):

| State | When | Treatment (the rule) | Principle |
|---|---|---|---|
| **1. Default** | loaded, has data | the normal, content-first view; one clear primary action | Clarity, One primary action |
| **2. Empty** ("ghosted") | no data yet (no jobs, no notes) | **encourage, don't apologize** — show what *will* appear + the action to create it; never a blank screen | Humane tone |
| **3. Loading** | fetching | **skeleton of the real layout**, never a bare spinner; optimistic UI where possible | Speed |
| **4. Error** | something failed | **plain language: what happened + a way forward**; never a dead end or a code | Forgiving, Humane |
| **5. Offline / syncing** | no/spotty signal | **honest status** ("saved on device · will sync"); never block, never falsely show "done" | Trust |
| **6. No-permission** | role-restricted | **compose to capability** — the feature simply isn't there; **no greyed-out teasing** | Humane (E2) |
| **7. Success** | action completed | confident, brief confirmation; optimistic UI already reflected it | Speed, Trust |

**Three rules that override everything:**
- **Offline is never an error.** A dead zone is a *normal* state (#5), styled calmly — not a red #4.
- **Money/customer never shows success until confirmed.** #7 for payment waits on server confirm (A5).
- **No-permission composes, never greys.** #6 removes, it doesn't tease (Personas E2).

---

## Per-screen states

Compact tables — each lists what the user sees per state and the linked [edge case](10-edge-cases.md).

### Mobile · Today list (technician)
| State | What the tech sees | Case |
|---|---|---|
| Default | chronological visits, current job pinned | — |
| Empty | "No visits scheduled. Enjoy the quiet — or pull to refresh." | — |
| Loading | skeleton rows (last-synced shown instantly if cached) | A1 |
| Error | "Couldn't refresh. Showing your last-synced day." + retry | A8 |
| Offline | subtle "Offline · last synced 8:02am" chip; list fully usable | A1 |
| No-permission | n/a (every tech has their own day) | — |
| Success | new assignment animates in when sync lands | — |

### Mobile · Job screen (technician)
| State | What the tech sees | Case |
|---|---|---|
| Default | heads-up: customer, problem, history, equipment, access notes; action bar | — |
| Empty | a brand-new job: prompts to start ("On my way") | — |
| Loading | skeleton of the job card; cached job opens instantly | A1 |
| Error | "Couldn't load latest. Showing saved version." | A8 |
| Offline | full job works; "changes saved on device" footer | A1, A2 |
| No-permission | pricing/cost hidden if role lacks it — fields simply absent | E2 |
| Success | "Job closed" confirmation; or "Return visit added" (C1) | C1 |

### Mobile · Capture (photo / voice / form)
| State | What the tech sees | Case |
|---|---|---|
| Default | camera/voice first; form fields below | — |
| Empty | "Add the first photo or note" prompt | — |
| Loading | thumbnail placeholder while media processes; never blocks | A7 |
| Error | "Upload paused — will retry when you're back online" (not alarming) | A7 |
| Offline | captures save locally; upload queued, visible | A1, A7 |
| No-permission | n/a | — |
| Success | photo/note appears attached to the equipment/property | C7 |

### Mobile · Estimate builder
| State | What the tech sees | Case |
|---|---|---|
| Default | good/better/best options; line items from pricebook | — |
| Empty | "Start an estimate" + add-from-pricebook | — |
| Loading | skeleton line rows; cached pricebook offline | A1 |
| Error | "Couldn't reach pricebook — using your offline copy" | A1 |
| Offline | builds fully offline; signature captured locally | A1 |
| No-permission | cost/margin hidden per role; price still shown to sell | E2 |
| Success | "Approved — Gold option signed" → flows to invoice | — |

### Mobile · Payment
| State | What the tech sees | Case |
|---|---|---|
| Default | amount, methods (tap-to-pay/ACH/cash/check) | — |
| Empty | "Nothing to collect yet" (balance $0) | — |
| Loading | "Processing…" (server confirm in flight — does **not** show Paid yet) | A5 |
| Error | **declined → calm retry + alternates** (ACH/cash/pay-by-link) | D2 |
| Offline | "Record cash/check now; card capture queues for confirm" | A5 |
| No-permission | n/a (all techs can collect) | — |
| Success | **"Paid" only after server confirm**; receipt sent | A5, D1 |

### Mobile · One-Line Report (tech compose) & office stream
| State | Tech compose | Office stream | Case |
|---|---|---|---|
| Default | auto-line from status tap + optional add | live per-tech feed, newest first | — |
| Empty | (auto, so rarely empty) | "Quiet so far today" | — |
| Loading | — | skeleton feed | — |
| Error | "Couldn't send — will retry" | "Reconnecting to live feed…" | A3 |
| Offline | line queues, "will send" | shows last-synced; "live in a moment" | A3 |
| No-permission | n/a | office-only view | E |
| Success | "Sent" tick | ⚠ concern lines surface to top; read/unread | — |

### Mobile · Personal notes & reflection (private layer)
| State | What the user sees | Case |
|---|---|---|
| Default | their private journal; **"Private to you" label always visible** | — |
| Empty | "Your private space. Jot a thought — only you see this." | — |
| Loading | skeleton list | — |
| Error | "Saved on device; couldn't sync your private notes yet" | A1 |
| Offline | fully writable offline | A1 |
| No-permission | **the inverse** — no one else can ever reach it; not even admin (NFR12) | — |
| Success | note saved; "shared to team" only on deliberate promote action | — |

### Mobile · AI write-it-fills review + gate
| State | What the tech sees | Case |
|---|---|---|
| Default | AI-filled fields with **provenance** (✓ from your note / ⚠ confirm) | — |
| Empty | "Speak or type — I'll fill the details" | — |
| Loading | "Reading your note…" skeleton fields | — |
| Error | "Couldn't parse that — here's a blank form to fill yourself" (graceful fallback) | — |
| Offline | AI assist may pause; **manual entry always works** (AI never blocks) | NFR10 |
| No-permission | AI features off if disabled in [guardrails](13-ai-operating-model.md) — manual flow remains | NFR13 |
| Success | **gate:** "This will charge $240 + email receipt" → one-tap approve; logged | A5, H4 |

### Desktop · Dispatch board
| State | What the dispatcher sees | Case |
|---|---|---|
| Default | techs × time, cards, unassigned queue; live status | — |
| Empty | "No jobs scheduled — drag from the queue or create one" | — |
| Loading | skeleton lanes; board frame renders instantly | — |
| Error | "Live updates paused — reconnecting" banner; board still usable | — |
| Offline | (desktop usually online) "reconnecting"; last state held, edits queue | — |
| No-permission | non-dispatch roles don't see the board at all | E |
| Success | assignment snaps in < 2s; conflict **prevented before** confirm | B1 |

### Cross-device · Owner home & job costing
| State | What the owner sees | Case |
|---|---|---|
| Default | today's revenue, jobs done/scheduled, team status; costing tables | — |
| Empty | new shop: "Your numbers will appear as jobs complete" | — |
| Loading | skeleton tiles | — |
| Error | "Couldn't refresh totals — showing last good figures (8:02am)" | — |
| Offline | cached summary + timestamp; never a wrong number | D7 |
| No-permission | financials hidden for non-owner roles | E |
| Success | numbers **reconcile to the penny**; over-budget flagged (G22) | D7 |

### Customer · Self-service portal / tracking link
| State | What the customer sees | Case |
|---|---|---|
| Default | their agreement, upcoming/past visits, balance, pay button | — |
| Empty | "No upcoming visits — you're all set" | — |
| Loading | skeleton; link resolves fast | — |
| Error | "Link trouble — tap to reload, or call us" (+ phone) | G2 |
| Offline | (customer's own connectivity) graceful "couldn't load — retry" | G2 |
| No-permission | token-scoped: customer sees only their own data; no login wall | G1 |
| Success | on-my-way ETA live; payment confirmed + receipt | G2 |

---

## How to use this catalog

- **Designers:** every screen spec ships with all seven states drawn — this table is the checklist.
- **Engineers:** these are real UI states to build, not edge-case afterthoughts; each maps to a
  [doc 10](10-edge-cases.md) case for behavior.
- **QA:** test the seven states × the field conditions in [doc 10](10-edge-cases.md). The
  **offline (#5)** and **payment success (#7)** states are highest-severity — that's where trust is
  won or permanently lost.

> The pattern to internalize: **offline is normal, not an error; success waits for truth; and
> "you can't do this" is shown by absence, never by a teasing grey button.** Get those three right
> and the product feels trustworthy in exactly the moments incumbents feel broken.
