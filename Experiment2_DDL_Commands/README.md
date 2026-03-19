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

![Question-1](Questions/image-1.png)

```sql
CREATE TABLE Department(
    DepartmentID INT PRIMARY KEY,
    DepartmentName TEXT NOT NULL UNIQUE,
    Location TEXT
);
```

**Output:**

![Output-1](Outputs/image-1.png)

**Question 2**

![Question-2](Questions/image-2.png)

```sql
CREATE TABLE Shipments(
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER NOT NULL,
    OrderID INTEGER NOT NULL,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

![Output-2](Outputs/image-2.png)

**Question 3**

![Question-3](Questions/image-3.png)

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER NOT NULL,
    ProjectID INTEGER NOT NULL,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

![Output-3](Outputs/image-3.png)

**Question 4**

![Question-4](Questions/image-4.png)

```sql
INSERT INTO Customers 
VALUES("301","Michael Jordan","123 Maple St","Chicago",60616);
```

**Output:**

![Output-4](Outputs/image-4.png)

**Question 5**

![Question-5](Questions/image-5.png)

```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL,
    CHECK(LENGTH(phone)>=10)
);
```

**Output:**

![Output-5](Outputs/image-5.png)

**Question 6**

![Question-6](Questions/image-6.png)

```sql
CREATE TABLE orders(
    ord_id TEXT NOT NULL,
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGER,
    cost INTEGER,
    PRIMARY KEy(item_id,ord_date)
    CHECK(LENGTH(ord_id)=4)
);
```

**Output:**

![Output-6](Outputs/image-6.png)

**Question 7**

![Question-7](Questions/image-7.png)

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;

ALTER TABLE Companies ADD COLUMN mobilenumber number;

ALTER TABLE Companies ADD COLUMN DOB Date;

ALTER TABLE Companies ADD COLUMN State varchar(30);
```

**Output:**

![Output-7](Outputs/image-7.png)

**Question 8**

![Question-8](Questions/image-8.png)

```sql
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

![Output-8](Outputs/image-8.png)

**Question 9**

![Question-9](Questions/image-9.png)


```sql
INSERT INTO Student_details
SELECT * FROM Archived_students;
```

**Output:**

![Output-9](Outputs/image-9.png)

**Question 10**

![Question-10](Questions/image-10.png)

```sql
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES("001","Sarah Parker","Manager","HR",60000);
```

**Output:**

![Output-10](Outputs/image-10.png)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
