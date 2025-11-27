# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders o
INNER JOIN customer c 
    ON o.customer_id = c.customer_id
INNER JOIN salesman s 
    ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1278" height="921" alt="image" src="https://github.com/user-attachments/assets/a1fef34a-8a68-4d9b-8f96-2f7c0dc7cc85" />


**Question 2**
---
-- Paste Question 2 hereWrite the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM patients p
INNER JOIN doctors d 
    ON p.doctor_id = d.doctor_id
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="909" height="488" alt="image" src="https://github.com/user-attachments/assets/711dabc2-a230-4514-8c3f-5075319fe5d2" />


**Question 3**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.

```sql
SELECT 
    s.name
FROM salesman s
LEFT JOIN customer c 
    ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';

```

**Output:**

<img width="1079" height="544" alt="image" src="https://github.com/user-attachments/assets/223fe71b-ac7d-4055-a457-17494e70abdf" />


**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

```sql
SELECT 
    n.*
FROM nurses n
INNER JOIN departments d
    ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';

```

**Output:**

<img width="1383" height="535" alt="image" src="https://github.com/user-attachments/assets/b7602efe-28f0-4c2d-a76f-3bce1307db55" />


**Question 5**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1351" height="893" alt="image" src="https://github.com/user-attachments/assets/86e42412-85d1-4945-bacc-5eea67630d05" />


**Question 6**
---
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  
```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="1322" height="874" alt="image" src="https://github.com/user-attachments/assets/9dbc15f4-d170-434b-9a37-f930eefa80c6" />


**Question 7**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.
```sql
SELECT 
    c.cust_name
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.purch_amt < 100;

```

**Output:**

<img width="658" height="611" alt="image" src="https://github.com/user-attachments/assets/204f1c9c-1cec-4a45-bb2d-c4ad7f794bb8" />


**Question 8**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="1333" height="599" alt="image" src="https://github.com/user-attachments/assets/ae7bd603-c086-4d01-9e11-657af6f4e562" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
