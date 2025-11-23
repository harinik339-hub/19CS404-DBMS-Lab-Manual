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

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
For example:

Result
InsuranceCompany   TotalPatients
-----------------  -------------
DEF Insurance      1
GHI Insurance      1
GLM Insurance      2
JKL Insurance      1
MNO Insurance      3
PQR Insurance      1
YZA Insurance      1


```sql
select
      InsuranceCompany,
      COUNT(*) as TotalPatients
from Insurance 
group by InsuranceCompany;
     
```

**Output:**

<img width="672" height="588" alt="image" src="https://github.com/user-attachments/assets/a997d5c5-14b2-4b4e-a9c8-960f5552fb5c" />


**Question 2**
---
How many prescriptions were written for each medication?

Sample tablePrescriptions Table



For example:

Result
Medication     TotalPrescriptions
-------------  ------------------
Ciprofloxacin  1
Doxorubicin    1
Ibuprofen      1
Levothyroxine  1
Lisinopril     1
MMR            1
Pending        1
Prenatal vita  1
Sertraline     1
Topiramate     1

```sql
select
     Medication,
     count(*) as TotalPrescriptions
from Prescriptions 
group by Medication;
```

**Output:**

<img width="720" height="662" alt="image" src="https://github.com/user-attachments/assets/97bfe412-6de7-42a8-a373-ea3c16ff883f" />


**Question 3**
---
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table



For example:

Result
DoctorID    TotalPrescriptions
----------  ------------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1

```sql
select 
     DoctorID,
     count(*) as TotalPrescriptions
from Prescriptions 
group by DoctorID;
```

**Output:**

<img width="662" height="677" alt="image" src="https://github.com/user-attachments/assets/45399590-2a21-4b3c-b0f0-fb0821cd6471" />


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
MAXIMUM
----------
5760.0


```sql
select
    max(purch_amt) as MAXIMUM
from orders;
```

**Output:**

<img width="321" height="285" alt="image" src="https://github.com/user-attachments/assets/e1341d8d-1b30-4a29-aba9-c00368667c17" />


**Question 5**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
age_difference
--------------
13


```sql
select 
     MAX(age) - MIN(age) as age_difference
from employee;
```

**Output:**

<img width="405" height="295" alt="image" src="https://github.com/user-attachments/assets/b378c0fb-0d60-41d3-b14f-a82d02157b44" />


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
 

For example:

Result
total
----------
225

```sql
select 
     sum(inventory) as total
from  fruits 
where unit='LB';
```

**Output:**

<img width="355" height="356" alt="image" src="https://github.com/user-attachments/assets/5c3a1118-3290-444b-b835-926fb0810bb1" />


**Question 7**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name        email           min_email_length
----------  --------------  ----------------
Ravi Kumar  ravi@gmail.com  14

```sql
select name,email,length(email) as min_email_length
from customer 
where length(email)=(
select min(length(email))
from customer
)
limit 1;
```

**Output:**
<img width="900" height="362" alt="image" src="https://github.com/user-attachments/assets/67c5667e-a1d0-47d1-a27d-266389485852" />


**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products



For example:

Result
category_id  Total_Cost
-----------  ----------
2            63


```sql
select
     category_id,
     sum(price) as Total_Cost 
from
      products
group by 
      category_id  
HAVING 
     sum(price) > 50; 
```

**Output:**

<img width="560" height="362" alt="image" src="https://github.com/user-attachments/assets/8b1dbb59-23b3-4ac0-a5a6-2d1a581f3d6d" />


**Question 9**
---
Write the SQL query to find how many patients have more than 3 medical records?.

Sample table: MedicalRecords

name        type
----------  ----------
RecordID    INTEGER
PatientID   INTEGER
DoctorID    INTEGER
Date        DATE
Diagnosis   TEXT
Treatment   TEXT
Medication  TEXT
For example:

Result
PatientID   TotalRecords
----------  ------------
1           4

```sql
select
     PatientID,
     count(*) as TotalRecords
from  MedicalRecords 
group by PatientID  
having count(*) > 3;
```

**Output:**

<img width="567" height="392" alt="image" src="https://github.com/user-attachments/assets/970c7d4d-782d-40b6-b846-a43ca734b257" />


**Question 10**
---
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
select 
     address,
     AVG(salary)
from customer1 
group by address 
having  AVG(salary) > 5000;
```

**Output:**

<img width="566" height="462" alt="image" src="https://github.com/user-attachments/assets/45b209a2-bf74-4fb5-813b-e9f577181315" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
