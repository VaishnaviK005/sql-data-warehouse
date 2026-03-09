
# SQL-data-warehouse
Building a modern data warehouse with SQL server, including ETL processes, data modelling and analytics.

This project demonstrates a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry best practices in data engineering and analytics.

---
## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.


---
 ### Building the Data Warehouse (Data Engineering)

#### Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

#### Specifications
- **Data Sources**: Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality**: Cleanse and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only; historization of data is not required.
- **Documentation**: Provide clear documentation of the data model to support both business stakeholders and analytics teams.


---
## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:


1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.

---
## Data Model 

The warehouse follows a star schema design consisting of a central fact table and supporting dimension tables.

- **fact_sales** – Stores transactional sales records including order details and sales metrics.
- **dim_customers** – Contains customer attributes such as customer name, region, and demographic information.
- **dim_products** – Contains product details including category, product name, and pricing information.

The fact table references the dimension tables through foreign keys to enable efficient analytical queries.

---
## Sample Analytics Queries

Example 1 – Revenue by Region

SELECT region, SUM(sales_amount) AS total_revenue
FROM fact_sales
GROUP BY region;

Example 2 – Top 5 Products by Sales

SELECT product_name, SUM(sales_amount) AS revenue
FROM fact_sales f
JOIN dim_products p ON f.product_id = p.product_id
GROUP BY product_name
ORDER BY revenue DESC
LIMIT 5;

Example 3 – Monthly Sales Trend

SELECT DATE_TRUNC('month', order_date) AS month,
       SUM(sales_amount) AS total_sales
FROM fact_sales
GROUP BY month
ORDER BY month;

---

### BI: Analytics & Reporting (Data Analysis)

#### Objective
Develop SQL-based analytics to deliver detailed insights into:
- **Customer Behavior**
- **Product Performance**
- **Sales Trends**

These insights empower stakeholders with key business metrics, enabling strategic decision-making.  

---
### How to Run the Project?

1. Create a SQL database (PostgreSQL / SQL Server).
2. Import the datasets from the `datasets/` folder.
3. Execute SQL scripts in order:
   - bronze layer scripts
   - silver layer scripts
   - gold layer scripts
4. Run analytics queries to generate insights.

--- 
## 📂 Repository Structure
```
data-warehouse-project/
│
├── datasets/                           # Raw datasets used for the project (ERP and CRM data)

├── scripts/                            # SQL scripts for ETL and transformations
│   ├── bronze/                         # Scripts for extracting and loading raw data
│   ├── silver/                         # Scripts for cleaning and transforming data
│   ├── gold/                           # Scripts for creating analytical models
│
├── tests/                              # Test scripts and quality files
│
├── README.md                           # Project overview and instructions
├── LICENSE                             # License information for the repository
├── .gitignore                          # Files and directories to be ignored by Git
└── requirements.txt                    # Dependencies and requirements for the project
```
now is it fine??
