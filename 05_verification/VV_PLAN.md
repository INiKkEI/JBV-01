# JBV-01 — System verification and validation plan

Written on the left branch of the V, before any hardware exists (#19). Agreed 2026-11-15, against
`01_requirements/REQUIREMENTS.md` at `req-v1`.

- **Verification** asks: did we build it right? Every L1 requirement, R1 to R16, passes its own
  pass/fail criterion.
- **Validation** asks: did we build the right aircraft? MOE-1 and MOE-2 (`NGO.md` §4) are judged on
  the real aircraft, after verification (`STAGE_8_NOTES.md`, points 1 and 2).

Pass/fail criteria live in `REQUIREMENTS.md` only and are not copied here. The test events are the
scenarios of `CONOPS.md` §6.

---

## 1. Verification matrix

Methods are NASA's four: test, demonstration, inspection, analysis. Analysis is arithmetic only
(`NGO.md` §8, #6). R7 is retired.

| R | Method | Event | Phase |
|---|---|---|---|
| R1 | Demonstration | DRM-0500 (full mission) | P7 |
| R2 | Test | DRM-0600 (endurance flight) | P7 |
| R3 | Demonstration | DRM-0300 (free hover), again DRM-0500 | P5, again P7 |
| R4 | Inspection | DRM-0100 (bench check), then the log of every verification flight | P4, then every flight |
| R5 | Inspection | Look at the built aircraft | P4, again after every rebuild |
| R6 | Demonstration | Pack, measure, travel by public transport, then DRM-0100 | First trip to the site, before P5 |
| R8 | Analysis | Cost sum of the rebuild set, `BOM.xlsx` plus C6 parcel costs | P3 design review (#54), again P4 after the order (#55) |
| R9 | Analysis | Rebuild-time sum, t = H_build / h_week + t_delivery | P3 design review (#54), again P4 with measured H_build |
| R10 | Demonstration | DRM-0400 (first wing-borne flight), one abort in each direction | P6 |
| R11 | Demonstration | DRM-0300, DRM-0400 | P5 (hover), P6 (transitions) |
| R12 | Demonstration | DRM-0100, DRM-0600 | P4 (bench), P7 (flight) |
| R13 | Demonstration | DRM-0100 | P4 |
| R14 | Demonstration | DRM-0100; commanded RTL in DRM-0400 or DRM-0500 | P4 (bench), P6 or P7 |
| R15 | Demonstration | DRM-0300 (QHOVER), DRM-0400 (FBWA) | P5, P6 |
| R16 | Inspection | Flight controller failsafe settings | Before every flight day, from P5 |

**Label.** The flight requirements keep the label "demonstration", although each is judged from
the flight log against written numbers.

## 2. Events and the requirements they verify

Every event names at least one requirement, and every requirement has an event (#23, 2026-11-15).

| Event | Verifies |
|---|---|
| DRM-0100 Bench check | R4, R6, R12, R13, R14 |
| DRM-0300 Free hover | R3, R11, R15 |
| DRM-0400 First wing-borne flight | R10, R11, R14, R15 |
| DRM-0500 Full mission | R1, R3, R14 |
| DRM-0600 Endurance flight | R2, R12 |
| Log of every verification flight | R4 |
| Look at the built aircraft | R5 |
| Pack, measure, travel | R6 |
| Cost sum | R8 |
| Rebuild-time sum | R9 |
| Failsafe settings check | R16 |
| V1, V2 | MOE-1, MOE-2 |

## 3. Validation matrix

| V | Activity | Expectation | Method | Place | Phase | Performer | Result |
|---|---|---|---|---|---|---|---|
| V1 | MOE-1: one complete flight, the six phases in order | All six phases in one log, read with `REQUIREMENTS.md` §3 | Demonstration, from the DRM-0500 log | Test site | P7, after R1–R16 passed | Pilot flies, both judge | Not run |
| V2 | MOE-2: that flight under control and stable | B1, B2 and B3 pass (`NGO.md` §3) | Demonstration, from the same log | Test site | P7, same flight as V1 | Pilot flies, both judge | Not run |
| V3 | Fit-check of the two transport packages | Both packages within R6 | Inspection, tape measure | Home | P4, before the first trip | Both | Not run |
| V4 | Dry run of the #22 checklists | Every checklist step can be done | Demonstration, on the bench | Home | P4, before the first hover | Both | Not run |
| V5 | SITL run of the full profile | Six phases flown in SITL | Demonstration in SITL. **No verification credit** (#6) | Laptop | After the configuration trade | Both | Not run |

For V1 and V2 the expected values are written before the flight (#72), in the ConOps conditions.

## 4. Rules for repeating checks

**Rebuilt airframe.** After a rebuild with no design change, the acceptance check is: DRM-0100
bench check, the R5 label, then a DRM-0300 hover.

**After a change (regression).**

| Change | Repeat |
|---|---|
| Parameter change | The hover checks: DRM-0300 for R11 and R15 |
| Airframe or CG change | DRM-0100 bench check, then DRM-0300 hover |
| Firmware change | DRM-0100 bench check, and every flight-mode check |

**Vendor figures.** Every vendor figure that a verification uses — a motor thrust table, a battery
capacity — is retested against something known before it is trusted (C8).
