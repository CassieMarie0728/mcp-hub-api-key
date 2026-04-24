# AuthStartBody

## Example Usage

```typescript
import { AuthStartBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: AuthStartBody = {
  callbackUrl: "https://app.example.com/mcp/auth/callback",
  scopes: [
    "tools:read",
    "resources:read",
  ],
};
```

## Fields

| Field                                    | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `callbackUrl`                            | *string*                                 | :heavy_minus_sign:                       | Client callback URL for completing auth. |
| `scopes`                                 | *string*[]                               | :heavy_minus_sign:                       | Requested scopes for the connection.     |