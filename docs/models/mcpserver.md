# McpServer

MCP server metadata


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    | Example                                        |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `id`                                           | *Optional[str]*                                | :heavy_minus_sign:                             | Unique server identifier                       | server-123                                     |
| `name`                                         | *Optional[str]*                                | :heavy_minus_sign:                             | Server display name                            | MCP Server Alpha                               |
| `url`                                          | *Optional[str]*                                | :heavy_minus_sign:                             | Base URL of the MCP server                     | https://mcp-alpha.example.com                  |
| `description`                                  | *OptionalNullable[str]*                        | :heavy_minus_sign:                             | Optional server description                    | Primary MCP server for region A                |
| `status`                                       | [Optional[models.Status]](../models/status.md) | :heavy_minus_sign:                             | Current server status                          | online                                         |
| `region`                                       | *OptionalNullable[str]*                        | :heavy_minus_sign:                             | Server region or location                      | us-east-1                                      |