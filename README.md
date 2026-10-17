# SQL_EDA_Project
This project focuses on exploring and analyzing sales, customer, and product data using PostgreSQL. It aims to identify trends, discover patterns, evaluate product performance, and generate meaningful business insights through SQL queries.

## About the Data

The data sits in a `gold` schema with three tables:

| Table | What it holds | Columns used in this project |
|---|---|---|
| `gold.customers` | One row per customer | `customer_key`, `customer_id`, `customer_number`, `first_name`, `last_name`, `country`, `marital_status`, `gender`, `birthdate`, `create_date`|
| `gold.products` | One row per product | `product_key`, `product_id`, `product_number`, `product_name`, `category_id`, `category`, `subcategory`, `maintenance`,  `cost`, `product_line`, `start_date` |
| `gold.sales` | One row per order line | `order_number`, `product_key`, `customer_key`, `order_date`, `shipping_date`, `due_date`, `quantity`, `price`, `sales_amount` |

How they connect:

- `gold.sales.customer_key` → `gold.customers.customer_key`
- `gold.sales.product_key` → `gold.products.product_key`
