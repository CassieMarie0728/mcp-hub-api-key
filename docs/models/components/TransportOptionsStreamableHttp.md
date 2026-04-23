# TransportOptionsStreamableHttp

Transport options for streamable HTTP MCP servers.


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `url`                                                         | *String*                                                      | :heavy_check_mark:                                            | HTTP endpoint for the MCP server transport.                   |
| `headers`                                                     | Map\<String, *String*>                                        | :heavy_minus_sign:                                            | Optional HTTP headers sent with transport requests.           |
| `sessionId`                                                   | *Optional\<String>*                                           | :heavy_minus_sign:                                            | Optional session identifier returned by the remote transport. |