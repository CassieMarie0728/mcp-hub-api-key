# Tool

Tool integrated within MCP Hub


## Fields

| Field                                           | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `id`                                            | *Optional\<String>*                             | :heavy_minus_sign:                              | Unique tool identifier                          | tool-001                                        |
| `name`                                          | *Optional\<String>*                             | :heavy_minus_sign:                              | Tool name                                       | Data Visualizer                                 |
| `description`                                   | *JsonNullable\<String>*                         | :heavy_minus_sign:                              | Tool description                                | Visualize data from MCP queries                 |
| `version`                                       | *Optional\<String>*                             | :heavy_minus_sign:                              | Tool version                                    | 1.2.3                                           |
| `url`                                           | *Optional\<String>*                             | :heavy_minus_sign:                              | URL or endpoint to access the tool              | https://tools.mcphub.example.com/datavisualizer |