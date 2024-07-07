# sql-challenge

## Overview
It’s been two weeks since you were hired as a new data engineer at Pewlett Hackard (a fictional company). Your first major task is to do a research project about people whom the company employed during the 1980s and 1990s. All that remains of the employee database from that period are six CSV files.

## Data Modeling
The Entity Relationship Diagram (ERD) outlines the relationships between different entities in the employee database. The primary entities include employees, departments, titles, salaries, department-employee relationships, and department-manager relationships.

### ERD Structure

- **employees**
  - emp_no (Primary Key)
  - emp_title_id (Foreign Key to titles)
  - birth_date
  - first_name
  - last_name
  - sex
  - hire_date

- **titles**
  - title_id (Primary Key)
  - title

- **departments**
  - dept_no (Primary Key)
  - dept_name

- **salaries**
  - emp_no (Primary Key, Foreign Key to employees)
  - salary

- **dept_emp**
  - emp_no (Primary Key, Foreign Key to employees)
  - dept_no (Primary Key, Foreign Key to departments)

- **dept_manager**
  - dept_no (Primary Key, Foreign Key to departments)
  - emp_no (Primary Key, Foreign Key to employees)

### Relationships
- Each employee is associated with a title and can have multiple salary records.
- Employees can work in multiple departments over time (recorded in dept_emp).
- Departments can have multiple managers over time (recorded in dept_manager).
- Departments and titles are independent entities with their own primary keys.

## Data Engineering
The table schemata define the structure of the tables in the database, including primary keys, foreign keys, and constraints.

### SQL Code to Create Tables
```sql
-- Creating the titles table
CREATE TABLE titles (
    title_id CHAR(5) PRIMARY KEY,
    title VARCHAR(40)
);

-- Creating the departments table
CREATE TABLE departments (
    dept_no CHAR(4) PRIMARY KEY,
    dept_name VARCHAR(40)
);

-- Creating the employees table
CREATE TABLE employees (
    emp_no INT PRIMARY KEY,
    emp_title_id CHAR(5),
    birth_date DATE,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    sex CHAR(1),
    hire_date DATE,
    FOREIGN KEY (emp_title_id) REFERENCES titles(title_id)
);

-- Creating the salaries table
CREATE TABLE salaries (
    emp_no INT,
    salary INT,
    PRIMARY KEY (emp_no, salary),
    FOREIGN KEY (emp_no) REFERENCES employees(emp_no)
);

-- Creating the dept_emp table
CREATE TABLE dept_emp (
    emp_no INT,
    dept_no CHAR(4),
    PRIMARY KEY (emp_no, dept_no),
    FOREIGN KEY (emp_no) REFERENCES employees(emp_no),
    FOREIGN KEY (dept_no) REFERENCES departments(dept_no)
);

-- Creating the dept_manager table
CREATE TABLE dept_manager (
    dept_no CHAR(4),
    emp_no INT,
    PRIMARY KEY (dept_no, emp_no),
    FOREIGN KEY (dept_no) REFERENCES departments(dept_no),
    FOREIGN KEY (emp_no) REFERENCES employees(emp_no)
);

## Data Analysis
The following SQL queries were used to perform data analysis:

- **List the employee number, last name, first name, sex, and salary of each employee:**
  - Retrieves the employee number, last name, first name, sex, and salary of each employee.

- **List the first name, last name, and hire date for the employees who were hired in 1986:**
  - Retrieves the first name, last name, and hire date of employees who were hired in 1986.

- **List the manager of each department along with their department number, department name, employee number, last name, and first name:**
  - Lists the manager of each department along with their department number, department name, employee number, last name, and first name.

- **List the department number for each employee along with that employee’s employee number, last name, first name, and department name:**
  - Lists the department number for each employee along with that employee’s employee number, last name, first name, and department name.

- **List first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B:**
  - Retrieves the first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B.

- **List each employee in the Sales department, including their employee number, last name, and first name:**
  - Lists each employee in the Sales department, including their employee number, last name, and first name.

- **List each employee in the Sales and Development departments, including their employee number, last name, first name, and department name:**
  - Lists each employee in the Sales and Development departments, including their employee number, last name, first name, and department name.

- **List the frequency counts, in descending order, of all the employee last names:**
  - Lists the frequency counts, in descending order, of all employee last names to see how many employees share each last name.


## Code Source
- Learning Assistant
- GitHub location: https://github.com/jeffjunohkim/sql-challenge.git
