create database mph;
use mph;


show databases;
show tables;
describe emp;
desc emp;

select * from emp;  -- selecting all rows and columns

select empno,hiredate from emp;

select empno,hiredate "DOJ time" from emp; -- alias with the data (as or "")
select empno,sal,sal+200 as Bonus from emp;  -- mathematical expressions
select distinct sal from emp; -- distinct gives you unique key value records

select * from emp where ename='smith';
select empno,ename,job,deptno from emp where deptno<=20;
select empno,ename,job,deptno from emp where deptno>20;
select empno,ename,job,deptno from emp where deptno!=20;

select empno,ename,deptno,job from emp where DEPTNO in(10,20);
select empno,ename,deptno,job from emp where DEPTNO not in(10,20);
select empno,ename,deptno,job from emp where DEPTNO=30 or deptno=10;

select empno,ename,deptno,job,sal from emp where deptno=20 order by 2;
select empno,ename,deptno,job,sal from emp where deptno=20 order by ename ;
select empno,ename "Ename",deptno,job,sal from emp where deptno=20 order by Ename ;

select empno,ename,deptno,job,sal from emp where ename like 'A%'; -- pattern matching operartor
select empno,ename,deptno,job,sal from emp where ename like '_A%'; -- second matching operator
select empno,ename,deptno,job,sal from emp where ename like '%n';   -- 

-- Range operator
select empno,ename,job,sal from emp where sal between 1250 and 3000; -- included
select empno,ename,job,sal from emp where sal between 1250 and 2900;
select empno,ename,job,sal from emp where sal not  between 1250 and 2900;
-- null operator
select empno,ename,job,sal,comm from emp where comm is null ;
select empno,ename,job,sal,comm from emp where comm is not null ;

-- Pre Defined Functions
-- 1)Number based Function
-- 2)character based function
-- 3)Date based Function
-- 4)General Function
-- 5)Group Funcion or Aggrergate Function

-- Number based Function

select round(14.56,-1); -- 20
select round(254.56,-2); -- 300
select round(15.56,1); -- 15.

select truncate (254.56,-2); -- 10
select truncate (15.56,1); -- 15.5
select truncate(15.56,2); -- 15.56
select truncate(15.56,0); -- 15

select mod(1600,4);
select 200 mod 2;
select 200 % 2;

select floor(1.93); -- nearest lowest Number
select ceil(1.13); -- nearest highest number

-- Character Based Function

select lower(ename) from emp;
select lower ('Anish');
select upper(ename) from emp;
select upper ('Anish');
select concat('mr.','Anish', 'Kumar') Name;

select length('Anishkumar') Namelength ;

select reverse('Kumar');
-- repeat function select repeat('hi',3);

select trim('       ram        ');
select substring('Learning mysql',3,5); -- index start with the character 

-- date functions
select curdate(),current_date(),curtime(),current_time();
select current_timestamp();
select day('2024-08-07');
select dayname('2024-08-07');
select dayofmonth('2024-08-07'),dayofweek('2024-08-07'),dayofyear('2024-08-07');
select date_add('2024-08-07',interval 2 day),date_sub('2024-08-07',interval 2 day);

select date_format('2024-08-07 02:02:14','%W %D %M %Y %T %I %s' );
select date_format('2024-08-07 02:02:14','%W %D %M %Y %T %I %s' );
select date_format('2024-08-07 05:02:14','%W %D %M %Y %T %I %s' );
select time_format('12:54:51', ' %p');





select distinct job from emp;

select * from emp order by sal;

select job,deptno from emp;
select job,deptno from emp  order by job asc;

select distinct job  from emp order by job desc ;

select ename,mgr from emp;

select empno,ename,sal from emp order by sal asc;
--------------------------------------------
-- group Function  -- do not give column names along with group functions along with select list
						-- group functions ignores null values
select min(sal),max(sal),avg(sal),sum(sal),count(sal) from emp;
select sum(sal),ename from emp;
select count (comm) from emp;

--------------------------
--- Data dictionary table  --meta data table -- are read only tables 

desc information_schema.tables;
desc information_schema.columns;
select table_name,create_time from information_Schema .tables
where table_name='emp';

select table_name,table_schema,column_name
where table_name='emp';

select user,current_connections,total_connections
from performance_schema.users;

-- 1
select * from emp;

-- 2
select distinct job from emp;
-- 3
select ename,job,sal from emp order by sal asc;
-- 4
select ename,deptno,job from emp order by deptno ,job desc;

-- 5
select job as jobs from emp group by job order by job desc;
 -- 6
 select * from emp where mgr is not null;
-- 7
select * from emp where EXTRACT(YEAR FROM hiredate)<1981;

-- 8
select  empno,ename,sal,sal*12 as ann from emp order by ann ;
 -- 9
select empno,ename,job,hiredate ,  DATEDIFF(DATE(NOW()),DATE(hiredate))/365   as exp from emp;
-- 10
select empno,ename,Sal, DATEDIFF(DATE(NOW()),DATE(hiredate))/365   as exp from emp where mgr=7698;

-- 11

select ename,comm,sal from emp ;
select ename,comm,sal from emp  where comm >sal;
-- 12
select ename,job,hiredate from emp where extract(YEAR FROM hiredate)>=1981 and extract(MONTH FROM HIREDATE)>6 ORDER BY hiredate;
-- 13

select job from emp order by job desc  ;

select job from emp order by job desc  ;

-- 14
select ename,hiredate from emp ;

-- 16
select empno,ename,deptno,job from emp where DEPTNO in(10,20);

-- 17
select ename,hiredate from emp where extract(year from hiredate)=1981;

-- 18

select ename,hiredate from emp where extract(year from hiredate)=1980 and extract(Month from hiredate)=8;
-- 19
select ename,sal from emp where sal between 220 and 4500;

-- 20
select empno,ename,deptno,job,sal from emp where ename like '_____';
