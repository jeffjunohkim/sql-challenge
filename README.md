# sql-challenge

## Overview
It’s been two weeks since you were hired as a new data engineer at Pewlett Hackard (a fictional company). Your first major task is to do a research project about people whom the company employed during the 1980s and 1990s. All that remains of the employee database from that period are six CSV files.

## Data Modeling/Engineering
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

### Schemata Summary
- Titles: title_id is a unique primary key.
- Departments: dept_no is a unique primary key.
- Employees: emp_no is a unique primary key.
- Salaries: Composite key on emp_no and salary_date ensures that each salary entry is unique for each employee at a given time.
- Dept_emp: Composite key on emp_no and dept_no ensures that each employee-department relationship is unique.
- Dept_manager: Composite key on dept_no and emp_no ensures that each department-manager relationship is unique.

### Relationships
- Each employee is associated with a title and can have multiple salary records.
- Employees can work in multiple departments over time (recorded in dept_emp).
- Departments can have multiple managers over time (recorded in dept_manager).
- Departments and titles are independent entities with their own primary keys.

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
