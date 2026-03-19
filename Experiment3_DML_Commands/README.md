# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.

```
SELECT
    product_id,
    discounted_price,
    discount_percentage,
    discounted_price/(1-discount_percentage) AS original_price
FROM products;
```

**Output:**

<img width="1212" height="228" alt="sm1" src="https://github.com/user-attachments/assets/65d97c7c-8c40-4d41-a89c-c12e6969b377" />


**Question 2**
---
write a SQL query to create a union of two queries that shows the customer id, cities, and ratings of all customers. Those with a rating of 300 or greater will have the words 'High Rating', while the others will have the words 'Low Rating'.

```
SELECT customer_id,city,grade,
CASE
    WHEN grade>=300 THEN 'High Rating'
    ELSE 'Low Rating'
END AS Rating
FROM customer
ORDER BY customer_id;
```

**Output:**
<img width="962" height="470" alt="image" src="https://github.com/user-attachments/assets/745b6d43-8eea-4baf-80ff-c2d404f56f12" />


**Question 3**
---
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

```
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE city='New York' OR grade<=100;
```

**Output:**
<img width="1182" height="352" alt="sm3" src="https://github.com/user-attachments/assets/ae3fcaa3-a784-4c53-87ac-9ed174b229ce" />


**Question 4**
---
Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.

```
SELECT SUBSTR(EmpLname, 1, 4)
FROM EmployeeInfo;
```

**Output:**
<img width="876" height="281" alt="image" src="https://github.com/user-attachments/assets/132a5242-3900-49c2-9d38-ca77bdd949da" />


**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

```
DELETE FROM customer 
WHERE grade<2;
```

**Output:**
<img width="921" height="488" alt="image" src="https://github.com/user-attachments/assets/d5a850b9-5121-444b-8400-16e249948618" />


**Question 6**
---
Write a SQL query to Select all patients who were admitted for one day.

```
SELECT 
    patient_id,
    first_name,
    admission_date,
    discharge_date
FROM Patients
WHERE admission_date=discharge_date;
```

**Output:**
<img width="1188" height="281" alt="image" src="https://github.com/user-attachments/assets/2f509e36-4544-4743-8d6b-4660a7939130" />


**Question 7**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```
UPDATE purchases
SET
    per_unit_price=25,
    total_price=quantity*25
WHERE purchase_date='2022-08-15'
  AND product_id=12;
```

**Output:**
<img width="1782" height="343" alt="image" src="https://github.com/user-attachments/assets/53730ab8-344c-46fc-8499-4ead07c4af9c" />


**Question 8**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

```
UPDATE suppliers
SET supplier_name=UPPER(supplier_name)
WHERE contact_person LIKE '%Singh%';
```

**Output:**

<img width="1781" height="216" alt="image" src="https://github.com/user-attachments/assets/801c35df-2dc2-4941-a920-032811130dc2" />


**Question 9**
---
Show the categoryName and description from the categories table sorted by categoryName.

```
SELECT 
    CategoryName,
    Description
FROM categories
ORDER BY CategoryName;
```

**Output:**
<img width="1182" height="527" alt="image" src="https://github.com/user-attachments/assets/2db3d2db-498a-4467-9659-c92cae4f07f9" />


**Question 10**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```
DELETE FROM Surgeries
WHERE surgery_date='2024-02-28';
```

**Output:**

<img width="1203" height="321" alt="image" src="https://github.com/user-attachments/assets/fd7a2899-2049-44b8-b190-b95241d45da9" />

## MODULE 2 GRADE

<img width="1136" height="77" alt="sm4" src="https://github.com/user-attachments/assets/1c87a766-8208-4e05-943f-6f3aea53d6a3" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
