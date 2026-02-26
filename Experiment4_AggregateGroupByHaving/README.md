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
<img width="717" height="647" alt="image" src="https://github.com/user-attachments/assets/a4d2c66d-79f8-468b-9a07-a3804703457b" />


```sql
select DATE(AppointmentDateTime) as AppointmentDate , count(*) as TotalAppointments from Appointments
group by DATE(AppointmentDateTime);
```

**Output:**

<img width="872" height="615" alt="image" src="https://github.com/user-attachments/assets/0a73591b-8a4b-403d-8316-b17ce765ab45" />


**Question 2**
---
<img width="981" height="248" alt="image" src="https://github.com/user-attachments/assets/583b419b-3b28-4f7c-a15e-4231f6758c85" />


```sql
select Medication,count(*) as  TotalPrescriptions from Prescriptions
group by Medication;
```

**Output:**

<img width="825" height="703" alt="image" src="https://github.com/user-attachments/assets/90efed51-9621-4ffe-808d-4b8fcf6bc15c" />


**Question 3**
---
<img width="1031" height="247" alt="image" src="https://github.com/user-attachments/assets/fd32bb4c-91fa-4e2e-90ac-fd77095c8dec" />


```sql
select InsuranceCompany,count(*) as TotalExpiredPatients from Insurance
group by InsuranceCompany;
```

**Output:**

<img width="867" height="716" alt="image" src="https://github.com/user-attachments/assets/69354cce-635a-478e-af40-31e6adbb42fd" />


**Question 4**
---
<img width="816" height="541" alt="image" src="https://github.com/user-attachments/assets/27f55f09-525f-4e27-813e-6d9c29028190" />

```sql
select sum(inventory) as total from fruits
where unit='LB'; 
```

**Output:**

<img width="540" height="292" alt="image" src="https://github.com/user-attachments/assets/8627cbe1-e723-4182-a0aa-331bc3c2682f" />


**Question 5**
---
<img width="847" height="475" alt="image" src="https://github.com/user-attachments/assets/ff9b5e58-64df-425e-9f65-659f30487a4a" />


```sql
select avg(income) as avg_income from employee
where name like 'A%';
```

**Output:**

<img width="583" height="303" alt="image" src="https://github.com/user-attachments/assets/ae096386-3908-45bf-ba6b-2bc6cc79aabc" />


**Question 6**
---
<img width="958" height="517" alt="image" src="https://github.com/user-attachments/assets/577bdc43-c7be-464d-83ef-c2b8a636edc6" />


```sql
select max(price)-min(price) as price_diff from fruits;
```

**Output:**

<img width="482" height="290" alt="image" src="https://github.com/user-attachments/assets/a5b201ed-e758-4fa2-bfd6-76831eeed205" />


**Question 7**
---
<img width="980" height="490" alt="image" src="https://github.com/user-attachments/assets/9ec5f602-7a3f-44a9-a2af-58cc751651fd" />


```sql
select count(*) as COUNT from customer
where grade>=1;
```

**Output:**

<img width="723" height="307" alt="image" src="https://github.com/user-attachments/assets/9bc0c111-5fe2-49ac-8f84-3fe2dbf47f06" />


**Question 8**
---
<img width="957" height="567" alt="image" src="https://github.com/user-attachments/assets/83a34561-465b-41b5-90ed-ff4ab3f3a455" />


```sql
select address,AVG(salary) as "AVG(salary)" from customer1
group by address
having AVG(salary)<15000

```

**Output:**

<img width="781" height="552" alt="image" src="https://github.com/user-attachments/assets/34370abc-db89-4c91-bf9c-7151b33e73ed" />


**Question 9**
---
<img width="1202" height="302" alt="image" src="https://github.com/user-attachments/assets/d4323792-06f5-4a52-adba-c0960237941d" />


```sql
select category_id, product_name,max(price) as Price from products
group by category_id
having max(price)>15
```

**Output:**

<img width="867" height="332" alt="image" src="https://github.com/user-attachments/assets/32cff180-8db0-4a7b-b717-13150cc00472" />

**Question 10**
---
<img width="1197" height="263" alt="image" src="https://github.com/user-attachments/assets/641712b8-b71b-4e02-b695-319c2c9695c0" />


```sql
select (age/5)*5 as age_group , min(age) as "MIN(age)" from customer1
group by age/5
having min(age)<25;
```

**Output:**

<img width="686" height="251" alt="image" src="https://github.com/user-attachments/assets/b706111c-a54f-4368-8859-23dca67ae285" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
