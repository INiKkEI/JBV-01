# Stage 3 — Architecture and configuration selection: notes

The Stage 3 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources, and before opening `02_concept/`. The rules for these notes are in
`REFERENCES.md`, "How the stage notes are written".

**Checks.** Spot check: not done yet. Talk-through: not done yet.

**Stage 3 has two halves.** NASA 4.3 is about **functions** — what the aircraft must do, written before
any hardware is named. NASA 4.4 is about **the design solution** — generating layouts, trading them,
choosing one. The configuration trade sits in the second half. The first half comes before it.

---

## 1. NASA 4.3 — Logical decomposition: the "what" before the "how"

Source: NASA SEH Rev 2, Section 4.3.

*"This process identifies the 'what' that should be achieved by the system at each level."* Its first
input is a validated requirement set — our L1 freeze. Its other input is the technical measures: the
MOEs and the TPMs.

**Architecture is not a hardware list.** *"The system architecture can be seen as the strategic
organization of the functional elements of the system, laid out to enable the roles, relationships,
dependencies, and interfaces between elements to be clearly defined and understood."*

**How many concepts:** *"at least one, but preferably multiple"*. Each specifies its functional
elements, their interfaces, and **its own ConOps**. So "tailsitter" is not a candidate. "Tailsitter,
with these elements, these interfaces and this version of [DRM-0300] to [DRM-0500]" is.

**The clause we are missing.** A good architecture needs *"an equally good knowledge of various
potential technical means of delivering the end products."* We have no V/STOL background. No process
fixes that. It is HYDRO's knowledge curve, arriving where it does the most damage.

**Functional analysis, three steps:**

1. *"Translate top-level requirements into functions that should be performed to accomplish the
   requirements."*
2. *"Decompose and allocate the functions to lower levels of the product breakdown structure."*
3. *"Identify and describe functional and subsystem interfaces."*

It *"is usually based on the ConOps"*. And: *"Each function identified is described in terms of
inputs, outputs, failure modes, consequence of failure, and interface requirements."* **Failure modes
at the function level, before hardware** — every function, not only the three off-nominal scenarios
we already wrote.

The result *"is highly dependent on the creativity, skills, and experience of the engineers doing the
analysis."*

**Outputs.** Decomposition models; **derived technical requirements** — *"requirements that arise from
the definitions of the selected architecture that were not explicitly stated in the baselined
requirements"*; and work products. The derived mass target promised in Stage 2 is one of these. Our L2
set is the derived set.

## 2. NASA 4.4 — Design solution definition: where the trade lives

Source: NASA SEH Rev 2, Section 4.4.

Layouts are *"analyzed through detailed trade studies that result in the selection of a preferred
alternative."*

**4.4.1.2.1 — three products per candidate.** *"a straw man architecture/design, the associated
ConOps, and the derived requirements"*, consistent with each other. That is the real cost of carrying
one candidate.

**4.4.1.2.2 — create concepts.** *"as wide a range of plausible alternatives as is consistent with the
design organization's charter"*. Then the warning written for us:

> *"…the designers tend to become fond of the designs they create, so they lose their objectivity;
> the systems engineer should stay an 'outsider' so that there is more objectivity."*

**We are the designers and the systems engineers. There is no outsider.** Settled decision 6 is our
answer.

**Heritage parts are not proven architecture.** *"…the modification of 'heritage' systems incorporated
into different architectures and operating in different environments from the ones for which they
were designed. If the required modifications and/or operating environments fall outside the realm of
experience, then these too should be considered technology development."* Hobby motors, ESCs, servos
and an ArduPilot controller in a tilting layout are technology development, not integration.

**Describe concepts as classes.** *"…each design concept should be described in terms of controllable
design parameters so that each represents as wide a class of designs as is reasonable."* Otherwise we
compare our best tailsitter sketch against our worst lift+cruise sketch.

**The interface habit:** *"Did you include the cabling?"* and *"Did you consider how the maintainers can
repair the system?"*

**4.4.1.2.3 — the trade study, four steps:** devise alternatives; evaluate them on the MOPs and life
cycle cost; rank them; drop the weak ones and go to the next level of detail. Around it:

- *"…subjectivity also plays a significant role."* The numbers do not do the choosing.
- System models help, *"but it does not depend upon them."* **We can run a trade without a validated
  model.** The most useful sentence in 4.4 for us.
- The result is bounds, not final values.

**4.4.1.2.4 — select.** Use the Decision Analysis Process, Section 6.8 — see section 3. A single
"objective function" is *"usually well worth the trouble"*, but *"Rarely (if ever) is it possible to
produce a combined quantitative measure that relates all of the important factors."* And: *"trade
studies are performed before decisions are made."*

**4.4.1.2.5 — how deep.** Deep enough for analytical validation against the requirements and ConOps,
for cost and operations modelling, and to convince a review team. We have no review team.

**4.4.1.2.6 — a paper study is a legal output.** *"…the form of the design solution definition could
be simply a simulation model or a paper study report."*

**4.4.1.2.7 — verify the design**, by peer review: realisable within the constraints; requirements
traceable **in both directions**; decisions consistent with the requirements. Both directions means
every parent has children too — a mechanical check on two files.

**4.4.1.2.8 — validate the design.** *"Does the system work as expected? How does the system respond to
failures, faults, and anomalies? Is the system affordable?"* A layout whose answer to [DRM-0900] is "it
falls" fails here, at the concept stage.

**4.4.1.2.9 — enabling products.** *"…life cycle support products and services (e.g., production,
test, deployment, training, maintenance, and disposal)…"*. Ours: thrust stand, tether, charger and LiPo
bag, makerspace laser cutter, test site, transmitter, licence, operator number. NASA wants need dates
on a schedule, secured *"as early in the design phase as possible."*

**4.4.1.2.10 — baseline late.** *"Baselining too early takes the inventive nature out of the concept
exploration. Therefore, baselining should be one of the last steps."*

**Outputs.** Nine, mostly for organisations. Mapped for us: L2 requirements; external interfaces
(ConOps §3.3); build drawings and print settings in `03_design/`; internal interfaces (motor–ESC,
ESC–controller, wing joint, battery mount); enabling-product list; verification plan
(`05_verification/TEST_LOG.md`); validation plan ([DRM-0500], MOE-1, MOE-2); operate-to procedures
(transport, LiPo, pre-flight checks). **Not nine documents** — a completeness check.

## 3. NASA 6.8 — Decision analysis

Source: NASA SEH Rev 2, Section 6.8. 4.4 sends the reader here twice.

**When it is worth it.** *"…warranted only when some of the following conditions are met"*:
complexity, uncertainty, multiple attributes, diversity of stakeholders. We meet the first three.

**Criteria (6.8.1.2.1).** Rank each by importance. *"Criteria should be objective and measurable.
Criteria should also permit differentiating among options… Some criteria may not be meaningful to a
decision; however, they should be documented as having been considered."* And:

> *"Criteria may be mandatory (i.e., 'shall have') or enhancing. An option that does not meet mandatory
> criteria should be disregarded."*

**Constraints are gates, not scores.** A layout that fails one is dropped, not marked down.

**Alternatives (6.8.1.2.2).** *"All possible options should be considered."* A **trade tree** prunes them
before expensive analysis. *"It is a best practice to document a decision matrix for a major decision
even if only one alternative is determined to be viable."*

**Normalisation (6.8.1.2.4).** *"…the most important thing to remember is to have operational
definitions of the scale. An operational definition is a repeatable, measurable number."* Without it,
scoring is opinion with a number next to it.

**Robustness (6.8.1.2.5).** Report *"whether the uncertainties are such that reducing them could
credibly change the ranking"*. If a lower-scoring option is chosen, say why — and *"the decision
criteria should be reevaluated"*.

**The decision report (6.8.1.3.1), ten items:** context; decision needed and outcomes; criteria;
alternatives; methods and tools; assumptions, uncertainties and sensitivities; results of all
evaluations; recommendations; final decision with rationale; lessons learned.

## 4. MIT Session 4 — Architecture and concept generation

Source: MIT 16.842, Session 4, 48 pages. **We cite PDF page numbers.** The footer runs one behind
around pages 11 to 17; where it matters, search for the slide title.

**Architecture, page 7:** *"The embodiment of concept, and the allocation of physical/informational
function (process) to elements of form (objects) and definition of structural interfaces among the
objects"*.

**Concept, pages 12–15:** a vision that maps form to function and names its **working principle** —
*"refrigerator = insulated box containing mechanically chilled air"*. "V/STOL aircraft" is a category,
not a concept. Each candidate needs one such sentence.

**Design versus architecture, page 24.** Architecture chooses the concept and so **sets which design
variables exist**. Design chooses their values. **The configuration trade is not a sizing exercise.**
Span, motor count and mass come after.

**Page 27:** generation finds systems *"that do the right thing"*; selection finds those that also
*"do it well … AND comply with current and future regulations and standards"*.

**Pages 30–34.** Restate NASA 4.3. Page 33 shows timing and state diagrams. A **state diagram** suits
us: hover, transition and wing-borne are modes, and the transition is a state change under time
pressure. It is a Stage 3 work product.

**Concept generation, pages 36–47.** Three families: group methods, models of creative people, and
structured methods.

- **Brainstorming** (pages 38–39) wants 5 to 10 people of different backgrounds. We are two, with the
  same reading. Its mechanism is mostly absent for us. Page 40's "creativity killer" sentences are
  still worth avoiding — *"This will never work!"*, *"There's no time for this!"*
- **Morphological matrix** (page 43): list the *m* key decisions as rows; give each its options
  *nᵢ*; enumerate **N = Π nᵢ** combinations. The lecture's warning: *"For many factors, may generate
  many infeasible architectures."* **This fits us.** The five names in C10 mix several separate
  decisions — what lifts in hover, what pushes in cruise, what rotates — so they cannot be compared
  as they stand.
- **Rule-based enumeration** (page 44): components plus rules on what can coexist. The answer to the
  infeasible-combination problem.
- **Abstraction layers** (pages 45–47). Page 47 shows a tool enumerating 240 designs.

## 5. MIT Session 5 — Concept selection and tradespace exploration

Source: MIT 16.842, Session 5, 39 pages. The PDF's own title is "Tradespace Exploration and Concept
Selection". **Pages 12 to 17 are images and were not read.**

**Page 4:** concept synthesis → **screening** → **selection**, moving from qualitative to quantitative.
Screening and selection are two steps, not one.

**Page 6** asks the question no trade can answer about itself: **"are the best alternatives
represented?"** A trade only chooses among what was generated.

**Pugh matrix, page 8.** Pick a datum; mark every other concept better, same or worse on each
criterion; count. *"All concepts should be compared at the same level of abstraction and in similar
language."* Totals are *"guidance only."*

**Page 18 criticises it:** *"Ranking of alternatives can depend on the choice of datum."* Weights must
be agreed. Utility analysis may rank differently. *"The most important criteria may be intangible and
missing from the list."* It *"Should not be used as the ONLY means of concept filtering and
selection."*

**Utility, pages 19–22.** Each criterion mapped to [0,1] and combined. The cautions matter more than
the formula: *"Physical meaning of aggregate objective is lost (no units)"*, and it *"Requires
formulation of preferences apriori"* — weights fixed before results are seen. The space tug example
keeps **cost on its own axis in money**, not folded into utility.

**Dominance, pages 28–36.** A point is efficient *"if it is not possible to move feasibly from it to
increase an objective without decreasing at least one of the others."* A design is dominated if another
is at least as good on every criterion and better on one. *"It's easier to show dominatedness than
non-dominatedness."* **Dominance needs no weights** — the cheapest honest filter we have.

**PDR content, page 37:** what was chosen; why; **compared against the rejected alternatives**;
quantitative confidence the requirements can be met; results of risk-reduction experiments; a preview
of detailed design.

**Page 38:** in conceptual design, use the Pugh matrix *"When detailed mathematical models not yet
available"*; in preliminary design, utility and Pareto filtering. We are in conceptual design.

## 6. HYDRO — the powertrain row

Source: HYDRO, Table 5 "Enablers for Lean Principle 3: Flow", row 3.3. Two reads disagreed on the
section heading above the table. Cite the table, not the section.

> **3.3 Front Load Architectural Design and Implementation**
> *Effectiveness in 2014:* "Structural architecture inherited from KTH was sound. Powertrain
> architecture was not set early. Validation of design was patchy."
> *Proposed changes:* "Define the architecture, validate it numerically and by small experiment.
> De-risk new technologies with minimum viable implementations."

1. **The half they inherited worked. The half they had to decide did not.** The architecture nobody is
   forced to decide stays undecided. Ours is the powertrain too: what lifts in hover, what pushes in
   cruise, whether they are the same, and what happens in the transition. **The transition is the
   project.**
2. **"Numerically and by small experiment."** Numbers: propulsion arithmetic and SITL. Experiment:
   thrust stand, bench mixer test, tethered lift [DRM-0200].
3. **"Minimum viable implementations."** For a tilt mechanism: one printed assembly with a servo and a
   motor, run through full travel under load, long before an airframe exists.

Their gearbox, added late *"to obtain sufficient thrust from the selected motor"*, is what an
unchecked powertrain costs.

## 7. Simulation tools — what exists, and what we chose

Researched 2026-09-08. Sources in `REFERENCES.md`.

**The transition can be simulated, two ways.** **Gazebo**, free: the VTOL models are in
`ArduPilot/SITL_Models` — `alti_transition_quad` (lift+cruise), `bicopter`, `skycat_tvbs` (a
tailsitter), and others. On Windows it needs WSL2. **RealFlight**, paid: *"This simulator only runs on
Windows and requires RealFlight version 8 or version 9."* Its QuadPlane models include a tilt-tricopter
and a tailsitter folder.

**Chosen: built-in ArduPilot SITL, XFLR5 and AVL. An external simulator is deferred until after the
configuration trade.** *Why defer:* the fallback rule (`NGO.md` §5.1) asks whether a proven fallback
exists and is affordable. Knowing it exists is what the rule asks. Installing it is not. *Why both
aerodynamic tools:* both free, both run on Windows, no Linux needed. XFLR5 adds aerofoil and wing
analysis with a GUI. AVL adds stability derivatives and **eigenmode analysis** — the closest analytical
statement we can make about G2-O3's return to trim.

**The limits:**

1. **No tool here models the aerodynamics of a transition.** AVL assumes a *"rigid-body, quasi-steady
   aero model"*. These tools cover cruise only.
2. **So transition risk gets control-logic evidence only.** SITL flies the mode logic, mixer and
   failsafes. It says nothing about our airflow.
3. **C9 still holds.** Every figure is an estimate. An external model simulates a *different* aircraft.
4. **The tilt-wing has no model anywhere we found.** `quadplane-cl84` is mapped in the source to a
   tilt-tricopter with a binary tilt servo.
5. **XFLR5's maintenance status is unresolved.** Recently updated, but labelled "Abandoned" on
   SourceForge. Do not call it actively maintained.

**Still to do:** install and run each once — one SITL flight, one XFLR5 run, one AVL case. *"A tool we
have not run is not a capability."* `NGO.md` §8.

## 8. Where our sources disagree

1. **How many concepts, for how long.** NASA: several, until cost and schedule stop it; prune early.
   MIT: generate many, then screen, then select. Not a conflict — a funnel. Settled decision 5 sets it.
2. **One number or not.** Produce numbers, do not let them decide, and write down what they missed.
3. **Weighting.** NASA asks for a rank; MIT's Pugh matrix is unweighted. Settled decision 4.
4. **Who stays objective.** All three sources assume more people than we have. Settled decision 6.
5. **Baseline early or late.** Architecture early; detailed design baselined late.
6. **Group methods.** We say which methods fit two people and which we skip.

---

## What Stage 3 changes for us

1. **Functions first.** Before any layout is compared, functions are written from the ConOps, each
   with inputs, outputs, failure modes, consequence of failure and interfaces.
2. **A candidate is not a name.** It is a concept sentence, a straw-man architecture, its own ConOps
   and its own derived requirements.
3. **Candidates come from a morphological matrix**, not from memory.
4. **Constraints are gates, not scores.**
5. **Every scoring scale has an operational definition before scoring starts**, and weights are fixed
   before results are seen.
6. **Dominance first, scoring second.**
7. **Scoring is absolute, against defined levels** — no datum. (Settled decision 6.)
8. **The trade study follows NASA 6.8's ten-item report**, and records what was dropped and why.
9. **Enabling products are named and dated.**
10. **Heritage parts do not make an architecture proven.** The fallback rule is answered for the
    architecture, not the part.

**What still blocks the trade:** the L1 freeze of `REQUIREMENTS.md` — NASA 4.3's first input — and
running each simulation tool once (section 7).

## Settled

Each was decided on 2026-09-08, one at a time, after the options and evidence were laid out. The
longer argument for each is in the git history of this file, in the version before 2026-10-14.
**Decisions 2, 5 and 8 were revised on 2026-10-17 in #38**, to fit P2. Each says what it was before.

**1. Functions get their own file, in two passes.** `02_concept/FUNCTIONS.md`. **Pass 1** from the
ConOps alone, before any layout is named, then frozen. **Pass 2** after concept generation: changes
allowed, and each records what changed, why, and **which candidate exposed it**. *Why a file:* a file
boundary is visible; a heading is not. *Why it matters for V/STOL:* on a normal aircraft, function and
form match one to one. On ours, whether lift at zero airspeed, lift with airspeed, forward thrust and
low-speed control come from the same devices **is the configuration choice**. *Why two passes:* we lack
NASA's *"good knowledge of various potential technical means"*, and pass 2 lets us learn without
hiding it. Pass 1 needs only the ConOps, so it is not blocked by L1.

**2. Rows are the independent decisions. One matrix, one pass, by hand.** *Revised 2026-10-17 in
#38; was: the paths enumerated by a script.* Rows are the genuinely free decisions taken from
`FUNCTIONS.md`, not one row per function. Each row names the functions it answers, with its reasoning
beside it. One table holds every decision. Coexistence rules are written, each as a claim of what is
impossible, and the paths are listed and screened by hand. If the list is too long to check by hand,
rows are merged, and each merge is recorded with its reason. *Why the change:* P2 has about a third of
the hours the full method needs, and the script cost more than it saved. *Accepted loss:* a
combination we did not think of can be missed. *Rejected:* two matrices by abstraction layer — a family
could be dropped before the detail that makes it work is seen.

**3. Three filters at three moments.** *Coexistence rule* — "this combination cannot exist" — at
enumeration. *Gate* — "this candidate is not allowed" — at screening. *Score* — "better or worse" — at
selection. **A gate cannot be outscored.** The fallback rule is none of these; it acts when the winner
is chosen. *Criteria* come from walking the twelve areas of Stage 2 decision 3; each surviving
criterion **names its source** in `NGO.md`, `RULES.md` or `CONOPS.md`. *Applied to our constraints:*

- **Documented and set aside** — C12, C13, C15, C16, C17, C20, C22, C23, and C18 as a distance. Every
  candidate meets them equally.
- **Gates** — C3, the money ceiling, and C2, buildable inside the academic year.
- **Scored** — C18 through transport, C8 through what we can verify without a laboratory, C4 through
  rebuildability, and C19 weakly.
- **Not criteria** — C10 defines the candidate set; C11 applies to all.

The heaviest scored criterion is **transition risk** (`NGO.md` §5.2). **Cost** above C3 is a gate;
below it, cost sits on its **own axis in euros** and is never folded into a score.

**4. Coarse weight levels, frozen before scoring.** Each scored criterion is decisive, important or
minor, with written reasoning, **frozen before any candidate is scored**. Gates and cost carry no
weight. *Why levels:* our scores are estimates (C9); a weight of 0.25 times a judged score looks
measured and is not, and a level change is visible. *Ties:* each of us owns a named group of criteria
and decides disagreements in it, named before any weight is set. Only the agreed weight is recorded.
*Sensitivity check:* move each criterion one level up and down in turn, plus one run with all equal,
and report whether the winner changed.

**5. Screening is gates then dominance. Selection takes 3 to 5 candidates, in two rounds.** *Revised
2026-10-17 in #38; was: everything non-dominated enters selection, no cap.* Enumerate → gates →
dominance. If more than five paths survive, we choose three to five, and write one line for every path
dropped. **Screening scores are computed by rule from the row choices**, written before the paths are
looked at. **Round 1** scores every candidate on what we already know. **Round 2** writes the three
products of NASA 4.4.1.2.1 for round 1's **top two** only. Each round records what was dropped and why.
*Chosen:* three to five, and two. *Accepted loss:* the cap is our judgement, not a rule, so a good path
can be dropped by us. The written line for each drop makes that visible.

**6. Sealed prediction, and absolute scoring.** Before scoring, each of us writes down which candidate
he expects to win, and why, and commits it. It is opened after round 1. **It does not prevent bias; it
measures it.** *Accepted risk:* the weights and the selection scores have no preventive defence, only
this weak detector. Decisions 1, 2, 3 and 5 limit it by putting most judgement into rules written
before any candidate is seen. *Scoring* is absolute, against levels with written operational
definitions, with decision 4's weights. No datum, so no datum bias. **The Pugh matrix is not used.**
*Rejected:* assigned advocacy, repeated datums, and publishing for comment as a planned defence.

**7. Experiments only where a gate is at stake.** An experiment belongs in the trade only if it could
flip a gate — C3 or C2. Experiments attach to matrix rows, so one bench test moves every path using
that option. C2 buildability is **tested where cheap and unknown** — printed parts and an afternoon,
nothing ordered. *Knowing departure from HYDRO 3.3:* **transition risk gets no physical evidence during
the trade.** G2-O5's tether and bench proof now comes after the choice, and can confirm it but not
inform it. **Nothing long-lead is ordered before round 1.**

**8. Mass is derived for the two round-2 candidates.** *Revised 2026-10-17 in #38; was: for every
round-1 survivor.* Each of the two closes its own mass loop approximately, from published motor and
propeller data — an estimate. This completes Stage 2 decision 2. *Why two and not only the winner:* the
loop might not close for the layout we chose, after the trade is spent, and the second candidate is the
fallback. **Before round 2, we name the derived requirements we expect each candidate to produce** —
items, not values. Anything else that appears is recorded as a finding.

**9. Enabling-product need dates are set after the trade. The test site is checked before it.** The
list is written now; dates come after the architecture is chosen. The operator number (C22) must be
dated backwards from the first flight anyway. *Knowing departure:* the licence exam (C23) and the
makerspace (AS6) depend on other people's calendars. **The test site (AS1) is checked first**, because
it is the only assumption whose failure makes MOE-1 impossible to fly.

**10. One document: `02_concept/TRADE_STUDY.md`, on NASA 6.8's ten items.** Everything above has a home
in it — criteria and sources, weight levels, operational definitions, round results and drops, sealed
predictions, the expected derived set and findings, the enabling-product list, and the departures from
HYDRO 3.3 and NASA 4.4.1.2.9. *Outside it:* `FUNCTIONS.md`, and the matrix with its rules and script.
*Why one file:* a short decision record is easy to cite without reading why. The final decision is
item 9 of 10, so later work cites that section.

## Read and skipped

- **Full multi-attribute utility analysis** with interview questionnaires (MIT Session 5, page 21). A
  later phase than ours, and it needs a stakeholder group.
- **Brainstorming as defined** (MIT Session 4, pages 38–39). Needs 5 to 10 people.
- **A formal PDR board.** There is none. The PDR content list stays.
- **NASA's configuration-control machinery** around baselining.
- **The NASA Expanded Guidance** (4.3.2, 6.8.2). A separate document. Not opened.
- **MIT Session 5, pages 12–17**, and **NASA Figure 4.4-3** and **MIT Session 4, page 34**. Images; not
  read. Two of the MIT pages, *Challenges* and *Role of the Facilitator*, would be worth a look before
  the trade.
