This note is created by sujay singh 
-----------------------------------------------------------

Command for create new database :-
```
	Create user <user_name> identified by <password>;
	
	1. Create user Employee identified by Emp;
	2. Grant dba to Employee;
	3. Conn Employee/Emp;
	4. Show user;
	5. Exit;
```

Data type :-
```
	1. varchar
	2. varchar2
	3. char
	4. number
	5. date
	6. clob       4gb
	7. blob       4gb
	8. bfile      4gb
```

Create table in Employee database :-
```
	Create table Emp
	(
		empId    int,
		empName  varchar(20),
		empGnd   varchar(10),
		empDob   date,
		empSal   int,
		empAdd   varchar,
	)
```

View all the object ( 1. table, 2. view, 3. synonym ):-
```
	Select * from tab;
```

View table structure:-
```
	desc <table_name>;
	desc Emp;
```

Tools of oracle
```
	sqlplus (SQL, PLSQL)
	farms
	report
	exp/imp
```

Remove table :-
```
	Drop table <table_name>;
	Drop table Emp;
```

Rename existing table :-
```
	rename <old_table_name> to <new_table_name>;
	rename Emp to Workers;
```

DML - Data Manipulation Language  -   ( select, insert, delete )

1. Insert command :- insert command is used to insert data in exist table :-
```
	insert into <table_name> values (val1, val2,.......,valn);
	1. insert into Workers (empId, empName, empDob, empGnd, empSal, empAdd) values 
	   (1, 'Mohan', 'Male', 22-02-2002, 22000, 'patna');
	2. insert into Workers values(2, 'Sohan', 'Male', 03-04-1998, 'Mumbai');
```

2.  View all record from table :-
```
	select * from <table_name>;
	select * from Workers;
```

3. View all columns and rows using where condition :-
```
	select * from Workers where empGnd = 'Male';
	select * from Workers where empSal > 20000;
	select * from Workers where empSal > 20000 and empGnd = 'Male';
```

4.  View all record specific field from table :- 
```
	select empId empName from Workers;
	select empName empSal from Workers;
```

4.  View all record specific field from table with where clause :- 
```
	select empName empSal from Workers where empGnd = 'Male';
	select empId empName from Workers where empSal > 20000 and empAdd = 'bihar';
```

5. In order to select data that is ascending or descending order with the use of order by clause :-
```
	select * from <table_name> order by <field_name>;
	select * from Worker order by empName;
	select * from Worker order by empName and empSal;
```

6. View unique data using distinct clause distinct :- the distinct clause can be used to eliminate duplicate rows from a set of records;
```
	select distinct <field_name> from <table_name>;
	select distinct empSal from Worker;
	select distinct empGnd from Worker;
	select distinct empAdd from Worker
```

Modify table structure using alter command :-
Alter command is used to modify exist table structure like "add new column" and "constraint modify" and "data type modify" and  "size drop" exist column and drop exist "constraint".

1. Add new column :-
```
	alter table <table_name> add (<new_column_name> datatype(size),......,n);
	alter table Worker add (empPho number(10), empEmail varchar2(50));
```

2. Add constraint :-
```
	alter table Worker add Primary key(empEmail);
	alter table Worker add Not Null(empName);
```

3. Modify datatype :-
```
	alter table Worker modify (empId number(5), empName varchar2(20));
```

4. Modify size :-
```
	alter table Worker modify (empId number(10), empName varchar2(50));
```

5. Drop exist column :-
```
	alter table <table_name> drop column <column_name>;
	alter table Worker drop column empEmail;
```

6. Drop exist constraint :-
```
	alter table <table_name> drop constraint <column_name>;
	alter table Worker drop primary key empEmail;
	alter table Worker drop constraint primary key empId;
```

Delete operation using delete command :-
Delete command is use for remove data from exist table

1. Remove all rows from table :-
```
	delete from <table_name>;
	delete from Worker;
```

2. Delete table name :-
```
	delete <table_name>;
	delete Worker;
```

3.  Remove all of specific rows by where and condition :-
```
	delete from <table_name> where <condition>;
	delete from Worker where empName = 'Mohan';
	delete from Worker where empSal < 20000;
```

Modify data using update command :-
Update command is used to modify data from exist table.

1. Update of all rows.
```
	update <table_name> set (col1 = exp1, col2 - exp2,........,n);
	update Worker set (empId = empNo, empAdd = empCity);
	update Worker set (empSal = empSal + 2000, empName = 'Mr' + empName);
```

2. Updating of selected rows.
```
	update <table_name> set col1 = exp1, col2 = exp2,......,n;
	update Worker set empName = 'Sujay', empNo = '987654321' where empId = 1;
	update Worker set empAdd = 'Delhi', empGnd = 'Female' where empId = 1 and empName = 'Sohan';
```

Operator :-
1. Arithmetical operator ( +, -, *, / )
```
	select 12*20-30/2 from dual;
	select upper('mr aman kumar');
	select empId, empName, empSal*0.5 from Worker;
	select empId, empName "orgSal", empSal*0.5 "incSal" from Worker;
```

Set heading off
Set heading on

Tittle "" 

Pattern matching :-
1. Like operator :- The like operator comparison one string to another string this is achieved by using two special character ( %, .)

```
	Question 
	1. Retrieve all the rows from table <table_name> whose name start with the letter'o'?
	Ans:- select * from <table_name> where name like o%.
	
	2. Retrive all the <table_name> whose name end with the letter 'r'?
	Ans:- select * from <table_name> where name like %r;

	3. Retrive all the rows from table <table_name> whose name start with the letter 'a' and end with the letter 'h'?
	Ans:- select * from <table_name> where name like 'a%h';

	4. Retrive all the rows from the table <table_name> whose name certain exact letter five?
	Ans:- select * from <table_name> where name like '_____'

	5. Retrive all the rows from table <table_name> whose name at the 2nd letter 'a'?
	Ans:- select * from <table_name> where name like '_a%';

	update Worker set empSal = empSal + 5000 where empSal like '_____'
	delete from Worker where empSal like '______';
```

Logical operator :-
1. And
2. Or
3. Not

And :- The oracle engine will process all rows in a table and display the result only when all of the condition are satisfied
```
	update ppu set fee = fee - 5000 where course = 'bca' and year = 'III' and college = 'coc' and fee > 50000;
```

Or : - 
The oracle engine will process all rows in a table and display the result only where any of the condition are satisfied.
```
	select * from Worker where empId = 1 or empName = 'sohan';
```

Not operator :- 
The oracle engine will process all row in a table display and display the result only those records do not satisfy the in operator in used.
```
	select * from Worker where not (empId = 1 or empName = 'sohan' or empSal =  20000);
```

Between operator :-
In order to select data that is within a range of value the between operator is used to the between that content value within a specify lower and upper limit. the two value in between the range must be link the keyword "and".
```
	select * from Worker where empSal between(20000 and 50000);
	delete * from Worker where empId between(1 and 5);
	update Worker set empSal = empSal + 5000 where empSal between(15000 and 25000)
    and job = 'manager'
 ```

In operator :- 
The relational operator = compare a single value to another value. in case value need to compare to a list of value the in operator is used. the in operator help reduce the need to use 'or' and 'equal' operator.

```
	select * from Worker where empId = 1;
	select * from Worker where empId = 5;
	select * from Worker where empId = 10;
	select * from Worker where empId = 10 or empId = 5;
	select * from Worker where empId in (1, 2, 5, 8, 10);
	select * from Worker where empId not between(1 and 10);
	select * from Worker where empId not in (1, 5, 8, 3, 12, 20);

	NOTE :- There are 1 lakhs data in table and it's format is random then,
		question are we have select data 1 to 20000.
		select * from Worker where rownum < 20001;
```

The concept of grouping :-
Till now all select statement have
1. Retrieve all the rows from table ?
2. Retrieve selected rows from table with the use of where clause ?
3. Retrieve unique rows and column with the use of distinct clause ? 
4. Retrieve rows in a started order that is ascending or descending order with the use of order by clause.

Other than the above clauses there are two other clauses which facility retrieve selective of rows. these are the group by clause and having clause

The group by clause is another section is the select statement this optional clause details oracle to group rows based on distinct value that exist for 	specified column.
```
	select col1,............,coln, groupfunction(argument) from tablename where condition group by col1,.......,coln;

	select sum(empSal) from Worker;
	select sum(empSal) from Worker where dep = 'manager';

	Group by :-
	select dist, count(paputation) from india where state = 'bihar' group by dist;
	select depno, count(empNo), sum(sal) from worker group by depno;
```

