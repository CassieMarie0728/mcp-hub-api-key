# Events
(*events*)

## Overview

Event streaming and request inspection

### Available Operations

* [stream_events](#stream_events) - Stream live events and notifications (SSE or WebSocket)
* [get_request_details](#get_request_details) - Get details and history of a specific request

## stream_events

Stream live events and notifications (SSE or WebSocket)

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.events.stream_events(security=cassie_marie_mcp_hub_api_python.StreamEventsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `security`                                                          | [models.StreamEventsSecurity](../../streameventssecurity.md)        | :heavy_check_mark:                                                  | The security requirements to use for the request.                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[str](../../models/.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## get_request_details

Get details and history of a specific request

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.events.get_request_details(security=cassie_marie_mcp_hub_api_python.GetRequestDetailsSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), request_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `security`                                                                    | [models.GetRequestDetailsSecurity](../../models/getrequestdetailssecurity.md) | :heavy_check_mark:                                                            | N/A                                                                           |
| `request_id`                                                                  | *str*                                                                         | :heavy_check_mark:                                                            | Unique identifier of the request                                              |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.RequestDetails](../../models/requestdetails.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 401, 404         | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |