# Tools
(*tools*)

## Overview

Access to related tools integrated within MCP Hub

### Available Operations

* [list_tools](#list_tools) - List available tools integrated within MCP Hub
* [get_tool_by_id](#get_tool_by_id) - Get details of a specific tool

## list_tools

Returns the hub-level tool catalog or cached tool registry.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.tools.list_tools(security=cassie_marie_mcp_hub_api_python.ListToolsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.ListToolsSecurity](../../listtoolssecurity.md)              | :heavy_check_mark:                                                  | The security requirements to use for the request.                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Tool]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_tool_by_id

Get details of a specific tool

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.tools.get_tool_by_id(security=cassie_marie_mcp_hub_api_python.GetToolByIDSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), tool_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.GetToolByIDSecurity](../../models/gettoolbyidsecurity.md)   | :heavy_check_mark:                                                  | N/A                                                                 |
| `tool_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | Unique identifier of the tool                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.Tool](../../models/tool.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |