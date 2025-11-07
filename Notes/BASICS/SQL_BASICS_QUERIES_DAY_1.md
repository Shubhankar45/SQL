Perfect ✅ — here’s your **complete all-in-one SQL Basics Notes** in **Markdown (`.md`) format** — including **table creation syntax**, **CRUD operations**, and **aggregation + filtering concepts**.

---

````markdown
# 🧠 SQL BASICS – COMPLETE NOTES

Comprehensive SQL revision covering all fundamental operations:
`CREATE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`, `WHERE`, `ORDER BY`, `GROUP BY`, `HAVING`, `DISTINCT`, and `LIMIT/TOP`.

---

## ⚙️ 1️⃣ CREATE TABLE – Define Table Structure

### ✅ Syntax:
```sql
CREATE TABLE table_name (
    column1 datatype(size) CONSTRAINTS,
    column2 datatype(size),
    column3 datatype(size),
    ...
);
````

### 📘 Example:

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY IDENTITY(1,1),
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    country VARCHAR(50),
    score INT,
    created_at DATE
);
```

### 🧩 Common Data Types:

| Type                | Description          |
| ------------------- | -------------------- |
| `INT`               | Integer numbers      |
| `VARCHAR(n)`        | Variable-length text |
| `CHAR(n)`           | Fixed-length text    |
| `DATE`              | Date value           |
| `FLOAT` / `DECIMAL` | Decimal numbers      |
| `BOOLEAN` / `BIT`   | True/False values    |

---

## 🧱 2️⃣ INSERT – Add Data to a Table

### ✅ Syntax:

```sql
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```

### 📘 Example:

```sql
INSERT INTO customers (first_name, last_name, country, score)
VALUES ('Maria', 'Lopez', 'Spain', 500);
```

---

## 🔍 3️⃣ SELECT – Retrieve Data

### ✅ Syntax:

```sql
SELECT column1, column2 FROM table_name;
```

### 📘 Examples:

```sql
SELECT * FROM customers; -- All columns
SELECT first_name, score FROM customers; -- Specific columns
```

---

## 🎯 4️⃣ WHERE – Filter Data

### ✅ Syntax:

```sql
SELECT * FROM table_name WHERE condition;
```

### 📘 Examples:

```sql
SELECT * FROM customers WHERE first_name = 'Maria';
SELECT * FROM customers WHERE score > 400 AND country = 'India';
```

---

## 📊 5️⃣ ORDER BY – Sort Data

### ✅ Syntax:

```sql
SELECT * FROM table_name ORDER BY column ASC|DESC;
```

### 📘 Examples:

```sql
SELECT * FROM customers ORDER BY score ASC;
SELECT * FROM customers ORDER BY score DESC;
SELECT * FROM customers ORDER BY country ASC, score DESC;
```

---

## 🧮 6️⃣ GROUP BY – Aggregate Data

Used with aggregate functions like:
`SUM()`, `AVG()`, `COUNT()`, `MIN()`, `MAX()`

### ✅ Syntax:

```sql
SELECT column, AGGREGATE_FUNCTION(column)
FROM table_name
GROUP BY column;
```

### 📘 Examples:

#### ➤ Total score for each country:

```sql
SELECT country AS Country, SUM(score) AS Total_Score
FROM customers
GROUP BY country;
```

#### ➤ Total score and total customers:

```sql
SELECT country AS Country,
       COUNT(id) AS Total_Customers,
       SUM(score) AS Total_Score
FROM customers
GROUP BY country;
```

---

## 🧠 7️⃣ HAVING – Filter After Aggregation

`HAVING` is used with `GROUP BY` for filtering aggregated data.

### 📘 Example:

```sql
SELECT country AS Country,
       COUNT(id) AS Total_Customers,
       SUM(score) AS Total_Score
FROM customers
GROUP BY country
HAVING SUM(score) > 800;
```

---

## 📈 8️⃣ WHERE + GROUP BY + HAVING Combined

### 📘 Example:

Average score (excluding score = 0) where average > 430:

```sql
SELECT country AS Country,
       AVG(score) AS Average_Score
FROM customers
WHERE score != 0
GROUP BY country
HAVING AVG(score) > 430;
```

---

## 🔁 9️⃣ DISTINCT – Remove Duplicates

### ✅ Syntax:

```sql
SELECT DISTINCT column FROM table_name;
```

### 📘 Example:

```sql
SELECT DISTINCT country FROM customers;
```

---

## 🧾 🔟 LIMIT / TOP – Retrieve Specific Number of Rows

> **SQL Server:** use `TOP`
> **MySQL / PostgreSQL:** use `LIMIT`

### 📘 Examples:

#### ➤ SQL Server

```sql
SELECT TOP 3 * FROM customers;
SELECT TOP 3 * FROM customers ORDER BY score DESC; -- Top 3 by score
SELECT TOP 3 * FROM customers ORDER BY score ASC;  -- Bottom 3 by score
```

#### ➤ MySQL / PostgreSQL

```sql
SELECT * FROM customers LIMIT 3;
SELECT * FROM customers ORDER BY score DESC LIMIT 3;
SELECT * FROM customers ORDER BY score ASC LIMIT 3;
```

---

## 🕒 11️⃣ ORDER EXAMPLE – Most Recent Orders

### 📘 Example:

```sql
SELECT * FROM orders;

-- Top 2 most recent
SELECT TOP 2 * FROM orders ORDER BY order_date DESC;   -- SQL Server
SELECT * FROM orders ORDER BY order_date DESC LIMIT 2; -- MySQL/PostgreSQL
```

---

## ✏️ 12️⃣ UPDATE – Modify Data

### ✅ Syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

### 📘 Example:

```sql
UPDATE customers
SET score = 700
WHERE first_name = 'Maria';
```

---

## ❌ 13️⃣ DELETE – Remove Data

### ✅ Syntax:

```sql
DELETE FROM table_name WHERE condition;
```

### ⚠️ Delete all rows:

```sql
DELETE FROM customers;
```

> Always use `WHERE` carefully to avoid deleting all records!

---

## 📦 14️⃣ DROP / ALTER – Modify or Remove Table

### Drop a table:

```sql
DROP TABLE table_name;
```

### Add a new column:

```sql
ALTER TABLE customers ADD email VARCHAR(100);
```

### Modify a column:

```sql
ALTER TABLE customers ALTER COLUMN score FLOAT;
```

### Delete a column:

```sql
ALTER TABLE customers DROP COLUMN email;
```

---

## 📚 15️⃣ Common Aggregate Functions

| Function        | Description                       |
| --------------- | --------------------------------- |
| `COUNT(column)` | Counts total rows/non-null values |
| `SUM(column)`   | Adds up values                    |
| `AVG(column)`   | Returns average                   |
| `MIN(column)`   | Minimum value                     |
| `MAX(column)`   | Maximum value                     |

---

## 🧩 16️⃣ SQL Query Execution Order

| Step | Clause      | Description         |
| ---- | ----------- | ------------------- |
| 1    | `FROM`      | Select table        |
| 2    | `WHERE`     | Filter rows         |
| 3    | `GROUP BY`  | Group data          |
| 4    | `HAVING`    | Filter grouped data |
| 5    | `SELECT`    | Select columns      |
| 6    | `ORDER BY`  | Sort results        |
| 7    | `LIMIT/TOP` | Restrict rows       |

---

## ✅ Quick Summary

| Clause       | Purpose                   |
| ------------ | ------------------------- |
| **CREATE**   | Define table structure    |
| **INSERT**   | Add new records           |
| **SELECT**   | Retrieve data             |
| **WHERE**    | Filter rows               |
| **ORDER BY** | Sort data                 |
| **GROUP BY** | Aggregate data            |
| **HAVING**   | Filter aggregated results |
| **DISTINCT** | Remove duplicates         |
| **UPDATE**   | Modify records            |
| **DELETE**   | Remove records            |
| **DROP**     | Delete table              |

---

## 💡 Pro Tips

* Use **WHERE** before **GROUP BY**, and **HAVING** after aggregation.
* Always **backup data** before using `DELETE` or `DROP`.
* Prefer **LIMIT** in MySQL and **TOP** in SQL Server.
* Use **aliases (AS)** to rename columns for readability.

---

⭐ **End of SQL Basics Notes**


