## Q1. Show first name, last name, and gender of patients whose gender is 'M'

<details>
<summary> SQL Answer for Q1 </summary>

```sql
SELECT first_name, last_name, gender 
FROM patients 
where gender = 'M';
```

</details>

## Q2. Show first name and last name of patients who does not have allergies. (null)

<details>
<summary> SQL Answer for Q2 </summary>

```sql
SELECT first_name, last_name
FROM patients 
WHERE allergies IS NULL;
```

</details>

## Q3. Show first name of patients that start with the letter 'C'

<details>
<summary> SQL Answer for Q3 </summary>

```sql
SELECT first_name
FROM patients 
WHERE first_name LIKE 'C%';
```

</details>

## Q4. Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)

<details>
<summary> SQL Answer for Q4 </summary>

```sql
SELECT first_name, last_name
FROM patients 
WHERE weight BETWEEN 100 AND 120;
```

</details>

## Q5. Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'

<details>
<summary> SQL Answer for Q5 </summary>

```sql
UPDATE patients
SET allergies = 'NKA'
WHERE allergies IS NULL;
```

</details>

## Q6. Show first name and last name concatenated into one column to show their full name. 

<details>
<summary> SQL Answer for Q6 </summary>

```sql
SELECT CONCAT(first_name, " ", last_name) AS full_name
FROM patients;
```

</details>

## Q7. Show first name, last name, and the full province name of each patient. (Example: 'Ontario' instead of 'ON')

<details>
<summary> SQL Answer for Q7</summary>

```sql
SELECT first_name, last_name, province_name
FROM patients JOIN province_names
ON patients.province_id = province_names.province_id;
```

</details>

## Q8. Show how many patients have a birth_date with 2010 as the birth year.

<details>
<summary> SQL Answer for Q8</summary>

```sql
SELECT COUNT(*) 
FROM patients
WHERE YEAR(birth_date) = 2010;
```

</details>

## Q9. Show the first_name, last_name, and height of the patient with the greatest height.

<details>
<summary> SQL Answer for Q9</summary>

```sql
SELECT first_name, last_name, height 
FROM patients
WHERE height = (SELECT MAX(height) FROM patients);
```

</details>

## Q10. Show all columns for patients who have one of the following patient_ids: 1, 45, 534, 879, 1000

<details>
<summary> SQL Answer for Q10</summary>

```sql
SELECT * FROM patients
WHERE patient_id IN (1, 45, 534, 879, 1000);
```

</details>

## Q11. Show the total number of admissions.

<details>
<summary> SQL Answer for Q11</summary>

```sql
SELECT COUNT(*) FROM admissions;
```

</details>

## Q12. Show all the columns from admissions where the patient was admitted and discharged on the same day.

<details>
<summary> SQL Answer for Q12</summary>

```sql
SELECT * FROM admissions
WHERE admission_date = discharge_date;
```

</details>

## Q13. Show the patient id and the total number of admissions for patient_id 579.

<details>
<summary> SQL Answer for Q13</summary>

```sql
SELECT patient_id, COUNT(*)
FROM admissions
WHERE patient_id = 579;
```

</details>

## Q14. Based on the cities that our patients live in, show unique cities that are in province_id 'NS'?

<details>
<summary> SQL Answer for Q14</summary>

```sql
SELECT distinct(city)
FROM patients 
WHERE province_id = 'NS';
```

</details>

## Q15. Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70.

<details>
<summary> SQL Answer for Q15</summary>

```sql
SELECT first_name, last_name, birth_date
FROM patients 
WHERE height > 160 AND weight > 70;
```

</details>

## Q16. Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'

<details>
<summary> SQL Answer for Q16</summary>

```sql
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies IS NOT NULL
AND city = 'Hamilton';
```

</details>

## Q17. Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'

<details>
<summary> SQL Answer for Q17</summary>

```sql
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies IS NOT NULL
AND city = 'Hamilton';
```

</details>