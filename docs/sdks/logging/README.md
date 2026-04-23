# Logging
(*logging()*)

## Overview

Logging level management

### Available Operations

* [setLoggingLevel](#setlogginglevel) - Set logging level for MCP Hub runtime

## setLoggingLevel

Set logging level for MCP Hub runtime

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.Level;
import org.openapis.openapi.models.components.LoggingLevelBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.SetLoggingLevelResponse;
import org.openapis.openapi.models.operations.SetLoggingLevelSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        LoggingLevelBody req = LoggingLevelBody.builder()
                .level(Level.INFO)
                .build();

        SetLoggingLevelResponse res = sdk.logging().setLoggingLevel()
                .request(req)
                .security(SetLoggingLevelSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.inlineResponse2001().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                            | Type                                                                                                                 | Required                                                                                                             | Description                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                            | [LoggingLevelBody](../../models/shared/LoggingLevelBody.md)                                                          | :heavy_check_mark:                                                                                                   | The request object to use for the request.                                                                           |
| `security`                                                                                                           | [org.openapis.openapi.models.operations.SetLoggingLevelSecurity](../../models/operations/SetLoggingLevelSecurity.md) | :heavy_check_mark:                                                                                                   | The security requirements to use for the request.                                                                    |

### Response

**[SetLoggingLevelResponse](../../models/operations/SetLoggingLevelResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |