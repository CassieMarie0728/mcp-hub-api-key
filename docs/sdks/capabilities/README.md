# Capabilities
(*capabilities()*)

## Overview

Capability and server metadata inspection

### Available Operations

* [listCapabilities](#listcapabilities) - List capabilities of connected MCP servers

## listCapabilities

Returns a summarized view of negotiated capabilities across active connections.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListCapabilitiesResponse;
import org.openapis.openapi.models.operations.ListCapabilitiesSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListCapabilitiesResponse res = sdk.capabilities().listCapabilities()
                .security(ListCapabilitiesSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.capabilities().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                              | Type                                                                                                                   | Required                                                                                                               | Description                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                             | [org.openapis.openapi.models.operations.ListCapabilitiesSecurity](../../models/operations/ListCapabilitiesSecurity.md) | :heavy_check_mark:                                                                                                     | The security requirements to use for the request.                                                                      |

### Response

**[ListCapabilitiesResponse](../../models/operations/ListCapabilitiesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |