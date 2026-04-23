# TransportOptionsStdio

Transport options for stdio-based MCP servers.


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `command`                                          | *String*                                           | :heavy_check_mark:                                 | Executable used to launch the MCP server process.  |
| `args`                                             | List\<*String*>                                    | :heavy_minus_sign:                                 | Optional command-line arguments.                   |
| `env`                                              | Map\<String, *String*>                             | :heavy_minus_sign:                                 | Environment variables passed to the child process. |
| `cwd`                                              | *Optional\<String>*                                | :heavy_minus_sign:                                 | Working directory for the child process.           |