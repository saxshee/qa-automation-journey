# Day 14 – Test Design Techniques Review

## Goal
Review the test design techniques covered in Days 8–13 and understand when to apply each technique.

## 1. Equivalence Partitioning (EP)
Divide input data into groups (partitions) expected to behave similarly. Test representative values from each valid and invalid partition.

Example: If an allowed age range is 18–60:
- Below 18: invalid partition
- 18–60: valid partition
- Above 60: invalid partition

Representative values could be 15, 30 and 65.

## 2. Boundary Value Analysis (BVA)
Test values at and around the edges of an allowed range, because defects often occur at boundaries.

Example: Quantity allowed from 1 to 10:
- 0: just below minimum
- 1: minimum
- 2: just above minimum
- 9: just below maximum
- 10: maximum
- 11: just above maximum

**EP vs BVA:** EP tests representative values from groups; BVA focuses on boundary values.

## 3. Decision Table Testing
Use a decision table when the expected result depends on combinations of conditions.

Example: An order receives a discount only when:
- Customer is a registered member; AND
- Order amount is at least ₹2,000.

List the possible Yes/No combinations and define the expected outcome for each combination.

For n independent binary conditions, there are 2^n possible combinations before any valid rule-based reduction.

## 4. State Transition Testing
Test how an application moves from one state to another after an event or action.

Example: An account becomes locked after three consecutive incorrect password attempts.

Test:
- First and second incorrect attempts: account remains unlocked.
- Third incorrect attempt: account becomes locked.
- Correct password after lockout: account remains locked if that is the specified rule.

Validate both allowed and disallowed transitions.

## 5. Exploratory Testing
The tester learns the application, designs tests and executes them while exploring. It is purposeful and guided by observations, risks and questions—not random clicking.

Example: Disconnect the internet during checkout and observe whether the application handles the failure safely.

## 6. Error Guessing
Use experience and knowledge of the application to predict where defects may occur.

Examples:
- Submit the same request twice quickly.
- Enter unexpected or very long input.
- Disconnect a dependent service during processing.
- Refresh or navigate back during checkout.

## 7. Checklist-Based Testing
Use a prepared list of checks to guide testing. A checklist is usually higher-level than a detailed test case.

Example – Shopping cart:
- Item count is correct.
- Item price is correct.
- Discount is applied correctly.
- Tax and delivery charges are correct.
- Total payable amount is correct.
- Cart contents persist after refresh.

## 8. Test Case Design Reminder
A test case commonly includes:
- Test case ID and scenario
- Preconditions
- Test steps
- Test data
- Expected result
- Actual result
- Execution status

## Quick comparison

| Technique | Best used when |
|---|---|
| Equivalence Partitioning | Inputs can be grouped into similar classes |
| Boundary Value Analysis | Inputs have minimum/maximum limits |
| Decision Table | Outcomes depend on combinations of conditions |
| State Transition | Behavior depends on current state and events |
| Exploratory Testing | Learning and investigating behavior while testing |
| Error Guessing | Experience suggests likely failure areas |
| Checklist-Based Testing | A repeatable set of checks is useful |

## QA reminder
Choose techniques based on the requirement and risk. Do not assume a business rule that has not been specified; clarify it with the Product Owner or relevant stakeholder.
