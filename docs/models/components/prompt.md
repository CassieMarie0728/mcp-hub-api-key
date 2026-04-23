# Prompt

Prompt metadata

## Example Usage

```typescript
import { Prompt } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Prompt = {
  id: "prompt-001",
  name: "TranslatePrompt",
  description: "Prompt for translation tasks",
  content: "Translate the following text to French:",
};
```

## Fields

| Field                                   | Type                                    | Required                                | Description                             | Example                                 |
| --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| `id`                                    | *string*                                | :heavy_minus_sign:                      | Unique prompt identifier                | prompt-001                              |
| `name`                                  | *string*                                | :heavy_minus_sign:                      | Prompt name                             | TranslatePrompt                         |
| `description`                           | *string*                                | :heavy_minus_sign:                      | Optional prompt description             | Prompt for translation tasks            |
| `content`                               | *string*                                | :heavy_minus_sign:                      | Prompt content or template              | Translate the following text to French: |