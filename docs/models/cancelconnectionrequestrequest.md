# CancelConnectionRequestRequest


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    | Example                                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `connection_id`                                                | *str*                                                          | :heavy_check_mark:                                             | Unique identifier of the connection.                           |                                                                |
| `cancel_request_body`                                          | [models.CancelRequestBody](../models/cancelrequestbody.md)     | :heavy_check_mark:                                             | N/A                                                            | {<br/>"requestId": "req-123abc",<br/>"reason": "User navigated away"<br/>} |