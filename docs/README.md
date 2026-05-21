# Enterprise Retail Lakehouse using Microsoft Fabric

## Project Overview

This project implements an end-to-end enterprise retail lakehouse pipeline using Microsoft Fabric, OneLake, ADLS Gen2, PySpark, Delta Lake, Fabric Data Pipelines, and Power BI.

The goal of this project is to build a production-style data engineering solution that ingests raw retail data, transforms it through Bronze, Silver, and Gold layers, supports incremental upserts using Delta MERGE, validates data quality, and serves analytics through Power BI.


## Business Problem

Retail organizations receive data from multiple systems such as customers, orders, products, sellers, payments, and logistics. Raw files are not directly suitable for reporting because they may contain duplicates, inconsistent data types, missing values, and non-business-friendly fields.

This project solves that problem by creating a reliable lakehouse pipeline that converts raw files into clean, validated, analytics-ready Gold tables for business reporting.

## Architecture

ADLS Gen2
   ↓
Fabric Data Pipeline
   ↓
OneLake Bronze Files
   ↓
Bronze Delta Tables
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

For detailed architecture, see [Architecture Diagram](../architecture/architecture_diagram.md).
