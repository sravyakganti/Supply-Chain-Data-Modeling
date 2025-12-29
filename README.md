# Supply-Chain-Data-Modeling
Project Overview
This project transforms raw supply chain data (TPC-H dataset) from a transactional 3rd Normal Form (3NF) structure into a clean **Star Schema** optimized for Business Intelligence (BI) reporting.

The Problem
The raw data source scattered critical information across multiple tables (`CUSTOMER`, `NATION`, `REGION`, `ORDERS`, `LINEITEM`). This required complex, expensive joins for simple queries, resulting in:
- Slow query performance.
- Complex SQL for analysts to write.
- Redundant calculations (e.g., Net Revenue).

The Solution
I engineered a Star Schema in Snowflake using ELT (Extract, Load, Transform) methodologies:

1.  DIM_CUSTOMER: Denormalized Customer, Nation, and Region into a single dimension for fast slicing by geography.
2.  FCT_SALES: Combined header and detail records into a comprehensive transaction table.
3.  Feature Engineering: Pre-calculated `NET_REVENUE` inside the pipeline to standardize business logic.

Technical Results (The "Flex")
By modeling the data, I reduced the complexity of a standard "Revenue by Region" query significantly:

| Metric | Raw Data (3NF) | New Star Schema |
| :--- | :--- | :--- |
| Joins Required | 5 | 1 |
| Code Complexity | High | Low |
| Readability | Poor | Excellent |

Tech Stack
- Database:Snowflake
- Language:SQL (DDL & DML)
- Modeling Technique:Dimensional Modeling (Star Schema)

How to Run
1. Open a Snowflake SQL Worksheet.
2. Run the scripts in `data_modeling.sql` sequentially.
