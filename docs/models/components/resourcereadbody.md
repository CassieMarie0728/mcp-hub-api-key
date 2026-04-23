# ResourceReadBody

## Example Usage

```typescript
import { ResourceReadBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ResourceReadBody = {
  uri: "file:///workspace/notes/todo.md",
};
```

## Fields

| Field                                   | Type                                    | Required                                | Description                             |
| --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| `uri`                                   | *string*                                | :heavy_check_mark:                      | Resource URI exposed by the MCP server. |
| `cursor`                                | *string*                                | :heavy_minus_sign:                      | Optional pagination cursor.             |