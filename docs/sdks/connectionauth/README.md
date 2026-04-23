# ConnectionAuth
(*connection_auth*)

## Overview

Per-connection authentication bootstrap and status

### Available Operations

* [get_connection_auth_status](#get_connection_auth_status) - Get auth status for a connection
* [start_connection_auth](#start_connection_auth) - Start auth flow for a connection

## get_connection_auth_status

Returns whether the remote MCP server connection is authenticated and what auth type is active.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connection_auth.get_connection_auth_status(security=cassie_marie_mcp_hub_api_python.GetConnectionAuthStatusSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `security`                                                                                | [models.GetConnectionAuthStatusSecurity](../../models/getconnectionauthstatussecurity.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `connection_id`                                                                           | *str*                                                                                     | :heavy_check_mark:                                                                        | Unique identifier of the connection.                                                      |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |

### Response

**[models.AuthStatus](../../models/authstatus.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## start_connection_auth

Bootstraps remote authentication for MCP servers that require browser or token-based authorization.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.connection_auth.start_connection_auth(security=cassie_marie_mcp_hub_api_python.StartConnectionAuthSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", callback_url="https://app.example.com/mcp/auth/callback", scopes=[
        "tools:read",
        "resources:read",
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `security`                                                                        | [models.StartConnectionAuthSecurity](../../models/startconnectionauthsecurity.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `connection_id`                                                                   | *str*                                                                             | :heavy_check_mark:                                                                | Unique identifier of the connection.                                              |
| `callback_url`                                                                    | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | Client callback URL for completing auth.                                          |
| `scopes`                                                                          | List[*str*]                                                                       | :heavy_minus_sign:                                                                | Requested scopes for the connection.                                              |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.AuthStartResponse](../../models/authstartresponse.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |