# Week 3 – Day 17: SQL Operators and NULL

## 1. AND
Use `AND` when **both conditions** must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Pending'
  AND amount > 1000;
```

## 2. OR
Use `OR` when **at least one condition** must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
   OR amount > 4000;
```

## 3. IN
Use `IN` to match a value against a list of possible values. It is a concise alternative to multiple `OR` conditions.

```sql
SELECT *
FROM orders
WHERE status IN ('Failed', 'Pending');
```

## 4. BETWEEN
Use `BETWEEN` to filter values within a range. The endpoints are inclusive.

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1200 AND 3000;
```

This includes amounts equal to 1200 and 3000.

## 5. LIKE
Use `LIKE` for pattern matching with wildcards:

- `'R%'`: starts with R.
- `'%a'`: ends with a.
- `'%a%'`: contains a anywhere.

```sql
SELECT *
FROM orders
WHERE customer_name LIKE 'R%';
```

## 6. NULL
`NULL` represents a missing or unknown value. It is not the same as zero or an empty string.

Use `IS NULL` to find missing values:

```sql
SELECT *
FROM employees
WHERE department IS NULL;
```

Use `IS NOT NULL` to find rows where a value is present:

```sql
SELECT *
FROM employees
WHERE department IS NOT NULL;
```

**Important:** Do not use `= NULL` or `!= NULL` to check for NULL values. Use `IS NULL` or `IS NOT NULL`.

## Sample orders table

| order_id | customer_name | amount | status |
|---|---|---:|---|
| 101 | Rahul | 2500 | Completed |
| 102 | Priya | 1200 | Pending |
| 103 | Aman | 5000 | Completed |
| 104 | Neha | 800 | Failed |
| 105 | Rahul | 3000 | Pending |
| 106 | Ananya | 1500 | Failed |
| 107 | Rohan | 4500 | Completed |
| 108 | Simran | 900 | Pending |

## Quick revision

- `AND`: every condition must be true.
- `OR`: at least one condition must be true.
- `IN`: match any value in a list.
- `BETWEEN`: match an inclusive range.
- `LIKE`: match a text pattern.
- `IS NULL`: find missing values.
- `IS NOT NULL`: find non-missing values.

## Practice queries

1. Find Pending orders with an amount greater than 1000.
2. Find orders that are Completed or have an amount greater than 4000.
3. Find orders with status Failed or Pending using `IN`.
4. Find orders with an amount between 1200 and 3000.
5. Find customers whose names start with R.
6. Find employees whose department is NULL.
7. Find employees whose department is not NULL.
