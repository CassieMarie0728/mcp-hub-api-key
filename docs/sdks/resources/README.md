# Resources
(*resources()*)

## Overview

Resource management and subscription

### Available Operations

* [listResources](#listresources) - List resources available from MCP servers
* [readResource](#readresource) - Read a specific resource
* [listResourceTemplates](#listresourcetemplates) - List resource templates
* [subscribeResource](#subscriberesource) - Subscribe to resource updates
* [unsubscribeResource](#unsubscriberesource) - Unsubscribe from resource updates

## listResources

Returns cached resource metadata discoverable from connected MCP servers.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListResourcesResponse;
import org.openapis.openapi.models.operations.ListResourcesSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListResourcesResponse res = sdk.resources().listResources()
                .security(ListResourcesSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.resources().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                        | Type                                                                                                             | Required                                                                                                         | Description                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                       | [org.openapis.openapi.models.operations.ListResourcesSecurity](../../models/operations/ListResourcesSecurity.md) | :heavy_check_mark:                                                                                               | The security requirements to use for the request.                                                                |
| `serverId`                                                                                                       | *Optional\<String>*                                                                                              | :heavy_minus_sign:                                                                                               | Filter resources by MCP server ID                                                                                |

### Response

**[ListResourcesResponse](../../models/operations/ListResourcesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## readResource

Read a specific resource

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ReadResourceResponse;
import org.openapis.openapi.models.operations.ReadResourceSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ReadResourceResponse res = sdk.resources().readResource()
                .security(ReadResourceSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .resourceId("<id>")
                .call();

        if (res.resourceContent().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                     | [org.openapis.openapi.models.operations.ReadResourceSecurity](../../models/operations/ReadResourceSecurity.md) | :heavy_check_mark:                                                                                             | The security requirements to use for the request.                                                              |
| `resourceId`                                                                                                   | *String*                                                                                                       | :heavy_check_mark:                                                                                             | Unique identifier of the resource                                                                              |

### Response

**[ReadResourceResponse](../../models/operations/ReadResourceResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## listResourceTemplates

List resource templates

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListResourceTemplatesResponse;
import org.openapis.openapi.models.operations.ListResourceTemplatesSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListResourceTemplatesResponse res = sdk.resources().listResourceTemplates()
                .security(ListResourceTemplatesSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.resourceTemplates().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                       | [org.openapis.openapi.models.operations.ListResourceTemplatesSecurity](../../models/operations/ListResourceTemplatesSecurity.md) | :heavy_check_mark:                                                                                                               | The security requirements to use for the request.                                                                                |

### Response

**[ListResourceTemplatesResponse](../../models/operations/ListResourceTemplatesResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## subscribeResource

Subscribe to resource updates

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.SubscribeResourceResponse;
import org.openapis.openapi.models.operations.SubscribeResourceSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        SubscribeResourceResponse res = sdk.resources().subscribeResource()
                .security(SubscribeResourceSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .resourceId("<id>")
                .call();

        if (res.inlineResponse2005().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                               | [org.openapis.openapi.models.operations.SubscribeResourceSecurity](../../models/operations/SubscribeResourceSecurity.md) | :heavy_check_mark:                                                                                                       | The security requirements to use for the request.                                                                        |
| `resourceId`                                                                                                             | *String*                                                                                                                 | :heavy_check_mark:                                                                                                       | Unique identifier of the resource                                                                                        |

### Response

**[SubscribeResourceResponse](../../models/operations/SubscribeResourceResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## unsubscribeResource

Unsubscribe from resource updates

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.UnsubscribeResourceResponse;
import org.openapis.openapi.models.operations.UnsubscribeResourceSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        UnsubscribeResourceResponse res = sdk.resources().unsubscribeResource()
                .security(UnsubscribeResourceSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .resourceId("<id>")
                .call();

        if (res.inlineResponse2006().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                   | [org.openapis.openapi.models.operations.UnsubscribeResourceSecurity](../../models/operations/UnsubscribeResourceSecurity.md) | :heavy_check_mark:                                                                                                           | The security requirements to use for the request.                                                                            |
| `resourceId`                                                                                                                 | *String*                                                                                                                     | :heavy_check_mark:                                                                                                           | Unique identifier of the resource                                                                                            |

### Response

**[UnsubscribeResourceResponse](../../models/operations/UnsubscribeResourceResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |