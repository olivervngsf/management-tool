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

## The one-paragraph pitch

**Fieldwork** is the operating system for a service business. A dispatcher runs the day from
a live board on the desktop. A technician runs the job from their phone — arriving, diagnosing,
quoting, collecting payment, and closing out, even with no signal in a basement. The owner sees
the money. The customer gets a tracking link that feels like ordering a rideshare. Every screen
holds to a single standard: it should feel inevitable, fast, and quietly beautiful.

## Status

- **Now:** Product & design foundation (this repo).
- **Next:** Monorepo scaffold + design-token package + clickable prototype of the technician
  job flow and the dispatch board. See [Roadmap](docs/08-roadmap.md).
