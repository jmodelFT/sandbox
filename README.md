# sandbox

Backlog: Distant future work (more than 2 weeks)
Future: Work in next 2 weeks (or fewer)
In Progress: Current work
Review: In process of being reviewed
In QA: In process of being reviewed
Ready For Production: Needs to be merged and released
Complete: Deployed in production


```mermaid
sequenceDiagram 
    participant Backlog as Backlog
    participant Future as Future
    participant InProgress as In Progress
    participant Review as Review
    participant QA as Ready For QA 
    participant ReadyForProduction as Ready For Production
    participant Complete as Complete


    Backlog ->> Future: Prioritized to work on next
    Future -->> Backlog: Deprioritized 
    
    Future->> InProgress: Work started
    InProgress -->> Future: Deprioritized
    
    InProgress ->> Review: Needs peer review
    Review -->> InProgress: Needs rework

    Review ->> QA: Passed peer review and needs testing
    QA -->> InProgress: Failed QA case(s)

    QA ->> ReadyForProduction: Passed QA

    ReadyForProduction ->> Complete: Deployed on Production

    Complete -->> InProgress: Failed smoke testing
```

