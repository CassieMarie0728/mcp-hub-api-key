# MCP Hub API GraphQL Schema Documentation

## Schema Overview
The MCP Hub API provides a comprehensive interface for managing and interacting with MCP (Model-Client Protocol) servers. It facilitates a variety of operations such as user authentication, server management, resource interaction, and real-time event streaming. This GraphQL schema allows clients to leverage these functionalities seamlessly.

## Queries
The following queries can be executed to retrieve data related to MCP servers, connections, resources, prompts, and more.

1. **Get Current User**
   - **Operation:** `currentUser`
   - **Arguments:** None
   - **Returns:** `User` - Information about the currently authenticated user.

2. **List MCP Servers**
   - **Operation:** `listMcpServers`
   - **Arguments:**
     - `region: String` (optional) - Filter servers by specific region.
     - `status: String` (optional) - Filter servers by their current status (`online`, `offline`).
   - **Returns:** `[McpServer]` - An array of MCP server objects.

3. **Get MCP Server by ID**
   - **Operation:** `getMcpServerById`
   - **Arguments:**
     - `serverId: String` (required) - Unique identifier of the MCP server.
   - **Returns:** `McpServer` - The details of the specified MCP server.

4. **List All Connections**
   - **Operation:** `listConnections`
   - **Arguments:** None
   - **Returns:** `[Connection]` - An array of connection objects for the authenticated user.

5. **Get Connection Details by ID**
   - **Operation:** `getConnectionById`
   - **Arguments:**
     - `connectionId: String` (required) - Unique identifier of the connection.
   - **Returns:** `Connection` - The details and status of the specified connection.

6. **List Resources**
   - **Operation:** `listResources`
   - **Arguments:**
     - `serverId: String` (optional) - Filter resources by a specific MCP server ID.
   - **Returns:** `[Resource]` - An array of resource metadata objects.

7. **Get Prompt by ID**
   - **Operation:** `getPromptById`
   - **Arguments:** 
     - `promptId: String` (required) - Unique identifier of the prompt.
   - **Returns:** `Prompt` - The details of the specified prompt.

## Mutations
The following mutations allow for creating, updating, and deleting resources, connections, and user sessions.

1. **Login User**
   - **Operation:** `login`
   - **Arguments:**
     - `username: String` (required) - Username or email for authentication.
     - `password: String` (required) - User password.
   - **Returns:** `inline_response_200_2` - Authentication token along with user information.

2. **Logout User**
   - **Operation:** `logout`
   - **Arguments:** None
   - **Returns:** `inline_response_200_1` - Confirmation of successful logout.

3. **Register MCP Server**
   - **Operation:** `registerMcpServer`
   - **Arguments:**
     - `name: String` (required) - Display name for the server.
     - `url: String` (required) - Base URL of the MCP server.
     - `description: String` (optional) - Description of the server.
   - **Returns:** `McpServer` - The details of the registered MCP server.

4. **Create Connection**
   - **Operation:** `createConnection`
   - **Arguments:**
     - `serverId: String` (required) - MCP server ID to connect to.
     - `transport: String` (required) - Transport type (either `stdio` or `streamable-http`).
     - `options: Object` (optional) - Transport-specific options.
   - **Returns:** `Connection` - The initialized connection object.

5. **Delete Connection**
   - **Operation:** `deleteConnection`
   - **Arguments:**
     - `connectionId: String` (required) - Unique identifier of the connection to delete.
   - **Returns:** `inline_response_200` - Confirmation of successful deletion.

## Types & Fields

### User
- **id:** `Int` - Primary key identifier.
- **openId:** `String` - Unique OpenID identifier.
- **name:** `String` (nullable) - User's name.
- **email:** `String` (nullable) - User's email address.
- **loginMethod:** `String` (nullable) - Method used for login.
- **role:** `String` - User role; can be `user` or `admin` (default: `user`).
- **createdAt:** `String` (format: `date-time`) - Timestamp of user creation.
- **updatedAt:** `String` (format: `date-time`) - Last updated timestamp.
- **lastSignedIn:** `String` (format: `date-time`) - Last sign-in time.

### McpServer
- **id:** `String` - Unique server identifier.
- **name:** `String` - Server display name.
- **url:** `String` (format: `uri`) - Base URL of the MCP server.
- **description:** `String` (nullable) - Optional server description.
- **status:** `String` - Current server status; can be `online` or `offline`.
- **region:** `String` (nullable) - Server's geographical region.

### Connection
- **id:** `String` - Unique connection identifier.
- **serverId:** `String` - MCP server ID connected to.
- **transport:** `String` - Type of transport used (`stdio` or `streamable-http`).
- **status:** `String` - Current connection status; can be `initializing`, `connected`, `disconnected`, or `error`.
- **protocolVersion:** `String` - Negotiated MCP protocol version.
- **capabilities:** `[String]` - List of supported capabilities.
- **createdAt:** `String` (format: `date-time`) - Timestamp of connection creation.
- **updatedAt:** `String` (format: `date-time`) - Timestamp of last update.

### Resource
- **id:** `String` - Unique resource identifier.
- **serverId:** `String` - MCP server ID.
- **name:** `String` - Resource name.
- **description:** `String` (nullable) - Optional resource description.

### Prompt
- **id:** `String` - Unique prompt identifier.
- **name:** `String` - Prompt name.
- **description:** `String` (nullable) - Optional prompt description.
- **content:** `String` - Prompt content or template.

### Error
- **status:** `Int` - HTTP status code.
- **message:** `String` - Error message.

## Directives & Custom Resolvers
The API utilizes built-in directives for managing authorization. Security is handled via JSON Web Tokens (JWT) and session cookies. Specific schema-level validations and error handling are implemented to ensure robust API interaction.

This documentation covers the main aspects of the MCP Hub API's GraphQL schema designed for efficient server management and user interactions. Further details regarding specific components can be referenced in sections detailing their schemas.

---
*Documentation generated by* **[AutoCodeDocs.ai](https://autocodedocs.ai)**