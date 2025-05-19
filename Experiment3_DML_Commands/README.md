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
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE products SET reorder_lvl = reorder_lvl * 0.7 
WHERE LOWER(product_name) LIKE "%cream%" AND quantity > reorder_lvl;
```

**Output:**
![S1](https://github.com/user-attachments/assets/b980db87-261a-462e-97f8-8b8b31193bbe)
![S2](https://github.com/user-attachments/assets/a224341b-6de0-4532-bac5-555fcc338f9d)



**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products SET product_name = 'Premium Bread' WHERE product_id = 5;
```

**Output:**

![S1](https://github.com/user-attachments/assets/276c34f7-fb4a-4204-b44f-3f48d1d11671)
![S2](https://github.com/user-attachments/assets/37f80cb3-d57d-4262-9fd5-c9f597960687)


**Question 3**
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products SET reorder_lvl = 20 WHERE quantity < 10 AND category = 'Snacks';
```

**Output:**

![S1](https://github.com/user-attachments/assets/561b08a3-a497-4b3b-b886-b34dd7b4e21a)
![S2](https://github.com/user-attachments/assets/e5864295-3f42-4e8f-b024-0b922c120355)


**Question 4**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
UPDATE Suppliers SET address = '58 Lakeview, Magnolia' WHERE supplier_id = 5;
```

**Output:**

![Screenshot 2025-05-19 183923](https://github.com/user-attachments/assets/40832d4b-1edc-42d0-90fc-3338f7d27e38)
![Screenshot 2025-05-19 183928](https://github.com/user-attachments/assets/cd306452-56d7-4191-af6c-dfdd68f76839)


**Question 5**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees SET hire_date = '2024-01-24' WHERE department_id = 50;
```

**Output:**

![Screenshot 2025-05-19 184158](https://github.com/user-attachments/assets/cf2b19cb-c444-404b-81f7-d6c8c34701a8)


**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM Surgeries WHERE surgery_date = '2024-02-28';
```

**Output:**

![Screenshot 2025-05-19 184233](https://github.com/user-attachments/assets/278c05eb-2a84-4e50-b99f-fe3452e484f9)


**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```sql
DELETE FROM Customer WHERE CUST_CITY LIKE 'L%';
```

**Output:**

![Screenshot 2025-05-19 184336](https://github.com/user-attachments/assets/a0232f34-e82a-4e2a-9f24-7a805953751e)


**Question 8**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors WHERE (specialization = 'Pediatrics' OR specialization = 'Cardiology') AND (last_name LIKE '%Brown');
```

**Output:**

![Screenshot 2025-05-19 184427](https://github.com/user-attachments/assets/3106ceb8-9123-4968-b864-832fe9bdf41f)


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer
```sql
DELETE FROM Customer WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**

![Screenshot 2025-05-19 184502](https://github.com/user-attachments/assets/1e6bc331-4811-4d85-9239-94d47adf3260)
![Screenshot 2025-05-19 184507](https://github.com/user-attachments/assets/59d29faa-2625-48b4-937d-913b9c56f834)


**Question 10**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

```sql
DELETE FROM Customer WHERE CUST_COUNTRY = 'UK' AND WORKING_AREA = 'London' AND GRADE < 3;
```

**Output:**

![Screenshot 2025-05-19 184558](https://github.com/user-attachments/assets/60de7276-c41e-46b2-bdbc-f10b339b9395)
![Screenshot 2025-05-19 184606](https://github.com/user-attachments/assets/2324ee2f-b040-4ec6-9168-68ba7ab771e9)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

![Screenshot 2025-05-19 184639](https://github.com/user-attachments/assets/8bc90374-f49d-4823-8d70-1d85a7e3ad18)

