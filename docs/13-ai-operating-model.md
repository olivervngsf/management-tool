# AI Operating Model — the Intelligence Layer

> How AI behaves in Fieldwork. The short version: **AI does the work; a human is accountable at the
> final gate.** AI fills the forms, drafts the estimates, watches for trouble — but nothing becomes
> truth, money, or a customer-facing action until a human confirms it. Built for **trust, full
> transparency, and reliability** — not autonomy for its own sake.

This is the spec for **Layer 5** of the [System Layers](12-system-layers.md) and it resolves the AI
open question in the [PRD](09-prd.md). It deliberately diverges from the "autonomous AI agent" wave
([research §4](research/market-and-competitors.md)): they remove the human; we keep the human in
charge and make the AI *earn trust*.

---

## The core stance

> **AI augments. Humans are accountable.** The AI's job is to remove clicks and surface what
> matters — not to make the final call on anything that carries risk. Every AI action is
> transparent (you can see what it did and why), reversible (you can undo it), and gated (a human
> approves at the last step). Accountability never transfers to the machine.

Why this wins: the field already distrusts software and resents feeling surveilled
([pain points](research/user-pain-points.md)). A system that does the busywork **and** visibly keeps
the human in control builds the one thing this market is starved of — trust.

---

## AI principles

1. **Human at the last gate.** AI can prepare anything; a human confirms before it's committed,
   sent, or charged. The gate is non-negotiable for money, customer-facing, and irreversible actions.
2. **Write, don't click.** The primary input is natural language (typed or spoken). AI turns it into
   structured data. The user reviews and approves — they don't fill forms field-by-field.
3. **Always show your work.** Every AI-filled field shows *what it inferred and from what*
   (provenance). No black boxes. The user can see, trust, and correct.
4. **Honest about confidence.** AI states how sure it is. Low-confidence items are flagged *for* the
   human, never hidden or auto-committed. "I think" looks different from "I know."
5. **Say what's wrong and where you're stuck.** AI surfaces, at a high level, what it couldn't do,
   what's blocked, and where it needs a human — proactively, in plain language.
6. **Reversible by default.** Anything AI does can be undone. Reliability means the user is never
   trapped by an AI mistake.
7. **Disclosure is governed.** Admins control what information AI may share, and with whom
   (internal / customer / partner). AI never over-shares.
8. **Bounded & stable.** AI acts only inside guardrails the company has set, **never changes its own
   rules**, and **never makes a random or unexpected change**. Predictability is part of the product.

---

## The Autonomy Ladder — what AI is allowed to do

Not all actions carry the same risk, so AI gets different leashes. Every AI capability is assigned a
level. **The higher the risk, the closer the human gate.**

| Level | AI is allowed to… | Human gate | Example capabilities |
|---|---|---|---|
| **L0 · Suggest** | Offer a draft/option; do nothing on its own | Human does everything | "Here's a suggested next step" |
| **L1 · Auto-fill** | Turn natural language into structured fields, pre-filled | Human reviews & approves **before commit** | Fill a job from a phone note; draft an estimate from "replaced capacitor, added tune-up" |
| **L2 · Act-with-approval** | Propose a complete action, ready to execute | Human approves with **one tap** | "Book Thu 1–3pm?" · "Send this quote?" · "Reschedule these 3 and notify?" |
| **L3 · Act-and-notify** | Do a **low-risk, reversible, internal** thing, then report it | Human can review/undo after | Tag a job, file a photo to the right equipment, draft an internal summary |
| **🚫 Never autonomous** | — | Human **must** act | Take payment · send anything to a customer · close/finalize a job · change a price · anything irreversible |

**Rule:** money, customer-facing, and irreversible actions are *always* at the human gate (L1/L2),
**never** L3. AI can prepare them perfectly; a person presses the button.

---

## Pattern 1 — "Write, it fills" (the input you asked for)

The everyday magic: the user writes or speaks freely; AI does the data entry.

```
  Tech speaks/types:  "AC not cooling, found a bad run capacitor, swapped it,
                       also recommend a full tune-up next visit"
                          │
                          ▼  AI extracts (L1)
  ┌─────────────────────────────────────────────────────────────┐
  │  Problem:    AC not cooling                    ✓ from your note │
  │  Diagnosis:  failed run capacitor              ✓ from your note │
  │  Work done:  replaced run capacitor            ✓ from your note │
  │  Materials:  Run capacitor 45/5 µF   $24   ⚠ price — confirm?   │
  │  Follow-up:  recommend tune-up (next visit)    ✓ from your note │
  └─────────────────────────────────────────────────────────────┘
                          │
              Human reviews — edits the one ⚠, taps Confirm  ← the gate
                          │
                          ▼
              Now it's truth. Estimate/notes/follow-up created. No form filled.
```

- **Few clicks:** the user produced a structured job from one sentence.
- **Transparent:** every field shows where it came from (`✓ from your note`); inferences needing a
  decision are flagged (`⚠`).
- **Gated:** nothing is saved until the human confirms. Accountability stays with the tech.

Same pattern everywhere: office books a job from a caller's words; owner asks "how did we do today?"
and gets an answer drawn from real data (read-only, so no gate needed).

---

## Pattern 2 — The human gate (where it lives)

The gate is a **deliberate, low-friction confirmation step** placed at the moment of commitment:

- It shows **what will happen** in plain language ("This will charge $240 and email a receipt").
- It shows **what AI is unsure about**, highlighted for attention.
- It's **one tap to approve**, one tap to edit — never a wall of fields.
- After approval, it's **logged with who approved it** (the audit trail = accountability).

The gate is the product's spine of trust. It's why a tech, owner, or customer can rely on the output
even though AI produced it: a human they trust said yes.

---

## Pattern 3 — AI tells you what's wrong and where it needs help

AI is **honest about its own limits**, at a high level, so the human always knows the real state:

- **Confidence, surfaced:** "I filled 5 fields confidently; 1 needs your call." Never a false sense
  of certainty.
- **Blockers, raised early:** "I couldn't price this part — it's not in your pricebook. Add it?"
- **What it couldn't do:** "I drafted the estimate but can't send it — that needs your approval."
- **Plain language, high level:** the tech sees "needs your input on the part price," not a stack
  trace. Detail is available on tap for those who want it.

This turns AI from an opaque oracle into a **reliable junior teammate** who flags problems instead of
hiding them — which is exactly how it earns trust.

---

## Pattern 4 — Operational awareness: nothing slips, even when a partner is slow

You asked that everything stay **on-plan and in-scope**, and that the team gain awareness when
something slips — *even external delays like a slow partner/supplier.* AI watches the whole operation
and raises exceptions early:

- **Off-plan detection:** a job running long, a window about to be missed, a tech stuck — surfaced
  to dispatch *before* the customer calls angry.
- **Out-of-scope detection:** work growing beyond the approved estimate — flagged so it's re-quoted,
  not eaten.
- **External dependencies tracked:** a **part on order from a supplier that's late** is a first-class
  status, not a sticky note. AI flags "Job #1432 is waiting on a part due yesterday — follow up?" so
  the team knows and the customer can be told proactively.
- **Shared awareness:** what happened is visible to the people who need it (per the disclosure rules
  below) — the office, the owner, the next tech — so nothing lives only in one person's head.

AI's role here is **vigilance, not action**: it notices and tells the right human early. The human
decides what to do. (Acting on it — reschedule, reorder, notify — runs back through the gate.)

---

## Governance — admins control what AI shares

Per your requirement: **the admin/manager decides which information AI may share, and with whom.**
Disclosure is a configured policy, not an AI judgment call.

| Audience | Default sharing | Admin can adjust |
|---|---|---|
| **Internal (office/owner)** | Full operational status, confidence, blockers | Restrict sensitive financials to Owner/Admin roles |
| **Technician (field)** | What they need for their jobs; their own status | Toggle cost/margin visibility per role |
| **Customer** | Only what's approved: ETA, quote, receipt — **never** internal status/notes | Choose which updates auto-send vs. require approval |
| **Partner/supplier** | Nothing unless explicitly enabled | Opt-in per integration; scope what's shared |

- AI **never discloses across a boundary the admin hasn't opened.** Internal "what went wrong" stays
  internal unless a human chooses to share it.
- Disclosure rules compose with the [role/permission model](02-personas-and-roles.md) — same engine.
- Every share is **logged**: who/what/when, for accountability.

---

## Guardrails — configured per company (because every shop runs differently)

AI never has a fixed, universal set of powers. It operates inside a **guardrail configuration that
each company owns** — part of the [Configuration layer](12-system-layers.md) (Layer 3), the same
place JobTypes, Forms, and Roles live. Two shops with the same software can give AI very different
leashes, and both are correct for them.

A company's AI guardrails define:

- **Which capabilities are on at all** (write-it-fills? receptionist? supplier tracking?).
- **What autonomy level each capability gets** — pinned to the [ladder](#the-autonomy-ladder--what-ai-is-allowed-to-do).
  A cautious shop can force *everything* to L1 (review-before-commit). A confident one can let L3
  routine filing run with undo. Money/customer actions stay gated no matter what — that floor is not
  configurable.
- **What AI may touch** — which objects and fields are in or out of bounds.
- **Who can approve at the gate** (which roles).
- **Disclosure rules** (the matrix above).

> The guardrails are themselves **just configuration** — they live in the flexible layer, not in the
> AI. The AI reads them; it cannot rewrite them. This is what makes "every company runs differently"
> and "the system stays stable" true at the same time.

## AI helps the admin set the rules (confirm & clarify — never assume)

Defining guardrails shouldn't be a wall of switches the admin faces alone. **AI helps set its own
boundaries — by asking, not assuming:**

- On setup, AI proposes a **conservative default** (everything low-autonomy, money/customer gated)
  and walks the admin through it in plain language: *"I can draft estimates from your techs' notes,
  but I'll always show them to the tech before saving. Want that on?"*
- Where a company's way of working is unclear, **AI asks the admin to clarify** rather than guessing:
  *"Should new bookings I take from calls go straight to the board, or wait for dispatch to confirm?"*
- The admin's answers become the configured guardrails. AI **confirms back** what it will and won't
  do, in writing, so there's no ambiguity.
- Changing the rules later is always a **deliberate admin action** — AI can *suggest* a change ("you
  approve every estimate unchanged; want me to lower the gate?") but **never applies it itself.**

This makes the guardrails fit *this* team, while keeping a human firmly in control of where the
lines are drawn.

## The AI Capability Charter — everyone knows what AI can and can't do

Out of the setup above, the system generates a plain-language **Capability Charter** for the
company: a single, visible page that states *exactly* what AI is allowed to do here, what it will
always ask before doing, and what it will never do.

- **Visible to everyone** (per their role) — the tech, dispatcher, and owner can all see the rules
  the AI plays by. No surprises, no hidden powers.
- **Written in plain language**, not settings jargon: *"AI drafts your job notes — you always
  confirm. AI never takes payment or messages a customer without you."*
- **Always current** — it's generated from the live guardrail config, so it can't drift from reality.

The Charter is how you deliver on "**they know clearly about what AI can and cannot do**." Clarity
about the boundary is itself a trust feature.

## Stability — no random changes, ever

The hard guarantee behind "we want the system stable":

- **Bounded action space.** AI can only ever do what the guardrails permit — there is no path for it
  to act outside them. Out-of-bounds is impossible, not just discouraged.
- **No self-modification.** AI never changes its own rules, permissions, or another company's data.
  Rules change only by deliberate human admin action, which is logged.
- **No random changes.** AI does not quietly alter records, settings, prices, or schedules on its
  own. Every change is either gated (a human approved) or a logged, reversible L3 action the human
  can see and undo. If AI is uncertain, it **asks — it does not act.**
- **Predictable behavior.** The same input and config produce the same kind of result; the human
  always knows what to expect. Updates to AI behavior ship through the same change control as any
  other release — never as a silent surprise to a running shop.
- **Stable when AI is absent.** Because AI only augments, the system behaves identically with AI
  quiet — so it can never *destabilize* the daily loop ([Layer 5 rule](12-system-layers.md)).

> The mental model: **AI is a capable assistant working inside a fenced yard the company built. It
> can do a lot inside the fence, it asks before stepping near the gate, and it can never move the
> fence.** That is how you get help *and* stability at once.

---

## Trust mechanisms (the things that make it reliable, not just clever)

| Mechanism | What it guarantees |
|---|---|
| **Provenance** | Every AI-filled value shows its source — you can always see *why* |
| **Confidence display** | Sureness is visible; low-confidence is flagged, never hidden |
| **Human gate + audit log** | A person approved it; the record shows who and when |
| **Undo everywhere** | No AI action is a trap; reliability means reversibility |
| **Graceful degradation** | If AI is unavailable, the app works fully without it (it augments, never blocks — [Layer 5 rule](12-system-layers.md)) |
| **No silent actions** | AI never does anything the human can't see in the timeline |

---

## Where it ships (resolving the PRD open question)

AI is layered in *after* the experience is solid, so it augments a product that already works:

| Release | AI capability | Level | Gate |
|---|---|---|---|
| **R1** (tech job) | **Write-it-fills** — voice/text → structured job, notes, draft estimate | L1 | review-before-commit |
| **R1** | AI files photos to the right equipment; drafts internal summary | L3 | review/undo after |
| **R2** (dispatch) | AI **receptionist/booking** (proposes a booking from a call) | L2 | one-tap approve |
| **R2** | Off-plan / late-window detection on the board | L0/L3 | surfaced to dispatch |
| **R3** (money) | AI drafts invoice from approved work; flags out-of-scope | L1 | human sends/charges |
| **R3+** | Partner/supplier delay tracking & proactive customer updates | L0/L2 | human approves outbound |
| **R4+** | Owner Q&A over real data ("how did we do?"), recommendations | L0 (read-only) | — |

Every level above respects the ladder: **nothing that touches money or the customer is ever
autonomous.** The AI gets more helpful over time (the [flywheel](12-system-layers.md)); the human
gate never moves.

---

## The one-line summary

**AI removes the clicks and watches your back; the human keeps the keys.** That combination — fast
*and* trustworthy — is something the autonomous-AI competitors structurally can't claim, and it's
exactly what a skeptical field audience will choose.
