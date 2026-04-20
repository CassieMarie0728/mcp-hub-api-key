# MCP Hub API Documentation

## Overview

The **MCP Hub API** provides a unified wrapper for discovering MCP servers, managing connections, inspecting server capabilities, invoking tools, reading resources, retrieving prompts, streaming events, and handling user and session authentication. This API supports both browser-based applications and programmatic clients, with mechanisms for cookie-based sessions and bearer-token authentication.

### API Information
- **Title**: MCP Hub API
- **Version**: 2.0.0
- **Description**: A comprehensive set of endpoints for managing MCP operations.
- **Terms of Service**: [Terms of Service](https://cassiemarie0728.github.io/policies/mcp-hub-terms-of-service/)
- **Contact**: 
  - **Support Name**: MCP Hub Support
  - **Contact URL**: [Support](https://github.com/cassiemarie0728)
  - **Email**: cmcrossno@gmail.com
- **License**: Apache License, Version 2.0 ([License URL](https://www.apache.org/licenses/LICENSE-2.0))

### Servers
The API is accessible via the following servers:
1. **SwaggerHub API Auto Mocking**
   - URL: `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0`
2. **Base Path Prefix for API Routes**
   - URL: `/api/`

## API Tags
The API is organized into the following tags:
- **System**: System-related endpoints.
- **Auth**: Authentication and session management.
- **Servers**: Managing MCP servers.
- **Contexts**: Managing contexts and models.
- **Queries**: Sending queries to MCP servers.
- **Tools**: Accessing integrated tools.
- **Connections**: Managing incoming and outgoing connections.
- **Capabilities**: Inspecting server metadata.
- **Resources**: Managing resources.
- **Prompts**: Retrieving prompts.
- **Completions**: Generating completions based on prompts.
- **Logging**: Managing logging levels.
- **Events**: Streaming events.
- **Runtime**: Operations related to the MCP runtime.
- **ConnectionAuth**: Authentication management for connections.

## API Endpoints

### System Endpoints
#### Health Check
**GET** `/system/health`
- **Summary**: Retrieve health status of the system.
- **Parameters**: 
  - `timestamp`: A non-negative number representing the time of check.
- **Responses**:
  - `200`: Health check successful.
  - `400`: Invalid timestamp parameter.

#### Notify Owner
**POST** `/system/notifyOwner`
- **Summary**: Notify the owner via a message.
- **Request Body**: Contains `title` and `content`.
- **Responses**:
  - `200`: Notification sent.
  - `400`: Invalid request body.
  - `401`: Authentication required.
  - `403`: Admin role required.

### Authentication Endpoints
#### User Login
**POST** `/auth/login`
- **Summary**: Logs in a user and returns a session token.
- **Request Body**: Contains `username` and `password`.
- **Responses**:
  - `200`: Successful login with token.
  - `400`: Invalid credentials.
  - `401`: Unauthorized.

#### Get Current User
**GET** `/auth/me`
- **Summary**: Retrieves current authenticated user info.
- **Responses**:
  - `200`: User info or null if not authenticated.
  - `401`: Authentication required.

#### User Logout
**POST** `/auth/logout`
- **Summary**: Logs out the user and clears their session.
- **Responses**:
  - `200`: Logout successful.
  - `401`: Authentication required.

### MCP Server Endpoints
#### List Available Servers
**GET** `/servers`
- **Summary**: Lists available MCP servers.
- **Parameters** (optional):
  - `region`: Filter by region.
  - `status`: Filter by status (e.g., online, offline).
- **Responses**:
  - `200`: List of servers.
  - `401`: Authentication required.

#### Register a New MCP Server
**POST** `/servers`
- **Summary**: Registers a new MCP server (admin only).
- **Request Body**: Contains `name`, `url`, and optional `description`.
- **Responses**:
  - `201`: Server registered.
  - `400`: Invalid request body.
  - `401`: Authentication required.
  - `403`: Admin role required.

#### Get Server Details
**GET** `/servers/{serverId}`
- **Summary**: Retrieves details of a specific MCP server.
- **Parameters**:
  - `serverId`: Unique identifier for the server.
- **Responses**:
  - `200`: Server details.
  - `404`: Server not found.

### Connection Management Endpoints
#### List Connections
**GET** `/connections`
- **Summary**: Lists all MCP connections for the authenticated user.
- **Responses**:
  - `200`: List of connections.
  - `401`: Authentication required.

#### Create a New Connection
**POST** `/connections`
- **Summary**: Creates and initializes a new MCP connection.
- **Request Body**: Contains `serverId` and `transport` options.
- **Responses**:
  - `201`: Connection created.
  - `400`: Invalid request.
  - `401`: Authentication required.

#### Get Connection Details
**GET** `/connections/{connectionId}`
- **Summary**: Retrieves details of a specific connection.
- **Parameters**:
  - `connectionId`: Unique identifier for the connection.
- **Responses**:
  - `200`: Connection details.
  - `401`: Authentication required.
  - `404`: Connection not found.

#### Disconnect a Connection
**DELETE** `/connections/{connectionId}`
- **Summary**: Disconnects and removes an MCP connection.
- **Parameters**:
  - `connectionId`: Unique identifier for the connection.
- **Responses**:
  - `204`: Connection deleted successfully.
  - `401`: Authentication required.
  - `404`: Connection not found.

### Resource Management Endpoints
#### List Resources
**GET** `/resources`
- **Summary**: Lists resources available from MCP servers.
- **Parameters** (optional):
  - `serverId`: Filter by MCP server ID.
- **Responses**:
  - `200`: List of resources.
  - `401`: Authentication required.

#### Read Resource
**GET** `/resources/{resourceId}`
- **Summary**: Reads a specific resource.
- **Parameters**:
  - `resourceId`: Unique identifier for the resource.
- **Responses**:
  - `200`: Resource content.
  - `401`: Authentication required.
  - `404`: Resource not found.

#### Subscribe to Resource
**POST** `/resources/{resourceId}/subscribe`
- **Summary**: Subscribes to updates for a resource.
- **Parameters**:
  - `resourceId`: Unique identifier for the resource.
- **Responses**:
  - `200`: Subscription successful.
  - `401`: Authentication required.
  - `404`: Resource not found.

### Tools Management Endpoints
#### List Available Tools
**GET** `/tools`
- **Summary**: Lists integrated tools within MCP Hub.
- **Responses**:
  - `200`: List of tools.
  - `401`: Authentication required.

#### Get Tool Details
**GET** `/tools/{toolId}`
- **Summary**: Retrieves details of a specific tool.
- **Parameters**:
  - `toolId`: Unique identifier for the tool.
- **Responses**:
  - `200`: Tool details.
  - `401`: Authentication required.
  - `404`: Tool not found.

### Event Streaming Endpoints
#### Stream Events
**GET** `/events/stream`
- **Summary**: Streams live events and notifications.
- **Responses**:
  - `200`: Event stream established.
  - `401`: Authentication required.

### Error Handling
Errors are conveyed using a standard structure:
- **Error Object**:
  - `status`: HTTP status code.
  - `message`: Description of the error.

This documentation provides a comprehensive overview of the MCP Hub API and its functionalities, relevant structures, request/response formats, and error handling specifics. The API is designed to facilitate ease of access and comprehensive management of resources, tools, and connections within the MCP Hub ecosystem.

---
*Documentation generated by* **[AutoCodeDocs.ai](https://autocodedocs.ai)**