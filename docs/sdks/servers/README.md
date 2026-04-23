# Servers
(*servers()*)

## Overview

MCP server discovery and management

### Available Operations

* [listMcpServers](#listmcpservers) - List available MCP servers
* [registerMcpServer](#registermcpserver) - Register a new MCP server (admin only)
* [getMcpServerById](#getmcpserverbyid) - Get details of a specific MCP server

## listMcpServers

Returns MCP servers that the current user can browse or connect to.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListMcpServersResponse;
import org.openapis.openapi.models.operations.ListMcpServersSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListMcpServersResponse res = sdk.servers().listMcpServers()
                .security(ListMcpServersSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.mcpServers().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                         | [org.openapis.openapi.models.operations.ListMcpServersSecurity](../../models/operations/ListMcpServersSecurity.md) | :heavy_check_mark:                                                                                                 | The security requirements to use for the request.                                                                  |
| `region`                                                                                                           | *Optional\<String>*                                                                                                | :heavy_minus_sign:                                                                                                 | Filter servers by region                                                                                           |
| `status`                                                                                                           | [Optional\<Status>](../../models/operations/Status.md)                                                             | :heavy_minus_sign:                                                                                                 | Filter servers by status (e.g., online, offline)                                                                   |

### Response

**[ListMcpServersResponse](../../models/operations/ListMcpServersResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## registerMcpServer

Register a new MCP server (admin only)

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.ServersBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.RegisterMcpServerResponse;
import org.openapis.openapi.models.operations.RegisterMcpServerSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ServersBody req = ServersBody.builder()
                .name("MCP Server Alpha")
                .url("https://mcp-alpha.example.com")
                .description("Primary MCP server for region A")
                .build();

        RegisterMcpServerResponse res = sdk.servers().registerMcpServer()
                .request(req)
                .security(RegisterMcpServerSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.mcpServer().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                | [ServersBody](../../models/shared/ServersBody.md)                                                                        | :heavy_check_mark:                                                                                                       | The request object to use for the request.                                                                               |
| `security`                                                                                                               | [org.openapis.openapi.models.operations.RegisterMcpServerSecurity](../../models/operations/RegisterMcpServerSecurity.md) | :heavy_check_mark:                                                                                                       | The security requirements to use for the request.                                                                        |

### Response

**[RegisterMcpServerResponse](../../models/operations/RegisterMcpServerResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401, 403              | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getMcpServerById

Get details of a specific MCP server

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetMcpServerByIdResponse;
import org.openapis.openapi.models.operations.GetMcpServerByIdSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetMcpServerByIdResponse res = sdk.servers().getMcpServerById()
                .security(GetMcpServerByIdSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .serverId("<id>")
                .call();

        if (res.mcpServer().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                              | Type                                                                                                                   | Required                                                                                                               | Description                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                             | [org.openapis.openapi.models.operations.GetMcpServerByIdSecurity](../../models/operations/GetMcpServerByIdSecurity.md) | :heavy_check_mark:                                                                                                     | The security requirements to use for the request.                                                                      |
| `serverId`                                                                                                             | *String*                                                                                                               | :heavy_check_mark:                                                                                                     | Unique identifier of the MCP server                                                                                    |

### Response

**[GetMcpServerByIdResponse](../../models/operations/GetMcpServerByIdResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 404                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |