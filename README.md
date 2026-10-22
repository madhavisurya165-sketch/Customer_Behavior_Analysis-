
## Project Overview

A retail business wants to understand **who its customers are, what they buy, and how much they spend**. This project answers questions such as:

- Do male or female customers generate more revenue?
- Do subscribers spend more than non-subscribers?
- Which product categories and age groups bring in the most revenue?
- Which products are discounted most often?
- How loyal are the customers?

## Dataset

- **File:** `customer_shopping_behavior.csv`
- **Size:** 3,900 rows and 18 columns
- **Key columns:** customer ID, age, gender, item purchased, category, purchase amount (USD), location, season, review rating, subscription status, shipping type, discount applied, previous purchases, payment method, frequency of purchases

## Tools Used

- **Python:** pandas, SQLAlchemy, PyMySQL (Jupyter Notebook)
- **MySQL:** MySQL Workbench
- **Power BI:** Power Query, DAX, data modeling, dashboard design

## Workflow

### 1. Data cleaning and preparation (Python)
- Filled 37 missing `Review Rating` values with the **median rating of each product category**
- Renamed columns to **snake_case** (for example, `Purchase Amount (USD)` became `purchase_amount`)
- Created **`age_group`** (Young Adult, Adult, Middle Age, Senior) using age quartiles
- Created **`purchase_frequency_days`** from the purchase frequency text (for example, Weekly = 7)
- Dropped `promo_code_used` because it was identical to `discount_applied`
- Loaded the clean data into MySQL using SQLAlchemy

### 2. Business analysis (MySQL)
10 business questions answered with SQL, using aggregations, `CASE`, subqueries, CTEs and window functions:

1. Total revenue by gender
2. Customers who used a discount but still spent more than the average
3. Top 5 products by average review rating
4. Average spend by shipping type (Standard vs Express)
5. Subscribers vs non-subscribers: average spend and total revenue
6. Top 5 products by discount rate
7. Customer segments: New, Returning, Loyal
8. Top 3 most purchased products in each category (`ROW_NUMBER`)
9. Are repeat buyers more likely to subscribe?
10. Revenue contribution of each age group

### 3. Dashboard (Power BI)
- **KPIs:** number of customers, average product amount, average review rating
- **Charts:** subscriber share, revenue by category, orders by category, total spending by age group, number of purchases by age group
- **Slicers:** subscription status, gender, category, age group
- **Design:** custom theme in navy, teal and orange, with a header banner and card layout

## Key Insights

- **Male customers bring in more revenue** (about $157.9K vs $75.2K), mainly because they make up about 68% of customers. Average spend per purchase is almost the same for both groups (about $59.5 vs $60.2).
- **Subscribers do not spend more.** About 27% of customers are subscribers, and their average spend (about $59.49) is about the same as non-subscribers (about $59.87).
- **Clothing is the top category** with about 45% of revenue, followed by Accessories (about 32%). Footwear and Outerwear are much smaller.
- **Young Adults spend the most** among the four age groups, but the gap between groups is small.
- **Discounts are used in about 43% of purchases.** Hats, Sneakers and Coats have the highest discount rates (around 49-50%).
- **Average purchase amount** is about $59.76 and **average review rating** is about 3.75.
