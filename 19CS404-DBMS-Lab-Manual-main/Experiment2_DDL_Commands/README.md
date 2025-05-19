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

![image](https://github.com/user-attachments/assets/219bf5e2-9208-4c6f-8229-e1a9c0b2d545)

```sql
CREATE TABLE Orders(
 OrderID INTEGER PRIMARY KEY,
 OrderDate DATE NOT NULL,
 CustomerID INTEGER,
 FOREIGN KEY(CustomerID) REFERENCES CustomerS(CustomerID)
 );
```

**Output:**

![image](https://github.com/user-attachments/assets/6709e358-ded9-4297-b80c-2dd36c2d62dc)

**Question 2**

![image](https://github.com/user-attachments/assets/dcc48243-a82c-41c8-9b34-b26f240bf572)


```sql
CREATE TABLE item(
 item_id TEXT PRIMARY KEY,
 item_desc TEXT NOT NULL,
 rate INTEGER NOT NULL,
 icom_id TEXT CHECK (length(icom_id = 4)),
 FOREIGN KEY (icom_id) REFERENCES company(com_id)
 ON UPDATE CASCADE
 ON DELETE CASCADE
 );
```

**Output:**

![image](https://github.com/user-attachments/assets/a2122bb7-2821-40b5-bba7-3a4f365aada3)

**Question 3**

![image](https://github.com/user-attachments/assets/17220573-306d-44a6-bab5-f2a1b50c420f)


```sql
INSERT INTO Customers (CustomerID, Name,Address,City,ZipCode)
VALUES (302, 'Laura Croft', '456 Elm St','Seattle', 98101);

INSERT INTO Customers (CustomerID, Name,Address,City,ZipCode)
VALUES (303, 'Bruce Wayne', '789 Oak St ','Gotham ', 10001);

```

**Output:**

![image](https://github.com/user-attachments/assets/c9f8889e-0893-46ef-95e8-50fa91250ed6)


**Question 4**

![image](https://github.com/user-attachments/assets/f23ccb5d-4675-4b45-a582-732fe6cfc116)


```sql
CREATE TABLE  Reviews(
    ReviewID  INTEGER,
    ProductID  INTEGER,
    Rating REAL,
    ReviewText TEXT
);
```

**Output:**
![image](https://github.com/user-attachments/assets/7365cb07-a963-4b90-bd7e-5e7cea3cdec9)



**Question 5**
![image](https://github.com/user-attachments/assets/e3b31a9f-99c4-469f-8c95-cc4b85ce6ae4)


```sql
ALTER TABLE employee
ADD COLUMN department_id INTEGER;

ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/ab3f86bd-0580-4a79-b5ab-4f9f28a483da)


**Question 6**

![image](https://github.com/user-attachments/assets/7bd765ab-79f8-4d55-8869-195293bc88f4)

```sql
INSERT INTO Products( ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM Discontinued_products;
```


**Output:**

![image](https://github.com/user-attachments/assets/c6a8d724-84fa-404b-a372-345634603889)


**Question 7**

![image](https://github.com/user-attachments/assets/0535afec-4e16-4ac3-b3b0-fae3d06529e3)


```sql
CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10, 2) NOT NULL,
    discount DECIMAL(10, 2) NOT NULL DEFAULT 0,
    CHECK (list_price >= discount),
    CHECK (discount >= 0),
    CHECK (list_price >= 0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/01b7b738-3e54-4288-8373-d864b6fa6cb2)

**Question 8**

![image](https://github.com/user-attachments/assets/67b2ca3e-6486-472f-97f2-d5f24a91f944)


```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**
![image](https://github.com/user-attachments/assets/88d6a2ed-1baf-4599-8ae6-f11e435e12bd)



**Question 9**

![image](https://github.com/user-attachments/assets/2182ae38-63f6-4014-815f-9b8ae9632a5a)


```sql
CREATE TABLE orders (
    ord_id TEXT NOT NULL CHECK (LENGTH(ord_id) = 4),
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGER,
    cost INTEGER,
    PRIMARY KEY (item_id, ord_date)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/d1092dbf-8484-48a2-b805-9dd8982bc67c)


**Question 10**

![image](https://github.com/user-attachments/assets/4333c8c6-f8a5-495a-af25-bafd3a25e27b)


```sql
INSERT INTO Employee (EmployeeID, Name, Position)
VALUES (4, 'Emily White', 'Analyst');
```

**Output:**

![image](https://github.com/user-attachments/assets/01e7b248-9972-4263-b5e4-4754d0327def)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
