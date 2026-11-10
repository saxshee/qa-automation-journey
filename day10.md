# Day 10 — Decision Table Testing

## Learning objectives
- Understand decision table testing.
- Identify conditions, possible values, rules, and actions.
- Enumerate combinations of conditions.
- Convert each rule into test scenarios.

## 1. What is Decision Table Testing?
Decision Table Testing is a black-box test design technique used when application behavior depends on combinations of multiple conditions. A decision table makes those combinations and their expected outcomes visible.

A column represents one rule or combination. Rows typically represent conditions and resulting actions.

## 2. E-commerce discount example
Policy:
- Customer must be a registered member.
- Order value must be at least ₹2,000.
- A 20% discount is applied only when both conditions are true.

| Condition / action | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Registered member? | Yes | Yes | No | No |
| Order ≥ ₹2,000? | Yes | No | Yes | No |
| Apply 20% discount? | Yes | No | No | No |

Rules:
- R1: Member and qualifying order → 20% discount.
- R2: Member but order below threshold → no discount.
- R3: Non-member with qualifying order → no discount.
- R4: Non-member and order below threshold → no discount.

## 3. Banking login example
Conditions:
- Username correct?
- Password correct?

| Rule | Username | Password | Expected result |
|---|---|---|---|
| R1 | Correct | Correct | Login successful |
| R2 | Correct | Incorrect | Login rejected |
| R3 | Incorrect | Correct | Login rejected |
| R4 | Incorrect | Incorrect | Login rejected |

The expected result may include the appropriate error response, but exact messages and account-security behavior must be based on requirements.

## 4. How to create a decision table
1. Read the requirement and identify all relevant conditions.
2. List the possible values for each condition.
3. Enumerate all meaningful combinations.
4. Define the expected action or outcome for every rule.
5. Convert rules into test cases with data and expected results.
6. Check for missing, duplicate, or impossible combinations.

## 5. Number of combinations
If there are n independent conditions and each has two possible values (for example, Yes/No), the maximum number of combinations is:
`2^n`

Examples:
- 1 binary condition → 2 combinations.
- 2 binary conditions → 4 combinations.
- 3 binary conditions → 8 combinations.
- 4 binary conditions → 16 combinations.

This formula assumes binary conditions and that all combinations are relevant. If a condition has more than two possible values, or some combinations are impossible, the table must be adjusted accordingly.

## 6. Food delivery exercise
Requirement: An order can be placed only when:
- Restaurant is open.
- Delivery location is serviceable.
- Payment method is valid.

Expected result: Place order only when all three conditions are Yes; otherwise reject the order.

All eight combinations:

| Rule | Restaurant open | Location serviceable | Payment valid | Expected result |
|---|---|---|---|---|
| R1 | Yes | Yes | Yes | Place order |
| R2 | Yes | Yes | No | Reject |
| R3 | Yes | No | Yes | Reject |
| R4 | Yes | No | No | Reject |
| R5 | No | Yes | Yes | Reject |
| R6 | No | Yes | No | Reject |
| R7 | No | No | Yes | Reject |
| R8 | No | No | No | Reject |

Learner's handwritten table used a different ordering of combinations but covered all eight combinations and correctly identified that only Yes/Yes/Yes places the order.

## 7. Learner knowledge check
Question: A banking transaction requires:
- Account active.
- Sufficient balance.
- Transaction limit not exceeded.

How many combinations are there?
Learner answer: “Same as above.”
Evaluation: Correct. Three independent binary conditions produce `2^3 = 8` combinations.

## Key takeaways
- A decision table is useful when several conditions jointly determine an outcome.
- Each rule represents one combination of condition values.
- Test every meaningful combination, not only the happy path.
- The expected result must follow the stated business rule.
- Use `2^n` only when there are n independent binary conditions.
