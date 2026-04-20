# MCP Hub API Documentation

## Overview

The MCP Hub API provides a unified interface for discovering MCP servers, managing connections, inspecting server capabilities, invoking tools, reading resources, retrieving prompts, and handling user/session authentication. This API is designed to be used by both browser-based applications and programmatic clients, supporting both cookie-based sessions and bearer-token authentication.

### API Information

- **Title**: MCP Hub API
- **Version**: 2.0.0
- **Terms of Service**: [MCP Hub Terms of Service](https://cassiemarie0728.github.io/policies/mcp-hub-terms-of-service/)
- **Contact Information**:
  - **Name**: MCP Hub Support
  - **Email**: cmcrossno@gmail.com
  - **URL**: [GitHub Profile](https://github.com/cassiemarie0728)
- **License**: [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

### Servers

| Description                  | URL                                                                  |
|------------------------------|----------------------------------------------------------------------|
| SwaggerHub API Auto Mocking  | `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0` |
| Base path for all API routes | `/api/`                                                             |

## Tags

The API is organized into the following categories (tags):

- **system**: System-related endpoints.
- **auth**: Authentication and user session management.
- **servers**: MCP server discovery and management.
- **contexts**: MCP server contexts and models management.
- **queries**: Sending queries and commands to MCP servers.
- **tools**: Access to related tools integrated within MCP Hub.
- **connections**: MCP connection lifecycle management.
- **capabilities**: Capability and server metadata inspection.
- **resources**: Resource management and subscription.
- **prompts**: Prompt listing and retrieval.
- **completions**: Completion requests.
- **logging**: Logging level management.
- **events**: Event streaming and request inspection.
- **runtime**: Per-connection MCP runtime operations (e.g., initialization, tool invocation, and cancellation).
- **connectionAuth**: Per-connection authentication bootstrap and status.

## Paths

### System Endpoints

#### Check System Health
- **GET** `/system/health`
  - **Summary**: Checks the health status of the system.
  - **Parameters**:
    - **timestamp** (query, required): Time for the health check, must be a non-negative number.
  - **Responses**:
    - **200**: Health check response. Returns a successful response.
    - **400**: Invalid timestamp parameter.

#### Notify Owner
- **POST** `/system/notifyOwner`
  - **Summary**: Notifies the owner (admin only).
  - **Request Body**:
    - **title** (string, required): Notification title.
    - **content** (string, required): Notification content.
  - **Responses**:
    - **200**: Notification sent successfully.
    - **400**: Invalid request body.
    - **401**: Unauthorized – authentication required.
    - **403**: Forbidden – admin role required.

### Authentication Endpoints

#### User Login
- **POST** `/auth/login`
  - **Summary**: Authenticates a user with username and password.
  - **Request Body**:
    - **username** (string, required): Username or email.
    - **password** (string, required): User password.
  - **Responses**:
    - **200**: Successful login returns authentication token and user info.
    - **400**: Invalid login credentials.
    - **401**: Unauthorized – invalid credentials.

#### Get Current User
- **GET** `/auth/me`
  - **Summary**: Fetches the current authenticated user information.
  - **Responses**:
    - **200**: Current user information or null if not authenticated.
    - **401**: Unauthorized – authentication required.

#### User Logout
- **POST** `/auth/logout`
  - **Summary**: Logs out the user and clears the session cookie.
  - **Responses**:
    - **200**: Logout successful.
    - **401**: Unauthorized – authentication required.

### Server Management Endpoints

#### List Available MCP Servers
- **GET** `/servers`
  - **Summary**: Returns MCP servers that the current user can browse or connect to.
  - **Parameters**: 
    - **region** (query, optional): Filter by server region.
    - **status** (query, optional): Filter by server status (online/offline).
  - **Responses**:
    - **200**: List of MCP servers.
    - **401**: Unauthorized – authentication required.

#### Register a New MCP Server
- **POST** `/servers`
  - **Summary**: Registers a new MCP server (admin only).
  - **Request Body**:
    - **name** (string, required): Server display name.
    - **url** (string, required): Base URL of the MCP server.
    - **description** (string, optional): Server description.
  - **Responses**:
    - **201**: MCP server registered successfully.
    - **400**: Invalid request body.
    - **401**: Unauthorized – authentication required.
    - **403**: Forbidden – admin role required.

### Connection Management Endpoints

#### List Connections
- **GET** `/connections`
  - **Summary**: Lists all MCP connections for the authenticated user.
  - **Responses**:
    - **200**: List of MCP connections.
    - **401**: Unauthorized – authentication required.

#### Create Connection
- **POST** `/connections`
  - **Summary**: Creates and initializes a new MCP connection.
  - **Request Body**:
    - **serverId** (string, required): MCP server ID to connect to.
    - **transport** (string, required): Transport type (stdio/streamable-http).
    - **options** (object, optional): Transport-specific options.
  - **Responses**:
    - **201**: Connection created successfully.
    - **400**: Invalid request body or initialization failure.
    - **401**: Unauthorized – authentication required.

#### Get Connection Status
- **GET** `/connections/{connectionId}`
  - **Summary**: Fetches details of a specific MCP connection.
  - **Parameters**:
    - **connectionId** (path, required): Unique identifier of the connection.
  - **Responses**:
    - **200**: Connection details.
    - **401**: Unauthorized – authentication required.
    - **404**: Connection not found.

### Additional Functionality
The API includes endpoints for querying, tools management, resources management, event streaming, capabilities management, and the handling of prompts and completions. Each endpoint is detailed with a full request and response structure, along with the parameters required.

For the complete list of endpoints and their documentation, please refer to the API specification provided above.

---

This documentation should give a robust overview of the MCP Hub API and help in understanding its endpoints and how to interact with them effectively.

---
*Documentation generated by* **[AutoCodeDocs.ai](https://autocodedocs.ai)**