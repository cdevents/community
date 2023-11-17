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
| dev.cdevents.repository.deleted |   ref-updated   |  Hide the Project State under Gerrit Repository Options / <br/>  {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"2d351d6d3bd1bec64f6b165a843c9dd18ac4d2cd","newRev":"5a2347177cdc707c6b42444c505b974d6499047d","refName":"refs/meta/config","project":"TestRepo3"},"type":"ref-updated","eventCreatedOn":1700221454} |
| dev.cdevents.branch.created   |  ref-updated     |   {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"0000000000000000000000000000000000000000","newRev":"0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6","refName":"refs/heads/test_branch","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700147670} |
| dev.cdevents.branch.deleted |   ref-updated    |    {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6","newRev":"0000000000000000000000000000000000000000","refName":"refs/heads/test_branch","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700222081} |
| dev.cdevents.change.created |    patchset-created     |  {"uploader":{"name":"Administrator","email":"admin@example.com","username":"admin"},"patchSet":{"number":2,"revision":"ba8c3584916c93b3e17a1ab63072b0ebd0d3ed84","parents":["0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6"],"ref":"refs/changes/01/1/2","uploader":{"name":"Administrator","email":"admin@example.com","username":"admin"},"createdOn":1700230164,"author":{"name":"Administrator","email":"admin@example.com","username":"admin"},"kind":"NO_CODE_CHANGE","sizeInsertions":9,"sizeDeletions":0},"change":{"project":"TestRepo","branch":"test_branch","id":"I55862204ef71f69bc88c79fe2259f7cb8365699a","number":1,"subject":"updates to the test branch 2 Change-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a","owner":{"name":"Administrator","email":"admin@example.com","username":"admin"},"url":"http://959be7129610/c/TestRepo/+/1","commitMessage":"updates to the test branch 2\nChange-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a\n","createdOn":1700229687,"status":"NEW"},"project":{"name":"TestRepo"},"refName":"refs/heads/test_branch","changeKey":{"key":"I55862204ef71f69bc88c79fe2259f7cb8365699a"},"type":"patchset-created","eventCreatedOn":1700230165} <br/><br/> Followed by ref-updated event </br> {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"0000000000000000000000000000000000000000","newRev":"83b1dc8216db96bd7c6c3aa859f626ceaf579b7b","refName":"refs/changes/01/1/meta","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700229688}  |
| dev.cdevents.change.reviewed |    comment-added     | {"author":{"name":"Administrator","email":"admin@example.com","username":"admin"},"approvals":[{"type":"Code-Review","description":"Code-Review","value":"2","oldValue":"1"}],"comment":"Patch Set 2: Code-Review+2","patchSet":{"number":2,"revision":"ba8c3584916c93b3e17a1ab63072b0ebd0d3ed84","parents":["0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6"],"ref":"refs/changes/01/1/2","uploader":{"name":"Administrator","email":"admin@example.com","username":"admin"},"createdOn":1700230164,"author":{"name":"Administrator","email":"admin@example.com","username":"admin"},"kind":"NO_CODE_CHANGE","sizeInsertions":9,"sizeDeletions":0},"change":{"project":"TestRepo","branch":"test_branch","id":"I55862204ef71f69bc88c79fe2259f7cb8365699a","number":1,"subject":"updates to the test branch 2 Change-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a","owner":{"name":"Administrator","email":"admin@example.com","username":"admin"},"url":"http://959be7129610/c/TestRepo/+/1","commitMessage":"updates to the test branch 2\nChange-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a\n","createdOn":1700229687,"status":"NEW"},"project":{"name":"TestRepo"},"refName":"refs/heads/test_branch","changeKey":{"key":"I55862204ef71f69bc88c79fe2259f7cb8365699a"},"type":"comment-added","eventCreatedOn":1700231622}  </br></br> Followed by ref-updated event </br> {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"552f864688cb7c660bb149cd4746f6e69882efcf","newRev":"ba876fbc1bbe1c3c1670163275bceca061eb98e8","refName":"refs/changes/01/1/meta","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700231622}  |
| dev.cdevents.change.merged |      change-merged   |   {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"newRev":"4c688da535ea3352536e3b320880aa353bd404b2","patchSet":{"number":2,"revision":"ba8c3584916c93b3e17a1ab63072b0ebd0d3ed84","parents":["0c8c548ca93b44dd501c000ebb79ecc8f9aa4bd6"],"ref":"refs/changes/01/1/2","uploader":{"name":"Administrator","email":"admin@example.com","username":"admin"},"createdOn":1700230164,"author":{"name":"Administrator","email":"admin@example.com","username":"admin"},"kind":"NO_CODE_CHANGE","sizeInsertions":9,"sizeDeletions":0},"change":{"project":"TestRepo","branch":"test_branch","id":"I55862204ef71f69bc88c79fe2259f7cb8365699a","number":1,"subject":"updates to the test branch 2 Change-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a","owner":{"name":"Administrator","email":"admin@example.com","username":"admin"},"url":"http://959be7129610/c/TestRepo/+/1","commitMessage":"updates to the test branch 2\nChange-Id: I55862204ef71f69bc88c79fe2259f7cb8365699a\n","createdOn":1700229687,"status":"MERGED"},"project":{"name":"TestRepo"},"refName":"refs/heads/test_branch","changeKey":{"key":"I55862204ef71f69bc88c79fe2259f7cb8365699a"},"type":"change-merged","eventCreatedOn":1700231698}  </br></br> Followed by ref-updated event </br> {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"ba876fbc1bbe1c3c1670163275bceca061eb98e8","newRev":"2ae17bf7464a6a4871d16d3d506df75476ea87e4","refName":"refs/changes/01/1/meta","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700231698} |
| dev.cdevents.change.abandoned |   change-abandoned      |  {"abandoner":{"name":"Administrator","email":"admin@example.com","username":"admin"},"reason":"change not needed","patchSet":{"number":1,"revision":"e88822ed72749d99e3b1d09fe73a1fdffc8e482c","parents":["ba8c3584916c93b3e17a1ab63072b0ebd0d3ed84"],"ref":"refs/changes/21/21/1","uploader":{"name":"Administrator","email":"admin@example.com","username":"admin"},"createdOn":1700236344,"author":{"name":"Administrator","email":"admin@example.com","username":"admin"},"kind":"REWORK","sizeInsertions":13,"sizeDeletions":1},"change":{"project":"TestRepo","branch":"test_branch","id":"Ifc7af9f849cbfb677ef6f1adcf05956292d4f571","number":21,"subject":"Revert \"updates to the test branch 2\"","owner":{"name":"Administrator","email":"admin@example.com","username":"admin"},"url":"http://959be7129610/c/TestRepo/+/21","commitMessage":"Revert \"updates to the test branch 2\"\n\nThis reverts commit ba8c3584916c93b3e17a1ab63072b0ebd0d3ed84.\n\nReason for revert: Testing abort\n\nChange-Id: Ifc7af9f849cbfb677ef6f1adcf05956292d4f571\n","createdOn":1700236344,"status":"ABANDONED"},"project":{"name":"TestRepo"},"refName":"refs/heads/test_branch","changeKey":{"key":"Ifc7af9f849cbfb677ef6f1adcf05956292d4f571"},"type":"change-abandoned","eventCreatedOn":1700236563}  </br></br> Followed by ref-updated event </br> {"submitter":{"name":"Administrator","email":"admin@example.com","username":"admin"},"refUpdate":{"oldRev":"c69dc799c251a0023e78382225a90f9f1e9cfbf5","newRev":"8e4477b221efd63f6c064aacb75395e7480174a3","refName":"refs/changes/21/21/meta","project":"TestRepo"},"type":"ref-updated","eventCreatedOn":1700236563}  |
| dev.cdevents.change.updated |   ref-updated    |     |
|  |       |     |

Once mapped the CDEvent will be created using CDEvents SDK(Java/Go) and send to the configured `Events Broker URL`

The Gerrit events that do not have corresponding CDEvents mapping as of today,
| Gerrit Event Type  |
|:-------------------|
|change-deleted|
|change-restored|
|dropped-output|
|hashtags-changed|
|batch-ref-updated|
|reviewer-added|
|reviewer-deleted|
|topic-changed|
|wip-state-changed|
|private-state-changed|
|vote-deleted|
