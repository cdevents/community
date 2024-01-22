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
- [2023 Meeting Notes](https://github.com/cdevents/community/blob/main/working-group-notes-2023.md)

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
    - ~~Andrea to create an issue about conformance groups
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
