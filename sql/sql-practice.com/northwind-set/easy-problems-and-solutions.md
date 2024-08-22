# SQL 🠊 Online Practice Website 🠊 Northwind Problem Set (EASY)

## Q1. Show the category_name and description from the categories table sorted by category_name.

<details>
<summary> SQL Answer for Q1 </summary>

```sql
SELECT category_name, description
FROM categories
ORDER BY category_name;
```

</details>

---

## Q2. Show all the contact_name, address, city of all customers which are not from 'Germany', 'Mexico', 'Spain'.

<details>
<summary> SQL Answer for Q2 </summary>

```sql
SELECT contact_name, address, city
FROM customers
WHERE country NOT IN ('Germany', 'Mexico', 'Spain');
```

</details>

---

## Q3. Show order_date, shipped_date, customer_id, Freight of all orders placed on 2018 Feb 26.

<details>
<summary> SQL Answer for Q3 </summary>

```sql
SELECT order_date, shipped_date, customer_id, freight
FROM orders
WHERE order_date = '2018-02-26';
```

</details>

---

## Q4. Show the employee_id, order_id, customer_id, required_date, shipped_date from all orders shipped later than the required date.

<details>
<summary> SQL Answer for Q4 </summary>

```sql
SELECT employee_id, order_id, customer_id, required_date, shipped_date
FROM orders
WHERE shipped_date > required_date;
```

</details>

---

## Q5. Show all the even numbered Order_id from the orders table.

<details>
<summary> SQL Answer for Q5 </summary>

```sql
SELECT order_id
FROM orders
WHERE order_id % 2 = 0;
```

</details>

---

## Q6. Show the city, company_name, contact_name of all customers from cities which contains the letter 'L' in the city name, sorted by contact_name.

<details>
<summary> SQL Answer for Q6 </summary>

```sql
SELECT city, company_name, contact_name
FROM customers
WHERE city LIKE '%L%'
ORDER BY contact_name;
```

</details>

---

## Q7. Show the company_name, contact_name, fax number of all customers that has a fax number. (not null).

<details>
<summary> SQL Answer for Q7 </summary>

```sql
SELECT company_name, contact_name, fax 
FROM customers
WHERE fax IS NOT NULL;
```

</details>

---

## Q8. Show the first_name, last_name, hire_date of the most recently hired employee.

<details>
<summary> SQL Answer for Q8 </summary>

```sql
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date = (SELECT MAX(hire_date) FROM employees);
```

</details>

---

## Q9. Show the average unit price rounded to 2 decimal places, the total units in stock, total discontinued products from the products table.

<details>
<summary> SQL Answer for Q9 </summary>

```sql
SELECT ROUND(AVG(unit_price), 2), SUM(units_in_stock), SUM(discontinued)
FROM products;
```

</details>

---