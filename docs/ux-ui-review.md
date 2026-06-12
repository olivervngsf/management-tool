# UX/UI Review & Gap Analysis

A design-lead review of the full documentation set as of 2026-06-12. Purpose: confirm the
foundation is coherent and surface **what's still missing from a UX/UI standpoint** before any
screens are designed. Think of this as the "did I miss anything?" checklist.

**Verdict:** The *strategic and structural* foundation is strong and internally consistent. The gap
is the **execution layer of UX/UI** — screens, states, content, and accessibility detail — which is
expected (this was a docs-first pass) but should be filled before/with prototyping. Priorities below.

---

## 1. Coherence check — what's in good shape ✅

| Check | Result |
|---|---|
| All internal doc links resolve | ✅ No broken links across README + all docs |
| Personas consistent across docs | ✅ Same 5 people (Tech/Dispatch/Owner/Admin/Customer) in IA, flows, edges, PRD |
| Strategy → PRD traceability | ✅ Goals (G1–G6) and metrics trace to requirements and edge cases |
| Principles → requirements | ✅ The 10 principles appear as design rules *and* NFRs |
| Research → strategy grounding | ✅ Pricing, white space, risks all cite the research |
| Object model used consistently | ✅ Customer→Property→Job→Visit spine holds in IA, flows, edges, PRD |
| Design tokens single-source | ✅ tokens.json drives the documented pipeline |

No contradictions found. The numbering has one cosmetic quirk (the design system is `06` but lives
in a folder, not `06-design-system.md`) — harmless, the README handles it.

---

## 2. Gap analysis — the missing UX/UI artifacts

Ordered by priority. **P1 = needed before/with the first prototype; P2 = before build; P3 = before GA.**

| # | Missing artifact | Pri | Why it matters | What it should contain |
|---|---|:---:|---|---|
| G1 | **Screen inventory / sitemap** | P1 | We have navigation, not a complete list of every screen. You can't design or estimate what isn't enumerated | Every screen per app (mobile/desktop/customer), its purpose, entry points, and which flow/persona it serves |
| G2 | **Wireframes / lo-fi layouts** | P1 | The biggest "UX/UI" gap — words describe flows, but nobody has *seen* a screen. The technician Job screen and the dispatch board especially | Lo-fi layouts for the ~10 critical screens, annotated with the primary action and key states |
| G3 | **Screen state catalog** | P1 | The DS lists component states; no screen says what its empty / loading / error / **offline** / permission-restricted states look like. This is where field apps fail | Per critical screen: default, empty, loading, error, offline/syncing, no-permission, success |
| G4 | **UX writing / voice & tone guide** | P1 | Principle 10 promises a humane, respectful tone but there's no guide. Microcopy *is* the experience for a stressed tech | Voice principles, button-label conventions, error-message formula, empty-state copy, notification tone, terminology glossary (per-trade vocab) |
| G5 | **Onboarding / first-run UX** | P2 | "Live the same day" (G5) is a core promise with no designed flow. Empty account = first impression | Admin setup wizard (Alex), first-job walkthrough (Maria), data-import UX, empty states for a brand-new account |
| G6 | **Accessibility spec & checklist** | P2 | Principle 9 + NFR4 commit to WCAG 2.2 AA but there's no concrete checklist to design/test against | Contrast targets, Dynamic Type behavior, VoiceOver/TalkBack labeling rules, focus order, touch-target audit, reduced-motion, sunlight/glove conditions |
| G7 | **Interaction & gesture spec** | P2 | Motion is defined; gestures aren't. The board is drag-driven; mobile needs swipe/long-press/pull-to-refresh | Gesture inventory per platform, drag-and-drop rules, haptics, keyboard shortcuts (desktop `⌘K` and beyond) |
| G8 | **Notification & communication UX** | P2 | "Quick communication" is your stated goal; Flow 5 covers customer comms but there's no notification matrix | Every notification: trigger, channel (push/SMS/email), recipient, copy, timing, frequency caps, opt-down |
| G9 | **Responsive breakpoints & layout grid** | P2 | DS says "mobile-first → desktop density" without defined breakpoints or the desktop grid | Breakpoints, column grid, how the board and lists reflow, tablet handling (techs use tablets) |
| G10 | **Form design patterns** | P2 | The "under-30-second job" depends on form craft, which has no pattern spec | Field types, smart defaults, voice/photo input, inline validation, autosave behavior, adaptive forms per JobType |
| G11 | **Data-viz guidelines (Owner's Home)** | P3 | Sofia's home has "numbers and tiles" but no charting standards; trust depends on legible, honest data | Chart types, number formatting (`MoneyDisplay`), trend/comparison conventions, "reconciles to the penny" display rules |
| G12 | **Localization / i18n plan** | P3 | Customer language is noted (edge G4) but there's no i18n strategy | String externalization, RTL readiness (DS mentions it), date/currency/units, per-region tax display |
| G13 | **Design QA / review checklist (artifact)** | P2 | Principle doc says screens are "scored against all ten" — but the scoring sheet doesn't exist | The reusable checklist in §4 below, formalized into the review process |
| G14 | **Prototype / clickable flow** | P1 | The Phase-0 exit gate per the roadmap; the real test of all the above | Clickable technician Job flow + dispatch board (Figma or coded) |

---

## 3. Smaller consistency nits (low effort to fix)

- **Numbering:** design system is referenced as `06` but is a folder. Optional: add a one-line
  `docs/06-design-system.md` pointer, or just leave it (README disambiguates). *Cosmetic.*
- **Tablet persona:** techs often use tablets (research notes ST's app is tablet-optimized). Our IA
  is phone-first; we should explicitly state the tablet stance (G9) rather than leave it implicit.
- **AI surfaces:** AI is in strategy/PRD/scorecard but has no home in the IA or flows yet — once AI
  scope is decided, it needs to appear as concrete UI (where does the AI receptionist's booking land?
  where does voice-to-structured-notes live on the Job screen?).
- **Glossary:** per-trade vocabulary (the flexibility thesis) deserves a single terminology source
  (fold into G4).

None of these block progress; they're polish.

---

## 4. Bonus: the Design Review Checklist (use on every screen)

Formalizes "scored against all ten principles" ([doc 05](05-design-principles.md)) into a usable
gate. A screen ships only when every box is honestly checked or the exception is recorded.

- [ ] **1. Clarity** — every element serves the task; nothing decorative survived the edit
- [ ] **2. Deference** — the user's content (job, customer, photo) is the hero, not chrome
- [ ] **3. One primary action** — the biggest, most obvious thing is the right next step
- [ ] **4. Speed** — optimistic UI; < 100ms perceived; skeletons not spinners
- [ ] **5. Forgiving** — undo present; autosave; destructive actions gated
- [ ] **6. Progressive disclosure** — surface simple, depth on demand; density matched to role
- [ ] **7. Thumb/glove/sun** — targets ≥ 44pt; primary action in thumb zone; high contrast
- [ ] **8. Trustworthy** — numbers/status/ETA true and current; sync state honest
- [ ] **9. Consistent & accessible** — patterns reused; WCAG 2.2 AA; color never the only signal
- [ ] **10. Humane tone** — copy talks to a skilled pro; errors explain + offer a way forward
- [ ] **States covered** — default / empty / loading / error / **offline** / no-permission / success
- [ ] **Edge cases** — the relevant cases in [doc 10](10-edge-cases.md) have defined behavior

---

## 5. Recommended next moves (UX/UI)

In order, to convert this strong foundation into something you can *see and feel*:

1. **G1 Screen inventory** — fast, unlocks everything else (half a day).
2. **G2 Wireframes** of the 10 critical screens — the technician Job flow + the dispatch board first.
3. **G3 State catalog** + **G4 voice/tone guide** — in parallel with wireframing; they shape it.
4. **G14 Clickable prototype** — the Phase-0 exit gate; put it in front of a real shop owner.
5. Then **G5–G10** as the prototype firms up.

> Bottom line: you didn't miss anything *strategically* — the thinking is complete and coherent.
> What's left is the **craft layer**: turning these well-reasoned words into screens, states, and
> words-on-buttons. That's the next phase, and this list is its backlog.
