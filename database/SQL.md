# 🌿 SQL Study Notes

> *A calm, bite-sized guide to the fundamentals of SQL. Read it top to bottom, or jump to any topic.*

---

## 📑 Table of Contents

1. [What is SQL?](#-what-is-sql)
2. [What Can SQL Do?](#-what-can-sql-do)
3. [RDBMS](#-rdbms)
4. [Important SQL Commands](#-important-sql-commands)
5. [SELECT](#-select)
6. [SELECT DISTINCT](#-select-distinct)
7. [WHERE](#-where)
8. [Operators (overview)](#-operators)
9. [ORDER BY](#-order-by)
10. [AND / OR](#-and--or)
11. [NOT](#-not)
12. [INSERT INTO](#-insert-into)
13. [NULL Values](#-null-values)
14. [UPDATE](#-update)
15. [DELETE & DROP](#-delete--drop)
16. [SELECT TOP / LIMIT](#-select-top--limit)
17. [Aggregate Functions](#-aggregate-functions)
18. [MIN()](#-min)
19. [MAX()](#-max)
20. [COUNT()](#-count)
21. [SUM()](#-sum)
22. [AVG()](#-avg)
23. [LIKE](#-like)
24. [Wildcards](#-wildcards)
25. [IN](#-in)
26. [BETWEEN](#-between)
27. [Aliases](#-aliases)
28. [UNION](#-union)
29. [GROUP BY](#-group-by)
30. [HAVING](#-having)
31. [EXISTS](#-exists)
32. [ANY and ALL](#-any-and-all)
33. [SELECT INTO](#-select-into)
34. [INSERT INTO SELECT](#-insert-into-select)
35. [CASE](#-case)
36. [NULL Functions](#-null-functions)
37. [Stored Procedures](#-stored-procedures)
38. [Comments](#-comments)
39. [SQL Operators (in depth)](#-sql-operators-in-depth)
40. [Quick Cheat Sheet](#-quick-cheat-sheet)

> 📝 *Joins are intentionally skipped in these notes.*

---

## 📘 What is SQL?

**SQL** = **S**tructured **Q**uery **L**anguage, the standard language for accessing and manipulating databases.

| 🗓️ Year | 🏛️ Milestone |
|:------:|--------------|
| 1986 | Became an **ANSI** standard (American National Standards Institute) |
| 1987 | Became an **ISO** standard (International Organization for Standardization) |

---

## 🛠️ What Can SQL Do?

| 🎯 Action | 💬 Meaning |
|-----------|-----------|
| Execute queries | Ask questions of a database |
| Retrieve data | Read records |
| Insert records | Add new data |
| Update records | Change existing data |
| Delete records | Remove data |
| Create databases | Make new databases |
| Create tables | Define new structures |
| Create stored procedures | Save reusable logic |
| Create views | Save virtual tables |
| Set permissions | Control access to tables, procedures, and views |

---

## 🗄️ RDBMS

**RDBMS** = **R**elational **D**atabase **M**anagement **S**ystem.

- 🧱 It is the **basis for SQL** and all modern database systems.
- 🏷️ Examples: **MS SQL Server, IBM DB2, Oracle, MySQL, Microsoft Access**
- 📊 Data lives in **tables**, collections of related data made of **columns** and **rows**.

---

## ⌨️ Important SQL Commands

| Command | What it does |
|---------|--------------|
| `SELECT` | Extracts data from a database |
| `UPDATE` | Updates data in a database |
| `DELETE` | Deletes data from a database |
| `INSERT INTO` | Inserts new data into a database |
| `CREATE DATABASE` | Creates a new database |
| `ALTER DATABASE` | Modifies a database |
| `CREATE TABLE` | Creates a new table |
| `ALTER TABLE` | Modifies a table |
| `DROP TABLE` | Deletes a table |
| `CREATE INDEX` | Creates an index (search key) |
| `DROP INDEX` | Deletes an index |

---

## 🔍 SELECT

Used to **select data** from a database.

```sql
SELECT column1, column2, ...
FROM table_name;
```

**Select ALL columns** with `*`:

```sql
SELECT * FROM Customers;
```

---

## ✨ SELECT DISTINCT

Returns only **distinct (unique)** values, with no duplicates.

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

> 💡 **Tip:** Don't forget the word `DISTINCT`. Without it, you just get a normal `SELECT`.

---

## 🎯 WHERE

Used to **filter records**, extracting only those that fulfill a specific condition.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

---

## ⚙️ Operators

A quick overview (the full breakdown is in [SQL Operators (in depth)](#-sql-operators-in-depth) further down).

| Type | Operators |
|------|-----------|
| 🔗 Logical / special | `AND`, `OR`, `NOT`, `BETWEEN`, `IN`, `LIKE`, `IS NULL`, `IS NOT NULL` |
| ⚖️ Comparison | `>`  `<`  `=`  `!=`  `<>`  `>=`  `<=` |

---

## 🔃 ORDER BY

Sorts the result set in **ascending** or **descending** order.

- Default is **ascending (`ASC`)**.

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

**Combine ASC and DESC.** Sort by Country (A→Z), then CustomerName (Z→A):

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

---

## 🤝 AND / OR

| Operator | Shows a record if... |
|:--------:|----------------------|
| **AND** | **ALL** conditions are TRUE |
| **OR** | **ANY** condition is TRUE |

### AND

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

*Example: customers from Spain whose name starts with 'G'*

```sql
SELECT *
FROM Customers
WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
```

### OR

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

*Example: customers from Germany or Spain*

```sql
SELECT *
FROM Customers
WHERE Country = 'Germany' OR Country = 'Spain';
```

---

## 🚫 NOT

Returns records that **do NOT** match the condition. It flips TRUE ↔ FALSE.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

Often combined with other operators: `NOT LIKE` · `NOT BETWEEN` · `NOT IN` · `IS NOT NULL` · `NOT EXISTS`

### 🔤 NOT LIKE

Excludes rows matching a pattern. Wildcards:

- `%` → zero, one, or many characters
- `_` → exactly one character

```sql
SELECT * FROM Customers
WHERE CustomerName NOT LIKE 'A%';
```

### 📏 NOT BETWEEN

Selects values **outside** an inclusive range (works with numbers, text, dates).

```sql
SELECT * FROM Customers
WHERE CustomerID NOT BETWEEN 10 AND 60;
```

### 📋 NOT IN

Excludes rows matching **any value** in a list or subquery.

```sql
SELECT * FROM Customers
WHERE City NOT IN ('Paris', 'London');
```

### ⬆️ NOT Greater Than

```sql
SELECT * FROM Customers
WHERE NOT CustomerID > 50;
```

### ⬇️ NOT Less Than

```sql
SELECT * FROM Customers
WHERE NOT CustomerID < 50;
```

---

## ➕ INSERT INTO

Adds **new records** to a table. There are two ways:

**Syntax 1: specify columns and values**

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

**Syntax 2: values for ALL columns** (column names can be omitted, but the order must match the table)

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

**Insert multiple rows** at once:

```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES
('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway'),
('Greasy Burger', 'Per Olsen', 'Gateveien 15', 'Sandnes', '4306', 'Norway'),
('Tasty Tee', 'Finn Egan', 'Streetroad 19B', 'Liverpool', 'L1 0AA', 'UK');
```

---

## 🕳️ NULL Values

- A field can be **optional**, so a record can be saved without a value in it.
- **NULL** = unknown, missing, or inapplicable data. It's a *placeholder for "no data"*, not a value itself.

> ⚠️ You **cannot** test for NULL with `=`, `<`, or `<>`. Use `IS NULL` / `IS NOT NULL`.

```sql
-- Find empty values
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

-- Find non-empty values
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

---

## ✏️ UPDATE

Modifies **existing records** in a table.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

*Example: update one customer's contact and city*

```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
WHERE CustomerID = 1;
```

> 🛑 **Careful:** forgetting `WHERE` in an `UPDATE` changes **every** row!

---

## 🗑️ DELETE & DROP

| Goal | Command | Result |
|------|---------|--------|
| Delete specific rows | `DELETE FROM table_name WHERE condition;` | Only matching rows removed |
| Delete **all** rows | `DELETE FROM table_name;` | Rows gone; table structure, attributes & indexes stay intact |
| Delete the **whole table** | `DROP TABLE table_name;` | Table removed completely |

> 🛑 **Careful:** forgetting `WHERE` in a `DELETE` removes **every** row!

---

## 🔝 SELECT TOP / LIMIT

Limits the **number of records** returned. Handy on big tables. The syntax differs between database systems:

| 🗄️ Database | Syntax |
|-------------|--------|
| **SQL Server / MS Access** | `SELECT TOP 3 * FROM Customers;` |
| **MySQL** | `SELECT * FROM Customers LIMIT 3;` |
| **Oracle** | `SELECT * FROM Customers FETCH FIRST 3 ROWS ONLY;` |

**Percentage of rows** (SQL Server / MS Access):

```sql
SELECT TOP 50 PERCENT * FROM Customers;
```

**Combine with WHERE** and **ORDER BY**:

```sql
SELECT TOP 3 * FROM Customers
WHERE Country = 'Germany';

SELECT TOP 3 * FROM Customers
ORDER BY CustomerName DESC;
```

> 💡 **Tip:** use `ORDER BY` with it, otherwise "the first 3 rows" has no guaranteed meaning.

---

## 🧮 Aggregate Functions

A function that **calculates on a set of values and returns a single value**.

- Often used with **`GROUP BY`**, which splits results into groups so the function returns one value *per group*.
- They **ignore NULL values** (except `COUNT(*)`).

| Function | Returns |
|----------|---------|
| `MIN()` | Smallest value of a column |
| `MAX()` | Largest value of a column |
| `COUNT()` | Number of rows in a set |
| `SUM()` | Sum of a numeric column |
| `AVG()` | Average of a numeric column |

---

## 📉 MIN()

Returns the **smallest value** of the selected column. Works with numeric, string, and date types.

```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

*Example:*

```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

---

## 📈 MAX()

Returns the **largest value** of the selected column. Works with numeric, string, and date types.

```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

*Example:*

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products;
```

---

## 🔢 COUNT()

Returns the **number of rows** that match a criterion.

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

| Form | Counts |
|------|--------|
| `COUNT(*)` | All rows (including NULLs) |
| `COUNT(column)` | Rows where the column is **not NULL** |
| `COUNT(DISTINCT column)` | Number of **unique** non-NULL values |

```sql
SELECT COUNT(*) FROM Products;

SELECT COUNT(ProductName) FROM Products WHERE Price > 20;

SELECT COUNT(DISTINCT Price) FROM Products;
```

---

## ➕ SUM()

Returns the **total sum** of a numeric column.

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

*Example:*

```sql
SELECT SUM(Quantity)
FROM OrderDetails;
```

SUM also accepts **expressions**:

```sql
SELECT SUM(Quantity * 10)
FROM OrderDetails;
```

---

## 📊 AVG()

Returns the **average value** of a numeric column. NULL values are ignored.

```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

*Example: products priced above the average*

```sql
SELECT * FROM Products
WHERE Price > (SELECT AVG(Price) FROM Products);
```

---

## 🔎 LIKE

Searches for a **pattern** in a column. Used inside `WHERE`, with two wildcards:

- `%` → zero, one, or many characters
- `_` → exactly one character

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column LIKE pattern;
```

| Pattern | Matches |
|---------|---------|
| `LIKE 'a%'` | Starts with "a" |
| `LIKE '%a'` | Ends with "a" |
| `LIKE '%or%'` | Contains "or" anywhere |
| `LIKE '_r%'` | "r" is the **second** character |
| `LIKE 'a_%'` | Starts with "a" and is at least 2 characters long |
| `LIKE 'a__%'` | Starts with "a" and is at least 3 characters long |
| `LIKE 'a%o'` | Starts with "a" and ends with "o" |

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```

> 💡 **Tip:** `LIKE` without a wildcard behaves just like `=`.

---

## 🃏 Wildcards

Substitute for **one or more characters** in a string. Used **only with `LIKE`** (and `NOT LIKE`).

| Wildcard | Represents |
|:--------:|------------|
| `%` | Zero, one, or multiple characters |
| `_` | Exactly one character |
| `[]` | Any single character **within** the brackets |
| `^` | Any single character **not** in the brackets (inside `[]`) |
| `-` | A **range** of characters (inside `[]`) |

> ⚠️ `[]`, `^` and `-` work in **SQL Server** (and MS Access, with `!` instead of `^`). MySQL and Oracle mainly support `%` and `_`. MS Access also uses `*` and `?` in place of `%` and `_`.

```sql
-- City starts with b, s, or p
SELECT * FROM Customers
WHERE City LIKE '[bsp]%';

-- City starts with a, b, or c (range)
SELECT * FROM Customers
WHERE City LIKE '[a-c]%';

-- City does NOT start with b, s, or p
SELECT * FROM Customers
WHERE City LIKE '[^bsp]%';

-- or equivalently
SELECT * FROM Customers
WHERE City NOT LIKE '[bsp]%';
```

---

## 📋 IN

A shorthand for **multiple `OR` conditions**. Matches any value in a list (or a subquery result).

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

```sql
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');
```

**With a subquery:**

```sql
SELECT * FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders);
```

Negate it with `NOT IN`:

```sql
SELECT * FROM Customers
WHERE Country NOT IN ('Germany', 'France', 'UK');
```

---

## 📏 BETWEEN

Selects values within a **given range** (numbers, text, or dates). The range is **inclusive**: begin and end values are included.

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

```sql
-- Numbers
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;

-- Text (alphabetical range)
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;

-- Dates
SELECT * FROM Orders
WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31';
```

Combine with `NOT` and `IN`:

```sql
SELECT * FROM Products
WHERE Price NOT BETWEEN 10 AND 20;

SELECT * FROM Products
WHERE (Price BETWEEN 10 AND 20)
AND CategoryID NOT IN (1, 2, 3);
```

> ⚠️ Behavior with text and date edges can differ between databases, so always test.

---

## 🏷️ Aliases

**Temporary names** for tables or columns. They make output more readable and exist **only for the duration of that query**.

```sql
-- Column alias
SELECT column_name AS alias_name
FROM table_name;

-- Table alias
SELECT column_name(s)
FROM table_name AS alias_name;
```

```sql
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;
```

**Alias with spaces:** wrap it in square brackets or double quotes.

```sql
SELECT ProductName AS [My Great Products]
FROM Products;

SELECT ProductName AS "My Great Products"
FROM Products;
```

**Concatenate columns into one alias:**

```sql
-- SQL Server
SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;

-- MySQL
SELECT CustomerName, CONCAT(Address, ', ', PostalCode, ', ', City, ', ', Country) AS Address
FROM Customers;
```

**Table alias** (shorter to type, great in complex queries):

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName = 'Around the Horn' AND c.CustomerID = o.CustomerID;
```

---

## 🧩 UNION

Combines the result sets of **two or more `SELECT` statements**.

**Rules:**

- Every `SELECT` must have the **same number of columns**
- Columns must have **similar data types**
- Columns must be in the **same order**

```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

| Operator | Duplicates |
|----------|-----------|
| `UNION` | **Removed** (distinct values only) |
| `UNION ALL` | **Kept** |

```sql
-- Distinct cities from both tables
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;

-- With duplicates
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers
ORDER BY City;

-- With WHERE
SELECT City, Country FROM Customers
WHERE Country = 'Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country = 'Germany'
ORDER BY City;
```

> 💡 **Tip:** column names in the result come from the **first** `SELECT`. Add a label column to tell the sources apart:
> `SELECT 'Customer' AS Type, ContactName, City FROM Customers UNION SELECT 'Supplier', ContactName, City FROM Suppliers;`

---

## 🗂️ GROUP BY

Groups rows that have **the same values** into summary rows, e.g. "number of customers in each country". Almost always used with aggregate functions.

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

```sql
-- Customers per country
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;

-- Same, sorted high → low
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
```

> 💡 Every non-aggregated column in `SELECT` must appear in `GROUP BY`.

---

## 🧱 HAVING

Filters **groups** after aggregation. It exists because `WHERE` **cannot** be used with aggregate functions.

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

```sql
-- Countries with more than 5 customers
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;

-- Same, sorted high → low
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC;
```

| Clause | Filters | Runs |
|--------|---------|------|
| `WHERE` | Individual **rows** | **Before** grouping |
| `HAVING` | **Groups** (can use aggregates) | **After** grouping |

---

## ❓ EXISTS

Tests whether a **subquery returns any record**. Returns TRUE if the subquery returns one or more rows.

```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS
  (SELECT column_name FROM table_name WHERE condition);
```

*Example: suppliers that have a product priced under 20*

```sql
SELECT SupplierName
FROM Suppliers
WHERE EXISTS
  (SELECT ProductName FROM Products
   WHERE Products.SupplierID = Suppliers.SupplierID AND Price < 20);
```

Use `NOT EXISTS` for the opposite.

---

## 🎚️ ANY and ALL

Compare a value against the **values returned by a subquery**.

| Operator | Returns TRUE if... |
|:--------:|--------------------|
| **ANY** | the comparison is TRUE for **at least one** subquery value |
| **ALL** | the comparison is TRUE for **every** subquery value |

### ANY

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
  (SELECT column_name FROM table_name WHERE condition);
```

```sql
-- Products that appear in an order with Quantity = 10
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
```

### ALL

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
  (SELECT column_name FROM table_name WHERE condition);
```

```sql
-- TRUE only if EVERY OrderDetails row for the product has Quantity = 10
SELECT ProductName
FROM Products
WHERE ProductID = ALL
  (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
```

> 💡 `operator` can be any comparison operator: `=` `<>` `!=` `>` `>=` `<` `<=`.

---

## 📥 SELECT INTO

**Copies data** from one table into a **new** table.

```sql
SELECT *
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;
```

```sql
-- Backup copy
SELECT * INTO CustomersBackup2024
FROM Customers;

-- Only some columns
SELECT CustomerName, ContactName INTO CustomersBackup2024
FROM Customers;

-- Only some rows
SELECT * INTO CustomersGermany
FROM Customers
WHERE Country = 'Germany';

-- Copy the structure only (no data)
SELECT * INTO newtable
FROM oldtable
WHERE 1 = 0;
```

> ⚠️ **MySQL** doesn't support `SELECT INTO` this way. Use:
> `CREATE TABLE newtable AS SELECT * FROM oldtable;`
> 💡 The new table gets the column names and types of the old one; use `AS` to rename columns.

---

## 📤 INSERT INTO SELECT

Copies data from one table and **inserts it into an existing table**. Existing rows in the target table are unaffected.

> Data types in source and target must **match**.

```sql
-- All columns
INSERT INTO table2
SELECT * FROM table1
WHERE condition;

-- Chosen columns
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```

```sql
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers;

INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers
WHERE Country = 'Germany';
```

| Command | Target table |
|---------|--------------|
| `SELECT INTO` | Must **not** exist (it is created) |
| `INSERT INTO SELECT` | Must **already** exist |

---

## 🔀 CASE

SQL's **if-then-else**. It goes through the conditions and returns a value when the **first** condition is met. If none match, it returns the `ELSE` value, or **NULL** if there is no `ELSE`.

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

```sql
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```

**Custom sort order:** sort by City, but by Country if City is NULL:

```sql
SELECT CustomerName, City, Country
FROM Customers
ORDER BY
(CASE
    WHEN City IS NULL THEN Country
    ELSE City
END);
```

---

## 🛟 NULL Functions

Handle NULLs in calculations. Any arithmetic with `NULL` returns `NULL`, so replace NULLs with a default first.

| 🗄️ Database | Function |
|-------------|----------|
| **SQL Server** | `ISNULL(expr, replacement)` |
| **MySQL** | `IFNULL(expr, replacement)` or `COALESCE(...)` |
| **Oracle** | `NVL(expr, replacement)` |
| **MS Access** | `IsNull(expr)` |
| **Most systems** | `COALESCE(expr1, expr2, ...)` returns the first non-NULL |

*Problem:* if `UnitsOnOrder` is NULL, this returns NULL:

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + UnitsOnOrder)
FROM Products;
```

*Fix:*

```sql
-- MySQL
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products;

-- SQL Server
SELECT ProductName, UnitPrice * (UnitsInStock + ISNULL(UnitsOnOrder, 0))
FROM Products;

-- Oracle
SELECT ProductName, UnitPrice * (UnitsInStock + NVL(UnitsOnOrder, 0))
FROM Products;

-- Works almost everywhere
SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))
FROM Products;
```

---

## 📦 Stored Procedures

**Saved SQL code** you can reuse again and again. It can also accept **parameters**. (Syntax below is **SQL Server**.)

```sql
CREATE PROCEDURE procedure_name
AS
sql_statement
GO;
```

**Execute it:**

```sql
EXEC procedure_name;
```

```sql
CREATE PROCEDURE SelectAllCustomers
AS
SELECT * FROM Customers
GO;

EXEC SelectAllCustomers;
```

**With one parameter:**

```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;

EXEC SelectAllCustomers @City = 'London';
```

**With multiple parameters:**

```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;

EXEC SelectAllCustomers @City = 'London', @PostalCode = 'WA1 1DP';
```

---

## 💬 Comments

Text that SQL **ignores**. Use them to explain code or temporarily disable parts of a statement.

| Style | Syntax |
|-------|--------|
| Single line | `-- comment` |
| Multi-line | `/* comment ... */` |

```sql
-- Select all customers:
SELECT * FROM Customers;

SELECT * FROM Customers -- WHERE City = 'Berlin';

/* Select all the columns
of all the records
in the Customers table: */
SELECT * FROM Customers;

SELECT CustomerName, /*City,*/ Country FROM Customers;
```

> ⚠️ MS Access does not support `--` or `/* */` comments, so check your system.

---

## 🧰 SQL Operators (in depth)

### ➗ Arithmetic Operators

| Operator | Meaning |
|:--------:|---------|
| `+` | Add |
| `-` | Subtract |
| `*` | Multiply |
| `/` | Divide |
| `%` | Modulo (remainder) |

```sql
SELECT 30 + 20;   -- 50
SELECT 30 - 20;   -- 10
SELECT 30 * 20;   -- 600
SELECT 30 / 20;   -- 1 (integer division in some systems)
SELECT 30 % 20;   -- 10
```

### 🔧 Bitwise Operators

| Operator | Meaning |
|:--------:|---------|
| `&` | Bitwise AND |
| `\|` | Bitwise OR |
| `^` | Bitwise exclusive OR (XOR) |

### ⚖️ Comparison Operators

| Operator | Meaning |
|:--------:|---------|
| `=` | Equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |
| `<>` | Not equal to (`!=` also works in most systems) |

```sql
SELECT * FROM Products WHERE Price = 18;
SELECT * FROM Products WHERE Price > 30;
SELECT * FROM Products WHERE Price < 30;
SELECT * FROM Products WHERE Price >= 30;
SELECT * FROM Products WHERE Price <= 30;
SELECT * FROM Products WHERE Price <> 18;
```

### 🧮 Compound Operators

Shorthand: *do the operation, then assign the result back*.

| Operator | Meaning | Same as |
|:--------:|---------|---------|
| `+=` | Add equals | `x = x + y` |
| `-=` | Subtract equals | `x = x - y` |
| `*=` | Multiply equals | `x = x * y` |
| `/=` | Divide equals | `x = x / y` |
| `%=` | Modulo equals | `x = x % y` |
| `&=` | Bitwise AND equals | `x = x & y` |
| `^=` | Bitwise exclusive OR equals | `x = x ^ y` |
| `\|=` | Bitwise OR equals | `x = x \| y` |

> ⚠️ Compound operators are supported mainly in **SQL Server**.

### 🔗 Logical Operators

| Operator | TRUE if... |
|:--------:|------------|
| `ALL` | **all** of the subquery values meet the condition |
| `AND` | **all** the conditions separated by AND are TRUE |
| `ANY` | **any** of the subquery values meet the condition |
| `BETWEEN` | the operand is within the range |
| `EXISTS` | the subquery returns one or more records |
| `IN` | the operand equals one of a list of expressions |
| `LIKE` | the operand matches a pattern |
| `NOT` | displays a record if the condition(s) is NOT TRUE |
| `OR` | **any** of the conditions separated by OR is TRUE |
| `SOME` | **any** of the subquery values meet the condition (same as `ANY`) |

---

## 🧾 Quick Cheat Sheet

```sql
SELECT [DISTINCT] columns      -- what to show
FROM table                     -- where from
WHERE condition                -- filter rows
GROUP BY column                -- bundle rows into groups
HAVING condition               -- filter groups
ORDER BY column ASC|DESC;      -- sort results
```

| 💭 I want to... | ✅ Use |
|-----------------|-------|
| See everything | `SELECT *` |
| Remove duplicates | `SELECT DISTINCT` |
| Filter rows | `WHERE` |
| Match *all* conditions | `AND` |
| Match *any* condition | `OR` |
| Exclude matches | `NOT` |
| Sort results | `ORDER BY` |
| Limit the number of rows | `TOP` / `LIMIT` / `FETCH FIRST` |
| Check for empty data | `IS NULL` / `IS NOT NULL` |
| Replace NULL with a default | `COALESCE()` / `ISNULL()` / `IFNULL()` / `NVL()` |
| Add rows | `INSERT INTO` |
| Change rows | `UPDATE ... SET ... WHERE` |
| Remove rows | `DELETE FROM ... WHERE` |
| Remove a table | `DROP TABLE` |
| Find the smallest / largest value | `MIN()` / `MAX()` |
| Count rows | `COUNT()` |
| Total / average | `SUM()` / `AVG()` |
| Match a text pattern | `LIKE` with `%` and `_` |
| Match a list of values | `IN` |
| Match a range | `BETWEEN` |
| Rename a column or table temporarily | `AS` (alias) |
| Stack results of several queries | `UNION` / `UNION ALL` |
| Summarize per group | `GROUP BY` |
| Filter on an aggregate | `HAVING` |
| Check a subquery has results | `EXISTS` |
| Compare to any / every subquery value | `ANY` / `ALL` |
| Copy rows into a new table | `SELECT INTO` |
| Copy rows into an existing table | `INSERT INTO SELECT` |
| Add if-then-else logic | `CASE` |
| Save reusable SQL | `CREATE PROCEDURE` |
| Leave notes in code | `--` or `/* */` |

---

<p align="center">🌱 <i>Take it one query at a time. You've got this.</i> 🌱</p>
