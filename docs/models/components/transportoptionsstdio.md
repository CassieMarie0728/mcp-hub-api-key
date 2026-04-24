# TransportOptionsStdio

Transport options for stdio-based MCP servers.

## Example Usage

```typescript
import { TransportOptionsStdio } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: TransportOptionsStdio = {
  command: "<value>",
};
```

## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `command`                                          | *string*                                           | :heavy_check_mark:                                 | Executable used to launch the MCP server process.  |
| `args`                                             | *string*[]                                         | :heavy_minus_sign:                                 | Optional command-line arguments.                   |
| `env`                                              | Record<string, *string*>                           | :heavy_minus_sign:                                 | Environment variables passed to the child process. |
| `cwd`                                              | *string*                                           | :heavy_minus_sign:                                 | Working directory for the child process.           |