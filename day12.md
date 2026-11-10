# Day 12 — Exploratory Testing, Error Guessing, and Checklist-Based Testing

## Learning objectives
- Explain exploratory testing and how it differs from random testing.
- Use experience and product knowledge to predict likely defects through error guessing.
- Execute checks systematically using a checklist.
- Distinguish the three approaches.

## 1. Exploratory Testing
Exploratory Testing is an approach in which the tester learns the application, designs tests, and executes them at the same time. The tester explores behavior and adapts the next test based on what is observed.

It is not random clicking. It should have a clear objective, a scope, and notes/evidence of what was explored.

### Example: Food delivery checkout
Objective: Explore checkout behavior.
A tester might:
- Add an item to the cart.
- Increase and decrease quantity.
- Remove an item.
- Apply a coupon.
- Change delivery address.
- Switch payment methods.
- Refresh during checkout.
- Disconnect the internet while placing an order.
- Click Place Order more than once.

Potential finding: Clicking Place Order twice during a slow response creates two orders. This is an illustrative defect that exploratory testing might uncover.

### Characteristics
- Learning and testing happen together.
- Test ideas can change based on observations.
- Useful for uncovering unexpected behavior not covered by predefined cases.
- Relies on tester judgment, product knowledge, and observation.
- Findings should still be documented with steps, data, expected/actual behavior, and evidence where possible.

## 2. Error Guessing
Error Guessing is a technique where testers use experience, domain knowledge, and intuition to predict areas where defects may occur.

Examples:
| Feature | Possible error to investigate |
|---|---|
| Login | Blank username or password |
| Registration | Existing email address |
| Payment | Multiple clicks on Pay |
| Shopping cart | Quantity 0 or negative |
| File upload | Unsupported file type |
| Password | Spaces-only input |
| Search | Special characters |

### Banking transfer example
A tester might investigate:
- Negative transfer amount.
- Zero transfer amount.
- Multiple submission clicks.
- Network disconnection during submission.
- Insufficient account balance.

These are test ideas based on likely failure points. The expected behavior must still be established from requirements.

## 3. Checklist-Based Testing
Checklist-Based Testing uses a predefined list of checks to guide verification. A checklist is usually higher-level and shorter than a detailed test case with preconditions, steps, and expected results.

### Login page checklist
- Verify login with valid username and password.
- Verify login with invalid password.
- Verify blank username.
- Verify blank password.
- Verify password masking.
- Verify Forgot Password functionality.
- Verify account lock after repeated failed attempts.
- Verify logout functionality.

A tester marks each check as completed and records failures or evidence. A checklist helps prevent important areas from being overlooked, but it does not automatically provide the detailed steps or test data of a full test case.

## 4. Comparison
| Technique | Main focus | Example |
|---|---|---|
| Exploratory Testing | Learn, explore, and test while adapting | Explore checkout and discover duplicate order behavior |
| Error Guessing | Predict likely defects using experience | Suspect multiple Pay clicks may duplicate a transaction |
| Checklist-Based Testing | Follow a predefined list of checks | Verify the agreed login checklist |

## 5. Knowledge check
1. Exploring a shopping application and discovering duplicate orders by clicking Place Order twice: Exploratory Testing.
2. Predicting that a negative payment amount may cause a defect: Error Guessing.
3. Verifying predefined login checks from a list: Checklist-Based Testing.

These are the concepts and examples covered in the lesson. A full practical assessment and review should be completed before marking Day 12 fully complete.

## Key takeaways
- Exploratory testing is purposeful exploration, not random clicking.
- Error guessing uses experience to identify likely failure areas.
- Checklist-based testing provides a repeatable set of checks.
- These approaches can complement formal test cases and other test design techniques.
- Always record defects and evidence clearly.
