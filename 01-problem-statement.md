# 1. Problem Statement

## Context

The company sells energy solutions across Latin America: power conversion and battery storage for photovoltaic projects, and data centre solutions. New contracts and tenders go through an internal review workflow before they are signed. Purchases from existing customers skip the contract review and only go through a commercial check.

The workflow is run by four **Contract and Commercial Fulfilment Managers (CCFM)** at regional level, who share the Latin American countries between them. Reviewers come from six functions (Product, Service, Channel, Finance, Supply Chain, Commercial) and three levels:

- **Country level:** first review round, with the reviewers the CCFM selects for the project
- **Regional level:** always a second round; its size depends on the risk level
- **Headquarters:** an extra round when the risk is high

In each round, every reviewer votes **Agree**, **Agree with comments** or **Disagree**, and sets a risk level (low, medium or high). Most reviewers set low; Finance or Commercial may set medium or high and must explain why in their comments. The risk level then decides the path. At every level, a round with Disagree votes or comments is followed by a new round with the same logic, until the contract is approved.

| Risk level | Next steps |
|---|---|
| Low | Regional round with one reviewer only (a regional CCFM, for Commercial), then signature |
| Medium | Full regional round with three regional reviewers, then signature |
| High | Full regional round, then a headquarters round, then signature |

The workflow runs in an in-house platform, and every pending review appears in the reviewer's inbox.

## Pain points

**P1. Reviews stall.**
Reviews appear in each reviewer's inbox, but reviewers delay action because of workload or oversight. The CCFM compensates by tagging reviewers in one messaging group per country, posting the project name and a link. This duplicates what the platform already does and depends on individual follow-up.

**P2. Reasons for disagreement are unclear.**
When a reviewer votes Disagree or Agree with comments, the reason is sometimes missing or too vague. The CCFM has to contact the reviewer to understand it before opening a new round. Because rounds repeat until approval, at country and regional level, every unclear reason adds a full cycle.

**P3. Risk classification is inconsistent.**
Risk is assessed with an Excel document called the "Risk Table", which lists contract situations and their risk level (low, medium, high). The table itself is well built, but some countries do not apply it fully or consistently.

**P4. Classification errors travel downstream.**
The risk level decides how many review rounds a contract needs. When a reviewer assigns the wrong level, or explains a medium or high level only vaguely in the comments, the contract follows the wrong path or stalls while the CCFM asks for clarification. Correcting the level is not the CCFM's role: risk assessment involves details outside the commercial domain.

**P5. Backup reviewers add confusion.**
Backups exist, but when a reviewer is travelling or on leave it is not always clear who should review.

**P6. No prioritisation.**
There is no shared rule to rank contracts by business value, risk or urgency. A less critical contract can therefore move faster than a high-priority one.

## Root causes

| Root cause | Pain points |
|---|---|
| Follow-up depends on people, not on the system | P1, P5 |
| Votes can be cast without a structured reason | P2 |
| Risk rules live in an Excel file outside the workflow | P3, P4 |
| Risk level justified in free comments, not linked to Risk Table criteria | P4 |
| No prioritisation criteria agreed between countries | P6 |

## Scope

**In scope:** the internal review workflow for new contracts and tenders, from the request by Sales to the hand-off for signature.
**Out of scope:** customer negotiation, contract drafting, how the headquarters round is run, fulfilment after signature.

## Objective

Reduce review time and make risk classification consistent across countries, without adding manual work for the CCFM.
