# CancelConnectionRequestRequest


## Fields

| Field                                                             | Type                                                              | Required                                                          | Description                                                       | Example                                                           |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `connectionId`                                                    | *String*                                                          | :heavy_check_mark:                                                | Unique identifier of the connection.                              |                                                                   |
| `cancelRequestBody`                                               | [CancelRequestBody](../../models/components/CancelRequestBody.md) | :heavy_check_mark:                                                | N/A                                                               | {<br/>"requestId": "req-123abc",<br/>"reason": "User navigated away"<br/>} |