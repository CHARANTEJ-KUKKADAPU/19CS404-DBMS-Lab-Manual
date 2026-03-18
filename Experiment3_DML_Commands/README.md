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
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id


## PROGRAM:
```sql
UPDATE products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**
<img width="1174" height="510" alt="image" src="https://github.com/user-attachments/assets/444367e0-de04-4564-8fda-3fa4fd3cd8fa" />

**Question 2**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

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

## PROGRAM:

```sql
UPDATE employees
SET email = 'not available',
    commission_pct = 0.55
WHERE department_id = 110;
```

**Output:**
<img width="1186" height="373" alt="image" src="https://github.com/user-attachments/assets/92bb5010-b407-41d4-bfbe-bcb123ab2a94" />


**Question 3**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

## PROGRAM:

```sql
UPDATE products
SET product_name = 'Premium Bread'
WHERE product_id = 5;
```

**Output:**
<img width="1182" height="392" alt="image" src="https://github.com/user-attachments/assets/c6e08c6f-dc01-40d3-8b0e-f2bb29d8e54f" />


**Question 4**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

## PROGRAM:

```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**
<img width="1182" height="393" alt="image" src="https://github.com/user-attachments/assets/74825dac-fb95-40cb-a75e-94a11f330779" />

**Question 5**
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

## PROGRAM:

```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
  AND category = 'Snacks';
```

**Output:**
<img width="1182" height="564" alt="image" src="https://github.com/user-attachments/assets/6568339b-1cda-46fa-84bd-501fccf889a7" />


**Question 6**
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

## PROGRAM:

```sql
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';
```

**Output:**
<img width="1179" height="826" alt="image" src="https://github.com/user-attachments/assets/8b047bc7-a37b-4e97-9153-e3f6b3205a28" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

## PROGRAM:
 
```sql
DELETE FROM customer
WHERE grade = 2;
```

**Output:**

<img width="926" height="564" alt="image" src="https://github.com/user-attachments/assets/cd811bd6-ff87-4b5f-a29f-b43c5e691f4e" />


**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Last Name
## PROGRAM:

```sql
DELETE FROM doctors
WHERE last_name IS NULL;
```

**Output:**
<img width="1193" height="719" alt="image" src="https://github.com/user-attachments/assets/8a76c241-e5af-4ff4-b6f9-dcff2248ba5d" />

**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

## PROGRAM:

```sql
DELETE FROM customer
WHERE grade = 2
  AND cust_name LIKE 'M%'
  AND payment_amt < 3000;
```

**Output:**
<img width="1184" height="391" alt="image" src="https://github.com/user-attachments/assets/5539d8e8-d6e1-4bda-a55c-951e36ced142" />

**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
## PROGRAM:

```sql
DELETE FROM customer
WHERE cust_city <> 'New York'
  AND outstanding_amt > 5000;
```

**Output:**
<img width="1189" height="589" alt="image" src="https://github.com/user-attachments/assets/605e00e6-4f2c-4606-bd82-54126ab9640e" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
