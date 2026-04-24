# Context

MCP server context information

## Example Usage

```typescript
import { Context } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Context = {
  id: "context-456",
  serverId: "server-123",
  name: "User Data Context",
  description: "Context containing user-related models",
};
```

## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `id`                                   | *string*                               | :heavy_minus_sign:                     | Unique context identifier              | context-456                            |
| `serverId`                             | *string*                               | :heavy_minus_sign:                     | Associated MCP server ID               | server-123                             |
| `name`                                 | *string*                               | :heavy_minus_sign:                     | Context name                           | User Data Context                      |
| `description`                          | *string*                               | :heavy_minus_sign:                     | Optional context description           | Context containing user-related models |