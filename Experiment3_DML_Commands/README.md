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
Write a SQL query to remove rows from the table 'customer' with the following condition -

'cust_country' must be 'India',

'cus_city' must not be 'Chennai',
program
```
DELETE FROM Customer
WHERE cust_country ='India'
AND cust_city != 'Chennai';
```
**Output:**

<img width="1256" height="927" alt="image" src="https://github.com/user-attachments/assets/80ea3c69-015e-4245-bd7f-41da465a6cde" />


**Question 2**
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
program
```
DELETE FROM customer
WHERE CUST_CITY != 'New York'
AND OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="1261" height="617" alt="image" src="https://github.com/user-attachments/assets/bad85dba-e4ee-4294-8af6-95f0f8a7ecf1" />

**Question 3**
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.
program
```
SELECT product_id,
original_price,discount_percentage,
original_price-(original_price*discount_percentage)AS discounted_price
FROM Products
WHERE discount_percentage > 0
ORDER BY discounted_price ASC;
```

**Output:**

<img width="1262" height="282" alt="image" src="https://github.com/user-attachments/assets/fe2a4d11-620c-4f76-b43b-cd20bc1e1281" />


**Question 4**
Write a SQL query to Get the employees whose name starts and ends with the same two characters:
program
```
SELECT ename
FROM emp
WHERE LOWER(SUBSTR(ename,1,2))=LOWER(SUBSTR(ename,-2));
```

**Output:**

<img width="567" height="362" alt="image" src="https://github.com/user-attachments/assets/8e5f216b-fc60-4fa1-aaf3-da1309b29b27" />


**Question 5**
Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table
program
```
SELECT id,
value2,
CASE 
WHEN value2<30 THEN 'Poor'
WHEN value2>=30 AND value2<70 THEN 'Average'
ELSE 'Excellent'
END AS performance
FROM Calculations;
```

**Output:**

<img width="1012" height="512" alt="image" src="https://github.com/user-attachments/assets/ef6e02bb-8f24-4ec5-b0cc-9d48381654c9" />

**Question 6**
Write a SQL query to display hire dates in the format "DD-MM-YYYY" from the emp table
program
```
SELECT ename,
strftime('%d-%m-%Y',hiredate)AS HireDateFormatted
FROM emp;
```
**Output:**

<img width="897" height="437" alt="image" src="https://github.com/user-attachments/assets/6675c8da-5ea4-447d-a0e1-5bd4abe92b90" />


**Question 7**
Write a SQL statement to Display names and city of salesman, who belongs to the city of London or Rome.
program
```
SELECT name,city
FROM salesman
WHERE city = 'London' 
OR city='Rome';
```

**Output:**

<img width="737" height="432" alt="image" src="https://github.com/user-attachments/assets/66943e6e-1912-4ab1-b0f5-a095166a362b" />


**Question 8**
---Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.
program
```
DELETE FROM customer
WHERE LENGTH(CUST_NAME)=6;
```


**Output:**

<img width="1267" height="775" alt="image" src="https://github.com/user-attachments/assets/4fb2b534-7bbc-491e-a0d0-2e90cb64b6f2" />


**Question 9**
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.
program
```
DELETE FROM doctors
WHERE last_name='Brown'
AND specialization IN ('Pediatrics','Cardiology');
```

**Output:**

<img width="1256" height="955" alt="image" src="https://github.com/user-attachments/assets/a198e03d-04ca-4c49-8e65-1112a69782e7" />


**Question 10**
Write a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.
program
```
SELECT 
product_id,original_price,
discount_percentage,
original_price-(original_price*discount_percentage) AS discounted_price
FROM Products;
```

**Output:**

<img width="1251" height="457" alt="image" src="https://github.com/user-attachments/assets/c1827811-6457-44af-90db-0070f99d9112" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
