# CallConnectionToolRequest

## Example Usage

```typescript
import { CallConnectionToolRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: CallConnectionToolRequest = {
  connectionId: "<id>",
  toolName: "<value>",
};
```

## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 | Example                                                                     |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `connectionId`                                                              | *string*                                                                    | :heavy_check_mark:                                                          | Unique identifier of the connection.                                        |                                                                             |
| `toolName`                                                                  | *string*                                                                    | :heavy_check_mark:                                                          | Name of the MCP tool to invoke.                                             |                                                                             |
| `toolCallBody`                                                              | [components.ToolCallBody](../../models/components/toolcallbody.md)          | :heavy_check_mark:                                                          | N/A                                                                         | {<br/>"arguments": {<br/>"path": "/docs/readme.md"<br/>},<br/>"requestId": "req-tool-001"<br/>} |