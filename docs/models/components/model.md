# Model

Model within a context

## Example Usage

```typescript
import { Model } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Model = {
  id: "model-789",
  contextId: "context-456",
  name: "UserModel",
  description: "Model representing user entities",
};
```

## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *string*                                               | :heavy_minus_sign:                                     | Unique model identifier                                | model-789                                              |
| `contextId`                                            | *string*                                               | :heavy_minus_sign:                                     | Associated context ID                                  | context-456                                            |
| `name`                                                 | *string*                                               | :heavy_minus_sign:                                     | Model name                                             | UserModel                                              |
| `description`                                          | *string*                                               | :heavy_minus_sign:                                     | Optional model description                             | Model representing user entities                       |
| `schema`                                               | Record<string, *any*>                                  | :heavy_minus_sign:                                     | JSON schema or metadata describing the model structure |                                                        |