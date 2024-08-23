# SQL 🠊 Online Practice Website 🠊 Northwind Problem Set (MEDIUM)

## Q1. Show the ProductName, CompanyName, CategoryName from the products, suppliers, and categories table.

<details>
<summary> SQL Answer for Q1 </summary>

```sql
SELECT product_name, company_name, category_name
FROM products
JOIN categories ON categories.category_id = products.category_id
JOIN suppliers ON suppliers.supplier_id = products.supplier_id;
```

</details>

---

## Q2. Show the category_name and the average product unit price for each category rounded to 2 decimal places.

<details>
<summary> SQL Answer for Q2 </summary>

```sql
SELECT category_name, ROUND(AVG(unit_price), 2)
FROM products
JOIN categories ON categories.category_id = products.category_id
GROUP BY category_name;
```

</details>

---

## Q3. Show the city, company_name, contact_name from the customers and suppliers table merged together. Create a column which contains 'customers' or 'suppliers' depending on the table it came from.

<details>
<summary> SQL Answer for Q3 </summary>

```sql
SELECT city, company_name, contact_name, 'customers' AS role
FROM customers
UNION ALL
SELECT city, company_name, contact_name, 'suppliers' AS role
FROM suppliers;
```

</details>

---