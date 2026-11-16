# Week 3 – Day 16: SELECT, WHERE, ORDER BY and DISTINCT

## 1. SELECT
Use `SELECT` to retrieve data from a table.

```sql
SELECT *
FROM orders;
```

- `*` returns all columns.
- You can specify column names to retrieve only the fields you need.

```sql
SELECT customer_name, amount
FROM orders;
```

## 2. WHERE
Use `WHERE` to filter rows based on a condition.

```sql
SELECT *
FROM orders
WHERE status = 'Completed';
```

Example with a comparison:

```sql
SELECT *
FROM orders
WHERE amount > 2000;
```

## 3. ORDER BY
Use `ORDER BY` to sort the returned rows.

- `ASC`: ascending order (smallest to largest / A to Z). This is the default.
- `DESC`: descending order (largest to smallest / Z to A).

```sql
SELECT *
FROM orders
ORDER BY amount DESC;
```

## 4. DISTINCT
Use `DISTINCT` to return unique values and remove duplicates from the result.

```sql
SELECT DISTINCT customer_name
FROM orders;
```

## Difference: SELECT vs SELECT DISTINCT

```sql
SELECT customer_name
FROM orders;
``

Returns every row's customer name, so a name such as Rahul can appear more than once.

```sql
SELECT DISTINCT customer_name
FROM orders;
``

Returns each customer name only once.

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

- `SELECT` retrieves columns.
- `WHERE` filters rows.
- `ORDER BY` sorts the result; default is `ASC`.
- `DISTINCT` removes duplicate values from the result.

## Practice queries

1. Display all columns from `orders`.
2. Display only `customer_name` and `amount`.
3. Find orders where `status = 'Pending'`.
4. Sort orders by `amount` from highest to lowest.
5. Display unique customer names.
