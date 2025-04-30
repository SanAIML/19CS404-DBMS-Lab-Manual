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
 Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```sql
 insert into Student_details(RollNo,Name,Gender,Subject,MARKS)
values('201','David Lee','M','Physics','92');
```

**Output:**


![Screenshot 2025-04-30 154012](https://github.com/user-attachments/assets/bd04e1aa-c089-4ae7-96ca-3181d8945713)

**Question 2**
---
 Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- create table Invoices(
InvoiceID  INTEGER primary key,
InvoiceDate  DATE,
Amount real
CHECK(Amount>0),
DueDate DATE
CHECK(DueDate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderID) references Orders(OrderID)
)
```

**Output:**


![Screenshot 2025-04-30 154026](https://github.com/user-attachments/assets/145b13ad-5e22-4698-858c-26e758aadd96)

**Question 3**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

```sql
create table Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```

**Output:**


![Screenshot 2025-04-30 154056](https://github.com/user-attachments/assets/baf36dde-fbb1-4ad7-b6e5-ff6f7aa8834a)

**Question 4**
---
 Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```sql
alter table employee add column first_name varchar(50); 
alter table employee add column last_name varchar(50);
```

**Output:**


![Screenshot 2025-04-30 154113](https://github.com/user-attachments/assets/22359850-9f71-43fb-b599-afa0e2dd88b1)

**Question 5**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
alter table employee rename id to employee_id;
```

**Output:**


![Screenshot 2025-04-30 154124](https://github.com/user-attachments/assets/fcf1b75e-d549-469b-b549-fca50de7022a)

**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs(
job_id integer,
job_title text default '',
min_salary integer default 8000,
max_salary integer null

);

```

**Output:**


![Screenshot 2025-04-30 154137](https://github.com/user-attachments/assets/26b7a62d-8100-489c-a237-0f47b724238a)

**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
create table item(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT CHECK(length(icom_id)==4),
foreign key (icom_id) references company(com_id) 
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**


![Screenshot 2025-04-30 154146](https://github.com/user-attachments/assets/ef00be80-b578-44e7-ab00-1e7e726d6f60)

**Question 8**
---
Insert the following customers into the Customers table:

```sql
insert into Customers (CustomerID,Name,Address,City,ZipCode)
values('302','Laura Croft' , '456 Elm St' , 'Seattle' ,'98101'),
(303, 'Bruce Wayne'  ,'789 Oak St',  'Gotham','10001');
```

**Output:**


![Screenshot 2025-04-30 154204](https://github.com/user-attachments/assets/4eb03818-12e3-48ab-b577-2c50967789ae)

**Question 9**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```sql
create table Attendance(
AttendanceID  INTEGER primary key,
EmployeeID INTEGER ,
AttendanceDate  DATE,
Status TEXT check(Status in( 'Present', 'Absent', 'Leave')),
foreign key (EmployeeID) references Employees(EmployeeID)
);
```

**Output:**


![Screenshot 2025-04-30 154217](https://github.com/user-attachments/assets/69a68eae-55d5-454a-9292-12af033bdfa1)

**Question 10**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
insert into Employee(EmployeeID, Name, Department, Salary)
select EmployeeID, Name, Department, Salary from Former_employees;
```

**Output:**


![Screenshot 2025-04-30 154224](https://github.com/user-attachments/assets/7be92b8c-8fc1-4bd8-b8f6-d2106fcad482)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
