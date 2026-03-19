# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1188" height="277" alt="dm1" src="https://github.com/user-attachments/assets/00cf41e1-fffd-4b21-a080-6a30d31a817f" />


**Question 2**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```
CREATE TABLE jobs (
    job_id INTEGER,
    job_title TEXT DEFAULT ' ',
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER DEFAULT NULL
);
```

**Output:**
<img width="1797" height="242" alt="dm2" src="https://github.com/user-attachments/assets/63042a6d-8eed-4071-826c-12c0fcde2a9d" />



**Question 3**
---
Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'

```
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;
ALTER TABLE Employees
RENAME COLUMN job_title TO
Designation;
```

**Output:**

<img width="1270" height="253" alt="dm3" src="https://github.com/user-attachments/assets/4995f2d6-971d-4c3b-9fa0-3ec26d6d14f8" />


**Question 4**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

```
INSERT INTO Employee(EmployeeID,Name,Position)
VALUES(4,'Emily White','Analyst')
```

**Output:**
<img width="1127" height="296" alt="dm4" src="https://github.com/user-attachments/assets/9ee77a39-0a20-4c67-ae1d-c5de5900542d" />


**Question 5**
---

In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
INSERT INTO Student_details(RollNo,Name,Gender,Subject,Marks) VALUES
(205, 'Olivia Green', 'F', NULL, NULL),
(207, 'Liam Smith', 'M', 'Mathematics', 85),
(208, 'Sophia Johnson', 'F', 'Science', NULL);
```

**Output:**

<img width="1226" height="210" alt="dm5" src="https://github.com/user-attachments/assets/3fb3f3eb-048f-46a3-81a2-ba65ae3473c6" />

**Question 6**
---

Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).
```
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**
<img width="1267" height="217" alt="dm6" src="https://github.com/user-attachments/assets/9f4c94b9-3bf4-4bc7-b172-c2f0227cb796" />

**Question 7**
---
Create a new table named item with the following specifications and constraints:
1. item_id as TEXT and as primary key.
2. item_desc as TEXT.
3. rate as INTEGER.
4. icom_id as TEXT with a length of 4.
5. icom_id is a foreign key referencing com_id in the company table.
6. The foreign key should cascade updates and deletes.
7. item_desc and rate should not accept NULL.

```
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT,
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
        ON UPDATE CASCADE
        ON DELETE CASCADE
);
```

**Output:**
<img width="1247" height="242" alt="dm7" src="https://github.com/user-attachments/assets/8d1dbe4e-6839-42b0-809a-9a244637330a" />


**Question 8**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```
CREATE TABLE Department(
  DepartmentID INTEGER PRIMARY KEY,
  DepartmentName TEXT NOT NULL UNIQUE,
  Location TEXT
);
```

**Output:**
<img width="1831" height="188" alt="dm8" src="https://github.com/user-attachments/assets/8a102271-879b-4921-8dd1-267f2a8a9274" />



**Question 9**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**
<img width="1263" height="212" alt="dm9" src="https://github.com/user-attachments/assets/b2e2b492-6ccf-48ea-8d5a-7f390ca38e0b" />


**Question 10**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary INTEGER CHECK (Salary>0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES DepartmentS(DepartmentID)
)
```

**Output:**
<img width="1291" height="261" alt="dm10" src="https://github.com/user-attachments/assets/b8bb4c32-f1e3-41aa-8efa-d39111e7db80" />
## MODULE 1 GRADE

<img width="1156" height="72" alt="dm11" src="https://github.com/user-attachments/assets/8a640f13-9c98-4c9f-aa59-20b2528a7de0" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
