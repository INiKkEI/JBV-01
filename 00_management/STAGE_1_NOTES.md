# Stage 1 — Mission needs and concept of operations: reading notes

What we took from the Stage 1 sources listed in `REFERENCES.md`. One section per source, then
what it changes about how we run JBV-01. Read this before we write the ConOps.

---

## 1. The process: NASA's ten activities

Source: NASA SEH, Section 4.1 "Stakeholder Expectations Definition", subsections 4.1.1.1 to
4.1.1.3.

NASA's own summary of the purpose, in one line: "to identify who the stakeholders are and how
they intend to use the product." This is done through use-case scenarios (also called Design
Reference Missions, DRMs) and the ConOps.

The process has three inputs (4.1.1.1):

| Input | For us |
|---|---|
| Initial customer expectations | Ours only. We are the customer. There is no supervisor setting acceptance criteria |
| Other stakeholder expectations | Regulator, people near a test site, readers of the portfolio, suppliers. Full list in `01_requirements/STAKEHOLDERS.md`. **Revised** — readers of the portfolio removed, suppliers moved to dependencies, ILT added |
| Customer flow-down requirements | None. There is no level above us. This input is empty, and we should say so rather than leave it blank |

The process has ten activities (4.1.1.2.1 to 4.1.1.2.10):

| # | Activity | What it costs us |
|---|---|---|
| 4.1.1.2.1 | Identify stakeholders | One list. Cheap |
| 4.1.1.2.2 | Understand stakeholder expectations | Read the regulator's rules. The rest is us. Cheap |
| 4.1.1.2.3 | Identify needs, goals, and objectives (NGOs) | Real work. See section 2 |
| 4.1.1.2.4 | Establish ConOps and support strategies | The largest job in Stage 1 |
| 4.1.1.2.5 | Define expectations in acceptable statements | Writing up 4.1.1.2.3 after the ConOps has corrected it |
| 4.1.1.2.6 | Analyse statements for Measures of Effectiveness | Real work. See section 3 |
| 4.1.1.2.7 | Validate bidirectional traceability | We already have this rule |
| 4.1.1.2.8 | Obtain stakeholder commitments | Shrinks to a conversation. See section 6 |
| 4.1.1.2.9 | Baseline stakeholder expectations | A commit and a dated log entry |
| 4.1.1.2.10 | Capture work products | Decisions, rationale, assumptions, lessons learned. We already do this in the design log |

The four outputs (4.1.1.3): validated stakeholder expectations, the ConOps, enabling product
support strategies, and Measures of Effectiveness. A fifth is optional — human/system function
allocation.

**Order matters, and it is not the order we assumed.** NASA writes the initial expectations
first (4.1.1.2.3), *then* the ConOps (4.1.1.2.4), and then goes back and rewrites the
expectations (4.1.1.2.5). The handbook says this directly: developing the ConOps "may lead to
further refinement of the initial set of stakeholder expectations if gaps or ambiguous
statements are discovered." So the first list of needs and goals is a draft on purpose. We
should not try to get it right before writing the ConOps.

Figures and tables in this section, checked against the page:

- Figure 4.1-1 — process flow diagram, inputs / activities / outputs
- Table 4.1-1 — "Stakeholder Identification", examples by life cycle phase
- Figure 4.1-2 — "Information Flow for Stakeholder Expectations", how the information becomes
  high-level requirements. The yellow lines on it are validation paths
- Figure 4.1-3 — an example Lunar Sortie DRM early in the life cycle

## 2. Needs, Goals and Objectives — and the problem with our three goals

Source: NASA SEH, Section 4.1.1.2.3 "Identify Needs, Goals, and Objectives". NASA credits the
definitions to *Applied Space Systems Engineering* (Larson, Kirkpatrick, Sellers, Thomas and
Verma).

NASA's definitions, shortened but not changed in meaning:

- **Need** — "A single statement that drives everything else." It should relate to the problem
  the system solves, not to the solution.
- **Goals** — an elaboration of the need. A specific set of expectations. Goals do not have to
  be quantitative, but they must let us judge whether the system achieved them.
- **Objectives** — specific target levels of output. Each objective relates to one goal.

The four criteria for an objective, from the handbook:

1. Specific enough to give clear direction. About results, and about *what* not *how*
2. Measurable, quantifiable, and verifiable
3. Aggressive but attainable. Challenging but reachable
4. Results-oriented — desired outputs, not the method used to reach them

**Two lines from this subsection matter more to us than the rest.**

First: *"Objectives 'To Be Determined' (TBD) may be included until trade studies occur,
operations concepts solidify, or technology matures."* This is the sentence that unblocks Stage
1. Our configuration and our scale are both undecided. NASA says openly that an objective may
stay TBD until the trade study happens. So we can write the ConOps and the NGOs now, mark the
parts that depend on configuration and scale as TBD, and close them in Stage 3. We do not have
to decide the configuration early, and we do not have to stop.

The same subsection sets the deadline for those TBDs: "Objectives need to be feasible before
requirements are written and systems designed." So TBD is allowed in the ConOps, and not
allowed in `01_requirements/REQUIREMENTS.md` at the freeze.

Second: *"The need statement is singular. Trying to satisfy more than one need requires a trade
between the two, which could easily result in failing to meet at least one, and possibly
several, stakeholder expectations."*

We have three goals in a ranked order: portfolio piece, hands-on breadth, professional growth.
NASA's rule says the Need is one statement, not three. This is not a contradiction, but it does
force us to sort out something we have been carrying loosely since Stage 0.

The way the three items fit NASA's structure, as far as we can tell:

- They are not three needs. They are our goals for the **project**.
- The Need is about the **system** — the aircraft. NASA says the need is the problem the system
  solves.
- Our aircraft has no external user. Its purpose is to be the demonstration. So one candidate
  need statement is: *we need a way to show that the two of us can take a V/STOL aircraft from
  requirements to flight.* The three goals then sit under it as goals, in the order we already
  ranked them.

This looks right to us, but it is our reading, not something the handbook says about student
projects.

**First settled as, then rewritten as and fixed as.** The reading above led us to a
need statement about *us* — "demonstrate that the two of us can take a V/STOL aircraft to
verified flight". On re-reading it had four faults: the subject was us rather than the aircraft,
it carried our own method inside it, it duplicated a constraint, and it named V/STOL as a given
without explaining it.

The need is now about the aircraft and states a problem: *"We need an aircraft that does not
force a choice between landing anywhere and flying as long as a plane."* Runway independence sits
inside the problem, so V/STOL follows from the need instead of being assumed. The full history,
with everything rejected on the way, is in `01_requirements/NGO.md` sections 1 and 7.

Also worth keeping in mind: NASA says NGOs "are not contractual requirements or designs", and
that objectives "are not requirements". Objectives are pre-Phase A. They help form the
requirement set later. So Stage 1 output is not `REQUIREMENTS.md`. That file stays empty until
Stage 2.

## 3. Measures of Effectiveness — the name for the thing Stage 0 said we were missing

Source: NASA SEH, Section 4.1.1.2.6 "Analyze Expectations Statements for Measures of
Effectiveness".

Two terms:

- **Mission success criteria** define what the mission needs to accomplish to be successful,
  and how well.
- **Measures of Effectiveness (MOEs)** are "the measures of success that are designed to
  correspond to accomplishment of the system objectives as defined by the stakeholder's
  expectations." They are stated from the stakeholder's point of view. The handbook says they
  "can be synonymous with mission/project success criteria."

The test for whether something is an MOE, from the handbook's own definition of the outputs:
"failure to satisfy these measures will cause the stakeholder to deem the system unacceptable."

This closes an item Stage 0 left open. In Stage 0 section 3 we wrote that our validation
criteria — portfolio value and hands-on breadth — had not been written down, and that
professional growth was not going to be a validation criterion because we cannot fail it.
NASA's test gives the same answer from the other direction. If we cannot fail it, it cannot
make us call the system unacceptable, so it is not an MOE. Stage 0 and NASA 4.1 agree. Good.

**Superseded on 2026-08-09.** Portfolio value and hands-on breadth were both written down as
measures of effectiveness, and both have since been removed with the goals above them. The project
is about designing and building the aircraft. The reasoning in this section still holds — it is how
we test whether something is an MOE — but the two criteria it produced are gone.

MOEs are written when the NGOs are written, not later. NASA points to Section 6.7.2.4 of the
Expanded Guidance for more.

## 4. The ConOps: what it is, and what it is not

Source: NASA SEH, Section 4.1.1.2.4 "Establish Concept of Operations and Support Strategies",
and the boxed comparison "Concept of Operations vs. Operations Concept" in Section 4.1.

**The one property that matters most to us.** The ConOps gives "an implementation-free
understanding of the stakeholders' expectations by defining what is expected without addressing
how (the design) to satisfy the need."

Implementation-free means the ConOps does not name a tiltrotor, a tailsitter, or a ducted fan.
It says the aircraft takes off vertically, transitions to wing-borne flight, cruises, transitions
back, and lands vertically. Every V/STOL configuration on our list satisfies that sentence. So
writing the ConOps does not quietly decide the configuration, and it is not blocked by the
configuration being open. This is the strongest reason to do the ConOps next.

**Do not confuse the two documents:**

| | Concept of Operations | Operations Concept |
|---|---|---|
| Written when | Early, in Pre-Phase A | Later |
| Written by | The technical team | The operational team |
| Says what | The high-level concept of how the system will be used to meet stakeholder expectations, usually in a time-sequenced way | How the flight system and the ground system are used together to make the concept of operation reasonable |

We want the first one. NASA gives NPR 7120.5 as the source for the second.

What a ConOps typically contains, from this subsection: major phases; operation timelines;
operational scenarios and DRMs; fault management strategies; description of human interaction
and required training; end-to-end communications strategy; command and data architecture;
operational facilities; integrated logistic support; staffing levels and skill sets; and
critical events.

Two instructions in this subsection we should not skip:

1. **Off-nominal scenarios are required, not optional.** "The ConOps should include scenarios
   for all significant operational situations, including known off-nominal situations. To
   develop a useful and complete set of scenarios, important malfunctions and degraded-mode
   operational situations should be considered." For us that means writing down what happens on
   loss of radio link, loss of one motor in hover, a failed transition, a low battery in cruise,
   and a tip-over on landing — before we choose hardware, because these are the scenarios that
   produce requirements.
2. **Support strategies are part of this process.** "Support strategies include provisions for
   fabrication, test, deployment, operations, sustainment, and disposal." See section 8 below —
   this is where two of our sources disagree.

The handbook repeats the line the MIT lecture also gives: "Thinking through the ConOps and use
cases often reveals requirements and design functions that might otherwise be overlooked."

## 5. Appendix S — the outline we will actually fill in

Source: NASA SEH, Appendix S "Concept of Operations Annotated Outline".

The appendix opens by saying the exact content and sequence "will be a function of the type,
size, and complexity of the project." So cutting sections is allowed, as long as we say which
ones we cut and why.

The full outline, with our first judgement on each section. **These judgements are a proposal,
not a decision.**

| Section | Title | Our view |
|---|---|---|
| 1.1.1 | Background | Keep. Why we are building this |
| 1.1.2 | Assumptions and Constraints | Keep. Budget, one academic year, what we can make, EASA/RDW |
| 1.2.1 | Overview | Keep. One picture and a paragraph |
| 1.2.2 | System Scope | Keep, partly TBD. Size and complexity depend on scale, which is open. Range or TBD |
| 2.1 | Applicable Documents | Keep. EASA and RDW rules go here. Must be checked against the current pages, not from memory |
| 2.2 | Reference Documents | Keep. Short |
| 3.1 | Needs, Goals and Objectives | Keep. This is the output of section 2 above |
| 3.2 | Overview of System and Key Elements | Keep. Must stay implementation-free — functional elements only |
| 3.3 | Interfaces | Keep. Aircraft to pilot, aircraft to ground station, aircraft to battery and charger, aircraft to test site |
| 3.4 | Modes of Operations | Keep. Hover, transition, cruise, transition, hover, plus bench, tethered, and disposal modes |
| 3.5 | Proposed Capabilities | Keep. Includes capabilities needed only for verification, such as a tether point and a telemetry log |
| 4.0 | Physical Environment | Keep. Wind, temperature, rain, surface we land on. Netherlands weather is a real constraint |
| 5.0 | Support Environment | Keep, short. Spares, repair after the crash we are planning for, LiPo charging and storage, battery disposal |
| 6.1 | Nominal Conditions scenarios | Keep. Label them, e.g. [DRM-0100], so requirements can trace to them. The appendix recommends this labelling |
| 6.2 | Off-Nominal Conditions scenarios | Keep. Required by 4.1.1.2.4, and the highest-value part for us |
| 7.1 | Environmental Impacts | Cut down to a few lines. Noise at the test site, LiPo and foam waste |
| 7.2 | Organizational Impacts | Cut. Written for hiring and retraining. Two people |
| 7.3 | Scientific/Technical Impacts | Keep, short. This is where the portfolio goal is stated in the ConOps' own words |
| 8.0 | Risks and Potential Issues | Keep. The appendix says "Pay special attention to closeout issues at the end of the project" |
| App. A | Acronyms | Keep. We are writing in our second language and the reader may be too |
| App. B | Glossary of Terms | Keep |

Section 6.0 gives the labelling advice in full: "A good practice is to label each of these
scenarios to facilitate requirements traceability; e.g., [DRM-0100], [DRM-0200], etc." This
matches our own rule that every requirement names its parent. We should adopt the labels.

## 6. MIT Session 1 — the stakeholder half

Source: MIT 16.842, Session 1 "Systems Engineering Overview and Stakeholder Analysis"
(de Weck, Fall 2015). The stakeholder half runs from slide 30 to slide 54. Slide numbers are
the ones printed in the footer of each slide, checked against the PDF.

| Slide | Content |
|---|---|
| 32 | Concept Question 2 — why engage stakeholders before designing |
| 33–34 | NASA view of the stakeholder process, and where it sits in the SE engine |
| 35 | Who is a stakeholder — customers vs. other interested parties |
| 36 | Table: examples of stakeholders and their typical expectations |
| 37 | ConOps — why it is a major output of capturing expectations |
| 38 | Example ConOps: Lunar Design Reference Mission |
| 39 | Relationships among the upstream system design processes, citing SP-2007-6105 Figure 4.0-1 |
| 40 | Stakeholder Expectations Definition — best practice process flow diagram |
| 41 | Benefits of the stakeholder expectations process |
| 42–54 | Stakeholder Value Network (SVN) analysis, incl. the BP Whiting refinery case |

The definition on slide 35 is the same as NASA's: "A group or an individual who is affected by
or is in some way accountable for the outcome of an undertaking", split into customers and other
interested parties.

**Slide 36 is the most directly useful slide in the deck for us.** It is a table of stakeholder
types against their typical expectations. Reproduced here, and then translated:

| Stakeholder (MIT) | Typical expectation (MIT) | Our equivalent |
|---|---|---|
| Customer | Product quality, delivered on time, affordable, life cycle support | Us. There is no external customer — see the settlement below |
| Subcontractors / vendors | Well defined requirements | Hobby suppliers. We only need a correct part number and a delivery date |
| Local, state, national public | Products must not contaminate the environment | People near the test site. For us this is noise and safety, not contamination |
| Org management | Internal commitments met, compliance with policies | Nobody. There is no organisation above us — |
| Project manager | Technical work products on time, usable for decisions | Us |
| Technical team | Clear tasks, job security, rewards, teamwork | Us |
| Functional organisations (e.g. test) | Test support products available, clear test requirements | Nobody. We have no laboratory. Every test rig is one we build —, constraint C8 |

Slide 41, benefits of the process: build a system that meets customer expectations; build a
system that can be tested, operated and maintained; ensure stakeholder commitments are obtained
and realised.

**The question this raises: who is our customer?** NASA defines a customer as an organisation
or individual that requested the product and will receive it. Two readings are possible, and
they lead to different projects:

1. **We are the customer.** We asked for it, we build it, we keep it. Then activity 4.1.1.2.8
   "obtain stakeholder commitments" is the two of us agreeing and writing it in the design log.
   The risk is the one NASA warns about — with no external customer, nothing stops requirements
   creep except our own discipline.
2. **The supervisor and grader are the customer.** They receive the portfolio piece and they set
   the acceptance criteria, since a grade is an acceptance criterion. Then 4.1.1.2.8 is a real
   meeting with a real sign-off, and our MOEs have to be things they would recognise.

Reading 2 gives us an external check we would otherwise not have, and Stage 0's HYDRO lesson was
about a team with no external check. Reading 1 is closer to the truth of who wants this aircraft.

**Settled as reading 1.** We are the only customer. There is no supervisor setting
acceptance criteria. The cost is no external brake on requirements creep. Recorded in
`01_requirements/NGO.md`, and carried as a risk into the ConOps.

**Stakeholder Value Network analysis, slides 42–54.** Stage 0 already recorded this as noted and
skipped on purpose, and reading the slides has not changed that. The method has four steps —
map, quantify, search, analyse — and needs a questionnaire scoring every value flow for
intensity, importance and timing. The BP Whiting case study ran 5,039 value paths against 20 for
the simple hub-and-spoke model. The finding was real and useful: the two stakeholders that
mattered most, the public media and the local public, were the two the managers' own mental model
had ignored. But this is a tool for finding indirect relationships among a dozen organisations.
We have six stakeholders and no indirect relationships worth modelling. Still skipped.

## 7. HYDRO Table 3 — one row, and it is about us

Source: HYDRO — Sutherland, Kamiyama, Aoyama, Oizumi, IMDC 2015, Table 3 "Enablers for Lean
Principle 1: Value", enabler 1.2 "Establish the Value of the End Product or System to the
Customer". The enabler itself comes from Oppenheim, Murman and Secor 2011, "Lean Enablers for
Systems Engineering".

Table 3 has exactly one row. That is the whole table. The three columns:

| Enabler | Effectiveness in 2014 | Proposed change |
|---|---|---|
| 1.2 Establish the Value of the End Product or System to the Customer | "Multiple definitions of value were being worked towards, including to win the race and to maximize potential performance to increase student learning." | "At the project startup survey the students to learn their interests and use this to define value." |

The body text around Table 3 adds the consequence: "the project had considerable confusion over
what value was as there was a bias to attempt to build a very high performance boat to maximize
potential value but which ultimately sacrificed robustness of the craft when in the race."

That is the same failure in two sentences. They wanted to win *and* to learn. They never chose.
The bias fell towards the ambitious build. The ambitious build broke down during the race and
lost to simpler boats.

**Their fix is a survey. For two people, a survey is a conversation.** The same fix appears again
in Table 8, enabler 6.3: "Survey team members to understand their skills and aspirations." So for
us, defining value and mapping what each of us wants to learn is one conversation, and it should
happen before the ConOps is finished, not after.

We are in a slightly better position than they were. Stage 0 already ranked our three goals, and
HYDRO's problem was a missing ranking, not missing goals. What we still do not have is the thing
NASA asks for — the single Need statement above the ranking.

**One correction to the paper, for our own records.** In the section "LOOKING BEYOND THE V-MODEL
FOR DEVELOPMENT IMPROVEMENTS", the paragraph beginning "Flow:" says "Lean Enablers are detailed
in Table 3". That is wrong. The Flow enablers are in Table 5, which is titled "Enablers for Lean
Principle 3: Flow". Table 3 is Value. `REFERENCES.md` already points Stage 2 at Table 5 for
enabler 3.2, so our reference list is correct and the paper's body text is not. Recorded so that
neither of us wastes time on it later.

## 8. Where our sources disagree

Two places. Both are worth writing down because we have to choose.

**Disagreement 1 — does the V cover support and disposal?**

Stage 0 section 4 recorded, from REQI's "Limitations of the V-Model", that operation,
maintenance, repair and disposal sit *outside* the V and must be handled separately.

NASA 4.1 says the opposite. "Enabling Product Support Strategies" is one of the four named
outputs of the stakeholder expectations process, and it explicitly covers "fabrication, test,
deployment, operations sustainment, and disposal of the end product."

We should follow NASA here. Not because NASA outranks REQI, but because it costs us almost
nothing and it catches things we would otherwise miss: LiPo charging and storage, spare parts,
the rebuild after the crash we have planned for, and battery disposal at the end of the year.
Section 5.0 of the Appendix S outline is where these go. Stage 0's point still stands for
regulation and site selection — those are genuinely outside the V, and nothing in NASA 4.1
covers them either.

**Disagreement 2 — how much stakeholder machinery is proportionate?**

NASA 4.1 assumes an external customer, a mission authority, formal signatures, and a baseline
under change control. MIT Session 1 adds SVN analysis on top. HYDRO is a student team that
failed partly from having *too little* of this.

Our line: keep every activity that produces a written artefact we will reread (the stakeholder
list, the NGOs, the MOEs, the ConOps). Shrink the two activities that only exist to move
agreement between organisations — 4.1.1.2.8 commitments and 4.1.1.2.9 baseline — to a
conversation, a dated design log entry, and a commit. This is the same line Stage 0 drew between
a checkpoint and a ceremony.

---

## What Stage 1 changes for us

**Things we are adopting that we had not written down before:**

1. The ConOps is written to the Appendix S outline, with the cuts listed in section 5 above, and
   with the cuts stated in the document itself.
2. Operational scenarios get labels — [DRM-0100], [DRM-0200] and so on — so requirements can
   trace to them by name.
3. Off-nominal scenarios are written in Stage 1, not left to Stage 3. Radio loss, motor-out in
   hover, failed transition, low battery in cruise, tip-over on landing. At least these five.
4. TBD is allowed in the ConOps where a value depends on configuration or scale. TBD is not
   allowed in `REQUIREMENTS.md` at the freeze. NASA sets this boundary and we are taking it.
5. The first pass of needs and goals is written *before* the ConOps and rewritten *after* it.
   Two passes, on purpose, not one careful pass.
6. Support and disposal go in ConOps section 5.0. LiPo charging, storage, spares, the rebuild,
   and battery disposal.
7. MOEs are the name for our validation criteria. They are written at the same time as the NGOs,
   and the test for whether something is an MOE is whether failing it would make us call the
   aircraft unacceptable.

**Things we are deliberately not adopting:** Stakeholder Value Network analysis (confirmed
skipped after reading it, not skipped unread), Appendix S sections 7.2 and most of 7.1, and the
Operations Concept as a separate document from the ConOps.

**The items Stage 1 had to close, and where they now stand:**

| # | Item | Status |
|---|---|---|
| 1 | Who is the customer | **Closed.** We are the only customer, no supervisor |
| 2 | The single Need statement | **Closed.**, rewritten, fixed — the aircraft must not force a choice between landing anywhere and flying as long as a plane. `NGO.md` §1 |
| 3 | What value means | **Closed.** The fallback rule, in `NGO.md` §4 |
| 4 | The stakeholder list | **Closed.** `01_requirements/STAKEHOLDERS.md`. Restructured 2026-08-09 into three groups — who constrains us, who is affected by us, and dependencies |
| 5 | The MOEs | **Closed.** Four at the time, each failable. **Two remain** since 2026-08-09 — the two about how we work went with their goals. `NGO.md` §4 |
| 6 | The ConOps itself | **Closed.** `01_requirements/CONOPS.md`, written to the Appendix S outline with the cuts listed in section 5 above. Revised 2026-08-09: sections 7.1 and 7.3 had been left out and are now written, the cuts are now stated in the document itself, and the risk table moved from 7.0 to 8.0 |

Items 1 to 5 were settled on 2026-08-04, item 6 on 2026-08-05. The decisions, and what was
rejected in each case, are tracked as GitHub issues. This file is the reading behind those
decisions, not the record of them.

**Stage 1 is complete.** All four outputs exist: the stakeholder expectations in `NGO.md`, the
ConOps in `CONOPS.md`, the support strategies in ConOps section 5, and the measures of
effectiveness in `NGO.md` section 4.

Two things are carried forward rather than closed, and both are written down where they will be
seen. The Open Category subcategory conditions are still unread, so no test site can be chosen —
this blocks nothing in Stage 2 but blocks flying. And 11 of the 21 objectives still carry a TBD,
which is allowed here and not allowed at the requirements freeze.

**The process earned its keep, and it is worth recording where.** Walking through the off-nominal
scenarios revealed three objectives we had missed entirely. [DRM-0900], a lift unit failing in
hover, produced a maximum hover height (**deleted 2026-08-09**) and a minimum distance to
any person — the only two
objectives in the project that exist to protect a person rather than the project. Thinking through
a failed transition produced the ability to abandon one and return to hover: we had written that
the transition must work, but never that it must be possible to stop trying. That one is verified
in the [DRM-0400] test plan rather than as a scenario of its own, per.

None of the three is obvious from the need or the goals. We would have decided all of them at the
field, on the day, if we had not walked through the failures first.

**Still open, and Stage 1 does not close either of them:** configuration and scale. Section 2
above explains why this no longer blocks us. NASA allows a TBD objective until the trade study
happens, and the ConOps is implementation-free by design, so neither the ConOps nor the NGOs
require a configuration. Both close in Stage 3.

**One thing we have to do outside the reading.** ConOps section 2.1 "Applicable Documents" has to
list the current EASA and RDW rules, and ConOps section 4.0 has to describe the environment we
will actually fly in. Neither can be written from memory or from these four sources. The mass
limits we had been carrying — 250 g, 900 g, 25 kg — and the Netherlands operator registration route
have to be checked against the current EASA and RDW pages when we write that section. We have not
checked them in Stage 1, and nothing in this file should be read as having checked them.

**The row on slide 36 that turned out to be empty.** The slide lists "functional organisations,
e.g. test" as a stakeholder whose expectation is that clear test requirements reach them. When we
wrote this file we treated that row as a laboratory we would have access to. closed
that row to nobody. We have no laboratory.

The cost is recorded as constraint C8 in `01_requirements/NGO.md`: aerodynamic numbers are
estimates rather than measurements, and any test rig we want, we build ourselves.

**Partly re-opened on 2026-08-09.** A makerspace gives us laser cutting, free to us
as students. That is not a laboratory and it does not bring the university back stands — but
the row is no longer completely empty. It also breaks the pattern established: this is the one
capability in the project that depends on someone else's opening hours and someone else's machine.
Recorded as assumption AS6. Whether the makerspace holds any measuring instrument is unchecked, so
C8 itself has not moved.
