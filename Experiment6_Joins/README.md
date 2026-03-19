# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.

```
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id=c.salesman_id
WHERE c.city='New York';
```

**Output:**

<img width="860" height="383" alt="image" src="https://github.com/user-attachments/assets/f0f63b09-fd27-4000-945a-9a76b122f486" />


**Question 2**
---

Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.
```
select c.cust_name , o.ord_no, o.ord_date, o.purch_amt
from orders o
left join customer c on o.customer_id=c.customer_id
where purch_amt>1000;
```

**Output:**
<img width="1218" height="613" alt="image" src="https://github.com/user-attachments/assets/9a924b31-f82d-43ed-b9c1-ab0edbe5005b" />


**Question 3**
---

Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.


```
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt
FROM  customer c
LEFT JOIN orders o ON c.customer_id=o.customer_id
WHERE c.city='London';
```

**Output:**

<img width="1252" height="368" alt="image" src="https://github.com/user-attachments/assets/1d141f46-afc6-4383-a116-718b4724e56a" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column. Include conditions to filter for patients discharged between '2024-03-01' and '2024-03-31' but not admitted during the same period.



```
SELECT p.first_name,s.*
FROM patients p
INNER JOIN surgeries s ON p.patient_id=s.patient_id
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31' AND p.admission_date NOT BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**


<img width="1257" height="272" alt="image" src="https://github.com/user-attachments/assets/04fa5502-8261-4b33-879f-05e9262736c2" />

**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```
SELECT p.first_name AS patient_name,d.specialization AS Doctor_speciali
FROM patients p
INNER JOIN doctors d ON p.doctor_id=d.doctor_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**


<img width="965" height="306" alt="image" src="https://github.com/user-attachments/assets/78e89282-fc18-4afc-ae0d-208d36bd8acc" />

**Question 6**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```SELECT 
    customer.cust_name, 
    customer.city, 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt AS "Order Amount"
FROM 
    customer
LEFT JOIN 
    orders ON customer.customer_id = orders.customer_id
ORDER BY 
    orders.ord_date ASC;

```

**Output:**


<img width="1255" height="918" alt="image" src="https://github.com/user-attachments/assets/1af2f46c-6ebb-4814-b91e-cf76b6ede730" />

**Question 7**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 
```
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name AS Salesman,s.commission
FROM orders o
JOIN customer c ON o.customer_id=c.customer_id
JOIN salesman s ON o.salesman_id=s.salesman_id;
```

**Output:**


<img width="1296" height="770" alt="image" src="https://github.com/user-attachments/assets/8484f82c-7e53-428d-95e0-7962277200be" />

**Question 8**
---

 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.
```
SELECT c.cust_name as "Customer Name",c.city,s.name AS "Salesman",s.commission
FROM customer c
JOIN salesman s ON c.salesman_id=s.salesman_id;
```

**Output:**

 <img width="1245" height="721" alt="image" src="https://github.com/user-attachments/assets/64702efb-c2b3-4562-a4d1-890a200877b8" />


**Question 9**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

```
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';

```

**Output:**


<img width="858" height="373" alt="image" src="https://github.com/user-attachments/assets/3cc27c9b-172f-4b94-af3d-5002f2b3533f" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'
```
SELECT p.*
FROM patients p
INNER JOIN appointments a ON p.patient_id=a.patient_id
WHERE a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

<img width="1822" height="320" alt="image" src="https://github.com/user-attachments/assets/e7dd7150-ae8f-4a4f-a25a-7ef020952352" />

## MODULE 5 GRADE


<img width="1141" height="72" alt="image" src="https://github.com/user-attachments/assets/22acb4ef-5bd6-49a4-b746-09d191f078ef" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
