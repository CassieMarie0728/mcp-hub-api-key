# Connections
(*connections*)

## Overview

MCP connection lifecycle management

### Available Operations

* [listConnections](#listconnections) - List all MCP connections for the authenticated user
* [createConnection](#createconnection) - Create and initialize a new MCP connection
* [getConnectionById](#getconnectionbyid) - Get details and status of a specific MCP connection
* [deleteConnection](#deleteconnection) - Disconnect and remove an MCP connection
* [pingConnection](#pingconnection) - Send a ping to the MCP server via the connection

## listConnections

List all MCP connections for the authenticated user

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.connections.listConnections({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { connectionsListConnections } from "@cassie-marie/mcp-hub-api-typescript/funcs/connectionsListConnections.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await connectionsListConnections(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("connectionsListConnections failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                                                                                     | [operations.ListConnectionsSecurity](../../models/operations/listconnectionssecurity.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Connection[]](../../models/.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401              | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## createConnection

Create and initialize a new MCP connection

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.connections.createConnection({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    serverId: "server-123",
    transport: "stdio",
    options: {
      command: "/usr/local/bin/mcp-server",
      args: [
        "--stdio",
      ],
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
import { connectionsCreateConnection } from "@cassie-marie/mcp-hub-api-typescript/funcs/connectionsCreateConnection.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await connectionsCreateConnection(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    serverId: "server-123",
    transport: "stdio",
    options: {
      command: "/usr/local/bin/mcp-server",
      args: [
        "--stdio",
      ],
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("connectionsCreateConnection failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [components.ConnectionsBody](../../models/components/connectionsbody.md)                                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.CreateConnectionSecurity](../../models/operations/createconnectionsecurity.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Connection](../../models/components/connection.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 400, 401         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## getConnectionById

Get details and status of a specific MCP connection

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.connections.getConnectionById({
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
import { connectionsGetConnectionById } from "@cassie-marie/mcp-hub-api-typescript/funcs/connectionsGetConnectionById.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await connectionsGetConnectionById(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("connectionsGetConnectionById failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetConnectionByIdRequest](../../models/operations/getconnectionbyidrequest.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.GetConnectionByIdSecurity](../../models/operations/getconnectionbyidsecurity.md)                                                                                   | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.Connection](../../models/components/connection.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## deleteConnection

Disconnect and remove an MCP connection

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  await mcpHubApiTypescript.connections.deleteConnection({
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });


}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { McpHubApiTypescriptCore } from "@cassie-marie/mcp-hub-api-typescript/core.js";
import { connectionsDeleteConnection } from "@cassie-marie/mcp-hub-api-typescript/funcs/connectionsDeleteConnection.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await connectionsDeleteConnection(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    
  } else {
    console.log("connectionsDeleteConnection failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.DeleteConnectionRequest](../../models/operations/deleteconnectionrequest.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.DeleteConnectionSecurity](../../models/operations/deleteconnectionsecurity.md)                                                                                     | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<void\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |

## pingConnection

Send a ping to the MCP server via the connection

### Example Usage

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.connections.pingConnection({
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
import { connectionsPingConnection } from "@cassie-marie/mcp-hub-api-typescript/funcs/connectionsPingConnection.js";

// Use `McpHubApiTypescriptCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const mcpHubApiTypescript = new McpHubApiTypescriptCore();

async function run() {
  const res = await connectionsPingConnection(mcpHubApiTypescript, {
    appSessionCookie: "<YOUR_API_KEY_HERE>",
  }, {
    connectionId: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("connectionsPingConnection failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.PingConnectionRequest](../../models/operations/pingconnectionrequest.md)                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `security`                                                                                                                                                                     | [operations.PingConnectionSecurity](../../models/operations/pingconnectionsecurity.md)                                                                                         | :heavy_check_mark:                                                                                                                                                             | The security requirements to use for the request.                                                                                                                              |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[components.InlineResponse2004](../../models/components/inlineresponse2004.md)\>**

### Errors

| Error Type       | Status Code      | Content Type     |
| ---------------- | ---------------- | ---------------- |
| errors.ErrorT    | 401, 404         | application/json |
| errors.APIError  | 4XX, 5XX         | \*/\*            |