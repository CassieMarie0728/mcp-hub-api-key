# Runtime
(*runtime*)

## Overview

Per-connection MCP runtime operations such as initialize, tool invocation, and cancellation

### Available Operations

* [initialize_connection](#initialize_connection) - Initialize an existing MCP connection
* [get_connection_capabilities](#get_connection_capabilities) - Get negotiated capabilities for a connection
* [list_connection_tools](#list_connection_tools) - List tools for a connection
* [call_connection_tool](#call_connection_tool) - Call a tool on a connection
* [list_connection_resources](#list_connection_resources) - List resources for a connection
* [read_connection_resource](#read_connection_resource) - Read a resource by URI on a connection
* [list_connection_prompts](#list_connection_prompts) - List prompts for a connection
* [get_connection_prompt](#get_connection_prompt) - Get a rendered prompt from a connection
* [cancel_connection_request](#cancel_connection_request) - Cancel an in-flight request on a connection

## initialize_connection

Performs MCP initialize and initialized lifecycle calls for a created connection.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.initialize_connection(security=cassie_marie_mcp_hub_api_python.InitializeConnectionSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", client_name="MCP Hub", client_version="2.1.0", protocol_version="2025-06-18", client_capabilities={
        "roots": {
            "listChanged": True,
        },
        "sampling": {

        },
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `security`                                                                          | [models.InitializeConnectionSecurity](../../models/initializeconnectionsecurity.md) | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `connection_id`                                                                     | *str*                                                                               | :heavy_check_mark:                                                                  | Unique identifier of the connection.                                                |
| `client_name`                                                                       | *str*                                                                               | :heavy_check_mark:                                                                  | Human-readable name of the MCP Hub client.                                          |
| `client_version`                                                                    | *str*                                                                               | :heavy_check_mark:                                                                  | Semantic version of the MCP Hub client.                                             |
| `protocol_version`                                                                  | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | Preferred MCP protocol version.                                                     |
| `client_capabilities`                                                               | Dict[str, *Any*]                                                                    | :heavy_minus_sign:                                                                  | Client capabilities advertised during initialization.                               |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.ConnectionInitializeResponse](../../models/connectioninitializeresponse.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_connection_capabilities

Returns the current server and client capability view for a single connection.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.get_connection_capabilities(security=cassie_marie_mcp_hub_api_python.GetConnectionCapabilitiesSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `security`                                                                                    | [models.GetConnectionCapabilitiesSecurity](../../models/getconnectioncapabilitiessecurity.md) | :heavy_check_mark:                                                                            | N/A                                                                                           |
| `connection_id`                                                                               | *str*                                                                                         | :heavy_check_mark:                                                                            | Unique identifier of the connection.                                                          |
| `retries`                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                              | :heavy_minus_sign:                                                                            | Configuration to override the default retry behavior of the client.                           |

### Response

**[models.Capability](../../models/capability.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## list_connection_tools

Fetches the live tool list exposed by the connected MCP server.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.list_connection_tools(security=cassie_marie_mcp_hub_api_python.ListConnectionToolsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `security`                                                                        | [models.ListConnectionToolsSecurity](../../models/listconnectiontoolssecurity.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `connection_id`                                                                   | *str*                                                                             | :heavy_check_mark:                                                                | Unique identifier of the connection.                                              |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[List[models.Tool]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## call_connection_tool

Invokes a named MCP tool against the target connection.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.call_connection_tool(security=cassie_marie_mcp_hub_api_python.CallConnectionToolSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", tool_name="<value>", arguments={
        "path": "/docs/readme.md",
    }, request_id="req-tool-001")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `security`                                                                      | [models.CallConnectionToolSecurity](../../models/callconnectiontoolsecurity.md) | :heavy_check_mark:                                                              | N/A                                                                             |
| `connection_id`                                                                 | *str*                                                                           | :heavy_check_mark:                                                              | Unique identifier of the connection.                                            |
| `tool_name`                                                                     | *str*                                                                           | :heavy_check_mark:                                                              | Name of the MCP tool to invoke.                                                 |
| `arguments`                                                                     | Dict[str, *Any*]                                                                | :heavy_check_mark:                                                              | Arguments passed to the target tool.                                            |
| `request_id`                                                                    | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | Optional client-generated id for tracing.                                       |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.ToolCallResult](../../models/toolcallresult.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## list_connection_resources

Fetches the live resource list from the connected MCP server.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.list_connection_resources(security=cassie_marie_mcp_hub_api_python.ListConnectionResourcesSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `security`                                                                                | [models.ListConnectionResourcesSecurity](../../models/listconnectionresourcessecurity.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `connection_id`                                                                           | *str*                                                                                     | :heavy_check_mark:                                                                        | Unique identifier of the connection.                                                      |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |

### Response

**[List[models.Resource]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## read_connection_resource

Reads a live resource from the MCP server using its resource URI.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.read_connection_resource(security=cassie_marie_mcp_hub_api_python.ReadConnectionResourceSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", uri="file:///workspace/notes/todo.md")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `security`                                                                              | [models.ReadConnectionResourceSecurity](../../models/readconnectionresourcesecurity.md) | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `connection_id`                                                                         | *str*                                                                                   | :heavy_check_mark:                                                                      | Unique identifier of the connection.                                                    |
| `uri`                                                                                   | *str*                                                                                   | :heavy_check_mark:                                                                      | Resource URI exposed by the MCP server.                                                 |
| `cursor`                                                                                | *OptionalNullable[str]*                                                                 | :heavy_minus_sign:                                                                      | Optional pagination cursor.                                                             |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 404    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## list_connection_prompts

Fetches prompt templates directly from the connected MCP server.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.list_connection_prompts(security=cassie_marie_mcp_hub_api_python.ListConnectionPromptsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `security`                                                                            | [models.ListConnectionPromptsSecurity](../../models/listconnectionpromptssecurity.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `connection_id`                                                                       | *str*                                                                                 | :heavy_check_mark:                                                                    | Unique identifier of the connection.                                                  |
| `retries`                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                      | :heavy_minus_sign:                                                                    | Configuration to override the default retry behavior of the client.                   |

### Response

**[List[models.Prompt]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_connection_prompt

Retrieves a prompt template and applies optional prompt arguments.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.get_connection_prompt(security=cassie_marie_mcp_hub_api_python.GetConnectionPromptSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", prompt_name="<value>", arguments={
        "targetLanguage": "fr",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `security`                                                                        | [models.GetConnectionPromptSecurity](../../models/getconnectionpromptsecurity.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `connection_id`                                                                   | *str*                                                                             | :heavy_check_mark:                                                                | Unique identifier of the connection.                                              |
| `prompt_name`                                                                     | *str*                                                                             | :heavy_check_mark:                                                                | Name of the prompt template.                                                      |
| `arguments`                                                                       | Dict[str, *Any*]                                                                  | :heavy_minus_sign:                                                                | Prompt template arguments.                                                        |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.Prompt](../../models/prompt.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## cancel_connection_request

Requests cancellation for an active MCP request.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.runtime.cancel_connection_request(security=cassie_marie_mcp_hub_api_python.CancelConnectionRequestSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), connection_id="<id>", request_id="req-123abc", reason="User navigated away")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `security`                                                                                | [models.CancelConnectionRequestSecurity](../../models/cancelconnectionrequestsecurity.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `connection_id`                                                                           | *str*                                                                                     | :heavy_check_mark:                                                                        | Unique identifier of the connection.                                                      |
| `request_id`                                                                              | *str*                                                                                     | :heavy_check_mark:                                                                        | Identifier of the in-flight request to cancel.                                            |
| `reason`                                                                                  | *OptionalNullable[str]*                                                                   | :heavy_minus_sign:                                                                        | Optional user-facing cancellation reason.                                                 |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |

### Response

**[models.InlineResponse202](../../models/inlineresponse202.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |