# Stage 1 — Mission needs and concept of operations: notes

The Stage 1 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources. The rules for these notes are in `REFERENCES.md`, "How the stage notes are
written".

**Checks.** Spot check: not done yet. Talk-through: not done yet.

**Stage 1 is complete.** Its four outputs exist: stakeholder expectations in `NGO.md`, the ConOps in
`CONOPS.md`, support strategies in ConOps §5.0, and the measures of effectiveness in `NGO.md` §4.

---

## 1. The process — NASA's ten activities

Source: NASA SEH, Section 4.1 "Stakeholder Expectations Definition", 4.1.1.1 to 4.1.1.3.

Purpose, in NASA's words: "to identify who the stakeholders are and how they intend to use the
product." It is done through use-case scenarios (Design Reference Missions, DRMs) and the ConOps.

**Three inputs.** Customer expectations — ours only, we are the customer. Other stakeholders —
`STAKEHOLDERS.md`. Customer flow-down requirements — none, there is no level above us. Say so rather
than leave it blank.

**Ten activities, and what each costs us:**

| # | Activity | Cost for us |
|---|---|---|
| 4.1.1.2.1 | Identify stakeholders | One list |
| 4.1.1.2.2 | Understand their expectations | Read the regulator's rules. The rest is us |
| 4.1.1.2.3 | Identify needs, goals, objectives | Real work — section 2 |
| 4.1.1.2.4 | Establish the ConOps and support strategies | The largest job — section 4 |
| 4.1.1.2.5 | Rewrite expectations as acceptable statements | After the ConOps has corrected them |
| 4.1.1.2.6 | Find the Measures of Effectiveness | Real work — section 3 |
| 4.1.1.2.7 | Check traceability in both directions | We already have this rule |
| 4.1.1.2.8 | Obtain stakeholder commitments | A conversation between the two of us |
| 4.1.1.2.9 | Baseline the expectations | A commit |
| 4.1.1.2.10 | Capture work products | Decisions and rationale go in GitHub issues |

**Order matters.** NASA writes the first needs and goals, *then* the ConOps, *then* rewrites the needs
and goals. Writing the ConOps "may lead to further refinement of the initial set of stakeholder
expectations if gaps or ambiguous statements are discovered." The first list is a draft on purpose.

## 2. Needs, goals and objectives

Source: NASA SEH, Section 4.1.1.2.3 "Identify Needs, Goals, and Objectives".

- **Need** — "a single statement that drives everything else". About the problem, not the solution.
- **Goals** — an elaboration of the need. They need not be numbers, but they must let us judge
  whether they were achieved.
- **Objectives** — specific target levels. Each relates to one goal.

An objective must be (1) specific — about *what*, not *how*; (2) measurable and verifiable;
(3) aggressive but attainable; (4) about results, not methods.

**Two lines that mattered most.**

*"The need statement is singular. Trying to satisfy more than one need requires a trade between the
two, which could easily result in failing to meet at least one."* Our need is one statement, about
the aircraft, and it states a problem: *"We need an aircraft that does not force a choice between
landing anywhere and flying as long as a plane."* Runway independence is inside the problem, so
V/STOL follows from the need instead of being assumed. `NGO.md` §1.

*"Objectives 'To Be Determined' (TBD) may be included until trade studies occur."* But also:
"Objectives need to be feasible before requirements are written." So TBD is allowed in the ConOps
and not allowed in `REQUIREMENTS.md` at the freeze. `NGO.md` now carries no TBD.

NASA also says objectives "are not requirements". They help form the requirement set later.

## 3. Measures of Effectiveness

Source: NASA SEH, Section 4.1.1.2.6 "Analyze Expectations Statements for Measures of Effectiveness".

MOEs are "the measures of success that are designed to correspond to accomplishment of the system
objectives as defined by the stakeholder's expectations." They can be the same as the mission
success criteria.

**The test for whether something is an MOE:** "failure to satisfy these measures will cause the
stakeholder to deem the system unacceptable." If we cannot fail it, it is not an MOE. This agrees with
Stage 0: a criterion we cannot fail is not a criterion.

MOEs are written at the same time as the needs, goals and objectives. Ours are MOE-1 and MOE-2,
`NGO.md` §4.

## 4. The ConOps — what it is, and what it is not

Source: NASA SEH, Section 4.1.1.2.4, and the box "Concept of Operations vs. Operations Concept" in
Section 4.1.

**Implementation-free.** The ConOps defines "what is expected without addressing how (the design) to
satisfy the need." So it never names a tiltrotor or a tailsitter. It says the aircraft takes off
vertically, transitions, cruises, transitions back and lands vertically. Every candidate layout
satisfies that, so writing the ConOps does not quietly choose the configuration.

**Not the Operations Concept.** The Concept of Operations is written early by the technical team. The
Operations Concept is written later by the operational team. We want the first.

**Two instructions we must not skip:**

1. **Off-nominal scenarios are required.** "The ConOps should include scenarios for all significant
   operational situations, including known off-nominal situations." These scenarios produce
   requirements, so they are written before hardware is chosen.
2. **Support strategies belong here.** They cover "fabrication, test, deployment, operations,
   sustainment, and disposal". See section 8.

"Thinking through the ConOps and use cases often reveals requirements and design functions that might
otherwise be overlooked." This happened to us: walking through the failure scenarios produced the
minimum distance to any person and the ability to abandon a transition. Neither follows from the need
or the goals.

## 5. Appendix S — the ConOps outline

Source: NASA SEH, Appendix S "Concept of Operations Annotated Outline".

The appendix says the content "will be a function of the type, size, and complexity of the project."
So cutting sections is allowed, if we say which and why.

We cut one section: **7.2 Organisational Impacts**. It is written for hiring, retraining and
reorganising staff, and there are two of us. Every other section is in `CONOPS.md` under the
outline's own numbers.

Section 6.0 gives one piece of advice we took: "A good practice is to label each of these scenarios to
facilitate requirements traceability; e.g., [DRM-0100], [DRM-0200], etc." Our scenarios are
[DRM-0100] to [DRM-0900] in ConOps §6.

Section 8.0 says "Pay special attention to closeout issues at the end of the project."

## 6. MIT Session 1 — the stakeholder half

Source: MIT 16.842, Session 1, slides 30 to 54, footer numbering.

Slide 35 defines a stakeholder the same way NASA does: "A group or an individual who is affected by or
is in some way accountable for the outcome of an undertaking."

**Slide 36 is the useful one.** Stakeholder types against what they expect, translated to us:

| Stakeholder (MIT) | Typical expectation | Ours |
|---|---|---|
| Customer | Quality, on time, affordable, support | Us |
| Subcontractors / vendors | Well defined requirements | Hobby suppliers — a part number and a date |
| Local, state, national public | No harm to the environment | People near the test site — noise and safety |
| Organisation management | Commitments met, policies followed | Nobody |
| Project manager / technical team | Work on time; clear tasks | Us |
| Functional organisations, e.g. test | Test support available, clear test requirements | Nobody. We have no laboratory — C8 |

**Who is our customer?** NASA: the person or organisation that asked for the product and receives it.
**We are the only customer.** There is no supervisor setting acceptance criteria. The cost: nothing
outside us stops requirements creep. That is carried as a risk.

## 7. HYDRO Table 3 — value

Source: HYDRO, Table 3, enabler 1.2 "Establish the Value of the End Product or System to the
Customer". The table has one row.

| Effectiveness in 2014 | Proposed change |
|---|---|
| "Multiple definitions of value were being worked towards, including to win the race and to maximize potential performance to increase student learning." | "At the project startup survey the students to learn their interests and use this to define value." |

The body text adds the result: "a bias to attempt to build a very high performance boat … which
ultimately sacrificed robustness of the craft when in the race." They wanted to win *and* to learn,
never chose, and the ambitious build broke down.

For two people, the survey is one conversation. Table 8, enabler 6.3 asks for the same thing: "Survey
team members to understand their skills and aspirations."

**A fault in the paper.** The "Flow:" paragraph in "LOOKING BEYOND THE V-MODEL FOR DEVELOPMENT
IMPROVEMENTS" says the Flow enablers are in Table 3. They are in Table 5. Table 3 is Value.

## 8. Where our sources disagree

**Does the V cover support and disposal?** REQI (Stage 0, section 4) says no. NASA 4.1 lists "Enabling
Product Support Strategies" as an output, covering "fabrication, test, deployment, operations
sustainment, and disposal". **We follow NASA.** It costs almost nothing and catches LiPo charging and
storage, spares, the rebuild and battery disposal. They are in ConOps §5.0. Regulation and site
selection stay outside the V.

**How much stakeholder machinery?** NASA assumes an external customer, signatures and change control.
HYDRO failed partly from having too little. **Our line:** keep every activity that produces a file we
will reread — stakeholder list, needs, goals, objectives, MOEs, ConOps. Shrink commitments and
baselining to a conversation and a commit.

---

## What Stage 1 changes for us

1. The ConOps follows the Appendix S outline, and states its own cuts.
2. Operational scenarios carry labels — [DRM-0100] and on — so requirements trace to them by name.
3. Off-nominal scenarios are written before hardware is chosen.
4. TBD is allowed in the ConOps. It is not allowed in `REQUIREMENTS.md` at the freeze.
5. Needs and goals are written before the ConOps and rewritten after it. Two passes, on purpose.
6. Support and disposal go in ConOps §5.0.
7. MOEs are our validation criteria. The test is whether failing one would make us call the aircraft
   unacceptable.

**What Stage 1 does not close:** configuration and scale. It does not need to. The ConOps is
implementation-free, and both close in Stage 3.

## Read and skipped

- **Stakeholder Value Network analysis** (MIT Session 1, slides 42–54). Read and confirmed skipped. It
  needs a questionnaire scoring every value flow. The BP Whiting case is a good example — the two
  stakeholders that mattered were the two management had ignored — but it is a tool for a dozen
  organisations. We have no indirect relationships worth modelling.
- **The Operations Concept** as a separate document.
- **Appendix S section 7.2**, organisational impacts.
- **NASA Figures 4.1-1 to 4.1-3 and Table 4.1-1.** Process flow and examples. Nothing in them changes
  what we do.
