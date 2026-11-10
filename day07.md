# Day 7 — Week 1 Review: Mock QA Interview

**Date:** 10 November 2026  
**Repository:** `saxshee/qa-automation-journey`  
**Status:** Mock interview practice completed; full Week 1 revision and quiz still pending.

## Interview format

- One question at a time.
- Answers given verbally in the user's own words.
- Interviewer provided corrections and follow-up questions.
- Examples were grounded in PIAM and mobile credential workflows.

## Questions, answers and feedback

### 1. Differentiate QA and QC

**User's understanding**
- QA means Quality Assurance and is process-oriented.
- QA activities help prevent defects throughout the product lifecycle.
- QC means Quality Control and involves testing the product to identify defects.

**Interview example**
- QA: reviewing requirements and identifying possible risks or unclear rules while a mobile credential feature is being built.
- QC: executing test cases to verify whether activating a mobile credential changes its status to Active as expected.

**Correction**
- QC does not simply happen after development. QC activities are performed during the product's testing and quality-control activities.
- Say that QA focuses on improving processes and preventing defects, while QC focuses on evaluating the product and detecting defects.

**Interview-ready answer**
> QA is process-oriented and focuses on preventing defects by improving quality throughout the software development lifecycle. QC is product-oriented and focuses on detecting defects by inspecting and testing the software.

### 2. Purpose of a Sprint Goal

**User's answer**
The user explained a Sprint Goal using a mobile credential example: deliver a capability that lets an employee request a mobile credential and have it assigned and activated.

**Feedback**
- Good understanding of the outcome the team is working toward.
- A Sprint Goal is not necessarily “complete an entire module.” It is the single coherent objective for the Sprint.
- A Sprint is a fixed-length event of one month or less; common durations are one to four weeks.

**Interview-ready answer**
> A Sprint Goal is the single objective that gives the Sprint its purpose. For example, enable eligible employees to request and successfully receive a mobile credential.

### 3. Name two states in a defect life cycle

**User's answer**
- Assigned
- Retesting

**Feedback**
Both are valid workflow states in many defect-management processes. The exact states and transitions depend on the organisation's Jira workflow.

**Typical illustrative flow**
New → Assigned → In Progress → Fixed/Resolved → Retest → Verified → Closed.

If the defect still exists during retesting, it may be Reopened. Do not assume every organisation uses exactly the same labels.

### 4. Scenario: request is Completed but mobile credential is not provisioned

**Scenario**
An employee's mobile credential request displays **Completed**, but the credential is not provisioned on the device.

**User's response**
- Correctly classified identifying this issue during testing as a QC activity.
- Suggested documenting reproduction steps, capturing screenshots as evidence, and creating a developer ticket.

**Feedback**
Good practical approach. Improve the defect report by recording:
- Environment and build/version.
- Test identity and relevant request details (using approved, non-sensitive test data).
- Preconditions and exact reproduction steps.
- Expected result: credential is provisioned and status accurately reflects the outcome.
- Actual result: request says Completed but credential is absent from the device.
- Evidence: screenshots, request ID, timestamps, relevant logs/API responses where accessible.
- Impact and frequency/reproducibility.

After the fix:
1. Retest the exact failed scenario.
2. Run risk-based regression around request submission, provisioning, status updates and related credential flows.

**Important distinction**
The developer investigates and fixes the defect; QA verifies the fix and checks for regressions.

### 5. Retesting vs Regression Testing

**User's answer**
- Retesting: after a defect has been fixed and released to the tester, QA tests the same issue again.
- Regression: test related functionality that may have been affected. The user gave examples including active/inactive cases, assignment and valid-from/valid-to dates around mobile credential provisioning.

**Feedback**
Correct distinction and a good PIAM example.

**Interview-ready answer**
> Retesting verifies that a specific reported defect has been fixed. Regression testing checks that existing or related functionality still works after a change.

Example:
- Retesting: verify that a duplicate mobile credential request is now rejected.
- Regression: verify that a valid first-time request, provisioning, status updates and relevant date validations still work.

### 6. What are Acceptance Criteria?

**User's answer**
Acceptance criteria are conditions describing what should happen for a change request, including preconditions and expected behavior.

**Feedback**
Good foundation. Avoid describing acceptance criteria as the test steps themselves. They define the conditions a feature must satisfy; QA derives test scenarios and test cases from them.

**Interview-ready answer**
> Acceptance Criteria are specific, testable conditions that a feature must satisfy to meet the requirement and be considered acceptable.

### 7. Acceptance Criterion: prevent duplicate mobile credential requests

**User's example**
If a user already has a mobile credential on their profile and tries to submit another request, the system should show an error indicating that the user already has a mobile credential.

**Feedback**
This is a useful negative acceptance criterion. The business rule should explicitly define which existing credential states prevent a new request (for example, Active, Pending, or both). Do not assume those states without confirmation.

**Possible Given–When–Then wording**
- **Given** an employee already has an active mobile credential,
- **When** the employee submits another mobile credential request,
- **Then** the system rejects the duplicate request and displays a clear message explaining that an active mobile credential already exists.

### 8. Sprint Goal vs Sprint Tasks

**User's answer**
- Sprint Goal: activate/enable mobile credential functionality.
- Sprint Tasks: the work needed to achieve it, such as requiring an active profile and creating the backend request.

**Feedback**
Correct distinction. Keep the goal focused on the outcome, not a list of implementation tasks.

**Interview-ready answer**
> The Sprint Goal describes the outcome the team wants to achieve; Sprint tasks are the individual pieces of work the team plans to complete to achieve that outcome.

## Strengths demonstrated

- Connects QA concepts to real PIAM workflows.
- Understands that QC includes executing test cases and identifying product defects.
- Can explain retesting and regression using relevant integration examples.
- Includes reproducibility steps and screenshots when reporting a defect.
- Understands the difference between a Sprint Goal and the work/tasks used to achieve it.
- Recognises acceptance criteria as conditions describing expected feature behavior.

## Areas to improve

1. **Use precise terminology:** say QC detects defects; it does not “control” bugs.
2. **Make answers concise:** start with a direct definition, then give one example.
3. **Acceptance Criteria vs Test Cases:** criteria define what must be true; test cases describe how QA verifies it.
4. **Use Given–When–Then consistently:** state the precondition, action and expected outcome separately.
5. **Defect reporting:** include expected vs actual result, environment, build, evidence and reproducible steps—not screenshots alone.
6. **Sprint terminology:** describe the Sprint Goal as an outcome, not simply completion of a module.

## Practice status

| Activity | Status |
|---|---|
| Verbal mock interview practice | Completed |
| QA vs QC discussion | Practiced |
| Sprint Goal and Sprint Tasks | Practiced |
| Defect life cycle states | Practiced |
| PIAM mobile credential defect scenario | Practiced |
| Retesting vs Regression | Practiced |
| Acceptance Criteria | Practiced |
| Given–When–Then formulation | Practiced; needs further practice |
| Full Week 1 ten-question quiz | Pending |
| SDLC/STLC explanation without notes | Pending |
| Remaining Day 5 topics (severity, priority, RCA, etc.) | Pending |

## Next steps

- Complete the full Week 1 quiz, focusing on previously weak topics.
- Practice explaining SDLC and STLC without notes.
- Continue Day 5 topics: severity, priority, defect workflow, RCA and related concepts.
- Continue Week 2, Day 8 after the planned Week 1 review.
