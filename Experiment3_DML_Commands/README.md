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
---
Write a SQL statement to double the availability of the product with product_id 1.
products table
<br>
product_id product_name category_id availability
```sql
update products 
set availability = availability*2
where product_id= 1;

```

**Output:**


![image](https://github.com/user-attachments/assets/a652ac8e-9052-4a8a-a1a5-72f5abfcdee1)

**Question 2**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.
<br>
Employees table
<br>
employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
```sql

update Employees
set EMAIL='not available' , COMMISSION_PCT=0.55
where DEPARTMENT_ID = 110;

```

**Output:**


![image](https://github.com/user-attachments/assets/1d87d02f-ba86-4e12-a68a-53eba10fc0f8)


**Question 3**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'
<br>
Employees table
<br>
employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id

```sql

update Employees
set SALARY=SALARY*2
where department_id=20 and job_id LIKE '%MAN';


```

**Output:**


![image](https://github.com/user-attachments/assets/c48121d4-0d20-4eab-a49b-54ffc46f7e59)


**Question 4**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.
<br>
PRODUCTS TABLE
<br>
name type
<br>
product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

```sql

update PRODUCTS 
set reorder_lvl=reorder_lvl*0.7
where product_name LIKE '%cream%' and quantity>reorder_lvl ;

```

**Output:**


![image](https://github.com/user-attachments/assets/a951229b-f74b-40ba-a42b-db61f5e4e7de)


**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.
<br>
Sample table: Customer
<br>
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |

```sql

delete from Customer
where grade!=3;

```

**Output:**


![image](https://github.com/user-attachments/assets/f6625421-28e3-48c7-a558-f2ea09945516)

**Question 6**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:
<br>
Sample table: Customer
<br>
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00
```sql

delete from Customer 
where 
(grade >2 and payment_amt<(select avg(payment_amt) from Customer) or outstanding_amt>8000);


```

**Output:**


![image](https://github.com/user-attachments/assets/929fecb4-8b0e-4321-990e-2c018d3c52b2)


**Question 7**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.
<br>
Sample table: Doctors
<br>
attributes : doctor_id, first_name, last_name, specialization

```sql

delete from doctors where doctor_id =1;

```

**Output:**


![image](https://github.com/user-attachments/assets/3a94ddb5-78c7-4b36-87f0-76fc4e5944b0)


**Question 8**
---
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.
<br>
Sample table: customer
<br>
customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002

```sql

select customer_id,cust_name,city,grade,salesman_id  from customer where city='London' and grade>200;

```

**Output:**


![image](https://github.com/user-attachments/assets/baed54a9-38d8-41ef-81ef-5a03ffb7c09d)


**Question 9**
---
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.
<br>
Sample table: customer
<br>
customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002
```sql

select customer_id,cust_name,city,grade,salesman_id from customer 
where city='New York' or grade<=100;

```

**Output:**


![image](https://github.com/user-attachments/assets/29898c4b-85a8-4b8a-b8fd-82b12477a7a9)


**Question 10**
---
Write a SQL query to Select all patients whose name starts with A.
<br>
Table: Patients
<br>
name type
<br>
patient_id INT first_name VARCHAR(50) last_name VARCHAR(50) date_of_birth DATE admission_date DATE discharge_date DATE doctor_id INT

```sql

select * 
from Patients 
where first_name like 'A%';

```

**Output:**


![image](https://github.com/user-attachments/assets/0b5127d0-1ad8-4647-a76f-2c9038a0866f)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
