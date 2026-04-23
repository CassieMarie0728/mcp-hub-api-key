# Capability

Capability metadata for MCP servers

## Example Usage

```typescript
import { Capability } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Capability = {
  serverId: "server-123",
  capabilities: [
    "tools/list",
    "resources/list",
    "prompts/list",
  ],
};
```

## Fields

| Field                                              | Type                                               | Required                                           | Description                                        | Example                                            |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `serverId`                                         | *string*                                           | :heavy_minus_sign:                                 | MCP server ID                                      | server-123                                         |
| `capabilities`                                     | *string*[]                                         | :heavy_minus_sign:                                 | List of supported capabilities                     | [<br/>"tools/list",<br/>"resources/list",<br/>"prompts/list"<br/>] |