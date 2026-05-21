# Power BI Dashboard

## Overview

The Power BI dashboard connects to the Gold semantic model created from the lakehouse Gold tables.

Main table used: gold.sales_fact

Monitoring table used: gold.validation_results

## Executive Summary Page

KPIs:

- Total Revenue
- Total Orders
- Average Order Value
- Total Customers
- Total Sellers

Visuals:

- Monthly Revenue Trend
- Revenue by State
- Top Product Categories by Revenue

## Operational Monitoring Page

Visuals:

- Validation results table
- Failed records by validation rule
- Data quality status
- Validation timestamp

## Measures Created

Total Revenue = SUM(sales_fact[total_sale_amount])

Total Orders = DISTINCTCOUNT(sales_fact[order_id])

Average Order Value = DIVIDE([Total Revenue], [Total Orders])

Total Customers = DISTINCTCOUNT(sales_fact[customer_id])

Total Sellers = DISTINCTCOUNT(sales_fact[seller_id])

## Dashboard Purpose

The dashboard provides business insights and operational visibility into the lakehouse pipeline.
