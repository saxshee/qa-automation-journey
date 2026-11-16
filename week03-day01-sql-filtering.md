# Week 3 — SQL + Database Testing
## Day 1: SQL Filtering

**Status:** Completed for this study session  
**Topics:** `AND`, `OR`, `IN`, `BETWEEN`, `LIKE`

## Practice table: orders

| order_id | customer_name | amount | status |
|---:|---|---:|---|
| 101 | Rahul | 2500 | Completed |
| 102 | Priya | 1200 | Pending |
| 103 | Aman | 5000 | Completed |
| 104 | Neha | 800 | Failed |
| 105 | Rahul | 3000 | Pending |
| 106 | Ananya | 1500 | Failed |
| 107 | Rohan | 4500 | Completed |
| 108 | Simran | 900 | Pending |

## 1. AND

Use `AND` when all conditions must be true.

Example: completed orders with amount greater than 2,000.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
AND amount > 2000;
```

## 2. OR

Use `OR` when at least one condition must be true.

Example: completed orders or orders with amount greater than 4,000.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
OR amount > 4000;
```

## 3. IN

Use `IN` to match any value from a list. It is a concise alternative to multiple equality checks joined with `OR`.

```sql
SELECT *
FROM orders
WHERE status IN ('Completed', 'Pending');
```

Equivalent logic:

```sql
WHERE status = 'Completed'
OR status = 'Pending'
```

## 4. BETWEEN

Use `BETWEEN` to filter an inclusive range. Both endpoints are included.

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1200 AND 3000;
```

## 5. LIKE

Use `LIKE` for text pattern matching. The pattern must be enclosed in quotes.

| Pattern | Meaning |
|---|---|
| `'A%'` | Starts with A |
| `'%A'` | Ends with A |
| `'%A%'` | Contains A anywhere |
| `'_a%'` | Second character is a |

Examples:

```sql
-- Names starting with R
SELECT *
FROM orders
WHERE customer_name LIKE 'R%';

-- Names containing a
SELECT *
FROM orders
WHERE customer_name LIKE '%a%';
```

## Assessment practice and learner results

### Question 1 — AND

**Task:** Find Completed orders with amount greater than 2,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
AND amount > 2000;
```

**Result:** Correct. Expected order IDs: 101, 103, 107.

### Question 2 — OR

**Task:** Find Pending orders or orders with amount greater than 4,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status = 'Pending'
OR amount > 4000;
```

**Result:** Correct. Expected order IDs: 102, 103, 105, 107, 108.

### Question 3 — IN

**Task:** Find orders with status Completed or Failed.

Learner query:

```sql
SELECT *
FROM orders
WHERE status IN ('Completed', 'Failed');
```

**Result:** Correct. Expected order IDs: 101, 103, 104, 106, 107.

### Question 4 — BETWEEN

**Task:** Find orders with amount between 1,500 and 4,500 inclusive.

Learner query:

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1500 AND 4500;
```

**Result:** Query correct. Expected order IDs: 101, 105, 106, 107. Learner initially listed only 105 and 107, missing the inclusive boundaries and another in-range value.

### Question 5 — LIKE

**Task:** Find names starting with R.

Correct query:

```sql
SELECT *
FROM orders
WHERE customer_name LIKE 'R%';
```

**Result:** Learner used the right pattern but omitted quotes. Expected names: Rahul (orders 101 and 105), Rohan (order 107).

### Question 6 — LIKE

**Task:** Find names ending with a.

Correct query:

```sql
SELECT *
FROM orders
WHERE customer_name LIKE '%a';
```

**Result:** Learner identified the pattern `%a` but omitted the `LIKE` keyword. Expected names: Priya, Neha, Ananya.

### Question 7 — IN + AND

**Task:** Find orders whose status is Pending or Failed, and amount is greater than 1,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status IN ('Pending', 'Failed')
AND amount > 1000;
```

**Result:** Correct. Expected order IDs: 102 and 106.

### Question 8 — LIKE + AND

**Task:** Find orders where customer name starts with R and amount is greater than 2,000.

**Status:** Not attempted; learner chose to move to the next day.

## Key takeaways

- `AND`: every condition must be true.
- `OR`: at least one condition must be true.
- `IN`: match one of several listed values.
- `BETWEEN`: inclusive range; check both endpoints and all values inside the range.
- `LIKE 'A%'`: starts with A.
- `LIKE '%A'`: ends with A.
- `LIKE '%A%'`: contains A anywhere.
- Put text patterns in single quotes.
- When writing test queries, validate the expected row IDs as well as the SQL syntax.

## Progress

Day 1 filtering practice covered all five operators. The learner requested to move to the next day before attempting Question 8. Continue with Day 2 in the Week 3 plan.


## Additional practice notes

The learner also practiced the following patterns during the lesson:

- Pending status with amount greater than 1,000: used `AND` correctly; initially used the wrong comparison operator (`<` instead of `>`), then corrected it.
- Completed status OR amount greater than 4,000: selected `OR` correctly; corrected a typo in the column name from `amont` to `amount`.
- Status in Failed or Pending: wrote the `IN` query correctly.
- Amount between 1,200 and 3,000: wrote the `BETWEEN` query correctly.
- Names containing the letter a: understood the `%a%` pattern; corrected by enclosing the pattern in quotes.
- Explained correctly that `'A%'` matches names starting with A, while `'%A%'` matches names containing A anywhere.

The learner chose to stop the assessment after Question 7 and proceed to Day 2 rather than complete all 10 questions.