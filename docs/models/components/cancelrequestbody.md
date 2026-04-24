# CancelRequestBody

## Example Usage

```typescript
import { CancelRequestBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: CancelRequestBody = {
  requestId: "req-123abc",
  reason: "User navigated away",
};
```

## Fields

| Field                                          | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `requestId`                                    | *string*                                       | :heavy_check_mark:                             | Identifier of the in-flight request to cancel. |
| `reason`                                       | *string*                                       | :heavy_minus_sign:                             | Optional user-facing cancellation reason.      |