# Contexts
(*contexts*)

## Overview

MCP server contexts and models management

### Available Operations

* [list_contexts](#list_contexts) - List available contexts from connected MCP servers
* [get_context_by_id](#get_context_by_id) - Get details of a specific context
* [list_models_in_context](#list_models_in_context) - List models available in a specific context

## list_contexts

List available contexts from connected MCP servers

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.contexts.list_contexts(security=cassie_marie_mcp_hub_api_python.ListContextsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.ListContextsSecurity](../../models/listcontextssecurity.md) | :heavy_check_mark:                                                  | N/A                                                                 |
| `server_id`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter contexts by MCP server ID                                    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Context]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_context_by_id

Get details of a specific context

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.contexts.get_context_by_id(security=cassie_marie_mcp_hub_api_python.GetContextByIDSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), context_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `security`                                                              | [models.GetContextByIDSecurity](../../models/getcontextbyidsecurity.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `context_id`                                                            | *str*                                                                   | :heavy_check_mark:                                                      | Unique identifier of the context                                        |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.Context](../../models/context.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## list_models_in_context

List models available in a specific context

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.contexts.list_models_in_context(security=cassie_marie_mcp_hub_api_python.ListModelsInContextSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), context_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `security`                                                                        | [models.ListModelsInContextSecurity](../../models/listmodelsincontextsecurity.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `context_id`                                                                      | *str*                                                                             | :heavy_check_mark:                                                                | Unique identifier of the context                                                  |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[List[models.Model]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |