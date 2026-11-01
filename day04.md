# Day 4 — Test Scenarios, Test Cases & Test Design

**Learning track:** Manual QA  
**Focus:** Turning requirements into testable scenarios, conditions and detailed test cases  
**Practical domain:** Login functionality and PIAM / AccessKeeper badge deactivation

---

## Learning objectives

By the end of Day 4, you should be able to:
- Explain the difference between a requirement, test scenario, test condition and test case.
- Identify preconditions and test data.
- Write clear test steps and expected results.
- Compare expected and actual results during execution.
- Distinguish Pass, Fail, Blocked and Not Executed.
- Understand positive and negative testing.
- Write login test cases.
- Apply test design to a real PIAM badge-deactivation workflow.
- Identify a defect and write a clear bug title from a failed test.

---

## 1. From requirement to test execution

Example requirement:

> The system should allow an active employee to log in using a valid username and password.

A tester breaks this down into:

1. **Requirement:** What does the business want?
2. **Test scenario:** What functionality should be tested?
3. **Test conditions:** Which rules or aspects must be verified?
4. **Test cases:** What exact steps, data and expected results will verify each condition?
5. **Test execution:** Run the test and compare actual behaviour with the expected result.

A simple flow:

**Requirement → Test Scenario → Test Conditions → Test Cases → Test Execution → Result**

---

## 2. Test scenario — what should we test?

A **test scenario** is a high-level situation or functionality that needs to be verified.

Example: for an e-commerce application:
- Verify login functionality.
- Verify new user registration.
- Verify product search.
- Verify adding products to the cart.
- Verify checkout.
- Verify payment.

One module can have multiple scenarios, and one scenario can have multiple test cases.

### Lift example

- **Test scenario:** Verify the overall functionality of a lift.
- **Possible test cases:**
  1. Verify that the lift moves when Floor 2 is selected.
  2. Verify that the lift door opens after reaching the selected floor.
  3. Verify that the lift does not operate when overloaded.
  4. Verify that the emergency alarm works.
  5. Verify that the floor indicator displays the correct floor.

A test case is not merely a component. It is a specific test with steps, data and expected results.

---

## 3. Test case — how should we test?

A **test case** is a documented set of instructions used to verify a particular functionality or requirement.

Common test case fields:

| Field | Meaning |
|---|---|
| Test Case ID | Unique identifier |
| Test Scenario | Functionality being tested |
| Test Description | What exactly is being verified |
| Preconditions | What must be true before execution |
| Test Steps | Actions performed by the tester |
| Test Data | Inputs used during execution |
| Expected Result | What should happen |
| Actual Result | What happened during execution |
| Status | Pass, Fail, Blocked or Not Executed |

### Example: login with valid credentials

**Test Case ID:** TC_LOGIN_001  
**Scenario:** Verify login functionality.  
**Description:** Verify that an active registered user can log in using valid credentials.

**Preconditions:**
- User account exists.
- User account is active.
- Login page is accessible.

**Test Data:**
- Username: `sakshi.qa`
- Password: `Valid@123`

**Steps:**
1. Open the application.
2. Navigate to the login page.
3. Enter the username.
4. Enter the password.
5. Click Login.

**Expected Result:** User should successfully log in and land on the dashboard.  
**Actual Result:** Record after execution.  
**Status:** Not Executed.

### Why do we need preconditions?

Preconditions describe what must already be true before starting a test. For successful login, the user must already exist in the application.

- **Precondition:** User account is already created.
- **Test step:** Enter username and password.

Preconditions are not the same as test steps.

---

## 4. Test condition — which specific rule are we verifying?

A **test condition** is a particular requirement, rule or aspect of a feature that needs to be tested.

For a login requirement:
1. Username is mandatory.
2. Password is mandatory.
3. Only active users can log in.
4. Invalid credentials should be rejected.

These are test conditions.

| Test condition | Related test case |
|---|---|
| Username is mandatory | Login with blank username |
| Password is mandatory | Login with blank password |
| Only active users can log in | Login using an inactive account |
| Invalid credentials are rejected | Login using wrong password |

- **Scenario:** Verify login functionality.
- **Condition:** Password cannot be blank.
- **Case:** Leave password empty, enter a valid username and click Login.

Terminology can vary slightly between organisations and test management tools, but this practical distinction is useful.

---

## 5. Test data — choosing the inputs

**Test data** is the information used while executing test cases.

| Category | Username | Password |
|---|---|---|
| Valid | sakshi.qa | Valid@123 |
| Invalid username | random123 | Valid@123 |
| Invalid password | sakshi.qa | Wrong@123 |
| Both blank | Empty | Empty |
| Username blank | Empty | Valid@123 |
| Password blank | sakshi.qa | Empty |
| Inactive user | inactive.qa | Valid@123 |

A tester should not test only one input. Different data combinations help reveal different defects.

---

## 6. Positive testing vs negative testing

### Positive testing

Provide valid inputs and verify that the system works as expected.

**Example:** Log in using a registered active account and the correct password.  
**Expected:** Login succeeds.

### Negative testing

Provide invalid inputs or unexpected conditions and verify that the system handles them correctly.

**Example:** Log in using an incorrect password.  
**Expected:** Login is rejected with an appropriate error.

Negative testing is not about making the application fail. It verifies that the application handles invalid situations correctly.

---

## 7. Expected result vs actual result

- **Expected result:** What should happen according to the requirement.
- **Actual result:** What actually happened when the test was executed.

Example: the requirement says an incorrect password must not allow login.

| Item | Result |
|---|---|
| Test data | Correct username + wrong password |
| Expected result | Login should be rejected |
| Actual result | Dashboard opens |
| Status | Fail |

### Execution statuses

- **Pass:** Actual result matches expected result.
- **Fail:** Actual result does not match expected result.
- **Blocked:** The test cannot be executed because a dependency or blocker prevents it.
- **Not Executed:** The test has not yet been run.

An application error during execution is not automatically a blocker. If the application was expected to work and instead throws an error, that may be a failure/defect. If the test environment is unavailable, the test may be blocked.

---

## 8. Ten login test cases

### TC_LOGIN_001 — Valid login
**Type:** Positive  
**Steps:** Enter valid username and password, then click Login.  
**Expected:** User reaches the dashboard.

### TC_LOGIN_002 — Invalid password
**Type:** Negative  
**Steps:** Enter a valid username and incorrect password.  
**Expected:** Login fails with an appropriate error message.

### TC_LOGIN_003 — Non-existing username
**Type:** Negative  
**Steps:** Enter an unregistered username and a password.  
**Expected:** User is not allowed to log in.

### TC_LOGIN_004 — Both fields blank
**Type:** Negative  
**Steps:** Leave username and password empty; click Login.  
**Expected:** Required-field validation appears.

### TC_LOGIN_005 — Blank username
**Type:** Negative  
**Steps:** Leave username blank and enter a valid password.  
**Expected:** Username validation appears and login does not proceed.

### TC_LOGIN_006 — Blank password
**Type:** Negative  
**Steps:** Enter a valid username and leave password blank.  
**Expected:** Password validation appears.

### TC_LOGIN_007 — Password masking
**Type:** UI / Functional  
**Steps:** Enter a password in the password field.  
**Expected:** Password characters are masked by default.

### TC_LOGIN_008 — Show/hide password
**Type:** UI / Functional  
**Steps:** Enter a password and click the eye icon; click it again.  
**Expected:** Password becomes visible and is masked again when toggled.

### TC_LOGIN_009 — Whitespace handling
**Type:** Negative / Validation  
**Steps:** Enter spaces in username and/or password.  
**Expected:** Application handles whitespace according to defined requirements and does not allow unintended authentication.

### TC_LOGIN_010 — Locked account
**Type:** Negative  
**Steps:** Attempt login using an account that has been locked.  
**Expected:** Login is denied and an appropriate message is displayed.

---

## 9. Practical PIAM example — Deactivate Badge

### Requirement

A PIAM Admin should be able to deactivate an active physical badge assigned to an employee.

### Test scenario

Verify the badge deactivation functionality.

### Test conditions

1. Only authorised PIAM Admins can deactivate badges.
2. Only active badges can be deactivated.
3. Badge status should change after successful deactivation.
4. Deactivated badges should no longer grant access.
5. The system should show an appropriate confirmation or error message.

### Test data

| Field | Value |
|---|---|
| User role | PIAM Admin |
| Badge ID | BADGE-1001 |
| Initial status | Active |
| Employee | Active employee |
| Second badge | BADGE-1002 |
| Second badge status | Deactivated |

### Detailed test case: TC_BADGE_001 — Deactivate an active badge

**Preconditions:**
1. PIAM Admin has access to the application.
2. Employee is active.
3. Employee has an active physical badge assigned.
4. Badge is eligible for deactivation.

**Test data:**
- User: Active employee
- Badge ID: BADGE-1001
- Initial status: Active
- User role: PIAM Admin

**Steps:**
1. Log in as PIAM Admin.
2. Navigate to the Deactivate Badge request.
3. Search for and select an active employee.
4. Select the employee's active badge.
5. Submit the deactivation request.
6. Complete any required approval or processing.
7. Verify the badge status and assignment details.

**Expected results:**
1. Deactivation request should be processed successfully.
2. Badge status should change from Active to the configured deactivated status.
3. Badge Valid To date should be updated to the current date, if this is the defined business rule.
4. Badge should be unassigned from the employee's inventory, if required by the system design.
5. Deactivated badge should no longer grant physical access.

**Actual Result:** Record after execution.  
**Status:** Not Executed.

### Important workflow distinction

Submitting a request does not necessarily mean the badge has already been deactivated. In a workflow-driven PIAM system, validate both request processing and the final badge state.

---

## 10. Day 4 assignment — learner's work and review

### Task 1: Explain test scenario vs test case

**Learner's answer:** A test scenario is an overview of what can be tested. The learner used a lift as an example. A test case covers specific checks such as buttons, lights, maximum weight, overload behaviour and alarm.

**Review:** Correct understanding. Refinement: a test case is not merely a component; it is a specific test with steps, test data and expected results.

### Task 2: Write test conditions for badge deactivation

**Learner's conditions:**
1. Badge should be active to deactivate.
2. After deactivation, badge status should change.
3. Already deactivated badge cannot be deactivated again.

**Review:** All three are valid test conditions. Use the exact configured status value (for example, Inactive or Deactivated) rather than assuming the terms are interchangeable.

### Task 3: Write five badge-deactivation test cases

**Learner's cases and feedback:**

1. **Active badge appears for deactivation:** Verify that an active badge is available for selection. This checks availability for selection.
2. **Already inactive badge:** Negative test. Verify the system prevents another deactivation or displays the expected validation, according to requirements.
3. **Status changes from Active to Inactive:** Verify the badge's final status after successful processing.
4. **Only authorised user can deactivate:** Verify an end user cannot deactivate their own badge and only authorised roles can perform the action. This is an authorisation/security test.
5. **Valid To date changes to current date:** Verify the date is updated according to the configured business rule.

**Additional suggested test case:** If deactivation processing fails, verify that the badge is not incorrectly marked as deactivated. Use a controlled failure condition in a suitable test environment.

### Task 4: Detailed badge-deactivation test case

**Learner's initial preconditions:**
- User should be active.
- User should have an active badge.

**Learner's initial test data:** Active badge assigned to an active user.

**Learner's initial steps:**
1. User logs into the application.
2. User opens the request.
3. Select a valid active user with an active badge.
4. Select a badge to deactivate.
5. Click confirm.

**Learner's expected results:**
- User badge is deactivated.
- User badge Valid To is current date.
- Badge is unassigned from the user's asset inventory.
- Status changes to inactive.

**Improved professional test case:**

**Test Case ID:** TC_BADGE_001  
**Title:** Verify successful deactivation of an active badge.

**Preconditions:**
1. PIAM Admin has access to the application.
2. Employee is active.
3. Employee has an active physical badge assigned.
4. Badge is eligible for deactivation.

**Test data:**
- User: Active employee
- Badge ID: BADGE-1001
- Initial status: Active
- User role: PIAM Admin

**Steps:**
1. Log in as PIAM Admin.
2. Navigate to the Deactivate Badge request.
3. Search for and select an active employee.
4. Select the employee's active badge.
5. Submit the deactivation request.
6. Complete any required approval or processing.
7. Verify the badge status and assignment details.

**Expected results:**
1. Deactivation request should be processed successfully.
2. Badge status should change from Active to the configured deactivated status.
3. Badge Valid To date should be updated to the current date, if this is the defined business rule.
4. Badge should be unassigned from the employee's inventory, if required by system design.
5. Deactivated badge should no longer grant physical access.

**Key review point:** Separate request submission from workflow completion and final badge state. A submitted request does not necessarily mean the badge has already been deactivated.

### Task 5: Pass, Fail and Blocked

**Learner's answer:**
- Expected result equals actual result → Pass.
- Expected result does not equal actual result → Fail.
- Any other exception → Blocked.

**Review:**
- Pass and Fail definitions are correct.
- Blocked needs refinement: a test is Blocked when it cannot be executed because a dependency or blocker prevents testing. An application error during execution may be a Fail if the application was expected to work. An unavailable test environment may make the test Blocked.

---

## 11. Final Day 4 challenge — request completed but badge remains active

**Scenario:** A PIAM Admin submits a Deactivate Badge request. The request status becomes Completed, but the badge is still showing Active in AccessKeeper.

**Learner's answers:**

1. **Status:** Fail.
2. **Expected result:** The badge should have been marked as Inactive.
3. **Bug title:** `WF:PROD: Deactivate badge req got completed but badge status is still active`

**Review:** All three answers are correct.

Suggested polished bug title:

**[PROD] Deactivate Badge request is marked Completed, but the badge status remains Active.**

A fuller expected result may also include the Valid To date being updated, the badge being unassigned, and access being revoked—where those behaviours are required by the specification.

**Important QA principle:** A request marked Completed does not necessarily mean the underlying business operation succeeded. Always validate the final system state.

---

## 12. Day 4 knowledge-check quiz

Use these questions to revise the core concepts.

1. You need to test whether a user can reset their password. Is this a test scenario, test case or test data?
2. You write detailed steps, username, password and expected output. What are you creating?
3. You enter wrong credentials to test login. What are the wrong credentials?
4. The requirement says login must fail, but the application opens the dashboard. What is the status?

**Answer key:**
1. Test Scenario.
2. Test Case.
3. Test Data.
4. Fail.

### Additional review questions

1. What is the difference between a test scenario and a test case?
2. Can one test scenario have multiple test cases?
3. What are preconditions in a test case?
4. What is test data?
5. What is the difference between expected and actual results?
6. What is positive testing?
7. What is negative testing?
8. What is the difference between a test condition and a test case?
9. When do you mark a test case as Blocked?
10. How do you decide whether a test case has passed or failed?

**Interview-ready answer — Can one test scenario have multiple test cases?**

Yes. One test scenario can have multiple test cases because the same functionality needs to be tested under different conditions, such as valid inputs, invalid inputs, blank fields and boundary conditions.

---

## Day 4 completion checklist

- [x] Understand test scenarios.
- [x] Understand test cases and their fields.
- [x] Understand test conditions.
- [x] Understand preconditions.
- [x] Understand test data.
- [x] Understand positive and negative testing.
- [x] Understand expected vs actual results.
- [x] Understand Pass, Fail, Blocked and Not Executed.
- [x] Review ten login test cases.
- [x] Apply test design to PIAM badge deactivation.
- [x] Write and review five badge-deactivation test cases.
- [x] Write a detailed badge-deactivation test case.
- [x] Complete the final defect-identification challenge.

**Day 4 status:** Completed after the learner's answers and final challenge review.

**Next lesson:** Day 5 — Bug Life Cycle, Severity, Priority and professional Jira bug reporting.
