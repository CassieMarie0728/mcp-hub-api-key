# Capability

Capability metadata for MCP servers


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        | Example                                            |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `server_id`                                        | *Optional[str]*                                    | :heavy_minus_sign:                                 | MCP server ID                                      | server-123                                         |
| `capabilities`                                     | List[*str*]                                        | :heavy_minus_sign:                                 | List of supported capabilities                     | [<br/>"tools/list",<br/>"resources/list",<br/>"prompts/list"<br/>] |