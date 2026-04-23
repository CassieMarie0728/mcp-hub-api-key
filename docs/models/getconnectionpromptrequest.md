# GetConnectionPromptRequest


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `connection_id`                                              | *str*                                                        | :heavy_check_mark:                                           | Unique identifier of the connection.                         |                                                              |
| `prompt_name`                                                | *str*                                                        | :heavy_check_mark:                                           | Name of the prompt template.                                 |                                                              |
| `prompt_get_body`                                            | [Optional[models.PromptGetBody]](../models/promptgetbody.md) | :heavy_minus_sign:                                           | N/A                                                          | {<br/>"arguments": {<br/>"targetLanguage": "fr"<br/>}<br/>}  |