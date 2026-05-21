# Production Features

This project includes multiple production-style data engineering features.

## Implemented Features

| Feature | Description |
|---|---|
| Medallion Architecture | Bronze, Silver, and Gold layered design |
| ADLS Gen2 Ingestion | External source storage ingestion |
| OneLake Storage | Fabric-native lakehouse storage |
| Delta Lake Tables | ACID-compliant storage format |
| PySpark Transformations | Scalable data processing |
| Delta MERGE | Incremental upsert processing |
| Delta Versioning | Table history and auditability |
| Data Quality Checks | Validation framework for business rules |
| Pipeline Orchestration | End-to-end Fabric pipeline |
| Wait Activities | Reduces Spark capacity throttling |
| Gold Partitioning | Partitioned by order year and month |
| OPTIMIZE | Delta file compaction |
| VACUUM | Delta storage cleanup |
| Power BI Dashboard | Executive and operational reporting |

## Why These Features Matter

These features make the project closer to a real enterprise lakehouse implementation rather than a simple CSV-to-dashboard project.

The project demonstrates:

- Scalable ingestion
- Clean transformation layers
- Incremental processing
- Reliable Delta transactions
- Data quality monitoring
- Analytics-ready Gold tables
- Power BI reporting
