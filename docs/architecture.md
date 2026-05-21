# Architecture

## Overview

This project implements an enterprise retail lakehouse architecture using Microsoft Fabric, OneLake, ADLS Gen2, PySpark, Delta Lake, Fabric Data Pipelines, and Power BI.

## Architecture Flow

```text
ADLS Gen2
   ↓
Fabric Data Pipeline
   ↓
OneLake Bronze Files
   ↓
Bronze Delta Tables Notebook
   ↓
Wait Activity
   ↓
Silver Transformation Notebook
   ↓
Wait Activity
   ↓
Gold Sales Fact Notebook
   ↓
Wait Activity
   ↓
Incremental MERGE Notebook
   ↓
Wait Activity
   ↓
Data Quality Validation Notebook
   ↓
Power BI Dashboard
```

## Design Explanation

ADLS Gen2 acts as the external source landing zone.

Fabric Data Pipeline copies raw files into OneLake Bronze storage.

PySpark notebooks process the data through Bronze, Silver, and Gold layers.

Delta Lake is used for:

- ACID transactions
- Delta versioning
- MERGE upserts
- Partitioning
- Optimization

Power BI consumes Gold tables for analytics and operational reporting.

## Production Design Decisions

- ADLS Gen2 used as source storage
- OneLake used as Fabric-native lakehouse storage
- Delta tables used for ACID transactions
- Medallion architecture implemented
- MERGE used for incremental processing
- Data quality checks persisted for monitoring
- Gold tables partitioned by year and month

## Spark Capacity Handling

Fabric trial or limited capacity can hit Spark concurrency or API rate limits when multiple notebook activities start too quickly.

To reduce this issue, Wait activities were added between notebook executions.

Benefits:

- Improved pipeline stability
- Reduced Spark contention
- Better sequential orchestration
- Fewer TooManyRequestsForCapacity errors

## Wait Activity Design

Recommended wait duration:

```text
60 to 120 seconds
```
