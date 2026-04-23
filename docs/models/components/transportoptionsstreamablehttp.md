# TransportOptionsStreamableHttp

Transport options for streamable HTTP MCP servers.

## Example Usage

```typescript
import { TransportOptionsStreamableHttp } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: TransportOptionsStreamableHttp = {
  url: "https://ample-colon.com",
};
```

## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `url`                                                         | *string*                                                      | :heavy_check_mark:                                            | HTTP endpoint for the MCP server transport.                   |
| `headers`                                                     | Record<string, *string*>                                      | :heavy_minus_sign:                                            | Optional HTTP headers sent with transport requests.           |
| `sessionId`                                                   | *string*                                                      | :heavy_minus_sign:                                            | Optional session identifier returned by the remote transport. |