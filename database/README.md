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
8. [Operators](#-operators)
9. [ORDER BY](#-order-by)
10. [AND / OR](#-and--or)
11. [NOT](#-not)
12. [INSERT INTO](#-insert-into)
13. [NULL Values](#-null-values)
14. [DELETE & DROP](#-delete--drop)
15. [Aggregate Functions](#-aggregate-functions)
16. [MIN()](#-min)
17. [Quick Cheat Sheet](#-quick-cheat-sheet)

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

## 🗑️ DELETE & DROP

| Goal | Command | Result |
|------|---------|--------|
| Delete specific rows | `DELETE FROM table_name WHERE condition;` | Only matching rows removed |
| Delete **all** rows | `DELETE FROM table_name;` | Rows gone; table structure, attributes & indexes stay intact |
| Delete the **whole table** | `DROP TABLE table_name;` | Table removed completely |

> 🛑 **Careful:** forgetting `WHERE` in a `DELETE` removes **every** row!

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

---

## 🧾 Quick Cheat Sheet

```sql
SELECT [DISTINCT] columns      -- what to show
FROM table                     -- where from
WHERE condition                -- filter rows
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
| Check for empty data | `IS NULL` / `IS NOT NULL` |
| Add rows | `INSERT INTO` |
| Remove rows | `DELETE FROM ... WHERE` |
| Remove a table | `DROP TABLE` |
| Find the smallest value | `MIN()` |

---

<p align="center">🌱 <i>Take it one query at a time. You've got this.</i> 🌱</p>
