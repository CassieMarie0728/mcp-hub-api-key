# ConnectionInitializeBody

## Example Usage

```typescript
import { ConnectionInitializeBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ConnectionInitializeBody = {
  clientName: "MCP Hub",
  clientVersion: "2.1.0",
  protocolVersion: "2025-06-18",
  clientCapabilities: {
    "roots": {
      "listChanged": true,
    },
    "sampling": {},
  },
};
```

## Fields

| Field                                                 | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `clientName`                                          | *string*                                              | :heavy_check_mark:                                    | Human-readable name of the MCP Hub client.            |
| `clientVersion`                                       | *string*                                              | :heavy_check_mark:                                    | Semantic version of the MCP Hub client.               |
| `protocolVersion`                                     | *string*                                              | :heavy_minus_sign:                                    | Preferred MCP protocol version.                       |
| `clientCapabilities`                                  | Record<string, *any*>                                 | :heavy_minus_sign:                                    | Client capabilities advertised during initialization. |