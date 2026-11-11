# Stage 6 — Component and subsystem verification: notes

The Stage 6 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources, and before writing a test plan (#19, #20, #52, #53) or a line of
`05_verification/TEST_LOG.md`. The rules for these notes are in `REFERENCES.md`, "How the stage
notes are written".

**Checks.** Spot check: not done yet. Talk-through: not done yet.

**Read on 2026-11-11.** NASA 5.3 and Appendix I from the nasa.gov web version of the handbook (Rev 2).
MIT Session 9 from the OCW PDF, slide numbers as printed in the footer. HYDRO Figures 13 to 16 read
as images; page numbers are PDF pages.

**Stage 6 in one sentence.** Every test we run is planned before the hardware exists, run as
written, read while the rig is still set up, and written down with enough detail that someone else
could repeat it and get the same pass or fail.

---

## 1. NASA 5.3 — Product verification: what it is

Source: NASA SEH Rev 2, Section 5.3, introduction and "Differences Between Verification and
Validation Testing".

**Verification and validation ask two different questions.** *"the Product Verification Process
answers the critical question, "Was the end product realized right?" The Product Validation Process
addresses the equally critical question, "Was the right end product realized?""*

- **Verification** looks back at the requirements: does JBV-01 meet R1 to R16?
- **Validation** looks back at the ConOps and the need: does JBV-01 do what we built it for? That is
  Stage 8 (#30), not this file.

**Verification relates to the requirement set; validation to the ConOps.** *"Verification testing
relates back to the approved requirements set (such as an SRD)"* and *"Validation relates back to the
ConOps document."*

**Verification tests are the official record.** *"Verification tests are the official "for the
record" testing performed on a system or element to show that it meets its allocated requirements or
specifications including physical and functional interfaces."* They *"use instrumentation and
measurements"* and are done *"in a controlled environment to facilitate failure analysis."*

For us: a controlled environment is the bench, the thrust stand or the tether — not the field. The
field is where validation and the G2 demonstrations happen.

---

## 2. NASA 5.3.1.1 — What must exist before a test starts

Source: NASA SEH Rev 2, Section 5.3.1.1 "Inputs".

Four inputs, quoted by their headings:

1. **"The product to be verified"** — *"The product will likely have been through at least a
   functional test to ensure it was assembled correctly."*
2. **"Verification plan"** — *"baselined before entering this verification."*
3. **"Specified requirements baseline"** — *"Acceptance criteria should have been identified for each
   requirement to be verified."*
4. **"Enabling products"** — *"This may include test fixtures and support equipment."*

For us:

- **Input 2** means the test plan is committed before the test day, not written after it. This is
  already our V-model rule.
- **Input 3** is `REQUIREMENTS.md` after the freeze (`req-v1`): each R has its pass/fail. A test of a
  requirement that is not yet frozen is an engineering test, not a verification (see section 5).
- **Input 4** is our rigs: the thrust stand (#27), the tether rig (B4), the scale, the balance for
  centre of gravity. C8 already says each rig is checked against something known before we trust it.
  NASA treats the rig as an input of its own, with its own readiness — so the rig check is a step in
  the procedure, not something assumed.

---

## 3. NASA 5.3 — Verification, qualification, acceptance, certification

Source: NASA SEH Rev 2, Section 5.3.1.1, box "Differences Between Verification, Qualification,
Acceptance and Certification".

- **Verification:** *"The Verification program is performed once regardless of how many flight units
  may be generated (as long as the design doesn't change)."*
- **Qualification:** tests *"at the extremes of the environmental envelope"*. We have no environmental
  test facility (C8). Skipped, see the end.
- **Acceptance:** *"The selected Acceptance activities are performed on each of the flight units as
  they are manufactured"*, to *"show that the manufacturing/workmanship of the unit conforms to the
  design that was previously verified/qualified."*
- **Certification:** an audit by a certifying authority. We have none (open category, A3).

**This matters for the rebuild.** C4 plans at least one crash and a second airframe. By NASA's
definitions:

- The **first airframe** carries the verification program.
- The **rebuilt airframe** does not need the whole program again *"as long as the design doesn't
  change"*. It needs an **acceptance check**: a short subset that shows it was built like the verified
  one.
- If the rebuild **changes** the design, verification of what changed is repeated.

So the plan needs a short, named list: which tests are repeated on every rebuilt airframe. Nothing
in our files has this yet. To decide in #19.

---

## 4. NASA 5.3.1.2 — The five activities, and the four methods

Source: NASA SEH Rev 2, Section 5.3.1.2 "Process Activities" and box "Methods of Verification".

**The loop.** *"There are five major activities in the Product Verification Process: (1) prepare to
conduct product verification; (2) perform verification; (3) analyze verification results; (4)
preparing a product verification report; and (5) capture work products generated during the
verification activities."*

Sections 5 to 8 below take them one at a time. Every bench test, thrust-stand run and tether run
follows this loop.

**Tailor it.** *"A verification approach should be adapted (tailored) to the project it supports."*
NASA's list of factors includes cost and schedule, risk, the facilities available, and *"Degree of
design heritage and hardware/software reuse."* For us: €800, one airframe plus one rebuild, no lab.

**The four methods**, as NASA defines them:

- **Analysis:** *"The use of mathematical modeling and analytical techniques to predict the
  suitability of a design"*. NASA adds: *"Analysis includes the use of modeling and simulation as
  analytical tools."* and *"Analysis can include verification by similarity of a heritage product."*
- **Demonstration:** *"Showing that the use of an end product achieves the individual specified
  requirement. It is generally a basic confirmation of performance capability, differentiated from
  testing by the lack of detailed data gathering."*
- **Inspection:** *"The visual examination of a realized end product."* Also: *"Inspection can include
  inspection of drawings, documents, or other records."*
- **Test:** *"The use of an end product to obtain detailed data needed to verify performance"*. It
  *"produces data at discrete points for each specified requirement under controlled conditions and
  is the most resource-intensive verification technique."* And: *"Test as you fly, and fly as you
  test."*

**Where we are narrower than NASA, on purpose.** NASA lets analysis include simulation and
similarity to a heritage product. We do not: analysis alone verifies a requirement only when it is
arithmetic with no model inside, and every input is our measurement or a figure from a named
document (`NGO.md` §8, #6). So R8, R9 and R16 (arithmetic or inspection of settings) are allowed;
a SITL result never is.

**Where our files and NASA use a word differently.** NASA separates demonstration from test by *"the
lack of detailed data gathering"*. Our G2 requirements (R10, R11, R15) are called demonstrations,
but they are judged from detailed log data (`RCIN`, `RCOU`, `ATT`). By NASA's wording they are
closer to tests. The pass/fail does not change. Only the label does. To decide in #19 whether to
keep the label or change it (it would be a modification under Settled 4 of Stage 2).

---

## 5. NASA 5.3.1.2.1 — Prepare

Source: NASA SEH Rev 2, Section 5.3.1.2.1 "Product Verification Preparation".

**Procedures are step by step, written before, and grow with the design.** *"Procedures capturing
detailed step-by-step activities and based on the verification type and methods are finalized and
approved. Development of procedures typically begins during the design phase of the project life
cycle and matures as the design is matured."*

**The test environment is part of the procedure.** *"The final element is preparation of the
verification environment; e.g., facilities, equipment, tools, measuring devices, and climatic
conditions."* For us: wind and temperature on the day go in the record (B1 already asks for the
wind).

**Humans in the loop.** *"When operator or other user interaction is involved, it is important to
ensure that humans are properly represented in the verification activities."* For us: any test that
involves the pilot (B1, B2, B3, R13, R14) is flown by the Pilot himself, with the real transmitter.

**A readiness check before testing.** *"In earlier phases of the life cycle, these Test Readiness
Reviews (TRRs) may be held informally"*. NASA's list of what a TRR checks: *"test ranges, test
facilities, trained testers, instrumentation, integration labs, support equipment, and other
enabling products."*

For us, an informal TRR is a short checklist at the start of a test day: procedure committed, rig
checked against a known value, firmware and parameter file noted, people briefed, safety rules from
#22 in place. That fits the pre-flight checklist in #22.

**Outcomes of preparation**, as NASA lists them (shortened): plan, approved procedures and the
requirement baseline on hand; test articles and enabling products on hand and integrated; people
and money available; *"The verification environment is evaluated for adequacy, completeness,
readiness, and integration."*

---

## 6. NASA 5.3.1.2.2 — Perform

Source: NASA SEH Rev 2, Section 5.3.1.2.2 "Perform Product Verification".

**Follow the procedure, and check the instruments.** *"The verification lead should ensure that the
procedures were followed and performed as planned, the verification-enabling products and
instrumentation were calibrated correctly, and the data were collected and recorded for required
verification measures."*

**Verify at the lowest level where it can be done.** *"Some verifications need to be performed at
the lowest component level if the ability to verify a requirement at a higher assembly is not
possible."* For us: a motor's thrust can only be measured on the stand, not in flight (C8), so it
is verified at component level (#56).

**End-to-end.** *"If practicable, a final set of testing with as much of the end-to-end
configuration as possible is important."* For us this is the bench check [DRM-0100]: transmitter →
receiver → flight controller → ESCs and servos, plus telemetry to the ground and the log. Planned in
Stage 7 (#32, #20).

**Stop on a discrepancy.** *"When a "discrepancy" is observed (i.e., any variance, lack of agreement,
or contradiction with the required or expected outcome, configuration, or result), verification
activities should stop and a discrepancy report should be generated."* Then: was the **product**
wrong, or the **procedure or its conduct**?

For us: when a test does something unexpected, we stop the test, not just note it and carry on. It
goes in `TEST_LOG.md`. If the product was wrong, our V-model rule sends us back to the left-branch
level that was wrong. If the procedure was wrong, the procedure is fixed and the test is run again.

---

## 7. NASA 5.3.1.2.3 — Analyse and report

Source: NASA SEH Rev 2, Section 5.3.1.2.3 "Analyze Product Verification Results and Report".

**Read the data before the rig comes apart.** *"If possible, this analysis is performed while the
test/analysis configuration is still intact. This allows a quick turnaround in case the data
indicates that a correction to the test or analysis run needs to be performed again."*

For us this is the most practical line in Stage 6. Read the log on the field, before packing up.
A test site is a trip by public transport (R6). A repeat costs a day.

**Record against each requirement.** *"Verification results should be recorded in a requirements
compliance or verification matrix"* to *"trace compliance for each product requirement."*

**A failed result can change the requirement, by its own process.** *"Waivers needed as a result of
verification to request relief from or modify a requirement are identified."* For us there are no
waivers. A requirement changes only by a six-field issue (Stage 2, Settled 4), never in the test
log, and never after the flight for a demonstration criterion.

**A fix means testing again.** *"If the mitigation of the nonconformance results in a change to the
product, the verification may need to be planned and performed again."*

---

## 8. NASA 5.3.1.2.4 and 5.3.1.3 — Capture, and when verification is done

Source: NASA SEH Rev 2, Sections 5.3.1.2.4 "Capture Product Verification Work Products" and 5.3.1.3
"Outputs".

**The step people skip.** *"The capture and recording of verification results and related data is a
very important, but often underemphasized, step in the Product Verification Process."*

**What a verification report holds**, quoted as NASA lists it:

- *"recorded test/verification results/data;"*
- *"version of the set of specified requirements used;"*
- *"version of the product verified;"*
- *"version or standard for tools, data, and equipment used;"*
- *"results of each verification including pass or fail declarations; and"*
- *"discrepancies."*

For us, each `TEST_LOG.md` entry can carry exactly these six, made concrete:

| NASA item | For JBV-01 |
|---|---|
| Results and data | The log file name and where it is stored; the numbers the pass/fail reads |
| Version of the requirements | The git tag or commit of `REQUIREMENTS.md` (`req-v1` or later) |
| Version of the product | Which airframe (first or rebuilt), firmware version, the parameter file used |
| Version of tools and equipment | Which rig, and when it was last checked against a known value |
| Pass or fail | Per requirement, against the criterion written before the test |
| Discrepancies | What was unexpected, and whether product or procedure was wrong |

The report also *"includes the requirement that was to be verified and its bidirectional
traceability, the verification method used"* (5.3.1.3). So every entry names its R number.

**When verification is complete.** *"Criteria for completing verification of the product include:
(1) documented objective evidence of compliance with requirements or waiver and (2) closure of all
discrepancy and nonconformance reports."* For us: every R has a passed entry in `TEST_LOG.md`, and
no discrepancy is left open.

---

## 9. NASA Appendix I — The V&V plan outline, cut down

Source: NASA SEH Rev 2, Appendix I "Verification and Validation Plan Outline" (nasa.gov web page).

**When the plan is fixed.** *"The Verification and Validation (V&V) Plan needs to be baselined after
the comments from PDR are incorporated."* Our PDR is the design review (#54).

**The outline has nine sections and four appendices.** Most of it assumes a large programme. The
parts that do work for us:

| Appendix I section | What it asks | For JBV-01 |
|---|---|---|
| 1.2 Responsibility and change authority | Who keeps the plan, who approves changes | Both of us; a change goes through a six-field issue |
| 3.4 Ground support equipment | *"special test fixtures, lifting aids, simulators"* | Thrust stand, tether rig, scale, balance, SITL |
| 4.2 Verification methods | How each of the four methods *"will be applied to this system"* | Our narrower analysis rule (#6) goes here |
| 5.2 Test articles | *"the pedigree of test articles"*: prototypes, engineering units, flight units | Prototype loop (#51), first airframe, rebuilt airframe |
| 5.4 Facilities | *"test stands, and other facilities"* | Makerspace (AS6), test site (#25) |
| 6.x End item V&V | Per subsystem: tests, analysis, inspection, demonstration | One block per subsystem: propulsion, avionics, airframe, radio |
| 6.1.1 Developmental unit evaluations | Tests done *"prior to performing official verification"* | Engineering tests on prototypes, kept apart from the record |
| 6.1.4 Acceptance testing | Shows a unit *"has the same design as the one that is being verified"* | The rebuild check from section 3 |
| 7.1 / 7.2 Integration and complete system | Assemblies, then the whole system | Stage 7 (#20) and Stage 8 (#19) |
| Appendix C Verification matrix | *"For a smaller project, this may be the completed verification matrix."* | One table: R number, method, test, date, result |

**Engineering tests versus the record.** Appendix I keeps *"Developmental/Engineering Unit
Evaluations"* (6.1.1) apart from verification (6.1.2). It calls them *"the unofficial (not the formal
verification/validation) testing"* (7.1.1). For us: a quick try on a prototype is useful, but it is
not the verification of a requirement. `TEST_LOG.md` should show which kind each entry is.

---

## 10. MIT Session 9 — Verification and validation

Source: MIT 16.842, Session 9 "Verification and Validation", Prof. de Weck, 48 slides.

**The same two questions as NASA.** Slide 7: verification is *"Check if requirements are met"*,
*"Typically in the laboratory"*, *"Component/subsystem centric"*. Validation is *"Check if stakeholder
intent is met"*, *"Full-up system"*. We have no laboratory (C8): our "laboratory" is the bench and the
rigs we build.

**What aircraft ground testing covers.** Slide 16, "Aircraft Testing", ground testing: *"Weights and
Balance (determine mass, CG …)"*, *"Engine Testing"*, *"Fatigue Testing (static and dynamic
structural)"*, *"Avionics checkout"*, *"Pre-flight Testing (extended checklist)"*. Flight testing:
*"Flight Performance Testing"* and *"Stability and Controls (stall speed, trim, flutter …)"*.

For us, the ground-test list maps almost one to one onto P4: mass and centre of gravity
(`MASS_BUDGET.xlsx`), motors on the thrust stand (#56), avionics on the bench (#57), the pre-flight
checklist (#22). Fatigue testing has no issue yet; a static load test is named in #52.

**Testing caveats.** Slide 24, the whole list is worth knowing. Quoted in short:

- *"Testing is critical, but expensive"*
- *"Trust parts vendors or retest everything?"*
- *"Calibration of sensors and equipment"* — *"If sensors are not calibrated properly can lead to
  erroneous conclusions"*
- *"To what extent do the test conditions reflect actual operational usage?"*
- *"Use "dummy" components if the real ones are not available"* — *"are they representative?"*
- *"Failures often occur outside any test scenarios"*

For us: the vendor question is real. A motor's published thrust table is a named document, and
`REQUIREMENTS.md` allows a figure from a named document as input. But #47 already says every figure
is an estimate until our stand measures it. So we retest the parts our requirements rest on, and
trust the vendor for the rest. The plan should say which is which.

**How seriously V&V is taken decides the outcome.** Slide 26, on Appendix I: *"The degree to which
V&V is taken seriously and resources are made available is critical for project outcome"*. Among the
points: *"Planning ahead for tests"*, *"End-to-end functional testing"*, *"Can often "piggy-back" on
existing facilities, equipment …"*, *"Document outcomes well and follow-up with discrepancies"*. And:
*"This work is often not glamorous (except for some flight testing) but critical !"*

**A readiness review before flight.** Slide 45, Flight Readiness Review: *"Have all the V&V activities
been passed successfully?"*, *"Are there any waivers that need to be granted?"*, *"What are the
residual risks?"* For us: three questions to answer in writing before the first free hover
([DRM-0300]) and before the first free transition ([DRM-0400]). No board, just the two of us and the
issue for that flight.

---

## 11. HYDRO Figures 13 to 16 — A V&V schedule month by month

Source: Sutherland et al., IMDC 2015, section "Reviewing and Improving Activity on the
Assurance-V", Figures 12 to 16, PDF pages 8 to 10. The figures are images; read by rendering the
pages.

**What went wrong first (Figure 12, 2014).** *"much of the verification occurred only shortly before
the race itself and little to no validation work was performed on several critical systems."*

**The fix: one Assurance-V per month.** *"The Assurance-V is rebuilt as multiple diagrams for clarity
with each depicting a period of time"*. Each figure puts every test as a box on the V level it
checks, with a planned date. Read from the images:

| Figure | Month | Tests on the V (red = verification, blue = validation) |
|---|---|---|
| 13 | April/May | Validation by simulation only: energy balance, roll, drag/thrust/lift |
| 14 | June | Parts: GPS/electronics test. System: prototype test in tank, prototype test on lake. Ongoing simulation |
| 15 | July | Parts: tail foil endurance, motor endurance, hull water-proof. Sub-systems: V-foil, underwater pod, thrust, powertrain (ESC). System: drag test, water-proof test. Simulation updated |
| 16 | August | Whole boat: test in tank, test on lake. Then the race result, linked to stakeholder satisfaction |

**Three things in these figures that apply to us:**

1. **Every test has a date before it happens.** The boxes carry planned dates, some with a question
   mark (e.g. "2014-07-2?"). A date can be rough. It cannot be missing. For us: every test is an
   issue on the board with a Due date, set when the test plan is written.
2. **Parts first, then sub-systems, then the system — spread over months.** Not all in the last
   weeks. For us: P4 (component tests, due 21 Feb), P5 hover, P6 transition.
3. **Verification data improves the model.** *"The validation simulation is improved based on data
   gathering during the verification testing."* For us: thrust-stand data replaces the published
   motor figures in our sizing (#47), and the first flight log is the real test of any estimate (C9).
   SITL may be tuned with our data, but its output still never verifies a requirement (#6).

**A link back to the work products.** Figure 13's text: validation work *"now links to work products
displayed in the updated Development-V (Figure 11) such the work products can be marked as completed
based on the success of the validation work."* For us: an issue closes when its test passes and the
entry is in `TEST_LOG.md`, not when the test was run.

---

## 12. Where the sources and our files differ

| Point | Source says | We do | Why |
|---|---|---|---|
| Analysis | NASA: includes simulation and similarity (5.3) | Arithmetic only, measured or documented inputs | #6, C9: our models are not validated |
| Demonstration | NASA: no detailed data gathering (5.3) | G2 demonstrations read detailed log data | Label only; to decide in #19 |
| Waivers | NASA: a failed result can lead to a waiver (5.3.1.2.3) | No waivers; a six-field issue, or a fix and a retest | We are both judge and pilot |
| Qualification | NASA: tests at the environmental extremes | None | No facility (C8); wind and weather limits are written into each test plan instead |
| Laboratory | MIT slide 7: verification typically in the laboratory | Bench and our own rigs, each checked against a known value | C8 |

---

## What Stage 6 changes for us

1. **The loop for every test:** prepare, perform, analyse, report, capture. No test is run from
   memory.
2. **The procedure is written and committed before the test day,** with the requirement it verifies,
   the method, the pass/fail, and the rig check as a step.
3. **Every rig is an input with its own check.** Thrust stand against a known mass, scale against a
   known weight — written in the record of each test, not assumed.
4. **A short readiness check opens each test day** (an informal TRR): procedure, rig, firmware and
   parameter file, people, #22 safety rules.
5. **Stop on a surprise.** A discrepancy stops the test. Then decide: was the product wrong, or the
   procedure?
6. **Read the log before packing up.** A repeat costs a trip.
7. **A `TEST_LOG.md` entry has six parts:** data and log file, requirement version, product version
   (airframe, firmware, parameters), rig version and last check, pass or fail per R number,
   discrepancies.
8. **Engineering tests and verification are kept apart** in the log. A try on a prototype does not
   verify a requirement.
9. **Verification is done** when every R has a passed entry and no discrepancy is open.
10. **The rebuilt airframe gets an acceptance check,** a short named subset of tests, unless the
    design changed.
11. **Every test is an issue with a Due date on the board,** spread from parts to system over P4 to
    P6, as in HYDRO's monthly Assurance-V.
12. **Before the first free hover and the first free transition,** answer in writing: all planned
    V&V passed? Any open discrepancy? What risk is left?

**Open, for #19:** which tests repeat on a rebuilt airframe (point 10); whether the G2 requirements
keep the label "demonstration" (section 4); which vendor figures we retest and which we trust
(section 10).

## Read and skipped

- **Qualification testing** (NASA 5.3 box; Appendix I 4.2.4.1, 6.1.2.1.1). Needs environmental test
  facilities.
- **Certification** (NASA 5.3 box; Appendix I 4.4, 9.0). No certifying authority for an open-category
  privately built aircraft.
- **Payload classification, NPR 7120.5, NPR 8705.4, contractor SOWs** (NASA 5.3.1.2 factor list).
  Organisational.
- **Material Review Board, Configuration Control Board** (NASA 5.3.1.2.3 note). Assume an
  organisation.
- **Appendix I sections 2, 3.1–3.3, 3.5, 8.0** (documents, architecture descriptions, vehicle
  integration, on-orbit V&V). Covered by our own files, or not ours.
- **NASA 5.3.2 and the NASA Expanded Guidance.** A separate document. Not opened.
- **NASA Figure 5.3-1** (process flow) and **Figure 5.3-2** (end-to-end data flow). Images; not read.
- **NASA Table 5.3-1** (what a procedure and a report contain). Image; it did not load on nasa.gov on
  2026-11-11. Not read. Section 8 uses the text list in 5.3.1.2.4 instead.
- **MIT Session 9, slides 10–12** (NASA life-cycle phases and reviews). A large-programme review
  sequence; our two reviews are set in Stage 2.
- **MIT Session 9, slides 14, 25, 37.** Images ("Types of Testing", Appendix E matrix, risk process
  flow); not read.
- **MIT Session 9, slides 17–23** (F/A-18, spacecraft, JWST). Examples only.
- **MIT Session 9, slides 28–42** (technical risk management, risk matrix, STAMP/STPA). Risk is in
  `CONOPS.md` §8 already; STPA is for software-heavy systems with many controllers, a method we have
  no time to learn before P4. Worth a look if a crash cause is not found.
- **HYDRO Figure 17** (rebuilt project plan on the Basic-V). Belongs to Stage 8 and the cross-cutting
  sources.
