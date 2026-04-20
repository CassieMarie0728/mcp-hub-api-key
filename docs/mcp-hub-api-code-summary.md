# MCP Hub API Documentation

## Overview
The **MCP Hub API** is designed to facilitate interactions with MCP servers through a unified interface that enables discovering servers, managing connections, inspecting capabilities, handling user authentication, and invoking tools. The API is structured to support both browser-based applications and programmatic clients, offering authentication via cookies and bearer tokens.

### API Version
- **Version**: 2.0.0

### License
- **License Type**: Apache License, Version 2.0
- **URL**: [Apache License](https://www.apache.org/licenses/LICENSE-2.0)

### Contact Information
- **Support Name**: MCP Hub Support
- **Contact URL**: [MCP Hub Support GitHub](https://github.com/cassiemarie0728)
- **Email**: cmcrossno@gmail.com

### Terms of Service
- [Terms of Service](https://cassiemarie0728.github.io/policies/mcp-hub-terms-of-service/)

## Servers
### Available Endpoints
- SwaggerHub Autos Mocking: `https://virtserver.swaggerhub.com/cassiemarieauthor/MCPHUB_API_KEY/2.0.0`
- Base path for all API routes: `/api/`

## API Tags
The API is organized into the following functional areas:

- **system**: Endpoints related to system health and notifications.
- **auth**: Authentication and user session management.
- **servers**: CRUD operations for MCP server discovery and management.
- **contexts**: Management of contexts and models within MCP servers.
- **queries**: Interacting with MCP servers via queries and commands.
- **tools**: Access to various tools integrated within the MCP Hub.
- **connections**: Lifecycle management and details of MCP connections.
- **capabilities**: Inspection of capabilities and metadata of servers.
- **resources**: Management and retrieval of resources.
- **prompts**: Listing and retrieval of prompt templates.
- **completions**: Handling completion requests.
- **logging**: Management of logging levels.
- **events**: Streaming of live events and notifications.
- **runtime**: Per-connection runtime operations.
- **connectionAuth**: Authentication within individual MCP server connections.

## API Endpoints

### System Endpoints

#### Health Check
- **Endpoint**: `/system/health`
- **Method**: `GET`
- **Description**: Health check endpoint for evaluating the API's operational status.
- **Parameters**:
  - `timestamp`: (required) A non-negative number indicating the time of the health check.
- **Responses**:
  - `200`: Health check response.
  - `400`: Invalid timestamp parameter.

#### Notify Owner
- **Endpoint**: `/system/notifyOwner`
- **Method**: `POST`
- **Description**: Notifies the owner about important events (admin only).
- **Request Body**: 
  - `title`: Title for the notification.
  - `content`: Content of the notification.
- **Responses**:
  - `200`: Notification sent successfully.
  - `400`: Invalid request body.
  - `401`: Unauthorized - authentication required.
  - `403`: Forbidden - admin role required.

### Authentication Endpoints

#### User Login
- **Endpoint**: `/auth/login`
- **Method**: `POST`
- **Description**: Authenticates a user using credentials and initiates a session.
- **Request Body**: 
  - `username`: User’s username or email (required).
  - `password`: User’s password (required).
- **Responses**:
  - `200`: Authentication token and user info returned.
  - `400`: Invalid credentials.
  - `401`: Unauthorized - invalid credentials.

#### Get Current User
- **Endpoint**: `/auth/me`
- **Method**: `GET`
- **Description**: Fetches information about the currently authenticated user.
- **Responses**:
  - `200`: Returns current user information or null if not authenticated.
  - `401`: Unauthorized - authentication required.

#### Logout
- **Endpoint**: `/auth/logout`
- **Method**: `POST`
- **Description**: Logs out the current user and clears the session cookie.
- **Responses**:
  - `200`: Logout successful.
  - `401`: Unauthorized - authentication required.

### Server Management Endpoints

#### List Available MCP Servers
- **Endpoint**: `/servers`
- **Method**: `GET`
- **Description**: Lists all available MCP servers.
- **Parameters**:
  - `region`: (optional) Filter servers by region.
  - `status`: (optional) Filter servers by status (online/offline).
- **Responses**:
  - `200`: List of MCP servers.
  - `401`: Unauthorized - authentication required.

#### Register a New MCP Server
- **Endpoint**: `/servers`
- **Method**: `POST`
- **Description**: Registers a new MCP server (admin only).
- **Request Body**:
  - `name`: Display name of the server (required).
  - `url`: Base URL of the server (required).
  - `description`: Optional server description.
- **Responses**:
  - `201`: MCP server registered successfully.
  - `400`: Invalid request body.
  - `401`: Unauthorized - authentication required.
  - `403`: Forbidden - admin role required.

#### Get MCP Server Details
- **Endpoint**: `/servers/{serverId}`
- **Method**: `GET`
- **Description**: Retrieves details for a specific MCP server.
- **Parameters**:
  - `serverId`: Unique identifier of the server (required).
- **Responses**:
  - `200`: MCP server details.
  - `404`: MCP server not found.

### Connection Management Endpoints

#### List Connections
- **Endpoint**: `/connections`
- **Method**: `GET`
- **Description**: Lists all MCP connections for the authenticated user.
- **Responses**:
  - `200`: List of MCP connections.
  - `401`: Unauthorized - authentication required.

#### Create Connection
- **Endpoint**: `/connections`
- **Method**: `POST`
- **Description**: Creates and initializes a new MCP connection.
- **Request Body**:
  - `serverId`: MCP server ID to connect to (required).
  - `transport`: Type of transport to use (required).
  - `options`: Transport-specific options.
- **Responses**:
  - `201`: Connection created and initialized.
  - `400`: Invalid request body or initialization failure.
  - `401`: Unauthorized - authentication required.

#### Get Connection Details
- **Endpoint**: `/connections/{connectionId}`
- **Method**: `GET`
- **Description**: Gets the details and status of a specific MCP connection.
- **Parameters**:
  - `connectionId`: Unique identifier of the connection (required).
- **Responses**:
  - `200`: Connection details.
  - `401`: Unauthorized - authentication required.
  - `404`: Connection not found.

### Resource Management Endpoints

#### List Resources
- **Endpoint**: `/resources`
- **Method**: `GET`
- **Description**: Lists resources available from connected MCP servers.
- **Parameters**:
  - `serverId`: (optional) Filter resources by MCP server ID.
- **Responses**:
  - `200`: List of resources.
  - `401`: Unauthorized - authentication required.

#### Subscribe to Resource Updates
- **Endpoint**: `/resources/{resourceId}/subscribe`
- **Method**: `POST`
- **Description**: Subscribes to updates for a specific resource.
- **Parameters**:
  - `resourceId`: Unique identifier of the resource (required).
- **Responses**:
  - `200`: Subscription successful.
  - `401`: Unauthorized - authentication required.
  - `404`: Resource not found.

### Event Streaming Endpoints

#### Stream Events
- **Endpoint**: `/events/stream`
- **Method**: `GET`
- **Description**: Streams live events and notifications.
- **Responses**:
  - `200`: Event stream established.
  - `401`: Unauthorized - authentication required.

### Completion Request Endpoints

#### Request a Completion
- **Endpoint**: `/completions`
- **Method**: `POST`
- **Description**: Sends a completion request to an MCP server.
- **Request Body**:
  - `serverId`: ID of the target MCP server (required).
  - `contextId`: ID of the target context (required).
  - `modelId`: ID of the target model (required).
  - `prompt`: The prompt string to complete (required).
- **Responses**:
  - `200`: Completion response.
  - `400`: Invalid request or parameters.
  - `401`: Unauthorized - authentication required.
  - `404`: Server, context, or model not found.

## Error Handling
Each request can return standard error representations. The error response object contains:
- `status`: The HTTP status code.
- `message`: A description of the error.

## Security
The API employs two types of security schemes:
- **Session Cookies**: For authenticated user sessions.
- **Bearer Tokens**: For programmatic API access.

This documentation outlines the structure and details of the MCP Hub API, providing developers with the necessary information to utilize the API effectively. For any issues, refer to the provided contact information for support.

---
*Documentation generated by* **[AutoCodeDocs.ai](https://autocodedocs.ai)**