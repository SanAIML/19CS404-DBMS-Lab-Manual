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
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

```sql
UPDATE Employees
set first_name = 'John'
where DEPARTMENT_ID = 80 and commission_pct < 0.35;
```

**Output:**

![Screenshot 2025-05-01 224831](https://github.com/user-attachments/assets/f0acbdca-3bb8-495d-8367-e61058e5a941)


**Question 2**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

```sql
UPDATE Employees
set EMAIL='not available' , COMMISSION_PCT=0.55
where DEPARTMENT_ID = 110;
```

**Output:**

![Screenshot 2025-05-01 224841](https://github.com/user-attachments/assets/4a3b909a-04cf-4cf4-bdb0-85eebf17374b)


**Question 3**
---
Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

```sql
update sales
set total_sell_price  = quantity * sell_price
where product_id   = 10;
```

**Output:**

![Screenshot 2025-05-01 224848](https://github.com/user-attachments/assets/8c20bfd2-d976-44e9-8d2a-f9ea804cdb03)


**Question 4**
---
Write a SQL statement to double the availability of the product with product_id 1.

```sql
update products
set availability = 2*availability
where product_id = 1;
```

**Output:**
![Screenshot 2025-05-01 224857](https://github.com/user-attachments/assets/eb068c41-722b-436c-af09-8b9ad6ba9944)


**Question 5**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

```sql
update products
set reorder_lvl = reorder_lvl*1.3
where category = 'Food' and quantity< 0.5*reorder_lvl;
```

**Output:**


![Screenshot 2025-05-01 224905](https://github.com/user-attachments/assets/54526702-1493-41be-9e17-d82b08d001c9)

**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
delete from Surgeries 
where surgery_date = '2024-02-28';
```

**Output:**

![Screenshot 2025-05-01 224913](https://github.com/user-attachments/assets/99ab8b44-7a16-4fc1-a0dd-8dbec2b543a2)


**Question 7**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

```sql
delete from Customer
where GRADE=3 and CUST_NAME LIKE '%BBB%'and PAYMENT_AMT>2000;
```

**Output:**


![Screenshot 2025-05-01 224924](https://github.com/user-attachments/assets/a724aee7-695e-46e9-88f3-f01d50e9d182)


**Question 8**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3

```sql
Delete from Customer
where CUST_COUNTRY not in ('UK', 'USA', 'Canada') and GRADE >=3; 
```

**Output:**


![Screenshot 2025-05-01 224935](https://github.com/user-attachments/assets/6d97e8ba-45b0-49dd-a8f8-e8f66b02e265)

**Question 9**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
 delete from Doctors 
where doctor_id =1;
```

**Output:**


![Screenshot 2025-05-01 224942](https://github.com/user-attachments/assets/e73a1def-7c83-4a30-b6d5-6963575e26b2)

**Question 10**
---
 Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

Sample table: Surgeries

```sql
delete from Surgeries
where surgery_id = 3 or surgeon_id =4;
```

**Output:**
![Screenshot 2025-05-01 224954](https://github.com/user-attachments/assets/abd3aacd-7548-4eac-803a-ed447e6caf2f)



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
