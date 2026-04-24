# CompletionsBody

## Example Usage

```typescript
import { CompletionsBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: CompletionsBody = {
  serverId: "server-123",
  contextId: "context-456",
  modelId: "model-789",
  prompt: "Translate the following text to French:",
  parameters: {
    "maxTokens": 100,
  },
};
```

## Fields

| Field                                  | Type                                   | Required                               | Description                            |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `serverId`                             | *string*                               | :heavy_check_mark:                     | Target MCP server ID                   |
| `contextId`                            | *string*                               | :heavy_check_mark:                     | Target context ID                      |
| `modelId`                              | *string*                               | :heavy_check_mark:                     | Target model ID                        |
| `prompt`                               | *string*                               | :heavy_check_mark:                     | Prompt string to complete              |
| `parameters`                           | Record<string, *any*>                  | :heavy_minus_sign:                     | Optional parameters for the completion |