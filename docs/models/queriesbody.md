# QueriesBody


## Fields

| Field                              | Type                               | Required                           | Description                        |
| ---------------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------- |
| `server_id`                        | *str*                              | :heavy_check_mark:                 | Target MCP server ID               |
| `context_id`                       | *str*                              | :heavy_check_mark:                 | Target context ID                  |
| `model_id`                         | *str*                              | :heavy_check_mark:                 | Target model ID                    |
| `query`                            | *str*                              | :heavy_check_mark:                 | Query or command string to execute |
| `parameters`                       | Dict[str, *Any*]                   | :heavy_minus_sign:                 | Optional parameters for the query  |