# ReadConnectionResourceRequest

## Example Usage

```typescript
import { ReadConnectionResourceRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: ReadConnectionResourceRequest = {
  connectionId: "<id>",
};
```

## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                | Example                                                                    |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `connectionId`                                                             | *string*                                                                   | :heavy_check_mark:                                                         | Unique identifier of the connection.                                       |                                                                            |
| `resourceReadBody`                                                         | [components.ResourceReadBody](../../models/components/resourcereadbody.md) | :heavy_check_mark:                                                         | N/A                                                                        | {<br/>"uri": "file:///workspace/notes/todo.md"<br/>}                       |