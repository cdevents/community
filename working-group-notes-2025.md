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

### December, 16th 2025 (Americas)

Participants:
- Ben Powell, Apple, CST
- Luke Philips, MST
- Dadisi Sanyika, Apple, Pacific
- Name / affiliation / TZ

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
    - Meetings return in January
    - v0.5 waiting on Andrea to make the meeting to have Ben shadow the release.
        - Need to figure out how we can go about generating the SDKs in an automated fashion.
        - Are the SDKs automated in any fashion to make releasing them easier?
    - CDEvents clarifying semantics
        - PR (github broker will link later)
        - one final gloss over in the definitions
    - Have both SDK automation and clarity SDK done by February
        - Need a roadmap (2026)
    - Clean up website
        - https://cdevents.dev/docs/primer/ is outdated
        - Link definition from https://cdevents.dev/docs/primer/#terminology
    - Good patterns, practices, and guides with CDEvents
        - Like custom data and namespacing is not properly defined (2026 namespacing)
        - Source in subject, how are they used, for example (basic usage guides)
    - [Argo CDEvent](https://github.com/argoproj/argo-cd/pull/24106)
        - NA Argocon Luke will have some examples and how Argo works with CDEvents
        - Mapping CDEvents to a tool/service needs documentation.
            - Scalability of CDEvents, e.g. Spinnaker CDEvent production
            - Trials and tribulations talk for CDCon.
                - Start documentation of from when I first learned about CDEvents to integration to Spinnaker - Ben
    - Verifiability with CDEvents
        - No CloudEvent meetings til January
        - PR will be updated short with the added approach.
- \<addme\>

### December, 2nd 2025 (Americas)

Participants:
- Ben Powell, Apple, CST
- Luke Philips, MST
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
    - Ping Andrea about v0.5 release - Ben
        - Issues have been resolved and PRs merged, so v0.5 is ready to go
    - https://github.com/cdevents/spec/pull/276
        - Recommended using semvar library as opposed to writing our own
        - https://python-semver.readthedocs.io/en/2.9.0/usage.html
        - Always tests
        - Also ask to convert the full shell script to python
        - Get more information around his capstone project to ensure we dont include a library that does his work
- \<addme\>

### November, 4th, 2025 (Americas)

Participants:
- Ben Powell, Apple, CST
- Luke Philips, open, MST

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- https://github.com/cdevents/cdevents.dev/pull/53 - Expanding on test definition and what to do
    - Analysis seems to make more sense
    - Create a slack thread to hopefully encourage discussion
    - Otherwise we will merge this next week; contingent on discussion
- \<addme\>

### November, 4th, 2025 (Europe/Asia)

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- https://github.com/cdevents/spec/pull/270
    - need maintainer approval to merge
    - build script looks okay, but still need to test
- https://github.com/cdevents/cdevents.dev/pull/53
    - Test may need to be a more generic definition like analysis to add for things like security, and linting.
    - Open slack thread to add discussion - (Ben)
- Andrea to have context version to be renamed to specversion
    - Due by Friday
        - I will ping him on Friday, if unable, I'll do it - Ben
- Jenkins CDEvents plugin - v0.3 compatible (but unsure)
    - May need a migration tool or updated plugin for CDEvents
- \<addme\>

### October, 7th, 2025 (Americas)

Participants:
- Ben Powell, Apple, CST
- Luke Philips, open, MT ⛰️
-

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
    - v0.5 updates
        - Update linter for $id validation
        - Definitions PR https://github.com/cdevents/cdevents.dev/pull/53 | Oct 21st <Decision>

### October, 7th, 2025 (Europe/Asia)

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
    - Verifiability PR open to CloudEvents https://github.com/cloudevents/spec/pull/1371
    - v0.5
        - Internal PRs approved - (Ben)
            - $id will be consistent and PR will go out after this meeting
        - version to renamed to specversion - (Ben)
            - I can create a PR internally today, and probably get it out to OSS today.
        - Definitions PR https://github.com/cdevents/cdevents.dev/pull/53
            - Try to come to some decision by Oct 21st to close and/or merge
            - Website needs to be easily found in the spec repo
- \<addme\>

### September 30, 2025 (Americas)

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- Luke Philips, open, MT ⛰️

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- [Definitions PR](https://github.com/cdevents/cdevents.dev/pull/53/files?short_path=4535411#diff-4535411189be273207c49e284ff1310580e19cc01d842a0fde01f2bfb05c5e90)

### September 23, 2025 (Americas)

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- Luke Philips, open, MT

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Definitions: https://github.com/cdevents/cdevents.dev/pull/53
- Argo / cdViz example project: https://github.com/argo-multiverse-labs/local-cluster/tree/feat/cdviz/argo-cdviz
-

### September 23, 2025 (Europe/Asia)

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- v0.5 roadmap
    - Alignment of schema IDs https://github.com/cdevents/spec/issues/187
        - Ben: Open internally, waiting for approval from Apple legal
        - Linting rule to be added
    - Versioning: https://github.com/cdevents/spec/issues/112
        - Andrea: Not started working on it yet, should be able to work on it next week
- Look at outstanding PRs
    - https://github.com/cdevents/cdevents.dev/pull/53/files
    - Review needed
    - Where to put these definitions on the website
- CDEvents and GitOps
    - (luke adding a comment after the meeting): does CDEvents capture the '4 principles' of GitOps effectively? https://opengitops.dev/ (particularly a 'continuous reconcile loop')
- CDEvents and DataOps
    - SPDX being extended to "AIBOM"
    - DataOps WG is working on defining what is DataOps
    - OpenAPI has a new WG for Aync API
        - How to make a workflow work when there is a combination of APIs and events
    -
- Action for David: capture the discussion about GitOps vs. CDEvents
- Lesson learnt about reconciling GitOps with CI/CD CDevents

- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- \<addme\>


### September 16th, 2025 (Europe/Asia)

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review [v0.5 milestone](https://github.com/cdevents/spec/issues?q=is%3Aissue%20state%3Aopen%20milestone%3Av0.5)
    - https://github.com/cdevents/spec/issues/263
        - Upcoming PR by Ben with opinionated description of build
    - https://github.com/cdevents/spec/issues/112
        - WIP
    - https://github.com/cdevents/spec/issues/187
        - WIP
    - Targeting v0.5 in a couple of weeks
    - We need to update the website too!
- Releases
    - Document the process
        - For the spec
        - Website updates
        - Anything else?
    - Next time let's release in a zoom call

- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
    - update on the meeting links
        - https://github.com/cdevents/spec/pull/267
        - https://github.com/cdevents/community/pull/51
- \<addme\>




### September 9th, 2025 (Europe/Asia)
Participants:
- Ben Powell, Apple, CST
- Dadisi Sanyika, Apple, Pacific
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- Definitions and concepts (https://github.com/cdevents/spec/issues/263)
    - build removal should not be done, but definitions should be clear and opinionated
        - build != artifact.packaged
        - PR coming to define these concepts
- Update meeting times in repos (community) - Ben
- Think about dataops CDEvents (Victor)
    - Have clear and opinonated definitions - (Dadisi)
    - Contributing
        - Start with GH issue
- \<addme\>

### September 2nd, 2025 (Asia/Europe)

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2
-
Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- https://github.com/cdevents/spec/issues/263
    - ArgoCD - more gitops, e.g. do builds

### September 2nd, 2025 (Americas)
Participants:
- Ben Powell, Apple, CST
- Luke Philips, MT, open

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

### September 2nd, 2025 (Asia/Europe)

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2
-
Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- https://github.com/cdevents/spec/issues/263
    - ArgoCD - more gitops, e.g. do builds

```
CDEvents - v0.5 Release Candidate

Completed

1. Move from snake case to camel case
2. https://github.com/cdevents/spec/pull/171 (SBOM URI to artifact event)
3. https://github.com/cdevents/spec/issues/189 (remove subject.type)
4. https://github.com/cdevents/spec/issues/124 (content.outcome should be enum)

Pending
1. https://github.com/cdevents/spec/issues/187 (alignment of $id and context.type) - Ben
2. https://github.com/cdevents/spec/issues/112 (version is ambiguous) - Andrea
~~3. http://github.com/cdevents/spec/issues/109 (improve spec consistency)~~
~~4. https://github.com/cdevents/spec/issues/263 (remove build discussion) - Ben | David~~

Optimistic Goals

1. Approval events (proposal needed)
```

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Look at meeting calendar to make sure meetings aren't duplicated
    - CDEvents meeting may need region if it is missing. Need to check (Ben)
- v0.5 (progress)
    - ~~Was out last week, so was unable to create PR for subject.type removal (Ben)~~
    - subject.type removal done by David
- https://github.com/cdevents/spec/issues/263 (removing build)
    - instead of deleting we need to first define what the terms mean in CDEvents, e.g. build (Ben)
- Blog post for getting started
    - Will start work on this - Ben
    - Or maybe it does not need to be a blog but a "Getting Started" page in cdevents.dev
- \<addme\>

### August 19th, 2025 (Americas)

Participants:
- Ben Powell, Apple, CST
- Luke Philips, MT, open

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- A hello world for CDEvents
    - Consumers showing list of events coming through (potentially)
    - A blog post regarding this
- Luke talking cdEvents - https://sched.co/28D2u
- \<addme\>

### August 19th, 2025 (EMEA)

Participants:
- Andrea Frittoli, IBM, BST
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- https://github.com/cdevents/spec/issues/109
    - Proposal: deprecate build, to be replaced by task/pipeline/artifact events instead
    - David to comment on the issue
- All milestone issues assigned


### August 12th, 2025 (Americas)

Participants:
- Ben Powell, CST, Apple
- Luke Philips, MT, open
- Dadisi Sanyika, Pacific, Apple
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- v0.5 updates
- https://github.com/argoproj/argo-cd/pull/24106
    - Ask David about demo and cdviz bridge (Ben)
    - Review PR (Ben)
- \<addme\>

### August 4th, 2025

Participants:
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2
- Dadisi Sanyika, Apple, Pacific
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- Status of v0.5
    - https://github.com/cdevents/spec/issues/189 (remove subject.type)
        - https://github.com/cdevents/spec/issues/258 - Tests to enforce formats
    - https://github.com/cdevents/spec/issues/112 (is event versions really needed?)
        - To ping Andrea on this (Ben)
    - http://github.com/cdevents/spec/issues/109 (consistency)
- https://opentelemetry.io/docs/specs/semconv/registry/attributes/cicd/
    - Potentially use the same enums to be consistent with opentelemetry?
    - One issue it looks like that CDEvents is after the fact an event happened, versus open telemetry which says exactly when something is happening.
- \<addme\>

### July 28th, 2025

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- David Bernard, Alchim312/CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- v0.5 Release Candidate
```
CDEvents - v0.5 Release Candidate

Completed

1. Move from snake case to camel case
2. https://github.com/cdevents/spec/pull/171 (SBOM URI to artifact event)

Pending

1. https://github.com/cdevents/spec/issues/189 (remove subject.type)
2. https://github.com/cdevents/spec/issues/187 (alignment of $id and context.type)
3. https://github.com/cdevents/spec/issues/124 (content.outcome should be enum)
4. https://github.com/cdevents/spec/issues/112 (version is ambiguous)
5. http://github.com/cdevents/spec/issues/109 (improve spec consistency)

Optimistic Goals

1. Approval events (proposal needed)
```
- Moving to TZs WG
    - Move all SIGs to Tuesday
    - 9AM CST/15:00 UTC for Europe/Asia and merge with implementation SIG
    - 12PM CST for America (Need to ask PST folks)
        - If we dont get more people by end of year, we can remove this SIG meeting
- https://github.com/cdevents/spec/issues/252 will be main topic for next week
- \<addme\>

### July 7th, 2025

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, BST
- Adam Kaplan, Red Hat, EDT
- Luke Philips, MDT

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)


Agenda:
- New attendees
    - Adam Kaplan
    - Luke Philips
- Adam: idea for "Release" event
    - Previous Context
        - https://github.com/cdevents/spec/issues/152 (For bulk APIs)
        - https://github.com/cdevents/spec/issues/39 (Dependency updates through events)
    - What does a release look like?
        - It contains metadata
            - Link to an issue which describes release
            - Possibly list of vulnerabilities
            - Can be used to cascade software updates
        - Should it be a subject or a predicate to an existing subject?
        - How would tools react to this event? Is it for observability?
- Review roadmap
    - (Andrea) Plans for v0.5
- CDEvents and ArgoCD
    - https://github.com/argoproj/argo-cd/pull/13723
    - https://hackmd.io/@cdfoundation/SydQ9uDjT?utm_source=preview-mode&utm_medium=rec
    - Flux CDEvents receiver design: https://github.com/fluxcd/flux2/tree/main/rfcs/0006-cdevents
    -
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items




### Topics for coming meetings
- \<addme\>

### June 9th, 2025

Meeting Video: https://youtu.be/hWXtx4a-kGs?si=cNyv9EGNYE6jyKDB

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, BST
- Rajiv Singh

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- Conduit project
    - Presentation at cdCon
- Verifiability of events
    - CloudEvents Extension, proposed to CDEvents
        - More specific proposal
    - Also submitted to CloudEvent
        - More generic
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- \<addme\>



### May 19th, 2025
Participants:
- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+2
- Dadisi Sanyika, Apple, UTC-7
- Rasheed Mudasiru, KnowNow, WAT
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- [CloudEvents and CDEvents](https://github.com/cdevents/spec/issues/254)
    - Reach back out for more information and specify that we do, in fact, rely on CloudEvents FULLY but just using structured mode.
- [Interoperability Proposal](https://github.com/cdevents/spec/issues/253)
- \<addme\>

### May 5th, 2025

Participants:
- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+2
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
- Action Items
- [Namespacing Proposal](https://github.com/cdevents/spec/issues/250)
- [Source issues](https://github.com/cdevents/spec/issues/252)
- Links presentation to be worked on - Ben

### April 14th, 2025

- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Dadisi and Ben talk accepted at cdCon

### March 31st, 2025

- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
    - https://github.com/cdevents/spec/issues/247
        - Can work in tandem with implementations SIG to figure out how new events could work (Ben)
- Goals for CDEvents
    - Be more specific in the CDEvents, themselves.
        - For example, subject.source is too hand wavy
    - Start thinking about how swapping tool A for tool B a system has the exact same behavior (Interoperability).
    - More real world examples.
        - When a new events are added, real world examples should be provided
- Action Items
- \<addme\>

### March 24th, 2025

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+1
- Dadisi Sanyika, Apple, UTC-8


Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Look at [open issues](https://github.com/cdevents/spec/issues) to be triaged
    - Private namespace: https://github.com/cdevents/spec/issues/245
        - Guidelines for SDKs implementation of custom schemas are needed
        - Spec needs work if we wanted to support custom namespaces like `com.orgx....` type of events
        - Let's make a pseudo-code / use case proposal
        - We can use sub-issues on GitHub
        - Dadisi to create sub-issues for this
    -
- Review roadmap
- Look at outstanding PRs
- Action Items
- \<addme\>
- [Verifability proposal](https://github.com/cloudevents/spec/pull/1330) submitted to CloudEvents
    - One of supported frameworks https://github.com/secure-systems-lab/dsse

### Topics for coming meetings
- \<addme\>

### March 10th, 2025

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, CST
- David Bernard, CDviz, UTC+2
- Dadisi Sanyika, Apple, Pacific

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
    - https://github.com/cdevents/spec/pulls
- Supporting DORA
    - `change.committed`
    - https://github.com/cdevents/spec/blob/v0.4.1/source-code-version-control.md#change-created
    - This is the time where a developer starts working on a change, by creating the first commit
- Supporting private JSON schema for events outside of CDEventsX
    - Private JSON schema support outside of CDEventsx -- Private URIs
    - Are the SDKs aware of the `dev.cdeventsx.<namespace>-<subject>.<predicate>.<version>`?
- Action Items
- \<addme\>

### February 24th, 2025

Cancelled

### February 10th, 2025

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, CST
- David Bernard, - , UTC+2

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
    - https://github.com/cdevents/spec/issues/27 WIP
    - https://github.com/cdevents/spec/issues/215 removed from the sprint for now as it depends on the modelling language
- Approval events: https://github.com/cdevents/spec/issues/243
- Smithy:
    - Really focused on REST API, it requires a service, resources, etc
    - Smithy always generates everything, client, server, model
    - However validation logic may not be in the model, but in the client/server packages
    - Smithy relies on the plugin to know how things will look like on the wire
    - Ben: a model plugin exists, that might provide an answer to the points above
    - https://smithy.io/2.0/guides/using-code-generation/generating-a-client.html
- Look at outstanding PRs
- Action Items
- \<addme\>

### February 3rd, 2025

Participants:
- Name / affiliation / TZ
- Ben Powell, Apple, CST
- David Bernard

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
  - More inconsistency issues:
    - https://github.com/cdevents/spec/issues/188
    - https://github.com/cdevents/spec/issues/187
    - Need issue for naming convention linting (Ben)
  - Semantics need better clarity and definitions, esp. context attributes
      - Package URL: PURL format provides good examples on how its used
      - We recently moved our examples to conformance given they weren't really examples
          - However, we still need examples for end users.
          - Need issue (Ben)

### January 27th, 2025

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, CST

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Naming Conventions
    - We should have consistent naming in subjects
        - e.g. taskRun, pipelineRun, but... build
        - We should define that certain type of subjects use `Run` and other not so we are consistent in future
        - Related issue: https://github.com/cdevents/spec/issues/27
        - Ben to take ownership of the issue (added to the project)
- Review roadmap
    - Reviewed https://github.com/orgs/cdevents/projects/1/views/16
- Look at outstanding PRs
    - https://github.com/cdevents/spec/pull/238
        - Ben to ping Ole about this change
- Action Items
- \<addme\>

### Topics for coming meetings
- \<addme\>

### January 13th, 2025

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- David Bernard

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)
- [Outstanding PRs](https://github.com/cdevents/spec/pull/)

Agenda:
- New attendees
- Review roadmap
- Look at outstanding PRs
    - To be reviewed: https://github.com/cdevents/spec/pull/242
- Action Items
- \<addme\>

### Topics for coming meetings
- \<addme\>


### Spec and Implementation WG SIGs canceled until 2025
