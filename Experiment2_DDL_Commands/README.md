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
---
- Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.
```sql
alter table Student_details add column Email varchar(50);
alter table Student_details add column MARKS int DEFAULT 0;

```
**Output:**
<img width="1347" height="216" alt="image" src="https://github.com/user-attachments/assets/66ae1e08-86ff-4cd5-9b98-4239b462efa0" />



**Question 2**
---
- Insert all books from Out_of_print_books into Books
- Table attributes are ISBN, Title, Author, Publisher, YearPublished
```sql
insert into Books select * from out_of_print_books;
```

**Output:**
<img width="1382" height="240" alt="image" src="https://github.com/user-attachments/assets/c7b61a20-12bb-4e82-bcff-c9b4a85c259c" />


**Question 3**
---
- Create a table named ProjectAssignments with the following constraints:
* AssignmentID as INTEGER should be the primary key.
* EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
* ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
* AssignmentDate as DATE should be NOT NULL.
```sql
create table ProjectAssignments(
AssignmentID int primary key, 
EmployeeID int,ProjectID int,
AssignmentDate date not null,
foreign key(EmployeeID) references Employees(EmployeeID),
foreign key(ProjectID) references Projects(ProjectID));


```
**Output:**
<img width="1297" height="202" alt="image" src="https://github.com/user-attachments/assets/4df3e7be-9b2f-48e4-90d3-8d15cdac1fa5" />

**Question 4**
---
- Create a new table named orders with the following specifications:
* ord_id as TEXT with a length of 4.
* item_id as TEXT.
* ord_date as DATE.
* ord_qty as INTEGER.
* cost as INTEGER.
* The primary key is a composite key consisting of item_id and ord_date.
* ord_id and item_id should not accept NULL
```sql
create table orders(
ord_id text check(length(ord_id)<=4) not null,
item_id text  not null,
ord_date date,
ord_qty int,
cost int,
primary key(item_id,ord_date));
```
**Output:**
<img width="1317" height="242" alt="image" src="https://github.com/user-attachments/assets/f60085dc-3691-4c35-93aa-56e6c2422907" />

**Question 5**
---
- Create a table named Members with the following columns:
*MemberID as INTEGER
*MemberName as TEXT
*JoinDate as DATE
```sql
create table members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**
<img width="1322" height="282" alt="image" src="https://github.com/user-attachments/assets/4421622a-e33b-47ba-acc1-23603d4cdd2d" />

**Question 6**
---
- Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.
```sql
insert into Student_details(RollNo,Name,Gender,Subject,MARKS) VALUES(201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1322" height="192" alt="image" src="https://github.com/user-attachments/assets/cfa2102f-288c-483b-9c96-dd99fcfb16e2" />



**Question 7**
---
- In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

|RollNo | Name |Gender |Subject|MARKS|
|----------|  ------------|    ----------|  ----------|   ----------|
205 |Olivia Green| F|||
207 | Liam Smith| M|Mathematics| 85|
208 | Sophia Johnson|  F|Science||

```sql

insert into Student_details values(205,'Olivia Green','F',null,null);
insert into Student_details values(207,'Liam Smith','M','Mathematic',85);
insert into Student_details values(208 ,'Sophia Johns', 'F' ,'Science',null);



```

**Output:**
<img width="1285" height="187" alt="image" src="https://github.com/user-attachments/assets/a939f5ee-9d65-4378-aa8e-39b6f91c7023" />



**Question 8**
---
- Create a table named Department with the following constraints:
* DepartmentID as INTEGER should be the primary key.
* DepartmentName as TEXT should be unique and not NULL.
* Location as TEXT.

```sql
create table Department(
DepartmentID INTEGER primary key,
DepartmentName TEXT unique not NULL,
Location TEXT
);

```

**Output:**
<img width="1337" height="211" alt="image" src="https://github.com/user-attachments/assets/ade45c37-e10a-4946-91dd-8e9d89a24aa5" />



**Question 9**
---
- Create a table named Employees with the following constraints:

* EmployeeID should be the primary key.
*FirstName and LastName should be NOT NULL.
* Email should be unique.
* Salary should be greater than 0.
* DepartmentID should be a foreign key referencing the Departments table.
```sql
create table Employees(
EmployeeID INTEGER primary key,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL, 
Email TEXT UNIQUE,
Salary INT CHECK(Salary>0),
DepartmentID int,
foreign key(DepartmentID) references Departments(DepartmentID));

```

**Output:**
<img width="1321" height="340" alt="image" src="https://github.com/user-attachments/assets/38de81cd-bfc1-482d-bc3f-90342b617605" />



**Question 10**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

| customer_id |   cust_name    |    city    | grade | salesman_id| 
|-------------|----------------|------------|-------|-------------|
|        3002 | Nick Rimando   | New York   |   100 |        5001|
|       3007 | Brad Davis     | New York   |   200 |        5001|
|        3005 | Graham Zusi    | California |   200 |        500|
```sql
alter table customer add column birth_date timestamp;
```

**Output:**
<img width="1316" height="252" alt="image" src="https://github.com/user-attachments/assets/a3527cf8-be02-4de4-8a7e-9ff51487c322" />

**FINAL GRADE:**
<img width="1502" height="452" alt="image" src="https://github.com/user-attachments/assets/0b83f370-8a74-4344-93f4-95c9aac7f702" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
