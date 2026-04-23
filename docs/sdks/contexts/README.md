# Contexts
(*contexts()*)

## Overview

MCP server contexts and models management

### Available Operations

* [listContexts](#listcontexts) - List available contexts from connected MCP servers
* [getContextById](#getcontextbyid) - Get details of a specific context
* [listModelsInContext](#listmodelsincontext) - List models available in a specific context

## listContexts

List available contexts from connected MCP servers

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListContextsResponse;
import org.openapis.openapi.models.operations.ListContextsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListContextsResponse res = sdk.contexts().listContexts()
                .security(ListContextsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.contexts().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                     | [org.openapis.openapi.models.operations.ListContextsSecurity](../../models/operations/ListContextsSecurity.md) | :heavy_check_mark:                                                                                             | The security requirements to use for the request.                                                              |
| `serverId`                                                                                                     | *Optional\<String>*                                                                                            | :heavy_minus_sign:                                                                                             | Filter contexts by MCP server ID                                                                               |

### Response

**[ListContextsResponse](../../models/operations/ListContextsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getContextById

Get details of a specific context

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetContextByIdResponse;
import org.openapis.openapi.models.operations.GetContextByIdSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetContextByIdResponse res = sdk.contexts().getContextById()
                .security(GetContextByIdSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .contextId("<id>")
                .call();

        if (res.context().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                         | [org.openapis.openapi.models.operations.GetContextByIdSecurity](../../models/operations/GetContextByIdSecurity.md) | :heavy_check_mark:                                                                                                 | The security requirements to use for the request.                                                                  |
| `contextId`                                                                                                        | *String*                                                                                                           | :heavy_check_mark:                                                                                                 | Unique identifier of the context                                                                                   |

### Response

**[GetContextByIdResponse](../../models/operations/GetContextByIdResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## listModelsInContext

List models available in a specific context

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListModelsInContextResponse;
import org.openapis.openapi.models.operations.ListModelsInContextSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListModelsInContextResponse res = sdk.contexts().listModelsInContext()
                .security(ListModelsInContextSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .contextId("<id>")
                .call();

        if (res.models().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                   | [org.openapis.openapi.models.operations.ListModelsInContextSecurity](../../models/operations/ListModelsInContextSecurity.md) | :heavy_check_mark:                                                                                                           | The security requirements to use for the request.                                                                            |
| `contextId`                                                                                                                  | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Unique identifier of the context                                                                                             |

### Response

**[ListModelsInContextResponse](../../models/operations/ListModelsInContextResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |