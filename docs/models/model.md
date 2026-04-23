# Model

Model within a context


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `id`                                                   | *Optional[str]*                                        | :heavy_minus_sign:                                     | Unique model identifier                                | model-789                                              |
| `context_id`                                           | *Optional[str]*                                        | :heavy_minus_sign:                                     | Associated context ID                                  | context-456                                            |
| `name`                                                 | *Optional[str]*                                        | :heavy_minus_sign:                                     | Model name                                             | UserModel                                              |
| `description`                                          | *OptionalNullable[str]*                                | :heavy_minus_sign:                                     | Optional model description                             | Model representing user entities                       |
| `schema_`                                              | Dict[str, *Any*]                                       | :heavy_minus_sign:                                     | JSON schema or metadata describing the model structure |                                                        |