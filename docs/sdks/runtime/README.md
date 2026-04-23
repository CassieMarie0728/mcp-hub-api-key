# Runtime
(*runtime*)

## Overview

Per-connection MCP runtime operations such as initialize, tool invocation, and cancellation

### Available Operations

* [initializeConnection](#initializeconnection) - Initialize an existing MCP connection
* [getConnectionCapabilities](#getconnectioncapabilities) - Get negotiated capabilities for a connection
* [listConnectionTools](#listconnectiontools) - List tools for a connection
* [callConnectionTool](#callconnectiontool) - Call a tool on a connection
* [listConnectionResources](#listconnectionresources) - List resources for a connection
* [readConnectionResource](#readconnectionresource) - Read a resource by URI on a connection
* [listConnectionPrompts](#listconnectionprompts) - List prompts for a connection
* [getConnectionPrompt](#getconnectionprompt) - Get a rendered prompt from a connection
* [cancelConnectionRequest](#cancelconnectionrequest) - Cancel an in-flight request on a connection

## initializeConnection

Performs MCP initialize and initialized lifecycle calls for a created connection.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.initializeConnection({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    connectionInitializeBody: {
      clientName: "MCP Hub",
      clientVersion: "2.1.0",
      protocolVersion: "2025-06-18",
      clientCapabilities: {
        "roots": {
          "listChanged": true,
        },
        "sampling": {

        },
      },
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
import { runtimeInitializeConnection } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeInitializeConnection.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeInitializeConnection(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    connectionInitializeBody: {
      clientName: "MCP Hub",
      clientVersion: "2.1.0",
      protocolVersion: "2025-06-18",
      clientCapabilities: {
        "roots": {
          "listChanged": true,
        },
        "sampling": {
  
        },
      },
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeInitializeConnection failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.InitializeConnectionRequest](../../models/operations/initializeconnectionrequest.md)                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.InitializeConnectionSecurity](../../models/operations/initializeconnectionsecurity.md)                                                                             | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.ConnectionInitializeResponse](../../models/components/connectioninitializeresponse.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401, 404    | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## getConnectionCapabilities

Returns the current server and client capability view for a single connection.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.getConnectionCapabilities({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { runtimeGetConnectionCapabilities } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeGetConnectionCapabilities.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeGetConnectionCapabilities(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeGetConnectionCapabilities failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetConnectionCapabilitiesRequest](../../models/operations/getconnectioncapabilitiesrequest.md)                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetConnectionCapabilitiesSecurity](../../models/operations/getconnectioncapabilitiessecurity.md)                                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Capability](../../models/components/capability.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## listConnectionTools

Fetches the live tool list exposed by the connected MCP server.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.listConnectionTools({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { runtimeListConnectionTools } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeListConnectionTools.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeListConnectionTools(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeListConnectionTools failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListConnectionToolsRequest](../../models/operations/listconnectiontoolsrequest.md)                                                                                 | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.ListConnectionToolsSecurity](../../models/operations/listconnectiontoolssecurity.md)                                                                               | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Tool[]](../../models/.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## callConnectionTool

Invokes a named MCP tool against the target connection.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.callConnectionTool({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    toolName: "<value>",
    toolCallBody: {
      arguments: {
        "path": "/docs/readme.md",
      },
      requestId: "req-tool-001",
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
import { runtimeCallConnectionTool } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeCallConnectionTool.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeCallConnectionTool(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    toolName: "<value>",
    toolCallBody: {
      arguments: {
        "path": "/docs/readme.md",
      },
      requestId: "req-tool-001",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeCallConnectionTool failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CallConnectionToolRequest](../../models/operations/callconnectiontoolrequest.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CallConnectionToolSecurity](../../models/operations/callconnectiontoolsecurity.md)                                                                                 | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.ToolCallResult](../../models/components/toolcallresult.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401, 404    | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## listConnectionResources

Fetches the live resource list from the connected MCP server.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.listConnectionResources({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { runtimeListConnectionResources } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeListConnectionResources.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeListConnectionResources(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeListConnectionResources failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListConnectionResourcesRequest](../../models/operations/listconnectionresourcesrequest.md)                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.ListConnectionResourcesSecurity](../../models/operations/listconnectionresourcessecurity.md)                                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Resource[]](../../models/.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## readConnectionResource

Reads a live resource from the MCP server using its resource URI.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.readConnectionResource({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    resourceReadBody: {
      uri: "file:///workspace/notes/todo.md",
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
import { runtimeReadConnectionResource } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeReadConnectionResource.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeReadConnectionResource(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    resourceReadBody: {
      uri: "file:///workspace/notes/todo.md",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeReadConnectionResource failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ReadConnectionResourceRequest](../../models/operations/readconnectionresourcerequest.md)                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.ReadConnectionResourceSecurity](../../models/operations/readconnectionresourcesecurity.md)                                                                         | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[{ [k: string]: any }](../../models/.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401, 404    | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## listConnectionPrompts

Fetches prompt templates directly from the connected MCP server.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.listConnectionPrompts({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { runtimeListConnectionPrompts } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeListConnectionPrompts.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeListConnectionPrompts(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeListConnectionPrompts failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListConnectionPromptsRequest](../../models/operations/listconnectionpromptsrequest.md)                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.ListConnectionPromptsSecurity](../../models/operations/listconnectionpromptssecurity.md)                                                                           | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Prompt[]](../../models/.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## getConnectionPrompt

Retrieves a prompt template and applies optional prompt arguments.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.getConnectionPrompt({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    promptName: "<value>",
    promptGetBody: {
      arguments: {
        "targetLanguage": "fr",
      },
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
import { runtimeGetConnectionPrompt } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeGetConnectionPrompt.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeGetConnectionPrompt(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    promptName: "<value>",
    promptGetBody: {
      arguments: {
        "targetLanguage": "fr",
      },
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeGetConnectionPrompt failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetConnectionPromptRequest](../../models/operations/getconnectionpromptrequest.md)                                                                                 | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetConnectionPromptSecurity](../../models/operations/getconnectionpromptsecurity.md)                                                                               | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Prompt](../../models/components/prompt.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## cancelConnectionRequest

Requests cancellation for an active MCP request.

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.runtime.cancelConnectionRequest({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    cancelRequestBody: {
      requestId: "req-123abc",
      reason: "User navigated away",
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
import { runtimeCancelConnectionRequest } from "@cassie-marie/mcp-hub-api-typescript/funcs/runtimeCancelConnectionRequest.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await runtimeCancelConnectionRequest(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
    cancelRequestBody: {
      requestId: "req-123abc",
      reason: "User navigated away",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("runtimeCancelConnectionRequest failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CancelConnectionRequestRequest](../../models/operations/cancelconnectionrequestrequest.md)                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CancelConnectionRequestSecurity](../../models/operations/cancelconnectionrequestsecurity.md)                                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.InlineResponse202](../../models/components/inlineresponse202.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |