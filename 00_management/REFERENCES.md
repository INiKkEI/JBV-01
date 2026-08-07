# References

The sources we are working from, sorted by V-model stage. For each one we write what it is
good for and where inside it to look. This way we do not read 300 pages again to find one
checklist.

---

## Source key

| ID | Source | Link | Access |
|----|--------|------|--------|
| REQI | Reqi — "What Is Systems Engineering V Model?" (Mike Wayne) | https://reqi.io/articles/what-is-systems-engineering-v-model | Free, ~11 min |
| REQI-V | Reqi — "The V diagram, explained arm by arm" | https://reqi.io/articles/system-engineering-v-diagram-the-vee | Free |
| MIT | MIT OCW 16.842 *Fundamentals of Systems Engineering*, Fall 2015 (Olivier de Weck), Aeronautics & Astronautics | https://ocw.mit.edu/courses/16-842-fundamentals-of-systems-engineering-fall-2015/pages/lecture-notes/ | Free PDFs, graduate level |
| NASA | NASA Systems Engineering Handbook, NASA/SP-2016-6105 Rev 2 | https://explorers.larc.nasa.gov/2023ESE/pdf_files/NASA04.%20SysEng%20Handbook%20(NASA_SP-2016-6105%20Rev%202).pdf | Free PDF, 300+ pp. Also available section by section as HTML at nasa.gov/reference/ |
| HYDRO | Sutherland, Kamiyama, Aoyama, Oizumi — "Systems Engineering and the V-Model: Lessons from an Autonomous Solar Powered Hydrofoil", IMDC 2015 | https://www.joshuasutherland.com/wp-content/uploads/2020/02/2015_Sutherland-et-al_IMDC2015-v1.7.pdf | Free PDF, ~12 pp |
| GH | GitHub Docs | https://docs.github.com | Free. Changes without notice — check the page, do not quote from memory |
| EAR | EASA Easy Access Rules for Unmanned Aircraft Systems — consolidated text of Regulations (EU) 2019/947 and (EU) 2019/945, **January 2021 edition**, 309 pp. | https://drones.gov.cy/wp-content/uploads/2021/02/Easy-Access_Rules_for_Unmanned_Aircraft_Systems_January_2021.pdf | Free PDF. **This is our working copy of the law.** Dated January 2021 — the regulation has been amended since, so re-check before the requirements freeze |
| EASA | EASA — Open category FAQ | https://www.easa.europa.eu/en/the-agency/faqs/open-category | Free. **Built by JavaScript — a plain fetch returns an empty page.** Superseded for our purposes by EAR above, which is the actual text |
| RDW | RDW — drone registration and pilot licence, Netherlands | https://www.rdw.nl/drone | Free, in Dutch. Readable. **Note: the correct path is `/drone`, not the longer `/particulier/voertuigen/drone/...` paths, which redirect** |
| ILT | Human Environment and Transport Inspectorate — the Dutch aviation authority for drones | https://english.ilent.nl/topics/aviation/drones-and-model-aircraft | Free, has an English version. Where a Specific category authorisation would be applied for |
| AP | ArduPilot Plane documentation (ArduPlane) | https://ardupilot.org/plane/ | Free. Versioned with the firmware — record which page and check it again when we pick a release |

---

## Stage 0 — Before we start

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| REQI | Section "The Two Arms of the V: Every Definition Paired With Its Test" | The pairing table. It also follows one requirement ("the aircraft shall stop within 1,500 m") down the left arm and back up the right. Start here |
| REQI | Section "How to Read the Systems Engineering V Model Diagram" — three subsections: "Down the left side: decomposition and definition", "At the base: build", "Up the right side: integration and recomposition" | How to read the diagram, stage by stage |
| REQI | Section "Validation vs. Verification" | The difference, in two paragraphs. If we mix these two up early, everything after that is wrong |
| REQI | Section "Limitations of the V-Model" | What the V does not cover |
| MIT | Session 1 — "Systems Engineering Overview and Stakeholder Analysis" (PDF, 4.8 MB) | Overview of the whole subject, written for aerospace |
| HYDRO | Section "The V-Model" — body text, and Figure 5 | The four V views (Basic / Development / Assurance / Dynamic) are named in the body text, citing Scheithauer & Forsberg 2013. They are not in a figure. Figure 4 is a simplified single V from INCOSE 2011. Figure 5 gives NASA's formal definitions of verification and validation |
| — | Notes taken from all of the above: `00_management/STAGE_0_NOTES.md` | Stage 0 is read and written up. Start there instead of reading the sources again |

## Stage 1 — Mission needs and concept of operations → `01_requirements/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 4.1 "Stakeholder Expectations Definition" — 4.1.1.1 Inputs, the ten activities 4.1.1.2.1 to 4.1.1.2.10, and 4.1.1.3 Outputs. Figure 4.1-1 process flow, Table 4.1-1 stakeholder identification, Figure 4.1-2 information flow, Figure 4.1-3 example Lunar Sortie DRM | How to collect and write down what the aircraft must do, before we write requirements. Note the boxed comparison "Concept of Operations vs. Operations Concept" — we want the first one |
| NASA | Section 4.1.1.2.3 "Identify Needs, Goals, and Objectives" | The definitions of need, goal and objective, the four criteria for an objective, and the two lines that matter most to us: the need statement is singular, and a TBD objective is allowed until the trade study happens |
| NASA | Section 4.1.1.2.6 "Analyze Expectations Statements for Measures of Effectiveness" | What an MOE is, and the test for whether something is one. These are the validation criteria Stage 0 said we were missing |
| NASA | Appendix S "Concept of Operations Annotated Outline" — sections 1.0 to 8.0 plus Appendix A Acronyms and Appendix B Glossary. Section 6.0 gives the [DRM-0100] scenario labelling advice | A ConOps outline we can fill in directly. The most useful ready-made thing in the handbook for us |
| MIT | Session 1 — slides 30 to 54 (footer numbering). Slide 35 defines stakeholder, slide 36 is the table of stakeholder types against typical expectations, slides 37–38 ConOps and the Lunar DRM example, slide 41 benefits, slides 42–54 Stakeholder Value Network analysis | How to find stakeholders and map what they value. Slide 36 is the template we use for our own stakeholder list. Slides 42–54 read and skipped on purpose — too heavy for two people |
| HYDRO | Table 3, enabler 1.2 "Establish the Value of the End Product or System to the Customer". Table 3 has one row only. Also the body paragraph beginning "Value:" in the section "Looking Beyond the V-Model for Development Improvements" | Their team had two different ideas of value at the same time — win the race, or learn as much as possible — and never chose. We have the same problem between portfolio value and learning. We need to settle it early. Warning: the "Flow:" paragraph in the same section misnames Table 3; the Flow enablers are in Table 5 |
| HYDRO | Table 8, enabler 6.3 — the words "Survey team members to understand their skills and aspirations" | Same conversation as enabler 1.2. Defining value and mapping what each of us wants to learn is one conversation, not two |
| — | Notes taken from all of the above: `00_management/STAGE_1_NOTES.md` | Stage 1 is read and written up, with the open items it leaves. Start there instead of reading the sources again |

## Regulatory and technical sources — used across every stage

These are not method sources. They are the rules we must obey and the hardware and software we
will actually use. They are listed separately because they change on their own schedule, and a
figure from one of them is only good on the day it was checked.

| Source | Exact location | What we need it for | Checked? |
|--------|----------------|---------------------|----------|
| EAR | Regulation (EU) 2019/947, **Article 4(1)(a)–(f)** — the six conditions for the Open Category | Constraints C6, C8, C11, C12, C13, C14. This one article is the source of almost every rule that binds JBV-01 | **Yes.** Read in full from the consolidated text |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(d)** — "the remote pilot keeps the unmanned aircraft in VLOS at all times except when flying in follow-me mode or when using an unmanned aircraft observer" | Constraint C11. It is why "long range" was removed from the Need | **Yes** |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(e)** — "the unmanned aircraft is maintained within 120 metres from the closest point of the surface of the earth, except when overflying an obstacle" | Constraint C12. A height ceiling we did not previously have | **Yes** |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(b)** — MTOM below 25 kg | Constraint C6 | **Yes** |
| EAR | Regulation (EU) 2019/947, **definition (16)** — "'privately built UAS' means a UAS assembled or manufactured for the builder's own use, not including UAS assembled from sets of parts placed on the market as a single ready-to-assemble kit", read with Article 4(1)(a) | Constraint C13. It is the route that lets a home-built aircraft fly in the Open Category at all, and buying a complete kit would close it | **Yes** |
| EAR | Regulation (EU) 2019/947, **definitions (7) and (8)** — VLOS is "continuous unaided visual contact"; BVLOS is any operation not conducted in VLOS | Constraint C11. "Unaided" rules out using goggles or a screen to satisfy it | **Yes** |
| EAR | Regulation (EU) 2019/947, **recital (15)** — aircraft of 250 g or more present risks to security, so their operators must register | Constraint C7 | **Partly.** The recital gives the threshold and the reason. Article 14, which is the operative rule, was beyond the part of the PDF we could extract |
| EAR | **Annex, Part A — UAS.OPEN.020, .030, .040** (subcategories A1, A2, A3) | Constraint C6a and objective O1.4. Decides which subcategory a privately built aircraft above 250 g falls into, and therefore how far from people we must fly | **No.** Beyond the extracted portion of the PDF. **This is the biggest open regulatory question** |
| RDW | "Exploitantnummer aanvragen (registreren)" — sections "Wanneer is registreren verplicht", "Exploitantnummer aanbrengen op de drone", "Kosten". https://www.rdw.nl/drone/exploitantnummer-aanvragen | Constraint C7. Who must register, the €23 fee, and the rule that only the part of the number before the dash goes on the airframe | **Yes.** Read 2026-08-04 |
| RDW | "Vliegbewijs aanvragen" — sections "Alleen nodig vanaf 250 gram!", "Voorwaarden aanvraag vliegbewijs", "Kosten", "Soorten vliegbewijzen". https://www.rdw.nl/drone/vliegbewijs-aanvragen | Constraint C15. The A1/A3 licence, €10, valid 5 years, exam at a recognised Dutch flight school, carried on every flight, and that under 16 requires supervision | **Yes.** Read 2026-08-04 |
| ILT | "Flying drones in the Netherlands" — opening paragraph, and the line "all drone flights in the Netherlands must comply with Regulation [EU]2019/947". https://english.ilent.nl/topics/aviation/drones-and-model-aircraft/drones-eu-residents | Confirms the EU rules apply here in full, that an Open Category flight needs no permission, and that GoDrone shows the closed areas | **Yes.** Read 2026-08-04 |
| RDW | "Verzekeringen en vluchtvergunningen" | Whether insurance is compulsory for us | **No.** The page returned 503 on every attempt |
| — | Consolidated rules file: `01_requirements/RULES.md` | Every rule that binds JBV-01, with its source and how well it is checked, in one place. **Start here instead of re-reading the sources** | — |
| AP | "QuadPlane Frame setup" — sections "Plane VTOL Motor Configurations", "Frame Types and Classes" (the `Q_FRAME_CLASS` and `Q_FRAME_TYPE` value lists), and "VTOL Motor Ordering" (Quad-X default, outputs 5 to 8). https://ardupilot.org/plane/docs/quadplane-frame-setup.html | Decision D3. Proves a proven fallback exists in software and at configuration level, which is what the value rule's first question asks for | **Yes.** Page read directly. Note: the page calls Quad-X the *default* frame. It does not call it the easiest or the beginner option — that wording came from a search summary and was wrong |
| AP | "Tilt Rotor Planes". https://ardupilot.org/plane/docs/guide-tilt-rotor.html | Stage 3, if the trade picks a tiltrotor | Linked from the frame setup page. Not yet read |
| AP | "Tailsitter Planes". https://ardupilot.org/plane/docs/guide-tailsitter.html | Stage 3, if the trade picks a tailsitter | Linked from the frame setup page. Not yet read |

**Standing rule for this table.** A regulatory figure is only as good as the day it was checked.
Anything marked "No" above must not be written into a requirement, and must not be presented to a
reader as a fact.

**Two jobs left that need a browser, because a plain fetch cannot reach these pages:**

1. Annex Part A of 2019/947 — the A1, A2, A3 subcategory conditions. Until we have these we do not
   know how far from people we must fly, and we cannot settle whether the 900 g figure applies to
   us at all.
2. The RDW registration page — cost, duration, and where the operator number must be marked.

**And one job that needs no browser:** the consolidated text we are working from is the January
2021 edition. Check what has been amended since, before the requirements freeze.

## Stage 2 — System requirements → `01_requirements/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 4.2 "Technical Requirements Definition" | How requirements are derived and passed down the levels |
| NASA | Appendix C "How to Write a Good Requirement" — C.1 Use of Correct Terms, C.2 Editorial Checklist, C.3 General Goodness Checklist, C.4 Requirements Validation Checklist | Four checklists. Every requirement we write goes through C.2 and C.3 |
| NASA | Appendix D "Requirements Verification Matrix" | The table that links each requirement to its verification method. We copy this structure into `REQUIREMENTS.md` |
| MIT | Session 2 — "Requirements Definition" (PDF, 2.4 MB) | Types of requirement, common mistakes, worked aerospace examples |
| HYDRO | Table 2, row "Focusing on Requirements" | Their requirements document "was not attainable, read once and not looked at again". Their fix: *set a few attainable requirements at each level of the decomposition and ensure they are verified and validated.* The line that fits us best |
| HYDRO | Table 5, enabler 3.2 "Clarify, Derive, Prioritize Requirements Early and Often" | Why a list of wishes is worse than no requirements at all |

## Stage 3 — Architecture and configuration selection → `02_concept/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 4.3 "Logical Decomposition" | How to split the aircraft into functions before we choose hardware |
| NASA | Section 4.4 "Design Solution Definition" | How to turn the chosen architecture into a specification we can build from |
| MIT | Session 4 — "System Architecture and Concept Generation" (PDF, 3.1 MB) | How to produce a full set of concepts instead of defending the first idea we like |
| MIT | Session 5 — "Concept Selection and Tradespace Exploration" (PDF, 2.0 MB) | Trade study method for the tiltrotor / tailsitter / lift+cruise / tilt-wing decision |
| HYDRO | Table 5, enabler 3.3 "Front Load Architectural Design and Implementation" | They never fixed their powertrain architecture early and it cost them. Their fix: define the architecture, check it with calculations and a small experiment, and test anything new in a simple form first |

## Stage 4 — Subsystem and component design → `03_design/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| MIT | Session 6 — "Design Definition and Multidisciplinary Optimization" (PDF, 2.6 MB) | How to handle design variables that affect aero, structures, and propulsion at the same time |
| MIT | Session 8 — "Systems Integration and Interface Management" (PDF, 2.1 MB) | How to define interfaces. Read it during design. Leaving it until integration is the mistake |
| NASA | Appendix L "Interface Requirements Document Outline" | How to write subsystem interfaces down before they surprise us |
| HYDRO | Figures 10 and 11, section "Reviewing and Improving Activity on the Development-V" | Their work products had no owner and no completion date. Figure 11 is the corrected version with both |

## Stage 5 — Build → `04_build/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 5.1 "Product Implementation", incl. Figure 5.1-1 process flow | How to decide between buy, build, and reuse, and what each option needs as input |
| HYDRO | Section "Reviewing and Improving Activity on the Dynamic-V", Figures 8 and 9 | Every iteration on their project happened only after something failed. Figure 9 is the same project with a prototype loop planned from the start. We want ours planned |

## Stage 6 — Component and subsystem verification → `05_verification/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 5.3 "Product Verification", incl. Figure 5.3-1 process flow and the five verification activities | Prepare, perform, analyse, report, capture. Every bench test follows this loop |
| NASA | Appendix I "Verification and Validation Plan Outline" — https://www.nasa.gov/reference/appendix-i-verification-and-validation-plan-outline/ | We cut this down into the structure of `TEST_LOG.md`. Note: the contents list on nasa.gov gives this appendix the wrong name, "Integration Plan Outline". The page itself is correct |
| MIT | Session 9 — "Verification and Validation" (PDF) | The four verification methods — test, analysis, inspection, demonstration — and when to use each |
| HYDRO | Figures 13–16, section "Reviewing and Improving Activity on the Assurance-V" | A month by month V&V schedule for a small student vehicle. The closest thing we have to a template for our own test planning |

## Stage 7 — Integration → `05_verification/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 5.2 "Product Integration", incl. subsection 5.2.1.2.1 "Prepare to Conduct Product Integration" | How to plan the order of integration |
| NASA | Appendix H "Integration Plan Outline" | Outline for an integration plan |
| MIT | Session 8 — "Systems Integration and Interface Management" | Second read, this time from the integration side |
| HYDRO | Figure 12 vs. Figure 15 | They pushed integration and verification into the last few weeks. Figure 15 shows what it looks like when the work is spread out |

## Stage 8 — System verification and validation → `06_flight/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 5.4 "Product Validation" | How to show the aircraft does what we set out to build, not only what the specification says |
| NASA | Appendix E "Creating the Validation Plan with a Validation Requirements Matrix" | Format of the validation matrix |
| NASA | Section 5.5 "Product Transition" | Handover and operational readiness |
| MIT | Session 10 — "Commissioning and Operations" (PDF, 3.4 MB) | How to plan first operation. For us that is the first hover and the first transition |
| NASA | Appendix T "Systems Engineering in Phase E" | How to operate the aircraft once it is built |

## Cross-cutting — planning, iteration, and keeping ourselves honest

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| HYDRO | Figure 7 "Knowledge / Skill growth for 2014 development" | The Knowledge Growth Curve. They learned most of what they needed only in the final weeks. We start with no V/STOL background, so this is the mistake we are most likely to repeat |
| HYDRO | Conclusions, "Product Development Improvements" bullets | Six clear process changes from a real student project review. The shortest useful read in this list |
| HYDRO | Table 1 "NASA Key Enablers", rows "Capability Maturity" and "Design Robustness Mindset" | The two areas they rated themselves lowest on, with the fixes they propose |
| HYDRO | Table 4, enablers 2.3, 2.4, 2.6 | Doing work early, not building what is not needed, and choosing metrics that mean something |
| HYDRO | Table 5, enabler 3.5 and Table 8, enabler 6.3 | How sub-teams should communicate, and giving every deliverable a named owner. This applies directly to a team of two |
| NASA | Appendix J "SEMP Content Outline" | Outline of a Systems Engineering Management Plan. Much heavier than we need. Read the section headings only |
| MIT | Session 11 — "Lifecycle Management" (PDF, 4.2 MB) | Lifecycle view, cost and schedule |
| GH | "About large files on GitHub" — sections "File size limits", "Repository size limits", "Removing files from a repository's history". https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github | The size limits we work to: 50 MiB warning, 100 MiB block, repository ideally under 1 GB. Also why deleting a large file in a later commit does not shrink the repository. This is the reason `.gitignore` blocks video. Checked against the page |
| GH | "Removing sensitive data from a repository". https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository | What to do if something private reaches a commit. The repository is public, so read this before it is needed, not after |

---

## Why we are not following all of this exactly

Almost every text on the V-model assumes a large programme. It assumes formal design reviews,
a large set of documents, and a customer outside the team. We have none of these.

Two things do apply to us. First, each requirement is paired with the test that verifies it.
Second, verification is planned before anything is built.

Two things do not apply. The formal review meetings and the full document set. If we copied
those, they would take the whole year and we would have no aircraft.

HYDRO is the exception, and that is why it appears at almost every stage above. It is a student
team, about our size, and it says openly what went wrong. Their main finding was that
requirements were written once, never looked at again, and never verified. That is the mistake
we are most likely to repeat.
