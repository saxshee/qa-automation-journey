# Day 9 — Boundary Value Analysis (BVA)

## Learning objectives
- Understand Boundary Value Analysis as a black-box test design technique.
- Identify minimum and maximum input boundaries.
- Derive two-value and three-value BVA test data.
- Distinguish BVA from Equivalence Partitioning (EP).

## 1. What is Boundary Value Analysis?
Boundary Value Analysis is a black-box test design technique that focuses on values at and around the edges of an allowed input range. Defects often occur at boundaries because of incorrect comparison operators or off-by-one errors.

For an inclusive range:
`minimum <= input <= maximum`

Three-value BVA typically checks:
- Minimum − 1
- Minimum
- Minimum + 1
- Maximum − 1
- Maximum
- Maximum + 1

The expected results must come from the stated requirement.

## 2. Banking transfer example
Requirement: A transfer amount must be between ₹100 and ₹50,000, inclusive.

| Test value | Expected result | Reason |
|---:|---|---|
| ₹99 | Reject | Below minimum |
| ₹100 | Accept | Minimum boundary |
| ₹101 | Accept | Just above minimum |
| ₹49,999 | Accept | Just below maximum |
| ₹50,000 | Accept | Maximum boundary |
| ₹50,001 | Reject | Above maximum |

## 3. More real-world examples

### E-commerce quantity
Requirement: A customer can order 1–10 items.
BVA values: 0, 1, 2, 9, 10, 11.
- 0: reject, one below minimum.
- 1: accept, minimum.
- 2: accept, just above minimum.
- 9: accept, just below maximum.
- 10: accept, maximum.
- 11: reject, one above maximum.

### Registration age
Requirement: Age must be 18–60 inclusive.
Values: 17, 18, 19, 59, 60, 61.

### Movie ticket booking
Requirement: A booking can contain 1–6 tickets.
Values: 0, 1, 2, 5, 6, 7.

### Online shopping order
Requirement: A customer can purchase 5–20 products in one order.
Values: 4, 5, 6, 19, 20, 21.

## 4. Two-value vs three-value BVA
For a range of 18–60:
- Two-value BVA: 17, 18, 60, 61 (boundary and adjacent outside value).
- Three-value BVA: 17, 18, 19, 59, 60, 61 (one below, at, and one above each boundary).

This study uses three-value BVA for practice.

## 5. EP vs BVA
| Equivalence Partitioning | Boundary Value Analysis |
|---|---|
| Divides inputs into groups expected to behave similarly | Focuses on values at and around range boundaries |
| Selects representative values from each partition | Selects values immediately below, at, and above boundaries |
| Example for age 18–60: 15, 30, 65 | Example: 17, 18, 19, 59, 60, 61 |

EP focuses on partitions; BVA focuses on edges.

## 6. Assessment and learner feedback

### Q1 — E-commerce quantity 5–20
Learner answer: 4, 5, 6, 19, 20, 21.
Evaluation: Correct. All six three-value BVA values identified.

### Q2 — Banking withdrawal ₹500–₹25,000
Learner answer:
- ₹499 — rejected
- ₹500 — accepted
- ₹501 — accepted
- ₹24,999 — accepted
- ₹25,000 — accepted
- ₹25,001 — rejected

Evaluation: Correct values and expected outcomes.

### Q3 — Explain EP vs BVA
Learner explained that EP groups values expected to produce similar behavior, using groups such as a/b/c and d/e/f.
Feedback: The EP concept was broadly understood, but the answer needed to explain BVA as well. Interview-ready answer: “Equivalence Partitioning divides input data into groups expected to behave similarly and tests representative values from each group. Boundary Value Analysis focuses on values at and around the boundaries because defects commonly occur at the edges.”

Indicative assessment: 5/6 for the three-question assessment.

### Additional interview practice
Requirement: Password length must be 8–16 characters.
Three-value BVA values: 7, 8, 9, 15, 16, 17.
Expected: 7 and 17 rejected; 8, 9, 15 and 16 accepted.

## Key takeaways
- Identify the exact minimum and maximum from the requirement.
- Confirm whether boundaries are inclusive or exclusive.
- Calculate values carefully; do not confuse the value just below a boundary with the boundary itself.
- Define expected results for every test value.
- Do not assume a business rule that is not stated.
