# RequestDetails

Details and event history of a request

## Example Usage

```typescript
import { RequestDetails } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: RequestDetails = {
  requestId: "req-123abc",
  status: "completed",
  events: [
    {
      timestamp: new Date("2023-03-01T10:00:01Z"),
      type: "request_sent",
      message: "Request sent to MCP server",
    },
    {
      timestamp: new Date("2023-03-01T10:00:02Z"),
      type: "response_received",
      message: "Response received from MCP server",
    },
  ],
};
```

## Fields

| Field                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                               | Required                                                                                                                                                                                                                           | Description                                                                                                                                                                                                                        | Example                                                                                                                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `requestId`                                                                                                                                                                                                                        | *string*                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                 | Unique request identifier                                                                                                                                                                                                          | req-123abc                                                                                                                                                                                                                         |
| `status`                                                                                                                                                                                                                           | [components.RequestDetailsStatus](../../models/components/requestdetailsstatus.md)                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                 | Request status                                                                                                                                                                                                                     | completed                                                                                                                                                                                                                          |
| `events`                                                                                                                                                                                                                           | [components.RequestDetailsEvents](../../models/components/requestdetailsevents.md)[]                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                 | List of events related to the request                                                                                                                                                                                              | [<br/>{<br/>"timestamp": "2023-03-01T10:00:01Z",<br/>"type": "request_sent",<br/>"message": "Request sent to MCP server"<br/>},<br/>{<br/>"timestamp": "2023-03-01T10:00:02Z",<br/>"type": "response_received",<br/>"message": "Response received from MCP server"<br/>}<br/>] |