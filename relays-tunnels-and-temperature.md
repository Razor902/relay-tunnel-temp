# Relays, Tunnels, and Temperature

**DRAFT / GATHERED — not a finished device, not a proven product.**
**Status:** concept document, plain language, for Curtis's review and testing.

> Curtis's words, 2026-10-28: "Its all about the relays and tunnels and temperature."

This document describes one idea in three levers that have to agree with each
other: relays choose the path, tunnels cross the barrier, and temperature
sets the noise. If any one of the three is wrong, the signal is lost, even
if the other two are right.

---

## 1. The idea in one paragraph

A signal travels around a laser relay circle. A relay switches it from one
route to another without breaking the whole system. At the heart of the
system sits a silicon disc. Inside that disc, the signal does not climb
over an energy barrier. It tunnels through it, the way a wave passes
through a thin wall. Heat is the enemy of that clean signal: too warm, and
ordinary thermal current and leakage swamp the tunneling current, so you
can no longer tell what you are measuring. Keep the temperature where
tunneling beats thermal leakage, keep the relay path clean, keep the
barrier thin and uniform, and the current-versus-voltage curve will tell
you whether the device works. The curve is the judge, not the idea.

---

## 2. Lever one: relays choose the path

### The laser relay circle

- A circular **blue tube** forms the outer ring.
- A **red tube** and a **yellow tube** cross in the middle, like an X
  through the center of the circle.
- The tubes are color-coded lasers: blue is the ring, red is one crossing
  route, yellow is the other crossing route.
- A relay is a switch. It moves the signal from the ring onto a crossing
  tube, or from a crossing tube back onto the ring, without cutting the
  system apart.

### What a relay must do

1. Switch cleanly. No half-open state that leaks signal down two paths
   at once.
2. Switch without breaking the rest of the system. The ring keeps working
   while one route changes.
3. Report its state. At any moment, it must be plain which path is live:
   blue ring, red tube, or yellow tube.
4. Fail safe, not fail open. If a relay loses power or control, it must
   fall into a known, safe state, not an unknown one.

### Relay switch points

The blueprint marks four switch points where the crossing tubes meet the
ring, plus the center crossing where red meets yellow. On the blueprint
these four switch points are labeled S1, S2, S3, and S4. Each switch point
is a place where the path can be chosen, and a place where a bad switch
can lose the signal. Test each point on its own before testing the
whole circle.

---

## 3. Lever two: tunnels cross the barrier

### Tunneling, in plain language

At the everyday scale, a ball cannot roll through a hill. It has to go
over the top. At the quantum scale, a particle is also a wave, and a
little of that wave reaches the other side of a thin barrier. That is
quantum tunneling. It is not a leak in the everyday sense. In this
concept, tunneling is the device itself: the way current is meant to
move.

### The silicon disc tunneling stage

- The tunneling stage is a **silicon disc**.
- Inside the disc, the signal meets a barrier only **atoms thick**.
- Whether tunneling can happen, and how much current flows, is decided
  by two things:
  - **Barrier thickness.** Thinner means more tunneling current.
    The current falls off fast as the barrier gets thicker, roughly
    exponentially, so a barrier that is a few atoms too thick can kill
    the signal.
  - **Bandgap and band alignment.** Different materials have different
    energy bands. How those bands line up across the barrier sets the
    height the particle has to tunnel through. Lower and better-aligned
    means more tunneling; misaligned means less.

### Background material swaps

These swaps come from Curtis's earlier thread. They are background
options for tuning the barrier, not claims about a finished device:

- **Germanium** as an alternative channel material to silicon.
- **III-V materials, indium arsenide with gallium antimonide**, a
  broken-gap pair whose band alignment can favor tunneling.
- **Barrier swap: silicon oxide to hafnium oxide**, changing the
  barrier material and therefore its height and quality.

Each swap changes the same two knobs: barrier height and barrier
quality. None of them, on its own, makes a disc work. The disc works
only if the barrier is thin, uniform, and well aligned, whatever
material it is made from.

### Why tunneling is real, and why this disc is not yet proven

Tunneling as physics is proven and already used: tunnel diodes, flash
memory that writes by tunneling, and microscopes that image atoms using
tunneling current all depend on it. That proves the effect. It does not
prove this specific silicon disc design. A specific disc is proven only
when it is built and measured, and its current-versus-voltage curve
shows the tunneling signature. Until then, this design is GATHERED, not
standing, and this document says so plainly.

---

## 4. Lever three: temperature sets the noise

Heat shakes things up. At higher temperature:

- More particles have enough thermal energy to go over the barrier the
  ordinary way, instead of tunneling through it.
- Leakage current rises.
- Defects and imperfect contacts leak more.

The result is that thermal current can swamp tunneling current. When
that happens, you are no longer measuring tunneling at all. You are
measuring heat leaking through.

At controlled, cooler temperature:

- Thermal current falls.
- The tunneling signature stands out against the background.
- The same disc, with the same barrier, gives a cleaner, more readable
  curve.

Temperature is therefore not a side detail. It is a control knob, and
it decides what the measurement means. The blueprint marks a
temperature control zone around the tunneling stage. In a real build,
that zone is where cooling, insulation, and a temperature sensor live.
In the companion app, temperature is a slider, and you can watch the
thermal leakage rise as temperature rises.

Rules for temperature in this concept:

1. Measure temperature at the disc, not somewhere else in the box.
2. Hold it steady while you sweep voltage. A drifting temperature
   makes a drifting curve, and a drifting curve proves nothing.
3. Record the temperature with every curve. A curve without a
   temperature is an incomplete record.
4. If the tunneling signature disappears when the device warms up and
   returns when it cools down, that is evidence about temperature, not
   proof the disc is broken. Test at more than one temperature before
   judging the disc.

---

## 5. How the three levers work together

1. **Relay** picks the path: blue ring, red tube, or yellow tube.
2. **Tunnel** carries the signal across the barrier inside the silicon
   disc on that path.
3. **Temperature** keeps the background quiet enough that the tunneling
   signal can be seen.

Change one lever and the other two must still hold:

- A perfect disc with a bad relay loses the signal at the switch.
- A perfect relay with a thick or defective barrier gives no tunneling
  current to switch.
- A perfect relay and a perfect disc, run too hot, give a curve full
  of thermal leakage, and the tunneling signal is buried.

The test of the whole concept is therefore a system test, not a test
of one part: relay path set, barrier known, temperature held, voltage
swept, curve read.

---

## 6. Test criteria: the current-versus-voltage curve is the judge

Build, then measure. Do not judge the concept from the drawing.

### Setup

- Set one relay path: blue ring, red tube, or yellow tube.
- Set and record the barrier thickness (in atoms, as built, not as
  hoped).
- Set and hold the temperature at the disc.
- Sweep the voltage across the disc, negative to positive, and record
  the current at each step.

### What a tunneling signature looks like

- Current rises with voltage, but not like an ordinary resistor.
- The shape of the curve changes in a specific way as barrier
  thickness changes: thinner barrier, much more current at the same
  voltage.
- The signature survives when temperature is controlled, and fades
  into thermal leakage when the device is run too hot.
- The same signature repeats on a second sweep, on the same path, at
  the same temperature. A curve that appears once and never again is
  not a result.

### Pass, fail, and inconclusive

- **Pass:** a repeatable tunneling-shaped curve, on a known relay
  path, at a recorded temperature, that changes the expected way when
  barrier thickness changes.
- **Fail:** no repeatable tunneling shape at any tested barrier or
  temperature, or a curve that is explained entirely by leakage,
  shorts, or bad contacts.
- **Inconclusive:** a promising shape that does not repeat, a
  temperature that drifted during the sweep, or a relay path that was
  not recorded. Inconclusive means test again, properly, not that the
  idea is proven or disproven.

### Test each part alone first

1. Relay alone: switch paths, confirm the live path, confirm no
   signal on the off paths.
2. Disc alone: sweep voltage at a fixed, recorded temperature, with
   the relay path fixed.
3. Temperature alone: repeat the same sweep at two or three
   temperatures, and watch thermal leakage rise with temperature.
4. Whole system: relay, disc, and temperature together, with all
   three recorded.

---

## 7. Open decisions

These are not decided in this document. They are questions for Curtis
and for testing, and they must not be filled in by guessing:

1. What is the target barrier thickness, in atoms, for the first disc?
2. Which channel material for the first build: silicon, germanium, or
   an indium arsenide / gallium antimonide pair?
3. Which barrier material for the first build: silicon oxide or
   hafnium oxide?
4. What temperature range is the operating range, and what cooling or
   insulation does that require?
5. What happens at each relay switch point when power or control is
   lost: what is the safe state?
6. What does the relay circle connect to on the outside: what is the
   signal in, and what is the signal out?
7. How is the disc made, and how is barrier thickness verified after
   fabrication, not just designed on paper?

---

## 8. Honest limits

- Tunneling physics is proven. This specific disc design is not.
- A drawing, a document, and an app model are not a device. The app
  in this package shows how the numbers move when you change barrier
  thickness, temperature, and relay path. It is a teaching model with
  simplified numbers, not a simulation of a real fabricated disc.
- Color-coded laser tubes are a design language for the relay circle.
  They are not, by themselves, a working optical relay. Turning the
  drawing into a working relay is a separate build with its own tests.
- No safety, medical, or power-system claim is made here. If this
  concept ever touches real power, real heat, or real people, it needs
  its own safety review, separate from this document.

---

## 9. Companion files in this package

- `relays-tunnels-and-temperature.md` — this document.
- `relay-tunnel-temp-blueprint.svg` — technical blueprint schematic.
- `relay-tunnel-temp-blueprint.pdf` — the same blueprint as a PDF.
- `relay-tunnel-temp.apk` — interactive Android app: switch the relay
  path, slide barrier thickness and temperature, watch tunneling
  current versus thermal leakage, and read a current-versus-voltage
  curve. No internet permission. Not installed by the builder; install
  is Curtis's tap, if he wants it.

---

*DRAFT / GATHERED — concept only, awaiting Curtis's review and testing.*

© Crimson Rose LLC, Curtis Ray Dyess 2026-27
