# Week 3 – Day 18: SQL INSERT, UPDATE and DELETE

Use these SQL commands to add, modify and remove records in a table.

Sample table: `employees`

| employee_id | name | department |
|---|---|---|
| 101 | Rahul | IT |
| 102 | Priya | HR |
| 103 | Aman | Finance |

## 1. INSERT
Use `INSERT` to add a new row.

Syntax:

```sql
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```

Example:

```sql
INSERT INTO employees (employee_id, name, department)
VALUES (105, 'Simran', 'Finance');
```

Text values are generally enclosed in single quotes; numeric values generally do not need quotes. Follow the data types and constraints defined for the table.

## 2. UPDATE
Use `UPDATE` to modify existing rows.

Syntax:

```sql
UPDATE table_name
SET column_name = new_value
WHERE condition;
```

Example: Change Priya's department from HR to IT.

```sql
UPDATE employees
SET department = 'IT'
WHERE employee_id = 102;
```

The WHERE condition limits the update to the matching row(s).

**Warning:** If you omit WHERE, every row in the table is updated.

## 3. DELETE
Use `DELETE` to remove rows.

Syntax:

```sql
DELETE FROM table_name
WHERE condition;
```

Example: Delete Simran's record.

```sql
DELETE FROM employees
WHERE employee_id = 105;
```

**Warning:** If you omit WHERE, all rows are deleted. The table structure remains.

## 4. Important safety practice
Before executing an UPDATE or DELETE:
1. Run a SELECT using the same WHERE condition.
2. Check that the selected rows are exactly the intended records.
3. Execute the change only after verifying the target rows.
4. Where appropriate, use a transaction and commit only after validation; rollback if the result is incorrect. Follow your database and environment procedures.

Example pre-check:

```sql
SELECT *
FROM employees
WHERE employee_id = 105;
```

## 5. Quick comparison

| Command | Purpose |
|---|---|
| INSERT | Add a new row |
| UPDATE | Modify existing row(s) |
| DELETE | Remove row(s) |

## DELETE examples

Delete every row:

```sql
DELETE FROM employees;
```

Delete only employee 105:

```sql
DELETE FROM employees
WHERE employee_id = 105;
```

## QA / database testing reminder
After an INSERT, UPDATE or DELETE, verify the database state with a SELECT query. Check the affected row(s), related constraints and any dependent application behavior. Never assume that a successful SQL execution alone proves the full business workflow is correct.
