# Rules for flying JBV-01 in the Netherlands

Every rule we must obey, with its source and how well we have checked it. This file feeds ConOps
section 2.1 "Applicable Documents" and constraints C6, C6a, C7, C8 and C11 to C16 in `NGO.md`.

Rules here are numbered **EU1–EU7** and **B1–B2**. Note that **A1, A2 and A3 always mean the Open
Category subcategories** in this project, because that is what they mean in the regulation.

**Checked on 2026-08-04.** Rules change. Check again before the requirements freeze, and again
before the first flight.

## How to read the status column

| Status | Means |
|---|---|
| **Confirmed** | We read it in the source document ourselves |
| **Partly** | We read part of it, or the source is one step removed |
| **Not checked** | We have only seen it in a search result or a hobby website. **Do not rely on it** |

---

## A. EU rules — the Open Category

Source: **Regulation (EU) 2019/947**, read in the EASA consolidated text *Easy Access Rules for
Unmanned Aircraft Systems*, January 2021 edition.

- The copy we actually read: [Easy Access Rules for UAS, January 2021 (PDF, 309 pp.)](https://drones.gov.cy/wp-content/uploads/2021/02/Easy-Access_Rules_for_Unmanned_Aircraft_Systems_January_2021.pdf)
- The current edition, which we have **not** read: [EASA — Easy Access Rules for Unmanned Aircraft Systems](https://www.easa.europa.eu/document-library/easy-access-rules/easy-access-rules-unmanned-aircraft-systems-regulation-eu)
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

**"Visual line of sight" (VLOS)** — an operation in which the remote pilot "is able to maintain
continuous **unaided** visual contact with the unmanned aircraft, allowing the remote pilot to
control the flight path ... for the purpose of avoiding collisions". Definition (7). Anything not
conducted in VLOS is BVLOS, definition (8). **Confirmed.**

*Unaided* is the important word. Looking at a screen or through goggles does not satisfy EU4. If we
ever want to fly first-person view, we need a second person watching the aircraft directly.

---

## B. Netherlands — registration and pilot licence

Source: **RDW**, the Dutch registration authority. Pages read 2026-08-04.
Hub page: [rdw.nl/drone](https://www.rdw.nl/drone). Note the short path — the longer
`/particulier/voertuigen/drone/...` addresses redirect.

### B1. Operator number (*exploitantnummer*)

Source: [Exploitantnummer aanvragen (registreren) — RDW](https://www.rdw.nl/drone/exploitantnummer-aanvragen).
Renewal: [Exploitantnummer verlengen](https://www.rdw.nl/drone/exploitantnummer-verlengen).

| Item | Value | Status |
|---|---|---|
| Who must have one | The owner of a drone or other unmanned aircraft **with a camera, or weighing 250 g or more**. Also anyone flying such an aircraft belonging to someone else | **Confirmed** |
| Cost to apply | **€23.00** | **Confirmed** |
| How many | **One number covers all your aircraft** | **Confirmed** |
| Validity | Expires after **one year**, then must be renewed | **Confirmed** that it expires yearly. Renewal fee **not checked** |
| Marking | The number looks like `NLD87astrdge12kc - xyz`. **Only the part before the dash goes on the aircraft**, clearly visible on the outside, for example as a sticker. The last three characters are left off so nobody can misuse the number. May also be programmed in if the aircraft supports it | **Confirmed** |
| How to apply | Online with DigiD, or in person at an RDW station with a printed form and ID | **Confirmed** |
| Insurance | If insurance is compulsory for us, it must be added to our operator record | **Confirmed that this is required if applicable.** Whether it applies to us is **not checked** |

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
| Minimum age | Under 16 may only fly **under the supervision of someone over 16 who holds a licence** | **Confirmed** |

---

## C. Where we may fly

| Rule | Status |
|---|---|
| The Netherlands publishes geographical zones. The **GoDrone** app and map show them. Red areas are closed to Open Category flights | **Partly.** ILT names GoDrone and confirms red areas exist. We have not opened the map |
| A flight in a red area needs a permit, applied for at ILT | **Partly.** ILT lists this as a question it answers |
| **Subcategory conditions — how far we must stay from people and buildings** | **NOT CHECKED. This is the biggest gap in this file** |

Where to look: [GoDrone operator portal](https://operatorportal.godrone.nl/) ·
[ILT — Flying drones in the Netherlands](https://english.ilent.nl/topics/aviation/drones-and-model-aircraft/drones-eu-residents) ·
[ILT — Wegwijzer drones](https://www.ilent.nl/onderwerpen/luchtvaart/drones-en-modelvliegtuigen/wegwijzer-drones)

### The subcategory gap, stated plainly

The Open Category is divided into A1, A2 and A3. Which one we fall into decides how far from
people and buildings we must fly. Those conditions are in Annex Part A of 2019/947, points
UAS.OPEN.020, .030 and .040. **We have not been able to read them.** The PDF we are working from
was cut off before the Annex, and the EASA website returns an empty page without a browser.

What we expect, from search results only and **therefore not to be relied on**:

- A privately built aircraft over 250 g most likely falls in **A3**.
- A3 is expected to require at least **150 m horizontally from residential, commercial, industrial
  and recreational areas**, and an area where no uninvolved person is endangered.
- A2 requires a C2 class marking, which a privately built aircraft cannot have, so A2 is probably
  closed to us.

If A3 and the 150 m figure are right, the test site must be genuinely open country. That is a
strong constraint on where we can fly and it should be settled before we choose a site.

---

## D. What we still do not know

| Gap | How to close it |
|---|---|
| Annex Part A — the A1/A2/A3 conditions | [EASA Easy Access Rules, online edition](https://www.easa.europa.eu/en/document-library/easy-access-rules/online-publications/easy-access-rules-unmanned-aircraft-systems) — needs a browser |
| Whether insurance is compulsory for us | [Verzekeringen en vluchtvergunningen — RDW](https://www.rdw.nl/drone/verzekeringen-en-vluchtvergunningen) |
| Renewal fee for the operator number | [Exploitantnummer verlengen — RDW](https://www.rdw.nl/drone/exploitantnummer-verlengen) |
| Whether the Netherlands restricts flying to daylight | Seen in search results as 15 minutes before sunrise to 15 minutes after sunset. **Unverified.** Try [Rijksoverheid — drone](https://www.rijksoverheid.nl/onderwerpen/drone) |
| Whether JBV-01 counts as a **model aircraft**, which has its own route under Article 16 | [Regels voor modelvliegen — Rijksoverheid](https://www.rijksoverheid.nl/onderwerpen/drone/regels-voor-modelvliegen). RDW's own licence page links model aircraft here, so this may be a second legal route worth understanding |
| Amendments to 2019/947 since January 2021 | [EUR-Lex record for 2019/947](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32019R0947) lists the amending acts. Our copy of the law is five years old |

---

## E. What these rules change about JBV-01

**Money.** Registration and licence together cost at least **€23 + €10 = €33**, plus a yearly
renewal of the operator number. The €800 allocation in `NGO.md` had no line for this. It does now.

**The airframe.** The operator number must be visible on the outside. A sticker on foam is
enough, but it has to survive weather and a crash, and it must be planned rather than added at
the last minute.

**Flight testing.** The 120 m ceiling, EU5, is a hard limit on every test we plan. Nothing in our
flight test plan may exceed it.

**No first-person view as our primary method.** EU4 requires unaided visual contact. If we want a
camera view for telemetry, one of us must still be watching the aircraft directly.

**Purchasing.** Rule EU1 with definition (16): **do not buy a complete ready-to-assemble kit.**
Buying individual parts is fine. This belongs in `04_build/BOM.xlsx` as a rule, not just here.

**The test site.** Depends entirely on the subcategory gap in section C. Until that is closed we
cannot say whether a field at the edge of a village is legal or not.

**Timing.** The online exam and the RDW applications take real days. Neither of us can legally
fly JBV-01 without both. This belongs on the schedule now, not in the week before the first
flight.
