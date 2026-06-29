# Using the Set Operators
## 1. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job, for departments 10, 20, and 30, giving each column an appropriate heading.
```sql
SELECT job_id,
       SUM(CASE WHEN department_id = 10 THEN salary ELSE 0 END) AS "Dept 10",
       SUM(CASE WHEN department_id = 20 THEN salary ELSE 0 END) AS "Dept 20",
       SUM(CASE WHEN department_id = 30 THEN salary ELSE 0 END) AS "Dept 30",
       SUM(salary) AS "Total Salary"
FROM employees
GROUP BY job_id
ORDER BY job_id;
```
## 2. Using set operator display the DEPTNO,SUM(SAL) for each dept,  JOB,SUM(SAL) for each Job and Total Salary.
```sql
SELECT department_id AS deptno,
       NULL AS job,
       SUM(salary) AS total_salary
FROM employees
GROUP BY department_id

UNION

SELECT NULL AS deptno,
       job_id AS job,
       SUM(salary) AS total_salary
FROM employees
GROUP BY job_id

UNION

SELECT NULL AS deptno,
       'TOTAL' AS job,
       SUM(salary) AS total_salary
FROM employees;
```
## 3. Using Set Operator display the JOB and Deptno  in employees working in deptno 20,10,30 in that order.
```sql
SELECT job_id, department_id
FROM employees
WHERE department_id = 20

UNION

SELECT job_id, department_id
FROM employees
WHERE department_id = 10

UNION

SELECT job_id, department_id
FROM employees
WHERE department_id = 30;
```