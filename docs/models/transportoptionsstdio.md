# TransportOptionsStdio

Transport options for stdio-based MCP servers.


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `command`                                          | *str*                                              | :heavy_check_mark:                                 | Executable used to launch the MCP server process.  |
| `args`                                             | List[*str*]                                        | :heavy_minus_sign:                                 | Optional command-line arguments.                   |
| `env`                                              | Dict[str, *str*]                                   | :heavy_minus_sign:                                 | Environment variables passed to the child process. |
| `cwd`                                              | *Optional[str]*                                    | :heavy_minus_sign:                                 | Working directory for the child process.           |