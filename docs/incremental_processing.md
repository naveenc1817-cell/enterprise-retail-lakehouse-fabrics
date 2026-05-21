# Incremental Processing

## Overview

This project implements incremental processing using Delta Lake MERGE.

The incremental files used are:

- customer_updates.csv
- order_updates.csv

These files simulate CDC-style updates from source systems.

## MERGE Logic

The MERGE operation compares incoming update records with existing Silver records using business keys.

Customer key: customer_id

Order key: order_id

## MERGE Behavior

| Condition | Action |
|---|---|
| Matching record exists | Update existing record |
| Matching record does not exist | Insert new record |

## Customer MERGE Example

The customer update file contains:

- One existing customer record to update
- One new customer record to insert

Delta MERGE result:

- numSourceRows = 2
- numTargetRowsUpdated = 1
- numTargetRowsInserted = 1
- operation = MERGE

## Production Value

Incremental processing avoids full reloads and supports scalable data processing.

Benefits:

- Lower compute cost
- Faster pipeline execution
- Transactional updates
- Delta version tracking
- CDC-style pipeline pattern
