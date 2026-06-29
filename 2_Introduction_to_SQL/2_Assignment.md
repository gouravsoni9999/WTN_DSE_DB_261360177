# Restricting and Storing Data
## 1.  Display the Ename,Sal,Comm from Emp table who earn commission and sort the records in descending order of Salary and Comm. Use column’s numeric position in the ORDER BY clause
```sql
select ename,sal,comm from emp where comm is not null order by 2 desc, 3 desc;
```
## 2.  The HR department needs a query to display all unique job codes from the EMP table.
```sql
select distinct job_code from emp;
```
## 3.  The HR department wants more descriptive column headings for its report on employees. Name the column headings Emp #, Employee, Job, and Hire Date, respectively by giving Column Alias.
```sql
select employee_id as "Emp #", first_name || ' ' || last_name as "Employee", job_id as "Job", hire_date as "Hire Date" from emp;
```
## 4.  The HR department has requested a report of all employees and their job IDs. Display the last name concatenated with the job ID (separated by a comma and space) and name the column Employee and Title by giving Column Alias.
```sql
 select last_name || ', ' || job_id as "Employee and Title" from emp;
```
## 5.  To familiarize yourself with the data in the EMP table, create a query to display all the data from that table. Separate each column output by a comma. ENAME,JOB,HIREDATE,MGR.Name the column title THE_OUTPUT.
```sql
select e.ename || ', ' || e.job || ', ' || e.hiredate || ', ' || mgr.ename as the_output from emp e inner join emp mgr on e.manager_id = mgr.employee_id;  
```
## 6.  Create a report to display the ename, job , and Hiredate  for the employees name is SCOTT or TURNER. Order the query in ascending order by hiredate.
```sql
select ename, job_id as job, hire_date as hiredate from emp where ename in ('Scott', 'Turner') order by 3;
```
## 7.  Display the ename and department number of all employees in departments 20 or 30 in ascending alphabetical order by ename.
```sql
select ename, department_id from emp where department_id in (20, 30) order by 1;
```
## 8. Modify the previous query  to display the last name and salary of employees who earn between 2000 and 3000 and are in department 20 or 30. Label the columns Employee and Monthly Salary, respectively giving Column Alias.
```sql
select last_name "Employees", salary "Monthly Salary" from employees where salary between 2000 and 3000 and department_id in (20, 30);
```
## 9. The HR department needs a report that displays the last name and hire date for all employees who were hired in 1981
```sql
select last_name, hire_date from employees where extract(year from hire_date) = 1981;
```
## 10.  Display the Ename, Sal of employees who earn more than an amount the user specifies after a Prompt.
```sql
select ename, salary from emp where salary > &amount;
```
## 11.  Create a report to display the last name and job title of all employees who do not have a manager.
```sql
select last_name, job_id from employees where manager_id is null;
```
## 12.  Create a query that prompts the user for Manager ID  and generate EMPNO,ENAME, SAL,DEPTNO. The user should have the ability to sort the records on a selected Column.
```sql
select employee_id, last_name, salary, department_id from employees where manager_id = &manager_id order by &sort_column; 
```
## 13. The HR department wants to run reports based on a manager. Create a query that prompts the user for a MGR and generates the empno, ename, salary, and department for that manager’s employees. The HR department wants the ability to sort the report on a selected column
```sql
select employee_id, first_name || ' ' || last_name ename, salary, department_id from employees where manager_id = &manager_id order by &sort_column;
```
## 14.  Display all employee last names in which the third letter of the name is A
```sql
select last_name from employees where lower(last_name) like '%a__';
```
## 15. Display the last name of all employees who have both an A and an S in their ename
```sql
select last_name from employees where upper(last_name) like '%A%' and upper(last_name) like '%S%';
```
## 16.  Display the Ename, Job, Sal for all employees whose jobs are CLERK and whose salary is in 800 or 950 or 1300.
```sql
select first_name, last_name, job_id, salary from employees where job_id = 'CLERK' and salary in (800, 950, 1300);
```