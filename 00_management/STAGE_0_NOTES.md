# Stage 0 — Before we start: reading notes

What we took from the Stage 0 sources listed in `REFERENCES.md`. One section per source, then
what it changes about how we run JBV-01. Read this before we write a single requirement.

Status: complete. Sources read, and the section locations checked against the documents.

---

## 1. The core idea: every definition is paired with its test

Source: REQI, section "The Two Arms of the V: Every Definition Paired With Its Test".

The V is not a schedule. It is a way of pairing things. Each level where we *define* something
on the way down has exactly one level where we *verify* it on the way up. The horizontal line
between them is a promise that nothing is left to be tested later.

| Down the left arm — define | Up the right arm — verify |
|---|---|
| Stakeholder needs | Validation — does it solve the real need? |
| System requirements | System verification — does it meet the spec? |
| Architecture / high-level design | Integration testing — do the parts work together? |
| Detailed design | Unit testing — does each part work alone? |
| *At the base:* build the components | — |

This is the same table as the one in our project method, with fewer levels. Ours splits
"detailed design" into subsystem and component. That is right for us. A tiltrotor nacelle
assembly and the servo inside it are not the same size of thing.

**The worked example, in the article's own words:** "The aircraft shall stop within 1,500 metres"
enters at the system requirements level. It is broken down into detailed designs for brakes,
spoilers, and reverse thrust. Those are built, unit tested, and integrated. Then the whole
aircraft is verified against that same 1,500 m figure, at the level where it was written.

What we take from this: the number in the requirement is the number in the test. If we cannot
write the number, we do not have a requirement.

**The point we almost missed.** The article says clearly that each test plan — unit, subsystem,
system verification, system validation — is *written during the matching phase on the left side*,
before any hardware exists. Not only the pass/fail criterion. The whole plan. That is stricter
than the rule we had already written down.

## 2. Reading the diagram, stage by stage

Source: REQI, section "How to Read the Systems Engineering V Model Diagram", subsections
"Down the left side: decomposition and definition" / "At the base: build" / "Up the right side:
integration and recomposition".

Left side, from general to detailed:

1. **ConOps** — what the system must achieve for its stakeholders
2. **System level requirements** — verifiable "shall" statements for the whole aircraft
3. **Subsystem requirements and high-level architecture** — the aircraft split into subsystems,
   with requirements given to each
4. **Component level detailed design** — the specification we can build each part from

Base: fabrication. This is the one point where the model changes from definition to building.

Right side, mirroring the left:

1. **Unit testing** — components against the detailed design
2. **Subsystem integration and verification** — each subsystem against its requirements
3. **System integration and verification** — the whole aircraft against the system requirements
4. **System validation** — the finished aircraft delivers the ConOps

Look at item 1 on the left. **We do not have a ConOps yet.** We have a folder called
`01_requirements/` and nothing above it. Every source in Stage 0 and Stage 1 says the ConOps
comes first. They also say that thinking it through shows requirements and functions we would
otherwise miss. So this is our next piece of work, not the requirements.

## 3. Verification vs. validation

Sources: REQI, section "Validation vs. Verification"; HYDRO, Figure 5 (which reproduces
NASA, 2007).

NASA's wording, as given in HYDRO Figure 5:

> **Verification** of a product shows proof of compliance with requirements — that the product
> can meet each "shall" statement as proven through performance of a test, analysis, inspection,
> or demonstration.
>
> **Validation** of a product shows that the product accomplishes the intended purpose in the
> intended environment, that it meets the expectations of the customer and other stakeholders,
> as shown through performance of a test, analysis, inspection, or demonstration.

Short version: verification asks "did we build it right", validation asks "did we build the right
thing". Both use the same four methods — test, analysis, inspection, demonstration.

For us: an aircraft that hovers for 120 s and transitions cleanly is **verified**. An aircraft
that does all of that, but which we cannot photograph, explain, and show our reasoning for, has
failed **validation**. The portfolio piece is our first goal, so this is a real pass/fail
criterion, and we have not written it down yet. Hands-on breadth can also be checked, if we
state it as coverage: did we do our own work across aero, structures, electronics, and controls,
or did the project quietly shrink to the two of those we already liked?

Professional growth is **not** going to be a validation criterion. Finishing a project this size
teaches us something whether we write a criterion or not. A criterion we cannot fail is not a
criterion. It stays a project goal, and it does not go in the validation matrix. Writing the
first two criteria is a Stage 1 job.

## 4. What the V does not cover

Source: REQI, section "Limitations of the V-Model".

The article names contracting for services, and the organisation and execution of operation,
maintenance, repair, and disposal. These sit outside the V and have to be handled separately.

For us that means: battery care and replacement, spare parts, repair after the crash we are
planning for, airframe storage, and disposal of LiPos at the end of the project. We are adding
one more that the article does not mention. Regulatory compliance and site selection are also
outside the V. The V will not remind us that a mass estimate has crossed 900 g. We have to.

## 5. The four V views

Source: HYDRO, section "The V-Model". The four views are named in the body text, citing
Scheithauer & Forsberg 2013. Figure 4 is a simplified single V from INCOSE 2011, and Figure 5
gives the verification and validation definitions quoted above.

A single V becomes crowded as soon as you put a real project on it. Scheithauer and Forsberg
split it into four views, and HYDRO applies all four to their boat:

| View | Shows | HYDRO figure |
|---|---|---|
| Basic-V | Architectural decomposition, in a standard form | 6 (as built), 17 (improved) |
| Development-V | Hand-over of information between work products | 10, 11 |
| Assurance-V | Verification and validation activities | 12, then 13–16 |
| Dynamic-V | Iterations that happen during development | 8, 9 |

On the Basic-V, HYDRO puts time along the horizontal axis instead of the logical sequence that
Scheithauer and Forsberg intended. We should do the same. Our project is bounded by an academic
year, and the calendar is the thing we keep getting wrong.

Worth knowing: they say the four views were applied *after the project was over*, and that
nobody had yet published an example of using them during a project. So this is a promising tool,
not a proven one. If we use the views while we work, we are doing something the authors listed
as still open.

## 6. Systems engineering, aerospace version

Source: MIT 16.842, Session 1 "Systems Engineering Overview and Stakeholder Analysis"
(de Weck, Fall 2015).

**How deep to decompose.** If we assume about 7 items per level (Miller 1956), the number of
levels in a drawing tree is about

    n_levels ≈ log(n_parts) / log(7)

Their table: screwdriver ~3 parts / 1 level; inkjet printer ~300 / 3; automobile ~10,000 / 5;
airliner ~100,000 / 6. This is a rule of thumb, not a derivation.

Applied to us — **and this is an estimate, not a measurement, because our scale is not decided
yet** — a small V/STOL RC aircraft probably has a few hundred separate parts if we count
fasteners and wiring one by one. log(300)/log(7) ≈ 2.9. Call it **3 to 4 levels** of
decomposition: aircraft → subsystem → assembly → component. That agrees with the five-level left
branch we already chose, which is a good sign. If the real part count turns out closer to 1,000,
the answer is still about 3.5 levels. The rule is not sensitive, so there is no reason to redo
this once the scale is fixed.

**Two definitions worth keeping side by side.** NASA (1995): identify and quantify goals, create
alternative concepts, perform trades, select and implement the best design, verify it is properly
built and integrated, then assess how well it met the goals. INCOSE (2004): "an interdisciplinary
approach and means to enable the realization of successful systems." The NASA one is a process we
can follow. The INCOSE one is a definition we can quote.

**Lifecycle gates.** NASA runs Pre-Phase A through Phase F with named reviews — MCR, SRR, PDR,
CDR, SIR, FRR, and others. The lecture says these matter. We are choosing not to run the formal
version, but two of them are cheap and would catch real mistakes: a **requirements review** (SRR)
before we freeze the requirements, and a **design review** (PDR) before we buy anything
expensive. Two meetings with an agenda and a written outcome. That is the whole cost.

**The lecturer's own criticisms of formal systems engineering.** These are worth recording,
because they are the most honest statement of limits here, and they come from the person
teaching the method:

- it assumes a clean-sheet design, while most real projects modify existing systems and reuse
  off-the-shelf parts
- it assumes requirements and stakeholder needs are known and stable, while in fact they change
- it does not give enough weight to outside factors such as policy
- it does not give enough weight to the effect of design iteration and rework on budget and
  outcome

Points one and four apply to us strongly. We will reuse hobby parts, and we have already planned
for at least one crash and rebuild.

**Stakeholders.** Defined as a group or individual affected by, or in some way accountable for,
the outcome. They are split into customers, who asked for the product and will receive it, and
other interested parties, who set constraints or influence success. The lecture's concept
question makes the point directly: talk to stakeholders before designing anything, mainly because
we need to understand their needs first.

Our stakeholders are not obvious and we have not listed them. First attempt, to be discussed
properly in Stage 1: the two of us; future employers reading the portfolio; RDW and EASA as the
regulator; and anyone near a test site. The regulator is a stakeholder whose requirements cannot
be negotiated and are already written down. That makes it the easiest one to satisfy and the most
expensive one to ignore.

**ConOps.** Named as one of the main outputs of capturing stakeholder expectations, and as an
input to both requirements and architecture. The lecture's line: thinking through the ConOps and
the use cases often shows requirements and functions that would otherwise be missed. To be done
early.

**Stakeholder Value Network analysis** also appears in this session. Four steps: map, quantify,
search, analyse, with the BP Whiting refinery case study. Its value is in finding *indirect*
stakeholder relationships that a simple hub-and-spoke view misses. In the case study, the two
stakeholders that actually mattered were the ones management had not modelled. For a two-person
project this is too heavy a tool. Noted, and skipped on purpose.

## 7. HYDRO: a student team that did this badly, and said so

Source: HYDRO — Sutherland, Kamiyama, Aoyama, Oizumi, IMDC 2015.

Context: 21 masters students across two universities (12 Tokyo, 9 KTH). They built two autonomous
solar powered hydrofoils, 14 kg and 16 kg, mostly CFRP. They placed 3rd and 4th, broke down
repeatedly, failed to finish the course, and were **beaten by significantly simpler designs using
displacement hulls**. That sentence is the most useful line in the whole Stage 0 reading for a
team about to choose between a tiltrotor and something boring.

What went wrong, matched to the views:

| Finding | Where | Their fix |
|---|---|---|
| Most of their learning happened at the end, not the start | Figure 7, Knowledge Growth Curve | Do work early across all of the V; test last year's boat first |
| Every iteration happened only after something failed | Figure 8 (Dynamic-V) | Plan a prototype loop from the start (Figure 9) |
| A major yaw control fault was found in a lake test **one day before the race**, and was still there after day one of racing | Figure 8, the large red loop | Same fix — prototype loop, verification starts early |
| A gearbox had to be added during the project because the chosen motor could not produce enough thrust | Figure 8, lower red loop | Check the powertrain architecture with calculations and a small experiment before committing |
| Very few requirements reached the lower levels; work products such as "System design" had no known completion date and no owner | Figures 10 → 11 (Development-V) | Name the work products, give each an owner and a date, and make requirements flow down |
| Verification happened only shortly before the race; several critical systems had little or no validation | Figure 12 → 13–16 (Assurance-V) | Spread V&V across April to August, month by month |
| The requirements document "was not attainable, read once and not looked at again" — closer to a wish list than an analysed document | Table 2, "Focusing on Requirements"; Table 5, enabler 3.2 | **Set a few attainable requirements at each level of the decomposition and ensure they are verified and validated** |
| Several competing ideas of value at once: win the race, or maximise performance, or maximise student learning. Never resolved | Table 1 "Visionary Leadership"; Table 3, enabler 1.2 | Ask the team at the start and write down what value means |
| Technology was developed that nobody needed (a height sensor) | Table 4, enabler 2.4 | Identify the need before developing anything |
| Progress was tracked only as deviation from a fixed plan, written when the team knew least about the system | Table 4, enabler 2.6 | Use weekly metrics that mean something — time on project, wasted time, requirements met |
| Work was done in separate groups; one large passive weekly meeting | Table 2 "Building Culture"; Table 5, enabler 3.5 | One *active* weekly meeting where everyone reports; shared work products always available |
| Skills were not developed until late; "test plans and data recording was unacceptably poor at times" | Table 8, enabler 6.3 | Define who is responsible for what, and hold people to delivery |

They rated themselves **Low** on Capability Maturity, Systems Engineering Culture, Design
Robustness Mindset, and Accountability Structure. They named the first and third as the most
important to fix. Their reason for low capability maturity is one line: "most work was completed
only once."

The quote that frames the whole paper, from Scheithauer via HYDRO: *"iterations are the rule in
systems engineering, not the exceptions."* That is why our schedule assumes a crash instead of
being surprised by one.

---

## What Stage 0 changes for us

**Things we are adopting that we had not written down before:**

1. Test *plans*, not only pass/fail criteria, are written during the matching phase on the left
   branch.
2. Every work product gets a target date, kept as a GitHub milestone or issue. No owner field —
   with two of us it carries no information.
3. One prototype loop is planned into the schedule on purpose, before we commit to anything. Not
   an iteration we fall into after a failure.
4. Two light reviews: a requirements review before we freeze, and a design review before we
   spend money.
5. A short weekly written note — what moved, what is stuck. One file per week at
   `00_management/weekly/YYYY-WW.md`, so we are never editing the same file in the same week. No
   metric set, no hours tracking.
6. Value is defined and written down before the requirements. We already have a priority order
   (portfolio, then hands-on breadth, then professional growth). HYDRO's problem was not missing
   goals but a missing *ranking* between them. Ours is ranked. It still has to survive a real
   trade study, and we should expect it to be tested the first time the portfolio-friendly option
   and the learning-friendly option point in different directions.

**Things we are deliberately not adopting:** the full NASA document set, the SEMP, stakeholder
value network analysis, and MBSE tooling. Reason: they cost time and give us nothing back at two
people and one academic year.

**On gates, since item 4 looks like a contradiction.** Adding two reviews while rejecting the
NASA model needs a line drawn, because "no gates" is not what we mean. What costs time there is
the *ceremony*: an external review board, an entry and exit document package, formal sign-off,
and a schedule built around the review date. What is nearly free is the *checkpoint*: the two of
us agreeing out loud that a stage is finished before starting the next one. We keep the
checkpoint and drop the ceremony. If a check ever takes longer than the work it is checking, it
has turned into ceremony and we cut it.

**What Stage 0 tells us to do next, in order:**

1. Write the ConOps. Nothing above it exists yet and everything below it depends on it.
2. List the stakeholders and what each of them expects.
3. Decide what value means for us, including what we are willing to give up when portfolio value
   and learning value pull in different directions.
4. Then, and only then, write the system requirements.

**Still open, and Stage 0 does not close either of them:** configuration and scale. The one thing
Stage 0 does say about configuration is HYDRO's result. A technically ambitious hydrofoil lost to
simple displacement hulls. That is an argument about ambition, not an argument for any particular
V/STOL layout.

**Value, first pass — to be tested, not treated as settled.** We are deciding case by case rather
than adopting a single standing rule. Our starting lean is that **learning wins, where the thing
is not too complicated for us**.

Recorded honestly: "too complicated for us" is not yet a test, and an untested adjective is what
lost HYDRO a year — they also had goals and no way to adjudicate between them in the moment. Two
questions make it decidable at the point of decision, and both are answerable in a minute:

1. Does a proven off-the-shelf fallback exist, and can we afford it?
2. What is the date by which we switch to the fallback if ours is not working?

If both have answers, learning wins and we take the ambitious path. If either does not, we take
the proven one. This turns the lean into something a Stage 2 trade study can actually be checked
against, without pre-committing us to a configuration or a scale. Strike this clause if we decide
it is more machinery than we want — but then we need something else in its place.

**Closed during Stage 0:** file sync. The project lives in a git repository at
https://github.com/INiKkEI/JBV-01. This settles the third of the three items that were open when
we started, and it changes one thing about how we work: history is now kept for us, so the
append-only rule for the design log stops depending on our discipline. It does not mean a quiet
edit is acceptable — a logged revision is still a logged revision — but a mistake is now
recoverable.
