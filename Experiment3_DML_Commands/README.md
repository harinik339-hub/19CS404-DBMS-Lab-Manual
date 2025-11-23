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
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
update products
set product_name='Grapefruit'
where product_id=4;
```

**Output:**

<img width="1216" height="203" alt="image" src="https://github.com/user-attachments/assets/7c34025a-b987-4e69-a9d9-d6c09c754a26" />


**Question 2**
---
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
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES 
WHERE department_id = 20;
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
201          Michael     MHARTSTE    26000       MK_MAN
202          Pat         PFAY        6000        MK_REP

```sql
update Employees
set salary=salary*2
where department_id=20
   and job_id LIKE '%MAN%';
```

**Output:**

<img width="1232" height="315" alt="image" src="https://github.com/user-attachments/assets/69a0eb3e-0c57-48a0-ad37-196d07cd5df5" />


**Question 3**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

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
For example:

```sql
update PRODUCTS
set sell_price = cast((sell_price*1.10) as int)
where supplier_id=6;
```

**Output:**

<img width="1231" height="510" alt="image" src="https://github.com/user-attachments/assets/1c5e20a4-9931-4cd5-858e-9c769d45f075" />


**Question 4**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

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
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES 
WHERE job_id = 'SA_REP' AND EMAIL='updated' LIMIT 5;
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
150          Peter       updated     10500       SA_REP
151          David       updated     10000       SA_REP
152          Peter       updated     9500        SA_REP
153          Christophe  updated     8500        SA_REP
154          Nanette     updated     8000        SA_REP

```sql
update Employees 
set salary=salary+500, email='updated'
where job_id='SA_REP' and commission_pct>0.15;

```

**Output:**

<img width="1218" height="497" alt="image" src="https://github.com/user-attachments/assets/62ec76c6-8aba-466a-af56-83543bb766ca" />


**Question 5**
---
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
For example:

Test	Result
select changes();
changes()
----------
4


```sql
update Products
set category='Household'
where product_name LIKE '%Detergent%';
```

**Output:**

<img width="1212" height="446" alt="image" src="https://github.com/user-attachments/assets/f6c95ff5-1508-45ea-8dbc-e8da6a83e475" />


**Question 6**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
4


```sql
delete from Customer
where CUST_COUNTRY='UK' AND WORKING_AREA='London' and GRADE<3;
```

**Output:**

<img width="1227" height="417" alt="image" src="https://github.com/user-attachments/assets/1b7f9713-1393-4027-8066-cb9a9fff34b2" />


**Question 7**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28

```sql
delete from Surgeries
where surgery_id=3;
```

**Output:**

<img width="1267" height="351" alt="image" src="https://github.com/user-attachments/assets/087b3326-957d-416e-b39d-7179b589652c" />


**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
delete from Doctors
where specialization='Cardiology';
```

**Output:**

<img width="1208" height="345" alt="image" src="https://github.com/user-attachments/assets/4706a10b-7c62-4843-bf01-ea3a634c6d1d" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
delete from customer
where GRADE <> 3;
```

**Output:**

<img width="645" height="473" alt="image" src="https://github.com/user-attachments/assets/4081e7cd-6d05-46c2-9efa-96081f754460" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
delete from Customer
where CUST_NAME LIKE '______';
```

**Output:**

<img width="1232" height="661" alt="image" src="https://github.com/user-attachments/assets/3f849adc-5dc7-40fa-926d-2f4e99f998f3" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
