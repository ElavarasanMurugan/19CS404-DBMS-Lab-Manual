# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

![alt text](Questions/image-1.png)

```sql
SELECT SUM(workhour) AS "Total working hours"
FROM employee1;
```

**Output:**

![alt text](Outputs/image-1.png)

**Question 2**

![alt text](Questions/image-2.png)

```sql
SELECT AVG(LENGTH(email)) AS "avg_email_length"
FROM customer;
```

**Output:**

![alt text](Outputs/image-2.png)

**Question 3**

![alt text](Questions/image-3.png)

```sql
SELECT name,LENGTH(name) as length
FROM customer
ORDER BY LENGTH(name) DESC
LIMIT 1;
```

**Output:**

![alt text](Outputs/image-3.png)

**Question 4**

![alt text](Questions/image-4.png)

```sql
SELECT PatientID,COUNT(*) AS "TotalMedications"
FROM Prescriptions
GROUP BY PatientID
ORDER BY PatientID;
```

**Output:**

![alt text](Outputs/image-4.png)

**Question 5**

![alt text](Questions/image-5.png)

```sql
SELECT strftime('%Y',ValidityPeriod) AS ValidityYear,COUNT(*) AS TotalPatients
FROM Insurance
WHERE ValidityPeriod IS NOT NULL
GROUP BY ValidityYear
ORDER BY ValidityYear;
```

**Output:**

![alt text](Outputs/image-5.png)

**Question 6**

![alt text](Questions/image-6.png)

```sql
SELECT DoctorID,COUNT(DISTINCT RecordID) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

![alt text](Outputs/image-6.png)

**Question 7**

![alt text](Questions/image-7.png)

```sql
SELECT age AS "age",MIN(income) AS "Income"
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000
ORDER BY age;
```

**Output:**

![alt text](Outputs/image-7.png)

**Question 8**

![alt text](Questions/image-8.png)

```sql
SELECT jdate,MIN(workhour)
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10
ORDER BY jdate
```

**Output:**

![alt text](Outputs/image-8.png)

**Question 9**

![alt text](Questions/image-9.png)

```sql
SELECT category_id,SUM(price) AS "Total_Cost"
FROM products
GROUP BY category_id
HAVING SUM(price) > 50
ORDER BY category_id;
```

**Output:**

![alt text](Outputs/image-9.png)

**Question 10**

![alt text](Questions/image-10.png)

```sql
SELECT age,AVG(income)
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000
ORDER BY age;
```

**Output:**

![alt text](Outputs/image-10.png)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
