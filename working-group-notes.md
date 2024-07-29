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

### Template

Participants:
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items
- \<addme\>

### Topics for coming meetings

- Review proposal for demo system https://github.com/cdevents/community/issues/31


### July 29th, 2024

Participants:
- Name / affiliation / TZ

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items
  - (Andrea) Cancelled CDEvents WG on Aug 05 and Aug 19
    - One meeting per week between CDEvents and CDEvents Implementation WG

- PRs pending review
  - Spec: https://github.com/cdevents/spec/pulls
  - Go SDK: https://github.com/cdevents/sdk-go/pull/87
  - Java SDK: https://github.com/cdevents/sdk-java/pull/83
  - Jira Translator: https://github.com/cdevents/jira-translator/pull/1
  - Gerrit Translator: https://github.com/cdevents/gerrit-translator/pull/3
- Spec [v0.5](https://github.com/orgs/cdevents/projects/1/views/15) review: 
- \<addme\>


### July 22nd, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Brett Smith, SAS, UTC-4
- Ben Powell, Apple, CST 

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items
- Summer Schedule
  - Andrea: several vacations in August
  - Emil: away in July, back in August
  - Brett: available throught summer
  - Ben: switch to be-weekly for summer, also happy to host the meetings if needed
  - Proposal:
    - Alternate CDEvents WG with Implementation WG in July/August
    - Resume normal schedule in September
    - Use Slack to see if we need fewer/more meetings

- Determining what events are custom programmatically
  - Type: dev.cdeventsx -> custom events
  - Go SDK generators: looking "schema/custom" https://github.com/cdevents/sdk-go/blob/5e81f2367a798914b19fd97ec4f2175241b803f8/tools/generator.go#L555

- [Spec Milestone v0.5](https://github.com/cdevents/spec/milestone/5) review
  - Relooking at CD CDEvents
- \<addme\>


### July 8th, 2024

Participants:
- Ben Powell, Apple, CST
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Agenda:
- New attendees
- Action Items

- Standardizing on `outcome` - Ben
    * Brett will update for consistency
    * https://github.com/cdevents/spec/issues/237
- Updates for CloudEvents Zero Trust - Ben
    * S/MIME and Jose (CMS types) were recommended by Cloudevents
        * Security said they were a little too flexible
    * Look at DSSE
- jira-translator PR
    * Formatting is a little hairy to even fix
    * Need a repo to be created - `jira-translator`, once the RFC approved
- gerrit-translator [PR](https://github.com/cdevents/gerrit-translator/pull/3) needs review
    - Ben will review
- SDK Java [PR](https://github.com/cdevents/sdk-java/pull/83) for custom events
    - Needs reviewers
        - Ben will review

- Links issue will be created in the new implementations repo - Ben

### July 1st, 2024

Participants:
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, UTC+1
- Emil Bäckmark, Ericsson, UTC+2
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items

- ([Martin](https://github.com/6543)) [cicd_feedback](https://github.com/6543/cicd_feedback) demo and discussion (~15min)
  - [Gitea](https://about.gitea.com/)
  - [Woodpecker CI](https://woodpecker-ci.org/)
  - Use case: Gitea to display status of CI pipelines and logs
  - MVP Solution: https://github.com/6543/cicd_feedback/tree/main

- Status of CloudEvents Zero Trust - Ben
   * [GH Issue](https://github.com/cloudevents/spec/issues/1302)
   * Please provide feedback on the issue directly

- \<addme\>



### June 24, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST 
- Steve Taylor, DeployHub/Ortelis, MST
- Tracy Ragan, DeployHub/Ortelius, MST
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1


Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items
- New Working Group kicking off 25/06
  - https://hackmd.io/o-vCvOq0SrCq4csB5Bl29g
  - Topic: define mission and scope of the WG
  - [Draft WG Mission](https://docs.google.com/document/d/1RgROt_MRep81bQp2qZ2HgZKG3tce7DHRUHhY2WscJts/edit?usp=sharing)
  - Tracy talked about CDEvents to DevOps Finos automation https://devops.finos.org/
    - They would like us to present draft architecture in September
    - [OSS Supply Chain](https://devops.finos.org/docs/working-groups/osssc) managed by [John Mark Walker](https://www.linkedin.com/in/johnmarkwalker/) (former CDF GB @CapitalOne)

- (Ben) Secure / Signed events
  - Ben talking to the CloudEvents community
  - Ben went through all various protocols supported by CloudEvents
    - Pre-proposal focussed on that
    - To be done (hopefully) today
    - Initial review from Apple security team
    - (Action) Ben to share the current proposal
    - Discussion at Serverless WG
      - [SIG Meeting](https://calendar.google.com/calendar/u/0/r/month/2024/6/20?ctz=UTC)

- Golang SDK 0.4
  - Most PRs merged
  - Review before release
    - Ben interested to take a look
  - Link support in 0.4
    - Only embedded links for now
    - No support for standalone links
    - No helpers for propagation
  - Support for custom events
    - Support for the schemaUri field for now
  - Tags for webhook adapter
    - Not only for webhook adapters
    - Used by other golang SDKs as strategy
    - Should not block v0.4 release

- Java SDK 0.4
  - Review needed
    - Andrea to review the PR
  - Custom Event support using Java SDK
    - PR on top

- [RFC Jira CDEvents integration](https://github.com/cdevents/community/blob/842923d76943545b456bbc5c1ca7c8d41f7437f4/rfc/jira-translator-cdevents.md)
  - Review required

### June 17, 2024

Participants:
- Name / affiliation / TZ
- Steve Taylor / DeployHub Ortelius/ MST
- Emil Bäckmark, Ericsson, UTC+2
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1
- Adam

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees

- Action Items

- Schema Questions? (Steve)
    - How can I see how an artifact relates to a source change commit?
        - There are multiple ways, but none is clearly documented yet though
        - Newly added 'links' could be used
        - artifact.packaged.change could be used

- SDK updates for v0.4.1
  - SchemaURI support
      - Waiting for Ben to create an issue on this
  - Java SDK
      - Waiting for reviews
      - Waiting for an issue to be created on adding links support

- New CDEvents Working Group Proposal
    - First meeting in this new group proposed to be on June 25 (replacing the SIG Events meeting)
    - Steve will initiate the mission doc
    - Andrea will inform on Slack and mail

- Flux integration current state
    - Demo by Adam K

- Brett presented the EPR workshop in San Diego recently
    - https://github.com/xbcsmith/epr-workshop
    - interested in the link service

- \<addme\>


### Jun 10, 2024

Participants:
- Name / affiliation / TZ
- Steve Taylor, Ortelius/DeployHub, MST
- Andrea Frittoli, IBM, UTC+1
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items

- SDK updates for v0.4.1
  - SchemaURI support
    - We should support the property
    - Perform validation against standard schema
    - Validate against custom schema
      - if the schema is available?
        - Andrea to create an issue about this in the community repo
          - Define standard approach across SDKs
    - For custom events we can still validate against the custom root schema
    - Support for customizing / subclassing the SDK for custom schema?
      - Do we need support for this?
      - We should look into how many people are interested in this feature
      - SDKs could provide hooks to help supporting schemaURI
      - Users may need support for schemaURI for tool-specific events
      - If SDK hooks are designed well, this may help users migrating from custom events into CDEvents
    - Process for adding a custom event and a proposing new event to CDEvents could be very similar
    - Ben to create an issue in the community repo
  - Java SDK: https://github.com/cdevents/sdk-java/pull/82
    - Review please!
    - Links and schemaURI pending
      - Implementation to be defined across SDKs first
      - For links, Ben to create an issue about this
        - This will be some work to define
        - Links propagation

- New CDEvents Working Group Proposal
  - Re-use the SIG Events time slot
  - Monthly meeting right now
    - We could change it to every other week
    - Starting two weeks from now
  - Steve to draft the working group mission doc for the first meeting
  - Andrea to setup the calendar
    - Use the current one and rename it for now
  - Andrea to announce the new meeting on slack and cdevents-dev

- [Enum or string](https://github.com/cdevents/spec/issues/215)
  - Ben: we should look into the Rust / Java SDKs if there is a way to solve this with existing generators

- <Jalander> https://github.com/cdevents/sdk-go/pull/82
    - for [gerrit-translator](https://github.com/cdevents/gerrit-translator/pull/1#pullrequestreview-2105053961)
- <Jalander> [RFC Jira CDEvents integration](https://github.com/cdevents/community/blob/842923d76943545b456bbc5c1ca7c8d41f7437f4/rfc/jira-translator-cdevents.md)


### June 3, 2024

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST
- Steve Taylor, Ortelius/DeployHub, MST
- Brett Smith, SAS, UTC-4

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees

- Action Items

- SDK updates for [v0.4.1](https://github.com/cdevents/spec/releases/tag/v0.4.1)
    - Add support for [custom schemaUri](https://github.com/cdevents/spec/issues/236)
        - Should the SDKs validate towards the custom schemas and also provide objects for easily creating such events?
        - Could we enable simple 'sub classing' of our SDKs so that users of CDEvents could easily create the own adapted SDKs?
        - (Steve) customData should be avoided as much as possible
        - (Ben) customData/customEvents could be needed for tools specific to one company/org, when interoperability might not be the main goal
        - Let's primarily support schemaUri as a uri-formatted string. Later we should consider validating towards a custom schema and potentially generate classes/objects for such. Providing a means to sub class our schemas is probably better in many cases.
    - Add support for [links](https://github.com/cdevents/spec/issues/213)
        - Start with embedded links
        - How to propagate needed references in the SDK between events
        - Extend it with external links and links service after that
    - (old) [Conformance tests](https://github.com/cdevents/community/issues/12) - outdated issue?
    - [Document SDK requirements](https://github.com/cdevents/community/issues/4)

- [Enum or string](https://github.com/cdevents/spec/issues/215)
    - [Comment from last WG](https://github.com/cdevents/spec/issues/215#issuecomment-2120787980)
    - There is an issue with the Rust SDK for the current schema

- New CDEvents Working Group Proposal
    - Any news?

- \<addme\>



### May 20th, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Emil Bäckmark, Ericsson, UTC+2
- Tracy Ragan, DeployHub / Ortelius UTC-7
- Steve Taylor, DeployHub / Ortelius UTC-7
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items

- [Release v0.4.1](https://github.com/cdevents/spec/releases/tag/v0.4.1) is out
  - SDK work ongoing
    - Java
    - Golang
    - Rust
  - [Enum or string](https://github.com/cdevents/spec/issues/215)

- Meeting schedule and holidays
  - APAC friendly meeting
    - Andrea to e-mail/slack about this
    - If no interest we can cancel
  - Andrea on PTO 24/05 to 04/06
  - 27/05 is a holiday on the US
    - Emil away, Andrea on PTO
    - Let's cancel the meeting
  - 03/06 Emil to facilitate the meeting

- New CDEvents Working Group Proposal
  - Name TBD - Tools / Implementation / Infra / else?
  - Topics:
    - SDKs
    - Event buses
    - Link service
    - Adapters, apps & plugins
    - Storing CDEvents
    - Public playground
  - Interested parties
    - Ben
    - Andrea
    - Emil
    - Natwest (OpenSSF)
    - JP Morgan
    - Harness
  - Schedule
  - Steve:
    - Let's find interested parties and then find a schedule that works
  - Proposal:
    - Let's keep this meeting for spec discussions
    - The new WG would cover non-spec discussions

- Andrea to send an email to CDF GB
  - Include Fidelity, Brett (SAS)
  - How to promote about CDEvents adoption based on discussion from last TOC meeting

- [Enum or string](https://github.com/cdevents/spec/issues/215)
  - Proposal
    - Switch to "string" only
    - Use "examples" to carry some example values
    - For v0.4.x SDKs, hardcode type to string on the SDK side
    - Implement the change in v0.5
  - Check with Ben if he agrees with the proposal

### May 13th, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC+1
- Ben Powell, Apple, CST
- Brett Smith, SAS, UTC-4

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items

- CloudEvents and trust
  - Ben to join CloudEvents SIG to discuss on Thursday
  - CNCF Serverless WG Meeting
  - [Meeting notes](https://docs.google.com/document/d/1OVF68rpuPK5shIHILK9JOqlZBbfe91RNzQ7u_P7YCDE/edit#heading=h.6xidlvhv1goi)
  - Related issue: https://github.com/cloudevents/spec/issues/565

- Release v0.4.1 preparation
  - Content: https://github.com/cdevents/spec/milestone/4
    - add JSON schema validation https://github.com/cdevents/spec/pull/220
    - fix the JSON schemas to pass validation https://github.com/cdevents/spec/pull/220
    - change snake casing to match spec requirements in the links schemas https://github.com/cdevents/spec/pull/222
    - add JSON linting (to validate the snake case)  - PR on main https://github.com/cdevents/spec/pull/205, cherry-pick PR pending
    - adding links to the custom schema (PR pending)
    - bump spec to v0.4.1 (PR to be done)
    - make a release

- Release v0.4 SDKs
  - After v0.4.1 release
  - No support for standalone links yet

- Versioning and Releasing
  - We could use automation to make the contribution process smoother
  - We need to store metadata about minor/major changes in PRs
    - It could be more than one kind in a single PR
  - We might need a dedicated proposal / meeting to discuss this

- OSS EU / CD Mini Summit, Vienna, Sept 16-19
  - [CD Mini Summit CFP](https://cd.foundation/blog/2024/05/03/cd-mini-summit-2024-cfp/) is open now, until May 30



### May 6, 2024

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+2
- Ben Powell, Apple, CST
- Brett Smith, SAS, UTC-4

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:

- New attendees
    - Vonny Jap, Screwdriver, Yahoo

- Action Items

- [OTel & CDEvents](https://github.com/open-telemetry/semantic-conventions/issues/915)

- OSS EU / CD Mini Summit, Vienna, Sept 16-19
  - [CD Mini Summit CFP](https://cd.foundation/blog/2024/05/03/cd-mini-summit-2024-cfp/) is open now, until May 30

- Other upcoming conferences
    - [Cloudnative SecurityCon NA](https://events.linuxfoundation.org/cloudnativesecuritycon-north-america/), Seattle, June 26-27
    - [KubeCon NA](https://events.linuxfoundation.org/kubecon-cloudnativecon-north-america/), Salt Lake City, Nov 12-15
        - CFP open, closes on June 9

- Links schemas need to updated as some of them are in the wrong format
    - SDK and adapters being updated. Problem found in spec. Issue to be created.

- Create GitHub issue for what all needs to be updated and changed in SDK to fully support links
    - This will probably be one of many issues as implementing links is a larger than normal task

- Should a proposal be written for all ideas around breaking changes? Or at least some overarching issue?
    - [Open issues labeled for breaking changes](https://github.com/cdevents/spec/issues?q=is%3Aissue+label%3A%22breaking+change%22+is%3Aopen)

- Any CDEvents [PRs](https://github.com/cdevents/spec/pulls) or [issues](https://github.com/cdevents/spec/issues) to discuss?


- \<addme\>


### April 29, 2024

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+2
- Andrea Frittoli, IBM, UTC+1
- Steve Taylor, DeployHub/Ortelius
- Tracy Ragan, DeployHub/Ortelius
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1

Links:
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:
- New attendees
- Action Items

- From the GB meeting
  - Roxanne@CDF throughout 2024
  - Ambassadors cohort: https://cd.foundation/ambassadors/
  
- OTEL / CDEvents
  - Follow converstation on this [issue](https://github.com/open-telemetry/semantic-conventions/issues/915)
  
- OSS EU / CD Mini Summit
  - OSS EU CfP closes tomorrow
  - CD Mini Summit
    - Olivier Vernin to chair the program committee
    - Colocated event (not an OSS track)
    - Dedicated CfP - not open yet
      - Not sure if that will grant a ticked to OSS, waiting for an answer

- cdCon @ OSS NA
  - Two days conferences, one of OSS tracks
  - Dedicated room, CDF swag station
  - Many submissions, good selection of talks
    - LF offers up to 2 days, so no room for more talks
  - 40/50 people in the room at most times
  - CDEvents related notes from the talks:
    - [The State of CDF, Dadisi, Apple](https://sched.co/1aJXn)
      - Dadisi talked about the importance of interoperability
    - [Adopting CDEvents and Embracing Interoperability, Andrea, IBM](https://sched.co/1aBN2)
      - [Slides](https://static.sched.com/hosted_files/ossna2024/21/cdevents_interoperability.pdf)
      - [Slide sources](https://github.com/afrittoli/cdevents_interoperability)
    - [Bringing CI/CD Practices to Machine Learning with MLOps, Robert, Comcast](https://sched.co/1aBNa)
      - DevOps Practices, Event Triggers, Observability
      - CDevents for MLOps domain?
    - [Guardians of Code: Continuously Monitoring Security and DevOps Compliance, Steve, DeployHub](https://sched.co/1cAOV)
      - Collect CDEvents from tools into Ortelius
      - Improve security posture
      - Automate security features "out of band"
    - [Panel Discussion: Let's Improve - Leverage DORA to improve Your Team's Software Delivery and Operations Performance, Nathen, Amanda and Dave, Google](https://sched.co/1aBNr)
      - Opportunity to present CDEvents at "Metrics Mondays"
    - [Using CD Events to Capture End to End Application Security Posture, Ashmita and Gopinath, OpsMx](https://sched.co/1aBOa) 
      - The team at OpsMx experimented using CDEvents with a number of tools to improve security posture. CDEvents could benefit from their experience.
    - Hallway track
      - CNOE.io (Nima):
        - CDEvents as interop layer in CNOE IDPBuilder to allow CNOE adopters to pick their favorite tools
        - Action: document and compare Flux and Argo events (consumed and produced). Started https://hackmd.io/0XnerLOdROiI_JAKuRlUfQ 
        - Possibly setup a meeting with ArgoCD, Flux, CDEvents and CNOE people to discuss a way forward
      - Screwdriver (Vonny):
        - Discussed CDEvents and possibility of adoption at Screwdriver
    - [CDF Awards](https://cd.foundation/cdf-community-awards-2024/)
    - [Recordings](https://www.youtube.com/playlist?list=PLbzoR-pLrL6qHuD538QsuJUw3eRuCfvgU)

- (Andrea) [Shall we remove the Run part from pipeline, task and run events?](https://github.com/cdevents/spec/issues/207)
  - There is most likely not going to be a 1:1 mapping
  - Most people in the room prefers to keep the `Run` part in the name
 
- (Tracy) Adoption of CDEvents
    - When is a tool 'CDEvents compliant'? - [CDEvents Conformance issue](https://github.com/cdevents/spec/issues/182)
    - Users generally don't want to change their workflows
    - Conversations at cdCon about making it easier to add steps to workflows
    - Security requirements disrupt existing workflows with extra requirements
    - Example: build SBOMs "out of band" upoing consuming CDEvents
      - SBOMs do not have a link to the source code
      - Creating the link allows do discover where a vulnerability exists
    - OpenSFF GUAC: https://guac.sh/
      - Create the link between an SBOM and where the SBOM was created

- Jenkins + Eiffel:
  - Events are configured centrally
  - Users can instrument their pipelines to get custom data in the events

- \<addme\>




### April 22, 2024

Participants:
- Emil Bäckmark, Ericsson, UTC+2
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1


Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)
- [v0.5 Roadmap](https://github.com/orgs/cdevents/projects/1/views/15)

Agenda:

- New attendees

- Action Items

- [CDEvents v0.4 announced](https://cd.foundation/blog/2024/04/16/cdevents-v04/)

- post-v0.4 activities
    - SDK updates
        - Java SDK to be updated
    - PoC updates
    - Comment added on v0.4 release issue, to add issues in each tool repo to add support for the new release

- v0.5 plans
    - Focus on cleanup and consistency fixes. Might be non-backwards compatible due to that

- [cdCon](https://cd.foundation/cdcon-2024/) & OSS NA takeaways
    - No takeaways noted so far

- [Open-source summit EU 2024](https://events.linuxfoundation.org/open-source-summit-europe/)
    - Austria, September 16-18
    - CFP closes April 30
    - [CD Mini Summit](https://events.linuxfoundation.org/open-source-summit-europe/features/co-located-events/#cd-mini-summit) planned for Sept 19. No CFP announced yet.

- [KubeCon NA 2024](https://events.linuxfoundation.org/kubecon-cloudnativecon-north-america/)
    - Salt Lake City, Nov 12-15
    - CFP closes June 9

- Brett: AI & CDEvents
    - Brett is considering to propose an angle on this, potentially for KubeCon NA

- Brett: Event Provenance Workshop
    - Ongoing

- Brett: Scorecard for dependencies
    - Snyk has had something in their portfolio, where a go.mod file could be uploaded to retrieve a score on it
    - https://snyk.io/advisor/check/golang
    - Should be notified by an event

- \<addme\>



### April 15, 2024

Participants:
- Ben Powell, Apple, CST
- Emil Bäckmark, Ericsson, UTC+2
- Andrea Frittoli, IBM, PST
- Brett Smith, SAS, UTC-4
- Christian Provenzano, Fidelity, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC+1


Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- Action Items
- \<addme\>

- v0.4 release
  - https://github.com/cdevents/spec/releases/tag/v0.4.0
  - Blog post live tomorrow
  - Release Project: https://github.com/orgs/cdevents/projects/1/views/13
  - Issue: https://github.com/cdevents/community/issues/44
    - Announcement once blog post is live
    - Link to issue is on the blog post, so we should keep it open
    - We shall open dedicated issues for SDK development
    - Let's at least do the autogenerated part soon and work on other features incremenetally
    - Ben may be able to find mentees for the Python SDK
    - Ben's code contribution pending internal approval
    - Brett can do reviews to python SDK

- post v0.4 / v0.5 ideas
  - Spec: Breaking changes, cleanup, consistency
    - We should lint to keep the spec consistent
    - Ben to start a project to track this work / v0.5 work
  - Improve tooling and generation of docs
  - Links SDKs
  - Links service reference implementation
  - Propagation docs and reference architecture
  - Proof of concepts with v0.4
  - v0.5 Release tracker: https://github.com/orgs/cdevents/projects/1/views/15

- Let's start with a slim v0.5 planning
- Add everything else to a roadmap project and we can then
  - prioritize items
  - pick them from the roadmap for specific releases

- Visualisation POC
  - Let's make the first PR
  - Add a new PR for grafana changes
  - POC will be apdated with v0.4 as follow-up

### April 8, 2024

Participants:
- Ben Powell, Apple, CST
- Andrea Frittoli, IBM, UTC
- Sean Brennan, Bloomberg, UTC-4
- Emil Bäckmark, Ericsson, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- Action Items
- \<addme\>

- CDEvents v0.4 Release
  - [Tracking Issue](https://github.com/cdevents/community/issues/44)
  - [Milestone](https://github.com/cdevents/spec/milestone/4)
  - [Blog Post](https://docs.google.com/document/d/1vmwMnW1gb4njGzFTv8BDZe-MO8lbg5-MKcMdfu4oMGk/edit#heading=h.q2md51f8azih)
  - Doc on CDEvents, events - Ben


### Mar 25, 2024

Participants:
- Ben Powell, Apple, CST
- Emil Bäckmark, Ericsson, UTC+1
- Sean Brennan, Bloomberg, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:

- New attendees

- Action Items

- Coming Meetings
    - April 1. Canceled
    - April 8. Note! DST - https://time.is/3pm_8_april_2024_in_UTC

- KubeCon EU takeaways
    - https://kccnceu2024.sched.com/event/1YeNY/the-chain-of-trust-towards-slsa-l3-with-tekton-trusted-artifacts-jerop-kipruto-google-andrea-frittoli-ibm?iframe=no

- CDEvents MVC Award - [last call _now_](https://forms.gle/omMPBmtViP6VT6Tc7)!

- Recently merged
    - [Tickets](https://github.com/cdevents/spec/pull/180)
    - [Links](https://github.com/cdevents/spec/pull/139)
    - [Custom Events](https://github.com/cdevents/spec/pull/185)
    - [webhook-adapter](https://github.com/cdevents/webhook-adapter/pull/1)

- Release v0.4
    - [Milestone v0.4](https://github.com/cdevents/spec/milestone/4)
    - Many outstanding issues in the current milestone plan
    - Action: Emil to synch with Andrea on what remains for 0.4

- CloudEvents size limit
    - CE limits the event to 64KB - https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md#size-limits
    - Do we need to validate the payload size in our SDKs?
    - Proposal: Add info about this to the primer and to SDK docs
        - Emil: Write issues about this in appropriate projects

- Approval events
    - Automated or human approvals
    - Somewhat related to 'artifact verified', or?
    - For example about approving an artifact before going to production
    - Somewhat related to 'artifact released'
    - Action: Sean - Write an issue about this event

- Service events
    - Are the 'upgraded' & 'removed' predicates really useful?
    - Ben: Create an issue to propose removal of the above

- Webhook adapter
    - Demoed by Jalander at the meeting
    - Issue to be created on how to handle multiple brokers when sending CDEvents

- \<addme\>



### Mar 11, 2024

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+1
- Brett Smith, SAS, UTC-5
- Sean Brennan, Bloomberg, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC

Agenda:

- New attendees

- Action Items
  - Define interoperability (TBD)

- KubeCon EU next week
    - Andrea will talk about CDEvents (through Tekton)
    - No CDEvents WG meeting on March 18. Andrea and Emil off due to KubeCon

- DST
    - In NA on March 10, in Europe on March 31
    - [CDF Public Calendar](https://calendar.google.com/calendar/u/0/embed?src=linuxfoundation.org_mhf0kmgedn67ihni8r129avp24@group.calendar.google.com) - Do you want to be added to the invite?
    - Poll: What time to have the meetings on March 25 (and 18)?
        - [4pm UTC](https://time.is/4pm_18_March_2024_in_UTC)
        - [3pm UTC](https://time.is/3pm_18_March_2024_in_UTC)
    - Proposal on the meeting is to keep it as-is (4pm UTC)

- Easter
    - Andrea won't join on March 25

- [Ticketing PR](https://github.com/cdevents/spec/pull/180)
    - Almost ready to be merged. A minor fix and then Andrea and Ben should be able to approve.

- [Links PR](https://github.com/cdevents/spec/pull/139)
    - Ready to be merged

- [Custom Events PR](https://github.com/cdevents/spec/pull/185)
    - Some changes needed

- CDEvents Webhook Adapter
    - [RFC](https://github.com/cdevents/community/pull/42)
    - [PR for RPC client/server](https://github.com/cdevents/webhook-adapter/pull/1)

- Copyright statements
    - What format to use? Examples:
        - https://github.com/cdevents/sdk-go/blob/39341b23818a6a352fea15ebbb79a0bdf91d4dd0/pkg/api/bindings.go#L1-L17
        - [Eiffel example](https://github.com/eiffel-community/eiffel/blob/master/find-latest-schemas.py)
        - https://github.com/cdevents/webhook-adapter/blob/cd215d57b76a87f0f7487effd4e68aa99522216e/buf.gen.yaml
    - We should prepare a recommendation for the CDEvents community projects. Issue to be created in community repo (Action Emil)
    - References
        - https://www.linuxfoundation.org/blog/blog/copyright-notices-in-open-source-software-projects
        - https://opensource.guide/legal/#does-my-project-need-an-additional-contributor-agreement

- Release v0.4
    - Include links
    - Include others that are close to be ready, but leave the rest for the next release
    - For SDKs, they might not support all features of v0.4 for their first release
        - For the Rust SDK an idea has been raised to enable generating modules for various versions of CDEvents, not just the latest/current
    - Blog post to be created for v0.4. Initiated by Roxanne.


### Mar 4, 2024

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC
- Brett Smith, SAS, UTC-4
- Sean Brennan, Bloomberg, UTC-5
- Christian Provenzano, Fidelity, UTC-5
- Jalander Ramagiri, Ericsson Software Technology, UTC

Agenda:

- New attendees

- Action Items
  - Define interoperability (TBD)

- (David, Andrea) Removal of `subject.type`
  - https://github.com/cdevents/spec/issues/189
  - Relates a bit to https://github.com/cdevents/spec/issues/51

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)
  - PR waiting for reviews, all comments addressed
  - Several conversations waiting to be closed / replied by commenters

- [Link Proposal](https://github.com/cdevents/spec/pull/139)
  - CI to be fixed
  - 1 conversation open

- Custom Events proposal:
    - SchemaUri: https://github.com/cdevents/spec/pull/184
    - Custom Events: https://github.com/cdevents/spec/pull/185

- RFC:CDEvents Webhook Adapter [design review](https://github.com/cdevents/community/pull/42)
  - Waiting for further reviews
  - Keep adapter for the repo name, use translator internally where applicable

- CDEvents Webhook Adapter [PR review](https://github.com/cdevents/webhook-adapter/pull/1)
  - Needs reviews!!

- [Jenkins GSoC CDEvents plugin](https://www.jenkins.io/projects/gsoc/2024/project-ideas/cloudevents-plugin/)

- (Jalander) CDEvents & Jira?
  - Ericsson is interested in this
  - Ben mentioned Jira before
  - Andrea to reach out to Steve Pereira @ VSMI
  - Sean would be interested too
  - Brett is not interested! :D just kidding

### Feb 26, 2024

Participants:
- Name / affiliation / TZ
- Emil Bäckmark, Ericsson, UTC+1
- Andrea Frittoli, IBM, UTC
- Brett Smith, SAS, UTC-4
- Sean Brennan, Bloomberg, UTC-5
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Christian Provenzano, Fidelity, UTC-5

Agenda:

- New attendees

- Action Items
  - (Andrea) Update custom events proposal
    - Create PRs:
      - SchemaUri: https://github.com/cdevents/spec/pull/184
      - Custom Events: https://github.com/cdevents/spec/pull/185
    - Section about versioning: done in PR
    - Reply to comments: done
    - Add worst case scenario handling: added more context in PR
  - Define interoperability (TBD)

- Brett's workshop preview

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)

- [Link Proposal](https://github.com/cdevents/spec/pull/139)

- Custom Events proposal
      - SchemaUri: https://github.com/cdevents/spec/pull/184
      - Custom Events: https://github.com/cdevents/spec/pull/185

- RFC:CDEvents Webhook Adapter [design review](https://github.com/cdevents/community/pull/42)

### Feb 19, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, UTC-6
- Brett Smith, SAS, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC


Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- Action Items
  - (Andrea) Update custom events proposal https://hackmd.io/LftfRirGRbKuAcLg9pdOag
    - To be done, section about versioning
    - To be done, create a PR
    - Reply to comments
    - Add worst case scenario handling, tools define their own competing custom events

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)

- [Link Proposal](https://github.com/cdevents/spec/pull/139)
- 

- New Repository creation for webhook-cdevents-adapter under cdevents
  - RFC: comments addressed, re-review required
  - Action: Andrea to create the new repo
    - Jalander, Adam and Ben as maintainers
  - Mozilla license should be ok

- (Ben) What is interoperability? How far do we go?
  - We should describe what we mean by interoperability
  - Data migration is not part of the scope
    - i.e. pipeline definitions, git repos, artifacts are not in scope
  - Add a section to the primer https://cdevents.dev/docs/primer/
    - Source https://github.com/cdevents/cdevents.dev/tree/main/assets
  - We could use definitions from SIG Interop, and how much of that CDEvents covers https://github.com/cdfoundation/sig-interoperability
  - With the current spec and definitions, interoperability could be painted to mean more than what we are solving for. For example, swapping out a new CD tool will not have all the old CD's pipelines.

### Feb 12, 2024

Participants:
- Name / affiliation / TZ
- Brett Smith, SAS, UTC-4
- Ben Powell, Apple, UTC-6
- Andrea Frittoli, IBM, UTC
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Sean Brennan, Bloomberg, UTC-5

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- Action Items
  - (Andrea) Update custom events proposal https://hackmd.io/LftfRirGRbKuAcLg9pdOag
    - Added transitioning from custom to core
    - Added section about links
    - To be done, section about versioning
    - To be done, create a PR
- \<addme\>

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)
  - Some updates to the PR
  - Only one outstanding comment to be addressed
  - Please re-review

- [Link Proposal](https://github.com/cdevents/spec/pull/139)
  - Some updates to the PR
  - Ready to be re-reviewed
  - Andrea to prepare an example for linking to a subject

- Next release
  - We could do a release as soon a links is merged
  - Tickets could go in the following release

- cdevents-translator [design PR](https://github.com/cdevents/community/pull/42/files) review
  - Addressed most comments
  - Hashicorp plugins are MPL-2 - Ben to check if the license is acceptable from Apple POV. MPL-2 is fine from CDF POV
  
- GitOps + CDEvents: 
  - https://hackmd.io/0XnerLOdROiI_JAKuRlUfQ

- Spinnaker
  - https://spinnaker.io/docs/setup/other_config/features/notifications/#cdevents

  - https://spinnaker.io/docs/guides/user/pipeline/triggers/cdevents/

### Feb 5, 2024

Participants:
- Name / affiliation / TZ
- Andrea Frittoli, he/him, IBM, UTC
- Brett Smith, SAS, UTC-4
- Emil Bäckmark, Ericsson, UTC+1
- Christian Provenzano, Fidelity, UTC-4
- Sean Brennan, Bloomberg, UTC-5

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
- 
- Action Items
  - Andrea to formalise a proposal for [#168](https://github.com/cdevents/spec/issues/168) in an hackmd doc linked into the issue
    - Proposal: https://hackmd.io/LftfRirGRbKuAcLg9pdOag
      - Emil: What happens is custom events become core CDEvents?
      - Emil: Is there any limitation on how custom events would link to core events?
      - Brett: We can provide advice, but not provide restrictions
          - We should consider how we handle custom events that might become core events. See Emil's question above. 
      - Andrea: add a section about version

- OpenTelemetry CI/CD Observability
  - Meeting recordings lookup https://docs.google.com/spreadsheets/d/1SYKfjYhZdm2Wh2Cl6KVQalKg_m4NhTPZqq-8SzEVO6s/edit#gid=0
  - https://docs.google.com/document/d/10xG7DNKWRhxNmFGt3yYd3980a9uwS8lMl2LvQL3VNK8
  - 

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)

- [Link Proposal](https://github.com/cdevents/spec/pull/139)

- (Ben) outcome enum https://github.com/cdevents/spec/pull/179

- cdevents-translator [design PR](https://github.com/cdevents/community/pull/42/files) review

### Jan 29, 2024

Participants:
- Andrea Frittoli, IBM, UTC
- Ben Powell, Apple, UTC-6
- Andrew Larsen, SAS, UTC-4
- Sean Brennan, Bloomberg, UTC-5
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Emil Bäckmark, Ericsson, UTC+1

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees

- Action Items
    - Owen to create an issue about capitalizing URI
    - Andrea to formalise a proposal for [#168](https://github.com/cdevents/spec/issues/168) in an hackmd doc linked into the issue
        - WIP https://hackmd.io/LftfRirGRbKuAcLg9pdOag

- OpenTelemetry CI/CD Observability
    - Working Group approved by the TC
    - See https://github.com/open-telemetry/community/pull/1822
    - First meeting running in parallel to this one

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)

- [Link Proposal](https://github.com/cdevents/spec/pull/139)

- (Ben) outcome enum, "failure"

- cdevents-translator [design PR](https://github.com/cdevents/community/pull/42/files) review

### Jan 22, 2024

Participants:
- Andrea Frittoli, IBM, UTC
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, UTC-6
- Andrew Larsen, SAS, UTC-4
- Christian Provenzano, Fidelity, UTC-4
- Jalander Ramagiri, Ericsson Software Technology, UTC
- Brett Smith, SAS, UTC-4
- Adam Kenihan, Ericsson Software Technology, UTC
- Sean Brennan, Bloomberg, UTC-5

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees
    - Hergy Fongue, Prodyna, UTC

- Action Items
    - Owen to create an issue about capitalizing URI
    - ~~Andrea to create an issue about conformance groups~~
        - https://github.com/cdevents/spec/issues/182
    - Andrea to formalise a proposal for [#168](https://github.com/cdevents/spec/issues/168) in an hackmd doc linked into the issue

- OpenTelemetry CI/CD Observability
    - Working Group approved by the TC
    - See https://github.com/open-telemetry/community/pull/1822

- Rust SDK
    - Two new contributors, Hergy (since 2021) and David
        - https://github.com/cdevents/sdk-rust
        - David's project: https://github.com/davidB/cdviz 
    - Setting up CI and generator framework

- [Ticket Proposal](https://github.com/cdevents/spec/pull/180)
    - Please review!

- [Link Proposal](https://github.com/cdevents/spec/pull/139)
    - Only few things left to address
    - Versioning with `-draft` fixed
    - Almost ready for finaly review, Ben to ping the team on slack once ready

- (Ben) Enum discussion around outcome
    - https://github.com/cdevents/spec/blob/main/schemas/testsuiterunfinished.json#L101
    - Should we use past tense in enums?
    - Let's check with Ole / testkube if it's ok to replace enum values
        - If not, we could add new values and deprecate the old ones, which adds complexity for consumers
        - Document that we shall use past tense in enums, predicates etc
    - PR for the testing events: https://github.com/cdevents/spec/pull/105
    - Christian: verbs can be made past tense but nouns (e.g. "error") shall be kept, "errored" sounds strange
    - For reference, this is how it is defined in the Eiffel protocol:
        - [Activity outcomes](https://github.com/eiffel-community/eiffel/blob/master/eiffel-vocabulary/EiffelActivityFinishedEvent.md#dataoutcome) (like pipelines, tasks, builds)
        - [Test execution outcomes](https://github.com/eiffel-community/eiffel/blob/master/eiffel-vocabulary/EiffelTestCaseFinishedEvent.md#dataoutcome)

- (Brett) CDEvents Workshop
    - Updates to EPR ongoing - https://github.com/sassoftware/event-provenance-registry
    - Workshop Repository - https://github.com/cdevents/event-provenance-registry-workshop

- (Andrew) Event Provenance Registry CD Foundation Blog Post
    - SAS Legal/Marketing Approved 
    - SAS to post a companion blog post for developer community to point to the CDF post
    - Waiting on a few features to be merged in EPR to publish
    - What are the next steps when we're ready to publish?
        - Talk to Michelle Martineau and Roxanne Joncas.

- GB Elections
    - Election Official
        - Should not be a nominee
    - Governance documentation: https://github.com/cdevents/community/blob/main/governance.md



### Jan 22, 2024, EMEA/APAC

Participants:
- Andrea Frittoli, IBM, UTC

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- No attendees - cancelled


### Jan 15, 2024

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, UTC-6
- Adam Kenihan, EST, UTC+0
- Andrea Frittoli, IBM, UTC
- Jalander Ramagiri, Ericsson Software Technology, UTC

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:
- New attendees

- Action Items
    - Owen to create an issue about capitalizing URI
    - Andrea to create an issue about conformance groups
    - ~~Andrea to update the [Artifact PR](https://github.com/cdevents/spec/pull/172) based on feedback~~
    - ~~Andrea to update the [SBOM PR](https://github.com/cdevents/spec/pull/171) based on feedback~~
    - ~~Andrea to make an Release Candidate of Java SDK in Jan to let people test it~~
    - Andrea to formalise a proposal for [#168](https://github.com/cdevents/spec/issues/168) in an hackmd doc linked into the issue

- Artifact PRs https://github.com/cdevents/spec/pull/172
    - Ready to merge after spell check fixed

- Initial design review [cdevents-translator common library](https://github.com/cdevents/community/pull/42)
    - (Action) Ben to review and meet with Jalander to discuss this
    - Emil: should it be called cdevents-scm-translator?
    - Jalander: in future it could be extended to non-SCM events

- Ticket Proposal
    - Sean working on the proposal, draft should be available this week
    - Ben will do initial review, everyone welcome to wait or review as they wish

- Link Proposal https://github.com/cdevents/spec/pull/139
    - We should have a CI job about the `-draft`
    - Emil: this is also related to doc documentation

- Outcome missing PR https://github.com/cdevents/spec/pull/179
    - Ben to add enums to TaskRuns and PipelineRuns as well as follow-up
    - Emil: it could be in one PR too, since it's the same enum
    - Examples to be updated

- Java SDK v0.3 released
    - Apple working on iternal POC with CDEvents

- Updatecli published blog
    - https://www.updatecli.io/blog/cd-events-and-updatecli/
    - 

- Flux + CDEvents (Adam)
    - RFC has got one approval, pending second approval
    - https://github.com/fluxcd/flux2/pull/4534

- OpenTelemetry
    - CI/CD Observability SIG to be formed: https://github.com/open-telemetry/community/pull/1822/files#diff-41c277076e06d5ea84d2e8bc9eded2bc97e7f0888502f4f8d691b6c5c3639e57
    - Pending review 

- Approvals
    - Ben to start working on this after the link proposal is merged
    - Emil: the change updated event could be used?
    - The approval could be on a pipeline or process, so multiple subjects
    - Could be a dedicated event or a new predicate on several subjects

- Apple f2f meeting happening to discuss CDEvents



- \<addme\>


### Jan 08, 2024

Participants:
- Emil Bäckmark, Ericsson, UTC+1
- Ben Powell, Apple, UTC-6
- Brett Smith, SAS, UTC-4

Links:
- [v0.4 Roadmap](https://github.com/orgs/cdevents/projects/1/views/13)

Agenda:

- New attendees

- Action Items
    - ~~Ben to prepare a demo on the maintainability topic~~
        - ~~Topic will be raised when the demo is prepared~~
    - Owen to create an issue about capitalizing URI
    - ~~Andrea to archive meeting notes for 2023~~
        - ~~Done by Emil~~
    - Andrea to create an issue about conformance groups
    - Andrea to update the [Artifact PR](https://github.com/cdevents/spec/pull/172) based on feedback
    - Andrea to update the [SBOM PR](https://github.com/cdevents/spec/pull/171) based on feedback
    - Andrea to make an Release Candidate of Java SDK in Jan to let people test it
    - Andrea to formalise a proposal for [#168](https://github.com/cdevents/spec/issues/168) in an hackmd doc linked into the issue


- (Sean/Ben) Ticket/Approvals Proposal
    - [Tickets/issues](https://github.com/cdevents/spec/issues/164)
    - [Draft proposal](https://hackmd.io/9eTiXHu6RfedSuSwUMGTLw?both)
    - Proposal planned for 1st/2nd week in Jan 2024

- (Brett) CDEvents Workshop
    - Updates to EPR ongoing - https://github.com/sassoftware/event-provenance-registry

- (Ben) Outcome missing from build events
    - It was probably just not added when the build events where specified.
    - Proposal is to use the same syntax as in taskRun.finished for example (https://github.com/cdevents/spec/blob/main/core.md#taskrun-finished)
    - Ben might do a PR for it

- (Ben) Java SDK new issues filed
    - https://github.com/cdevents/sdk-java/issues/64
    - https://github.com/cdevents/sdk-java/issues/65
    - https://github.com/cdevents/sdk-java/issues/67
    - https://github.com/cdevents/sdk-java/issues/68
    - (Emil) looks reasonable
    - Ben to ping Jalander for input and possible PRs to be created

- (Ben) GitHub webhook adapter
    - First discussions held with Jalander
    - Kind of related to https://github.com/cdevents/github-action but rather uses the GitHub webhook than GitHub actions.

- \<addme\>
