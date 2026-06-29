# Reporting Aggregated Data Using the Group Functions
## 1. Find the highest, lowest, sum, and average salary of all employees. Label the columns
```sql
select max(salary) as "Highest Salary", min(salary) as "Lowest Salary", sum(salary) as "Sum of Salaries", avg(salary) as "Average Salary" from employees;
```
## 2. Maximum, Minimum, Sum, and Average, respectively. Round your results to the nearest whole number.
```sql
select ROUND(max(salary)) as "Highest Salary", ROUND(min(salary)) as "Lowest Salary", ROUND(sum(salary)) as "Sum of Salaries", ROUND(avg(salary)) as "Average Salary" from employees;
```
## 3. Modify the above query to display the minimum, maximum, sum, and average salary for each job type.
```sql
select job_id, ROUND(max(salary)) as "Highest Salary", ROUND(min(salary)) as "Lowest Salary", ROUND(sum(salary)) as "Sum of Salaries", ROUND(avg(salary)) as "Average Salary" from employees group by job_id;
```
## 4.  Write a query to display the number of people with the same job
```sql
select job_id, count(employee_id) from employees group by job_id;
```
## 5. Determine the number of managers without listing them. Label the column Number of Managers
```sql
select count(manager_id) as "Number of Managers" from employees;
```
## 6. Find the difference between the highest and lowest salaries. Label the column DIFFERENCE.
```sql
select max(salary) - min(salary) as difference from employees;
```
## 7. Create a report to display the manager number and the salary of the lowest-paid employee for that manager. Exclude anyone whose manager is not known. Exclude any groups where the minimum salary is $2000 or less. Sort the output in descending order of salary.
```sql
SELECT manager_id,
       MIN(salary) AS lowest_salary
FROM employees
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) > 2000
ORDER BY lowest_salary DESC;
```
## 8. Create a query to display the total number of employees and, of that total, the number of employees hired in 1980, 1981, and 1982. Create appropriate column headings.
```sql
SELECT COUNT(*) AS "Total Employees",
       COUNT(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1980 THEN 1 END) AS "Total Employees hired in 1980",
       COUNT(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1981 THEN 1 END) AS "Total Employees hired in 1981",
       COUNT(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1982 THEN 1 END) AS "Total Employees hired in 1982"
FROM employees;
```
