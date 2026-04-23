# ConnectionAuth
(*connectionAuth()*)

## Overview

Per-connection authentication bootstrap and status

### Available Operations

* [getConnectionAuthStatus](#getconnectionauthstatus) - Get auth status for a connection
* [startConnectionAuth](#startconnectionauth) - Start auth flow for a connection

## getConnectionAuthStatus

Returns whether the remote MCP server connection is authenticated and what auth type is active.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetConnectionAuthStatusResponse;
import org.openapis.openapi.models.operations.GetConnectionAuthStatusSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetConnectionAuthStatusResponse res = sdk.connectionAuth().getConnectionAuthStatus()
                .security(GetConnectionAuthStatusSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.authStatus().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                           | [org.openapis.openapi.models.operations.GetConnectionAuthStatusSecurity](../../models/operations/GetConnectionAuthStatusSecurity.md) | :heavy_check_mark:                                                                                                                   | The security requirements to use for the request.                                                                                    |
| `connectionId`                                                                                                                       | *String*                                                                                                                             | :heavy_check_mark:                                                                                                                   | Unique identifier of the connection.                                                                                                 |

### Response

**[GetConnectionAuthStatusResponse](../../models/operations/GetConnectionAuthStatusResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## startConnectionAuth

Bootstraps remote authentication for MCP servers that require browser or token-based authorization.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.AuthStartBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.StartConnectionAuthResponse;
import org.openapis.openapi.models.operations.StartConnectionAuthSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        StartConnectionAuthResponse res = sdk.connectionAuth().startConnectionAuth()
                .security(StartConnectionAuthSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .authStartBody(AuthStartBody.builder()
                    .callbackUrl("https://app.example.com/mcp/auth/callback")
                    .scopes(List.of(
                        "tools:read",
                        "resources:read"))
                    .build())
                .call();

        if (res.authStartResponse().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  | Example                                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                   | [org.openapis.openapi.models.operations.StartConnectionAuthSecurity](../../models/operations/StartConnectionAuthSecurity.md) | :heavy_check_mark:                                                                                                           | The security requirements to use for the request.                                                                            |                                                                                                                              |
| `connectionId`                                                                                                               | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Unique identifier of the connection.                                                                                         |                                                                                                                              |
| `authStartBody`                                                                                                              | [Optional\<AuthStartBody>](../../models/components/AuthStartBody.md)                                                         | :heavy_minus_sign:                                                                                                           | N/A                                                                                                                          | {<br/>"callbackUrl": "https://app.example.com/mcp/auth/callback",<br/>"scopes": [<br/>"tools:read",<br/>"resources:read"<br/>]<br/>} |

### Response

**[StartConnectionAuthResponse](../../models/operations/StartConnectionAuthResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 404              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |