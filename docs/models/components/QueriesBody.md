# QueriesBody


## Fields

| Field                              | Type                               | Required                           | Description                        |
| ---------------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------- |
| `serverId`                         | *String*                           | :heavy_check_mark:                 | Target MCP server ID               |
| `contextId`                        | *String*                           | :heavy_check_mark:                 | Target context ID                  |
| `modelId`                          | *String*                           | :heavy_check_mark:                 | Target model ID                    |
| `query`                            | *String*                           | :heavy_check_mark:                 | Query or command string to execute |
| `parameters`                       | Map\<String, *Object*>             | :heavy_minus_sign:                 | Optional parameters for the query  |