# Connections
(*connections*)

## Overview

MCP connection lifecycle management

### Available Operations

* [list_connections](#list_connections) - List all MCP connections for the authenticated user
* [create_connection](#create_connection) - Create and initialize a new MCP connection
* [get_connection_by_id](#get_connection_by_id) - Get details and status of a specific MCP connection
* [delete_connection](#delete_connection) - Disconnect and remove an MCP connection
* [ping_connection](#ping_connection) - Send a ping to the MCP server via the connection

## list_connections

List all MCP connections for the authenticated user

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connections.list_connections(security=cassie_marie_mcp_hub_api_python.ListConnectionsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.ListConnectionsSecurity](../../listconnectionssecurity.md)  | :heavy_check_mark:                                                  | The security requirements to use for the request.                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Connection]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## create_connection

Create and initialize a new MCP connection

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connections.create_connection(security=cassie_marie_mcp_hub_api_python.CreateConnectionSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), server_id="server-123", transport=cassie_marie_mcp_hub_api_python.ConnectionsBodyTransport.STDIO, options={
        "command": "/usr/local/bin/mcp-server",
        "args": [
            "--stdio",
        ],
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                                       | [models.CreateConnectionSecurity](../../models/createconnectionsecurity.md)                                                      | :heavy_check_mark:                                                                                                               | N/A                                                                                                                              |
| `server_id`                                                                                                                      | *str*                                                                                                                            | :heavy_check_mark:                                                                                                               | MCP server ID to connect to                                                                                                      |
| `transport`                                                                                                                      | [models.ConnectionsBodyTransport](../../models/connectionsbodytransport.md)                                                      | :heavy_check_mark:                                                                                                               | Transport type (stdio or streamable-http)                                                                                        |
| `options`                                                                                                                        | [Optional[models.Options]](../../models/options.md)                                                                              | :heavy_minus_sign:                                                                                                               | Transport-specific options. Use stdio options for stdio connections and streamable HTTP options for streamable-http connections. |
| `retries`                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                 | :heavy_minus_sign:                                                                                                               | Configuration to override the default retry behavior of the client.                                                              |

### Response

**[models.Connection](../../models/connection.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_connection_by_id

Get details and status of a specific MCP connection

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connections.get_connection_by_id(security=cassie_marie_mcp_hub_api_python.GetConnectionByIDSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `security`                                                                    | [models.GetConnectionByIDSecurity](../../models/getconnectionbyidsecurity.md) | :heavy_check_mark:                                                            | N/A                                                                           |
| `connection_id`                                                               | *str*                                                                         | :heavy_check_mark:                                                            | Unique identifier of the connection                                           |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.Connection](../../models/connection.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## delete_connection

Disconnect and remove an MCP connection

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    mcp_hub_api_python.connections.delete_connection(security=cassie_marie_mcp_hub_api_python.DeleteConnectionSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `security`                                                                  | [models.DeleteConnectionSecurity](../../models/deleteconnectionsecurity.md) | :heavy_check_mark:                                                          | N/A                                                                         |
| `connection_id`                                                             | *str*                                                                       | :heavy_check_mark:                                                          | Unique identifier of the connection                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## ping_connection

Send a ping to the MCP server via the connection

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connections.ping_connection(security=cassie_marie_mcp_hub_api_python.PingConnectionSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `security`                                                              | [models.PingConnectionSecurity](../../models/pingconnectionsecurity.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `connection_id`                                                         | *str*                                                                   | :heavy_check_mark:                                                      | Unique identifier of the connection                                     |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.InlineResponse2004](../../models/inlineresponse2004.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |