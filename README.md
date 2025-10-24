# Data Warehouse and Analytics Project

Welcome to the Data Warehouse and Analytics Project repository! 🚀  
This project demonstrates a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry patterns and practical SQL-based analytics while keeping the original scope and wording as much as possible.

Table of Contents
- Project Requirements
  - Building the Data Warehouse (Data Engineering)
- BI: Analytics & Reporting (Data Analytics)
- Quickstart / How to run
- Files and structure
- License
- About Me

🚀 Project Requirements
Building the Data Warehouse (Data Engineering)

Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

Specifications
- Data Sources: Import data from two source systems (ERP and CRM) provided as CSV files.
- Data Quality: Cleanse and resolve data quality issues prior to analysis.
- Integration: Combine both sources into a single, user-friendly data model designed for analytical queries.
- Scope: Focus on the latest dataset only; historization of data is not required.
- Documentation: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

BI: Analytics & Reporting (Data Analytics)
Objective
Develop SQL-based analytics to deliver detailed insights into:
- Customer Behavior
- Product Performance
- Sales Trends

These insights empower stakeholders with key business metrics, enabling strategic decision-making.

Quickstart / How to run (high level)
- Prerequisites: Microsoft SQL Server (Express / Developer / Azure SQL) and a SQL client (SSMS or Azure Data Studio). Place source CSVs in a data/ folder or update paths in scripts.
- Typical steps:
  1. Create schema and staging tables (run provided SQL scripts in /sql).
  2. Load CSVs into staging tables (BULK INSERT / OPENROWSET / SSIS / Python).
  3. Cleanse and reconcile data in staging.
  4. Upsert dimensions and load the fact table.
  5. Run the sample analytics queries to verify KPIs.
- File convention (by habit): data/erp_orders.csv and data/crm_customers.csv

Files and structure (suggested)
- /data/              - put CSV source files here (erp, crm)
- /sql/               - T-SQL scripts: schema, staging load, transforms, sample queries
  - 01_create_schema.sql
  - 02_staging_load.sql
  - 03_transform_merge.sql
  - 04_create_analytics_views.sql
  - 05_sample_queries.sql
- /docs/              - documentation assets (ERD, design notes)
- /samples/           - optional small CSV extracts for testing
- README.md

Notes on modelling and ETL (kept concise)
- Use a dimensional (star) schema: a fact_sales table plus dimensions like dim_date, dim_customer, dim_product, dim_salesperson.
- Surrogate integer keys are recommended for joins and performance; keep original source IDs for traceability.
- Staging should handle cleansing: trim strings, normalize casing, standardize dates, validate numeric fields, and deduplicate by business key.
- Reconcile CRM and ERP customers using deterministic matching (email, normalized name/address).
- For this project: focus on the latest snapshot (no SCD2 historization required), but note where SCD2 could be applied later.

Example analytics (conceptual)
- Top customers by revenue, sales trend by month, product performance, repeat purchase rate, average order value (AOV).
- KPIs to implement in SQL: Total Revenue = SUM(sales_amount), AOV = Total Revenue / COUNT(DISTINCT order_id), Repeat Purchase Rate, Month-over-month growth.

License
This project is licensed under the MIT License. You are free to use, modify, and share this project with proper attribution.

💡 About Me
Hello! I am **Joseph Jones**, also known as **Patriotic Jetpack**. I am learning through data.

