# InlineResponse2003

A user registered in the system

## Example Usage

```typescript
import { InlineResponse2003 } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: InlineResponse2003 = {
  id: 123,
  openId: "openid-xyz",
  name: "John Doe",
  email: "john.doe@example.com",
  loginMethod: "oauth",
  createdAt: new Date("2023-01-01T12:00:00Z"),
  updatedAt: new Date("2023-01-10T12:00:00Z"),
  lastSignedIn: new Date("2023-02-01T08:00:00Z"),
};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                                                                                          | *number*                                                                                      | :heavy_minus_sign:                                                                            | Primary key identifier                                                                        | 123                                                                                           |
| `openId`                                                                                      | *string*                                                                                      | :heavy_minus_sign:                                                                            | Unique OpenID identifier                                                                      | openid-xyz                                                                                    |
| `name`                                                                                        | *string*                                                                                      | :heavy_minus_sign:                                                                            | User's name                                                                                   | John Doe                                                                                      |
| `email`                                                                                       | *string*                                                                                      | :heavy_minus_sign:                                                                            | User's email address                                                                          | john.doe@example.com                                                                          |
| `loginMethod`                                                                                 | *string*                                                                                      | :heavy_minus_sign:                                                                            | Method used for login                                                                         | oauth                                                                                         |
| `role`                                                                                        | [components.InlineResponse2003Role](../../models/components/inlineresponse2003role.md)        | :heavy_minus_sign:                                                                            | User role in the system                                                                       | user                                                                                          |
| `createdAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | Timestamp when user was created                                                               | 2023-01-01T12:00:00Z                                                                          |
| `updatedAt`                                                                                   | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | Timestamp when user was last updated                                                          | 2023-01-10T12:00:00Z                                                                          |
| `lastSignedIn`                                                                                | [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | :heavy_minus_sign:                                                                            | Timestamp of last sign-in                                                                     | 2023-02-01T08:00:00Z                                                                          |