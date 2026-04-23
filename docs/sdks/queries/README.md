# Queries
(*queries*)

## Overview

Sending queries and commands to MCP servers

### Available Operations

* [post_query](#post_query) - Send a query or command to an MCP server

## post_query

Send a query or command to an MCP server

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.queries.post_query(security=cassie_marie_mcp_hub_api_python.PostQuerySecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), server_id="server-123", context_id="context-456", model_id="model-789", query="SELECT * FROM users WHERE active = true", parameters={
        "limit": 10,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.PostQuerySecurity](../../models/postquerysecurity.md)       | :heavy_check_mark:                                                  | N/A                                                                 |
| `server_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Target MCP server ID                                                |
| `context_id`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Target context ID                                                   |
| `model_id`                                                          | *str*                                                               | :heavy_check_mark:                                                  | Target model ID                                                     |
| `query`                                                             | *str*                                                               | :heavy_check_mark:                                                  | Query or command string to execute                                  |
| `parameters`                                                        | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | Optional parameters for the query                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.InlineResponse2008](../../models/inlineresponse2008.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |