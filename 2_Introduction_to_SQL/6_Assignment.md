# Displaying Data from Multiple Tables Using Joins
## 1. Write a query for the HR department to produce the addresses of all the departments. Use the EMP and DEPT tables. Show the EMPNO, ENAME,SAL, DNAME and LOC in the output. Use a NATURAL JOIN to produce the results.
```sql
select empno, ename, sal, d.dname, loc from emp e natural join dept d; 
```
## 2. The HR department needs a report of all employees. Write a query to display the JOB,MGR,SAL,COMM,DNAME of employees whose JOB is SALESMAN.
```sql
select job, mgr, sal, comm, dname from emp natural join dept where job = 'SALESMAN';
```
## 3. The HR department needs a report of employees in LOC  DALLAS. Display the ENAME, job, DEPTNO, and DNAME for all employees who work in DALLAS.
```sql
select ename, job, deptno, dname from emp natural join dept where loc = 'DALLAS';
```
## 4. Create a report to display employees’ ename and employee number along with their manager’s name and manager number. Label the columns Employee, Emp#, Manager, and Mgr#, respectively.
```sql
SELECT e.ename AS "Employee",
       e.empno AS "Emp#",
       m.ename AS "Manager",
       m.empno AS "Mgr#"
FROM emp e
JOIN emp m
ON e.mgr = m.empno;
```
## 5. Modify the previous Query to display all employees including King, who has no manager. Order the results by the employee number.
```sql
SELECT e.ename AS "Employee",
       e.empno AS "Emp#",
       m.ename AS "Manager",
       m.empno AS "Mgr#"
FROM emp e
LEFT JOIN emp m
ON e.mgr = m.empno
ORDER BY e.empno;
```
## 6. The HR department needs a report on job grades and salaries. To familiarize yourself with the SALGRADE table, first show the structure of the SALGRADE table. Then create a query that displays the name, job, department name, salary, and grade for all employees.
```sql
desc salgrade;
SELECT e.ename,
       e.job,
       d.dname,
       e.sal,
       s.grade
FROM emp e
JOIN dept d
ON e.deptno = d.deptno
JOIN salgrade s
ON e.sal BETWEEN s.losal AND s.hisal;
```
## 7. Display the ENAME,DNAME of all the employees. Also display those department name which do not have any employees working.
```sql
select ename, d.dname from emp e right outer join dept d on e.deptno = d.deptno;
```
## 8. The HR department needs to find the names and hire dates for all employees who were hired before their managers, along with their managers’ names and hire dates.
```sql
SELECT e.ename AS employee,
       e.hiredate AS employee_hiredate,
       m.ename AS manager,
       m.hiredate AS manager_hiredate
FROM emp e
JOIN emp m
ON e.mgr = m.empno
WHERE e.hiredate < m.hiredate;
```
## 9. Display the EMPNO,ENAME,DNAME,LOC of those employees who are working as CLERK. Use the USING clause.
```sql
select empno, ename, dname, loc from emp join dept using (deptno) where job = 'CLERK';
```
## 10. Display the ENAME,SAL,MGR,DNAME of employees whose salary is more than 2000. Use the ON clause.
```sql
SELECT e.ename, e.sal, e.mgr, d.dname FROM emp e JOIN dept d ON e.deptno = d.deptno WHERE e.sal > 2000;
```
## 11. Display the EMPNO,ENAME,JOB,DEPTNO,DNAME,LOC of employees. Use LEFT OUTER JOIN.
```sql
SELECT e.empno, e.ename, e.job, e.deptno, d.dname, d.loc FROM emp e LEFT OUTER JOIN dept d ON e.deptno = d.deptno;
```
## 12. Display the ENAME,DNAME of employees. Use RIGHT OUTER JOIN.
```sql
select e.ename, d.dname from emp e right outer join dept d on e.deptno = d.deptno; 
```
## 13. Display the EMPNO,DNAME,LOC of employees. Use FULL OUTER JOIN.
```sql
select e.empno, d.dname, d.loc from emp e full outer join dept d on e.deptno = d.deptno;
```