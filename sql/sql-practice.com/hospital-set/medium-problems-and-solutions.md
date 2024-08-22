# SQL 🠊 Online Practice Website 🠊 Hospital Problem Set (MEDIUM)

## Q1. Show unique birth years from patients and order them by ascending.

<details>
<summary> SQL Answer for Q1 </summary>

```sql
SELECT DISTINCT(YEAR(birth_date)) 
FROM patients
ORDER BY YEAR(birth_date) ASC;
```

</details>

---

## Q2. Show unique first names from the patients table which only occurs once in the list. For example, if two or more people are named 'John' in the first_name column then don't include their name in the output list. If only 1 person is named 'Leo' then include them in the output.

<details>
<summary> SQL Answer for Q2 </summary>

```sql
SELECT DISTINCT(first_name)
FROM patients
GROUP BY first_name
HAVING COUNT(first_name) = 1;
```

</details>

---

## Q3. Show patient_id and first_name from patients where their first_name start and ends with 's' and is at least 6 characters long.

<details>
<summary> SQL Answer for Q3 </summary>

```sql
SELECT patient_id, first_name
FROM patients
WHERE first_name LIKE 's____%s';
```

</details>

---

## Q4. Show patient_id, first_name, last_name from patients whos diagnosis is 'Dementia'. Primary diagnosis is stored in the admissions table.

<details>
<summary> SQL Answer for Q4 </summary>

```sql
SELECT patients.patient_id, first_name, last_name
FROM patients JOIN admissions ON patients.patient_id = admissions.patient_id
WHERE diagnosis = 'Dementia';
```

</details>

---

## Q5. Display every patient's first_name. Order the list by the length of each name and then by alphabetically.

<details>
<summary> SQL Answer for Q5 </summary>

```sql
SELECT first_name
FROM patients
ORDER BY LEN(first_name), first_name;
```

</details>

---