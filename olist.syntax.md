# Analysis and Findings

## Top 10 Cities that Generate Most Revenue

```sql
SELECT customer_city, ROUND(SUM(p.payment_value), 2) AS payment_value
FROM olist_customers c
JOIN olist_orders o 
	ON c.customer_id = o.customer_id
JOIN olist_order_payments p 
	ON p.order_id = o.order_id
GROUP BY customer_city
ORDER BY payment_value DESC
LIMIT 10;
```

### Top 10 Cities that have the Most Customers

```sql
SELECT customer_city, COUNT(*) AS total_customer
FROM olist_customers
GROUP BY customer_city
ORDER BY COUNT(customer_city) DESC
LIMIT 10;
```

## Top 10 Product Category Generates that Most Revenue

```sql
SELECT t.product_category_name_english AS product_name, ROUND(SUM(i.price), 2) AS total_price
FROM olist_products p 
JOIN olist_order_items i 
	ON p.product_id = i.product_id
JOIN product_category_name_translation t
    ON p.product_category_name = t.product_category_name
GROUP BY t.product_category_name_english
```

### Average Review Score for each Product

```sql
SELECT t.product_category_name_english AS product_name, COUNT(i.product_id) AS total_sold, ROUND(AVG(r.review_score), 2) AS avg_review_score
FROM olist_order_reviews r
JOIN olist_order_items i 
    ON r.order_id = i.order_id
JOIN olist_products p 
    ON i.product_id = p.product_id
JOIN product_category_name_translation t 
    ON p.product_category_name = t.product_category_name
GROUP BY t.product_category_name_english
HAVING total_sold >= 10
ORDER BY avg_review_score DESC;
```

ORDER BY total_price DESC
LIMIT 10;
```
