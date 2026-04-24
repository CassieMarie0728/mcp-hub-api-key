# InlineResponse2008

## Example Usage

```typescript
import { InlineResponse2008 } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: InlineResponse2008 = {};
```

## Fields

| Field                                                                                          | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `results`                                                                                      | [components.Results](../../models/components/results.md)[]                                     | :heavy_minus_sign:                                                                             | Query results as an array of objects                                                           |
| `metadata`                                                                                     | [components.InlineResponse2008Metadata](../../models/components/inlineresponse2008metadata.md) | :heavy_minus_sign:                                                                             | Additional metadata about the query execution                                                  |