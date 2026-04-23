# Completions
(*completions*)

## Overview

Completion requests

### Available Operations

* [postCompletion](#postcompletion) - Request a completion from an MCP server

## postCompletion

Request a completion from an MCP server

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.completions.postCompletion({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    serverId: "server-123",
    contextId: "context-456",
    modelId: "model-789",
    prompt: "Translate the following text to French:",
    parameters: {
      "maxTokens": 100,
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { completionsPostCompletion } from "@cassie-marie/mcp-hub-api-typescript/funcs/completionsPostCompletion.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await completionsPostCompletion(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    serverId: "server-123",
    contextId: "context-456",
    modelId: "model-789",
    prompt: "Translate the following text to French:",
    parameters: {
      "maxTokens": 100,
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("completionsPostCompletion failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.CompletionsBody](../../models/components/completionsbody.md)                                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.PostCompletionSecurity](../../models/operations/postcompletionsecurity.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.InlineResponse2007](../../models/components/inlineresponse2007.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401, 404    | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |