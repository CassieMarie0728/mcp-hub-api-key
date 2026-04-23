# CompletionsBody


## Fields

| Field                                  | Type                                   | Required                               | Description                            |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `server_id`                            | *str*                                  | :heavy_check_mark:                     | Target MCP server ID                   |
| `context_id`                           | *str*                                  | :heavy_check_mark:                     | Target context ID                      |
| `model_id`                             | *str*                                  | :heavy_check_mark:                     | Target model ID                        |
| `prompt`                               | *str*                                  | :heavy_check_mark:                     | Prompt string to complete              |
| `parameters`                           | Dict[str, *Any*]                       | :heavy_minus_sign:                     | Optional parameters for the completion |