# SQL Analysis of a Food Delivery App Database

**Author:** Ahmad Shoukat 
**Course:** Google Data Analytics Certificate

## Project Overview
This project uses SQL (MySQL) to analyze a food delivery app database. The analysis focuses on app revenue trends, restaurant performance, and customer behaviors to provide actionable business insights.

## Dataset & Schema
Tables included:
- `users` (user_id, name, email, ...)
- `restaurants` (r_id, r_name, cuisine)
- `food` (f_id, f_name, type)
- `menu` (menu_id, r_id, f_id, price)
- `orders` (order_id, user_id, r_id, amount, date, delivery_rating, restaurant_rating)
- `order_details` (id, order_id, f_id, quantity)

*(See `/docs/P3-Food Delivery App SQL Analysis Project.docx` for full documentation and metadata.)*

## What I did
- Wrote SQL queries to calculate monthly revenue, month-over-month growth, top restaurants, repeat customers, favorite dishes, and per-customer order histories.
- Used joins, aggregate functions, CTEs and window functions for analysis.
- Interpreted results to propose business actions (promotions, retention strategies, personalization).

## Key Findings
- Monthly revenue increased by roughly **33%** and **50%** in subsequent months (strong growth).
- **KFC** had the highest number of orders and the highest number of repeat customers.
- Identified inactive users and customers’ favorite dishes (e.g., Choco Lava Cake for user_id=1).

## File structure
- `/sql/` — SQL scripts for each analysis (run in MySQL)
- `/docs/` — full project documentation (docx/pdf)
- `README.md` — this file

## How to run
1. Import the SQL files into your MySQL environment (MySQL Workbench / CLI).  
2. Ensure schema and table names match those in the SQL scripts.  
3. Run scripts in logical order (e.g., `01_monthly_revenue.sql` → `02_month_over_month_growth.sql`, etc.)

## Example queries
`01_monthly_revenue.sql`
```sql
SELECT MONTHNAME(date) AS month, SUM(amount) AS total_revenue
FROM orders
GROUP BY MONTH(date)
ORDER BY MONTH(date);
