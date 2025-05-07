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
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT 

```sql
update Products set category='Household' where product_name like '%Detergent%';
```

**Output:**

![Screenshot 2025-05-07 082518](https://github.com/user-attachments/assets/6394e0bb-750a-4664-9a75-c48c56810215)


**Question 2**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
update PRODUCTS set reorder_lvl=reorder_lvl*0.7 where product_name like '%cream%' and quantity>reorder_lvl;
```

**Output:**

![Screenshot 2025-05-07 082535](https://github.com/user-attachments/assets/89e8da6e-c8ed-453b-b008-7bd0a4ccbddb)


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
update Employees set first_name='John' where department_id=80 and commission_pct<0.35;
```

**Output:**

![Screenshot 2025-05-07 082555](https://github.com/user-attachments/assets/cce25973-9a02-4de7-bbb1-2b69962ac55c)


**Question 4**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
update PRODUCTS set reorder_lvl=40 where category='Grocery';
```

**Output:**

![Screenshot 2025-05-07 082609](https://github.com/user-attachments/assets/14c41524-1865-4707-b28c-d7a201fea84e)


**Question 5**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
update Employees set salary=8000 where Employee_ID=105 and salary<5000;
```

**Output:**

![Screenshot 2025-05-07 082621](https://github.com/user-attachments/assets/91c70a21-ba96-459f-a01a-a1879306db5d)


**Question 6**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from Doctors where last_name is NULL;
```

**Output:**

![Screenshot 2025-05-07 082644](https://github.com/user-attachments/assets/c8dc962d-05ef-4c63-93a3-84defe5cf81b)


**Question 7**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors where specialization in ('Pediatrics','Cardiology') and last_name='Brown';
```

**Output:**

![Screenshot 2025-05-07 082704](https://github.com/user-attachments/assets/eb1e1801-6c77-4650-9899-3d456f621768)


**Question 8**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

```sql
delete from Customer where (GRADE>2 and PAYMENT_AMT<(select avg(PAYMENT_AMT) from Customer)) or OUTSTANDING_AMT>8000
```

**Output:**

![Screenshot 2025-05-07 082722](https://github.com/user-attachments/assets/da799b04-6986-4ba3-b937-ceed5bbf06d3)


**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

```sql
delete from surgeries where surgery_id=3;
```

**Output:**


![Screenshot 2025-05-07 082738](https://github.com/user-attachments/assets/50090238-1a54-4c93-b439-259edda40006)

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

```sql
delete from Customer where CUST_CITY!='New York' and OUTSTANDING_AMT>5000;
```

**Output:**

![Screenshot 2025-05-07 082756](https://github.com/user-attachments/assets/d23cf37b-f2b4-42b4-9e5a-e4d51e2f43e8)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
