# Stage 2 — System requirements: reading notes

What we took from the Stage 2 sources listed in `REFERENCES.md`. One section per source, then
what it changes about how we run JBV-01. Read this before we write a single line of
`01_requirements/REQUIREMENTS.md`.

---

## 1. NASA 4.2 — the process that turns the ConOps into "shall" statements

Source: NASA SEH, Section 4.2 "Technical Requirements Definition", subsections 4.2.1.1 to
4.2.2.

NASA's own one-line purpose: the process "transforms the stakeholder expectations into a
definition of the problem and then into a complete set of validated technical requirements
expressed as 'shall' statements". It is "recursive and iterative". It runs from the top level
down to the lowest component.

**The four inputs (4.2.1.1).** All four are things Stage 1 produced.

| NASA input | Where ours is | State |
|---|---|---|
| Baselined stakeholder expectations | `01_requirements/NGO.md` | Exists. **9 objectives**, of which 6 carry a TBD |
| Baselined ConOps | `01_requirements/CONOPS.md` | Exists |
| Baselined enabling support strategies | ConOps section 5.0 | Exists |
| Measures of Effectiveness | `NGO.md` section 4 | Exists. **Two** MOEs — one per half of the need |

A fifth input is optional: human/system function allocation. Ours is one line — one remote pilot,
one observer, both of us.

**The seven activities (4.2.1.2.1 to 4.2.1.2.7).**

| # | Activity | What it costs us |
|---|---|---|
| 4.2.1.2.1 | Define constraints, functional and behavioural expectations | Mostly done. `NGO.md` section 6 holds **22** constraints, C1 to C23 |
| 4.2.1.2.2 | Define requirements | The main work of Stage 2 |
| 4.2.1.2.3 | Define requirements in acceptable statements | Rewriting activity 2 to the Appendix C rules. See section 6 below |
| 4.2.1.2.4 | Validate technical requirements | Six steps. This is the agenda of our requirements review |
| 4.2.1.2.5 | Define MOPs and TPMs | New to us. See section 4 |
| 4.2.1.2.6 | Establish the technical requirement baseline | The freeze. NASA holds an SRR here |
| 4.2.1.2.7 | Capture work products | We already do this |

> **Counts out of date since 2026-09-08.** The two tables above were written on 2026-09-04,
> against the requirements baseline as it stood that day. The rewrite of 2026-09-08 removed the
> performance goal and every objective under it. Counted from `NGO.md` today: **7 objectives** —
> G1-O1, G1-O2 and G2-O1 to G2-O5 — and **no objective carries a TBD**. Section 6 holds **23
> constraints**, C1 to C23; the "22" above was a miscount as well as out of date. The two MOEs are
> unchanged. Only the counts are wrong. Nothing in the reading below depends on them.

**The three outputs (4.2.1.3):** validated technical requirements, Measures of Performance, and
Technical Performance Measures.

**Types of requirement named in 4.2.1.2.2.** Functional (what functions must be performed),
performance (how well), interface (product to product). Crosscutting: environmental, safety,
human factors, the "-ilities", and design and construction standards. NASA is explicit that a
complete set needs all of these types, not only the exciting ones.

**Key Driving Requirements (KDRs), in 4.2.1.2.3.** A KDR is a requirement "that can have a large
impact on cost or schedule when implemented". NASA says a KDR can have any priority. Knowing
which requirements are KDRs lets you manage them.

This is the single most useful idea in 4.2 for us. Our budget is €800 hard (C3) and our schedule
is one academic year (C2). A requirement that quietly costs €200 or six weeks is more dangerous
to this project than a requirement that is merely hard.

**Rationale, in 4.2.1.2.3.** NASA asks for four things in the rationale, and asks that it be kept
up to date:

1. the reason for the requirement, referencing the parent requirement or trade study;
2. the assumptions it was written under;
3. the relationship to expected operations — a link to the ConOps;
4. design constraints imposed by decisions made as the design evolves. If the requirement states
   a method of implementation, the rationale must say why the solution was limited to that method.

**The note at the top of the section, and why it is empty for us.** NASA opens 4.2 with a warning
that the team "must not rely solely on the requirements received", and that communication and
iteration with stakeholders is needed so nobody builds the wrong thing. This assumes requirements
arrive from someone else. We are the only customer, so no requirement arrives from outside. The warning does not apply — and that is a cost, not a saving. Stage 1 already
recorded it as our missing external brake.

**Where the baseline is set (4.2.1.2.6).** Requirements are baselined and put under configuration
control once they are validated and agreed. NASA holds a System Requirements Review at this point
and points to Section 6.7 for it. Stage 0 already decided to hold a light requirements review
before the freeze. This is the same event, and now it has a name and an agenda.

## 2. The six validation steps — 4.2.1.2.4

Source: NASA SEH, Section 4.2.1.2.4 "Validate Technical Requirements".

Requirements are validated against the stakeholder expectations, the mission objectives and
constraints, the ConOps, and the mission success criteria. Six steps, in NASA's order:

| # | Question | For us |
|---|---|---|
| 1 | Are the requirements written correctly? | Appendix C.2 and C.3, run by whoever did not write the requirement |
| 2 | Are they technically correct? | Check three things: bidirectional traceability to `NGO.md`, valid assumptions, and that the requirement is essential |
| 3 | Do they satisfy stakeholders? | We are the stakeholder. Cheap, and weak |
| 4 | Are they feasible? | The step that catches an aircraft we cannot build for €295 |
| 5 | Are they verifiable? | The step that catches a requirement we cannot test with no laboratory (C8) |
| 6 | Are they redundant or over-specified? | Every requirement unique and necessary |

NASA then lists five things the team should be prepared to demonstrate before moving on. Two of
them matter to us: that requirements and MOEs are consistent with stakeholder needs, and that
**the process for managing change in requirements is established, documented, and communicated**.
We do not have that process written down yet. Our project method says changes go through an open
logged revision, but we have never said what a revision looks like.

## 3. Two smaller points from 4.2

Both worth keeping, neither large enough for a section of its own.

**Requirements can come from non-obvious stakeholders.** NASA says the systems engineer should
look early for ways the system can collect information not related to the primary mission.
Translated to us: if a telemetry log or an onboard camera is nearly free once the aircraft exists,
adding it early is cheaper than adding it later. **This line originally pointed at a goal that has
since been removed.** The point survives without it: telemetry and logging are already
required capabilities in the ConOps, §3.5, and the flight log is how MOE-1 is verified.

**Every requirement gets a "shall", one per statement.** Complete sentences. This sounds trivial
and is the rule most often broken, because two requirements in one sentence look efficient.

## 4. MOPs and TPMs — a new layer we did not have

Source: NASA SEH, Section 4.2.1.2.5 "Define MOPs and TPMs".

| Term | NASA's definition, shortened | Point of view |
|---|---|---|
| MOE | Measure of Effectiveness. Success as the stakeholder sees it. Can be qualitative | Stakeholder |
| MOP | Measure of Performance. Performance the system must show when operated in its intended environment. Quantitative and measurable | Supplier |
| TPM | Technical Performance Measure. A physical or functional characteristic, taken from the MOPs, that is critical to mission success and is **tracked over time** | Project management |

Two things follow from the definitions. MOPs are derived from MOEs, and there are usually several
MOPs for one MOE. TPMs are the small set you plot against the calendar: you compare the current
value with the value you expected at this date, to catch a problem before it becomes a failure.

NASA points to Section 6.7.2.6.2 of the Expanded Guidance for more. We have not read it.

**Our reading, not NASA's.** MOEs we have. MOPs are close to what our project method already
calls the pass/fail criterion on each requirement, so a separate MOP list would be a second copy
of the same numbers. TPMs are different, and cheap, and we have nothing like them: two numbers
tracked by date would tell us early whether the project is going wrong. The obvious two are total
mass and money spent. This is a proposal for section 10, not a decision.

## 5. Appendix D — and the tables we could not read

Source: NASA SEH, Appendix D "Requirements Verification Matrix".

What the page says in text:

- Identify an approach for verifying each requirement **while the requirements are being
  developed**, not later.
- Only "shall" requirements go in the matrix.
- Each "shall" is identified by a unique identifier.
- The matrix is definitive about the source — the document each requirement is taken from.
- It may be split into several matrices, one per requirements document.
- Table D-1 is an example, showing "the minimum information that should be included".
- A note on the page: the same matrix appears as Appendix C of the Verification and Validation
  Plan outline in Appendix I.

**Table D-1 itself is an image on the NASA page, and we could not read it.** The same is true of
Table 4.2-1, Table 4.2-2, Figure 4.2-2 and Figure 4.2-3. The text of the handbook PDF stops
before those pages when fetched, and the page images cannot be read as text.

So we know what Appendix D is for, and we do not know its column headings. Under the standing
rule in `REFERENCES.md`, we must not write those columns from memory and must not present them to
a reader as NASA's. **This needs a browser, same as the two open jobs already listed in
`REFERENCES.md`.** Until then, the column set in `REQUIREMENTS.md` is ours, not NASA's, and
should be labelled that way.

Two page numbers we did check, from the contents list of the Rev 2 PDF: Appendix D starts at
page 240, and Table D-1 is on page 241.

## 6. Appendix C — the four checklists we will actually run

Source: NASA SEH, Appendix C "How to Write a Good Requirement", subsections C.1 to C.4.

### C.1 Use of correct terms

Three words, three meanings. This is the whole subsection:

| Word | Meaning |
|---|---|
| **shall** | requirement |
| **will** | facts or declaration of purpose |
| **should** | goal |

### C.2 Editorial checklist

Split into personnel requirements and product requirements. Ours are product requirements.

- Form: "product ABC shall XYZ". Active voice.
- Consistent terminology for the product and its lower-level parts.
- Complete with tolerances for any quantitative value — less than, greater than or equal to,
  plus or minus, 3 sigma root sum squares.
- Free of implementation. State the problem, not the solution. NASA's test: ask "why do you need
  the requirement?" The answer may be the real requirement.
- Free of descriptions of operations. NASA's test: a sentence starting "the operator shall…" is
  almost always an operational statement, not a requirement.

NASA's own example requirements: "The system shall operate at a power level of…", "The structure
shall withstand loads of…", "The hardware shall have a mass of…".

### C.3 General goodness checklist

Seven items. Two of them change what we do:

- **"The requirement is stated positively (as opposed to negatively, i.e., 'shall not')."**
  Several of our constraints are naturally negative. C17 is "no dangerous goods carried, nothing
  dropped in flight". That has to be rewritten in positive form or it fails this check.
- **TBD versus TBR.** NASA: the use of TBD "should be minimized. It is better to use a best
  estimate for a value and mark it 'To Be Resolved' (TBR) with the rationale along with what
  should be done to eliminate the TBR, who is responsible for its elimination, and by when it
  should be eliminated."

The other five: grammatically correct; free of typos and punctuation errors; complies with the
project's template and style rules; accompanied by an intelligible rationale including any
assumptions, which must be confirmed before baselining; and located in the proper section of the
document, not in an appendix.

### C.4 Requirements validation checklist

Thirteen groups: Clarity, Completeness, Compliance, Consistency, Traceability, Correctness,
Functionality, Performance, Interfaces, Maintainability, Reliability, Verifiability/Testability,
Data Usage.

The items that will cost us the most work:

- **Clarity.** No indefinite pronouns (this, these). No ambiguous terms — "as appropriate",
  "etc.", "and/or", "but not limited to". One thought per statement. One subject and one
  predicate.
- **Completeness.** NASA lists the areas that get overlooked: functional, performance, interface,
  environment (development, manufacturing, test, transport, storage, operations), facility,
  transportation, training, personnel, operability, safety, security, appearance and physical
  characteristics, and design.
- **Traceability.** "Are all requirements needed?… Distinguish between needs and wants. If it is
  not necessary, it is not a requirement." NASA's test: "What is the worst that could happen if
  the requirement was not included?" Every requirement bidirectionally traceable, and uniquely
  numbered.
- **Performance.** "Are the tolerances overly tight?" NASA's test: "What is the worst thing that
  could happen if the tolerance was doubled or tripled?"
- **Verifiability/Testability.** The banned word list, given in full by NASA: *flexible, easy,
  sufficient, safe, ad hoc, adequate, accommodate, user-friendly, usable, when required, if
  required, appropriate, fast, portable, light-weight, small, large, maximize, minimize,
  sufficient, robust, quickly, easily, clearly, other "ly" words, other "ize" words.*

**That list already catches wording we have written.** *(The maximum hover height objective was
deleted on 2026-08-09. The example below is kept, because it is the clearest one we have of the C.4
check finding a real fault in our own writing. The same problem now sits in **G2-O4**'s "under
control".)* That objective set a maximum
hover height "chosen
so that a fall from it is survivable for the airframe and harmless to any person". "Survivable"
and "harmless" are exactly the kind of word C.4 bans, because no test can be written for them.
The objective is right. The sentence will not survive as a requirement.

The banned word list is also the cheapest check in the whole appendix, because it can be run as a
text search over `REQUIREMENTS.md` before the freeze instead of by reading.

## 7. MIT Session 2 — Requirements Definition

Source: MIT 16.842, Session 2 "Requirements Definition" (de Weck, Fall 2015), 55 slides. Slide
numbers below are the ones printed in the footer of each slide, checked against the PDF. Slides
28 and 47 carry a number but no text we could extract; they are images.

| Slide | Content |
|---|---|
| 2 | The V-model, with the session number marked on each stage |
| 4 | What requirements are. Performance, schedule, cost, lifecycle properties. High level says what, not how |
| 5 | Mars Climate Orbiter. Bad requirements example |
| 6 | DC-3. Good requirements example |
| 7 | Requirements explosion since the 1970s (AIAA MDO TC white paper, 1991) |
| 8 | Requirements standards: NASA SP-2007-6105, INCOSE SE Handbook v3.1, ISO/IEC 15288 |
| 9 | Requirements set constraints and goals in the design space and the objective space |
| 10 | Concept Question 3 — requirements versus specifications |
| 11 | Requirements versus specifications, with a microwave oven example |
| 13 | The NASA technical requirements definition process in the SE engine |
| 15 | Purpose: transform baselined stakeholder expectations into unique, quantitative, measurable requirements |
| 16–17 | Why requirements development matters. Seven benefits |
| 18 | Interrelationships among the system design processes (cites SP-2007-6105, Figure 4.01) |
| 19 | Types of requirement, with a worked example of each |
| 20 | Attributes of acceptable requirements — per statement, and per set |
| 22 | Decomposition, allocation and validation (cites SE HB Figure 4.2-3) |
| 23 | Requirements margins management |
| 24 | Historical mass growth in manned spacecraft (NASA JSC-26098, Nov 1994) |
| 25 | Monitoring a requirement with a TPM |
| 26 | Technical requirements definition best practice process flow diagram |
| 27 | Capturing requirements: document versus database |
| 29 | Worked example of hierarchical requirements with links |
| 31–32 | Requirements allocation, and the allocation process |
| 33–41 | Isoperformance, and the Nexus spacecraft case study |
| 42–43 | Concept Question 4 — the balloon, and its solution |
| 44–45 | Common problems with requirements |
| 46 | Verification: every requirement verified by examination, test, demonstration or analysis |
| 49–50 | The System Requirements Review |
| 51 | Requirements volatility |
| 55 | Summary |

Two readings are named on the slides: de Weck and Jones, "Isoperformance", *Systems Engineering*
9(1), 45–61, 2006 (slide 33); and Peña and Valerdi, "Characterizing the Impact of Requirements
Volatility on Systems Engineering Effort", *Systems Engineering* 18, 59–70, 2015 (slide 51).
Neither has been read.

**Slide 8 gives page numbers for the 2007 edition, not ours.** It cites Appendix C at pp. 279–281
and Appendix D at pp. 282–283 of SP-2007-6105. We work from Rev 2 (SP-2016-6105), where Appendix
D is at p. 240. The section and appendix letters are the same in both. The page numbers are not.
Do not use MIT's page numbers against our copy.

### The two examples on slides 5 and 6, and why they are the right pair

**Mars Climate Orbiter (slide 5).** Launched 11 December 1998, lost on orbit insertion on
23 September 1999. Ground software produced output in pound-force seconds instead of newton
seconds. The contract did specify SI units, and the requirement was flowed down to the Software
Interface Specification — but it was never verified and never implemented. The lecture's point is
not "use SI". It is that a correct requirement that is written down, flowed down, and then never
verified, is worth nothing. That is exactly the failure our V-model pairing rule exists to stop.

**DC-3 (slide 6).** A three-page request for proposal and a long phone call. Key requirements:
range 1000 miles (1609 km), cruise speed 150 mph (241 km/h, 67 m/s), 20 to 30 passengers, twin
engines, rugged and economical. First flight 17 December 1935. Over 10,000 built.

Five numbers on three pages. For a two-person project this is the more encouraging of the two
slides, and it is the one that supports HYDRO's advice in section 8 below. Note also that
"rugged and economical" would fail NASA's C.4 word check — and the aircraft was still built.

### Slide 9 — where "shall" and "should" sit

"Shall" requirements set the boundaries of the design space and the objective space. "Should"
requirements set goals **once the "shall" requirements are satisfied**. The slide uses a house:
"the house shall sleep between 4 and 6 people" is a hard box; "the house should have a fireplace"
is a preference inside it.

This gives us a use for "should" that we did not have. Our four goals in `NGO.md` are project
goals. A "should" statement is a different thing: an aircraft-level preference that only counts
after every "shall" is met.

### Slide 11 — requirements are not specifications

| Requirements say | Specifications say |
|---|---|
| What the product shall or should do: functions, how well, degree of automation, compatibility | How the system is built: form, materials, overall dimensions, schematics, blueprints, user interface |

Concept Question 3 asks whether the two words differ. The supplemental file for it is the poll
form only; it does not contain the answer. So the lecture's own position on slide 11 is the best
we have: they differ, and requirements come before specifications.

For us the line is clean: `01_requirements/` holds requirements. `03_design/` holds
specifications. A dimension in millimetres in `REQUIREMENTS.md` is a sign something went wrong.

### Slide 19 — the five types, with the lecture's own examples

| Type | Example from the slide |
|---|---|
| Functional | "The TVC shall provide vehicle control about the pitch and yaw axes" |
| Performance | "The TVC shall gimbal the engine a maximum of 9 degrees, +/- 0.1 degree" |
| Constraint | "The TVC shall weigh less than 120 lbs" |
| Interface | "The TVC shall interface with the J-2X per conditions specified in [document], Section 3.4.3" |
| Environmental | "The TVC shall use the vibroacoustic and shock loads defined in [document] in all design, analysis and testing activities" |

The slide's definition of a constraint: **a requirement that cannot be traded off against cost,
schedule or performance.** NASA 4.2.1.2.1 says the same thing in different words — constraints
"typically cannot be changed based on trade-off analyses". The two agree.

The functional example has a form worth copying: **actor – action verb – object acted on.**

### Slide 20 — attributes of an acceptable requirement

Per statement: clear and consistent, correct, feasible, flexible (not stated as how it is to be
satisfied), without ambiguity, singular (one actor-verb-object), verifiable at the level of the
architecture where it is stated.

Per set: absence of redundancy, consistency of terms, completeness (usable as a set of design-to
requirements), absence of conflicts.

The second list is the one we would forget. A set of individually good requirements can still
contradict itself, and nothing in a per-requirement check finds that.

### Slide 23 — margins, and the number this gives us

The slide, in its own words: because of uncertainty in early design, use requirement margins for
mass, power, memory and so on. Margins are reserves that are **not allocated to subsystems** and
are controlled by project managers. Mass growth has been seen on almost all vehicle programmes
and typically ranges from **10 to 60%**, depending on how novel the project is.

Typical guidelines given on the slide:

| Point in the project | Mass margin |
|---|---|
| At SRR | 30% |
| Pre-PDR | 20% |
| Pre-CDR | 10% |
| Pre-IOC | 5% |

**This is the most directly usable number in the whole of Stage 2, because our mass limits are
legal ones.** But the slide does not say how the percentage is measured, and the two obvious
readings give different answers. Both are computed below against the two limits we care about.

Reading A — the estimate plus its margin must stay under the limit, so allowed estimate = limit /
(1 + m). Reading B — the margin is a fraction of the limit itself, so allowed estimate =
limit × (1 − m).

| Stage | Margin | 250 g limit, reading A | 250 g, reading B | 900 g limit, reading A | 900 g, reading B |
|---|---|---|---|---|---|
| SRR | 30% | 192.3 g | 175.0 g | 692.3 g | 630.0 g |
| Pre-PDR | 20% | 208.3 g | 200.0 g | 750.0 g | 720.0 g |
| Pre-CDR | 10% | 227.3 g | 225.0 g | 818.2 g | 810.0 g |
| Pre-IOC | 5% | 238.1 g | 237.5 g | 857.1 g | 855.0 g |

Computed, not quoted. Two warnings go with this table. First, 900 g may not be our limit at all —
C21 says that boundary belongs to a class marking a privately built aircraft cannot carry, and
C18 is still unread. Second, mass growth of 10 to 60% is for professional vehicle programmes.
Two people building a first aircraft from foam and printed parts should expect the top of that
range, not the bottom.

> **Corrected 2026-09-08.** C18 is not unread. Annex Part A was read on 2026-08-14 from the
> Official Journal text, CELEX 32019R0947, and `RULES.md` §C settles it: we fly in subcategory A3.
> So the **900 g columns above describe a limit that does not bind us.** C21 records why — the
> boundary belongs to the C1 class marking, which a privately built aircraft cannot carry — and
> C13 puts our ceiling at 25 kg. The 250 g columns still mean something, because 250 g is the
> registration threshold behind C22. The margin schedule itself, 30% at SRR down to 5%, is not
> affected by any of this.

### Slide 27 — do we need a requirements tool?

The slide's rule: a document, in a word processor or a spreadsheet, "works okay for smaller
projects with dozens or a few hundred requirements", which it puts at about three levels of
decomposition — (7 ± 2)³, that is **125 to 729** requirements. Above roughly 1,000 requirements
you need a relational database, and it names IBM Rational DOORS as the commercial option.

Stage 0 section 6 estimated our decomposition at 3 to 4 levels. So we are inside the range where
a plain document is the right tool. **`REQUIREMENTS.md` as a Markdown file is the correct choice,
and we can stop wondering about it.** This also closes it in the other direction: if our
requirement count ever passes a few hundred, that is a signal we have over-specified, not a
signal to go and find a tool.

### Slide 29 — the worked hierarchy, and a fault in it

The slide numbers requirements R1.0, R1.1, R1.2 … and marks one as a derived requirement, linked
rather than decomposed. Hyperlinks give traceability, one-to-one or many-to-one.

Two of the example statements use "must" instead of "shall", and one of them — "the mass of the
system must be verified using a Mettler-Toledo XYZ Bench Scale" — puts the verification method
and a named instrument inside the requirement text. Both break NASA Appendix C.1 and C.2. We
should copy the numbering scheme and the linking idea from this slide, and not the wording.

### Slides 31 and 32 — allocation, and the warning that applies to us

Allocation is four steps: define the lower-level functions needed to satisfy the requirement,
create an architecture of sub-components to provide those functions, allocate a level of
performance to each lower-level function, and specify the interface requirements between them.
Then **closure**: check that satisfying the whole lower-level set really does guarantee the
higher-level requirement.

Slide 32 carries one line at the bottom: *"Difficult to decompose reqts to lower levels while
staying solution neutral."*

That line is about us. Our configuration is open on purpose. Allocation step two needs an
architecture. So we cannot write subsystem-level requirements in Stage 2 without deciding the
configuration, which is Stage 3. This is not a problem with our plan; it is the reason the plan
has that order. But it does mean Stage 2 produces aircraft-level requirements only, and that has
to be said in `REQUIREMENTS.md` rather than discovered later.

### Slides 42 and 43 — the balloon, and why we checked it

Concept Question 4 asks which of four requirement pairs is infeasible. A balloon must lift 1000 kg
including its own mass, using helium (ρ = 0.2 kg/m³) or hydrogen (ρ = 0.1 kg/m³), in air
(ρ = 1.3 kg/m³).

Lift = (ρ_air − ρ_gas) × V, with V = (4/3)πr³.

| Case | Gas | r | V | Lift | Feasible |
|---|---|---|---|---|---|
| A | He | 6.1 m | 950.8 m³ | 1045.9 kg | yes |
| B | H₂ | 5.9 m | 860.3 m³ | 1032.3 kg | yes |
| C | He | 5.9 m | 860.3 m³ | 946.3 kg | **no** |
| D | H₂ | 6.1 m | 950.8 m³ | 1140.9 kg | yes |

We computed this rather than reading the answer off the slide, and it agrees with the slide's
solution table. The lesson is validation step 4 of section 2 above: **a pair of requirements can
each look reasonable and still be impossible together.** Nothing in the wording of case C is
wrong. Only the physics says no. For us the equivalent pair is a mass limit and a hover time, and
we will not know they conflict until we do the arithmetic.

### Slides 44 and 45 — the common problems

- Writing implementation ("how") instead of requirement ("what"). It forces the design, and it
  makes the requirement look already covered.
- Using incorrect terms: "support", "but not limited to", "etc", "and/or".
- Bad sentence structure or grammar.
- Unverifiable requirements: minimize, maximize, rapid, user-friendly, easy, sufficient, adequate,
  quick.
- Missing requirements. The slide gives a grid of twelve areas that get forgotten: functional,
  performance, interface, environment, facility, transportation, training, personnel, reliability,
  maintainability, operability, safety.
- Over-specifying.

The twelve-area grid is a shorter version of the completeness list in NASA C.4. The short one is
more likely to be used.

### Slides 49 to 51 — the SRR, and what happens after it

SRR is "primarily a human / social peer-review process". Its main goal: vet the requirements as
written, and find any missing, misstated, redundant or otherwise unsatisfactory ones. It happens
early — in Phase A, before preliminary design.

Slide 50 says the top two levels of requirements need to be clearly defined by then: L0 is the
mission requirement and ConOps, L1 the major systems, L2 the major subsystems. Requirements must
be written down, validated, and accessible to everyone. **At this point they go under formal
configuration management.** After that, adding, deleting or modifying a requirement needs
approval.

Slide 51 introduces requirements volatility: the degree to which requirements keep changing
during a project, even after SRR, measured as the percentage added, removed or modified per time
period. Generally undesirable.

For us configuration management is free — the repository already does it. What we do not have is
the approval step. With two people, "approval" means the other person has to see the change
before it lands. That is worth saying out loud, because a quiet edit to a frozen requirement is
exactly the failure the freeze exists to prevent.

### Slides 33 to 41 — isoperformance, read and skipped on purpose

Isoperformance is a method for requirements flow-down. You start with a vector of desired
performance targets, run simulation models to find whether that vector is feasible, and if it is,
generate the set of non-unique design combinations that all reach the same performance. Those
combinations become the sub-system requirements. The lecture demonstrates it on the Nexus
spacecraft concept — a 2.8 m aperture telescope, 752.5 kg, $105.88M — with sensitivity analysis
over 25 parameters and a line-of-sight jitter requirement of 5 µm.

The method needs a validated dynamic model of the whole system before it can say anything. We do
not have one, we have no laboratory to validate one against (C8), and our aerodynamic numbers
will be estimates. Skipped, for the same reason and in the same way as Stakeholder Value Network
analysis in Stage 1: read, understood, and not used.

## 8. HYDRO — the two rows about requirements

Source: HYDRO — Sutherland, Kamiyama, Aoyama, Oizumi, IMDC 2015.

**Table 2, row "Focusing on Requirements".** The NASA best practice is "Mission Success Driven
Requirements & Validation Process".

| Effectiveness in 2014 | Proposed change |
|---|---|
| "Low. Original requirements document was not attainable, read once and not looked at again." | "Set a few attainable requirements at each level of the architecture decomposition and ensure they are verified and validated." |

**Table 5, enabler 3.2, "Clarify, Derive, Prioritize Requirements Early and Often During
Execution".**

| Effectiveness in 2014 | Proposed change |
|---|---|
| "A requirements document was created by KTH students, but it was more of a 'wish list' than a rigorously analyzed and generated document." | "Set a few attainable requirements at each level of the architecture decomposition." |

Two tables, one sentence. The word we should notice is **attainable**. Their document failed
before anyone stopped reading it: it was a list of things they wanted, so no page in it could be
checked against anything. A wish list has no failure mode, which is why it gets abandoned.

One small correction to `REFERENCES.md`, now checked against the paper: the fix reads "at each
level of the **architecture** decomposition". Our reference list drops the word "architecture".
Not a change in meaning, but the quotation should be exact.

We are better placed than they were on two counts and worse on one. Better: we already pair every
requirement with a verification method and a pass/fail criterion, and our MOEs are written to be
failable. Worse: we have no external reader, so nobody outside will notice if our list drifts
into a wish list.

## 9. Where our sources disagree

**Disagreement 1 — the names of the four verification methods.** MIT slide 46 gives examination,
test, demonstration, analysis. NASA, quoted in HYDRO Figure 5 and adopted in Stage 0 section 3,
gives test, analysis, **inspection**, demonstration. Three of the four match; the fourth is the
same idea under two names. We keep NASA's four, because Stage 0 already recorded them and
`REQUIREMENTS.md` will use one vocabulary. This is a naming difference, not a real
disagreement — but if we mix the two words in one document, a reader cannot tell.

**Disagreement 2 — TBD.** NASA 4.1.1.2.3 says an objective may stay TBD until the trade study
happens. NASA Appendix C.3 says the use of TBD in requirements should be minimised, and a best
estimate marked TBR is better. These are consistent, because they are talking about different
documents, but together they set us a real job: our 11 TBD objectives cannot walk into
`REQUIREMENTS.md` unchanged. Each becomes either a number, or a best estimate marked TBR with a
closing date.

**Disagreement 3 — how deep the requirements go before the review.** MIT slide 50 expects L1 and
L2 defined at SRR. NASA 4.2 describes the process as recursive and iterative down to the lowest
level, without demanding all levels at once, and slide 32 admits that decomposing while staying
solution-neutral is difficult. Our configuration is open, so L2 cannot exist yet. We follow NASA's
recursive reading: freeze L1 now, write L2 after the configuration trade, and hold a second,
smaller review then. This is a proposal, and it is item 1 in section 11.

**Disagreement 4 — few, or complete?** HYDRO says set *a few attainable* requirements at each
level. NASA C.4 asks whether any of about twenty requirement areas has been overlooked. Pulled to
its extreme, one gives a short list that misses things and the other gives a long list nobody
reads. Our line, proposed: walk the twelve-area grid from MIT slide 45, write **at most one
requirement per area at each level**, and for any area that does not apply, write one line saying
why instead of leaving it out silently. The record of what we excluded is what stops the short
list from being careless.

---

## What Stage 2 changes for us

**Things we are adopting that we had not written down before:**

1. Every requirement carries a rationale in NASA's four parts: reason and parent, assumptions,
   link to the ConOps scenario, and any design constraint that limited the solution.
2. Requirements are flagged as **KDR** where they have a large effect on cost or schedule. With
   €295 for the first aircraft this is our early-warning field.
3. TBD becomes TBR at the freeze: a best estimate, what closes it, and the date it closes. We keep
   Stage 0's decision to have no owner field — with two people it carries no information — so we
   take NASA's TBR minus the "who".
4. Requirements are aircraft-level only in Stage 2. `REQUIREMENTS.md` says so at the top.
5. The C.4 banned word list is run as a text search over `REQUIREMENTS.md` before the freeze, not
   read by eye.
6. Verification method and pass/fail criterion stay in their own columns, never inside the
   requirement sentence.
7. The requirements review has NASA's six validation questions as its agenda, in order.
8. Two Technical Performance Measures are tracked against the calendar from the freeze onward:
   total mass and money spent. Both already have a home — `MASS_BUDGET.xlsx` and `BOM.xlsx` — and
   both have a hard ceiling.

**Things we are deliberately not adopting:** isoperformance (read, and skipped for the reason in
section 7), a separate MOP list (our pass/fail criteria are the same numbers), a requirements
database or tool (slide 27 says a document is right at our size), and NASA's waiver and
configuration-control machinery from Figure 4.2-2, which assumes an organisation.

**One thing Stage 1 got wrong, and this stage corrects.** Stage 1 recorded that the unread Open
Category subcategory conditions "block nothing in Stage 2 but block flying". That is not right.
the maximum take-off mass and the distance we must keep from people both depend on C18. NASA 4.1.1.2.3 says objectives must be feasible before requirements are written. So the
unread Annex Part A now blocks the requirements freeze, not only the choice of test site. It has
moved from a job we can do later to a job that must be done first.

**Two jobs from earlier stages that Stage 2 now depends on:**

1. Annex Part A of Regulation (EU) 2019/947 — the A1, A2, A3 subcategory conditions. Needs a
   browser. Blocks C18, C21 and therefore the freeze.
2. Table D-1, Table 4.2-1, Table 4.2-2, Figure 4.2-2 and Figure 4.2-3 in the NASA handbook. Also
   needs a browser. Not blocking — we can write a column set of our own and label it as ours —
   but we should see NASA's before the freeze rather than after.

> **Job 1 was already closed when this file was written.** Annex Part A was read on 2026-08-14 from
> the Official Journal text, CELEX 32019R0947. The answer is subcategory A3 — 150 m from
> residential, commercial, industrial and recreational areas — and it is carried in `RULES.md` §C
> and in constraints C18, C19, C20 and C21, all of which now read **Confirmed** in `NGO.md` §6. The
> paragraph and the list above were written on 2026-09-04 and missed it. **Annex Part A does not
> block the requirements freeze.** Job 2 is still open, and still not blocking.

**Still open, and Stage 2 does not close either of them:** configuration and scale. Slide 32
explains why, and it is the same answer as Stage 1: aircraft-level requirements do not need a
configuration, and subsystem-level requirements cannot be written without one.

## What we have to decide before writing requirements

These are open. None of them should be settled quietly while writing `REQUIREMENTS.md`.

| # | Question | Why it matters |
|---|---|---|
| 1 | Do we freeze aircraft level only now, and hold a second review after the configuration trade? | Section 9, disagreement 3. Changes what "freeze" means and how many reviews we hold |
| 2 | Which mass margin reading, A or B, and against which limit? | Section 7, slide 23. Reading A and B differ by 62 g at the 900 g limit. And C18 may move the limit |
| 3 | How many requirements is "a few"? A cap per level, or no cap? | Section 9, disagreement 4. HYDRO's team died of a wish list, not of a short list |
| 4 | What does a logged revision to a frozen requirement look like, in practice? | NASA 4.2.1.2.4 step 5 of the "be prepared to demonstrate" list. We have the rule and not the procedure |
| 5 | Do we use "should" statements at all, or only "shall"? | Slide 9 gives "should" a real meaning. It also gives us a way to smuggle in wants |
| 6 | Which requirement numbering scheme? | Slide 29 uses R1.0 / R1.1. Our objectives use G1-O1 and our constraints C1. Whatever we pick has to survive being renumbered |

### Settled

Answered one at a time, in the chat, with the options and the evidence laid out before each answer.
A question is only written here after we have agreed it.

**1. Two freezes, aircraft level first. Settled 2026-09-08.**

Freeze **L1**, the aircraft level, now — before the configuration trade study. Write **L2**, the
subsystem level, after the trade, review it against the same six validation questions, and freeze it
then.

*Why.* A trade study judged against requirements we can still edit is not a trade study. If a
configuration scores badly, nothing stops us softening the requirement that made it score badly.
Freezing L1 first removes that. And L2 cannot be written yet in any case: allocation needs an
architecture (slide 31, step 2), and a tailsitter, a lift+cruise and a tilt-wing do not have the same
parts. Writing "the tilt mechanism shall…" today would choose the configuration through the wording
of a requirement instead of through the trade.

*The condition that makes this safe.* At freeze 1 we also write down **which L1 requirement numbers
we expect the trade to re-open**. Only the numbers, not new values. That turns a later L1 change from
a surprise into a planned check, and it gives the second review its agenda.

*Rejected.* One freeze after the trade — nothing would be frozen during the largest decision in the
project, which is HYDRO's wish-list failure exactly. Freeze L1 with no second review — the L2 set
would never be checked as a set for conflicts and completeness (slide 20), and slide 31's closure
step would never be asked.

*What breaks if we delete this item.* We drift into the no-second-review option without choosing it:
`REQUIREMENTS.md` gets written, and subsystem requirements get added during design, one at a time,
unreviewed, because no review was ever planned.

*Knock-on.* Question 6 — the numbering scheme has to survive a second level being added underneath.

**2. No mass requirement at L1. Mass is a TPM. Settled 2026-09-08.**

*The question dissolved.* It asked which mass-margin reading to use and against which limit. There is
no binding limit to apply either reading to. **25 kg is our ceiling (C13, law)** and a foam-and-print
V/STOL aircraft will not approach it. **250 g is a registration threshold, not a limit (C22, law)** —
we are above it, the €23 is already budgeted, and crossing it costs nothing more. **900 g was never
ours (C21).** So reading A versus reading B was arithmetic about a ceiling that is not there, and the
62 g gap between them decides nothing. Section 7 of this file keeps the working, with its correction
block.

*What we do instead.* Mass is tracked as a **Technical Performance Measure** from now on — the
estimate plotted against the calendar in `MASS_BUDGET.xlsx`, as already adopted in item 8 of "What
Stage 2 changes for us". No mass figure is written as a requirement at the L1 freeze.

*This is written as a planned gap, not an omission.* `REQUIREMENTS.md` states that aircraft mass is
deliberately unconstrained at L1, and that **a derived mass target is the first thing the
configuration trade study must produce.** So the gap has a closing date and a closing
condition, in the same way a TBR does.

*Why mass still drives everything, even with no legal limit.* Hover thrust must exceed weight. Mass
sets the thrust needed, which sets motor and propeller size, which sets current, which sets battery
size — which is itself mass. The loop closes on itself, and on a hovering aircraft it closes hard.
G1-O2 asks for over 5 minutes with more than half wing-borne, and hovering costs far more power than
cruising, so every gram is paid for out of that 5 minutes. Mass is constrained by physics, not by law,
and the physics cannot be evaluated until configuration and scale are chosen.

*No number is chosen by this decision.* The margin schedule quoted on MIT slide 23 — 30% at SRR down
to 5% — stays in section 7 as a quotation from professional vehicle programmes. It is not adopted, and
it is not applied to anything.

*What breaks if we delete this item.* Mass drifts with nothing watching it, and the first time anyone
asks "how heavy is this allowed to be" is when the aircraft will not hover.

**3. One requirement per named area, not a number cap. Settled 2026-09-08.**

Walk the **twelve areas from MIT slide 45** — functional, performance, interface, environment,
facility, transportation, training, personnel, reliability, maintainability, operability, safety. At
most **one requirement per area**. For every area we skip, **one written line saying why**. A second
requirement in an area is allowed only when covering it in one sentence would force two "shall" verbs
into it, and the reason is written next to it. The same twelve headings are walked again at L2.

*Why areas and not a count.* A count cap is arbitrary and easy to cheat without meaning to: at the
cap, the next requirement gets merged into an existing sentence, which breaks NASA C.1 and C.2 —
one "shall" per statement — and hides a requirement where verification will not find it. The areas
are named in advance, so they cannot be invented to make room, and a merge across two areas is
obvious. The "why not" line for a skipped area is what makes a short list defensible instead of
careless: **HYDRO's list did not fail for being long, it failed because nothing in it could be
checked and nothing recorded what they had decided not to do.**

*This is what settles disagreement 4 in section 9.* HYDRO says "a few". NASA C.4 asks about twenty
areas. Counting areas instead of requirements makes both true at once. The walk produces roughly
**ten to twelve requirements at L1** plus two or three skip lines — a few by HYDRO's standard,
complete by NASA's.

*Three areas the walk found that we would have missed.* **Transportation** — C18 puts the test site
150 m from every residential, commercial, industrial and recreational area, so the aircraft has to
travel out of town; if it does not come apart, span decides the test site as firmly as the law does.
**Training** — C23 buys the licence for €10, and a licence is not skill; neither of us has much RC
experience. **Maintainability** — C4 plans a crash and the rebuild allowance assumes the aircraft can
be rebuilt, which is only true if damaged sections and propulsion units can be replaced.

*Not a tooling question.* Slide 27 puts the ceiling for a plain document at roughly 125 to 729
requirements. At ten to twelve on L1 we are far below it. The cap exists so that the list gets
reread, not so that it fits in a file.

*What breaks if we delete this item.* Either the list grows until nobody rereads it, or it stays short
by accident with no record of what was left out — and we cannot tell those two apart afterwards.

**4. A logged revision is a pull request with six fields, in three tiers. Settled 2026-09-08.**

This closes the gap recorded in section 2: NASA 4.2.1.2.4 asks that the process for managing change
in requirements be established, documented and communicated, and we had the rule without the
procedure.

*The six fields.* Every revision to a frozen requirement records: **(1)** the requirement ID;
**(2)** the old text and the new text, both; **(3)** why now — what we learned since the freeze that
we did not know at it, not "we changed our minds"; **(4)** what else moves — the other requirements,
objectives and ConOps scenarios affected; **(5)** whether the verification method or the pass/fail
criterion changes; **(6)** the date.

**Field 4 is the one that gets skipped and the one that matters most.** A requirement almost never
moves alone, and our own rule already makes every requirement name its parent. Without field 4 the
set stays consistent on the day of the change and quietly stops being consistent a month later.
Field 3 is what makes requirements volatility (slide 51) visible: several revisions in a row reading
"we could not meet it" is a signal about the design, not about the requirement.

*Three tiers, because a process that costs the same for a typo as for a number gets routed around.*
**Editorial** — a typo, or wording that does not change the meaning: no approval, commit straight to
`main`. The C.4 banned-word search will produce a batch of these before the freeze. **Modification** —
the number or the meaning changes: full six-field revision through the mechanism below.
**Addition or deletion** — full revision, plus one extra check that the twelve-area walk in decision 3
still holds, because adding a requirement can put an area over one without anyone noticing.

*The mechanism: a pull request.* Changes to `01_requirements/` after the freeze go on a branch and
open a pull request carrying the six fields, and the other person approves before it merges.

*Why this and not an issue plus a direct commit.* The issue route fits what we already do and it never
stalls, but nothing enforces it — a commit with no issue is accepted and nobody finds out unless they
read the log. The pull request is the only option where **the tool enforces the rule instead of our
discipline**, and Stage 1 recorded exactly why we need that: we chose reading 1, we are the only
customer, and there is no external brake on requirements creep. This is the one place we can buy a
brake for free. The cost is that a modification stalls if one of us is away; the editorial tier takes
most of that away, because most changes are editorial.

*Rejected.* A revision table inside `REQUIREMENTS.md` — it duplicates what git already stores, makes
the file long, and contradicts our rule that rationale lives in the issue and not in the baseline file.

*Two conditions before we rely on this, neither yet done.*

1. **Check the current GitHub docs** for how to require a review on `main`, and whether a repository
   owner can bypass it. Unchecked. The standing rule in `REFERENCES.md` forbids quoting GitHub docs
   from memory, and that rule applies here.
2. **Agree now what happens if one of us is unreachable for more than a few days.** A rule written
   today is worth more than one invented in March under deadline pressure.

*What breaks if we delete this item.* A quiet edit to a frozen requirement — the exact failure the
freeze exists to prevent, and the one nothing else in the project would catch.

**5. "Shall" only. No "should", no "will". Settled 2026-09-08.**

`REQUIREMENTS.md` contains exactly one verb. Preferences and tie-breakers go to `NGO.md` §5 as
design rules. A line saying this goes at the top of `REQUIREMENTS.md`, because the reason is not
obvious to a reader six months later, and because it explains why the file is shorter than expected.

*The argument that decides it.* NASA Appendix D: **only "shall" requirements go in the verification
matrix.** So a "should" is never verified — no test, no pass mark, no failure mode. Put that next to
our own rule 3: *before writing any item, answer what breaks if we delete it; if the answer is
"nothing", it does not go in.* **A "should" breaks nothing when deleted, by construction.** Every
"should" we could write fails rule 3 on the day it is written. And it is HYDRO's failure in
miniature: their document was "more of a 'wish list' than a rigorously analyzed and generated
document", and a "should" is a wish with formatting.

*The second cost.* With both verbs in one file, a reader must check the verb on every line to know
what is binding. We write in a second language, under time pressure, and reread months later. That
is a reliable way to eventually read a "should" as a "shall".

*What we give up, and where it goes instead.* When two configurations both pass every "shall",
something has to break the tie, and a tie-breaker written in advance is engineering while one
invented on the day is preference. That job is real — and `NGO.md` §5 already exists to do it: *"How
we decide when we have a choice. Not measures, and not constraints."* It is a better home than a
"should" for two reasons: it sits outside `REQUIREMENTS.md` so it can never be misread as binding,
and a design rule can carry its reasoning while a bare "should" cannot.

*"Will" is banned there too.* C.1 gives "will" to facts and declarations of purpose. "The aircraft
will be flown by one of the two of us" is a fact and belongs in the rationale or the ConOps, not as a
numbered line. With one verb in the file, two checks become one text search each: every numbered item
contains "shall", and no numbered item contains anything else — the same trick as the C.4 banned-word
search in item 5 of "What Stage 2 changes for us".

*What breaks if we delete this item.* Unverifiable wishes end up sitting next to verifiable
requirements, and the document stops being checkable as a whole.

**6. Flat IDs — R1, R2, R3. Settled 2026-09-08.**

Requirements are numbered flat, exactly like constraints. The ID encodes nothing. The parent is a
field in the rationale, where NASA 4.2.1.2.3 already requires it.

*The evidence is our own repository, and it is close to a controlled experiment.* **Constraints
C1–C23** are flat and encode nothing; our rule says they are not reused and not renumbered. The
2026-09-08 rewrite deleted a goal, five objectives and two assumptions, and rewrote the need — **not
one constraint number moved.** **Objectives O1.x and O2.x** encoded the goal grouping. The
performance goal was deleted, every O2.x died with it, every survivor was renumbered, and a mapping
table had to be written so that older issues, commits and the ConOps could still be read.

*The rule that follows.* **The more an ID encodes, the more ways it can become wrong — and our own
rule says IDs are never renumbered, so a wrong ID is permanent.** The right question is not which
scheme reads best but **which part of a requirement is least likely to change.** A goal can change;
we deleted one. An area can change; a requirement filed under operability may be reclassified as
safety. A number that means nothing cannot change at all.

*Rejected.* A level prefix, L1-01 / L2-01 — the level is stable, but L1 and L2 will live in separate
files, so it is redundant. An area prefix, R-SAF-01 — attractive because it makes the one-per-area cap
of decision 3 visible in the ID, but a later reclassification leaves the ID permanently wrong. A goal
prefix, R-G1-01 — this is the scheme that just failed for objectives, and it is worse for
requirements, because many of ours descend from constraints or the ConOps rather than from a goal:
transportation from C18, environment from ConOps §4.0, safety from the off-nominal scenarios. Filing
those under G1 or G2 would be false.

*Old objective IDs are not being mapped; the citations are being removed instead.* Settled the same
day. The four places that cited retired flat IDs now describe the objective instead, or name the
current ID where it is unambiguous. **This was the safer choice, because the old IDs are genuinely
ambiguous:** O1.5 named the maximum hover height objective when it was deleted on 2026-08-09, and
later named "abandon a transition and return to hover". The ID was reused before the
never-reuse rule existed, so a mapping table would have had to record one ID meaning two things.

*What breaks if we delete this item.* Nothing forces a scheme, so one gets chosen while writing
`REQUIREMENTS.md` — which is exactly the "settled quietly" failure this section exists to prevent.

**A safety note that belongs in the requirement set, not in the design.** The completeness lists
in both NASA C.4 and MIT slide 45 name safety as its own area. Ours will come from the
off-nominal scenarios already in the ConOps: propeller clearance during any bench thrust test,
LiPo charging and storage, holding or tethering the aircraft on a first flight, and arming
discipline. These are requirements with pass/fail criteria, written now, and not advice added to
the build notes later.
