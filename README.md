# sql_PRACTICE
WEEK 1


show databases;

create database vit;
drop database vit;
use vit;
create table cse(
s_id int,
s_name varchar(30),
s_mark int
);
drop table cse;
show tables from vit;

select * from cse;
insert into cse values (1001,'ram',99);
insert into cse values (1021,'sham',69);
insert into cse values (1301,'dam',29);
insert into cse values (1231,'tam',77);
insert into cse values (1351,'nam',39);
ALTER TABLE cse ADD(
    s_num VARCHAR(200),
    father_name varchar(40)
);

alter table cse drop address;
insert into cse values (1007,'ham',46, 5677);




alter table cse rename column
s_id to name;
delete from cse where name=1231;
update cse set s_mark=81 where name=1351;
update cse set s_mark = s_mark+1;
select name from cse;




desc cse







create database practice1;
use practice1;
create table Mech(s_id int,s_name varchar(25));
START TRANSACTION;
insert into Mech values (101,'jayanth');
savepoint A;
update mech set s_id=102 where s_id=101;
savepoint B;
insert into Mech values (103,'karthick');
select * from mech;
savepoint C;
select * from mech;
rollback to B;
select * from mech;







CREATE DATABASE ORG123;
SHOW DATABASES;
USE ORG123;

CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

INSERT INTO Worker 
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');
        
        SELECT * FROM Worker WHERE SALARY > 100000 AND DEPARTMENT = 'HR';
        SELECT * FROM Worker WHERE SALARY > 200000;
        
        select * from worker
where salary between 100000 and 200000;
select * from worker
where salary not between 100000 and 200000;

select first_NAME from worker where worker_id=4;
select first_NAME from worker where worker_id=4 or worker_id=2;

select first_NAME from worker where worker_id in (2,4,6);

select * from worker
where salary between 100000 and 200000
and worker_id in (1,2,3,4,5);

SELECT MIN(salary)
FROM worker
WHERE department='HR';

SELECT MIN(salary)
FROM worker
WHERE department = 'account';  
SELECT MAX(salary)
FROM worker
WHERE department = 'account';  

SELECT COUNT(salary)
FROM worker
WHERE salary>100000;

SELECT AVG(salary)
FROM worker
WHERE salary>100000;

SELECT SUM(salary)
FROM worker
WHERE salary>100000;





WEEK 2

3/2/25

use org123;
select * from worker;
select department from worker;
select distinct (department) from worker;

select worker_id from worker;
select worker_id as emp_code from worker;

select worker_id from worker
union
select worker_id from worker;

SELECT department, worker_id FROM worker
WHERE salary=100000
UNION
SELECT department, worker_id FROM worker
WHERE salary=200000
ORDER BY worker_id;

SELECT department, worker_id FROM worker
WHERE department='HR'
UNION
SELECT department, worker_id FROM worker
WHERE department='Account'
ORDER BY worker_id;

SELECT worker_id, first_name,department,
CASE
    WHEN salary > 300000 THEN 'Rich people'
    WHEN salary <=300000 && salary >=100000 THEN 'Middle stage'
    ELSE 'Poor people'
END 
AS People_stage_wise
FROM worker;

SELECT 'HR' AS DEPARTMENT, COUNT(WORKER_ID) AS Total_Employees
FROM Worker 
WHERE DEPARTMENT = 'HR'
UNION
SELECT 'Admin' AS DEPARTMENT, COUNT(WORKER_ID) AS Total_Employees
FROM Worker 
WHERE DEPARTMENT = 'Admin'
UNION
SELECT 'Account' AS DEPARTMENT, COUNT(WORKER_ID) AS Total_Employees
FROM Worker 
WHERE DEPARTMENT = 'Account'
ORDER BY DEPARTMENT;




4/2/25


use org123;
select * from worker;
select * from worker where department= 'Admin' order by salary;    
select * from worker where department= 'Admin' order by department desc;
select * from worker where department= 'Admin' order by salary desc; 
select * from worker where department= 'Admin' order by salary desc limit 1;

select department, count(department) as total_employees from worker 
where department = 'HR' or department = 'Account' group by department;


# select department, count(department) as total_employees from worker
#  group by department;
# SELECT MIN(total_employees);
# SELECT MAX(total_employees);  


(
  SELECT department, COUNT(department) AS total_employees
  FROM worker
  GROUP BY department
  ORDER BY total_employees ASC
  LIMIT 1
)

UNION ALL

(
  SELECT department, COUNT(department) AS total_employees
  FROM worker
  GROUP BY department
  ORDER BY total_employees DESC
  LIMIT 1
);





6/2/25

use org123;
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
show tables from org123;
select * from persons;

ALTER TABLE Persons
MODIFY Age int NOT NULL;


CREATE TABLE Person (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    UNIQUE (ID)
);

select * from person;

CREATE TABLE Persons1 (
    ID int primary key,
    LastName varchar(255) NOT NULL unique,
    FirstName varchar(255) NOT NULL unique,
    Age int
   );
   
   CREATE TABLE Persons2 (
    ID int,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) ,
    Age int,
    PRIMARY KEY (ID)
);

desc persons1;
desc persons2;


ALTER TABLE Persons





7/2/25

use org123;
create table category(
c_id int primary key,
c_name varchar(25) not null unique,
c_descrp varchar(250) not null
);

insert into category values (101, 'electronics', 'it stores all set of electronics items');

insert into category values (102, 'furnitures', 'it stores all set of wood items');

select * from category;
desc category;


create table products (
p_id int primary key,
p_name varchar(250) not null,
c_id int,
constraint c_id foreign key (c_id)
references category (c_id)
);

desc products;


drop table products;

create table products (
p_id int primary key,
p_name varchar(250) not null,
c_id int not null,
constraint c_id foreign key (c_id)
references category (c_id)
);

insert into products values (901, 'IPhone 14 Pro', 101);
insert into products values (902, 'wireless eraphone', 101);
insert into products values (903, 'chair', 102);
insert into products values (984, 'IPhone 15 Pro', 103);
select * from products;
insert into products values (901, 'IPhone 14 Pro', null);

select * from category;
delete from category where c_id=101;
drop table category;







8/2/25

create database saturday;
use saturday;
create table category(
c_id int primary key,
c_name varchar(25) not null unique,
c_decrp varchar(250) not null
);
insert into category values (101, 'electronics', 'it stores all set of electronics items');
insert into category values (102, 'furnitures', 'it stores all set of wooden items');
select * from category;
desc category;

CREATE TABLE Products (
    P_ID int primary key,
    p_Name varchar(250) NOT NULL,
    c_id int ,
    CONSTRAINT c_id FOREIGN KEY (c_id)
    REFERENCES category(c_id) on delete cascade
);

desc products;

insert into products values (904, 'Wooden table', null);
select * from products;

select * from category;

insert into products values (902, 'intel i7 processor', 101);
select * from products;
delete from category where c_id=101;
update products set p_name='wooden chair' where p_id=904;
select * from products;





create table college(
cid int primary key,
c_name varchar(25) not null unique,
c_decrp varchar(250) not null
);
insert into college values (101, 'VIT Bhopal', 'in bhopal');
insert into college values (102, 'VIT Chennai', 'in chennai');
insert into college values (103, 'VIT vellore', 'in vellore');
select * from college;
drop table college;
CREATE TABLE Departments (
    D_ID int primary key,
    D_Name varchar(250) NOT NULL,
    cid int ,
    CONSTRAINT cid FOREIGN KEY (cid)
    REFERENCES college(cid)
);
insert into departments values (201, 'CSE', 101);
insert into departments values (202, 'MECHANICAL', 102);
insert into departments values (203, 'AEROSPACE', 103);
select * from Departments;
CREATE TABLE Students (
    S_ID int primary key,
    D_Name varchar(250) NOT NULL,
    D_id int ,
    CONSTRAINT D_id FOREIGN KEY (D_id)
    REFERENCES departments(D_id)
);
insert into students values (501, 'aryan', 201);
insert into students values (502, 'krish', 202);
insert into students values (503, 'raj', 203);
select * from students;



ADD PRIMARY KEY (ID);

ALTER TABLE Persons
DROP PRIMARY KEY;



