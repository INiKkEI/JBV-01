# Stakeholders

Who is affected by JBV-01, and what they can impose on it.

**Definition.** A stakeholder is a group or a person affected by the outcome, or accountable for
it. Two kinds:

- **Customer** — requested the product and receives it.
- **Other interested parties** — set limits we work inside, or are exposed to what we do.

---

## 1. Customer

| Stakeholder | Expectation |
|---|---|
| The two of us | An aircraft that takes off vertically, transitions to wing-borne flight, transitions back, and lands vertically |

**We are the only customer.** Nobody outside the two of us sets acceptance criteria.

That has one cost, and it is the largest process risk in the project. An outside customer is what
normally stops requirements growing during a project. We do not have one. The requirements freeze
and our own discipline are the whole brake. Carried as risk R2 in `CONOPS.md` §8.

## 2. Those who set limits

Their conditions are published, and we cannot negotiate them.

| Stakeholder | What they require | What it costs us |
|---|---|---|
| **EASA** | Open Category compliance: below 25 kg, unaided visual line of sight, 120 m ceiling, subcategory A3 conditions | No money. `RULES.md` §A and §C |
| **RDW** | A registered operator, the operator number visible on the airframe, a licensed pilot on every flight | €23 + €10, and days on the schedule for the exam and the applications. `RULES.md` §B |
| **ILT** | No flight in a closed geographical zone. Daylight only | No money. The site must be checked on the GoDrone map. `RULES.md` §C |

## 3. Those exposed to what we do

| Stakeholder | What they require | Where it is handled |
|---|---|---|
| **People near the test site** | Not to be endangered. Not to be disturbed more than is reasonable, mainly by noise | C14, C19, C20 |

They did not ask to be involved and they cannot refuse the risk. [DRM-0900] says the aircraft falls
if a lift unit fails in hover, so this is the only row in this file where a person can be hurt.

We hold no distance figure of our own. C19 gives one — the greatest of 30 m, our flying height, and
2 seconds at maximum speed — and it is law rather than our judgement.

## 4. Not stakeholders

Recorded so the list above stays honest. Each one is managed as an assumption or a constraint
instead.

| | Why not | Where it is handled |
|---|---|---|
| Suppliers — hobby shops, JLCPCB and its sister services | Not affected by whether JBV-01 flies. They influence stock, price and lead time, which is an input we manage, not an expectation we must meet | AS3, C6 |
| The makerspace | Provides a capability and has no stake in the outcome | AS6 |
| Readers of the record | Not affected by the outcome. Nothing in the project fails if they cannot follow it | Nothing. We keep the record because we want it |
