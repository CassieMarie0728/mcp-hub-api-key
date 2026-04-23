# System
(*system()*)

## Overview

System related endpoints

### Available Operations

* [getSystemHealth](#getsystemhealth) - Health check endpoint
* [postNotifyOwner](#postnotifyowner) - Notify owner (admin only)

## getSystemHealth

Health check endpoint

### Example Usage

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

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `timestamp`                                               | *double*                                                  | :heavy_check_mark:                                        | Timestamp for health check, must be a non-negative number |

### Response

**[GetSystemHealthResponse](../../models/operations/GetSystemHealthResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## postNotifyOwner

Notify owner (admin only)

### Example Usage

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
| `request`                                                                                                            | [SystemNotifyOwnerBody](../../models/shared/SystemNotifyOwnerBody.md)                                                | :heavy_check_mark:                                                                                                   | The request object to use for the request.                                                                           |
| `security`                                                                                                           | [org.openapis.openapi.models.operations.PostNotifyOwnerSecurity](../../models/operations/PostNotifyOwnerSecurity.md) | :heavy_check_mark:                                                                                                   | The security requirements to use for the request.                                                                    |

### Response

**[PostNotifyOwnerResponse](../../models/operations/PostNotifyOwnerResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 403              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |