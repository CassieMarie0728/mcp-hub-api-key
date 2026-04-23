# StartConnectionAuthRequest

## Example Usage

```typescript
import { StartConnectionAuthRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: StartConnectionAuthRequest = {
  connectionId: "<id>",
};
```

## Fields

| Field                                                                                                        | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  | Example                                                                                                      |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `connectionId`                                                                                               | *string*                                                                                                     | :heavy_check_mark:                                                                                           | Unique identifier of the connection.                                                                         |                                                                                                              |
| `authStartBody`                                                                                              | [components.AuthStartBody](../../models/components/authstartbody.md)                                         | :heavy_minus_sign:                                                                                           | N/A                                                                                                          | {<br/>"callbackUrl": "https://app.example.com/mcp/auth/callback",<br/>"scopes": [<br/>"tools:read",<br/>"resources:read"<br/>]<br/>} |