# Day 18 – SQL INSERT, UPDATE and DELETE

Use these commands to add, modify and remove records in a table.

Sample `employees` table:

| employee_id | name | department |
|---|---|---|
| 101 | Rahul | IT |
| 102 | Priya | HR |
| 103 | Aman | Finance |

## INSERT
Use `INSERT` to add a new row.

```sql
INSERT INTO employees (employee_id, name, department)
VALUES (105, 'Simran', 'Finance');
```

Text values are generally enclosed in single quotes; numeric values generally do not need quotes.

## UPDATE
Use `UPDATE` to modify existing rows.

```sql
UPDATE employees
SET department = 'IT'
WHERE employee_id = 102;
```

The WHERE condition limits the update to the matching row(s).

**Warning:** Without a WHERE clause, every row in the table is updated.

## DELETE
Use `DELETE` to remove rows.

```sql
DELETE FROM employees
WHERE employee_id = 105;
```

**Warning:** Without a WHERE clause, all rows are deleted. The table structure remains.

## Safety practice
Before executing UPDATE or DELETE:
1. Run a SELECT with the same WHERE condition.
2. Verify that the selected rows are exactly the intended records.
3. Execute the change only after checking the target rows.
4. Where appropriate, use a transaction and follow your database/environment procedures.

Example pre-check:

```sql
SELECT *
FROM employees
WHERE employee_id = 105;
```

## Quick comparison

| Command | Purpose |
|---|---|
| INSERT | Add a new row |
| UPDATE | Modify existing row(s) |
| DELETE | Remove row(s) |

## DELETE examples

Delete all rows:

```sql
DELETE FROM employees;
```

Delete only employee 105:

```sql
DELETE FROM employees
WHERE employee_id = 105;
```

After an INSERT, UPDATE or DELETE, verify the database state with SELECT. Check affected rows, related constraints and dependent application behavior.
