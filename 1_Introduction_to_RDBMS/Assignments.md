**Assignments on Normalization**

1. Observe the structure of a given EMPLOYEE table as below and suggest if this table can be further Normalized
EMPNO,ENAME,SAL,DEPTNO,DNAME,LOC
Explain what normal form this table is and how you can make this into next normal form

Ans.

I consider that the table doesn't have any multi-valued attributes, therefore the table is already in First Normal Form.

Employee(empno, ename, sal, deptno, dname, loc)

I can assume these dependencies are present

empno -> ename, sal, deptno   
deptno -> dname, loc

now, Primary key is: empno  
therefore, 
empno -> deptno and deptno -> dname,loc  
This is transitive dependency

and as PK is a single attribute(empno), therefore having any partial dependency is not a chance. Thus, the table is in 2nd Normal Form

but, since it has transitive dependency, it is not in 3rd normal form

to make into 3rd normal form:  
split into 2 tables  

**employee**(empno, ename, sal, deptno)  
and  
**department**(deptno, dname, loc)

this table is also in BCNF

2. Observe the structure of a given STUDENT table as below and suggest if this table can be further Normalized
ROLLNO, NAME,AGE,EXAM, MARKS, GRADE.
Explain what normal form this table is and how you can make this into next normal form


Ans.

We have Student(rollno, name, age, exam, marks, grade)

identify PK
rollno -> age, name  
(rollno, exam) -> marks  
marks -> grade

therefore it has composite candidate key
{rollno, exam}

relation is in 1NF (already known fact)

but not in 2NF
as rollno -> name, age
(becoz of partial dependency!)

converting to 2NF

Student(rollno, name, age)  
result(rollno, exam, marks, grade)

and we can further normalize into 3NF 

as you can see marks -> grade

to remove it

Student(rollno, name, age)  
result(rollno, exam, marks)
grade_master(marks, grade)

3. Observe the structure of a given EMPLOYEE table and suggest what kind of problem this table has and how to solve the problem
EMPNO,PROJECT_NO,NO_OF_DAYS,CUSTOMERNAME
In the above table EMPNO AND PROJECT_NO both are together a composite primary key 

employee(empno, project_no, no_of_days, customername)

composite PK (given) : (empno, project_no)

since project_no -> no_of_days, customername

therefore PD is present

to resolve into 2NF 

employee(empno, project_no)  
projectDetails(project_no, no_of_days, customername)









