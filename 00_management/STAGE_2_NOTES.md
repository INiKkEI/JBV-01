# Stage 2 — System requirements: notes

The Stage 2 sources in `REFERENCES.md`, cut down to what changes how we run JBV-01. Read this
instead of the sources, and before writing a line of `01_requirements/REQUIREMENTS.md`. The rules for
these notes are in `REFERENCES.md`, "How the stage notes are written".

**Checks.** Spot check: not done yet. Talk-through: not done yet.

---

## 1. NASA 4.2 — turning the ConOps into "shall" statements

Source: NASA SEH, Section 4.2 "Technical Requirements Definition", 4.2.1.1 to 4.2.2.

The process "transforms the stakeholder expectations into a definition of the problem and then into a
complete set of validated technical requirements expressed as 'shall' statements". It is "recursive
and iterative", from the top level down.

**Inputs.** Stakeholder expectations (`NGO.md`), the ConOps (`CONOPS.md`), support strategies (ConOps
§5.0), and the MOEs (`NGO.md` §4). All four exist.

**Seven activities:**

| # | Activity | For us |
|---|---|---|
| 4.2.1.2.1 | Define constraints and functional expectations | Mostly done — `NGO.md` §6 |
| 4.2.1.2.2 | Define requirements | The main work |
| 4.2.1.2.3 | Write them as acceptable statements | Appendix C rules — section 6 |
| 4.2.1.2.4 | Validate them | Six steps — section 2. The agenda of our review |
| 4.2.1.2.5 | Define MOPs and TPMs | Section 4 |
| 4.2.1.2.6 | Baseline them | The freeze. NASA holds an SRR here |
| 4.2.1.2.7 | Capture work products | Already done |

**Types of requirement.** Functional (what), performance (how well), interface (product to product).
Crosscutting: environmental, safety, human factors, the "-ilities", design and construction
standards. A complete set needs all of these, not only the interesting ones.

**Key Driving Requirements (KDRs), 4.2.1.2.3.** A requirement "that can have a large impact on cost
or schedule when implemented". Any priority can be a KDR. With €800 in total (C3) and one academic
year (C2), a requirement that quietly costs €200 or six weeks is more dangerous than one that is
merely hard. **This is the most useful idea in 4.2 for us.**

**Rationale, 4.2.1.2.3 — four parts:**

1. the reason, with the parent requirement or trade study;
2. the assumptions it was written under;
3. the link to the ConOps;
4. any design constraint from earlier decisions. If the requirement names a method, the rationale
   says why.

**NASA's opening warning** — do "not rely solely on the requirements received" — assumes
requirements come from someone else. Ours do not. That is a cost, not a saving: no outside check.

## 2. The six validation steps — 4.2.1.2.4

Requirements are checked against the stakeholder expectations, the objectives and constraints, the
ConOps, and the success criteria. In NASA's order:

| # | Question | For us |
|---|---|---|
| 1 | Written correctly? | Appendix C.2 and C.3, run by the one who did not write it |
| 2 | Technically correct? | Traceability both ways to `NGO.md`, valid assumptions, essential |
| 3 | Satisfy stakeholders? | We are the stakeholder. Cheap, and weak |
| 4 | Feasible? | Catches an aircraft we cannot build for the money |
| 5 | Verifiable? | Catches a requirement we cannot test without a laboratory (C8) |
| 6 | Redundant or over-specified? | Every requirement unique and needed |

NASA also asks the team to show that **"the process for managing change in requirements is
established, documented, and communicated."** Settled decision 4 below is our answer.

## 3. Two smaller points

- **Requirements can come from non-obvious places.** If telemetry or logging is nearly free once the
  aircraft exists, add it early. Ours is already a required capability, ConOps §3.5, and the flight
  log is how MOE-1 is verified.
- **One "shall" per statement, as a complete sentence.** The rule most often broken, because two
  requirements in one sentence look efficient.

## 4. MOPs and TPMs

Source: NASA SEH, Section 4.2.1.2.5.

| Term | Meaning | Point of view |
|---|---|---|
| MOE | Measure of Effectiveness. Success as the stakeholder sees it | Stakeholder |
| MOP | Measure of Performance. Quantitative performance in the intended environment | Supplier |
| TPM | Technical Performance Measure. A critical characteristic **tracked over time** | Project management |

MOPs come from MOEs, usually several per MOE. TPMs are the small set plotted against the calendar, to
catch a problem before it becomes a failure.

**For us:** a separate MOP list would copy the pass/fail criteria. TPMs are cheap and new: total mass
and money spent, tracked by date. Adopted — item 8 below.

## 5. Appendix D — the verification matrix

Source: NASA SEH, Appendix D "Requirements Verification Matrix". Rev 2 p. 240, Table D-1 on p. 241.

What the text says: choose how each requirement will be verified **while the requirements are being
written**; only "shall" requirements go in the matrix; each has a unique ID; the matrix names the
source document of each requirement.

**Table D-1 itself is an image and was not read.** So we do not know NASA's column headings. The
column set in `REQUIREMENTS.md` is ours, and is labelled as ours.

## 6. Appendix C — the four checklists we run

Source: NASA SEH, Appendix C "How to Write a Good Requirement", C.1 to C.4.

### C.1 Correct terms

| Word | Meaning |
|---|---|
| **shall** | requirement |
| **will** | fact, or declaration of purpose |
| **should** | goal |

### C.2 Editorial checklist (product requirements)

- Form: "product ABC shall XYZ". Active voice.
- The same name for the product and its parts every time.
- Every number has a tolerance — less than, at least, plus or minus.
- No implementation. State the problem, not the solution. Test: ask "why do you need it?" The answer
  may be the real requirement.
- No descriptions of operations. A sentence starting "the operator shall…" is almost always one.

### C.3 General goodness checklist

Seven items. Two change what we do:

- **"The requirement is stated positively (as opposed to negatively, i.e., 'shall not')."** Some of
  our constraints are negative, for example C17. They must be turned into positive statements.
- **TBD versus TBR.** Use of TBD "should be minimized. It is better to use a best estimate for a value
  and mark it 'To Be Resolved' (TBR) with the rationale along with what should be done to eliminate
  the TBR, who is responsible for its elimination, and by when."

The other five: correct grammar; no typos; follows our template; has a rationale with its
assumptions; sits in the right section, not an appendix.

### C.4 Requirements validation checklist

Thirteen groups. The items that will cost us the most:

- **Clarity.** No "this" or "these". No "as appropriate", "etc.", "and/or", "but not limited to". One
  thought, one subject, one predicate.
- **Completeness.** Commonly forgotten areas: functional, performance, interface, environment
  (including test, transport, storage), facility, transportation, training, personnel, operability,
  safety, security, appearance, design.
- **Traceability.** "If it is not necessary, it is not a requirement." Test: "What is the worst that
  could happen if the requirement was not included?"
- **Performance.** "Are the tolerances overly tight?" Test: what is the worst that could happen if the
  tolerance were doubled or tripled?
- **Verifiability — the banned words:** *flexible, easy, sufficient, safe, ad hoc, adequate,
  accommodate, user-friendly, usable, when required, if required, appropriate, fast, portable,
  light-weight, small, large, maximize, minimize, robust, quickly, easily, clearly, other "ly" words,
  other "ize" words.*

The banned word list catches our own writing. G2-O4's "under control" has the same problem a deleted
objective had with "survivable" and "harmless": no test can be written for it. **Run the list as a
text search over `REQUIREMENTS.md` before the freeze, not by reading.**

## 7. MIT Session 2 — Requirements Definition

Source: MIT 16.842, Session 2, 55 slides, footer numbering. **Slide 8 cites page numbers from the 2007
NASA edition.** Ours is Rev 2. The appendix letters match; the pages do not.

**Slides 5 and 6 — the right pair of examples.** Mars Climate Orbiter: the contract specified SI
units, the requirement was flowed down — and **never verified**, so ground software sent pound-force
seconds and the spacecraft was lost. A correct requirement that is never verified is worth nothing.
The DC-3: a three-page request with five key numbers, and over 10,000 built. Few requirements can be
enough.

**Slide 9 — "shall" and "should".** "Shall" sets the hard boundaries. "Should" sets preferences that
count only after every "shall" is met. Settled decision 5 bans "should" for us.

**Slide 11 — requirements are not specifications.** Requirements say what the product does and how
well. Specifications say how it is built — form, materials, dimensions, drawings. `01_requirements/`
holds requirements; `03_design/` holds specifications. **A dimension in millimetres in
`REQUIREMENTS.md` means something went wrong.**

**Slide 19 — five types**, with a form worth copying for functional requirements: **actor – action
verb – object**. A constraint is "a requirement that cannot be traded off against cost, schedule or
performance". NASA 4.2.1.2.1 agrees.

| Type | Slide's example |
|---|---|
| Functional | "The TVC shall provide vehicle control about the pitch and yaw axes" |
| Performance | "The TVC shall gimbal the engine a maximum of 9 degrees, +/- 0.1 degree" |
| Constraint | "The TVC shall weigh less than 120 lbs" |
| Interface | "The TVC shall interface with the J-2X per conditions specified in [document]…" |
| Environmental | "The TVC shall use the vibroacoustic and shock loads defined in [document]…" |

**Slide 20 — a good requirement, and a good set.** Each one: clear, correct, feasible, not stating
how, unambiguous, singular, verifiable at its level. The set: no redundancy, consistent terms,
complete, **no conflicts**. The set checks are the ones we would forget.

**Slide 23 — margins.** Mass growth on vehicle programmes is typically 10 to 60%. The slide's
guideline margin falls from 30% at SRR to 5% before first operation. **Not adopted** — settled
decision 2 explains why. A first aircraft built by two students should expect the top of that range.

**Slide 27 — no requirements tool.** A plain document "works okay for smaller projects with dozens or
a few hundred requirements". A Markdown file is right for us. If our count ever passes a few hundred,
we have over-specified.

**Slide 29 — numbering and links.** Copy the linking idea, not the wording: two of its examples say
"must", and one puts a named scale inside the requirement. Both break C.1 and C.2.

**Slides 31–32 — allocation.** Four steps: define lower-level functions, create an architecture,
allocate performance, define interfaces. Then check that the lower set really guarantees the upper
one. And: *"Difficult to decompose reqts to lower levels while staying solution neutral."* Our
configuration is open, so **Stage 2 writes aircraft-level requirements only.**

**Slides 42–43 — the balloon.** Four pairs of radius and gas; one pair cannot lift 1000 kg. We
computed it and it agrees with the slide. **Two requirements can each look reasonable and be
impossible together.** Only arithmetic finds it. For us: a hover time and a mass.

**Slides 44–45 — common problems.** Implementation instead of requirement; wrong terms ("support",
"etc", "and/or"); bad grammar; unverifiable words; missing requirements; over-specifying. Slide 45 has
a grid of **twelve commonly forgotten areas**: functional, performance, interface, environment,
facility, transportation, training, personnel, reliability, maintainability, operability, safety.
Settled decision 3 uses it.

**Slides 49–51 — the SRR.** "Primarily a human / social peer-review process" that finds missing,
misstated or redundant requirements. After it, requirements go under configuration control and every
change needs approval. Slide 51: **requirements volatility** — the share added, removed or changed
per period — is generally bad.

## 8. HYDRO — the two rows about requirements

Source: HYDRO, Table 2 row "Focusing on Requirements", and Table 5 enabler 3.2.

| Row | Effectiveness in 2014 | Proposed change |
|---|---|---|
| Table 2 | "Low. Original requirements document was not attainable, read once and not looked at again." | "Set a few attainable requirements at each level of the architecture decomposition and ensure they are verified and validated." |
| Table 5, 3.2 | "…more of a 'wish list' than a rigorously analyzed and generated document." | "Set a few attainable requirements at each level of the architecture decomposition." |

The word to notice is **attainable**. A wish list has no failure mode, so nobody checks it, so it gets
abandoned. We pair every requirement with a test; but we have no outside reader to notice a drift
into a wish list.

## 9. Where our sources disagree

1. **Names of the verification methods.** MIT: examination, test, demonstration, analysis. NASA:
   test, analysis, **inspection**, demonstration. Same idea. **We use NASA's four**, and never mix the
   two words in one file.
2. **TBD.** NASA 4.1 allows TBD objectives until the trade study. Appendix C.3 says use TBR in
   requirements. Different documents — so nothing TBD enters `REQUIREMENTS.md`.
3. **How deep before the review.** MIT expects levels 1 and 2 at SRR. NASA allows a recursive
   process, and slide 32 admits staying solution-neutral is hard. Settled decision 1: two freezes.
4. **Few, or complete?** HYDRO says a few. NASA C.4 asks about twenty areas. Settled decision 3:
   count areas, not requirements.

---

## What Stage 2 changes for us

1. Every requirement has a rationale in NASA's four parts.
2. Requirements with a large effect on cost or schedule are flagged **KDR**.
3. TBD becomes TBR at the freeze: a best estimate, what closes it, and when. No owner field — with two
   people it carries no information.
4. Stage 2 requirements are aircraft level only. `REQUIREMENTS.md` says so at the top.
5. The C.4 banned word list is run as a text search before the freeze.
6. Verification method and pass/fail criterion stay in their own columns, never in the requirement
   sentence.
7. The requirements review uses NASA's six validation questions as its agenda, in order.
8. Two TPMs are tracked against the calendar from the freeze: total mass (`MASS_BUDGET.xlsx`) and
   money spent (`BOM.xlsx`).

## Settled

Each was decided on 2026-09-08, one at a time, after the options and evidence were laid out. The
longer argument for each is in the git history of this file, in the version before 2026-10-14.

**1. Two freezes, aircraft level first.** Freeze **L1**, the aircraft level, before the configuration
trade. Write **L2**, the subsystem level, after the trade; review it with the same six questions; then
freeze it. *Why:* a trade judged against requirements we can still edit is not a trade — we could
soften whatever made a layout score badly. And L2 needs an architecture to allocate to. *The
condition:* at freeze 1 we write down which L1 requirement numbers we expect the trade to re-open —
numbers only, no new values. *Rejected:* one freeze after the trade (nothing frozen during the biggest
decision); L1 freeze with no second review (L2 never checked as a set).

**2. No mass requirement at L1. Mass is a TPM.** No legal mass limit binds us: 25 kg is far above us
(C13), 250 g is a registration threshold we already pay for (C22), and 900 g was never ours (C21).
Mass is still constrained by physics — hover thrust must exceed weight, and the loop of mass, thrust,
motor, current and battery closes on itself. So mass is tracked as a TPM in `MASS_BUDGET.xlsx`, and
`REQUIREMENTS.md` states that **a derived mass target is the first thing the configuration trade must
produce.** The slide 23 margin schedule is quoted, not adopted.

**3. One requirement per area, not a number cap.** Walk the twelve areas of MIT slide 45. At most one
requirement per area, and **one written line for every area skipped**. A second requirement in an area
only when one sentence would need two "shall" verbs, with the reason written next to it. Walk the same
areas again at L2. *Why not a count:* at a count cap the next requirement gets merged into an existing
sentence, which breaks C.1 and C.2 and hides it from verification. The skip lines make a short list
defensible instead of careless. *Areas we would have missed:* **transportation** — the site is out of
town (C18), so span and whether the airframe comes apart matter; **training** — a licence (C23) is not
skill; **maintainability** — the planned crash (C4) assumes the aircraft can be rebuilt.

**4. A logged revision has six fields, in three tiers. No pull requests (changed 2026-10-14).** *Six fields:* the
requirement ID; old and new text; why now — what we learned, not "we changed our minds"; **what else
moves** — the field that gets skipped and matters most; whether the verification method or criterion
changes; the date. *Three tiers:* editorial (typo, same meaning) — commit straight to `main`;
modification — a GitHub issue with the six fields, the other person agrees in the issue, then the
commit names the issue; addition or deletion — the same, plus a re-check of decision 3's area walk.
*Why no pull request:* we work on one branch, `main`, and both push. A branch and an approval step
add work for two people who meet twice a week. The rule that matters — the other person sees the
change before it lands — is kept by the issue. *The cost:* git does not enforce it. A commit to a
frozen file with no issue is a broken rule, and is raised at the next session. *Still to agree:* what
happens if one of us is unreachable for several days.

**5. "Shall" only.** No "should", no "will" in `REQUIREMENTS.md`. *Why:* Appendix D puts only "shall"
in the verification matrix, so a "should" is never verified, and it breaks nothing when deleted — it
fails our own rule 3 on the day it is written. Preferences and tie-breakers go to `NGO.md` §5 as
design rules. Facts go in the rationale or the ConOps.

**6. Flat IDs — R1, R2, R3.** The ID encodes nothing; the parent is a field in the rationale. *The
evidence is our own repository:* the 2026-09-08 rewrite deleted a goal and several objectives, and
**not one flat constraint number moved**, while the objective IDs that encoded their goal all had to be
renumbered. **The more an ID encodes, the more ways it can become wrong** — and IDs are never reused,
so a wrong ID is permanent. *Rejected:* level prefix (redundant), area prefix (wrong after a
reclassification), goal prefix (the scheme that just failed).

**A safety note for the requirement set.** Safety is its own area in both C.4 and slide 45. Ours comes
from the off-nominal scenarios: propeller clearance in bench tests, LiPo charging and storage,
tethering on a first flight, and arming discipline. These are requirements with pass/fail criteria,
not advice in the build notes.

## Read and skipped

- **Isoperformance** (MIT Session 2, slides 33–41). Needs a validated dynamic model of the whole
  system. We will not have one (C8).
- **A separate MOP list.** Our pass/fail criteria are the same numbers.
- **NASA's waiver and configuration-control machinery** (Figure 4.2-2). Assumes an organisation.
- **The two journal papers named on slides 33 and 51.** Not read.
- **NASA Tables 4.2-1, 4.2-2, D-1 and Figures 4.2-2, 4.2-3.** Images; not read. See `REFERENCES.md`.
