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

## Top 10 Product Category Generates that Most Revenue

```sql
SELECT t.product_category_name_english AS product_name, ROUND(SUM(i.price), 2) AS total_price
FROM olist_products p 
JOIN olist_order_items i 
	ON p.product_id = i.product_id
JOIN product_category_name_translation t
    ON p.product_category_name = t.product_category_name
GROUP BY t.product_category_name_english
ORDER BY total_price DESC
LIMIT 10;
```
