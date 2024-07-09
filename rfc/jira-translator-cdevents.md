## Jira-CDEvents Integration

### Design-Overview:
Jira emits variuos type of events like Issue related, Project related, User related, Configuration and Software related.
[Jira webhooks](https://developer.atlassian.com/server/jira/platform/webhooks/) can be configured to notify external applications when certain events occur in Jira.

CDEvents can be integrated with Jira using CDEvents's [webhook-adapter](https://github.com/cdevents/webhook-adapter) which exposes an interface to be implemented as plugin.


### Jira-translator-CDEvents:

`jira-translator-cdevents` plugin will be implemented to translate [Jira events](https://developer.atlassian.com/platform/forge/events-reference/jira/) into CDEvents and served using Hashicorp's [go-plugin](https://github.com/hashicorp/go-plugin/).

The plugin details needs to be updated in webhook-adapter's [translator-plugins.yaml](https://github.com/cdevents/webhook-adapter/blob/main/translator-plugins.yaml) to serve as a translator endpoint, which is configured as Jira Webhook URL.

Issue related Jira events can be mapped to CDEvent's [Ticket Events](https://cdevents.dev/docs/tickets/), The below is the list of CDEvents Ticket Events will be mapped with corresponding Jira event types.



| CDEvent Type  | Jira Event Type  | Comments / Jira Event Format   |
| :------------ |:-------------------|:----------------------------------|
| dev.cdevents.ticket.created| jira:issue_created  | [`Issue ceated event JSON`](#jiraissue_created) |
|  dev.cdevents.ticket.updated   | jira:issue_updated </br> jira:worklog_updated  |`jira:issue_updated` event type has various actions, issue_updated  issue_commented, issue_assigned </br>[`Issue updated event JSON`](#jiraissue_updated) </br>[`Issue commented event JSON`](#jiraissue_commented) </br>[`Issue assigned event JSON`](#jiraissue_assigned) </br></br>  `jira:worklog_updated` event type has various actions, issue_work_logged  issue_worklog_updated, issue_worklog_deleted </br> [`Issue work logged event JSON`](#jiraissue_work_logged) </br>[`Issue worklog updated event JSON`](#jiraissue_worklog_updated) </br>[`Issue worklog deleted event JSON`](#jiraissue_worklog_deleted) |
| dev.cdevents.ticket.closed |   jira:issue_updated   | For ticket closed the type `issue_generic` will be created with the `resolution` field set to `Done` </br>[`Issue updated generic event JSON`](#jiraissue_generic) |


#### jira:issue_created

<details><summary>Issue ceated event JSON</summary>

```json

{
  "timestamp": 1716991458232,
  "webhookEvent": "jira:issue_created",
  "issue_event_type_name": "issue_created",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": null,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": null,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": null,
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 0,
        "isWatching": false
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": null,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "updated": "2024-05-29T15:04:18.022+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira",
      "timetracking": {},
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": null,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@6f5ce47b[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2658d383[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@5d1d8c4f[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@3db998a4[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@14ec6fe6[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@fb11e8b[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@3eff84c6[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@4ff25705[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@38968242[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@3fd4869d[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@7d4fec15[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@2058d6c6[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 0
      },
      "comment": {
        "comments": [],
        "maxResults": 0,
        "total": 0,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  }
}
```
</details>

#### jira:issue_updated
<details><summary>Issue updated event JSON</summary>

```json

{
  "timestamp": 1716992387526,
  "webhookEvent": "jira:issue_updated",
  "issue_event_type_name": "issue_updated",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": null,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": null,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-29T15:14:18.184+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": null,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "updated": "2024-05-29T15:19:47.389+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {},
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": null,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@314e1b0d[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2d06df[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@35d32094[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@5d20d30f[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@38ef0f2a[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@6ae24cd6[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@4619169e[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@1dfa0df9[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@5dacc733[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@2550a4ac[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2b73fb7e[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@662bae2c[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 0
      },
      "comment": {
        "comments": [],
        "maxResults": 0,
        "total": 0,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10027",
    "items": [
      {
        "field": "description",
        "fieldtype": "jira",
        "from": null,
        "fromString": "CDEvents integration with Jira",
        "to": null,
        "toString": "CDEvents integration with Jira updates needed"
      }
    ]
  }
}

```
</details>

#### jira:issue_commented

<details><summary>Issue commented event JSON</summary>

```json
{
  "timestamp": 1716992564052,
  "webhookEvent": "jira:issue_updated",
  "issue_event_type_name": "issue_commented",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": null,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": null,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-29T15:19:47.733+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": null,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "updated": "2024-05-29T15:22:43.937+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {},
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": null,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@451a472c[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@f57ab5c[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@507b8518[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@62c4d900[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@259bef5a[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@1e20a2da[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@127fa743[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@563760d5[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2caca476[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@3701f54b[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@582b0957[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@3577fb4f[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 0
      },
      "comment": {
        "comments": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
            "id": "10019",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "is the issue fixed?",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-29T15:22:43.937+0100",
            "updated": "2024-05-29T15:22:43.937+0100"
          }
        ],
        "maxResults": 1,
        "total": 1,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  },
  "comment": {
    "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
    "id": "10019",
    "author": {
      "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
      "name": "rjalander",
      "key": "JIRAUSER10000",
      "emailAddress": "jalander.ramagiri@est.tech",
      "avatarUrls": {
        "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
        "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
        "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
        "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
      },
      "displayName": "jalander.ramagiri@est.tech",
      "active": true,
      "timeZone": "Europe/Dublin"
    },
    "body": "is the issue fixed?",
    "updateAuthor": {
      "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
      "name": "rjalander",
      "key": "JIRAUSER10000",
      "emailAddress": "jalander.ramagiri@est.tech",
      "avatarUrls": {
        "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
        "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
        "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
        "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
      },
      "displayName": "jalander.ramagiri@est.tech",
      "active": true,
      "timeZone": "Europe/Dublin"
    },
    "created": "2024-05-29T15:22:43.937+0100",
    "updated": "2024-05-29T15:22:43.937+0100"
  }
}

```
</details>

#### jira:issue_assigned

<details><summary>Issue assigned event JSON</summary>

```json
{
  "timestamp": 1717163183565,
  "webhookEvent": "jira:issue_updated",
  "issue_event_type_name": "issue_assigned",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": null,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": null,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-31T14:46:23.243+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": null,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": null,
      "updated": "2024-05-31T14:46:23.467+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {},
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": null,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@5bb224de[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@67fcd09d[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@3a883ec7[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@3bf17933[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@64eb3b4f[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@344a5f8[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@7841dd51[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@48c90b8b[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@7545609e[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@530860ab[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@25d594ce[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@25c056ac[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 0
      },
      "comment": {
        "comments": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
            "id": "10019",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "is the issue fixed?",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-29T15:22:43.937+0100",
            "updated": "2024-05-29T15:22:43.937+0100"
          },
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10100",
            "id": "10100",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "updating to Unassigned",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-31T14:46:23.440+0100",
            "updated": "2024-05-31T14:46:23.440+0100"
          }
        ],
        "maxResults": 2,
        "total": 2,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10100",
    "items": [
      {
        "field": "assignee",
        "fieldtype": "jira",
        "from": "JIRAUSER10000",
        "fromString": "jalander.ramagiri@est.tech",
        "to": null,
        "toString": null
      }
    ]
  },
  "comment": {
    "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10100",
    "id": "10100",
    "author": {
      "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
      "name": "rjalander",
      "key": "JIRAUSER10000",
      "emailAddress": "jalander.ramagiri@est.tech",
      "avatarUrls": {
        "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
        "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
        "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
        "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
      },
      "displayName": "jalander.ramagiri@est.tech",
      "active": true,
      "timeZone": "Europe/Dublin"
    },
    "body": "updating to Unassigned",
    "updateAuthor": {
      "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
      "name": "rjalander",
      "key": "JIRAUSER10000",
      "emailAddress": "jalander.ramagiri@est.tech",
      "avatarUrls": {
        "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
        "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
        "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
        "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
      },
      "displayName": "jalander.ramagiri@est.tech",
      "active": true,
      "timeZone": "Europe/Dublin"
    },
    "created": "2024-05-31T14:46:23.440+0100",
    "updated": "2024-05-31T14:46:23.440+0100"
  }
}

```
</details>

#### jira:issue_work_logged

<details><summary>Issue work logged event JSON</summary>

```json
{
  "timestamp": 1717164468987,
  "webhookEvent": "jira:worklog_updated",
  "issue_event_type_name": "issue_work_logged",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": 46800,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": 46800,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-31T15:07:48.793+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": 0,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": null,
      "updated": "2024-05-31T15:07:48.986+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {
        "remainingEstimate": "0m",
        "timeSpent": "1d 5h",
        "remainingEstimateSeconds": 0,
        "timeSpentSeconds": 46800
      },
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": 0,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@1bbaf445[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@490e04f7[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@78895598[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@4119dfc2[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@460ac642[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@1e33f8ce[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2ca44b05[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@23cc769c[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@33649c71[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@3210f75b[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@3c626e7f[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@7c5a97f9[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 46800,
        "total": 46800,
        "percent": 100
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 46800,
        "total": 46800,
        "percent": 100
      },
      "comment": {
        "comments": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
            "id": "10019",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "is the issue fixed?",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-29T15:22:43.937+0100",
            "updated": "2024-05-29T15:22:43.937+0100"
          },
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10100",
            "id": "10100",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "updating to Unassigned",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-31T14:46:23.440+0100",
            "updated": "2024-05-31T14:46:23.440+0100"
          }
        ],
        "maxResults": 2,
        "total": 2,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 1,
        "worklogs": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/worklog/10000",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "comment": "Work in progress integrating CDEvents with Jira",
            "created": "2024-05-31T15:07:48.978+0100",
            "updated": "2024-05-31T15:07:48.978+0100",
            "started": "2024-05-30T15:06:00.000+0100",
            "timeSpent": "1d 5h",
            "timeSpentSeconds": 46800,
            "id": "10000",
            "issueId": "10023"
          }
        ]
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10101",
    "items": [
      {
        "field": "WorklogId",
        "fieldtype": "jira",
        "from": "10000",
        "fromString": "10000",
        "to": null,
        "toString": null
      },
      {
        "field": "timeestimate",
        "fieldtype": "jira",
        "from": null,
        "fromString": null,
        "to": "0",
        "toString": "0"
      },
      {
        "field": "timespent",
        "fieldtype": "jira",
        "from": null,
        "fromString": null,
        "to": "46800",
        "toString": "46800"
      }
    ]
  }
}

```
</details>

</details>

#### jira:issue_worklog_updated

<details><summary>Issue worklog updated event JSON</summary>

```json
{
  "timestamp": 1717164704071,
  "webhookEvent": "jira:worklog_updated",
  "issue_event_type_name": "issue_worklog_updated",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": 46800,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": 46800,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-31T15:11:44.055+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": 0,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": null,
      "updated": "2024-05-31T15:11:44.070+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {
        "remainingEstimate": "0m",
        "timeSpent": "1d 5h",
        "remainingEstimateSeconds": 0,
        "timeSpentSeconds": 46800
      },
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": 0,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@18f7b9f2[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2c60ebe6[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@38211d67[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@1335ee5e[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@1f3be9e9[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@62027952[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@52788a50[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@6e03d95f[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2eb701d7[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@5f8e35ba[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@49321e11[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@398bef49[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 46800,
        "total": 46800,
        "percent": 100
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 46800,
        "total": 46800,
        "percent": 100
      },
      "comment": {
        "comments": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
            "id": "10019",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "is the issue fixed?",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-29T15:22:43.937+0100",
            "updated": "2024-05-29T15:22:43.937+0100"
          },
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10100",
            "id": "10100",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "updating to Unassigned",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-31T14:46:23.440+0100",
            "updated": "2024-05-31T14:46:23.440+0100"
          }
        ],
        "maxResults": 2,
        "total": 2,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 1,
        "worklogs": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/worklog/10000",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "comment": "Work in progress integrating CDEvents with Jira\r\nWorking with design integration",
            "created": "2024-05-31T15:07:48.978+0100",
            "updated": "2024-05-31T15:11:44.058+0100",
            "started": "2024-05-30T15:06:00.000+0100",
            "timeSpent": "1d 5h",
            "timeSpentSeconds": 46800,
            "id": "10000",
            "issueId": "10023"
          }
        ]
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10102",
    "items": [
      {
        "field": "WorklogId",
        "fieldtype": "jira",
        "from": "10000",
        "fromString": "10000",
        "to": null,
        "toString": null
      }
    ]
  }
}

```
</details>

</details>

#### jira:issue_worklog_deleted

<details><summary>Issue worklog deleted event JSON</summary>

```json
{
  "timestamp": 1717167743759,
  "webhookEvent": "jira:worklog_updated",
  "issue_event_type_name": "issue_worklog_deleted",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10023",
    "self": "http://localhost:9090/rest/api/2/issue/10023",
    "key": "ES-24",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": 0,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i00053:",
      "customfield_10111": null,
      "aggregatetimespent": 0,
      "resolution": null,
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": null,
      "workratio": -1,
      "lastViewed": "2024-05-31T16:02:12.962+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T15:04:18.022+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": 46800,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": null,
      "updated": "2024-05-31T16:02:23.758+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10000",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "To Do",
        "id": "10000",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/2",
          "id": 2,
          "key": "new",
          "colorName": "default",
          "name": "To Do"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": "CDEvents integration with Jira updates needed",
      "timetracking": {
        "remainingEstimate": "1d 5h",
        "timeSpent": "0m",
        "remainingEstimateSeconds": 46800,
        "timeSpentSeconds": 0
      },
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": 46800,
      "summary": "CDEvents integration with Jira",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@12dc1a84[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@2b3dea0[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@606cec3a[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@7cb66849[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@19a6ae48[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@3d72b1c6[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@3af8976e[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@75c34458[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@593b6046[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@71ef0626[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@f52bc92[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@605cd8a4[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 46800,
        "percent": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 46800,
        "percent": 0
      },
      "comment": {
        "comments": [
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10019",
            "id": "10019",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "is the issue fixed?",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-29T15:22:43.937+0100",
            "updated": "2024-05-29T15:22:43.937+0100"
          },
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10100",
            "id": "10100",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "updating to Unassigned",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-31T14:46:23.440+0100",
            "updated": "2024-05-31T14:46:23.440+0100"
          },
          {
            "self": "http://localhost:9090/rest/api/2/issue/10023/comment/10101",
            "id": "10101",
            "author": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "body": "Jira can be integrated with https://github.com/cdevents/webhook-adapter",
            "updateAuthor": {
              "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
              "name": "rjalander",
              "key": "JIRAUSER10000",
              "emailAddress": "jalander.ramagiri@est.tech",
              "avatarUrls": {
                "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
                "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
                "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
                "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
              },
              "displayName": "jalander.ramagiri@est.tech",
              "active": true,
              "timeZone": "Europe/Dublin"
            },
            "created": "2024-05-31T15:14:29.285+0100",
            "updated": "2024-05-31T15:14:29.285+0100"
          }
        ],
        "maxResults": 3,
        "total": 3,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-24/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10106",
    "items": [
      {
        "field": "WorklogId",
        "fieldtype": "jira",
        "from": "10000",
        "fromString": "10000",
        "to": null,
        "toString": null
      },
      {
        "field": "WorklogTimeSpent",
        "fieldtype": "jira",
        "from": "46800",
        "fromString": "1 day, 5 hours",
        "to": null,
        "toString": null
      },
      {
        "field": "timeestimate",
        "fieldtype": "jira",
        "from": "0",
        "fromString": "0",
        "to": "46800",
        "toString": "46800"
      },
      {
        "field": "timespent",
        "fieldtype": "jira",
        "from": "46800",
        "fromString": "46800",
        "to": "0",
        "toString": "0"
      }
    ]
  }
}

```
</details>

#### jira:issue_generic

<details><summary>Issue updated generic event JSON</summary>

```json

{
  "timestamp": 1717165102467,
  "webhookEvent": "jira:issue_updated",
  "issue_event_type_name": "issue_generic",
  "user": {
    "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
    "name": "rjalander",
    "key": "JIRAUSER10000",
    "emailAddress": "jalander.ramagiri@est.tech",
    "avatarUrls": {
      "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
      "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
      "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
      "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
    },
    "displayName": "jalander.ramagiri@est.tech",
    "active": true,
    "timeZone": "Europe/Dublin"
  },
  "issue": {
    "id": "10008",
    "self": "http://localhost:9090/rest/api/2/issue/10008",
    "key": "ES-9",
    "fields": {
      "issuetype": {
        "self": "http://localhost:9090/rest/api/2/issuetype/10002",
        "id": "10002",
        "description": "Created by Jira Software - do not edit or delete. Issue type for a user story.",
        "iconUrl": "http://localhost:9090/images/icons/issuetypes/story.svg",
        "name": "Story",
        "subtask": false
      },
      "timespent": null,
      "project": {
        "self": "http://localhost:9090/rest/api/2/project/10000",
        "id": "10000",
        "key": "ES",
        "name": "EST-SeaTel",
        "projectTypeKey": "software",
        "avatarUrls": {
          "48x48": "http://localhost:9090/secure/projectavatar?avatarId=10324",
          "24x24": "http://localhost:9090/secure/projectavatar?size=small&avatarId=10324",
          "16x16": "http://localhost:9090/secure/projectavatar?size=xsmall&avatarId=10324",
          "32x32": "http://localhost:9090/secure/projectavatar?size=medium&avatarId=10324"
        }
      },
      "fixVersions": [],
      "customfield_10110": "0i0001r:",
      "customfield_10111": 3,
      "aggregatetimespent": null,
      "resolution": {
        "self": "http://localhost:9090/rest/api/2/resolution/10000",
        "id": "10000",
        "description": "Work has been completed on this issue.",
        "name": "Done"
      },
      "customfield_10107": null,
      "customfield_10108": null,
      "customfield_10109": null,
      "resolutiondate": "2024-05-31T15:18:22.446+0100",
      "workratio": -1,
      "lastViewed": "2024-05-31T15:18:22.419+0100",
      "watches": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-9/watchers",
        "watchCount": 1,
        "isWatching": true
      },
      "created": "2024-05-29T14:18:38.402+0100",
      "priority": {
        "self": "http://localhost:9090/rest/api/2/priority/3",
        "iconUrl": "http://localhost:9090/images/icons/priorities/medium.svg",
        "name": "Medium",
        "id": "3"
      },
      "customfield_10100": null,
      "customfield_10101": null,
      "customfield_10102": null,
      "labels": [],
      "customfield_10103": null,
      "timeestimate": null,
      "aggregatetimeoriginalestimate": null,
      "versions": [],
      "issuelinks": [],
      "assignee": null,
      "updated": "2024-05-31T15:18:22.450+0100",
      "status": {
        "self": "http://localhost:9090/rest/api/2/status/10001",
        "description": "",
        "iconUrl": "http://localhost:9090/",
        "name": "Done",
        "id": "10001",
        "statusCategory": {
          "self": "http://localhost:9090/rest/api/2/statuscategory/3",
          "id": 3,
          "key": "done",
          "colorName": "success",
          "name": "Done"
        }
      },
      "components": [],
      "timeoriginalestimate": null,
      "description": null,
      "timetracking": {},
      "archiveddate": null,
      "attachment": [],
      "aggregatetimeestimate": null,
      "summary": "As a developer, I'd like to update story status during the sprint >> Click the Active sprints link at the top right of the screen to go to the Active sprints where the current Sprint's items can be updated",
      "creator": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "subtasks": [],
      "reporter": {
        "self": "http://localhost:9090/rest/api/2/user?username=rjalander",
        "name": "rjalander",
        "key": "JIRAUSER10000",
        "emailAddress": "jalander.ramagiri@est.tech",
        "avatarUrls": {
          "48x48": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=48",
          "24x24": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=24",
          "16x16": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=16",
          "32x32": "https://www.gravatar.com/avatar/acc35d47cafd5f3edca6b0f6db7f3921?d=mm&s=32"
        },
        "displayName": "jalander.ramagiri@est.tech",
        "active": true,
        "timeZone": "Europe/Dublin"
      },
      "customfield_10000": "{summaryBean=com.atlassian.jira.plugin.devstatus.rest.SummaryBean@368b0950[summary={pullrequest=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@57d89d90[byInstanceType={},overall=PullRequestOverallBean{stateCount=0, state='OPEN', details=PullRequestOverallDetails{openCount=0, mergedCount=0, declinedCount=0}}], build=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@6fd95e24[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BuildOverallBean@7c7e6a52[failedBuildCount=0,successfulBuildCount=0,unknownBuildCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], review=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@47d13bf4[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.ReviewsOverallBean@76206dc3[dueDate=<null>,overDue=false,state=<null>,stateCount=0,count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], deployment-environment=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@532d355d[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.DeploymentOverallBean@5c8ee990[showProjects=false,successfulCount=0,topEnvironments=[],count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], repository=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@12ce676e[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.CommitOverallBean@67f54e81[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]], branch=com.atlassian.jira.plugin.devstatus.rest.SummaryItemBean@5d4808ff[byInstanceType={},overall=com.atlassian.jira.plugin.devstatus.summary.beans.BranchOverallBean@7621b8af[count=0,lastUpdated=<null>,lastUpdatedTimestamp=<null>]]},configErrors=[],errors=[]], devSummaryJson={\"cachedValue\":{\"errors\":[],\"configErrors\":[],\"summary\":{\"pullrequest\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":\"OPEN\",\"details\":{\"openCount\":0,\"mergedCount\":0,\"declinedCount\":0,\"total\":0},\"open\":true},\"byInstanceType\":{}},\"build\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"failedBuildCount\":0,\"successfulBuildCount\":0,\"unknownBuildCount\":0},\"byInstanceType\":{}},\"review\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"stateCount\":0,\"state\":null,\"dueDate\":null,\"overDue\":false,\"completed\":false},\"byInstanceType\":{}},\"deployment-environment\":{\"overall\":{\"count\":0,\"lastUpdated\":null,\"topEnvironments\":[],\"showProjects\":false,\"successfulCount\":0},\"byInstanceType\":{}},\"repository\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}},\"branch\":{\"overall\":{\"count\":0,\"lastUpdated\":null},\"byInstanceType\":{}}}},\"isStale\":false}}",
      "aggregateprogress": {
        "progress": 0,
        "total": 0
      },
      "environment": null,
      "duedate": null,
      "progress": {
        "progress": 0,
        "total": 0
      },
      "comment": {
        "comments": [],
        "maxResults": 0,
        "total": 0,
        "startAt": 0
      },
      "votes": {
        "self": "http://localhost:9090/rest/api/2/issue/ES-9/votes",
        "votes": 0,
        "hasVoted": false
      },
      "worklog": {
        "startAt": 0,
        "maxResults": 20,
        "total": 0,
        "worklogs": []
      },
      "archivedby": null
    }
  },
  "changelog": {
    "id": "10104",
    "items": [
      {
        "field": "resolution",
        "fieldtype": "jira",
        "from": null,
        "fromString": null,
        "to": "10000",
        "toString": "Done"
      },
      {
        "field": "status",
        "fieldtype": "jira",
        "from": "10000",
        "fromString": "To Do",
        "to": "10001",
        "toString": "Done"
      }
    ]
  }
}

```
</details>

Note:

CDEvents do not have corresponding mapping with Jira Project related, User related, Configuration and Software related events, this needs a discussion on how to handle these Jira events.
Various Jira event types can be found at https://developer.atlassian.com/server/jira/platform/webhooks/#configuring-a-webhook.


