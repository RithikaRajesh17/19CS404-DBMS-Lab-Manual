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

How many patients are covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```sql

SELECT InsuranceCompany, COUNT(DISTINCT PatientID) AS TotalPatients from Insurance group by InsuranceCompany order by InsuranceCompany

```

**Output:**

![image](https://github.com/user-attachments/assets/fdd93a6b-4b41-4392-b0f5-28461f3a415e)


**Question 2**

What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE

```sql

select InsuranceCompany, AVG(EndDate-StartDate)as AvgCoverageDurationDays from Insurance
group by InsuranceCompany ;

```

**Output:**

![image](https://github.com/user-attachments/assets/35ed3a4a-fead-40ec-ba10-05e31396e44c)


**Question 3**

How many medical records does each doctor have?

Sample table:MedicalRecords Table
For example:
Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3


```sql

select DoctorID, count(*) as TotalRecords from MedicalRecords group by DoctorID order by DoctorID;

```

**Output:**

![image](https://github.com/user-attachments/assets/268c0551-b4e9-42fe-bd7b-5d5dc86cec3c)


**Question 4**

Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001


```sql

select sum(purch_amt) as TOTAL from orders;

```

**Output:**

![image](https://github.com/user-attachments/assets/58bbf4ac-d9e2-45ed-b991-55a0feb6d5d8)

**Question 5**

Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER


```sql

select sum(income)as total_income from employee where age >=40;

```

**Output:**

![image](https://github.com/user-attachments/assets/5d6757e2-b989-4552-9cab-bf9cf6d9e47f)


**Question 6**

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

![image](https://github.com/user-attachments/assets/461b9892-de2c-42a7-9e3b-2144cdfa3b78)


**Question 7**

Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql

SELECT MAX(age)-MIN(AGE) as age_difference from employee;

```

**Output:**

![image](https://github.com/user-attachments/assets/2e14ba4c-f96b-4685-99db-64f10779c5d0)


**Question 8**

Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee
For example:

Result
age         AVG(income)
----------  -----------
45          450000.0

```sql

SELECT age, AVG(income) FROM employee group by age having AVG(income) between 300000 and 500000;


```

**Output:**

![image](https://github.com/user-attachments/assets/894f183a-45d5-43c6-915a-17d41054bcc0)


**Question 9**

Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1
For example:

Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0

```sql

select occupation,AVG(workhour) from employee1 group by occupation having AVG(workhour) between 10 and 12;


```

**Output:**


![image](https://github.com/user-attachments/assets/a85262d8-14a4-4c94-b180-29309a4876bd)


**Question 10**

Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1
For example:

Result
address     AVG(salary)
----------  -----------
Bhopal      8500.0
Indore      10000.0
Mumbai      6500.0


```sql

select address,AVG(salary) from customer1 group by address having AVG(salary)>5000

```

**Output:**


![image](https://github.com/user-attachments/assets/c8506ea5-e263-47d4-9bac-a9a2eba3d925)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
