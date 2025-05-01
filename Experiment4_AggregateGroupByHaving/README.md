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
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```sql
select DoctorID, count(*) as TotalAppointments from Appointments group by DoctorID order by DoctorID;
```

**Output:**

![Screenshot 2025-05-01 231352](https://github.com/user-attachments/assets/19a958d0-25fb-4e1e-a3df-ed3383f48948)


**Question 2**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

```sql
select AVG(income) as Average_Salary from employee;
```

**Output:**

![Screenshot 2025-05-01 231359](https://github.com/user-attachments/assets/648dacc0-716e-4956-aabd-c65f44d195cc)


**Question 3**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

```sql
select name,email,MIN(length(email )) as min_email_length from customer;
```

**Output:**

![Screenshot 2025-05-01 231404](https://github.com/user-attachments/assets/60d44443-b042-4801-80d1-3ab42c327f15)

**Question 4**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

```sql
select count(*) as employees_count from employee where income>50000; 
```

**Output:**


![Screenshot 2025-05-01 231411](https://github.com/user-attachments/assets/1b15bfc9-a1f8-4c40-a2ac-55c985459903)

**Question 5**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

```sql
select AVG(length(name)) as avg_name_length from customer where city = 'Chennai';
```

**Output:**

![Screenshot 2025-05-01 231418](https://github.com/user-attachments/assets/c815553b-4175-4b4f-a663-e689fe932581)


**Question 6**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```sql
select age, SUM(income) from employee group by age having SUM(income) > 1000000;
```

**Output:**


![Screenshot 2025-05-01 231423](https://github.com/user-attachments/assets/3a34c2ad-6dff-468b-a3fa-29ca33dc02b7)

**Question 7**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1

```sql
select (age/5)*5 as age_group,AVG(age) from customer1 group by age_group having AVG(age)<24; 
```

**Output:**

![Screenshot 2025-05-01 231428](https://github.com/user-attachments/assets/c9d83bb1-88f8-4808-a048-3bb37309c1bc)


**Question 8**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products

```sql
select category_id, AVG(Price) from products group by category_id having AVG(Price) between 10 and 15;
```

**Output:**


![Screenshot 2025-05-01 231434](https://github.com/user-attachments/assets/4d0872a8-c7e4-4626-b26e-9f2ae46629b4)

**Question 9**
---

How many medical records are there for each patient?

Sample table:MedicalRecords Table
```sql
SELECT PatientID, count (*) as TotalRecords from MedicalRecords
group by PatientID
```

**Output:**


![Screenshot 2025-05-01 232132](https://github.com/user-attachments/assets/61ac4560-aad4-4492-99b4-f011a9f6c0c6)

**Question 10**
---
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

```sql
select InsuranceCompany, AVG(EndDate-StartDate)as AvgCoverageDurationDays from Insurance
group by InsuranceCompany ;
```

**Output:**


![Screenshot 2025-05-01 232348](https://github.com/user-attachments/assets/7bcce727-7f03-4d02-bafd-9669d63946c9)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
