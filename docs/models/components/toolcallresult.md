# ToolCallResult

## Example Usage

```typescript
import { ToolCallResult } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ToolCallResult = {
  isError: false,
  content: [
    {
      "type": "text",
      "text": "Readme loaded successfully.",
    },
  ],
  structuredContent: {
    "bytes": 1024,
  },
  metadata: {
    "executionTimeMs": 42,
  },
};
```

## Fields

| Field                   | Type                    | Required                | Description             |
| ----------------------- | ----------------------- | ----------------------- | ----------------------- |
| `isError`               | *boolean*               | :heavy_minus_sign:      | N/A                     |
| `content`               | Record<string, *any*>[] | :heavy_minus_sign:      | N/A                     |
| `structuredContent`     | Record<string, *any*>   | :heavy_minus_sign:      | N/A                     |
| `metadata`              | Record<string, *any*>   | :heavy_minus_sign:      | N/A                     |