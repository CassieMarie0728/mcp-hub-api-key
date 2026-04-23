# Context

MCP server context information


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `id`                                   | *Optional[str]*                        | :heavy_minus_sign:                     | Unique context identifier              | context-456                            |
| `server_id`                            | *Optional[str]*                        | :heavy_minus_sign:                     | Associated MCP server ID               | server-123                             |
| `name`                                 | *Optional[str]*                        | :heavy_minus_sign:                     | Context name                           | User Data Context                      |
| `description`                          | *OptionalNullable[str]*                | :heavy_minus_sign:                     | Optional context description           | Context containing user-related models |