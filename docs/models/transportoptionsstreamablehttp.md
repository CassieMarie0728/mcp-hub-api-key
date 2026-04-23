# TransportOptionsStreamableHTTP

Transport options for streamable HTTP MCP servers.


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `url`                                                         | *str*                                                         | :heavy_check_mark:                                            | HTTP endpoint for the MCP server transport.                   |
| `headers`                                                     | Dict[str, *str*]                                              | :heavy_minus_sign:                                            | Optional HTTP headers sent with transport requests.           |
| `session_id`                                                  | *Optional[str]*                                               | :heavy_minus_sign:                                            | Optional session identifier returned by the remote transport. |