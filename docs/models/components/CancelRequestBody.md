# CancelRequestBody


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `requestId`                                    | *String*                                       | :heavy_check_mark:                             | Identifier of the in-flight request to cancel. |
| `reason`                                       | *JsonNullable\<String>*                        | :heavy_minus_sign:                             | Optional user-facing cancellation reason.      |