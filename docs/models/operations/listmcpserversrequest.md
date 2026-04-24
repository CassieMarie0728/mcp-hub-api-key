# ListMcpServersRequest

## Example Usage

```typescript
import { ListMcpServersRequest } from "@cassie-marie/mcp-hub-api-typescript/models/operations";

let value: ListMcpServersRequest = {};
```

## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `region`                                               | *string*                                               | :heavy_minus_sign:                                     | Filter servers by region                               |
| `status`                                               | [operations.Status](../../models/operations/status.md) | :heavy_minus_sign:                                     | Filter servers by status (e.g., online, offline)       |