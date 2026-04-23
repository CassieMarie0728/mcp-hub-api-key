# mcp-hub-api-java

Developer-friendly, idiomatic Java SDK for the *mcp-hub-api-java* API.

<div align="left">
    <a href="https://www.scalar.com/?utm_source=mcp-hub-api-java&utm_campaign=java"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20scalar+speakeasy-212015?style=for-the-badge&logo=scalar&labelColor=252525" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>

<br />

## Summary

MCP Hub API: MCP Hub API provides a unified wrapper for discovering MCP servers, creating and managing connections, inspecting capabilities, invoking tools, reading resources, retrieving prompts, streaming events, and handling user/session authentication.

This contract is designed for both browser-based app sessions and programmatic clients, with support for cookie-based sessions and bearer-token authentication.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [cassie-marie-mcp-hub-api-java](#cassie-marie-mcp-hub-api-java)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

### Getting started

JDK 11 or later is required.

The samples below show how a published SDK artifact is used:

Gradle:
```groovy
implementation 'org.cassie-marie:mcp-hub-api-java:2.0.0'
```

Maven:
```xml
<dependency>
    <groupId>org.cassie-marie</groupId>
    <artifactId>mcp-hub-api-java</artifactId>
    <version>2.0.0</version>
</dependency>
```

### How to build
After cloning the git repository to your file system you can build the SDK artifact from source to the `build` directory by running `./gradlew build` on *nix systems or `gradlew.bat` on Windows systems.

If you wish to build from source and publish the SDK artifact to your local Maven repository (on your filesystem) then use the following command (after cloning the git repo locally):

On *nix:
```bash
./gradlew publishToMavenLocal -Pskip.signing
```
On Windows:
```bash
gradlew.bat publishToMavenLocal -Pskip.signing
```

### Logging
A logging framework/facade has not yet been adopted but is under consideration.

For request and response logging (especially json bodies) use:
```java
SpeakeasyHTTPClient.setDebugLogging(true); // experimental API only (may change without warning)
```
Example output:
```
Sending request: http://localhost:35123/bearer#global GET
Request headers: {Accept=[application/json], Authorization=[******], Client-Level-Header=[added by client], Idempotency-Key=[some-key], x-speakeasy-user-agent=[speakeasy-sdk/java 0.0.1 internal 0.1.0 org.openapis.openapi]}
Received response: (GET http://localhost:35123/bearer#global) 200
Response headers: {access-control-allow-credentials=[true], access-control-allow-origin=[*], connection=[keep-alive], content-length=[50], content-type=[application/json], date=[Wed, 09 Apr 2025 01:43:29 GMT], server=[gunicorn/19.9.0]}
Response body:
{
  "authenticated": true, 
  "token": "global"
}
```
WARNING: This should only used for temporary debugging purposes. Leaving this option on in a production system could expose credentials/secrets in logs. <i>Authorization</i> headers are redacted by default and there is the ability to specify redacted header names via `SpeakeasyHTTPClient.setRedactedHeaders`.

Another option is to set the System property `-Djdk.httpclient.HttpClient.log=all`. However, this second option does not log bodies.
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name               | Type   | Scheme  |
| ------------------ | ------ | ------- |
| `appSessionCookie` | apiKey | API key |

To authenticate with the API the `appSessionCookie` parameter must be set when initializing the SDK client instance. For example:
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
                .appSessionCookie("<YOUR_API_KEY_HERE>")
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```

### Per-Operation Security Schemes

Some operations in this SDK require the security scheme to be specified at the request level. For example:
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.SystemNotifyOwnerBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PostNotifyOwnerResponse;
import org.openapis.openapi.models.operations.PostNotifyOwnerSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        SystemNotifyOwnerBody req = SystemNotifyOwnerBody.builder()
                .title("System Alert")
                .content("An important event has occurred.")
                .build();

        PostNotifyOwnerResponse res = sdk.system().postNotifyOwner()
                .request(req)
                .security(PostNotifyOwnerSecurity.builder()

                    .build())
                .call();

        if (res.inlineResponse2001().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [auth()](docs/sdks/auth/README.md)

* [postLogin](docs/sdks/auth/README.md#postlogin) - User login with username and password
* [getCurrentUser](docs/sdks/auth/README.md#getcurrentuser) - Get current authenticated user
* [postLogout](docs/sdks/auth/README.md#postlogout) - Logout user and clear session cookie

### [capabilities()](docs/sdks/capabilities/README.md)

* [listCapabilities](docs/sdks/capabilities/README.md#listcapabilities) - List capabilities of connected MCP servers

### [completions()](docs/sdks/completions/README.md)

* [postCompletion](docs/sdks/completions/README.md#postcompletion) - Request a completion from an MCP server

### [connectionAuth()](docs/sdks/connectionauth/README.md)

* [getConnectionAuthStatus](docs/sdks/connectionauth/README.md#getconnectionauthstatus) - Get auth status for a connection
* [startConnectionAuth](docs/sdks/connectionauth/README.md#startconnectionauth) - Start auth flow for a connection

### [connections()](docs/sdks/connections/README.md)

* [listConnections](docs/sdks/connections/README.md#listconnections) - List all MCP connections for the authenticated user
* [createConnection](docs/sdks/connections/README.md#createconnection) - Create and initialize a new MCP connection
* [getConnectionById](docs/sdks/connections/README.md#getconnectionbyid) - Get details and status of a specific MCP connection
* [deleteConnection](docs/sdks/connections/README.md#deleteconnection) - Disconnect and remove an MCP connection
* [pingConnection](docs/sdks/connections/README.md#pingconnection) - Send a ping to the MCP server via the connection

### [contexts()](docs/sdks/contexts/README.md)

* [listContexts](docs/sdks/contexts/README.md#listcontexts) - List available contexts from connected MCP servers
* [getContextById](docs/sdks/contexts/README.md#getcontextbyid) - Get details of a specific context
* [listModelsInContext](docs/sdks/contexts/README.md#listmodelsincontext) - List models available in a specific context

### [events()](docs/sdks/events/README.md)

* [streamEvents](docs/sdks/events/README.md#streamevents) - Stream live events and notifications (SSE or WebSocket)
* [getRequestDetails](docs/sdks/events/README.md#getrequestdetails) - Get details and history of a specific request

### [logging()](docs/sdks/logging/README.md)

* [setLoggingLevel](docs/sdks/logging/README.md#setlogginglevel) - Set logging level for MCP Hub runtime


### [prompts()](docs/sdks/prompts/README.md)

* [listPrompts](docs/sdks/prompts/README.md#listprompts) - List available prompts
* [getPromptById](docs/sdks/prompts/README.md#getpromptbyid) - Get details of a specific prompt

### [queries()](docs/sdks/queries/README.md)

* [postQuery](docs/sdks/queries/README.md#postquery) - Send a query or command to an MCP server

### [resources()](docs/sdks/resources/README.md)

* [listResources](docs/sdks/resources/README.md#listresources) - List resources available from MCP servers
* [readResource](docs/sdks/resources/README.md#readresource) - Read a specific resource
* [listResourceTemplates](docs/sdks/resources/README.md#listresourcetemplates) - List resource templates
* [subscribeResource](docs/sdks/resources/README.md#subscriberesource) - Subscribe to resource updates
* [unsubscribeResource](docs/sdks/resources/README.md#unsubscriberesource) - Unsubscribe from resource updates

### [runtime()](docs/sdks/runtime/README.md)

* [initializeConnection](docs/sdks/runtime/README.md#initializeconnection) - Initialize an existing MCP connection
* [getConnectionCapabilities](docs/sdks/runtime/README.md#getconnectioncapabilities) - Get negotiated capabilities for a connection
* [listConnectionTools](docs/sdks/runtime/README.md#listconnectiontools) - List tools for a connection
* [callConnectionTool](docs/sdks/runtime/README.md#callconnectiontool) - Call a tool on a connection
* [listConnectionResources](docs/sdks/runtime/README.md#listconnectionresources) - List resources for a connection
* [readConnectionResource](docs/sdks/runtime/README.md#readconnectionresource) - Read a resource by URI on a connection
* [listConnectionPrompts](docs/sdks/runtime/README.md#listconnectionprompts) - List prompts for a connection
* [getConnectionPrompt](docs/sdks/runtime/README.md#getconnectionprompt) - Get a rendered prompt from a connection
* [cancelConnectionRequest](docs/sdks/runtime/README.md#cancelconnectionrequest) - Cancel an in-flight request on a connection

### [servers()](docs/sdks/servers/README.md)

* [listMcpServers](docs/sdks/servers/README.md#listmcpservers) - List available MCP servers
* [registerMcpServer](docs/sdks/servers/README.md#registermcpserver) - Register a new MCP server (admin only)
* [getMcpServerById](docs/sdks/servers/README.md#getmcpserverbyid) - Get details of a specific MCP server

### [system()](docs/sdks/system/README.md)

* [getSystemHealth](docs/sdks/system/README.md#getsystemhealth) - Health check endpoint
* [postNotifyOwner](docs/sdks/system/README.md#postnotifyowner) - Notify owner (admin only)

### [tools()](docs/sdks/tools/README.md)

* [listTools](docs/sdks/tools/README.md#listtools) - List available tools integrated within MCP Hub
* [getToolById](docs/sdks/tools/README.md#gettoolbyid) - Get details of a specific tool

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or raise an exception.

By default, an API error will throw a `models/errors/APIException` exception. When custom error responses are specified for an operation, the SDK may also throw their associated exception. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `getSystemHealth` method throws the following exceptions:

| Error Type                 | Status Code | Content Type     |
| -------------------------- | ----------- | ---------------- |
| models/errors/Error        | 400         | application/json |
| models/errors/APIException | 4XX, 5XX    | \*/\*            |

### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally using the `.serverIndex(int serverIdx)` builder method when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                                                                     | Description                          |
| --- | -------------------------------------------------------------------------- | ------------------------------------ |
| 0   | `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0` | SwaggerHub API Auto Mocking          |
| 1   | `/api/`                                                                    | Base path prefix for all API routes. |

#### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
                .serverIndex(1)
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```

### Override Server URL Per-Client

The default server can also be overridden globally using the `.serverURL(String serverUrl)` builder method when initializing the SDK client instance. For example:
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
                .serverURL("https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0")
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Server Selection [server] -->

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release.

### SDK Created by [Scalar](https://www.scalar.com/?utm_source=mcp-hub-api-java&utm_campaign=java)