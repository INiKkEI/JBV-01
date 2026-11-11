# Stage 8 — System verification and validation: notes

The Stage 8 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources, and before writing the system V&V plan (#19), the flight test plans, or a
line of `06_flight/FLIGHT_LOG.md`. The rules for these notes are in `REFERENCES.md`, "How the stage
notes are written". Read `STAGE_6_NOTES.md` first: Stage 8 uses the same loop one level up.

**Checks.** Spot check: not done yet. Talk-through: not done yet.

**Read on 2026-11-11.** NASA 5.4, 5.5, Appendix E and Appendix T from the nasa.gov web version of
the handbook (Rev 2). MIT Session 10 from the OCW PDF, slide numbers as printed in the footer.

**Stage 8 in one sentence.** Verification asks whether JBV-01 meets R1 to R16; validation asks
whether it meets the need in `NGO.md` §1 — and an aircraft can pass the first and fail the second.

---

## 1. NASA 5.4 — Validation: the other question

Source: NASA SEH Rev 2, Section 5.4, introduction.

**What validation is.** *"While verification proves whether "the product was done right," validation
proves whether "the right product was done.""* Then: *"verification provides objective evidence that
every "shall" statement in the requirements document or specification was met, whereas validation is
performed for the benefit of the customers and users to ensure that the system functions in the
expected manner when placed in the intended environment."*

**What it is measured against.** *"System validation confirms that the integrated realized end
products conform to stakeholder expectations as captured in the MOEs, MOPs, and ConOps."*

For us:

- The stakeholder is the two of us (`STAKEHOLDERS.md` §1). Our expectations are `NGO.md` (need,
  goals, MOEs) and `CONOPS.md`.
- **MOE-1 and MOE-2 are our validation pass marks.** #72 judges them. Verification of R1 to R16 is
  not the same thing, even where the flight is the same.
- The **intended environment** is the test site: unprepared ground, Dutch wind and weather, reached by
  public transport. Not the bench.

---

## 2. NASA 5.4.1.1 and 5.4.1.2 — Inputs, and who validates

Source: NASA SEH Rev 2, Sections 5.4.1.1 "Inputs" and 5.4.1.2 "Process Activities".

**Verification comes first.** The first input is the *"End product to be validated: This is the end
product that is to be validated and which has successfully passed through the verification
process."* So a validation flight is flown on an aircraft whose requirements are already verified.

**The plan is fixed before.** *"Validation plan: This plan would have been developed under the
Technical Planning Process and baselined prior to entering this process."* It *"may be a separate
document or a section within the Verification and Validation Plan."* For us: one plan, #19.

**Expectations are baselined.** *"Baselined stakeholder expectations"* — *"It includes the needs,
goals, and objectives as well as the baselined and updated concept of operations and MOEs."* For us:
`NGO.md` and `CONOPS.md` as they stand at the freeze. A ConOps that is out of date is an input
error. (`CONOPS.md` §5.0 still says transport by car; D2 in #9 changed that.)

**The real operator validates.** Validation is *"performed by anticipated operators and/or users
whenever possible."* And in 5.4.1.2.1: *"When possible, actual end users/operators should be used"*.
For us: the Pilot, with the real transmitter, at the real site. Not a SITL run, not the bench.

**The same five steps as verification.** *"(1) preparing to conduct validation, (2) conduct planned
validation (perform validation), (3) analyze validation results, (4) prepare a validation report,
and (5) capture the validation work products."* See `STAGE_6_NOTES.md` sections 4 to 8.

**Validation includes the human.** One objective is *"To ensure the human has been properly
integrated into the system"*, among them: *"Operators and maintainers have the required skills and
abilities."* and *"Instructions are provided and training programs are in place."* For us: the Pilot's
SITL practice (#22, 3 profiles before the first free hover) and the checklists in #22 are part of
what validation looks at.

---

## 3. NASA 5.4 — Methods of validation

Source: NASA SEH Rev 2, Section 5.4.1.2, box "Methods of Validation".

The same four words as verification, but measured against expectations, not "shall" statements:

- **Demonstration:** *"Showing that the use of an end product achieves the stakeholder expectations as
  defined in the NGOs and the ConOps."* Again *"differentiated from testing by the lack of detailed
  data gathering."*
- **Test:** *"The use of an end product to obtain detailed data needed to determine a behavior"*.
- **Analysis:** *"Analysis includes the use of modeling and simulation as analytical tools."*
- **Inspection:** *"The visual examination of a realized end product."*

**Our MOEs are judged from the log.** MOE-1 and MOE-2 read the flight log in detail. By NASA's
wording that is a test, not a demonstration — the same label question as in `STAGE_6_NOTES.md`
section 4. To decide in #19, together.

---

## 4. NASA 5.4.1.2.2 to 5.4.1.2.4 — Perform, analyse, report

Source: NASA SEH Rev 2, Sections 5.4.1.2.2 "Perform Product Validation", 5.4.1.2.3 "Analyze Product
Validation Results", 5.4.1.2.4 "Prepare Report and Capture Product Validation Work Products".

**Validation is the normal flight, not the extreme.** *"Validation testing is focused on the expected
environments and operations of the system where as qualification testing includes the worst case
loads and environmental requirements"*. For us: a validation flight is flown in the conditions the
ConOps describes, inside the wind limit of its test plan — not in the worst wind we can find.

**Stop on a discrepancy, then find out whose fault it is.** *"When a discrepancy is observed, the
validation should be stopped and a discrepancy report generated."* Then: *"If there are no product
issues, the validation is replanned as necessary, the environment preparation anomalies are
corrected, and the validation is conducted again with improved or correct procedures and
resources."*

**Compare actual with expected.** *"It is important to compare the actual validation results to the
expected results."* Then decide whether a gap is *"a result of the test configuration or analysis
assumptions or whether they are a true characteristic or behavior of the end product."*

**What the validation report holds**, quoted as NASA lists it:

- *"Recorded validation results/data;"*
- *"Version of the set of stakeholder expectations used;"*
- *"Version and form of the end product validated;"*
- *"Version or standard for tools and equipment used, together with applicable calibration data;"*
- *"Outcome of each validation including pass or fail declarations; and"*
- *"Discrepancy between expected and actual results."*

For us: the same six fields as a `TEST_LOG.md` entry (`STAGE_6_NOTES.md` section 8), with two
changes: "version of the requirements" becomes the version of `NGO.md` and `CONOPS.md`, and a
**predicted** result is written before the flight, so the actual can be compared with it.

**Done means no open issue.** *"the validation process should not be considered or designated as
complete until all issues and actions are resolved."*

---

## 5. NASA 5.4 — Why validation fails

Source: NASA SEH Rev 2, Section 5.4.1.2.3, "Re-engineering", "Validation Deficiencies" and "Pass
Verification but Fail Validation?".

**Poor conduct is the first reason.** *"One reason is poor conduct of the validation (e.g., enabling
products and supporting resources missing or not functioning correctly, untrained operators,
procedures not followed, equipment not calibrated, or improper validation environmental
conditions)"*. For us, on a field day: a flat transmitter battery, a pilot who has not practised,
a checklist skipped, a rig not checked, too much wind.

**A gap in verification is the second.** *"A second reason could be a shortfall in the verification
process of the end product."* So a failed validation can send us back below the system level.

**A fix can break what worked.** *"Care should be taken that correcting a deficiency or set of
deficiencies does not generate a new issue with a part or performance that had previously operated
satisfactorily."* NASA names *"Regression testing, a formal process of rerunning previously used
acceptance tests"* as one way to catch it.

For us this is concrete: a change of a parameter to fix the transition can change the hover. After a
fix, the earlier passed checks that the change could touch are flown again — for example B1 and B2 in
hover before the next transition attempt. Which checks repeat after which kind of change is to be
decided in #19.

**Validate early.** *"Validation should be performed as early and as iteratively as possible in the
SE process since the earlier re-engineering needs are discovered, the less expensive they are to
resolve."*

**Pass verification, fail validation.** *"Sometimes systems successfully complete verification but
then are unsuccessful in some critical phase of the validation process"*. NASA's defence: *"Developing
a solid ConOps in early phases of the project (and refining it through the requirements development
and design phases) is critical to preventing unsuccessful validation."*

**Where this could happen to us.** All of R1 to R16 could pass and the aircraft still not meet the
need, for example if every wing-borne minute needed the lift motors (R2's known weak spot, VTOL assist
counts as wing-borne). The need in `NGO.md` §1 is a wing that carries the aircraft. A gap like that
is what validation is for.

**One airframe: validation is the acceptance.** *"For systems where only a single deliverable item is
developed, the Product Validation Process normally completes acceptance testing of the system."* For
several units, *"acceptance testing is the preferred means to ensure that subsequent deliverables meet
stakeholder expectations."* For us: the rebuilt airframe gets the acceptance check from
`STAGE_6_NOTES.md` section 3, not a second full validation.

---

## 6. NASA Appendix E — The validation matrix

Source: NASA SEH Rev 2, Appendix E "Creating the Validation Plan with a Validation Requirements
Matrix", text and Table E-1 (an image, read on the page).

**Plan validation while writing requirements.** *"When developing requirements, it is important to
identify a validation approach for how additional validation evaluation, testing, analysis, or other
demonstrations will be performed to ensure customer/sponsor satisfaction."*

**Where the plan comes from.** NASA's list starts with: *"ConOps"*, *"Stakeholder/customer needs,
goals, and objectives documentation"*, *"Rationale statements for requirements and in verification
requirements"*. For us: `CONOPS.md`, `NGO.md`, and the rationale fields in `REQUIREMENTS.md`.

**Validation is not only the final flight.** Validation products *"can take the form of a wide range
of deliverables"*, including *"Physical models of all fidelities"*, *"Simulations"*, *"Tests"*,
*"Fit-checks"* and *"Procedure dry-runs"*. And: *"early validation can have a profound impact on the
design and cost in the later life cycle phases."*

For us, small early validation products that cost almost nothing:

- a **fit-check** of the packed aircraft in two 85 cm packages before the first trip (R6);
- a **procedure dry-run** of the #22 checklists at home, before the first field day;
- a **SITL run** of the full profile, as an early look only. Whether a simulation may count as a
  validation product is open: `NGO.md` §8 (#6) says no simulation output is an input to
  verification; it says nothing on validation. To decide in #19.

**Table E-1, the columns.** *Validation Product #*, *Activity*, *Objective*, *Validation Method*,
*Facility or Lab*, *Phase*, *Performing Organization*, *Results*. The footnote lists phases from
*"during product selection process"* to *"during on-orbit functional"*.

Cut down for JBV-01:

| Column | For us |
|---|---|
| Validation product # | V1, V2, … (flat, never reused, like R numbers) |
| Activity and objective | What is done, and which expectation it checks: MOE-1, MOE-2, a ConOps scenario |
| Method | Test, demonstration, inspection — analysis only under the #6 rule |
| Facility | Home, makerspace, test site, SITL |
| Phase | P4 to P7 milestone |
| Performer | Pilot, Nikita, both |
| Results | Link to the `FLIGHT_LOG.md` or `TEST_LOG.md` entry |

---

## 7. NASA 5.5 — Product transition

Source: NASA SEH Rev 2, Section 5.5 "Product Transition".

**For us, "transition" in NASA's sense is moving the aircraft.** NASA's two forms are delivery to the
next level up, and *"The delivery of the final end product to the customer or user that will use it
in its operational environment."* We are both builder and user. Our transition is every trip from
home or makerspace to the test site, and the final hand-over is the end of the project (C2).

**Packaging is an enabling product, planned in design.** *"The requirements for packaging, handling,
storage, training, and transportation should have been identified during system design."* NASA warns
about *"protecting surfaces from physical damage"*, *"eliminating damage to electronic wiring or
cabling, shock or stress damage"* and *"moisture"*. And: *"The ease and safety of packing and
unpacking the product should also have been addressed."*

For us: the two packages of R6 are an enabling product. They are designed with the airframe (P3),
not found on the morning of the first flight.

**Check after every trip.** Under "Confirm Ready to Support": *"After installation, whether into the
next higher assembly or into the final customer site, functional and acceptance testing of the end
product should be conducted. This ensures no damage from the shipping/handling process has occurred
and that the product is ready for support."* For us: R6 already asks for the bench check [DRM-0100]
after the trip. It belongs at the start of every field day, not only once.

**Hazardous material travels with rules.** *"Special consideration should be given to safety,
including clearly identifiable tags and markings that identify the use of hazardous materials,
special handling instructions, and storage requirements."* For us: LiPo packs on public transport.
The NS terms read on 2026-11-11 (Art. 5.5) say nothing on batteries; the carriers' rules for LiPo are
**not checked**. To check before the first trip with packs (#22).

**Survey the site early.** *"the site survey should be made during an early phase in the product life
cycle."* For us: the test site (#25, `CONOPS.md` risk R1) is found and checked against `RULES.md` NL1
to NL4 long before the first flight.

---

## 8. NASA Appendix T — Operating the aircraft once it is built

Source: NASA SEH Rev 2, Appendix T "Systems Engineering in Phase E". Phase E is operations; for us
that is the flight campaign, P5 to P7.

**Four things must exist before operations.** *"Successful Phase E execution requires the prior
establishment of mission operations capabilities in four (4) distinct categories: tools, processes,
products, and trained personnel."* For us: tools (transmitter, laptop with Mission Planner, log
download), processes (checklists, anomaly handling), products (parameter file, flight test plans),
trained personnel (the Pilot, practised in SITL).

**Write down what the aircraft can and cannot do.** *"Development phase activities need to clearly and
concisely document system knowledge in the form of operational techniques, characteristics, limits,
and constraints"*. For us: one short page of limits for the Pilot (wind, battery reserve, heights,
failsafe actions R14 and R16), taken from the files, not from memory.

**Use the same products in testing and in operations.** *"system engineers should identify
opportunities for product reuse early in the development process and establish common standards,
formats, and content expectations"*. For us: the `TEST_LOG.md` entry format and the `FLIGHT_LOG.md`
entry format share the same fields, so a bench check and a flight read the same way.

**Have an anomaly process before the first flight.** *"every project should develop a formal process
for handling anomalies and managing risk during operations. This process should be exercised before
flight, and decision-makers should be well versed in the process details."* For us: what we do when
something unexpected happens on the field — land, disarm, stop, write it down, decide at home. In
#22, and tried once in a dry run.

**Changes during operations are change requests.** *"These changes or additions are generally handled
as change requests to an operations baseline"*. For us: a parameter changed on the field is written
in `FLIGHT_LOG.md` with the old and new value before the next flight. The parameter file is part of
the product version (`STAGE_6_NOTES.md` section 8).

**Keep the flight data safe and at hand.** *"Critical operations materials, including procedures,
plans, flight datasets, and technical reference material need to be secure, up to date, and easily
accessed"*. And: *"Tools, procedures, and other infrastructure for Technical Data Management must be
baselined, implemented, and verified prior to flight operations."* For us: the checklists and the
parameter file are on the phone, offline; the log is downloaded and copied before leaving the field;
the `FLIGHT_LOG.md` format is fixed before the first flight, not invented after it.

---

## 9. MIT Session 10 — Commissioning and operations

Source: MIT 16.842, Session 10 "Commissioning and Operations", Prof. de Weck, 38 slides.

**The questions to answer before operating.** Slide 10, "Operational Considerations", in full:
*"How will the system be operated?"*, *"What insights do the operators need into the system
status?"*, *"Before turning over to the operators what checks need to be performed?"*, *"How might the
system fail?"*, *"What options are available to the operators in the event of system failures?!"*,
*"What spares are needed to repair the system?"*, *"Will the system still perform even under partial
failures?"*

For us, most already have an answer: operation (`CONOPS.md`), status (R12 telemetry), checks
([DRM-0100]), failure (DRM-0700 to DRM-0900), options (R14, R16, R13 kill switch), spares (R9, no
spares), partial failure (DRM-0900: no). The last two are the weak ones.

**Commissioning = checkout before use.** Slide 16, "Product Transitioning", under Checkout:
*"Turning on all systems and subsystems"* and *"Comparing predicted parameters against actual
behaviors"*. For us: before the first free hover, every system is switched on once on the field, and
the measured values are compared with the predicted ones written down beforehand (hover throttle,
current draw, battery use per minute).

**Review every flight against the prediction.** Slide 34, "Post Flight Assessment Review (PFR)":
*"Review telemetry from flight"*, *"Compare against predictions (e.g. from simulation)"*, *"Find /
repair any failures"*, *"Secure data for later use"*. For us: this is #71 (flight log analysis after
every flight). A prediction may come from SITL or from arithmetic; it is compared, never used as a
pass mark (#6).

**The ops checklist.** Slide 35, "Summary: Ops Checklist", quoted:

- *"System checkout in lab/hangar/field; everything working OK?"*
- *"Bring sufficient consumables (batteries, fuel, lubricants etc…), including reserves"*
- *"Spare parts and tools to repair"*
- *"Other support equipment (remote control, telemetry, cameras …)"*
- *"Training operators and support personnel"*
- *"Checklist for normal operations and emergency/contingencies"*
- *"Transportation logistics (forward and reverse)"*
- *"Plan in enough time for commissioning"*

For us: this list is almost a ready field-day packing and readiness list for #22. "Reverse" logistics
matters: a crashed airframe and a damaged LiPo must also travel home, in the same two packages.

**Off-nominal states.** Slide 29: aerospace systems spend *"significant time operating in degraded or
off-nominal states"*. For us: covered by DRM-0700 to DRM-0900 and R14, R16. The multi-state design
method on slides 29 to 32 is skipped (see the end).

---

## 10. Where the sources and our files differ

| Point | Source says | We do | Why |
|---|---|---|---|
| Simulation in validation | NASA 5.4 and App. E: simulation is a validation method and product | Open — #6 only rules on verification | To decide in #19 |
| Customer discussions | NASA 5.4: deficiencies are discussed with the customer | We are the customer; a change to `NGO.md` or `CONOPS.md` is a six-field issue | Stage 2, Settled 4 |
| Demonstration | NASA: no detailed data | MOE-1 and MOE-2 read the log in detail | Label only; to decide in #19 |
| Configuration Control Board | NASA App. T: changes in operations go through a CCB | Old and new value in `FLIGHT_LOG.md`; a requirement change is an issue | Two people |
| Transport | NASA 5.5: packaging set in design | `CONOPS.md` §5.0 still says car | D2 (#9) changed it; the ConOps is not yet updated |

---

## What Stage 8 changes for us

1. **Verification and validation are two checks.** R1 to R16 are verified; MOE-1 and MOE-2 (#72)
   validate against `NGO.md` and `CONOPS.md`. Passing the first does not prove the second.
2. **Validation comes after verification,** on an aircraft whose requirements already passed, flown
   by the Pilot at the real site, in the conditions the ConOps describes.
3. **The ConOps must be current before validation.** `CONOPS.md` §5.0 (car → public transport) needs
   its six-field change.
4. **Write the prediction before the flight.** Every validation or commissioning flight has expected
   values written down first; the report compares actual with expected.
5. **After a fix, repeat what the fix could break** (regression): e.g. a parameter change for the
   transition is followed by the hover checks again.
6. **Validate early with cheap products:** a fit-check of the two packages, a dry run of the #22
   checklists, and possibly a SITL look at the full profile.
7. **A validation matrix,** V1, V2, …, with activity, expectation, method, place, phase, performer,
   result. MOE-1 and MOE-2 are its main rows.
8. **The transport packages are designed with the airframe** (P3), and a bench check opens every
   field day.
9. **Before the first flight:** the four operations capabilities exist (tools, processes, products,
   trained Pilot); a one-page limits sheet; an anomaly process tried once; `FLIGHT_LOG.md` format
   fixed; checklists and parameter file offline on the phone.
10. **A changed parameter on the field** is written with old and new value before the next flight.
11. **Every flight is reviewed against its prediction** (#71), and the log is secured before leaving
    the field.
12. **The field-day list** follows MIT slide 35, including reserves and the trip home.

**Open, for #19:** may a SITL run count as an early validation product (section 6); which checks
repeat after which kind of change (section 5); the demonstration label (section 3). **To check before
the first trip with packs:** the carriers' rules for LiPo on public transport (section 7).

## Read and skipped

- **NASA 5.4.2, 5.5.2 and the NASA Expanded Guidance.** A separate document. Not opened.
- **NASA Figures 5.4-1 and 5.5-1** (process flows). Images; not read.
- **NASA 5.4, HSI Plan** (human systems integration). A separate NASA plan; our human factors are the
  Pilot's practice and the checklists.
- **NASA 5.5, delivery to thousands of users, KSC examples, NEPA approvals.** Not our scale.
- **NASA Appendix T, T.3.1.2 to T.3.2.4 and T.3.3.1 to T.3.3.3, T.3.3.7, T.3.3.8** (requirement,
  interface and decision management during a space mission). Our process is the same before and
  during flight testing.
- **MIT Session 10, slides 5, 8, 9** (F/A-18 selection, fatigue monitoring, Space Shuttle cost).
  Examples only. Slide 9's point that maintainability must be designed in is already R8 and R9.
- **MIT Session 10, slides 11, 13 to 15, 17** (NASA life-cycle phases and process charts). Covered by
  NASA 5.5.
- **MIT Session 10, slides 18 to 21** (JWST commissioning). Example only.
- **MIT Session 10, slides 23 to 28** (spare-parts models with Poisson failures and
  reconfigurability). Needs failure-rate data we will not have; R9 chose no spares.
- **MIT Session 10, slides 29 to 32** (multi-state design for degraded aircraft). A research method
  needing a validated performance model (C8).
