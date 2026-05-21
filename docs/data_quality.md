# Data Quality Framework

## Overview

A lightweight data quality framework was implemented using PySpark.

The validation results are written to gold.validation_results.

## Validation Checks

| Check | Purpose |
|---|---|
| Null Customer IDs | Ensures customer records have valid keys |
| Duplicate Orders | Ensures order IDs are unique |
| Negative Prices | Detects invalid financial values |

## Validation Output Columns

| Column | Description |
|---|---|
| validation_check | Name of the validation rule |
| failed_records | Number of records that failed the check |
| validation_timestamp | Time when validation was executed |

## Production Value

The data quality layer improves trust in the reporting layer and provides visibility into pipeline health.

It supports:

- Data validation
- Operational monitoring
- Power BI quality reporting
- Auditability
- Early detection of data issues
