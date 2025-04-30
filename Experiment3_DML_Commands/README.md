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

Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability


```sql

update products 
set availability = availability*2
where product_id= 1;

```

**Output:**

![Screenshot 2025-04-30 201922](https://github.com/user-attachments/assets/d73750de-d526-4d0e-8e3d-3bba6a538aa6)


**Question 2**

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


```sql

update Employees
set EMAIL='not available' , COMMISSION_PCT=0.55
where DEPARTMENT_ID = 110;

```

**Output:**

![Screenshot 2025-04-30 202001](https://github.com/user-attachments/assets/984f3871-bcff-4d85-861d-8defc7b5cbea)


**Question 3**

Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

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

update Employees
set SALARY=SALARY*2
where department_id=20 and job_id LIKE '%MAN';


```

**Output:**

![Screenshot 2025-04-30 202023](https://github.com/user-attachments/assets/4ad41e99-7ac2-4176-8f11-9368cd965eac)



**Question 4**

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

update PRODUCTS 
set reorder_lvl=reorder_lvl*0.7
where product_name LIKE '%cream%' and quantity>reorder_lvl ;

```

**Output:**

![Screenshot 2025-04-30 202157](https://github.com/user-attachments/assets/2acb6ddd-183f-4201-9719-222ebf0d4d1d)



**Question 5**

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```sql

delete from Customer
where grade!=3;

```

**Output:**

![Screenshot 2025-04-30 202219](https://github.com/user-attachments/assets/f1c722f6-a717-411c-92ac-27d8cb5f3311)


**Question 6**

Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00

```sql

delete from Customer 
where 
(grade >2 and payment_amt<(select avg(payment_amt) from Customer) or outstanding_amt>8000);


```

**Output:**

![Screenshot 2025-04-30 202305](https://github.com/user-attachments/assets/ee681a33-89ae-49f4-bbd2-6f02573ca1ed)



**Question 7**

Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql

delete from doctors where doctor_id =1;

```

**Output:**


![Screenshot 2025-04-30 202336](https://github.com/user-attachments/assets/75131e48-4ce2-44e8-b9f7-b41b036bd16c)





**Question 8**

Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002


```sql

select customer_id,cust_name,city,grade,salesman_id  from customer where city='London' and grade>200;

```

**Output:**

![Screenshot 2025-04-30 202534](https://github.com/user-attachments/assets/251c9213-14ce-4895-8528-c6fe6f817130)




**Question 9**

Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002


```sql

select customer_id,cust_name,city,grade,salesman_id from customer 
where city='New York' or grade<=100;

```

**Output:**

![Screenshot 2025-04-30 202544](https://github.com/user-attachments/assets/da75484d-cc39-4748-8623-8603062ee940)


**Question 10**

Write a SQL query to Select all patients whose name starts with A.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```sql

select * 
from Patients 
where first_name like 'A%';

```

**Output:**

![Screenshot 2025-04-30 201856](https://github.com/user-attachments/assets/d403c112-d02d-45b7-8f4f-9df54dd5848d)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
