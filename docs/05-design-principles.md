# 05 · Design Principles

Ten rules. Every screen, in every review, is judged against them. They are how we operationalize
"Apple product standards" and "world class" so those words mean something a designer can act on and
a reviewer can hold the line with.

The north star: **Apple's Human Interface Guidelines applied to operational software.** Clarity,
deference, depth — adapted for people working with gloves on, under time pressure, sometimes with
no signal.

---

### 1. Clarity over decoration

Every element earns its place by serving a task. Content is the interface; chrome recedes.
Generous whitespace, unambiguous typography, and a ruthless edit of anything that doesn't help the
user act. If you can remove it and the task still reads, remove it.

### 2. Deference — the content is the hero

The UI defers to the user's data: the job, the customer, the photo of the broken unit. The
interface is a quiet, confident frame. No gratuitous gradients, no chrome competing with content.
Color and emphasis are spent only where they guide action.

### 3. One primary action per screen

Each screen has a single, obvious next step — large, reachable, unmistakable. Secondary actions are
present but visually subordinate. The technician should never wonder "what do I do here?" The
answer is the biggest thing on the screen.

### 4. Speed is a feature — design for the perception of instant

Sub-100ms perceived response on every primary action. Optimistic UI: act immediately, reconcile in
the background. Skeletons over spinners. Never block the user behind the network. A fast app feels
respectful; a slow one feels broken regardless of why.

### 5. Forgiving by default

People make mistakes on small screens in bad conditions. Undo everywhere. Confirm only the
genuinely destructive. Autosave constantly — the field user never "loses work." Destructive actions
are reversible or clearly gated; nothing irreversible happens by accident.

### 6. Progressive disclosure — depth without clutter

Show what's needed now; reveal complexity on demand. The technician's job screen is simple on the
surface and deep when tapped. The dispatcher's board is dense by design (that's the exception in
principle 1 — for the power user, density *is* clarity). Match information density to the role.

### 7. Designed for the thumb, the glove, and the sun

Mobile-first, literally. Touch targets ≥ 44pt. Primary actions in the thumb zone. High contrast
that survives direct sunlight and a cracked screen protector. Assume one-handed, interrupted,
imperfect conditions — design for the truck, not the studio.

### 8. Trustworthy — especially with money and status

When we show a number, a status, or an ETA, it is *true* and current. Money reconciles. Status
reflects reality. Sync state is honest and visible, never silently wrong. Trust is the entire asset
in operational software; one wrong total and the user stops believing the screen.

### 9. Consistent, learnable, and accessible

The same gesture does the same thing everywhere. Patterns repeat so that learning one screen
teaches the next. Meet WCAG 2.2 AA: color is never the only signal, full dynamic-type/text-scaling
support, VoiceOver/TalkBack labels on every control. Accessible design is just good design under
hard conditions — which is every field condition.

### 10. Humane and respectful in tone

The product talks to a skilled tradesperson as a capable professional, never a child or a suspect.
Empty states encourage, errors explain and offer a way forward, microcopy is plain and warm.
Tracking serves the customer and the team, never feels like surveillance of the tech. Respect is a
design decision made in a hundred small words.

---

## How we enforce these

- **Design reviews** score against all ten, explicitly. A screen that fails one doesn't ship until
  it's resolved or the exception is argued and recorded.
- **The design system** ([06](design-system/README.md)) encodes most of these so they're the
  path of least resistance — the right thing is the easy thing.
- **"Would Apple ship this?"** is a real, repeated question in critique. Not as worship — as a
  calibration bar for craft, restraint, and finish.

## Anti-patterns we refuse

- Enterprise "everything on one screen" dumping (except the deliberately dense dispatch board).
- Modal-stacking and dialog mazes.
- Greyed-out features that tease permissions a user doesn't have (compose to capability instead).
- Tiny tap targets, dense forms, and desktop layouts crammed onto phones.
- Spinners as a substitute for fast, optimistic UI.
- Cute illustration that delays a stressed user from doing their job.

These principles are the contract. The [design system](design-system/README.md) is how we make
keeping it the default.
