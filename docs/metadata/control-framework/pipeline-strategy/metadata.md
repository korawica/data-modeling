# Metadata

## Schema Config

### Pipeline

|       Column        | Data Type |  PK  | Description                                       |
|:-------------------:|-----------|:----:|---------------------------------------------------|
|    pipeline_name    | STRING    |  Y   | Pipeline name                                     |
|      set_date       | INTEGER   |      | A number for decrease process date before running |
|      frequency      | STRING    |      | D, W, M, Q, Y                                     |
|   data_frequency    | STRING    |      | D, W, M, Q, Y                                     |
|     active_flag     | BOOLEAN   |      | Active flag for this config data                  |
|      update_by      | STRING    |      | Who that add or update this config data           |
|     update_date     | DATETIME  |      | Update datetime of this config data               |

### Node Group

|     Column      | Data Type |  PK  | Description                             |
|:---------------:|-----------|:----:|-----------------------------------------|
| node_group_name | STRING    |  Y   | Node process group name                 |
|  pipeline_name  | STRING    |      |                                         |
|    priority     | INTEGER   |      |                                         |
|   active_flag   | BOOLEAN   |      | Active flag for this config data        |
|    update_by    | STRING    |      | Who that add or update this config data |
|   update_date   | DATETIME  |      | Update datetime of this config data     |

### Node

|     Column      | Data Type | PK | Description                             |
|:---------------:|-----------|:--:|-----------------------------------------|
|    node_name    | STRING    | Y  | Node process name                       |
| node_group_name | STRING    |    |                                         |
|    priority     | INTEGER   |    |                                         |
|    load_type    | STRING    |    |                                         |
| data_load_type  | STRING    |    | T, D, F, SCD1, SCD2_D, SCD2_F, SCD2_T   |
|     extras      | JSON      |    |                                         |
|   active_flag   | BOOLEAN   |    | Active flag for this config data        |
|    update_by    | STRING    |    | Who that add or update this config data |
|   update_date   | DATETIME  |    | Update datetime of this config data     |

### Node Dependency

|        Column        | Data Type | PK | Description                                                  |
|:--------------------:|-----------|:--:|--------------------------------------------------------------|
|      node_name       | STRING    | Y  | Node process name                                            |
| node_dependency_name | STRING    | Y  | Node process dependency name                                 |
| dependency_set_date  | INTEGER   |    | A number for decrease dependency process date before running |
|     active_flag      | BOOLEAN   |    | Active flag for this config data                             |
|      update_by       | STRING    |    | Who that add or update this config data                      |
|     update_date      | DATETIME  |    | Update datetime of this config data                          |


!!! note

    The `extras` field on the node table contain all of necessary node arguments;

    ```text
    extras
      ├─ files
      │   ├─ name
      │   ├─ path
      │   ├─ header
      │   ╰─ encoding
      ├─ storage
      │   ├─ system
      │   ╰─ container
      ╰─ framwork
          ├─ archiving
          ╰─ timeout
    ```

## Schema Data

### Pipeline Logging

|        Column         | Data Type | PK | Description                                                |
|:---------------------:|-----------|:--:|------------------------------------------------------------|
|     pipeline_name     | STRING    | Y  | Pipeline name                                              |
|     process_date      | DATETIME  |    |                                                            |
|   next_process_date   | DATETIME  |    |                                                            |
| previous_process_date | DATETIME  |    |                                                            |
|       data_date       | DATETIME  |    |                                                            |
|    next_data_date     | DATETIME  |    |                                                            |
|  previous_data_date   | DATETIME  |    |                                                            |
|     running_flag      | BOOLEAN   |    | A running flag for tacking this pipeline is running or not |
|       update_by       | STRING    |    | Who that add or update this config data                    |
|      update_date      | DATETIME  |    | Update datetime of this config data                        |

### Pipeline Watermark

|    Column     | Data Type | PK | Description                             |
|:-------------:|-----------|:--:|-----------------------------------------|
| pipeline_name | STRING    | Y  | Pipeline name                           |
|  process_id   | INTEGER   | Y  |                                         |
|  start_date   | DATETIME  |    |                                         |
|   end_date    | DATETIME  |    |                                         |
| process_date  | DATETIME  |    |                                         |
|    status     | STRING    |    | Success, Failed, Start                  |
|      log      | STRING    |    |                                         |
|   tracking    | JSON      |    |                                         |
|   update_by   | STRING    |    | Who that add or update this config data |
|  update_date  | DATETIME  |    | Update datetime of this config data     |

### Node Logging

|    Column    | Data Type | PK | Description                             |
|:------------:|-----------|:--:|-----------------------------------------|
|  node_name   | STRING    | Y  | Node process name                       |
|  process_id  | INTEGER   | Y  |                                         |
|  start_date  | DATETIME  |    |                                         |
|   end_date   | DATETIME  |    |                                         |
| process_date | DATETIME  |    |                                         |
|    status    | STRING    |    | Success, Failed, Start                  |
|     log      | STRING    |    |                                         |
|   records    | JSON      |    |                                         |
|  update_by   | STRING    |    | Who that add or update this config data |
| update_date  | DATETIME  |    | Update datetime of this config data     |


!!! note

    The `records` field on the node log table contain all of necessary result records;

    ```text
    records
      ├─ src
      │   ├─ count
      │   ╰─ control_count
      ╰─ tgt
          ├─ count
          ╰─ control_count
    ```

## Query

```sql
SELECT
      pipe.pipeline_name            AS pipeline_name
    , node_group.node_group_name    AS node_group_name
    , node.node_name                AS node_name
FROM control.control_pipeline       AS pipe
JOIN control.control_node_group     AS node_group
    ON  pipe.pipeline_name   = node_group.node_group_name
JOIN control.control_node           AS node
    ON  node_group.node_name = node.node_name
WHERE
        pipe.active_flag is true
    AND node_group.active_flag is true
    AND node.active_flag is true
```
