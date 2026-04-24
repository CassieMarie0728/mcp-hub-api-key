# mcp-hub-api-typescript

Developer-friendly, idiomatic Typescript SDK for the *mcp-hub-api-typescript* API.

<div align="left">
    <a href="https://www.scalar.com/?utm_source=mcp-hub-api-typescript&utm_campaign=typescript"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20scalar+speakeasy-212015?style=for-the-badge&logo=scalar&labelColor=252525" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>

<br />

## Summary

MCP Hub API: MCP Hub API provides a unified wrapper for discovering MCP servers, creating and managing connections, inspecting capabilities, invoking tools, reading resources, retrieving prompts, streaming events, and handling user/session authentication.

This contract is designed for both browser-based app sessions and programmatic clients, with support for cookie-based sessions and bearer-token authentication.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [@cassie-marie/mcp-hub-api-typescript](#cassie-mariemcp-hub-api-typescript)
  * [SDK Installation](#sdk-installation)
  * [Requirements](#requirements)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Standalone functions](#standalone-functions)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

The SDK can be installed with either [npm](https://www.npmjs.com/), [pnpm](https://pnpm.io/), [bun](https://bun.sh/) or [yarn](https://classic.yarnpkg.com/en/) package managers.

### NPM

```bash
npm add @cassie-marie/mcp-hub-api-typescript
```

### PNPM

```bash
pnpm add @cassie-marie/mcp-hub-api-typescript
```

### Bun

```bash
bun add @cassie-marie/mcp-hub-api-typescript
```

### Yarn

```bash
yarn add @cassie-marie/mcp-hub-api-typescript zod

# Note that Yarn does not install peer dependencies automatically. You will need
# to install zod as shown above.
```

> [!NOTE]
> This package is published with CommonJS and ES Modules (ESM) support.
<!-- End SDK Installation [installation] -->

<!-- Start Requirements [requirements] -->
## Requirements

For supported JavaScript runtimes, please consult [RUNTIMES.md](RUNTIMES.md).
<!-- End Requirements [requirements] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name               | Type   | Scheme  |
| ------------------ | ------ | ------- |
| `appSessionCookie` | apiKey | API key |

To authenticate with the API the `appSessionCookie` parameter must be set when initializing the SDK client instance. For example:
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript({
  appSessionCookie: "<YOUR_API_KEY_HERE>",
});

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();

```

### Per-Operation Security Schemes

Some operations in this SDK require the security scheme to be specified at the request level. For example:
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.system.postNotifyOwner({}, {
    title: "System Alert",
    content: "An important event has occurred.",
  });

  console.log(result);
}

run();

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [auth](docs/sdks/auth/README.md)

* [postLogin](docs/sdks/auth/README.md#postlogin) - User login with username and password
* [getCurrentUser](docs/sdks/auth/README.md#getcurrentuser) - Get current authenticated user
* [postLogout](docs/sdks/auth/README.md#postlogout) - Logout user and clear session cookie

### [capabilities](docs/sdks/capabilities/README.md)

* [listCapabilities](docs/sdks/capabilities/README.md#listcapabilities) - List capabilities of connected MCP servers

### [completions](docs/sdks/completions/README.md)

* [postCompletion](docs/sdks/completions/README.md#postcompletion) - Request a completion from an MCP server

### [connectionAuth](docs/sdks/connectionauth/README.md)

* [getConnectionAuthStatus](docs/sdks/connectionauth/README.md#getconnectionauthstatus) - Get auth status for a connection
* [startConnectionAuth](docs/sdks/connectionauth/README.md#startconnectionauth) - Start auth flow for a connection

### [connections](docs/sdks/connections/README.md)

* [listConnections](docs/sdks/connections/README.md#listconnections) - List all MCP connections for the authenticated user
* [createConnection](docs/sdks/connections/README.md#createconnection) - Create and initialize a new MCP connection
* [getConnectionById](docs/sdks/connections/README.md#getconnectionbyid) - Get details and status of a specific MCP connection
* [deleteConnection](docs/sdks/connections/README.md#deleteconnection) - Disconnect and remove an MCP connection
* [pingConnection](docs/sdks/connections/README.md#pingconnection) - Send a ping to the MCP server via the connection

### [contexts](docs/sdks/contexts/README.md)

* [listContexts](docs/sdks/contexts/README.md#listcontexts) - List available contexts from connected MCP servers
* [getContextById](docs/sdks/contexts/README.md#getcontextbyid) - Get details of a specific context
* [listModelsInContext](docs/sdks/contexts/README.md#listmodelsincontext) - List models available in a specific context

### [events](docs/sdks/events/README.md)

* [streamEvents](docs/sdks/events/README.md#streamevents) - Stream live events and notifications (SSE or WebSocket)
* [getRequestDetails](docs/sdks/events/README.md#getrequestdetails) - Get details and history of a specific request

### [logging](docs/sdks/logging/README.md)

* [setLoggingLevel](docs/sdks/logging/README.md#setlogginglevel) - Set logging level for MCP Hub runtime


### [prompts](docs/sdks/prompts/README.md)

* [listPrompts](docs/sdks/prompts/README.md#listprompts) - List available prompts
* [getPromptById](docs/sdks/prompts/README.md#getpromptbyid) - Get details of a specific prompt

### [queries](docs/sdks/queries/README.md)

* [postQuery](docs/sdks/queries/README.md#postquery) - Send a query or command to an MCP server

### [resources](docs/sdks/resources/README.md)

* [listResources](docs/sdks/resources/README.md#listresources) - List resources available from MCP servers
* [readResource](docs/sdks/resources/README.md#readresource) - Read a specific resource
* [listResourceTemplates](docs/sdks/resources/README.md#listresourcetemplates) - List resource templates
* [subscribeResource](docs/sdks/resources/README.md#subscriberesource) - Subscribe to resource updates
* [unsubscribeResource](docs/sdks/resources/README.md#unsubscriberesource) - Unsubscribe from resource updates

### [runtime](docs/sdks/runtime/README.md)

* [initializeConnection](docs/sdks/runtime/README.md#initializeconnection) - Initialize an existing MCP connection
* [getConnectionCapabilities](docs/sdks/runtime/README.md#getconnectioncapabilities) - Get negotiated capabilities for a connection
* [listConnectionTools](docs/sdks/runtime/README.md#listconnectiontools) - List tools for a connection
* [callConnectionTool](docs/sdks/runtime/README.md#callconnectiontool) - Call a tool on a connection
* [listConnectionResources](docs/sdks/runtime/README.md#listconnectionresources) - List resources for a connection
* [readConnectionResource](docs/sdks/runtime/README.md#readconnectionresource) - Read a resource by URI on a connection
* [listConnectionPrompts](docs/sdks/runtime/README.md#listconnectionprompts) - List prompts for a connection
* [getConnectionPrompt](docs/sdks/runtime/README.md#getconnectionprompt) - Get a rendered prompt from a connection
* [cancelConnectionRequest](docs/sdks/runtime/README.md#cancelconnectionrequest) - Cancel an in-flight request on a connection

### [servers](docs/sdks/servers/README.md)

* [listMcpServers](docs/sdks/servers/README.md#listmcpservers) - List available MCP servers
* [registerMcpServer](docs/sdks/servers/README.md#registermcpserver) - Register a new MCP server (admin only)
* [getMcpServerById](docs/sdks/servers/README.md#getmcpserverbyid) - Get details of a specific MCP server

### [system](docs/sdks/system/README.md)

* [getSystemHealth](docs/sdks/system/README.md#getsystemhealth) - Health check endpoint
* [postNotifyOwner](docs/sdks/system/README.md#postnotifyowner) - Notify owner (admin only)

### [tools](docs/sdks/tools/README.md)

* [listTools](docs/sdks/tools/README.md#listtools) - List available tools integrated within MCP Hub
* [getToolById](docs/sdks/tools/README.md#gettoolbyid) - Get details of a specific tool

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Standalone functions [standalone-funcs] -->
## Standalone functions

All the methods listed above are available as standalone functions. These
functions are ideal for use in applications running in the browser, serverless
runtimes or other environments where application bundle size is a primary
concern. When using a bundler to build your application, all unused
functionality will be either excluded from the final bundle or tree-shaken away.

To read more about standalone functions, check [FUNCTIONS.md](./FUNCTIONS.md).

<details>

<summary>Available standalone functions</summary>

- [`authGetCurrentUser`](docs/sdks/auth/README.md#getcurrentuser) - Get current authenticated user
- [`authPostLogin`](docs/sdks/auth/README.md#postlogin) - User login with username and password
- [`authPostLogout`](docs/sdks/auth/README.md#postlogout) - Logout user and clear session cookie
- [`capabilitiesListCapabilities`](docs/sdks/capabilities/README.md#listcapabilities) - List capabilities of connected MCP servers
- [`completionsPostCompletion`](docs/sdks/completions/README.md#postcompletion) - Request a completion from an MCP server
- [`connectionAuthGetConnectionAuthStatus`](docs/sdks/connectionauth/README.md#getconnectionauthstatus) - Get auth status for a connection
- [`connectionAuthStartConnectionAuth`](docs/sdks/connectionauth/README.md#startconnectionauth) - Start auth flow for a connection
- [`connectionsCreateConnection`](docs/sdks/connections/README.md#createconnection) - Create and initialize a new MCP connection
- [`connectionsDeleteConnection`](docs/sdks/connections/README.md#deleteconnection) - Disconnect and remove an MCP connection
- [`connectionsGetConnectionById`](docs/sdks/connections/README.md#getconnectionbyid) - Get details and status of a specific MCP connection
- [`connectionsListConnections`](docs/sdks/connections/README.md#listconnections) - List all MCP connections for the authenticated user
- [`connectionsPingConnection`](docs/sdks/connections/README.md#pingconnection) - Send a ping to the MCP server via the connection
- [`contextsGetContextById`](docs/sdks/contexts/README.md#getcontextbyid) - Get details of a specific context
- [`contextsListContexts`](docs/sdks/contexts/README.md#listcontexts) - List available contexts from connected MCP servers
- [`contextsListModelsInContext`](docs/sdks/contexts/README.md#listmodelsincontext) - List models available in a specific context
- [`eventsGetRequestDetails`](docs/sdks/events/README.md#getrequestdetails) - Get details and history of a specific request
- [`eventsStreamEvents`](docs/sdks/events/README.md#streamevents) - Stream live events and notifications (SSE or WebSocket)
- [`loggingSetLoggingLevel`](docs/sdks/logging/README.md#setlogginglevel) - Set logging level for MCP Hub runtime
- [`promptsGetPromptById`](docs/sdks/prompts/README.md#getpromptbyid) - Get details of a specific prompt
- [`promptsListPrompts`](docs/sdks/prompts/README.md#listprompts) - List available prompts
- [`queriesPostQuery`](docs/sdks/queries/README.md#postquery) - Send a query or command to an MCP server
- [`resourcesListResources`](docs/sdks/resources/README.md#listresources) - List resources available from MCP servers
- [`resourcesListResourceTemplates`](docs/sdks/resources/README.md#listresourcetemplates) - List resource templates
- [`resourcesReadResource`](docs/sdks/resources/README.md#readresource) - Read a specific resource
- [`resourcesSubscribeResource`](docs/sdks/resources/README.md#subscriberesource) - Subscribe to resource updates
- [`resourcesUnsubscribeResource`](docs/sdks/resources/README.md#unsubscriberesource) - Unsubscribe from resource updates
- [`runtimeCallConnectionTool`](docs/sdks/runtime/README.md#callconnectiontool) - Call a tool on a connection
- [`runtimeCancelConnectionRequest`](docs/sdks/runtime/README.md#cancelconnectionrequest) - Cancel an in-flight request on a connection
- [`runtimeGetConnectionCapabilities`](docs/sdks/runtime/README.md#getconnectioncapabilities) - Get negotiated capabilities for a connection
- [`runtimeGetConnectionPrompt`](docs/sdks/runtime/README.md#getconnectionprompt) - Get a rendered prompt from a connection
- [`runtimeInitializeConnection`](docs/sdks/runtime/README.md#initializeconnection) - Initialize an existing MCP connection
- [`runtimeListConnectionPrompts`](docs/sdks/runtime/README.md#listconnectionprompts) - List prompts for a connection
- [`runtimeListConnectionResources`](docs/sdks/runtime/README.md#listconnectionresources) - List resources for a connection
- [`runtimeListConnectionTools`](docs/sdks/runtime/README.md#listconnectiontools) - List tools for a connection
- [`runtimeReadConnectionResource`](docs/sdks/runtime/README.md#readconnectionresource) - Read a resource by URI on a connection
- [`serversGetMcpServerById`](docs/sdks/servers/README.md#getmcpserverbyid) - Get details of a specific MCP server
- [`serversListMcpServers`](docs/sdks/servers/README.md#listmcpservers) - List available MCP servers
- [`serversRegisterMcpServer`](docs/sdks/servers/README.md#registermcpserver) - Register a new MCP server (admin only)
- [`systemGetSystemHealth`](docs/sdks/system/README.md#getsystemhealth) - Health check endpoint
- [`systemPostNotifyOwner`](docs/sdks/system/README.md#postnotifyowner) - Notify owner (admin only)
- [`toolsGetToolById`](docs/sdks/tools/README.md#gettoolbyid) - Get details of a specific tool
- [`toolsListTools`](docs/sdks/tools/README.md#listtools) - List available tools integrated within MCP Hub

</details>
<!-- End Standalone functions [standalone-funcs] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries.  If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API.  However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a retryConfig object to the call:
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  }, {
    retries: {
      strategy: "backoff",
      backoff: {
        initialInterval: 1,
        maxInterval: 50,
        exponent: 1.1,
        maxElapsedTime: 100,
      },
      retryConnectionErrors: false,
    },
  });

  console.log(result);
}

run();

```

If you'd like to override the default retry strategy for all operations that support retries, you can provide a retryConfig at SDK initialization:
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript({
  retryConfig: {
    strategy: "backoff",
    backoff: {
      initialInterval: 1,
      maxInterval: 50,
      exponent: 1.1,
      maxElapsedTime: 100,
    },
    retryConnectionErrors: false,
  },
});

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`McpHubAPITypescriptError`](./src/models/errors/mcphubapitypescripterror.ts) is the base class for all HTTP error responses. It has the following properties:

| Property            | Type       | Description                                                                             |
| ------------------- | ---------- | --------------------------------------------------------------------------------------- |
| `error.message`     | `string`   | Error message                                                                           |
| `error.statusCode`  | `number`   | HTTP response status code eg `404`                                                      |
| `error.headers`     | `Headers`  | HTTP response headers                                                                   |
| `error.body`        | `string`   | HTTP body. Can be empty string if no body is returned.                                  |
| `error.rawResponse` | `Response` | Raw HTTP response                                                                       |
| `error.data$`       |            | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";
import * as errors from "@cassie-marie/mcp-hub-api-typescript/models/errors";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  try {
    const result = await mcpHubApiTypescript.system.getSystemHealth({
      timestamp: 6433.07,
    });

    console.log(result);
  } catch (error) {
    // The base class for HTTP error responses
    if (error instanceof errors.McpHubAPITypescriptError) {
      console.log(error.message);
      console.log(error.statusCode);
      console.log(error.body);
      console.log(error.headers);

      // Depending on the method different errors may be thrown
      if (error instanceof errors.ErrorT) {
        console.log(error.data$.status); // number
        console.log(error.data$.message); // string
      }
    }
  }
}

run();

```

### Error Classes
**Primary errors:**
* [`McpHubAPITypescriptError`](./src/models/errors/mcphubapitypescripterror.ts): The base class for HTTP error responses.
  * [`ErrorT`](docs/models/errors/errort.md): Standard error response.

<details><summary>Less common errors (6)</summary>

<br />

**Network errors:**
* [`ConnectionError`](./src/models/errors/httpclienterrors.ts): HTTP client was unable to make a request to a server.
* [`RequestTimeoutError`](./src/models/errors/httpclienterrors.ts): HTTP request timed out due to an AbortSignal signal.
* [`RequestAbortedError`](./src/models/errors/httpclienterrors.ts): HTTP request was aborted by the client.
* [`InvalidRequestError`](./src/models/errors/httpclienterrors.ts): Any input used to create a request is invalid.
* [`UnexpectedClientError`](./src/models/errors/httpclienterrors.ts): Unrecognised or unexpected error.


**Inherit from [`McpHubAPITypescriptError`](./src/models/errors/mcphubapitypescripterror.ts)**:
* [`ResponseValidationError`](./src/models/errors/responsevalidationerror.ts): Type mismatch between the data returned from the server and the structure expected by the SDK. See `error.rawValue` for the raw value and `error.pretty()` for a nicely formatted multi-line string.

</details>
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally by passing a server index to the `serverIdx: number` optional parameter when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                                                                     | Description                          |
| --- | -------------------------------------------------------------------------- | ------------------------------------ |
| 0   | `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0` | SwaggerHub API Auto Mocking          |
| 1   | `/api/`                                                                    | Base path prefix for all API routes. |

#### Example

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript({
  serverIdx: 1,
});

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();

```

### Override Server URL Per-Client

The default server can also be overridden globally by passing a URL to the `serverURL: string` optional parameter when initializing the SDK client instance. For example:
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript({
  serverURL:
    "https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0",
});

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The TypeScript SDK makes API calls using an `HTTPClient` that wraps the native
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). This
client is a thin wrapper around `fetch` and provides the ability to attach hooks
around the request lifecycle that can be used to modify the request or handle
errors and response.

The `HTTPClient` constructor takes an optional `fetcher` argument that can be
used to integrate a third-party HTTP client or when writing tests to mock out
the HTTP client and feed in fixtures.

The following example shows how to use the `"beforeRequest"` hook to to add a
custom header and a timeout to requests and how to use the `"requestError"` hook
to log errors:

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";
import { HTTPClient } from "@cassie-marie/mcp-hub-api-typescript/lib/http";

const httpClient = new HTTPClient({
  // fetcher takes a function that has the same signature as native `fetch`.
  fetcher: (request) => {
    return fetch(request);
  }
});

httpClient.addHook("beforeRequest", (request) => {
  const nextRequest = new Request(request, {
    signal: request.signal || AbortSignal.timeout(5000)
  });

  nextRequest.headers.set("x-custom-header", "custom value");

  return nextRequest;
});

httpClient.addHook("requestError", (error, request) => {
  console.group("Request Error");
  console.log("Reason:", `${error}`);
  console.log("Endpoint:", `${request.method} ${request.url}`);
  console.groupEnd();
});

const sdk = new McpHubApiTypescript({ httpClient });
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass a logger that matches `console`'s interface as an SDK option.

> [!WARNING]
> Beware that debug logging will reveal secrets, like API tokens in headers, in log messages printed to a console or files. It's recommended to use this feature only during local development and not in production.

```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const sdk = new McpHubApiTypescript({ debugLogger: console });
```
<!-- End Debugging [debug] -->

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release.

### SDK Created by [Scalar](https://www.scalar.com/?utm_source=mcp-hub-api-typescript&utm_campaign=typescript)