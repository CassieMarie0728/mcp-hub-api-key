# Completions
(*completions()*)

## Overview

Completion requests

### Available Operations

* [postCompletion](#postcompletion) - Request a completion from an MCP server

## postCompletion

Request a completion from an MCP server

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.CompletionsBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PostCompletionResponse;
import org.openapis.openapi.models.operations.PostCompletionSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        CompletionsBody req = CompletionsBody.builder()
                .serverId("server-123")
                .contextId("context-456")
                .modelId("model-789")
                .prompt("Translate the following text to French:")
                .parameters(Map.ofEntries(
                    Map.entry("maxTokens", 100L)))
                .build();

        PostCompletionResponse res = sdk.completions().postCompletion()
                .request(req)
                .security(PostCompletionSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.inlineResponse2007().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                          | [CompletionsBody](../../models/shared/CompletionsBody.md)                                                          | :heavy_check_mark:                                                                                                 | The request object to use for the request.                                                                         |
| `security`                                                                                                         | [org.openapis.openapi.models.operations.PostCompletionSecurity](../../models/operations/PostCompletionSecurity.md) | :heavy_check_mark:                                                                                                 | The security requirements to use for the request.                                                                  |

### Response

**[PostCompletionResponse](../../models/operations/PostCompletionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |