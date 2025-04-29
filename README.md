# Task-6

# Monthly Order Revenue Aggregation (SQL + Visualization)

## Overview
This project demonstrates how to generate monthly revenue and order volume summaries using SQL and visualize the results in both tabular and chart formats.

---

## Files Included

1. **aggregate_orders_2023.sql**
   - SQL script to aggregate total revenue and distinct order volume by month for the year 2023.
   - Uses `EXTRACT()` for date processing and `GROUP BY` for aggregation.

2. **monthly_revenue_summary_2023.pdf**
   - A two-page PDF:
     - **Page 1**: Tabular summary of monthly revenue and order volume.
     - **Page 2**: Bar chart visualization of total monthly revenue.

---

## SQL Query Summary

```sql
SELECT
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month,
    COUNT(DISTINCT order_id) AS order_volume,
    SUM(revenue) AS total_revenue
FROM
    orders
WHERE
    order_date >= DATE '2023-01-01' AND order_date < DATE '2024-01-01'
GROUP BY
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY
    order_year,
    order_month;
```

---

## Data
- Mock dataset of 100 orders with:
  - `order_id`
  - `order_date`
  - `revenue`
- All orders are dated within the year 2023.

---

## Usage
1. Run the SQL script on a database with the `orders` table containing `order_id`, `order_date`, and `revenue`.
2. Use the generated PDF to present the aggregated results in reports or dashboards.

