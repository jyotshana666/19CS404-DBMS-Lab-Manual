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
How many patients are covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```sql
SELECT InsuranceCompany, COUNT(*) AS TotalPatients FROM Insurance GROUP BY InsuranceCompany;
```

**Output:**

![Screenshot 2025-05-19 185347](https://github.com/user-attachments/assets/67997298-ae32-4a2d-a74c-0197c8ba57c6)


**Question 2**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table



```sql
SELECT PatientID,COUNT(*) AS TotalMedications FROM Prescriptions GROUP BY(PatientID);
```

**Output:**

![Screenshot 2025-05-19 185425](https://github.com/user-attachments/assets/d83b7f5a-9b06-4ff6-a965-0cd0507908f2)


**Question 3**
---
How many doctors specialize in each medical specialty?

Sample table:Doctors Table

```sql
SELECT Specialty , COUNT(*) AS TotalDoctors FROM Doctors GROUP BY Specialty;
```

**Output:**

![Screenshot 2025-05-19 185459](https://github.com/user-attachments/assets/9b9868f7-3838-4ce7-9518-8b22fb9d92bb)


**Question 4**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT COUNT(name) AS employees_count FROM employee WHERE income > 50000;
```

**Output:**
![image](https://github.com/user-attachments/assets/4425e139-a5ed-4eb4-8751-09bc83321bbf)


**Question 5**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT name , email,MIN(LENGTH(email)) AS min_email_length FROM customer; 
```

**Output:**

![image](https://github.com/user-attachments/assets/5099670d-1603-42c2-b9b3-bba3e8b04723)


**Question 6**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

```sql
SELECT SUM(inventory) AS total FROM fruits WHERE unit = 'LB';
```

**Output:**

![image](https://github.com/user-attachments/assets/d55f5ee5-901c-4ea0-84d3-bd029625a838)


**Question 7**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer



```sql
SELECT COUNT(*) AS COUNT FROM customer WHERE city <> 'Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/48bfa0fe-fcbe-420e-82bd-86374b069cd1)


**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1



```sql
SELECT occupation,SUM(workhour) FROM employee1 GROUP BY occupation HAVING SUM(workhour) > 20;
```

**Output:**

![Screenshot 2025-05-19 185839](https://github.com/user-attachments/assets/0fbb5ca6-b2ab-4bbb-93e0-d67e16ee3bc0)


**Question 9**
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee

```sql
SELECT age, MAX(income) FROM employee GROUP BY age HAVING MAX(income) > 2000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/6f26ecca-ef93-49a1-892f-07da55813eab)


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

```sql
SELECT age , AVG(income) FROM employee GROUP BY age HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

![image](https://github.com/user-attachments/assets/4c09c570-54a8-408c-8324-9f9fb7f756a5)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
![image](https://github.com/user-attachments/assets/fea05eaf-f4cd-483f-a006-46e5691148fc)

