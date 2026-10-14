# Stage 0 — Before we start: notes

The Stage 0 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources. The rules for these notes are in `REFERENCES.md`, "How the stage notes are
written".

**Checks.** Spot check: not done yet. Talk-through: not done yet.

---

## 1. Every definition is paired with its test

Source: REQI, section "The Two Arms of the V: Every Definition Paired With Its Test".

The V is not a schedule. It is a way of pairing things. Each level where we *define* something on
the way down has exactly one level where we *verify* it on the way up.

| Left arm — define | Right arm — verify |
|---|---|
| Stakeholder needs | Validation — does it solve the real need? |
| System requirements | System verification — does it meet the spec? |
| Architecture / high-level design | Integration testing — do the parts work together? |
| Detailed design | Unit testing — does each part work alone? |
| *At the base:* build the components | — |

Our own table splits "detailed design" into subsystem and component. That is right for us: a
nacelle assembly and the servo inside it are not the same size of thing.

**The worked example.** "The aircraft shall stop within 1,500 metres" is written at the system
requirements level. It is broken down into brakes, spoilers and reverse thrust. Those are built,
tested alone and integrated. Then the whole aircraft is verified against the same 1,500 m, at the
level where it was written. **The number in the requirement is the number in the test.** If we
cannot write the number, we do not have a requirement.

**The point we almost missed.** Each test *plan* — unit, subsystem, system verification, system
validation — is written during the matching phase on the left side, before any hardware exists. The
whole plan, not only the pass/fail criterion.

## 2. Reading the diagram

Source: REQI, section "How to Read the Systems Engineering V Model Diagram", three subsections.

- **Left side, general to detailed:** ConOps → system requirements → subsystem requirements and
  high-level architecture → component detailed design.
- **Base:** fabrication. The one point where definition changes into building.
- **Right side, mirroring the left:** unit testing → subsystem integration and verification →
  system integration and verification → system validation.

The ConOps comes first. Thinking it through shows requirements and functions we would otherwise
miss. Ours is `01_requirements/CONOPS.md`.

## 3. Verification and validation

Sources: REQI, section "Validation vs. Verification"; HYDRO, Figure 5, which reproduces NASA 2007.

> **Verification** of a product shows proof of compliance with requirements — that the product
> can meet each "shall" statement as proven through performance of a test, analysis, inspection,
> or demonstration.
>
> **Validation** of a product shows that the product accomplishes the intended purpose in the
> intended environment, that it meets the expectations of the customer and other stakeholders,
> as shown through performance of a test, analysis, inspection, or demonstration.

Short version: verification asks "did we build it right", validation asks "did we build the right
thing". Both use the same four methods — test, analysis, inspection, demonstration.

**A criterion we cannot fail is not a criterion.** Our validation criteria are the measures of
effectiveness in `NGO.md` §4. Stage 1 explains how they are tested.

## 4. What the V does not cover

Source: REQI, section "Limitations of the V-Model".

Outside the V: contracting for services, and the operation, maintenance, repair and disposal of the
system. For us: battery care, spare parts, repair after a crash, storage, and LiPo disposal. Also
outside it, and not named by the article: regulation and site selection. The V will not remind us
about the law. We have to.

Stage 1 found that NASA disagrees about support and disposal, and we follow NASA there. See Stage 1,
section 8.

## 5. The four V views

Source: HYDRO, section "The V-Model". The four views are named in the body text, citing Scheithauer
& Forsberg 2013. They are not in a figure.

A single V gets crowded on a real project. It can be split into four views:

| View | Shows | HYDRO figure |
|---|---|---|
| Basic-V | The architecture, broken down in a standard form | 6 as built, 17 improved |
| Development-V | Hand-over of information between work products | 10, 11 |
| Assurance-V | Verification and validation activities | 12, then 13–16 |
| Dynamic-V | Iterations during development | 8, 9 |

HYDRO puts time on the horizontal axis of the Basic-V. We do the same, because our calendar is
fixed.

**A warning.** HYDRO applied the views *after* their project ended, and says nobody had yet
published an example of using them during a project. A promising tool, not a proven one.

## 6. MIT Session 1 — systems engineering, aerospace version

Source: MIT 16.842, Session 1 "Systems Engineering Overview and Stakeholder Analysis".

**How deep to break the aircraft down.** With about 7 items per level (Miller 1956):

    n_levels ≈ log(n_parts) / log(7)

The lecture's table: screwdriver ~3 parts, 1 level; printer ~300, 3; car ~10,000, 5; airliner
~100,000, 6. A rule of thumb, not a derivation.

For us — **an estimate, because scale is not decided** — a few hundred parts counting fasteners and
wires: log(300) / log(7) ≈ 2.9. At 1,000 parts it is about 3.5. So 3 to 4 levels: aircraft →
subsystem → assembly → component. The rule is not sensitive, so there is no need to redo it once
the scale is fixed.

**Lifecycle reviews.** NASA runs named reviews — MCR, SRR, PDR, CDR, SIR, FRR and others. We keep
two, because they are cheap and catch real mistakes: a **requirements review** (SRR) before the
freeze, and a **design review** (PDR) before we spend money.

**The lecturer's own criticisms of formal systems engineering:**

- it assumes a clean-sheet design, while most projects reuse existing and off-the-shelf parts;
- it assumes requirements are known and stable, while they change;
- it gives too little weight to outside factors such as policy;
- it gives too little weight to iteration and rework.

The first and the fourth apply to us strongly: we reuse hobby parts, and we plan for a crash and a
rebuild.

**Stakeholders.** A group or person affected by, or accountable for, the outcome. Split into
customers, who asked for the product, and other interested parties, who set constraints. Talk to
them before designing anything. Ours are in `01_requirements/STAKEHOLDERS.md`.

## 7. HYDRO — a student team that did this badly, and said so

Source: HYDRO — Sutherland, Kamiyama, Aoyama, Oizumi, IMDC 2015.

21 masters students, two universities, two solar hydrofoils of 14 and 16 kg, mostly carbon fibre.
They placed 3rd and 4th, broke down repeatedly, did not finish the course, and were **beaten by much
simpler boats with displacement hulls**. That is the most useful line in Stage 0 for a team about to
choose between an ambitious V/STOL layout and a boring one.

| What went wrong | Where | Their fix |
|---|---|---|
| Most learning happened at the end | Figure 7, Knowledge Growth Curve | Do work early across the whole V |
| Every iteration came only after a failure | Figure 8, Dynamic-V | Plan a prototype loop from the start (Figure 9) |
| A yaw control fault was found **one day before the race** | Figure 8, large red loop | Same — start verification early |
| A gearbox was added late because the motor gave too little thrust | Figure 8, lower red loop | Check the powertrain with calculations and a small experiment first |
| Work products had no owner and no date; few requirements reached lower levels | Figures 10 → 11, Development-V | Name each work product, give it an owner and a date |
| V&V only just before the race | Figure 12 → 13–16, Assurance-V | Spread V&V month by month |
| The requirements document "was not attainable, read once and not looked at again" | Table 2; Table 5, enabler 3.2 | **A few attainable requirements at each level, each verified** |
| Several ideas of value at once, never resolved | Table 1; Table 3, enabler 1.2 | Decide at the start what value means |
| Technology nobody needed was developed | Table 4, enabler 2.4 | Identify the need first |
| Test plans and data recording "unacceptably poor at times" | Table 8, enabler 6.3 | Name who is responsible for what |

They rated themselves lowest on capability maturity — "most work was completed only once" — and on
design robustness.

The line that frames the paper, from Scheithauer via HYDRO: *"iterations are the rule in systems
engineering, not the exceptions."* That is why our schedule plans for a crash.

---

## What Stage 0 changes for us

**Adopted:**

1. Test *plans*, not only pass/fail criteria, are written during the matching phase on the left
   branch.
2. Every work product has a target date, kept as a GitHub milestone or issue.
3. One prototype loop is planned on purpose, before we commit to anything.
4. Two light reviews: requirements review before the freeze, design review before we spend money.
5. A short weekly note — what moved, what is stuck — at `00_management/weekly/YYYY-WW.md`.

**Checkpoint, not ceremony.** What costs time in NASA's model is the ceremony: a review board,
document packages, formal sign-off. What is nearly free is the checkpoint: the two of us agreeing out
loud that a stage is finished before starting the next. We keep the checkpoint. If a check takes
longer than the work it checks, it has become ceremony and we cut it.

**How we choose between an ambitious path and a proven one.** Two questions, answered at the moment
of choosing: does a proven off-the-shelf fallback exist that we can afford, and by what date do we
switch to it if ours is not working? If both have answers, we take the ambitious path. If not, the
proven one. This is now the fallback rule in `NGO.md` §5.1.

## Read and skipped

- **Stakeholder Value Network analysis** (MIT Session 1, slides 42–54). Finds indirect relationships
  among many organisations. Too heavy for two people.
- **The full NASA document set, the SEMP, and MBSE tooling.** They cost time and give nothing back at
  two people and one year.
- **The NASA and INCOSE definitions of systems engineering** (MIT Session 1). Correct, and change
  nothing we do.
