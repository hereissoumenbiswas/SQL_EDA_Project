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
