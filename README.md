# amazon_sales structured streaming Pipeline using Databicks

## 📌 Overview
This project implements a streaming data pipeline using Databricks, PySpark, and Delta Lake following the medallion architecture (Bronze, Silver, Gold). It ingests CSV files from a cloud storage, cleans and transforms the data, builds a star schema, and exposes aggregated data for business intelligence in Power BI. Orchestration is handled by Databricks Jobs to automate the entire workflow.

## 🏗️ Architecture

![image](https://github.com/KatlegoPhoka2/amazon_sales-structured-streaming-Pipeline/blob/89be793c84dcaeb84414ccdd780d2a9ee77d6386/architecture%20diagram2.png)
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


## 🔄 Pipeline Steps
1. **Data Ingestion**  
   - CSV files are streamed/uploaded to a landing zone (bronze container).  
   - A Databricks notebook reads the files and writes them as Delta tables in the Bronze layer.

2. **Bronze to Silver**  
   - A second notebook reads from Bronze Delta tables.  
   - Data cleaning: handle nulls, remove duplicates, standardise formats, add audit columns.  
   - Write cleaned data to Silver Delta tables.

3. **Silver to Gold**  
   - Build star schema: create dimension tables (e.g., customer, product, time) and fact tables (e.g., sales).  
   - Perform aggregations and business calculations.  
   - Store final datasets in Gold layer.

4. **Orchestration with Databricks Jobs**  
   - A Databricks Job runs the notebooks in sequence, handling dependencies and retries.  
   - Job is triggered on a schedule or via file arrival events (if using Auto Loader or cloud triggers).
![image](https://github.com/KatlegoPhoka2/amazon_sales-structured-streaming-Pipeline/blob/84ac1e1d1d2766c5eaa443b8d5cf0f49c2db584f/pipeline%20job%20graph.png)
5. **BI Reporting**  
   - Power BI connects directly to Gold Delta tables via Databricks SQL endpoint or JDBC/ODBC.  
   - Dashboards visualise key metrics (e.g., sales trends, customer insights).
