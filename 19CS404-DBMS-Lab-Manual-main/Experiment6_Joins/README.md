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

![image](https://github.com/user-attachments/assets/5b936da4-b778-408b-adc2-c850f00f7a04)

```sql
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/020a1685-7857-4485-977b-c29f11a32294)

**Question 2**

![image](https://github.com/user-attachments/assets/b9369423-4fb8-4265-981e-59dfc0c6fead)


```sql
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/dec393d5-5ce6-4b59-b3d6-4b486bf4436b)


**Question 3**

![image](https://github.com/user-attachments/assets/1953161d-5b0b-4777-aa72-062dfa523c00)

```sql
SELECT 
    c.cust_name ,
    c.city ,
    c.grade,
    s.name as  Salesman  ,
    s.city 
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
3
```

**Output:**

![image](https://github.com/user-attachments/assets/929856d3-1320-4f5d-acc8-81b4bd345d21)


**Question 4**

![image](https://github.com/user-attachments/assets/9e9520f2-2a1d-425a-96ad-9ad5630d0d9f)

```sql
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt AS "Order Amount", 
    s.name, 
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/1cd006c1-6e32-46d0-bded-839a10001c00)


**Question 5**

![image](https://github.com/user-attachments/assets/46160731-9ae6-40c3-9098-a00720a77665)


```sql
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.city , 
    s.commission 
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city != s.city
    AND s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/8e54b1d5-a030-4188-ae18-c26772a6f9d6)


**Question 6**

![image](https://github.com/user-attachments/assets/034231f4-ee51-496f-a199-bf24841b1ced)


```sql
SELECT
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM
    salesman s
JOIN
    customer c ON s.city = c.city;

```

**Output:**

![image](https://github.com/user-attachments/assets/a49a153a-b6db-48ce-918b-f8cd964980d2)


**Question 7**

![image](https://github.com/user-attachments/assets/fdc430cd-ed67-4f59-b0f0-b9b385bf300f)


```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/7cc3f79a-faa1-462c-a812-f9ab79c41f78)


**Question 8**

![image](https://github.com/user-attachments/assets/8ace6368-acde-4f4c-8941-f2dbed4b3272)


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
ORDER BY 
    o.ord_date ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/e2a4306d-a29c-41d0-8ae5-316d9b1182c8)


**Question 9**

![image](https://github.com/user-attachments/assets/ede04ca3-83ba-4003-bc3a-10c5e908afa8)


```sql
SELECT 
    p.*,
    d.first_name AS doctor_name
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/58625dd1-9765-4df0-bb15-bf8ef978ebf3)


**Question 10**

![image](https://github.com/user-attachments/assets/4eeb3953-9f2e-454a-a2dd-67e6c5bc49f8)


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

![image](https://github.com/user-attachments/assets/62897191-9dbe-4f00-bdcc-8617914f9ec5)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
