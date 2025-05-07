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
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

```sql
select Medication,Avg(Dosage) as AvgDosage 
from Prescriptions
group by Medication;
```

**Output:**

![Screenshot 2025-05-07 192315](https://github.com/user-attachments/assets/b241b94d-8719-4461-9df7-87b16f7b52c3)


**Question 2**
---
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

```sql
select Specialty,Gender,Count(*) as TotalDoctors
from Doctors
group by Specialty,Gender;
```

**Output:**

![Screenshot 2025-05-07 192328](https://github.com/user-attachments/assets/e3c2a59c-2668-45d8-801c-b1c6e42cb107)


**Question 3**
---
How many medical records are there for each patient?

Sample table:MedicalRecords Table

```sql
select PatientID,count(*) as TotalRecords
from MedicalRecords
group by PatientID;
```

**Output:**

![Screenshot 2025-05-07 192342](https://github.com/user-attachments/assets/a03fdad1-bde1-4dfb-9f7a-70aa34fc9c20)


**Question 4**
---
Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
select count(*) as COUNT from customer;
```

**Output:**

![Screenshot 2025-05-07 192354](https://github.com/user-attachments/assets/f1a61176-b400-4d45-bd0e-be3933c861e7)


**Question 5**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select name as Employee_Name,
age as Age
from employee
order by age 
limit 1;
```

**Output:**

![Screenshot 2025-05-07 192406](https://github.com/user-attachments/assets/66116f8c-8392-489a-8f66-9a3e49a5ff4b)


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
select sum(inventory) as total
from fruits where unit='LB';
```

**Output:**

![Screenshot 2025-05-07 192419](https://github.com/user-attachments/assets/3f5180ac-e27d-4757-9d72-7419fd83996a)


**Question 7**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee


```sql
select count(*) as COUNT
from employee where age>32;
```

**Output:**


![Screenshot 2025-05-07 192431](https://github.com/user-attachments/assets/d6e03af5-1758-4df9-a27b-541868cb2dd0)

**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

```sql
select occupation ,AVG(workhour)
from employee1
group by occupation
having avg(workhour) between 10 and 12;
```

**Output:**

![Screenshot 2025-05-07 192443](https://github.com/user-attachments/assets/4b290117-a997-42eb-947f-60fbe4edb662)


**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1

```sql
select (age/5)*5 as age_group,
AVG(age) 
from customer1
group by age_group
having AVG(age)<24;
```

**Output:**

![Screenshot 2025-05-07 192454](https://github.com/user-attachments/assets/7389d64e-7cd1-4267-b82a-7991414c8dff)


**Question 10**
---
Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

```sql
select (age/5)*5 as age_group,
MIN(salary)
from customer1
group by age_group 
having min(salary)<2000
;
```

**Output:**


![Screenshot 2025-05-07 192517](https://github.com/user-attachments/assets/76375a3b-571c-4da4-99fc-7906245f04a9)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
