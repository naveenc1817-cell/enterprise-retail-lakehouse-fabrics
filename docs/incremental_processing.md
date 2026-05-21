
## `docs/incremental_processing.md`

```markdown
# Incremental Processing

## Overview

This project implements incremental processing using Delta Lake MERGE.

The incremental files used are:

- customer_updates.csv
- order_updates.csv

These files simulate CDC-style updates from source systems.

## MERGE Logic

The MERGE operation compares incoming update records with existing Silver records using business keys.

Customer key:

```text
customer_id
