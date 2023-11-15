# CDEvents Governance

The CDEvents Governing Board is the governing body of the CDEvents open source project. It's an elected group that represents the contributors to the project, and has an oversight on governance and technical matters.


- [CDEvents Governing Board](#CDEvents-governing-board)
- [Governance Facilitator Role (optional)](#governance-facilitator-role-optional)
- [Maximum Representation](#maximum-representation)
- [Committee Responsibilities and Deliverables](#committee-responsibilities-and-deliverables)
- [Governance Meetings and Decision-Making Process](#governance-meetings-and-decision-making-process)
- [Elections](#elections)
- [Permissions and access](#permissions-and-access)
- [Governing Board leave policy](#governing-board-leave-policy)

## CDEvents Governing Board

The CDEvents Governing Board consists of five elected individuals. The five seats are held for two year terms, staggered by one year: every year either two or three of the seats are up for election.

### Current members (Bootstrap)

| Full Name         | Company    | GitHub                                      | Slack                                                         | From | Until    |
|-------------------|:----------:|---------------------------------------------|---------------------------------------------------------------|------------|----------|
| Emil Bäckmark     | Ericsson   | [@e-backmark-ericsson](https://github.com/e-backmark-ericsson) | [@Emil Bäckmark](https://cdeliveryfdn.slack.com/team/USR6E330D) | Oct 2021 | 1 year after first election |
| Andrea Frittoli   | IBM        | [@afrittoli](https://github.com/afrittoli)  | [@Andrea Frittoli](https://cdeliveryfdn.slack.com/team/URNB1NTGR)   | Oct 2021 | 1 year after first |
| Mattias Linnér    | Ericsson   | [@m-linner-ericsson](https://github.com/m-linner-ericsson) | [@Mattias Linnér](https://cdeliveryfdn.slack.com/team/U01AHR341T8) | Oct 2021 | First Election |
| Erik Sternerson   | Volvo Cars | [@erkist](https://github.com/erkist) | [@Erik Sternerson](https://cdeliveryfdn.slack.com/team/U01HSV3UVAN) | Oct 2021 | First Election |
| Steve Taylor      | DeployHub  | [@sbtaylor15](https://github.com/sbtaylor15) | [@Steve Taylor](https://cdeliveryfdn.slack.com/team/U01FMSQSZBN) | Oct 2021 | First Election |

There is no designated facilitator at the moment, the responsibility is distributed across the five members of the committee.

The committee MUST:

* Represent a cross-section of interests, not just one company
* Balance technical, architectural, and governance expertise since its initial mission is the establishment of structure around contributions, community, and decision-making
* Hold staggered terms, sufficient to ensure an orderly transition of power via elections as designed and implemented by the committee (see below for specific deliverables)
* Provide designated alternates in cases where quorum is required but not attainable with the current set of members
* Communicate with the Continuous Delivery Foundation on a regular cadence

#### Former members ❤️

None yet.

## Governance Facilitator Role (optional)

The governance facilitator role is a non-voting, non-technical advisory position that helps ensure all Governing Board meetings are inclusive, and key milestones toward governance are met. The facilitator is a role, meaning it may be occupied by a single individual, or a series of individuals over time. The goal of this position is servant leadership for the project, community, and stakeholders. The committee may choose to make this a permanent role at their discretion. Deliverables may include creation of mailing lists, project tracking boards, governance draft documents, and so forth.

## Maximum Representation

No single employer/company may be represented by more than 40% (i.e., 2 seats) of the board at any one time. If the results of an election result in greater than 40% representation, the lowest vote getters from any particular company will be removed until representation on the board is less than one-third.

If percentages shift because of job changes, acquisitions, or other events, sufficient members of the committee must resign until max one-third representation is achieved. If it is impossible to find sufficient members to resign, the entire company’s representation will be removed and new special elections held. In the event of a question of company membership (for example evaluating independence of corporate subsidiaries) a majority of all non-involved Governing Board members will decide.

## Committee Responsibilities and Deliverables

The committee MUST:

- [Represent a cross-section of interests, not just one company](#maximum-representation)
- Balance technical, architectural, and governance expertise
- Hold staggered terms, sufficient to ensure an orderly transition of power via elections
- Provide designated alternates in cases where quorum is required but not attainable with the current set of members
- Communicate with the Continuous Delivery Foundation on a regular cadence

The committee is responsible for a series of specific artifacts and activities:

- The [Code of Conduct](https://github.com/cdevents/.github/blob/main/docs/CODE_OF_CONDUCT.md) and handling violations
- The [Project Communication Channels](README.md#how-to-get-involved)
- The [Contribution Process and Standards](README.md#contributing)
- The [CDEvents Mission and Vision](https://cdevents.dev)
- Select [election officers](#election-officers) to run elections

## Governance Meetings and Decision-Making Process

Governance decisions, votes and questions should take place on the cdevents-governance@googlegroups.com mailing list.
The mailing list is publicly readable by everyone.

The Governing Board decisions are taken by seeking consensus towards a motion from all its members. If the consensus cannot be reached, the motion may be altered or dropped.

## Elections

### Voter Eligibility

Anyone who has at least 5 [contributions](/processes.md#contributions) in the last 12 months. The [dashboard on cdevents.devstats.cd.foundation](https://cdevents.devstats.cd.foundation/d/9/developer-activity-counts-by-repository-group-table?orgId=1&var-period_name=Last%20year&var-metric=contributions&var-repogroup_name=All&var-country_name=All) will show GitHub based contributions; contributions that are not GitHub based must be called out explicitly by the voter to confirm eligibility.

### Candidate Eligibility

Candidates themselves must be [contributors](/processes.md#contributor) who are eligible to vote, and must be nominated by contributors from at least two companies, which can include their own, and they can self-nominate.

### Nominations Process

The election officers may decide how to implement the nomination process, as long as the following requirements are fulfilled:

- Nominations are publicly readable
- Nominations are persisted over time and can be linked to for future reference
- Nominations shall contain:
  - The nominee’s email address, github handle, company affiliation, and CDEvents project(s) they contribute to
  - For each of two contributors nominating this individual:
    - The company they work for
    - Their github handles
    - The CDEvents project(s) they contribute to
- Nominee must be nominated by contributors from at least two companies, and they can self-nominate
- Once all requirements are satisfied, one election officer shall mark the nomination as accepted
- Nominee may decline a nomination, though it is recommended to reach out to the nominee before posting a public nomination

Two common ways of implementing nominations are either via a dedicated mailing list (e.g. `cdevents-governance@googlegroups.com` or through a dedicated GitHub issue in the community repo). 

Any nominee who accepts the nomination will be on the ballot.

### Election Process

Elections will be held using time-limited [Condorcet](https://en.wikipedia.org/wiki/Condorcet_method) ranking on [CIVS](https://civs.cs.cornell.edu/) using the [Schulze method](https://en.wikipedia.org/wiki/Schulze_method). The top vote getters will be elected to the open seats. This is the same process used by the Kubernetes project. Voters must opt into the CIVS system at https://civs1.civs.us/cgi-bin/opt_in.pl or they won't receive an invitation to vote.

It may not always be possible for election officers to have access to all voters e-mail addresses. Nomination officials should setup a form or alternate mechanism for eligible voters to share their e-mail address for voting purposes.

Details about the schedule and logistics of the election will be announced in a timely manner by the election officers to eligible candidates and voters via the cdevents-dev@googlegroups.com mailing list, on the #cdevents slack channel and at CDEvents working group meetings.

Example timeline:

1. Before or during nominations, send an email to all eligible voters to notify them that they are eligible (allowing people time to reach out if they believe they are eligible but are not on our list)
1. Prompt eligible voters to opt into CIVS at https://civs1.civs.us/cgi-bin/opt_in.pl so they will be able to vote
1. 1 week for nominations (starting on a Thursday until midnight UTC the next Wednesday)
1. 1 week for the election itself (starting the following Thursday until midnight UTC the next Wednesday)

### Election Officers

For every election, the Governing Board wll choose two election officers, by the following criteria, so as to promote healthy rotation and diversity:

- election officers must be eligible to vote
- one election officers should have served before
- one election officer should have never served before
- each officer should come from a different company to maintain 50% maximal representation
- election officers should not be currently running in the election

The Governing Board can decide to make exceptions to the above requirements if needed (for example, if two people cannot be found who have served before and want to be officers).

### Vacancies

In the event of a resignation or other loss of an elected Governing Board member, the candidate with the next most votes from the previous election will be offered the seat. This process will continue until the seat is filled.

In case this fails to fill the seat, a special election for that position will be held as soon as possible. Eligible voters from the most recent election will vote in the special election (ie: eligibility will not be redetermined at the time of the special election). A board member elected in a special election will 
serve out the remainder of the term for the person they are replacing, regardless of the length of that remainder.

### Changes to Governing Board

When someone joins the Governing Board:

- They should be added to [the list of current Governing Board members](#current-members)
- They will be added as "owners" to [the CDEvents GitHub org](https://github.com/cdevents/) via the `governance` GitHub team
- They will be added to these mailing lists as owners:
  - [`cdevents-governance`](https://groups.google.com/g/cdevents-governance)
  - [`cdevents-dev`](https://groups.google.com/g/cdevents-dev)
  - [`cdevents-code-of-conduct`](https://groups.google.com/g/cdevents-code-of-conduct)

When someone leaves the Governing Board:

- They should be moved from
  [the list of current Governing Board members](#current-members) to
  [the list of former members](#former-members-%EF%B8%8F)
- They will be removed as admins from [the CDEvents GitHub org](https://github.com/cdevents)
- They will be removed from the `governance` GitHub team
- They will be removed as owners from these mailing lists:
  - [`cdevents-governance`](https://groups.google.com/g/cdevents-governance)
  - [`cdevents-dev`](https://groups.google.com/g/cdevents-dev)
  - [`cdevents-code-of-conduct`](https://groups.google.com/g/cdevents-code-of-conduct)

### Exceptions

There could be cases where Election Officers may need to follow different processes to ensure the election process can be completed.

One such case is the number of candidates who run for the Governing Board elections. If the number of candidates is less than the number of seats up for election in Governing Board, Election Officers are authorized to extend the nomination period for one more week. If the number of candidates is still less than the number of seats in Governing Board, Election Officers are authorized to end the nomination and election process so all the candidates assume their seats without election. The remaining seats are left vacant. The new Governing Board is responsible to determine if, when, and how to fill the vacant seats. If the number of candidates is equal to the number of seats in Governing Board, Election Officers are authorized to end the nomination and election process so all the candidates assume their seats without election.

## Governing Board leave policy

Any member of the Governing Board is welcome to take leave from being a Governing Board member, for any reason (which they are not required to disclose). The actions taken will depend on both of:

1. The length of the leave: whether this is greater or less than approximately (at the discretion of the other Governing Board members) 1/4 of their total term (since terms are 2 years, this means the criteria is whether or not the leave is greater than 6 months).
2. Whether their seat will be up for election during the period of their leave

If the leave is less than or equal to 1/4 of the board member's total term, and their seat will not be up for re-election during that time, the Governing Board member may select someone to be an acting Governing Board member for the length of the leave. This person must:

- Meet [the maximum representation requirement](#maximum-representation)
- Meet [the candidate eligibility requirements](#candidate-eligibility)

If the length of the leave is greater than 1/4 of the total term, or their seat will be up for election during the leave period, the Governing Board member will
be required to step down from their seat and an election will be held.

## Code of Conduct

The code of conduct MUST set expectations for contributors on expected behavior, as well as explaining the consequences of violating the terms of the code.
The [Contributor Covenant](https://www.contributor-covenant.org) has become the de facto standard for this language.

Members of the Governing Board are responsible for handling [CDEvents code of conduct](https://github.com/cdevents/.github/blob/main/docs/CODE_OF_CONDUCT.md)
violations via cdevents-code-of-conduct@googlegroups.com.

## Outstanding Policies

The following policies have not yet been fully detailed by the governing committee.

### Roadmap and Meetings

Define and maintain the project roadmap:
* How is work tracked? Example steering project board

How are meetings conducted:
* Recorded or not, and if not, how is the information shared
* Frequency, duration, and required consistency

### Contribution Process

The committee MUST define a contribution process that:

* Explains to potential contributors how/if they can add code to the repository/repositories
* Documents Workflow and management of pull requests
* Identifies who is authorized to commit or revert code
* Identifies automation is required for normal operations
* Defines how release decisions are made
  * Who is authorized to release and when.
  * Frequency limits
* Defines the documentation process
* Defines what Contributor License Agreement (CLA) process is required and how it is programmatically enforced before code is merged

### Security/Vulnerability Reporting and Response Process

* Identify and document where vulnerability reporting can be done to the project
* Identify and document who is responsible for receiving vulnerability reports
* Document process responsible parties go through to triage and determine veracity of vulnerability
* Document process for facilitating fix, generating release update, and communicating vulnerability and fix to public
