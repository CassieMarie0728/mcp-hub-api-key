# SystemNotifyOwnerBody

## Example Usage

```typescript
import { SystemNotifyOwnerBody } from "@cassie-marie/mcp-hub-api-typescript/models/components";

let value: SystemNotifyOwnerBody = {
  title: "System Alert",
  content: "An important event has occurred.",
};
```

## Fields

| Field                | Type                 | Required             | Description          |
| -------------------- | -------------------- | -------------------- | -------------------- |
| `title`              | *string*             | :heavy_check_mark:   | Notification title   |
| `content`            | *string*             | :heavy_check_mark:   | Notification content |