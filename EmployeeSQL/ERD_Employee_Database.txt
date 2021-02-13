ERD_Employee_Database
-
titles
-
title_id VARCHAR PK
title VARCHAR
# 7 unique emp_title_id


departments
-
dept_no VARCHAR PK
dept_name VARCHAR
# 9 unique dept_no

employees
-
emp_no INTEGER PK 
emp_title_id VARCHAR FK >- titles.title_id
birth_date VARCHAR
first_name VARCHAR
last_name VARCHAR
sex VARCHAR
hire_date VARCHAR
# 30024 unique emp_no
# 7 unique emp_title_id, all emp_no have an emp_title_id

salaries
-
emp_no INTEGER FK - employees.emp_no
salary INTEGER
(emp_no, salary) PK
# 30024 unique emp_no


dept_emp
-
emp_no INTEGER FK >- employees.emp_no 
dept_no VARCHAR FK >- departments.dept_no
(emp_no, dept_no) PK
# 331603 non-unique emp_no rows (emp_no can be assigned multiple dept_no)
# 30024 unique emp_no, all rows are assigned an emp_no
# 9 unique dept_no, all emp_no have a dept_no


dept_manager
-
dept_no VARCHAR FK >- departments.dept_no
emp_no INTEGER FK - employees.emp_no
(dept_no, emp_no) PK
# 9 unique dept_no, each row is assigned a dept_no
# 24 unique emp_no (a department may be assigned multiple dept_manager)






