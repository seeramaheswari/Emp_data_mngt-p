## ***Employee_data_management***
### Creating database called emp_payroll_mngt
>create database emp_payroll_mngt;

### Using database 
>use emp_payroll_mngt;
#### Creating table called Employees and declaring its variables
```
create table Employees(
employee_id int primary key,
employee_name varchar(20),
department varchar(10),
position varchar(10),
hire_date date,
base_salary decimal(5,2)
);
```
To view the employees table structure
>desc employees;

modifying column base_salary to change its position to(7,2)
>alter table employees modify column base_salary decimal(7,2);
#### Creating table called Attendance
```
create table Attendance(
attendance_id int primary key,
employee_id int ,foreign key(employee_id) references Employees(employee_id),
attendance_date date,
status enum('present','absent','leave')
);
```
To view the Attendance table structure
>desc attendance;

>select * from employees;
#### Creating table named as salaries with its variables
```
create table salaries(
salary_id int primary key,
employee_id int ,foreign key(employee_id) references Employees(employee_id),
base_salary decimal(5,2),
bonus decimal(3,2),
deduction decimal(3,2),
month varchar(10),
year int
);
```
To view the salaries table structure
>desc salaries;

modifying the columns base_salary(7,2),bonus(6,2) and deduction(6,2) positions
```
alter table salaries modify column base_salary decimal(7,2);
alter table salaries modify column bonus decimal(6,2);
alter table salaries modify column deduction decimal(6,2);
```
#### Creating table called payroll
```
create table payroll(
payroll_id int primary key,
employee_id int ,foreign key(employee_id) references Employees(employee_id),
total_salary decimal(5,2),
payment_date date
);
```
Modifying column total_salary position to(7,2)
>alter table payroll modify column total_salary decimal(7,2);

To view the payroll table struture
>desc payroll;
#### Inserting the values into employees table
``` 
-- inserting values into table employees 
insert into employees values(101,'James','IT','Manager','2018-03-12',8500.00);
insert into employees values(102,'Maria','HR','Director','2018-03-12',9500.00);
insert into employees values(103,'Robert','Finance','Analyst','2018-03-12',1000.00);
insert into employees values(104,'Sarah','Sales','Lead','2019-07-12',1100.00);
insert into employees values(105,'Liam','IT','Associate','2018-09-20',1200.00);
insert into employees values(106,'Emma','Sales','Lead','2018-08-26',9200.00);
insert into employees values(107,'Noah','Sales','Associate','2018-09-12',9900.00);
insert into employees values(108,'Olivia','Sales','Manager','2020-02-12',1700.00);
insert into employees values(109,'William','IT','Manager','2018-03-20',1800.00);
insert into employees values(110,'Sofia','Finance','Manager','2001-12-03',1700.00);
insert into employees values(111,'Lucas','IT','DEV','2003-08-03',1000.00);
insert into employees values(112,'Mia','Marketing','Manager','2021-03-19',9300.00);
insert into employees values(113,'Ethan','Sales','Associate','2020-03-10',9700.00);
insert into employees values(114,'Isabella','HR','Assistant','2018-08-25',9900.00);
insert into employees values(115,'Aiden','IT','Security','2018-11-11',8500.00);
insert into employees values(116,'Chloe','Finance','Analyst','2019-07-06',9500.00);
insert into employees values(117,'Logan','Marketing','Designer','2019-03-15',9900.00);
insert into employees values(118,'Grace','Sales','Lead','2020-03-22',8900.00);
insert into employees values(119,'Jacob','IT','Dev','2018-03-22',1800.00);
insert into employees values(120,'Lily','HR','Specialist','2018-05-11',8300.00);
```
Viewing the Employees table data
>select * from employees;

#### Inserting values into the attendance table
```
insert into attendance (attendance_id, employee_id, attendance_date, status) values
(1, 101, '2026-01-01', 'present'),
(2, 102, '2026-01-01', 'present'),
(3, 103, '2026-01-01', 'leave'),
(4, 104, '2026-01-01', 'present'),
(5, 105, '2026-01-01', 'absent'),
(6, 106, '2026-01-02', 'present'),
(7, 107, '2026-01-02', 'absent'),
(8, 108, '2026-01-02', 'present'),
(9, 109, '2026-01-02', 'present'),
(10, 110, '2026-01-02', 'present'),
(11, 111, '2026-01-03', 'present'),
(12, 112, '2026-01-03', 'present'),
(13, 113, '2026-01-03', 'leave'),
(14, 114, '2026-01-03', 'absent'),
(15, 115, '2026-01-03', 'present'),
(16, 116, '2026-01-04', 'absent'),
(17, 117, '2026-01-04', 'present'),
(18, 118, '2026-01-04', 'present'),
(19, 119, '2026-01-04', 'present'),
(20, 120, '2026-01-04', 'leave');
```
To view the attendance table data
>select * from attendance;

#### Inserting values into salaries table
```
insert into salaries(salary_id, employee_id, base_salary, bonus, deduction, month, year) values
(1,101,8500.00,500.00,250.00,'January',2026),
(2,102,9500.00,300.00,150.00,'January',2026),
(3,103,1000.00,1200.00,400.00,'January',2026),
(4,104,1100.00,0.00,100.00,'January',2026),
(5,105,1200.00,2000.00,550.00,'January',2026),
(6,106,9200.00,450.00,250.00,'January',2026),
(7,107,9900.00,150.00,250.00,'February',2026),
(8,108,1700.00,150.00,150.00,'February',2026),
(9,109,1800.00,250.00,180.00,'January',2026),
(10,110,1700.00,1500.00,800.00,'January',2026),
(11,111,1000.00,100.00,50.00,'January',2026),
(12,112,9300.00,800.00,320.00,'January',2026),
(13,113,9700.00,0.00,120.00,'January',2026),
(14,114,9900.00,550.00,260.00,'January',2026),
(15,115,8500.00,1100.00,450.00,'January',2026);
insert into salaries values (16,116,3500.00,500.00,700.00,'January',2026);
insert into salaries values (17,117,5500.00,600.00,100.00,'January',2026);
insert into salaries values (18,118,4500.00,800.00,1100.00,'January',2026);
insert into salaries values (19,119,1500.00,400.00,200.00,'January',2026);
insert into salaries values (20,120,2000.00,900.00,1000.00,'January',2026);
```
Modifying the column total_salary position(7,2)
>alter table salaries add column total_salary decimal(7,2);

To view the Salaries table structure

#### Inserting values into payroll table
```
insert into payroll(payroll_id, employee_id, total_salary, payment_date) values
(1,101,8750.00,'2025-01-31'),
(2,102,9150.00,'2025-02-28'),
(3,103,1800.00,'2025-02-28'),
(4,104,1000.00,'2025-01-31'),
(5,105,2650.00,'2025-01-31'),
(6,106,9400.00,'2025-02-28'),
(7,107,9800.00,'2025-02-28'),
(8,108,1700.00,'2025-02-28'),
(9,109,1870.00,'2025-02-28'),
(10,110,2400.00,'2025-02-28'),
(11,111,1050.00,'2025-03-31'),
(12,112,9780.00,'2025-03-31'),
(13,113,9580.00,'2025-03-31'),
(14,114,10190.00,'2025-03-31'),
(15,115,9150.00,'2025-03-31'),
(16,116,3300.00,'2025-04-30'),
(17,117,6000.00,'2025-04-30'),
(18,118,4200.00,'2025-04-30'),
(19,119,1700.00,'2025-04-30'),
(20,120,1900.00,'2025-04-30');
```
To view the payroll table data structure
>select * from payroll;

#### Creating new table called emp_data for combining all values
```
create table emp_data as
select e.employee_id,e.employee_name,e.department,e.position,e.hire_date,e.base_salary,
s.salary_id,s.bonus,s.deduction,s.month,s.year,p.payroll_id,p.total_salary,p.payment_date
from employees as e
inner join salaries as s on e.employee_id=s.employee_id
inner join payroll as p on e.employee_id=p.employee_id;
```
Toview the emp_data structure
>desc emp_data;
to view the emp_data table data

>select * from emp_data;

#### Creating new table as emp_data2 by adding attendance table and emp_data table 
``` 
create table emp_data2 as
select e1.employee_id,e1.employee_name,e1.department,e1.position,e1.hire_date,e1.base_salary,
e1.salary_id,e1.bonus,e1.deduction,e1.month,e1.year,e1.payroll_id,e1.total_salary,
e1.payment_date,att.attendance_id,att.attendance_date,att.status
from emp_data as e1
inner join attendance as att on e1.employee_id=att.employee_id;
```
To view the emp_data2 table structure
>desc emp_data2;

To view the emp_data2 table data
>select * from emp_data2;
## Data Analysis & 10 Buisiness key problems and answers

***--Q.1 Counting no of employees in each department***

>select department,count(employee_id) from employees group by department;

***-- Q.2 Counting no of employees in each position***

>select position,count(employee_id) from employees group by position;

***-- Q.3 Write sql query to check count of  employees joined in each year and month wise*** 

>select extract(year from hire_date) as join_year ,extract(month from hire_date) as join_month ,count(*)
from employees group by 1,2 order by 1,2 desc;

***-- Q.4 Write sql query to check employee_id and names and also salary whose salary grater than 5000***

>select employee_id,employee_name ,base_salary from employees where base_salary>=5000 order by base_salary desc;

***-- Q.5 Write sql query to check  names,bonus whose bonus that are between 200 to 1000 in descending order***
>select e.employee_id,s.bonus
from employees as e
inner join salaries as s on e.employee_id=s.employee_id 
where s.bonus>200 and s.bonus<1000 order by s.bonus desc ;

***-- Q.6 Write sql query to check count employees in each month that got payment***
>select extract(month from payment_date) as month,count(*) from payroll
 group by 1;

 ***-- Q.7 Write a sql query to which position get highest salary***

 >WITH RankedSalaries as (
 select 
 e.position,s.base_salary,
 dense_rank() over (order by s.base_salary desc) as salary_rank
 from employees as e 
 inner join salaries as s on e.employee_id=s.employee_id
 )
 select position,base_salary
 from RankedSalaries
 where salary_rank=1;

 ***-- Q.8 Write sql query to check who are absent on what date***
 >select employee_name,attendance_date from emp_data2 where status='absent';

 ***-- Q.9 Write sql query to check who are on leave and  on what date***
  >select employee_name,attendance_date from emp_data2 where status='leave';

  ***-- Q.10 Write a sql query total amount credited to employees and total amount that deducted from all employees***

  >select sum(base_salary),sum(deduction) from emp_data2;
















 
