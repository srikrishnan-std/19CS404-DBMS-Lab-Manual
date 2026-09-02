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
--
```
CREATE TABLE STUDENT (
    STUDENT_ID NUMBER(5),
    NAME VARCHAR2(30),
    DEPARTMENT VARCHAR2(20),
    MARKS NUMBER(3)
);

DESC STUDENT;
```

**Output:**

<img width="398" height="197" alt="{58AB363A-863B-40FF-ADB5-01C5318B4DE9}" src="https://github.com/user-attachments/assets/53b1ba66-ecf1-40fb-b546-0be457479753" />


**Question 2**
---
```
ALTER TABLE STUDENT
ADD (ADDRESS VARCHAR2(30));

DESC STUDENT;
```
**Output:**

<img width="338" height="192" alt="{E734C350-CDAA-4CBE-888A-589DE5790BCD}" src="https://github.com/user-attachments/assets/2ae352bc-e955-4633-8153-684de979c064" />


**Question 3**
---
```
ALTER TABLE STUDENT
MODIFY (NAME VARCHAR2(50));

DESC STUDENT;
```

**Output:**

<img width="314" height="212" alt="{FB3A5471-7CA8-4080-BFD4-0E37D19CF263}" src="https://github.com/user-attachments/assets/d957d751-efab-4ae8-a919-22e1aabdb325" />

**Question 4**
---
```
ALTER TABLE STUDENT
DROP COLUMN ADDRESS;

DESC STUDENT;
```

**Output:**

<img width="291" height="184" alt="{5D392C9B-64AB-4CB1-A35E-29E39E86A1D6}" src="https://github.com/user-attachments/assets/d48fbc41-c2e2-4921-be98-3576d4e90694" />

**Question 5**
---
```
ALTER TABLE STUDENT
RENAME COLUMN NAME TO STUDENT_NAME;

DESC STUDENT;
```

**Output:**

<img width="314" height="211" alt="{8DC3A23B-6CA3-4681-B864-DB1F8189B7C0}" src="https://github.com/user-attachments/assets/b791c179-e229-4c05-9b06-86e433865ef5" />


**Question 6**
---
```
CREATE TABLE EMPLOYEE (
    EMP_ID NUMBER(5) PRIMARY KEY,
    EMP_NAME VARCHAR2(30) NOT NULL,
    SALARY NUMBER(8,2)
);

DESC EMPLOYEE;
```

**Output:**

<img width="972" height="377" alt="image" src="https://github.com/user-attachments/assets/15ed40b5-588f-4fc6-b743-93e768f73d2d" />


**Question 7**
---
```
CREATE TABLE COURSE (
    COURSE_ID NUMBER(5) PRIMARY KEY,
    COURSE_NAME VARCHAR2(30) UNIQUE,
    DURATION NUMBER(2) CHECK (DURATION > 0)
);

DESC COURSE;
INSERT INTO COURSE VALUES (101, 'Python', 6);
INSERT INTO COURSE VALUES (102, 'Java', 4);

SELECT * FROM COURSE;
```

**Output:**
<img width="992" height="352" alt="image" src="https://github.com/user-attachments/assets/e5c950e4-7582-4f7c-863c-ffcad34c88ac" />

**Question 8**
---
```
CREATE TABLE DEPARTMENT (
    DEPT_ID NUMBER(3) PRIMARY KEY,
    DEPT_NAME VARCHAR2(30)
);

CREATE TABLE STUDENT_DEPT (
    STUDENT_ID NUMBER(5) PRIMARY KEY,
    STUDENT_NAME VARCHAR2(30),
    DEPT_ID NUMBER(3),
    FOREIGN KEY (DEPT_ID) REFERENCES DEPARTMENT(DEPT_ID)
);

DESC STUDENT_DEPT;
```

**Output:**
<img width="932" height="392" alt="image" src="https://github.com/user-attachments/assets/dee7670f-d1bc-4f71-8a4f-b623e2f9493f" />

**Question 9**
---
```
CREATE TABLE CUSTOMER (
    CUSTOMER_ID NUMBER(5) PRIMARY KEY,
    CUSTOMER_NAME VARCHAR2(30) NOT NULL,
    CITY VARCHAR2(20) DEFAULT 'Chennai'
);

INSERT INTO CUSTOMER (CUSTOMER_ID, CUSTOMER_NAME)
VALUES (101, 'Ravi');

SELECT * FROM CUSTOMER;
```

**Output:**
<img width="992" height="417" alt="image" src="https://github.com/user-attachments/assets/85f267e3-3043-47b4-99c7-ba699d6cf08a" />

**Question 10**
---
```
CREATE TABLE TEMP_STUDENT (
    ID NUMBER(5),
    NAME VARCHAR2(30)
);

RENAME TEMP_STUDENT TO STUDENT_DETAILS;

DESC STUDENT_DETAILS;

DROP TABLE STUDENT_DETAILS;
```

**Output:**

<img width="962" height="392" alt="image" src="https://github.com/user-attachments/assets/acd6528f-8bc8-4937-b1cb-964e194881d9" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
