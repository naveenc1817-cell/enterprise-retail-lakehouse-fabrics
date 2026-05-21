# Transformation Logic

## Bronze Layer

The Bronze layer converts raw files from OneLake into Delta tables.

Key steps:

- Read raw CSV files from OneLake Bronze folder
- Infer schema
- Add audit metadata
- Save data as Delta tables

Audit columns:

- bronze_load_timestamp
- source_file_name

## Silver Layer

The Silver layer standardizes and cleans the raw data.

| Transformation | Purpose |
|---|---|
| Deduplication | Removes duplicate business records |
| Data type casting | Converts columns into correct data types |
| Timestamp conversion | Converts date strings into timestamp columns |
| Category translation | Maps Portuguese product categories to English |
| Audit timestamp | Tracks when Silver records were processed |
| Dimensional cleanup | Standardizes customers, products, sellers, orders, and payments |

## Gold Layer

The Gold layer builds business-ready analytics tables.

The main Gold table is gold.sales_fact.

This table joins:

- silver.orders
- silver.customers
- silver.order_items
- silver.products
- silver.sellers
- silver.payments

Calculated metric:

total_sale_amount = price + freight_value

Partition columns:

- order_year
- order_month
