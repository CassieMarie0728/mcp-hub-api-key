# Prompts
(*prompts*)

## Overview

Prompt listing and retrieval

### Available Operations

* [list_prompts](#list_prompts) - List available prompts
* [get_prompt_by_id](#get_prompt_by_id) - Get details of a specific prompt

## list_prompts

Returns cached prompt metadata available through MCP connections.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.prompts.list_prompts(security=cassie_marie_mcp_hub_api_python.ListPromptsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.ListPromptsSecurity](../../listpromptssecurity.md)          | :heavy_check_mark:                                                  | The security requirements to use for the request.                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.Prompt]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_prompt_by_id

Get details of a specific prompt

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.prompts.get_prompt_by_id(security=cassie_marie_mcp_hub_api_python.GetPromptByIDSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), prompt_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `security`                                                            | [models.GetPromptByIDSecurity](../../models/getpromptbyidsecurity.md) | :heavy_check_mark:                                                    | N/A                                                                   |
| `prompt_id`                                                           | *str*                                                                 | :heavy_check_mark:                                                    | Unique identifier of the prompt                                       |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.Prompt](../../models/prompt.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |