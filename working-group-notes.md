---
tags: CDEvents
---

# CDEvents Working Group Meeting Notes

[![hackmd-github-sync-badge](https://hackmd.io/2FRGlw9fTMmKN1OQUVvguA/badge)](https://hackmd.io/2FRGlw9fTMmKN1OQUVvguA)

This document contains the notes from the [CDEvents Working Group](https://hackmd.io/lBlDCrL7TvmtNOjxdopJ5g).

## Meeting Details

### Schedule

- Tuesday meetings are held at [3pm UTC](https://time.is/3pm_in_UTC) during summer time and at [4pm UTC](https://time.is/4pm_in_UTC) during winter time)
- Monday meetings are held at [11am UTC](https://time.is/10am_in_UTC) during summer time and at [12pm UTC](https://time.is/11am_in_UTC) during winter time).

### Previous Years

- [2022 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2022.md)

### Template

Participants:
- Name / affiliation / TZ

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th

Agenda:
- Action Items
- <addme>

## Jan 16th, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Brad McCoy, Basiq, UTC+10
- Ole Lensmar, Kubeshop, UTC+1
- Bruno Lopes, Kubeshop, UTC+1

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th

Agenda:
- Action items from last week
    - Needs review https://github.com/cdevents/sdk-java/pull/12
        - Review comments need to be addressed
        - (Andrea) How are we planning the migration?
    - Spinnaker RFC ad-hoc meeting
        - Left a comment on https://github.com/spinnaker/governance/pull/299
        - Any more updates?

- Shall we archive meeting notes from 2022?
    - (Andrea) Create an archive file for CDEvents and SIG
    - (Andrea) Sync to GitHub, add link to past ones

- Test events
    - Proposal by Ole (TestKube) https://github.com/kubeshop/cdevents-spec/blob/main/testing-events.md
        - Moving events to a dedicated bucket
        - Tests can be executed outside of CI
    - Are CDEvents only for automated scenarios?
        - Not necessarily!
    - Agreed: Move test events to a new bucket
        - Update schema
    - Test types
        - Could be an enum
        - We could start with plain string
        - Work in the interop WG about standard naming

- Incident events
    - https://github.com/cdevents/spec/issues/59
    - ([@menehune23](https://github.com/menehune23)) proposed to start with a minimalist model
    - (Emil) We need a formal definition of incidents
    - Minimal data model (starting point)
        - Subject: Incident
        - Attributes:
            - ID, Source (mandatory in all subjects)
            - Environment (reference, mandatory)
            - Service or Artifact (reference, optional)
        - Predicates:
            - reported
            - resolved

- Conferences
    - cdCon CFP open, early bird ends Jan 17th
        - Feb 10th CFP deadline
        - https://cd.foundation/blog/2023/01/11/cdcon-2023-call-for-papers-now-open/

- Other updates?
    - Jenkins X
        - Starting back after holidays, next week meeting
    - Python SDK


## Jan 10th, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple
- Jalander Ramagiri, Ericsson Software Technology, UTC


Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th

Agenda:
- Spec Updates
    - Connecting events, [design](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA) WIP 

- SDK Updates
    - Golang
        - No updates
    - Java
        - Adam is working on it
        - Update to the continuous deployment events
        - Needs review: https://github.com/cdevents/sdk-java/pull/12
    - Python

- Tool Updates
    - Spinnaker
    - [RFC](https://github.com/spinnaker/governance/pull/299)
    - Proposal: setup an ad-hoc meeting to discuss and progress on the RFC

## Dec 19th

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC
- Erik Sternerson, dowhile, UTC+1
- 

Agenda:
- SIG Events meeting
    - Presentations
    - Interactions for other SIGs
    - Event architecture
    - Held on demand (if there is an agenda)
- Holiday meetings
    - Jan 2nd SIG Events, CDEvents Cancelled
    - Dec 27th CDEvents Cancelled
    - Next CDEvents WG Jan 10th
    - Next SIG Events meeting (if agenda) Jan 16th
- New timeslot for APAC friendly meeting since today
    - https://time.is/11am_19_december_2022_in_UTC

- (A) Andrea to track TOC presentation feedback in an issue
- v0.2 planning


## Dec 13th

Participants:
- Andrea Frittoli, he/him, IBM, UTC
- Emil Bäckmark, he/him, Ericsson, UTC+1
- Erik Sternerson, he/him, doWhile, UTC+1
- 

Agenda:

- Action Items
    - [New meeting time poll](https://doodle.com/meeting/participate/id/e1W8D43b)
    - [Top3 Issues for contributors](https://github.com/orgs/cdevents/projects/1/views/10)
    - [Connecting events](https://github.com/cdevents/spec/issues/104)

- cdevents.dev
    - PRs merged

- v0.2 roadmap

- Enforcing global config in the cdevents GitHub org
    -  github.com/github/safe-settings or github.com/probot/settings?

- Connecting Events
    - 

- Release Events
    - 


## Dec 7th

Participants:
- Andrea Frittoli, he/him, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Mattias Linnér, Ericsson, UTC+1
- Brad McCoy, he/hime, Basiq, UTC+10


Agenda:

- Meeting time
    - Current time on Wednesday is a permanent conflict for Erik
    - Alternatives (proposed by for Erik). Please vote with +1
        - Tuesdays at the same time or 
        - Tuesdays one hour earlier +2
        - Wednesdays one hour earlier +2
        - Wednesdays one hour later +2
        - Thursdays one hour later +1
        - Fridays almost any time
    - Andrea to make a Doodle
        - Ping Vibhav, Adam, Jalander, Salaboy, Hergy Tchuinkou, Christoffer Vig

- CDEvents presentation to TOC
    - Surface POC / videos on the website
        - Showcase CDEvents
        - Robert can help
    - Provide a top 3 list of things CDEvents needs help with
        - Maintain a list at all times
        - TOC can help advertise how to contribute to CDEvents
    - [Slides](https://github.com/afrittoli/cdevents_roadmap/blob/toc_update_202212/cdevents_roadmap.pdf)

- TOP three priorities (good candidates for new contributors)
    - Help with Java SDK
    - Help with Python SDK
    - Revamp POCs
        - Port existing POC to v0.1
        - Move to CDEvents GitHub org
        - Document on website

    - Other priorities, probably not good for newcomers
        - Incident events
            - Andrea working on it
        - Release events
            - Interest in contributing from IBM/RedHat
            - Release stage defined by SIG Interop: https://github.com/cdfoundation/sig-interoperability/blob/main/docs/pipelines-terminology.md#release-stage
        - Feature request events
            - Eiffel has issues events
        - These need more internal discussions to clarify what we want to do

- Connecting events
    - [Event Links](https://github.com/cdevents/spec/issues/10) 
        - Eiffel model
        - Database of events
        - Links with different semantics
    - Propagated Context
        - Issue to be created by Ben
            - https://github.com/cdevents/spec/issues/100 
        - If an event does not have a context, it generates one (UUID)
        - Events pass along a list(?) of contexts from "source" events
        - Context ID meant to be used to easily filter events
            - For the CloudEvents binding it could be a CE extension
    - Existing art
        - [Distributed tracing over CloudEvents](https://opentelemetry.io/docs/reference/specification/trace/semantic_conventions/cloudevents/)
            - OpenTelemetry defines a semantic convention for CloudEvents
        - [Trace Context RFC](https://www.w3.org/TR/trace-context/)
    - Span IDs
        - Honeycomb build events
            - https://user-images.githubusercontent.com/361454/57872910-ac9eea00-77c1-11e9-8bdd-db7a870dcd61.png
    - Linked events
        -
    - Use Cases:
        - Find vulnerabilities upstream
        - Visualise ditributed workflows
        - Metric collections 
    - Visualisation tools
        - Jaeger
        - Honeycomb
        - Aspecto https://www.aspecto.io/ 


- Release Events
    - 
