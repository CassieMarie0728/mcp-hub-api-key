# Prompts
(*prompts()*)

## Overview

Prompt listing and retrieval

### Available Operations

* [listPrompts](#listprompts) - List available prompts
* [getPromptById](#getpromptbyid) - Get details of a specific prompt

## listPrompts

Returns cached prompt metadata available through MCP connections.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListPromptsResponse;
import org.openapis.openapi.models.operations.ListPromptsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListPromptsResponse res = sdk.prompts().listPrompts()
                .security(ListPromptsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.prompts().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                   | [org.openapis.openapi.models.operations.ListPromptsSecurity](../../models/operations/ListPromptsSecurity.md) | :heavy_check_mark:                                                                                           | The security requirements to use for the request.                                                            |

### Response

**[ListPromptsResponse](../../models/operations/ListPromptsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getPromptById

Get details of a specific prompt

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetPromptByIdResponse;
import org.openapis.openapi.models.operations.GetPromptByIdSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetPromptByIdResponse res = sdk.prompts().getPromptById()
                .security(GetPromptByIdSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .promptId("<id>")
                .call();

        if (res.prompt().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                        | Type                                                                                                             | Required                                                                                                         | Description                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                       | [org.openapis.openapi.models.operations.GetPromptByIdSecurity](../../models/operations/GetPromptByIdSecurity.md) | :heavy_check_mark:                                                                                               | The security requirements to use for the request.                                                                |
| `promptId`                                                                                                       | *String*                                                                                                         | :heavy_check_mark:                                                                                               | Unique identifier of the prompt                                                                                  |

### Response

**[GetPromptByIdResponse](../../models/operations/GetPromptByIdResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |