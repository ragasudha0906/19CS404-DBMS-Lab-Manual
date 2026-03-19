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
--
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

```
SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**
<img width="1172" height="295" alt="1" src="https://github.com/user-attachments/assets/477e1aea-36ca-403b-99ce-3cff76f7ddda" />



**Question 2**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?

```
SELECT MAX(price) - MIN(price) AS price_diff
FROM fruits;
```

**Output:**

<img width="1185" height="300" alt="2" src="https://github.com/user-attachments/assets/dd2c0581-dcd5-41e0-8c8c-dafa3cfcd2b2" />

**Question 3**
---
Write a SQL query to count the number of customers. Return number of customers.

```
SELECT COUNT(*) AS COUNT
FROM Customer;
```

**Output:**

<img width="687" height="247" alt="3" src="https://github.com/user-attachments/assets/38f60c5a-ca4a-4170-a324-29e6b0dd0464" />


**Question 4**
---
How many patients are covered by each insurance company?

```
SELECT InsuranceCompany,
COUNT(PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**
<img width="1167" height="672" alt="Screenshot 2026-03-19 105547" src="https://github.com/user-attachments/assets/11c8b0f7-65fb-44f1-b2d5-f3d5200a5cd0" />


**Question 5**
---
What is the most common diagnosis among patients?

```
SELECT Diagnosis, COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC LIMIT 1;
```

**Output:**
<img width="1135" height="301" alt="5" src="https://github.com/user-attachments/assets/924225e0-6691-494a-b74d-9f762ebd5dba" />


**Question 6**
---
What is the total number of medications prescribed for each patient?

```
SELECT PatientID,
COUNT(*) AS  TotalMedications
FROM Prescriptions
GROUP BY PatientID;
```

**Output:**

<img width="1062" height="738" alt="6" src="https://github.com/user-attachments/assets/6bf907e0-4cae-41d9-81a0-c196da0c8bb3" />

**Question 7**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```
SELECT age,SUM(income)
FROM employee
GROUP BY age
HAVING SUM(income)>1000000;
```

**Output:**

<img width="1155" height="397" alt="7" src="https://github.com/user-attachments/assets/d2a497ac-9538-4aef-80f1-c41cb683a569" />

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```
SELECT jdate, SUM(workhour) 
FROM employee1
GROUP BY jdate
HAVING SUM(workhour)>40;
```

**Output:**

<img width="1157" height="371" alt="8" src="https://github.com/user-attachments/assets/bae24b8a-01ed-4caf-9198-4c51fec11d3c" />

**Question 9**
---
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

```
SELECT address, AVG(salary) 
FROM customer1
GROUP BY address
HAVING AVG(salary)<15000;
```

**Output:**
<img width="1082" height="587" alt="9" src="https://github.com/user-attachments/assets/e7f47337-4107-4e1e-b4df-c2aae907f6b9" />


**Question 10**
---

Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.
```
SELECT 
  age,
  MAX(income)
FROM employee
GROUP BY age
HAVING MAX(income)>2000000
ORDER BY age;
```

**Output:**

<img width="1047" height="345" alt="10" src="https://github.com/user-attachments/assets/aa3aa03e-4862-49f4-91eb-a79938384801" />

## MODULE 3 GRADE
<img width="1137" height="98" alt="image" src="https://github.com/user-attachments/assets/39cb9010-4b66-4447-9bcc-19c59e828ef5" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
