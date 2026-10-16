# SQL_EDA_Project
This project focuses on exploring and analyzing sales, customer, and product data using PostgreSQL. It aims to identify trends, discover patterns, evaluate product performance, and generate meaningful business insights through SQL queries.

## About the Data

The data sits in a `gold` schema with three tables:

| Table | What it holds | Columns used in this project |
|---|---|---|
| `gold.customers` | One row per customer | `customer_key`, `customer_id`, `customer_number`, `first_name`, `last_name`, `country`, `marital_status`, `gender`, `marital_status`, `birthdate` |
| `gold.products` | One row per product | `product_key`, `product_id`, `product_name`, `category`, `subcategory`, `product_line`, `cost` |
| `gold.sales` | One row per order line | `order_number`, `customer_key`, `product_key`, `order_date`, `shipping_date`, `quantity`, `price`, `sales_amount` |

How they connect:

- `gold.sales.customer_key` → `gold.customers.customer_key`
- `gold.sales.product_key` → `gold.products.product_key`
