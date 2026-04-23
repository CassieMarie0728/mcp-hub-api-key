# McpServer

MCP server metadata


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Unique server identifier                               | server-123                                             |
| `name`                                                 | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Server display name                                    | MCP Server Alpha                                       |
| `url`                                                  | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Base URL of the MCP server                             | https://mcp-alpha.example.com                          |
| `description`                                          | *JsonNullable\<String>*                                | :heavy_minus_sign:                                     | Optional server description                            | Primary MCP server for region A                        |
| `status`                                               | [Optional\<Status>](../../models/components/Status.md) | :heavy_minus_sign:                                     | Current server status                                  | online                                                 |
| `region`                                               | *JsonNullable\<String>*                                | :heavy_minus_sign:                                     | Server region or location                              | us-east-1                                              |