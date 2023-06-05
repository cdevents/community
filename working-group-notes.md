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
    - Planned for [31.08](https://github.com/cdevents/spec/milestone/4)


Agenda:
- Action Items
- \<addme\>

### Topics for coming meetings

- To be added


### Jun 5, 2023

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
    - 

### May 30, 2023

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


### May 22, 2023

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


### May 16, 2023

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

### May 2nd, 2023

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

### May 2nd, 2023
Meeting canceled due to too few participants

### April 24th, 2023

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


### April 4th, 2023

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

### March 27st, 2023

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

### March 21st, 2023

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

### March 13th, 2023

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


### March 7th, 2023

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




### Feb 27th, 2023

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

### Feb 21st, 2023

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


### Feb 13th, 2023

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


### Feb 7th, 2023

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
    - 

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



### Jan 30th, 2023

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


### Jan 24th, 2023

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
