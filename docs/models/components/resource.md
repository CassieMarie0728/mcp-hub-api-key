# Resource

MCP resource metadata

## Example Usage

```typescript
import { Resource } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Resource = {
  id: "resource-001",
  serverId: "server-123",
  name: "UserProfiles",
  description: "Collection of user profiles",
};
```

## Fields

| Field                         | Type                          | Required                      | Description                   | Example                       |
| ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| `id`                          | *string*                      | :heavy_minus_sign:            | Unique resource identifier    | resource-001                  |
| `serverId`                    | *string*                      | :heavy_minus_sign:            | MCP server ID                 | server-123                    |
| `name`                        | *string*                      | :heavy_minus_sign:            | Resource name                 | UserProfiles                  |
| `description`                 | *string*                      | :heavy_minus_sign:            | Optional resource description | Collection of user profiles   |