# Logging
(*logging*)

## Overview

Logging level management

### Available Operations

* [set_logging_level](#set_logging_level) - Set logging level for MCP Hub runtime

## set_logging_level

Set logging level for MCP Hub runtime

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.logging.set_logging_level(security=cassie_marie_mcp_hub_api_python.SetLoggingLevelSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), level=cassie_marie_mcp_hub_api_python.Level.INFO)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `security`                                                                | [models.SetLoggingLevelSecurity](../../models/setlogginglevelsecurity.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `level`                                                                   | [models.Level](../../models/level.md)                                     | :heavy_check_mark:                                                        | Logging level to set                                                      |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.InlineResponse2001](../../models/inlineresponse2001.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |