## CDEvents Translator

### Overview:
This proposal describes translating events from various source control systems into CDEvents and sending them to configured message-broker, by using a common cdevents-translator 

A library cdevents-translator will be developed to receive various event types and convert them into CDEvents.

Various types of source code version control systems like GitHub, Gerrit and Gitlab endpoints/webhooks can be configured and implemented with in the cdevents-translator.

Instructions for configuring Gerrit webhooks and implementation details can be found in [gerrit-cdevent](gerrit-cdevents.md) 

### Design approach
Create a Golang application with an API server configured to initialize SCM systems webhooks/endpoints to receive events and translate them into CDEvents.

Example of initializing endpoints for Gerrit and GitHub in `cdevents-translator`, these endpoints needs to be configured in the respective SCM systems to receive events.

````go
POST("/gerrit-webhooks", gerrit.HandleTranslateGerritEvent)
POST("/github-webhooks", github.HandleTranslateGitHubEvent)
````

Methods will be implemented to handle translation of different types of SCM events received into CDEvents and send to configured message-broker

Go structs will be created for different types of events to Deserialize JSON data into a struct.
It can be a common struct If the event structure is common for all the events produced by SCM system.

For example the event structure is different for various events produced by Gerrit and an example struct of Gerrit project created event as below,
````go
type ProjectCreated struct {
	ProjectName    string  `json:"projectName"`
	HeadName       string  `json:"headName"`
	Type           string  `json:"type"`
	EventCreatedOn float64 `json:"eventCreatedOn"`
}
````
By passing this `ProjectCreated` struct as reference a corresponding CDEvent will be constructed

Note: A sample events creation for Gerrit Webhooks implemented as [PoC](https://github.com/rjalander/cdevents_translator/pull/1) 



