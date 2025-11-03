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

<img width="832" height="392" alt="image" src="https://github.com/user-attachments/assets/5fa2ae47-5cbb-460b-b0d7-78dbf3866015" />

```
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department,Salary
FROM Former_employees;
```
**Output:**

<img width="1116" height="313" alt="image" src="https://github.com/user-attachments/assets/ec00753d-9750-40a1-95b8-93b96457ad20" />


**Question 2**

<img width="905" height="227" alt="image" src="https://github.com/user-attachments/assets/f440c33e-ff8d-4a25-b299-3dae14e5e124" />

```
CREATE TABLE Bonuses  (
            BonusID INTEGER PRIMARY KEY,
            EmployeeID INTEGER,
            BonusAmount REAL CHECK (BonusAmount > 0),
            BonusDate DATE,
            Reason TEXT NOT NULL,
            FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID))
```
**Output:**

<img width="1138" height="318" alt="image" src="https://github.com/user-attachments/assets/4c4e845d-0271-4589-b6f8-490222e13572" />

**Question 3**

<img width="1130" height="258" alt="image" src="https://github.com/user-attachments/assets/329cd313-66a3-4531-ae0b-2cab432d6abd" />

```
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)
VALUES (1,'Sarah Parker','Manager','HR',60000);
```

**Output:**

<img width="1138" height="318" alt="image" src="https://github.com/user-attachments/assets/378a8e72-ddea-417a-a21c-dafa68757530" />


**Question 4**

<img width="1123" height="369" alt="image" src="https://github.com/user-attachments/assets/429e18e4-391d-460a-b34f-890df3adbd8f" />


```
CREATE TABLE Departments (DepartmentID INTEGER, DepartmentName TEXT);

```
**Output:**

<img width="1127" height="356" alt="image" src="https://github.com/user-attachments/assets/16667e1c-be92-452d-a405-7d41cce7aa8c" />

**Question 5**

<img width="1044" height="506" alt="image" src="https://github.com/user-attachments/assets/2a89cfa1-1a53-4d02-bc4b-f12a4fd09730" />


```

INSERT INTO  Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (202, 'Ella King', 'F', 'Chemistry', 87),
       (203, 'James Bond', 'M', 'Literature', 78);
```

**Output:**

<img width="1113" height="256" alt="image" src="https://github.com/user-attachments/assets/17caaadf-bc17-45df-89a7-4ab7040b7630" />


**Question 6**

<img width="919" height="161" alt="image" src="https://github.com/user-attachments/assets/2a75b9bb-202a-4015-8841-4f0260a33cea" />


```

CREATE TABLE Orders (
        OrderID INTEGER PRIMARY KEY,
        OrderDate DATE NOT NULL,
        CustomerID INTEGER,
        FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID));
```
**Output:**

<img width="1111" height="262" alt="image" src="https://github.com/user-attachments/assets/452ea455-5597-4dcd-a422-bce44c57217d" />


**Question 7**

<img width="1114" height="456" alt="image" src="https://github.com/user-attachments/assets/fa57920d-ca93-4bfe-88dd-d95bfe911598" />

```
ALTER TABLE employee ADD COLUMN department_id INTEGER;
ALTER TABLE employee ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1102" height="271" alt="image" src="https://github.com/user-attachments/assets/a4d51e4b-0cb9-4a1b-aaa0-485db7049f82" />


**Question 8**

<img width="915" height="204" alt="image" src="https://github.com/user-attachments/assets/889a4362-981a-4f4b-9c9d-091414d366c1" />

```

CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

<img width="1122" height="247" alt="image" src="https://github.com/user-attachments/assets/3c8bce6d-c523-40a0-9dae-4432f363b98a" />


**Question 9**

<img width="1118" height="384" alt="image" src="https://github.com/user-attachments/assets/60c519e5-0175-4146-9188-a209d3a38c79" />

```

ALTER TABLE Student_details
ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="1115" height="325" alt="image" src="https://github.com/user-attachments/assets/60301651-e526-4587-951f-6120b4c5e4aa" />


**Question 10**
<img width="770" height="289" alt="image" src="https://github.com/user-attachments/assets/643492db-0e1f-46ff-aea8-9f44c3959ad9" />

```
CREATE TABLE orders (
        ord_id TEXT NOT NULL CHECK (length(ord_id) = 4),
        item_id TEXT NOT NULL,
        ord_date DATE NOT NULL,
        ord_qty INTEGER,
        cost INTEGER,
        PRIMARY KEY (item_id,ord_date)
        );
```

**Output:**

<img width="1117" height="308" alt="image" src="https://github.com/user-attachments/assets/8ca1f00e-df89-4240-994d-cfb7bbb7934c" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
