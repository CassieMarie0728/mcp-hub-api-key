# Tool

Tool integrated within MCP Hub


## Fields

| Field                                           | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `id`                                            | *Optional[str]*                                 | :heavy_minus_sign:                              | Unique tool identifier                          | tool-001                                        |
| `name`                                          | *Optional[str]*                                 | :heavy_minus_sign:                              | Tool name                                       | Data Visualizer                                 |
| `description`                                   | *OptionalNullable[str]*                         | :heavy_minus_sign:                              | Tool description                                | Visualize data from MCP queries                 |
| `version`                                       | *Optional[str]*                                 | :heavy_minus_sign:                              | Tool version                                    | 1.2.3                                           |
| `url`                                           | *Optional[str]*                                 | :heavy_minus_sign:                              | URL or endpoint to access the tool              | https://tools.mcphub.example.com/datavisualizer |