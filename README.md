# SQL


-- --1 JOIN TABLES
SELECT employees.emp_no, employees.first_name, employees.last_name, employees.gender, salaries.salary, salaries.from_date
FROM salaries
LEFT JOIN employees
ON employees.emp_no=salaries.emp_no;

-- -- 2 LIMIT BY DATE
SELECT hire_date
FROM employees
WHERE hire_date BETWEEN '1986-01-01' AND '1987-01-01';

--3. Manager Information
SELECT manager.emp_no, employees.first_name, employees.last_name, department.dept_no, department.dept_name, manager.emp_no, manager.from_date, manager.to_date
FROM department
LEFT JOIN manager
ON manager.dept_no=department.dept_no
JOIN employees
ON manager.emp_no=employees.emp_no;


--4. Employee/dept
SELECT department.dept_name, employees.first_name, employees.last_name, employees.emp_no, dept_emp.emp_no
FROM dept_emp
LEFT JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN department
ON dept_emp.dept_no=department.dept_no;

--5. Finding Hercules
SELECT employees.first_name, employees.last_name
FROM employees
WHere first_name='Hercules'
AND last_name LIKE '%B%';

--6. Mr and Ms Sales
SELECT employees.first_name, employees.last_name, dept_emp.emp_no, department.dept_name
FROM dept_emp
LEFT JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN department
ON dept_emp.dept_no=department.dept_no
WHERE department.dept_no='d007';

--7. THe ultimate battle between sales and dev
SELECT employees.first_name, employees.last_name, dept_emp.emp_no, department.dept_name
FROM dept_emp
LEFT JOIN employees
ON dept_emp.emp_no=employees.emp_no
JOIN department
ON dept_emp.dept_no=department.dept_no
WHERE department.dept_no='d007' 
OR department.dept_no='d005';

--8. the family tree
SELECT last_name,
COUNT(last_name) AS "frequency"
FROM employees
GROUP BY last_name
ORDER BY
COUNT(last_name) DESC;
