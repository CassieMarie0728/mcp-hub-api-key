# ConnectionInitializeResponse

## Example Usage

```typescript
import { ConnectionInitializeResponse } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ConnectionInitializeResponse = {
  success: true,
  protocolVersion: "2025-06-18",
  serverInfo: {
    "name": "Filesystem MCP",
    "version": "1.4.0",
  },
  capabilities: {
    "tools": {
      "listChanged": true,
    },
    "resources": {
      "subscribe": true,
    },
  },
  instructions: "Use resources for file reads and tools for write operations.",
};
```

## Fields

| Field                 | Type                  | Required              | Description           |
| --------------------- | --------------------- | --------------------- | --------------------- |
| `success`             | *boolean*             | :heavy_minus_sign:    | N/A                   |
| `protocolVersion`     | *string*              | :heavy_minus_sign:    | N/A                   |
| `serverInfo`          | Record<string, *any*> | :heavy_minus_sign:    | N/A                   |
| `capabilities`        | Record<string, *any*> | :heavy_minus_sign:    | N/A                   |
| `instructions`        | *string*              | :heavy_minus_sign:    | N/A                   |