********** Primary key:-
column or set of columns that uniquely identifies a row. Primary key is a type of constraints.
* duplicate values are not allowed (has to be unique)
* null values are not allowed ( it's a mandatory column)
* it's recommended that every table should have a Primary Key
* purpose of Primary Key is row uniqueness (with the help of Primary Key column, you can distinguish between 2 rows
 of a table)
* unique index is automatically created
COMPOSITE PRIMARY KEY: - when we define primary key in set of columns then it is called Composite key. Like for
example year and month column.


************ UNIQUE
* will not allow duplicate values (similar to Primary Key)
* will allow null values (unlike Primary Key) (can have any number of null values)
* UNIQUE INDEX is created automatically
* can combine upto 32 columns in a composite unique
* CAN HAVE ANY NUMBER OF UNIQUE KEY CONSTRAINTS


**********FOREIGN KEY: -
* One table column or set of columns that references a column or set of columns of another table
* Foreign key constraint is specified on the child column (not the parent column)
* parent column has to be PRIMARY Key or UNIQUE
* Foreign Key will allow duplicate values (unless specified otherwise)
* Foreign Key will allow null values (unless specified otherwise)
* Foreign Key may reference a column of the same table also (known as self-referencing)
CHECK CONSTRAINT: -
* used for validations (used for checking purposes)
e.g sal < 10000, age > 21, etc.
* Operators we can use
- Relational operator - Logical operator Arithematic operator - Logical operator

*******View :- View is the virtual table . stores the address of table (HD pointer) (also known as LOCATOR)
used for indirect access to the table * USED FOR SECURITY PURPOSES
* used to restrict the access of the users * it does not contain the data * DML operations can be done on a view
* DML operations performed on a view will affect the base table
* create view v2 as select * from emp where deptno = 1; grant select, insert on v2 to scott;

********Stored Procedure:-
1) Stored procedure are the data base object . procedure’s always return type will be void and it can take three
type of parameter like in which is by default , out we have to write explicitly , inout.
In is read only , out is write only , in out is read and write only
2) Procedure is simple function like function in c and cpp. But in Procedure we write inside it pl program for dml
operation in table.
3) Procedure can be called from any back end software , work bech and command line.
4) Procedure can call another procedure
5) Procedure can call itself also
6) Actually after making procedure it is compiled . and then we can call it any times so not need to again again for
compilation. It becomes in server hard Disk. There fore it is faster
7) Basically it saved backend application from sql injection.

****** Stored Function:-
1) Stored function are data base object , stored function will always return some data type value. It can also take
parameter of type in , out , in out that is for read and write only.
2) Inside the procedure we write the pl program which it does operation and after it return the single value , we
have some implicit faction like sum , min , max, count , avg ,
3) Procedure can be called in select query and it return some value.
4) One function can call to another function.
5) Recursion is allowed by function
6) Actually after making function it is compiled . and then we can call it any times so not need to again again for
compilation. It becomes in server hard Disk. There fore it is faster.

********ACID:-
Atomicity:- atomicity ensure that a transaction is treated as s single unit of work. It means that all the operation
within a transaction should completed successfully, or else if any of them get failed that transaction should not
reflect on database.
Consistency:- the word consistency means that the value should remain preserved always. After the transaction the
value should be consistence. Take example of A, B and C account .
Isolation:- the term isolation means separation. Isolation property ensures that no data get effect by concurrently.
Means simultaneously in database there should allowed to read and write data multiple thread.
Durability:- it ensure that after every transaction there must be commit and rollback if transaction get failed.
Sql database vs No Sql database
Sql:- sql database have fixed or predefine schema. It is structured data base.
Sql database are best suited for complex queries or object . data is stored in column and row format
Nosql:- no sql does not have fixed and predefine schema. It is not structured data base.
Nosql database are not good complex quries.beacuse these are not powerful as sql database. Data is stored in object
format.
SQL vs NoSQL :- Sql is used for manage RDBMS .
Operation (Practice)
1. Creating Table :-
Formate : colname type constraints
Create table student (id int primary key,
Name varchar(50) ,
Age int not null
);
2. Adding Data in Table :-
Insert into student (id , name ,age) values(1, ‘danish’ ,250), (2, ‘daj ’ ,350);;
Insert into student values (1, ‘danish’ ,250), (2, ‘daj ’ ,350);;
3. Drop database dbName;
Create table student (
id int ,
Name varchar(50) ,
Age int not null,
primary key(id)
);
4. Select * from student marks between 80 and 90 (exclusive 80 and 90)
5. Select * from student where city in ( “delhi”,”pun”);
6. Select * from student where city not in ( “delhi”,”pun”); ( city !=”delhi” And city !=”pun”)
7. Select * from student where city not in (“del”,”lokc”) limit 3; (only 3 rows )
8. Select * from student order by city asc ;
9. Select * from student order by marks desc limit 3 ;
3. Aggregate function :-
It does some operation and returns single value.
Count(colName) , Max(colName) , Min(colName) , Sum(colName) , Avg(colName)
4. Group by clause :
Most of the with group by we use aggregate function .
Select city , count(rollNo) from student group by city;
5. Having clause ( where is normally to put condition in row but having is for group condition)
Select count(name) , city from student group by city having max(marks) >90 ;
6. general order :- select from where group by having order by limit
7. update : update student set marks= marks+1 ;
8. Delete :- delete from student where marks <33;
Foreign key :- create table dept ( id int primary key , name varchar(50));
Create table teacher ( id int primary key ,
Name varchar(50) , dept_id int ,
Foreign key (dept_id) references dept(id)
on delete cascade
on update cascade );
Add column :- alter table tabName add column age int ; alter table student add column age Int not null default 19; (imp)
Drop column :- alter table tabName drop column age;
Rename Table :- alter table tabName rename to new_tabName;
Change column (rename) : alter table tabName CHANGE COLUMN old_name new_name new_datatype
new_constraint;
Modify (modify datatype / constraint)
ALTER TABLE tab_name MODIFY col_name new_dataType new_constraint;
Truncate ( to delete the table’s data)
Truncate table tab_name ; ( it will delete the data only . later on u can insert)
Joins in Sql :- Inner join :- Returns records that have matching value in both table
Select col1 ,col2 ,col3 from tabA inner join tabB on tabA.colName= tabB.colName . ( it is not mand that tabB have FK)
In condition we can only compare same datatype column
Left Exclusive join :- select * from student as a left join course as b on a.id=b.id where b.id is null ;
Right Exclusive Join :- select * from student as a right join course as b on a.id=b.id where a.id is null.
select * from student as a left join course as b on a.id=b.id union select * from student as a right join course as b on
a.id=b.id where a.id is null or b.id is null
Self join :- self join is used to connect a table with itself .
Assume we have employee table . in which we have employees details but in the same table we have a column which
name is manager_id . for each employee there is writtern over ther manager_id . and manager also itself a employee
whos information is also in the same table. And manager id actually referencing to emp_id.
Select a.id, a.name , b.name as manager_name from emp as a join emp as b on a.id=b.manager_id .