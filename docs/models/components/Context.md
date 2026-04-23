# Context

MCP server context information


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `id`                                   | *Optional\<String>*                    | :heavy_minus_sign:                     | Unique context identifier              | context-456                            |
| `serverId`                             | *Optional\<String>*                    | :heavy_minus_sign:                     | Associated MCP server ID               | server-123                             |
| `name`                                 | *Optional\<String>*                    | :heavy_minus_sign:                     | Context name                           | User Data Context                      |
| `description`                          | *JsonNullable\<String>*                | :heavy_minus_sign:                     | Optional context description           | Context containing user-related models |