# amazon_sales structured streaming Pipeline using Databicks

## 📌 Overview
This project implements a streaming data pipeline using Databricks, PySpark, and Delta Lake following the medallion architecture (Bronze, Silver, Gold). It ingests CSV files from a cloud storage, cleans and transforms the data, builds a star schema, and exposes aggregated data for business intelligence in Power BI. Orchestration is handled by Databricks Jobs to automate the entire workflow.

## 🏗️ Architecture

![image]()
- **Bronze Layer**: Raw CSV files are loaded as Delta tables, preserving the original data.
- **Silver Layer**: Data is cleaned, deduplicated, and validated using PySpark; results stored as Delta tables.
- **Gold Layer**: Star schema modeling (fact and dimension tables) and aggregations for analytical queries.
- **Orchestration**: Databricks Jobs schedule and run the pipeline notebooks/tasks.
- **BI & Analytics**: Gold tables are connected to Power BI for interactive dashboards.

## 🛠️ Technologies Used
- **Databricks** (Workspace, Jobs, Delta Lake)
- **Apache Spark** (PySpark, SQL)
- **Delta Lake** (ACID transactions, time travel)
- **Power BI** (Data visualization)
- **Cloud Storage** (e.g., AWS S3 / Azure Data Lake / DBFS)
- **Python** (for additional transformations)
