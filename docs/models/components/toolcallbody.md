# ToolCallBody

## Example Usage

```typescript
import { ToolCallBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ToolCallBody = {
  arguments: {
    "path": "/docs/readme.md",
  },
  requestId: "req-tool-001",
};
```

## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `arguments`                               | Record<string, *any*>                     | :heavy_check_mark:                        | Arguments passed to the target tool.      |
| `requestId`                               | *string*                                  | :heavy_minus_sign:                        | Optional client-generated id for tracing. |