# ConnectionsBody

## Example Usage

```typescript
import { ConnectionsBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ConnectionsBody = {
  serverId: "server-123",
  transport: "stdio",
  options: {
    command: "/usr/local/bin/mcp-server",
    args: [
      "--stdio",
    ],
  },
};
```

## Fields

| Field                                                                                                                            | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `serverId`                                                                                                                       | *string*                                                                                                                         | :heavy_check_mark:                                                                                                               | MCP server ID to connect to                                                                                                      |
| `transport`                                                                                                                      | [components.ConnectionsBodyTransport](../../models/components/connectionsbodytransport.md)                                       | :heavy_check_mark:                                                                                                               | Transport type (stdio or streamable-http)                                                                                        |
| `options`                                                                                                                        | *components.Options*                                                                                                             | :heavy_minus_sign:                                                                                                               | Transport-specific options. Use stdio options for stdio connections and streamable HTTP options for streamable-http connections. |