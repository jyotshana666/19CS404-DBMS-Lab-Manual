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

Create a new table named contacts with the following specifications:

contact_id as INTEGER and primary key.

first_name as TEXT and not NULL.

last_name as TEXT and not NULL.

email as TEXT.

phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
create table contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL CHECK(LENGTH(phone)>=10)
);
```

**Output:**

![S1](https://github.com/user-attachments/assets/a58252e0-77c7-41df-bfd1-847f8681b307)
![S2](https://github.com/user-attachments/assets/45a9754a-9d74-44f0-b081-9dfffb98f44a)


**Question 2**
---
Create a new table named item with the following specifications and constraints:
1. item_id as TEXT and as primary key.
2. item_desc as TEXT.
3. rate as INTEGER.
4. icom_id as TEXT with a length of 4.
5. icom_id is a foreign key referencing com_id in the company table.
6. The foreign key should set NULL on updates and deletes.
7. item_desc and rate should not accept NULL.

```sql
create table item(
item_id TEXT PRIMARY KEY,
item_desc TEXT not NULL,
rate INTEGER not NULL,
icom_id TEXT CHECK(LENGTH(icom_id)=4),
FOREIGN KEY(icom_id) REFERENCES company(com_id) ON DELETE SET NULL ON UPDATE SET NULL
);
```

**Output:**

![S1](https://github.com/user-attachments/assets/e6424407-2f0a-4d5c-af10-183d7929aa6a)


**Question 3**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
1. designation as VARCHAR(50)
2. net_salary as NUMBER
3. dob as DATE

```sql
alter table Companies
add column designation varchar(50);
alter table Companies
add column net_salary number;
alter table Companies
add column dob date;
```

**Output:**

![S1](https://github.com/user-attachments/assets/3eb90d38-015d-4c0a-b1cb-953dfbab62a9)


**Question 4**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
insert into Customers(CustomerID,Name,Address,City,ZipCode)
VALUES('302','Laura Croft','456 Elm St','Seattle','98101'),
      ('303','Bruce Wayne','789 Oak St','Gotham','10001');
```

**Output:**

![S1](https://github.com/user-attachments/assets/0be15cd9-650c-49d2-bc39-205b11d42b39)


**Question 5**
---
Create a table named Orders with the following columns:

OrderID as INTEGER

OrderDate as TEXT

CustomerID as INTEGER

```sql
create table Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER 
);
```

**Output:**

![S1](https://github.com/user-attachments/assets/1cbcbb7a-29b8-4b83-bfd5-8508487dbc2a)
![S2](https://github.com/user-attachments/assets/f61a5e2b-e013-46c9-8ede-9267d6d9db88)


**Question 6**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.

product_name as TEXT and not NULL.

list_price as DECIMAL (10, 2) and not NULL.

discount as DECIMAL (10, 2) with a default value of 0 and not NULL.

A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount

discount is greater than or equal to 0

list_price is greater than or equal to 0

```sql
create table products(
product_id INTEGER PRIMARY KEY,
product_name TEXT not NULL,
list_price DECIMAL(10, 2) not NULL CHECK(list_price>=0),
discount DECIMAL(10, 2) not NULL DEFAULT 0 CHECK(discount>=0),
CHECK(list_price>=discount)
);
```

**Output:**

![S1](https://github.com/user-attachments/assets/116722ab-de07-4b24-b10b-72c0af142895)
![S2](https://github.com/user-attachments/assets/b1817dd1-d328-4833-90f6-efd040469d6b)


**Question 7**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key. 

EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).

ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).

AssignmentDate as DATE should be NOT NULL.

```sql
create table ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER, 
AssignmentDate DATE NOT NULL,
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

![S1](https://github.com/user-attachments/assets/67d72a84-98a8-4f40-867e-b4d37d0b0f26)
![S2](https://github.com/user-attachments/assets/9c0015ce-59a6-4335-94a1-4c72e300a38f)


**Question 8**
---
Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

```sql
alter table Student_details
add column Country TEXT;
```

**Output:**

![S1](https://github.com/user-attachments/assets/ab126abd-0747-4a24-baba-4e209cc3c34c)


**Question 9**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
insert into Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('1','Sarah Parker','Manager','HR','60000');
```

**Output:**

![S1](https://github.com/user-attachments/assets/180adf58-922e-4e9f-94c0-628b971c755f)


**Question 10**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
insert into Customers(CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email from Old_customers;
```

**Output:**

![S1](https://github.com/user-attachments/assets/943ebbbe-d165-4cf6-96a0-40e76b3414cb)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
![GRADES](https://github.com/user-attachments/assets/b6602c23-1ee2-442f-af43-b738cd5cd2af)

