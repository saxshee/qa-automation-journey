# Day 17 – SQL Operators and NULL

## AND
Use `AND` when both conditions must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Pending'
  AND amount > 1000;
```

## OR
Use `OR` when at least one condition must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
   OR amount > 4000;
```

## IN
Use `IN` to match a value against a list. It is a concise alternative to multiple OR conditions.

```sql
SELECT *
FROM orders
WHERE status IN ('Failed', 'Pending');
```

## BETWEEN
Use `BETWEEN` to filter values within a range. The endpoints are inclusive.

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1200 AND 3000;
```

## LIKE
Use `LIKE` for text pattern matching:
- `'R%'`: starts with R.
- `'%a'`: ends with a.
- `'%a%'`: contains a anywhere.

```sql
SELECT *
FROM orders
WHERE customer_name LIKE 'R%';
```

## NULL
`NULL` represents a missing or unknown value. It is not the same as zero or an empty string.

Find missing values:

```sql
SELECT *
FROM employees
WHERE department IS NULL;
```

Find values that are present:

```sql
SELECT *
FROM employees
WHERE department IS NOT NULL;
```

**Important:** Do not use `= NULL` or `!= NULL`. Use `IS NULL` or `IS NOT NULL`.

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
