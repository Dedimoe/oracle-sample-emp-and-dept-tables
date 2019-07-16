# oracle-sample-emp-and-dept-tables
Sample EMP and DEPT tables. 
Classic Oracle tables with 4 departments and 14 employees. Includes a join query example.

- Script Name : EMP and DEPT
- Description : Sample EMP and DEPT tables. Classic Oracle tables with 4 departments and 14 employees. Includes a join query example.
- Category    : SQL General
- Contributor : Mike Hichwa (Oracle)
- Created Monday October 05, 2015 

```
create table dept(  
  deptno     number(2,0),  
  dname      varchar2(14),  
  loc        varchar2(13),  
  constraint pk_dept primary key (deptno)  
);
/
```

```
create table emp(  
  empno    number(4,0),  
  ename    varchar2(10),  
  job      varchar2(9),  
  mgr      number(4,0),  
  hiredate date,  
  sal      number(7,2),  
  comm     number(7,2),  
  deptno   number(2,0),  
  constraint pk_emp primary key (empno),  
  constraint fk_deptno foreign key (deptno) references dept (deptno)  
);
/

insert all
  into DEPT values(10, 'ACCOUNTING', 'NEW YORK')
  into dept values(20, 'RESEARCH', 'DALLAS')
  into dept values(30, 'SALES', 'CHICAGO')
  into dept values(40, 'OPERATIONS', 'BOSTON')
SELECT * FROM dual;
/

insert all
   into emp values(7839, 'KING', 'PRESIDENT', null, to_date('17-11-1981','dd-mm-yyyy'), 5000, null, 10)
   into emp values(7698, 'BLAKE', 'MANAGER', 7839,  to_date('1-5-1981','dd-mm-yyyy'), 2850, null, 30 )
   into emp values(7782, 'CLARK', 'MANAGER', 7839,  to_date('9-6-1981','dd-mm-yyyy'),  2450, null, 10 )
   into emp values(7566, 'JONES', 'MANAGER', 7839,  to_date('2-4-1981','dd-mm-yyyy'),  2975, null, 20  )
   into emp values(7788, 'SCOTT', 'ANALYST', 7566,  
 to_date('13-JUL-87','dd-mm-rr') - 85,  
 3000, null, 20  
)
into emp  
values(  
 7902, 'FORD', 'ANALYST', 7566,  
 to_date('3-12-1981','dd-mm-yyyy'),  
 3000, null, 20  
)
into emp  
values(  
 7369, 'SMITH', 'CLERK', 7902,  
 to_date('17-12-1980','dd-mm-yyyy'),  
 800, null, 20  
)
into emp  
values(  
 7499, 'ALLEN', 'SALESMAN', 7698,  
 to_date('20-2-1981','dd-mm-yyyy'),  
 1600, 300, 30  
)
into emp  
values(  
 7521, 'WARD', 'SALESMAN', 7698,  
 to_date('22-2-1981','dd-mm-yyyy'),  
 1250, 500, 30  
)
into emp  
values(  
 7654, 'MARTIN', 'SALESMAN', 7698,  
 to_date('28-9-1981','dd-mm-yyyy'),  
 1250, 1400, 30  
)
into emp  
values(  
 7844, 'TURNER', 'SALESMAN', 7698,  
 to_date('8-9-1981','dd-mm-yyyy'),  
 1500, 0, 30  
)
into emp  
values(  
 7876, 'ADAMS', 'CLERK', 7788,  
 to_date('13-JUL-87', 'dd-mm-rr') - 51,  
 1100, null, 20  
)
into emp  
values(  
 7900, 'JAMES', 'CLERK', 7698,  
 to_date('3-12-1981','dd-mm-yyyy'),  
 950, null, 30  
)
into emp  
values(  
 7934, 'MILLER', 'CLERK', 7782,  
 to_date('23-1-1982','dd-mm-yyyy'),  
 1300, null, 10  
)
SELECT * FROM dual;
```

```
select ename, dname, job, empno, hiredate, loc  
from emp, dept  
where emp.deptno = dept.deptno  
order by ename

 
ENAME	DNAME	JOB	EMPNO	HIREDATE	LOC
ADAMS	RESEARCH	CLERK	7876	23-MAY-87	DALLAS
ALLEN	SALES	SALESMAN	7499	20-FEB-81	CHICAGO
BLAKE	SALES	MANAGER	7698	01-MAY-81	CHICAGO
CLARK	ACCOUNTING	MANAGER	7782	09-JUN-81	NEW YORK
FORD	RESEARCH	ANALYST	7902	03-DEC-81	DALLAS
JAMES	SALES	CLERK	7900	03-DEC-81	CHICAGO
JONES	RESEARCH	MANAGER	7566	02-APR-81	DALLAS
KING	ACCOUNTING	PRESIDENT	7839	17-NOV-81	NEW YORK
MARTIN	SALES	SALESMAN	7654	28-SEP-81	CHICAGO
MILLER	ACCOUNTING	CLERK	7934	23-JAN-82	NEW YORK
SCOTT	RESEARCH	ANALYST	7788	19-APR-87	DALLAS
SMITH	RESEARCH	CLERK	7369	17-DEC-80	DALLAS
TURNER	SALES	SALESMAN	7844	08-SEP-81	CHICAGO
WARD	SALES	SALESMAN	7521	22-FEB-81	CHICAGO

14 rows selected.
Statement 22
The GROUP BY clause in the SQL statement allows aggregate functions of non grouped columns. The join is an inner join thus departments with no employees are not displayed.
```

```
select dname, count(*) count_of_employees
from dept, emp
where dept.deptno = emp.deptno
group by DNAME
order by 2 desc

```
