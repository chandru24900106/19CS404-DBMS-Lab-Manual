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
<img width="1102" height="647" alt="image" src="https://github.com/user-attachments/assets/36cd0661-14d5-49d8-8fb4-43e3a278a34d" />


```sql
update employees
set email='Unavailable'
```

**Output:**

<img width="1207" height="522" alt="image" src="https://github.com/user-attachments/assets/972f03ad-7511-4355-8935-b12664d624ec" />


**Question 2**
---
<img width="997" height="320" alt="image" src="https://github.com/user-attachments/assets/6f4811ed-eca0-4d64-8fe2-ca988e7e2160" />


```sql
update products 
set product_name='Premium Bread'
where product_id=5;
```

**Output:**

<img width="1171" height="401" alt="image" src="https://github.com/user-attachments/assets/def0dfca-2d62-4911-a16c-fe5e87d970d5" />


**Question 3**
---
<img width="1143" height="602" alt="image" src="https://github.com/user-attachments/assets/527c121d-a9f4-4e8e-8a91-76436ad7e719" />


```sql
update PRODUCTS 
set reorder_lvl=reorder_lvl*0.7 
where product_name like '%cream%' and quantity>reorder_lvl;
```

**Output:**

<img width="1176" height="406" alt="image" src="https://github.com/user-attachments/assets/5832f77e-b1b7-46e4-8f31-5f628438de83" />


**Question 4**
---
<img width="1182" height="518" alt="image" src="https://github.com/user-attachments/assets/6131ec3f-2008-4492-8fb3-093b2ed0a7d3" />


```sql
update Products
set reorder_lvl=20
where quantity<10 and category='Snacks'
```

**Output:**

<img width="1171" height="482" alt="image" src="https://github.com/user-attachments/assets/e6fd6469-e4db-4cbb-96d5-6e1470addac9" />


**Question 5**
---
<img width="1217" height="526" alt="image" src="https://github.com/user-attachments/assets/88fac0be-d2a5-4062-acc6-317a88a22fa3" />


```sql
update products
set reorder_lvl=reorder_lvl*1.30
where category='Food' and quantity < (reorder_lvl*0.5);
```

**Output:**

<img width="1192" height="322" alt="image" src="https://github.com/user-attachments/assets/ad57e105-7a9d-4333-9d6c-9de5d0b7eb49" />


**Question 6**
---
<img width="1208" height="502" alt="image" src="https://github.com/user-attachments/assets/bf270035-ff1e-4c84-9aa0-3e4310db2a2d" />


```sql
delete from Customer where (GRADE > 2 and PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer)) or OUTSTANDING_AMT>8000
```

**Output:**

<img width="1197" height="507" alt="image" src="https://github.com/user-attachments/assets/23ca9941-93c8-4951-9a1c-6db627f6b706" />


**Question 7**
---
<img width="937" height="462" alt="image" src="https://github.com/user-attachments/assets/851043a6-d695-42a9-99cc-eef541cf6cc5" />


```sql
delete from customer
where cust_country='India' and cust_city<>'Chennai'
```

**Output:**

<img width="1145" height="840" alt="image" src="https://github.com/user-attachments/assets/5d234f20-6e81-40dc-8b39-35146eb58ba1" />


**Question 8**
---
<img width="1216" height="493" alt="image" src="https://github.com/user-attachments/assets/1d8ad74c-423e-4967-84e5-708fc52b97ff" />


```sql
delete from Customer 
where  CUST_CITY<>'New York' and OUTSTANDING_AMT>5000
```

**Output:**

<img width="1148" height="507" alt="image" src="https://github.com/user-attachments/assets/cfd89b39-8e86-4e34-8df6-80ac84fe5fab" />


**Question 9**
---
<img width="1177" height="331" alt="image" src="https://github.com/user-attachments/assets/d438e8f4-8a62-4610-a21a-b18a9646e708" />


```sql
delete from Customer
where CUST_CITY like 'l%'
```

**Output:**

<img width="1192" height="777" alt="image" src="https://github.com/user-attachments/assets/eb53ce8c-1d2d-4e9a-aad8-17559d65fca3" />


**Question 10**
---
<img width="1242" height="517" alt="image" src="https://github.com/user-attachments/assets/dcc69f7e-7956-4bcc-80b9-3a388162efea" />


```sql
delete from Doctors
where (specialization='Pediatrics' or specialization='Cardiology') and last_name='Brown';
```

**Output:**

<img width="997" height="897" alt="image" src="https://github.com/user-attachments/assets/0f9753ab-8ed1-485a-b087-f4887b97ca43" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
