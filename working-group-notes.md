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
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- Action Items
- \<addme\>

### Topics for coming meetings

- Review proposal for demo system https://github.com/cdevents/community/issues/31


## Nov 20, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Ben Powell, Apple, CST
- Sean Brennan, Bloomberg, EST

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees

- Action Items

- (Adam) Flux CD Integration with CDEvents
    - Discussion held in Flux dev meeting
    - https://github.com/fluxcd/flux2/discussions/4339
    - Showcased a receiver & provider demo
    - Reciever (consumer) will get a PR up soon
    - The provider (producer) will need some more discussions before being implemented
    - Where should source change events be sent from, when Flux directly integrates with e.g. GitHub?
    - (Emil) The CDEvents protocol doesn't dictate who should send what event
    - (Emil) It's important that the same event is not sent from multiple producers. Events should be unique.
    - (Emil, Ben) The event should be sent as close to the source of the occurrence as possible. I.e. SCM related events should be sent from the SCM system if possible.
    - (Emil) It's up to the system integrator to decide what tool sends what events.

- (Jalander) Design approach [Gerrit CDEvents integration](https://github.com/rjalander/community/blob/main/rfc/gerrit-cdevents.md)
    - (Emil) Would it be relevant/helpful to also have Argo-events in this picture? https://github.com/argoproj/argo-events/issues/2841
    - (Andrea) We shouldn't maintain a lot of tool specific CDEvents implementations. With our limited community we need to take concious decisions on what tools to provide plugins or translators for
    - (Emil) Webhook vs Gerrit 'stream-event' (inbout vs outbound connection & https vs ssh)?

- Connecting & linking events
    - [PR](https://github.com/cdevents/spec/pull/139)

- Ticket/Approvals Proposal
    - [Tickets/issues](https://github.com/cdevents/spec/issues/164)
    - [Draft proposal](https://hackmd.io/9eTiXHu6RfedSuSwUMGTLw?both)
    - PR to be created

- (Andrea) Proposal for [Governance and Contributor Ladder](https://github.com/cdevents/community/pull/38)
    - Targeting final review at next CDEvents meeting

- Postponed to next meeting: (Andrea) Harbor integration & custom events
    - Artifact events https://github.com/cdevents/spec/issues/143
    - Custom events https://github.com/cdevents/spec/issues/168

- Java SDK updates
    - To be reviewed - https://github.com/cdevents/sdk-java/pull/60



## Nov 13, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, CST
- Sean Brennan, Bloomberg, EST
- Jalander Ramagiri, Ericsson Software Technology, UTC

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
    - Felipe Silveira, Farfetch
        - Focussed on CI/CD, ArgoCD, Workflow, Jenkins

- Action Items
- \<addme\>

- (Andrea) Proposal for [Governance and Contributor Ladder](https://github.com/cdevents/community/pull/38)
    - Once we have an agreed version we can
        - Start GB elections
        - Setup GitHub reviewes/maintainers teams and files

- (Andrea) Updates from KubeCon+CloudNativeCon NA
    - Make projects and companies available on the CDEvents website https://github.com/cdevents/cdevents.dev/issues/36
    - Harbor
        - Still supportive of CDEvents adoption
        - CDEvents notifications must cover all event types. For Harbor events that are not defined by the CDEvents spec
            - A schema should be defined
            - The schema could be maintained on Harbor side
            - Versioning to be clarified
            - Extension mechanism on CDEvents side
            - Proposal: https://github.com/cdevents/spec/issues/168
        - Other registries to look into
            - https://quay.io/ 
            - https://zothub.io/
    - CNCF App Delivery TAG
        - Still interested in CDEvents
        - Need contributors to work with Podtato Head
    - Argo CD / Workflow
        - Still interested in CDEvents
        - (Initial) implementation could be achieved via Argo Notifications
            - Use templates instead of SDKs
        - Met together with CNOE.io team repr
    - CNOE.io
        - IDP platform, very interested in CDEvents
        - Define capabilities as well as CNOE favourite set of tools
        - Would like to support interoperability
            - Make it easy to swap tools
            - Single language for a Backstage plugin to surface data to users
        - Would need IaaS events
        - Will help drive implementation in Argo CD/Workflow and possibly other tools
    - Guac.sh
        - Interested in ingesting SBOM through CDEvents
        - SBOM link in artifact events
            - Artifact type already in purl
            - SBOM type is not important for guac (for now at least)
        - Should try and include in upcoming v0.4
        - Interested in asyncapi.io / openapi definitions for CDEvents
    - Pelorus project for DORA metrics
        - https://github.com/dora-metrics/pelorus/
        - Related to https://github.com/dora-team/fourkeys ?
    - Harness
        - CDEvents integration may be technically simple
        - Engineering focussed on end-user demand, CDEvents not in scope yet
        - May be possible to build a POC in collaboration with Dev Advocacy
    - Dagger.io
        - Interested in pipeline observability
        - Looked into distributed tracing, however the lack of fan-in was a showstopper
        - CDEvents is an interesting alternative as long as it supports fan-in/fan-out
    - Some vendors associated the idea of interoperability with making it easiers for users to leave their platform
        - My take on this is that it also makes it easier for users to adopt their platform. Users should stay because the platform is excellent in solving their problem, not because of lock-in and attrition.
        - Ben: how do we alleviate that fear? Similar to early days of SQL.

- Connecting & linking events
    - [PR](https://github.com/cdevents/spec/pull/139)
    - New link type
        - Connecting of the graph
        - Attach metadata to nodes in the graph
        - Commit 1. New PR coming up to separate the two things
        - Commit 2. Adding optional links to context
        - Commit 3. Examples being added

- Tickets / Approvals
    - Probably two separate proposals
    - Tickets first, only a couple of outstanding questions
        - How to link tickets to anything else
        - Trying to envision how a consumer would use this events
        - We won't model the consumer workflow in the protocol
    - Next week or two ready for initial review

- Java SDK
    - Generating the SDK - review pending

- Flux
    - Flux integration work in progress
        - Planning to present to flux community this week or next

## Nov 6, 2023

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, CST
- Sean Brennan, Bloomberg, EST

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees

- Action Items
    - Ben, Add reviewers to Spinnaker FE PR

- [Hacktoberfest](https://github.com/cdevents/community/issues/35)
    - [Project](https://github.com/orgs/cdevents/projects/5/views/1)
    - No resolved issues this time

- CDEvents integrations
    - Project: https://github.com/orgs/cdevents/projects/4
    - Proposed implementations at Apple that could potentially be open-sourced if the community is interested
        - Event bus - with authentication/autorization
        - Collector - for collecting events in a distributed way. Might not be needed at this stage, before we reach a certain scale of events sent
        - Links service - for connecting events
        - Events storage - for storing and retrieving events
    - Does the CDEvents SDK propagate for any specific infrastructure?
        - No, they should all be based on the corresponding Cloudevents SDK

- Connecting & linking events
    - [PR](https://github.com/cdevents/spec/pull/139)
    - (Andrea) Fan-out/fan-in support
        - Supported today through links
        - It would be nice to support through CDEvents context alone
            - What about adding a list of parent_ids into the context (together with chain_id) for a simple solution for fan-out/fan-in?
            - Alternative add the link list into the context?
        - NIT: could we call the chain_id a graph_id

 

- \<addme\>


## Oct 30, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, he/him, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Sean Brennan, Bloomberg, UTC-4

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees

- Action Items
    - Andrea, Meeting times :heavy_check_mark: 
    - Andrea, create [an issue](https://github.com/cdevents/spec/issues/165) about deprecations :heavy_check_mark: 
    - Ben, Add reviewers to Spinnaker FE PR

- Meeting recordings
    - New notification in the #cdevents channel

- LF Member Summit Updates (Andrea)
    - [Presentation](https://lfms23.sched.com/event/1S3Ae/unlocking-the-potential-how-standardization-empowers-security-in-modern-software-factories-andrea-frittoli-ibm)
    - Possible collaboration with Guac / OpenSSF
        - [Guac](https://guac.sh/) provides storage for supply chain documents, needs data/context with events in the CI/CD pipeline
        - CDEvents could provide that link
        - [Prototype by Michael Libermann](https://github.com/kusaridev/sscp/tree/main)

- CDEvents mentioned in CNCF slack channels
    - #aep
    - #cicd-o11y (opentelemetry)

- CNOE https://cnoe.io/ 

- Cloud Native Telco Day
    - Andrea - [CDEvents lightning talk](https://sched.co/1Rj5Y)

- CDEvents integrations
    - Project: https://github.com/orgs/cdevents/projects/4
    - GitHub action repo https://github.com/cdevents/community/issues/28
    - Andrea to follow up on potential JFrog integration

- Connecting Events 
    - [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - New PR version to be reviewed

- Ticket/Approvals Proposal
    - [Tickets/issues](https://github.com/cdevents/spec/issues/164)
    - [Draft proposal](https://hackmd.io/9eTiXHu6RfedSuSwUMGTLw?both)

- Planning for v0.4
    - Proposal: aiming for a v0.4 by the end of November
    - In time for cdCon Japan Dec 4
    - Scope:
        - Connecting events
        - SBOM link in artifact events
            - Do we need to store the format of the SBOM?
            - Ortelius registry link?

- Implementing CDEvents
    - Is there any guidance about implementing CDEvents
    - Setting up topics
    - Architecture
    - Emil: no experience in prod with CDEvents, but could share best practices about Eiffel
    - Fidelity and SAS may have some insight
    - CDF User Stories https://cd.foundation/user-stories-and-whitepapers/
    - CDF Best Practices https://bestpractices.cd.foundation/
        - CDF Reference Architecture  https://bestpractices.cd.foundation/architecture/
    - CDEvents https://cdevents.dev/docs/primer/
        - We could expand on the primer

- \<addme\>


## Oct 23, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, he/him, IBM, PDT
- Ben Powell, Apple, CST
- Emil Bäckmark, Ericsson, UTC+2
- Sean Brennan, Bloomberg, EST
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Owen Bower Adams, Intelligent Growth Solutions, BST

[Meeting Recording](https://youtu.be/8x1HWvTKqXs?si=zbOfoJHU9qg0X-DK)

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/4)

- New meeting schedule (reminder)
    - CDEvents: Every Monday at 3pm UTC (Summer) / 4pm (Winter)
    - Every 4 weeks APAC friendly meeting at 11am UTC (Nov 27th ->)
    - DST in Americas end on Nov 5: https://en.wikipedia.org/wiki/Daylight_saving_time_in_the_United_States
    - DST in Europe end on Oct 29: https://en.wikipedia.org/wiki/Summer_time_in_Europe#Table_of_transition_dates_for_European_Summer_Time
    - Andrea to propose the exact time for next week on slack (1h later for EU timezone)

- Connecting Events 
    - [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - Ben to address comments on the links section
    - Ben will update the PR with schema updates (all events)
    - Ben plans to create a mock CI/CD system to demonstrate links to demonstrate CDEvents at Apple

- Ticket Proposal
    - Sean and Ben met weekly to discuss about this
    - Approvals
        - Dedicated subject or use the tickets subject
        - At Apple: an approval is every time a manual approval is involved
        - Good for auditing
            - Example, during freeze, two step approval process is required
        - Emil: at Ericsson, approval is only at review time
        - Alternative: add "approved" preticate to all (many) events
        - Ben and Sean to identify pros/cons of the two options
            - A new "approval" subject (declined, accepted?, in progress)
            - Add "approval" predicate to several existing subjects
    - [Tickets](https://github.com/cdevents/spec/issues/164)
        - ticket subject
        - Predicates could be what happened or the ticket state
        - Emil: workflow can be customised per project/team, predicates should not dictate the workflow names
    - Approvals
        - Owen:
            - Automated approval can be part of the model
            - An approval can come from humans or machines or a combination
            - It would be good to include this in the "approval" subject docs
        - Emil:
            - PRs can be automatically approved if they are small enough

- PR Reviews
    - https://github.com/cdevents/spec/pulls

- Deprecation of fields
    - Option1 - Document on the markdown, define an ETA for removal
    - Option2 - Keep the deprecate fields forever
    - Option3 - Just update the version and drop the field
    - [Related PR](https://github.com/cdevents/spec/pull/162)
        - PR not urgent, good to use to define the deprecation process
    - Action Andrea to capture this in a ticket

- SDKs Updates
    - Java
        - Part 2 of generating the SDK to be reviewed
        - https://github.com/cdevents/sdk-java/pull/60
    - Rust
        - Scaffolding started as part of Hacktoberfest
    - .NET
        - Owen: have been working wih a manually generated .NET SDK for a couple of months. Work is starting on a generated version.
    - Ben: what languages are tools written in?
    - Swift used heavly at Apple

- CDEvents Use Cases
    - Owen to present internal use cases for CDEvents (added to the agenda in a few weeks)

- Spinnaker
    - Ben to add reviewers to the Front End PR

- \<other topics, please add\>


## Oct 9, 2023

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC+1
- Jalander Ramagiri, Ericsson Software Technology, UTC+1


Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/4)

- New attendees

- Adam working on a Flux integration
    - Jalander: Plan to include in the original POC
    - Emil: should we have a dedicated POC instead?
    - https://github.com/orgs/cdevents/projects/4
    - Adam to file an issue on CDEvents side

- Connecting Events 
    - [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - Emil: Call for reviews!

- Proposed New Meeting Schedule:
    - CDEvents APAC meeting, 10am UTC, every 4 weeks on Monday, starting 30/10
    - CDEvents EMEA/NA meeting 1, 3pm UTC, every other Tuesday, starting on 17/10 (no change!)
    - CDEvents EMEA/NA meeting 2, 3pm UTC, every other Monday, starting on 09/10 (takes the slot that used to be SIG Events)
    - SIG Events, 3pm UTC, every 4 weeks on Monday, starting 16/10 (same time, different week)
        - Topics that are broader than CDEvents, e.g. VSMI or events in general

- PR Reviews
    - https://github.com/cdevents/spec/pulls
    - URL to URI https://github.com/cdevents/spec/pull/162
        - Version numbers ok now
        - Will the backwards incompatible change cause issues for SDKs?

- SDKs Updates
    - Java
        - Part 1 of generating the SDK is merged
        - Part 2 to be reviewed?

- Spinnaker integration
    - Jalander working on addressing review comments
    - 

- Ben: can we add links to recording in these notes?
    - Andrea to share the link to the videos

- \<other topics, please add\>


## Oct 3, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST
- Emil Bäckmark, Ericsson, UTC+2
- Daniel Han, Bloomberg, EDT

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/4)

- New attendees
    - Sean Brennan - Bloomberg
        - E2E visibility
        - Automation in pipelines

- Discuss introduction of new ticket/issue events, with Sean Brennan, base on [Slack chat](https://cdeliveryfdn.slack.com/archives/C030SKZ0F4K/p1695312825361389)
    - Also detailed in [issue 164](https://github.com/cdevents/spec/issues/164)
    - Sean: Product approvals through issues
    - Ben: CDEvents for ticketing systems needed at Apple
    - Link between PRs and issues
        - At bloomberg: Jira ID in the PR title
        - Emil: at Ericsson, specific syntax in the commit message
        - Andrea: CDEvents should define the data model of how tickets and CSM/other events are connected
    - What does the data model look like?
        - Possibly a ticket subject
        - Several events:
            - Create event is needed
            - Ben: we will need a "resolved" event too. It would be important for deploy/rollback use cases
            - Sean: updates / transition events, e.g. approval
            - Do we need to track all ticket events?
                - Emil: we should not replicate the whole data model of ticketing systems
                - Ben: we can optional components of the tickets spec
                - Sean: if we define events, consumers may use those they need
        - Daniel: identify the bare minimum data model we can start with
            - We can add more fields, but we need to be careful and not to slip into adding too much
    - Next steps:
        - Example proposals
            - Testing events https://github.com/cdevents/spec/pull/126
            - Incident events https://github.com/cdevents/spec/pull/107
        - Sean and Ben to collaborate on getting this started

- Meetings Schedule Review
    - Weekly alternate times
    - SIG Events bi-weekly
    - Proposal for new meeting schedule
        - Every other Monday and every other Tuesday
        - Reduce APAC meeting to monthly/optional

- OTel proposal
    - [OpenTelemetry and CDEvents](https://github.com/open-telemetry/oteps/pull/223)
    - Ben cannot share example payloads from Apple about how CDEvents would work at Apple

- [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - Ben to document advantages of using separate link events

- [Hacktoberfest](https://github.com/cdevents/community/issues/35)

- PR Reviews
    - https://github.com/cdevents/spec/pulls

- SDKs Updates
    - Java
        - Part 1 of generating the SDK is merged
        - Part 2 to be reviewed?


## Sep 19, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli. IBM, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/4)


- New attendees

- OTel proposal
    - [OpenTelemetry and CDEvents](https://github.com/open-telemetry/oteps/pull/223)

- [Connecting/linking events](https://github.com/cdevents/spec/pull/139)

- [Hacktoberfest](https://github.com/cdevents/community/issues/35)

- PR Reviews
    - https://github.com/cdevents/spec/pulls

- SDKs
    - 

## Sep 19, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, he/him, IBM, UTC+1
- Ben Powell, Apple, CST
- Daniel Han, Bloomberg, EDT
- Emil Bäckmark, Ericsson, UTC+2
- Dotan Horovits, Logz.io, CNCF, UTC+3
- Adam Kenihan
- Evan Elms

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)


Agenda:
- New attendees

- Action Items

- Focus on "Tracing with CDEvents"
    - with Dotan Horovits, [OpenTelemetry and CDEvents](https://github.com/open-telemetry/oteps/pull/223)
        - A new OTEP to add CI/CD observability semantics to OpenTelemetry 
    - Dotan presented
        - Brief intro to OTel
        - Main uses case is monitoring a production system
        - Monitoring the release pipeline is just as critical
        - Otel plugin for Jenkins shows some pipeline data: https://plugins.jenkins.io/opentelemetry/ (in proprietary format)
        - OTel is not just for distributed tracing, but also to monitoring and logging
        - Blog post: https://logz.io/learn/cicd-observability-jenkins/
        - The [PR](https://github.com/open-telemetry/oteps/pull/223) focuses on the modelling part ([read it in repo](https://github.com/horovits/oteps-cicd-o11y/blob/95672d53dc2bf9d13ecee737ac85e7236da1437c/text/0223-cicd-observability-OTEP.md))
        - OTLP allows to transmit OTel data within other protocols
        - OpenObservability Talks podcast episode on observability in CI/CD pipelines, hosting Oleg Nenashev: https://podcasters.spotify.com/pod/show/openobservability/episodes/Continuous-Observability-Shedding-Light-on-CICD-Pipelines---OpenObservability-Talks-S3E02-e26p5fk
    - Questions
        - Where should the border between CDEvents and OTel be? What should be notified with what technology/protocol?
    - Next steps
        - Andrea to call for a separate session to continue the discussion on OTel & CDEvents
        - It would be great to have a simple PoC showcasing how we can manage this


- [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - Ben will add example payloads to the sequence diagram events, for clarity
    - Also add some pros/cons on keeping the relation object as a separate event compared to including it as an optional array of relations within the events
    - Consider architectural differences

- [Hacktoberfest](https://github.com/cdevents/community/issues/35)
    - Not many issues labeled yet

- SDK Updates

- Integration updates
    - Tekton: [proposal merged](https://github.com/tektoncd/community/pull/1046)


- 


## Sep 11, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Andrea Frittoli, IBM, UTC+1
- Victor Lu

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
- Action Items

- Visualisation POC (@SIG Events meeting)
    - PR: https://github.com/cdevents/visualisation/pull/1
    - GitHub Action with hosted worker
    - Visualization independent from tools
    - Two kind of visualization tools
        - CDEvents specific
        - Generic (Grafana based)
    - Dependency to the link model
        - Current assumption do not affect the visualisation codebase much
        - Data collection part depends on the link model
    - [POC Demo Recording](https://youtu.be/KIGhmPQ2V9c)

- (Victor) Comparison of different CI/CD
    - It would be nice to have a comparision table to understand which tool can be used for what
    - Discussion forum would be helpful too

- [Hacktoberfest](https://github.com/cdevents/community/issues/35)
    - Action for all: label issues for hacktoberfest

- [Release Planning](https://github.com/cdevents/spec/milestone/4)
    - A few PR were merged
    - We could make a release if it takes too long for connecting events to be implemented

- SDK Updates
    - Java v0.1.2 released
    - Dotnet SDK
        - [obowersa](https://github.com/obowersa) plans to contribute the SDK
        - [slack thread](https://cdeliveryfdn.slack.com/archives/C030SKZ0F4K/p1692915343895089)
        - Would be good to plan a presentation / discussion in the CDEvents WG

- Integration updates
    - Tekton: [proposal approved](https://github.com/tektoncd/community/pull/1046)
    - Harbor: [proposal pending approval](https://github.com/goharbor/community/pull/229)
    - Argo CD: [draft proposal](https://github.com/argoproj/argo-cd/pull/13723) - next step is building a POC, Andrea to follow-up
    - Spinnaker: PRs pending reviews 
        - https://github.com/spinnaker/deck/pull/9997
        - https://github.com/spinnaker/echo/pull/1295

- [Connecting/linking events](https://github.com/cdevents/spec/pull/139)
    - Ben has some action items to update the PR based on the latest discussion
    - List of parent ids to be removed for now and potentially added back later on


- \<addme\>


## Sep 5, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST

Agenda:
- [Connecting/linking events](https://github.com/cdevents/spec/pull/139), using trace spans
    - [How to create/finish spans](https://github.com/cdevents/spec/pull/139#issuecomment-1696934569)
        - We could hide the complexity of calling a Links Service, when producing events, within the SDK.
        - Having a links service as part of producing an event adds a synchronous/blocking call, unless the links service is also called through the asynchronous message bus
    - [Specific or generic relations types](https://github.com/cdevents/spec/pull/139#discussion_r1305661282)
    - Links/relationships between events is critically important if not all info relevant for a consumer is contained within a specific event.
        - Should a service.deployed event contain all relevant info from artifact.packaged and change.merged event, or should the relationships between the events be used to find that info.
    - What should the global id / trace id be called?
        - Global id, Trace id, Context id, Trail id, Lifecycle id, ...
        - Ben will create a poll on CDEvents Slack to vote for the right term
    - For now the parent id will be removed from the [PR](https://github.com/cdevents/spec/pull/139), just keeping the global id in there.
    - To be discussed further and eventually decided on:
        - Should the relationships/links be contained in the Links Spec and event data in CDEvents spec, or should it all be combined in the CDEvents spec?
            - Span id to be the only relationship to keep in the CDEvents spec, and the rest of relationships in the Links spec?
            - Separating the data from relationships introduced a dependency between the two, both ways, and they need to evolve hand-in-hand

- Hacktoberfest
    - https://github.com/cdevents/community/issues/35
    - Let's label more issues
    - https://docs.google.com/document/d/1IxVtP7GTm0NqwIn98pLSHONKllbzm0kVRmURn8x394w/edit
    - Ben will create/identify some issues and ask Emil/Andrea to label them.


## Aug 28, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Brad McCoy, Basiq, UTC+11
- Adam Kenihan, UTC+1

Agenda:
- Incident Events
    - (Brad) shows an implementation of incident.reported event with Atlassian Jira

- GitHub Actions
    - (Brad) Working on GitHub actions as well (TestKube folks interested)
    - GitHub actions runner (self-hosted runner). Could either pull or push.
    - https://github.com/cdevents/github-action

- OpenTelemetry integration. Not much news. Looking forward to discussion on Sept 5.


## Aug 22, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Daniel Han, Bloomberg, EDT
- Evan Elms
- Name / affiliation / TZ

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4). Will most certainly be delayed.

Agenda:
- New attendees

- Action Items

- [Hacktoberfest 2023](https://hacktoberfest.com/)
    - [Hacktoberfest on CDF Website](https://cd.foundation/hacktoberfest/)
    - [CDEvents Hacktoberfest issue 2022](https://github.com/cdevents/community/issues/7)
    - [CDEvents Hacktoberfest project 2023](https://github.com/orgs/cdevents/projects/5/views/1)
        - Emil to notify CDF about the new issue link once its there
    - Items to add
        - Ideas from Microcks presentation? https://github.com/cdevents/spec/issues/148
        - Visualization?
        - Python SDK?
            - Code generation
            - Putting it on PyPi
        - Other SDK improvements?
            - Daniel to write an issue about code generation for e.g. Python/Go (could relate to https://github.com/cdevents/sdk-go/issues/24)
        - Generate DB schemas for the events?
        - Client hooks for SDK usage
            - Create github issue (Ben)

- [Connecting Events PR](https://github.com/cdevents/spec/pull/139)

- Visualization proposals
    - https://github.com/cdevents/presentations/blob/main/CDEvents-Visualisation/CDEvents_visualisation_types.pdf
    - A demo of the current state of the visualization PoC to be presented on SIG Events next week

- Other current PRs and issues
    - Java SDK generator https://github.com/cdevents/sdk-java/pull/58/
    - Spinnaker integration 
        https://github.com/spinnaker/deck/pull/9997
        https://github.com/spinnaker/echo/pull/1295
        Ben will invite reviewers to these reviews

- \<addme\>


## Aug 14, 2023

**Meeting canceled since no one showed up**


## Aug 8, 2023

Participants:
- Andrea Frittoli, IBM, UTC+1
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Tracy Ragan, DeployHub / Ortelius
- Adam Kenihan

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
- Action Items

- [Hacktoberfest 2023](https://hacktoberfest.com/):
    - From CDF TOC meeting:
        - Roxanne wants to know by August 31st
            - Which projects plan to participate
            - Blog posts need to be live and sent to CDF by September 29th
            - Project contact persons need to be identified
        - Hacktoberfest 2022 info on [CDF Website](https://cd.foundation/hacktoberfest/)
        - Ideally list of participating projects and contact persons by next TOC meeting on Aug 15th
    - Shall CDEvents participate?
        - It requires a little bit of initial investment, but not too much
        - The more we invest, the better the return, see Jenkins 2022 https://www.jenkins.io/events/hacktoberfest/	
        - It requires extra review bandwidth during the event
        - Good for new reviewers and prospective reviewers to refine their skills and build review numbers
        - It usually brings mostly occasional contributors, but it may help us tackling our bug backlog and implement small improvements on docs, tools and website
    - If we participate, we need:
        - One person driving the effort (contact for CDF)
        - List of interested CDEvents projects, and project/areas ideas
        - A blog post or github issue
        - Ideally (but optional) list of interested reviewers / mentors
    - Tracy:
        - We should participate
        - Happy to write a blog post
        - Security Events?
        - Point of contact for the CDF
    - Ben: security events might be too much for hacktoberfest
    - Emil: hacktobefest should be easy to review
    - Topics:
        - Ben:
            - SDK code generation, modelling
            - Documentation
            - Abstraction layers
        - Andrea:
            - CLI
            - Autogeneration of docs
            - Investigate async
    - 2022 Project: https://github.com/orgs/cdevents/projects/3/views/1

- [Connecting events](https://github.com/cdevents/spec/pull/139)

- [v0.4 Release](https://github.com/orgs/cdevents/projects/1/views/13)

- v1.0 release

- \<please add\>


## July 31, 2023

Participants:
- Andrea Frittoli, IBM, UTC+1
- Neil McGonigle, Fidelity, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
- Action Items

- Request for reviews:
    - [Connecting events](https://github.com/cdevents/spec/pull/139)
    - [OpenTelemetry and CDEvents](https://github.com/open-telemetry/oteps/pull/223)

- Java SDK v0.1.2 released


## July 25, 2023

Participants:
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, UTC+1
- Daniel Han, Bloomberg, EDT
- Neil McGonigle, Fidelity, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
- Action Items

- (Ben) New *optional* fields for change events
    - [created change event should contain a top level description](https://github.com/cdevents/spec/issues/151)
    - [commit array should be present in change events](https://github.com/cdevents/spec/issues/150)
    - [Branch info in change events](https://github.com/cdevents/spec/issues/149)
    - Bundle artifacts are required to avoid sending one event for each single artifact
        - Example deployment @ Apple with 500+ artifacts
        - This is a single deployment, and there are many deployments

    - Ben: adding more fields, but make them optional
        - Note: optional -> mandatory is a breaking change
        - Requiring API Calls is not good for interoperability as they shift the issue of interoperability
    - Dan: for test cases we have testcaserun which could generate 1000s if events
        - How would bundling help? 
    - Dan: is there a cadence for releases
        - Andrea: We are automating the SDKs updates
        - Andrea: Currently we plan releases on demand, we could switch to a regular cadence if we have enough contributions
        - (A) Andrea to make a proposal for regular release candence
    - Ben: How do we help people transition from customData to CDEvents data
    - Daniel: we could add helpers/adapters in the SDK that help with that
    - (A) Ben to create an issue to track this discussion

- (Ben) Not all data in events can be disclosed to everyone
    - Some team cannot broadcast their events to all
    - Identity of sender
    - Ben to create an issue
    - Dan: can we have an FAQ page, recommendation about things
        - How do I deal with security
        - How do I add data to the subject
        - Can be open-ended i.e. we have the question, not the answer yet
            - Andrea: we have the [primer](https://cdevents.dev/docs/primer/) today, but that does not answer specific questions
            - Ben: it should not be in the spec
            - Daniel: create an issue

- (Ben) What about Ticket/Feature/Issues
    - Brad McCoy is interested in this feature
    - Steve Pereira from VSMI

- Connecting Events

- Bundling of events
    - Daniel: Binding events in the some format, so that they are sent out all together, it could help consumers connect the dots
    - 


## July 17, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
- Action Items
    - (Andrea) Create a repo for the visualisation reference architecture and poc
        - https://github.com/cdevents/visualisation/
    - (Jalander) Share slides at https://github.com/cdevents/presentations
        - https://github.com/cdevents/presentations/pull/25

- [Support of custom types](https://github.com/cdevents/spec/issues/147)


- How does CDEvents fit with the big platform picture?
    - We should add diagrams to document the big picture

- What about CDEvents and software supply chain
    - We have artifact signed event today
    - We want to have more, looking to collaborate with OpenSSF

- \<addme\>


## July 11, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, UTC+5
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- 

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
    - 
- Action Items
    - (Ben) Meeting with Spinnaker for CDEvents demo
        - Ben to create the meeting in the next ~1w
        - Invite Spinnaker team as optional
    - (Andrea) Create an issue / doc / slack channel to discuss artifact events
        - Issue: https://github.com/cdevents/spec/issues/143
        - Design doc: https://hackmd.io/AfT-5D3JQZynKk5yDyAWeA?both
        - Slack channel: #cdevents-artifacts

 
- CDEvents Visualization - Reference Architecture
    - (Jalander) Share slides at https://github.com/cdevents/presentations
    - (Andrea) Create a repo for the visualisation reference architecture and poc

- Connecting Events
    - [PR](https://github.com/cdevents/spec/pull/139)
    - (Andrea) How do we handle proposals?
        - Switch to hackmd
        - Add a proposal folder in the spec repo
        - Use a separate repo
        - Else?
    - (Andrea) Trying to visualise the connecting events proposal in a simple example
        - ![](https://hackmd.io/_uploads/SJXvCnqt2.png)
        - ![](https://hackmd.io/_uploads/Hysk60cFh.png)

        - How do we carry the context?
            - Where global_id, parent_id and links come from in each step?
        - How does each of those help us in connecting those three events



## June 30, 2023


Participants:
- Victor Lu
- Ben Powell
- Emil Bäckmark
- Andrea Frittoli

Agenda: Session dedicated at Connecting Events

- [PR](https://github.com/cdevents/spec/pull/139)
- Review of comments on the PR, discussion tracked in comments
- We could use some of the nomenclature from the [VSMI reference arch](https://docs.google.com/presentation/d/16-c-Kui3LKmiIc54N7f_4tebTt-zcbCnKDypksT5WRo/edit#slide=id.p)
- 

## June 27, 2023

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+2
- Fatih Degirmenci, CDF, UTC+2
- Tracy Ragan, DeployHub / Ortelius
- Daniel Han / Bloomberg / NY
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Neil McGonigle, Fidelity, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- New attendees
    - Carmit from JFrog

- Action Items
    - (Ben) Meeting with Spinnaker for CDEvents demo
        - The PR is being reviewed
        - Meeting still TBD

- SDK Updates
    - Golang: v0.3.2 patch release
        - Fix the CDEvents spec version
        - Set CloudEvents Id
    - Java:
        - Release v0.1.2 - ready to be done
        - Generating the SDK

    - Security Events:
        - Ortelius and GUAC talking to develop security use cases / events

- Tools Adoption Updates
    - Harbor:
        - Proposal: https://github.com/goharbor/community/pull/229
        - Implementation: https://github.com/goharbor/harbor/pull/18853
        - Demo
    - Tekton:
        - [Enhancement Proposal](https://github.com/tektoncd/community/pull/1028/files?short_path=bae3223#diff-bae3223ff38b679c88bd900ea859b210404aa243536087b842df3324d825f957)
    - ArgoCD: 
        - [Proposal](https://github.com/argoproj/argo-cd/pull/13723)
    - Spinnaker
        - PR being reviewed
    - Testkube
        - (Andrea) Reach out to Ole for updates

- CDF Online meeting
    - Testkube team presented, including CDEvents
    - Available on youtube playlist https://youtu.be/d2BRv3sY2A8

- Artifact events
    - Carmit:
        - Events produced by an artifact registry
            - bundling of artifacts
            - promotion of artifacts/bundles
            - distribution
            - release
    - Dan: 
        - Tagging of artifacts as event
    - Carmit: 
        - Generally events should contain only event data
        - More data about the artifact can be pulled via APIs
    - Emil: What is the bundling of events specifically
    - Carmit: a bundle is a group of artifacts (like docker image, helm chart etc), a bundle can inculde up to 1k artifacts
    - (Andrea) Create initial tickets to track the events
        - Link issues about events to artifact registries
            - https://github.com/cdevents/spec/issues/143 
    - Artifact pull/pushed/deleted but also moved (for artifactory)
    - Artifact scanning events are security type of events and should be produced by the tool the perform the security scan
    - Quota events in Harbor may not be good candidates for CDEvents
    - Archiving may be relevant from an audit trail point of view, less relevant from and SDLC point of view
    - Tags could be used to indicate that an artifact is ready for promotion or deployment

    - Emil: start a document about events from registries
        - Capture events for different artifact registry
        - Collaborate on the document
        - Use this document as input for the specification work
        - Create a slack channel for artifact registry specific discussions

- Issue tracking events
    - Carmit: it would be interesting to have those associated with artifacts

- Spec Topics
    - Connecting Events
        - [PR](https://github.com/cdevents/spec/pull/139) ready for review

- Collaborations
    - VSM Interoperability
        - New monthly meeting for CDEvents + VSMI collaboration
        - [Meeting Notes](https://hackmd.io/Du6iay8PTyypWchaINsRiA)
            - Steve introduced the VSMI Topology and Ontology
            - CDEvents is part of picture
    - CNCF App Delivery TAG
        - Looking for contributors to drive/work on a version of podtato-head based on CDEvents

- CDEvents visualisation

- \<addme\>


## Jun 19, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Neil McGonigle, Fidelity Investments, UTC
- Andrea Frittoli, IBM, UTC+1
- Name / affiliation / TZ
- 

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)


Agenda:
- Action Items
    - Ben to arrange a meeting with Spinnaker team for CDEvents demo

- (Brad) Update on GitHub action for CDEvents
    - Mock end point implemented
    - Testing different example, getting ready for first version
    - To be presented in the next version

- (Brad) Events for featureas and issues
    - CDEvents in scope for features and issues?
        - Issues can be associated with incidents as well
        - Related to VSM interop
        - Related to connecting events discussion
        - Source code events could be associated to issues/features delivered in a certain code change

- (Andrea) Harbor proposal [pull request](https://github.com/goharbor/community/pull/229)
    - Changes on CDEvents side [may be required](https://github.com/cdevents/spec/issues/143)
    - (Emil) We should be consciuous about the use cases associated with events when adding new events
    - (Emil) Are events related to CD? We don't have a definition today of what is in scope for CD
        - Relevant for triggering a CI/CD workflow
        - Relevant for observation of a CI/CD overall workflow
    - (Emil) We should invite JFrog to the conversation about relevant events for artifact registries
    - (Neil) What kind of events (if any) does artifactory support today?

- (Andrea) Parent-child pipelines use case https://github.com/cdevents/spec/issues/142
    - (Emil) Is this within a pipeline execution or upstream/downstream dependencies?
    - (Emil) Example: a test step is replaced with a call to an external test system which may have its own pipeline and events. How do events from the test system refer back to the original pipeline?

- v0.4 Planning (in progress):
    - [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - [all in roadmap](https://github.com/orgs/cdevents/projects/1/views/8)
    - [issues in CDEvents org not labeled with roadmap](https://github.com/issues?page=1&q=is%3Aopen+is%3Aissue+archived%3Afalse+user%3Acdevents+-label%3Aroadmap)



## Jun 13, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- Action Items (None)

- CDF TOC:
    - Voting for the CDF TOC representatives ongoing
    - Please vote if you're eligible!

- CDF Outreach Committee:
    - Proposed project updates:
        - CDEvents, a common specification for Continuous Delivery events: it drives interoperability and brings disruption in the CD ecosystem with a growing and active community. Contributors from 20 companies, 142 twitter followers, 85 GitHub stars.
            - Releases v0.2, v0.3: test and incident events, initial software supply chain security. Java SDK to Maven.
            - Tools: Jenkins, Testkube, Spinnaker (implementing), Tekton (experimental), ArgoCD (RFC), Harbor (RFC). More tools have expressed interest (Shipwright, JX, Tracetest, JReleaser, Flux)
            - Collaborations: VSM Interop, CNCF App Delivery TAG, OpenSSF, CDF SIG Interop
            - Interested companies: Fidelity (adopter), SAS, Apple, Ericsson, IBM and more
            - What’s next: connecting events, visualisation, supply chain security, more tools and adoption

- Connecting events
    - Reminder to review 
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - https://github.com/cdevents/spec/issues/104
    - https://github.com/cdevents/spec/pull/139 (Very Rough Draft)
    - Ben working on client API and storage description
    - PR will be available soon-ish

- Spinnaker
    - Ben to arrange a meeting for a demo of the current implementation

- Fidelity adoption:
    - [User story](https://cd.foundation/wp-content/uploads/sites/78/2023/02/CDF_SecuringtheFinancialServicesSupplyChainthroughContinuousDelivery_012023.pdf)
    - Starting from the central point: Jenkins
    - Looking forward to artifactory plugin
    - Challenges:
        - Versioning (of Jenkins)
        - Implementation of the plugin (Jenkins documentation issue)
    - Events are sent to a Kafka queue
    - Goals:
        - Improve developer experience: automatic audit trail for artifacts, track via commit id
        - Visibility towards management of application landscape
    - Non-relational DBs are really beneficial
        - But they do present challenges with versioning
        - Posgres provide a JSON type column

- CDEvents visualisation

- Python SDK
    - Adopting pydantic in progress
    - Release to pypi in progress
    - Question: generation of the SDK?

- v0.4 Planning (in progress):
    - [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - [all in roadmap](https://github.com/orgs/cdevents/projects/1/views/8)
    - [issues in CDEvents org not labeled with roadmap](https://github.com/issues?page=1&q=is%3Aopen+is%3Aissue+archived%3Afalse+user%3Acdevents+-label%3Aroadmap)


## Jun 5, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Andrea Frittoli, IBM, UTC+1
- Name / affiliation / TZ

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)

Agenda:
- Action Items
    - [Emil's nomination for TOC](https://github.com/cdfoundation/foundation/issues/442#issuecomment-1568928869)
    - Nominations close today

- v0.4 Planning
    - [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - [all in roadmap](https://github.com/orgs/cdevents/projects/1/views/8)
    - [issues in CDEvents org not labeled with roadmap](https://github.com/issues?page=1&q=is%3Aopen+is%3Aissue+archived%3Afalse+user%3Acdevents+-label%3Aroadmap)

- Connecting events
    - Reminder to review 
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - https://github.com/cdevents/spec/issues/104
    - https://github.com/cdevents/spec/pull/139 (Very Rough Draft)

- Updates
    - [Harbor draft RFC](https://hackmd.io/fNI4B111Sq6HESk7a5KVNA)
        - [Issue](https://github.com/goharbor/community/issues/225)
    - Java SDK: ready for v0.1.2

## May 30, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Ben powell, Apple, CST
- Fatih Degirmenci, CDF, UTC+2
- Andrea Frittoli, IBM, UTC+1
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Daniel Han, Bloomberg, UTC-4
- Andrew Fenner, Ericsson Software Technology, UTC+1
- Adam Kenihan, Ericsson Software Technology, UTC+1
- Name / affiliation / TZ

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD]

Agenda:

- Action Items

- Welcome Daniel Han!
    - Standardization around testing
    - Special focus on integration testing
    - Interested in contributing back to CDEvents

- TOC Project representatives
    - [Process](https://github.com/cdfoundation/toc/blob/main/elections/2023/README.md#project-representative-elections)
        - 4 seats from 9 projects in TOC 
    - [Nominations](https://github.com/cdfoundation/foundation/issues/442)
        - The nomination period starts on May 22, 2023 and ends on June 5, 2023.
    - Emil has volunteered to be nominated from CDEvents. The nomination will be submitted later today.

- CDEvents visualization discussion - Adam/Andrew/Jalander from Ericsson Software Technology
    - Follow-up: track slide questions on github
    - Discuss libraries vs. services in this area
    - Share screenshots of demos?
    - Issue on visualizing CDEvents: https://github.com/cdevents/community/issues/25

- Update on Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - https://github.com/cdevents/spec/issues/104
    - https://github.com/cdevents/spec/pull/139 (Very Rough Draft)
    - Should be ready in a couple of weeks
    - Ben to let the team know when it's ready for review

- CDEvents usage at Bloomberg - Daniel Han from Bloomberg

- (Andrea) Signed CDEvents
    - We should probably delegate signature to the envelope layer
        - That would allow us to sign the entire payload
        - Which CE headers would we like to be included in the signature?
    - Trying to restart the conversation on [CloudEvents side](https://github.com/cloudevents/spec/issues/565)
    - It would be really useful to have a security expert involved in the discussion
    - Signatures associated to the envelope layer means that they would only be available with certain bindings
        - That should be acceptable

- Updates:
    - CDEvents  + Argo: 
        - [Project View](https://github.com/orgs/cdevents/projects/4/views/10)
        - [Draft RFC](https://github.com/argoproj/argo-cd/pull/13723)
        - Question
            - Do we need separate proposal for each Argo project?
    - CDEvents + Harbor:
        - Discussed in the CNCF Harbor slack channel
        - Andrea to start and RFC
        - https://github.com/goharbor/community/tree/main/proposals
    - CDEvents + other registries
        - JFrog, meeting today
        - Chainguard, planning POC
    - CDEvents + GitHub:
        - Brad working on a GitHub App
            - SCM events
            - Pipeline events (GH Actions)
    - CDEvents + Testkube:
        - Implemented in dev
        - Release coming soon
    - CDEvents + Spinnaker
        - PRs ready for review
        - Demo available for Spinnaker meetings
        - Ben to ping people on Spinnaker side
            - Organise a meeting to see the demo with all interested parties

- CDEvents v0.4 planning

- Other topics?


## May 22, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Brad McCoy, Basiq, UTC+10
- Name / affiliation / TZ

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - Planned for [TBD]

Agenda:

- Updates from last meeting
    - Discussed connecting events
    - Ben presented a proposal
    - Ben to make a PR, discuss internally at Apple and then present to the group

- Brad created a PRs to update licensing
    - https://github.com/cdevents/sdk-go/pull/55
    - https://github.com/cdevents/spec/pull/137
    - https://github.com/cdevents/sdk-java/issues/52 (issue)
    - https://github.com/cdevents/sdk-python/pull/27
    - We may want to remind about this in the TOC

- [v0.3 review](https://github.com/orgs/cdevents/projects/1/views/12)
    - Blog post
- Updates from CDCon
    - CDEvents Summit
        - Events broker
            - Challenges with Kafka. It would be great to get a sharable feedback on Kafka experiences
            - Should it be part of CDEvents or reference architecture
            - [FRSCA](https://buildsec.github.io/frsca/) use an opinionated set of tools, but as an example to represent their reference architecture
        - Platform and CDEvents
            - submit CDEvents to the evidence storage and then the platform take over
            - Then you can switch between tools (Tekton, Jenkins, etc) as long as they can provide CDEvents JSON to the storage
        - Modeling feature flags
            - In the context of OpenFeature, should model feature flags (and perhaps configurations in general) in CDEvents? 
            - We don’t support those events today, but that’s something we could model more accurately
            - Feature flag changes are a runtime event, with no deployment involved
            - Is that a deployment too? CDEvents could help make common terminology here
            - If we put feature flags data in deployments, a change to feature flags would require a new deployment event. Too much granularity can become difficult to manage
        - How do we get CDEvents in big cloud vendors?
            - We should have projects in the CDF adopting CDEvents, explain benefits at TOC
            - Users that use CDF tools adopt CDEvents and can explain the benefits
            - It becomes easier to talk to commercial CI/CD tools first, and then to cloud providers
            - What about CDEvents for GitHub actions?
                - We’re building an adapter, but really we should have CDEvents natively eventually
        - Cloud is not the only place where we deliver software, creating momentum there would help too
        - Hosting CDEvents presentations for the benefits of other projects
        - [Visualization](https://github.com/cdevents/community/issues/25)
            - It would be nice to have an open source framework (react?) to visualise events
            - Visualisation can be good do demonstrate the value of CDEvents
            - Similar project in the JS space
            - UI would be really a cherry on the cake on top of standardisation, it can add great value

        - Benefit from artifactory and other registries if they had a plugin that generates CDEvents automatically
        - End users can help by talking to vendors about features they’d like to see in products

    - Michael Crenshaw reached out about implementing CDEvents in Argo CD
        - GitOps, update from registry use case
        - Also generating events
        - Michael to start the process on Argo side

- Argo
    - image updater https://argocd-image-updater.readthedocs.io/en/stable/
        - Now part of ArgoCD
    - Argo integration interesting for Ericsson
    - Argo integration interesting for RedHat

- CDEvents in the OSS keynote, thank you Tracy!

- Include updated architecture picture in docs
    - It would be good to show what kind of events are used where
    - Links to examples

- Configuration changes
    - Not part of the CDEvents scope today
    - Good match for VSMI scope

- GitHub adapter
    - Brad to start this week
    - Adam is also working on similar adapter for Gitlab
    - SCM, Pipeline and Testing event can all be in scope, so we could provide visualizatio of GitHub and GitLab pre-merge pipelines
    - With GitLab we used to talk to Kevin 
    - Interoperability stories
        - Switch betweeb GitLab and GitHub, combined with other tools (e.g. Tekton and Testkube)
        - Send test events from Tekton first, then adopt Testkube - similar CDEvents are sent and consumers are not affected
    - Brad to create issues to track this

- SDK updates
    - Golang v0.3
    - Java updated to v0.1.2
        - Working on a release for v0.1.2
        - Working on integrating JReleaser too
        - Next: automation for the Java SDK
    - Python
        - 

- Implementation updates
    - testkube initial implementation done
    - Spinnaker PR created and under reviews
        - Consume CDEvents - Using Automated Trigger
            https://github.com/spinnaker/deck/pull/9977
            https://github.com/spinnaker/echo/pull/1290
            https://github.com/spinnaker/gate/pull/1651

        - Produce CDEvents - using Notification
            https://github.com/spinnaker/echo/pull/1295
            https://github.com/spinnaker/deck/pull/9997

- V0.4 planning

- Other topics?


## May 16, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple
- Tracy Ragan
- Name / affiliation / TZ

Links:
- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)
    - Planned for [Apr 20th]
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
    - No due date yet

Agenda:
- Action Items

- TOC Project representatives
    - https://github.com/cdfoundation/toc/pull/202
    - 4 seats from 9 projects in TOC 
    - The nomination period starts on May 22, 2023 and ends on June 5, 2023.
    - Eligible Voters
        - Are you on [the voters list](https://protect2.fireeye.com/v1/url?k=31323334-501d5122-313273af-454445555731-4b8c207147c35781&q=1&e=14a79fae-dd7b-404d-85c3-fd3782645f4d&u=https%3A%2F%2Fgithub.com%2Fcdfoundation%2Ftoc%2Fblob%2Ff4accdde9248981c80507b982f4214b098c780d6%2Felections%2F2023%2Fvoters.md)? If not, and if you consider yourself a contributor to CDF or any of its projects, you could sign up on [this form](https://protect2.fireeye.com/v1/url?k=31323334-501d5122-313273af-454445555731-7c934222755ef6a8&q=1&e=14a79fae-dd7b-404d-85c3-fd3782645f4d&u=https%3A%2F%2Fdocs.google.com%2Fforms%2Fd%2Fe%2F1FAIpQLSdsxCadKwauQ4EHjaNihGtVQJQ027ECsXBZACU7WqXm4dBMCw%2Fviewform).

- v0.3 release
    - Tracking issue: https://github.com/cdevents/community/issues/24
    - Release done, announcements missing

- v0.4 release
    - Focus: Connecting events

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - A lot of discussion around the links model, clearing out some misconceptions about Eiffel and nailing down some scenarios and use cases for the links/parents
    - To find other events than the parents there is a need for a "links service", i.e. a database of previously sent events (often called Event Repository in Eiffel)
    - Ben will provide a draft PR hopefully later this week

- \<addme\>

## May 2, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Andrea Frittoli, IBM, UTC+1
- Name / affiliation / TZ

Links:
- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)
    - Planned for [Apr 20th]

Agenda:
- Action Items

- v0.3 release
    - Test events merged
    - Artifact signed event merged
    - [Prepare v0.3 PR](https://github.com/cdevents/spec/pull/131)
    - Planning to release tomorrow 03.05.2023
    - CDEvents website update due after release on spec repo
    - Blog post for v0.2 + v0.3 after announcement
        - https://hackmd.io/nuoflXZnRwO4RbTXdzt3xA
    - Tracking issue: https://github.com/cdevents/community/issues/24

- Java SDK updates
    - Release process in place, draft release on maven central
    - All v1 events included, but format still v0.1-draft
    - SDK alignment to v0.1.x in progress
        - [Doc: Update readme with the example to create PipelineRunFinished CDEvent](https://github.com/cdevents/sdk-java/pull/40)
        - [Core CDEvents to render as CloudEvent and schema validation](https://github.com/cdevents/sdk-java/pull/41)
        - [Source code CDEvents to render as CloudEvent and schema validation](https://github.com/cdevents/sdk-java/pull/42)
        - More PRs to come
    - [Moving away from reload4j](https://github.com/cdevents/sdk-java/issues/39)

- Golang SDK updates
    - Support for more complex subjects merged
    - Session with TestKube this week to demonstrate the process of updating the SDK. After that v0.3.0 to be relesed

- Python SDK updates
    - Update pydantic in progress (improved JSON parser)
    - Evan working on automated releases and publishing to PyPi

- Jenkins Plugin update
    - GitHub repo: https://github.com/jenkinsci/cdevents-plugin
    - Plugin site: https://plugins.jenkins.io/cdevents/
    - Still not fully integrated in the Jenkins release management
    - Jenkins to Jenkins communication enabled by the plugin
    - It would be great to have a demo in a SIG-events meeting

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA

## May 2, 2023
Meeting canceled due to too few participants

## April 24, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Emil Bäckmark, Ericsson, UTC+2

Links:
- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)
    - Planned for [Apr 30th]

Agenda:

- Test Events
    - https://github.com/cdevents/spec/pull/105
    - Comments made in the PR

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - No updates yet

- Artifact signed event
    - https://github.com/cdevents/spec/pull/125
    - 

- Release v0.3 status
    - [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)

- Java SDK status
    - Work in progress to fix issues and align to v0.1
        - https://github.com/cdevents/sdk-java/pull/35
        - https://github.com/cdevents/sdk-java/pull/34
        - https://github.com/cdevents/sdk-java/pull/24
    - Proposal do adopt JReleases

- Python SDK status
    - Evan working on publishing to pypi
    - https://github.com/cdevents/sdk-python/issues/22

- Golang SDK status
    - 


## April 4, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Tracy Ragan, DeployHub, CDF TOC, UTC-7
- Evan Elms
- Name / affiliation / TZ

Links:
- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)
    - Planned for [Apr 20th](https://github.com/cdevents/spec/milestone/3)


Agenda:
- Action Items

- Release v0.2 status
    - Remaining actions:
        - Andrea to finish the announcements

- Release v0.3 status

- SDK updates
    - Golang
        - [v0.2 released](https://github.com/cdevents/sdk-go/releases/tag/v0.2.0)
        - SDK is now generated from schemas hosted in the spec repo
            - [SDK generator](https://github.com/cdevents/sdk-go/tree/main/tools)
            - Can be used for other languages as well, with dedicated [template files](https://github.com/cdevents/sdk-go/tree/main/tools/templates)
        - SDK now runs tests against the examples defined in the spec repo
    - Python
        - Working on GitHub Actions to automate stuff
    - Java

- [Testing events](https://github.com/cdevents/spec/pull/105)

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)
    - [Spinnaker](https://github.com/spinnaker/governance/pull/299)
    - Jenkins
        - Progressing well
        - Hopefully be contributed to open source by May
    - TestKube

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA

- Upcoming meetings
    - Monday April 10th.
        - Bank Holiday in Sweden, but not everywhere else so the meeting is kept.
    - Tuesday April 18th.
        - Canceled due to KubeCon Europe? To be discussed on Slack

## March 27, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Name / affiliation / TZ

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [Mar 20th](https://github.com/cdevents/spec/milestone/2)
- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)
    - Planned for [Apr 20th](https://github.com/cdevents/spec/milestone/3)


Agenda:
- Action Items

- Release v0.2 status
    - [Release notes](https://github.com/cdevents/spec/releases/tag/v0.2.0)
    - [Documentation](https://cdevents.dev/docs/)

    - Golang SDK
        - Added support for multiple versions
            - Always produce latest version
            - Parse any compatible future version (minor/patch)
            - Parse any compatible old version (minor/patch)
            - Unknown data in future versions is ignored for now
        - V0.2 updates WIP
            - 80% implemented generating the SDK
    - Next steps:
        - Release golang SDK
        - Move to v0.3-draft on main
        - Andrea to finish the announcements

- Python SDK
    - New contributor from Fidelity to work on pydantic issue
    - Evan continued working on release automation for Python and Java

- [Testing events](https://github.com/cdevents/spec/pull/105)
    - The existing PR will need to be updated based on v0.2

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)
    - [Spinnaker](https://github.com/spinnaker/governance/pull/299)
        - RFC merged!
        - It should be ok to start the implementation
    - Jenkins
        - Framework up, pipelinerun events
        - Work happening internally at Fidelity for now

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA


- [v0.3 Roadmap](https://github.com/orgs/cdevents/projects/1/views/12)

## March 21, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, UTC-6
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Name / affiliation / TZ

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [Mar 20th](https://github.com/cdevents/spec/milestone/2)

Agenda:
- Action Items
    - n/a

- Release v0.2 status
    - All spec PRs merged
        - Nice to have: https://github.com/cdevents/spec/pull/121
    - Website update ready
        - https://github.com/cdevents/cdevents.dev/pull/34
    - Golang SDK
        - Added support for multiple versions
            - Always produce latest version
            - Parse any compatible future version (minor/patch)
            - Parse any compatible old version (minor/patch)
            - Unknown data in future versions is ignored for now
        - Release 0.1.1 and 0.1.2
        - Main branch updated to 0.1.2
        - V0.2 updates WIP (incident events)
    - Next steps:
        - Merge spec PR https://github.com/cdevents/spec/pull/121
        - Tag spec and do release notes
        - Merge website PR https://github.com/cdevents/cdevents.dev/pull/34
        - Update spec in go SDK to v0.2
        - Implement v0.2 changes
        - Release golang SDK
        - Move to v0.3-draft on main

- Python SDK
    - CI linting using flake8 working locally (ready to go)
    - Release to pypi
        - Vanilla framework is already there
        - TOML file with metadata required
    - Next step: v0.1 release

- [Testing events](https://github.com/cdevents/spec/pull/105)
    - The existing PR will need to be updated based on v0.2

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)
    - [Spinnaker](https://github.com/spinnaker/governance/pull/299)
        - RFC is getting close to merge
        - It should be ok to start the implementation
    - Jenkins
        - Framework up, pipelinerun events
        - Work happening internally at Fidelity for now

- Connecting Events
    - https://hackmd.io/-Or6hobHSLWVj4duAWX7nA
    - Make a PR with hybrid approach so we can have hands on experience
    - Continue working on the DORA metrics POC and try to apply different way of connecting events

## March 13, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC
- Name / affiliation / TZ

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [TBD](https://github.com/cdevents/spec/milestone/2)

Agenda:
- Action Items

- Incident Events
    - [PR Merged](https://github.com/cdevents/spec/blob/main/continuous-operations.md)
    - Next steps
        - Include in SDKs
            - Andrea Create and issue for each SDK
        - Cut a release
        - Update the [website](https://cdevents.dev/docs/) with the new event group
            - Emil will create an issue for this - [CDEvents.dev #31](https://github.com/cdevents/cdevents.dev/issues/31)

- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Open PRs
        - https://github.com/cdevents/spec/pull/118
        - https://github.com/cdevents/spec/pull/119
    - Open Issues
        - https://github.com/cdevents/spec/issues/110
    - Review content
    - Plan date
    - Next steps

- SDKs
    - Python SDK
        - We will need pypi publishing
    - Java SDK
        - For v0.2 (or v0.3) for Maven central repository
        - Naming: defined in the pom files dev.cdevents/java-sdk
    - Go SDK
        - Managed by the tooling directly
    - Investigate external tool for secrets for release mgmt
        - 1password
    - Discorability of SDKs important for integrations
    - Licensing
        - Apache 2.0 license should be in all SDK repos


- [Testing events](https://github.com/cdevents/spec/pull/105)

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)
    - [Spinnaker RFC](https://github.com/spinnaker/governance/pull/299)
    - Jenkins
        - Fidelity plans to contribute a CDEvents plugin

- \<addme\>


## March 7, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC
- Robert Reeves, Liquibase, UTC-6
- Name / affiliation / TZ

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [March 13th](https://github.com/cdevents/spec/milestone/2)

Agenda:
- Action Items

- Spinnaker integration:
    - Robert's proposed plan is:
        - Spinnaker to support CDEvents - RFC
        - Ben talking about Spinnaker + CDEvents on behalf of Apple

- [Incident events](https://github.com/cdevents/spec/pull/107)
    - "Continuous Operations" or "Continuous Operation"?
        - No reference in the json schema
        - let's keep the plural version for now
        - we can discuss with SIG interop about naming

- URI vs. URI-reference
    - Proposal: keep URI-reference as enforcement, propose URI as best practice in the spec
    - Extend https://github.com/cdevents/spec/pull/116 to include best practices

- [Connected events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - What would it take to have more options optional?
    - What it would look like from syntax POV

- [Testing events](https://github.com/cdevents/spec/pull/105)

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)
    - [Spinnaker RFC](https://github.com/spinnaker/governance/pull/299)
    - Jenkins
        - Fidelity plans to contribute a CDEvents plugin


- SDK Updates
    - Python SDK
        - Erik in between jobs
        - No may not expect updates until May/June
    - Java SDK
        - Should be ready for v0.1
- \<addme\>




## Feb 27, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [Feb 28th](https://github.com/cdevents/spec/milestone/2)
    - Need to reschedule - take cdCon into account

Agenda:
- Action Items
    - (Andrea) Create an issue about defining the process for formal releases
        https://github.com/cdevents/community/issues/23
    - (Andrea) Add details about tracing contexts in [Connecting events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
        - Still pending
    - [Connected events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
      - Flesh out Hybrid approach section (Ben)
      - Ask AI/ML what links proposal works best (Ben/Emil)
  - [Spinnaker RFC](https://github.com/spinnaker/governance/pull/299)
    - Review new commits on RFC (Ben)

- [Incident events](https://github.com/cdevents/spec/pull/107)
    - Comments to be answered

- [Connected events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - Need to clarify the difference between various IDs (trace, context, global)
    - For hybrid approach, how does it work from a consumer POV if either or both links and global ID can be provided? Needs to be clarified

- [Testing events](https://github.com/cdevents/spec/pull/105)
    - Comments to be answered

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)

- [Spinnaker RFC](https://github.com/spinnaker/governance/pull/299)
    - Review new commits on RFC (Ben)

- SDK Updates
    - Python SDK
        - Erik in between jobs
        - No may not expect updates until May/June
    - Java SDK
        - Should be ready for v0.1

- Events for Supply Chain
    - To be discussed at SIG Events this afternoon
    - Signatures, SBOM, etc

- \<add me\>

## Feb 21, 2023

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, CST
- Robert Reeves, Liquibase, CST
- Fatih Degirmenci, CDF, UTC+1

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for [Feb 28th](https://github.com/cdevents/spec/milestone/2)

Agenda:
- Action Items
    - (Andrea) Create an issue about defining the process for formal releases
    - ~~(Ben) Add use cases about Global ID in [Connecting events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)~~
    - (Andrea) Add details about tracing contexts in [Connecting events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)

- [Incident events](https://github.com/cdevents/spec/pull/107)

- [Connected events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - Flesh out Hybrid approach section (Ben)
        - Expand on how to relate test artifact events to eachother, which can be done by relying on Eiffel instead of the global ID.
    - Ask AI/ML what links proposal works best (Ben/Emil)

- [Testing events](https://github.com/cdevents/spec/pull/105)

- [Tools integrations](https://github.com/orgs/cdevents/projects/4)

- [Spinnaker RFC](https://github.com/spinnaker/governance/pull/299)
    - Review new commits on RFC (Ben)

- SDK Updates
    - Can we generate SDKs from our schemas?
        - Similar generations has been done at Liquibase (Robert)
        - OpenAPI/Swagger
            - Used everywhere
            - JSON/Yaml
        - Smithy
            - Heavily used in AWS

- \<add me\>


## Feb 13, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, GMT
- Emil Bäckmark, Ericsson, CET
- Ben Powell, Apple, CST
- Brad McCoy, Basiq, AEST

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th
        - (Andrea) Should we reschedule?
        - We could release even if we have incident events alone

Agenda:
- Action Items
    - We can document in the primer that if there is risk of confusion between an object and its execution we should append `Run` to the subject
        - Emil wrote an issue: https://github.com/cdevents/spec/issues/109

- [Test events](https://github.com/cdevents/spec/pull/105)
    - Ole cannot join today
    - Ole to review latest comments on PR
    - Emil would like to review

- Release process - how long changes can be merged before a release
    - Relatively informal process for now
    - Favouring speed for now, initial 0.x release
    - More formal process required in future
        - (Andrea) Create an issue about defining the process

- [Incident events](https://github.com/cdevents/spec/pull/107)
    - Review remaining comments
    - Subject Type
        - Type is optional
        - We should link standard fields in table to the core
        - Goal should be to make things as easy as possible
        - Separate PR to document subject type is a more clear way in scope for 0.2
        - Andrea to check the go SDK - if it's required
        - We should document that it's the same as what's in the event type

- [Connecting events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - (A) Ben to add use cases about Global ID
    - (A) Andrea to add details about tracing contexts
    - 

- SDK updates
    - Java
    - Golang
    - Python

- Tool integration updates
    - Spinnaker
    - Jenkins
    - Jenkins-X
    - Tekton
    - Kubetest

- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9) Review


## Feb 7, 2023

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, GMT
- Ben Powell, Apple
- Emil Bäckmark, Ericsson, GMT+1
- Robert Reeves, Liquibase / CDF TOC, CST (GMT-6)

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th
    - Should we use the GitHub roadmap view? https://github.blog/changelog/2023-01-31-roadmap-in-projects-public-beta/
        - Emil to try the roadmap functionality

Agenda:
- Action Items
    - We can document in the primer that if there is risk of confusion between an object and its execution we should append `Run` to the subject
        - Emil wrote an issue: https://github.com/cdevents/spec/issues/109

- Spinnaker RFC for CDEvents
    - Lessen scope of RFC and then iterate
        - RFC originally wanted to rework Spinnaker's architecture, which is very difficult, so instead we lessened the scope to just have Spinnaker first injest CDEvents
            - If this goes well, we can look to re-architecting Spinnaker to utilize more of CDEvents
    - Integrating CDEvents with Spinnaker
    - Jalander created the RFC: https://github.com/spinnaker/governance/pull/299
    - From the meeting:
        - Limited to a new event type in Spinnaker
        - The CDEvents event type in Spinnaker will be able to inject any CDEvent and define reactions to it
        - RFC limited for now to receiving events (to reduce scope)
        - Next RFC for sending events
    - Robert: what does CDEvents give Spinnaker Users?
    - Ben:
        - End users: plugin any system that uses CDEvents to trigger Spinnaker
        - Spinnaker maintainers: no need to maintain /add ad-hoc integration

- Jenkins and CDEvents
    - Fidelity interested in it
    - A CloudEvents plugin for Jenkins exists today
    - Project (GSoC?): create a CDEvents pluing
        - Mentor required

- Tekton and CDEvents

- Jenkins X and CDEvents
    - Dependency on Tekton?
    - There was interest from the project
    - GSoC idea by Brad https://jenkins-x.io/blog/2023/02/06/gsoc2023-ideas/ 
    - 

- [Test events](https://github.com/cdevents/spec/pull/105)
    - Ben: abort -> cancel (consistency)

- [Incident events](https://github.com/cdevents/spec/pull/107)
    - Andrea to update the PR
    - Next step after merge golang SDK

- [Connecting events](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - Proposed plan:
        - next meeting (SIG meeting) for further notes from all parties
        - decision in two meetings (two weeks from now)
        - we can use customData to begin with to carry the information

- SDK updates
    - Java
    - Golang
        - Plan to update once test/incident events are in
    - Python

- \<addme\>



## Jan 30, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ole Lensmar, Kubeshop, UTC+1

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th

Agenda:
- Action Items
    - Action Andrea: archive SIG Events notes too
        - https://github.com/cdfoundation/sig-events/blob/main/docs/SIG%20Meeting%20Notes%202022.md
            - Any meeting in December? Andrea to check
    - Andrea to create an issue / PR about reason for current version structure
        - Issue: https://github.com/cdevents/cdevents.dev/issues/30

- Test events
    - [PR](https://github.com/cdevents/spec/pull/105) proposed by Ole (thank you!)
        - TestCase / TestSuite: should we rename to TestCaseRun / TestSuiteRun
            - Consistent with TaskRun / PipelineRun
            - Emil: PipelineRun / TaskRun is tekton specific
            - Execution could be an alternative, but it's very long
        - Json schema editing is error prone
            - It would be good to have automation for boiler plate schema parts
        - Agreed that we will use `*Run` events
        - We can document in the primer that if there is risk of confusion between an object and its execution we should append `Run` to the subject
            - Emil to create an issue
            - We probably don't need to add "Run" to the "build" events, since Build is a verb already

- Incident events
    - [Draft PR](https://github.com/cdevents/spec/pull/107)
    - [Design in hackmd](https://hackmd.io/h8DBfgwLQuKR7JyUPy0Xow)
    - Incident reported
        - Ticket reference should be an URI
        - URI Optional or Mandatory
        - URI vs. details protect potential sensitive data in the Ticket
    - Do we need alerts?
        - Eiffel has a proposed extension about alerts
        - In eiffel an alert should be sent when there is an incident
        - Alerts are not necessarly associated to a "negative" occurrence
        - Alert events might be considered later, but not as part of the incident events PR
    - Andrea to update the PR

- Environment uses URL (as field name) instead of URI
    - The type is URI
    - Create an issue to update events to consistent naming with URI
    - Enforce the URI type directly in the JSON schema
    - JSON format uri: https://json-schema.org/understanding-json-schema/reference/string.html#resource-identifiers

- Connecting events
    - [Design doc](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - No progress since last discussed
    - Comments welcome

- Roadmap Review


## Jan 24, 2023

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple

Links:
- [v0.2 Roadmap](https://github.com/orgs/cdevents/projects/1/views/9)
    - Planned for Feb 16th

Agenda:
- Action Items
    - Java SDK migration: (Adam) Working on a single PR
    - Spinnaker RFC: meeting setup for Jan 31st (thanks Ben)
    - Notes for 2022 archived (notes moved to CDEvents community repo)
        - Action Andrea: archive SIG Events notes too

- Test events
    - [PR](https://github.com/cdevents/spec/pull/105) proposed by Ole (thank you!)
    - Review cycle ongoing
    - More feedback welcome

- Incident events
    - [Draft PR](https://github.com/cdevents/spec/pull/107)
    - [Design in hackmd](https://hackmd.io/h8DBfgwLQuKR7JyUPy0Xow)
    - Reviews welcome
    - Incident will require triaging / ticketing
    - Incident
        - Detected
        - Reported -> Include a references to a ticket
        - Resolved
    - We don't want to replicate the entire lifecycle of tickets
    - Severity could be on the incident
        - Keep in custom data for now to keep things simple
    - Priority on the ticket
    - Track decision reasoning, not in the spec directly but supporting document (tbd)

- Connecting events
    - [Design doc](https://hackmd.io/-Or6hobHSLWVj4duAWX7nA)
    - No progress since last discussed
    - Comments welcome

- Event versions
    - Ben - The current approach with versions requires string splitting
        - For the SDK it makes (de-)serilization more complex
    - Action:
        - Document the reason for the current version structure
        - Andrea to create an issue / PR



## Jan 16, 2023

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


## Jan 10, 2023

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

## Dec 19

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


## Dec 13

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


## Dec 7

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
