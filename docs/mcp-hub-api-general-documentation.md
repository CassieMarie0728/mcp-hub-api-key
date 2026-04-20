# MCP Hub Documentation

This documentation is designed to provide an overview of the MCP Hub, covering various aspects from database schema to API design and roadmap for implementation.

## Table of Contents

1. [Compatibility Caveats](#compatibility-caveats)
2. [Database Schema](#database-schema)
3. [Example Payloads](#example-payloads)
4. [Implementation Roadmap](#implementation-roadmap)
5. [MCP Hub API Blueprint](#mcp-hub-api-blueprint)
6. [OpenAPI Specification](#openapi-specification)
7. [Transport and Protocol Notes](#transport-and-protocol-notes)

---

## Compatibility Caveats

### Honest Positioning
- Do not claim universal compatibility with every MCP server in existence.
- Instead, describe compatibility using terms such as:
    - Compatible with standards-compliant MCP servers
    - Supports standard MCP transports and lifecycle
    - Extensible through pluggable transport and authentication adapters

### Why the Caveat Matters
Real-world MCP servers may differ significantly due to:
- Differences between draft and released protocol versions
- Custom transport implementations
- Provider-specific authentication methods
- Incomplete server implementations
- Additional optional feature support
- Server-side bugs

### Practical Compatibility Target
The goal is to aim for compatibility with:
- Standard lifecycle management
- `stdio` and Streamable HTTP
- Core capabilities integral to server function
- Optional client capabilities as required

This focus ensures that the majority of feasible integrations can be established without overextending claims regarding compatibility.

---

## Database Schema

This section details the primary tables involved in the MCP Hub’s PostgreSQL-ish schema. Adjustments for dialect-specific types such as `JSONB` and `TIMESTAMPTZ` may be necessary if migrating to MySQL.

### Overview of Tables

1. **mcp_servers**
   - Stores information about the MCP servers with relevant attributes like the transport type, HTTP endpoint, command, and authentication mode.

2. **mcp_connections**
   - Tracks active connections to the servers, preserving state and capabilities information.

3. **mcp_credentials**
   - Keeps credential data for authenticated interactions with MCP servers.

4. **mcp_requests**
   - Logs request transactions between the hub and the MCP servers, tracking status and payload details.

5. **mcp_events**
   - Records asynchronous events linked to connections for tracking changes or status updates.

6. **mcp_tools_cache, mcp_resources_cache, mcp_prompts_cache**
   - Caches metadata about tools, resources, and prompts for efficiency and quicker access.

7. **mcp_roots**
   - Maintains registered roots relevant for client-server exchanges.

8. **mcp_subscriptions**
   - Tracks subscriptions tied to resources or events.

### Sample Schema Definition

```sql
CREATE TABLE mcp_servers (
  id UUID PRIMARY KEY,
  name TEXT NOT NULL,
  transport_type TEXT NOT NULL CHECK (transport_type IN ('stdio', 'streamable_http')),
  ...
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```

Refer to the complete schema in `db-schema.sql` for all table definitions and constraints.

---

## Example Payloads

This section provides JSON-formatted examples of various interactions with the MCP Hub, illustrating client-server communications.

### Create Connection Example

```json
{
  "createConnectionStdio": {
    "request": {
      "name": "filesystem-server",
      "transport": "stdio",
      ...
    },
    "response": {
      "connectionId": "conn_01",
      "status": "created"
    }
  }
}
```

### Tool Call Example

```json
{
  "callTool": {
    "request": {
      "arguments": {
        "path": "/workspace/README.md"
      },
      "requestOptions": {
        "timeoutMs": 30000,
        "progressToken": "prog_1"
      }
    },
    "response": {
      "requestId": "req_123",
      ...
    }
  }
}
```

### Error Response Example

```json
{
  "error": {
    "code": "MCP_TOOL_CALL_FAILED",
    "message": "Server returned an error while executing tool 'read_file'",
    "details": {
      "connectionId": "conn_01",
      ...
    }
  }
}
```

---

## Implementation Roadmap

The roadmap outlines the development phases necessary to build the MCP Hub system progressively:

### Phase 0: Repository Foundation
- Select Node.js + TypeScript
- Establish foundational modules
- Set up logging, configuration, and migrations

### Phase 1: Core Protocol Spine
- Implement transport protocols for `stdio` and `Streamable HTTP`
- Create JSON-RPC dispatcher and connection state machine

### Phase 2: Basic Features
- Implement essential MCP calls for tools, resources, and operations

### Phase 3: Operational Quality Enhancements
- Focus on logging, event streams, and error management

### Phase 4: Authentication and Secrets Handling
- Develop secure authentication flows for various transport types

### Phase 5: Advanced Features and Enhancements
- Include capabilities for resource subscription and notification systems

Refer to `implementation-roadmap.md` for a comprehensive outline and deadline details.

---

## MCP Hub API Blueprint

This document outlines the standard API structure and functionalities that will be provided by the MCP Hub.

### Core API Functionalities

1. **Connections Management**:
   - Create, retrieve, delete, and manage connections to MCP servers.
  
2. **Authentication**:
   - Initiate, refresh, and manage authentication procedures.

3. **Tool and Resource Handling**:
   - Access and execute tools, read resources, and manage templates.

### Example Endpoint Definition

```http
POST /connections
```
#### Request Body:
```json
{
  "name": "filesystem-server",
  ...
}
```
#### Response:
```json
{
  "connectionId": "conn_01",
  "status": "created"
}
```

Refer to `mcp-hub-api-blueprint.md` for further details on API endpoints and their specifications.

---

## OpenAPI Specification

The OpenAPI specification (`openapi.yaml`) provides a structured description of the API, covering endpoints, request and response schemas, and authentication models.

### Components Overview

1. **Paths**: Define all API routes.
2. **Schemas**: Describe structure for requests and responses.
3. **Parameters**: Includes reusable parameters for clarity and consistency.

Refer to the complete `openapi.yaml` for the full specification, which is crucial for API definition and client generation.

---

## Transport and Protocol Notes

This section covers notes on transport methods and lifecycle management throughout the communications with MCP servers.

### Transports

1. **stdio**
   - Launches servers as subprocesses and manages input/output streams.

2. **Streamable HTTP**
   - Used for connections to remote MCP servers, supporting JSON-RPC over HTTP.

### Lifecycle Management

- Opening a connection involves establishing transport, initializing the protocol, and managing operational calls.

Refer to `transport-notes.md` for detailed communication protocols, notification types, and guidelines on ensuring smooth front-end interactions.

---

This documentation serves as a comprehensive guide to understanding and developing the MCP Hub. For more detailed entries, please refer to the respective files provided in the repository.

---
*Documentation generated by* **[AutoCodeDocs.ai](https://autocodedocs.ai)**
