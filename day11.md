# Day 11 — State Transition Testing

## Learning objectives
- Understand states, events/actions, and transitions.
- Test valid and invalid state changes.
- Create state-transition scenarios for login and order lifecycles.
- Verify that an invalid action does not change the current state.

## 1. What is State Transition Testing?
State Transition Testing is a black-box test design technique used to verify how an application behaves when it moves from one state to another after an event or action.

A state is the application's current condition. A transition is the movement from one state to another because of an event or action.

Think in three parts:
1. Current state.
2. Event/action.
3. Expected next state.

## 2. Banking login example
Assumption for this example: the application locks an account after three consecutive incorrect password attempts.

Possible states:
- Active: account is not locked.
- Failed Attempt 1.
- Failed Attempt 2.
- Locked.
- Logged In after successful authentication.

Example transitions:

| Current state | Action | Expected next state |
|---|---|---|
| Active | Incorrect password (1st) | Failed Attempt 1 |
| Failed Attempt 1 | Incorrect password (2nd) | Failed Attempt 2 |
| Failed Attempt 2 | Incorrect password (3rd) | Locked |
| Active | Correct password | Logged In |
| Failed Attempt 1 | Correct password | Logged In |
| Failed Attempt 2 | Correct password | Logged In |
| Locked | Correct password | Remains Locked |

For three allowed failed attempts:
- After first incorrect attempt: 2 attempts remain.
- After second incorrect attempt: 1 attempt remains.
- After third incorrect attempt: account becomes locked.

The exact reset behavior for failed-attempt counters and account-unlock process must be confirmed from product requirements.

## 3. What should QA verify?
- The account moves to the correct state after each action.
- The lock happens at the specified attempt count, not earlier or later.
- Correct credentials work when the account is not locked.
- A locked account cannot log in merely by entering the correct password if the requirement says an unlock process is required.
- Error messages and remaining-attempt counts are accurate.
- The account state is persisted correctly.

## 4. E-commerce order lifecycle
Illustrative order states:
`Order Placed → Confirmed → Shipped → Delivered`

QA should test:
- Valid transitions, such as Confirmed → Shipped.
- Invalid transitions, such as Delivered → Shipped, if the business rules prohibit them.
- Whether an action leaves the order unchanged when the transition is not permitted.

### Delivered order cancellation scenario
Scenario: An order is already Delivered and the customer clicks Cancel Order.

Expected behavior under the example business rule:
- Cancellation is not allowed after delivery.
- The application displays a suitable message.
- Order status remains Delivered.
- No cancellation or refund workflow is incorrectly initiated.

This is State Transition Testing because QA checks the current state (Delivered), the action (Cancel), and the expected next state (still Delivered). It tests an invalid transition.

Important: Actual cancellation/refund rules vary by product and must be confirmed rather than assumed.

## 5. Decision Table vs State Transition Testing
| Decision Table Testing | State Transition Testing |
|---|---|
| Focuses on combinations of conditions | Focuses on states and movement between states |
| Example: transaction allowed based on account, balance, and limit | Example: account moves from active to locked |
| Useful for business rules with multiple conditions | Useful for workflows, status lifecycles, and account states |

## 6. Learner assessment and feedback
Question 1: Initial state?
Learner answer: Open.
Feedback: Correct; “Active” is a clearer state label for the example.

Question 2: After first incorrect password?
Learner answer: Error, 3 attempts left.
Feedback: The remaining count should be 2, assuming three total attempts are allowed.

Question 3: After second incorrect password?
Learner answer: Error, 2 attempts left.
Feedback: The remaining count should be 1. The learner had the right idea of decrementing the counter, but the displayed count was one too high.

Question 4: After third incorrect password?
Learner answer: Account locks.
Feedback: Correct.

Question 5: Correct password after account is locked?
Learner answer: Remains locked.
Feedback: Correct under the stated example assumption.

Indicative assessment: 4.5/5.

Practical question: What if a user tries to cancel an order after it reaches Delivered?
Initial learner response suggested changing it to Cancelled. Feedback clarified that, under the example rule, Delivered → Cancelled is invalid; the order should remain Delivered and cancellation should not start. Learner confirmed understanding.

## Key takeaways
- Always identify the current state, action/event, and expected next state.
- Test both valid and invalid transitions.
- Verify the resulting status, message, and any related side effects.
- State-transition expectations must come from documented business rules.
