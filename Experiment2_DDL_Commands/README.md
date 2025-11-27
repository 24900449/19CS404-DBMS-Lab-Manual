<img width="1075" height="454" alt="438542685-c8c69844-81cf-4cf9-8eba-a0b0d0bb6701" src="https://github.com/user-attachments/assets/21add323-8fb6-43d7-8850-f4e8fef3ccf4" />Experiment 2: DDL Commands
AIM
To study and implement DDL commands and different types of constraints.

THEORY
1. CREATE
Used to create a new relation (table).

Syntax:
```
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
2. ALTER
Used to add, modify, drop, or rename fields in an existing relation. (a) ADD
```
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP

ALTER TABLE relation_name DROP COLUMN field_name;
(d) RENAME
```
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```

3. DROP TABLE
Used to permanently delete the structure and data of a table.
```
DROP TABLE relation_name;
```
4. RENAME
Used to rename an existing database object.
```
RENAME TABLE old_relation_name TO new_relation_name;
```

CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).

1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
2. UNIQUE
Ensures that values in a column are unique. Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```

3. CHECK
Specifies a condition that each row must satisfy. Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
4. PRIMARY KEY
Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields. Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
5. FOREIGN KEY
Used to reference the primary key of another table. Syntax:
```
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```
Question 1

<img width="1187" height="307" alt="438551416-1ff73ec5-f6a1-4e70-9010-161c6f3772f6" src="https://github.com/user-attachments/assets/4c2e2830-f78b-47da-88a1-3f87ad807c73" />
```
--
INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
Output: Screenshot 2025-04-29 124245
```
output:

<img width="1253" height="175" alt="438616641-89435e54-9c59-4711-bc20-d0f6f9f6e311" src="https://github.com/user-attachments/assets/b081a69f-319b-46bd-b728-5aa49a60be78" />


Question 2
```
-- 
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
```
Output:

<img width="1247" height="382" alt="438539788-c39daf8f-3430-4210-a8ff-d01b24a63277" src="https://github.com/user-attachments/assets/c0af17d7-0db9-4204-8e25-e8b15f682371" />


Question 3

<img width="1140" height="358" alt="438542915-dae1d226-9026-4d29-9254-7de0910c737f" src="https://github.com/user-attachments/assets/72a77871-5432-4f42-b905-844c360a165e" />
```

--
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;
```

Output:

<img width="1220" height="415" alt="438540080-34ffec3a-d6f4-4db9-a215-4b0e07cf2498" src="https://github.com/user-attachments/assets/f67a9975-263d-4791-a12b-cb16ff3a2c53" />


Question 4

<img width="1394" height="349" alt="438542847-5269cf0c-35ef-423a-8f4d-e23d598326c0" src="https://github.com/user-attachments/assets/37280aa2-e0f5-4154-89f5-6ff9446c1119" />

```
--
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
```
Output: 

<img width="1252" height="434" alt="438540313-6ac5521f-2c29-4742-8243-8b4e41797c86" src="https://github.com/user-attachments/assets/4f779807-2923-4285-bbca-8fed40ec1720" />

Question 5

<img width="1485" height="381" alt="438542784-df2640c1-2236-4197-a730-8d3801cdb17b" src="https://github.com/user-attachments/assets/fbaec1bb-490b-4839-b17a-a294d183d4a3" />
```
--
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```
Output:

<img width="1236" height="442" alt="438540767-455829b4-4134-45de-b480-5692c256072d" src="https://github.com/user-attachments/assets/07fb3aa2-850f-42f7-94f2-8b43e580b4ed" />


Question 6

<img width="1063" height="350" alt="438542740-9e2758a1-6ee5-4c45-8061-abac41022770" src="https://github.com/user-attachments/assets/d921eef1-f0ce-4e73-b8f5-a37afdcd124c" />
```
--
select *from Out_of_print_books
union all
select *from Books

```
Output: 

<img width="1229" height="380" alt="438541479-151cdda8-17c8-4153-9df3-34567f3eaa0f" src="https://github.com/user-attachments/assets/ec111ca2-a25b-4356-a3e3-dff20a8fbaa2" />


Question 7

<img width="1075" height="454" alt="438542685-c8c69844-81cf-4cf9-8eba-a0b0d0bb6701" src="https://github.com/user-attachments/assets/ac44fdbb-6404-4552-930e-df206ded729d" />


```
--
CREATE TABLE item (  
    item_id TEXT PRIMARY KEY,  
    item_desc TEXT NOT NULL,  
    rate INTEGER NOT NULL,  
    icom_id TEXT CHECK(4),  
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    ON UPDATE CASCADE  
    ON DELETE CASCADE  
);
```
Output: 

<img width="1236" height="438" alt="438541764-4880a2ef-a33b-4cc3-b31c-216f255b2b67" src="https://github.com/user-attachments/assets/ce7e3128-bea9-4cfe-8a61-56e73c076679" />


Question 8

<img width="1099" height="297" alt="438542632-7096c7b2-8067-45fb-95ce-c61bec119446" src="https://github.com/user-attachments/assets/7a37a46d-63d9-476f-a4db-d1c1d6b7499e" />
```
--
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```
Output:

<img width="1242" height="375" alt="438542140-0f2267dc-bc94-49e4-84e3-2a143335f3cf" src="https://github.com/user-attachments/assets/49486826-6e5e-4728-879c-f17712c043aa" />


Question 9

<img width="1243" height="289" alt="438542206-06d2e58d-4853-4ba5-9d54-f03e0c410af6" src="htt  ps://github.com/user-attachments/assets/d3ac9a2d-86a8-4537-bda9-5bc07624745a" />
```
--
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
```
Output:

<img width="1270" height="326" alt="438542302-439c6599-0b13-49c7-95a4-3d53ecfde7bc" src="https://github.com/user-attachments/assets/08a0dd2c-108e-4c2a-bb80-c84a0f2134de" />

Question 10

```
--
CREATE TABLE Employees(
EmployeeID INTEGER primary key,
FirstName INTEGER NOT NULL,
LastName INTEGER NOT NULL,
Email VARCHAR(50) unique,
Salary CHECK (Salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references Departments(DepartmentID)
);
```
Output: 

<img width="1234" height="488" alt="438543486-8631abbc-db12-4fe7-bbf9-06bffaa06c5a" src="https://github.com/user-attachments/assets/9aa1b908-2ab7-4049-86a7-20e899916c40" />

RESULT

Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.


