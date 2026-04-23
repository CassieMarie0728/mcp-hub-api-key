# Connection

MCP connection metadata and status

## Example Usage

```typescript
import { Connection } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Connection = {
  id: "conn-abc123",
  serverId: "server-123",
  transport: "stdio",
  status: "connected",
  protocolVersion: "1.0.0",
  capabilities: [
    "tools/list",
    "resources/list",
  ],
  createdAt: new Date("2023-03-01T10:00:00Z"),
  updatedAt: new Date("2023-03-01T10:05:00Z"),
};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                                                                                          | *string*                                                                                      | :heavy_minus_sign:                                                                            | Unique connection identifier                                                                  | conn-abc123                                                                                   |
| `serverId`                                                                                    | *string*                                                                                      | :heavy_minus_sign:                                                                            | MCP server ID connected to                                                                    | server-123                                                                                    |
| `transport`                                                                                   | [components.Transport](../../models/components/transport.md)                                  | :heavy_minus_sign:                                                                            | Transport type used                                                                           | stdio                                                                                         |
| `status`                                                                                      | [components.ConnectionStatus](../../models/components/connectionstatus.md)                    | :heavy_minus_sign:                                                                            | Current connection status                                                                     | connected                                                                                     |
| `protocolVersion`                                                                             | *string*                                                                                      | :heavy_minus_sign:                                                                            | Negotiated MCP protocol version                                                               | 1.0.0                                                                                         |
| `capabilities`                                                                                | *string*[]                                                                                    | :heavy_minus_sign:                                                                            | List of server capabilities                                                                   | [<br/>"tools/list",<br/>"resources/list"<br/>]                                                |
| `createdAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | Timestamp when connection was created                                                         | 2023-03-01T10:00:00Z                                                                          |
| `updatedAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | Timestamp when connection was last updated                                                    | 2023-03-01T10:05:00Z                                                                          |