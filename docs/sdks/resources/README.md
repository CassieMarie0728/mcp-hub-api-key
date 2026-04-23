# Resources
(*resources*)

## Overview

Resource management and subscription

### Available Operations

* [list_resources](#list_resources) - List resources available from MCP servers
* [read_resource](#read_resource) - Read a specific resource
* [list_resource_templates](#list_resource_templates) - List resource templates
* [subscribe_resource](#subscribe_resource) - Subscribe to resource updates
* [unsubscribe_resource](#unsubscribe_resource) - Unsubscribe from resource updates

## list_resources

Returns cached resource metadata discoverable from connected MCP servers.

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.resources.list_resources(security=cassie_marie_mcp_hub_api_python.ListResourcesSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `security`                                                            | [models.ListResourcesSecurity](../../models/listresourcessecurity.md) | :heavy_check_mark:                                                    | N/A                                                                   |
| `server_id`                                                           | *Optional[str]*                                                       | :heavy_minus_sign:                                                    | Filter resources by MCP server ID                                     |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[List[models.Resource]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## read_resource

Read a specific resource

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.resources.read_resource(security=cassie_marie_mcp_hub_api_python.ReadResourceSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), resource_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.ReadResourceSecurity](../../models/readresourcesecurity.md) | :heavy_check_mark:                                                  | N/A                                                                 |
| `resource_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Unique identifier of the resource                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## list_resource_templates

List resource templates

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.resources.list_resource_templates(security=cassie_marie_mcp_hub_api_python.ListResourceTemplatesSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `security`                                                                     | [models.ListResourceTemplatesSecurity](../../listresourcetemplatessecurity.md) | :heavy_check_mark:                                                             | The security requirements to use for the request.                              |
| `retries`                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)               | :heavy_minus_sign:                                                             | Configuration to override the default retry behavior of the client.            |

### Response

**[List[models.ResourceTemplate]](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## subscribe_resource

Subscribe to resource updates

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.resources.subscribe_resource(security=cassie_marie_mcp_hub_api_python.SubscribeResourceSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), resource_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `security`                                                                    | [models.SubscribeResourceSecurity](../../models/subscriberesourcesecurity.md) | :heavy_check_mark:                                                            | N/A                                                                           |
| `resource_id`                                                                 | *str*                                                                         | :heavy_check_mark:                                                            | Unique identifier of the resource                                             |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.InlineResponse2005](../../models/inlineresponse2005.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## unsubscribe_resource

Unsubscribe from resource updates

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.resources.unsubscribe_resource(security=cassie_marie_mcp_hub_api_python.UnsubscribeResourceSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), resource_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `security`                                                                        | [models.UnsubscribeResourceSecurity](../../models/unsubscriberesourcesecurity.md) | :heavy_check_mark:                                                                | N/A                                                                               |
| `resource_id`                                                                     | *str*                                                                             | :heavy_check_mark:                                                                | Unique identifier of the resource                                                 |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.InlineResponse2006](../../models/inlineresponse2006.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |