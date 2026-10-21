# SQL EDA Project

**Sales Analytics (PostgreSQL)**

Project Overview

This project focuses on performing Exploratory Data Analysis (EDA) on sales, customer, and product data using PostgreSQL. The goal is to identify sales trends, understand customer behavior, evaluate product performance, and generate meaningful business insights through SQL queries.

The analysis follows a structured, step-by-step EDA workflow, starting with understanding the database structure and data dimensions, followed by analyzing date ranges and key business metrics. Finally, SQL queries are used to answer business questions related to sales performance, product rankings, and overall business trends.

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

### 5. Magnitude Analysis (Done)
Answered 20 questions that compare measures across dimensions.
- Combined the three tables through the key relationships to compare measures across customer and product dimensions
- Showed where the business volume sits, for example across countries, categories and customer groups

### 6. Ranking Analysis (Done)
Answered 10 questions on top and bottom performers.
- Ranked products, categories and customers by measures to find the best and worst performers
- Supports decisions on which products and segments deserve more attention

### 7. Change Over Time Analysis (In progress)
10 questions that look at how sales and customers change across months and years.

## Key Insights

## Business Snapshot
| Metric | Value |
|---|---|
| Time span between first and last order | 3 years 30 days |
| Total sales | 29,356,250 |
| Total quantity sold | 60,423 |
| Average selling price | 486.05 |
| Total orders | 27,659 |
| Total products | 295 |
| Total customers | 18,484 |

## Products and Categories

| Category | Products | Units Sold | Total Sales |
|---|---|---|---|
| Bikes | 97 | 15,205 | 28,316,272 |
| Accessories | 29 | 36,112 | 700,262 |
| Clothing | 35 | 9,106 | 339,716 |
| Components | 127 | No sales recorded | No sales recorded |

- Bikes generate about 96.5% of total revenue, even though they account for only about 25.2% of units sold.
- Accessories sell the most units (about 59.8% of all units) but bring in only about 2.4% of revenue.
- The Components category is the largest by product count, but no sales were recorded for it.
- 7 products have no category.
- The average product cost is 949.44 for Bikes and 264.72 for Components, compared with 24.80 for Clothing and 13.17 for Accessories.

## Subcategories, Product Lines and Products

| Top 5 Subcategories | Total Sales |
|---|---|
| Road Bikes | 14,519,438 |
| Mountain Bikes | 9,952,254 |
| Touring Bikes | 3,844,580 |
| Tires and Tubes | 244,634 |
| Helmets | 225,435 |

| Worst 5 Subcategories | Total Sales |
|---|---|
| Socks | 5,112 |
| Cleaners | 7,272 |
| Caps | 19,710 |
| Gloves | 34,320 |
| Vests | 36,160 |

| Product Line | Total Sales |
|---|---|
| Road | 14,622,850 |
| Mountain | 10,250,982 |
| Touring | 3,879,135 |
| Other Sales | 603,283 |

| Top 5 Products | Total Sales |
|---|---|
| Mountain-200 Black- 46 | 1,373,454 |
| Mountain-200 Black- 42 | 1,363,128 |
| Mountain-200 Silver- 38 | 1,339,394 |
| Mountain-200 Silver- 46 | 1,301,029 |
| Mountain-200 Black- 38 | 1,294,854 |

| Worst 5 Products | Total Sales |
|---|---|
| Racing Socks- L | 2,430 |
| Racing Socks- M | 2,682 |
| Patch Kit/8 Patches | 6,382 |
| Bike Wash - Dissolver | 7,272 |
| Touring Tire Tube | 7,440 |

- The three bike subcategories together generate about 96.5% of total sales.
- The top 10 products come from just two models: Mountain-200 (six variants) and Road-150 Red (four variants).
- The weakest products are low-priced accessories and clothing items.

## Sales and Orders Over Time

| Year | Total Sales | Orders |
|---|---|---|
| 2010 | 43,419 | 14 |
| 2011 | 7,075,088 | 2,216 |
| 2012 | 5,842,231 | 3,269 |
| 2013 | 16,344,878 | 21,287 |
| 2014 | 45,642 | 871 |

- 2013 is the strongest year, with about 55.7% of all sales and about 77% of all orders.
- From 2012 to 2013, sales grew about 180% while orders grew about 6.5 times.
- 2012 sales were about 17.4% lower than 2011.
- 2010 and 2014 are partial years: all 2010 sales fall in December and all 2014 sales fall in January. Comparisons involving these years are misleading.
- A small amount of sales (4,992) has no order date, so it is not counted in any year.

## Customers

| Country | Customers |
|---|---|
| United States | 7,482 |
| Australia | 3,591 |
| United Kingdom | 1,913 |
| France | 1,810 |
| Germany | 1,780 |
| Canada | 1,571 |
| n/a | 337 |

- The United States has about 40.5% of all customers.
- Gender is almost evenly split: 9,341 male and 9,128 female customers (15 marked n/a).
- Female customers generated slightly more sales (14,804,168) than male customers (14,522,393).
- The top customers are very close in value. The highest total is 13,294, shared by customer IDs 12132 and 12301, followed by 12308 (13,268), 12131 (13,265) and 12300 (13,242).

## Geography

| Country | Units Sold | Share of Units |
|---|---|---|
| United States | 20,481 | 33.90% |
| Australia | 13,346 | 22.09% |
| Canada | 7,630 | 12.63% |
| United Kingdom | 6,910 | 11.44% |
| Germany | 5,626 | 9.31% |
| France | 5,559 | 9.20% |
| n/a | 871 | 1.44% |

- The United States and Australia lead both in customers and in units sold.
- The top three countries by units sold (United States, Australia, Canada) make up about 68.6% of all units.

## Data Quality Notes

- 337 customers have `n/a` as country, and 15 have `n/a` as gender.
- 7 products have no category, and some products have no product line.
- Sales totals tie out to 29,356,250 across the year, category, product line and gender breakdowns.

## Author

**Soumen Biswas**
(Data Science graduate)

- GitHub: (https://github.com/hereissoumenbiswas)
- LinkedIn: (https://www.linkedin.com/in/hereissoumenbiswas/?isSelfProfile=true)
