# System
(*system*)

## Overview

System related endpoints

### Available Operations

* [get_system_health](#get_system_health) - Health check endpoint
* [post_notify_owner](#post_notify_owner) - Notify owner (admin only)

## get_system_health

Health check endpoint

### Example Usage

```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `timestamp`                                                         | *float*                                                             | :heavy_check_mark:                                                  | Timestamp for health check, must be a non-negative number           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.InlineResponse200](../../models/inlineresponse200.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400              | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |

## post_notify_owner

Notify owner (admin only)

### Example Usage

```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.post_notify_owner(security=cassie_marie_mcp_hub_api_python.PostNotifyOwnerSecurity(
        app_session_cookie="<YOUR_API_KEY_HERE>",
    ), title="System Alert", content="An important event has occurred.")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `security`                                                                | [models.PostNotifyOwnerSecurity](../../models/postnotifyownersecurity.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `title`                                                                   | *str*                                                                     | :heavy_check_mark:                                                        | Notification title                                                        |
| `content`                                                                 | *str*                                                                     | :heavy_check_mark:                                                        | Notification content                                                      |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.InlineResponse2001](../../models/inlineresponse2001.md)**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| models.Error     | 400, 401, 403    | application/json |
| models.APIError  | 4XX, 5XX         | \*/\*            |