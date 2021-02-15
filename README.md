# sql-challenge

1) Created, cloned, set up and pushed updates to repository - sql-challenge on GitHub

2) Inspected CSVs and sketched out ERD of each csv table
	- sql-challenge/EmployeeSQL/ERD_Employee_Database.png and 
	- sql-challenge/EmployeeSQL/ERD_Employee_Database.sql

3) Created tables based on ERD in the Employee_DB database using PostreSQL
	- sql-challenge/EmployeeSQL/Create_Tables.sql

4) Performed the following queries using PGAdmin, PostreSQL:

	- sql-challenge/EmployeeSQL/Queries.sql

	1. List the following details of each employee: employee number, 		last name, first name, sex, and salary.

	- sql-challenge/EmployeeSQL/output/employee_list.csv

	- Joined (inner join) the employees and salaries table - one to 			one relationship

	2. List first name, last name, and hire date for employees who 	were hired in 1986.

	- sql-challenge/EmployeeSQL/output/employees_hired_in_1986.csv

	- All information in employees table, queried on employees that 			had a hire date in 1986 (Like '%1986')

	3. List the manager of each department with the following 	information: department number, department name, the manager's 	employee number, last name, first name.

	- sql-challenge/EmployeeSQL/output/department_managers_list.csv

	- Joined the dept_manager table to the departments table and then 		to the employees table.  Note that there are multiple 				managers for each department.  

	4. List the department of each employee with the following 	information: employee number, last name, first name, and 	department name.

	- sql-challenge/EmployeeSQL/output/department_employees_list.csv

	- Joined the employees table to the dept_emp table and the to the 		departments table.  Note that since some employees are 			assigned to multiple departments, some employees were listed 		more than once.

	- Created a department_employees_view from this query to be used 		for item 6 and 7 below

	5. List first name, last name, and sex for employees whose first 	name is "Hercules" and last names begin with "B."

	- sql-challenge/EmployeeSQL/output/employees_hercules_b.csv

	- All information in this query was in the employee table.  			Noted that there were a surprising number of employees with 			the first name Hercules and the last name beginning with 			"B".  Also noted that both males and females were named 			Hercules which is traditionally (but not necessarily always) 		a male name.  

	6. List all employees in the Sales department, including their 	employee number, last name, first name, and department name.

	- sql-challenge/EmployeeSQL/output/sales_employees.csv

	- Used the department_employees_view created in item 4 above for 			this query.  Queried on the dept_name column for sales 			employees

	7. List all employees in the Sales and Development departments, 	including their employee number, last name, first name, and 	department name.

	- sql-challenge/EmployeeSQL/output/
					sales_and_development_employees.csv

	- Used the department_employees_view created in item 4 above for 			this query.  Queried on the dept_name column for sales and 		development employees

	8. In descending order, list the frequency count of employee last 	names, i.e., how many employees share each last name.

	- sql-challenge/EmployeeSQL/output/employee_name_count.csv

	- Used the employees table, grouped by last_name, counted emp_no 			and ordered the results in descending order.  It was 				surprising to see that with 30,024 employees that there were 		only 1,638 unique last names. 

Observations:

As noted above, the queries produced some suspicious results.

When querying on the first name Hercules and last names beginning with the letter "B", I Noted that there were a surprising number of employees with the first name Hercules and the last name beginning with "B".  Also noted that both males and females were named Hercules which is traditionally (but not necessarily always) a male name.  

When counting unique last names, I was surprised to see that with 30,024 employees that there were only 1,638 unique last names. 





 


