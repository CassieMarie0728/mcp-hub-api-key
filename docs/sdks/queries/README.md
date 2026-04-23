# Queries
(*queries()*)

## Overview

Sending queries and commands to MCP servers

### Available Operations

* [postQuery](#postquery) - Send a query or command to an MCP server

## postQuery

Send a query or command to an MCP server

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.Map;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.QueriesBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PostQueryResponse;
import org.openapis.openapi.models.operations.PostQuerySecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        QueriesBody req = QueriesBody.builder()
                .serverId("server-123")
                .contextId("context-456")
                .modelId("model-789")
                .query("SELECT * FROM users WHERE active = true")
                .parameters(Map.ofEntries(
                    Map.entry("limit", 10L)))
                .build();

        PostQueryResponse res = sdk.queries().postQuery()
                .request(req)
                .security(PostQuerySecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.inlineResponse2008().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                | [QueriesBody](../../models/shared/QueriesBody.md)                                                        | :heavy_check_mark:                                                                                       | The request object to use for the request.                                                               |
| `security`                                                                                               | [org.openapis.openapi.models.operations.PostQuerySecurity](../../models/operations/PostQuerySecurity.md) | :heavy_check_mark:                                                                                       | The security requirements to use for the request.                                                        |

### Response

**[PostQueryResponse](../../models/operations/PostQueryResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |