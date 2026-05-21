```markdown
# Data Model

## Source Tables

| Source File | Purpose |
|---|---|
| olist_customers_dataset | Customer profile and location data |
| olist_orders_dataset | Order lifecycle and status data |
| olist_order_items_dataset | Product-level order transactions |
| olist_order_payments_dataset | Payment method and payment amount data |
| olist_products_dataset | Product attributes and category data |
| olist_sellers_dataset | Seller profile and location data |
| olist_geolocation_dataset | Zip-code based geolocation data |
| product_category_name_translation | Product category translation lookup |
| customer_updates | Incremental customer update data |
| order_updates | Incremental order update data |

## Silver Tables

| Table | Description |
|---|---|
| silver.customers | Cleaned customer dimension |
| silver.orders | Cleaned order data with timestamp fields |
| silver.order_items | Cleaned order line item transactions |
| silver.payments | Cleaned payment data |
| silver.products | Product dimension with English category names |
| silver.sellers | Cleaned seller dimension |

## Gold Tables

| Table | Description |
|---|---|
| gold.sales_fact | Denormalized analytics fact table |
| gold.validation_results | Data quality validation output |

## Gold Sales Fact

The `gold.sales_fact` table combines orders, customers, products, sellers, payments, and order items into one analytics-ready table for Power BI reporting.

Important fields:

- order_id
- customer_id
- product_id
- seller_id
- order_status
- order_purchase_timestamp
- order_year
- order_month
- customer_state
- seller_state
- product_category_name_english
- payment_type
- price
- freight_value
- total_sale_amount
