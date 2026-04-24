# InlineResponse2002

## Example Usage

```typescript
import { InlineResponse2002 } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: InlineResponse2002 = {
  token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  user: {
    id: 123,
    openId: "openid-xyz",
    name: "John Doe",
    email: "john.doe@example.com",
    loginMethod: "oauth",
    createdAt: new Date("2023-01-01T12:00:00Z"),
    updatedAt: new Date("2023-01-10T12:00:00Z"),
    lastSignedIn: new Date("2023-02-01T08:00:00Z"),
  },
};
```

## Fields

| Field                                              | Type                                               | Required                                           | Description                                        | Example                                            |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `token`                                            | *string*                                           | :heavy_minus_sign:                                 | JWT or session token for authenticated requests    | eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...            |
| `user`                                             | [components.User](../../models/components/user.md) | :heavy_minus_sign:                                 | A user registered in the system                    |                                                    |