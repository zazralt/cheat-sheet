# SQL Basics Cheat Sheet

Links: [Wiki](https://en.wikipedia.org/wiki/SQL) | [W3C Schools](https://www.w3schools.com/sql/default.asp)

## Data Querying

### SELECT
```sql
SELECT column1, column2 FROM table;
SELECT * FROM table; -- all columns
````

### WHERE

```sql
SELECT * FROM table
WHERE column = 'value';
```

### Comparison Operators

| Operator    | Meaning          |
| ----------- | ---------------- |
| `=`         | Equal            |
| `!=` / `<>` | Not equal        |
| `>`         | Greater than     |
| `<`         | Less than        |
| `>=`        | Greater or equal |
| `<=`        | Less or equal    |

### Logical Operators

| Operator | Meaning     |
| -------- | ----------- |
| `AND`    | Logical AND |
| `OR`     | Logical OR  |
| `NOT`    | Logical NOT |

### IN, BETWEEN, LIKE

```sql
SELECT * FROM table
WHERE column IN ('A', 'B');

SELECT * FROM table
WHERE column BETWEEN 10 AND 20;

SELECT * FROM table
WHERE column LIKE 'A%'; -- starts with A
```

## Sorting and Limiting

### ORDER BY

```sql
SELECT * FROM table
ORDER BY column ASC;  -- or DESC
```

### LIMIT / OFFSET

```sql
SELECT * FROM table
LIMIT 10 OFFSET 20;
```

## Aggregation

### Functions

| Function  | Description |
| --------- | ----------- |
| `COUNT()` | Count rows  |
| `SUM()`   | Sum values  |
| `AVG()`   | Average     |
| `MIN()`   | Minimum     |
| `MAX()`   | Maximum     |

### GROUP BY / HAVING

```sql
SELECT column, COUNT(*)
FROM table
GROUP BY column
HAVING COUNT(*) > 1;
```

## Joins

### INNER JOIN

```sql
SELECT a.col, b.col
FROM table1 a
JOIN table2 b ON a.id = b.id;
```

### LEFT JOIN / RIGHT JOIN

```sql
SELECT *
FROM table1
LEFT JOIN table2 ON table1.id = table2.id;
```

### FULL OUTER JOIN (if supported)

```sql
SELECT *
FROM table1
FULL OUTER JOIN table2 ON table1.id = table2.id;
```

## Subqueries

```sql
SELECT name
FROM employees
WHERE department_id = (
  SELECT id FROM departments WHERE name = 'Sales'
);
```

## Aliases

```sql
SELECT name AS employee_name
FROM employees;
```

## Create, Insert, Update, Delete

### CREATE TABLE

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  salary DECIMAL(10, 2)
);
```

### INSERT INTO

```sql
INSERT INTO employees (id, name, salary)
VALUES (1, 'Alice', 50000.00);
```

### UPDATE

```sql
UPDATE employees
SET salary = 55000.00
WHERE id = 1;
```

### DELETE

```sql
DELETE FROM employees
WHERE id = 1;
```

---

Reference: [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
