# Model

Model within a context


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Unique model identifier                                | model-789                                              |
| `contextId`                                            | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Associated context ID                                  | context-456                                            |
| `name`                                                 | *Optional\<String>*                                    | :heavy_minus_sign:                                     | Model name                                             | UserModel                                              |
| `description`                                          | *JsonNullable\<String>*                                | :heavy_minus_sign:                                     | Optional model description                             | Model representing user entities                       |
| `schema`                                               | Map\<String, *Object*>                                 | :heavy_minus_sign:                                     | JSON schema or metadata describing the model structure |                                                        |