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
-- How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table



For example:

Result
Specialty          Gender    TotalDoctors
-----------------  --------  --------------
Cardiology         Male      1
Dermatology        Male      1
Gastroenterology   Female    4
Gastroenterology   Male      1
Pediatrics         Female    1
Pediatrics         Male      2


```sql
-- SELECT Specialty, Gender, COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty, Gender
ORDER BY Specialty, Gender;
```

**Output:**

<img width="1817" height="1189" alt="image" src="https://github.com/user-attachments/assets/9eaf7b3c-9c8c-4926-9b85-3eb7bbe2f6ce" />


**Question 2**
---
-- What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table



For example:

Result
DoctorID    TotalAppointments
----------  -----------------
1           1
2           3
5           3
9           2
10          1


```sql
-- SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="1308" height="1007" alt="image" src="https://github.com/user-attachments/assets/a31bd348-eb5c-41f7-8016-036edf652356" />


**Question 3**
---
-- How many appointments are scheduled for each doctor?

Sample table:Appointments Table



For example:

Result
DoctorID    TotalAppointments
----------  -----------------
3           3
4           2
6           1
7           3
10          1


```sql
-- SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;
```

**Output:**

<img width="1275" height="1148" alt="image" src="https://github.com/user-attachments/assets/31d42726-4f27-4889-8315-b3a1c99f1df7" />

**Question 4**
---
-- Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
AVERAGE
----------
1461.765


```sql
-- SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="728" height="629" alt="image" src="https://github.com/user-attachments/assets/200aed35-296d-45a2-93d4-37e2297c3033" />


**Question 5**
---
-- Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000

 

For example:

Result
COUNT
----------
4


```sql
-- SELECT COUNT(DISTINCT age) AS COUNT
FROM employee;
```

**Output:**

<img width="930" height="623" alt="image" src="https://github.com/user-attachments/assets/143b99c7-00b3-4c59-bad5-0533677f7be6" />


**Question 6**
---
-- Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
total
----------
225


```sql
-- SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**

<img width="717" height="633" alt="image" src="https://github.com/user-attachments/assets/1f32c56d-f086-45ab-814e-bb72d7af5ddc" />


**Question 7**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer



 

For example:

Result
COUNT
----------
1


```sql
-- SELECT COUNT(*) AS COUNT
FROM customer
WHERE city = 'Noida';
```

**Output:**

<img width="778" height="616" alt="image" src="https://github.com/user-attachments/assets/7a74f43e-ade1-4d64-8ee9-1447ebba0d36" />


**Question 8**
---
-- Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products



For example:

Result
category_id  AVG(Price)
-----------  ----------
1            12.375


```sql
-- SELECT category_id, AVG(Price) 
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;
```

**Output:**

<img width="1100" height="678" alt="image" src="https://github.com/user-attachments/assets/ff9fedd5-2762-4111-8b95-819f325322b2" />


**Question 9**
---
-- Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1



For example:

Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0

```sql
-- SELECT occupation, AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="1123" height="751" alt="image" src="https://github.com/user-attachments/assets/e55b85d4-5f11-4965-b420-80b91d10cce1" />


**Question 10**
---
-- Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee



For example:

Result
city        Income
----------  ----------
Alaska      450000
Arizona     1000000
California  5300000
Florida     5350000
Georgia     250000


```sql
-- SELECT city, SUM(income) AS Income
FROM employee
GROUP BY city
HAVING SUM(income) > 200000;
```

**Output:**

<img width="1061" height="991" alt="image" src="https://github.com/user-attachments/assets/02f6e23d-e8cb-43bc-af6d-2a385a6547d9" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
