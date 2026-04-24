# AuthLoginBody

## Example Usage

```typescript
import { AuthLoginBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: AuthLoginBody = {
  username: "john.doe",
  password: "secret123",
};
```

## Fields

| Field              | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `username`         | *string*           | :heavy_check_mark: | Username or email  |
| `password`         | *string*           | :heavy_check_mark: | User password      |