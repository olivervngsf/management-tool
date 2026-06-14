# Market & Competitive Research

> Cited research synthesized from five parallel research streams (June 2026): ServiceTitan;
> Jobber + Housecall Pro; Swivl and the AI-native wave; the FSM market; and user sentiment /
> white space. This report is the evidence base for everything in
> [Product Strategy](../01-product-strategy.md) and the [PRD](../09-prd.md).
>
> **Methodology & confidence:** Findings are drawn from multi-source web research, cross-checked
> across independent sources. In this environment direct page-fetch (WebFetch) was blocked (HTTP
> 403) on most vendor and review domains, so claims rest on search-surfaced excerpts rather than
> full-page reads, and Reddit was reached via review-synthesis aggregators rather than directly.
> Competitor **pricing is largely unpublished or promo-variable** — treat specific dollar figures
> as well-corroborated estimates, not contract quotes. Items needing primary-source confirmation
> before external/financial use are flagged inline as *(verify)*.

---

## Executive summary

The field service management (FSM) software market is **~$5–6.5B (2025–26), growing to
~$9.5–13.8B by 2030–34 at roughly 10–13% CAGR**, sitting on top of a **~$1.5 trillion** annual
trades-services TAM in the US/Canada. The defining fact for a new entrant is the **digitization
gap**: ~45% of trades/construction buyers still run on pen-and-paper or spreadsheets and ~56% use
no purpose-built FSM software, with QuickBooks as the default "system."

The incumbents have sorted themselves by company size, and each leaves a clear seam:

- **ServiceTitan** owns the enterprise (20+ techs) — powerful, but with a 12–16 week, $5K–$50K
  onboarding, $245–500/tech/mo pricing, punitive lock-in, and a **mobile/offline experience that
  is its most consistent weakness** (the app redesign dropped to ~3.3★).
- **Jobber** and **Housecall Pro** own the SMB — approachable and well-liked, but they get
  expensive as you grow (per-seat creep / add-on creep) and shallow past ~15–20 techs, and their
  Android/offline reliability is a recurring complaint.
- **Swivl and a well-funded AI-native wave** (Avoca, Netic, Quantra, FieldCamp) are attacking from
  the AI angle — mostly AI *voice/agents on the inbound call*, plus AI estimating. This is the
  fastest-moving front and reframes the bar from "good UX" to "AI-assisted operations."

**The white space we are built for:** an experience-led platform that is **genuinely offline-first**
(incumbents silently lose field data), **radically low-friction for the technician** (the "under-30-
second job"), **honestly priced with day-not-quarter onboarding**, **trust-first rather than
surveillance-first**, and **configurable across trades without a per-vertical rebuild** — with AI
woven in rather than bolted on. The biggest risks are data-gravity/switching costs, the
simplicity-vs-depth tension that dragged ServiceTitan into complexity, the genuine engineering
difficulty of offline-first, and a conservative, word-of-mouth-driven buyer base.

---

## 1. Market size & growth

Estimates diverge by scope (software-only vs. software+services; differing base years). Report the
**range**, not any single figure.

| Firm | Base-year size | Forecast | CAGR | Horizon |
|---|---|---|---|---|
| Grand View Research | ~$4.49B (2023) | $11.78B by 2030 | 13.3% | 2023–2030 |
| MarketsandMarkets | ~$5.10B (2025) | $9.17B by 2030 | 12.5% | 2025–2030 |
| Fortune Business Insights | $6.14B (2026) | $13.79B by 2034 | 10.7% | 2026–2034 |
| Mordor Intelligence | $6.26B (2026) | $9.87B by 2031 | 9.54% | 2026–2031 |

**Synthesis:** ~$5–6.5B today → roughly doubling to ~$9.5–13.8B by 2030–34, ~10–13% CAGR. Cloud is
the dominant deployment (~68% share); Asia-Pacific the fastest-growing region.

**The TAM beneath the software:** ServiceTitan estimates ~**$1.5 trillion/yr** spent on trades
services in the US/Canada *(verify — self-reported in IPO materials)*; the US home-services market
was **>$657B (2022)**.

Sources: [Grand View](https://www.grandviewresearch.com/industry-analysis/field-service-management-market),
[MarketsandMarkets](https://www.marketsandmarkets.com/PressReleases/field-service-management.asp),
[Fortune Business Insights](https://www.fortunebusinessinsights.com/field-service-management-fsm-market-102215),
[Mordor](https://www.mordorintelligence.com/industry-reports/field-service-management-market),
[ServiceTitan home-services stats](https://www.servicetitan.com/blog/home-services-industry-statistics).

---

## 2. The digitization gap (why now)

The single most important market fact for a new entrant — most of the market is still un-digitized:

- **~45%** of construction/trades buyers still use manual methods (pen-and-paper, spreadsheets);
  **~56%** use no purpose-built FSM software; ~12% have no system at all.
  ([Gartner Digital Markets](https://www.gartner.com/en/digital-markets/insights/stand-out-in-your-category-with-construction-buyer-insights))
- **QuickBooks is the default "system"** for trades — ~62% accounting-software share, with
  construction its #1 vertical (~17.2%). Many shops run on general accounting software, not FSM —
  a direct displacement opportunity. ([electroiq](https://electroiq.com/stats/quickbooks-statistics/))
- A **"missing middle"** (~80% of field-service businesses) is too big for consumer tools but too
  small for ServiceTitan. ([FieldCamp](https://fieldcamp.medium.com/the-missing-middle-why-80-of-field-service-businesses-are-underserved-0978a3fe40c3))

**Tailwinds:** an acute skilled-trades labor shortage (~2.1M jobs potentially unfilled by 2030; a
JLL-estimated ~$1T economic risk) is pushing shops to do more with fewer techs via software; and
PE roll-ups (a record HVAC deal year in 2024; ~27 active US platforms) are driving enterprise FSM
demand. ServiceTitan's Dec 2024 IPO validated the category.
Sources: [JLL](https://www.jll.com/en-us/newsroom/critical-skilled-trades-shortage-threatens-economic-losses),
[Fortune/JLL](https://fortune.com/2026/04/21/america-silent-army-jll-report-skilled-trades-job-shortage-cost/),
[pipelineon (PE)](https://pipelineon.com/blog/private-equity-buying-hvac/).

---

## 3. Competitor profiles

### ServiceTitan — the enterprise incumbent

- **Positioning (their words):** "the operating system for the trades." Mission framing from the
  S-1: ensure tradespeople are never "left behind by technology." Values: "customers first, company
  second, individual third." ([company](https://www.servicetitan.com/company))
- **Scale:** Nasdaq: TTAN, IPO'd Dec 2024 (~$8.9B market cap at open); FY2026 revenue **$961M, +24%
  YoY**, crossing a $1B run-rate; ~8,000–11,000+ customers; >$55.7B GTV processed; enterprise gross
  retention >95%. *(exact financials verify against 10-K)*
- **Scope:** the broadest — call booking, dispatch board w/ GPS & route optimization, technician
  app, pricebook, multi-option proposals, invoicing, **ServiceTitan Payments** + consumer
  financing, memberships, CRM, Marketing Pro, reporting, inventory. "Pro" add-ons (Dispatch Pro,
  Marketing Pro, Pricebook Pro). AI: **Titan Intelligence** + **Atlas** conversational "sidekick."
- **GTM:** sales-led, demo-gated; best fit 20+ techs with office staff and budget; explicitly *not*
  a fit for shops under ~5–10 techs.
- **Strengths:** all-in-one consolidation, strong dispatch/scheduling, deep reporting. G2 4.5★,
  Capterra 4.3★ (Value for Money its weakest at 3.9).
- **Complaints (the seam):** steep learning curve (its #1 cited weakness); 12–16 week, $5K–$50K
  implementation (some "never onboarded"); cost & add-on stacking; contract lock-in with documented
  early-termination fees ($15K–$46K cases); **mobile app regressed to ~3.3★** after redesign
  ("more complex," "updates slow it down"); **limited offline** — techs in basements/rural areas
  lose access and have lost unsynced data.

Sources: [getonecrew](https://www.getonecrew.com/post/servicetitan-reviews),
[fieldcamp](https://fieldcamp.ai/reviews/servicetitan/),
[FY26 results](https://investors.servicetitan.com/news-releases/news-release-details/servicetitan-announces-fiscal-fourth-quarter-and-full-fiscal),
[ST Community: offline sync](https://community.servicetitan.com/t5/Mobile/Offline-Synching-Issues/m-p/24503).

### Jobber — the SMB favorite

- **Positioning:** "#1 end-to-end platform built for home and commercial service businesses";
  mission "to help people in small businesses be successful." Surpassed **100,000 customers** (2026).
- **Target:** SMB, sweet spot 1–10 employees; ~97% of customers <50 employees; home *and* commercial.
- **Scope:** CRM, scheduling/dispatch, quoting, invoicing, online booking, **Jobber Payments**,
  marketing, reporting. AI: **Copilot** advisor + **AI Receptionist** (24/7 call/text answering).
- **Strengths:** ease of use (wins "Best Ease of Use" awards), strong support, reliable mobile app;
  ~4.6★. **Complaints:** per-user pricing gets expensive as teams grow; QuickBooks sync
  unreliability; businesses outgrow it past ~15–50 employees (reporting/automation/inventory too
  shallow).

Sources: [Jobber 100k customers](https://www.prnewswire.com/news-releases/jobber-surpasses-100-000-customers-cementing-its-position-as-the-market-leading-platform-for-home-and-commercial-service-businesses-302768759.html),
[checkthat reviews](https://checkthat.ai/brands/jobber/reviews),
[getonecrew](https://www.getonecrew.com/post/jobber-reviews).

### Housecall Pro — the SMB growth-tools play

- **Positioning:** "Champion the Trades"; aims to be "the default operating system for small and
  mid-sized home services businesses." Founded 2013; **45,000+ businesses / 180,000+ pros**; ~$1.1B
  valuation.
- **Target:** home services only; sweet spot 1–20 techs, $250K–$2M revenue; notable HVAC/membership
  strength.
- **Scope:** scheduling/dispatch, app, estimates, invoicing, **Payments + Instapay**, online
  booking, sales pipeline, marketing automation, recurring plans, lead integrations (Yelp, Google).
  AI: **"AI Crew"** — CSR AI (paid), Marketing/Analyst/Coach/Help AI (free).
- **Strengths:** fast onboarding ("operational in days"), intuitive UI, Capterra ~4.7★.
  **Complaints:** **add-on cost creep is the #1 complaint** (a 5-tech setup can reach ~$1,600/mo,
  ~9× the advertised entry price); billing/cancellation friction (Trustpilot ~2.9); **Android app
  3.2★** vs 4.5★ iOS — crashes during invoice creation, photo-upload trouble.

Sources: [projul HCP pricing](https://projul.com/blog/housecall-pro-pricing-analysis-2026/),
[checkthat HCP](https://checkthat.ai/brands/housecall-pro/reviews),
[contractortoolstack](https://contractortoolstack.com/software/housecall-pro/).

### Joby (joby.io) — lead-management & communications-first (home services)

> Profiled from the **live product screens** (app.joby.io) the user supplied — "real screens from the
> actual app, not mockups." **Identity caveat:** do **not** confuse **Joby (joby.io)** with **Jobi
> (jobi.pro)**, a separate HVAC "run-your-business-from-your-phone" product that dominates search.

- **What it is:** a home-services management platform that leads with the **front of the funnel** —
  *lead capture + communications* — rather than field execution. Office/desktop web app.
- **Positioning (their words):** **"Never miss a lead."** · **"Every call, text, and lead in one
  inbox."** · *"calls, texts, voicemail, and team chat all in one place — when you can't pick up,
  Joby [answers]."*
- **Target:** home-services / home-improvement contractors, notably ones running on **paid lead-gen
  and subcontractors** — the leads carry **ad-source attribution** (Yelp, HomeAdvisor, Thumbtack,
  Facebook, Referral) and jobs route to **subcontractors** with **commission reports** (kitchen/bath
  remodel, HVAC, electrical, plumbing).
- **Modules (from the nav):** *Communication* — Dashboard · Conversations · Emails · Calls · SMS
  History; *Management* — Leads · Leads Map · Callback Tickets · Clients · Tasks · Estimates ·
  Appointments · Agent Schedule; *Reports* — Call · Statistic · Commission · Lead · Payments.
- **Standout capabilities:**
  - **Leads pipeline** with a full status flow (Created → Sent → In Progress → Appointment → Estimate
    → Deposit → Follow Up), ad-source, location, subcontractor — plus a **Leads Map**.
  - **Unified comms inbox + built-in phone dialer** (calls/texts/voicemail/team chat in one screen).
  - **AI:** *AI Generate* estimates; AI call-answering ("when you can't pick up").
  - **Dashboard:** revenue trend, leads-by-status donut, call activity, **Top Subcontractors by sales**.
  - Estimates with line items (labor/materials, qty/price/disc/tax), appointments with a **copy
    booking link**.
- **Its angle / strength:** *never miss a lead* — consolidating every call/text/voicemail, tracking
  lead-source ROI, and managing subcontractors. Strong on **demand capture & communications**.
- **The seam (where we differ):** it's **office/desktop- and CRM/inbox-first** — these screens show
  little **field-technician mobile execution or offline**, and not the equipment/service-history/
  service-agreement depth of ServiceTitan. Its **subcontractor + paid-lead** flavor suits lead-gen
  remodelers more than in-house service-trade crews. So our **technician-mobile, offline wedge**
  stands — but Joby exposes a real gap on *our* side: a strong **leads + unified-comms front end**
  (see [§6 white space](#6-white-space--where-an-experience-led-entrant-wins)).

Screens: [leads](assets/joby-leads.jpeg) · [schedule](assets/joby-schedule.jpeg) ·
[dashboard](assets/joby-dashboard.jpeg) · [estimates](assets/joby-estimates.jpeg) ·
[conversation](assets/joby-conversation.jpeg).

### Swivl — the AI-forward small-shop challenger

- **Identity (high confidence):** swivl.tech ("Swivl Tech"), founder Rob Heller (built/sold a
  plumbing business). Distinct from the Swivl classroom-camera company and swivl.ai (self-storage).
  *Funding figures unverifiable — database records are contaminated by other "Swivl" entities.*
- **Positioning:** "an AI-powered operating system built for the millions of home and field service
  businesses that have been **ignored by enterprise software**" — the explicit anti-ServiceTitan.
- **Scope:** CRM, scheduling/dispatch, estimating, invoicing, payments, QuickBooks, GPS, mobile.
  AI: **AI Receptionist** (books jobs while you're in the field), **AI estimating** (profit-checked
  before you send), **AI website builder**.
- **Pricing:** **free "forever" tier**; paid from **~$25/mo + usage** (250 SMS, GPS, AI
  receptionist; receptionist $0.18/min after 25 free min). No contracts.

Sources: [swivl.tech](https://swivl.tech/), [swivl.tech/about](https://swivl.tech/about),
[swivl.tech/pricing](https://swivl.tech/pricing/).

### Hubstaff — adjacent: the surveillance archetype (what *not* to be)

- **What it is:** workforce **time-tracking + productivity/GPS monitoring**, not a full FSM. 112,000+
  teams. Features: timesheets, payroll, GPS + geofencing (auto-start timers at job sites), breadcrumb
  route trails, app/URL monitoring, **periodic screenshots**, scheduling, invoicing, 30+ integrations.
  It overlaps FSM only on **time/GPS/scheduling** — there's no dispatch board, proposals, customer
  portal, or service agreements.
- **Pricing:** **$7–$25/user/mo** (GPS on the ~$9 "Grow" tier); 2 months free annual — cheap, because
  it's a point tool, not a platform.
- **Positioning:** employee monitoring / "see where your team is in real time," "military-grade GPS."
- **Why it matters to us — it's the anti-pattern.** Hubstaff is the **surveillance-first** approach our
  [trust-first stance](../15-transparency-and-control.md) is built against, and the reviews are the
  evidence: surveillance "creates trust issues, decreased morale, and a culture of micromanagement";
  **1 in 3 employees say monitoring has hurt their mental health**; screenshots/webcam capture feel
  invasive; and the **Android app is ~3.1★** (a real problem for field teams on Android). A shop that
  bolts Hubstaff onto its techs is exactly the resentment we avoid — we make tracking *serve* the tech
  and customer, never spy on them.

Sources: [timetrackreviews](https://www.timetrackreviews.com/reviews/hubstaff.html),
[connecteam review](https://connecteam.com/reviews/hubstaff/),
[trackingtime: is Hubstaff invasive](https://trackingtime.co/is-hubstaff-invasive),
[Hubstaff monitoring stats](https://hubstaff.com/blog/employee-monitoring-statistics/).

### Generic work-management tools (Infinity, ClickUp, Notion, Monday) — the "build-it-yourself" alternative

- **What they are:** horizontal, **customizable work platforms** — not FSM. Infinity, for example, is a
  "customizable work management platform" with **six views of the same data** (Table, Kanban, List,
  Calendar, Gantt, Form) plus templates, automations, forms, and AI recommendations, from **~$6 for 5
  users/mo** ([startinfinity](https://startinfinity.com/features), [GetApp](https://www.getapp.com/project-management-planning-software/a/startinfinity/)).
- **Why it matters:** some shops run their business on these (or Notion/spreadsheets) *instead of*
  FSM — part of the [~45% on manual/general tools](#2-the-digitization-gap-why-now). They're cheap and
  flexible, which is genuinely appealing.
- **Two takeaways for us:**
  1. **Inspiration — multiple views, one dataset.** Showing the *same jobs* as a list, a board, a
     calendar, and a map is a powerful, expected pattern. We adopt it (see
     [IA: multiple views](../03-information-architecture.md)).
  2. **Caution — generic = you build it yourself.** These tools have **no domain fit**: no dispatch
     board, no payments, no equipment/service history, no offline field app, no proposals or
     agreements. You assemble your own structure from blank blocks. **Our edge:** configurable like
     them, but **purpose-built for the trades with sensible defaults** — a shop is running *its*
     workflow on day one, not designing one from scratch.

**All-in-one business suites (PMSuite, Zoho One, Odoo, Bitrix24) — "replace your whole stack."** A
sibling category: suites that bundle **HR · CRM · Finance · Projects · Workspace** as modules, each
module a "product" with its own tools (e.g. PMSuite's "HR & People → Hiring · Payroll · Benefits ·
Leave · Admin"), sometimes sold as a **lifetime deal** ($49 once). Useful in two ways: (1) they model
the exact **platform → products → capabilities** shape we use ([product map](../20-ecosystem-and-self-improvement.md)),
and (2) they're the *horizontal* version of the bet — broad but shallow, and **not built to run a
field-service business** (no dispatch, no field app, no equipment history, no on-site payments). Our
bet is the *vertical* one: the same all-in-one consolidation, but deep where the trades actually work.

---

## 4. The AI-native wave (the fast-moving new front)

The newest competition isn't "prettier FSM" — it's **AI agents handling the inbound call and the
estimate**. This reframes the experience bar and is where venture money is flowing:

| Player | Angle | Funding/traction |
|---|---|---|
| **Avoca AI** | "AI workforce" — agents take inbound calls, schedule, follow up, dispatch | **$125M+ at ~$1B valuation** (Apr 2026); 8-figure ARR |
| **Netic** | AI that executes whole workflows autonomously (outreach, booking, marketing) | **~$43M** (Founders Fund, Greylock; angels incl. Dylan Field) |
| **Quantra** | "AI-first mobile platform, 26 interconnected systems," desktop-free, 1–50 employees | ~$129/mo all-in |
| **FieldCamp** | AI-first FSM; intelligent dispatch (claims 96% scheduling-time cut) | — |
| **Fieldproxy** | "AI-tailored" FSM configured "in days not months"; autonomous CSR/dispatch agents | 450+ teams |

**Implication for us:** AI voice/agent capability (an AI receptionist that books into the same Job
object) is becoming **table stakes**, not a differentiator. Our edge has to be the *experience and
data spine* the AI runs on — and AI woven natively into the technician/dispatcher loop, not bolted
on as a call-center product. (Also note the mis-attribution trap: the Inc.com "AI superpowers for
HVAC" article is about **Netic**, not Swivl.)

Sources: [Avoca $125M](https://www.prnewswire.com/news-releases/avoca-raises-125m-at-1b-valuation-to-power-americas-services-economy-with-ai-302753962.html),
[Netic](https://techfundingnews.com/netic-ai-raises-23m-for-plumbers-roofers-home-services/),
[Quantra](https://quantrahq.com/servicetitan-vs-quantra-ai-first-contractors-2026/),
[Fieldproxy](https://www.fieldproxy.ai/).

---

## 5. Pricing comparison

| Product | Entry | Mid | Top | Per extra seat | Payments | Onboarding | Contract |
|---|---|---|---|---|---|---|---|
| **ServiceTitan** | ~$245/tech/mo (Starter)* | ~$300–400/tech/mo | ~$400–500+/tech/mo (The Works) | per-tech | ~3% cards *(neg.)* | **$5K–$50K**, 12–16 wks | 12-mo min; steep ETF |
| **Jobber** | $39/user/mo (Core) | $119 (Connect) / $199 (Grow) | $599 (Plus) | +$29/user/mo | 2.9%+30¢ / 1% ACH | days, self-serve | monthly/annual |
| **Housecall Pro** | $59/mo (Basic, 1 user) | $149 (Essentials, ≤5) | $299–329 (MAX) | +$35/user/mo (MAX) | from 2.59% / 1% ACH | days | monthly/annual; cancel friction |
| **Swivl** | **Free** | ~$25/mo + usage | usage-based | — | yes | self-serve | none |

\* All ServiceTitan figures are user-reported; pricing is unpublished.

**Pattern:** the market runs from "free + usage" (Swivl) to "$50K to even start" (ServiceTitan).
The two loudest pricing complaints across the category are **add-on creep** (Housecall Pro, ST) and
**lock-in / termination fees** (ST). Transparent, all-inclusive, no-lock-in pricing is itself a
differentiator.

---

## 6. White space — where an experience-led entrant wins

Each opportunity is tied to evidence from user sentiment (see Sources). The pains behind these are
catalogued, scored, and tracked in the [User Pain Points Registry](user-pain-points.md).

1. **Truly offline-first, not "offline-ish."** ~20% of jobs hit dead zones; incumbents (incl. ST)
   silently lose photos/notes/signatures and can erase unsynced data. A locally-authoritative model
   with conflict-aware sync and a **zero-data-loss guarantee** is a hard, defensible wedge.
2. **The "under-30-second job."** Techs reject apps with too many screens and data entry. Win on
   tap-count, voice-to-text, pre-filled/adaptive forms, and role-based screens — exactly where ST's
   redesign regressed and where Jobber/HCP earn loyalty.
3. **Day-not-quarter onboarding, zero implementation fee.** ST's 12–16 wk / $5K–$50K setup is a top
   complaint. Self-serve, template-driven setup + transparent flat pricing attacks it directly.
4. **Honest, all-inclusive pricing, no lock-in.** "Cost creep from add-ons" (HCP #1 complaint; ST
   too) and punitive ETFs make bundled, month-to-month pricing a clean trust differentiator.
5. **Performance as a feature — fast on cheap Android too.** HCP's 3.2★ Android vs 4.5★ iOS gap and
   "updates slow it down" show field reliability is unmet. Native-quality speed is felt daily.
6. **Trust-first, not surveillance-first.** 23% of monitored workers feel watched; heavy tracking
   degrades morale *and* data quality. An explicitly tech-respecting model improves both adoption
   and data accuracy — a win owners also benefit from.
7. **A dispatcher cockpit with reliable real-time state.** Double-booking and stale visibility
   persist even on premium tools. A dense, conflict-preventing board with trustworthy live status
   addresses under-served office-side pain.
8. **Multi-industry flexibility without the rigidity tax.** The market forces a choice between
   trade-specific tools and "fully customizable" platforms. A configurable core that adapts per
   trade without a per-vertical rebuild is genuine white space.
9. **AI woven into the loop, not bolted on.** With Avoca/Netic making AI voice table stakes, the
   differentiator is AI that lives *inside* the technician and dispatch experience on a clean data
   spine — not a separate call-center product.

Sources: [offline/dead-zones](https://mobile.wednesday.is/writing/offline-sync-mobile-apps-field-teams-dead-zones-2026),
[under-30-sec forms](https://www.repair-crm.com/2026/05/30/digital-forms-for-service-technicians-a-2026-guide-for-small-field-teams),
[surveillance sentiment](https://www.fieldservicely.com/blog/how-to-track-field-employees-without-micromanaging),
[double-booking](https://www.fieldproxy.ai/blog/fix-double-booking-issues-service-scheduling-guide).

---

## 7. Biggest risks for a new entrant

1. **Switching costs & data gravity.** Years of customer history, pricebooks, integrations. Import/
   migration must be effortless or trials stall.
2. **Simplicity vs. depth tension.** The same buyers who want simple also demand payments,
   marketing, financing, reporting, QuickBooks, memberships. This tension is what dragged ST into
   complexity — staying simple *and* complete-enough is the central product challenge.
3. **Offline-first is genuinely hard.** Conflict resolution and zero-data-loss sync are *why*
   incumbents fail here — a differentiator because it's difficult, which means real execution risk.
4. **Conservative, word-of-mouth buyers.** Tradespeople distrust "another software" and ask "will
   they exist in 3 years?" Brand and peer proof matter as much as features.
5. **Incumbent response.** Well-funded incumbents (and the AI wave) can copy UX wins, bundle, or
   discount to defend accounts; ST has aggressive sales.
6. **Payments/financial-services moat.** Much incumbent stickiness and revenue is embedded payments/
   financing/marketing, not the core app. UX alone, without a payments story, limits monetization
   and retention.
7. **Breadth dilutes depth.** Serving many trades risks being "good for none"; trade-specific
   incumbents (FieldEdge, etc.) can out-specialize on vertical workflows.

---

## 8. What this means for our product

The research **confirms and sharpens** the strategy:

- **The wedge is right.** "Win the technician's daily loop" maps directly to the two biggest,
  best-evidenced seams: mobile/offline failure and data-entry friction. This is the most defensible
  place to attack.
- **Offline-first is non-negotiable and must be real** (zero-data-loss), not a checkbox — it's both
  the clearest white space and the hardest thing, so we treat it as a first-class engineering bet
  ([Architecture](../07-technical-architecture.md)).
- **Pricing is a strategic weapon:** transparent, all-inclusive, no-lock-in, fast self-serve
  onboarding — the inverse of ServiceTitan, and cleaner than Housecall Pro's add-on creep. This
  feeds the [pricing model in the strategy](../01-product-strategy.md).
- **AI is table stakes on the inbound side** (receptionist/booking) — we must have a credible AI
  story, but our durable edge is the experience + data spine, with AI woven into the technician and
  dispatch loops rather than sold as a separate call center.
- **Multi-industry flexibility is validated white space** — our configurable, industry-agnostic
  object model ([IA](../03-information-architecture.md)) is the right structural bet.

These conclusions flow into the refreshed [Product Strategy](../01-product-strategy.md), the
[PRD](../09-prd.md), and the [user flows](../04-core-workflows.md) / [edge cases](../10-edge-cases.md).

---

## Full source list

**Market & trends:**
Grand View, MarketsandMarkets, Fortune Business Insights, Mordor, GM Insights, BuildOps;
[Gartner Digital Markets](https://www.gartner.com/en/digital-markets/insights/stand-out-in-your-category-with-construction-buyer-insights),
[electroiq/QuickBooks](https://electroiq.com/stats/quickbooks-statistics/),
[FieldCamp missing-middle](https://fieldcamp.medium.com/the-missing-middle-why-80-of-field-service-businesses-are-underserved-0978a3fe40c3),
[JLL trades shortage](https://www.jll.com/en-us/newsroom/critical-skilled-trades-shortage-threatens-economic-losses),
[devprojournal (autonomy)](https://www.devprojournal.com/market-trends/field-service/field-service-software-in-2026-moving-from-automation-to-autonomy/),
[servicepower (self-service)](https://www.servicepower.com/blog/field-service-and-the-age-of-consumer-self-service).

**ServiceTitan:**
[company](https://www.servicetitan.com/company), [features](https://www.servicetitan.com/features),
[FY26 results](https://investors.servicetitan.com/news-releases/news-release-details/servicetitan-announces-fiscal-fourth-quarter-and-full-fiscal),
[IPO/CNBC](https://www.cnbc.com/2024/12/12/servicetitan-starts-trading-on-nasdaq-after-ipo.html),
[G2](https://www.g2.com/products/servicetitan/reviews), [Capterra](https://www.capterra.com/p/150053/ServiceTitan/),
[getonecrew](https://www.getonecrew.com/post/servicetitan-reviews),
[fieldcamp](https://fieldcamp.ai/reviews/servicetitan/),
[ST Community offline](https://community.servicetitan.com/t5/Mobile/Offline-Synching-Issues/m-p/24503).

**Jobber / Housecall Pro:**
[tekpon Jobber pricing](https://tekpon.com/software/jobber/pricing/),
[Jobber 100k](https://www.prnewswire.com/news-releases/jobber-surpasses-100-000-customers-cementing-its-position-as-the-market-leading-platform-for-home-and-commercial-service-businesses-302768759.html),
[Jobber AI Receptionist](https://www.getjobber.com/features/ai-receptionist/),
[projul HCP pricing](https://projul.com/blog/housecall-pro-pricing-analysis-2026/),
[HCP about](https://www.housecallpro.com/about/),
[HCP fall-2025 AI](https://www.prnewswire.com/news-releases/housecall-pro-unveils-major-ai-powered-updates-for-fall-2025-302594189.html),
[checkthat HCP](https://checkthat.ai/brands/housecall-pro/reviews),
[contractortoolstack](https://contractortoolstack.com/software/housecall-pro/).

**Swivl & AI-native wave:**
[swivl.tech](https://swivl.tech/), [swivl about](https://swivl.tech/about), [swivl pricing](https://swivl.tech/pricing/),
[Avoca $125M](https://www.prnewswire.com/news-releases/avoca-raises-125m-at-1b-valuation-to-power-americas-services-economy-with-ai-302753962.html),
[Netic](https://techfundingnews.com/netic-ai-raises-23m-for-plumbers-roofers-home-services/),
[Quantra](https://quantrahq.com/servicetitan-vs-quantra-ai-first-contractors-2026/),
[Fieldproxy](https://www.fieldproxy.ai/).

**User sentiment / white space:**
[getonecrew ST](https://www.getonecrew.com/post/servicetitan-reviews),
[offline dead-zones](https://mobile.wednesday.is/writing/offline-sync-mobile-apps-field-teams-dead-zones-2026),
[repair-crm forms](https://www.repair-crm.com/2026/05/30/digital-forms-for-service-technicians-a-2026-guide-for-small-field-teams),
[fieldproxy double-booking](https://www.fieldproxy.ai/blog/fix-double-booking-issues-service-scheduling-guide),
[fieldservicely surveillance](https://www.fieldservicely.com/blog/how-to-track-field-employees-without-micromanaging),
[memtime micromanagement](https://www.memtime.com/blog/is-time-tracking-micromanagement).
