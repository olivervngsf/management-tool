# 19 · Data Visualization & the Owner Dashboard

> Closes UX gap **G11**. How we turn the owner's numbers into a **visual story told over time** —
> stat cards with trend deltas and a hero chart — instead of a wall of figures. Inspired by clean
> consumer analytics (the Substack "Overview" style) and built to the
> [compact, Apple-grade](design-system/README.md) bar.

See it live: the **Insights** screen in the [prototype](prototype/fieldwork-prototype.html).

---

## How competitors do it (and where they fall short)

| Tool | Dashboard style | The gap |
|---|---|---|
| **ServiceTitan** | Deep, powerful reporting; granular per-customer/unit metrics; report-builder | **Dense & enterprise** — powerful but overwhelming; users cite "limited reporting-template customization"; it's a *data tool*, not a *story* |
| **Jobber / Housecall Pro** | Simpler number tiles + some widgets; HCP adds "Analyst AI" Q&A | **Flat** — mostly bare tiles and tables; little time-based storytelling; you read numbers, you don't *see the trend* |
| **The pattern** | Number tiles + tables | Almost everyone shows *what the number is*, not *where it's going or why it matters* |

**The opening:** the trades market has powerful-but-dense (ServiceTitan) or simple-but-flat
(Jobber/HCP). Nobody pairs **consumer-grade visual storytelling** with operational truth. That's us.

---

## How we get better — six moves

1. **Tell the story by time.** One **hero time-series chart** (revenue, month by month) is the
   centerpiece — the owner *sees* the year's shape in a glance, not a grid of cells. Time is the
   narrative.
2. **Numbers with meaning, not bare figures.** Every KPI card = **value + trend delta (% vs prior
   period) + context** (e.g. "$1.84M ↑28% vs last year", "3,420 jobs · avg ticket $538"). A number
   without a direction and a comparison is trivia.
3. **One period selector, many zooms.** Today / week / month / year — the same story at different
   altitude. Default to the most useful (the owner's "how are we doing?" is usually month or year).
4. **Glanceable first, drill-down on demand.** The dashboard answers "are we winning?" in one look;
   tapping any number opens the **jobs/invoices behind it** (progressive disclosure, [principle 6](05-design-principles.md)).
5. **Trust-first, not vanity.** Every chart **reconciles to real invoices** — "to the penny"
   ([transparency](15-transparency-and-control.md)). We never show a flattering number that doesn't
   tie out; trust is the whole asset of an operational dashboard.
6. **Restraint = clarity (Apple-grade).** One accent color, generous whitespace, soft gradient fills,
   sparklines for micro-trends, **no chart junk**. The Substack-overview feel: confident, calm,
   legible. Compact house density, but the hero chart gets room to breathe.

---

## Data-viz guidelines (the house rules)

- **Chart types — pick by intent:**
  - **Area / line** → a trend or cumulative story over time (revenue, jobs, members). *Default hero.*
  - **Bars** → comparison between peers (revenue by tech, jobs by type).
  - **Donut/segments** → part-to-whole, used *sparingly* (e.g. paid vs. unpaid).
  - **Big stat + sparkline** → a single KPI with its recent shape.
  - Avoid: 3-D anything, pie charts with >4 slices, dual axes, decorative gradients.
- **Money & numbers:** one `MoneyDisplay` everywhere; abbreviate at scale ($1.84M, not $1,840,000);
  align decimals; currency formatting consistent.
- **Trend deltas:** green up / red down — but **never color alone** ([principle 9](05-design-principles.md));
  always pair with an arrow + the % and the comparison period.
- **Color:** the brand accent for the primary series; neutrals for everything else; semantic colors
  only for true meaning (over-budget, overdue).
- **Motion:** charts may draw-in once (≤ 400ms), respect `prefers-reduced-motion` (fall back to
  static). Never animate on every data refresh.
- **Accessibility:** every chart has a text/table equivalent; series labeled; sufficient contrast;
  data points reachable, not hover-only ([WCAG 2.2 AA](09-prd.md) NFR4).
- **Responsive:** the hero chart reflows from desktop full-width down to a phone sparkline-card; KPI
  cards stack ([NFR15](09-prd.md)).

---

## The owner dashboard, two altitudes

- **Phone (glanceable):** the [Owner screen](prototype/fieldwork-prototype.html) — KPI tiles +
  job-costing, "how did today go?" Same data, simplified.
- **Desktop (the story):** the **Insights** screen — KPI stat cards with deltas + the hero revenue
  area chart + period selector. "How is the business trending?" *Same numbers, more room to tell the
  story.*

Both are the *same reconciled data* at different zoom — never a separate "reporting database"
([one object model](03-information-architecture.md)).

---

## What to build (maps to the backlog)

- ✅ Prototype: Insights screen with KPI deltas + hero area chart (visual reference).
- 🔲 [C1 Owner home](build-backlog.md) / [C2 job costing](build-backlog.md): wire these to real,
  reconciled data.
- 🔲 [C3 reporting depth](build-backlog.md) (R5): revenue-by-tech bars, job-type mix, AR aging,
  membership growth — each following the house rules above.

> **The principle:** *show the story, not just the score.* Competitors show the owner a number;
> we show them where the business is going — truthfully, at a glance, beautifully.
