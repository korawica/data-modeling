# Requirement Gathering

## Project Starter

| Component | Question                                                        | Answer                                                                                                                                   |
|-----------|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Infra     | What is the data source system type?                            | RDBMS (Postgres, MySQL, SQL Server, etc.),<br>NO-SQL (MongoDB, Elastic),<br>API                                                          |
|           | What is data compute service to extract from the source system? | Docker Application (FastAPI), Batch job via Cloud services (Azure Batch, AWS Batch, etc.) ETL Services (Azure Databricks, AWS Glue etc.) |
|           | How to authenticate to the data source system?                  | Use user and password. Use service account on that cloud provider.                                                                       |

## Data Ingestion

| Component   | Question                                     | Answer                                                                                  |
|-------------|----------------------------------------------|-----------------------------------------------------------------------------------------|
| Data source | How to incremental load of this data source? | The filter fields for filter period of changed data like create_date, updated_date etc. |
|             |                                              |                                                                                         |
|             |                                              |                                                                                         |
