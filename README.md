# SQL EDA Project

**Sales Analytics (PostgreSQL)**

## Project Overview

This project focuses on exploring and analyzing sales, customer, and product data using PostgreSQL. It aims to explore patterns, evaluate product performance, and generate meaningful business insights through SQL queries.

The analysis follows a step-by-step Exploratory Data Analysis (EDA) workflow: first understand the structure of the database, then the dimensions and dates, then the key measures, and finally answer business questions on magnitude and ranking.

## About the Data

The data sits in a `gold` schema with three tables:

| Table | What it holds | Columns used in this project |
|---|---|---|
| `gold.customers` | One row per customer | `customer_key`, `customer_id`, `customer_number`, `first_name`, `last_name`, `country`, `marital_status`, `gender`, `birthdate`, `create_date`|
| `gold.products` | One row per product | `product_key`, `product_id`, `product_number`, `product_name`, `category_id`, `category`, `subcategory`, `maintenance`,  `cost`, `product_line`, `start_date` |
| `gold.sales` | One row per order line | `order_number`, `product_key`, `customer_key`, `order_date`, `shipping_date`, `due_date`, `sales_amount`, `quantity`, `price` |

### How the tables connect

- `gold.sales.customer_key` links to `gold.customers.customer_key`
- `gold.sales.product_key` links to `gold.products.product_key`

In other words, `gold.sales` is the central table, and each order line points to one customer and one product.

## What I Did: Analysis Workflow

### 1. Database Exploration (Done)
Got familiar with the database before running any analysis.
- Explored the tables available in the `gold` schema
- Checked the columns and data types of `customers`, `products` and `sales`

### 2. Dimensions Exploration (Done)
Looked at the descriptive columns used to slice and group the data.
- Customer dimensions such as `country`, `gender` and `marital_status`
- Product dimensions such as `category`, `subcategory` and `product_line`
- Checked the distinct values in each dimension to understand how the data can be segmented

### 3. Date Exploration (Done)
Understood the time coverage of the data.
- Worked with the date columns: `order_date`, `shipping_date`, `due_date`, `birthdate` and `create_date`
- Identified the time span the data covers, which sets the boundaries for later trend analysis

### 4. Measures Exploration (Done)
Calculated the key numbers that describe the business.
- Worked with the numeric columns `sales_amount`, `quantity`, `price` and `cost`
- Built key totals and averages that summarize overall sales performance
