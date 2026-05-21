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
```text

## Wait Activity Design

Wait activities are included between notebook executions to reduce Spark session contention and capacity throttling.

This was added because Fabric capacity can return TooManyRequestsForCapacity errors when notebook jobs are triggered too quickly.

Recommended wait duration:

60 to 120 seconds
   ↓
Power BI Dashboard
