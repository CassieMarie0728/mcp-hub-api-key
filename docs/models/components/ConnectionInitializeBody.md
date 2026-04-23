# ConnectionInitializeBody


## Fields

| Field                                                 | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `clientName`                                          | *String*                                              | :heavy_check_mark:                                    | Human-readable name of the MCP Hub client.            |
| `clientVersion`                                       | *String*                                              | :heavy_check_mark:                                    | Semantic version of the MCP Hub client.               |
| `protocolVersion`                                     | *Optional\<String>*                                   | :heavy_minus_sign:                                    | Preferred MCP protocol version.                       |
| `clientCapabilities`                                  | Map\<String, *Object*>                                | :heavy_minus_sign:                                    | Client capabilities advertised during initialization. |