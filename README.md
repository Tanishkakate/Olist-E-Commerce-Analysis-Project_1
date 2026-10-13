# Olist-E-Commerce-Analysis-Project_1

# Olist E-Commerce Analysis (MySQL + Power BI)

**Business question:** Which product categories and states drive sales, and how much does late delivery hurt customer satisfaction?

**Data:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle), 2016 to 2018, 99,441 orders across 8 tables (the geolocation file was not used).

## Tools
MySQL (SQL: joins, CTEs, window functions), Python (pandas, for cleaning the reviews file), Power BI (data model, DAX, 3-page dashboard)

## Data preparation
- Loaded 8 CSVs into MySQL and defined date and numeric types.
- Reviews file: the comment text broke the MySQL load, so I removed the comment columns with pandas (`reviews_clean.csv`; 99,224 reviews kept).
- Checks: duplicate order IDs, delivered-before-purchase dates, orders with no items (775, excluded from revenue).
- Revenue = item price on delivered orders only (96,478 orders).

## Key findings
- Revenue grew about 8x, from R$112K (Jan 2017) to R$925K (Jan 2018). Nov 2017 spiked (7,289 orders, likely Black Friday).
- Health & beauty leads revenue (R$1.23M). Watches & gifts earns R$1.17M from far fewer orders (about R$212 per order vs R$143).
- About 8% of delivered orders arrive late. Late orders average a review score of **2.57 vs 4.29** for on-time orders.
- Late-delivery rates are highest in Northeast states (AL 23.9%, MA 19.7%, PI 16.0%, CE 15.3%, SE 15.2%).
- Only 3.0% of customers (2,801 of 93,358) ordered more than once.
- Credit card is 78.3% of payment value; boleto (bank slip) is 17.9%.

## Recommendations
1. Review carrier performance and delivery estimates for Northeast states.
2. Prioritize high-volume states like Rio de Janeiro, which has 1,664 late orders.
3. Run post-purchase campaigns to lift the repeat rate.

## Limitations
- Late delivery and low reviews are associated, but this analysis does not prove cause.
- A possible driver (distance from seller to customer) was not tested.
- Payment totals include freight and all order statuses, so they differ from item revenue.
- Average review score is 4.09 across all orders and 4.16 on delivered orders; the Delivery page uses delivered orders.

## Dashboard
![Sales overview](<img width="1366" height="768" alt="Screenshot (301)" src="https://github.com/user-attachments/assets/9b0d5e9e-c9c0-4612-a338-d9b81aad5931" />
)
![Delivery](<img width="1366" height="768" alt="Screenshot (302)" src="https://github.com/user-attachments/assets/083bfca9-881d-44d0-8d0c-63b82e47c38b" />
)
![Customers & payments](<img width="1366" height="768" alt="Screenshot (303)" src="https://github.com/user-attachments/assets/db4e1cca-dd95-40ef-9042-0dcd6ea62493" />
)

## Repo contents
`sql/` (load, quality checks, analysis) · `python/` (clean_reviews.py) · `powerbi/olist_dashboard.pbix` · `screenshots/`
