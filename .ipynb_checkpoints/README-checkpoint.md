Data Cleaning Project — Retail Store Sales
Project Overview

This project demonstrates a full data cleaning workflow on a dirty retail sales dataset.
The goal was to transform raw transactional data into a consistent, analysis-ready dataset, following professional data quality practices.

Dataset Description

Rows (raw): 12,575

Columns: 11

Type: Retail sales transactions

Common issues: missing values, inconsistent completeness of transactions, incorrect data types

Data Quality Issues Identified

Missing values in critical transaction fields (Price Per Unit, Quantity, Total Spent)

Missing product identifiers (Item)

Incorrect data types (Transaction Date, Discount Applied)

Potential inconsistency in transaction totals

Incomplete transactions with insufficient information

Cleaning Strategy

The cleaning process followed rule-based and deterministic logic, avoiding assumptions where recovery was not reliable.

1. Data Type Standardization

Converted Transaction Date to datetime

Converted Discount Applied to boolean (NaN interpreted as no discount)

2. Transaction Consistency Validation

Verified that
Total Spent = Price Per Unit × Quantity
for all complete transactions

No inconsistencies found

3. Handling Missing Numeric Values

If exactly one numeric field was missing → restored deterministically using the formula

If two or more numeric fields were missing → transaction removed as incomplete

4. Recovering Missing Item Values

Built a mapping Price Per Unit → Item

Restored Item where price uniquely identified the product

Ambiguous cases labeled as "Unknown"

5. Duplicates & Integrity

Transaction ID verified as unique

No duplicate rows found

Final Dataset

Rows: 11,971

Columns: 11

Missing values: 0

Status: fully cleaned, validated, and ready for analysis

Tools Used

Python

pandas

Jupyter Notebook

Project Structure
retail-data-cleaning/
├── data/
│   ├── raw/
│   │   └── retail_store_sales_dirty.csv
│   └── cleaned/
│       └── retail_store_sales_clean.csv
├── notebooks/
│   └── 01_data_cleaning.ipynb
└── README.md

Key Takeaway

This project focuses on data reliability, logical consistency, and transparent decision-making, which are essential for real-world business analytics and reporting.