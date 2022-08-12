# Proposed task status and flows

## Communication Principles
- **Target no more than 5 tickets per board, per status category.** If there's more, task must be either deployed or put back in the backlog.
- **If you're finished with a stage, it's YOUR responsibility to assign it to the next person:** If you don't know who that is, ASK your manager or the team.
- **Whoever creates the ticket is the assumed owner of the ticket:** Unless specified otherwise. The owner's job is to sheperd the ticket to completion. 
- **Don't assume automated notifications are read:** Priority tickets should have redudant communication via Slack 
- **Always Acknowledge handoffs:** It takes two seconds and it's a great way to initiate a conversation for any clarification.
- **Tickets Without Testing Instructions Don't Get QAed:** Test cases should be created as early as possible - ideally with the ticket creation.


## Status definitions
- **Backlog**: Distant future work (more than 2 weeks)
- **Future**: Work in next 2 weeks (or fewer)
- **In Progress**: Current work
- **Review**: Needs review
- **Ready for QA**: Needs testing or retesting
- **Ready For Production**: Needs to be merged and released
- **Complete**: Deployed in production


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

