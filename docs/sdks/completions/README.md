# Completions
(*completions*)

## Overview

Completion requests

### Available Operations

* [post_completion](#post_completion) - Request a completion from an MCP server

## post_completion

Request a completion from an MCP server

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.completions.post_completion(security=cassie_marie_mcp_hub_api_python.PostCompletionSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), server_id="server-123", context_id="context-456", model_id="model-789", prompt="Translate the following text to French:", parameters={
        "maxTokens": 100,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `security`                                                              | [models.PostCompletionSecurity](../../models/postcompletionsecurity.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `server_id`                                                             | *str*                                                                   | :heavy_check_mark:                                                      | Target MCP server ID                                                    |
| `context_id`                                                            | *str*                                                                   | :heavy_check_mark:                                                      | Target context ID                                                       |
| `model_id`                                                              | *str*                                                                   | :heavy_check_mark:                                                      | Target model ID                                                         |
| `prompt`                                                                | *str*                                                                   | :heavy_check_mark:                                                      | Prompt string to complete                                               |
| `parameters`                                                            | Dict[str, *Any*]                                                        | :heavy_minus_sign:                                                      | Optional parameters for the completion                                  |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.InlineResponse2007](../../models/inlineresponse2007.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |