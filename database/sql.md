What is SQL?
SQL is a standard language for accessing and manipulating databases.

SQL stands for Structured Query Language
SQL lets you access and manipulate databases
SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987
What Can SQL do?
SQL can execute queries against a database
SQL can retrieve data from a database
SQL can insert records in a database
SQL can update records in a database
SQL can delete records from a database
SQL can create new databases
SQL can create new tables in a database
SQL can create stored procedures in a database
SQL can create views in a database
SQL can set permissions on tables, procedures, and views


RDBMS
RDBMS stands for Relational Database Management System.

RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.

The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

Some of The Most Important SQL Commands
SELECT - extracts data from a database
UPDATE - updates data in a database
DELETE - deletes data from a database
INSERT INTO - inserts new data into a database
CREATE DATABASE - creates a new database
ALTER DATABASE - modifies a database
CREATE TABLE - creates a new table
ALTER TABLE - modifies a table
DROP TABLE - deletes a table
CREATE INDEX - creates an index (search key)
DROP INDEX - deletes an index

The SQL SELECT Statement
The SELECT statement is used to select data from a database.
SELECT Syntax
SELECT column1, column2, ...
FROM table_name;

Select ALL Columns
To select ALL columns, without specifying every column name, use the SELECT * syntax:

Example
Select ALL columns from the "Customers" table:

SELECT * FROM Customers;

The SQL SELECT DISTINCT Statement
The SELECT DISTINCT statement is used to return only distinct (unique) values.

SELECT column1, column2, ...
FROM table_name;

The SQL WHERE Clause
The WHERE clause is used to filter records.
The WHERE clause is used to extract only those records that fulfill a specific condition.
WHERE Syntax
SELECT column1, column2, ...
FROM table_name
WHERE condition;

Operators
and, or, not, between, in, like, is null, is not null
(>, <, =, !=, <>, >=, <=)

The SQL ORDER BY
The ORDER BY keyword is used to sort the result-set in ascending or descending order.
The ORDER BY keyword sorts the result-set in ascending order (ASC) by default.
ORDER BY Syntax
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
Combine ASC and DESC
The following SQL statement selects all customers from the "Customers" table, and sorts it ASCENDING by the "Country" and DESCENDING by the "CustomerName" column:
Example
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;

he SQL AND Operator
The WHERE clause can contain one or many AND operators.

The AND operator is used to filter records based on more than one condition.

Note: The AND operator displays a record if all the conditions are TRUE.

The following SQL selects all customers from Spain that starts with the letter 'G':

ExampleGet your own SQL Server
Select all customers where Country is "Spain" AND CustomerName starts with the letter 'G':
SELECT *
FROM Customers
WHERE Country = 'Spain' AND CustomerName LIKE 'G%';

AND Syntax
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;

AND vs. OR
The AND operator displays a record if all the conditions are TRUE.
The OR operator displays a record if any of the conditions are TRUE.

The SQL OR Operator
The WHERE clause can contain one or more OR operators.

The OR operator is used to filter records based on more than one condition.

Note: The OR operator displays a record if any of the conditions are TRUE.

The following SQL selects all customers from Germany OR Spain:

ExampleGet your own SQL Server
Select all customers where Country is "Germany" OR "Spain":
SELECT *
FROM Customers
WHERE Country = 'Germany' OR Country = 'Spain';
OR Syntax
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;


The NOT Operator
The NOT operator is used in the WHERE clause to return all records that DO NOT match the specified criteria. It reverses the result of a condition from true to false and vice-versa.
The NOT operator is also used in combination with other operators to exclude data, such as:

NOT LIKE
NOT BETWEEN
NOT IN
IS NOT NULL
NOT EXISTS
NOT Syntax
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;

The NOT LIKE Operator
The NOT LIKE operator is used in the WHERE clause to exclude rows that match a specified character pattern.

There are two wildcards often used in conjunction with the NOT LIKE operator:

A percent sign % - represents zero, one, or multiple characters
A underscore sign _ - represents a single character
SELECT * FROM Customers
WHERE CustomerName NOT LIKE 'A%';

The NOT BETWEEN Operator
The NOT BETWEEN operator is used in the WHERE clause to select rows where a value falls outside a specified inclusive range.
The NOT BETWEEN operator can be used with numeric, text, or date values.
SELECT * FROM Customers
WHERE CustomerID NOT BETWEEN 10 AND 60;

The NOT IN Operator
The NOT IN operator is used in the WHERE clause to exclude rows that match any value in a specified list or a subquery result set.
SELECT * FROM Customers
WHERE City NOT IN ('Paris', 'London');

NOT Greater Than
The "NOT Greater Than" condition is expressed with the NOT operator in conjunction with the standard greater than or equal to (>=) operator.
SELECT * FROM Customers
WHERE NOT CustomerID > 50;

NOT Less Than
The "NOT Less Than" condition is expressed with the NOT operator in conjunction with the standard less than or equal to (<=) operator.
SELECT * FROM Customers
WHERE NOT CustomerId < 50;
