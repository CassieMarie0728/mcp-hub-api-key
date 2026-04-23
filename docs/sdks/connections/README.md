# Connections
(*connections()*)

## Overview

MCP connection lifecycle management

### Available Operations

* [listConnections](#listconnections) - List all MCP connections for the authenticated user
* [createConnection](#createconnection) - Create and initialize a new MCP connection
* [getConnectionById](#getconnectionbyid) - Get details and status of a specific MCP connection
* [deleteConnection](#deleteconnection) - Disconnect and remove an MCP connection
* [pingConnection](#pingconnection) - Send a ping to the MCP server via the connection

## listConnections

List all MCP connections for the authenticated user

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.ListConnectionsResponse;
import org.openapis.openapi.models.operations.ListConnectionsSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ListConnectionsResponse res = sdk.connections().listConnections()
                .security(ListConnectionsSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.connections().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                            | Type                                                                                                                 | Required                                                                                                             | Description                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                           | [org.openapis.openapi.models.operations.ListConnectionsSecurity](../../models/operations/ListConnectionsSecurity.md) | :heavy_check_mark:                                                                                                   | The security requirements to use for the request.                                                                    |

### Response

**[ListConnectionsResponse](../../models/operations/ListConnectionsResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## createConnection

Create and initialize a new MCP connection

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.CreateConnectionResponse;
import org.openapis.openapi.models.operations.CreateConnectionSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        ConnectionsBody req = ConnectionsBody.builder()
                .serverId("server-123")
                .transport(ConnectionsBodyTransport.STDIO)
                .options(Options.of(TransportOptionsStdio.builder()
                    .command("/usr/local/bin/mcp-server")
                    .args(List.of(
                        "--stdio"))
                    .build()))
                .build();

        CreateConnectionResponse res = sdk.connections().createConnection()
                .request(req)
                .security(CreateConnectionSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.connection().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                              | Type                                                                                                                   | Required                                                                                                               | Description                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `request`                                                                                                              | [ConnectionsBody](../../models/shared/ConnectionsBody.md)                                                              | :heavy_check_mark:                                                                                                     | The request object to use for the request.                                                                             |
| `security`                                                                                                             | [org.openapis.openapi.models.operations.CreateConnectionSecurity](../../models/operations/CreateConnectionSecurity.md) | :heavy_check_mark:                                                                                                     | The security requirements to use for the request.                                                                      |

### Response

**[CreateConnectionResponse](../../models/operations/CreateConnectionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getConnectionById

Get details and status of a specific MCP connection

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetConnectionByIdResponse;
import org.openapis.openapi.models.operations.GetConnectionByIdSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetConnectionByIdResponse res = sdk.connections().getConnectionById()
                .security(GetConnectionByIdSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.connection().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                                | Type                                                                                                                     | Required                                                                                                                 | Description                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                               | [org.openapis.openapi.models.operations.GetConnectionByIdSecurity](../../models/operations/GetConnectionByIdSecurity.md) | :heavy_check_mark:                                                                                                       | The security requirements to use for the request.                                                                        |
| `connectionId`                                                                                                           | *String*                                                                                                                 | :heavy_check_mark:                                                                                                       | Unique identifier of the connection                                                                                      |

### Response

**[GetConnectionByIdResponse](../../models/operations/GetConnectionByIdResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## deleteConnection

Disconnect and remove an MCP connection

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.DeleteConnectionResponse;
import org.openapis.openapi.models.operations.DeleteConnectionSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        DeleteConnectionResponse res = sdk.connections().deleteConnection()
                .security(DeleteConnectionSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                              | Type                                                                                                                   | Required                                                                                                               | Description                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                             | [org.openapis.openapi.models.operations.DeleteConnectionSecurity](../../models/operations/DeleteConnectionSecurity.md) | :heavy_check_mark:                                                                                                     | The security requirements to use for the request.                                                                      |
| `connectionId`                                                                                                         | *String*                                                                                                               | :heavy_check_mark:                                                                                                     | Unique identifier of the connection                                                                                    |

### Response

**[DeleteConnectionResponse](../../models/operations/DeleteConnectionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## pingConnection

Send a ping to the MCP server via the connection

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PingConnectionResponse;
import org.openapis.openapi.models.operations.PingConnectionSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        PingConnectionResponse res = sdk.connections().pingConnection()
                .security(PingConnectionSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .connectionId("<id>")
                .call();

        if (res.inlineResponse2004().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                         | [org.openapis.openapi.models.operations.PingConnectionSecurity](../../models/operations/PingConnectionSecurity.md) | :heavy_check_mark:                                                                                                 | The security requirements to use for the request.                                                                  |
| `connectionId`                                                                                                     | *String*                                                                                                           | :heavy_check_mark:                                                                                                 | Unique identifier of the connection                                                                                |

### Response

**[PingConnectionResponse](../../models/operations/PingConnectionResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401, 404                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |