# Events
(*events()*)

## Overview

Event streaming and request inspection

### Available Operations

* [streamEvents](#streamevents) - Stream live events and notifications (SSE or WebSocket)
* [getRequestDetails](#getrequestdetails) - Get details and history of a specific request

## streamEvents

Stream live events and notifications (SSE or WebSocket)

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.StreamEventsResponse;
import org.openapis.openapi.models.operations.StreamEventsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        StreamEventsResponse res = sdk.events().streamEvents()
                .security(StreamEventsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.res().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                     | [org.openapis.openapi.models.operations.StreamEventsSecurity](../../models/operations/StreamEventsSecurity.md) | :heavy_check_mark:                                                                                             | The security requirements to use for the request.                                                              |

### Response

**[StreamEventsResponse](../../models/operations/StreamEventsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getRequestDetails

Get details and history of a specific request

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetRequestDetailsResponse;
import org.openapis.openapi.models.operations.GetRequestDetailsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetRequestDetailsResponse res = sdk.events().getRequestDetails()
                .security(GetRequestDetailsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .requestId("<id>")
                .call();

        if (res.requestDetails().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                               | [org.openapis.openapi.models.operations.GetRequestDetailsSecurity](../../models/operations/GetRequestDetailsSecurity.md) | :heavy_check_mark:                                                                                                       | The security requirements to use for the request.                                                                        |
| `requestId`                                                                                                              | *String*                                                                                                                 | :heavy_check_mark:                                                                                                       | Unique identifier of the request                                                                                         |

### Response

**[GetRequestDetailsResponse](../../models/operations/GetRequestDetailsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |