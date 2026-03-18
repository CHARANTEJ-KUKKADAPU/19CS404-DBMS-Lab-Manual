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
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

## PROGRAM:

```PY
ProductID Name Category Price Stock

106 Fitness Tracker Wearables 107 Laptop Electronics 999.99 50 108 Wireless Earbuds Accessories 100

insert into Products(ProductID,Name,Category,Price,Stock)
values(106,"Fitness Tracker","Wearables",NULL,NULL);
insert into Products(ProductID,Name,Category,Price,Stock) 
values(107,"Laptop","Electronic",999.99,50);
insert into Products(ProductID,Name,Category,Price,Stock) 
values(108,"Wireless Earbud","Accessorie",NULL,100); 
```


## **Output:**

<img width="1174" height="266" alt="image" src="https://github.com/user-attachments/assets/375fc8cd-9713-4095-9438-74ee8ac22dd9" />


**Question 2**
---
Write a SQL Query to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

## PROGRAM:
```PY
alter table books add  ISBN varchar(30);
alter table books add domain_dept  varchar(30);
```

## **Output:**

<img width="1178" height="378" alt="image" src="https://github.com/user-attachments/assets/7e5af9da-c55f-4735-97c6-c83b2d947083" />


**Question 3**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.


## PROGRAM:
```PY
insert into Customers(CustomerID,Name,Address,City,ZipCode)
values(301,"Michael Jordan","123 Maple St","Chicago",60616);
```
## **Output:**

<img width="1184" height="229" alt="image" src="https://github.com/user-attachments/assets/593a7c7c-2596-44b9-9ccb-bd58115e7b83" />


**Question 4**
---
Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
## PROGRAM:

```PY
create table contacts(
contact_id  INTEGER  primary key,
first_name  TEXT not NULL,
last_name  TEXT  not NULL,
email  TEXT,
phone  TEXT  not NULL  check(LENGTH(phone)>=10) 
);
```
## **Output:**

<img width="1192" height="323" alt="image" src="https://github.com/user-attachments/assets/b1a3c63c-136d-490a-9923-f85494c0e5dc" />


**Question 5**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. DueDate as DATE should be greater than the InvoiceDate. Amount as REAL should be greater than 0.
## PROGRAM:
```PY
create table Invoices(
InvoiceID INTEGER  primary key,
InvoiceDate  DATE,
DueDate  DATE check(DueDate>InvoiceDate),
Amount  REAL check(Amount > 0) 
);
```

## **Output:**

<img width="1176" height="265" alt="image" src="https://github.com/user-attachments/assets/b97a6c1e-c785-47fe-b901-8cffe20c3fd8" />


**Question 6**
Create a new table named item with the following specifications and constraints: item_id as TEXT and as primary key. item_desc as TEXT. rate as INTEGER. icom_id as TEXT with a length of 4. icom_id is a foreign key referencing com_id in the company table. The foreign key should set NULL on updates and deletes. item_desc and rate should not accept NULL.

## PROGRAM:
```PY
create table item(
item_id  TEXT  primary key,
item_desc  TEXT not null,
rate  INTEGER not null,
icom_id TEXT(4),
foreign key(icom_id) references company(com_id) on update set null on delete set null
);
```
## **Output:**

<img width="1179" height="343" alt="image" src="https://github.com/user-attachments/assets/af01e3e8-cf25-4c6e-a645-5d33a4fdf486" />


**Question 7**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

## PROGRAM:

```PY

insert into Products(ProductID, ProductName, Price, Stock)
select * from Discontinued_products;

```

## **Output:**

<img width="1186" height="286" alt="image" src="https://github.com/user-attachments/assets/6f961221-00e7-45ee-b49c-747a062adccb" />

**Question 8**
---
Create a table named Events with the following columns:

EventID as INTEGER EventName as TEXT EventDate as DATE
## PROGRAM:
```PY
create table Events(
EventID  INTEGER,
EventName  TEXT,
EventDate  DATE 
);
```

## **Output:**

<img width="1189" height="376" alt="image" src="https://github.com/user-attachments/assets/53e55ad0-db5b-458a-995d-59d110facdc8" />

**Question 9**
---
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.


## PROGRAM:
```PY
alter table Student_details  add Email VARCHAR(50);
alter table Student_details  add MARKS default 0;
```

## **Output:**

<img width="1187" height="233" alt="image" src="https://github.com/user-attachments/assets/23cc9d71-fe32-47e9-944b-6af5749d7689" />


**Question 10**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key. FirstName and LastName should be NOT NULL. Email should be unique. Salary should be greater than 0. DepartmentID should be a foreign key referencing the Departments table.

## PROGRAM:

```PY
create table Employees(
EmployeeID  primary key,
FirstName varchar(225)NOT NULL,
LastName varchar(225) NOT NULL,
Email  UNIQUE,
Salary check(salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references  Departments(DepartmentID)
```
## **Output:**

<img width="1177" height="421" alt="image" src="https://github.com/user-attachments/assets/35b69fa7-3489-4ab5-81e1-baa0e99a305e" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
