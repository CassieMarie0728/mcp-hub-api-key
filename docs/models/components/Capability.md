# Capability

Capability metadata for MCP servers


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        | Example                                            |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `serverId`                                         | *Optional\<String>*                                | :heavy_minus_sign:                                 | MCP server ID                                      | server-123                                         |
| `capabilities`                                     | List\<*String*>                                    | :heavy_minus_sign:                                 | List of supported capabilities                     | [<br/>"tools/list",<br/>"resources/list",<br/>"prompts/list"<br/>] |