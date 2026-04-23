# ResourceTemplate

Template metadata for resources

## Example Usage

```typescript
import { ResourceTemplate } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: ResourceTemplate = {
  id: "template-001",
  name: "UserProfileTemplate",
  description: "Template for user profile resources",
};
```

## Fields

| Field                               | Type                                | Required                            | Description                         | Example                             |
| ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- |
| `id`                                | *string*                            | :heavy_minus_sign:                  | Unique template identifier          | template-001                        |
| `name`                              | *string*                            | :heavy_minus_sign:                  | Template name                       | UserProfileTemplate                 |
| `description`                       | *string*                            | :heavy_minus_sign:                  | Optional template description       | Template for user profile resources |