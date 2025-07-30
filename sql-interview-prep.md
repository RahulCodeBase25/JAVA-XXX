
# 🧠 SQL Interview Preparation Guide (For Java Backend Developers)

This document covers high-priority SQL interview questions and answers with real examples, tailored for backend roles like at MCX, banks, trading firms, and enterprise companies.

---

## 1. What is the difference between WHERE and HAVING?

- `WHERE`: filters rows **before** grouping.
- `HAVING`: filters groups **after** aggregation.

```sql
-- Get departments with total salary > 50,000
SELECT department, SUM(salary)
FROM employees
GROUP BY department
HAVING SUM(salary) > 50000;
```

---

## 2. What are JOINS? Types of joins in SQL?

Joins combine rows from multiple tables using a related column.

- INNER JOIN: Only matching rows
- LEFT JOIN: All from left + matching from right
- RIGHT JOIN: All from right + matching from left
- FULL JOIN: All from both tables
- CROSS JOIN: Cartesian product

```sql
SELECT e.name, d.name
FROM employee e
INNER JOIN department d ON e.dept_id = d.id;
```

---

## 3. What’s the difference between UNION and UNION ALL?

- UNION: Removes duplicates.
- UNION ALL: Keeps everything (faster).

```sql
SELECT name FROM customers_india
UNION
SELECT name FROM customers_usa;
```

---

## 4. How do you find duplicate rows in a table?

```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

---

## 5. What is a Primary Key vs Foreign Key?

- **Primary Key**: Uniquely identifies a record, cannot be null.
- **Foreign Key**: Refers to the primary key of another table (used for relationships).

---

## 6. How to get the 2nd highest salary from a table?

```sql
SELECT MAX(salary)
FROM employee
WHERE salary < (SELECT MAX(salary) FROM employee);
```

---

## 7. DELETE vs TRUNCATE vs DROP

- **DELETE**: Removes rows (can use WHERE), can rollback.
- **TRUNCATE**: Deletes all rows, cannot rollback.
- **DROP**: Deletes entire table structure.

---

## 8. What is a subquery? Give an example

A query inside another query.

```sql
SELECT name, salary
FROM employee
WHERE salary > (SELECT AVG(salary) FROM employee);
```

---

## 9. How do you update data in SQL?

```sql
UPDATE employee
SET salary = salary + 1000
WHERE dept_id = 3;
```

---

## 10. What are indexes in SQL? When to use them?

Indexes speed up searches on large tables. Create them on columns used in `WHERE`, `JOIN`, or `ORDER BY`.

```sql
CREATE INDEX idx_email ON users(email);
```

---

## 11. CHAR vs VARCHAR

- CHAR(n): Fixed-length, always uses `n` characters.
- VARCHAR(n): Variable-length, uses only needed space.

---

## 12. How to fetch only unique records?

```sql
SELECT DISTINCT city FROM users;
```

---

## 13. Count of employees in each department

```sql
SELECT department_id, COUNT(*) AS emp_count
FROM employees
GROUP BY department_id;
```

---

## 14. What is normalization?

Process of organizing tables to reduce redundancy:

- 1NF: Atomic values only
- 2NF: No partial dependency on primary key
- 3NF: No transitive dependency

---

## 15. NULL in SQL and how to check for it?

NULL means absence of value.

```sql
SELECT * FROM users WHERE last_login IS NULL;
```

---

## 🔁 Bonus: Common Query Scenarios

### Get top 3 earners
```sql
SELECT * FROM employee ORDER BY salary DESC LIMIT 3;
```

---

### Employees with no department
```sql
SELECT * FROM employee WHERE dept_id IS NULL;
```

---

### Total salary per department (only if > 1 lakh)
```sql
SELECT dept_id, SUM(salary) AS total
FROM employee
GROUP BY dept_id
HAVING SUM(salary) > 100000;
```

---

## ✅ Tips for SQL in Interviews

- Always mention performance: indexes, `LIMIT`, filtering early
- Mention data consistency: transactions, constraints
- Practice writing nested queries and join-based aggregations
- Understand EXPLAIN plans (for advanced rounds)

---

_This guide is prepared for backend devs appearing for SQL-heavy interviews like MCX, ICICI, Infosys, and more._
