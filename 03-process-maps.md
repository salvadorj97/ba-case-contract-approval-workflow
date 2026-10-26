# 3. Process Maps

CCFM = Contract and Commercial Fulfilment Manager (regional level), owner of the workflow.

## As-is

```mermaid
flowchart TD
    A([Sales asks the CCFM for a contract review]) --> B[CCFM creates the review in the platform and enters data manually]
    B --> C[CCFM selects country reviewers by project type]
    C --> D[Review appears in each reviewer's inbox]
    D --> E[CCFM tags reviewers in the country chat group with the link]
    E --> F[Each reviewer votes and sets a risk level, using the Excel Risk Table]
    F --> G{All reviewers Agree?}
    G -- Disagree or unclear comment --> H[CCFM contacts the reviewer to understand the reason]
    H --> I[New round with the reviewers who disagreed]
    I --> G
    G -- Yes --> J{Highest risk level given?}
    J -- Low --> K[Regional round: one regional CCFM checks the commercial part]
    J -- Medium or High --> L[Regional round: 3 regional reviewers, CCFM writes the context]
    K --> RG{Regional reviewers all Agree?}
    L --> RG
    RG -- No --> RR[New regional round until approved]
    RR --> RG
    RG -- Yes --> HI{High risk?}
    HI -- Yes --> M[CCFM asks an HQ contact to organise a final round]
    HI -- No --> S([Sent to HQ for signature])
    M --> S

    classDef pain fill:#fde2e2,stroke:#c0392b,color:#000;
    class E,F,H,RR pain;
```

Red steps are the pain points. A wrong or poorly justified risk level at step F sends the contract down the wrong path, or stalls it while the CCFM asks for clarification. There is no priority rule: contracts are handled in whatever order reviewers open them.

## To-be

```mermaid
flowchart TD
    A([Sales asks the CCFM for a contract review]) --> B[CCFM creates the review in the platform]
    B --> C[CCFM selects country reviewers by project type]
    C --> P[System flags priority from risk and urgency]
    P --> D[Automatic notification to reviewers]
    D --> T{Vote within agreed delay?}
    T -- No --> R[Automatic reminder, or reassignment to the declared backup]
    R --> T
    T -- Yes --> F[Reviewer votes and selects Risk Table criteria; risk level suggested by the platform]
    F --> G{All reviewers Agree?}
    G -- No --> W[Reason mandatory for Disagree and Agree with comments]
    W --> I[New round with the reviewers who disagreed]
    I --> G
    G -- Yes --> J{Highest risk level, with its criterion visible}
    J -- Low --> K[Regional CCFM check created automatically]
    J -- Medium or High --> L[Regional round created with a context template]
    K --> RG{Regional reviewers all Agree?}
    L --> RG
    RG -- No --> RR[Reason mandatory, new regional round until approved]
    RR --> RG
    RG -- Yes --> HI{High risk?}
    HI -- Yes --> M[HQ round requested in the platform]
    HI -- No --> S([Sent to HQ for signature])
    M --> S

    classDef new fill:#e2f0fd,stroke:#1F4E79,color:#000;
    class P,R,F,W,J,K,L,RR,M new;
```

Blue steps are the changes. What disappears: tagging in chat groups, chasing reviewers for their reasons, the separate Excel file, and risk levels justified only in free comments.

## Change summary

| Step | As-is | To-be |
|---|---|---|
| Ordering | No priority | Priority flag (risk and urgency) |
| Follow-up | CCFM tags reviewers in chat groups | Automatic reminder, then backup |
| Disagreement | Reason optional, CCFM chases it | Reason mandatory |
| Risk level | Set from an Excel file, justified in free comments | Set from Risk Table criteria in the platform |
| Routing by risk | CCFM reads the comments and opens the next round by hand | Next round created from the highest risk level |
| Regional and HQ rounds | Context written from scratch, HQ contacted by message | Context template, HQ request in the platform |
