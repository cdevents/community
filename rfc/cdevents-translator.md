## CDEvents Translator

### Overview:
This design describes the approaches to translate events from various source control systems into CDEvents and sending them to configured message-broker, by using a common cdevents-translator.

A library cdevents-translator will have an interface that can be implemented for various SCM systems like GitHub, Gerrit and Gitlab to translate events into CDEvents format.

Different SCM systems or applications that are exposing events with endpoints/webhooks can be configured and mapped with the corresponding CDEvent.

For Example configuring Gerrit webhooks and mapping with CDEvents can be found in [gerrit-cdevent](gerrit-cdevents.md) 

### Goals and Non-Goals
Goals:
- Create shared packages/interfaces that will be used as common in translating/sending CDEvents
- Using `cdevents-translator` library to implement Gerrit translator initially

Non-Goals:
- Implement translators for other SCM tools or any application that needs a translation to CDEvents


### Design
Based on the initial design discussion we have come up with 3 different approaches to create `cdevents-translator` library, each one has it's own pros/cons to pick the best suitable approach.

### Approach 1 : Creating a Web Service with Libraries/Packages for different translators
A Golang main application "cdevents-translator" will be created to expose the translation functionality as a web service with HTTP/REST API server.</br>
SCM system's webhooks/endpoints are registered to handle the translation of the events into CDEvents.</br>
An interface `EventTranslator` will be created to handle `TranslateEvent` and this needs to be implemented by different translators.

- Example structure of cdevents-translator application
````go
package main

type EventTranslator interface {
	TranslateEvent()
}

func main() {
  
   // Register translators in the main application
   http.HandleFunc("/translate/gerrit-webhooks", gerrittranslator.TranslateEvent)
   http.HandleFunc("/translate/github-webhooks", githubtranslator.TranslateEvent)

   // Start the main application's HTTP server on port 8080
   http.ListenAndServe(":8080", nil)
}
````
#### Create a Library/Package gerrit-translator-cdevents
Library with the name "gerrit-translator-cdevents" will be created in a separate package/repo.</br>
Declare a struct to hold fields related to translation of Gerrit event.</br>
Implement "TranslateEvent" to translate Gerrit event to CDEvent.

- Example structure of gerrit-translator-cdevents library
````go
package gerrittranslator


type GerritTranslator struct {
   //Fields for Gerrit event Translator
}

func (translator *GerritTranslator) TranslateEvent(req *http.Request) (CDEvent, error) {
	//handle translate Gerrit event to CDEvent
}
````

#### Pros and Cons
This structure can be extended by adding more translator libraries in the future without modifying the main application code.</br>
The problem with this approach anyone who is wanting some custom set of translator would need to write their own main class.

### Approach 2 : Creating a Go's plugin system to implement different Translators
Plugins are Go interface implementations that can be compiled and loaded during the runtime of a Go program using Go's [plugin](https://pkg.go.dev/plugin) package

#### Create a shared interface cdevents-translator
Define an interface "EventTranslator" that represents the common functionality to "TranslateEvent" and expected to implement from all translator plugins.

- Example structure of cdevents-translator interface
````go
package cdeventstranslator

type EventTranslator interface {
	TranslateEvent()
}
````

#### Implement gerrit-translator-cdevents plugin
Plugin with the name `gerrit-translator-cdevents` will be created in a separate repo.</br>
GerritTranslator needs to implement the cdeventstranslator.EventTranslator interface to handle the translation from Gerrit event to CDEvent.</br>
Build the `gerrit-translator-cdevents` plugin as shared object using `go build -buildmode=plugin`, so that the plugin can be loaded/used from other Golang main application to `TranslateEvent` using Go's [plugin](https://pkg.go.dev/plugin) package.

- Example structure of gerrit-translator-cdevents plugin
````go
package main


type GerritTranslator struct {
   //Fields for Gerrit event Translator
}

func (translator *GerritTranslator) TranslateEvent(event string) {
	//handle translate Gerrit event to CDEvent
}

func main() {
	// Create an instance of the GerritTranslator
	translator := &GerritTranslator{}
  
}
````

#### Pros and Cons

This structure can be extended by adding more translator plugins in the future without having to recompile the entire application.</br>
But the Go plugin system is currently only supported on Unix-like systems and has some limitations, such as the need to compile everything with the same Go version.</br>
Expose the functionality of Go translator plugins as an HTTP/REST API, if this needs be used from other languages.


### Approach 3 : Creating Go Plugin System over RPC(gRPC) using HashiCorp's go-plugin
 
HashiCorp's [`go-plugin`](https://github.com/hashicorp/go-plugin) library simplifies the implementation of a plugin system in Go, it is a Go (golang) plugin system over RPC created by HashiCorp.</br>
gRPC is a high-performance RPC (Remote Procedure Call) framework developed by Google.

gRPC-based plugins with HashiCorp's go-plugin library will help to enable communication between the main Go application (the server) and different translator plugins (the clients) using the gRPC framework.

As per the HashiCorp's `go-plugin` library [usage documentation](https://github.com/hashicorp/go-plugin/tree/main?tab=readme-ov-file#usage) the translator services can be implemented as below,

#### Create a shared interface cdevents-translator
Define an interface "EventTranslator" that represents the common functionality to "TranslateEvent" and will be exposed for plugins to implement.</br>
Different translator plugins can be implemented that communicates over a gRPC connection.

- Example structure of cdevents-translator interface
````go
package cdeventstranslator

type EventTranslator interface {
	TranslateEvent()
}
````

#### Implement gerrit-translator-cdevents plugin
Plugin with the name `gerrit-translator-cdevents` will be created in a separate repo/package.</br>
GerritTranslator needs to implement the cdeventstranslator.EventTranslator interface to handle the translation from Gerrit event to CDEvent and that communicates over a gRPC connection.</br>
Call `plugin.Serve` to serve a plugin from the main function to GRPC server using hashicorp's go-plugin

Build the `gerrit-translator-cdevents` plugin using `go build`, so that the plugin can be loaded/used from other Golang main application to `TranslateEvent`

- Example structure of gerrit-translator-cdevents plugin:
````go
package main


type GerritTranslator struct {
   //Fields for Gerrit event Translator
}

func (translator *GerritTranslator) TranslateEvent(event string) {
	//handle translate Gerrit event to CDEvent
}

func main() {
	//using hashicorp's plugin
	plugin.Serve(&plugin.ServeConfig{
		.....

		GRPCServer: plugin.DefaultGRPCServer,
	})
  
}
````
#### GRPC client and server implementations using protocol buffers
Creating GRPC Client and Server implementations is a common template that can be generated 
by using `protoc-gen-go-grpc` plugin from the below [protocol buffers](https://protobuf.dev/getting-started/gotutorial/) (.proto) file.

- Example structure of cdevents-translator proto file
````proto
// cdevents_translator.proto

syntax = "proto3";
package proto;
option go_package = "./proto";

message TranslateRequest {
  string text = 1;
}

message TranslateResponse {
  string result = 1;
}

message Empty {}

service EventTranslator {
  rpc TranslateEvent (TranslateRequest) returns (TranslateResponse);
}
````

The GRPC client/server will help to handle EventTranslator request/response over GRPC by using the proto generated files.

````go
package cdeventstranslator

type GRPCClient struct {
   //init client
}

func (m *GRPCClient) TranslateEvent(event string) error {
	_, err := m.client.TranslateEvent(context.Background(), &proto.TranslateRequest{Event: event})
	return err
}

type GRPCServer struct {
	//init server
}

func (m *GRPCServer) TranslateEvent(ctx context.Context, req *proto.TranslateRequest) (*proto.Empty, error) {
	return &proto.Empty{}, m.Impl.TranslateEvent(req.Event)
}

````

The GRPC client/server implementations can be [generated in other languages](https://protobuf.dev/getting-started/), to enable Cross-language support for Plugins implemented.</br>
Plugin users use `plugin.Client` to launch a subprocess and request an interface implementation using hashicorp's go-plugin over RPC.
More detailed implementation cab be referred from HashiCorp's go-plugin [gRPC examples](https://github.com/hashicorp/go-plugin/tree/main/examples/grpc) 

### Known Unknowns
- Creating CDEvents from other type of events and sending them to configured Message-broker can be implemented in a shared package.