# CancelRequestBody


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `request_id`                                   | *str*                                          | :heavy_check_mark:                             | Identifier of the in-flight request to cancel. |
| `reason`                                       | *OptionalNullable[str]*                        | :heavy_minus_sign:                             | Optional user-facing cancellation reason.      |