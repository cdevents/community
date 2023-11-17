## Gerrit-CDEvents Integration

### Design-Overview:
This design approach of integrating CDEvents with Gerrit is achieved by translating Gerrit events to CDEvents, making use of existing Gerrit Webhooks instead of implementing a new CDEvent producer for each source code control actions.

Gerrit sends events for each occurrence in real time for changes in source code, these events can be translated to CDEvents-Source Code Control Events by implementing a new event translator from Gerrit to CDEvents.


### Gerrit Webhooks configuration:

Gerrit Webhooks plugin allows to propagate all Gerrit events to remote http URL endpoints,
This Webhooks plugin can be created at the global/single project level.

Example Webhook configuration at `All-Projects` level, and this configuration will be inherited to all projects by default.

```curl
curl --user admin:password -H 'Content-Type: application/json' -X PUT -d '{"url" : "https://gerrit-translator-cdevents/gerrit-events","maxTries" : "3","sslVerify": "true"}' http://gerrit.est.tech/a/config/server/webhooks~projects/All-Projects/remotes/gerrit-events
```

The `webhooks.config` file will be created as below under `All-Projects/refs/meta/config`, once the above request is successful

```config
[remote "gerrit-events"]
  url = http://gerrit-translator-cdevents.est.tech/gerrit-events
  maxTries = 3
  sslVerify = true
```

More details on Gerrit plugin configuration and APIs can be found at [Webhooks-Documentation](https://gerrit.googlesource.com/plugins/webhooks/+/refs/heads/master/src/main/resources/Documentation)

### Gerrit-translator-CDEvents:

A new REST endpoint `/gerrit-events` will be implemented to receive all the Gerrit events and translate them to CDEvents.
The below list of [CDEvents-Source Code Control Events](https://github.com/cdevents/spec/blob/v0.3.0/source-code-version-control.md) will be mapped with corresponding Gerrit event types to translate.


| CDEvent Type  | Gerrit Event Type  | Comments / Gerrit Event Format   |
| :------------ |:-------------------|:----------------------------------|
| dev.cdevents.repository.created| project-create | {"projectName":"TestRepo3","headName":"refs/heads/master","type":"project-created","eventCreatedOn":1700131789} |
|  dev.cdevents.repository.modified   | project-head-updated    |   {"projectName":"TestRepo3","oldHead":"refs/heads/master","newHead":"refs/heads/main","type":"project-head-updated","eventCreatedOn":1700148011} |
| dev.cdevents.repository.deleted |   ref-updated   |  Hide the Project State under Gerrit Repository Options / {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"2d351d6d3bd1bec64f6b165a843c9dd18ac4d2cd","newRev":"5a2347177cdc707c6b42444c505b974d6499047d","refName":"refs/meta/config","project":"TestRepo3"},"type":"ref-updated","eventCreatedOn":1700221454} |
| dev.cdevents.branch.created   |  ref-updated     |   {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"0000000000000000000000000000000000000000","newRev":"0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6","refName":"refs/heads/test_branch","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700147670} |
| dev.cdevents.branch.deleted |   ref-updated    |    {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6","newRev":"0000000000000000000000000000000000000000","refName":"refs/heads/test_branch","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700222081} |
| dev.cdevents.change.created |    patchset-created     |     |
| dev.cdevents.change.reviewed |    comment-added     |     |
| dev.cdevents.change.merged |      change-merged   |     |
| dev.cdevents.change.abandoned |   change-abandoned      |     |
| dev.cdevents.change.updated |       |     |


Once mapped corresponding CDEvent will be created using CDEvents SDK(Java/Go) and send to configured `Events Broker URL`