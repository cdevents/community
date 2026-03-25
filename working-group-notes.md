---
tags: CDEvents
---

# CDEvents Working Group Meeting Notes

[![hackmd-github-sync-badge](https://hackmd.io/2FRGlw9fTMmKN1OQUVvguA/badge)](https://hackmd.io/2FRGlw9fTMmKN1OQUVvguA)

This document contains the notes from the [CDEvents Working Group](https://hackmd.io/lBlDCrL7TvmtNOjxdopJ5g).

## Meeting Details

### Schedule

- APAC friendly Monday meetings are held at [11am UTC](https://time.is/10am_in_UTC) during summer time and at [12pm UTC](https://time.is/11am_in_UTC) during winter time).
- NA friendly Monday meetings are held at [3pm UTC](https://time.is/3pm_in_UTC) during summer time and at [4pm UTC](https://time.is/4pm_in_UTC) during winter time)

### Previous Years

- [2022 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2022.md)
- [2023 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2023.md)
- [2024 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2024.md)
- [2025 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2025.md)


### Template

Participants:
- Name / affiliation / TZ

Links:
- [v0.6 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged 
- Action Items
- \<addme\>

### March, 24th 2026 (Americas)

Participants:
- Dadisi Sanyika, Sol Duara, Pacific
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Agenda:
- New attendees
- Review roadmap
- https://github.com/cdevents/spec/pull/302 source + id merge
    - To vote next week
- https://github.com/cdevents/spec/pull/292 Link + domainId
    - Lessen scope to domain ID
    - Introduce another proposal/PR that addresses subject to subject linking.
        - Side meeting w/ David to address this
- https://github.com/cdevents/spec/pull/276 automation of python
    - Rewrite in JS (David)
    - Still pending
- https://github.com/cdevents/spec/issues/297 Feature Flag
    - Ping Matt on this (Ben)

### March, 17th 2026 (Americas)
Participants:
- Dadisi Sanyika, Sol Duara, Pacific
- Andrea Frittoli, IBM, UTC
- David Bernard, Alchim312/CDviz, UTC+2

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
    - https://github.com/cdevents/spec/pull/292
        - Discussion ongoing, continue offline
    - https://github.com/cdevents/spec/pull/276
        - Needs to be reworked in js
    - https://github.com/cdevents/spec/pull/298
        - Needs Signed-off-by in commits for DCO
        - 
- (Action) Dasisi to archive old files and notes to git to free up space on hackmd
- JSON Schema generation
    - Demo: https://github.com/davidB/sandbox_cdevents_jsonschema_generation
- CDViz include cdevents version translators tools
- David to draft a google form to find out about CDEvents user
    - Andrea to check with Kate if we can use a CDF account
- Feedback needed on https://github.com/cdevents/spec/issues/252#issuecomment-4032746973 so David can author the PR

### March, 10th 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- https://github.com/cdevents/spec/pull/298 (Approval)
    - David has approval depends on conformance example
    - Add that after meeting
- https://github.com/cdevents/spec/pull/276
    - To close and rewrite in Javascript
- https://github.com/cdevents/spec/issues/252 (Revisit next week)



### March, 3rd 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, UTC
- David Bernard, Alchim312/CDviz, UTC+2

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- https://github.com/cdevents/spec/pull/298 (Approval)
    - Enums format needs documentation - Ben
    - https://github.com/cdevents/spec/issues/252 slated for v0.6
    - Vote for merging next week
- https://github.com/cdevents/spec/pull/292 - Ben
    - Vote for merging next week
- https://github.com/cdevents/spec/pull/300 - Merged (Thanks Andrea)
- DataOps CDEvents
    - Reach out to individual projects related to data ops
    - Create a blog regarding CDEvents / What does data ops mean?
    - Creating a list of projects relevant to data ops
    - https://cdeliveryfdn.slack.com/archives/C07N3QS2KGS
- Generate JSON Schema from a meta data model
    -  tried with Cuelang (but not happy with it, see the README of repo)
    -  current proposal:
        - yaml (pseudo json-schema fragment)
        - typescript (to assemble, compose and generate json-schemas)
    - https://github.com/davidB/sandbox_cdevents_jsonschema_generation

### February, 17th 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, UTC
- David Bernard, Alchim312/CDviz, UTC+2
- Dadisi Sanyika, Sol Duara
- Candace Stump, Sol Duara

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Semantics - https://github.com/cdevents/spec/pull/291/ (Vote for approval next week)
- Links - https://github.com/cdevents/spec/pull/292
    - Examples needed for PR
- Cherry-pick s/version/schemaversion
    - Was able to release rust SDK
    - ~~Add CI test for json schema validator~~
        - Did not raise an error
        - Fix https://github.com/cdevents/spec/commit/5ac28b18ab8217313be8f81ea9c2c33ce85016d5
    - SDK consistencies
        - https://github.com/cdevents/sdk-rust?tab=readme-ov-file#features
- Devoxx French CDViz and CDEvents Talk (Paris - April 22-24)
    - Accepted - David
- Create GH issue for potentially replacing mdtoc with JS
    - When introducing new CI tooling/validation, please use JS.
- Data Ops (Victor Lu):
    - DOK (Database on Kubernetes)
    - Execution flow - core to orchestration
        - Diagram needed
            - Simple
            - Complex
- Approval event PR (next week-ish?) - Ben


### February, 3rd 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- Dadisi Sanyika, Sol Duara, Pacific
- Victor Lu, Independent, EST

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items:
    - Website (almost ready for review) - Ben
        - February 13th goal
    - Base event criteria
        - Must have subject, context, customdata as required fields.
    - SDKs will allow for hooks into the event lifecycle
        - Serialization, deserialization, sending via protocol, receiving via protocol (HTTP)
        - SDK refactor goal is end of the month 28th of Feb
    - Data op events
        - Data ops next Wednesday 11 EST
        - CDF Calendar (DataOps Initiative SIG)

### January, 27th 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- Dadisi Sanyika, Sol Duara, Pacific


Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items:
    - namespace for SDKs? https://github.com/cdevents/spec/issues/250
        - SDKs should enforce namespaces at the CustomData root level
        - Proposal for namespace - Dadisi
    - Base Event - https://github.com/cdevents/spec/issues/250 & https://github.com/cdevents/spec/issues/253
    - SDK proposal pattern - Ben
        - Proposal first then PR for Java SDK - Ben
    - Road map CDEvents for website - Ben
        - namespacing
        - base events
        - sdks
        - approval event - https://github.com/cdevents/spec/issues/243

### January, 13th 2026 (Americas)

Participants:
- Ben Powell, Apple, CST
- Dadisi Sanyika, Sol Duara, Pacific  

Links:
- [v0.6 Roadmap] needs a v0.6 roadmap
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged 
- Action Items
    - Mid December v0.5 was released
        - Some bugs regarding release reported by David
    - Website primer needs updating: https://github.com/cdevents/spec/issues/287
        - Needs to be synced with what is currently out
        - Needs concepts like namespacing at some point
    - How will namespacing work? - Low priority
        - Namespacing will need to a first class citizen in SDKs
    - SDKs need to be more user friendly
        - Create an issue outlining the overall design for SDKs/best practices/patterns
    - Verifiability
        - Next week CloudEvents meeting, should have updated verifiability PR

