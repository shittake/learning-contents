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

## Q6. Show the total amount of male patients and the total amount of female patients in the patients table. Display the two results in the same row.

<details>
<summary> SQL Answer for Q6 </summary>

```sql
SELECT 
(SELECT COUNT(*) FROM patients WHERE gender = 'M') AS male_count,
(SELECT COUNT(*) FROM patients WHERE gender = 'F') AS female_count;
```

</details>

---

## Q7. Show first and last name, allergies from patients which have allergies to either 'Penicillin' or 'Morphine'. Show results ordered ascending by allergies then by first_name then by last_name.

<details>
<summary> SQL Answer for Q7 </summary>

```sql
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies IN ('Penicillin', 'Morphine')
ORDER BY allergies, first_name, last_name;
```

</details>

---

## Q8. Show patient_id, diagnosis from admissions. Find patients admitted multiple times for the same diagnosis.

<details>
<summary> SQL Answer for Q8 </summary>

```sql
SELECT patient_id, diagnosis
FROM admissions
GROUP BY patient_id, diagnosis
HAVING COUNT(*) > 1;
```

</details>

---

## Q9. Show the city and the total number of patients in the city. Order from most to least patients and then by city name ascending.

<details>
<summary> SQL Answer for Q9 </summary>

```sql
SELECT city, COUNT(*) AS city_size
FROM patients
GROUP BY city
ORDER BY city_size DESC, city;
```

</details>

---

## Q10. Show first name, last name and role of every person that is either patient or doctor. The roles are either "Patient" or "Doctor"

<details>
<summary> SQL Answer for Q10 </summary>

```sql
SELECT first_name, last_name, 'Patient' AS role
FROM patients
UNION ALL
SELECT first_name, last_name, 'Doctor' AS role
FROM doctors;
```

</details>

---

## Q11. Show all allergies and their popularity, ordered by popularity. Remove NULL values from query.

<details>
<summary> SQL Answer for Q11 </summary>

```sql
SELECT allergies, COUNT(*) AS allergy_count
FROM patients
GROUP BY allergies
HAVING allergies IS NOT NULL
ORDER BY allergy_count DESC;
```

</details>

---

## Q12. Show all patient's first_name, last_name, and birth_date who were born in the 1970s decade. Sort the list starting from the earliest birth_date.

<details>
<summary> SQL Answer for Q12 </summary>

```sql
SELECT first_name, last_name, birth_date
FROM patients
WHERE YEAR(birth_date) >= 1970 AND year(birth_date) <= 1979
ORDER BY birth_date;
```

</details>

---

## Q13. We want to display each patient's full name in a single column. Their last_name in all upper letters must appear first, then first_name in all lower case letters. Separate the last_name and first_name with a comma. Order the list by the first_name in decending order (EX: SMITH,jane)

<details>
<summary> SQL Answer for Q13 </summary>

```sql
SELECT CONCAT(upper(last_name), ",", LOWER(first_name))
FROM patients
ORDER BY first_name DESC;
```

</details>

---

## Q14. Show the province_id(s), sum of height; where the total sum of its patient's height is greater than or equal to 7,000.

<details>
<summary> SQL Answer for Q14 </summary>

```sql
SELECT province_id, SUM(height) AS total_height
FROM patients
GROUP BY province_id
HAVING total_height >= 7000;
```

</details>

---

## Q15. Show the difference between the largest weight and smallest weight for patients with the last name 'Maroni'

<details>
<summary> SQL Answer for Q15 </summary>

```sql
SELECT MAX(weight) - MIN(weight)
FROM patients
WHERE last_name = 'Maroni';

```

</details>

---

## Q16. Show all of the days of the month (1-31) and how many admission_dates occurred on that day. Sort by the day with most admissions to least admissions.

<details>
<summary> SQL Answer for Q16 </summary>

```sql
SELECT DAY(admission_date) AS date, COUNT(*) AS admission_count
FROM admissions
GROUP BY date
ORDER BY admission_count DESC;

```

</details>

---

## Q17. Show all columns for patient_id 542's most recent admission_date.

<details>
<summary> SQL Answer for Q17 </summary>

```sql
SELECT * 
FROM admissions
WHERE patient_id = 542
ORDER BY admission_date DESC
LIMIT 1;

```

</details>

---

## Q18. Show patient_id, attending_doctor_id, and diagnosis for admissions that match one of the two criteria: - patient_id is an odd number and attending_doctor_id is either 1, 5, or 19. and - attending_doctor_id contains a 2 and the length of patient_id is 3 characters.

<details>
<summary> SQL Answer for Q18 </summary>

```sql
SELECT patient_id, attending_doctor_id, diagnosis
FROM admissions
WHERE patient_id % 2 = 1 AND attending_doctor_id IN (1, 5, 19)
OR 
attending_doctor_id LIKE '%2%' AND patient_id LIKE '___';
```

</details>

---

## Q19. Show first_name, last_name, and the total number of admissions attended for each doctor.Every admission has been attended by a doctor.

<details>
<summary> SQL Answer for Q19 </summary>

```sql
SELECT first_name, last_name, COUNT(*)
FROM admissions JOIN doctors
ON admissions.attending_doctor_id = doctors.doctor_id
GROUP BY doctor_id;
```

</details>

---

## Q20. For each doctor, display their id, full name, and the first and last admission date they attended.

<details>
<summary> SQL Answer for Q20 </summary>

```sql
SELECT doctor_id, CONCAT(first_name, " ", last_name), MIN(admission_date), MAX(admission_date)
FROM admissions JOIN doctors
ON admissions.attending_doctor_id = doctors.doctor_id
GROUP BY doctor_id;
```

</details>

---

## Q21. Display the total amount of patients for each province. Order by descending.

<details>
<summary> SQL Answer for Q21 </summary>

```sql
SELECT province_name, COUNT(*) AS province_population
FROM patients JOIN province_names
ON patients.province_id = province_names.province_id
GROUP BY province_name 
ORDER BY province_population DESC;
```

</details>

---

## Q22. For every admission, display the patient's full name, their admission diagnosis, and their doctor's full name who diagnosed their problem.

<details>
<summary> SQL Answer for Q22 </summary>

```sql
SELECT CONCAT(patients.first_name, " ", patients.last_name), admissions.diagnosis, CONCAT(doctors.first_name, " ", doctors.last_name)
FROM admissions
JOIN patients ON patients.patient_id = admissions.patient_id
JOIN doctors ON doctors.doctor_id = admissions.attending_doctor_id;
```

</details>

---

## Q23. display the first name, last name and number of duplicate patients based on their first name and last name. (Ex: A patient with an identical name can be considered a duplicate.)

<details>
<summary> SQL Answer for Q23 </summary>

```sql
SELECT first_name, last_name, COUNT(*)
FROM patients
GROUP BY first_name, last_name
HAVING COUNT(*) > 1;
```

</details>

---

## Q24. Display patient's full name, height in the units feet rounded to 1 decimal, weight in the unit pounds rounded to 0 decimals, birth_date, gender non abbreviated. Convert CM to feet by dividing by 30.48. Convert KG to pounds by multiplying by 2.205.

<details>
<summary> SQL Answer for Q24 </summary>

```sql
SELECT CONCAT(first_name, " ", last_name) AS full_name,
ROUND(height/30.48, 1) AS height_in_feet,
ROUND(weight * 2.205) AS weight_in_pounds,
birth_date,
CASE
	WHEN gender = 'M' THEN 'MALE'
    ELSE 'FEMALE'
END AS gender_full
FROM patients;
```

</details>

---

## Q25. Show patient_id, first_name, last_name from patients whose does not have any records in the admissions table. (Their patient_id does not exist in any admissions.patient_id rows.)

<details>
<summary> SQL Answer for Q25 </summary>

```sql
SELECT patients.patient_id, first_name, last_name
FROM patients
WHERE patients.patient_id NOT IN (SELECT admissions.patient_id FROM admissions);
```

</details>

---

