# Fabric Pipeline Design

## Pipeline Name

Retail_pipeline

## Purpose

The pipeline automates the full data engineering workflow from ADLS Gen2 ingestion to validated Gold tables.

## Pipeline Flow

ADLS Gen2 Source Files → Copy Data Activity → OneLake Bronze Files → Bronze Delta Tables Notebook → Wait Activity → Silver Transformations Notebook → Wait Activity → Gold Sales Fact Notebook → Wait Activity → Incremental MERGE Notebook → Wait Activity → Data Quality Notebook

## Design Notes

- Copy activity uses folder-level ingestion.
- Source files are copied from ADLS Gen2.
- Raw files are stored in OneLake Bronze.
- Notebooks are executed sequentially.
- Wait activities are used between notebooks to reduce Spark capacity throttling.
- MERGE processing runs after Gold table creation.
- Data quality checks run at the end.
- The pipeline can be scheduled for automated execution.

## Production Value

This design provides repeatable, automated, and observable ETL orchestration using Microsoft Fabric.
