# wanderbricks-capstone--project

## Overview

**Wander Bricks** is a comprehensive Databricks SQL deep-analysis project that demonstrates advanced analytics and data exploration techniques using a real-world vacation rental dataset. This repository showcases practical SQL workflows for querying, transforming, analyzing, and visualizing data to extract actionable business insights.

The project focuses on performance optimization, data quality assessment, and strategic decision-making through exploratory data analysis (EDA) on booking, property, host, user, and amenities data.

---

## 🎯 Project Objectives

- **Data Exploration**: Comprehensive analysis of vacation rental datasets to understand data structure and quality
- **Business Analytics**: Derive insights into booking trends, property performance, and revenue patterns
- **Performance Optimization**: Write efficient SQL queries for large-scale data analysis
- **Actionable Insights**: Identify opportunities for business improvement and growth

---

## 📊 Dataset Overview

The project analyzes a vacation rental platform dataset with the following core tables:

### Tables Included:
- **Bookings**: Booking records with status (confirmed, pending, cancelled, completed), revenue, and guest information
- **Properties**: Property listings including type, location, title, and host information
- **Hosts**: Host profile data and statistics
- **Users**: Guest/user information and booking history
- **Amenities**: Property amenities and features

### Key Metrics:
- Total booking records across multiple booking statuses
- Property performance by revenue, booking count, and cancellation rate
- Seasonal and temporal booking trends
- User repeat booking behavior
- Property type analysis and comparison

---

## 📁 Project Structure

```
wander-bricks_project/
├── README.md                                  # Project documentation
├── 01_data_exploration/
│   ├── Bookings Table EDA.dbquery.ipynb       # Booking analysis and trends
│   ├── Properties Table EDA.dbquery.ipynb     # Property-level insights
│   ├── Hosts Table EDA.dbquery.ipynb          # Host analytics
│   ├── Users Table EDA.dbquery.ipynb          # User behavior analysis
│   └── Amenities Table EDA.dbquery.ipynb      # Amenities feature analysis
├── imgs/                                       # Visualizations and charts
```

---

## 🔍 Key Analysis Areas

### 1. Bookings Analysis
- Booking volume trends by month and year
- Booking status distribution (completed, pending, cancelled, confirmed)
- Revenue analysis by property and booking status
- Seasonal patterns and peak booking periods
- Stay duration analysis
- Guest count patterns by property type

**Sample Insights:**
- Tracks completed bookings vs. cancelled bookings over time
- Identifies top revenue-generating properties
- Highlights cancellation patterns for improvement opportunities

### 2. Properties Performance
- Revenue generation by property type
- Booking success rates and completion metrics
- Top-performing properties ranking
- Property type performance comparison
- Average booking value by property

### 3. Host Insights
- Host performance metrics
- Property management patterns
- Response and booking rates

### 4. User Behavior
- Repeat booking patterns
- User segmentation by booking frequency
- Customer lifetime value analysis

### 5. Amenities Analysis
- Feature correlation with booking success
- Amenity popularity and impact

---

## 🛠️ Technologies & Tools

- **Platform**: Databricks (Apache Spark SQL)
- **Language**: SQL
- **Environment**: Databricks Notebooks (.dbquery.ipynb)
- **Data Format**: Parquet / Delta Lake
- **Visualization**: Databricks built-in charting and Redash

---

## 💡 SQL Techniques Demonstrated

- **Aggregations**: `SUM()`, `COUNT()`, `AVG()`, `GROUP BY`, `HAVING`
- **Joins**: `INNER JOIN`, `LEFT JOIN` for multi-table analysis
- **Window Functions**: Revenue and booking analysis across periods
- **Date Functions**: `YEAR()`, `MONTH()`, `DATE_FORMAT()`, `DATEDIFF()`
- **Conditional Aggregations**: `CASE WHEN` statements for status-based analysis
- **Temporary Views**: `CREATE OR REPLACE TEMP VIEW` for modular analysis
- **Subqueries**: Nested queries for complex analysis

---

## 🚀 Getting Started

### Prerequisites
- Access to Databricks workspace
- SQL knowledge and experience
- Access to the `databricks_wanderbricks_dataset_dais_2025` schema

### Running the Notebooks

1. Clone or import this repository into your Databricks workspace
2. Navigate to the `01_data_exploration/` folder
3. Open any `.dbquery.ipynb` notebook
4. Attach to a running Databricks cluster
5. Execute the cells to run the SQL queries
6. View visualizations and results directly in Databricks

**Example Query:**
```sql
-- Booking trends by month
SELECT 
  date_format(check_in, 'yyyy-MM') as month,
  SUM(CASE WHEN status = 'completed' THEN 1 ELSE 0 END) as completed,
  SUM(CASE WHEN status = 'cancelled' THEN 1 ELSE 0 END) as cancelled,
  SUM(CASE WHEN status = 'confirmed' THEN 1 ELSE 0 END) as confirmed,
  SUM(CASE WHEN status = 'pending' THEN 1 ELSE 0 END) as pending
FROM bookings
GROUP BY date_format(check_in, 'yyyy-MM')
ORDER BY month;
```

---

## 📈 Key Findings & Insights

- **Property Performance**: Serviced Residences in Singapore and premium properties generate the highest revenue
- **Cancellation Patterns**: Top-performing properties show relatively high cancellation rates, indicating a retention opportunity
- **Seasonal Trends**: Clear seasonal patterns in booking volume, with peak periods identifiable
- **User Behavior**: Strong repeat booking indicators among high-value customers
- **Revenue Opportunities**: Significant variance in property type performance suggests optimization potential

---

## 📝 Notes for Users

- All notebooks use the `databricks_wanderbricks_dataset_dais_2025` schema
- Temporary views are created for modular analysis; they persist only within the session
- Visualizations are rendered using Databricks charting engine and Redash
- Queries are optimized for Databricks/Spark SQL syntax
- Visualizations and charts are available in the `imgs/` directory

---

## 👤 Author

**Made by Vicky Ingle**

---

**Last Updated**: September 2026  
**Dataset**: Databricks WanderBricks Dataset (DAIS 2025)  
**Status**: Active Analysis
