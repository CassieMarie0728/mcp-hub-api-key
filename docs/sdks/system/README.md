# System
(*system*)

## Overview

System related endpoints

### Available Operations

* [getSystemHealth](#getsystemhealth) - Health check endpoint
* [postNotifyOwner](#postnotifyowner) - Notify owner (admin only)

## getSystemHealth

Health check endpoint

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { systemGetSystemHealth } from "@cassie-marie/mcp-hub-api-typescript/funcs/systemGetSystemHealth.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await systemGetSystemHealth(mcpHubApiTypescript, {
    timestamp: 6433.07,
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("systemGetSystemHealth failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetSystemHealthRequest](../../models/operations/getsystemhealthrequest.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.InlineResponse200](../../models/components/inlineresponse200.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400              | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## postNotifyOwner

Notify owner (admin only)

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.system.postNotifyOwner({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    title: "System Alert",
    content: "An important event has occurred.",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { systemPostNotifyOwner } from "@cassie-marie/mcp-hub-api-typescript/funcs/systemPostNotifyOwner.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await systemPostNotifyOwner(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    title: "System Alert",
    content: "An important event has occurred.",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("systemPostNotifyOwner failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.SystemNotifyOwnerBody](../../models/components/systemnotifyownerbody.md)                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.PostNotifyOwnerSecurity](../../models/operations/postnotifyownersecurity.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.InlineResponse2001](../../models/components/inlineresponse2001.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401, 403    | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |