# 03 · Information Architecture

IA is where multi-role and multi-industry promises are kept or broken. Two ideas govern
everything here:

1. **A single, industry-agnostic object model** (the spine).
2. **Role-tailored navigation over that shared model** (the surfaces).

---

## The object model (the spine)

Every entity below is universal across trades. Trade-specific meaning lives in *configuration and
templates*, never in the core schema.

```
Organization
 └─ Location(s)                 a physical branch / dispatch hub
     ├─ User ── Role(s)         the five people; composable permissions
     ├─ Customer                a person or company we serve
     │   └─ Property            an address with equipment, history, access notes
     │       └─ Job             a unit of work at a property ("AC not cooling")
     │           ├─ Visit       a scheduled appointment by a tech (jobs can have many)
     │           │   └─ TimeEntry  on-my-way / arrived / working / done
     │           ├─ Estimate    proposed line items, one or more options (good/better/best)
     │           │   └─ LineItem service or material, priced from the Price Book
     │           ├─ Invoice     what's owed, derived from approved work
     │           │   └─ Payment card / ACH / cash / check
     │           ├─ Note        text / photo / voice / form submission
     │           └─ FormResult  a completed configurable form (inspection, checklist)
     └─ Catalog
         ├─ PriceBook           services & materials with price, cost, tax
         ├─ JobType             template: default forms, line items, duration, skills
         └─ Form                configurable field set attached to job types
```

### Why this shape is the whole bet on flexibility

- **Job ≠ Visit.** A furnace install is one Job with three Visits. A drain clear is one Job, one
  Visit. Conflating them (as simpler tools do) breaks the moment a job needs a second trip — which
  in the trades is constantly. Getting this right on day one avoids a painful migration later.
- **Property is a first-class object, not an address string.** Equipment, warranty, access codes,
  "dog in the backyard," and full service history live on the Property. The second time a tech
  visits, the app already knows the unit's model number. This is a durable moat: the data
  compounds.
- **JobType + Form = the configuration layer.** An HVAC "Maintenance" job type ships with a coil
  inspection form and standard tune-up line items. A landscaper later defines a "Spring Cleanup"
  job type with its own form. Same engine, different config. No core code changes.
- **Two first-class concepts above the Job** (confirmed by [data-model research](14-data-model.md)):
  a **Service Agreement / Membership** (the *contract* — a recurring plan that generates Jobs on a
  schedule), and a **Project** (a container above Job for multi-visit installs with phases, deposits,
  and progress billing). Simple jobs need neither; big jobs and recurring revenue need both.

> For the complete field-by-field breakdown of every entity — and **who needs each field** (field
> technician vs. office/admin vs. owner) — see the [Data Model & Field Dictionary](14-data-model.md).

---

## Navigation: role-tailored surfaces over one model

### Mobile (the Technician app — Maria)

Mobile is **focused, not a shrunk-down desktop.** A flat structure, four destinations max in a
tab bar, everything thumb-reachable.

```
┌─────────────────────────────────┐
│  Today        (default)         │  ← chronological list of my visits, current job pinned
│  Schedule                       │  ← my week, calendar view
│  Customers                      │  ← search any property/customer + history
│  More          (profile, etc.)  │
└─────────────────────────────────┘
        the JOB is the center of gravity
```

The technician spends ~90% of time *inside one Job*. So the Job screen is the real home: a vertical
flow of arrive → diagnose → quote → do work → collect → close, with a persistent action bar. We
optimize the depth of one screen, not the breadth of navigation. See
[Core Workflows](04-core-workflows.md).

### Desktop (the Office console — David, Alex)

Desktop is **dense and lateral.** A persistent left rail; the Dispatch Board is the heart.

```
┌──────────┬──────────────────────────────────────────────┐
│ Dispatch │  THE BOARD — techs × time, drag to assign     │
│ Schedule │  live status, unassigned queue, map toggle    │
│ Jobs     │                                               │
│ Customers│  ── detail panels slide in, board stays ──    │
│ Invoices │                                               │
│ Reports  │                                               │
│ Settings │  (Settings = Alex's configuration home)       │
└──────────┴──────────────────────────────────────────────┘
```

Desktop favors keyboard, multi-select, and side-by-side context (board + job detail at once).
The dispatcher should rarely leave the board.

### Cross-device Home (the Owner — Sofia)

A glanceable summary that is *the same data, different altitude.* Works on phone and desktop.
Today's revenue, jobs completed vs. scheduled, team status, anything needing attention. Every tile
drills into the same objects David and Maria touch — one source of truth, three altitudes.

---

## The "same model, different altitude" principle

| Object | Maria (tech) sees | David (dispatch) sees | Sofia (owner) sees |
|---|---|---|---|
| **Job** | the work to do now, step by step | a card on the board to place & track | a number in "revenue in progress" |
| **Customer** | who I'm helping + this property's history | a record to reach and route to | a segment in "repeat vs. new" |
| **Payment** | the tap that gets me paid before I leave | confirmation a job can close | today's cash, reconciled |

One object model. No data silos. This is why the owner's numbers tie out — they are literally the
technician's actions, aggregated.

## Multiple views, one model (different *representations*, same data)

Beyond altitude, the same objects are shown as different **views** — the pattern generic tools like
Infinity/Notion/ClickUp made popular ([research](research/market-and-competitors.md)). A set of Jobs
is the *same data* rendered as:

| View | Best for | In the product |
|---|---|---|
| **List** | "what's next" (the tech) | Today |
| **Board** (techs × time) | running the day (dispatch) | Dispatch board |
| **Calendar** (week) | capacity & planning (office) | Schedule |
| **Map** | proximity & routing (dispatch) | board map toggle |

**Our difference vs. the generic tools:** they hand you blank views and make you *build* your own
structure; we ship the **right views with trade-tuned defaults**, so a shop runs *its* workflow on day
one instead of designing one. Flexibility *with* a head start — the [configuration layer](12-system-layers.md)
lets a power user add or tune views later, but nobody starts from a blank canvas.

---

## Search and the command surface

- **Mobile:** a single search reaches any customer, property, or job. Bias to recent and nearby.
- **Desktop:** a command palette (`⌘K`) — jump to any object, run any action, no menu hunting.
  This is core to the "dispatcher never thinks about the tool" goal and a strong Apple-grade signal.

## What does *not* belong in navigation

Resist the incumbent urge to expose every object as a top-level nav item. If it isn't part of a
daily loop for that role, it lives inside the object it belongs to or in Settings. Navigation is
a statement of priorities, not a sitemap.
