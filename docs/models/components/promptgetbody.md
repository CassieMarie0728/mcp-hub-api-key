# PromptGetBody

## Example Usage

```typescript
import { PromptGetBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: PromptGetBody = {
  arguments: {
    "targetLanguage": "fr",
  },
};
```

## Fields

| Field                      | Type                       | Required                   | Description                |
| -------------------------- | -------------------------- | -------------------------- | -------------------------- |
| `arguments`                | Record<string, *any*>      | :heavy_minus_sign:         | Prompt template arguments. |