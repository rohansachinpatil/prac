# prac

ALL DATABASE PRACTICALS — TEXT TRANSCRIPTION

==========================================
PRACTICAL 1 — SQL DDL COMMANDS
==========================================

Aim:
Study of Open-Source Relational Databases: MySQL/Oracle and Design and Develop SQL DDL statements which demonstrate the use of SQL objects such as Table, View, Index, Sequence.

Objective:
To Study of MySQL open source database.

Software/Tools Required:
1. MySQL
2. MySQL Workbench
3. Windows/Linux operating system

THEORY:

What is DBMS?

It stands for Database Management System. It is a collection of interrelated data and a set of programs to access that data.

A system which manages the database is called a Database Management System.

MySQL:

MySQL is a powerful open-source database management system that is widely used for storing and organizing data. It is known for its fast performance, reliability, and ease of use, making it a popular choice for web applications, business data, and other types of data storage.

MySQL is based on Structured Query Language (SQL), a standard language for interacting with databases.

With MySQL, you can create and modify databases, tables, and other database objects, as well as insert, query, and update data.

Characteristics of MySQL:
1. Relational Database Management System (RDBMS).
2. It is secure.
3. Client/Server Architecture.
4. It is scalable.
5. Speed.
6. Memory efficiency.
7. High Performance.

Advantages of MySQL:
1. Open Source.
2. Data Security.
3. Scalability On Demand.
4. Higher Efficiency.
5. 24x7 Server Uptime.
6. Complete Transactional Support.
7. Comprehensive Workflow Control.

Applications of MySQL:
1. Web applications, including Drupal, Joomla, phpBB, and WordPress.
2. Popular websites including Facebook, Flickr, MediaWiki, Twitter and YouTube.
3. Bank Management.
4. College Management.
5. Library Management.

DDL COMMANDS IN SQL

The DDL commands in Structured Query Language are used to create and modify the schema of the database and its objects.

Following are the five DDL commands in SQL:

1. CREATE COMMAND

CREATE is a DDL command used to create databases, tables, triggers and other database objects.

Syntax:

CREATE TABLE table_name
(
    column1 datatype,
    column2 datatype,
    column3 datatype
);

Example:

CREATE TABLE Student
(
    Student_ID INT PRIMARY KEY,
    Student_Name VARCHAR(50),
    Department VARCHAR(50),
    Marks INT
);

Verify the table:

DESC Student;

2. DROP COMMAND

DROP is a DDL command used to delete/remove database objects from the SQL database.

Syntax:

DROP TABLE table_name;

Example:

DROP TABLE Student;

This removes the Student table, its structure, and its data.

Important:

DROP is different from DELETE.

DROP: Removes the table itself.
DELETE: Removes selected/all records.

3. ALTER COMMAND

ALTER is a DDL command which changes or modifies the existing structure of the database.

A. Add a Column

Syntax:

ALTER TABLE table_name
ADD column_name datatype;

Example:

ALTER TABLE Student
ADD Email VARCHAR(100);

B. Modify a Column

Syntax:

ALTER TABLE table_name
MODIFY (column_name datatype);

Example:

ALTER TABLE Student
MODIFY (Last_Name VARCHAR(25));

C. Remove a Column

Syntax:

ALTER TABLE table_name
DROP COLUMN column_name;

Example:

ALTER TABLE Student
DROP COLUMN Age;

4. TRUNCATE COMMAND

The TRUNCATE TABLE command deletes the data inside a table, but not the table itself.

Syntax:

TRUNCATE TABLE Table_Name;

Example:

TRUNCATE TABLE Student;

5. RENAME COMMAND

RENAME is a DDL command which is used to change the name of a database table.

Syntax:

RENAME TABLE Old_Table_Name TO New_Table_Name;

Example:

RENAME TABLE Student TO Student_Details;

CREATE VIEW

A View is a virtual table based on the result of a SQL query.

Syntax:

CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;

Example:

CREATE VIEW High_Marks_Students AS
SELECT Student_ID, Student_Name, Marks
FROM Student
WHERE Marks >= 75;

To display the view:

SELECT * FROM High_Marks_Students;

Drop View:

DROP VIEW High_Marks_Students;

CREATE INDEX

An Index is used to improve the speed of data retrieval.

Syntax:

CREATE INDEX index_name
ON table_name(column_name);

Example:

CREATE INDEX idx_student_name
ON Student(Student_Name);

Now Student_Name can be indexed for queries such as:

SELECT *
FROM Student
WHERE Student_Name = 'Amit';

Drop Index:

DROP INDEX idx_student_name
ON Student;

CREATE SEQUENCE — ORACLE

A Sequence generates sequential numeric values and is commonly used for generating unique IDs.

Note: Oracle supports native sequences. In MySQL, AUTO_INCREMENT is commonly used for this purpose.

Syntax:

CREATE SEQUENCE sequence_name
START WITH initial_value
INCREMENT BY increment_value;

Example:

CREATE SEQUENCE Student_Seq
START WITH 101
INCREMENT BY 1;

Generate the next value:

SELECT Student_Seq.NEXTVAL
FROM dual;

SUMMARY OF DDL COMMANDS

CREATE: Creates database objects.
ALTER: Modifies object structure.
DROP: Removes database object.
TRUNCATE: Removes all records.
RENAME: Changes object name.
CREATE VIEW: Creates a virtual table.
CREATE INDEX: Creates an index.
CREATE SEQUENCE: Generates sequential numbers.

CONCLUSION:

In this practical we learned about all the basic concepts of DBMS, its advantages and also learned about database software (MySQL software), characteristics, advantages, applications and DDL commands for database creation.


==========================================
PRACTICAL 2 — SQL DML, OPERATORS, JOINS, SUBQUERIES AND VIEWS
==========================================

AIM:

Design at least 10 SQL queries for suitable database application using SQL DML statements: Insert, Select, Update, Delete with operators, functions, and set operator, all types of Joins, Sub-Query and View.

Objective:
1. To Study of MySQL open source database.
2. To study DML queries.
3. To study Set operators.

Prerequisite:
Basic database concept, DDL Commands.

THEORY:

(2-A) DML STATEMENTS

1. DML (Data Manipulation Language)

Data manipulation capabilities of DML allow one to retrieve contents of the database.

DML can be used for the following operations:

1. INSERT
2. UPDATE
3. DELETE

1.1 INSERT

To insert data into MySQL table, we need to use SQL INSERT INTO command.

Syntax:

1. Specify all column names:

INSERT INTO table_name
(col1, col2, col3, ..., coln)
VALUES
(val1, val2, val3, ..., valn);

2. Specify specific columns:

INSERT INTO table_name(col1, col2)
VALUES (val1, val2);

3. Without specifying column name:

INSERT INTO table_name
VALUES (val1, val2, val3, ..., valn);

4. To insert more than one row:

INSERT INTO table_name
(col1, col2, col3)
VALUES
(val1, val2, val3),
(val1, val2, val3);

To insert string data types, it is required to keep all the values into double or single quotes.

Example: "value".

1.2 UPDATE

There may be a requirement where existing data in a MySQL table needs to be modified.

We can do so by using SQL UPDATE command.

1. To update all rows:

UPDATE table_name
SET attribute = value;

2. To update specific rows:

UPDATE table_name
SET attribute = value
WHERE search_condition;

We can specify any condition using WHERE clause.

The WHERE clause is very useful when we want to update selected rows in a table.

1.3 DELETE

If we want to delete a record from any MySQL table, then we can use SQL command DELETE FROM.

Syntax:

1. To delete all rows:

DELETE FROM table_name;

2. To delete specific rows:

DELETE FROM table_name
WHERE search_condition;

If WHERE clause is not specified, then all the records will be deleted from the given MySQL table.

1.4 SELECT

The SQL SELECT command is used to fetch data from MySQL database.

1. To select all rows:

SELECT * FROM table_name;

2. To select specific columns:

SELECT col1, col2
FROM table_name;

3. To select distinct values:

SELECT DISTINCT col_name
FROM table_name;

4. To select rows with search condition:

SELECT *
FROM table_name
WHERE search_condition;

We can use one or more tables separated by comma to include various conditions using a WHERE clause.

We can specify star (*) in place of fields. In this case, SELECT will return all the fields.

We can specify an offset using OFFSET from where SELECT will start returning records.

By default offset is zero.

We can limit the number of returned records using LIMIT attribute.

(2-B) OPERATORS AND SET OPERATORS

What is SQL Operator?

The operators are symbols and keywords that are used to perform operations with values.

These operators are used with SQL clauses such as:
1. SELECT
2. WHERE
3. ON

Types of Operators:

Arithmetic operators:
A comparison (or relational) operator is a mathematical symbol which is used to compare two values.

The result of a comparison can be TRUE, FALSE, or UNKNOWN.

SQL Assignment operator:
In SQL, the assignment operator (=) assigns a value to a variable or to a column or field of a table.

SET OPERATORS IN SQL

Set operators are used to combine the results of two or more SELECT statements.

(2-C) TYPES OF JOINS

SQL JOINS:

The SQL JOIN joins two tables based on a common column and selects records that have matching values in these columns.

SQL JOIN Syntax:

SELECT columns_from_both_tables
FROM table1
JOIN table2
ON table1.column1 = table2.column2;

Example:

SELECT Customers.customer_id,
       Customers.first_name,
       Orders.item
FROM Customers
JOIN Orders
ON Customers.customer_id = Orders.customer_id;

Types of SQL JOINS:

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. FULL OUTER JOIN

INNER JOIN:

It joins two tables on a common column and selects rows that have matching values in these columns.

Syntax:

SELECT columns_from_both_tables
FROM table1
INNER JOIN table2
ON table1.column1 = table2.column2;

Example:

SELECT Customers.customer_id,
       Customers.first_name,
       Orders.amount
FROM Customers
INNER JOIN Orders
ON Customers.customer_id = Orders.customer;

SQL INNER JOIN WITH AS ALIAS

We can use AS aliases inside INNER JOIN to make our query short and clean.

Example:

SELECT C.cat_name, P.prod_title
FROM Categories AS C
INNER JOIN Products AS P
ON C.cat_id = P.cat_id;

LEFT JOIN:

It joins two tables based on a common column. It selects records that have matching values and the remaining rows from the left table.

Syntax:

SELECT columns_from_both_tables
FROM table1
LEFT JOIN table2
ON table1.column1 = table2.column2;

Example:

SELECT Customers.customer_id,
       Customers.first_name,
       Orders.amount
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer;

RIGHT JOIN:

It joins two tables based on a common column. It selects matching records and the remaining rows from the right table.

Syntax:

SELECT columns_from_both_tables
FROM table1
RIGHT JOIN table2
ON table1.column1 = table2.column2;

Example:

SELECT Customers.customer_id,
       Customers.first_name,
       Orders.item
FROM Customers
RIGHT JOIN Orders
ON Customers.customer_id = Orders.customer_id;

FULL OUTER JOIN:

It joins two tables based on a common column. It selects matching records and the remaining rows from both tables.

Syntax:

SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column1 = table2.column2;

Example:

SELECT Customers.customer_id,
       Customers.first_name,
       Orders.amount
FROM Customers
FULL OUTER JOIN Orders
ON Customers.customer_id = Orders.customer_id;

(2-D) VIEW

Views in SQL are considered as a virtual table. A view also contains rows and columns.

To create the view, we can select the fields from one or more tables present in the database.

A view can either have specific rows based on certain conditions or all the rows of a table.

Advantages of View:

1. Complexity:
Views help to reduce complexity. Different views can be created on the same base table for different users.

2. Security:
It increases security by excluding sensitive information from the view.

3. Query Simplicity:
It helps to simplify commands from the user. A view can draw data from several different tables and present it as a single table.

4. Consistency:
A view can present a consistent, unchanged image of the structure of the database.

5. Data Integrity:
If data is accessed and entered through a view, the DBMS can automatically check the data to ensure that it meets the specified integrity constraints.

6. Storage Capacity:
Views take very little space to store the data.

Disadvantages of View:

1. You cannot INSERT if the base table has any NOT NULL column that does not appear in the view.

2. You cannot INSERT or UPDATE if any of the columns referenced contains group functions or columns defined by expression.

3. You cannot execute INSERT, UPDATE, DELETE statements on a view if the WITH READ ONLY option is enabled.

4. You cannot create a view on temporary tables.

CREATING VIEW FROM A SINGLE TABLE

Syntax:

CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;

Example:

CREATE VIEW DetailsView AS
SELECT NAME, ADDRESS
FROM Student_Details
WHERE STU_ID < 4;

CREATING VIEW FROM MULTIPLE TABLES

A view from multiple tables can be created by including multiple tables in the SELECT statement.

Example:

CREATE VIEW MarksView AS
SELECT Student_Detail.NAME,
       Student_Detail.ADDRESS,
       Student_Marks.MARKS
FROM Student_Detail, Student_Marks
WHERE Student_Detail.NAME = Student_Marks.NAME;

TO DISPLAY DATA OF VIEW

SELECT * FROM MarksView;

DELETING VIEW

Syntax:

DROP VIEW view_name;

Example:

DROP VIEW MarksView;

CONCLUSION:

Thus we have successfully studied different operators, DML statements, Joins, and views in SQL.
