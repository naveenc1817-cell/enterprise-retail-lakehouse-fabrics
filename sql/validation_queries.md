-- Null customer ID check
SELECT COUNT(*) AS failed_records
FROM silver.customers
WHERE customer_id IS NULL;

-- Duplicate order ID check
SELECT order_id, COUNT(*) AS duplicate_count
FROM silver.orders
GROUP BY order_id
HAVING COUNT(*) > 1;

-- Negative price check
SELECT COUNT(*) AS failed_records
FROM silver.order_items
WHERE price < 0;

-- Gold sales fact row count
SELECT COUNT(*) AS gold_sales_fact_count
FROM gold.sales_fact;

-- Data quality results
SELECT *
FROM gold.validation_results;
