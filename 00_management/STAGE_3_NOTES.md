# Stage 3 — Architecture and configuration selection: reading notes

What we took from the Stage 3 sources listed in `REFERENCES.md`. One section per source, then
what it changes about how we run JBV-01. Read this before we open `02_concept/`.

**Written 2026-09-08.** Sections 1 to 6 and 8 are what the sources say and what follows from them;
they contain no decisions of ours. Section 7 is different — it records the simulation-tool research
and the choice made from it the same day. The ten questions the reading raised were settled the same
day too, in the chat, and are recorded under **Settled** at the end.

**One thing to know before reading.** Stage 3 has two halves and our reference list treats them as
one. NASA 4.3 is about **functions** — what the aircraft must do, written down before any hardware
is named. NASA 4.4 is about **the design solution** — generating alternatives, trading them, and
choosing one. The configuration trade study everyone in this project keeps talking about sits in
the second half. The first half has to happen before it, and we have never written it down.

---

## 1. NASA 4.3 — Logical decomposition: the "what", before any "how"

Source: NASA SEH Rev 2, Section 4.3, read in full from the nasa.gov page on 2026-09-08.

NASA's own one-line purpose: *"Logical decomposition is the process for creating the detailed
functional requirements that enable NASA programs and projects to meet the stakeholder
expectations."* And: *"This process identifies the 'what' that should be achieved by the system at
each level."*

The section says the process is used for two things:

1. improve understanding of the technical requirements and the relationships among them —
   functional, performance, behavioural, temporal;
2. decompose the parent requirements into logical decomposition models and **derived technical
   requirements**, as input to the Design Solution Definition Process (4.4).

**The two inputs (4.3.1.1).**

| NASA input | Where ours would be | State on 2026-09-08 |
|---|---|---|
| Technical Requirements — *"A validated set of requirements … approved by the customer and other stakeholders"* | `01_requirements/REQUIREMENTS.md` | **Does not exist.** The L1 freeze settled in Stage 2 has not happened |
| Technical Measures — MOEs, MOPs and TPMs | `NGO.md` §4 for the two MOEs; mass and money as TPMs | MOEs exist. TPMs were adopted in Stage 2 but neither `MASS_BUDGET.xlsx` nor `BOM.xlsx` exists yet |

**So Stage 3 is blocked, and by our own decision.** Stage 2 settled that L1 freezes before the
configuration trade study. NASA 4.3 says the same thing from the other end: its first input is a
validated requirement set. Neither half of Stage 3 can start on a file that is not written.

### 4.3.1.2.1 — Define one or more logical decomposition models

*"The key first step in the Logical Decomposition Process is establishing the system architecture
model."* The system architecture activity *"defines the underlying structure and relationships of
hardware, software, humans-in-the-loop, support personnel, communications, operations, etc."*

The definition worth keeping:

> *"The system architecture can be seen as the strategic organization of the functional elements of
> the system, laid out to enable the roles, relationships, dependencies, and interfaces between
> elements to be clearly defined and understood. It is strategic in its focus on the overarching
> structure of the system and how its elements fit together to contribute to the whole, instead of
> on the particular workings of the elements themselves."*

And the sentence that says an architecture is not a hardware list:

> *"It enables the elements to be developed separately from each other while ensuring that they work
> together effectively to achieve the top-level (or parent) requirements."*

**How many concepts.** *"the system architect should develop at least one, but preferably multiple,
concept architectures capable of achieving program objectives."* Each one has to specify three
things: the functional elements (what the pieces do), their relationships to each other (interface
definition), and **the ConOps** — how the parts operate as a system from start of operations to end
of mission.

That third item matters to us. **A configuration is not a candidate until its ConOps is written.**
"Tailsitter" is not an architecture. "Tailsitter, with these functional elements, these interfaces,
and this version of [DRM-0300] to [DRM-0500]" is.

**How the architecture is developed.** *"Much like the other elements of functional decomposition,
the development of a good system-level architecture is a creative, recursive, collaborative, and
iterative process that combines an excellent understanding of the project's end objectives and
constraints with an equally good knowledge of various potential technical means of delivering the
end products."*

Read that last clause honestly. It asks for good knowledge of the available technical means. We have
no V/STOL background at all. **The second half of that sentence is the thing we are missing, and no
process fixes it.** It is HYDRO's Knowledge Growth Curve, arriving at the stage where it does the
most damage.

**How long multiple concepts survive.** *"Cost and schedule constraints will ultimately limit how
long a program or project can maintain multiple architectural concepts."* NASA baselines a single
architecture during Phase A, and notes that *"the later in the development process that changes
occur, the more expensive they become."*

**The tools NASA names** for developing an architecture: modelling and simulation tools, functional
analysis tools, architecture frameworks, and trade studies. Two of those four we do not have and one
we have not run — `NGO.md` §8 still lists "which simulation tools we use" as open, and nobody here
has run SITL.

### 4.3.1.2.2 — Allocate requirements, resolve conflicts, baseline

*"Functional analysis is the primary method used in system architecture development and functional
requirement decomposition. It is the systematic process of identifying, describing, and relating
the functions a system should perform to fulfill its goals and objectives."* And: *"It is usually
based on the ConOps for the system of interest."*

The three steps, verbatim:

1. *"Translate top-level requirements into functions that should be performed to accomplish the
   requirements."*
2. *"Decompose and allocate the functions to lower levels of the product breakdown structure."*
3. *"Identify and describe functional and subsystem interfaces."*

**The part we would have skipped.** *"Each function identified is described in terms of inputs,
outputs, failure modes, consequence of failure, and interface requirements."* Failure modes are
named at the function level, before any hardware exists. Our ConOps already has three off-nominal
scenarios — [DRM-0700] link loss, [DRM-0800] early reserve, [DRM-0900] a lift unit fails — and this
says every function gets that treatment, not only the three we thought of.

**Alternative decompositions exist, and the outcome depends on who does it.** NASA's own example:
there may be several ways to communicate with the crew — RF, laser, Internet. *"Therefore, the
outcome is highly dependent on the creativity, skills, and experience of the engineers doing the
analysis."*

**When to stop.** *"the systems engineer should keep an open mind and a willingness to go back and
change previously established architecture and system requirements … Only at that point should the
system architecture and requirements be baselined"* — that point being when the system is fully
defined with all requirements *"understood and known to be viable, verifiable, and internally
consistent."*

### 4.3.1.3 — Outputs

Three of them. The middle one is the one Stage 2 was waiting for:

- **Logical decomposition models** — the relationship of requirements and functions and their
  behaviours, including the system architecture models and *"the basis for the partitioning of
  requirements into lower levels to the point that design work can be accomplished."*
- **Derived technical requirements** — *"requirements that arise from the definitions of the
  selected architecture that were not explicitly stated in the baselined requirements that served
  as an input to this process."*
- **Logical decomposition work products.**

**"Derived technical requirement" is the name for the thing we already promised to produce.** Stage 2
settled that `REQUIREMENTS.md` will say aircraft mass is deliberately unconstrained at L1, and that
*a derived mass target is the first thing the configuration trade study must produce*. That target is
a derived technical requirement in NASA's sense: it does not come from the need, the goals or the
law. It comes from the architecture we pick. Our L2 set is the derived set.

### 4.3.2 — Guidance we cannot reach

4.3.2 points at the *NASA Expanded Guidance for Systems Engineering* for Product Breakdown Structures
and Functional Analysis Techniques. That is a different document from the handbook, hosted on
nen.nasa.gov. **We have not opened it and it is not in `REFERENCES.md`.** Everything we know about
how to actually perform a functional decomposition therefore comes from MIT Session 4 and from the
three steps quoted above.

---

## 2. NASA 4.4 — Design solution definition: where the configuration trade actually lives

Source: NASA SEH Rev 2, Section 4.4, read in full from the nasa.gov page on 2026-09-08.

The opening sentence describes the whole of our Stage 3 second half: the process translates the
high-level requirements and the outputs of 4.3 into alternative solutions, *"These alternative
solutions are then analyzed through detailed trade studies that result in the selection of a
preferred alternative. This preferred alternative is then fully defined into a final design solution
that satisfies the technical requirements."*

Ten activities. Here is what each one costs us.

### 4.4.1.2.1 Define alternative design solutions

*"The realization of a system over its life cycle involves a succession of decisions among
alternative courses of action. If the alternatives are precisely defined and thoroughly understood
to be well differentiated in the cost-effectiveness space, then the systems engineer can make
choices among them with confidence."*

The "create concepts" loop produces three things together — *"a straw man architecture/design, the
associated ConOps, and the derived requirements"* — under cost and schedule constraints, and:
*"These three products should be consistent with each other and will require iterations and design
decisions to achieve this consistency."*

**Three products, not one.** Each configuration we carry into the trade needs its own straw-man
architecture, its own ConOps, and its own derived requirements. That is the real cost of carrying a
candidate, and it is what will decide how many we can afford to carry.

The sentence that binds hardest on us:

> *"Therefore, system architecture issues need to be resolved early so that the system can be
> modeled with sufficient realism to do reliable trade studies."*

And the reason:

> *"As the system is realized, its particulars become clearer—but also harder to change."*

### 4.4.1.2.2 Create alternative design concepts

*"Ideally, as wide a range of plausible alternatives as is consistent with the design organization's
charter should be defined."*

Then the warning that is written for a team like ours, and which we cannot fully obey:

> *"When the bottom-up process is operating, a problem for the systems engineer is that the designers
> tend to become fond of the designs they create, so they lose their objectivity; the systems
> engineer should stay an 'outsider' so that there is more objectivity."*

**We are two people, and we are the designer and the systems engineer at once. There is no
outsider.** This is the same hole Stage 1 found — no external customer, no external brake — arriving
at the stage where it costs the most. It has to be answered with a mechanism, not with good
intentions, in the same way the pull-request rule answered requirements creep in Stage 2.

On technology maturity, NASA is blunt:

> *"There is a tendency on the part of technology developers and project management to overestimate
> the maturity and applicability of a technology that is required to implement a design. This is
> especially true of 'heritage' equipment."*

And the definition of technology development that catches us:

> *"a frequently overlooked area is that associated with the modification of 'heritage' systems
> incorporated into different architectures and operating in different environments from the ones
> for which they were designed. If the required modifications and/or operating environments fall
> outside the realm of experience, then these too should be considered technology development."*

That is exactly what a tiltrotor or tilt-wing is for us: proven hobby components — motors, ESCs,
servos, an ArduPilot flight controller — assembled into an architecture and an operating regime
none of them was sold for. **Under NASA's own definition that is technology development, not
integration.** Buying proven parts does not make it proven.

Two more from this activity:

- *"If requirements are defined without fully understanding the resources required to accomplish
  needed technology developments, then the program/project is at risk."*
- *"Given that resources will always be limited, it is necessary to pursue only the most promising
  technologies that are required to enable a given concept."*

And the reason not to settle early:

> *"The reason for avoiding a premature focus on a single design is to permit discovery of the truly
> best design."*

**The interface check, as a habit.** NASA says part of the job is making sure the concepts being
compared take interfaces into account, with two characteristic questions: *"Did you include the
cabling?"* and *"Did you consider how the maintainers can repair the system?"* The second is
Stage 2's maintainability area, asked at the concept stage instead of at the rebuild.

**Describe concepts as classes, not points.** *"When possible, each design concept should be
described in terms of controllable design parameters so that each represents as wide a class of
designs as is reasonable."* So "lift+cruise" should enter the trade as a family with named
parameters, not as one drawing. Otherwise we compare our best tailsitter sketch against our worst
lift+cruise sketch and call the result a trade study.

### 4.4.1.2.3 Analyse each alternative — the trade study

*"The purpose of the trade study process is to ensure that the system architecture, intended
operations (i.e., the ConOps) and design decisions move toward the best solution that can be
achieved with the available resources. The basic steps in that process are:*

1. *Devise some alternative means to meet the functional requirements. In the early phases of the
   project life cycle, this means focusing on system architectures; in later phases, emphasis is
   given to system designs.*
2. *Evaluate these alternatives in terms of the MOPs and system life cycle cost.*
3. *Rank the alternatives according to appropriate selection criteria.*
4. *Drop less promising alternatives and proceed to the next level of resolution, if needed."*

Four points around those steps that we should not lose:

- *"The trade study process should be done openly and inclusively. While quantitative techniques and
  rules are used, subjectivity also plays a significant role."* NASA does not pretend the numbers do
  the choosing.
- *"Trade study assumptions, models, and results should be documented as part of the project
  archives."*
- *"The ability to perform these studies is enhanced by the development of system models that relate
  the design parameters to those assessments, but it does not depend upon them."* **We can run a
  trade study without a validated model.** Given C9, this is the single most useful sentence in 4.4
  for us.
- The output is bounds, not values: *"The end result is the determination of bounds on the relative
  cost-effectiveness of the design alternatives … (Only bounds, rather than final values, are
  possible because determination of the final details of the design is intentionally deferred.)"*

NASA also says what the system model should cover — the roles of crew, operators, maintainers,
logistics, hardware and software; the critical technologies; the whole life cycle from fabrication
to disposal — and that *"Cost is always a limiting factor. However, other criteria, such as time to
develop and certify a unit, risk, and reliability, also are critical."*

### 4.4.1.2.4 Select the best alternative

The team selects *"taking into account subjective factors that the team was unable to quantify, such
as robustness"*, and the Decision Analysis Process of Section 6.8 *"should be used"*. See section 3
below — 6.8 is not in our reference list.

On reducing everything to one number:

> *"When it is possible, it is usually well worth the trouble to develop a mathematical expression,
> called an 'objective function,' that expresses the values of combinations of possible outcomes as
> a single measure of cost-effectiveness … even if both cost and effectiveness should be described
> by more than one measure."*

And then, three paragraphs later, the qualification:

> *"Rarely (if ever) is it possible to produce a combined quantitative measure that relates all of
> the important factors, even if it is expressed as a vector with several components. Even when that
> can be done, it is essential that the underlying actors and relationships be thoroughly revealed
> to and understood by the systems engineer. The systems engineer should weigh the importance of the
> unquantifiable factors along with the quantitative data."*

The rule underneath both:

> *"An essential feature of the systems engineering process is that trade studies are performed
> before decisions are made."*

Figure 4.4-3 plots cost against effectiveness with probability clouds for three concepts A, B and C —
*"the risks are relatively high for design concept A. There is little risk in either effectiveness or
cost for concept B, while the risk of an expensive failure is high for concept C."* **The figure
itself is an image on the page and we have not read it.** The caption text quoted here is machine
readable; the plot is not.

### 4.4.1.2.5 Increase the resolution of the design

*"One might ask, 'When do we stop refining the design?' The answer is that the design effort proceeds
to a depth that is sufficient to meet several needs: the design should penetrate sufficiently to
allow analytical validation of the design to the requirements and ConOps; it should also have
sufficient depth to support cost and operations modeling and to convince a review team of a feasible
design with performance, cost, and risk margins."*

Three sufficiency tests. **We have no review team**, so the third one has to be replaced by something
or dropped openly. The first two we can apply.

### 4.4.1.2.6 Fully describe the design solution

The scope should suit the life cycle phase, and *"Depending on these factors, the form of the design
solution definition could be simply a simulation model or a paper study report."* At our size and
phase, a written study is a legitimate output. NASA says so.

### 4.4.1.2.7 Verify the design solution

By **peer review**, and the verification shows that the design solution definition:

- *"Is realizable within the constraints imposed on the technical effort;"*
- *"Has specified requirements that are stated in acceptable statements and have bidirectional
  traceability with the technical requirements and stakeholder expectations; and"*
- *"Has decisions and assumptions made in forming the solution consistent with its set of technical
  requirements and identified system product and service constraints."*

Note the word **bidirectional**. Not just "every derived requirement has a parent", but also "every
parent requirement has children". That is a check we can run mechanically on two files.

NASA is explicit that this is not the same as verifying the built article: *"This design solution
verification is in contrast to the verification of the end product … That verification occurs in a
later life cycle phase."*

### 4.4.1.2.8 Validate the design solution

*"A simplified validation asks the questions: Does the system work as expected? How does the system
respond to failures, faults, and anomalies? Is the system affordable? If the answer to any of these
questions is no, then changes to the design or stakeholder expectations will be required, and the
process is started over again."*

Three questions, and the third one is a hard ceiling for us at C3. Question two is where [DRM-0900]
lives: a configuration whose answer to "one lift unit stops" is "it falls" has failed this question
at the concept stage, not at the flight test.

### 4.4.1.2.9 Identify enabling products

> *"Enabling products are the life cycle support products and services (e.g., production, test,
> deployment, training, maintenance, and disposal) that facilitate the progression and use of the
> operational end product through its life cycle."*

> *"When a suitable enabling product does not already exist, the project that is responsible for the
> end product can also be responsible for creating and using the enabling product."*

**This is the name for a list we have been keeping in pieces.** The thrust stand (C8, AS2), the
tether for [DRM-0200], the charger and LiPo bag, the laser cutter at the makerspace (AS6), the test
site (AS1), the transmitter, the pilot licence and the operator number are all enabling products.
NASA asks for their **need dates on the project schedule, with slack**, and says *"it is important to
identify enabling products and secure the commitments for them as early in the design phase as
possible."*

We have no schedule. This is the activity that says we need one, and it names what goes on it first.

### 4.4.1.2.10 Baseline the design solution

> *"Baselining a particular design solution enables the technical team to focus on one design out of
> all the alternative design concepts. This is a critical point in the design process. It puts a
> stake in the ground and gets everyone on the design team focused on the same concept."*

And the counterweight:

> *"While baselining a design is beneficial to the design process, there is a danger if it is
> exercised too early in the Design Solution Definition Process. The early exploration of alternative
> designs should be free and open to a wide range of ideas, concepts, and implementations. Baselining
> too early takes the inventive nature out of the concept exploration. Therefore, baselining should be
> one of the last steps in the Design Solution Definition Process."*

### 4.4.1.3 Outputs — nine, and what they mean at our size

NASA lists nine outputs plus one optional. Most assume an organisation. Mapped honestly:

| NASA output | What it would be for JBV-01 |
|---|---|
| System Specification | The L2 requirement set, `REQUIREMENTS.md` second level |
| System External Interface Specifications | Airframe to ground: transmitter link, telemetry, charger, transport. ConOps §3.3 already sketches this |
| End-Product Specifications — *"detailed, exact statements of design particulars, such as statements prescribing materials, dimensions, and quality of work"* | Our build drawings and print settings, in `03_design/` |
| End-Product Interface Specifications | Motor-to-ESC, ESC-to-controller, wing-to-fuselage joints, battery mount |
| Initial Subsystem Specifications | Only if needed |
| Enabling Product Requirements | The thrust stand, tether and test site list above |
| Product Verification Plan | `05_verification/TEST_LOG.md`, already planned from Stage 0 |
| Product Validation Plan | The [DRM-0500] flight and MOE-1 and MOE-2 |
| Logistics and Operate-to Procedures | Transport, LiPo storage and charging, pre-flight checks |
| *Optional:* Human Systems Integration Plan | Two people. C23 and the training area from Stage 2 |

**We are not producing nine documents.** But every row above is a real thing that has to exist
somewhere, and the table is a better completeness check than our memory.

---

## 3. NASA 6.8 — Decision Analysis: the section 4.4 sends us to, and which our reference list misses

Source: NASA SEH Rev 2, Section 6.8, read in full from the nasa.gov page on 2026-09-08.
**It is not listed under Stage 3 in `REFERENCES.md`.** 4.4.1.2.4 says the Decision Analysis Process
"should be used" to pick the best alternative, and 4.4.1.2.3 sends the reader to 6.8 for the trade
study process itself. We would have run the configuration trade without the section that describes
how to run it.

**When formal decision analysis is worth the effort.** NASA gives four conditions and says its
application *"is warranted only when some of the following conditions are met"*:

| Condition | NASA's words | Us |
|---|---|---|
| Complexity | *"The actual ramifications of alternatives are difficult to understand without detailed analysis"* | Yes. None of us can predict a tailsitter's behaviour from the drawing |
| Uncertainty | *"Uncertainty in key inputs creates substantial uncertainty in the ranking of alternatives"* | Yes, and worse than usual — C9 means every input is an estimate |
| Multiple Attributes | *"Greater numbers of attributes cause a greater need for formal analysis"* | Yes |
| Diversity of Stakeholders | *"Extra attention is warranted … when the set of stakeholders reflects a diversity of values"* | **No.** Two of us, same values |

NASA adds: *"Satisfaction of all of these conditions is not a requirement for initiating decision
analysis."* Three of four is more than enough.

**Criteria (6.8.1.2.1).** Identify the types of criteria, the acceptable range and scale of each, and
*"The rank of each criterion by its importance."* Then:

> *"Criteria should be objective and measurable. Criteria should also permit differentiating among
> options or alternatives. Some criteria may not be meaningful to a decision; however, they should be
> documented as having been considered."*

And the sentence that turns our constraint list into a filter:

> *"Criteria may be mandatory (i.e., 'shall have') or enhancing. An option that does not meet
> mandatory criteria should be disregarded."*

**That is how C10 to C23 enter the trade.** They are not scored, they are gates. A configuration that
cannot meet a mandatory criterion is dropped, not given a low mark that a high mark elsewhere can
cancel out. A criterion that "does not differentiate" — one every candidate passes equally — is
documented as considered and then left out of the scoring.

**Alternatives (6.8.1.2.2).** *"All possible options should be considered. This can get unwieldy if a
large number of variations is possible. A 'trade tree' … is an excellent way to prune the set of
variations before extensive analysis is undertaken, and to convey to other stakeholders the basis
for that pruning."* Also: options should be built on the **primary** factors; secondary factors can
be evaluated but *"should not, in general, define separate alternatives."*

And a line we should copy:

> *"It is a best practice to document a decision matrix for a major decision even if only one
> alternative is determined to be viable."*

**Evaluation and normalisation (6.8.1.2.4).** Different criteria have different units, so
*"normalization can be used to establish a common base."* It can be informal (low / medium / high),
on a scale (NASA's example is 1-3-9), or done with a tool. The condition:

> *"No matter how normalization is done, the most important thing to remember is to have operational
> definitions of the scale. An operational definition is a repeatable, measurable number. For
> example, 'high' could mean 'a probability of 67 percent and above.'"*

**An operational definition for every level of every scale.** Without it, scoring is opinion with a
number written next to it — and with two people who both want the same aircraft to win, that is the
whole risk.

**Robustness of the ranking (6.8.1.2.5).** The recommendation comes back with *"an assessment of the
robustness of the ranking (i.e., whether the uncertainties are such that reducing them could
credibly change the ranking of the alternatives)."* If alternatives do not differ much, or if
reducing uncertainty could flip them, all the close ones go forward rather than one.

There is also a rule for overriding the top score: if a lower-scoring option is recommended, say why,
and *"If this occurs, the decision criteria should be reevaluated, not only the weights, but the
basic definitions of what is being measured for each alternative."* In other words, overriding the
score is allowed, but it is evidence the criteria were wrong and they get fixed.

**The decision report (6.8.1.3.1).** Ten contents, and this is the outline of the document that will
live in `02_concept/`:

1. mission and system context for the decision
2. decision needed and intended outcomes
3. decision criteria
4. identified alternative solutions
5. decision evaluation methods and tools employed
6. assumptions, uncertainties, and sensitivities in the evaluations and recommendations
7. results of all alternative evaluations
8. alternative recommendations
9. final decision made with rationale
10. lessons learned

**The methods 6.8.2 names**, all of them in the Expanded Guidance we do not have: trade studies,
cost-benefit analysis, influence diagrams, decision trees, analytic hierarchy process, Borda
counting, and utility analysis. MIT Session 5 covers two of these — utility analysis and, in
substance, the trade study — so the MIT deck partly fills the gap left by the missing document.

---

## 4. MIT Session 4 — System Architecture and Concept Generation

Source: MIT OCW 16.842, Fall 2015, de Weck. PDF read 2026-09-08, **48 pages**.

> **How the pages are numbered in this file.** We cite **PDF page numbers**, not the footer numbers.
> The two are the same for most of the deck, but they drift apart around pages 11 to 17, where the
> footer runs one behind. Three separate reads of the PDF were compared; two disagreed by one page on
> the Morphological Matrix slide. Where a page number here matters, the **slide title** is given with
> it, and the title is the thing to search for.

### The frame — pages 5 to 7

Page 5 puts the three lecture questions in order: *"Why are we doing the project?"* → stakeholder
analysis (our Stage 1). *"What must we achieve?"* → requirements definition (our Stage 2). *"How could
we do it?"* → **this stage**. With the note: *"Oftentimes there are many different ways."*

Page 6 gives the three themes the lecture is built on — **ambiguity, creativity, complexity** — with
ambiguity reduced by requirements, creativity focused into concepts, and complexity managed by
decomposition.

Page 7, the definition:

> *"The embodiment of concept, and the allocation of physical/informational function (process) to
> elements of form (objects) and definition of structural interfaces among the objects"*

Form, function, and concept as the mapping between them.

### Concept — pages 12 to 15

The informal definition: a system vision that maps form to function, embodies **working principles**,
and is expressed in solution-specific vocabulary. The lecture's example is *"refrigerator = insulated
box containing mechanically chilled air"*.

The formal definition, page 15:

> *"The specialization of function and mapping to its physical embodiment of form"*

and, in the same slide, *"The specification of the list of design variables, which when specified will
define the design."*

Page 14 notes that new concepts need a few words or a short phrase, established ones one or two
words, and that **once the concept is specified the parts list is largely determined**.

**Our concept sentence does not exist yet.** "V/STOL aircraft" is a category, not a concept. The
equivalent of the refrigerator sentence for a lift+cruise would be something like "a fixed-wing
aircraft carrying a separate set of upward-facing rotors used only below flying speed" — one sentence,
naming the working principle. Writing that sentence for each candidate is cheap and it is the first
thing Session 4 asks for.

### Design vs. architecture — page 24

The distinction that settles what our trade study is actually choosing:

- **Architecture** selects the concept, the decomposition, and the form-to-function mapping, and
  thereby **establishes the vector of design variables**.
- **Design** selects the values of those variables. Optimisation belongs here.

**So the configuration trade is not a sizing exercise, and must not turn into one.** Wingspan, motor
count, battery cells and mass are values — they belong to design, after the architecture is chosen.
The trade picks which variables exist at all. This also explains why Stage 2's decision to hold L2
until after the trade was right: you cannot allocate requirements to parts that the architecture has
not created yet.

### Concept generation versus selection — page 27

> Concept generation: *"Find systems that do the right thing"*
> Concept selection: *"Find systems that do the right thing AND do it well, i.e. deliver value, AND
> comply with current and future regulations and standards"*

Two different jobs, and Session 5 is the second one. Regulations are named in the selection half —
for us that is `RULES.md` and constraints C12 to C23, and NASA 6.8 says they are mandatory criteria,
so they are gates and not scores.

### The architecture summary — page 28

Architecture requires form and function considered together through the concept; concepts elaborate
into architectures with form-function and structural complexity; and architecture "goodness" is
**multiobjective** — performance, resource utilisation, cost, operability, capacity. Not one number.

### The NASA block — pages 30 to 34

Pages 30 to 34 restate the Logical Decomposition process covered in section 1 above. Page 30 quotes
a NASA requirement — numbered 17 in the deck — that Center Directors *"shall establish and maintain a
process … for logical decomposition of the validated technical requirements"*, and page 33 shows
examples of decomposition models (timing diagrams, state diagrams). Page 34, *"Logical Decomposition Best Practice Process Flow
Diagram"*, is a figure and **we have not read it**.

**Timing diagrams and state diagrams are worth noticing.** Our aircraft has modes — hover,
transition, wing-borne — and the transition is a state change under time pressure. ConOps §3.4
already lists modes of operation. A state diagram is the natural way to write down what commands are
legal in each mode and what happens on a failure, and it is a Stage 3 work product, not a Stage 4
one.

### Concept generation methods — pages 36 to 47

The lecture gives three families: **group dynamics** (brainstorming), **models** (study a creative
person — the Da Vinci material on pages 41 and 42), and **structured processes** (mind maps,
morphological matrix, architecture enumeration).

**Brainstorming (pages 38 and 39).** Defined as *"Creativity technique designed to find new ideas as a
TEAM"*, to lower creativity barriers and increase idea production by mutual stimulation. The rules:
announce the topic days ahead as the only agenda item; ideally **5 to 10 participants (7±2)** with
diverse backgrounds; take turns with no order constraint; extend and combine others' ideas; a
facilitator takes visible notes **without attaching names**; the *"principle of delayed judgement"* —
no criticism and no particular praise during the session; aim for quantity and diversity; 30 to 60
minutes; post-processing is a separate activity. Attributed to A.F. Osborn, *Applied Imagination*
(1957).

**We are two people.** The method's own group size is 7±2 and its whole mechanism is mutual
stimulation between different backgrounds. With two people who have read the same sources, the
mechanism is mostly absent. **This is a real limit, and pretending otherwise would be the first
dishonest line in the project.** Page 40's list of 17 "creativity killer sentences" is still useful
between two people — *"This will never work!"*, *"There's no time for this!"*, *"Everyone does it this
way!"* — because those are the sentences that end a two-person discussion.

**Morphological matrix (page 43).** The simplest structured method, and the one that survives a team
of two:

- list the *m* key decisions or factors as rows;
- for each row, determine the number of possible alternatives *n<sub>i</sub>*;
- enumerate all combinations, **N = Π n<sub>i</sub>** over i = 1 to m.

The lecture's worked example is three factors with three alternatives each, giving 27 architectures,
and a concept written as a path such as "A2-B1-C3". The lecture's own warning: *"For many factors, may
generate many infeasible architectures. How to prevent that?"*

**This is the method that answers a real question for us.** Our five named configurations —
tiltrotor, tailsitter, lift+cruise, tilt-wing, ducted fan (C10) — are not a set of options along one
axis. They are points that mix several independent decisions: what provides lift in hover, what
provides thrust in cruise, whether anything rotates, and what rotates if so. A morphological matrix
makes those decisions the rows, which both generates layouts we have not named and shows why the five
names are not comparable as they stand.

**Rule-based architecture enumeration (page 44)** is the answer to the infeasible-combination problem:
express creativity, experience and analysis as **components plus rules** — rules constraining which
components can coexist and which connections can exist — and let the enumeration obey them.

**Abstraction layers (pages 45 to 47).** Defined as the *"Formal Division of design into different
layers of fidelity and subsystem aggregation"*, with two benefits: an intellectually manageable number
of components and connections, and lower computational cost per level. The worked example is an
aircraft engine — layer 0 is "turboprop", layer 1 opens it into intake, propeller, compressors, burner,
turbines, nozzle — and it cites Raymer, *Aircraft Design: A Conceptual Approach*. Page 47 shows a
spreadsheet enumeration tool producing 240 designs.

**Abstraction layers are how we keep the matrix from exploding.** Layer 0 asks how lift and thrust are
produced. Only after a layer-0 architecture is chosen does layer 1 ask about motor count, tilt
mechanism or duct.

### Lecture summary — page 48

*"System Architecture is the most abstract, but also the most influential activity in Systems
Engineering."* Concept = mapping function to form, taken down about two levels of abstraction and not
to every detail. NASA's approach centres on logical decomposition. Concept generation is a creative
activity with three families of method — group dynamics, models, structured processes.

---

## 5. MIT Session 5 — Concept Selection and Tradespace Exploration

Source: MIT OCW 16.842, Fall 2015, de Weck. PDF read 2026-09-08, **39 pages**.

> **A naming difference worth recording.** The OCW lecture-notes page calls this session *"Concept
> Selection and Tradespace Exploration"*. The PDF's own resource title is *"Tradespace Exploration and
> Concept Selection"*. Same file. `REFERENCES.md` uses the OCW page's wording.

> **Six pages we could not read.** Pages 12 to 17 — *Architectural Space*, *Filtered Concepts*,
> *Concept Screening Matrix (Pugh)*, *What is Pugh Matrix for?*, *Challenges*, *Role of the
> Facilitator* — are images with no machine-readable text, and several are marked in the deck as
> excluded from the Creative Commons licence. **We have the titles and nothing else.** Two of those
> six (*Challenges*, *Role of the Facilitator*) are exactly the practical material a two-person team
> would want. Reading them needs the PDF opened by eye. Not blocking; worth doing before the trade.

### The pipeline — page 4

The lecture's own picture of where we are: Need → **System Architecture** (concept synthesis →
concept screening → concept selection) → **System Design** → an "optimal" design, with the review
gates SRR, PDR and CDR marked along it, and the whole thing moving from qualitative to quantitative
as it goes left to right.

**Screening and selection are two steps, not one.** Screening cuts the field cheaply and
qualitatively; selection compares what survives, with more work per candidate. Our reference list
speaks of a single "configuration trade study", which quietly merges them.

### Decision analysis — pages 5 and 6

A decision has four components: alternatives, criteria, value judgments, and the decision maker's
preferences. Then page 6 lists the issues in concept selection as plain questions:

- multiple criteria — how to deal with them?
- what if there are ties between alternatives?
- group versus individual decision making?
- uncertainty
- right criteria?
- right valuation?
- **are the best alternatives represented?**

The last one is the one that cannot be fixed later. A trade study can only choose among what was
generated, and it will look just as rigorous whether or not the best layout was ever on the list.

### The Pugh matrix — page 8

Five steps:

1. Choose or develop the criteria for comparison, based on the system requirements and goals.
2. Select the alternatives to be compared — *"All concepts should be compared at the same level of
   abstraction and in similar language."*
3. Generate scores: pick one concept as the **datum**, and mark every other as better (+), same (S or
   0), or worse (−) against it, criterion by criterion.
4. Compute the total: count the (+), the (−) and the (0). The overall total is (+) minus (−). *"The
   totals should not be treated as absolute in the decision making process but as guidance only."*
5. Variations exist — for example a seven-level scale from +3 to −3.

Step 2 is the one we would fail. **The five configuration names in C10 are not at the same level of
abstraction**: "ducted fan" is a propulsor choice that a tiltrotor or a lift+cruise could also use.
Session 4's morphological matrix is what fixes that before Session 5's method is applied.

### The critique of the Pugh matrix — page 18

The lecture attacks its own method:

- *"Ranking of alternatives can depend on the choice of datum."*
- Weighting: some criteria matter more than others; a weighted version exists **but the weights have
  to be agreed**.
- Multi-attribute utility analysis and the Pugh method **may give a different rank order**.
- *"The most important criteria may be intangible and missing from the list."*
- And the lecturer's stated personal opinion: the method is useful and simple, *"It stimulates
  discussion about the important criteria, set of alternatives"*, and it *"Should not be used as the
  ONLY means of concept filtering and selection."*

**Datum dependence is a live risk for us.** If the datum is the layout one of us already prefers, the
result carries that preference. The cheap defence is to run the matrix more than once with different
datums and see whether the order holds — which is the same idea as NASA 6.8's robustness check.

### Utility analysis — pages 19 to 22

Utility maps each criterion onto a dimensionless [0,1] scale, and the partial utilities are combined
into one overall number. Page 20 gives the shapes a single-attribute utility curve can take —
monotonic increasing, monotonic decreasing, concave, convex, and non-monotonic — under two published
classifications (Cook: smaller-is-better, larger-is-better, nominal-is-better, range-is-better;
Messac: classes 1S to 4S). Page 21 gives the multi-attribute formula with scaling factors k and the
six MAUA steps, which include developing and administering an **interview questionnaire** to
establish the weights.

The cautions on pages 21 and 22 matter more to us than the formula:

- *"'Utility' is a surrogate for 'value', but while value has units of [$], utility is unitless."*
- *"Physical meaning of aggregate objective is lost (no units)."*
- *"Utility function can vary drastically depending on decision maker."*
- *"Requires formulation of preferences apriori"* — the weights are fixed **before** the results are
  seen.

That last one is the honest use of the method for us, and it is the same trick as writing a
demonstration's pass/fail sentence before the flight (`NGO.md` §3). Weights chosen after seeing which
layout scores well are not weights.

The worked example on pages 23 to 27 is a space tug, with utility built from ΔV, response time and
payload capability at weights 0.6, 0.1 and 0.3, **cost deliberately kept separate in millions of
dollars rather than folded into utility**, and the tradespace plotted as cost against utility. The
observation on page 27: the design families *"Hit a wall of either physics (can't change!) or utility
(can)."*

**Keeping cost out of the utility number is the part to copy.** C3 is €800 and it is a hard ceiling,
not a preference. Cost belongs on its own axis, where a candidate that exceeds it is out rather than
merely marked down.

### Non-dominance and the Pareto front — pages 28 to 36

Pareto's own statement of the optimum, quoted on page 29: *"The optimum allocation of the resources of
a society is not attained so long as it is possible to make at least one individual better off in his
own estimation while keeping others as well off as before in their own estimation."*

The working definition, page 30: a point is efficient *"if it is not possible to move feasibly from it
to increase an objective without decreasing at least one of the others."* Page 31 gives weak and
strong dominance formally: J₁ dominates J₂ weakly iff J₁ᵢ ≥ J₂ᵢ for all i and J₁ᵢ > J₂ᵢ for at least
one i.

Pages 32 to 35 work an aircraft example — eight designs scored on range, cost per km, passengers and
speed — and give a mechanical procedure: compare designs pairwise, score each criterion, and *"In
order to be dominated a solution must have a 'score' of 0 in pairwise comparison."* The results go
into a **domination matrix** where *"Non-dominated solutions have a zero in the column S!"*

Page 36 separates two ideas that are easy to confuse: *"All pareto optimal points are non-dominated.
Not all non-dominated points are pareto-optimal"*, and *"It's easier to show dominatedness than
non-dominatedness."*

**Why this is usable by us even without models.** Dominance needs no weights and no utility function.
If one configuration is worse than another on every criterion we care about, it is out, and nobody has
to agree on what matters most first. It is the cheapest honest filter available, and it is exactly
what NASA 6.8's trade tree is for — pruning before the expensive analysis.

### PDR — page 37

The lecture lists what a Preliminary Design Review has to do, citing the 2007 NASA handbook, p. 177:

- explain what concept and system architecture was chosen;
- explain **why** it was chosen — and approve it as the design baseline;
- **compare it against the rejected alternatives**;
- show quantitative analysis giving confidence that the requirements stated at SRR, and derived since,
  can be met;
- describe the results of any risk-reduction experiments or prototypes;
- preview the detailed design phase leading to CDR.

**This is the shape of our configuration decision document**, and it lines up with NASA 6.8's ten-item
report almost line for line. Point 5 is the one to notice: risk-reduction experiments are expected to
have already happened by this point. For us that is G2-O5 — both transitions proved on the tether or
bench before free flight — and HYDRO's *"de-risk new technologies with minimum viable
implementations"* below.

### Summary — page 38

The lecture's own sequencing, by phase:

- **Conceptual design** — use the Pugh matrix, *"When detailed mathematical models not yet available,
  but qualitative understanding exists."*
- **Preliminary design** — use utility analysis, *"Especially for non-commercial systems where NPV may
  not be easy to calculate"*, and non-dominance: *"Generate many designs for each concept, apply
  Pareto filter."*

**We are in the first bullet.** No validated model, qualitative understanding only, C9 saying every
number is an estimate. The deck says a Pugh matrix is the right tool at exactly this point, and that
it should not be the only one — which is what the dominance filter is for.

---

## 6. HYDRO — one enabler, and it is about the powertrain

Source: Sutherland, Kamiyama, Aoyama, Oizumi, IMDC 2015. **Table 5, *"Enablers for Lean Principle 3:
Flow"***, row 3.3. Columns: the enabler, "Effectiveness in 2014", "Proposed changes".

> **Which section the table sits under is not confirmed.** Two reads of the PDF gave two different
> section headings — *"Reviewing and Improving Activity on the Development-V"* and *"A Selection of Lean
> Enablers Viewed as Important to the Improvement of Solar Boat Development"*. The table number, title,
> columns and row 3.3 text were the same in both. Cite the table, not the section, until someone opens
> the PDF by eye.

> **3.3 Front Load Architectural Design and Implementation**
> *Effectiveness in 2014:* "Structural architecture inherited from KTH was sound. Powertrain
> architecture was not set early. Validation of design was patchy."
> *Proposed changes:* "Define the architecture, validate it numerically and by small experiment.
> De-risk new technologies with minimum viable implementations."

Three things in one row.

**1. The half they inherited worked; the half they had to decide did not.** Their structure came from
a previous team and was sound. The powertrain — the part they owned — was never fixed early. The
lesson is not "inherit more". It is that **the architecture nobody is forced to decide is the one that
stays undecided**, and it is usually the one the project is actually about.

Ours is worse than theirs in the same place. Our powertrain is not one decision but several tied
together: what produces lift in hover, what produces thrust in cruise, whether they are the same
devices, and what happens to them during the transition. That is the transition, and the transition is
the project.

**2. "Validate it numerically and by small experiment."** Two methods, and we have both. Numerically:
the propulsion arithmetic, and SITL, which has a QuadPlane model checked 2026-08-14 — with the two
limits already recorded in `NGO.md`, that it validates no aerodynamics of ours and that the frame it
names is lift+cruise. By small experiment: the thrust stand (C8, AS2), a bench mixer test, a tethered
lift [DRM-0200]. **Neither of these is a design review. They are cheap physical checks of the
architecture, done during Stage 3, not after it.**

**3. "De-risk new technologies with minimum viable implementations."** The smallest thing that proves
the risky part works. For a tilt mechanism that is one printed tilt assembly on a bench with a servo
and a motor, run through its full travel under load, long before an airframe exists. Our own fallback
rule (`NGO.md` §5.1) asks two questions at the moment of choosing; this adds a third habit — build the
smallest version of the risky part early enough that the fallback date still means something.

**One more from the paper.** *"The lower level red loop represents the integration
of a gearbox which was not included in the original design but was required to obtain sufficient thrust
from the selected motor."* A part they had not planned for, forced in late because the propulsion
numbers did not work. That is what an unvalidated powertrain architecture costs, in one sentence.

**Row 3.2 is the requirements row we already used in Stage 2** — the wish-list finding. Rows 3.2 and 3.3
sit next to each other for a reason: a wish list at the top and an unfixed architecture below it are the
same failure at two levels.

---

## 7. Simulation tools — what exists, and what we chose

Researched 2026-09-08, to close the `NGO.md` §8 item "which simulation tools we use". Sources are in
`REFERENCES.md`.

### The transition can be simulated. Two routes exist, and neither was in our reference list

**Route 1 — Gazebo, free.** The ArduPilot Gazebo plugin ships only an Iris quadcopter and a Zephyr
wing, which is why the documentation page looks unpromising. The VTOL models live in a separate
repository, `ArduPilot/SITL_Models`. Its Gazebo folder holds `alti_transition_quad` (a lift+cruise
VTOL), `bicopter` and `bicopter_with_ardupilot` (ArduPilot's BiCopter tilt type), `skycat_tvbs` — TVBS
is Thrust Vectored Belly Sitter, the tailsitter variant the ArduPilot tailsitter page describes —
plus `swan_k1_hwing` and `skywalker_x8_quad`. Costs nothing. ArduPilot supports *"Gazebo Garden and
Gazebo Harmonic which are available for Ubuntu 20.04 (Focal) and 22.04 (Jammy) and macOS Big Sur (11),
Monterey (12), and Ventura (13)"*, and Gazebo's own install page says *"Platforms supported at
best-effort include arm architectures, Windows and macOS."* On our machines that means WSL2.

**Route 2 — RealFlight, paid.** *"This simulator only runs on Windows and requires RealFlight version
8 or version 9."* Its released QuadPlane models are `Alti_Transition_QuadPlane`,
**`Convergence_Tilt_Tri_QuadPlane`** (a tilt-tricopter), `Griffin`, `Skywalker_X8_QuadPlane`, a
**`Tailsitters`** folder and `Titan_Cobra_VTOL`. These are quality-gated: the folder's README requires
that *"The model has been verified by a third party as meeting these requirements and flying well."*

### What we chose, and why

**Built-in ArduPilot SITL, XFLR5 and AVL. An external flight simulator is deferred until after the
configuration trade.**

*Why deferring the external simulator is safe now, and would not have been yesterday.* The fallback
rule (`NGO.md` §5.1) asks, at the moment of choosing, whether a proven off-the-shelf fallback exists
and whether we can afford it inside C3. That question is now answered for every layout except the
tilt-wing, and both its price and its operating-system cost are known. **Knowing that a fallback
exists is what the rule asks for. Installing it is not.**

*Why both aerodynamic tools and not one.* XFLR5 and AVL are both free and both run natively on
Windows. Choosing them instead of Gazebo spends the learning budget on analysis rather than on an
operating system — no WSL2, no Linux. XFLR5 embeds XFoil and adds lifting-line, vortex-lattice and
panel methods with a GUI; AVL adds stability derivatives and **eigenmode analysis**, which is the
closest thing we have to an analytical statement about G2-O3's return-to-trim criterion.

### The limits, recorded

1. **No tool here models the aerodynamics of a transition.** AVL states its own assumption — a
   *"rigid-body, quasi-steady aero model"* on horseshoe vortices — and a vortex-lattice method is not
   valid at the angles a tailsitter passes through or at a part-tilted rotor condition. XFLR5 rests on
   the same class of method plus XFoil, and is aimed at aeroplanes in ordinary flight. **These two
   tools analyse the cruise half of the flight and nothing else.**
2. **So transition risk gets control-logic evidence and no aerodynamic evidence.** Built-in SITL flies
   the mode logic, the mixer and the failsafes, and that is real. It says nothing about our airflow.
   Combined with decision 7 — experiments only where a gate is at stake — the heaviest scored
   criterion in the trade will be scored from control-logic simulation, published practice and
   reasoning. **Written down here so that it is a known condition of the result and not a discovery.**
3. **C9 is untouched.** Every figure from any of these is an estimate. An external VTOL model
   simulates a *different* aircraft that resembles the layout, not ours.
4. **The tilt-wing has no simulation model anywhere we found** — not in the built-in frames, not in
   Gazebo, not in RealFlight. `quadplane-cl84` is named after a tilt-wing aircraft but is mapped in
   the source to the tilt-tricopter model with a binary tilt servo.
5. **XFLR5's maintenance status is unresolved.** Version 6.62 with files updated 2026-06-30, but the
   SourceForge project also carries an "Abandoned" status label. The two disagree. Not blocking —
   the released version works or it does not — but do not describe it as actively maintained.

### What still has to happen before this item closes

`NGO.md` §8 asks for each tool to be installed and run once, with a note of what it is good for,
because *"A tool we have not run is not a capability."* That is unchanged. Three throwaway cases:
one SITL flight, one XFLR5 aerofoil or wing run, one AVL case.

---

## 8. Where our sources disagree

**1. How many concepts to carry, and for how long.** NASA 4.3 wants *"at least one, but preferably
multiple"* and then says cost and schedule limit how long multiple can be kept. MIT's morphological
matrix generates dozens on purpose. NASA 6.8 says prune early with a trade tree, before extensive
analysis. MIT Session 5 splits it into screening then selection. **They are not really in conflict —
they describe a funnel — but our reference list describes one "trade study", which hides the funnel.**
The open question is how wide the mouth is and where the cuts happen.

**2. Whether to reduce everything to one number.** NASA 4.4 says an objective function is *"usually
well worth the trouble"* when possible, then says a combined measure is *"Rarely (if ever)"* achievable
and the engineer must weigh unquantifiable factors as well. MIT Session 5 says the Pugh total is
*"guidance only"* and that the method must not be the only filter, and puts utility analysis in a later
phase than the one we are in. **Reading them together: produce numbers, do not let the numbers decide,
and write down what the numbers could not capture.**

**3. Weighting.** NASA 6.8 asks for *"The rank of each criterion by its importance."* MIT's basic Pugh
matrix is unweighted and the deck warns that weights have to be agreed and that utility and Pugh can
rank differently. **Whether we weight at all is a decision we have to make, not one the sources make
for us.**

**4. Who stays objective.** NASA 4.4 says the systems engineer should stay an *"outsider"* because
designers grow fond of their designs. MIT Session 5 assumes a facilitator and a group. NASA 6.8 lists
*"Diversity of Stakeholders"* as a reason for formal analysis. **All three assume more people than we
have.** This is the third stage in a row to find the same hole: Stage 1 found no external customer,
Stage 2 bought a brake with the pull-request rule, and Stage 3 needs one for the architecture choice.

**5. Baseline early or baseline late.** NASA 4.4.1.2.10 says baselining too early *"takes the inventive
nature out of the concept exploration"* and should be *"one of the last steps"*. NASA 4.4.1.2.1 says
*"system architecture issues need to be resolved early so that the system can be modeled with
sufficient realism to do reliable trade studies."* Both are in the same section, pulling opposite ways.
The resolution is that they talk about different things — the architecture is settled early, the
detailed design solution is baselined late — but the wording invites us to pick whichever suits us on
the day, and our schedule (C2) will make late feel expensive.

**6. Group methods against a team of two.** Brainstorming wants 7±2 people with diverse backgrounds.
We are two, with the same reading and the same coursework. **We should say plainly which methods we are
using because they fit us, and which we are skipping because the group they assume does not exist** —
in the same way Stage 1 read and skipped the Stakeholder Value Network and Stage 2 read and skipped
isoperformance.

---

## What Stage 3 changes for us

**Things we should adopt that we had not written down before:**

1. **Stage 3 has two halves, and the first one is functional.** Before any configuration is compared,
   the functions get written down — from the ConOps, per NASA 4.3 — with each function described by
   its inputs, outputs, **failure modes, consequence of failure**, and interfaces.
2. **A candidate configuration is not a name.** It is a concept sentence, a straw-man architecture, its
   own ConOps, and its own derived requirements. Anything less is not comparable with anything else.
3. **Configurations are generated with a morphological matrix, not listed from memory.** The five names
   in C10 are not at one level of abstraction, and Pugh's step 2 requires that they are.
4. **Abstraction layers keep the matrix from exploding.** Layer 0 decides how lift and thrust are
   produced; layer 1 opens the chosen one.
5. **Constraints are gates, not scores** (NASA 6.8: an option failing a mandatory criterion *"should be
   disregarded"*). C12 to C23 and C3 filter candidates; they never trade against a good score elsewhere.
6. **Every scoring scale gets an operational definition before scoring starts**, and any weights are
   fixed before results are seen.
7. **Dominance first, scoring second.** A candidate worse on every criterion than another is dropped
   with no weights agreed and no argument had.
8. **The Pugh matrix is run more than once, with a different datum each time**, and we report whether
   the order held. This is our substitute for the outsider NASA says we need.
9. **The trade study document follows NASA 6.8's ten-item report**, which is also MIT's PDR list. It
   records the alternatives we dropped and why, not only the one we kept.
10. **The architecture is validated numerically and by small experiment during Stage 3**, per HYDRO 3.3
    — thrust stand, bench mixer, tether — not after the choice is made.
11. **Enabling products get named and dated.** The thrust stand, tether, charger, laser cutter, test
    site, licence and operator number are a list with need dates, not a set of assumptions scattered
    through `NGO.md`.
12. **A "heritage parts" claim is not a maturity claim.** Proven hobby components in an architecture and
    an environment they were not sold for is technology development by NASA's own definition, and the
    fallback rule's first question has to be answered against the *architecture*, not the part.

**Things we should probably not adopt, and should say so:** the full multi-attribute utility machinery
with interview questionnaires (MIT puts it in a later phase than ours and it needs a stakeholder group
we do not have); a formal PDR meeting with a review board (there is no board — but the PDR **content**
list stays); NASA's configuration-control machinery around baselining; and brainstorming as the
lecture defines it, for the group-size reason above — the killer-sentence list is worth keeping anyway.

**What Stage 3 depends on that is not ready.** Every one of these is already written down elsewhere;
this is the first time they appear as a blocking set:

1. **`REQUIREMENTS.md` L1 does not exist.** NASA 4.3's first input. Stage 3 cannot start.
2. **Which simulation tools we use** — `NGO.md` §8 says "before Stage 3", and it is still open. NASA 4.3
   names modelling and simulation as an architecture tool; HYDRO 3.3 asks for numerical validation.
3. **Whether SITL simulates a tiltrotor or a tailsitter** — `NGO.md` §8 says "before the configuration
   trade". It feeds the fallback rule, and today only lift+cruise has a confirmed simulation fallback.
4. **The two ArduPilot pages listed for Stage 3 in `REFERENCES.md`** — "Tilt Rotor Planes" and
   "Tailsitter Planes" — are still marked *not yet read*.
5. **The makerspace visit and the sheet-material price** (AS6, AS7). Both feed what a configuration
   costs to build.

**Two corrections to `REFERENCES.md` that this stage found:**

1. **NASA Section 6.8 "Decision Analysis" is missing from the Stage 3 list.** Section 4.4 sends the
   reader to it twice, and it contains the trade study process, the mandatory-versus-enhancing criteria
   rule, the normalisation rule, and the ten-item decision report. It has now been read in full; it
   belongs in the table.
2. **The Stage 3 row for MIT Session 5 uses the OCW page's title**, which differs from the PDF's own
   title. Worth a note in the table so nobody thinks there are two decks.

**One unread item, recorded so it is not forgotten:** pages 12 to 17 of MIT Session 5 are images. Two of
them — *Challenges* and *Role of the Facilitator* — are about running a concept-selection session, which
is the part of Session 5 closest to what we will actually do. Not blocking.

---

## What we have to decide before the configuration trade study

**All ten were settled on 2026-09-08.** They are kept here as the agenda that produced the decisions
below. None of them was settled quietly while writing `02_concept/`, which is what this section
existed to prevent.

| # | Question | Why it matters |
|---|---|---|
| 1 | Do we write the functional decomposition (NASA 4.3) as its own document before generating concepts, or fold it into the trade study? | 4.3's outputs are 4.4's inputs. Folding them together is how "what it must do" quietly becomes "what our favourite layout does" |
| 2 | What are the rows of the morphological matrix, and at which abstraction layer? | Session 4, page 43 and page 45. This decides what gets generated, and a layout that is never generated can never be chosen |
| 3 | How many candidates survive screening into selection, and what is the cut made on? | Session 5, page 4; NASA 6.8's trade tree. Carrying a candidate costs three products (4.4.1.2.1), so this is a schedule decision as much as a method one |
| 4 | Which criteria, and which of them are mandatory gates rather than scores? | NASA 6.8.1.2.1. Constraints are gates; the open question is what else is |
| 5 | Do we weight the criteria, and if so how are the weights agreed and recorded before scoring? | Disagreement 3 above. Weights chosen after seeing scores are not weights |
| 6 | What replaces the "outsider" NASA asks for — repeated datums, a written pre-commitment, an outside reader, or something else? | Disagreement 4. Third stage in a row to hit this. The Stage 2 answer was a mechanism, not a promise |
| 7 | Which small experiments de-risk the architecture, and by when? | HYDRO 3.3, and MIT PDR point 5. G2-O5 already demands tether or bench proof; this asks what happens *before* that |
| 8 | Does the trade study produce the derived mass target Stage 2 promised, and what else is derived with it? | NASA 4.3 outputs; Stage 2 settled decision 2. Mass will not be the only derived requirement, and the others should be named in advance |
| 9 | What is the enabling-product list, and what are the need dates? | 4.4.1.2.9. We have no schedule; this is the activity that forces one |
| 10 | Is the trade study document one file in `02_concept/`, or a study plus a separate decision record? | NASA 6.8's report list and MIT's PDR list overlap but are not identical. Whichever we pick has to survive being reopened if a candidate comes back |

### Settled

Answered one at a time, in the chat, with the options and the evidence laid out before each answer.
A question is only written here after we have agreed. Same rule as Stage 2.

**1. The functions live in their own file, written in two passes, with a change log. Settled
2026-09-08.**

`02_concept/FUNCTIONS.md`. **Pass 1** is written from the ConOps alone, before any configuration is
named, and frozen. **Pass 2** runs after concept generation: changes are allowed, and every change
records what changed, why, and **which candidate exposed it**.

*Why the functions get their own file.* NASA 4.3's outputs are NASA 4.4's inputs. A file boundary is
visible; a section heading inside a larger file is not. And the function list is the axis set of the
morphological matrix — get the functions wrong and the matrix generates the wrong candidates, which
no amount of careful scoring afterwards can repair. MIT Session 5, page 6 asks the one question a
trade study cannot answer about itself: *"are the best alternatives represented?"*

*Why a V/STOL project cannot skip this the way an ordinary aeroplane could.* On a normal aircraft,
function and form match one to one — the wing lifts, the propeller pulls, the tail steadies. On ours
they do not. Something must produce lift at zero airspeed; something must produce lift with airspeed;
something must produce forward thrust; something must produce control moments while the control
surfaces are still too slow to work. **Whether those are the same devices or different devices is the
configuration choice.** So the functions are not preliminary paperwork. They are the decision,
written in a form that does not yet name an answer.

*Why two passes and not one.* NASA 4.3 asks for *"an equally good knowledge of various potential
technical means of delivering the end products."* We do not have it. A list frozen today would freeze
our gaps with it. Pass 2 admits that we will learn during concept generation. The log is what stops
the learning from being silent.

*What the log buys beyond honesty.* If pass 2 adds several functions and most of them were exposed by
one candidate, that is a signal: either that candidate is doing work the others are not, or we
understood it better because one of us preferred it. Either way it becomes visible instead of
invisible.

*Rejected.* **One file for functions and trade together** — the order collapses without anyone
deciding it: the function list gets written from the candidate list, and the finished document looks
identical either way, so nothing catches it. **A single frozen pass** — the strongest protection
against bias, but it pretends we already know enough, and it would make every later correction look
like a failure instead of like learning.

*What breaks if we delete this item.* We drift into the folded option by default, and the trade
study's functions section gets written after the candidate list, from the candidate list.

*This is not blocked by the L1 freeze.* NASA 4.3's formal input is the frozen requirement set, which
does not exist. But 4.3 also says functional analysis *"is usually based on the ConOps for the system
of interest"*, and our ConOps exists — modes in §3.4, capabilities in §3.5, nine DRM scenarios in
§6.0. **Pass 1 can be drafted now and checked against L1 when L1 is frozen.**

*Knock-on.* Q2 — the morphological matrix rows are drawn from this file. Q7 — a small experiment
de-risks a function, not a part. Q8 — derived requirements trace back to functions. Q6 — pass 1 is
the only bias defence available to us that acts *before* candidates exist, so it carries weight in
that answer.

**2. Rows are the independent decisions. One matrix, enumerated in one pass. Settled 2026-09-08.**

*Rows.* The matrix rows are the **genuinely free decisions** distilled from `FUNCTIONS.md`, not one
row per function. Every row records **which functions it answers**, and the reasoning for the row and
for its option list is written beside it.

*Why not one row per function.* A morphological matrix multiplies its rows — N = Π nᵢ — and that
product only means something if the rows are independent decisions. Ours are not. "Produce lift at
zero airspeed", "produce forward thrust in wing-borne flight" and "change between the two" are one
decision seen from three sides: saying *the same propellers do both, and they rotate* answers all
three at once. One row per function multiplies out combinations that cannot exist, which is MIT's own
warning on page 43: *"For many factors, may generate many infeasible architectures."*

*The cost we accept, and the guard on it.* Distilling functions into decisions is judgement, and
judgement is where a preferred layout gets in. A row whose option list quietly omits an option makes
every candidate using that option impossible to generate, and nothing downstream can recover it. Two
guards: each row cites the functions it answers, so the mapping is checkable in both directions the
way NASA 4.4.1.2.7 asks; and each row's option list is written with its reasoning, so an omission is
a visible claim rather than a silent gap.

*One matrix.* One table, in one file, holding every decision — family-level and detail-level
together.

*Rejected: two matrices, one per abstraction layer.* The two-layer version keeps the count small, but
it can eliminate a family before its details have been seen, and a detail choice can be exactly what
makes a family work. One matrix removes that failure instead of managing it with a safeguard rule.

*One pass, and what it makes load-bearing.* All rows are enumerated together, the coexistence rules
are applied, and the whole set is screened at once, so nothing is eliminated on a partial picture.
Two things stop being optional:

1. **Rule-based enumeration**, MIT page 44. Rules state which options can and cannot coexist. Each
   rule is a claim about what is impossible, written down, and therefore checkable.
2. **A script.** MIT's own worked enumeration tool on page 47 handled 240 designs. An illustrative row
   set worked through in the chat came out several times larger than that, so enumeration and the
   first cut are done in code, not by eye.

*Where the work moved.* One pass makes screening the heavy step. Q3 now carries the whole cut that
two layers would have made for us.

*The rows cannot be written yet.* They come from `FUNCTIONS.md` pass 1, which does not exist. What is
settled here is the rule for making them — agreed **before** pass 1 is written, so that pass 1 is not
shaped to fit a matrix we had already imagined.

*What breaks if we delete this item.* The matrix gets built from the five names in C10, which are not
at one level of abstraction: **"ducted fan" is a propulsor type**, and a tiltrotor and a lift+cruise
could both use one. MIT's Pugh step 2 requires candidates *"compared at the same level of abstraction
and in similar language"*, and that check would fail with no way to repair it afterwards.

*Knock-on.* Q3 — screening now does the entire cut. Q4 — coexistence rules and mandatory constraints
are different things and must not be mixed: a rule says a combination **cannot exist**, a gate says a
candidate **is not allowed**. Q7 — small experiments attach to rows, because a row is a decision and a
decision is what needs de-risking.

**3. Three filters at three moments. Criteria from the twelve-area walk, each with a source. Cost is
a gate and its own axis. Settled 2026-09-08.**

*The three filters, kept apart.*

| Filter | Says | Applied when |
|---|---|---|
| Coexistence rule | "this **combination** cannot exist" | enumeration |
| Gate — mandatory criterion | "this **candidate** is not allowed" | screening |
| Score — enhancing criterion | "this candidate is better or worse" | selection |

NASA 6.8.1.2.1: *"Criteria may be mandatory (i.e., 'shall have') or enhancing. An option that does not
meet mandatory criteria should be disregarded."* **Disregarded, not marked down. A gate cannot be
outscored.**

*The fallback rule is none of the three.* `NGO.md` §5.1 acts at the moment of choosing the winner, not
at screening. §6 already says so in its own words: the simulation situation is *"an input to the
configuration trade, not a decision"*. As a screening gate it would delete every layout except
lift+cruise today, on the strength of one ArduPilot page we have not read.

*Where the criteria come from.* Walk the **twelve areas** adopted in Stage 2 decision 3 — functional,
performance, interface, environment, facility, transportation, training, personnel, reliability,
maintainability, operability, safety. For each area, write one criterion **or** one line saying it does
not differentiate. Every surviving criterion **names its source** in `NGO.md`, `RULES.md` or
`CONOPS.md`. A criterion with no source is a finding: either it is not real, or our baseline has a gap.

*Why both halves and not one.* The walk alone reuses a method built for writing requirements, and a
requirement is not a criterion. The sources alone can only find what we have already written, and MIT
Session 5, page 18 warns that *"The most important criteria may be intangible and missing from the
list."* Together, the walk finds what our files missed and the source citation stops us inventing a
criterion that happens to suit a layout one of us likes.

*The differentiation test, and what it removes.* NASA 6.8: *"Criteria should also permit differentiating
among options or alternatives. Some criteria may not be meaningful to a decision; however, they should
be documented as having been considered."* Applied to our constraints:

- **Documented and set aside** — C12, C13, C15, C16, C17, C20, C22, C23, and C18 as a distance. Every
  candidate meets them equally, so scoring them adds nothing.
- **Gates** — C3, the money ceiling, and C2, whether it can be built inside the academic year.
- **Scored** — C18 through transport (the site is out of town, so span and whether the airframe splits
  matter), C8 through what we can verify without a laboratory, C4 through how rebuildable it is, and
  C19 weakly, because a faster candidate pushes uninvolved people further back and makes a legal site
  harder to find (AS1).
- **Not criteria at all** — C10 defines the candidate set; C11 applies to every candidate.

*The heaviest criterion is not a constraint.* `NGO.md` §5.2: *"Transition risk is project risk, and the
configuration trade study weights it as such."*

*Cost.* Above C3's ceiling a candidate is **disregarded, not marked down**. Below it, cost is plotted on
its **own axis in euros** and never folded into a combined score. This is what MIT's space tug example
does on pages 24 to 27 — cost kept in money on its own axis, utility separate.

*Why cost is not just another scored criterion.* C3 is a hard ceiling, so above it nothing else matters
and no score elsewhere may hide it. And our cost estimates at architecture level will be rough: a rough
figure on its own axis still reads as a range, while the same figure inside a weighted total becomes
invisible.

*Rejected.* Cost as one scored criterion among others — easier to total, but it lets a strong score
elsewhere hide an unaffordable candidate, and C3 is the one figure in this project with no give in it.

*What breaks if we delete this item.* The three filters get run as a single list, and a candidate that
breaks the budget or the law survives because it scored well somewhere else. That is the exact failure
NASA 6.8 wrote the mandatory-criterion rule to prevent.

*Knock-on.* Q5 — only scored criteria can carry weights; gates never do. Q3 — screening is where the
gates act, and decision 2 already moved the entire cut there.

**4. Coarse weight levels, frozen before scoring. Ties decided by the area owner. Settled
2026-09-08.**

*Weights.* Each scored criterion carries one of a small fixed set of levels — decisive, important,
minor — assigned with written reasoning and **frozen before any candidate is scored**. Gates carry no
weight, and cost carries none either, because it sits on its own axis (both from decision 3).

*Why levels and not numbers.* Our scores are estimates under C9, not measurements. A weight of 0.25
multiplied by a judged score gives a total that looks measured and is not. Coarse levels are also
harder to nudge: moving a criterion from *important* to *decisive* is a visible act, while changing
0.20 to 0.25 is not.

*Why weights at all.* With none, transition risk would count the same as whether the aircraft fits in
a car. `NGO.md` §5.2 says transition risk **is** project risk.

*Frozen first, and that is not negotiable.* MIT Session 5, page 22, on utility: *"Requires formulation
of preferences apriori."* Weights set after the scores are visible are a description of the answer,
not an input to it. Same rule as writing a demonstration's pass/fail sentence before the flight.

*Rejected.* **No weights** — see above. **Rank only, no arithmetic**, which is NASA 6.8's literal ask
— the top criterion would decide almost everything, and a candidate slightly worse on transition risk
but far better everywhere else would lose without the trade ever seeing it. **Continuous numeric
weights**, as in MIT's space tug — standard where the underlying scores are measurements, and ours
are not.

*Ties.* Each of us owns a named group of criteria and decides disagreements inside it. This follows
HYDRO Table 8, enabler 6.3 — a named owner for every deliverable — and it means neither of us owns
every tie-break. The groups are named when the criteria list is written, **before** any level is
assigned to anything.

*Rejected.* **Averaging the two views** — it produces a weight neither of us holds and hides that
there was a disagreement at all. **A single decider for the whole trade** — simplest and it can never
stall, but it puts every tie-break in one place.

*Only the agreed weight is recorded.* The losing view is not written down. **The mechanical
consequence:** the sensitivity re-run has no recorded alternative weight set to work from, so it uses
a defined rule instead — every criterion moved one level up and one level down in turn, plus one run
with all criteria equal — and reports whether the winner changed. That is NASA 6.8's robustness check:
*"whether the uncertainties are such that reducing them could credibly change the ranking of the
alternatives."*

*What breaks if we delete this item.* Weights get assigned while scoring is already under way, which
is the failure MIT page 22 names.

*Knock-on.* Q6 — decision 1's pass-1 freeze protects the function list, and nothing here protects the
weights, so the bias defence chosen in Q6 now carries more load than it otherwise would.

**5. Screening is gates then dominance and nothing else. Selection runs in rounds of increasing
resolution. Settled 2026-09-08.**

*The funnel.*

1. Enumerate every path in the one matrix (decision 2).
2. **Gates** — C3's ceiling, and whether it can be built inside C2. Pass or fail (decision 3).
3. **Dominance** — a candidate is dropped only if another is at least as good on **every** scored
   criterion and better on at least one. MIT Session 5, pages 30 to 36.
4. **No third filter.** Everything non-dominated enters selection. No cap.

*Why dominance runs before the weights are used.* It needs no weights, so it cannot be shaped by them,
and it can run before decision 4's levels are frozen. MIT page 36: *"It's easier to show dominatedness
than non-dominatedness!!!"*

*Screening scores are computed, not judged.* At screening, a candidate's score on a criterion is a
function of its row choices, applied by rule — a path carrying a tilt mechanism has more moving parts
than one that does not, and that holds for every such path. One set of rules, written before the paths
are looked at, applied by the script. Per-candidate judgement starts at selection. This is what makes
several hundred paths tractable, and a rule written in advance cannot be applied more kindly to one
layout than another.

*What we accept by having no third filter.* **Dominance filters less as criteria multiply.** A
candidate is only dominated if another beats it on everything, so with six criteria almost every
layout survives by being best at one thing. Coarse scores strengthen this, because ties are common and
a tie leaves both candidates standing. The surviving set may therefore be large. We accept that rather
than cut on judgement at the narrowest point of the funnel.

*Rejected.* **Best-in-family representatives** — produces a handful automatically, but "best in
family" is a rule we would have to invent at exactly the point where invention is most dangerous.
**Coarse Pugh screening against a datum** — the textbook step, but MIT page 18's first criticism is
that the ranking depends on the datum, and at the cut there is no room to test a datum by running it
twice. **The Pugh matrix is not used at any stage** — see decision 6.

*How a large surviving set stays affordable: rounds.* NASA 4.4's fourth trade step is *"Drop less
promising alternatives and proceed to the next level of resolution, if needed"*, and 4.4.1.2.5 is
successive refinement. So selection is not one deep pass:

- **Round 1** — every non-dominated candidate, scored against the weighted criteria on what we already
  know. No new documents written. Output: a ranking, plus the separate cost axis.
- **Round 2** — the three products NASA 4.4.1.2.1 asks for — straw-man architecture, its own ConOps,
  its own derived requirements — written **only** for what survives round 1.
- **Round 3, if needed** — deeper again.

Each round ends by recording what was dropped and why, which NASA 6.8's report needs in any case.

*Rejected.* **One deep round on every survivor** — the most thorough option available, and the one most
likely to run out of academic year, because the three products are expensive and the surviving set is
expected to be large.

*What breaks if we delete this item.* The cut happens anyway, informally, on the day somebody gets
tired of the list — and nothing records what was dropped or why.

*Knock-on.* Q7 — round 1 is where a small experiment first changes a score, so experiments are planned
against round 1's date, not against the end of the trade. Q10 — the document must hold a per-round
record of what was dropped.

**6. Sealed prediction is the bias defence. Selection scores absolutely against defined levels.
Settled 2026-09-08.**

*The defence.* Before any candidate is scored, each of us writes down which candidate he expects to
win, and why, and commits it. It is opened after round 1's result.

*What it does.* It does not prevent bias. It measures it. If we both predicted the winner and the
totals are close, that is a signal to look again. If we predicted different winners, the trade did
real work.

*What it does not do — recorded as an accepted risk.* The weight levels (decision 4) and the
per-candidate selection scores have **no preventive defence**, only this detector, and its signal is
weak: two people who have discussed the same layouts for weeks are likely to predict the same winner.
**This gap is accepted knowingly.** What limits it is that decisions 1, 2, 3 and 5 already push most
judgement into rules written before any candidate is looked at — the function list is frozen first,
every matrix row carries its reasoning, screening scores are computed by rule, and dominance needs no
weights at all.

*Rejected.* **Assigned advocacy** — each of us writing the strongest case for a layout he does not
favour and the strongest objection to the one he does. It attacks the mechanism NASA names, during the
work rather than after. Not taken. **Repeated datums** — running the selection matrix once per datum
and reporting whether the order held. Not taken, and dropping it is what settled the scoring method
below. **Publish and invite comment** — non-blocking exposure in the public repository. Not taken as a
planned defence; nothing stops us publishing anyway.

*Selection scoring is absolute, not relative.* Each candidate is scored against each criterion on a
coarse scale whose levels carry **written operational definitions**, and decision 4's weights are then
applied. This is NASA 6.8's decision matrix, and 6.8 is explicit about the condition: *"the most
important thing to remember is to have operational definitions of the scale. An operational definition
is a repeatable, measurable number."*

*Why this and not a Pugh matrix.* A Pugh matrix scores every candidate relative to a chosen datum, and
MIT page 18's first criticism is that *"Ranking of alternatives can depend on the choice of datum."*
The usual answer is to re-run with several datums, which was rejected above. **Scoring absolutely
removes the datum, so datum bias cannot occur** — the same move as choosing one matrix over two
abstraction layers in decision 2: remove the failure instead of managing it.

*The cost.* Absolute scoring is harder than relative scoring. "This is worse than that one" is easy;
"this is a 3, where 3 means…" is not. That difficulty is the point — the operational definitions force
us to say what *high transition risk* means **before** we look at any candidate.

*What breaks if we delete this item.* Selection scores get assigned with no defined scale, which makes
them unrepeatable: neither of us could reproduce his own score a month later, and NASA 6.8's
normalisation rule exists to stop exactly that.

*Knock-on.* Q10 — the operational definitions and the sealed predictions both need a home in the
document. Decision 5's line about keeping the Pugh matrix for selection is superseded by this item.

**7. Experiments only where a gate is at stake. C2 buildability is tested where cheap and unknown.
Nothing long-lead is ordered before round 1. Settled 2026-09-08.**

*The rule.* An experiment belongs in the trade study only if its result could flip a **gate** — C3's
ceiling, or C2's buildability. NASA 6.8 gives the underlying test: *"Uncertainty matters in a
particular analysis only if there is a non-zero probability that uncertainty reduction could alter the
ranking of alternatives."* We apply it more narrowly than NASA does — gates only, not scores.

*Experiments attach to rows, not to candidates.* A matrix row is a decision, and an option in that row
appears in many paths, so one bench test moves every path carrying that option. A direct benefit of
decision 2's single matrix.

*What this keeps.* The C2 gate is **tested, not judged**, wherever buildability is genuinely unknown
and the check costs only printed parts and an afternoon — inside C5, no ordered parts, no C6 lead
time. The clearest case is a tilt mechanism run through its full travel under load, which is HYDRO's
*"minimum viable implementation"* almost literally.

*What this drops, knowingly.* **Transition risk gets no physical evidence during the trade.** It is
the heaviest scored criterion and `NGO.md` §5.2 calls it project risk, but it is a score and not a
gate, so under this rule nothing is built to test it. Its score rests on estimates and published
practice. HYDRO 3.3 asks for validation *"numerically and by small experiment"*; we keep the numerical
half and drop most of the experimental half for Stage 3. **Recorded as a knowing departure from the
source, not an oversight.**

*What changes about G2-O5.* The objective is unchanged — both transitions are still proved on the
tether or the bench before any free flight. But that proof now happens **after** the configuration is
chosen, so it can confirm the choice and can no longer inform it. If it fails, the answer is a
rebuild, and C4 with the rebuild allowance is what pays for it.

*Nothing long-lead is ordered before round 1.* No parts are bought until the ranking shows a rig would
change an answer. **The cost, accepted:** C6's parcel lead time is 1 to 3 weeks, longer than a scoring
round, so if a rig turns out to be needed the schedule absorbs those weeks then rather than now. The
thrust stand is the case in point — C8 forces it eventually, and AS2 says it is still unpriced and
unbuilt.

*Rejected.* **Front-loading every ranking-changing experiment**, which is HYDRO's literal advice — it
builds rigs for questions that may not matter, and the trade waits for them. **Letting round 1 choose
the experiments** — targeted, and NASA's successive refinement applied to experiments, but it spends
effort on scores rather than on gates.

*One thing that happens regardless.* `NGO.md` §8 already requires "whether SITL simulates a tiltrotor
or a tailsitter" to close before the configuration trade, because it feeds the fallback rule. That is
analysis under C9, not an experiment, so this decision does not touch it.

*What breaks if we delete this item.* Experiments get proposed one at a time during the trade with no
rule for accepting them, and either none happen or the list grows until the trade stalls.

*Knock-on.* Q9 — enabling products still get need dates, but the dates for ordered rigs now follow
round 1 rather than leading it. Q10 — the departure from HYDRO 3.3 belongs in the document's risks,
not only here.

**8. Mass is derived per candidate in round 2. The expected derived set is named before round 2
starts. Settled 2026-09-08.**

*What was already settled.* Decision 5 makes derived requirements a **round-2 product per candidate**,
alongside the straw-man architecture and its own ConOps, as NASA 4.4.1.2.1 requires. This item settles
only what is in that set, and when mass joins it.

*Mass, per candidate.* Each candidate surviving round 1 closes its own mass loop approximately, using
published motor and propeller data — an estimate under C9, never a measurement. Mass then feeds the
round-2 comparison.

*Why not the winner only.* `NGO.md` already states the loop: hover thrust must exceed weight, so mass
sets thrust, which sets motor and propeller, which sets current, which sets battery, which is itself
mass. Deriving mass only after the choice risks a specific failure — choosing a layout, closing its
loop, and finding the loop does not close inside anything we can build, with the trade's budget
already spent. Mass is also what decides whether G1-O2 is reachable, because hovering costs far more
power than cruising.

*This completes the promise made in Stage 2, decision 2*, which said aircraft mass is deliberately
unconstrained at L1 and that a derived mass target is the first thing the configuration trade must
produce. It is produced in round 2, once per surviving candidate.

*The expected derived set is named in advance.* Before round 2 begins we write down which derived
requirements we expect each candidate to produce — the items only, never values. Anything that appears
and was not on the list is recorded as a **finding**: either our understanding of that architecture had
a gap, or that candidate is doing something the others are not.

*Why in advance.* Stage 2 used the same trick at the L1 freeze — naming the requirement numbers we
expect the trade to re-open — so that a later change is a planned check rather than a surprise. It
also gives round 2 an agenda.

*The risk, and the guard.* A named list can become a ceiling, where we stop looking once the boxes are
filled. The guard is decision 3's: an item not on the list is recorded as a finding, never quietly
added.

*What breaks if we delete this item.* Derived requirements still get written per candidate under
decision 5, but with no mass among them, and with no way to tell a gap in our understanding from a
genuine difference between candidates.

*Knock-on.* Q10 — the expected-set list and the findings list both need a home. `MASS_BUDGET.xlsx`
receives the winner's mass target as the TPM baseline adopted in Stage 2.

**9. Enabling-product need dates are set after the trade. The test site is checked before it. Settled
2026-09-08.**

*Need dates.* The enabling-product list is written now; every need date is set **after** the
architecture is chosen. Nothing is scheduled on a guess.

*The list as it stands.* **Configuration-dependent:** thrust stand (C8, AS2), tether for [DRM-0200],
sheet material (AS7), PCB order (C6). **Configuration-independent:** transmitter and receiver, charger
and LiPo safe bag, pilot licence (C23), operator number (C22), makerspace access (AS6), test site
(AS1).

*Where this is exactly right.* **C22.** The operator number costs €23, expires yearly, and `RULES.md`
records that a lapsed number cannot be renewed — it needs a fresh application. It is the one item on
the list where "early" is wrong: it must be dated **backwards from the first flight**. Setting dates
after the trade does that on its own.

*Where this costs us, recorded.* NASA 4.4.1.2.9 says commitments should be secured *"as early in the
design phase as possible."* Two items depend on other people's calendars, and delaying them is a
knowing departure from that advice:

- **C23, the licence** — the exam is booked at a recognised Dutch flight school, so the date is not
  ours to set.
- **AS6, the makerspace** — `NGO.md` calls it *"the only capability that depends on somebody else's
  opening hours"* and warns that *"free today is not free in March."*

If either has a queue, the schedule absorbs it after the trade instead of before.

*Rejected.* **Splitting by dependence** — dating the configuration-independent items now and the rest
after round 1. It protects C23 and AS6, but produces half a schedule. **Dating everything now** — it
forces a full schedule immediately, but several dates would be invented for rigs whose size we cannot
yet know.

*The test site is checked before the trade, and that is not an exception to the above.* Checking AS1
is de-risking an assumption, not scheduling an enabling product. **AS1 is the only assumption in
`NGO.md` whose failure would invalidate G1-O1, which is MOE-1** — no legal site within travel means
the pass mark can never be flown. C18 needs 150 m from every residential, commercial, industrial and
recreational area, C19 adds the distance formula, and the site must lie outside the GoDrone zones. The
check costs time and travel, not money, so it runs first and the trade is run knowing a site exists.

*What breaks if we delete this item.* The enabling-product list stays scattered through `NGO.md`'s
assumptions and constraints, and the first time anyone asks when the thrust stand is needed is the day
the propulsion system has to be sized.

*Knock-on.* Q10 — the enabling-product list is one of NASA 6.8's report items and lives in the trade
study document.

**10. One document: `02_concept/TRADE_STUDY.md`, on NASA 6.8's ten-item structure. Settled
2026-09-08.**

*The shape.* One file, structured on the ten items NASA 6.8 lists for a decision report: context;
decision needed and intended outcomes; decision criteria; identified alternatives; evaluation methods
and tools; assumptions, uncertainties and sensitivities; results of all alternative evaluations;
recommendations; **final decision with rationale**; lessons learned.

*Everything settled in this stage has a home in it.* The criteria and their sources (decision 3); the
weight levels and their reasoning (decision 4); the operational definitions for every point on every
scale (decision 6); the round-by-round scores and the per-round record of what was dropped and why
(decision 5); the sealed predictions (decision 6); the expected derived set and the findings against it
(decision 8); the enabling-product list (decision 9); and the knowing departures from HYDRO 3.3
(decision 7) and from NASA 4.4.1.2.9 (decision 9).

*Two things live outside it.* `02_concept/FUNCTIONS.md`, because decision 1 requires the file boundary.
And the matrix itself with its coexistence rules and its enumeration script, because decision 5 makes
screening scores computed rather than judged, and machine-readable data cannot live in prose.

*Why one file and not a study plus a short decision record.* The decision can never be read apart from
its evidence. A short record is easier to cite — and easier to cite **without reading why** — and this
project's method is that the reasoning is the product.

*Rejected.* **A separate `DECISION.md`** in MIT's PDR shape, matching the house pattern where a
baseline file holds the "what" and the issue holds the "why". Rejected because the later citations —
the L2 requirements, everything in `03_design/` — would point at the short file, and the study would
stop being read.

*The cost, and the guard.* The file will be long, and later work must cite a section of it rather than
a whole small file. The guard is NASA 6.8's own ordering: the final decision and its rationale are item
9 of 10, so the document ends with the thing everything else cites, and a citation can name that
section.

*MIT's PDR list is not a second document.* Page 37's six points — what was chosen, why, compared
against the rejected alternatives, quantitative confidence, risk-reduction results, and a preview of
detailed design — are a presentation of the same content. If we ever present this, it is a view of the
file, not a new one.

*What breaks if we delete this item.* The trade study gets whatever shape the first writing session
produces, and the items NASA 6.8 lists that are easiest to skip — assumptions and uncertainties, the
results of *all* evaluations, lessons learned — are exactly the ones that get skipped.
