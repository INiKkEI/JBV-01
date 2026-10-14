# JBV-01 — Concept of Operations

**This document is implementation-free on purpose.** It says what the aircraft must do, never how
it will do it. No configuration is named anywhere in it. The configuration — tiltrotor, tailsitter,
lift+cruise, tilt-wing, ducted fan — is decided later, in the configuration trade study. This
document must stay true whichever one wins. If a sentence here only makes sense for one
configuration, that sentence is wrong.

**Rewritten 2026-09-08**, against the new goals in `NGO.md` §1 and §2.

**What we cut from the NASA Appendix S outline.** Appendix S says its content and sequence "will be
a function of the type, size, and complexity of the project", so a cut is allowed if we say what we
cut and why. We cut **section 7.2, Organizational Impacts**: it is written for hiring, retraining
and reorganising staff, and there are two of us. Every other section is here, under the outline's
own numbers.

---

## 1.0 Introduction

### 1.1 Project description

#### 1.1.1 Background

Hovering costs energy for nothing but staying up. A wing carries the aircraft for far less, but a
wing needs a runway. JBV-01 exists to have neither problem.

Two students, until 12 June 2027, our own tools and our own money. The need, the goals and the
measures of success are in `NGO.md` and are not repeated here.

#### 1.1.2 Assumptions and constraints

Full list in `NGO.md` §6 and §7, and it is not copied here. **Only the ones that change how the
aircraft is operated** are listed below. The rest — money, schedule, what we can make — shape the
design instead, and they belong to `NGO.md`.

| | |
|---|---|
| At least one crash and rebuild is planned | C4 |
| **No laboratory.** Every test rig in this document is one we build ourselves | C8 |
| Vertical take-off and landing. Configuration open | C10 |
| Must remain a **privately built** aircraft — no complete ready-to-assemble kit | C12 |
| Visual line of sight at all times, **unaided** | C15 |
| **Maximum 120 m** above the surface | C16 |
| Nothing dropped, no dangerous goods | C17 |
| **At least 150 m from any built-up area** — subcategory A3 | C18 |
| **Keep from any person the greatest of 30 m, our height, and 2 s at maximum speed** | C19 |
| **Everyone present must be told the risks and agree to take part.** No bystanders | C20 |

### 1.2 Overview of the envisioned system

#### 1.2.1 Overview

JBV-01 is a small uncrewed aircraft. It takes off vertically from an unprepared piece of ground,
climbs to a working height, changes over to flight supported by its wing, flies on the wing for
more than half of the flight, changes back, and lands vertically on the same piece of ground.

It carries nothing but itself and what it needs to fly and to record what it did.

#### 1.2.2 System scope

**Inside the project:** the aircraft, its energy source, the link to the pilot, the link that sends
data to the ground, the ground equipment we operate, and the test rigs we build ourselves.

**Outside the project:** the airspace and its rules, the weather, the ground we land on, the supply
of parts, and any equipment we do not own.

**Size is not decided.** Mass and span follow from the scale, which closes with the configuration
trade study, `NGO.md` §8. The only fixed limit is below 25 kg, C13.

---

## 2.0 Documents

### 2.1 Applicable documents

These bind us. Every rule, its source and how well we have checked it is in `RULES.md`.

- Regulation (EU) 2019/947 — the Open Category, Article 4 and UAS.OPEN.040
- Delegated Regulation (EU) 2019/945 — class markings. Relevant because we **cannot** carry one
- RDW — operator number and remote pilot licence, Netherlands
- Dutch geographical zones, `RULES.md` NL1 to NL4 — shown in Aeret Kaartviewer first, GoDrone second

**`RULES.md` is the authority. If this document and `RULES.md` disagree, `RULES.md` is right.**

### 2.2 Reference documents

- `01_requirements/NGO.md` — need, goals, objectives, measures of effectiveness, constraints
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
Deciding that is exactly the configuration trade study. This document does not decide it.

### 3.3 Interfaces

| Interface | Between | Notes |
|---|---|---|
| Command | Pilot's transmitter ↔ aircraft | Must work reliably to the limit of what we can see, C15 |
| Telemetry | Aircraft ↔ ground station | Carries at least battery state and position while flying |
| Energy | Battery ↔ aircraft | Removable, so packs can be swapped and charged away from the aircraft |
| Charging | Charger ↔ battery | Off the aircraft. Never charge in the aircraft |
| Ground | Aircraft ↔ landing surface | Unprepared ground: grass, soil, gravel. Not a runway, not a prepared pad |
| Regulatory | Operator number ↔ airframe surface | The number must be **visible on the outside**. It needs a flat, reachable place that survives weather and a crash. `RULES.md` §B1 |
| Test | Aircraft or component ↔ our own test rigs | Thrust stand, tether point, scales. Required because there is no laboratory, C8 |

The regulatory interface is a real interface, not paperwork. It puts a requirement on the outside
surface of the airframe, and it is the kind of thing that gets forgotten until the week of the
first flight.

### 3.4 Modes of operation

| Mode | What is happening | Notes |
|---|---|---|
| **Stored** | Powered off, battery disconnected and stored separately | LiPo storage rules apply, §5.0 |
| **Transport** | Being carried to the site, powered off | Must survive being moved in a car |
| **Bench** | Powered, on the ground, propellers removed or guarded, checking control response and logging | No propeller may turn near a person unguarded |
| **Tethered** | Powered and lifting, held by a physical restraint | The first hover, and proving both transitions before free flight — G2-O5, the gate |
| **Armed and idle** | Powered, ready, not yet lifting | The moment before every flight. Arming discipline matters here |
| **Hover** | Airborne, weight carried by the lift function | Take-off, landing, and holding position |
| **Transition** | Changing between hover and wing-borne flight, in either direction | The hardest mode. The one the project is about |
| **Cruise** | Airborne, weight carried by the wing | More than half of every flight, G1-O2 |
| **Failsafe** | The aircraft is acting on a fault, not on a pilot command | Behaviour defined in §6.2 |
| **Post-crash** | On the ground, damaged, possibly with a damaged battery | Made safe before anyone approaches. §5.0 |
| **Disposal** | End of project | Batteries in particular. §5.0 |

### 3.5 Proposed capabilities

Including the ones that exist only so that we can verify things. **Each one is here because
something breaks if it is removed**, and the thing it would break is named.

| # | Capability | Breaks if removed |
|---|---|---|
| 1 | Take off vertically from unprepared ground | G1 |
| 2 | Hold a hover, and move under command, and stop under control | G2-O1 |
| 3 | Change from hover to wing-borne flight, and back | G1, and the whole project |
| 4 | Fly with the wing carrying the weight, for more than half the flight | G1-O2 |
| 5 | Land vertically on unprepared ground | G1 |
| 6 | **Log its own flight data** — attitude, height, speed, motor outputs, battery voltage and current, **and transmitter stick positions** | MOE-1, and all three G2 criteria are read off this log |
| 7 | **Send its state to the ground while flying** — at least battery and position | [DRM-0800]. Without it the flight ends after the reserve is broken, not before |
| 8 | Accept a physical tether for restrained testing | G2-O5 |
| 9 | Be armed and disarmed deliberately, with no ambiguity about which state it is in | Safety on every flight |
| 10 | Abandon a transition and return to hover under control | G2-O4 |
| 11 | Be repaired or rebuilt after a crash, using parts we can obtain | C4 |
| 12 | Carry the operator number visibly on its outside surface | C22, and it is law |

**Two capabilities were removed on 2026-09-08.** What each removal costs is written here, so that
it is a decision on the record and not something discovered later.

- **Descend under control with no propulsive thrust**, the wing carrying its weight. It belonged to
  the glide descent rate objective, deleted on 2026-09-08 for having no value. **What it costs: a propulsion failure in
  wing-borne flight now has no planned answer anywhere in this folder.** The aircraft falls. This is
  accepted, not overlooked.
- **Accept a first-person view camera later.** It constrained the design for a flight that may never
  happen, and its reason was measuring endurance cleanly, which is no longer a goal. No cost we can
  see. If we ever want it, a pilot wearing goggles does not satisfy C15 — one of us must watch the
  aircraft directly, unaided.

**No camera is carried.** Flights are filmed from the ground with equipment we already own.

---

## 4.0 Physical environment

Outdoors, in the Netherlands, over one academic year. That means a lot of wind and not much calm.

| Condition | Requirement | Source |
|---|---|---|
| Height above ground | **Never above 120 m** | C16, law |
| Distance from areas | **At least 150 m** horizontally from residential, commercial, industrial or recreational areas | C18, law |
| Distance from people | The greatest of **30 m**, our flying height, and **2 seconds at maximum speed**. Everyone present must also have agreed to take part | C19 and C20, law |
| Light | **Daylight only.** Flying on sight in the dark is forbidden, and the routes around it are closed to us | `RULES.md` §C, law |
| Rain | **No flight in rain.** The aircraft must tolerate light damp on the ground while being set up | Our rule |
| Landing surface | Unprepared. Grass, soil, gravel, uneven, possibly soft or wet | Fixed |
| Wind and temperature | **No figure is set in this document.** The limits for a given flight are stated in that flight's test plan, before the flight | See below |

**One wind figure will still be needed, and it is not this document's job.** Propulsion cannot be
sized without a design wind speed, because the aircraft has to hold a hover against it. That figure
belongs to the propulsion sizing decision. It is an open item in `NGO.md` §8.

**On C18, plainly.** We are in **A3** — a privately built aircraft over 250 g has no other route.
A3 puts us at least 150 m from any residential, commercial, industrial or recreational area. The
site must be genuinely open country, and in a country as built-up as the Netherlands finding one
will take real searching.

---

## 5.0 Support environment

How JBV-01 is kept working once it exists. There is no laboratory and no technician, C8. Every line
below is work one of us does.

**Energy.** LiPo packs are charged off the aircraft, never inside it, never unattended, in a
fire-resistant bag or container. Packs are stored at storage charge, not full and not empty. A pack
that has been crashed, swollen or deeply discharged is retired, not used one more time.

**Spares.** Propellers break first and are cheap; we hold spares from the start. A spare of any part
whose failure would stop testing for more than a week is worth its cost against a one-year
schedule.

**Repair and rebuild.** C4 says at least one crash is planned. €200 of the budget is held for it and
is not available for the first aircraft. The airframe should be designed so that the parts most
likely to break can be remade with our own tools, and so that the electronics can be moved into a
new airframe rather than being lost with the old one.

**Test equipment.** We build it. A thrust stand, a tether point, scales, a balance for centre of
gravity. Each rig is checked against something known before we trust a number from it — a thrust
stand is checked against a known mass.

**Transport.** The aircraft travels to the site in a car, more than once, in an unfinished state. It
has to survive that.

**End of project.** LiPo packs are disposed of at a proper collection point, not in household waste.
Planned now so it does not become somebody's problem in a cupboard.

---

## 6.0 Operational scenarios

Each scenario has a label so that requirements can point at it by name.

### 6.1 Nominal conditions

**[DRM-0100] Bench check.** Aircraft on the bench, propellers removed or guarded, battery
connected. Control surfaces and lift outputs respond to commands. Logging runs and the log is
readable afterwards, **including the stick positions**. Telemetry reaches the ground station.
Arming and disarming behave as expected. *No propeller turns unguarded near a person.*

**[DRM-0200] Tethered lift.** Aircraft restrained by a physical tether. Lift function raises it
until the tether is taut. Stability and control response are observed and logged. Both transitions
are attempted here before any free flight — **this scenario verifies G2-O5**. Nobody stands within
reach of the aircraft's possible movement. Ends with a controlled shutdown.

**[DRM-0300] Free hover.** Aircraft takes off vertically from unprepared ground, holds a hover,
moves under command, comes to a controlled stop, and lands vertically on the same spot. A short
stick input is given and released, to see whether the aircraft settles back to trim. Height is kept
low enough that a fall is survivable for the aircraft and harmless to everyone present. **This
scenario verifies G2-O1 and the hover half of G2-O3.**

**[DRM-0400] First wing-borne flight.** Aircraft takes off vertically, climbs to a working height
below 120 m, changes over to wing-borne flight, flies a simple circuit within sight, changes back,
and lands vertically. The first time the whole profile is flown. **Verifies G2-O2, G2-O4, and the
wing-borne half of G2-O3.**

**[DRM-0500] Full mission.** The complete profile flown deliberately rather than tentatively:
vertical take-off from a clearing, hover, transition, wing-borne circuits within visual line of
sight, transition back, hover, vertical landing on the same clearing. **This scenario is objective
G1-O1, and it decides MOE-1.**

**[DRM-0600] Endurance flight.** As DRM-0500, but flown to measure. Circuits are flown until the
battery reaches its stated reserve, then the aircraft transitions back and lands. Total flight time
and the wing-borne part of it are read off the log, with the conditions they were measured in.
**This scenario decides G1-O2.** Distance and speed are recorded and reported, but no longer
required.

Every scenario above ends the same way: aircraft disarmed, battery disconnected, and an entry
written in `06_flight/FLIGHT_LOG.md` before we leave the site.

### 6.2 Off-nominal conditions

These are the ones that produce safety requirements. Writing them before any hardware exists is the
point of doing this now.

**[DRM-0700] Loss of command link.** The link between the transmitter and the aircraft drops. The
aircraft is on its own.

*What it must do:* a defined, deliberate action — not whatever the flight controller does by
default. The choice is between holding position, returning to the take-off point, and landing where
it is. **This choice becomes a written requirement**, and it changes with how far the aircraft might
be and what is under it. Getting this wrong is how aircraft leave the field and are never found.

*What we must do:* know before the flight what it will do, and have agreed who calls it.

**[DRM-0800] Battery reaches reserve early.** The pack drops faster than planned — headwind, cold,
a tired cell.

*What it must do:* make its state visible on the ground while there is still time to act. This is
why capability 7 is in this document.

*What we must do:* agree an abort rule before take-off — at the reserve figure in C11 the flight
ends, no matter what it was going to prove. The rule is worthless if it is argued about while the
aircraft is in the air.

**[DRM-0900] A lift unit fails in hover.** One part of the lift function stops working while the
aircraft is hovering.

*What it must do:* on most V/STOL layouts, nothing. The aircraft falls. There is no failsafe that
recovers this, and pretending otherwise would be worse than admitting it. This scenario is not about
preventing the failure. It is about limiting what the failure costs.

*What we must do:* keep people away from the aircraft whenever it is hovering, and never stand
underneath it. **The distance is set by C19** — the greatest of 30 m, the height we are flying at,
and the distance we would cover in 2 seconds at maximum speed. Note what the middle term does: the
higher we hover, the further back people stand. Height and distance are tied together by the rule
itself. On top of that, 150 m from any built-up area, C18, and everyone present told the risks and
agreeing to take part, C20.

*Why this is written even though we cannot design against it:* it is the only failure in this
document that can injure a person.

**A failed or stalled transition is deliberately not a scenario here.** It is handled in the flight
test plan for [DRM-0400] instead. Recorded openly, because it is the failure most likely to happen
to us: **if the [DRM-0400] test plan is thin, nothing else in this document catches it.** The
capability it drives — abandoning a transition and returning to hover, G2-O4 — stands regardless.

---

## 7.0 Impacts

### 7.1 Environmental impacts

**Noise.** The lift function is the loud part of the aircraft, and hover is the loud phase of the
flight. We keep hover time short and we fly away from houses. It is also the thing people near the
test site will notice about us before anything else, `STAKEHOLDERS.md` §3.

**Waste.** LiPo packs go to a proper collection point at the end of the project, never into
household waste. Foam, depron, balsa and printed parts become waste at every rebuild, and C4 plans
at least one. Broken parts leave the field with us.

Nothing else. The aircraft carries no fuel, drops nothing (C17), and releases nothing.

### 7.2 Organizational impacts

**Cut.** This section of the outline is written for hiring, retraining and reorganising staff. There
are two of us and no organisation above us.

### 7.3 Scientific and technical impacts

JBV-01 produces no new science, and we should not pretend otherwise. It is one small uncrewed
aircraft, built once, by two people.

What it demonstrates is narrow and worth stating exactly: that a V/STOL aircraft can be designed,
built and flown through both transitions, under control, inside €295 of parts, with hand tools, a
3D printer, a laser cutter and no laboratory. The result is the transition, flown and logged.

**We make no performance claim.** Flight time, cruise speed and distance are measured and reported
with the conditions next to them. None of them is compared against another aircraft.

---

## 8.0 Risks and potential issues

| # | Risk | Why it matters | What we do now |
|---|---|---|---|
| R1 | **No legal test site is found**, AS1 | A3 needs 150 m from every residential, commercial, industrial and recreational area. In the Netherlands that rules out most of the map | Start the site search now, against the 150 m figure and the zones in `RULES.md` NL1 to NL4. It blocks every flight scenario above |
| R2 | **Requirements creep** | We are our own customer. There is no external check and nothing stops the aircraft growing except our own discipline | Freeze the requirements and log every change after that |
| R3 | **Transition is never achieved** | It is the project. G1-O1 and both halves of G2 | First attempt early in the schedule, not in the last month. Fallback named with a switch date |
| R4 | **Lift function fails in hover**, [DRM-0900] | Usually not recoverable. The only failure here that can hurt someone | Hold the C19 distance. Everyone present is a participant who has been told the risks, C20. Never stand underneath. First hover is tethered, [DRM-0200]. **We set no maximum hover height of our own**, but C19 makes height expensive: hovering higher pushes everybody further back |
| R5 | **LiPo fire** | Charging, storage, and after a crash | Charge in a fire-resistant container, never unattended, never in the aircraft. Retire damaged packs |
| R6 | **No money for a parallel fallback airframe** | The ceiling is €800. The fallback must be reached by rebuilding, not by switching to a second aircraft | Makes the switch date in the fallback rule more important, not less |
| R7 | **Weather eats the schedule** | A Dutch academic year offers few calm dry days, and we fly outdoors only | Plan flying windows generously. Do bench and tethered work on bad days |
| R8 | **Our numbers are estimates, not measurements** | No laboratory, C8. Aerodynamic figures come from published data and software | Say so every time. The first flight test of any decision resting on an estimate is its real verification |
| R9 | **We buy something that costs us the privately built route** | C12. A complete ready-to-assemble kit would end it | Written as a purchasing rule in `04_build/BOM.xlsx` |
| R10 | **The rules change** | Our text is the July 2024 edition, current at the time of reading | Re-check before the requirements freeze and again before the first flight |
| R11 | **The flight log does not record stick positions** | G2-O1 and G2-O2 are decided by them. If they are not logged, both criteria have to be rewritten | Install the flight controller software and open a log before the requirements freeze |

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
direction. **This is the one word we use for it**, because it is the term our sources use.

**Hover** — flight in which the aircraft's weight is carried by vertical thrust, not by the wing.

**Wing-borne flight** — flight in which the aircraft's weight is carried by the wing.

**Controllability** — the aircraft does what the pilot commands, when commanded.

**Stability** — the aircraft returns to its trimmed state after a disturbance, with no pilot input.
Separate from controllability, and in hover it comes almost entirely from the flight controller.

**Reserve** — the energy deliberately left in the battery at landing. Flying below it damages the
pack and risks the aircraft.

**Unprepared ground** — a piece of open ground with no runway, no pad and no launch equipment.
Grass, soil or gravel.

**Privately built** — assembled for the builder's own use, and not from a single ready-to-assemble
kit sold as one product. The legal route JBV-01 depends on, C12.

**Failsafe** — behaviour the aircraft performs on its own when something has gone wrong, without a
pilot command.
