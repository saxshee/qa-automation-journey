# Day 8 — Equivalence Partitioning

## Learning objectives
- Understand Equivalence Partitioning (EP).
- Identify valid and invalid equivalence partitions.
- Select representative test values from each partition.
- Apply EP to real-world application scenarios.

## 1. What is Equivalence Partitioning?

Equivalence Partitioning is a black-box test design technique. It divides input data into groups (equivalence partitions) that are expected to be processed in the same way.

Instead of testing every possible input, QA selects representative values from each partition.

The technique reduces repetitive test effort while providing coverage across distinct input categories. It does not guarantee that every defect will be found.

## 2. Example: Age validation

Requirement: A user must be between 18 and 60 years old, inclusive, to register.

| Partition | Example values | Expected result |
|---|---|---|
| Below 18 | 10, 15, 17 | Reject |
| 18–60 | 18, 25, 40, 60 | Accept |
| Above 60 | 61, 70, 80 | Reject |

Representative values: 15, 30, 65.

## 3. Real-world examples

### E-commerce — Order quantity
Requirement: A customer can order between 1 and 10 items in one order.

| Partition | Representative value | Expected result |
|---|---:|---|
| Below 1 | 0 | Reject |
| 1–10 | 5 | Accept |
| Above 10 | 11 | Reject |

### Banking — Money transfer
Requirement: A user can transfer between ₹100 and ₹50,000, inclusive.

| Partition | Representative value | Expected result |
|---|---:|---|
| Below ₹100 | ₹10 | Reject |
| ₹100–₹50,000 | ₹25,000 | Accept |
| Above ₹50,000 | ₹50,001 | Reject |

### Food delivery — Coupon eligibility
Requirement: A coupon can be applied when the order value is at least ₹500.

| Partition | Representative value | Expected result |
|---|---:|---|
| Below ₹500 | ₹300 | Coupon rejected |
| ₹500 or more | ₹700 | Coupon accepted |

### Social media — Username length
Requirement: Username must contain 5–15 characters.

| Partition | Representative value | Expected result |
|---|---:|---|
| Fewer than 5 characters | 3 characters | Reject |
| 5–15 characters | 8 characters | Accept |
| More than 15 characters | 20 characters | Reject |

### Movie ticket booking
Requirement: A user can book between 1 and 6 tickets per transaction.

| Partition | Representative value | Expected result |
|---|---:|---|
| Below 1 | 0 | Reject |
| 1–6 | 3 | Accept |
| Above 6 | 8 | Reject |

## 4. PIAM example — Mobile credential eligibility

Requirement: Only active employees are allowed to request mobile credentials.

| Partition | Test data | Expected result |
|---|---|---|
| Active employee | Active employee submits request | Request accepted, subject to other eligibility rules |
| Inactive employee | Inactive employee submits request | Request rejected |
| Terminated employee | Terminated employee submits request | Request rejected |

Note: The expected result for terminated employees must be supported by the stated business requirement. QA should clarify undefined rules rather than assume them.

## 5. How to apply Equivalence Partitioning

1. Understand the requirement and input constraints.
2. Identify categories of inputs expected to behave differently.
3. Divide them into valid and invalid partitions.
4. Select at least one representative value from each partition.
5. Execute the tests and compare actual results with expected results.

Important: Values belong in the same partition only when they are expected to follow the same behavior under the same conditions. If a different rule applies, create another partition.

## 6. Day 8 practice and assessment

### Practice 1 — Employee ID
Requirement: Employee ID must contain exactly 6 digits.

Learner's answer:
- Valid: 876543
- Invalid: 123, 1224, 11, 1, 12345

Feedback:
- Correctly identified a six-digit valid value and shorter invalid values.
- Missed the separate invalid partition for values longer than six digits.
- A complete breakdown is:
  - Fewer than 6 digits: e.g. 12345 — reject.
  - Exactly 6 digits: e.g. 876543 — accept.
  - More than 6 digits: e.g. 1234567 — reject.
- Consider non-numeric input too if the requirement means exactly six numeric digits.

### Practice 2 — Representative employee ID values
Learner's answer:
- Valid: 123455
- Invalid: 1234

Feedback:
- Both examples are valid representatives for their respective partitions.
- The answer omitted the more-than-six-digits partition.
- Representative values should cover every identified partition: 1234, 123455, 1234567.

### Practice 3 — Mobile credential eligibility
Learner's answer:
- Active employee requests mobile credential — accepted.
- Inactive employee requests mobile credential — rejected.
- Terminated employee requests mobile credential — rejected.

Feedback:
- Correctly identified three status partitions and expected outcomes.
- The terminated-employee rule should be confirmed in the requirements.

### Practice 4 — Banking transfer
Requirement: Transfer amount must be between ₹100 and ₹50,000, inclusive.

Learner's answer:
- Valid: ₹101, ₹49,999, ₹25,000.
- Invalid: ₹10, ₹50,001.

Feedback:
- Correctly identified the three partitions:
  - Below ₹100 — invalid.
  - ₹100 to ₹50,000 inclusive — valid.
  - Above ₹50,000 — invalid.
- The examples are valid representatives.
- Additional valid boundary values ₹100 and ₹50,000 should be considered to make the inclusive limits explicit. Boundary Value Analysis will examine boundary values systematically.

## 7. Equivalence Partitioning vs Boundary Value Analysis

- Equivalence Partitioning (EP) selects representative values from groups.
- Boundary Value Analysis (BVA) focuses on values at and around the edges of those groups.

For a six-digit employee ID:
- EP partitions: fewer than 6 digits, exactly 6 digits, more than 6 digits.
- BVA examples: 5, 6, and 7 digits.

For a transfer range of ₹100–₹50,000:
- EP partitions: below ₹100, ₹100–₹50,000, above ₹50,000.
- BVA examines values around ₹100 and ₹50,000.

## 8. Interview-ready definition

“Equivalence Partitioning is a black-box test design technique in which input data is divided into valid and invalid groups that are expected to behave similarly. Instead of testing every possible value, I select representative values from each partition to reduce test effort while maintaining meaningful coverage.”

## Day 8 completion checklist
- [x] Understand Equivalence Partitioning.
- [x] Identify valid and invalid partitions.
- [x] Select representative test values.
- [x] Create examples using real-world applications.
- [x] Practice employee ID validation.
- [x] Practice mobile credential eligibility.
- [x] Practice banking transfer limits.
- [ ] Study Boundary Value Analysis in the next lesson.
