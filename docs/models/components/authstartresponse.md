# AuthStartResponse

## Example Usage

```typescript
import { AuthStartResponse } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: AuthStartResponse = {
  authorizationUrl: "https://mcp.example.com/oauth/authorize?...",
  state: "oauth-state-123",
  codeVerifierRequired: true,
};
```

## Fields

| Field                  | Type                   | Required               | Description            |
| ---------------------- | ---------------------- | ---------------------- | ---------------------- |
| `authorizationUrl`     | *string*               | :heavy_minus_sign:     | N/A                    |
| `state`                | *string*               | :heavy_minus_sign:     | N/A                    |
| `codeVerifierRequired` | *boolean*              | :heavy_minus_sign:     | N/A                    |