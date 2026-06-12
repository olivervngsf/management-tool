# 06 · Design System — "Fieldwork DS"

The design system is how the [principles](../05-design-principles.md) become the default. It is the
shared language between the Next.js web app and the React Native (Expo) mobile app, and the reason
two platforms can feel like one product.

> **Single source of truth:** design tokens are defined once, in a platform-agnostic format
> ([`tokens.json`](tokens.json)), and compiled to CSS variables (web) and a TypeScript theme
> object (React Native). A color or spacing change happens in one place and lands everywhere. See
> [Technical Architecture](../07-technical-architecture.md) for the build pipeline.

---

## Design language: "calm instrument"

Fieldwork should feel like a precise tool that gets out of the way — closer to the iOS Camera or
Apple Wallet than to a dashboard. Restrained color, confident type, real depth through layering and
motion rather than ornament. The trade is the hero; the UI is the well-made handle.

---

## Foundations

### Color

A restrained system. One brand/action color carries intent; the rest is a calm neutral scale.
Semantic colors are reserved for true meaning (success, warning, danger, info) and never used
decoratively.

| Token | Light | Purpose |
|---|---|---|
| `brand/primary` | `#0A84FF` | Primary actions, active states (an iOS-system-blue lineage — trustworthy, not trendy) |
| `neutral/0…1000` | white → near-black | Surfaces, text, borders — the calm canvas |
| `success` | `#34C759` | Paid, completed, on-track |
| `warning` | `#FF9F0A` | Running late, attention needed |
| `danger` | `#FF3B30` | Overdue, failed, destructive actions |
| `info` | `#5E5CE6` | Neutral system notices |

Rules: color is never the *only* signal (principle 9). Full dark mode is a first-class theme, not
an afterthought — field techs work at night and in dark mechanical rooms. Every semantic color
passes AA contrast on its surface.

### Typography

System fonts for native feel and zero load cost: **SF Pro** on Apple, **Roboto** on Android,
system stack on web. A single modular type scale shared across platforms.

| Token | Size / Line | Use |
|---|---|---|
| `display` | 34 / 41 | Big numbers on the owner's home |
| `title1` | 28 / 34 | Screen titles |
| `title2` | 22 / 28 | Section headers |
| `headline` | 17 / 22 semibold | Card titles, the primary line of a row |
| `body` | 17 / 22 | Default reading text |
| `callout` | 16 / 21 | Secondary content |
| `subhead` | 15 / 20 | Supporting detail |
| `footnote` | 13 / 18 | Metadata, timestamps |
| `caption` | 12 / 16 | Labels, the smallest legible text |

Dynamic Type / text scaling is fully supported — layouts reflow, never clip, when a user sizes up.

### Spacing & layout

A strict **4-point grid** (`4, 8, 12, 16, 20, 24, 32, 40, 48, 64`). Consistent rhythm is most of
what makes a layout feel "designed." Touch targets are never below **44pt**. Safe areas (notch,
home indicator, keyboard) are respected on every mobile screen.

### Radius, elevation, depth

- Radius scale: `8 / 12 / 16 / full`. Soft, modern, consistent.
- Depth comes from **layering and subtle shadow**, not heavy borders — content sits on calm
  surfaces that lift on interaction. Sheets and popovers cast real, soft shadows; flat chrome does
  not.

### Motion

Motion communicates causality and spatial model; it is never decoration.

- **Fast and interruptible.** 200–300ms, spring-based easing that feels physical (iOS-like).
- **Meaningful.** A sheet rises from where you tapped; a completed job settles with a confident
  check. Motion answers "where did that go / where did this come from."
- **Respectful.** Honors `prefers-reduced-motion` — falls back to a simple fade.
- **Never blocking.** Animation never makes the user wait; it plays over already-actionable UI.

### Iconography

One coherent set (SF Symbols lineage on Apple; a matched custom/Lucide set on web/Android for
parity). Icons are always paired with a label in primary navigation — never icon-only where meaning
must be unambiguous.

---

## Component library

Built **mobile-first**, then composed up to desktop density. Each component ships with: all states
(default / pressed / disabled / loading / error / empty), full accessibility, light + dark, and
right-to-left readiness.

**Primitives** — `Button` (primary/secondary/tertiary/destructive), `TextField`, `Select`,
`Toggle`, `Checkbox`, `Stepper`, `SegmentedControl`, `Badge`, `Avatar`, `Icon`, `Chip`.

**Surfaces** — `Card`, `Sheet` (the mobile workhorse — actions rise from the bottom),
`Popover` (desktop), `Modal` (reserved for the genuinely blocking), `Toast`, `Banner`.

**Patterns (composed, product-specific)** —
- `JobCard` — the atom of the dispatch board and the technician's list; one design, multiple
  densities.
- `StatusPill` — the canonical job/payment state indicator; color **and** label, everywhere.
- `LineItemRow` — used identically in estimate, invoice, and price book.
- `Timeline` — the job's activity history (notes, photos, status changes).
- `MoneyDisplay` — the single, trusted way to render currency, so totals look and reconcile
  identically across the product.
- `ScheduleLane` / `BoardCard` — the dispatch board instrument.
- `SignaturePad`, `PhotoCapture`, `VoiceNote` — the field-capture trio.

**Rule:** product screens are assembled from these patterns, not from raw primitives. When a screen
needs something the library lacks, we add it to the library — screens never grow private one-offs.
This is what keeps two platforms and five roles feeling like one product over time.

---

## Cross-platform parity

| Concern | Web (Next.js) | Mobile (Expo) | Shared |
|---|---|---|---|
| Tokens | CSS variables | TS theme object | ✅ `tokens.json` source |
| Type scale | same scale | same scale | ✅ |
| Components | React (web primitives) | React Native | API-compatible props, platform-right rendering |
| Motion | CSS / Framer Motion | Reanimated | same durations & curves |

We do **not** force pixel-identical UIs — we force a **consistent system** rendered natively on each
platform. A button is a real iOS button on iOS and a proper web button on web; both obey the same
tokens, scale, and behavior. Native-right, system-consistent.

See [`tokens.json`](tokens.json) for the starting token set that seeds the build pipeline.
