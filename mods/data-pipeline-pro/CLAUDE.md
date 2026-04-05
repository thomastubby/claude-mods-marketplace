# Data Pipeline Pro

Deep expertise in modern data engineering. Apply automatically when working with data pipelines, ETL, analytics engineering, or data infrastructure.

## dbt

- Write idiomatic dbt models: staging (1:1 source mapping), intermediate (business logic), marts (output)
- Use `ref()` and `source()` consistently — never hardcode table names
- Incremental models: use `unique_key` + `merge` strategy, with `is_incremental()` filter
- Testing: `not_null`, `unique`, `relationships`, `accepted_values` on every model
- Use `dbt_utils` for surrogate keys, date spines, and pivot operations

## Orchestration

- Airflow: DAGs with proper `retries`, `retry_delay`, `sla`, and `on_failure_callback`
- Task dependencies via `>>` operator, use `TaskGroup` for organization
- XCom for small metadata only — never pass dataframes through XCom
- Prefer `@task` decorator (TaskFlow API) over classic operators for Python tasks
- Dagster/Prefect alternatives: mention when simpler scheduling fits better

## Warehouse Optimization

### Snowflake
- Cluster keys on large tables for common filter columns
- Warehouse sizing: start X-Small, scale up for specific queries, auto-suspend
- Use `COPY INTO` for bulk loads, not `INSERT INTO SELECT`
- Transient tables for staging/temp data to avoid Time Travel costs

### BigQuery
- Partition by date, cluster by high-cardinality filter columns
- Use `MERGE` for upserts, not delete-then-insert
- Materialize expensive CTEs as tables — BigQuery re-executes CTEs
- Slot reservations for predictable costs on production workloads

## Data Modeling

- Star schema for BI/reporting workloads (fact + dimension tables)
- One Big Table (OBT) for simple analytics on modern columnar warehouses
- Activity schema for event-driven analytics
- Always include `created_at`, `updated_at`, and a surrogate key

## When to Use What

- < 1GB: DuckDB or plain SQL. Don't overthink it.
- 1GB - 100GB: Warehouse (Snowflake/BigQuery) + dbt
- 100GB+: Spark or Databricks for transforms, warehouse for serving
- Real-time: Kafka + Flink or Materialize, not batch with 1-minute schedules
