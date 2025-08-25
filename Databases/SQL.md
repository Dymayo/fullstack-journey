## Resources

- https://sqlbolt.com/lesson/select_queries_introduction

* [https://www.sqlteaching.com/#!select_columns](https://www.sqlteaching.com/#!select_columns) (interactive teaching)
* [https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/](https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/) (Explanation of JOIN)
* https://sqlzoo.net/wiki/Nested_SELECT_Quiz (tutorials and quizs )

## Cheat sheet

### Setting up:

**Schema** is a special file where the setup info of a database is stored.

- `CREATE TABLE`– define tables and columns.

### Mucking data (CRUD):

- Create : `INSERT INTO ... VALUES ...`
- Read : `SELECT` / `SELECT DISTINCT` for unique values
- Update : `UPDATE ... SET ... WHERE ...`
- Destroy: `DELETE FROM`

### Mashing tables together:

- `(INNER) JOIN`: Returns records that have matching values in both tables
- `LEFT (OUTER) JOIN`: all left rows + matched right rows
- `RIGHT (OUTER) JOIN`: all right rows + matched left rows
- `FULL (OUTER) JOIN`: Returns all records when there is a match in either left or right table
- **Self joins** : Sometimes, it may make sense for you to join a table to itself. In that case, you need to use table aliases to determine which data is from the "first"/"left" table.

![venn diagram](/Databases/UI25E.jpg)

### Aggregating data:

- `COUNT`, `SUM`, `AVG`, `MAX`, `MIN`
- `ROUND(f,p)`: returns _f_ rounded to _p_ decimal places.Negative *p* rounds to the nearest 10 (when p is -1) or 100 (when p is -2),etc.
- NOTE: In some SQL versions, integer division stays integer; divide by a float (e.g., 1000000.0) to force decimals.

### Filtering data:

- `WHERE` : Use comparison operators (`>`, `<`, `<=`,`<>` etc.) to specify groups of rows, or logical operators (`AND`, `OR`, `NOT`,`XOR`,`BETWEEN`) to chain multiple clauses together.
- `LIKE` : Use for pattern matching, e.g. `WHERE name LIKE 'A%'` finds all names starting with A.
- `ALL` : Ensures the condition holds true for *every* value in the subquery result e.g., `WHERE column_name OPERATOR ALL (SELECT ...)`
- `ANY` : Compare a value to *any* in a subquery result.

* `GROUP BY` : Groups rows for aggregation; include all non-aggregated selected columns.
* `HAVING` : Filters **groups** (like `WHERE` for aggregates)

### Sorting data:

- `ORDER BY` : to sort the rows by some kind of attribute. To put the names in descending order, add `DESC` at the end of the query.

### Aliasing:

- `AS` : Shorten query names with aliases for tables or columns to avoid confusion.

### String functions:

- `SUBSTR(column_name, index, length)` : extracts a substring () in other SQL dialects, you could use `RIGHT` to do this)
- `CONCAT(a, b, ...)`  allows you to stick two or more strings together.
- `REPLACE(f, s1, s2)` returns the string _f_ with all occurrences of _s1_ replaced with _s2_.

### Null handling:

- `COALESCE` : takes a list of columns, and returns the value of the first column that is not null.

### Other notes:

- ###### Escaping single quotes:

  You can't put a single quote in a quoted string directly instead use two single quotes within a quoted string.

- ###### Logical order (simplified):
  `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY` → `LIMIT`
  `WHERE`: row-by-row filter (no aggregates yet).  
   `HAVING`: group-by-group filter (aggregates available).

## To Remember Queries

**Find countries with three or more 'a' in the name**

```
SELECT name FROM world
WHERE name LIKE '%a%a%a%';
```

**Find largest country (by area) in each continent**  
==Correlated subquery== pattern with aliases `x` (outer) and `y` (inner).

```
SELECT continent, name, area
FROM world x
WHERE area >= ALL (
  SELECT area
  FROM world y
  WHERE y.continent = x.continent
    AND area > 0
);
```

> A correlated subquery runs once per outer row. Here we keep rows whose `area` is ≥ **all** areas of countries in the same continent.
