# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**

![image](https://github.com/user-attachments/assets/bc4ca765-6c12-453c-af56-f0a8198394fe)


```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi' AND AGE < 30
ORDER BY ID;
```

**Output:**

![image](https://github.com/user-attachments/assets/164afd13-3206-4254-9deb-93d55cd8b88b)


**Question 2**

![image](https://github.com/user-attachments/assets/dec2ba69-7bfa-4b17-ba3d-0cd831375398)


```sql
SELECT g.student_name, g.grade
FROM GRADES g
JOIN (
    SELECT subject, MIN(grade) AS min_grade
    FROM GRADES
    GROUP BY subject
) AS min_grades ON g.subject = min_grades.subject AND g.grade = min_grades.min_grade;
```

**Output:**

![image](https://github.com/user-attachments/assets/7ee610bf-6fc4-4082-a633-127d9c910ca2)

**Question 3**

![image](https://github.com/user-attachments/assets/5e256c61-584c-4a7b-967c-026c40be5020)

```sql
SELECT g.*
FROM GRADES g
JOIN (
    SELECT subject, MAX(grade) AS max_grade
    FROM GRADES
    GROUP BY subject
) AS max_grades ON g.subject = max_grades.subject AND g.grade = max_grades.max_grade;
```

**Output:**

  ![image](https://github.com/user-attachments/assets/befdcf19-4e1d-4428-b484-846c0c8a9135)


**Question 4**

![image](https://github.com/user-attachments/assets/e28348cd-68d4-4a59-8f37-e8eaa5f232e1)


```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/7d82ab61-0500-4b66-8b46-bd3e6d53c1d3)

**Question 5**

![image](https://github.com/user-attachments/assets/807faebf-2a81-4c43-bed0-c8c0e5b8f66a)


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

![image](https://github.com/user-attachments/assets/cfa4590b-c9cf-43bf-ad22-2af2cee2aeba)

**Question 6**

![image](https://github.com/user-attachments/assets/f2d8fbcc-acc2-4e5c-9445-e22e68ffbad5)


```sql
SELECT * FROM orders WHERE salesman_id IN (select salesman_id FROM salesman WHERE city ='London');
```

**Output:**

![image](https://github.com/user-attachments/assets/27a3e527-0a65-4509-98e2-3988bf6a79b3)


**Question 7**

![image](https://github.com/user-attachments/assets/bb7dbeaa-5a09-49d9-92da-0918d002c1c5)


```sql
SELECT * FROM orders WHERE salesman_id IN (select salesman_id FROM salesman WHERE city ='New York');
```

**Output:**

![image](https://github.com/user-attachments/assets/82c8dc38-b695-4793-a71e-830d8f480fe6)

**Question 8**

![image](https://github.com/user-attachments/assets/e916ed3d-47ea-4d5d-b855-3aa44329965e)


```sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/f039ef9a-3a37-4ddd-a98d-89e78ef6626b)


**Question 9**

![image](https://github.com/user-attachments/assets/90d07760-06b4-4ee4-9965-dd6c1d9a5128)


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

![image](https://github.com/user-attachments/assets/ddc741c3-ef05-4b06-8d11-a09d8874e583)

**Question 10**

![image](https://github.com/user-attachments/assets/4667dcda-5d8e-4d32-ab12-73fdaa67a927)


```sql
SELECT g.*
FROM GRADES g
JOIN (
    SELECT subject, MIN(grade) AS min_grade
    FROM GRADES
    GROUP BY subject
) AS min_grades ON g.subject = min_grades.subject AND g.grade = min_grades.min_grade;
```

**Output:**

![image](https://github.com/user-attachments/assets/6e44fe4a-6677-4d8b-a026-f713de5f75e2)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
