# Tools
(*tools()*)

## Overview

Access to related tools integrated within MCP Hub

### Available Operations

* [listTools](#listtools) - List available tools integrated within MCP Hub
* [getToolById](#gettoolbyid) - Get details of a specific tool

## listTools

Returns the hub-level tool catalog or cached tool registry.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListToolsResponse;
import org.openapis.openapi.models.operations.ListToolsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListToolsResponse res = sdk.tools().listTools()
                .security(ListToolsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.tools().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `security`                                                                                               | [org.openapis.openapi.models.operations.ListToolsSecurity](../../models/operations/ListToolsSecurity.md) | :heavy_check_mark:                                                                                       | The security requirements to use for the request.                                                        |

### Response

**[ListToolsResponse](../../models/operations/ListToolsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getToolById

Get details of a specific tool

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetToolByIdResponse;
import org.openapis.openapi.models.operations.GetToolByIdSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetToolByIdResponse res = sdk.tools().getToolById()
                .security(GetToolByIdSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .toolId("<id>")
                .call();

        if (res.tool().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                   | [org.openapis.openapi.models.operations.GetToolByIdSecurity](../../models/operations/GetToolByIdSecurity.md) | :heavy_check_mark:                                                                                           | The security requirements to use for the request.                                                            |
| `toolId`                                                                                                     | *String*                                                                                                     | :heavy_check_mark:                                                                                           | Unique identifier of the tool                                                                                |

### Response

**[GetToolByIdResponse](../../models/operations/GetToolByIdResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |