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
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

|Products table|
|---------------|
|product_id|
|product_name|
|category|
|cost_price|
|sell_price|
|reorder_lvl|
|quantity|
|supplier_id|

```sql
update products set quantity=1.1*quantity;
```

**Output:**
<img width="1282" height="442" alt="image" src="https://github.com/user-attachments/assets/e9f6a851-eb81-44bf-8f58-07a62e601709" />



**Question 2**
---

For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

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
update products set sell_price=cast(1.35*cost_price as integer) where ((sell_price-cost_price)/sell_price)*100 < 30 and sell_price > 0;
```

**Output:**
<img width="1287" height="370" alt="image" src="https://github.com/user-attachments/assets/357f304a-0c66-4863-8870-4a1ed4c91ee9" />



**Question 3**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
update sales set sell_price=1.05*sell_price where product_id=15 and sale_date='2023-01-31';
```

**Output:**
<img width="1286" height="337" alt="image" src="https://github.com/user-attachments/assets/0e9922ab-5bfe-4421-b478-101052bfb694" />



**Question 4**
---
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
update customer set grade=5 where city='Chennai';
```

**Output:**
<img width="1337" height="351" alt="image" src="https://github.com/user-attachments/assets/2c459b7a-5508-4851-9a9e-48d2a468f1d0" />


**Question 5**
---
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name       |   type       
---------- |   ---------- 
product_id |    INT PRIMARY KEY        
product_name|   VARCHAR(10) 
category    |   VARCHAR(50) 
cost_price  |   DECIMAL(10) 
sell_price  |   DECIMAL(10) 
reorder_lvl |   INT        
quantity    |   INT        
supplier_id |   INT      

```sql
update products set category='Household' where product_name like "%Detergent%";
```

**Output:**

<img width="1360" height="387" alt="image" src="https://github.com/user-attachments/assets/fbb76fa9-f509-400f-9e2e-065fed44363c" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO|AGENT_CODE |
|-----------|-------------|-------------|--------------|--------------|-------|-------------|-------------|-------------|---------------|--------------|---------|
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003|
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008 |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008 |

```sql
delete from customer where cust_name like "%Holmes%";
```

**Output:**
<img width="1322" height="445" alt="image" src="https://github.com/user-attachments/assets/0f35024c-66a4-4611-848a-e7a1a417cc83" />



**Question 7**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO|AGENT_CODE |
|-----------|-------------|-------------|--------------|--------------|-------|-------------|-------------|-------------|---------------|--------------|---------|
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003 |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008 |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008 |

```sql
delete from customer where grade=3 and cust_name like '%BBB%' and payment_amt>2000;
```

**Output:**
<img width="1282" height="361" alt="image" src="https://github.com/user-attachments/assets/5d550f93-44f6-4fec-809a-cb853f91a3f3" />



**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors where last_name is NULL;
```

**Output:**
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/89e08dfa-ebd2-4b65-a5ae-011103ad506f" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO |AGENT_CODE |
|-----------|-------------|-------------|--------------|--------------|-------|-------------|-------------|-------------|--------------|--------------|---------|
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003 |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008 |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008 |

```sql
delete from customer where agent_code in ('A003','A008');
```

**Output:**

<img width="942" height="835" alt="image" src="https://github.com/user-attachments/assets/c42096db-d09e-49cf-b58b-ae95041e308b" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO |AGENT_CODE |
|-----------|-------------|-------------|--------------|--------------|-------|-------------|-------------|-------------|---------------|--------------|---------|
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003 |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008 |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008 |

```sql
delete from customer where grade =2;
```

**Output:**
<img width="771" height="432" alt="image" src="https://github.com/user-attachments/assets/e3194568-e017-4ae4-9b8e-939fcf1d56da" />

**Question 11**
---
Write a query to fetch last 5 rows in EmployeeInfo table.

EmpID|EmpFname |EmpLname| Department| Project| Address| DOB|Gender
|----|------|-------|--------|-------|--------|----|----|
1 |    Sanjay  | Mehra    |HR|P1|Hyderabad(HYD)|01/12/1976 |  M|
2|Ananya|Mishra|Admin|P2|Delhi(DEL)| 02/05/1968|F|

```sql
select * from employeeinfo order by EmpID DESC LIMIT 5;
```

**Output:**
<img width="1296" height="237" alt="image" src="https://github.com/user-attachments/assets/202f2f2a-abf1-4d4c-95ca-9b0d4b050178" />

**Question 12**
---
Show the categoryName and description from the categories table sorted by categoryName.

name            |         type
--------------- |      ---------------
CategoryID      |     INTEGER
CategoryName    | VARCHAR(25)
Description     |     VARCHAR(255)

```sql
select categoryName, Description from categories order by CategoryName;
```

**Output:**
<img width="1062" height="387" alt="image" src="https://github.com/user-attachments/assets/f47ab1a9-77bf-4e1c-8e68-fb3f6372d5dc" />

**Question 13**
---
Write a SQL query to evaluate the status of rows in the Calculations table based on whether value1 is positive, negative, or zero.

cid        | name     |   type    |   notnull  |   dflt_value|  pk
---------- |----------| ----------|  ----------|  ---------- | ----------|
0          | id        | INTEGER   | 0          |             |          1|
1          | value1    | REAL      | 0          |             |          0|
2          | value2    | REAL      | 0          |             |          0|
3          | base      | INTEGER   | 0          |             |          0|
4          | exponent  | INTEGER   | 0          |             |          0|
5          | number    | REAL      | 0          |             |          0|
6          | decimal   | REAL      | 0          |             |          0|

```sql
select id, value1, case when value1 > 0 THEN 'Positive' WHEN value1 < 0 THEN 'Negative' ELSE 'Zero' END AS value_status from calculations;
```
**Output:**

<img width="782" height="362" alt="image" src="https://github.com/user-attachments/assets/424c7534-100a-4795-a1b5-337b4180375f" />

**Question 14**
---
write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 |customer_id |   cust_name    |    city    | grade | salesman_id|
|-------------|----------------|------------|-------|-------------|
        3002 | Nick Rimando   | New York   |   100 |        5001|
        3007 | Brad Davis     | New York   |   200 |        5001|
        3005 | Graham Zusi    | California |   200 |        5002|
```sql
select * from customer where (city='New York') OR (grade <= 100);
```
**Output:**
<img width="1036" height="317" alt="image" src="https://github.com/user-attachments/assets/2e4dd67a-df45-4341-bbc6-69e8dd5248ab" />

**Question 15**
---
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 
-------------|---------------|-------------|-------|-------------|
        3002 | Nick Rimando   | New York   |   100 |        5001|
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```sql
select * from customer where grade is NULL;
```
**Output:**
<img width="1050" height="287" alt="image" src="https://github.com/user-attachments/assets/869cc5ba-6076-4e3f-bb34-904162e641e7" />


**Question 16**
---
Write a query to calculate the discounted_price and  discounted_price_percentage for each product from the products table. Return product_id, original_price, discount_percentage, discounted_price, and discounted_price_percentage.

Discounted Price: Calculate the price of the product after applying the discount.

Discounted Price Percentage: Calculate the percentage that the discounted price represents relative to the original price.
```sql
select product_id, original_price,discount_percentage,(original_price-original_price*discount_percentage) as discounted_price,CAST(CAST((1-discount_percentage)*100 AS INT) AS TEXT) ||"%" as discounted_price_percentage from products;
```
**Output:**
<img width="1302" height="172" alt="image" src="https://github.com/user-attachments/assets/933f71b7-5c47-4d2f-8304-e097632f06d0" />

**Question 17**
---
Write a query to list all products where the discount amount exceeds $50. The discount amount is calculated as original_price * discount_percentage. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: Products

product_id | original_price | discount_percentage|
-----------|----------------|--------------------|
"101"|"50"|"0.1"|
"102" |"150"| "0.15"|
"103" |"200" |"0.2"|
"104" |"300" |"0.25"|

 
```sql
select product_id, original_price, discount_percentage,(original_price*discount_percentage) as discount_amount from products where original_price*discount_percentage > 50;
```
**Output:**
<img width="1102" height="172" alt="image" src="https://github.com/user-attachments/assets/7127dc4f-886a-46e1-bee4-42d79e2dda9b" />


**Question 18**
---
Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.

```sql
select STRFTIME('%Y',hiredate) as Year,STRFTIME("%m",hiredate) as Month,STRFTIME('%d',hiredate) as Day from emp;
```

**Output:**

<img width="802" height="261" alt="image" src="https://github.com/user-attachments/assets/c5f9ac26-45d5-4c1e-933d-f7da0c383096" />


**Question 19**
Write a SQL query to select patient's names along with their age groups (e.g., 'Under 20', '20-30', '31-40', '41-50', 'Above 50') based on their date of birth. 

Note: Consider current date as '2023-12-30' while calculating age.

Table: Patients

name               |  type      |
-------------------|  ----------|
patient_id         |  INT       |  
first_name         | VARCHAR(50)|
last_name          | VARCHAR(50)|
date_of_birth      |   DATE     | 
admission_date     |   DATE     |
discharge_date     |   DATE     |
doctor_id          |   INT      |

```sql

select first_name, last_name,
CASE
WHEN CAST((JULIANDY(discharge_date)-JULIANDAY(date_of_birth))/365.25 AS INT) < 20 THEN 'Under 20'
WHEN CAST((JULIANDY(discharge_date)-JULIANDAY(date_of_birth))/365.25 AS INT) BETWEEN 20 AND 30 THEN '20-30'
WHEN CAST((JULIANDY(discharge_date)-JULIANDAY(date_of_birth))/365.25 AS INT) BETWEEN 30 AND 40 THEN '31-40'
WHEN CAST((JULIANDY(discharge_date)-JULIANDAY(date_of_birth))/365.25 AS INT) BETWEEN 40 AND 50 THEN '41-50'
ELSE 'Above 50'
END AS 'AgeGroup'
from patients;
```

**Output:**

<img width="1092" height="462" alt="image" src="https://github.com/user-attachments/assets/df06ded5-184b-46fb-9b7a-33b245f47643" />



**Question 20**
---
Create a report that shows the capitalized FirstName and capitalized LastName renamed as FirstName and Lastname respectively and EmployeeId from the employees table sorted by EmployeeId in descending order.

employees table

|cid       |       name  |       type |      notnull|  dflt_value|  pk      |
|----------|  ---------- | ---------- | ----------  |----------  |----------|
0          |EmployeeID   |  INTEGER   |            0|            | 1
1          |LastName     | VARCHAR(15)|            0|            |0
2          |FirstName    | VARCHAR(15)|            0|            |0
3          |BirthDate    | DATETIME   |            0|            |0
4          |Photo        | VARCHAR(25)|            0|            |0
5          |Notes        | VARCHAR(10)|            0|            |0
```sql
select UPPER(FirstName) as FirstName, UPPER(LastName) as LastName, EmployeeID from employees order by EmployeeID DESC;
```

**Output:**

<img width="660" height="372" alt="image" src="https://github.com/user-attachments/assets/91ca67f0-1d9c-4a12-913f-0d28fdd40705" />

**FINAL GRADE:**
<img width="1457" height="475" alt="image" src="https://github.com/user-attachments/assets/d5b39ea4-a50f-4cb2-a0e4-3049b192016b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
