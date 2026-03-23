# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-- Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

```sql
-- SELECT name, city FROM customer
WHERE city IN (SELECT city FROM customer WHERE id in (3,7));
```

**Output:**

<img width="1236" height="445" alt="image" src="https://github.com/user-attachments/assets/a91f280f-124e-422a-a2c1-017a94be2dba" />


**Question 2**
---
-- From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

```sql
-- SELECT * FROM ORDERS
WHERE purch_amt > (SELECT AVG(purch_amt) FROM ORDERS WHERE ord_date = '2012-10-10');
```

**Output:**

<img width="1237" height="447" alt="image" src="https://github.com/user-attachments/assets/3384494f-08eb-4efb-b48a-9f961ca70f56" />


**Question 3**
---
-- Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
-- SELECT * FROM GRADES g
WHERE grade = (SELECT MIN(grade) FROM GRADES WHERE subject = g.subject);

```

**Output:**

<img width="1234" height="428" alt="image" src="https://github.com/user-attachments/assets/0136158a-2fd2-48c4-9682-0f351323f4a2" />


**Question 4**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.


```sql
-- SELECT * FROM CUSTOMERS 
WHERE salary < 2500;
```

**Output:**

<img width="1235" height="440" alt="image" src="https://github.com/user-attachments/assets/55f1cf90-81ed-496e-9303-e512fdbb10ec" />


**Question 5**
---
-- Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
-- SELECT medication_id AS medic, medication_name, dosage FROM Medications
WHERE dosage = (SELECT MIN(dosage) FROM Medications);
```

**Output:**

<img width="1226" height="377" alt="image" src="https://github.com/user-attachments/assets/eab774b1-62aa-4cec-9243-042f9dfe70fb" />


**Question 6**
---
-- Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
-- SELECT * FROM GRADES g
WHERE grade = (SELECT MAX(grade) FROM GRADES WHERE subject = g.subject);

```

**Output:**

<img width="1235" height="425" alt="image" src="https://github.com/user-attachments/assets/3a31e9ff-9445-4496-bf4b-1b935a1f74bc" />


**Question 7**
---
-- From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

```sql
-- SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s
ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

**Output:**

<img width="1264" height="459" alt="image" src="https://github.com/user-attachments/assets/a3ead513-3f2c-4c5f-b49d-02e2daaf598e" />


**Question 8**
---
-- From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

```sql
-- SELECT s.salesman_id, s.name FROM salesman s JOIN customer c
ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id
HAVING COUNT(c.customer_id)>1;
```

**Output:**

<img width="1230" height="455" alt="image" src="https://github.com/user-attachments/assets/0f83eced-210d-464f-becc-0e14bae845de" />


**Question 9**
---
-- Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.

```sql
-- SELECT name FROM customer
WHERE phone IN (SELECT phone FROM customer GROUP BY phone HAVING COUNT(*) = 1);
```

**Output:**

<img width="1231" height="437" alt="image" src="https://github.com/user-attachments/assets/edfb1232-1a47-4208-b535-8e60608254b4" />


**Question 10**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
-- SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);
```

**Output:**

<img width="1229" height="414" alt="image" src="https://github.com/user-attachments/assets/87573b1b-e557-4903-8fe4-598cff7fbc68" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
