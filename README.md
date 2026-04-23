# mcp-hub-api-python

Developer-friendly, idiomatic Python SDK for the *mcp-hub-api-python* API.

<div align="left">
    <a href="https://www.scalar.com/?utm_source=mcp-hub-api-python&utm_campaign=python"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20scalar+speakeasy-212015?style=for-the-badge&logo=scalar&labelColor=252525" /></a>
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
* [cassie-marie-mcp-hub-api-python](#cassie-marie-mcp-hub-api-python)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with either *pip* or *poetry* package managers.

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install cassie-marie-mcp-hub-api-python
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add cassie-marie-mcp-hub-api-python
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from cassie-marie-mcp-hub-api-python python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "cassie-marie-mcp-hub-api-python",
# ]
# ///

from cassie_marie_mcp_hub_api_python import McpHubAPIPython

sdk = McpHubAPIPython(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asychronous requests by importing asyncio.
```python
# Asynchronous Example
import asyncio
from cassie_marie_mcp_hub_api_python import McpHubAPIPython

async def main():

    async with McpHubAPIPython() as mcp_hub_api_python:

        res = await mcp_hub_api_python.system.get_system_health_async(timestamp=6433.07)

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name                 | Type   | Scheme  |
| -------------------- | ------ | ------- |
| `app_session_cookie` | apiKey | API key |

To authenticate with the API the `app_session_cookie` parameter must be set when initializing the SDK client instance. For example:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython(
    app_session_cookie="<YOUR_API_KEY_HERE>",
) as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)

```

### Per-Operation Security Schemes

Some operations in this SDK require the security scheme to be specified at the request level. For example:
```python
import cassie_marie_mcp_hub_api_python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.post_notify_owner(security=cassie_marie_mcp_hub_api_python.PostNotifyOwnerSecurity(

    ), title="System Alert", content="An important event has occurred.")

    # Handle response
    print(res)

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [auth](docs/sdks/auth/README.md)

* [post_login](docs/sdks/auth/README.md#post_login) - User login with username and password
* [get_current_user](docs/sdks/auth/README.md#get_current_user) - Get current authenticated user
* [post_logout](docs/sdks/auth/README.md#post_logout) - Logout user and clear session cookie

### [capabilities](docs/sdks/capabilities/README.md)

* [list_capabilities](docs/sdks/capabilities/README.md#list_capabilities) - List capabilities of connected MCP servers

### [completions](docs/sdks/completions/README.md)

* [post_completion](docs/sdks/completions/README.md#post_completion) - Request a completion from an MCP server

### [connection_auth](docs/sdks/connectionauth/README.md)

* [get_connection_auth_status](docs/sdks/connectionauth/README.md#get_connection_auth_status) - Get auth status for a connection
* [start_connection_auth](docs/sdks/connectionauth/README.md#start_connection_auth) - Start auth flow for a connection

### [connections](docs/sdks/connections/README.md)

* [list_connections](docs/sdks/connections/README.md#list_connections) - List all MCP connections for the authenticated user
* [create_connection](docs/sdks/connections/README.md#create_connection) - Create and initialize a new MCP connection
* [get_connection_by_id](docs/sdks/connections/README.md#get_connection_by_id) - Get details and status of a specific MCP connection
* [delete_connection](docs/sdks/connections/README.md#delete_connection) - Disconnect and remove an MCP connection
* [ping_connection](docs/sdks/connections/README.md#ping_connection) - Send a ping to the MCP server via the connection

### [contexts](docs/sdks/contexts/README.md)

* [list_contexts](docs/sdks/contexts/README.md#list_contexts) - List available contexts from connected MCP servers
* [get_context_by_id](docs/sdks/contexts/README.md#get_context_by_id) - Get details of a specific context
* [list_models_in_context](docs/sdks/contexts/README.md#list_models_in_context) - List models available in a specific context

### [events](docs/sdks/events/README.md)

* [stream_events](docs/sdks/events/README.md#stream_events) - Stream live events and notifications (SSE or WebSocket)
* [get_request_details](docs/sdks/events/README.md#get_request_details) - Get details and history of a specific request

### [logging](docs/sdks/logging/README.md)

* [set_logging_level](docs/sdks/logging/README.md#set_logging_level) - Set logging level for MCP Hub runtime


### [prompts](docs/sdks/prompts/README.md)

* [list_prompts](docs/sdks/prompts/README.md#list_prompts) - List available prompts
* [get_prompt_by_id](docs/sdks/prompts/README.md#get_prompt_by_id) - Get details of a specific prompt

### [queries](docs/sdks/queries/README.md)

* [post_query](docs/sdks/queries/README.md#post_query) - Send a query or command to an MCP server

### [resources](docs/sdks/resources/README.md)

* [list_resources](docs/sdks/resources/README.md#list_resources) - List resources available from MCP servers
* [read_resource](docs/sdks/resources/README.md#read_resource) - Read a specific resource
* [list_resource_templates](docs/sdks/resources/README.md#list_resource_templates) - List resource templates
* [subscribe_resource](docs/sdks/resources/README.md#subscribe_resource) - Subscribe to resource updates
* [unsubscribe_resource](docs/sdks/resources/README.md#unsubscribe_resource) - Unsubscribe from resource updates

### [runtime](docs/sdks/runtime/README.md)

* [initialize_connection](docs/sdks/runtime/README.md#initialize_connection) - Initialize an existing MCP connection
* [get_connection_capabilities](docs/sdks/runtime/README.md#get_connection_capabilities) - Get negotiated capabilities for a connection
* [list_connection_tools](docs/sdks/runtime/README.md#list_connection_tools) - List tools for a connection
* [call_connection_tool](docs/sdks/runtime/README.md#call_connection_tool) - Call a tool on a connection
* [list_connection_resources](docs/sdks/runtime/README.md#list_connection_resources) - List resources for a connection
* [read_connection_resource](docs/sdks/runtime/README.md#read_connection_resource) - Read a resource by URI on a connection
* [list_connection_prompts](docs/sdks/runtime/README.md#list_connection_prompts) - List prompts for a connection
* [get_connection_prompt](docs/sdks/runtime/README.md#get_connection_prompt) - Get a rendered prompt from a connection
* [cancel_connection_request](docs/sdks/runtime/README.md#cancel_connection_request) - Cancel an in-flight request on a connection

### [servers](docs/sdks/servers/README.md)

* [list_mcp_servers](docs/sdks/servers/README.md#list_mcp_servers) - List available MCP servers
* [register_mcp_server](docs/sdks/servers/README.md#register_mcp_server) - Register a new MCP server (admin only)
* [get_mcp_server_by_id](docs/sdks/servers/README.md#get_mcp_server_by_id) - Get details of a specific MCP server

### [system](docs/sdks/system/README.md)

* [get_system_health](docs/sdks/system/README.md#get_system_health) - Health check endpoint
* [post_notify_owner](docs/sdks/system/README.md#post_notify_owner) - Notify owner (admin only)

### [tools](docs/sdks/tools/README.md)

* [list_tools](docs/sdks/tools/README.md#list_tools) - List available tools integrated within MCP Hub
* [get_tool_by_id](docs/sdks/tools/README.md#get_tool_by_id) - Get details of a specific tool

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
from cassie_marie_mcp_hub_api_python.utils import BackoffStrategy, RetryConfig


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07,
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    # Handle response
    print(res)

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
from cassie_marie_mcp_hub_api_python.utils import BackoffStrategy, RetryConfig


with McpHubAPIPython(
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
) as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or raise an exception.

By default, an API error will raise a models.APIError exception, which has the following properties:

| Property        | Type             | Description           |
|-----------------|------------------|-----------------------|
| `.status_code`  | *int*            | The HTTP status code  |
| `.message`      | *str*            | The error message     |
| `.raw_response` | *httpx.Response* | The raw HTTP response |
| `.body`         | *str*            | The response content  |

When custom error responses are specified for an operation, the SDK may also raise their associated exceptions. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `get_system_health_async` method may raise the following exceptions:

| Error Type      | Status Code | Content Type     |
| --------------- | ----------- | ---------------- |
| models.Error    | 400         | application/json |
| models.APIError | 4XX, 5XX    | \*/\*            |

### Example

```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython, models


with McpHubAPIPython() as mcp_hub_api_python:
    res = None
    try:

        res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

        # Handle response
        print(res)

    except models.Error as e:
        # handle e.data: models.ErrorData
        raise(e)
    except models.APIError as e:
        # handle exception
        raise(e)
```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally by passing a server index to the `server_idx: int` optional parameter when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                                                                     | Description                          |
| --- | -------------------------------------------------------------------------- | ------------------------------------ |
| 0   | `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0` | SwaggerHub API Auto Mocking          |
| 1   | `/api/`                                                                    | Base path prefix for all API routes. |

#### Example

```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython(
    server_idx=1,
) as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)

```

### Override Server URL Per-Client

The default server can also be overridden globally by passing a URL to the `server_url: str` optional parameter when initializing the SDK client instance. For example:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython(
    server_url="https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0",
) as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = McpHubAPIPython(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
from cassie_marie_mcp_hub_api_python.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = McpHubAPIPython(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `McpHubAPIPython` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
def main():

    with McpHubAPIPython() as mcp_hub_api_python:
        # Rest of application here...


# Or when using async:
async def amain():

    async with McpHubAPIPython() as mcp_hub_api_python:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from cassie_marie_mcp_hub_api_python import McpHubAPIPython
import logging

logging.basicConfig(level=logging.DEBUG)
s = McpHubAPIPython(debug_logger=logging.getLogger("cassie_marie_mcp_hub_api_python"))
```
<!-- End Debugging [debug] -->

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release.

### SDK Created by [Scalar](https://www.scalar.com/?utm_source=mcp-hub-api-python&utm_campaign=python)