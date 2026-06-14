# 18 · Location & Privacy — designing the balance

> The trade-off: the **customer** wants to know exactly when the tech will arrive (transparency); the
> **tech** doesn't want to feel followed all day like a suspect (privacy). Both are right. This is how
> we give the customer full certainty *without* surveilling the employee.

This is the concrete mechanics behind the [tracking bright line](15-transparency-and-control.md) and
the [trust-first stance](research/user-pain-points.md). It's the answer to "ServiceTitan/Hubstaff can
see people on a map all day — how do *we* do it differently?"

---

## The one idea that resolves it

> **Location follows the *job*, not the *person*.**

A customer's ETA only needs the tech's location **while the tech is driving to that customer** —
maybe 15 minutes. It does *not* need to know where the tech is on a break, at lunch, between jobs, or
after the last call. So we collect and share location **only for that en-route window, for that
purpose** — and the rest of the day, location is **off**.

That single rule gives the customer 100% of the transparency they want and removes ~95% of the
surveillance the tech hates. Everything below is built from it.

---

## The location lifecycle (tied to the Visit, not the day)

```
   Idle / between jobs        Tech taps "On my way"        Tech taps/geofences "Arrived"
        📍 OFF        ───────▶   📍 SHARING (en route)   ───────▶   📍 OFF again
   (no one sees you)         customer sees live ETA;            customer sees "Arrived";
                             dispatch sees en-route status      live dot stops
                                                                      │
   Break / lunch / off-shift                                          ▼
        📍 OFF  ◀────────────────────────────────────────────  job continues on site
   (explicit, no tracking)                                      (no live customer tracking)
```

- Location turns **on** at "On my way," **off** at "Arrived." It is **bound to a single trip.**
- Between jobs, on breaks, off-shift → **off**. Not "minimized" — *off*. The tech is not on a map.
- There is **no all-day breadcrumb trail**, and nothing is logged to be used against the tech later.

---

## Who sees what — scoped tightly

| Audience | Sees | When | Never sees |
|---|---|---|---|
| **Customer** | a live ETA + moving dot to *their* address (rideshare-style) | **only during the en-route window of their own appointment** | the tech's location any other time, or near any other customer |
| **Dispatcher** | tech **status** (en route / on site / available / break) + location *for routing/closest-tech* | while on the clock and relevant to dispatching | breaks, off-shift, or a punitive history log |
| **Owner** | aggregate status (who's where on the board) | working hours | a personal movement log of an individual's life |
| **The tech (themselves)** | exactly when location is on, and who can see it | always | — (they're never in the dark about their own tracking) |

The customer's view is the tightest on purpose: **they see *their* tech, for *their* window, then it
ends.** They never get a window into the tech's day.

---

## The tech's controls & guarantees (the anti-spy promise)

1. **Always visible on/off.** A persistent, honest indicator: *"📍 Sharing location · en route to
   Reyes"* while driving; *"📍 Location off"* the rest of the time. The tech is never tracked
   silently.
2. **They can pause.** Need a personal moment mid-route? They can pause sharing; the customer still
   sees an **ETA estimate** (not a live "stopped at the pharmacy" dot). No silent "gotcha" alert fires
   to the boss.
3. **Break / off-shift modes** explicitly stop location. Clocking out = tracking off, guaranteed.
4. **ETA, not a play-by-play.** The customer sees *"arriving ~9:15,"* not every stop, turn, or
   detour. We expose the *promise* (when), not the tech's literal movements. This is the difference
   between a service and surveillance.
5. **They see their own data.** Location serves the tech (routing, fair drive-time on timesheets),
   and the tech can see it — it's not a one-way mirror.
6. **Hard nevers:** no screenshots, no keystroke/app/URL monitoring, no webcam, no off-shift tracking,
   no permanent life-log. (These are exactly the [Hubstaff](research/market-and-competitors.md)
   behaviors we refuse.)
7. **The [private personal layer](16-notes-and-reflection.md) is untouchable** by any tracking.

---

## The customer's experience (full transparency, from their side)

The customer gets *complete* certainty — and it costs the tech almost no privacy:

1. **Confirmation:** "You're booked Thursday 1–3pm with Anytown HVAC."
2. **On the way:** a link opens a live map — tech's name, photo, **"arriving ~1:12pm."** Updates as
   they drive. (Rideshare-grade — this is the delight feature.)
3. **Arrived:** the live dot stops; "Maria has arrived." Tracking ends.
4. **Done:** receipt + summary.

From the customer's seat it feels like Uber. From the tech's seat, location was on for one 15-minute
drive and off the rest of the day. **Both win.**

---

## Why this is the *better* design (not just the nicer one)

- **It's enough for the job.** Dispatch and ETAs genuinely don't need 24/7 location — so collecting
  it is pure downside (resentment, bad data, battery, liability) for zero operational gain.
- **It improves data quality.** Tracking the [research](research/user-pain-points.md) shows surveilled
  workers disengage and the data rots; respected techs keep status honest because the tool helps them.
- **It's a differentiator.** Incumbents *can* surveil; a tech-respecting design is a reason a good
  technician chooses a shop that runs on Fieldwork — feeding the [word-of-mouth flywheel](12-system-layers.md).
- **It's defensible & compliant-friendly.** Purpose-bound, minimized, transparent collection is the
  right side of privacy norms (and regulation) by default.

---

## Design checklist (for the screens)

- [ ] Persistent tech-facing **location indicator** (on/off + who sees it) on the mobile app.
- [ ] Location **starts on "On my way," stops on "Arrived"** — scoped to the Visit ([data model](14-data-model.md)).
- [ ] **Break / clock-out** explicitly disables location.
- [ ] Customer link shows **ETA + live dot only while en route**, then ends.
- [ ] Customer sees **ETA, never a stop-by-stop trail**; pausing keeps an ETA, hides the live dot.
- [ ] A plain-language **"Your location & privacy"** page in the tech app (what's shared, when, with
      whom, and the nevers) — generated from the same [disclosure rules](13-ai-operating-model.md).
- [ ] No background/all-day location; **foreground, en-route only.**

> **The principle in one line:** *the customer sees when you'll arrive; nobody watches how you live.*
> Location is a tool to get the right person there fast and keep a promise to the customer — bound to
> the job, visible to the tech, and off the moment it's done.
