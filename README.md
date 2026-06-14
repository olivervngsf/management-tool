# Fieldwork — Product & Design Foundation

> A field service management platform for the trades, built to feel like an Apple product
> and bend to any industry. Mobile-first for the people in the field, powerful on the
> desktop for the people running the business.

This repository currently holds the **product and design strategy** — the shared
foundation a team aligns around before writing application code. It is opinionated,
concrete, and anchored to a real first vertical (HVAC / plumbing / electrical) while
designing the core to flex across industries.

## Why this exists

The incumbents (ServiceTitan, Jobber, Housecall Pro, Swivl) proved the market. They also
left a gap: software that field technicians actually *like* using, that a dispatcher can
run a busy board on without training, and that a multi-trade business can configure to its
own workflow without a six-week onboarding. Our wedge is **experience quality** — Apple-grade
interaction design applied to an unglamorous, high-stakes operational domain.

## How to read this

Read in order. Each document assumes the previous ones.

| # | Document | What it answers |
|---|----------|-----------------|
| 00 | [Market & Competitive Research](docs/research/market-and-competitors.md) | Cited evidence base: market size, competitor profiles, pricing, white space, risks |
| 00b | [User Pain Points Registry](docs/research/user-pain-points.md) | Living catalog of user pains by persona, with severity, evidence, and our response |
| 00c | [Competitor Lessons → Our Plays](docs/research/competitor-lessons.md) | Plain-language list: what each competitor does, where it breaks, how we win, mapped to your goals |
| 00d | [Competitor Scorecard](docs/research/competitor-scorecard.md) ([visual](docs/research/competitor-scorecard.html)) | One-page at-a-glance scorecard: us vs. ServiceTitan / Jobber / Housecall / Swivl |
| 01 | [Product Strategy](docs/01-product-strategy.md) | Who we serve, the wedge, how we win, pricing model, what we will *not* build first |
| 02 | [Personas & Roles](docs/02-personas-and-roles.md) | The five people in the system and what each one needs |
| 03 | [Information Architecture](docs/03-information-architecture.md) | The object model, navigation, and how mobile vs. desktop differ |
| 04 | [Core Workflows](docs/04-core-workflows.md) | The job lifecycle and the critical end-to-end flows |
| 05 | [Design Principles](docs/05-design-principles.md) | The ten rules every screen is judged against |
| 06 | [Design System](docs/design-system/README.md) | Tokens, type, color, motion, and the component library |
| 07 | [Technical Architecture](docs/07-technical-architecture.md) | Monorepo, shared design tokens, data model, offline, backend |
| 08 | [Roadmap](docs/08-roadmap.md) | Phased plan from prototype to GA |
| 09 | [Product Requirements (PRD)](docs/09-prd.md) | Scoped features, requirements, acceptance criteria, and success metrics |
| 10 | [User Edge Cases](docs/10-edge-cases.md) | The hard real-world cases each flow must handle |
| 11 | [UX/UI Review & Gap Analysis](docs/ux-ui-review.md) | Coherence check, missing-artifact backlog, and the reusable design-review checklist |
| 12 | [System Layers & the Improvement Flywheel](docs/12-system-layers.md) | The operating philosophy: LEGO-like layers, how they compose, the self-improvement loop, value per segment, and the quick-start slice |
| 13 | [AI Operating Model](docs/13-ai-operating-model.md) | How AI behaves: write-it-fills, the autonomy ladder, the human gate, AI self-reporting, operational awareness, and admin-governed disclosure |
| 14 | [Data Model & Field Dictionary](docs/14-data-model.md) | Every entity and its concrete fields, marked by who needs each (field tech vs office/admin vs owner); contracts, projects, the date/status model |
| 15 | [Transparency, Status & Staying in Control](docs/15-transparency-and-control.md) | Shared status, the One-Line Report, early concern-raising before things go out of scope, financial transparency, and keeping the human in control |
| 16 | [Notes, Communication & Reflection](docs/16-notes-and-reflection.md) | One safe home for all writing: operational notes, team messages, and a private personal layer for daily notes, reflection, and growth |
| 17 | [Screen-State Catalog](docs/17-screen-states.md) | The seven states (default/empty/loading/error/offline/no-permission/success) for every critical screen |
| 18 | [Location & Privacy Design](docs/18-location-privacy-design.md) | Designing the balance: customer ETA transparency without surveilling the tech — location follows the job, not the person |
| 19 | [Data Visualization & Owner Dashboard](docs/19-data-visualization.md) | Telling the story by time: stat cards with deltas + a hero chart; how competitors do it and how we do better |
| 20 | [The Ecosystem & Self-Improvement](docs/20-ecosystem-and-self-improvement.md) | Many small products as one living system: shared data, change-awareness that ripples, the "Top 5 to Improve" report, and the operating model |

**See it:** [Clickable prototype](docs/prototype/fieldwork-prototype.html) — the technician flow + dispatch board (open in a browser).
**Build menu:** [Build Backlog — flows to prioritize](docs/build-backlog.md).
**Must-haves:** [Table Stakes — the foundation (needs vs wants, with evidence)](docs/research/table-stakes.md).

## The one-paragraph pitch

**Fieldwork** is the operating system for a service business. A dispatcher runs the day from
a live board on the desktop. A technician runs the job from their phone — arriving, diagnosing,
quoting, collecting payment, and closing out, even with no signal in a basement. The owner sees
the money. The customer gets a tracking link that feels like ordering a rideshare. Every screen
holds to a single standard: it should feel inevitable, fast, and quietly beautiful.

## Where things stand & the smooth path forward

> The control center. Everything connects; here's the state and the next steps so it all moves
> smoothly without anything falling through.

**✅ Done — the foundation (this repo is coherent and cross-linked):**
- **Why & who:** [research](docs/research/market-and-competitors.md) · [pain points](docs/research/user-pain-points.md) · [strategy](docs/01-product-strategy.md) · [personas](docs/02-personas-and-roles.md)
- **What & how it works:** [IA](docs/03-information-architecture.md) · [flows](docs/04-core-workflows.md) · [edge cases](docs/10-edge-cases.md) · [data model](docs/14-data-model.md)
- **The experience & principles:** [design principles](docs/05-design-principles.md) · [design system](docs/design-system/README.md) · [transparency & control](docs/15-transparency-and-control.md) · [notes & reflection](docs/16-notes-and-reflection.md)
- **The AI & the system shape:** [AI operating model](docs/13-ai-operating-model.md) · [system layers](docs/12-system-layers.md) · [architecture](docs/07-technical-architecture.md)
- **The plan & the craft backlog:** [PRD](docs/09-prd.md) · [roadmap](docs/08-roadmap.md) · [UX/UI review (G1–G29)](docs/ux-ui-review.md) · [state catalog](docs/17-screen-states.md)
- **First artifact:** the [clickable prototype](docs/prototype/fieldwork-prototype.html).

**▶ Now — make it real & validate (the smooth next steps, in order):**
1. **Iterate the prototype** from real reactions (density, the AI capture screen).
2. **Add the last two core screens:** owner home / job costing, and the customer portal.
3. **Find one pilot shop** (HVAC/plumbing/electrical) to react to the prototype — the highest-leverage validation.
4. **Then build the Phase-1 slice** (the [quick-start](docs/12-system-layers.md): monorepo + tokens + the offline technician Job screen).

**⏳ Open decisions (so nothing stalls):**
- Confirm the name (**Fieldwork**?) and any brand direction beyond the iOS-blue system.
- Confirm first vertical (HVAC/plumbing/electrical — chosen).
- A pilot shop contact (or use the [find-a-partner guidance](docs/research/market-and-competitors.md) we discussed).

**The one rule that keeps it smooth:** every new idea gets written into the doc it belongs to and
cross-linked, so the foundation stays one coherent whole — and every build decision traces back to a
goal in the [PRD](docs/09-prd.md). Nothing floats unattached.
