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
| RDW | RDW — drone registration and pilot licence, Netherlands | https://www.rdw.nl/drone | Free, in Dutch. Readable. **Note: the correct path is `/drone`, not the longer `/particulier/voertuigen/drone/..` paths, which redirect** |
| ILT | Human Environment and Transport Inspectorate — the Dutch aviation authority for drones | https://english.ilent.nl/topics/aviation/drones-and-model-aircraft | Free, has an English version. Where a Specific category authorisation would be applied for |
| AP | ArduPilot Plane documentation (ArduPlane) | https://ardupilot.org/plane/ | Free. Versioned with the firmware — record which page and check it again when we pick a release |
| JLC | JLCPCB — help centre and product pages. Where we order circuit boards | https://jlcpcb.com | Free. Prices, shipping and tax rules change without notice, and several tables are published as images. Check the page on the day |
| CLIM | Current Results — Netherlands weather averages, compiled from the KNMI Klimaatviewer, normals for 1991–2020 | https://www.currentresults.com/Weather/Netherlands/average-netherlands-weather.php | Free. A secondary source that cites KNMI. The primary is the [KNMI Klimaatviewer](https://www.knmi.nl/klimaat-viewer), which we have **not** opened |
| ~~BENCH~~ | **Superseded 2026-09-08.** Benchmark aircraft for the performance goal, which was removed. Kept only so that older issues and commits can still be read. **Do not take a figure from these rows into any new work.** The SonicModell AR Wing Pro (fixed wing) and the DJI Mini 4K (multirotor) | https://www.getfpv.com/sonicmodell-ar-wing-pro-1000mm-wingspan-epp-fpv-flying-wing-rc-airplane-pnp-version.html · https://store.dji.com/product/dji-mini-4k | Retailer and manufacturer listings. Specifications change between production batches — re-check before freezing any G2 figure |
| OJ | Regulation (EU) 2019/947 as published in the **Official Journal of the European Union**, L 152, 11.6.2019 — CELEX 32019R0947. **Includes the full Annex** | https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32019R0947 | Free PDF. **This is the copy that closed Annex Part A**, which the EAR extract never reached. **It is the 2019 original and predates Amendments 3, 4 and 5** — see EAR24 |
| EAR24 | EASA Easy Access Rules for UAS, **July 2024 edition**, 468 pp. Incorporates all five amendments to 2019/947 and both to 2019/945 | https://drones.gov.cy/wp-content/uploads/2025/08/EAR_UAS_Jul24.pdf | Free PDF. **This is now our working copy of the law**, replacing the January 2021 extract and the 2019 Official Journal text |
| SITLM | ArduPilot `SITL_Models` — aircraft models for SITL, kept outside the main repository | https://github.com/ArduPilot/SITL_Models | Free. **A branch, not a release** — re-check against the firmware version we install |
| GZ | Gazebo (Garden / Harmonic), the open-source robotics simulator | https://gazebosim.org | Free, open source. Ubuntu first; Windows is best-effort |
| RF | RealFlight Evolution, RC flight simulator, on Steam | https://store.steampowered.com/app/2069310/RealFlight_Evolution/ | **Commercial.** Windows only. Price is region-dependent — check the Dutch store on the day |
| XFLR | XFLR5 — aerofoil, wing and plane analysis at low Reynolds numbers | https://www.xflr5.tech/xflr5.htm · https://sourceforge.net/projects/xflr5/ | Free, GPL. Windows, Linux, macOS |
| AVL | AVL — Athena Vortex Lattice, Mark Drela, MIT | https://web.mit.edu/drela/Public/web/avl/ | Free, GPL. Windows, Linux, macOS on both architectures |
| FREQ | *Regeling gebruik van frequentieruimte zonder vergunning en zonder meldingsplicht 2015*, BWBR0036378 — the Dutch list of licence-free radio use | https://wetten.overheid.nl/BWBR0036378/2025-07-01 | Free, in Dutch. Versioned: the link names the version in force from 1 July 2025. Check the "Geldend van" line on the day |
| RDI | Rijksinspectie Digitale Infrastructuur — the Dutch telecom inspectorate | https://www.rdi.nl | Free, in Dutch |

---

## How the stage notes are written

We read the notes, not the sources. So each notes file has to be short enough to read in one go and
correct enough to trust.

- **One file per stage:** `00_management/STAGE_N_NOTES.md`.
- **At most 480 lines.** Chosen: about one solo work block of reading. If it is wrong, a file either
  gets skimmed (too long) or drops things the next phase needs (too short) — the talk-through below
  shows which.
- **Only what changes a decision in the next phase.** Everything else read in a source is listed
  under "Read and skipped" at the end of the file, so a gap is a choice and not an accident.
- **Quotes are copied exactly, with their location.** A figure or table that could not be read is
  written down as not read.
- **Every file has a "What Stage N changes for us" section**, followed by "Read and skipped".
- **Spot check, once per stage.** One of us picks one quote or location from the file, opens the
  source and checks it. The date and the result go in the **Checks** line at the top of the file. If
  it is wrong, fix it and check a second one.
- **Talk-through, once per stage.** At the next shared session, each of us explains "What Stage N
  changes for us" without the file open. Anything neither of us can explain gets rewritten.
- **Stages 4 to 8 are tracked as GitHub issues**, each due before the work it feeds.

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
| EAR | Regulation (EU) 2019/947, **Article 4(1)(a)–(f)** — the six conditions for the Open Category | Constraints C13, C14, C15, C16, C12, C17. This one article is the source of almost every rule that binds JBV-01 | **Yes.** Read in full from the consolidated text |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(d)** — "the remote pilot keeps the unmanned aircraft in VLOS at all times except when flying in follow-me mode or when using an unmanned aircraft observer" | Constraint C15. It is why "long range" was removed from the Need | **Yes** |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(e)** — "the unmanned aircraft is maintained within 120 metres from the closest point of the surface of the earth, except when overflying an obstacle" | Constraint C16. A height ceiling we did not previously have | **Yes** |
| EAR | Regulation (EU) 2019/947, **Article 4(1)(b)** — MTOM below 25 kg | Constraint C13 | **Yes** |
| EAR | Regulation (EU) 2019/947, **definition (16)** — "'privately built UAS' means a UAS assembled or manufactured for the builder's own use, not including UAS assembled from sets of parts placed on the market as a single ready-to-assemble kit", read with Article 4(1)(a) | Constraint C12. It is the route that lets a home-built aircraft fly in the Open Category at all, and buying a complete kit would close it | **Yes** |
| EAR | Regulation (EU) 2019/947, **definitions (7) and (8)** — VLOS is "continuous unaided visual contact"; BVLOS is any operation not conducted in VLOS | Constraint C15. "Unaided" rules out using goggles or a screen to satisfy it | **Yes** |
| EAR | Regulation (EU) 2019/947, **recital (15)** — aircraft of 250 g or more present risks to security, so their operators must register | Constraint C22 | **Partly.** The recital gives the threshold and the reason. Article 14, which is the operative rule, was beyond the part of the PDF we could extract |
| EAR24 | "Incorporated amendments" table, **p. 5**; and **GM1 Article 2(16) Definitions**, ED Decision 2022/002/R | **The amendment history**: 2019/947 amended by 2020/639 (Amdt 1), 2020/746 (Amdt 2), 2021/1166 (Amdt 3), 2022/425 (Amdt 4) and **2024/1110 (Amdt 5, applicable 1/5/2025)**; 2019/945 by 2020/1058 and **2024/1108**. **The guidance on "privately built"** names our exact route — "(b) the assembly of the UAS from parts or sub-assemblies sold separately" — and confirms a ready-to-assemble kit is excluded. Constraint C12 | **Yes.** Read in full 2026-08-14 from the PDF. Article 4, UAS.OPEN.010, .020, .040 and .050(7) are unchanged from the 2019 text. **Two additions found:** AMC1 UAS.OPEN.040(1) — the distance formula, p. 282–283 — and the manufacturer's-instructions clause in UAS.OPEN.040(3) |
| OJ | **Annex, Part A — UAS.OPEN.010(2)–(3), UAS.OPEN.020(5)(a), UAS.OPEN.030(3), UAS.OPEN.040(1)–(4), UAS.OPEN.050(7)**; and **Article 14(5)(a)** | Constraints C18, C19, C20 and C21. **A3 is our subcategory**: privately built under 25 kg, 150 m from residential, commercial, industrial or recreational areas, no uninvolved person endangered in the range flown, and everyone present informed of the risks and explicitly agreeing to take part. Article 14(5)(a) adds an **80 J kinetic energy** trigger for registration alongside the 250 g one | **Yes.** Read 2026-08-14 from the Official Journal PDF, CELEX 32019R0947 |
| EAR | ~~Annex, Part A~~ — superseded by the OJ row above | Decided which subcategory a privately built aircraft above 250 g falls into, and therefore how far from people we must fly. Was the biggest open item in the project | **Closed 2026-08-14.** The EAR extract never reached this Annex; the Official Journal text did. See the OJ row |
| RDW | "Exploitantnummer aanvragen (registreren)" — sections "Wanneer is registreren verplicht", "Exploitantnummer aanbrengen op de drone", "Kosten". https://www.rdw.nl/drone/exploitantnummer-aanvragen | Constraint C22. Who must register, the €23 fee, and the rule that only the part of the number before the dash goes on the airframe | **Yes.** Read 2026-08-04 |
| ILT | "Vliegen buiten de Uniforme Daglicht Periode" — the opening two paragraphs. https://www.ilent.nl/onderwerpen/luchtvaart/drones-en-modelvliegtuigen/regels-voor-drones/specifiek-dronecategorie/buiten-udp | ConOps §4.0, the "light" row. Flying on sight in the dark is forbidden under VFR. Going outside the **Uniforme Daglicht Periode** needs an ILT *ontheffing*, the **Specific category**, and an *exploitatievergunning* — closed to us three times over | **Yes.** Read 2026-08-14; page modified 2026-07-15. **It does not define the UDP boundaries** — the "quarter of an hour either side" figure is from search results and is unverified |
| RDW | "Verzekeringen en vluchtvergunningen" — the sections "Verzekering verplicht" and "Vluchtvergunning verplicht". https://www.rdw.nl/drone/verzekeringen-en-vluchtvergunningen | Constraint C22 and the insurance question. Insurance is compulsory for private users only **from 20 kg**; RDW strongly advises insuring anyway and checking whether existing liability cover includes drones. No flight permit is needed in the Open Category | **Yes.** Read 2026-08-14. This page returned 503 on every earlier attempt |
| RDW | "Exploitantnummer verlengen" — the section "Kosten". https://www.rdw.nl/drone/exploitantnummer-verlengen | The **€13.00** renewal fee, and the rule that a lapsed number cannot be renewed — it needs a fresh €23 application | **Yes.** Read 2026-08-14 |
| RDW | "Vliegbewijs aanvragen" — sections "Alleen nodig vanaf 250 gram!", "Voorwaarden aanvraag vliegbewijs", "Kosten", "Soorten vliegbewijzen". https://www.rdw.nl/drone/vliegbewijs-aanvragen | Constraint C23. The A1/A3 licence, €10, valid 5 years, exam at a recognised Dutch flight school, carried on every flight, and that under 16 requires supervision | **Yes.** Read 2026-08-04 |
| ILT | "Flying drones in the Netherlands" — opening paragraph, and the line "all drone flights in the Netherlands must comply with Regulation [EU]2019/947". https://english.ilent.nl/topics/aviation/drones-and-model-aircraft/drones-eu-residents | Confirms the EU rules apply here in full, that an Open Category flight needs no permission, and that GoDrone shows the closed areas | **Yes.** Read 2026-08-04 |
| FREQ | **Artikel 2(3)**, **Artikel 3(c)**, **Bijlage 11 subcategorie 1, rows I and H1–H7**, and **subcategorie 2, row A** | `RULES.md` §F, RF1 to RF4. The power limits and conditions for the radio link | **Yes.** Read 2026-10-17, version in force from 2025-07-01. **Not read:** the model-control category in Bijlage 11 — the page stopped before it |
| RDI | "Vergunningvrij frequentiegebruik" — sections "Frequentiegebruik zonder vergunning" and "Voorwaarden". https://www.rdi.nl/onderwerpen/consumenten/vergunningvrij-frequentiegebruik | Names FREQ as the source of the conditions for licence-free radio use, and says most drones use these frequencies | **Yes.** Read 2026-10-17; page modified 2024-07-23 |
| RDW | "Verzekeringen en vluchtvergunningen" | Whether insurance is compulsory for us | **No.** The page returned 503 on every attempt |
| — | Consolidated rules file: `01_requirements/RULES.md` | Every rule that binds JBV-01, with its source and how well it is checked, in one place. **Start here instead of re-reading the sources** | — |
| AP | "QuadPlane Frame setup" — sections "Plane VTOL Motor Configurations", "Frame Types and Classes" (the `Q_FRAME_CLASS` and `Q_FRAME_TYPE` value lists), and "VTOL Motor Ordering" (Quad-X default, outputs 5 to 8). https://ardupilot.org/plane/docs/quadplane-frame-setup.html |. Proves a proven fallback exists in software and at configuration level, which is what the value rule's first question asks for | **Yes.** Page read directly. Note: the page calls Quad-X the *default* frame. It does not call it the easiest or the beginner option — that wording came from a search summary and was wrong |
| AP | "Tilt Rotor Planes" — the whole page. https://ardupilot.org/plane/docs/guide-tilt-rotor.html | Stage 3. ArduPilot's definition: a tilt-rotor is a VTOL aircraft where transition is done by *"tilting one or more rotors so that it provides forward thrust instead of upward thrust"*, as distinct from a tailsitter, where the fuselage and autopilot change orientation. Names the supported variants — front-two, all-four, tilt-tricopter with rear tilt for yaw, tilt-tricopter with **vectored yaw**, tilt-hexacopter, **tilt-wing** ("the entire wing rotates, instead of the motors"), **binary** tilt (two positions only) and **continuous** tilt (any angle). Key parameters `Q_TILT_ENABLE`, `Q_TILT_MASK`, `Q_TILT_TYPE` (0 continuous, 1 binary, 2 vectored, 3 bicopter), `Q_TILT_MAX`, `Q_TILT_RATE_UP` / `_DN`. Tilt-wing uses the same servo function 41 as a front tilt-rotor | **Yes.** Read 2026-09-08 |
| AP | "Tailsitter Planes" — the whole page. https://ardupilot.org/plane/docs/guide-tailsitter.html | Stage 3. ArduPilot's definition: tailsitters are *"any VTOL aircraft type that rotates the fuselage (and autopilot) when moving between forward flight and hover"* — and *"not all tailsitters land on their tails"*; belly landers exist. Split into **vectored** (rotors tilt independently of the fuselage) and **non-vectored** (fixed rotors, hover authority from large control surfaces in the prop wash, plus differential thrust if twin motor). Non-vectored splits again into Single/Dual Motor and **CopterMotor** (three or more motors, copter-like). `Q_TAILSIT_ENABLE` = 1, or 2 for copter-motor tailsitters with no control surfaces. Transition is set by `Q_TAILSIT_ANGLE` and the pitch rates `Q_TAILSIT_RAT_FW` / `_VT`. **During transitions pilot input is disabled** and attitude and throttle are controlled entirely by the autopilot. Centre of gravity matters in an extra axis | **Yes.** Read 2026-09-08 |
| AP | "Using SITL" — the section **"Frame Types"**, and the note under it. https://ardupilot.org/dev/docs/using-sitl-for-ardupilot-testing.html | **Closes the `NGO.md` §8 item "whether SITL simulates a tiltrotor or a tailsitter".** The Plane frame list includes `quadplane`, `plane-tailsitter`, `quadplane-cl84`, `quadplane-tilthvec`, `quadplane-tilttri`, `quadplane-tilttrivec`, `quadplane-tri`. The note is the important part: *"It is important to select the proper frame type. This not only loads the correct parameter set, but also selects the correct physics model … you cannot do that in SITL without having selected the exact QuadPlane frame type for the simulation to get the correct physics model."* The page calls its own list *"A partial listing"* and points at `sim_vehicle.py --help` for the current one | **Yes.** Read 2026-09-08 |
| AP | ArduPilot source, `Tools/autotest/pysim/vehicleinfo.json` — the ArduPlane section. https://raw.githubusercontent.com/ArduPilot/ardupilot/master/Tools/autotest/pysim/vehicleinfo.json | The full frame list, which is longer than the documentation page. VTOL frames: `quadplane`, `quadplane-tilt`, `quadplane-tilttri`, `quadplane-tilttrivec`, `quadplane-tilthvec`, `quadplane-tri`, `quadplane-cl84`, `quadplane-ice`, `quadplane-can`, `quadplane-PPP`, `plane-tailsitter`, `quadplane-copter_tailsitter`. Each carries its own default parameter file under `Tools/autotest/default_params/` | **Yes.** Read 2026-09-08 from the master branch. **A branch, not a release** — re-check against the firmware version we actually install |
| AP | ArduPilot source, `libraries/SITL/SIM_QuadPlane.cpp` — the frame-string parsing, and `libraries/SITL/SIM_Plane.cpp` — the tailsitter block. | **What SITL actually models.** `SIM_QuadPlane.cpp` maps `cl84` to `frame_type = "tilttri"` and sets motor 0 to `SERVO_RETRACT`, so **the CL-84 frame is simulated as a tilt-tricopter with a binary tilt servo — the wing is not rotated in the physics model.** `SIM_Plane.cpp` has no tilt handling at all; its tailsitter block adds prop-wash airspeed (`effective_airspeed += inputThrust * 20`), reduces angle of attack with thrust, and multiplies control-surface authority | **Yes.** Read 2026-09-08 from the master branch. **Tilt-wing has no distinct SITL physics model** |
| AP | ArduPilot source, `Tools/autotest/default_params/quadplane-cl84.parm` | The whole file is seven settings: `Q_FRAME_CLASS 7` (tricopter), `Q_TILT_ENABLE 1`, `Q_TILT_MASK 3` (front two motors), `Q_TILT_TYPE 1` (**binary**), `Q_TILT_RATE_DN` and `_UP` both 12.85 with the comment *"# 7 seconds to move servo"*, and `SERVO12_FUNCTION 41` (TiltMotorsFront) | **Yes.** Read 2026-09-08 |
| AP | "Simulators supported by SITL". https://ardupilot.org/dev/docs/simulation-2.html | The list of external flight dynamics models SITL can be driven by: Gazebo, RealFlight, X-Plane 10, JSBSim (*"a sophisticated open-source plane and multicopter simulator with no graphical interface"*), Webots (multicopter and rover only), PteroSim, Last Letter (*"fixed wing only"*), CRRCSim, MATLAB/Simulink, and a **generic JSON interface** *"designed to be easy to implement"* with Python and MATLAB examples — the route by which we could drive SITL from a physics model of our own | **Yes.** Read 2026-09-08 |
| AP · GZ | "SITL with Gazebo". https://ardupilot.org/dev/docs/sitl-with-gazebo.html, with https://gazebosim.org/docs/harmonic/install/ | The free route to simulating a transition. ArduPilot: *"We currently support Gazebo Garden and Gazebo Harmonic which are available for Ubuntu 20.04 (Focal) and 22.04 (Jammy) and macOS Big Sur (11), Monterey (12), and Ventura (13)."* **The plugin ships only an Iris quadcopter and a Zephyr wing** — the VTOL models are in SITLM below. Gazebo's own install page: officially supported are Ubuntu Jammy and Noble on amd64, and *"Platforms supported at best-effort include arm architectures, Windows and macOS."* On a Windows machine that means WSL2 | **Yes.** Both read 2026-09-08 |
| AP · RF | "SITL with RealFlight". https://ardupilot.org/dev/docs/sitl-with-realflight.html, with the Steam listing | The paid route. *"This simulator only runs on Windows and requires RealFlight version 8 or version 9. Note that RealFlight-X does not work with ArduPilot."* RealFlight Evolution on Steam lists at **$99.99 USD**, Windows 10 or 11, released 27 October 2022. **The euro price for the Netherlands has not been checked**, and against C3 this is roughly a third of the first-aircraft line | **Partly.** Pages read 2026-09-08; **the Dutch price is unchecked** |
| SITLM | `Gazebo/models/` and `RealFlight/Released_Models/QuadPlanes/`. https://github.com/ArduPilot/SITL_Models | **The models that make a transition simulable.** Gazebo: `alti_transition_quad` (lift+cruise VTOL), `bicopter` and `bicopter_with_ardupilot`, `skycat_tvbs` (Thrust Vectored Belly Sitter — a tailsitter), `swan_k1_hwing`, `skywalker_x8_quad`. RealFlight QuadPlanes: `Alti_Transition_QuadPlane`, **`Convergence_Tilt_Tri_QuadPlane`**, `Griffin`, `Skywalker_X8_QuadPlane`, a `Tailsitters` folder, `Titan_Cobra_VTOL`. The RealFlight folder is quality-gated — its README requires that *"The model has been verified by a third party as meeting these requirements and flying well"* | **Yes.** Folder listings read 2026-09-08. **No model has been run by us.** No tilt-wing model in either set |
| XFLR | Project page and SourceForge listing | **Chosen 2026-09-08 as one of our two aerodynamic tools.** *"an analysis tool for airfoils, wings and planes operating at low Reynolds Numbers"*, embedding *"XFoil's Direct and Inverse analysis capabilities"* plus lifting-line, vortex-lattice and 3D panel methods and stability analysis. The site's own warnings are worth keeping: *"Designed exclusively for the design and analysis of model aircraft"*, *"Not a professional product"*, released *"without any guarantee of any kind"*. **v6.62, files updated 2026-06-30**, Windows / Linux / macOS | **Partly.** Read 2026-09-08. **The SourceForge project also carries an "Abandoned" status label, which contradicts the update date. Maintenance status is unresolved** |
| AVL | Program page. https://web.mit.edu/drela/Public/web/avl/ | **Chosen 2026-09-08 as our second aerodynamic tool.** *"a program for the aerodynamic and flight-dynamic analysis of rigid aircraft of arbitrary configuration"* — extended vortex lattice for lifting surfaces, slender-body for fuselages. Gives forces and moments, **stability derivatives**, trim, and **eigenmode analysis**, which is the closest analytical statement we can make about G2-O3. **Version 3.40b, 18 April 2022.** Its own stated assumption is a *"rigid-body, quasi-steady aero model"* — so it is valid for cruise and **not** for a transition | **Yes.** Read 2026-09-08 |
| AP | **"QuadPlane Simulation"** — the whole page. https://ardupilot.org/plane/docs/quadplane-simulation.html | Constraint C9, assumption AS4, and the transition risk. *"A simple QuadPlane model is available in SITL, allowing you to test the features of the QuadPlane code without risking a real aircraft."* Started with `sim_vehicle.py -j4 -f quadplane --console --map`; defaults to a **Separate Lift Thrust (SLT) QuadPlane in quad configuration**; streams state to FlightGear on UDP 5503 for a view; accepts a **USB transmitter via the joystick module**; ships a sample VTOL take-off and landing mission, `Tools/autotest/Generic-Missions/KSFO-VTOL.txt` | **Yes.** Read 2026-08-14. **Two limits in the docs' own words:** the model is *simple*, so it validates no aerodynamics of ours; and the frame it names is **lift+cruise only** — tiltrotor and tailsitter simulation is not mentioned anywhere on this page |
| AP | "SITL Simulator (Software in the Loop)" — the "Overview" section. https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html | Constraint C9 and. SITL runs Plane, Copter or Rover on an ordinary PC with no hardware, built with a normal C++ compiler, taking sensor data from a flight dynamics model. Runs natively on Linux and Windows. The Overview lists the vehicle types it can simulate | **Yes.** Read 2026-08-09. **Important limit: the page lists "multi-rotor aircraft" and "fixed wing aircraft" separately and does not mention QuadPlane, V/STOL or transition anywhere.** Whether a transition can be simulated is **not** answered by this page. Do not claim it. Nobody here has run SITL |
| JLC | "EU Tax Reform July 2026 — Client FAQ" — the "Policy Overview" and "B2C shipments" sections, the "Before vs. After" comparison table, and the Q4 disbursement fee table, **Netherlands row**. https://jlcpcb.com/help/article/eu-customs-reform-faq | Constraint C6 and the €60 circuit board line in the C3 budget table. Gives the €3.00 temporary customs duty per HS code from 1 July 2026, and the Dutch carrier disbursement fees: UPS €16.05 min or €7.85 under €22, FedEx €15.00 min, DHL €16.50 min | **Yes.** Read 2026-08-09. The page itself was last updated 2026-08-07. Q6 also states the duty applies on top of IOSS VAT; Q10 states it is non-refundable on a returned B2C parcel |
| JLC | "JLCPCB Shipping Methods: Delivery Time & Global Options" — the paragraph "Tracking & Support for Air Mail Shipments". https://jlcpcb.com/help/article/shipping-methods-and-delivery-time | Lead time for. Customs clearance on air mail may take 5–7 working days with no tracking update, and JLCPCB asks customers to wait 20 working days before reporting a parcel missing | **Partly.** The table of shipping options and prices is published as an **image** and could not be read. We have no shipping figure |
| JLC | JLCPCB site navigation, "Mechanical Services" block — links to **JLC3DP** (3D printing, jlc3dp.com), **JLCCNC** (CNC machining and sheet metal, jlccnc.com) and **JLCMC** (mechatronic parts, jlcmc.com) | Constraint C6 and. Proves CNC machining, sheet metal and resin printing are available to us as ordered services in single quantities, so they were never capabilities we lacked | **Partly.** The links were read on the JLCPCB page on 2026-08-09. **No price, lead time or capability limit has been checked on any of the three sites.** Do not quote a figure from them |
| BENCH | SonicModell AR Wing Pro 1000 mm — the specification block on the retailer listing: **cruise speed 75–80 km/h at 5.5 A** with the SonicModell power combo, minimum speed 31 km/h, max 130 km/h; recommended battery **4S 3200–3500 mAh**; empty weight 340 g kit / 500 g PNP; max recommended take-off weight 1425 g | ~~**The fixed-wing benchmark for G2.**~~ **Superseded 2026-09-08 with the performance goal. O2.1, O2.3 and O2.5 no longer exist, and AS5a is deleted.** The cruise speed *paired with its current draw* is the whole reason we use this aircraft — it lets endurance be derived instead of guessed. Every figure in O2.1, O2.3 and O2.5 comes from it | **Yes.** Read 2026-08-14. **Manufacturer figures, not a logged flight.** Recorded as assumption AS5a. **Price in euros not checked** |
| BENCH | DJI Mini 4K **User Manual v1.0 EN**, the aircraft specification table. https://dl.djicdn.com/downloads/DJI_Mini_4K/DJI_Mini_4K_User_Manual_v1.0_EN.pdf | ~~The multirotor benchmark for O2.4.~~ **Superseded 2026-09-08 with the performance goal. O2.4 no longer exists.** **"Max Flight Time 31 mins (measured while flying at 17 kph in windless conditions)"** — so the cruise figure is **17 km/h = 4.7 m/s**. Also: max speed 16 m/s Sport / 10 m/s Normal / 6 m/s Cine; **max wind resistance 10.7 m/s**; MTOW 246 g | **Yes.** Read 2026-08-14 from DJI's own manual, not a summary. The 16 m/s is a Sport-mode maximum and is **not** the cruise speed |
| CLIM | "Annual Average Wind Speeds in the Netherlands" — the four regional tables. https://www.currentresults.com/Weather/Netherlands/wind-speed-annual.php | The 6 m/s steady wind figure in ConOps §4.0. (O2.2 is gone; the ConOps figure is not.) Inland places run 11.2 to 15.8 km/h annual mean — Venlo 11.2, Zwolle 11.5, Utrecht 13.0, Arnhem and Eindhoven 13.7, Rotterdam 15.8 — that is **3.1 to 4.4 m/s**. Coastal is far worse: Vlissingen 23.0 km/h, Hoek van Holland 26.3 | **Yes.** Read 2026-08-09. Note the page's own "strong gusts" threshold is >76 km/h (21 m/s) and inland sites see 4 to 10 such days a year. We would not fly then |
| CLIM | "January Temperature Averages for the Netherlands" — the four regional tables. https://www.currentresults.com/Weather/Netherlands/temperature-january.php | The 0 °C lower bound in ConOps §4.0. Inland January mean **low** is 0 to 1 °C and mean high 5 to 6 °C | **Yes.** Read 2026-08-09. **The 25 °C upper bound is ours, not from this page** — we did not read a July table. Cold is the binding case for battery capacity, so the sourced end is the one that matters |
| JLC | JLC3DP home page — the "3D Printing on Demand" service list, and the FAQ "Can I Order PCB and 3D Model Both Together?". https://jlc3dp.com/ | Constraint C6 and the trade-study filter. Floor prices and build times: SLA from $0.30 / 2 days, FDM-SLS-MJF from $1.00 / 3 days, **CNC from $5.00 / 3 days** (3-, 4- and 5-axis, aluminium, steel, copper, plastic, ±0.05 mm), SLM from $8.00 / 3 days, JLCMC from $0.10. **The FAQ confirms PCB and 3D printing orders can ship in one parcel**, so the €20–30 import overhead is per parcel, not per service | **Yes.** Read 2026-08-14. **"From" figures are floors, not our price** — same caveat as the $2 board. **Build time is manufacturing only**, excluding shipping and customs. **Whether CNC can join the same parcel is not stated** |
| JLC | "FR4 PCBs" — the line "FR4 PCBs starting from just $2" under "Why Choose JLCPCB FR4 PCBs?", and the capability table under "JLCPCB FR4 PCB Manufacturing Capabilities" | Board price floor, and the design rules a board of ours must obey. Minimum track width and spacing at 1oz is 0.10 / 0.10 mm for 1- and 2-layer. Minimum via hole 0.15 mm, diameter 0.25 mm | **Yes.** Read 2026-08-09. **Note: the widely repeated "$2 for five 100×100 mm boards" is not on this page.** The page says only "starting from just $2". The size and quantity that reach that price came from a search summary and are unconfirmed — same fault as the ArduPilot wording recorded in |

**Standing rule for this table.** A regulatory figure is only as good as the day it was checked.
Anything marked "No" above must not be written into a requirement, and must not be presented to a
reader as a fact.

**Jobs that need a browser, because a plain fetch cannot reach these pages. Two of the four are
closed, and neither of the two left blocks the requirements freeze.**

1. ~~Annex Part A of 2019/947 — the A1, A2, A3 subcategory conditions.~~ **Closed 2026-08-14.**
   Read from the Official Journal text, CELEX 32019R0947 — see the OJ row above. The answer is
   subcategory A3, carried in `RULES.md` §C and in constraints C18 to C21. **It does not block the
   requirements freeze.**
2. ~~The RDW registration page — cost, duration, and where the operator number must be marked.~~
   **Closed 2026-08-04 and 2026-08-14.** All three RDW rows above are marked read. Carried in
   `RULES.md` §B1 and constraint C22.
3. The NASA handbook tables that are published as images: Table D-1, Table 4.2-1, Table 4.2-2,
   Figure 4.2-2 and Figure 4.2-3. Not blocking, but we should see Table D-1 before the freeze.
4. The JLCPCB shipping options and price table, also an image. Not blocking. A real quote with a
   board outline would answer it better than the table would.

**And one job that needed no browser:** ~~the consolidated text we are working from is the January
2021 edition, so check what has been amended since.~~ **Closed 2026-08-14.** Our working copy is
now EAR24, the July 2024 edition, which carries all five amendments to 2019/947 and both to
2019/945. Article 4 and UAS.OPEN.040 are unchanged. Re-check again before the first flight, because
this only holds on the day it was read.

## Stage 2 — System requirements → `01_requirements/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 4.2 "Technical Requirements Definition" — 4.2.1.1 Inputs, the seven activities 4.2.1.2.1 to 4.2.1.2.7, 4.2.1.3 Outputs, and 4.2.2 Guidance | How requirements are derived and passed down the levels. 4.2.1.2.3 defines the Key Driving Requirement and the four parts of a rationale. 4.2.1.2.4 gives the six validation steps. 4.2.1.2.5 defines MOP and TPM |
| NASA | Section 4.2 — Figure 4.2-1 process flow, Figure 4.2-2 requirement flow and waiver ownership, Figure 4.2-3 parent/child flowdown, Table 4.2-1 "Benefits of Well-Written Requirements", Table 4.2-2 requirement metadata | **Not read.** All five are images on the nasa.gov page, and the handbook PDF text does not reach them. Needs a browser. Do not quote their contents |
| NASA | Appendix C "How to Write a Good Requirement" — C.1 Use of Correct Terms, C.2 Editorial Checklist, C.3 General Goodness Checklist, C.4 Requirements Validation Checklist | Four checklists. Every requirement we write goes through C.2 and C.3. C.3 gives the TBD-versus-TBR rule. C.4 gives the list of unverifiable words, which we run as a text search |
| NASA | Appendix D "Requirements Verification Matrix" — the page text. Rev 2 p. 240, Table D-1 on p. 241 | The rules: only "shall" requirements, each with a unique identifier and a named source document. **Table D-1 itself is an image and was not read.** The column set in `REQUIREMENTS.md` is therefore ours, not NASA's, until we can see it |
| MIT | Session 2 — "Requirements Definition" (PDF, 2.4 MB), 55 slides, footer numbering. Slide 9 shall/should, 11 requirements vs. specifications, 19 the five types, 20 attributes of an acceptable requirement, 23 mass margins, 27 document vs. database, 29 worked hierarchy, 31–32 allocation, 44–45 common problems, 46 the four verification methods, 49–51 SRR and volatility. Slides 33–41 isoperformance, read and skipped | Types of requirement, common mistakes, worked aerospace examples. Slide 23 is the mass margin schedule. Slide 27 says a plain document is the right tool at our size. **Slide 8 cites page numbers from the 2007 edition; ours is Rev 2 and the pages differ** |
| HYDRO | Table 2, row "Focusing on Requirements" | Their requirements document "was not attainable, read once and not looked at again". Their fix, quoted exactly: *set a few attainable requirements at each level of the architecture decomposition and ensure they are verified and validated.* The line that fits us best |
| HYDRO | Table 5, enabler 3.2 "Clarify, Derive, Prioritize Requirements Early and Often During Execution" | Why a list of wishes is worse than no requirements at all. Theirs "was more of a 'wish list' than a rigorously analyzed and generated document" |
| — | Notes taken from all of the above: `00_management/STAGE_2_NOTES.md` | Stage 2 is read and written up, with the open items it leaves. Start there instead of reading the sources again |

## Stage 3 — Architecture and configuration selection → `02_concept/`

| Source | Exact location | What we need it for |
|--------|----------------|---------------------|
| NASA | Section 4.3 "Logical Decomposition" | How to split the aircraft into functions before we choose hardware |
| NASA | Section 4.4 "Design Solution Definition" | How to turn the chosen architecture into a specification we can build from |
| MIT | Session 4 — "System Architecture and Concept Generation" (PDF, 3.1 MB) | How to produce a full set of concepts instead of defending the first idea we like |
| MIT | Session 5 — "Concept Selection and Tradespace Exploration" (PDF, 2.0 MB), 39 pages. **The OCW page and the PDF give this deck two different titles** — the PDF's own resource title is "Tradespace Exploration and Concept Selection". Same file, one deck. Pages 12 to 17 are images with no readable text | Trade study method for the configuration decision. Page 4 the screening-then-selection pipeline, page 8 the five Pugh steps, page 18 the critique of Pugh, pages 19–22 utility, pages 28–36 dominance and the Pareto front, page 37 the PDR content list, page 38 the summary by phase |
| NASA | **Section 6.8 "Decision Analysis"** — 6.8.1.1 inputs and the four conditions warranting formal analysis, 6.8.1.2.1 to 6.8.1.2.7, and 6.8.1.3.1 the ten-item decision report. https://www.nasa.gov/reference/6-8-decision-analysis/ | **Section 4.4 sends the reader here twice and it was missing from this table.** It carries the trade study process itself: mandatory versus enhancing criteria (*"An option that does not meet mandatory criteria should be disregarded"*), the differentiation test, the trade tree for pruning, normalisation with *"operational definitions"*, the robustness-of-ranking check, and the ten items a decision report must contain — which is the structure of `02_concept/TRADE_STUDY.md`. 6.8.2 lists the methods, all of them in the Expanded Guidance we do not have |
| HYDRO | Table 5, enabler 3.3 "Front Load Architectural Design and Implementation" | They never fixed their powertrain architecture early and it cost them. Their fix: define the architecture, check it with calculations and a small experiment, and test anything new in a simple form first |
| — | Notes taken from all of the above: `00_management/STAGE_3_NOTES.md` | Stage 3 is read and written up, with the ten settled decisions. Start there instead of reading the sources again |

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
