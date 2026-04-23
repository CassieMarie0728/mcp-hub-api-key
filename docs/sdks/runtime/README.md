# Runtime
(*runtime()*)

## Overview

Per-connection MCP runtime operations such as initialize, tool invocation, and cancellation

### Available Operations

* [initializeConnection](#initializeconnection) - Initialize an existing MCP connection
* [getConnectionCapabilities](#getconnectioncapabilities) - Get negotiated capabilities for a connection
* [listConnectionTools](#listconnectiontools) - List tools for a connection
* [callConnectionTool](#callconnectiontool) - Call a tool on a connection
* [listConnectionResources](#listconnectionresources) - List resources for a connection
* [readConnectionResource](#readconnectionresource) - Read a resource by URI on a connection
* [listConnectionPrompts](#listconnectionprompts) - List prompts for a connection
* [getConnectionPrompt](#getconnectionprompt) - Get a rendered prompt from a connection
* [cancelConnectionRequest](#cancelconnectionrequest) - Cancel an in-flight request on a connection

## initializeConnection

Performs MCP initialize and initialized lifecycle calls for a created connection.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.ConnectionInitializeBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.InitializeConnectionResponse;
import org.openapis.openapi.models.operations.InitializeConnectionSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        InitializeConnectionResponse res = sdk.runtime().initializeConnection()
                .security(InitializeConnectionSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .connectionInitializeBody(ConnectionInitializeBody.builder()
                    .clientName("MCP Hub")
                    .clientVersion("2.1.0")
                    .protocolVersion("2025-06-18")
                    .clientCapabilities(Map.ofEntries(
                        Map.entry("roots", Map.ofEntries(
                            Map.entry("listChanged", true))),
                        Map.entry("sampling", Map.ofEntries(
                        ))))
                    .build())
                .call();

        if (res.connectionInitializeResponse().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                                          | Type                                                                                                                                                               | Required                                                                                                                                                           | Description                                                                                                                                                        | Example                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                                                         | [org.openapis.openapi.models.operations.InitializeConnectionSecurity](../../models/operations/InitializeConnectionSecurity.md)                                     | :heavy_check_mark:                                                                                                                                                 | The security requirements to use for the request.                                                                                                                  |                                                                                                                                                                    |
| `connectionId`                                                                                                                                                     | *String*                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                 | Unique identifier of the connection.                                                                                                                               |                                                                                                                                                                    |
| `connectionInitializeBody`                                                                                                                                         | [ConnectionInitializeBody](../../models/components/ConnectionInitializeBody.md)                                                                                    | :heavy_check_mark:                                                                                                                                                 | N/A                                                                                                                                                                | {<br/>"clientName": "MCP Hub",<br/>"clientVersion": "2.1.0",<br/>"protocolVersion": "2025-06-18",<br/>"clientCapabilities": {<br/>"roots": {<br/>"listChanged": true<br/>},<br/>"sampling": {}<br/>}<br/>} |

### Response

**[InitializeConnectionResponse](../../models/operations/InitializeConnectionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getConnectionCapabilities

Returns the current server and client capability view for a single connection.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetConnectionCapabilitiesResponse;
import org.openapis.openapi.models.operations.GetConnectionCapabilitiesSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetConnectionCapabilitiesResponse res = sdk.runtime().getConnectionCapabilities()
                .security(GetConnectionCapabilitiesSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.capability().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                                | Type                                                                                                                                     | Required                                                                                                                                 | Description                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                               | [org.openapis.openapi.models.operations.GetConnectionCapabilitiesSecurity](../../models/operations/GetConnectionCapabilitiesSecurity.md) | :heavy_check_mark:                                                                                                                       | The security requirements to use for the request.                                                                                        |
| `connectionId`                                                                                                                           | *String*                                                                                                                                 | :heavy_check_mark:                                                                                                                       | Unique identifier of the connection.                                                                                                     |

### Response

**[GetConnectionCapabilitiesResponse](../../models/operations/GetConnectionCapabilitiesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## listConnectionTools

Fetches the live tool list exposed by the connected MCP server.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListConnectionToolsResponse;
import org.openapis.openapi.models.operations.ListConnectionToolsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListConnectionToolsResponse res = sdk.runtime().listConnectionTools()
                .security(ListConnectionToolsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.tools().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                   | [org.openapis.openapi.models.operations.ListConnectionToolsSecurity](../../models/operations/ListConnectionToolsSecurity.md) | :heavy_check_mark:                                                                                                           | The security requirements to use for the request.                                                                            |
| `connectionId`                                                                                                               | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Unique identifier of the connection.                                                                                         |

### Response

**[ListConnectionToolsResponse](../../models/operations/ListConnectionToolsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## callConnectionTool

Invokes a named MCP tool against the target connection.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.ToolCallBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.CallConnectionToolResponse;
import org.openapis.openapi.models.operations.CallConnectionToolSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        CallConnectionToolResponse res = sdk.runtime().callConnectionTool()
                .security(CallConnectionToolSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .toolName("<value>")
                .toolCallBody(ToolCallBody.builder()
                    .arguments(Map.ofEntries(
                        Map.entry("path", "/docs/readme.md")))
                    .requestId("req-tool-001")
                    .build())
                .call();

        if (res.toolCallResult().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                  | Type                                                                                                                       | Required                                                                                                                   | Description                                                                                                                | Example                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                 | [org.openapis.openapi.models.operations.CallConnectionToolSecurity](../../models/operations/CallConnectionToolSecurity.md) | :heavy_check_mark:                                                                                                         | The security requirements to use for the request.                                                                          |                                                                                                                            |
| `connectionId`                                                                                                             | *String*                                                                                                                   | :heavy_check_mark:                                                                                                         | Unique identifier of the connection.                                                                                       |                                                                                                                            |
| `toolName`                                                                                                                 | *String*                                                                                                                   | :heavy_check_mark:                                                                                                         | Name of the MCP tool to invoke.                                                                                            |                                                                                                                            |
| `toolCallBody`                                                                                                             | [ToolCallBody](../../models/components/ToolCallBody.md)                                                                    | :heavy_check_mark:                                                                                                         | N/A                                                                                                                        | {<br/>"arguments": {<br/>"path": "/docs/readme.md"<br/>},<br/>"requestId": "req-tool-001"<br/>}                            |

### Response

**[CallConnectionToolResponse](../../models/operations/CallConnectionToolResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## listConnectionResources

Fetches the live resource list from the connected MCP server.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListConnectionResourcesResponse;
import org.openapis.openapi.models.operations.ListConnectionResourcesSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListConnectionResourcesResponse res = sdk.runtime().listConnectionResources()
                .security(ListConnectionResourcesSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.resources().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                           | [org.openapis.openapi.models.operations.ListConnectionResourcesSecurity](../../models/operations/ListConnectionResourcesSecurity.md) | :heavy_check_mark:                                                                                                                   | The security requirements to use for the request.                                                                                    |
| `connectionId`                                                                                                                       | *String*                                                                                                                             | :heavy_check_mark:                                                                                                                   | Unique identifier of the connection.                                                                                                 |

### Response

**[ListConnectionResourcesResponse](../../models/operations/ListConnectionResourcesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## readConnectionResource

Reads a live resource from the MCP server using its resource URI.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.ResourceReadBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ReadConnectionResourceResponse;
import org.openapis.openapi.models.operations.ReadConnectionResourceSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ReadConnectionResourceResponse res = sdk.runtime().readConnectionResource()
                .security(ReadConnectionResourceSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .resourceReadBody(ResourceReadBody.builder()
                    .uri("file:///workspace/notes/todo.md")
                    .build())
                .call();

        if (res.resourceContent().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                          | Type                                                                                                                               | Required                                                                                                                           | Description                                                                                                                        | Example                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                         | [org.openapis.openapi.models.operations.ReadConnectionResourceSecurity](../../models/operations/ReadConnectionResourceSecurity.md) | :heavy_check_mark:                                                                                                                 | The security requirements to use for the request.                                                                                  |                                                                                                                                    |
| `connectionId`                                                                                                                     | *String*                                                                                                                           | :heavy_check_mark:                                                                                                                 | Unique identifier of the connection.                                                                                               |                                                                                                                                    |
| `resourceReadBody`                                                                                                                 | [ResourceReadBody](../../models/components/ResourceReadBody.md)                                                                    | :heavy_check_mark:                                                                                                                 | N/A                                                                                                                                | {<br/>"uri": "file:///workspace/notes/todo.md"<br/>}                                                                               |

### Response

**[ReadConnectionResourceResponse](../../models/operations/ReadConnectionResourceResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## listConnectionPrompts

Fetches prompt templates directly from the connected MCP server.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListConnectionPromptsResponse;
import org.openapis.openapi.models.operations.ListConnectionPromptsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListConnectionPromptsResponse res = sdk.runtime().listConnectionPrompts()
                .security(ListConnectionPromptsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.prompts().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                       | [org.openapis.openapi.models.operations.ListConnectionPromptsSecurity](../../models/operations/ListConnectionPromptsSecurity.md) | :heavy_check_mark:                                                                                                               | The security requirements to use for the request.                                                                                |
| `connectionId`                                                                                                                   | *String*                                                                                                                         | :heavy_check_mark:                                                                                                               | Unique identifier of the connection.                                                                                             |

### Response

**[ListConnectionPromptsResponse](../../models/operations/ListConnectionPromptsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getConnectionPrompt

Retrieves a prompt template and applies optional prompt arguments.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.PromptGetBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetConnectionPromptResponse;
import org.openapis.openapi.models.operations.GetConnectionPromptSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetConnectionPromptResponse res = sdk.runtime().getConnectionPrompt()
                .security(GetConnectionPromptSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .promptName("<value>")
                .promptGetBody(PromptGetBody.builder()
                    .arguments(Map.ofEntries(
                        Map.entry("targetLanguage", "fr")))
                    .build())
                .call();

        if (res.prompt().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  | Example                                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                   | [org.openapis.openapi.models.operations.GetConnectionPromptSecurity](../../models/operations/GetConnectionPromptSecurity.md) | :heavy_check_mark:                                                                                                           | The security requirements to use for the request.                                                                            |                                                                                                                              |
| `connectionId`                                                                                                               | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Unique identifier of the connection.                                                                                         |                                                                                                                              |
| `promptName`                                                                                                                 | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Name of the prompt template.                                                                                                 |                                                                                                                              |
| `promptGetBody`                                                                                                              | [Optional\<PromptGetBody>](../../models/components/PromptGetBody.md)                                                         | :heavy_minus_sign:                                                                                                           | N/A                                                                                                                          | {<br/>"arguments": {<br/>"targetLanguage": "fr"<br/>}<br/>}                                                                  |

### Response

**[GetConnectionPromptResponse](../../models/operations/GetConnectionPromptResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## cancelConnectionRequest

Requests cancellation for an active MCP request.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.CancelRequestBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.CancelConnectionRequestResponse;
import org.openapis.openapi.models.operations.CancelConnectionRequestSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        CancelConnectionRequestResponse res = sdk.runtime().cancelConnectionRequest()
                .security(CancelConnectionRequestSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .cancelRequestBody(CancelRequestBody.builder()
                    .requestId("req-123abc")
                    .reason("User navigated away")
                    .build())
                .call();

        if (res.inlineResponse202().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          | Example                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                           | [org.openapis.openapi.models.operations.CancelConnectionRequestSecurity](../../models/operations/CancelConnectionRequestSecurity.md) | :heavy_check_mark:                                                                                                                   | The security requirements to use for the request.                                                                                    |                                                                                                                                      |
| `connectionId`                                                                                                                       | *String*                                                                                                                             | :heavy_check_mark:                                                                                                                   | Unique identifier of the connection.                                                                                                 |                                                                                                                                      |
| `cancelRequestBody`                                                                                                                  | [CancelRequestBody](../../models/components/CancelRequestBody.md)                                                                    | :heavy_check_mark:                                                                                                                   | N/A                                                                                                                                  | {<br/>"requestId": "req-123abc",<br/>"reason": "User navigated away"<br/>}                                                           |

### Response

**[CancelConnectionRequestResponse](../../models/operations/CancelConnectionRequestResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |