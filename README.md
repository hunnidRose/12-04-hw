# Домашнее задание к занятию "Расширенные возможности SQL" - Шонгин Егор


### Задание 1

```sql
SELECT 
    s.last_name,
    s.first_name,
    c.city,
    COUNT(cust.customer_id) AS customer_count
FROM 
    store st
JOIN 
    staff s ON st.manager_staff_id = s.staff_id
JOIN 
    address a ON st.address_id = a.address_id
JOIN 
    city c ON a.city_id = c.city_id
JOIN 
    customer cust ON st.store_id = cust.store_id
GROUP BY 
    s.first_name, s.last_name, c.city
HAVING 
    customer_count > 300;
```


---

### Задание 2

```sql
SELECT COUNT(*) AS film_count
FROM film
WHERE length > (SELECT AVG(length) FROM film);
```


---

### Задание 3

```sql
SELECT 
    DATE_FORMAT(p.payment_date, '%Y-%m') AS payment_month,
    SUM(p.amount) AS total_amount,
    COUNT(DISTINCT r.rental_id) AS rental_count
FROM 
    payment p
LEFT JOIN 
    rental r ON p.rental_id = r.rental_id
GROUP BY 
    payment_month
ORDER BY 
    total_amount DESC
LIMIT 1;
```
