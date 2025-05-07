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
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
create table Products(
ProductID int,
ProductName TEXT not null,
Price real check(Price>0),
Stock int check(Stock>=0),
Primary key(ProductID));
```

**Output:**

![Screenshot 2025-05-06 195533](https://github.com/user-attachments/assets/2aab77d9-bbe6-4a7d-9089-9c7a1decf597)


**Question 2**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Invoices(
InvoiceID INTEGER,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
Primary key(InvoiceID),
Foreign key(OrderID) references Orders(OrderID));
```

**Output:**


![Screenshot 2025-05-06 195624](https://github.com/user-attachments/assets/33afc04d-2007-476b-badb-a136f82925dc)

**Question 3**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

```sql
alter table employee add designation varchar(50);
```

**Output:**


![Screenshot 2025-05-06 195700](https://github.com/user-attachments/assets/c6793a6c-a937-4849-9bcd-3fce72ee9e53)

**Question 4**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
create table Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE);
```

**Output:**

![Screenshot 2025-05-06 200029](https://github.com/user-attachments/assets/bd478a62-52d0-480c-85b4-424c9426e2e1)


**Question 5**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT

```sql
insert into Employee(EmployeeID,Name,Position) values(5,'George Clark','Consultant');
insert into Employee(EmployeeID,Name,Position,Department,Salary) values(7,'Noah Davis','Manager','HR',60000);
insert into Employee(EmployeeID,Name,Position,Department) values(8,'Ava Miller','Consultant','IT');
```

**Output:**

![Screenshot 2025-05-06 200103](https://github.com/user-attachments/assets/98591aa1-978d-43cb-928f-2305fd3c703a)


**Question 6**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.

```sql
insert into Products(ProductID,Name,Category,Price,Stock) values(101,'Laptop','Electronics',1500,50);
```

**Output:**

![Screenshot 2025-05-06 200140](https://github.com/user-attachments/assets/148a4696-5c73-43d8-9f5f-e3203bc2203e)


**Question 7**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
insert into Products(ProductID,ProductName,Price,Stock) select ProductID,ProductName,Price,Stock from Discontinued_products;
```

**Output:**

![Screenshot 2025-05-06 200223](https://github.com/user-attachments/assets/36398184-8803-4146-9011-6e88e41c5348)


**Question 8**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
create table item(
item_id TEXT,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
primary key(item_id),
foreign key(icom_id) references company(com_id)
on update cascade
on delete cascade);
```

**Output:**

![Screenshot 2025-05-06 200254](https://github.com/user-attachments/assets/9a7c766f-786c-447d-ba27-e6221166da70)


**Question 9**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
alter table customer add email VARCHAR(100);
```

**Output:**

![Screenshot 2025-05-06 200335](https://github.com/user-attachments/assets/e45cbd59-e536-4f36-986a-9d7bb7439ad5)


**Question 10**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
create table contacts(
contact_id INTEGER,
first_name TEXT not null,
last_name TEXT not null,
email TEXT,
phone TEXT not null check(length(phone)>=10),
primary key(contact_id));
```

**Output:**



![Screenshot 2025-05-07 081807](https://github.com/user-attachments/assets/d0479dd2-f9e9-4203-bc6a-ede2e1686ef8)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
