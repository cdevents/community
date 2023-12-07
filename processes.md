# CDEvents project processes

This doc explains general development processes that apply to all projects within the org. Individual projects may have their own processes as well, which you can find documented in their individual CONTRIBUTING.md files.

## Contributions

We try and track community contributions as much as possible to measure the health of the project.

Contributions can include opening PRs, reviewing and commenting on PRs, opening and commenting on issues, writing design docs, commenting on design docs, helping people on slack, and participating in working groups. Where possible, we use dashboards on [cdevents.devstats.cd.foundation](https://cdevents.devstats.cd.foundation) to track measurable engagement. We try our best to include contributions that are not GitHub, but accuracy varies when we don't have easily available data.

See our [contributor ladder](#contributor-ladder) for more information.

## Contributor Ladder

<!--Big thanks to the folks at https://github.com/cncf/project-template
for providing the base framework for this section.-->

This contributor ladder outlines the different contributor roles within the project, along with the responsibilities and privileges that come with them. Community members generally start at the first levels of the "ladder" and advance up it as their involvement in the project grows. Our project members are happy to help you advance along the contributor ladder.

Each of the contributor roles below is organized into lists of three types of things. "Responsibilities" are things that contributor is expected to do. "Requirements" are qualifications a person needs to meet to be in that role, and "Privileges" are things contributors on that level are entitled to.

### Community Participant

Description: A Community Participant engages with the project and its community, contributing their time, thoughts, etc. Community participants are usually users who have stopped being anonymous and started being active in project discussions.

* Responsibilities:
  * Must follow the [CDEvents Code of Conduct](https://github.com/cdevents/.github/blob/main/docs/CODE_OF_CONDUCT.md)
* How users can get involved with the community:
  * Participating in community discussions
    ([GitHub, Slack, mailing list, etc](/README.md#how-to-get-involved))
  * Helping other users
  * Submitting bug reports
  * Commenting on issues
  * Trying out new releases
  * Attending community events

### Contributor

Description: A Contributor makes direct contributions to the project and adds value to it. [Contributions need not be code](#contributions). People at the Contributor level may be new contributors, and they can contribute occasionally.

Contributors may be eligible to vote and run in elections. See [Elections](/governance.md#elections) for more details.

A Contributor must meet the responsibilities of a [Community Participant](#community-participant), plus:

* Responsibilities include:
  * Follow the project contributing guide (see `CONTRIBUTING.md` in the
    corresponding repo)
* Requirements (one or several of the below):
  * Report and sometimes resolve issues
  * Occasionally submit PRs
  * Contribute to the documentation
  * Participate in [meetings](/README.md#how-to-get-involved)
  * Answer questions from other community members
  * Submit feedback on issues and PRs
  * Test, review, and verify releases and patches
* Privileges:
  * Invitations to contributor events
  * Eligible to become an [Organization Member](#organization-member)

### Organization Member

Description: An Organization Member is an established contributor who regularly participates in the project. Organization Members have privileges in project repositories.

An Organization Member must meet the responsibilities and has the requirements of a [Contributor](#contributor), plus:

* Responsibilities include:
  * Continues to contribute regularly, as demonstrated by having at least 15
    contributions a year, as demonstrated by
    [the CDEvents devstats dashboard](https://cdevents.devstats.cd.foundation/d/9/developer-activity-counts-by-repository-group-table?orgId=1&var-period_name=Last%20year&var-metric=contributions&var-repogroup_name=All&var-country_name=All).
* Requirements:
  * Subscribed to the [cdevents-dev mailing list](/README.md#how-to-get-involved).
  * Actively contributing to 1 or more subprojects.
  * Must have successful contributions to the project, including at least one of
    the following:
    * Authored or Reviewed 5 PRs,
    * Or be endorsed by at least 2 existing Org Members:
      * Endorsers should have close interactions with the prospective member - e.g. code/design/proposal review, coordinating on issues, etc.
      * Endorsers must be maintainers of at least one of the CDEvents sub-projects.
      * Endorsers must be from multiple member organizations to demonstrate integration across community.
  * Must have 2FA enabled on their GitHub account
* Privileges:
  * [GitHub default organization member privileges](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#permissions-for-organization-roles)
  * Can recommend other contributors to become Org Members

The process for a Contributor to become an Organization Member is as follows:

1. Request an organization owner to be added to the GitHub organization

## Maintainer

Description: Maintainers are very established contributors who are responsible for entire projects. As such, they have the ability to approve PRs against any area of a project, and are expected to participate in making decisions about the strategy and priorities of the project.

A Maintainer must meet the responsibilities and requirements of an [organization member](#organization-member), plus:

- Responsibilities include:
  - Proactively help triage and respond to incoming issues (GitHub, Slack, mailing list)
  - Reviewing PRs that involve multiple parts of the project
  - Mentoring new [Contributors](#contributor)
  - Writing PRs that involve many parts of the project (e.g. refactoring)
  - Participating in CDEvents maintainer activities (Facilitate working group, triage issues)
  - Determining strategy and policy for the project
  - Participating in, and leading, community meetings
  - Mentoring other contributors
- Requirements
  - Has been actively participating in reviews for at least 3 months or 50% of the project lifetime, whichever is shorter
  - Has authored or reviewed at least 10 PRs to the codebase.
    - Has been the primary reviewer for at least 5 substantial PRs to the codebase.
  - Demonstrates a broad knowledge of the project across multiple areas
  - Is able to exercise judgement for the good of the project, independent of their employer, friends, or team
  - Be nominated by another Maintainer (with no objections from other Maintainers)
- Additional privileges:
  - Approve PRs to any area of the project
  - Granted access to shared CDEvents CI/CD infrastructure
  - Represent the project in public as a Maintainer
  - Have a vote in Maintainer decision-making meetings

To facilitate productivity, small repositories, repositories that do not contain production code or that have a low traffic of PRs may decide to use simpler requirements. Each of these projects may define their own requirements, in a local `processes.md` file.

Process of becoming an Maintainer:

1. Any current Maintainer may nominate a current [organization member](#organization-member) to become a new Maintainer, by opening an issue against the appropriate project.
2. The nominee will add a comment to the issue testifying that they agree to all requirements of becoming a Maintainer.
3. A majority of the current Maintainers must then approve.
4. Add the new maintainer to the corresponding GitHub team
5. (Optional) Update `CODEOWNWERS` with specific areas of expertise for the new maintainer. Add the new maintainer to the list of maintainers kept in a comment in `CODEOWNWERS`.

- Each project has a `<repo>-maintainers` team, where `<repo>` is the name of the GitHub repository.

## Governing Board Member

Description: The CDEvents Governing board is the governing body of the CDEvents open source project. It's an elected group that represents the contributors to the project, and has an oversight on governance and technical matters.

See [governance.md](/governance.md) for requirements, responsibilities, and election process.

- Additional privileges:
  - Maintainer privileges on all CDEvents projects
  - Organization admin access.

Members of the governing board belong to the the `governance` GitHub team.

## Inactivity

It is important for contributors, especially maintainers and governing board members, to be and stay active to set an example and show commitment to the project. Inactivity is harmful to the project as it may lead to unexpected delays, contributor attrition, and a lost of trust in the project.

- Inactivity is measured by:
  - Failing to meet role requirements.
  - Periods of no [contributions](./README.md#contributions) for longer than 4 months
  - Periods of no communication for longer than 2 months
- Consequences of being inactive include:
  - Involuntary removal or demotion
  - Being asked to move to Emeritus status

### Involuntary Removal or Demotion

Involuntary removal/demotion of a contributor (at any level) happens when responsibilities and requirements aren't being met. This may include repeated patterns of inactivity, extended period of inactivity, a period of failing to meet the requirements of your role, and/or a violation of the Code of Conduct. This process is important because it protects the community and its deliverables while also opens up opportunities for new contributors to step in.

Involuntary removal or demotion is handled through a vote by a majority of the [CDEvents Governing Board](/governance.md).

### Stepping Down/Emeritus Process

If and when contributors' commitment levels change, contributors (at any level) can consider stepping down (moving down the contributor ladder) vs moving to emeritus status (completely stepping away from the project).

[Community participants](#community-participant), [contributors](#contributor) and [organization members](#organization-member) may reduce their contributor level autonomously.

[Maintainers](#maintainer) shall contact the other maintainers about changing to Emeritus status, or reducing their contributor level.
CDEvents projects may opt for tracking emeritus maintainers in their `CODEOWNERS` file.

[Governing Board members](#governing-board-member) shall contact the other Governing Board members about changing to Emeritus status, or reducing their contributor level.
Emeritus Governing Board members are tracked in the [governance](/governance.md#former-members-❤️) documentation.