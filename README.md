# Brazillian e-Commerce (Olist)
Using MySQL to analyze Olist, a Brazilian e-commerce platform,  to understand sales performance, customer behavior, seller  performance and delivery trends across 8 interconnected tables  using JOINs, CTEs and window functions.

## Executive Summary
To be updated

## Dataset Overview

This dataset is from Olist, a Brazilian e-commerce platform that 
connects small businesses to customers across Brazil. The data covers 
customer orders, payments, reviews, products and sellers across 
multiple tables. All monetary values are in Brazilian Real (R$).

The dataset consists of 8 interconnected tables:

| Table | Description |
|---|---|
| `olist_customers` | Customer information including city and state |
| `olist_geolocation` | City and state information |
| `olist_order_items` | Items within each order including price and freight |
| `olist_order_payments` | Payment details for each order |
| `olist_order_reviews` | Customer reviews and scores for each order |
| `olist_orders` | Order details including status and timestamps |
| `olist_products` | Product details including category and dimensions |
| `olist_sellers` | Seller information including city and state |
| `olist_product_category_name_translation` | Product category names translated from Portuguese to English |

Since this dataset spans multiple tables, JOINs were used throughout 
the analysis to connect relevant information across tables.

## Analysis and Findings

### Top 10 Cities that Generate Most Revenue
Sao Paulo dominates by a very large margin with **R$2,203,373** in 
total payments, almost double the second highest city, Rio de Janeiro 
at **R$1,161,927**. Belo Horizonte comes third with **R$421,765**, 
followed by Brasilia and Curitiba rounding out the top 5.

The remaining cities from Porto Alegre to Niteroi all fall between 
**R$140,000** and **R$250,000**, showing a significant drop off from 
the top two cities.

Honestly, this is not surprising. Sao Paulo is the largest city in 
Brazil and one of the largest in the world, so it naturally leads in 
e-commerce spending. What is interesting is how big the gap is between 
Sao Paulo and everyone else. Even Rio de Janeiro, which is also a major 
city, generates less than half of Sao Paulo's revenue. This tells me 
that Olist's growth strategy should heavily prioritise Sao Paulo while 
finding ways to close the gap in other major cities.

![most_revenue_city](images/most_revenue_city.png)

### Top 10 Cities that have the Most Customers

Sao Paulo has by far the most customers with **15,540**, more than 
double the second city Rio de Janeiro at **6,882**. Belo Horizonte 
comes third with **2,773** followed by Brasilia and Curitiba.

This aligns with the revenue finding earlier where Sao Paulo also 
led by a significant margin. More customers naturally means more 
orders and higher revenue, confirming that Sao Paulo is Olist's 
most important market.

![most_customer](images/most_customer.png)

### Top 10 Product Category Generates that Most Revenue

Health and Beauty leads with **R$1,258,681** in total revenue, 
followed closely by Watches and Gifts at **R$1,205,006** and 
Bed, Bath and Table at **R$1,036,989**. Sports and Leisure and 
Computers and Accessories round out the top 5.

The top 3 categories are all everyday lifestyle products, which 
makes sense as these are things people tend to buy repeatedly 
rather than one-time purchases. From position 6 onwards the 
revenue drops significantly, with Furniture Decor at **R$729,763** 
being less than half of the top category.

![most_revenue_product](images/most_revenue_product.png)

### Average Review Score for each Product

To ensure reliability, only categories with at least 10 sales 
are included in this analysis.

Toys leads with the highest average review score at **4.50**, 
followed by Garden Tools at **4.47** and Computers and Accessories 
at **4.43**. These categories are clearly meeting customer expectations.

On the lower end, Housewares sits at **3.55** and Bed, Bath and 
Table at **3.75**, which are also the third and first highest 
revenue generating categories respectively. This is worth noting 
because despite generating strong revenue, customers are not 
particularly impressed with these categories, suggesting there 
is room to improve product quality or manage customer expectations 
better.

Health and Beauty, which leads in total revenue, has a decent 
score of **4.16**, showing that it not only sells well but also 
satisfies customers reasonably well.

Cross referencing with the revenue analysis, most top revenue 
categories also have decent review scores. However, Bed Bath 
and Table stands out as a concern. It ranks third in revenue 
at **R$1,036,989** but has the lowest average review score 
among top categories at **3.75**, suggesting customers are 
spending but not fully satisfied with what they receive.

![review_score](images/review_score.png)


