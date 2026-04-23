# ConnectionInitializeBody


## Fields

| Field                                                 | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `client_name`                                         | *str*                                                 | :heavy_check_mark:                                    | Human-readable name of the MCP Hub client.            |
| `client_version`                                      | *str*                                                 | :heavy_check_mark:                                    | Semantic version of the MCP Hub client.               |
| `protocol_version`                                    | *Optional[str]*                                       | :heavy_minus_sign:                                    | Preferred MCP protocol version.                       |
| `client_capabilities`                                 | Dict[str, *Any*]                                      | :heavy_minus_sign:                                    | Client capabilities advertised during initialization. |