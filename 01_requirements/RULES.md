# Rules for flying JBV-01 in the Netherlands

Every rule we must obey, with its source and how well we have checked it. This file feeds ConOps
section 2.1 "Applicable Documents" and constraints **C12 to C23** in `NGO.md`.

Rules here are numbered **EU1–EU7**, **B1–B2**, **A3-1–A3-3** and **NL1–NL4**. Note that **A1, A2 and A3 always mean the Open
Category subcategories** in this project, because that is what they mean in the regulation.

**First checked 2026-08-04. Re-checked against the July 2024 consolidated text on 2026-08-14.**
Rules change. Check again before the requirements freeze, and again before the first flight.

## How to read the status column

| Status | Means |
|---|---|
| **Confirmed** | We read it in the source document ourselves |
| **Partly** | We read part of it, or the source is one step removed |
| **Not checked** | We have only seen it in a search result or a hobby website. **Do not rely on it** |

---

## A. EU rules — the Open Category

Source: **Regulation (EU) 2019/947**, read in the EASA consolidated text *Easy Access Rules for
Unmanned Aircraft Systems*, **July 2024 edition**, which carries all five amendments. The January
2021 edition and the Official Journal original (CELEX 32019R0947) were read first and are kept below
as history.

> **Re-checked against the current law on 2026-08-14.** The regulation has been amended **five
> times**, and we have now read the **July 2024 edition**, which incorporates all of them. Article 4,
> UAS.OPEN.010, .020, .040 and .050(7) are **unchanged** from what this file already said. Two
> things were added and both are recorded below: the distance formula in §C, and the
> manufacturer's-instructions clause in UAS.OPEN.040(3). The amendment history, for the record:
>
> | Amending act | | Applicable from |
> |---|---|---|
> | 2019/947 | initial issue | 31/12/2020 |
> | 2020/639 | Amendment 1 | 2/6/2020 |
> | 2020/746 | Amendment 2 | 6/6/2020 |
> | 2021/1166 | Amendment 3 | 5/8/2021 |
> | 2022/425 | Amendment 4 | 4/4/2022 |
> | **2024/1110** | **Amendment 5** | **1/5/2025** |
>
> Delegated Regulation 2019/945 has also been amended twice, most recently by **2024/1108**,
> also applicable 1/5/2025.
>
> **"Confirmed" in this file now means confirmed against the July 2024 edition**, except the RDW
> rows in §B, which are Dutch pages checked separately and carry their own dates.

- Read first, now history: [Easy Access Rules for UAS, January 2021 (PDF, 309 pp.)](https://drones.gov.cy/wp-content/uploads/2021/02/Easy-Access_Rules_for_Unmanned_Aircraft_Systems_January_2021.pdf)
- **The edition we now work from:** [Easy Access Rules for UAS, July 2024 (PDF, 468 pp.)](https://drones.gov.cy/wp-content/uploads/2025/08/EAR_UAS_Jul24.pdf) — incorporates all five amendments
- The law itself: [Regulation (EU) 2019/947 on EUR-Lex](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32019R0947) and [Delegated Regulation (EU) 2019/945 on EUR-Lex](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32019R0945)

The Dutch inspectorate ILT states plainly that all drone flights in the Netherlands must comply
with Regulation (EU) 2019/947, and that a flight in the Open Category needs no permission —
[Flying drones in the Netherlands, ILT](https://english.ilent.nl/topics/aviation/drones-and-model-aircraft/drones-eu-residents).

| # | Rule | Where | Status |
|---|---|---|---|
| EU1 | The UAS must belong to a class in Delegated Regulation (EU) 2019/945, **or be privately built**, or meet Article 20 | Art. 4(1)(a) | **Confirmed** |
| EU2 | Maximum take-off mass **below 25 kg** | Art. 4(1)(b) | **Confirmed** |
| EU3 | Keep the aircraft a safe distance from people. **Never fly over assemblies of people** | Art. 4(1)(c) | **Confirmed** |
| EU4 | Keep the aircraft in **visual line of sight at all times**, except in follow-me mode or with an unmanned aircraft observer | Art. 4(1)(d) | **Confirmed** |
| EU5 | Stay **within 120 m of the closest point of the surface of the earth**, except when overflying an obstacle | Art. 4(1)(e) | **Confirmed** |
| EU6 | Carry no dangerous goods. **Drop nothing** | Art. 4(1)(f) | **Confirmed** |
| EU7 | If any of the above is not met, the flight is in the **Specific** category and needs an operational authorisation | Art. 5(1) | **Confirmed** |

### Two definitions that decide things for us

**"Privately built UAS"** — "a UAS assembled or manufactured for the builder's own use, **not
including UAS assembled from sets of parts placed on the market as a single ready-to-assemble
kit**". Definition (16). **Confirmed.**

This is the route that lets JBV-01 fly at all, because a home-built aircraft cannot carry a class
marking. Buying one complete ready-to-assemble kit would close it.

**Guidance that puts our route beyond doubt.** GM1 Article 2(16), ED Decision 2022/002/R, read
2026-08-14 in the July 2024 edition. A UAS counts as privately built when it is made or assembled
by the operator for their own use and **not placed on the market**, and "assembled or manufactured"
means one of:

- (a) the complete manufacturing of the UAS, or at least most of it;
- **(b) the assembly of the UAS from parts or sub-assemblies sold separately;**
- (c) the modification of a class C4 UAS (aeromodel).

**(b) is exactly what we are doing**, and it is now written down rather than assumed. Two further
lines from the same guidance: changing one or a few components of a class-marked UAS does **not**
make it privately built unless the manufacturer's instructions describe the change; and a UAS
assembled from a ready-to-assemble kit is **not** privately built. Route (c), modifying a C4
aeromodel, is a third path we had not known about.

**"Visual line of sight" (VLOS)** — an operation in which the remote pilot "is able to maintain
continuous **unaided** visual contact with the unmanned aircraft, allowing the remote pilot to
control the flight path.. for the purpose of avoiding collisions". Definition (7). Anything not
conducted in VLOS is BVLOS, definition (8). **Confirmed.**

*Unaided* is the important word. Looking at a screen or through goggles does not satisfy EU4. If we
ever want to fly first-person view, we need a second person watching the aircraft directly.

---

## B. Netherlands — registration and pilot licence

Source: **RDW**, the Dutch registration authority. Pages read 2026-08-04.
Hub page: [rdw.nl/drone](https://www.rdw.nl/drone). Note the short path — the longer
`/particulier/voertuigen/drone/..` addresses redirect.

### B1. Operator number (*exploitantnummer*)

Source: [Exploitantnummer aanvragen (registreren) — RDW](https://www.rdw.nl/drone/exploitantnummer-aanvragen).
Renewal: [Exploitantnummer verlengen](https://www.rdw.nl/drone/exploitantnummer-verlengen).

| Item | Value | Status |
|---|---|---|
| Who must have one | The owner of a drone or other unmanned aircraft **with a camera, or weighing 250 g or more**. Also anyone flying such an aircraft belonging to someone else | **Confirmed** |
| Cost to apply | **€23.00** | **Confirmed** |
| How many | **One number covers all your aircraft** | **Confirmed** |
| Validity | Expires after **one year**. Renewable online from 6 weeks before it lapses. **If it lapses you cannot renew — you must apply again at €23** | **Confirmed.** Read 2026-08-14 |
| Renewal cost | **€13.00** | **Confirmed.** Read 2026-08-14 |
| Marking | The number looks like `NLD87astrdge12kc - xyz`. **Only the part before the dash goes on the aircraft**, clearly visible on the outside, for example as a sticker. The last three characters are left off so nobody can misuse the number. May also be programmed in if the aircraft supports it | **Confirmed** |
| Who registers for JBV-01 | **The pilot, who is also the operator.** One number. RDW lists flying someone else's drone as a separate case that needs its own number, so splitting owner and pilot would probably cost a second €23 | **Chosen 2026-10-14.** RDW page read 2026-10-14; whether a pilot may use the owner's number is not stated there |
| How to apply | Online with DigiD, or in person at an RDW station with a printed form and ID | **Confirmed** |
| Insurance | **Not compulsory for us.** RDW: for private users, insurance is compulsory under EU rules only **from 20 kg**. We will be far below that. If it were compulsory, the policy number would have to be added to the operator record | **Confirmed.** Read 2026-08-14 |
| Insurance, what RDW advises anyway | RDW "strongly recommends" insuring against injury or property damage to third parties, and says to **check whether your existing liability insurance (*aansprakelijkheidsverzekering*) covers damage caused by drones** | **Confirmed.** Read 2026-08-14. Free to check, and worth doing |
| Flight permit (*vluchtvergunning*) | **Not needed** in the Open Category. Only the Specific category needs one | **Confirmed.** Read 2026-08-14 |

### B2. Remote pilot licence (*vliegbewijs*)

Source: [Vliegbewijs aanvragen — RDW](https://www.rdw.nl/drone/vliegbewijs-aanvragen).
List of approved exam providers: [Vliegbewijs drone — Rijksoverheid](https://www.rijksoverheid.nl/onderwerpen/drone/vraag-en-antwoord/vliegbewijs-drone).

| Item | Value | Status |
|---|---|---|
| Who must have one | Anyone flying a drone **or model aircraft** of **250 g or more** | **Confirmed** |
| Cost | **€10.00** | **Confirmed** |
| Validity | **5 years** from the date of the highest exam passed | **Confirmed** |
| How to get it | Pass an **online exam at a recognised Dutch flight school**, then apply to RDW with DigiD | **Confirmed** |
| Which one we need | **A1/A3** — "Bewijs van voltooiing theorie-examen". Valid across the EU. A2 is a separate, higher licence and requires A1/A3 first | **Confirmed** |
| Carrying it | Must be **with the pilot during every flight** — printed, on a phone, or in the RDW app | **Confirmed** |

---

## C. Where we may fly

| Rule | Status |
|---|---|
| The Netherlands publishes geographical zones, listed as NL1 to NL4 below. **Aeret Kaartviewer** shows them first, **GoDrone** second. Red areas are closed to Open Category flights | **Partly.** ILT names GoDrone and confirms red areas exist. We have not opened the map |
| A flight in a red area needs a permit, applied for at ILT | **Partly.** ILT lists this as a question it answers |
| **Subcategory conditions — how far we must stay from people and buildings** | **CONFIRMED 2026-08-14.** See below. We are in **A3** |

Where to look: [Aeret Kaartviewer](https://aeret.kaartviewer.nl/?@dpf_basic) · [GoDrone operator portal](https://operatorportal.godrone.nl/) ·
[ILT — Flying drones in the Netherlands](https://english.ilent.nl/topics/aviation/drones-and-model-aircraft/drones-eu-residents) ·
[ILT — Wegwijzer drones](https://www.ilent.nl/onderwerpen/luchtvaart/drones-en-modelvliegtuigen/wegwijzer-drones)

### Which subcategory we are in — settled

Read from the Annex to Regulation (EU) 2019/947 on **2026-08-14**, in the Official Journal text
(CELEX 32019R0947). This closes what was the biggest gap in the project.

**We are in A3.** The reasoning is short, and each step is a line in the Annex:

| Subcategory | The privately built route | Open to us? |
|---|---|---|
| **A1** | UAS.OPEN.020(5)(a) — privately built is allowed **only** under **250 g** *and* with a maximum operating speed under **19 m/s** | **No.** Any aircraft that can hover on a battery and also carry a wing will be well over 250 g — an estimate, not measured |
| **A2** | UAS.OPEN.030(3) — requires an aircraft **marked as class C2** | **No.** A privately built aircraft carries no class mark |
| **A3** | UAS.OPEN.040(4)(a) — privately built, **under 25 kg** | **Yes.** This is our route |

**The three A3 conditions, quoted:**

| # | Rule | Where |
|---|---|---|
| A3-1 | "be conducted in an area where the remote pilot reasonably expects that **no uninvolved person will be endangered** within the range where the unmanned aircraft is flown during the entire time of the UAS operation" | UAS.OPEN.040(1) |
| A3-2 | "be conducted at a **safe horizontal distance of at least 150 metres from residential, commercial, industrial or recreational areas**" | UAS.OPEN.040(2) |
| A3-3 | Remote pilot has completed the online course and passed the online theoretical examination defined in UAS.OPEN.020(4)(b) — the **A1/A3** exam we already costed at €10 | UAS.OPEN.040(3) |

**And one obligation we had not seen anywhere.** UAS.OPEN.050(7): the operator shall "ensure in the
case of an UAS operation in subcategory A2 or A3, that **all involved persons present in the area
of the operation have been informed of the risks and have explicitly agreed to participate**."

In plain terms: at an A3 flight there are no bystanders. Anyone in the area is a participant who
has been told what can go wrong and has said yes. That is the rule that replaces the distance-to-a-
person figure we do not have.

**There IS a minimum distance to a person, and it is a formula.** It lives in the guidance rather
than in the rule, which is why every earlier extract we had missed it — they were all cut off
before the AMC. **AMC1 UAS.OPEN.040(1)**, ED Decision 2019/021/R:

> A minimum horizontal distance from the person that is passing the area could be estimated as
> follows:
> (1) no less than **30 m**;
> (2) no less than **the height** ('1:1 rule', i.e. if the UA is flying at a height of 30 m, the
> distance of the UA from the uninvolved person should be at least 30 m), and
> (3) no less than the distance that the UA would cover in **2 seconds at the maximum speed** (this
> assumes a reaction time of 2 seconds).

So the rule is **max(30 m, our height, 2 s × our maximum speed)**, and the same AMC adds that if an
uninvolved person enters the range we adjust the operation, or stop it if safety is not assured.

**Two things this gives us that we did not have.** A real distance we can hold and check. And the
**1:1 rule ties distance to height** — the coupling we lost when the hover-height objective was
deleted comes back through the law instead.

**Which of the three terms is the largest depends on our maximum speed.** The 2-second term passes
30 m at a speed of 15 m/s. Below that speed the 30 m floor decides the distance; above it, our own
speed does. **We hold no speed figure** — the performance objectives that carried one were removed
on 2026-09-08 — so which term binds us is not known until the aircraft is flown and measured. A
faster aircraft needs people standing further back, and that is a design consequence, not a
paperwork one.

**Two more figures from the same Annex, both confirming what we had:**

- **UAS.OPEN.010(2)** — the 120 m is measured "from the closest point of the surface of the earth",
  and over hilly ground the measurement adapts to the terrain.
- **UAS.OPEN.010(3)** — within 50 m horizontally of an artificial obstacle taller than 105 m, the
  ceiling may rise to 15 m above that obstacle, but only at the request of whoever is responsible
  for the obstacle. Not a route we will use.

**Registration threshold, from Article 14(5)(a).** An operator must register when flying an
aircraft "with a MTOM of 250 g or more, **or, which in the case of an impact can transfer to a
human kinetic energy above 80 Joules**", or one carrying a sensor able to capture personal data.
The 80 J alternative is new to us and it can catch a light, fast aircraft that is under 250 g.

### Where we may not fly — the Dutch geographic layer

**Added 2026-09-08.** Everything above this point comes from EU Regulation 2019/947. It is not the
whole rule set for choosing a site. The Netherlands adds a geographic layer on top, and until today
this file did not mention it.

**Why it matters more than the 150 m.** Section §C's 150 m from residential, commercial, industrial
and recreational areas points us at open farmland. The Dutch layer then removes the parts of that
farmland crossed by main roads and railway lines. Those are exactly the features that run through
open land. **The binding constraint on our test site is probably this layer, not the 150 m.**

Source for the whole list: [Rijksoverheid, "Waar mag ik vliegen met een
drone?"](https://www.rijksoverheid.nl/vraag-en-antwoord/drone/waar-mag-ik-vliegen-met-een-drone),
read 2026-09-08.

| ID | Rule | Status |
|---|---|---|
| NL1 | **Forbidden everywhere, all categories:** royal palaces and buildings of the Dutch Royal House, and the protected nature areas above the **Wadden Sea** | **Partly.** Government summary page, not the underlying order |
| NL2 | **Restricted for Open Category flights**, quoted from the page: *"overheidsgebouwen; militaire (oefen)terreinen; evenementen of andere tijdelijk afgezette gebieden; wegen met een snelheidslimiet van 80 kilometer per uur of hoger; spoorlijnen; gebieden rond luchthavens"* — government buildings, military and military training areas, events and temporarily closed areas, **roads with a speed limit of 80 km/h or higher**, **railway lines**, and areas around airports | **Partly.** Quoted from the government page. **Each item still needs tracing to the instrument that imposes it** |
| NL3 | **Natura 2000 areas** where the province or the site manager has imposed a drone ban. Which areas these are is decided per province and per site, not nationally | **Partly.** Named on the government page. **We have checked no province and no site** |
| NL4 | Also listed as restricted: hospital helipads, power lines, drinking-water protection areas, major seaports, hazardous-material sites, secured areas, emergency-response zones, and low-flying routes (*laagvliegroutes*) | **Partly.** Same page, same caveat |

**Which map to use.** The government page names **Aeret Kaartviewer**,
`https://aeret.kaartviewer.nl/?@dpf_basic`, for viewing Open Category A1/A2/A3 no-fly zones, and
mentions **GoDrone**, `map.godrone.nl`, as a second resource. **Use Aeret first.**

**A third map exists and is not a source.** `vliegjedroneveilig.nl/kaart` shows CTR no-fly zones,
uncontrolled airfields that need the manager's permission, low-flight zones and Natura 2000 areas
with drone bans. Its own disclaimer says the maker *"kan geen enkele aansprakelijkheid aanvaarden"* —
accepts no liability — and tells the reader to check ICAO charts, AIS Netherlands and IL&T. **Useful
for looking. Never quote it.**

### When we may fly — daylight only

Read from ILT, the Dutch aviation authority, on 2026-08-14. Their page was last modified
2026-07-15, so it is current.

> "U mag met uw drone niet op zicht in het donker vliegen." — *You may not fly your drone on sight
> in the dark.* "Volgens de Visual Flight Rules (VFR) mag u niet met uw drone op zicht in het donker
> vliegen."

Flying outside the **Uniforme Daglicht Periode (UDP)** needs an **ontheffing** from the
ILT aviation authority, **and** the flight must be in the **Specific category**, **and** the
operator needs an *exploitatievergunning*. All three are closed to us.

**So: daylight only, with no route around it.** This is now a rule we can cite rather than caution
we chose. It also settles the FPV question from the other direction — night flying was never
available to us at any price.

**What the page does not give is the exact boundary of the UDP.** Search results say a quarter of
an hour either side of sunrise and sunset. **Not verified**, and we should not put a time in a
flight plan until it is.

Source: [Vliegen buiten de Uniforme Daglicht Periode — ILT](https://www.ilent.nl/onderwerpen/luchtvaart/drones-en-modelvliegtuigen/regels-voor-drones/specifiek-dronecategorie/buiten-udp)

**What this means for the test site.** 150 m from any residential, commercial, industrial or
recreational area is a hard filter. In a country as built-up as the Netherlands that rules out most
of the map, and it has to be checked against NL1 to NL4 as well — Aeret first, GoDrone second. The site search should
start from this figure, not end at it.

---

## D. What we still do not know

| Gap | How to close it |
|---|---|
| ~~Annex Part A — the A1/A2/A3 conditions~~ | **Closed 2026-08-14.** Read from the Official Journal text, CELEX 32019R0947. See §C |
| ~~Whether insurance is compulsory for us~~ | **Closed 2026-08-14.** Not compulsory below 20 kg. See §B1 |
| ~~Renewal fee for the operator number~~ | **Closed 2026-08-14.** €13.00. See §B1 |
| ~~Whether the Netherlands restricts flying to daylight~~ | **Closed 2026-08-14.** Daylight only in the Open Category. See §C. **The exact UDP boundaries are still unverified** — search results say 15 minutes either side of sunrise and sunset, and the ILT page does not state them |
| **Every item in NL1 to NL4** — the Dutch geographic layer | Trace each one to the instrument that imposes it, not to the government summary page. Railways and the 80 km/h road rule matter most, because they are what will decide the test site. Until then the rows read **Partly** and no site may be declared legal on the strength of them |
| **Which Natura 2000 areas near us carry a drone ban**, NL3 | Decided per province and per site manager. Check the province and the specific area, on the Aeret map and with the site manager. Nothing national to read |
| Whether JBV-01 counts as a **model aircraft** under Article 16 | **Partly closed 2026-08-14.** Article 16 is a route for a **club or association**, not for an individual: the competent authority may issue an authorisation *upon request by a model aircraft club or association*, limited to that Member State. So it is only open to us by joining a Dutch club that already holds one, and flying under its conditions. Whether any Dutch club does, and on what terms, is unchecked. Source: [Regels voor modelvliegen — Rijksoverheid](https://www.rijksoverheid.nl/onderwerpen/drone/regels-voor-modelvliegen). RDW's own licence page links model aircraft here, so this may be a second legal route worth understanding |
| ~~Re-check the A3 conditions against the current edition~~ | **Closed 2026-08-14.** Read in the [Easy Access Rules, July 2024 edition](https://drones.gov.cy/wp-content/uploads/2025/08/EAR_UAS_Jul24.pdf), which carries all five amendments. UAS.OPEN.040 is unchanged — the 150 m and the privately built route both still read as §C says. The block at the head of §A records this |

---

## E. Where each rule is carried in the rest of the folder

This file is the **source**. Nothing below is repeated here in full, so that the two cannot drift
apart. Section E used to hold the consequences in prose; on 2026-09-08 it became this table.

| Rule here | Where it binds the project |
|---|---|
| EU1 and definition (16) — privately built | **C12.** A purchasing rule in `04_build/BOM.xlsx`: buy parts, never a complete ready-to-assemble kit |
| EU2 — below 25 kg | **C13** |
| EU3 — safe distance, never over assemblies | **C14**, with the metres in **C19** |
| EU4 — unaided visual line of sight | **C15.** Also why no camera view can be our primary method |
| EU5 — 120 m ceiling | **C16.** A hard limit on every flight test we plan |
| EU6 — nothing dropped, no dangerous goods | **C17** |
| §C — A3, 150 m from built-up areas | **C18.** It decides the test site, `CONOPS.md` §4.0 |
| §C — max(30 m, height, 2 s × max speed) | **C19.** It ties how high we hover to how far back people stand, [DRM-0900] |
| §C — everyone present has agreed to take part | **C20** |
| §C — daylight only | `CONOPS.md` §4.0 |
| §C, NL1 to NL4 — the Dutch geographic layer | **AS1**, the test site. It is the layer that decides which open ground is usable, and it is why AS1 cannot be closed from a map of built-up areas alone |
| §B1 — operator number, €23, yearly | **C22**, the budget line in `NGO.md` §6, and the airframe surface interface in `CONOPS.md` §3.3. A sticker on foam is enough, but it must survive weather and a crash |
| §B2 — remote pilot licence, €10 | **C23**, and the budget line |

**One consequence has no home yet: timing.** The online exam and the RDW applications take real
days. The pilot, who is also the operator, may not legally fly JBV-01 until he holds both the
licence and the operator number. That belongs on the schedule in `00_management/`, not in the week
before the first flight.
