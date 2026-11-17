# Day 16 – SQL SELECT, WHERE, ORDER BY and DISTINCT

## SELECT
Use `SELECT` to retrieve data from a table.

```sql
SELECT *
FROM orders;
```

The asterisk (`*`) returns all columns. To select specific columns:

```sql
SELECT customer_name, amount
FROM orders;
```

## WHERE
Use `WHERE` to filter rows based on a condition.

```sql
SELECT *
FROM orders
WHERE status = 'Completed';
```

Example using a comparison:

```sql
SELECT *
FROM orders
WHERE amount > 2000;
```

## ORDER BY
Use `ORDER BY` to sort results.
- `ASC`: ascending order; this is the default.
- `DESC`: descending order.

```sql
SELECT *
FROM orders
ORDER BY amount DESC;
```

## DISTINCT
Use `DISTINCT` to return unique values and remove duplicates from the result.

```sql
SELECT DISTINCT customer_name
FROM orders;
```

## SELECT vs SELECT DISTINCT

```sql
SELECT customer_name
FROM orders;
``

Returns every row's customer name, so Rahul can appear more than once.

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
- `SELECT`: retrieves columns.
- `WHERE`: filters rows.
- `ORDER BY`: sorts results.
- `DISTINCT`: removes duplicate values from the result.
