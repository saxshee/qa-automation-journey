# Week 3 — SQL + Database Testing
# Day 1 — SQL Filtering

**Status:** Completed lesson and practice assessment  
**Focus:** WHERE, AND, OR, IN, BETWEEN, LIKE

## Sample table: orders

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

## 1. WHERE clause

Filters rows based on a condition.

```sql
SELECT *
FROM orders
WHERE status = 'Completed';
```

## 2. AND operator

All conditions must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
AND amount > 2000;
```

## 3. OR operator

At least one condition must be true.

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
OR amount > 4000;
```

## 4. IN operator

Matches a value against a list of possible values. It can replace multiple OR conditions on the same column.

```sql
SELECT *
FROM orders
WHERE status IN ('Completed', 'Pending');
```

## 5. BETWEEN operator

Filters values within a range. Both endpoints are included.

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1200 AND 3000;
```

## 6. LIKE operator

Matches text patterns using wildcards:
- `'A%'` — starts with A
- `'%A'` — ends with A
- `'%A%'` — contains A anywhere
- `'_a%'` — second character is a

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

Remember to put LIKE patterns inside quotes.

## Practice assessment

### Question 1 — AND

**Task:** Find orders where status is Completed and amount is greater than ₹2,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status = 'Completed'
AND amount > 2000;
```

Expected order IDs: 101, 103, 107.  
**Result:** Correct.

### Question 2 — OR

**Task:** Find orders where status is Pending or amount is greater than ₹4,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status = 'Pending'
OR amount > 4000;
```

Expected order IDs: 102, 103, 105, 107, 108.  
**Result:** Correct.

### Question 3 — IN

**Task:** Find orders with status Completed or Failed.

Learner query:

```sql
SELECT *
FROM orders
WHERE status IN ('Completed', 'Failed');
```

Expected order IDs: 101, 103, 104, 106, 107.  
**Result:** Correct.

### Question 4 — BETWEEN

**Task:** Find orders with amount between ₹1,500 and ₹4,500, inclusive.

Learner query:

```sql
SELECT *
FROM orders
WHERE amount BETWEEN 1500 AND 4500;
```

Expected order IDs: 101, 105, 106, 107.  
Learner initially listed 105 and 107, then was shown that 101 and 106 also qualify because BETWEEN includes both endpoints.  
**Result:** Query correct; expected output needed correction.

### Question 5 — LIKE: starts with R

Learner attempted:

```sql
SELECT *
FROM orders
WHERE customer_name LIKE r%;
```

Corrected query:

```sql
SELECT *
FROM orders
WHERE customer_name LIKE 'R%';
```

Expected names: Rahul (orders 101 and 105), Rohan (order 107).  
**Result:** Pattern understood; quotation marks were missing in the first attempt.

### Question 6 — LIKE: ends with a

Learner attempted the pattern but omitted LIKE.

Correct query:

```sql
SELECT *
FROM orders
WHERE customer_name LIKE '%a';
```

Expected names: Priya, Neha, Ananya.  
**Result:** Pattern understood; SQL syntax needed correction.

### Question 7 — IN + AND

**Task:** Find orders where status is Pending or Failed, and amount is greater than ₹1,000.

Learner query:

```sql
SELECT *
FROM orders
WHERE status IN ('Pending', 'Failed')
AND amount > 1000;
```

Expected order IDs: 102 and 106.  
**Result:** Correct.

### Question 8 — LIKE + AND

**Task:** Find orders where customer name starts with R and amount is greater than ₹2,000.

**Status:** Not attempted; learner chose to move to the next day.

## Key takeaways

- AND requires every condition to be true.
- OR requires at least one condition to be true.
- IN checks a list of values.
- BETWEEN includes the lower and upper boundaries.
- LIKE uses `%` for any sequence of characters and `_` for one character.
- Text patterns for LIKE must be quoted.
- When checking query results, verify the complete set of matching rows, not only the SQL syntax.

## Day 1 progress

Core filtering operators were covered and practiced. The learner correctly wrote queries using AND, OR, IN, BETWEEN, and LIKE after minor syntax/logic corrections. One final combined exercise was skipped by choice to proceed to Day 2.
