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
<br>
Sample table:Insurance Table
<br>
name type
<br>
InsuranceID INTEGER PatientID INTEGER InsuranceCompany TEXT PolicyNumber TEXT PolicyHolder TEXT ValidityPeriod TEXT
```sql

SELECT InsuranceCompany, COUNT(DISTINCT PatientID) AS TotalPatients from Insurance group by InsuranceCompany order by InsuranceCompany

```

**Output:**

![image](https://github.com/user-attachments/assets/f70730fb-cfff-4807-8f24-38c85ad50b58)


**Question 2**
---
What is the average duration of insurance coverage for patients covered by each insurance company?
<br>
Sample table:Insurance Table
<br>
name type
<br>
InsuranceID INTEGER PatientID INTEGER InsuranceCompany TEXT PolicyNumber TEXT PolicyHolder TEXT StartDate DATE EndDate DATE

```sql

select InsuranceCompany, AVG(EndDate-StartDate)as AvgCoverageDurationDays from Insurance
group by InsuranceCompany ;

```

**Output:**

![image](https://github.com/user-attachments/assets/9169664d-6f55-4171-8d0b-aec4957c4a22)


**Question 3**
---
How many medical records does each doctor have?
<br>
Sample table:MedicalRecords Table For example: Result DoctorID TotalRecords
<br>
3 4 5 1 6 1 7 1 8 3

```sql

select DoctorID, count(*) as TotalRecords from MedicalRecords group by DoctorID order by DoctorID;

```

**Output:**

![image](https://github.com/user-attachments/assets/340501d9-27ec-4dce-ba92-e8d70cf9a051)


**Question 4**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
<br>
Sample table: orders
<br>
ord_no purch_amt ord_date customer_id salesman_id
<br>
70001 150.5 2012-10-05 3005 5002
<br>
70009 270.65 2012-09-10 3001 5005
<br>
70002 65.26 2012-10-05 3002 5001
```sql

select sum(purch_amt) as TOTAL from orders;

```

**Output:**

![image](https://github.com/user-attachments/assets/0b5440c8-e766-48d4-bad8-67c4bbe63cce)


**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.
<br>
Table: employee
<br>
name type
<br>
id INTEGER name TEXT age INTEGER city TEXT income INTEGER

```sql

select sum(income)as total_income from employee where age >=40;

```

**Output:**

![image](https://github.com/user-attachments/assets/f69e21b3-4232-4948-940c-e1610121b9f3)


**Question 6**
---
Write a SQL query to count the number of customers. Return number of customers.
<br>
Sample table: customer
<br>
customer_id | cust_name | city | grade | salesman_id
<br>
-------------+----------------+------------+-------+-------------
<br>
    3002 | Nick Rimando   | New York   |   100 |        5001
<br>
    3007 | Brad Davis     | New York   |   200 |        5001
<br>
    3005 | Graham Zusi    | California |   200 |        5002
<br>

```sql

select count(*) as COUNT from customer;

```

**Output:**
![image](https://github.com/user-attachments/assets/05c6cbb2-9aeb-49b5-856e-b565ebca0536)


**Question 7**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.
<br>
Table: employee
<br>
name type
<br>
id INTEGER name TEXT age INTEGER city TEXT income INTEGER
<br>
```sql
SELECT MAX(age)-MIN(AGE) as age_difference from employee;

```

**Output:**

![image](https://github.com/user-attachments/assets/877e1c82-fffb-4663-aaff-b28088b1d7d6)


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.
<br>
Sample table: employee For example:
<br>
Result age AVG(income)
<br>
45 450000.0
<br>
```sql
SELECT age, AVG(income) FROM employee group by age having AVG(income) between 300000 and 500000;
```

**Output:**

![image](https://github.com/user-attachments/assets/4ce5b914-1692-45b6-ade4-61abd65ab8ce)


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.
<br>
Sample table: employee1 For example:
<br>
Result occupation AVG(workhour)
<br>
Business 10.0 Engineer 12.0
```sql

select occupation,AVG(workhour) from employee1 group by occupation having AVG(workhour) between 10 and 12;


```

**Output:**

![image](https://github.com/user-attachments/assets/3a829f12-4956-4038-9205-22b9cbbf3861)

**Question 10**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.
<br>
Sample table: customer1 For example:
<br>
Result address AVG(salary)
<br>
Bhopal 8500.0 Indore 10000.0 Mumbai 6500.0
```sql

select address,AVG(salary) from customer1 group by address having AVG(salary)>5000

```

**Output:**

![image](https://github.com/user-attachments/assets/aa47ffa2-6dc4-437f-8e42-c56d22517cae)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
