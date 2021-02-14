 Queries
 
-- 1. List the following details of each employee: employee number, 		
-- 		last name, first name, sex, and salary.

SELECT e.emp_no, e.last_name, e.first_name, e.sex, s.salary
FROM employees AS e
JOIN salaries AS s
ON (e.emp_no = s.emp_no)

-- Save to CSV
COPY(
SELECT e.emp_no, e.last_name, e.first_name, e.sex, s.salary
FROM employees AS e
JOIN salaries AS s
ON (e.emp_no = s.emp_no)
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/employee_list.csv' DELIMITER ',' CSV HEADER
;

-- 2. List first name, last name, and hire date for 
-- 		employees who were hired in 1986.

SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date LIKE '%1986'

-- Save to CSV
COPY(
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date LIKE '%1986'
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/employees_hired_in_1986.csv' DELIMITER ',' CSV HEADER
;

-- 3. List the manager of each department with the 
--		following information: department number, department 
-- 		name, the manager's employee number, last name, first name.

-- Tables/Columns 
-- 	dept_manager (m) (dept_no, emp_no), 
-- 	departments (d)(dept_no, dept_name), 
--	employees (e) (emp_no, first_name, last_name)

SELECT m.dept_no, d.dept_name, m.emp_no, e.last_name, e.first_name
FROM dept_manager AS m
JOIN departments AS d
ON (m.dept_no = d.dept_no)
JOIN employees AS e
ON (m.emp_no = e.emp_no)

-- Save to CSV
COPY(
SELECT m.dept_no, d.dept_name, m.emp_no, e.last_name, e.first_name
FROM dept_manager AS m
JOIN departments AS d
ON (m.dept_no = d.dept_no)
--FROM dept_manager AS m
JOIN employees AS e
ON (m.emp_no = e.emp_no)
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/department_managers_list.csv' DELIMITER ',' CSV HEADER
;

-- 4. List the department of each employee with the following 
-- 		information: employee number, last name, first name, 
--		and department name.

-- Tables/Columns 
-- 	dept_emp (z) (dept_no, emp_no), 
-- 	departments (d)(dept_no, dept_name), 
--	employees (e) (emp_no, first_name, last_name)
-- 	Note: some employees are in more than one department

SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM employees AS e
JOIN dept_emp AS z
ON (e.emp_no = z.emp_no)
JOIN departments AS d
ON (z.dept_no = d.dept_no)

-- Save to CSV
COPY(
SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM employees AS e
JOIN dept_emp AS z
ON (e.emp_no = z.emp_no)
JOIN departments AS d
ON (z.dept_no = d.dept_no)
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/department_employees_list.csv' DELIMITER ',' CSV HEADER
;
 -- Create View to use for #6
CREATE VIEW department_employees_view AS
SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM employees AS e
JOIN dept_emp AS z
ON (e.emp_no = z.emp_no)
JOIN departments AS d
ON (z.dept_no = d.dept_no)

-- 5. List first name, last name, and sex for employees whose 
-- 		first name is "Hercules" and last names begin with "B."

-- Tables/Columns 
-- 	employees (e) (first_name, last_name,sex)

SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE 'B%';

-- Save to CSV
COPY(
SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE 'B%'
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/employees_hercules_b.csv' DELIMITER ',' CSV HEADER
;

-- 6. List all employees in the Sales department, including their 
-- 		employee number, last name, first name, and department name.

-- use department_employees_view created in #4 above

SELECT *
FROM department_employees_view
WHERE dept_name = 'Sales';

-- Save to CSV
COPY(
SELECT *
FROM department_employees_view
WHERE dept_name = 'Sales'
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/sales_employees.csv' DELIMITER ',' CSV HEADER
;

-- 7. List all employees in the Sales and Development departments, 
-- 		including their employee number, last name, first name, 
-- 		and department name.

SELECT *
FROM department_employees_view
WHERE dept_name = 'Sales'OR dept_name = 'Development';

-- Save to CSV
COPY(
SELECT *
FROM department_employees_view
WHERE dept_name = 'Sales' OR dept_name = 'Development'
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/sales_and_development_employees.csv' DELIMITER ',' CSV HEADER
;


-- 8. In descending order, list the frequency count of employee last 
-- 		names, i.e., how many employees share each last name.

SELECT last_name, COUNT(emp_no) AS "#_of_Emps"
FROM employees
GROUP BY last_name
ORDER BY "#_of_Emps" DESC

-- Save to CSV
COPY(
SELECT last_name, COUNT(emp_no) AS "#_of_Emps"
FROM employees
GROUP BY last_name
ORDER BY "#_of_Emps" DESC
)
TO 'c:/Chris/Butler_Homework/Week_9/sql-challenge/EmployeeSQL/output/employee_name_count.csv' DELIMITER ',' CSV HEADER
;