# JBV-01 — Functions

**What this file is.** Every function the aircraft must perform, written as *what it must do* and
never as *what does it*. It is the first half of Stage 3 — NASA SEH Rev 2, Section 4.3, logical
decomposition. The configuration trade study **reads** this file. It does not write it.

**Why the separation matters here and not on an ordinary aeroplane.** On a normal aircraft, function
and form match one to one: the wing lifts, the propeller pulls, the tail steadies. On a V/STOL
aircraft they do not. Something must produce lift at zero airspeed. Something must produce lift with
airspeed. Something must produce forward thrust. Something must produce control moments while the
control surfaces still have too little airflow to work. **Whether those are the same devices or
different devices is the configuration choice.** Naming a device anywhere in this file would make
that choice by accident, before the trade study ran.

**Pass 1, written 2026-09-16 and frozen.** Written from `CONOPS.md` alone, before any configuration
was named, as Stage 3 decision 1 requires. See `00_management/STAGE_3_NOTES.md`, **Settled**.

**Pass 2 rule.** After concept generation this file may change. Every change records what changed,
why, and **which candidate exposed it**, in the change log at the end. A change with no log entry is
a mistake, not an edit.

**Why the detail is uneven, and that being deliberate.** Group A carries NASA 4.3's full description
— inputs, outputs, failure modes, consequence of failure, interfaces — because group A is where the
configuration decision lives. Groups B and C carry the function statement only. Their detail is
written when a candidate needs it. Settled 2026-09-08.

**One formal gap, recorded.** NASA 4.3's first input is a frozen requirement set, and
`REQUIREMENTS.md` does not exist yet. But 4.3 also says functional analysis *"is usually based on the
ConOps for the system of interest"*, and our ConOps does exist. So pass 1 is drafted from the ConOps
now and **must be checked against L1 on the day L1 freezes.** That check is not optional and it is
not the same thing as pass 2.

**No numbers appear in this file.** Where a function has a figure, the figure lives in its
constraint or objective and is cited by ID. This file says what must happen, not how much.

---

## Group A — the flight functions

The eight functions that a configuration answers. Every row of the morphological matrix will come
from this group.

### F1 — Produce lift at zero airspeed

| | |
|---|---|
| **Inputs** | Energy from the store (F12); a commanded vertical force; the aircraft's mass and its attitude |
| **Outputs** | An upward force: greater than weight to leave the ground, equal to weight in steady hover, less than weight in a controlled descent |
| **Failure modes** | Not enough force; asymmetric force; loss of part of the function; a runaway that cannot be commanded down |
| **Consequence of failure** | On the ground, no take-off. In the air, an uncontrolled descent or a roll-over. This is [DRM-0900], and the ConOps risk table already calls it *usually not recoverable* and the only failure that can hurt someone |
| **Interfaces** | F5 (if the same devices also produce hover control moments), F9, F12, F15, and the ground interface in `CONOPS.md` §3.3 |

### F2 — Produce lift in wing-borne flight

| | |
|---|---|
| **Inputs** | Airspeed; air density; the aircraft's attitude relative to the airflow |
| **Outputs** | An upward force equal to weight, produced by the airflow rather than by expending energy directly |
| **Failure modes** | Airspeed too low for the weight; stall; asymmetric loss of lift |
| **Consequence of failure** | The aircraft descends or departs controlled flight. **This has no planned answer.** The ConOps records that the unpowered descent capability was deleted on 2026-09-08, and that a propulsion failure in wing-borne flight therefore ends in a fall. Accepted, not overlooked |
| **Interfaces** | F3 (which supplies the airspeed), F7, F9 |

### F3 — Produce forward thrust in wing-borne flight

| | |
|---|---|
| **Inputs** | Energy from the store (F12); a commanded thrust |
| **Outputs** | A forward force that balances drag in steady cruise and accelerates the aircraft when more is commanded |
| **Failure modes** | Not enough thrust to hold cruise; total loss; asymmetric thrust producing an unwanted yaw |
| **Consequence of failure** | Airspeed falls until F2 can no longer carry the weight, and F2's consequence follows |
| **Interfaces** | F2, F9, F12, F15 |

### F4 — Change between hover and wing-borne flight, in both directions

| | |
|---|---|
| **Inputs** | The current flight state; a command to begin; time |
| **Outputs** | A change of the lift-producing mechanism from F1 to F2, and back, **with no interval in which neither carries the weight** |
| **Failure modes** | The change stalls part-way; it happens faster than the control function can follow; it cannot be reversed; the two lift sources work against each other during the overlap |
| **Consequence of failure** | Loss of the aircraft. This is the central risk of the project, and it is why G2-O5 exists as a gate rather than as a pass mark |
| **Interfaces** | Every function in group A, plus F15 and F19 — the log is how both transitions are judged |

### F5 — Produce control moments in hover

| | |
|---|---|
| **Inputs** | A commanded attitude or rate; the sensed state (F14) |
| **Outputs** | Pitch, roll and yaw moments large enough to hold attitude against a disturbance **with margin left** |
| **Failure modes** | Not enough authority on one axis; saturation, so a further command produces nothing; cross-coupling, where a command on one axis moves another |
| **Consequence of failure** | The pilot reaches full stick travel, and G2-O1 fails by its own written criterion |
| **Interfaces** | F1 (if the same devices produce both), F14, F15 |

### F6 — Produce control moments during the change

| | |
|---|---|
| **Inputs** | As F5, but through a flight state that is changing continuously |
| **Outputs** | Sufficient moments at **every** point of the change, including the part where the control surfaces have too little airflow to be effective and the lift devices may be partly re-pointed |
| **Failure modes** | A gap in authority part-way through; a handover between two mechanisms that is not continuous; authority that depends on airspeed arriving before it does |
| **Consequence of failure** | The aircraft departs controlled flight in the phase with the least margin. G2-O2 fails |
| **Interfaces** | F4, F5, F7, F14, F15 |
| **Note, from a source and not from us** | ArduPilot's tailsitter documentation states that during transitions *"pilot input is disabled"* and attitude and throttle are controlled entirely by the autopilot. On at least one layout, then, this function belongs wholly to the control function and not to the pilot — which changes what G2-O2's criterion can mean. Carried here so the trade study cannot miss it |

### F7 — Produce control moments in wing-borne flight

| | |
|---|---|
| **Inputs** | A commanded attitude; airspeed; the sensed state (F14) |
| **Outputs** | Pitch, roll and yaw moments at cruise airspeed |
| **Failure modes** | Not enough authority; authority that falls away or reverses as airspeed drops; structural coupling with the airframe |
| **Consequence of failure** | Loss of control in the phase that is meant to be the easy one, and the phase G1-O2 requires for more than half the flight |
| **Interfaces** | F2, F9, F14, F15 |

### F8 — Abandon a change and return to the previous flight state

| | |
|---|---|
| **Inputs** | A command to abort; the current partial state |
| **Outputs** | A controlled return to the state the aircraft came from |
| **Failure modes** | The abort is impossible past some point in the change; the abort itself is uncontrolled; the point of no return is not known to the pilot |
| **Consequence of failure** | G2-O4 fails. Worse than the objective failing: **every transition attempt becomes a commitment**, so the first one is flown with no way out |
| **Interfaces** | F4, F6, F15, F19 |

---

## Group B — structure and energy

Statement only. Detail is written when a candidate needs it.

| ID | Function |
|---|---|
| **F9** | Carry the loads of hover, cruise, the change between them, and landing |
| **F10** | Survive taking off from and landing on unprepared ground — grass, soil, gravel; not a runway and not a prepared pad |
| **F11** | Accept a physical restraint, so that flight can be tested without free flight |
| **F12** | Hold the energy for one flight and deliver it on demand, with a reserve still held at landing |
| **F13** | Allow the energy store to be removed, replaced and charged away from the aircraft |

---

## Group C — control, command and information

Statement only. Detail is written when a candidate needs it.

| ID | Function |
|---|---|
| **F14** | Sense what the aircraft is doing |
| **F15** | Move the right things so that the aircraft does what was commanded |
| **F16** | Return to the trimmed state after a disturbance, **with no pilot input** |
| **F17** | Receive the pilot's commands, throughout the flight and to the limit of what can be seen |
| **F18** | Send the aircraft's state to the ground while it is flying |
| **F19** | Record what happened during the flight, **including transmitter stick positions** |
| **F20** | Act safely on a fault, without waiting for a pilot command |
| **F21** | Be armed and disarmed deliberately, with no ambiguity about which state it is in |

**F16 is stability and F15 is controllability.** They are separate functions for the same reason
`NGO.md` §2 keeps them as separate properties: an aircraft can be stable and hard to command, or
unstable and easy to command. Almost every multirotor is the second.

**F19 is load-bearing beyond its own row.** MOE-1 and all three G2 criteria are read off the log,
and G2-O1 and G2-O2 are decided by whether the pilot ever needed full stick. If the log does not
hold stick positions, those criteria have to change — which is still an open item in `NGO.md` §8.

---

## What was considered and left out

Recorded because a list nobody can check what was excluded from is not a short list, it is a
careless one. Same rule as the twelve-area walk in Stage 2.

| Considered | Why it is not a function here | Where it lives instead |
|---|---|---|
| Be transported to the test site | It is a property the airframe must have, not something the aircraft does in flight. But it is **not harmless** — C18 puts the site out of town, so span and whether the airframe comes apart are decided by it | The requirement set, from C18. Also a scored criterion in the trade — `STAGE_3_NOTES.md` decision 3 |
| Be repaired or rebuilt after a crash | Same reason. C4 plans a crash and the rebuild allowance assumes the aircraft can be rebuilt | The requirement set, from C4. Also a scored criterion |
| Carry the operator number visibly on the outside | Same reason, and this one is **law** | The requirement set, from C22. `CONOPS.md` §3.3 already carries it as a real interface, not as paperwork |

**The risk in dropping these three, stated plainly.** All three are real, two of them decide the
airframe's shape, and one of them is a legal requirement for flying at all. They are safe here only
because each already has a home in a constraint. **If any of those three constraints is ever
relaxed, nothing in this file will notice.**

---

## Change log — pass 2

Pass 1 is frozen. **A correction found in a review is allowed, with a row here.** Its last column then says *None — found in review*.

Format, one row per change:

| Date | What changed | Why | Which candidate exposed it |
|---|---|---|---|
| 2026-10-14 | F8 interfaces: added F19 | G2-O4 is judged off the log, as F4's transitions are | None — found in review |

**Read this log before trusting the list.** If several entries name the same candidate, that is a
signal: either that candidate is doing work the others are not, or we understood it better because
one of us preferred it. Stage 3 decision 1 exists to make that visible.
