# Requirement Gathering

The most important task that effect to role responsibility is the
**Requirement Gathering** step.

## Project Starter

| Question                                                 | Answer                                                                         |
|----------------------------------------------------------|--------------------------------------------------------------------------------|
| What responsibility of a data engineer on this project?  | Load all data sources from RDBMS to the warehouse for making dashboards by DA. |

## Data Component

| Question                                                        | Answer                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| What is the data source system type?                            | RDBMS (Postgres, MySQL, SQL Server, etc.),<br>NO-SQL (MongoDB, Elastic),<br>API                                                          |
| What is data compute service to extract from the source system? | Docker Application (FastAPI), Batch job via Cloud services (Azure Batch, AWS Batch, etc.) ETL Services (Azure Databricks, AWS Glue etc.) |
| How to authenticate to the data source system?                  | Use user and password. Use service account on that cloud provider.                                                                       |

## Data Source

These questions use per data source.

| Question                                                                 | Answer                                                                                  |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| What is data source name?                                                |                                                                                         |
| What is the primary of this data source?                                 |                                                                                         |
| How to ingest data to this data source?                                  |                                                                                         |
| How to incremental load of this data source?                             | The filter fields for filter period of changed data like create_date, updated_date etc. |
| What is loading type of this data source?                                | Incremental via Merge or Append.<br>Full-dump load.                                     |
| When to load this data source that does not effect to the source system? | Every 1:30 AM to 3:00AM is good or not?                                                 |
