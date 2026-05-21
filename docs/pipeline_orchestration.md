# Pipeline Orchestration

## Pipeline Name

Retail_pipeline

## Purpose

The pipeline orchestrates the full lakehouse workflow from source ingestion to reporting-ready Gold tables.

## Pipeline Flow

Copy Files → Create Bronze Tables → Wait → Bronze to Silver Transformations → Wait → Create Gold Sales Fact → Wait → Incremental MERGE Upserts → Wait → Data Quality Checks

## Activities

| Activity | Purpose |
|---|---|
| Copy Data | Copies raw files from ADLS Gen2 to OneLake |
| Bronze Notebook | Creates Bronze Delta tables |
| Wait Activity | Reduces Spark session contention |
| Silver Notebook | Cleans and standardizes data |
| Gold Notebook | Builds analytics-ready sales fact table |
| MERGE Notebook | Applies incremental updates and inserts |
| Data Quality Notebook | Runs validation checks |

## Wait Activity Design

Wait activities are included between notebook executions to reduce Spark session contention and capacity throttling.

This was added because Fabric capacity can return TooManyRequestsForCapacity errors when notebook jobs are triggered too quickly.

Recommended wait duration: 60 to 120 seconds.

## Production Value

This orchestration pattern provides:

- End-to-end automation
- Dependency chaining
- Repeatable ETL execution
- Centralized workflow control
- Production-style monitoring
