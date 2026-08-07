# Needs, Goals, Objectives and Measures of Effectiveness

**Second pass.** We wrote the needs and goals, then wrote `CONOPS.md`, then came back and
corrected this file. Writing the ConOps revealed **three** objectives we had missed:

- **O1.7** maximum hover height and **O1.8** minimum distance to any person, both from scenario
  [DRM-1000], a lift unit failing in hover. That failure cannot be designed against, so the only
  answer is to limit what it costs. Neither objective would have been written without walking
  through it.
- **O1.9** the ability to abandon a changeover and return to hover. Verified in the [DRM-0400]
  flight test plan, since D12 decided a failed changeover is not written as its own scenario.

Recorded as decision D13. That is the process working, not a mistake.

These are **not requirements.** An objective is not a requirement. Requirements are written in
`REQUIREMENTS.md`, after this file is settled.

---

## 1. Need

> **We need an aircraft that does not force a choice between landing anywhere and flying as long
> as a plane.**

**The problem, stated plainly.** Today you have to choose. A rotorcraft lands anywhere but runs
its battery down quickly. A fixed-wing aircraft flies far longer but needs a runway or launch
equipment. Nothing at our price gives both. That forced choice is the problem, and not having to
make it is the need.

**Why this is one need and not two.** Landing anywhere and flying long can be traded against each
other, so at first sight this looks like two needs. It is not, because trading either half away
does not weaken the need — it destroys it. An aircraft that lands anywhere and flies for eight
minutes is a rotorcraft. An aircraft that flies for an hour and needs a runway is a plane. Both
already exist. The need is the combination.

**What this fixed.** An earlier version of this need was about us rather than about the aircraft,
carried the method inside it, duplicated a constraint, and named V/STOL as a given without
explaining it. Runway independence is now part of the problem statement, so **V/STOL follows from
the need rather than being assumed.** Which V/STOL configuration is still open.

## 2. Goals

Goals elaborate the need. A goal does not have to carry a number, but it must let us judge
whether the aircraft achieved it.

| ID | Goal | Descends from |
|---|---|---|
| **G1** | The aircraft operates from an unprepared site: vertical take-off, transition to wing-borne cruise, transition back, vertical landing | The need — "landing anywhere" |
| **G2** | The aircraft beats a comparable multirotor on flight time and distance, and reaches at least **70%** of a comparable fixed-wing aircraft on both | The need — "flying as long as a plane" |
| **G3** | The reasoning is visible. Requirements, trades, tests and flights are recorded so that a reader who was not there can follow them | Project goal. Does **not** descend from the aircraft need |
| **G4** | Both of us do our own hands-on work across aero, structures, electronics and control | Project goal. Does **not** descend from the aircraft need |

**G1 and G2 are not ranked against each other, and this is deliberate.** The need requires both.
Ranking them would reintroduce the forced choice that the need exists to escape.

**G3 and G4 are honestly labelled as not descending from the need.** They are goals about us, and
the need is about the aircraft. Rather than bend the need to cover them, we state that they sit
alongside it. Between those two our original ranking holds: G3 before G4.

**G2 is two-sided on purpose, and the two sides are the two halves of the need.**

- **The floor — beat the multirotor.** A multirotor already lands anywhere. If we do not fly
  longer and further than one, we have built a heavier multirotor and the need is not met. This
  side must be beaten outright, not by a fraction.
- **The target — approach the plane.** A plane already flies long. We will not match it, and the
  reason is physical rather than a lack of skill: a V/STOL aircraft carries hover hardware that a
  plane does not. Those motors, mounts and their share of the battery are dead weight and extra
  drag in cruise. That gap is the price of landing anywhere, and it is the thing our report should
  measure honestly.

**Why 70% and not parity.** Parity with a plane would mean carrying the hover system for free,
which is not possible. On top of the physical penalty, a bought aircraft has a moulded or
composite airframe, a matched propeller, and years of iteration behind it, while we have hand
tools, a 3D printer, no laboratory and one year. In the report, "we reached 74% of a comparable
plane's flight time, and here is where the gap comes from" is a stronger result than a missed
parity target. The fraction is fixed at 70% and can be revised only by a new dated entry in
section 7.

**Comparing against plain drones and plain planes, not against commercial V/STOL aircraft.**
A commercial V/STOL comparison would tell us how good our engineering is against specialists.
The drone-and-plane comparison tells us whether the aircraft solves the problem at all, which is
the question the need actually asks. Published figures are also far easier to find for ordinary
multirotors and ordinary fixed-wing models than for V/STOL products.

**Professional growth is not a goal here.** It is a project goal and it stays in the project
notes. It fails our own test for a goal: there is no state of the world in which we would judge
that it had not been achieved. We reached the same conclusion earlier from the other direction.
Carried here only so that its absence is visible and deliberate.

## 3. Objectives

Every objective must be four things: specific, measurable and verifiable, aggressive but
attainable, and about the result rather than the method — what, not how.

TBD is allowed here. An objective may stay TBD until the trade study that fixes it has been done,
or until the concept of operations settles. TBD is **not** allowed at the requirements freeze,
because an objective has to be shown feasible before requirements are written and the system is
designed.

### Under G1 — the aircraft flies

| ID | Objective | Status |
|---|---|---|
| O1.1 | At least one flight, before the end of the project, containing in sequence: vertical take-off, stable hover, transition to wing-borne cruise, sustained cruise, transition back to hover, vertical landing | Fixed. **Top goal, not a pass mark** — see MOE-1 and decision D9 |
| O1.2 | Stable hover held for at least **TBD** s | TBD — closes at requirements freeze |
| O1.3 | Wing-borne cruise sustained for at least **TBD** s | TBD — closes at requirements freeze |
| O1.4 | Maximum take-off mass below **TBD** kg, and below the EASA Open Category subcategory boundary we choose to fly under | TBD — depends on scale, and on rules we have not yet checked |
| O1.5 | The airframe can be repaired or rebuilt after one crash within **TBD** weeks, using parts we can obtain | TBD — depends on configuration |
| O1.6 | Transition capability is demonstrated by at least one of: a tethered test, a bench test, or logged flight data showing a transition | Fixed. **This is the pass mark** — MOE-1 |
| O1.7 | Maximum hover height **TBD** m, chosen so that a fall from it is survivable for the airframe and harmless to any person | TBD — closes with the configuration and scale. Revealed by writing the ConOps, scenario [DRM-1000] |
| O1.8 | Minimum horizontal distance between the aircraft and any person, **TBD** m, held at all times in hover | TBD — closes with the configuration and scale, and depends on the subcategory conditions in C16. Revealed by writing the ConOps, scenario [DRM-1000] |
| O1.9 | The aircraft can **abandon a changeover and return to hover** under control | Fixed. Verified in the [DRM-0400] flight test plan, per D12. Decision D13 |

O1.2 to O1.5 all depend on scale or configuration, both of which are open. Both close when those
two are chosen.

**O1.1 and O1.6 are deliberately different, and the difference is the whole of decision D9c.**
O1.1 is the complete flight and it is what we design for. O1.6 is the weaker thing that has to be
true for the project to count as acceptable. Without O1.6 written down separately, MOE-1 would
claim to verify O1.1, which it does not — and a measure that does not verify what it points at is
worse than no measure.

### Under G2 — the aircraft performs against its class

Every performance figure is quoted **with the condition it applies to** and **to a stated battery
reserve**, never to empty. A number without its condition is not testable.

| ID | Objective | Status |
|---|---|---|
| O2.1 | Identify two benchmarks at about **€350**, each with published flight time and distance and the conditions those were measured at: **(i)** an ordinary multirotor, **(ii)** an ordinary fixed-wing model | **Unblocked.** C3 is fixed and the aircraft-only figure is derived in section 5. Not yet done |
| O2.2 | Flight time ≥ **TBD** min in still air, at a stated temperature, to a stated battery reserve | TBD — 70% of the fixed-wing benchmark |
| O2.3 | Flight time ≥ **TBD** min in a steady wind of **TBD** m/s, same reserve | TBD. This is the figure that matters in the Netherlands, where calm days are rare |
| O2.4 | Total distance covered ≥ **TBD** km in one flight, to the same reserve | TBD — 70% of the fixed-wing benchmark |
| O2.5 | Battery reserve: **TBD** % remaining at landing | TBD. Needs checking against ordinary practice rather than guessed |
| O2.6 | Flight time and distance both **exceed** the multirotor benchmark outright | TBD. This is a floor, not a fraction. Failing it means we built a heavy multirotor |

**The trap in specifying both flight time and distance, and the guard against it.** Fixing O2.2
and O2.4 fixes the average cruise speed, because distance ≈ flight time × cruise speed. Cruise
speed stops being a free design variable and becomes a derived requirement the aerodynamics must
hit.

That is workable, but only if the two numbers are consistent with each other. **The guard: O2.2
and O2.4 must be taken from the same benchmark aircraft, not the best figure of each from
different aircraft.** Then the implied cruise speed is one a real aircraft achieves. Before either
number is frozen, compute

    v_cruise = distance / flight time

in SI units and check it against the benchmark aircraft's published cruise speed. If the derived
speed is far from anything real, the two targets are inconsistent and one of them is wrong. This
check costs one division and it is the difference between a specification and a wish.

The line-of-sight rule does not block O2.4. Total distance is accumulated flying circuits within
sight. Distance *covered* is legal; distance *away* is not.

### Under G3 — the reasoning is visible

| ID | Objective | Status |
|---|---|---|
| O3.1 | 100% of frozen requirements carry a verification method and a pass/fail criterion | Fixed |
| O3.2 | 100% of configuration, scale and component choices have a dated design log entry naming what was rejected and why | Fixed |
| O3.3 | 100% of entries in `TEST_LOG.md` name the requirement under test | Fixed |
| O3.4 | 100% of flights have a `FLIGHT_LOG.md` entry giving build state, conditions, objective, result, failures and next actions | Fixed |
| O3.5 | The final report contains the trade study behind the configuration choice and behind the scale choice | Fixed |

### Under G4 — hands-on breadth

| ID | Objective | Status |
|---|---|---|
| O4.1 | Each of us makes at least one design decision, performs at least one build task, and runs at least one test, in each of the four areas: aero, structures, electronics, control | Fixed |

O4.1 is written per person on purpose. A team of two can satisfy "the team covered all four areas"
while each person only ever touched two. That is the failure this objective exists to catch.

## 4. Measures of Effectiveness

A Measure of Effectiveness is a measure of success written from the stakeholder's point of view.
The test for whether something belongs here: **failing it makes the stakeholder call the system
unacceptable.** We are the stakeholder, so we are the ones who would have to say it.

Few on purpose.

| ID | Measure | Verifies | Fails if |
|---|---|---|---|
| **MOE-1** | Transition capability is demonstrated — by tethered test, by bench test, or by logged flight data showing a transition. One clean hover→cruise→hover flight is **not** required | O1.6, so G1 | Transition is never shown to work by any of those means |
| **MOE-2** | A reader who was not present can follow any single result back through test, design choice, and requirement, without asking us | G3 | The chain is broken anywhere it is checked |
| **MOE-3** | Each of us worked hands-on in all four areas | O4.1, so G4 | Either of us did not |
| **MOE-4** | The performance objectives are met: at least 70% of the fixed-wing benchmark on flight time and distance, and the multirotor benchmark beaten outright | O2.2, O2.3, O2.4 and O2.6, so G2 | Either the fraction or the floor is missed |

**Why MOE-1 was softened at the same time as MOE-4 was made hard.** Decision D9 in section 7,
which revises D4. G2 carries half the need, so leaving it without a pass mark would have made
half the need decorative. But adding a second hard line while keeping the first one at "one clean
flight on one day" would have given the project two separate ways to fail on weather. Softening
MOE-1 to demonstrated capability keeps the total at one demanding pass mark per half of the need,
and takes the weather lottery out of the one that was most exposed to it.

**What we gave up.** The report can now say "we showed the aircraft transitions" rather than "it
transitioned in flight, here is the log". That is a weaker sentence, and it is the price of the
change. The full transition flight is still the top goal and we still design for it — see G1 and
O1.1. It is simply no longer the thing that decides whether the project failed.

**Not an MOE: professional growth.** We cannot fail it, so it cannot make us call the system
unacceptable. We reached the same conclusion earlier.

### The transition still drives the design, even though it is no longer the pass mark

MOE-1 was a hard line on one complete flight under decision D4. Decision D9 revised that: the
pass mark is now demonstrated capability, and the complete flight is the top goal under O1.1.

**The complete flight has no deadline problem either way.** O1.1 says *at least one flight, before
the end of the project*. Not the first flight, and not a particular day. We get as many attempts
as the schedule allows. A crash in March is a rebuild, which is already in the plan.

**Three consequences of taking the transition seriously, which survive the revision unchanged.**
These came from D4 and D9 explicitly keeps them:

1. The configuration trade study is no longer only a technical choice. Transition risk is
   now project risk, and it must be weighted as such.
2. The value rule below now bites hard. If we choose a configuration with a difficult transition,
   the rule requires us to name lift+cruise as the fallback and to fix the switch date at the
   same time as the choice, not later.
3. The schedule must place the first transition attempt early enough that a failure leaves time
   for a second aircraft or a fallback configuration. Leaving it to the last month means we never
   find out whether O1.1 was reachable.

## 5. Constraints

A constraint is a condition that has to be met.

| ID | Constraint | Status |
|---|---|---|
| C1 | Two people | Fixed |
| C2 | One academic year, roughly 6 to 12 months | Fixed |
| C3 | Budget: **€800 total project spend, hard ceiling.** Not a target. Every purchase comes out of it, including the rebuild | Fixed. Decision D10 |
| C10 | Vertical take-off and landing. The configuration — tiltrotor, tailsitter, lift+cruise, tilt-wing, ducted fan — is open | Follows from the need, not assumed. Closes with the configuration trade study |
| C11 | The remote pilot keeps the aircraft in **visual line of sight at all times**, except in follow-me mode or when using an unmanned aircraft observer. VLOS means continuous **unaided** visual contact. Anything else is the Specific category and needs an authorisation | **Confirmed** — Article 4(1)(d), with VLOS and BVLOS defined in definitions (7) and (8) |
| C4 | We can make: FDM 3D printing in PLA and PETG, soldering and basic electronics, hand tools for foam, balsa and depron. **This list is complete.** No CNC, no laser cutter, no composite layup, no machining | Fixed |
| C5 | **No laboratory.** No wind tunnel, no thrust stand, no load cells, no lab instruments. Any measurement we want, we buy or build ourselves | Fixed. Decision D5 |
| C6 | Maximum take-off mass **below 25 kg**. This is the top of the Open Category | **Confirmed** — Regulation (EU) 2019/947, Article 4(1)(b) |
| C6a | The **900 g** boundary we had been carrying is **probably not ours**. It belongs to the C1 class marking under Delegated Regulation (EU) 2019/945, and a privately built aircraft cannot carry a class mark | **Unconfirmed.** Article 4 does not mention 900 g. We could not read Annex Part A, which holds the subcategory conditions. **Do not design to 900 g until this is settled** |
| C7 | **Operator number** from the RDW. Required for any aircraft with a camera or of 250 g or more. €23. Expires yearly. The number must be **visible on the outside of the airframe** | **Confirmed** — RDW, read 2026-08-04. See `RULES.md` §B1 |
| C15 | **Remote pilot licence** (*vliegbewijs*), subcategory A1/A3. Required from 250 g. €10, valid 5 years, online exam at a recognised Dutch flight school. Must be carried on every flight | **Confirmed** — RDW, read 2026-08-04. See `RULES.md` §B2 |
| C16 | **Where we may fly** — the A1/A2/A3 subcategory conditions decide the distance we must keep from people and buildings | **Not checked.** Annex Part A of 2019/947 could not be opened. **The largest open item in the whole project.** See `RULES.md` §C |
| C8 | Test site must be outside a no-fly zone. The aircraft must be kept at a safe distance from people and must never be flown over assemblies of people | **Confirmed** — Article 4(1)(c). Site not chosen |
| C12 | **Maximum height 120 m** above the closest point of the surface of the earth, except when overflying an obstacle | **Confirmed** — Article 4(1)(e). **New. We did not have this constraint before** |
| C13 | JBV-01 must qualify as a **privately built UAS**: "a UAS assembled or manufactured for the builder's own use, **not including UAS assembled from sets of parts placed on the market as a single ready-to-assemble kit**" | **Confirmed** — 2019/947, definition (16), and Article 4(1)(a) which admits privately built UAS to the Open Category. **Buying a complete ready-to-assemble kit would forfeit this route** and force us onto a class-marked aircraft we cannot obtain |
| C14 | No dangerous goods carried, nothing dropped in flight | **Confirmed** — Article 4(1)(f) |
| C9 | At least one crash and rebuild is planned, not a surprise | Fixed |

**Every rule that binds us, with its source and how well it is checked, is in
`01_requirements/RULES.md`.** The rows above are the short form. If the two ever disagree,
`RULES.md` is right, because that is where the source is recorded.

C6a and C16 have to be closed before the test site can be chosen or ConOps section 4.0 written.

**Three of these are new and one of them changes the design.** C12 caps us at 120 m above the
surface. C13 means we must not buy a complete ready-to-assemble kit, because doing so would stop
the aircraft being "privately built" and put us on a route we cannot take. C14 rules out dropping
anything. None of these was in the project notes we started from.

**How old the source is.** All of the above is confirmed against the EASA consolidated text of
Regulations (EU) 2019/947 and 2019/945, **January 2021 edition**. The regulation has been amended
since. Before the requirements freeze, one of us checks for later amendments and re-confirms every
row marked "Confirmed" above. A regulatory figure is only good on the day it was checked.

**What €800 has to cover, and why the first aircraft is not allowed to cost €800.** A hard ceiling
only works if the things that are not the aircraft are subtracted first. Rough allocation, to be
replaced by the real figures in `04_build/BOM.xlsx` as parts are chosen:

| Line | € | Note |
|---|---|---|
| Transmitter and receiver | 100 | Bought once. Survives every crash |
| Charger, LiPo safe bag, fire precautions | 80 | Bought once |
| Thrust stand — load cell, amplifier, microcontroller | 30 | Required by C5. Bought once |
| **Registration and pilot licence** | **35** | €23 operator number + €10 licence, plus a small margin for the yearly renewal. Required by C7 and C15. See `RULES.md` section B |
| **Rebuild allowance** | **200** | Required by C9. **Not available for the first aircraft** |
| **First aircraft — airframe, propulsion, avionics, battery** | **355** | This is the number that matters below |
| Total | 800 | |

**The benchmark price is €355, not €800.** O2.1 compares our aircraft against commercial aircraft
of comparable price, and a commercial ready-to-fly price does not include a transmitter, a
charger, a rebuild fund or our pilot licence. Comparing our whole project spend against a
commercial sticker price would handicap us by more than €400 before we started. **Round it to
€350 for the benchmark search.**

**A mass consequence, and it is less clear than we first thought.** Five motors and a battery
large enough to hover will put this aircraft well above 250 g, so operator registration under C7
applies. It will very likely be above 900 g too — but see C6a: that boundary belongs to a class
marking a privately built aircraft cannot carry, so it may not apply to us at all. The boundary
we know binds us is 25 kg, C6, and we are nowhere near it. **What actually decides where we may
fly is the subcategory in Annex Part A, which we have not been able to read.**

**C5 is the constraint that costs us the most, and it is worth being blunt about it.** MOE-2 asks
that any result can be followed back to the requirement it verifies. A result we never measured
cannot be followed anywhere. With no laboratory, every number we want on the right branch of the
V has to come from equipment we own. Three consequences:

1. **Thrust, current and RPM.** These have to be measured, because the whole propulsion sizing
   rests on them. The ordinary hobby answer is a home-made thrust stand — a load cell, an
   amplifier board, and a microcontroller. Cheap, and we can build it. It has to be priced,
   built, and itself checked against a known mass before we trust it. That is now a piece of work
   in its own right, not an assumption.
2. **Mass and centre of gravity.** A kitchen scale and a balance beam are enough. No problem here.
3. **Aerodynamic coefficients.** There is no substitute we can build. Lift, drag and stall
   behaviour will come from published aerofoil data and software, not from measurement. **Every
   one of these must be written down as an estimate, never as a measurement.** Where a design
   decision rests on an estimate, the first flight test of that decision becomes the real
   verification, and the flight test plan has to say so.

## 6. Assumptions

Written down because an assumption that is never written is never checked.

Prefixed **AS** rather than A, because A1, A2 and A3 already mean the Open Category subcategories
in the regulation, and we cannot rename those.

| ID | Assumption | Checked? |
|---|---|---|
| AS1 | A legal test site exists within reasonable travel of us | **No** |
| AS2 | We can build a thrust stand accurate enough to size the propulsion system, within budget | **No.** Needs pricing and a build |
| AS3 | Off-the-shelf hobby parts adequate for our scale are available in the EU within our budget | **No** |
| AS4 | A proven open-source flight controller stack supports whichever configuration we choose | Partly. ArduPilot's ArduPlane documents QuadPlane, tilt-rotor and tailsitter frame support. Not verified on hardware by us |
| AS5 | An ordinary multirotor and an ordinary fixed-wing model exist at our price point with published flight time and distance figures, given with the conditions they were measured at | **No.** If the published figures turn out to be marketing numbers with no stated conditions, the benchmark is worthless and G2 needs a different anchor. More likely to hold now than when the comparison was against V/STOL products, because these figures are widely published |

## 7. Decisions

Dated, and not to be rewritten. A change goes in as a new dated entry below.

These are decisions about the requirements baseline, and none of them yet traces to a
requirement, because no requirement exists. They are recorded here rather than in
`02_concept/DESIGN_LOG.md`, which starts when configuration trades start.

### 2026-08-04 — D1: We are the only customer

**Chosen:** the two of us are the customer. There is no supervisor and no examiner setting
acceptance criteria.
**Rejected:** a supervisor or grader as customer, which would have given an external check and a
real sign-off on the expectations.
**Why:** it is what is true. Inventing an external customer we do not have would produce criteria
nobody enforces.
**Cost accepted:** no external brake on requirements creep. Carried into ConOps section 7.0 as a
risk.

### 2026-08-04 — D2: The Need statement

> **Superseded the same day by D6, and the final wording fixed by D9a.** The entry below is kept
> as written. What changed: this need was about us rather than about the aircraft, it carried our
> method inside it, it duplicated constraint C1, and it named V/STOL without deriving it.

**Chosen:** "We need to demonstrate that the two of us can take a V/STOL aircraft from
requirements through to verified flight."
**Rejected:** an aircraft-first need statement. It is satisfied by an undocumented aircraft, and
it biases trades towards performance.
**Rejected:** a learning-first need statement. Nothing in it requires the aircraft to fly.
**Why:** *demonstrate* requires the aircraft and the record together, in one singular statement,
so neither can be traded away against the other.

### 2026-08-04 — D3: The value rule, with a level line added

**Chosen:** our original clause is kept. Learning wins where the thing is not too complicated for
us, and "too complicated" is decided at the moment of the decision by two questions:

1. Does a proven off-the-shelf fallback exist, and can we afford it?
2. What is the date by which we switch to the fallback if ours is not working?

If both have answers, take the ambitious path. If either does not, take the proven one.

**Added later — the level line.** The two-question test applies where a substitute product
or a substitute method exists: configuration, avionics, propulsion, control software. It does not
apply to airframe and aerodynamic design, where no off-the-shelf substitute for our own wing
exists. There the rule is simpler: prefer the simpler method.
**Why the line was added:** a test that cannot be answered gets ignored, and a rule that is
ignored is not a rule.
**Checked against the page, not remembered:** the ArduPilot Plane wiki page "QuadPlane Frame
setup" states that the QuadPlane code supports quad, hexa, octa and octaquad lifting arrangements,
tilting motors for transition, and tailsitters, selected through `Q_FRAME_CLASS` and
`Q_FRAME_TYPE`. So a proven fallback exists at configuration level and at software level. It does
not exist at airframe level.

**A correction to an earlier version of this entry.** We first wrote that the wiki "describes the
Quad-X quadplane as the straightforward setup". It does not. The page calls Quad-X the *default*
frame and gives its motor ordering on outputs 5 to 8. The word "straightforward" came from a
search engine summary, not from the page. The conclusion is unchanged — Quad-X is the default and
therefore the best-supported path — but the claim we wrote was not one the source makes.

### 2026-08-04 — D4: The full transition is a hard MOE

> **Revised the same day by D9c.** The entry below is kept as written. What changed: the full
> transition is no longer the pass mark. It is the top goal. The three consequences at the end of
> this entry still stand.

**Chosen:** MOE-1. If JBV-01 never completes a full transition flight, the project has failed.
**Rejected:** treating the transition as the top goal with a softer MOE built on hover, cruise and
a diagnosed transition attempt.
**Rejected:** an MOE on demonstrated transition capability by tethered or bench test rather than
by flight.
**Why:** we want the strongest claim, and a hard line forces every design choice towards making
the transition work.
**Cost accepted:** project success now rests on the hardest thing the aircraft does. The three
consequences are listed in section 4 above and must be carried into the schedule and into the
configuration trade study.

### 2026-08-04 — D5: The university is out of the project

**Chosen:** JBV-01 is built entirely with our own tools and our own money. No university lab, no
university equipment, no university as a stakeholder. This completes D1 — there was already no
supervisor and no examiner.
**Rejected:** carrying the university as an interested party with unknown lab capability, which
would have left an open question we were never going to close.
**Why:** it is what is true, and an assumed capability is worse than a known absence. We were
about to size a propulsion system against a thrust stand nobody had promised us.
**Cost accepted:** constraint C5. No wind tunnel, no thrust stand, no load cells, no CNC, no
laser cutter, no machining, no composite layup. Aerodynamic numbers become estimates rather than
measurements, and we have to build our own thrust stand before we can size anything.
**What this makes better:** every capability we now claim is one we actually control. Nothing in
the plan waits on someone else's permission.

### 2026-08-04 — D6: The Need is rewritten around the forced choice

**Chosen:** the need is about the aircraft, and states a problem — that today you must choose
between landing anywhere and flying long, and we want an aircraft that does not force that
choice. Final wording fixed the same day, see D9.
**Rejected:** the earlier "demonstrate that the two of us can take a V/STOL aircraft from
requirements through to verified flight". Four faults: the subject was us rather than the
aircraft, it contained our own method, it duplicated constraint C1, and it named V/STOL as a
given without explaining it.
**Rejected:** "a long-range aircraft capable of operating in almost any conditions". Range is
capped by the visual line of sight rule, "almost any conditions" cannot be tested, and the
sentence contained two capabilities that trade against each other.
**Why:** runway independence is now inside the problem statement, so V/STOL follows from the need
instead of being assumed. The fault we had recorded and dodged is now actually fixed.
**Cost accepted:** goals G3 and G4 no longer descend from the need. They are labelled as project
goals sitting alongside it rather than under it.

### 2026-08-04 — D7: Performance is benchmarked at 70% of the commercial class

> **Revised the same day by D9b.** The entry below is kept as written. The 70% figure stands.
> What changed: the benchmark is no longer a commercial V/STOL aircraft. It is an ordinary
> multirotor to beat outright, and an ordinary fixed-wing model to reach 70% of.

**Chosen:** G2 targets at least 70% of the flight time and distance of a commercial aircraft of
comparable price.
**Rejected:** full parity. Commercial airframes use moulding and composites we cannot make, and
parity on a first build in one year would add a second coin toss.
**Rejected:** beating the class. Highest risk, and it would consume the time the transition work
needs.
**Rejected:** an absolute number chosen by us. It was our first answer, and we changed it once it
was clear that a benchmark answers "why that number" and an invented figure does not.
**Cost accepted:** the benchmark cannot be identified until the budget number C3 is written down.
G2 is blocked until then. Assumption AS5 records the risk that published commercial figures come
without stated conditions and turn out to be unusable.

### 2026-08-04 — D8: Flight time and distance are both specified, cruise speed is derived

**Chosen:** O2.2 and O2.4 both carry numbers. Cruise speed is whatever falls out of them.
**Rejected:** specifying flight time alone and letting distance follow, which would have kept
cruise speed as a free design variable for the aerodynamics.
**Why:** total distance is part of what we want, and leaving it derived would have left it
unstated and therefore untested.
**Cost accepted:** cruise speed becomes a derived requirement the aerodynamic design must hit,
not a variable it can choose. Guard written into section 3: both numbers must come from the same
benchmark aircraft, and the implied cruise speed must be checked against that aircraft's
published figure before either number is frozen.

### 2026-08-04 — D9: The Need wording, and a revision of D4

Three linked choices, recorded together because each depends on the others.

**9a — The Need is fixed as:** *"We need an aircraft that does not force a choice between landing
anywhere and flying as long as a plane."*
**Rejected:** the alternative candidate, "an aircraft that can operate from an unprepared site
without giving up the flight time of a fixed-wing aircraft of the same price". Same meaning, but
it reads as a specification. The chosen wording names the problem — the forced choice — rather
than the solution, which is what a need is for.

**9b — The benchmark is an ordinary multirotor and an ordinary fixed-wing model, not a commercial
V/STOL aircraft.**
**Rejected:** benchmarking against commercial V/STOL products.
**Why:** the need says "as long as a plane", so the plane is the benchmark the need itself names.
A V/STOL comparison would have told us how we rank against specialists. This comparison tells us
whether the aircraft solves the problem at all. It also makes G2 two-sided, which mirrors the two
halves of the need: beat the multirotor outright, reach 70% of the plane.
**Practical gain:** flight time and distance figures are widely published for ordinary multirotors
and fixed-wing models, which lowers the risk recorded in assumption AS5.

**9c — MOE-4 is a hard pass mark, and MOE-1 is softened. This revises decision D4.**
D4 made one complete transition flight the pass mark for the whole project. That is no longer the
case.
**Chosen:** MOE-1 becomes demonstrated transition capability — tethered test, bench test, or
logged flight data showing a transition. MOE-4 becomes a hard pass mark on the performance
objectives.
**Why the revision:** G2 now carries half the need. Leaving it without a pass mark would have made
half the need decorative. But making it hard while MOE-1 still required one clean flight on one
day would have given the project two separate ways to fail on weather. One demanding pass mark
per half of the need, and the weather lottery removed from the half most exposed to it.
**Cost accepted:** the report will say "we showed the aircraft transitions" rather than "it
transitioned in flight, here is the log". A weaker sentence. The full transition flight remains
the top goal under G1 and objective O1.1, and we still design for it — it simply no longer decides
whether the project failed.
**What D4 got right and we are keeping:** the first transition attempt still has to sit early
enough in the schedule to leave room to recover from a failure, and the configuration
trade still has to weight transition risk as project risk.

### 2026-08-04 — D10: Budget is €800, as a hard ceiling

**Chosen:** €800 total project spend for the year, as a ceiling we do not cross, not a target.
The figure is the midpoint of the €700–900 range we agreed we could afford.
**Rejected:** €400–550. It funds one small aircraft and no rebuild, so the first crash would end
the project. It also forces a small airframe, which makes the endurance half of the need harder.
**Rejected:** €1200–1500. It would have let us build the proven fallback airframe alongside the
ambitious one, which is what the value rule in D3 asks for. We cannot afford it.
**Rejected:** a target with a held-back reserve, and a per-person split. A single ceiling is the
simplest thing that works, and the trade study can then reject any configuration we cannot buy.
**Why a ceiling and not a target:** a target is something you go over. Against a ceiling, the BOM
becomes a running total, and "we cannot afford this configuration" becomes a real answer in the
trade study rather than an argument.
**Cost accepted:** we cannot build the fallback airframe in parallel. If the trade study picks a
hard-transition configuration, the value rule's fallback has to be reached by *rebuilding* the
same aircraft, not by having a second one ready. That makes the switch date in D3 more important,
not less — we will not be able to change our minds quickly.
**Derived and recorded in section 5:** the first aircraft gets €355 of the €800. That is also the
price we benchmark against in O2.1, rounded to €350. The figure moved from €390 once decision D11
added the €35 line for registration and the pilot licence.

### 2026-08-04 — D11: The Open Category rules are confirmed from the regulation, not from a FAQ

**What we did:** read Article 4 of Regulation (EU) 2019/947 in the EASA consolidated text. We had
been carrying rules from our own project notes and from a search summary. The EASA website FAQ
could not be opened at all — it is built by JavaScript and returns an empty page — so we went to
the law instead, which is a better source anyway.

**What was confirmed:** the visual line of sight rule, C11. The 25 kg ceiling, C6. Safe distance
from people and no flying over assemblies, C8. And that a **privately built** aircraft is admitted
to the Open Category at all, C13, which is the route JBV-01 depends on.

**Three things we did not know before:**

1. **A 120 m height ceiling**, C12. Article 4(1)(e). It was in none of our notes.
2. **"Privately built" excludes ready-to-assemble kits**, C13. If we buy a complete kit, JBV-01
   stops being privately built and needs a class marking we cannot obtain. This is a purchasing
   rule, not just a paperwork detail, and it belongs in the BOM.
3. **Nothing may be dropped in flight**, C14.

**One thing we got wrong and have corrected:** we had been carrying a 900 g boundary since the
start. It does not appear in Article 4. It belongs to the C1 class marking under Delegated
Regulation (EU) 2019/945, and a privately built aircraft cannot carry a class mark. It is
therefore **probably not our boundary at all**, which would remove a constraint we had been
treating as hard. Recorded as C6a and marked unconfirmed, because we could not read the Annex.

**What is still not confirmed, and why it matters:** Annex Part A holds the A1, A2 and A3
subcategory conditions. Those decide how far from people we must fly. The PDF extraction stopped
before them. Until we have them, the test site cannot be chosen and O1.4 cannot be closed.

**Age of the source:** January 2021 consolidation. Amendments since then are unchecked.

### 2026-08-05 — D12: Mission, instruments, FPV, and one scenario we chose not to write

**Mission chosen:** pure demonstrator. The aircraft carries nothing beyond what it needs to fly.
The flight profile is the mission.
**Rejected:** an observation mission carrying a camera, and a carry-a-load mission. Both take mass
from the battery, and the battery is where the endurance in G2 comes from. Neither is required by
the need, which is about capability rather than application.

**Instruments chosen:** on-board flight data logging, and live telemetry to the ground.
**Why logging:** MOE-1 accepts logged flight data as proof of changeover, and every endurance
figure in G2 rests on it.
**Why live telemetry:** without it the battery reserve is discovered after landing rather than
during flight. Scenario DRM-0900 depends on it.
**Rejected:** flying with nothing beyond the minimum. It would have put every endurance number on
a stopwatch and made MOE-1 depend on a bench demonstration.

**FPV chosen:** fitted **later**, as a piloting aid, not on the first aircraft.
**Rejected:** fitting it from the start, and making the camera view the mission, and dropping it
entirely.
**Why later:** it lets us measure the G2 endurance figures clean, and then measure again with FPV
fitted. The cost of FPV in minutes of flight is a number worth having, and this is the only order
in which we can get it.
**Legal consequence, confirmed:** a pilot wearing goggles does not satisfy the visual line of
sight rule. Article 4(1)(d) permits it only with an unmanned aircraft observer. So once FPV is
fitted, **both of us must be present at every flight**. The detailed conditions on the observer
are in Annex Part A, which we still cannot read.
**Budget consequence:** goggles are ground equipment and are not in the €800 allocation. Analog
gear is the only affordable route; digital goggles alone cost more than our whole first aircraft.

**One scenario we chose not to write: a failed or stalled changeover.**
**Chosen:** handle it in the flight test plan for DRM-0400 rather than as a ConOps scenario.
**Rejected:** writing it as a fourth off-nominal scenario.
**Recorded honestly:** it is the failure most likely to happen to us, and it is the one MOE-1 is
about. If the DRM-0400 test plan is thin, nothing else catches it. Carried into ConOps section 7.0
as a risk so the gap stays visible.

### 2026-08-07 — D13: What writing the ConOps changed

The order was deliberate: needs and goals first, then `CONOPS.md`, then back to this file. Walking
through the operational scenarios found things the goals alone had not.

**Three new objectives.**

- **O1.7 and O1.8** — maximum hover height, and minimum distance between the aircraft and any
  person. Both came from scenario [DRM-1000], one lift unit failing during hover. On most V/STOL
  layouts that failure is not recoverable and the aircraft falls. Since we cannot design against
  it, the only honest answer is to limit the consequence: hover low, and keep people back. These
  are the only two objectives in this file that exist to protect a person rather than the project.
- **O1.9** — the ability to abandon a changeover and return to hover. We had written that the
  changeover must work. We had never written that it must be possible to stop trying. Verified in
  the [DRM-0400] flight test plan, not as its own scenario, per D12.

**Two capabilities promoted, recorded in `CONOPS.md` §3.5.** Live telemetry to the ground became a
required capability rather than a nice-to-have, because the abort rule in [DRM-0900] is impossible
without it. And carrying the operator number became an interface requirement on the outside
surface of the airframe, `CONOPS.md` §3.3 — a flat, reachable place that survives weather and a
crash.

**Reconciled with D12, which is older and which wins.** This entry originally added a scenario for
a failed changeover and stated that no camera would ever be carried. D12 had already decided both
questions the other way. What now stands:

1. **A failed changeover is not a scenario.** It is handled in the [DRM-0400] flight test plan.
   The risk D12 recorded stands with it — if that test plan is thin, nothing else catches the
   failure we are most likely to meet. Written into `CONOPS.md` §6.2 so it stays visible.
2. **First-person view is fitted later**, as a piloting aid, not on the first aircraft. Added to
   `CONOPS.md` §3.5 as capability 13, with the consequence D12 established: goggles do not satisfy
   the visual line of sight rule, so once it is fitted **both of us must be present at every
   flight**, one flying and one watching the aircraft unaided. Goggles are ground equipment and
   sit outside the €800.

**One numbering conflict fixed.** Two objectives had both been numbered O1.7, and two decisions had
both been numbered D12. The hover height objective keeps O1.7 and the changeover-abort objective
became O1.9; the older decision keeps D12 and this entry became D13.

---

## What is still open

| Item | Closes at |
|---|---|
| The two benchmark aircraft at about €350, O2.1, and the figures in O2.2 to O2.6 | **Next.** Then check the derived cruise speed before freezing anything |
| Battery reserve percentage, O2.5 | With the benchmark. To be checked against ordinary practice, not guessed |
| **Annex Part A of 2019/947** — the A1/A2/A3 subcategory conditions, C6a | Needs a browser. Blocks the test site and O1.4 |
| **RDW registration** — cost, duration, marking, C7 | Needs a browser |
| Amendments to 2019/947 since January 2021 | Before the requirements freeze |
| Configuration — tiltrotor, tailsitter, lift+cruise, tilt-wing, ducted fan | The configuration trade study |
| Scale, and therefore O1.2 to O1.5 | The configuration trade study |
| Thrust stand — price it, build it, check it against a known mass, AS2 | Before the propulsion system is sized |
| Current EASA and RDW rules, C6 and C7 | Before ConOps section 2.1 is written |
| Test site, C8 and AS1 | Before the first flight, and it constrains scale, so earlier is better |
| The ConOps itself | Next |
