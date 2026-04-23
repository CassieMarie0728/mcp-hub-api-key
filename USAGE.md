<!-- Start SDK Example Usage [usage] -->
```typescript
import { McpHubApiTypescript } from "@cassie-marie/mcp-hub-api-typescript";

const mcpHubApiTypescript = new McpHubApiTypescript();

async function run() {
  const result = await mcpHubApiTypescript.system.getSystemHealth({
    timestamp: 6433.07,
  });

  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->