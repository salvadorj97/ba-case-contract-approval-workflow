# 4. User Stories and Acceptance Criteria

## Epic

**EP-01. Contract reviews without manual follow-up**
As the regional contract team, we want reviews to move on their own and risk to be classified the same way in every country, so that contracts are signed faster and follow the right review path.

CCFM = Contract and Commercial Fulfilment Manager. Parameters marked **[to agree]** are decisions for the Product Owner, not assumptions of the analyst.

---

## US-01. Risk Table criteria in the workflow
**Priority:** Must have · **Pain point:** P3

As a **reviewer** (Finance, Commercial or any other function),
I want the platform to suggest a risk level based on the Risk Table criteria,
so that I classify contracts the same way as reviewers in other countries.

**Acceptance criteria**
```gherkin
Scenario: Risk level suggested from the contract situation
  Given a contract open for review
  When the reviewer selects the situations that apply from the Risk Table list
  Then the platform shows the suggested risk level (low, medium or high)
  And shows which criterion led to that level

Scenario: Override with justification
  Given a suggested risk level
  When the reviewer chooses a different level
  Then a written justification is mandatory before saving
```

---

## US-02. Routing by risk level
**Priority:** Must have · **Pain point:** P4

As a **CCFM**,
I want the next review round to be created from the highest risk level given, with the Risk Table criterion behind it,
so that I route the contract without reading every comment or checking a classification outside my domain.

**Acceptance criteria**
```gherkin
Scenario: Medium or high level needs a criterion
  Given a reviewer sets a medium or high risk level
  When the reviewer submits the vote
  Then at least one Risk Table criterion is mandatory

Scenario: Routing by the highest level
  Given all country reviewers have voted Agree
  When the CCFM closes the country round
  Then a low-risk contract opens a regional check by one regional CCFM
  And a medium-risk contract opens a regional round with three reviewers
  And a high-risk contract opens a regional round and creates a request for the HQ round
  And the CCFM sees which reviewer set the highest level and why
```

---

## US-03. Automatic reminders
**Priority:** Must have · **Pain point:** P1

As a **CCFM**,
I want pending votes to trigger automatic reminders,
so that I no longer have to tag reviewers in country chat groups.

**Acceptance criteria**
```gherkin
Scenario: Reminder after the agreed delay
  Given a vote pending for more than [to agree] working days
  When the daily check runs
  Then the reviewer receives a reminder with the project name and a direct link

Scenario: Follow-up visible to the CCFM
  Given reminders were sent for a contract
  When the CCFM opens the contract
  Then the CCFM sees which reviewers are still pending and when each reminder was sent
```

---

## US-04. Reason mandatory on disagreement
**Priority:** Must have · **Pain point:** P2

As a **CCFM**,
I want reviewers to give a structured reason when they vote Disagree or Agree with comments,
so that I can open the next round without contacting each reviewer first.

**Acceptance criteria**
```gherkin
Scenario: Reason required
  Given a reviewer votes Disagree or Agree with comments
  When the reviewer submits the vote
  Then a reason category and a free-text explanation are mandatory
  And the clause or section concerned can be selected

Scenario: Reasons visible in the next round
  Given a new round is opened with the reviewers who disagreed, at country or regional level
  Then each reviewer sees the reasons given in the previous round
```

---

## US-05. Declared backup reviewer
**Priority:** Should have · **Pain point:** P5

As a **reviewer** who will be travelling or on leave,
I want to declare my backup and my dates of absence in the platform,
so that contracts do not wait for my return.

**Acceptance criteria**
```gherkin
Scenario: Automatic reassignment during absence
  Given a reviewer has declared a backup for given dates
  When a review request arrives during those dates
  Then the request is assigned to the backup
  And the original reviewer is informed

Scenario: No backup declared
  Given a reviewer is marked absent without a backup
  When a review request arrives
  Then the CCFM is alerted to choose a replacement reviewer
```

---

## US-06. Priority flag
**Priority:** Should have · **Pain point:** P6

As a **CCFM**,
I want each contract flagged by risk level and urgency,
so that reviewers handle the most critical contracts first.

**Acceptance criteria**
```gherkin
Scenario: Priority displayed in the inbox
  Given contracts pending review
  When a reviewer opens the inbox
  Then contracts are sorted by priority (high, medium, low)
  And the priority rule is visible on hover

Scenario: Priority rule
  Given a contract with a high risk level or a tender deadline within [to agree] days
  Then its priority is "high"
```

---

## Not a user story: change enablement

Training reviewers on the Risk Table, and introducing Agile practices to regional and country teams, are needed for adoption. They are tracked as backlog tasks, not as user stories, because they do not change the product.

## Prioritisation (MoSCoW)

| Story | Priority | Reason |
|---|---|---|
| US-01 | Must | Root cause of inconsistent risk levels |
| US-02 | Must | Stops contracts from following the wrong review path |
| US-03 | Must | Removes the largest manual workload |
| US-04 | Must | Removes the second round of chasing |
| US-05 | Should | Frequent but not daily |
| US-06 | Should | Needs agreement between countries on the rule first |
