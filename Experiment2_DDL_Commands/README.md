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
<img width="1088" height="317" alt="image" src="https://github.com/user-attachments/assets/b52fcd66-5bdb-464c-b8f3-3da83301682e" />


```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,

FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectId));
```

**Output:**

<img width="1012" height="210" alt="image" src="https://github.com/user-attachments/assets/4b6bf3d0-1382-4505-aa50-d9902681a32e" />


**Question 2**
---
<img width="1133" height="412" alt="image" src="https://github.com/user-attachments/assets/fbb09691-9a79-4d33-84eb-165450f69e6f" />


```sql
ALTER TABLE Student_details
ADD ParentsNumber number;
ALTER TABLE Student_details
ADD Adhar_Number number ;
```

**Output:**

<img width="1141" height="292" alt="image" src="https://github.com/user-attachments/assets/4ae2c6a0-ac55-4f6b-8fed-0040cb8ed2ca" />


**Question 3**
---
<img width="1041" height="332" alt="image" src="https://github.com/user-attachments/assets/36838566-9cab-41ea-9ec8-d505d41dd7de" />


```sql
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT NOT NULL UNIQUE,
Location TEXT);
```

**Output:**

<img width="1082" height="190" alt="image" src="https://github.com/user-attachments/assets/44112df4-52d8-474d-b5e8-5c826df96e91" />


**Question 4**
---
<img width="832" height="471" alt="image" src="https://github.com/user-attachments/assets/c7f7add9-d7db-4649-881d-700528b6efc7" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
values(202,'Ella King','F','Chemistry',87),
(203,'James Bond'  ,'M'         ,'Literature'  ,78);
```

**Output:**

<img width="1125" height="170" alt="image" src="https://github.com/user-attachments/assets/66e93b70-d7c8-4a5b-8371-e151a4ba7978" />


**Question 5**
---
<img width="983" height="455" alt="image" src="https://github.com/user-attachments/assets/82786822-7446-4fea-9b3e-dc488753aa1c" />


```sqlcreate table Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME );
```

**Output:**

<img width="1042" height="315" alt="image" src="https://github.com/user-attachments/assets/ec439077-cb10-4752-a519-06ef147ca66f" />


**Question 6**
---
<img width="950" height="348" alt="image" src="https://github.com/user-attachments/assets/f7c39ced-1e16-47df-8cc0-5cf75bacb366" />


```sql
create table contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL check(length(phone)>=10));
```

**Output:**

<img width="803" height="256" alt="image" src="https://github.com/user-attachments/assets/0dcb7b8c-dcee-46f7-a0b0-bcf85faf6fc5" />


**Question 7**
---
<img width="817" height="440" alt="image" src="https://github.com/user-attachments/assets/ec1ff111-1129-42bc-9f84-017155b283eb" />


```sql
create table item(
item_id TEXT PRIMARY KEY,
item_desc TEXT,
rate INTEGER,
icom_id TEXT(4),
FOREIGN KEY(icom_id) REFERENCES company(com_id)
on update set NULL
on delete set NULL);
```

**Output:**

<img width="925" height="271" alt="image" src="https://github.com/user-attachments/assets/f76443d5-d750-4262-b432-44f95b06273a" />


**Question 8**
---
<img width="1208" height="295" alt="image" src="https://github.com/user-attachments/assets/2356d56e-8f93-4515-a8b1-3026f4b6a4d5" />


```sql
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**

<img width="1117" height="133" alt="image" src="https://github.com/user-attachments/assets/81fc0c9a-71a7-49e9-a808-ab8060e579f6" />

**Question 9**
---
<img width="1050" height="243" alt="image" src="https://github.com/user-attachments/assets/a4a11123-e5d6-4023-940c-5c9b05c92eda" />


```sql
alter table customer
add email VARCHAR(100);
```

**Output:**

<img width="871" height="297" alt="image" src="https://github.com/user-attachments/assets/f28d8993-9458-4353-906e-1828eb838d11" />


**Question 10**
---
<img width="978" height="347" alt="image" src="https://github.com/user-attachments/assets/4206d458-1106-473d-b9b4-3185f0e6b6b9" />

```sql
insert into Customers(CustomerID, Name, Address, Email)
select * from Old_customers;
```

**Output:**

<img width="900" height="232" alt="image" src="https://github.com/user-attachments/assets/29529ced-d0f5-41f3-8435-dbe608ea6a71" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
