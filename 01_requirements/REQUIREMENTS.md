# JBV-01 — System requirements

**Level: aircraft only (L1).** No subsystem requirement is written here before the configuration
trade. Subsystem requirements (L2) are written after the trade, reviewed with the same six
questions, and frozen as `req-v2` (#21). `00_management/STAGE_2_NOTES.md`, Settled 1.

**No mass requirement at L1.** Mass is a TPM, tracked in `04_build/MASS_BUDGET.xlsx`. **A derived
mass target is the first thing the configuration trade must produce.** Settled 2.

**"Shall" only.** One "shall" per requirement, as a complete sentence. No "should", no "will".
Settled 5.

**Verification methods** are NASA's four: test, analysis, inspection, demonstration. Analysis alone
verifies a requirement only when it is arithmetic with no model inside, and every input is a
measurement of ours or a figure from a named document (`NGO.md` §8, #6).

**Columns are our own set:** statement, area, parent, rationale in NASA's four parts, verification
method, pass/fail, KDR, status. NASA Table D-1 was not read (`STAGE_2_NOTES.md` §5).

**KDR — Key Driving Requirement:** a requirement that can change cost or schedule by a lot.

**Numbers** are tagged *law*, *derived* (formula and inputs) or *chosen* (and what changes if it is
wrong).

**IDs** R1, R2, … are flat, encode nothing, and are never reused. Settled 6.

**Log names.** A pass/fail criterion says what the flight log must show. Where ArduPilot record
names are given (AS4), they come from the ArduPilot source — `ArduPlane/Log.cpp`, `quadplane.cpp`,
`tailsitter.cpp`, master branch of 31 Oct 2026. `RCIN` is confirmed in a SITL log (#4). The other
records are not yet seen in a log of ours.

---

## 1. Requirements from G1

### R1 — The full profile in one flight

| | |
|---|---|
| **Statement** | JBV-01 shall fly one flight that contains, in this order: vertical take-off, hover, transition to wing-borne flight, wing-borne cruise, transition to hover, and vertical landing. |
| **Area** | Functional |
| **Parent** | G1-O1, under G1. Verifies MOE-1 |
| **Rationale** | **Reason:** G1-O1 is the pass mark of the project (MOE-1). Without R1, nothing asks for the whole profile in one flight: each phase could be shown on a different day. **Assumptions:** the log holds flight mode, transition state and flying state (R4). **ConOps:** capabilities 1, 3 and 5; [DRM-0500]. **Design constraint:** C10 — vertical take-off and landing, configuration open |
| **Verification** | Demonstration, [DRM-0500] |
| **Pass/fail** | Pass if the log of one flight shows the six phases in the order of the statement, each phase read as defined in §3. Fail otherwise |
| **KDR** | Yes. The transition decides the configuration, most of the cost and most of the schedule |
| **Status** | Draft, 2026-11-11 |

### R2 — Flight time, more than half of it wing-borne

| | |
|---|---|
| **Statement** | JBV-01 shall fly for more than 5 min from lift-off to landing, with more than half of that time in wing-borne flight. |
| **Area** | Performance |
| **Parent** | G1-O2, under G1 |
| **Numbers** | **5 min** — chosen 2026-09-08 (G1-O2). If wrong, the battery and the wing are sized wrong. **More than half** — chosen 2026-09-08 (G1-O2). If lower, the wing stops being necessary; if higher, the hover and transition time may not fit |
| **Rationale** | **Reason:** G1-O2. Flight time alone can be passed by hovering; the wing-borne share is what makes the wing necessary. **Assumptions:** take-off, hover check, both transitions, descent and landing take about 1.5 to 2 min (estimate from ordinary practice, `NGO.md` §3, not measured). If the rest of a 5 min flight is cruise, the wing-borne share is derived as (5 − 2) / 5 = 0.60 to (5 − 1.5) / 5 = 0.70. The margin over 0.5 is 0.10 to 0.20, and rests on that estimate. Wing-borne time includes any VTOL-assist time (§3, known weak spot), so R2 can pass with the lift motors helping. **ConOps:** capability 4; [DRM-0600]; [DRM-0800]. **Design constraint:** C11 — the flight is measured to the battery reserve; C3 — money |
| **Verification** | Test, [DRM-0600]. All three figures are read from the log |
| **Pass/fail** | Pass if all three hold: (1) t_flight = t_landing − t_lift-off > 300 s, with lift-off and landing from the flying state (ArduPilot: `STAT.isFlying`); (2) t_wing-borne / t_flight > 0.5, with wing-borne time as defined in §3; (3) the battery is at or above the C11 reserve at landing, judged as in R12. Fail if any one does not hold |
| **KDR** | Yes. Flight time and the wing-borne share set the battery and the wing, and so the loop of mass, thrust and battery |
| **Status** | Draft, 2026-11-11 |

### R3 — Unprepared ground

| | |
|---|---|
| **Statement** | JBV-01 shall take off from and land on unprepared ground. |
| **Area** | Environment |
| **Parent** | G1 ("from an unprepared site"), and the need: no runway |
| **Rationale** | **Reason:** runway independence is half of the need (`NGO.md` §1). Without R3, R1 could pass from a pad or with a launch aid. **Assumptions:** the test site surface is grass, soil or gravel; the site is not found yet (AS1). **ConOps:** §3.3 ground interface; §4.0 landing surface; glossary "unprepared ground"; F10. **Design constraint:** C18 puts the site in open country |
| **Verification** | Demonstration, [DRM-0300], and again in [DRM-0500] |
| **Pass/fail** | Pass if JBV-01 takes off from and lands on the natural surface of the test site, with nothing laid on the ground and no launch aid; comes to rest in its normal ground attitude; and flies again with no repair. Fail otherwise |
| **KDR** | Yes. Landing gear, propeller clearance above the ground and tipping over on soft ground differ a lot between layouts |
| **Status** | Draft, 2026-11-11 |

### R4 — Flight record

| | |
|---|---|
| **Statement** | JBV-01 shall record, from arming to disarming, its flight mode, transition state, flying state, attitude, height, motor and servo outputs, battery voltage, battery current, charge used, and the pilot's stick positions. |
| **Area** | Interface — aircraft to us, through the log file |
| **Parent** | G1-O1 and G1-O2 (judged from the log). Also serves G2-O1 to G2-O4 (#5) |
| **Rationale** | **Reason:** R1, R2 and every G2 criterion are judged from the log (MOE-1, MOE-2). Each item has a user: flight mode, transition state and flying state → R1, R2; charge used → R2 and C11; attitude → G2-O3; height → G2-O4, height loss in an abort; outputs → G2-O1 and G2-O2, aircraft margin (#5, B1); stick positions → G2-O1 and G2-O2, pilot margin. Speed is in ConOps capability 6, but no criterion uses it, so it is left out. **Assumptions:** AS4; ArduPilot records the sticks with default logging (closed 2026-10-29, #4). **ConOps:** capability 6; [DRM-0100]; F19. **Design constraint:** none |
| **Verification** | Inspection of the log of [DRM-0100], and of every flight log used to verify another requirement |
| **Pass/fail** | Pass if the log holds every listed quantity for the whole time from arming to disarming. With ArduPilot: `MODE`; `MSG` and `QTUN.Trn` (transition); `STAT.isFlying`; `ATT`; `POS.RelHomeAlt`; `RCOU`; `BAT` Volt, Curr and CurrTot; `RCIN` C1 to C4. Fail if any one is missing |
| **KDR** | No. The flight controller records this with default settings |
| **Status** | Draft, 2026-11-11 |

### R5 — Operator number on the outside

| | |
|---|---|
| **Statement** | JBV-01 shall carry the operator number on its outside surface. |
| **Area** | Interface — the regulatory interface (`CONOPS.md` §3.3). Second requirement in the area: one sentence would need two "shall" verbs (record, carry), for two different interfaces. Settled 3 |
| **Parent** | C22. Law: `RULES.md` §B1 |
| **Numbers** | **Only the part of the number before the dash** goes on the aircraft — law, `RULES.md` §B1 |
| **Rationale** | **Reason:** law. Without the number no flight is legal, so no flight counts for R1 or R2. **Assumptions:** the pilot is the operator and holds one number (`RULES.md` §B1, chosen 2026-10-14). **ConOps:** capability 12; §3.3 regulatory interface. **Design constraint:** needs a flat place on the outside that survives weather and a crash |
| **Verification** | Inspection of the built aircraft, and again after every rebuild |
| **Pass/fail** | Pass if the part of the operator number before the dash is on the outside surface of JBV-01, can be read by a person standing next to it, and can still be read after a flight. Fail otherwise |
| **KDR** | No |
| **Status** | Draft, 2026-11-11 |

### R6 — Transport to the site

| | |
|---|---|
| **Statement** | JBV-01 shall fit, packed for transport, into at most 2 packages, each no more than 85 cm in height, width and depth. |
| **Area** | Transportation |
| **Parent** | C18 (the site is out of town); G1 (the flight happens at that site) |
| **Numbers** | **85 cm** — carrier rule, not ours to change: NS may refuse any hand luggage with a height, width or depth over 85 cm (NS AVR, version UD.2026.26.8, Art. 5.5, p. 13; `REFERENCES.md` NSAVR). **2 packages** — chosen 2026-11-11: one per person. If fewer, the airframe needs more joints; if more, one of us carries two |
| **Rationale** | **Reason:** we travel to the site by public transport (D2), and the aircraft travels more than once, unfinished (`CONOPS.md` §5.0). This decides the span, and whether the airframe comes apart (Settled 3). Without R6, the trade could choose a span that cannot reach the site. **Assumptions:** the route uses NS trains and local buses; the bus house rules give no size in cm, only that luggage stays out of the aisle (`REFERENCES.md` KEO); the terms of the Keolis regional trains were not checked; the test site is not found yet (AS1); both of us travel on every flight day. **ConOps:** Transport mode, §3.4; Transport, §5.0. **Design constraint:** C18 |
| **Verification** | Demonstration: pack JBV-01, measure each package with a tape, travel by public transport, unpack |
| **Pass/fail** | Pass if the packed JBV-01 is in no more than 2 packages, each measured at no more than 85 cm in height, width and depth, and after a trip by public transport it passes the bench check [DRM-0100] with no repair. Fail otherwise |
| **KDR** | Yes. Every part longer than 85 cm — in practice the wing — must come apart |
| **Status** | Draft, 2026-11-11 |

### R7 — Retired 2026-11-01 (D3)

Practice is a procedure in #22: 3 SITL profiles in a row before the first free hover. The ID is not
reused.

### R8 — Rebuild cost after a crash

| | |
|---|---|
| **Statement** | A complete rebuild of JBV-01 after a crash shall cost no more than the rebuild allowance in `NGO.md` §6. |
| **Area** | Maintainability |
| **Parent** | C4 (a crash and rebuild is planned); C3 (money) |
| **Numbers** | The allowance is **cited, not copied**: it is a chosen line of the C3 apportionment, and lives in `NGO.md` §6 only |
| **Rationale** | **Reason:** C4 plans at least one crash, and part of C3 is held for it. Without R8, an airframe could be designed whose rebuild costs more than the allowance, and the project ends at the first crash. The time to rebuild is R9 (D4). **The rebuild set** is every part except the avionics that move to the new airframe (flight controller, receiver, telemetry radio, GNSS), and it includes one battery, because a crashed pack is retired (`CONOPS.md` §5.0). **Assumptions:** the avionics survive the crash. **ConOps:** capability 11; §5.0 repair and rebuild. **Design constraint:** C3, C4, C5, C6 |
| **Verification** | Analysis — arithmetic only (#6). Sum of the dated prices of the rebuild set in `BOM.xlsx`, plus the parcel costs from C6 for the parts that are ordered |
| **Pass/fail** | Pass if the cost is at or below the allowance at the design review (#54), and again after the parts order (#55). Fail otherwise |
| **KDR** | Yes. It forces an airframe that comes apart, and cheap parts where crashes happen |
| **Status** | Draft, 2026-11-11 |

### R9 — Rebuild time after a crash

| | |
|---|---|
| **Statement** | JBV-01 shall be ready to fly again within 2 weeks of a crash. |
| **Area** | Maintainability. Second requirement in the area: split from R8 because money and time are verified at different times (D4, Settled 5) |
| **Parent** | C4 (a crash and rebuild is planned); C2 (the project ends 12 June 2027) |
| **Numbers** | **2 weeks** — chosen 2026-11-01 (D4). If longer, a crash late in the schedule leaves no time for the flights after it; if shorter, no airframe can meet it. **8 h per week** of build work, h_week — chosen 2026-11-11: both of us, solo hours. If lower, the same build takes more weeks. **No spare parts held** — chosen 2026-11-11: the rebuild set is ordered after the crash |
| **Rationale** | **Reason:** C4 plans at least one crash, and C2 fixes the end date. Without R9, a rebuild could take so long that the flights after it no longer fit. **Assumptions:** the parts that must be ordered are ordered on the day of the crash; print time on the printer is not person time. **ConOps:** capability 11; §5.0 repair and rebuild. **Design constraint:** C2, C4, C6 |
| **Verification** | Analysis — arithmetic only (#6). t = H_build / h_week + t_delivery. H_build: person-hours to build the first airframe, measured in P4. t_delivery: the longest delivery time of any part of the rebuild set, from the dated quotes in `BOM.xlsx` and C6 |
| **Pass/fail** | Pass if t is at most 2 weeks at the design review (#54) with quoted delivery times and estimated build hours, and again in P4 with the measured H_build. Fail otherwise |
| **KDR** | Yes. With no spare parts, delivery alone can use most of the 2 weeks. It forces parts with short delivery and an airframe that is quick to build |
| **Status** | Draft, 2026-11-11 |

---

## 2. Area walk

The twelve areas of MIT 16.842 Session 2, slide 45 (Settled 3). At most one requirement per area; a
skipped area has its reason. This walk is for G1. G2 and safety get their own walk in #10 (D5).

| Area | Result |
|---|---|
| Functional | R1 |
| Performance | R2 |
| Interface | R4, R5 — two "shall" verbs for two interfaces, see R5 |
| Environment | R3. **Wind is not written:** the design wind speed is open (`NGO.md` §8) and closes with sizing (#17); no value, no item. Rain and daylight are operating rules (`CONOPS.md` §4.0, `RULES.md` §C), not properties of the aircraft |
| Facility | **Skipped.** The test site is bound by C18, C19 and NL1 to NL4, and found in #25; the makerspace is AS6. Neither puts a property on JBV-01 |
| Transportation | R6 |
| Training | **Skipped.** Practice is a rule for a person, not a property of the aircraft (D3). R7 is retired |
| Personnel | **Skipped.** C1 fixes two people. Who does what on the field is a procedure (#22), not a property of the aircraft |
| Reliability | **Skipped.** G1-O1 asks for one flight. A reliability figure needs many flights to verify, and C3 cannot pay for them. Damage is covered by R8 and R9 |
| Maintainability | R8, R9 — money and time are verified at different times, see R9 |
| Operability | In the G2 and safety walk, §5: R13, arming (F21) |
| Safety | In the G2 and safety walk, §5: R14 and R16. Rules for people are procedures in #22 |

---

## 3. Phases read from the log

R1 and R2 read the phases from the log with one set of definitions, written here once.

Phases are read from the autopilot state, not from airspeed (D1, option a). Record and message
names come from the ArduPilot source and are not yet seen in a log of ours.

| Phase | Read from the log |
|---|---|
| Vertical take-off | `STAT.isFlying` changes 0 → 1 in a VTOL mode (QHOVER, QLOITER, QSTABILIZE), until the first hover |
| Hover | A VTOL mode while `STAT.isFlying` = 1 |
| Transition to wing-borne flight | From the `MODE` change into a fixed-wing mode until the message "Transition done" ("Transition FW done" on a tailsitter). `QTUN.Trn` shows the state |
| Wing-borne flight | A fixed-wing mode after that message, until the next change to a VTOL mode |
| Transition to hover | From the change to a VTOL mode until steady as B3 defines it (`NGO.md` §3): VTOL state, attitude inside ±5° of trim for 2 s |
| Vertical landing | In a VTOL mode, until `STAT.isFlying` changes 1 → 0 |

**Known weak spot.** In a fixed-wing mode, VTOL assist may run the lift motors, and that time still
counts as wing-borne. `QTUN.Ast` marks assist, so it can be taken out if we ever change to D1
option (b).

---

## 4. Requirements from G2 and safety

G2 criteria B1 to B4 live in `NGO.md` §3. The requirements below **cite** them and copy no
number (rule 5). Never edited after a flight.

### R10 — Abort a transition

| | |
|---|---|
| **Statement** | JBV-01 shall abandon a transition when the pilot commands it, and return to hover, passing B3. |
| **Area** | Functional |
| **Parent** | G2-O4, under G2 |
| **Numbers** | None of its own. B3 in `NGO.md` §3 holds them |
| **Rationale** | **Reason:** the first transitions are the most dangerous moment of the project. Without R10, every transition attempt is all or nothing. **Assumptions:** the transition time used to time the abort is measured on the tether (B4, a test gate in #20). **ConOps:** capability 10; [DRM-0400]; F8. **Design constraint:** C10 — the configuration is open, so the abort is judged from the log, not from an attitude |
| **Verification** | Demonstration, [DRM-0400], from `MODE`, `ATT` and `POS` in the flight log |
| **Pass/fail** | Pass if the commanded abort passes B3. Fail if B3 fails |
| **KDR** | Yes. A back-transition from part-way differs a lot between layouts |
| **Status** | Draft, 2026-11-11 |

### R11 — Control margin

| | |
|---|---|
| **Statement** | JBV-01 shall keep the control margin of B1 in hover and through both transitions. |
| **Area** | Performance |
| **Parent** | G2-O1 and G2-O2, under G2 |
| **Numbers** | None of its own. B1 in `NGO.md` §3 holds them |
| **Rationale** | **Reason:** full stick, or an output at its limit, means nothing is left for the next gust. Without R11, nothing asks for margin, and an aircraft that only just flies would pass. **Assumptions:** the log holds `RCIN` and `RCOU` (R4); the radio is calibrated, so `RCn_MIN`/`RCn_MAX` are real. **ConOps:** capabilities 2 and 3; [DRM-0300], [DRM-0400]; F6, F15. **Design constraint:** C10 |
| **Verification** | Demonstration, [DRM-0300] and [DRM-0400], from `RCIN` and `RCOU` in the flight log |
| **Pass/fail** | Pass if B1 holds for the whole G2-O1 hover, and in each transition from the `MODE` change that starts it until the new flight mode is steady (B3's definition). Fail if B1 fails in any of these |
| **KDR** | Yes. Control margin sizes the motors and servos, and so mass and cost |
| **Status** | Draft, 2026-11-11 |

### R12 — Battery state on the ground

| | |
|---|---|
| **Statement** | JBV-01 shall show the pilot on the ground, during flight, the battery charge used, with a warning when 30 % of the rated capacity is left. |
| **Area** | Interface — aircraft to the pilot, during flight |
| **Parent** | C11 (the reserve); G1-O2 (flown to the reserve). Also [DRM-0800] |
| **Numbers** | **30 % left** (warning) — chosen 2026-11-11 (F). Set above the C11 reserve so that the flight can end and still land with the reserve: a transition and landing take about 1.5 to 2 min (estimate, R2). If too low, landings miss the reserve; if too high, flights are cut short. The reserve itself is **cited, not copied**: C11. **Rated capacity** is the capacity printed on the pack in use |
| **Rationale** | **Reason:** [DRM-0800]: the battery state must be visible while there is still time to act. Without R12, the flight ends after the reserve is broken, not before. **Reserve reading, used by R2:** the reserve is kept if, at landing, the charge used (`BAT.CurrTot`) is no more than (1 − C11) × the rated capacity. **Assumptions:** the current sensor reads correctly; it is checked against a known charge before it is trusted (C8). **ConOps:** capability 7; [DRM-0800]; F18. **Design constraint:** C11 |
| **Verification** | Demonstration: on the bench, [DRM-0100], the charge used is shown on the ground; in [DRM-0600], from `BAT` and `MSG` in the flight log |
| **Pass/fail** | Pass if (1) on the bench the charge used is shown on the ground, and (2) in [DRM-0600] the warning is in the log no later than the first `BAT` sample with charge used at or above 70 % of the rated capacity. Fail otherwise |
| **KDR** | No. A standard telemetry link and current sensor do this |
| **Status** | Draft, 2026-11-11 |

### R13 — Arming

| | |
|---|---|
| **Statement** | JBV-01 shall arm and disarm only by one dedicated transmitter switch. |
| **Area** | Operability |
| **Parent** | F21; capability 9. Safety on every flight |
| **Rationale** | **Reason:** arming makes the propellers live. Without R13, the aircraft could be armed by a stick movement and nobody would see its state on the transmitter. The same switch stops the motors at once (C, 2026-11-11). **Assumptions:** the switch disarms unconditionally, even in flight (ArduPilot docs, not tested), so the switch is one that is hard to hit by mistake, chosen in #48. **ConOps:** capability 9; [DRM-0100]. **Design constraint:** none |
| **Verification** | Demonstration on the bench, armed, propellers off, [DRM-0100] |
| **Pass/fail** | Pass if all hold: (1) the switch arms and disarms; (2) arming by the rudder stick is refused; (3) the aircraft shows its state by light and sound; (4) every arm and disarm is in the log; (5) no motor turns while disarmed. Fail if any one does not hold |
| **KDR** | No |
| **Status** | Draft, 2026-11-11 |

### R14 — Loss of the command link

| | |
|---|---|
| **Statement** | On loss of the command link, JBV-01 shall start a return to its take-off point within 5 s and land there vertically. |
| **Area** | Safety |
| **Parent** | [DRM-0700]; F20 |
| **Numbers** | **5 s** — chosen 2026-11-11 (D2), the ArduPilot default for the long failsafe (`FS_LONG_TIMEOUT`); in hover the return starts after 1 s (`RC_FS_TIMEOUT`). If shorter, a short link dropout ends a test flight; if longer, the aircraft is out of control for longer. **10 m** — chosen 2026-11-11 (D3). GNSS on a small aircraft is good to about 2 to 5 m (estimate, not sourced). If tighter, GNSS error alone fails it; if looser, a landing in the wrong place passes |
| **Rationale** | **Reason:** [DRM-0700] asks for one deliberate action, written down. Always come home (D, 2026-11-11): in hover by QRTL, in wing-borne flight by circling and then RTL with a vertical landing. Without R14, the action is whatever the defaults do, and a wing-borne aircraft could circle until the battery is empty. **Assumptions:** a GNSS is on board (R8's avionics); home is set with a good fix; a commanded RTL follows the same autopilot path as a link-loss RTL (ArduPilot source, not tested). **ConOps:** [DRM-0700]; F17, F20. **Design constraint:** C15, C18 |
| **Verification** | Demonstration: (1) on the bench, armed, propellers off, [DRM-0100], the transmitter is switched off once in a hover mode and once in a fixed-wing mode; (2) in [DRM-0400] or [DRM-0500], after B3 has passed, the pilot commands RTL from wing-borne flight |
| **Pass/fail** | Pass if both hold: (1) on the bench the log shows QRTL (hover mode) and RTL (fixed-wing mode) within 5 s of the transmitter going off; (2) the commanded RTL ends in a vertical landing within 10 m of the home point, read from `POS`. Fail otherwise |
| **KDR** | Yes. It needs a GNSS and an automatic back-transition |
| **Status** | Draft, 2026-11-11 |

### R15 — Stability

| | |
|---|---|
| **Statement** | JBV-01 shall return to its trimmed state after a disturbance with no pilot input, passing B2 in hover and in wing-borne flight. |
| **Area** | Performance. Second requirement in the area: controllability (R11) and stability are kept apart on purpose, so that passing one cannot be mistaken for passing both (`NGO.md` §3; A, 2026-11-11) |
| **Parent** | G2-O3, under G2 |
| **Numbers** | None of its own. B2 in `NGO.md` §3 holds them |
| **Rationale** | **Reason:** G2 asks for stability as well as control. Without R15, an aircraft that needs the pilot's hands all the time would pass. **Assumptions:** the log holds `ATT` (R4). **ConOps:** [DRM-0300], [DRM-0400]; F16. **Design constraint:** C10 |
| **Verification** | Demonstration, [DRM-0300] (hover, QHOVER) and [DRM-0400] (wing-borne, FBWA), from `ATT` in the flight log |
| **Pass/fail** | Pass if B2 holds in QHOVER and in FBWA. Fail if either fails |
| **KDR** | Yes. Stability in both modes shapes the layout, the centre of gravity and the tail |
| **Status** | Draft, 2026-11-11 |

### R16 — Battery at the reserve

| | |
|---|---|
| **Statement** | When the charge used reaches the C11 reserve in flight, JBV-01 shall start a return to its take-off point. |
| **Area** | Safety. Second requirement in the area: a different trigger and a different "shall" from R14 |
| **Parent** | C11; [DRM-0800]; F20 |
| **Numbers** | The reserve is **cited, not copied**: C11. Rated capacity as in R12 |
| **Rationale** | **Reason:** the backstop if the R12 warning is missed (F, 2026-11-11). Without R16, a missed warning ends in an empty battery in the air. A flight that ends this way lands below the reserve and fails R2: the backstop protects the battery, not the score. **Assumptions:** the return follows the same path as R14, which verifies it. **ConOps:** [DRM-0800]; F20. **Design constraint:** C11 |
| **Verification** | Inspection of the flight controller settings before every flight day; the return itself is verified by R14 |
| **Pass/fail** | Pass if the battery failsafe is set to start a return to the take-off point when the charge used reaches (1 − C11) × the rated capacity of the pack in use. Fail otherwise |
| **KDR** | No |
| **Status** | Draft, 2026-11-11 |

---

## 5. Area walk for G2 and safety

The twelve areas again, for G2 and safety (D5). At most one requirement per area; a second only
with its reason; a skipped area has its reason.

| Area | Result |
|---|---|
| Functional | R10 |
| Performance | R11, R15 — controllability and stability kept apart, see R15 |
| Interface | R12 |
| Environment | **Skipped.** As in §2: the design wind speed is open and closes with sizing (#17) |
| Facility | **Skipped.** The tether proof is a test gate (G2-O5, B4), written in #20 (B, 2026-11-11) |
| Transportation | **Skipped.** R6 covers it |
| Training | **Skipped.** Practice is a procedure in #22 (D3) |
| Personnel | **Skipped.** Rules for people — propeller clearance on the bench, LiPo charging and storage, never under a hovering aircraft, the C19 distance — are procedures in #22, each with a pass/fail line (E, 2026-11-11) |
| Reliability | **Skipped.** As in §2 |
| Maintainability | **Skipped.** R8 and R9 cover it |
| Operability | R13 |
| Safety | R14, R16 — two triggers, two "shall" verbs. A lift unit failing in hover ([DRM-0900]) has no design answer on most layouts (`CONOPS.md` §6.2); the C19 distance is the answer, in #22 |
