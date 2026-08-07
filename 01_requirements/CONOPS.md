# JBV-01 — Concept of Operations

**This document is implementation-free on purpose.** It says what the aircraft must do, never how
it will do it. No configuration is named anywhere in it. The configuration — tiltrotor,
tailsitter, lift+cruise, tilt-wing, ducted fan — is decided later, in the configuration trade
study. This document must stay true whichever one wins. If a sentence here only makes sense for
one configuration, that sentence is wrong.

Written 2026-08-04. **First version.** Writing this document is expected to show gaps in
`NGO.md`; when it does, `NGO.md` gets updated and this file says so.

---

## 1.0 Introduction

### 1.1 Project description

#### 1.1.1 Background

Today you have to choose. An aircraft that lands anywhere runs its battery down quickly. An
aircraft that flies for a long time needs a runway or launch equipment. Nothing we can buy for
our budget gives both.

JBV-01 exists to not force that choice. Two students, one academic year, our own tools and our
own money.

The need, the goals and the measures of success are in `NGO.md`. They are not repeated here.

#### 1.1.2 Assumptions and constraints

Full list in `NGO.md` section 5 and section 6. The ones that shape this document:

| | |
|---|---|
| Two people, one academic year | C1, C2 |
| €800 total, of which €355 is the first aircraft | C3 |
| Hand tools, 3D printing, soldering. **No laboratory** | C4, C5 |
| Vertical take-off and landing. Configuration open | C10 |
| Visual line of sight at all times, **unaided** | C11 |
| **Maximum 120 m** above the surface | C12 |
| Must remain a **privately built** aircraft — no complete ready-to-assemble kit | C13 |
| Nothing dropped, no dangerous goods | C14 |
| At least one crash and rebuild is planned | C9 |
| **How far we must fly from people and buildings is not yet known** | C16 |

C16 is the one that could change this document. See section 4.0.

### 1.2 Overview of the envisioned system

#### 1.2.1 Overview

JBV-01 is a small uncrewed aircraft. It takes off vertically from an unprepared piece of ground,
climbs to a working height, changes over to flight supported by its wing, flies for as long as it
can, changes back, and lands vertically on the same piece of ground.

It carries nothing but itself and what it needs to fly and to record what it did.

#### 1.2.2 System scope

**Inside the project:** the aircraft, its energy source, the link to the pilot, the link that
sends data to the ground, the ground equipment we operate, and the test rigs we build ourselves.

**Outside the project:** the airspace and its rules, the weather, the ground we land on, the
supply of parts, and any equipment we do not own.

**Size:** **TBD.** Mass and span depend on scale, which is not yet decided. What is fixed is
the ceiling — below 25 kg, C6 — and we expect to be far below it.

---

## 2.0 Documents

### 2.1 Applicable documents

These bind us. Every rule, its source and how well we have checked it is in
`01_requirements/RULES.md`. In summary:

- Regulation (EU) 2019/947 — the Open Category, Article 4
- Delegated Regulation (EU) 2019/945 — class markings. Relevant to us mainly because we
  **cannot** carry one
- RDW — operator number and remote pilot licence, Netherlands
- Dutch geographical zones, shown in the GoDrone map

**`RULES.md` is the authority. If this document and `RULES.md` disagree, `RULES.md` is right.**

### 2.2 Reference documents

- `01_requirements/NGO.md` — need, goals, objectives, measures of effectiveness, decisions
- `01_requirements/STAKEHOLDERS.md` — who is affected and what they expect
- `00_management/REFERENCES.md` — every source, with its exact location

---

## 3.0 Description of the envisioned system

### 3.1 Needs, goals and objectives

In `NGO.md`. Not repeated here, so that there is one place to change them.

### 3.2 Overview of the system and its key elements

Described by **what each part does**, not by what it is.

| Element | What it must do |
|---|---|
| **Lift function** | Produce enough vertical thrust to raise the aircraft from the ground, hold it steady in the air, and lower it under control |
| **Cruise function** | Produce forward thrust so the wing can carry the aircraft |
| **Wing** | Carry the whole weight of the aircraft in forward flight |
| **Structure** | Hold everything together, carry the loads of hover, cruise, transition and landing, and survive an ordinary landing on rough ground |
| **Control function** | Sense what the aircraft is doing and move the right things to keep it doing what the pilot asked |
| **Energy store** | Hold all the energy for one flight, with a reserve left at landing |
| **Command link** | Carry the pilot's commands to the aircraft |
| **Telemetry link** | Carry the aircraft's state to the ground while it is flying |
| **Recording function** | Store what happened during the flight so it can be read afterwards |
| **Ground segment** | The pilot, the transmitter, the ground station, and the two of us |

**The lift function and the cruise function may be the same hardware or different hardware.**
Deciding that is exactly the configuration trade study. This document does not decide it and
must not be read as deciding it.

### 3.3 Interfaces

| Interface | Between | Notes |
|---|---|---|
| Command | Pilot's transmitter ↔ aircraft | Must work reliably to the limit of what we can see, C11 |
| Telemetry | Aircraft ↔ ground station | Carries at least battery state and position while flying |
| Energy | Battery ↔ aircraft | Removable, so packs can be swapped and charged away from the aircraft |
| Charging | Charger ↔ battery | Off the aircraft. Never charge in the aircraft |
| Ground | Aircraft ↔ landing surface | Unprepared ground: grass, soil, gravel. Not a runway, not a prepared pad |
| Air | Aircraft ↔ atmosphere | See section 4.0 |
| Regulatory | Operator number ↔ airframe surface | The number must be **visible on the outside**. It needs a flat, reachable place that survives weather and a crash. `RULES.md` §B1 |
| Test | Aircraft or component ↔ our own test rigs | Thrust stand, tether point, scales. Required because there is no laboratory, C5 |

The regulatory interface is a real interface, not paperwork. It puts a requirement on the outside
surface of the airframe, and it is the kind of thing that gets forgotten until the week of the
first flight.

### 3.4 Modes of operation

| Mode | What is happening | Notes |
|---|---|---|
| **Stored** | Powered off, battery disconnected and stored separately | LiPo storage rules apply, §5.0 |
| **Transport** | Being carried to the site, powered off | Must survive being moved in a car |
| **Bench** | Powered, on the ground, propellers removed or guarded, checking control response and logging | No propeller may turn near a person unguarded |
| **Tethered** | Powered and lifting, held by a physical restraint | Used for the first hover and, if needed, to demonstrate transition capability for MOE-1 |
| **Armed and idle** | Powered, ready, not yet lifting | The moment before every flight. Arming discipline matters here |
| **Hover** | Airborne, weight carried by the lift function | Take-off, landing, and holding position |
| **Transition** | Changing between hover and wing-borne flight, in either direction | The hardest mode. The one MOE-1 is about |
| **Cruise** | Airborne, weight carried by the wing | Where the endurance in G2 is earned |
| **Failsafe** | The aircraft is acting on a fault, not on a pilot command | Behaviour defined in §6.2 |
| **Post-crash** | On the ground, damaged, possibly with a damaged battery | Made safe before anyone approaches. §5.0 |
| **Disposal** | End of project | Batteries in particular. §5.0 |

### 3.5 Proposed capabilities

Including the ones that exist only so that we can verify things.

1. Take off vertically from unprepared ground.
2. Hold a stable hover.
3. Change from hover to wing-borne flight, and back.
4. Fly with the wing carrying the weight, for as long as the energy store allows minus reserve.
5. Land vertically on unprepared ground.
6. **Log its own flight data** — attitude, height, speed, motor outputs, battery voltage and
   current — so a flight can be read afterwards. Required by MOE-1, which accepts logged flight
   data as proof of transition, and by every endurance figure in G2.
7. **Send its state to the ground while flying** — at least battery and position — so a flight can
   be stopped before the reserve is broken rather than after.
8. Accept a physical tether for restrained testing.
9. Be armed and disarmed deliberately, with no ambiguity about which state it is in.
10. Be repaired or rebuilt after a crash, using parts we can obtain, C9.
11. Carry the operator number visibly on its outside surface.

12. **Abandon a changeover and return to hover** under control, O1.9. Being able to stop trying is
    a capability, not an accident, and it must be designed in rather than hoped for.
13. **Accept a first-person view camera later**, as a piloting aid, D12. Not fitted to the first
    aircraft, so that the endurance figures in G2 are measured clean first and then measured
    again with it fitted. The cost of first-person view in minutes of flight is a number worth
    having, and this is the only order in which we can get it.

**No camera is carried on the first aircraft.** Flights are filmed from the ground with equipment
we already own. Capabilities 6 and 7 were chosen over carrying a camera, so that mass goes to the
battery.

**When first-person view is fitted, both of us must be at every flight.** A pilot wearing goggles
does not satisfy the visual line of sight rule. Article 4(1)(d) permits it only with an unmanned
aircraft observer, so one of us flies and the other watches the aircraft directly, unaided. The
detailed conditions on the observer are in Annex Part A, which we still cannot read, C16. Goggles
are ground equipment and are **not** in the €800 allocation.

---

## 4.0 Physical environment

Outdoors, in the Netherlands, over one academic year. That means we will be offered a lot of wind
and not much calm.

| Condition | Requirement | Status |
|---|---|---|
| Wind, steady | Must be able to fly and land safely in **TBD m/s** | **TBD.** Drives O2.3. Must be a real number before the requirements freeze |
| Wind, gusts | Must survive gusts of **TBD m/s** | **TBD** |
| Temperature | Must operate between **TBD °C** and **TBD °C** | **TBD.** Cold reduces battery capacity, which attacks G2 directly |
| Rain | **No flight in rain.** The aircraft must tolerate light damp on the ground while being set up | Fixed |
| Light | **Daylight only.** We must see the aircraft unaided, C11, and there may be a Dutch rule limiting flying to around sunrise and sunset hours | Fixed by C11. The Dutch rule is **unverified**, `RULES.md` §D |
| Height above ground | **Never above 120 m** | Fixed, C12 |
| Landing surface | Unprepared. Grass, soil, gravel, uneven, possibly soft or wet | Fixed |
| Distance from people and buildings | **NOT YET KNOWN** | **C16.** This is the largest open item in the project |

**On C16, plainly.** We do not yet know which Open Category subcategory a privately built aircraft
above 250 g falls into, and therefore how far from people and buildings we must fly. If the answer
is what we expect, the site must be genuinely open country. **We cannot choose a test site until
this is closed**, and in a country as built-up as the Netherlands it may take real searching.

---

## 5.0 Support environment

How JBV-01 is kept working once it exists. There is no laboratory and no technician, C5. Every
line below is work one of us does.

**Energy.** LiPo packs are charged off the aircraft, never inside it, never unattended, in a
fire-resistant bag or container. Packs are stored at storage charge, not full and not empty. A
pack that has been crashed, swollen or deeply discharged is retired, not used one more time.

**Spares.** Propellers break first and are cheap; we hold spares from the start. A spare of any
part whose failure would stop testing for more than a week is worth its cost against a one-year
schedule.

**Repair and rebuild.** C9 says at least one crash is planned. €200 of the budget is held for it
and is not available for the first aircraft. The airframe should be designed so that the parts
most likely to break can be remade with our own tools, and so that the electronics can be moved
into a new airframe rather than being lost with the old one.

**Test equipment.** We build it. A thrust stand, a tether point, scales, a balance for centre of
gravity. Each rig is itself checked against something known before we trust a number from it — a
thrust stand is checked against a known mass.

**Transport.** The aircraft travels to the site in a car, more than once, in an unfinished state.
It has to survive that.

**End of project.** LiPo packs are disposed of at a proper collection point, not in household
waste. This is planned now so it does not become somebody's problem in a cupboard.

---

## 6.0 Operational scenarios

Each scenario has a label so that requirements can point at it by name.

### 6.1 Nominal conditions

**[DRM-0100] Bench check.** Aircraft on the bench, propellers removed or guarded, battery
connected. Control surfaces and lift outputs respond to commands. Logging runs and the log is
readable afterwards. Telemetry reaches the ground station. Arming and disarming behave as
expected. *No propeller turns unguarded near a person.*

**[DRM-0200] Tethered lift.** Aircraft restrained by a physical tether. Lift function raises it
until the tether is taut. Stability and control response are observed and logged. Nobody stands
within reach of the aircraft's possible movement. Ends with a controlled shutdown.

**[DRM-0300] Free hover.** Aircraft takes off vertically from unprepared ground, holds a hover at
low height, moves gently in each axis, and lands vertically on the same spot. Height is kept low
enough that a fall is survivable for the aircraft and harmless to everyone present.

**[DRM-0400] First wing-borne flight.** Aircraft takes off vertically, climbs to a working height
below 120 m, changes over to wing-borne flight, flies a simple circuit within sight, changes back,
and lands vertically. This is the first time the whole flight profile is flown.

**[DRM-0500] Full mission.** The complete profile flown deliberately rather than tentatively:
vertical take-off from a clearing, hover, transition, wing-borne circuits within visual line of
sight, transition back, hover, vertical landing on the same clearing. Objective O1.1 and the top
goal of the project.

**[DRM-0600] Endurance flight.** As DRM-0500, but flown to measure. Circuits are flown until the
battery reaches its stated reserve, then the aircraft transitions back and lands. Flight time,
distance covered, and the conditions they were measured in are recorded. This is the flight that
produces the numbers for O2.2, O2.3, O2.4 and O2.6, and therefore decides MOE-4.

Every scenario above ends the same way: aircraft disarmed, battery disconnected, and an entry
written in `06_flight/FLIGHT_LOG.md` before we leave the site.

### 6.2 Off-nominal conditions

These are the ones that produce safety requirements. Writing them now is the point of doing this
before any hardware exists.

**[DRM-0700] Loss of command link.** The link between the transmitter and the aircraft drops.
The aircraft is on its own.

*What it must do:* a defined, deliberate action — not whatever the flight controller does by
default. The choice is between holding position, returning to the take-off point, and landing
where it is. **This choice becomes a written requirement**, and it changes with how
far the aircraft might be and what is under it. Getting this wrong is how aircraft leave the field
and are never found.

*What we must do:* know before the flight what it will do, and have agreed who calls it.

**A failed or stalled changeover is deliberately not a scenario here.** Decision D12 handles it in
the flight test plan for [DRM-0400] instead. Recorded openly because it is the failure most likely
to happen to us and the one MOE-1 is about: **if the [DRM-0400] test plan is thin, nothing else in
this document catches it.** The capability it drives — being able to abandon a changeover and
return to hover, objective O1.9 — stands regardless, and is listed in §3.5.

**[DRM-0900] Battery reaches reserve early.** The pack drops faster than planned — headwind, cold,
a tired cell.

*What it must do:* make its state visible on the ground while there is still time to act. This is
why capability 7, live telemetry, is in this document.

*What we must do:* have an abort rule agreed before take-off — at the reserve figure, the flight
ends, no matter what it was going to prove. The rule is worthless if it is argued about while the
aircraft is in the air.

**[DRM-1000] A lift unit fails in hover.** One part of the lift function stops working while the
aircraft is hovering.

*What it must do:* on most V/STOL layouts, nothing. The aircraft falls. There is no failsafe that
recovers this, and pretending otherwise would be worse than admitting it. This scenario is
therefore not about preventing the failure. It is about limiting what the failure costs.

*What we must do:* three things, and all three are design decisions rather than good intentions.
Hover no higher than the height at which a fall is survivable for the airframe and harmless to
anyone present — **objective O1.7**. Keep every person at least a stated distance away from the
aircraft whenever it is hovering — **objective O1.8**. Never stand underneath it, and never let
anyone else.

*Why this scenario is written even though we cannot design against it:* it is the only failure in
this document that can injure a person. Walking through it is what produced O1.7 and O1.8, and
neither would have been written otherwise.

---

## 7.0 Risks and potential issues

| # | Risk | Why it matters | What we do now |
|---|---|---|---|
| R1 | **We do not know where we may fly**, C16 | Blocks the test site, which blocks every flight scenario above | Close C16 before anything else. `RULES.md` §C |
| R2 | **Requirements creep** | We are our own customer, D1. There is no external check and nothing stops the aircraft growing except our own discipline | Freeze the requirements and log every change after that |
| R3 | **Transition is never achieved** | It is the top goal, O1.1, and the hardest thing the aircraft does | First attempt early in the schedule, not in the last month. Fallback named with a switch date, D3 |
| R4 | **Lift function fails in hover**, [DRM-1000] | Usually not recoverable. The only failure here that can hurt someone | Hover no higher than O1.7. Keep everyone at least O1.8 away. Never stand underneath. First hover is tethered, [DRM-0200] |
| R5 | **LiPo fire** | Charging, storage, and after a crash | Charge in a fire-resistant container, never unattended, never in the aircraft. Retire damaged packs |
| R6 | **No money for a parallel fallback airframe** | The ceiling is €800, D10. The fallback must be reached by rebuilding, not by switching to a second aircraft | Makes the switch date in D3 more important, not less |
| R7 | **Weather eats the schedule** | A Dutch academic year offers few calm dry days, and we fly outdoors only | Plan flying windows generously. Do bench and tethered work on bad days |
| R8 | **Our numbers are estimates, not measurements** | No laboratory, C5. Aerodynamic figures come from published data and software | Say so every time. The first flight test of any decision resting on an estimate is its real verification |
| R9 | **We buy something that costs us the privately built route** | C13. A complete ready-to-assemble kit would end it | Written as a purchasing rule in `04_build/BOM.xlsx` |
| R10 | **The rules change, or our copy is out of date** | Our consolidated text is the January 2021 edition | Re-check before the requirements freeze and again before the first flight |

---

## Appendix A — Acronyms

| | |
|---|---|
| ConOps | Concept of Operations — this document |
| DRM | Design Reference Mission — a labelled operational scenario |
| ESC | Electronic Speed Controller — the unit that drives a motor |
| LiPo | Lithium polymer battery |
| MOE | Measure of Effectiveness — a pass mark, in `NGO.md` |
| MTOM | Maximum Take-Off Mass |
| UAS | Unmanned Aircraft System — the aircraft plus everything needed to fly it |
| VLOS | Visual Line of Sight — unaided sight of the aircraft |
| V/STOL | Vertical and/or Short Take-Off and Landing |

## Appendix B — Glossary

**Transition** — the changeover between hovering and flight supported by the wing, in either
direction.

**Hover** — flight in which the aircraft's weight is carried by vertical thrust, not by the wing.

**Wing-borne flight** — flight in which the aircraft's weight is carried by the wing.

**Reserve** — the energy deliberately left in the battery at landing. Flying below it damages the
pack and risks the aircraft.

**Unprepared ground** — a piece of open ground with no runway, no pad and no launch equipment.
Grass, soil or gravel.

**Privately built** — assembled for the builder's own use, and not from a single ready-to-assemble
kit sold as one product. The legal route JBV-01 depends on, C13.

**Failsafe** — behaviour the aircraft performs on its own when something has gone wrong, without a
pilot command.

