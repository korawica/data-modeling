# Master

| Field Name      |  Alias   | Data Type | PK | Description                              |
|-----------------|:--------:|-----------|----|------------------------------------------|
| `created_at`    | created  | TIMESTAMP |    | Timestamp when the data was created      |
| `updated_at`    | updated  | TIMESTAMP |    | Timestamp when the data was last updated |

## SCD2

| Field Name     |    Alias    | Data Type | PK | Description                                  |
|----------------|:-----------:|-----------|----|----------------------------------------------|
| `id`           |     id      | STRING    | Y  | Surrogate key that unique per row of data    |
| `bussiness_id` |   bus_id    | STRING    |    |                                              |
| `deleted_flag` |  deleted_f  | BOOLEAN   |    | Delete flag that the data does not available |
| `start_date`   | valid_start | TIMESTAMP |    | Timestamp when the data start to use         |
| `end_date`     |  valid_end  | TIMESTAMP |    | Timestamp when the data end to use           |
