# Tool

Tool integrated within MCP Hub

## Example Usage

```typescript
import { Tool } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: Tool = {
  id: "tool-001",
  name: "Data Visualizer",
  description: "Visualize data from MCP queries",
  version: "1.2.3",
  url: "https://tools.mcphub.example.com/datavisualizer",
};
```

## Fields

| Field                                           | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `id`                                            | *string*                                        | :heavy_minus_sign:                              | Unique tool identifier                          | tool-001                                        |
| `name`                                          | *string*                                        | :heavy_minus_sign:                              | Tool name                                       | Data Visualizer                                 |
| `description`                                   | *string*                                        | :heavy_minus_sign:                              | Tool description                                | Visualize data from MCP queries                 |
| `version`                                       | *string*                                        | :heavy_minus_sign:                              | Tool version                                    | 1.2.3                                           |
| `url`                                           | *string*                                        | :heavy_minus_sign:                              | URL or endpoint to access the tool              | https://tools.mcphub.example.com/datavisualizer |