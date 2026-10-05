# E-Commerce ETL Data Pipeline & Dimensional Warehouse

An end-to-end batch ETL data pipeline that processes over 1,000,000 raw e-commerce transaction records from Kaggle, cleanses and deduplicates the data using PySpark, models a star schema data warehouse, and populates a local PostgreSQL database for downstream SQL analytics.

---

## 🏗️ Architecture Overview

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/94c6564b-a66d-4a0a-bf29-b99f5008c033" />

# Tech Stack
Processing Engine: Apache Spark (PySpark)

Database & Warehouse: PostgreSQL

Language: Python

Data Access / Connectors: PySpark JDBC, psycopg2

Analytics & Verification: Pandas, SQL

Environment: Google Colab / Linux

# Data Model (Star Schema)
The data warehouse uses a Star Schema design to optimize query performance and transactional reporting:

fact_sales (Fact Table): Contains quantitative metrics (quantity, unit_price, total_amount) along with keys pointing to dimensions.

dim_customer (Dimension Table): Unique customer profiles and locations.

dim_product (Dimension Table): Unique product descriptions and pricing details.

dim_time (Dimension Table): Time grain details (year, month, day, hour) extracted from timestamps.

# Key Pipeline Features
Automated Data Quality & Cleaning: Removes invalid orders (negative unit prices, missing customer IDs, cancelled invoices).

Deduplication Engine: Implements Spark dropDuplicates windowing to ensure strict Primary Key integrity on dimensional entities before JDBC load.

Automated Schema Provisioning: Executes DDL scripts via psycopg2 to build relational constraints and table relationships dynamically.

Batch JDBC Database Ingestion: Writes PySpark DataFrames into PostgreSQL tables using the official PostgreSQL JDBC driver.

## 📊 Sample Analytical Output

### Top 5 Revenue-Generating Countries

| Rank | Country            |     Total Revenue | Total Orders |
| :--: | ------------------ | ----------------: | -----------: |
| 🥇 1 | **United Kingdom** | **£8,983,124.32** |   **19,214** |
| 🥈 2 | **EIRE**           |   **£615,519.10** |      **582** |
| 🥉 3 | **Netherlands**    |   **£548,223.14** |      **230** |
|   4  | **Germany**        |   **£422,125.40** |      **802** |
|   5  | **France**         |   **£328,121.20** |      **610** |

> **Insight:** The United Kingdom generated the highest revenue by a significant margin, accounting for the majority of total sales in the dataset.



# How to Run
Clone or open the project notebook ECommerce_ETL_Pipeline.ipynb in Google Colab.

Supply your Kaggle API key credentials in Cell 2 (KAGGLE_USERNAME and KAGGLE_KEY).

Run all cells sequentially (Runtime > Run all).
