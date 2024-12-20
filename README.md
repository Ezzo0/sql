# CREATE TABLE
```
CREATE TABLE employees (
    employee_id NUMBER GENERATED CONSTRAINT pk_val PRIMARY KEY,
    first_name VARCHAR2(50) NOT NULL,
    last_name VARCHAR2(50) NOT NULL,
    email VARCHAR2(100) UNIQUE NOT NULL,
    phone_number VARCHAR2(15),
    hire_date DATE DEFAULT SYSDATE,
    salary NUMBER(8, 2) CHECK (salary >= 0),
    department_id NUMBER,
    CONSTRAINT fk_department
        FOREIGN KEY (department_id) REFERENCES departments (department_id)
	ON DELETE CASCADE || ON DELETE SET NULL
);
```
# Create table using subquery
```
CREATE TABLE high_salary_employees AS
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 60000;
```
# Inserting Data
```
INSERT INTO employees (employee_id, first_name, last_name, salary)
VALUES (101, 'John', 'Doe', 55000);
```

# UPDATE
```
UPDATE employees
SET 
    first_name = 'John',
    last_name = 'Doe',
WHERE employee_id = 1;
```
# DELETE FROM
```
DELETE FROM employees
WHERE department_id = 2;
```
# Adding a New Column
```
ALTER TABLE employees
ADD birth_date DATE;
```
# Modifying an Existing Column
```
ALTER TABLE employees
MODIFY salary NUMBER(10, 2) NOT NULL;
```
# Dropping a Column
```
ALTER TABLE employees
DROP COLUMN phone_number;
```
# Renaming a Column
```
ALTER TABLE employees
RENAME COLUMN last_name TO surname;
```
# Adding a Constraint
```
ALTER TABLE employees
ADD CONSTRAINT fk_department
FOREIGN KEY (department_id) REFERENCES departments (department_id);
```
# Dropping a Constraint
```
ALTER TABLE employees
DROP CONSTRAINT fk_department;
```
# Drop table
```
DROP TABLE table_name;
OR
DROP TABLE employees CASCADE CONSTRAINTS;
```
# Create View
```
CREATE VIEW high_salary_employees AS
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 60000;
WITH CHECK OPTION CONSTRAINT constraint_name;
```
# Describe the striucture of a view
```
DESCRIBE high_salary_employees;
```
# Modifing a view
```
CREATE OR REPLACE VIEW high_salary_employees AS
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 50000;
```
# Denying DML Operations
```
CREATE VIEW high_salary_employees AS
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 50000;
WITH READ ONLY
```

# Removing a View
```
DROP VIEW high_salary_employees
```
