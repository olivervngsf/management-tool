# 07 · Technical Architecture

This document describes the shape of the system that makes the strategy buildable. It is a target
architecture for the foundation phase — concrete enough to start, loose enough to evolve. It
follows from the stack decision: **Next.js (web) + React Native / Expo (mobile), one TypeScript
language, shared design tokens.**

> This is the *technical* expression of the [System Layers model](12-system-layers.md): the
> monorepo packages below map to the layers (foundation → bricks → configuration → experience →
> intelligence), and the "depend downward, never sideways" rule is what keeps it flexible at scale.

---

## Guiding constraints (from the strategy)

1. **Offline-first on mobile** — the technician's job flow must work with zero signal
   ([Flow 1](04-core-workflows.md)). This is the hardest constraint and it shapes everything.
2. **One object model, many surfaces** — the [IA spine](03-information-architecture.md) is the
   schema; no role gets its own data store.
3. **Real-time on the desktop** — the dispatch board reflects the field *now*.
4. **Money correctness** — financial data is transactional and reconciles to the penny.
5. **Multi-tenant from day one** — every row is scoped to an Organization; isolation is not
   retrofittable.

---

## Monorepo shape

One repository, TypeScript end to end, so types and design tokens are shared rather than
duplicated.

```
/
├─ apps/
│  ├─ web/            Next.js — office console (dispatch, jobs, invoices, settings) + owner home
│  ├─ mobile/         Expo / React Native — technician app
│  └─ booking/        lightweight customer-facing booking + tracking (no-download web)
├─ packages/
│  ├─ tokens/         compiles design-system/tokens.json → CSS vars + TS theme
│  ├─ ui/             shared component library (RN primitives + web adapters)
│  ├─ core/           domain model, validation (zod), business logic — platform-agnostic
│  ├─ api-client/     typed client generated from the API contract
│  └─ config/         shared tsconfig, eslint, prettier
└─ services/
   └─ api/            backend (see below)
```

Tooling: **pnpm workspaces + Turborepo** for fast, cached builds. The `tokens` and `core` packages
are the load-bearing "write once" wins — design and domain logic live in exactly one place.

---

## The design-token pipeline (the cross-platform glue)

```
docs/design-system/tokens.json   (source of truth, the design language)
            │  Style Dictionary build (in packages/tokens)
            ├──────────────▶ web:    :root { --color-brand-primary: #0A84FF; ... }
            └──────────────▶ mobile: export const theme = { color: { brand: { primary: '#0A84FF' }}}
```

A designer or engineer changes a token once; both apps update on next build. This is the mechanism
behind the [design system's](design-system/README.md) parity promise. Generated files are never
hand-edited.

---

## Backend

**Recommendation: a single TypeScript API service to start** (Node, e.g. NestJS or a tRPC/Fastify
setup), Postgres as the system of record, with a clear path to extract services later if scale
demands. Resist premature microservices — one well-factored service ships the first five flows far
faster, and the domain isn't yet understood well enough to draw good service boundaries.

- **Database:** **PostgreSQL.** Relational integrity matters here — jobs, invoices, and payments
  have real referential constraints and need transactions. Multi-tenancy via an `org_id` on every
  table, enforced with row-level security as a hard backstop.
- **API:** typed end-to-end (tRPC or OpenAPI-generated client in `packages/api-client`) so the
  frontend can't drift from the backend contract.
- **Real-time:** WebSocket channel (e.g. Postgres `LISTEN/NOTIFY` → socket fan-out, or a managed
  service) pushes board/job updates to the desktop console live.
- **Auth:** OIDC-based, with the [composable role/permission model](02-personas-and-roles.md)
  enforced server-side on every request — never trust the client's idea of permissions.
- **Files:** photos/signatures to object storage (S3-compatible), uploaded directly from the
  client with signed URLs; the API stores references, not blobs.

---

## Offline-first (the defining technical challenge)

The technician app is **local-first**: the device holds a real database, the UI reads and writes to
it instantly, and a sync engine reconciles with the server in the background.

- **Local store:** a device database (e.g. WatermelonDB or SQLite + a sync layer) holds the techs'
  jobs, properties, and price book.
- **Optimistic writes:** every action commits locally first (principle 4: speed). The UI never
  waits on the network.
- **Sync engine:** a durable outbox queues changes and flushes when connectivity returns, with
  retry and backoff. Sync status is surfaced honestly to the user (principle 8: trust).
- **Conflict policy:** the field is the source of truth for what happened on site (the tech was
  there). Server-authoritative data (price book, assignments) flows down; field observations and
  captures flow up and win on conflict. Money operations are the exception — payment capture is
  confirmed server-side before it's shown as "paid."
- **Scope:** a device only syncs the data that tech needs (their jobs + relevant properties), not
  the whole org — bounded, fast, and privacy-respecting.

This is genuinely hard and is why the [roadmap](08-roadmap.md) treats offline as a first-class
phase, not a late add-on. Retrofitting offline onto an online-first app is a rewrite; we don't make
that mistake.

---

## Integrations (partner, don't build — per strategy)

- **Payments:** Stripe (incl. Tap to Pay on iPhone) or an FSM-friendly processor. Payments are
  core to the product *and* a revenue line, so the integration is deep but the rails are theirs.
- **Accounting:** QuickBooks Online / Xero — one-directional, idempotent push of closed invoices.
- **Comms:** an SMS/email provider for customer notifications and the tracking link.
- **Maps/routing:** a maps provider for the on-my-way tracking and dispatch proximity.

Each integration sits behind an interface in `packages/core` so a provider can be swapped without
touching product code.

---

## Non-functional bar

| Concern | Target |
|---|---|
| Perceived primary-action latency | < 100 ms (optimistic UI) |
| Cold mobile launch → usable | < 2 s |
| Board update propagation | < 1 s field action → dispatcher screen |
| Offline job flow | 100% of [Flow 1](04-core-workflows.md) works with no signal |
| Tenant isolation | enforced at the DB row level, not just app logic |
| Financial reconciliation | exact; payments confirmed server-side |

---

## What we are explicitly deferring

- Microservice decomposition (until the domain and scale justify boundaries).
- Native Swift/Kotlin rewrites (Expo carries us well past product-market fit; revisit only if a
  specific capability demands it).
- A self-serve plugin/marketplace platform (a post-PMF motion).
- Data warehouse / advanced analytics (the owner's home is computed from the operational DB first).

Architecture serves the [roadmap](08-roadmap.md); we build exactly enough to make the next phase's
flows real, and no more.
