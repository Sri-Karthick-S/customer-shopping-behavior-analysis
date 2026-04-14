# Customer Shopping Behavior Analysis

Analysed 3,900 retail transactions using Python, PostgreSQL, and Power BI to uncover customer segments, discount dependency patterns, and subscription behaviour driving business recommendations.

## Project Overview

A retail company wanted to better understand what drives customer purchasing decisions across demographics, product categories, and sales channels. Using transactional data covering 3,900 purchases, this project explores spending patterns, customer loyalty, discount effectiveness, and subscription behaviour to support data-driven marketing and product strategy.

## Dataset

- Source: Kaggle (Consumer Behaviour and Shopping Habits Dataset)
- Rows: 3,900 | Columns: 18
- Key features: customer demographics (age, gender, location), purchase details (category, amount, season), and behavioural signals (discount applied, subscription status, review rating, shipping type, purchase frequency)
- Missing data: 37 null values in Review Rating column, imputed using category-wise median

## Steps Covered

**1. Data Preparation (Python/pandas)**
- Handled 37 missing values in Review Rating using category-wise median imputation
- Renamed columns to snake_case for consistency
- Engineered two new features: age_group (binned from age) and purchase_frequency_days
- Verified redundancy between discount_applied and promo_code_used, dropped promo_code_used
- Loaded cleaned dataframe into PostgreSQL for SQL analysis

**2. SQL Analysis (PostgreSQL)**

Ten structured queries were written to answer key business questions:

| # | Query | Purpose |
|---|-------|---------|
| 1 | Revenue by Gender | Compare total spend across gender |
| 2 | High-Spending Discount Users | Identify customers using discounts but spending above average |
| 3 | Top 5 Products by Rating | Find highest rated products |
| 4 | Shipping Type Comparison | Compare avg spend by shipping preference |
| 5 | Subscribers vs Non-Subscribers | Compare loyalty and revenue contribution |
| 6 | Discount-Dependent Products | Find products most reliant on discounts to drive sales |
| 7 | Customer Segmentation | Classify customers as New, Returning, or Loyal |
| 8 | Top 3 Products per Category | Rank best sellers within each category |
| 9 | Repeat Buyers and Subscriptions | Check if repeat buyers are more likely to subscribe |
| 10 | Revenue by Age Group | Measure revenue contribution across age segments |

**3. Dashboard (Power BI)**

Interactive dashboard with slicers for subscription status, gender, category, and shipping type, displaying KPIs, revenue breakdowns, and sales patterns across age groups and categories.

## Key Findings

- Male customers contributed $157,890 in revenue compared to $75,191 from female customers, despite females being a significant segment worth targeted engagement
- 80% of customers (3,116 out of 3,900) were classified as Loyal based on purchase history, indicating strong retention but limited new customer acquisition
- 73% of customers had no subscription despite average spend being nearly identical to subscribers ($59.87 vs $59.49), suggesting low perceived value in the subscription offering
- Hat, Sneakers, and Coat had the highest discount dependency (47-50% of purchases made with a discount), pointing to margin risk if discounts are withdrawn
- Young Adults contributed the highest revenue at $62,143, followed closely by Middle-aged customers at $59,197
- Express shipping customers spent slightly more on average ($60.48) than Standard shipping customers ($58.46)

## Business Recommendations

- **Subscription conversion**: With 73% non-subscribers spending at the same rate as subscribers, a targeted campaign offering exclusive perks could convert high-frequency buyers at low acquisition cost
- **Discount policy review**: Products with 47-50% discount rates need margin analysis — discounts may be driving volume without improving profitability
- **Female customer engagement**: Revenue gap between male and female customers warrants category-specific campaigns, particularly in Clothing and Accessories where female purchase intent is higher
- **New customer acquisition**: With only 83 new customers in the dataset, marketing investment should be evaluated against retention-heavy current patterns

## How to Run

**Requirements**
```
Python 3.8+
pip install pandas numpy sqlalchemy psycopg2
```

**Steps**
1. Place the dataset in the `data/` folder
2. Update PostgreSQL connection string in `data_cleaning.py`
3. Run `python python/data_cleaning.py` to clean data and load to PostgreSQL
4. Run queries in `sql/business_queries.sql` using pgAdmin or any PostgreSQL client
5. Open `dashboard/customer_behavior.pbix` in Power BI Desktop
