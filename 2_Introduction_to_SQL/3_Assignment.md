# using single-row functions to customize the output
## 1.  Write a query to display the current date. Label the column Date.
```sql
select sysdate as "date" from dual;
```
## 2. The HR department needs a report to display the employee number, last name, salary, and salary increased by 15.5% (expressed as a whole number) for each employee. Label the column New Salary.
```sql
select employee_id, last_name, salary, ROUND(salary + 15.5*salary/100) as "New Salary" from employees;
```
## 3.  Modify the previous query to add a column alias that subtracts the old salary from the new salary. Label the column Increase
```sql
select employee_id, last_name, salary, ROUND(salary + 15.5*salary/100) as "New Salary", ROUND(15.5*salary/100) as Increase from employees;
```
## 4. Write a query that displays the ename (with the first letter uppercase and all other letters lowercase) and the length of the  ename for all employees whose name starts with the letters J, A, or M. Give each column an appropriate label. Sort the results by the employees’ enames.
```sql
select INITCAP(first_name) || ' ' || last_name as ename, length(first_name)+length(last_name)+1 as "Length of ename" from employees where regexp_like(first_name, '^[JAM]') order by 1;
```
## 5. Rewrite the query so that the user is prompted to enter a letter that starts the last name. For example, if the user enters H when prompted for a letter, then the output should show all employees whose last name starts with the letter H.
```sql
select * from employees where lower(last_name) like lower('&enter_letter%');
```
## 6. The HR department wants to find the length of employment for each employee. For each employee, display the ename and calculate the number of months between today and the date on which the employee was hired. Label the column MONTHS_WORKED. Order your results by the number of months employed. Round the number of months up to the closest whole number.
```sql
select first_name || ' ' || last_name as ename, ROUND(MONTHS_BETWEEN(sysdate, hire_date)) as months_worked from employees order by 2;
```
## 7. Create a report that produces the following for each employee: earns monthly but wants <3 times salary>. Label the column Dream Salaries.
```sql
select first_name || ' ' || last_name || ' earns monthly but wants ' || (salary * 3) as "Dream Salaries" from employees;
```
## 8. Create a query to display the last name and salary for all employees. Format the salary to be 15 characters long, left-padded with the $ symbol. Label the column SALARY.
```sql
select last_name, '$' || ' ' ||  LPAD(salary,15,0) as salary from employees;
```
## 9. Display each employee’s last name, hire date, and salary review date, which is the first Monday after six months of service. Label the column REVIEW. Format the dates to appear in the format similar to “Monday, the Thirty-First of July, 2000.”
```sql
SELECT last_name,
       TO_CHAR(hire_date,
               'fmDay, "the" DDSPTH "of" Month, YYYY') AS hiredate,
       salary,
       TO_CHAR(ADD_MONTHS(hire_date, 6),
               'fmDay, "the" DDSPTH "of" Month, YYYY') AS review
FROM employees;
```
## 10. Display the last name, hire date, and day of the week on which the employee started. Label the column DAY. Order the results by the day of the week, starting with Monday.
```sql
select last_name, hire_date, to_char(hire_date, 'Day') as Day from employees order by 3;
```
## 11. Create a query that displays the employees’ last names and commission amounts. If an employee does not earn commission, show “No Commission.” Label the column COMM.
```sql
select last_name, NVL(TO_CHAR(commission_pct), 'NO Commission') as comm from employees;
```
## 12. Create a query that displays the first eight characters of the employees’ last names and indicates the amounts of their salaries with asterisks. Each asterisk signifies a thousand dollars. Sort the data in descending order of salary. Label the column EMPLOYEES_AND_THEIR_SALARIES.
```sql
select substr(last_name, 1, 8) || ' ' || RPAD('*', floor(salary/1000), '*') as employees_and_their_salaries from employees order by salary desc;
```
## 13. Using the DECODE function, write a query that displays the grade of all employees based on the value of the column JOB_ID, using the following data: PRESIDENT-A,MANAGER-B,SALESMAN-C,CLERK-D
```sql
SELECT last_name, 
       job_id,
       DECODE(job_id, 
              'PRESIDENT', 'A',
              'MANAGER',   'B',
              'SALESMAN',  'C',
              'CLERK',     'D',
              'Unknown') AS GRADE
FROM employees;
```
## 14. Rewrite the statement in the preceding exercise using the CASE syntax
```sql
SELECT last_name, 
       job_id,
       CASE job_id
           WHEN 'PRESIDENT'  THEN 'A'
           WHEN 'MANAGER'   THEN 'B'
           WHEN 'SALESMAN'   THEN 'C'
           WHEN 'CLERK' THEN 'D'
           ELSE 'Other'
       END AS GRADE
FROM employees;
```
## 15. 