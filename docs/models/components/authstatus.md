# AuthStatus

## Example Usage

```typescript
import { AuthStatus } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: AuthStatus = {
  authenticated: true,
  authType: "oauth",
  expiresAt: new Date("2026-04-09T06:00:00Z"),
  scopes: [
    "tools:read",
    "resources:read",
  ],
};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `authenticated`                                                                               | *boolean*                                                                                     | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `authType`                                                                                    | [components.AuthType](../../models/components/authtype.md)                                    | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `expiresAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `scopes`                                                                                      | *string*[]                                                                                    | :heavy_minus_sign:                                                                            | N/A                                                                                           |