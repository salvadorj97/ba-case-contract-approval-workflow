# Business Analysis Case: Contract Review Workflow

A Business Analysis case study on a real problem I lived as a Contract and Commercial Fulfilment Manager: **contract reviews that stall** in the Latin American operations of a multinational energy-solutions company.

I first described this problem in a recommendation report during my Mastère Spécialisé at Grenoble École de Management. This repository turns that report into the deliverables a Business Analyst produces: problem statement, stakeholder map, as-is and to-be process maps, user stories with acceptance criteria, and a KPI framework.

> **Scope note:** this is an analysis and a recommendation, not a delivered project. The targets below are proposed targets, not measured results. Company names, people and internal tools are anonymised.

---

## The problem in one sentence

Contract reviews waited too long because follow-up was manual, reasons for disagreement were often unclear, and the risk level that decides the review path was applied differently from one country to another.

## Deliverables

| # | Deliverable | What it shows |
|---|---|---|
| 1 | [Problem statement](docs/01-problem-statement.md) | Context, pain points, root causes, scope |
| 2 | [Stakeholders and RACI](docs/02-stakeholders-raci.md) | Who is involved and who decides |
| 3 | [As-is and to-be process maps](docs/03-process-maps.md) | Where the workflow breaks and how the redesign fixes it |
| 4 | [User stories and acceptance criteria](docs/04-user-stories.md) | 1 epic, 6 user stories, Gherkin acceptance criteria |
| 5 | [KPI framework](docs/05-kpi-framework.md) | How success would be measured |

## Pain points and the answer to each

| Pain point (as-is) | Proposed change (to-be) | User story |
|---|---|---|
| Reviewers miss inbox notifications; the contract manager tags them by hand in country chat groups | Automatic reminders | US-03 |
| Disagree votes come without a clear reason, so the contract manager has to chase each reviewer | Reason mandatory on Disagree and Agree with comments | US-04 |
| The Excel "Risk Table" is applied inconsistently by country | Risk Table criteria built into the workflow | US-01 |
| The risk level decides the review path, but it is justified only in free comments | Criterion mandatory for medium and high, next round created automatically | US-02 |
| Backup reviewers add confusion when someone is away | Backup declared in the tool, with automatic reassignment | US-05 |
| No prioritisation: low-value contracts can move faster than critical ones | Priority flag based on risk and urgency | US-06 |

## Approach

1. **Problem framing:** pain points taken from my own experience as Contract and Commercial Fulfilment Manager, coordinating reviews between country teams, regional managers and headquarters.
2. **Process analysis:** as-is map, then a to-be map that removes manual steps.
3. **Requirements:** one epic broken into user stories, each with testable acceptance criteria.
4. **Measurement:** KPIs tied to each pain point, with baselines to collect before any change.
5. **Delivery method:** a first two-week pilot sprint in two countries, then a regional rollout (the original report recommended SAFe for scaling).

## Tools

- Process maps: Mermaid (rendered by GitHub), also editable in draw.io
- Requirements: Markdown, Gherkin syntax for acceptance criteria
- Method: Scrum for the pilot sprint, SAFe for scaling

## Next steps for this repository

- [ ] Power Automate prototype of the to-be review flow (reminders, backup reviewer, mandatory reasons)

---

**Salvador Jiménez-Juárez**: Business Analyst, Digital Transformation
[LinkedIn](https://www.linkedin.com/in/salvador-jimenez97mx/) · [Medium](https://medium.com/@salvador.jimenez-juarez)
