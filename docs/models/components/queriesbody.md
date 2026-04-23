# QueriesBody

## Example Usage

```typescript
import { QueriesBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: QueriesBody = {
  serverId: "server-123",
  contextId: "context-456",
  modelId: "model-789",
  query: "SELECT * FROM users WHERE active = true",
  parameters: {
    "limit": 10,
  },
};
```

## Fields

| Field                              | Type                               | Required                           | Description                        |
| ---------------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------- |
| `serverId`                         | *string*                           | :heavy_check_mark:                 | Target MCP server ID               |
| `contextId`                        | *string*                           | :heavy_check_mark:                 | Target context ID                  |
| `modelId`                          | *string*                           | :heavy_check_mark:                 | Target model ID                    |
| `query`                            | *string*                           | :heavy_check_mark:                 | Query or command string to execute |
| `parameters`                       | Record<string, *any*>              | :heavy_minus_sign:                 | Optional parameters for the query  |