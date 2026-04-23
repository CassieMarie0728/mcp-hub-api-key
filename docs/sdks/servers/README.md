# Servers
(*servers*)

## Overview

MCP server discovery and management

### Available Operations

* [list_mcp_servers](#list_mcp_servers) - List available MCP servers
* [register_mcp_server](#register_mcp_server) - Register a new MCP server (admin only)
* [get_mcp_server_by_id](#get_mcp_server_by_id) - Get details of a specific MCP server

## list_mcp_servers

Returns MCP servers that the current user can browse or connect to.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.servers.list_mcp_servers(security=cassie_marie_mcp_hub_api_python.ListMcpServersSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `security`                                                              | [models.ListMcpServersSecurity](../../models/listmcpserverssecurity.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `region`                                                                | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | Filter servers by region                                                |
| `status`                                                                | [Optional[models.QueryParamStatus]](../../models/queryparamstatus.md)   | :heavy_minus_sign:                                                      | Filter servers by status (e.g., online, offline)                        |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[List[models.McpServer]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## register_mcp_server

Register a new MCP server (admin only)

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.servers.register_mcp_server(security=cassie_marie_mcp_hub_api_python.RegisterMcpServerSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), name="MCP Server Alpha", url="https://mcp-alpha.example.com", description="Primary MCP server for region A")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `security`                                                                    | [models.RegisterMcpServerSecurity](../../models/registermcpserversecurity.md) | :heavy_check_mark:                                                            | N/A                                                                           |
| `name`                                                                        | *str*                                                                         | :heavy_check_mark:                                                            | Server display name                                                           |
| `url`                                                                         | *str*                                                                         | :heavy_check_mark:                                                            | Base URL of the MCP server                                                    |
| `description`                                                                 | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | Optional server description                                                   |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.McpServer](../../models/mcpserver.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 403    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_mcp_server_by_id

Get details of a specific MCP server

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.servers.get_mcp_server_by_id(security=cassie_marie_mcp_hub_api_python.GetMcpServerByIDSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), server_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `security`                                                                  | [models.GetMcpServerByIDSecurity](../../models/getmcpserverbyidsecurity.md) | :heavy_check_mark:                                                          | N/A                                                                         |
| `server_id`                                                                 | *str*                                                                       | :heavy_check_mark:                                                          | Unique identifier of the MCP server                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.McpServer](../../models/mcpserver.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 404              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |