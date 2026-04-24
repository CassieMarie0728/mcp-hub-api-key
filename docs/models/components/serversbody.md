# ServersBody

## Example Usage

```typescript
import { ServersBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ServersBody = {
  name: "MCP Server Alpha",
  url: "https://mcp-alpha.example.com",
  description: "Primary MCP server for region A",
};
```

## Fields

| Field                       | Type                        | Required                    | Description                 |
| --------------------------- | --------------------------- | --------------------------- | --------------------------- |
| `name`                      | *string*                    | :heavy_check_mark:          | Server display name         |
| `url`                       | *string*                    | :heavy_check_mark:          | Base URL of the MCP server  |
| `description`               | *string*                    | :heavy_minus_sign:          | Optional server description |