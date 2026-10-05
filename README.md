# E-Commerce ETL Data Pipeline & Dimensional Warehouse

An end-to-end batch ETL data pipeline that processes over 1,000,000 raw e-commerce transaction records from Kaggle, cleanses and deduplicates the data using PySpark, models a star schema data warehouse, and populates a local PostgreSQL database for downstream SQL analytics.

---

## 🏗️ Architecture Overview

![E-Commerce ETL Architecture](architecture_diagram.png)

```text
[ Raw Kaggle CSV Dataset ] (1M+ Records)
           │
           ▼
[ PySpark Data Engine ] ──► Data Cleaning & Type Casting
           │            ──► Deduplication & Primary Key Integrity
           │            ──► Dimensional Modeling (Star Schema)
           ▼
[ PostgreSQL Warehouse ] ──► Dim_Customer, Dim_Product, Dim_Time
           │            ──► Fact_Sales (Foreign Key Constraints)
           ▼
[ Downstream SQL Analytics ] ──► pandas / Business Intelligence
