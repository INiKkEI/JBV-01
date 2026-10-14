# Requirements baseline

Need, goals, objectives, measures of effectiveness, design rules, constraints and assumptions.

**This file holds the baseline only.** Why a line reads the way it does, and what was rejected on
the way, lives in the GitHub issue that changed it.

These are **not requirements.** An objective is not a requirement. Requirements are written in
`REQUIREMENTS.md`, after this file is settled.

**Rewritten 2026-09-08.** The performance goal was removed. See §1.

---

## 1. Need

> **Hovering costs energy for nothing but staying up. A wing carries the aircraft for far less —
> but a wing needs a runway. We need an aircraft with neither problem.**

**The problem, stated plainly.** A rotorcraft spends its whole flight holding itself in the air.
Every second of hovering is paid for out of the battery. A wing does the same job for much less,
because the air moving over it does the work — but a wing only lifts once the aircraft is already
moving, and getting it moving needs a runway or launch equipment.

So today you take one problem or the other. Not having to take either is the need.

**Why this is one need and not two.** The two halves can be traded against each other, so at first
sight this looks like two needs. It is not. Trading either half away does not weaken the need — it
destroys it. Drop the wing and the aircraft is a rotorcraft. Drop the hover and it is a plane. Both
already exist.

**What follows from it.** The aircraft must hover, so it can leave from and return to ordinary
ground. It must fly on its wing, so the flight is not paid for entirely in hovering. And it must
change between the two. That changeover — the **transition** — is the hard part, and it is the
project.

Runway independence sits inside the problem, so **V/STOL follows from the need rather than being
assumed.** Which V/STOL configuration is still open.

**How much less a wing costs is not a claim we make.** That a wing is cheaper than hovering is
ordinary aerodynamics and we take it as given. The size of the gap depends on the wing, the
propellers and the mass, and we have measured none of them. We state no figure for it anywhere.

## 2. Goals

Goals elaborate the need. A goal does not have to carry a number, but it must let us judge whether
the aircraft achieved it.

| ID | Goal | Descends from |
|---|---|---|
| **G1** | The aircraft completes the full profile from an unprepared site: vertical take-off, hover, transition to wing-borne cruise, sustained cruise, transition back to hover, vertical landing | The need — the combination |
| **G2** | The aircraft is **controllable and stable** through every phase: the pilot can command it when he wants, and it returns to its trimmed state after a disturbance without pilot input | The need — the transition is the hard part |

**G1 and G2 are not ranked against each other.** G1 without G2 is one lucky flight we cannot repeat
and cannot learn from.

**Two properties, named apart on purpose.** *Controllability* is the aircraft doing what the pilot
commands. *Stability* is the aircraft returning to its trimmed state on its own, with no pilot
input. They are separate. An aircraft can be stable and hard to command, or unstable and easy to
command. Almost every multirotor is the second case: the airframe is unstable, and the flight
controller holds it steady many times per second.

**So most of the stability in G2 will come from the flight controller, not from the airframe
shape.** We should expect to meet the stability half by tuning software, and we should say that
when we report it rather than claiming the airframe did it.

## 3. Objectives

Every objective must be specific, measurable and verifiable, aggressive but attainable, and about
the result rather than the method.


### Under G1 — the aircraft flies the profile

| ID | Objective | Verification | Status |
|---|---|---|---|
| G1-O1 | At least one flight, before the end of the project, containing in sequence: vertical take-off, stable hover, transition to wing-borne cruise, sustained cruise, transition back to hover, vertical landing | The flight log for that flight. [DRM-0500] | Fixed. **The pass mark** — MOE-1 |
| G1-O2 | Total flight time greater than **5 min**, measured from lift-off to landing and flown to the battery reserve in C11, of which **more than half** is wing-borne | The flight log. [DRM-0600] | Both figures **set 2026-09-08** |

**Why G1-O2 has two parts.** Total flight time alone can be passed by hovering, and an aircraft
that hovers for five minutes is a rotorcraft. The wing-borne fraction is what makes the wing
necessary, so it is the half of this objective that carries the need.

**Why a fraction and not a number of minutes.** A fixed figure stops meaning anything if the
aircraft turns out to fly much longer than the floor — two minutes of wing-borne flight out of
fifteen would still pass. A fraction holds at any flight time.

**What this asks of the flight, on today's estimates.** Take-off, a hover check, both transitions,
the descent and the landing come to roughly 1.5 to 2 minutes. So a 5 minute flight leaves about 3
to 3.5 minutes for cruise, and half of 5 minutes is 2.5. It fits, but not by much. **These phase
times are estimates from ordinary practice, not measurements**, and hovering costs far more power
than cruising, so the overhead is the most expensive part of the flight. The first flight test is
what checks this.

### Under G2 — the aircraft is under control

Verified by **demonstration**, which NASA lists as a verification method alongside test, analysis
and inspection. A demonstration is only worth something if its pass/fail sentence is **written and
agreed before the flight**. We are both the pilot and the judge, so nothing else keeps us honest.

| ID | Objective | Verification | Status |
|---|---|---|---|
| G2-O1 | In hover, the pilot can hold the aircraft where he wants it, **with control margin left**. Criterion: *the pilot holds a hover for 60 s and never needs full stick travel on any axis* | Demonstration, checked against the recorded stick positions in the flight log. [DRM-0300] | **Set 2026-09-08.** Rests on the log recording stick positions, which is **unconfirmed** — see §8 |
| G2-O2 | The aircraft passes through both transitions with **control margin left**. Criterion: *from the start of each transition until the new flight mode is steady, the pilot never needs full stick travel on any axis* | Demonstration, checked against the recorded stick positions in the flight log. [DRM-0400] | **Set 2026-09-08.** Same measure and same log source as G2-O1 |
| G2-O3 | After a disturbance, the aircraft returns to its trimmed state **with no pilot input** — in hover and in wing-borne flight. Criterion: *after a short stick input is released, the oscillation gets smaller on each cycle and the aircraft settles back to trim* | Demonstration, read off the attitude trace in the flight log. [DRM-0300] and [DRM-0400] | **Set 2026-09-08** |
| G2-O4 | The aircraft can abandon a transition and return to hover under control | Demonstration. [DRM-0400] | Fixed. Being able to stop trying is a capability, not an accident |
| G2-O5 | Both transitions are proved on a tether or on the bench before any free-flight attempt | [DRM-0200] | Fixed. **The gate, not the pass mark** |

**G2-O1 and G2-O2 are controllability. G2-O3 is stability.** The two halves of G2, kept as separate
objectives so that passing one cannot be mistaken for passing both.

**Both controllability criteria use the same measure — no full stick travel.** Full stick means the
aircraft has no control margin left, so the next disturbance has nothing to answer it. One measure,
one source, checked the same way in hover and in transition.

**No angle limit is written for the transition, and that is deliberate.** Pitch and roll through a
transition depend entirely on the configuration — a tailsitter turns through about 90°, a lift+cruise
barely changes attitude. Any angle written here would rule out layouts before the trade study runs.

**G1-O1 and G2-O5 are different in kind.** G1-O1 is the complete flight, flown, and MOE-1 measures it.
G2-O5 is the capability, proved cheaply before the aircraft is risked. Verify at the lower level
before integrating — that is the V-model rule, and it is what keeps the first airframe in one
piece.

## 4. Measures of Effectiveness

A Measure of Effectiveness is a measure of success written from the stakeholder's point of view.
The test: **failing it makes the stakeholder call the system unacceptable.** We are the
stakeholder, so we are the ones who would have to say it.

| ID | Measure | Verifies | Verification | Fails if |
|---|---|---|---|---|
| **MOE-1** | The aircraft flies **one complete flight** containing, in sequence: vertical take-off, hover, transition to wing-borne cruise, sustained cruise, transition back to hover, vertical landing | G1-O1, so G1 | The flight log for that flight | No such flight is ever flown |
| **MOE-2** | That flight was flown **under control and stable** — the three criteria in §3 all passed | G2-O1 to G2-O4, so G2 | Demonstration, judged against the flight log | The pilot needed full stick travel in hover or in either transition, or the aircraft did not settle back to trim after a disturbance |

**MOE-2 is the weaker of the two, and we should say so.** We wrote the criteria, we fly against
them, and we judge them. There is no outside check. Two things reduce the problem: all three were
written on **2026-09-08, before any hardware exists**, and all three are read off the flight log
rather than off our opinion on the day. What is left is that we chose the measure — and that is
what a logged revision is for if we ever change it.

**Nothing fails if the record drifts.** No measure covers the requirements list, the design log,
the test log or the flight log. We keep them because we want them and because the V-model does not
work without them.

## 5. Design rules

How we decide when we have a choice. Not measures, and not constraints.

### 5.1 The fallback rule

Where an ambitious choice has a proven off-the-shelf alternative, we may take the ambitious one
**only if both of these have an answer at the moment we choose**:

1. Does a proven off-the-shelf fallback exist, and can we afford it inside C3?
2. What is the date by which we switch to the fallback if ours is not working?

If either question has no answer, we take the proven option.

**Where it applies:** configuration, avionics, propulsion, control software — anywhere a substitute
product or method exists. **Where it does not:** airframe and aerodynamic design, because there is
no off-the-shelf substitute for our own wing. There the rule is *prefer the simpler method*.

**What C3 costs here.** €800 does not fund a fallback airframe built alongside the ambitious one.
The fallback has to be reached by rebuilding the same aircraft. That makes the switch date in
question 2 more important, not less.

### 5.2 The transition drives the design

The project fails outright if the G1-O1 flight is never flown, so three things bind hard:

1. Transition risk is project risk, and the configuration trade study weights it as such.
2. A configuration with a difficult transition needs its fallback and switch date named **at the
   same time as the choice**, not later.
3. The schedule places the first transition attempt early enough that a failure leaves time for a
   rebuild or a fallback. Leaving it to the last month means we never find out whether G1-O1 was
   reachable.

## 6. Constraints

A condition that has to be met and cannot be traded against cost, schedule or performance.

**Constraint numbers are not reused and not renumbered.** `CONOPS.md`, `RULES.md` and
`STAKEHOLDERS.md` all cite them by number.

| ID | Constraint | Status |
|---|---|---|
| C1 | Two people | Fixed |
| C2 | **The project ends 12 June 2027** — last flight and write-up done | **Chosen 2026-10-14.** If it is wrong, every date in the plan moves |
| C3 | **€800 total project spend, hard ceiling.** Every purchase comes out of it, including the rebuild | Fixed. Apportioned below |
| C4 | At least one crash and rebuild is planned, not a surprise | Fixed |
| C5 | **What we make ourselves.** FDM printing in PLA and PETG; soldering and basic electronics; hand tools for foam, balsa and depron; laser cutting at the makerspace, free to us as students. No money per part, no lead time beyond our own hands | Fixed |
| C6 | **What we order as a service.** Circuit boards, CNC parts, sheet metal, resin and powder printing, in single quantities from JLCPCB and its sister services. **€20–30 and 1 to 3 weeks per _parcel_**, not per part — orders across services combine into one parcel | Fixed. Prices below. No part of ours has been quoted |
| C7 | **Excluded — factory grade only.** Any process needing production tooling, a minimum order quantity, or industrial plant we cannot buy in ones. **This is the only exclusion.** The test: if we can obtain one of the thing, inside C3 and inside the schedule, it is allowed | Fixed |
| C8 | **No laboratory.** No wind tunnel, no thrust stand, no load cells, no lab instruments. Any measurement we want, we buy or build the rig ourselves, and check it against something known first | Fixed. What the makerspace holds has never been checked, AS6 |
| C9 | **Simulation and published data are what we have instead.** Every number they produce is an **estimate, never a measurement**, and the first flight test of any decision resting on one is its real verification | Fixed. Tools chosen 2026-09-08, see §8. None has been run yet |
| C10 | Vertical take-off and landing. The configuration — tiltrotor, tailsitter, lift+cruise, tilt-wing, ducted fan — is open | Follows from the need. Closes with the configuration trade study |
| C11 | **Battery reserve at landing: 20% of pack capacity.** G1-O2 is measured to this reserve, and the abort rule in [DRM-0800] triggers here | **Set 2026-08-09.** Below roughly 20% a LiPo degrades quickly — rule of thumb from hobby practice, not measured and not sourced |
| C12 | Must qualify as a **privately built UAS** — assembled from parts or sub-assemblies sold separately, **not** from a single ready-to-assemble kit, and never placed on the market | **Confirmed.** `RULES.md` §A |
| C13 | Maximum take-off mass **below 25 kg** | **Confirmed.** `RULES.md` §A, EU2 |
| C14 | Kept a safe distance from people, and **never flown over assemblies of people** | **Confirmed.** `RULES.md` §A, EU3. The metres are in C19 |
| C15 | **Visual line of sight at all times**, unaided | **Confirmed.** `RULES.md` §A, EU4 |
| C16 | **Maximum height 120 m** above the closest point of the surface | **Confirmed.** `RULES.md` §A, EU5 |
| C17 | No dangerous goods carried, nothing dropped in flight | **Confirmed.** `RULES.md` §A, EU6 |
| C18 | **We fly in subcategory A3** — at least **150 m** horizontally from residential, commercial, industrial or recreational areas. A1 needs under 250 g and under 19 m/s; A2 needs a class mark we cannot carry | **Confirmed.** `RULES.md` §C, UAS.OPEN.040(2) and (4)(a) |
| C19 | Keep at least **max(30 m, our flying height, 2 s × our maximum speed)** from any uninvolved person. If one enters the area, adjust the operation or stop it | **Confirmed.** `RULES.md` §C, AMC1 UAS.OPEN.040(1) |
| C20 | **Everyone present must be told the risks and must explicitly agree to take part.** No bystanders, only participants | **Confirmed.** `RULES.md` §C, UAS.OPEN.050(7) |
| C21 | The **900 g** boundary is not ours. It belongs to the C1 class marking, which a privately built aircraft cannot carry. Our mass limit is 25 kg | **Confirmed.** `RULES.md` §C |
| C22 | **Operator number** from the RDW, €23, expires yearly, **visible on the outside of the airframe** | **Confirmed.** `RULES.md` §B1 |
| C23 | **Remote pilot licence** A1/A3, €10, valid 5 years, carried on every flight. The pilot must also be familiar with our own build and setup notes | **Confirmed.** `RULES.md` §B2 |

**`RULES.md` is the authority on C12 to C23.** The rows above are the short form and carry no
sources. If the two disagree, `RULES.md` is right.

**How old the source is.** Confirmed against the EASA consolidated text, **July 2024 edition**,
which carries all five amendments. Re-check before the requirements freeze and again before the
first flight.

### What the ordered services cost

Floor prices and build times from JLC3DP's own service list, read 2026-08-14. **Build time is
manufacturing only** — shipping and EU customs are the 1 to 3 weeks in C6.

| Service | From | Build time |
|---|---|---|
| SLA, resin | $0.30 | 2 days |
| FDM / SLS / MJF | $1.00 | 3 days |
| CNC machining | $5.00 | 3 days |
| SLM, metal printing | $8.00 | 3 days |
| PCB | $2.00 / 5 pcs | 24 hours |
| JLCMC mechatronic parts | $0.10 | same-day shipping |

**Every "from" figure is a floor, not our price.** Nothing of ours has been quoted.

**Orders combine into one parcel**, confirmed 2026-08-14 — 3D printing, CNC, PCB, PCBA and stencils
share one cart, one payment and one parcel. So the €20–30 is paid once, not once per service.

**What this means for the configuration trade.** C7 rules almost nothing out, so manufacturability
is not a filter. What replaces it:

    cost of a configuration ≈ parts + (number of parcels × €20–30)
    time of a configuration ≈ longest build time + 1 to 3 weeks per parcel

**The trade counts parcels and weeks, not machines.**

### Derivation of C3 — what €800 covers

Replaced by real figures in `04_build/BOM.xlsx` as parts are chosen.

| Line | € | Note |
|---|---|---|
| Transmitter and receiver | 100 | Bought once. Survives every crash |
| Charger, LiPo safe bag, fire precautions | 80 | Bought once |
| Thrust stand — load cell, amplifier, microcontroller | 30 | Required by C8 |
| Registration and pilot licence | 35 | €23 operator number + €10 licence for **one pilot, who is also the operator**, chosen 2026-10-14 — see `RULES.md` §B1. The operator number lasts one year, so registering from now on covers the project to 12 June 2027 with no renewal |
| Printed circuit boards | 60 | One order plus one re-spin, roughly €20–30 each |
| Rebuild allowance | 200 | Required by C4. **Not available for the first aircraft** |
| **First aircraft — airframe, propulsion, avionics, battery** | **295** | The number that matters |
| Total | 800 | |

**Laser cutting costs nothing** — the makerspace is free to us. Sheet material is **not yet priced**
and comes out of the first aircraft line.

### What C8 costs us

1. **Thrust, current and RPM** must be measured, because propulsion sizing rests on them. The
   ordinary answer is a home-made thrust stand. It has to be priced, built, and checked against a
   known mass before we trust it. That is work, not an assumption.
2. **Mass and centre of gravity.** A kitchen scale and a balance beam are enough. No problem here.
3. **Aerodynamic coefficients.** No substitute we can build. They come from published aerofoil data
   and software, and **every one is written down as an estimate**. The first flight test of a
   decision resting on one is its real verification.

**Simulation is analysis, and analysis verifies a requirement only when the model behind it is
validated.** Ours will not be. **Whether any requirement may be verified by analysis alone is open,
and until it is settled the answer is no.**

**SITL simulates every layout we are considering except the tilt-wing**, checked 2026-09-08 against
ArduPilot's Using SITL page and its own source. It starts with one command, takes a USB transmitter
through the joystick module, and ships with a sample VTOL take-off and landing mission. The named
Plane frames are `quadplane` for separate lift and thrust, `quadplane-tilt`, `quadplane-tilttri`,
`quadplane-tilttrivec` and `quadplane-tilthvec` for tilt-rotors, and `plane-tailsitter` and
`quadplane-copter_tailsitter` for tailsitters. Four things follow:

1. It reduces transition risk in a way nothing else we have does. We can fly the mode logic, the
   mixer and the failsafes before the aircraft exists.
2. It validates no aerodynamics. The docs' own word is *simple*. Every number out of it is still an
   estimate under C9.
3. **The frame type is not only a parameter set.** ArduPilot's own words: choosing it *"selects the
   correct physics model"*, and a QuadPlane cannot be simulated correctly without picking its exact
   frame. So the frame list above is a list of physics models, not of preset files.
4. **The tilt-wing is the layout with no simulation fallback.** The `quadplane-cl84` frame is named
   after a tilt-wing aircraft, but the source maps it to the tilt-tricopter model with a binary tilt
   servo, and the wing is not rotated. Under the fallback rule that asymmetry is an input to the
   configuration trade, not a decision — and it is the opposite of what we recorded on 2026-08-14.

Nobody here has run SITL yet.

## 7. Assumptions

Written down because an assumption that is never written is never checked. Prefixed **AS**, because
A1, A2 and A3 already mean the Open Category subcategories.

| ID | Assumption | Checked? |
|---|---|---|
| AS1 | A legal test site exists within reasonable travel of us | **No** |
| AS2 | We can build a thrust stand accurate enough to size the propulsion system, within budget | **No.** Needs pricing and a build |
| AS3 | Off-the-shelf hobby parts adequate for our scale are available in the EU within our budget | **No** |
| AS4 | A proven open-source flight controller stack supports whichever configuration we choose | **Mostly.** ArduPlane documents QuadPlane, tilt-rotor, tilt-wing and tailsitter frames, and SITL carries physics models for separate lift and thrust, tilt-rotors and tailsitters — checked 2026-09-08 from the docs and the source. **The tilt-wing has firmware support but no SITL physics model.** The source was read from the master branch, so re-check against the firmware version we install. Nothing is verified on hardware by us |
| AS6 | The makerspace laser cutter stays available to us, free, for the whole academic year | **No.** Free today is not free in March. The only capability that depends on somebody else's opening hours |
| AS7 | Sheet material for laser cutting is affordable inside the first aircraft line | **No.** Unpriced. Price it before any design decision rests on a cut part |
| AS8 | One PCB order plus one re-spin is enough for the whole project | **No.** A budget decision, not a measurement |
| AS9 | We can learn the simulation tools well enough to trust their output inside this academic year, alongside building the aircraft | **No.** Free software is not free time |

**AS5 and AS5a are deleted.** They existed to support the multirotor and fixed-wing benchmarks,
which were removed on 2026-09-08. IDs are not reused.

## 8. What is still open

| Item | Closes at |
|---|---|
| **Does the flight log record stick positions?** | Before the requirements freeze. G2-O1's criterion is checked against them, so if the log does not hold them the criterion has to change. Install the flight controller software, fly one throwaway case, and open the log |
| **What G2-O3 can never prove** | Nothing to close. Recorded so we do not overclaim: a hovering V/STOL aircraft is unstable without its flight controller, in the same way a multirotor is. So the hover pulse test measures **the airframe and the controller together**, and we report it that way. Only a wing-borne pulse test flown in manual pass-through mode would test the airframe alone, and we are not doing that on the first aircraft |
| **The G2 criteria cannot be tested as written** — G2-O1 and G2-O2 have no threshold for "full stick travel"; G2-O3 has no pulse size, pulse duration or settling limit; G2-O4 has no criterion, and MOE-2's "Fails if" leaves it out; G2-O5 has no verification method and no pass mark. **On a layout where the autopilot flies the transition, G2-O2's criterion passes by default** — `FUNCTIONS.md` F6 note. The fix must work for every candidate configuration | Before the requirements freeze, and before any flight, because a demonstration criterion is never edited after the flight. Decide after the SITL log check shows what the log records |
| **May a requirement be verified by analysis alone?** | Before `REQUIREMENTS.md`. Until settled the answer is no |
| **Which simulation tools we use**, C9 | **Chosen 2026-09-08: built-in ArduPilot SITL, XFLR5 and AVL.** All three are free and all three run on Windows, so no Linux or WSL2 install is needed. An external flight simulator — Gazebo or RealFlight — is deferred until after the configuration trade. **Still open until each has been installed and run once**, because a tool we have not run is not a capability. See `00_management/STAGE_3_NOTES.md` §7 |
| ~~**Whether SITL simulates a tiltrotor or a tailsitter**, C9~~ | **Closed 2026-09-08.** Yes to both, with named frames and their own physics models. The tilt-wing is the exception. See §6 and AS4 |
| **A real quote for a part of ours**, C6 | Before any design depends on an ordered part |
| **What the makerspace actually holds** — bed size, materials, any measuring instrument | Go and look. It may move C8. AS6 |
| Sheet material price, AS7 | With the makerspace visit |
| JLCPCB shipping cost and delivery time | Their table is an image. Needs a browser, or a real quote |
| **Configuration** — tiltrotor, tailsitter, lift+cruise, tilt-wing, ducted fan | The configuration trade study |
| **Scale** | The configuration trade study |
| Thrust stand — price it, build it, check it against a known mass, AS2 | Before the propulsion system is sized |
| **Design wind speed** — the steady wind the aircraft must hold a hover against. `CONOPS.md` §4.0 | Before the propulsion system is sized, with the thrust stand |
| **Test site**, C14, C18 and AS1 | Before the first flight. 150 m from every residential, commercial, industrial and recreational area, and outside the zones in `RULES.md` NL1 to NL4 — check Aeret Kaartviewer first, GoDrone second |
