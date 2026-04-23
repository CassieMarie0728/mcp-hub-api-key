# CancelConnectionRequestRequest

## Example Usage

```typescript
import { CancelConnectionRequestRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: CancelConnectionRequestRequest = {
  connectionId: "<id>",
};
```

## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  | Example                                                                      |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `connectionId`                                                               | *string*                                                                     | :heavy_check_mark:                                                           | Unique identifier of the connection.                                         |                                                                              |
| `cancelRequestBody`                                                          | [components.CancelRequestBody](../../models/components/cancelrequestbody.md) | :heavy_check_mark:                                                           | N/A                                                                          | {<br/>"requestId": "req-123abc",<br/>"reason": "User navigated away"<br/>}   |