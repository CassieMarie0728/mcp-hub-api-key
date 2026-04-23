# Capabilities
(*capabilities*)

## Overview

Capability and server metadata inspection

### Available Operations

* [list_capabilities](#list_capabilities) - List capabilities of connected MCP servers

## list_capabilities

Returns a summarized view of negotiated capabilities across active connections.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.capabilities.list_capabilities(security=cassie_marie_mcp_hub_api_python.ListCapabilitiesSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `security`                                                           | [models.ListCapabilitiesSecurity](../../listcapabilitiessecurity.md) | :heavy_check_mark:                                                   | The security requirements to use for the request.                    |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |

### Response

**[List[models.Capability]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |