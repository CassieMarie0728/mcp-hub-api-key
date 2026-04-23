# GetConnectionPromptRequest

## Example Usage

```typescript
import { GetConnectionPromptRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: GetConnectionPromptRequest = {
  connectionId: "<id>",
  promptName: "<value>",
};
```

## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          | Example                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `connectionId`                                                       | *string*                                                             | :heavy_check_mark:                                                   | Unique identifier of the connection.                                 |                                                                      |
| `promptName`                                                         | *string*                                                             | :heavy_check_mark:                                                   | Name of the prompt template.                                         |                                                                      |
| `promptGetBody`                                                      | [components.PromptGetBody](../../models/components/promptgetbody.md) | :heavy_minus_sign:                                                   | N/A                                                                  | {<br/>"arguments": {<br/>"targetLanguage": "fr"<br/>}<br/>}          |