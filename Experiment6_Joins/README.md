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
-- Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "salesman_name") and the "cust_name" column from the "customer" table (aliased as "customer_name"), with a left join on the "salesman_id" column.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
-- SELECT s.name AS "salesman_name", c.cust_name AS "customer_name" 
FROM Salesman s LEFT JOIN Customer c
ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="1236" height="893" alt="image" src="https://github.com/user-attachments/assets/d6f19f9c-30e6-4739-b442-92b7e5877e99" />


**Question 2**
---
-- Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

```sql
-- SELECT p.first_name, s.*
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1232" height="394" alt="image" src="https://github.com/user-attachments/assets/f298dc03-6520-4bd3-9188-a456ef18e188" />


**Question 3**
---
-- Write an SQL query that retrieves all columns from the 'customer' table (using the alias 'c'), performs a LEFT JOIN with the 'orders' table on the 'customer_id' column, and includes only those orders with an order date after '2012-08-17'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
-- SELECT c.*
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**

<img width="1239" height="834" alt="image" src="https://github.com/user-attachments/assets/34f84213-b949-428b-932b-c42b56930636" />


**Question 4**
---
-- From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
-- SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM orders o
INNER JOIN customer c
    ON o.customer_id = c.customer_id
INNER JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1236" height="768" alt="image" src="https://github.com/user-attachments/assets/f918df62-d7f8-4d5a-9219-ccc08222c2cd" />


**Question 5**
---
-- Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

```sql
-- SELECT p.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1244" height="392" alt="image" src="https://github.com/user-attachments/assets/d3fd8581-f4ad-4481-bdc6-7d1df16c2f8e" />


**Question 6**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

```sql
-- SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily'
AND d.last_name = 'Johnson'
AND p.discharge_date IS NOT NULL;
```

**Output:**

<img width="1236" height="387" alt="image" src="https://github.com/user-attachments/assets/49385a3a-ef39-40ed-b132-6019e7456e83" />


**Question 7**
---
-- Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
-- SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders o
JOIN customer c 
    ON o.customer_id = c.customer_id
JOIN salesman s 
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1234" height="772" alt="image" src="https://github.com/user-attachments/assets/264d62c7-12c2-4112-b86c-6356166e8bea" />


**Question 8**
---
-- From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```sql
-- SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.city,
    s.commission
FROM customer c
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
AND s.commission > 0.12;
```

**Output:**

<img width="1235" height="616" alt="image" src="https://github.com/user-attachments/assets/6f955c12-ba75-44dd-b3bf-e7feb62ff429" />


**Question 9**
---
--  From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
-- SELECT c.cust_name AS "Customer Name", c.city, s.name AS "Salesman", s.commission
FROM customer c INNER JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1233" height="906" alt="image" src="https://github.com/user-attachments/assets/00d0b0cd-30ec-4bdc-8cd0-1d79c715bd13" />


**Question 10**
---
-- From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
-- SELECT c.cust_name, c.city, c.grade, s.name AS "Salesman", s.city
FROM customer c INNER JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1235" height="765" alt="image" src="https://github.com/user-attachments/assets/63eca2b2-db09-4349-83bd-63732dc9d3c3" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
