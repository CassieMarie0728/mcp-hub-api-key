# McpServer

MCP server metadata

## Example Usage

```typescript
import { McpServer } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: McpServer = {
  id: "server-123",
  name: "MCP Server Alpha",
  url: "https://mcp-alpha.example.com",
  description: "Primary MCP server for region A",
  status: "online",
  region: "us-east-1",
};
```

## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *string*                                               | :heavy_minus_sign:                                     | Unique server identifier                               | server-123                                             |
| `name`                                                 | *string*                                               | :heavy_minus_sign:                                     | Server display name                                    | MCP Server Alpha                                       |
| `url`                                                  | *string*                                               | :heavy_minus_sign:                                     | Base URL of the MCP server                             | https://mcp-alpha.example.com                          |
| `description`                                          | *string*                                               | :heavy_minus_sign:                                     | Optional server description                            | Primary MCP server for region A                        |
| `status`                                               | [components.Status](../../models/components/status.md) | :heavy_minus_sign:                                     | Current server status                                  | online                                                 |
| `region`                                               | *string*                                               | :heavy_minus_sign:                                     | Server region or location                              | us-east-1                                              |