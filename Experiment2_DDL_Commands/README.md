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


Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql

create table Invoices(
InvoiceID INTEGER  primary key,
InvoiceDate  DATE,
Amount  REAl check (amount >=0),
DueDate  DATE check (DueDate > InvoiceDate),
OrderID  INTEGER,
foreign key (OrderId) references Orders(OrderID));

```

**Output:**

![image](https://github.com/user-attachments/assets/cb2f3677-e44f-4300-ad4a-ea9f0e6e1cbd)



**Question 2**

Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql

INSERT into student_details (RollNo,Name,Gender,subject,MARKS)
values('201','David Lee','M','Physics','92');

```

**Output:**

![image](https://github.com/user-attachments/assets/f1bf7a00-a342-4755-91ec-edd95e16e55e)



**Question 3**

Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.


```sql

create table Department(
DepartmentID INTEGER primary key,
DepartmentName TEXT unique not NULL,
Location TEXT
);

```

**Output:**


![image](https://github.com/user-attachments/assets/23b08643-e9da-4924-ae2a-194b44d98e69)




**Question 4**

Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql

create table Products(
ProductID integer primary key,
ProductName varchar(20) NOT NULL,
Price  real check (Price >0),
Stock integer check(Stock >=0)
);

```

**Output:**

![image](https://github.com/user-attachments/assets/0b73fef0-013e-48fb-96e4-a2015a44feae)



**Question 5**

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

        
```sql

ALTER TABLE customer
ADD COLUMN birth_date timestamp;

```

**Output:**

![image](https://github.com/user-attachments/assets/aa195b2a-185f-489b-975e-230ae4da6345)


**Question 6**

Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql

create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);

```

**Output:**

![image](https://github.com/user-attachments/assets/3900ebe5-8f6a-421d-8edc-b49e6ffb36c4)


**Question 7**

Write an SQL command can to add a column named email of type TEXT to the customers table

```sql

ALTER  table Customers
add column email TEXT; 

```

**Output:**

![image](https://github.com/user-attachments/assets/d4d74c66-8c0b-4a48-8cfc-c49b1ce32c1b)


**Question 8**

Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000


```sql

insert into Employee(EmployeeID,Name,Position,Department,Salary)
values('2','John Smith','Developer','IT','75000');
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values('3','Anna Bell','Designer','Marketing','68000')

```

**Output:**

![image](https://github.com/user-attachments/assets/771f87c7-7929-41fc-af9d-623115816454)


**Question 9**


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
item_id TEXT primary key,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK(length(icom_id)>=4),
foreign key (icom_id) references company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
);

```

**Output:**

![image](https://github.com/user-attachments/assets/49a70359-ed84-48c6-a93c-48a44048b820)


**Question 10**

Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql

insert into Products(ProductID,ProductName,Price,Stock)
select ProductID,ProductName,Price,Stock from Discontinued_products; 

```

**Output:**

![image](https://github.com/user-attachments/assets/4096d462-c837-4c8a-bf58-d154056c8279)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
