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
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date later than '2012-08-17'.

```sql
select 
      c.customer_id,
      c.cust_name,
      c.city,
      c.grade,
      c.salesman_id
from
      customer c
LEFT JOIN  orders o ON  o.customer_id = c.customer_id
where ord_date>'2012-08-17'
```

**Output:**

![444585446-a6772119-4823-4ff1-95d8-3964f6e2e606](https://github.com/user-attachments/assets/72a469cc-5af3-4715-8c15-4c3ecbb28f71)


**Question 2**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c") and the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the same city as the salesman.

```sql
select
    c.cust_name,
    s.name
from
    Customer c
LEFT JOIN salesman s ON s.salesman_id =c.salesman_id
where s.city=c.city
```

**Output:**
![444581548-1c20d121-59c2-40b5-ac98-e46e085be783](https://github.com/user-attachments/assets/3f0f874a-0ccb-4f98-bfb1-de72168b75cf)



**Question 3**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

```sql
select
      p.first_name,
      s.surgery_id,
      s.patient_id,
      s.surgeon_id,
      s.surgery_date
from
      patients p
INNER JOIN surgeries s ON s.patient_id =p.patient_id  
where p.first_name='Alice'
```

**Output:**
![444585605-ec0162e6-3a44-4079-ad0a-1d4ac76f0b8e](https://github.com/user-attachments/assets/10537c9e-c726-4b3a-8189-b5710865768d)



**Question 4**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
```


```sql
select 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
from
    customer c
JOIN orders o ON o.customer_id = c.customer_id
where o.purch_amt between 500 and 2000
```

**Output:**
![444585774-25bd3d22-7291-4d08-801b-cf4235af4d77](https://github.com/user-attachments/assets/9f673de9-9036-4709-9d24-c2bbc1ecd2ad)



**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column.
<br>
PATIENTS TABLE:
<br>
ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
<br>
APPOINTMENTS TABLE:
<br>
ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date
<br>
```sql

select 
    p.first_name as'patient_name',
    a.appointment_id,
    p.patient_id,
    a.doctor_id,
    a.appointment_date
from
    patients p
INNER JOIN appointments a ON a.patient_id = p.patient_id


```

**Output:**
![444585977-e847f246-ac73-4377-9d54-46c1f2d2999e](https://github.com/user-attachments/assets/56a54050-c1d0-466c-9211-a50cbee5d662)



**Question 6**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.
```
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
        
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
select 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name as 'Customer Name',
    c.grade,
    s.name as 'Salesman',
    s.commission
from
    orders o
JOIN customer c ON c.customer_id = o.customer_id
JOIN salesman s ON s.salesman_id=c.salesman_id;
```

**Output:**
![444586412-81b13e7f-3ede-40dd-bcac-ae1c2df1b167](https://github.com/user-attachments/assets/643731fe-c790-4b53-afcd-ca6dc1d5296b)


**Question 7**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.

```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql

select c.cust_name as 'Customer Name',
       c.city ,
       s.name as 'Salesman',
       s.city,
       s.commission
from customer c
JOIN salesman s ON s.salesman_id = c.salesman_id 
where 
      s.city <> c.city
and  commission>0.12
       
```

**Output:**
![444586712-ca6ff73e-6a35-42e6-9ab5-7457b3985497](https://github.com/user-attachments/assets/98002fbd-dcd1-40c6-aeb5-202882bd023b)


**Question 8**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12

```
```sql
select
c.cust_name,
c.city,
o.ord_no,
o.ord_date,
o.purch_amt as 'Order Amount',
s.name,
s.commission
from customer c
left join orders o ON o.customer_id = c.customer_id
left join salesman s ON s.salesman_id = o.salesman_id

```

**Output:**
![444587089-19c6ce66-3171-4564-ac00-37910000c621](https://github.com/user-attachments/assets/bef42a58-d0dc-45e1-8259-8e12edbe9278)



**Question 9**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.
```
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
select
    c.cust_name,
    c.city,
    c.grade,
    s.name as 'Salesman',
    s.city
from customer c
join salesman s on s.salesman_id = c.salesman_id
order by c.customer_id asc;
    
```

**Output:**
![444587473-7231674f-5b75-4592-8ae3-48d1e5149d9a](https://github.com/user-attachments/assets/98346b6c-9fd6-4e93-99ed-d948333c6d62)



**Question 10**
---
Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.
```
PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE
```
```sql
select p.admission_date,
       s.surgery_date
from patients p 
INNER JOIN surgeries s ON s.patient_id =p.patient_id;
```

**Output:**


![444583772-77f68e58-c1e3-4ca6-9d6b-9cc6f6f82222](https://github.com/user-attachments/assets/7b22af1a-6e16-40ee-97dc-959232a6bdda)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
