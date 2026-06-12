# System Layers & the Improvement Flywheel

> The operating philosophy. *Why* the product is built in flexible layers like LEGO, how those
> layers work together, how the product **improves itself** over time, and how a happy field user
> turns into a community. This is the doc that explains how to build **clear and flexible so it
> scales easily** — and where to start small.

---

## The philosophy in five sentences

1. **It just works.** The everyday user never wonders "is it working?" — they trust it and focus on
   the job. Reliability is the feature.
2. **It improves itself.** The product gets better from being used — usage and feedback flow back
   in, and the system learns. ([The flywheel](#the-improvement-flywheel))
3. **It's built like LEGO.** A stable foundation, snap-on capability bricks, and a configuration
   layer that lets each business assemble its own fit — without rebuilding anything.
4. **Layers have clean edges.** Each layer does one job and talks to its neighbors through clear
   contracts, so one can change without breaking the others. ([The layers](#the-five-layers))
5. **That's why it scales.** New features = new bricks. New industries = new configuration. New
   scale = more of the same spine. Almost never a rewrite.

---

## The five layers

Picture it as a stack. Lower layers are **stable and rarely change**; higher layers are **flexible
and change often**. This is the whole trick: put the things that must be reliable at the bottom, and
the things that must flex at the top.

```
   ┌─────────────────────────────────────────────────────────────┐
 5 │  INTELLIGENCE   — learns from usage; assists & improves       │  changes continuously
   │  (telemetry, AI assists, recommendations, the flywheel)       │
   ├─────────────────────────────────────────────────────────────┤
 4 │  EXPERIENCE     — the surfaces people touch                    │  flexes per role
   │  (tech mobile · dispatch desktop · owner home · customer link)│
   ├─────────────────────────────────────────────────────────────┤
 3 │  CONFIGURATION  — how THIS business assembles the product      │  flexes per business/trade
   │  (JobTypes · Forms · Pricebook · Roles · Workflows)           │
   ├─────────────────────────────────────────────────────────────┤
 2 │  CAPABILITY BRICKS — the snap-on features                      │  add bricks over time
   │  (scheduling · dispatch · estimating · invoicing · payments · │
   │   forms · inventory · communication · booking)               │
   ├─────────────────────────────────────────────────────────────┤
 1 │  FOUNDATION (the spine) — stable core                          │  rarely changes
   │  (data model · identity & roles · multi-tenancy · the Job)    │
   └─────────────────────────────────────────────────────────────┘
   ╎  CROSS-CUTTING (run through every layer):                      ╎
   ╎  Reliability/offline · Trust & money-correctness · Design System ╎
```

### Layer 1 — Foundation (the baseplate)
The unchanging spine: the [object model](03-information-architecture.md) (Customer → Property → Job →
Visit), users/roles, and multi-tenant isolation. Everything snaps onto this. It's deliberately small
and *industry-agnostic* — no trade-specific concept is hard-coded here. **If this is right, the
flexibility above comes almost for free.**

### Layer 2 — Capability bricks (the LEGO bricks)
Each feature is a **self-contained brick** that snaps onto the spine: scheduling, dispatch,
estimating, invoicing, payments, forms, inventory, communication, booking. A brick:
- Does **one thing** well and owns its own logic.
- Talks to the spine and to other bricks through **clean contracts**, never by reaching inside them.
- Can be **added, improved, or swapped** without disturbing the others (payments provider swaps
  behind an interface; a new "memberships" brick snaps on later).

This is why you can **start with a few bricks and add more** without a rewrite — the start-quick,
scale-later promise.

### Layer 3 — Configuration (the studs that connect bricks to a business)
The **flexibility layer** — where a specific shop assembles the bricks for *its* trade: JobTypes,
Forms, Pricebook, Roles, Workflows. An HVAC shop and a landscaper use the **same bricks**, arranged
differently *by configuration, not by code*. This is the multi-industry thesis made real, and the
reason one platform serves many segments.

### Layer 4 — Experience (the surfaces)
The role-tailored UIs people actually touch, composed from the [Design System](design-system/README.md)
and reading the layers below: **mobile** for the technician (quick, offline), **desktop** for
dispatch/admin (dense), **owner home** (glanceable), **customer link** (no download). Same data
underneath — different altitude per [persona](02-personas-and-roles.md).

### Layer 5 — Intelligence (the layer that improves itself)
The layer that makes the product **get better by being used**: telemetry that reveals friction, AI
assists (voice→structured notes, estimating help, the receptionist/booking), and recommendations.
It *observes* the lower layers and *augments* them — it never becomes a dependency they can't run
without. The app works fully with this layer "quiet"; intelligence makes it sharper over time.

### Cross-cutting — the things that must be true everywhere
Three concerns run vertically through all five layers and are non-negotiable at every one:
- **Reliability & offline** — it just works, signal or not ([why it matters](research/user-pain-points.md)).
- **Trust & money-correctness** — numbers and status are always true.
- **Design System** — one consistent language across every surface.

---

## How the layers work together (the rules that keep it smooth)

LEGO only works because every brick shares the same stud spacing. Our equivalent — **four rules**:

1. **Depend downward, never sideways into internals.** A surface uses a brick's contract; a brick
   uses the spine. Nothing reaches into another brick's guts. (This is what lets you change one
   piece safely.)
2. **The spine is sacred and small.** Trade-specific or feature-specific concepts live in bricks or
   configuration — never in Layer 1. Keeping the baseplate clean is what preserves flexibility.
3. **Flex at the top, stabilize at the bottom.** The higher the layer, the more it's allowed to
   change. Frequent change (experiments, AI, config) stays away from the stable core.
4. **Every brick ships with its states & edge cases.** A brick isn't "done" until its
   [edge cases](10-edge-cases.md) and [screen states](ux-ui-review.md) are handled — so adding bricks
   never erodes the "it just works" promise.

Follow these four rules and the system stays **clear** (you can reason about any one piece) and
**flexible** (you can change any one piece) as it grows — which is exactly how it **scales easily**.

---

## The improvement flywheel

"It improves itself" isn't magic — it's a loop you design on purpose. The field user is the engine:

```
        ┌───────────────────────────────────────────────────────┐
        │                                                       │
        ▼                                                       │
  It just works  ──▶  Field user trusts it  ──▶  They use it    │
  (reliability)        & feels respected        every day, for  │
        ▲                                        the whole job   │
        │                                            │           │
        │                                            ▼           │
   Product gets   ◀──  We learn from usage   ◀──  They spread    │
   sharper & more      + feedback (Layer 5)       the word ──▶ Community
   reliable                                       (happy techs)   │
        │                                                       │
        └───────────────────────────────────────────────────────┘
```

- **Reliability → trust → daily use.** If it just works, the field user relies on it. (The opposite
  is the incumbents' death spiral: flaky app → distrust → route around it → data rots.)
- **Daily use → signal.** Real usage + feedback (Layer 5) shows exactly where friction is. The
  product improves where it's actually used, not where we guess.
- **Happy field users → word of mouth → community.** A tradesperson who loves the app tells the next
  one. That's your stated growth engine — and a community is also a **feedback channel** that feeds
  the loop. ([Strategy: "win the technician"](01-product-strategy.md))
- **Community → better product → more reliability.** The loop tightens. Each turn makes the product
  harder to leave and harder to compete with.

**Design implications (so the flywheel actually spins):**
- Build feedback capture *into* the app (a tech can flag "this was slow/wrong" in two taps).
- Instrument the daily loop so we *see* friction (privacy-respecting, [trust-first](05-design-principles.md)).
- Treat the community as a first-class part of the product, not a marketing afterthought — a place
  for field users to be heard and to help each other.

---

## Value per segment (so the buyer sees it's worth the price)

Different people pay attention to different value. The layered model lets us speak to each
[segment](02-personas-and-roles.md) without building separate products:

| Segment | What they feel the value as | Which layer delivers it |
|---|---|---|
| **Technician** (everyday) | "It makes my day easier; I trust it" | Experience + Reliability |
| **Owner** (buyer) | "I see the money, my team's happy, it pays for itself" | Owner home + the flywheel (retention) |
| **Admin** | "I set it up for *us* in a day, no consultant" | Configuration layer |
| **Growing shop** | "It grows with me — I never have to switch" | Capability bricks + clean spine |

The buyer sees great value-for-price because the **same foundation serves all four** — we're not
charging enterprise prices for a tool only the office uses (the ServiceTitan trap), and not so thin
they outgrow it (the Jobber/Housecall trap). One flexible system, value at every seat.

---

## Quick start — how to begin *without* boiling the ocean

You want a strong, flexible foundation **and** to start quick. The layered model is what makes both
possible: **build one thin vertical slice through all the layers, not the whole of any one layer.**

> **The first slice = the [technician's Job flow](04-core-workflows.md) (the wedge).**
> It touches every layer in the smallest possible way, proves the architecture, and is the thing
> that wins your first happy field user — the start of the flywheel.

The minimum that proves the whole system:

| Layer | Build *only* this for the first slice |
|---|---|
| 1 · Foundation | Customer · Property · Job · Visit · one User with a Technician role |
| 2 · Bricks | Just two: **capture** (photo/voice/notes) and **payment**. Nothing else yet |
| 3 · Configuration | One JobType ("Service Call") with one simple form. Hard-code the rest for now |
| 4 · Experience | One surface: the **mobile Job screen**, offline-first |
| 5 · Intelligence | Skip for v0 — leave the hook, add voice→notes next |
| Cross-cutting | Offline + design tokens from day one (these can't be retrofitted) |

This is **Phase 1 / R1** in the [Roadmap](08-roadmap.md) and [PRD](09-prd.md) — already scoped. Build
*that* slice well, put it in front of one real shop, and you have proof the foundation works before
you add a single extra brick.

**The build-quick checklist:**
1. Scaffold the monorepo + design-token package (the cross-cutting layer that must exist first).
2. Stand up the spine (Layer 1) — just the four objects and one role.
3. Build the mobile Job screen (Layer 4) on a local-first store (offline cross-cutting).
4. Add the two bricks (capture, payment) behind clean contracts (Layer 2).
5. One JobType to make it real (Layer 3).
6. Run a real job through it. Celebrate. *Then* add the next brick.

> Start narrow, build through every layer once, prove it works — then widen. That's how you get a
> quick start **and** a foundation that scales.
