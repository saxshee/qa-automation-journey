# Day 5 — Defect Management (QA Learning Journey)

**Status:** In progress  
**Focus:** Defect terminology, bug life cycle, severity, priority, Jira reporting, RCA, workaround, retesting and regression.

> This document records the topics studied so far. The detailed modules on severity, priority, Jira reporting, RCA/workarounds, and retesting/regression remain to be completed.

---

## 1. Error, Defect, Bug and Failure

These terms are related but describe different things.

### Error
A human mistake, such as a developer writing an incorrect condition in code.

### Defect
A flaw in the software caused by an error. Example: the badge deactivation logic does not update the badge status.

### Bug
The commonly used industry term for a software defect. A tester typically raises a bug/defect ticket in Jira.

### Failure
Incorrect behaviour observed when the software executes. Example: a badge that should have been deactivated still permits building access.

### Relationship
1. A human error may introduce a defect.
2. The defect exists in the software.
3. When the defect is triggered during execution, it may cause a failure.

A defect can exist without an observed failure in every execution; the failure depends on whether and how the defect is triggered.

### PIAM example
A PIAM Admin submits a Deactivate Badge request:
- Request status becomes Completed.
- Badge remains Active.
- Employee can still access the building.

The incorrect code written by a developer would be an error; the flawed status-update logic is a defect; the observed access/status behaviour is a failure.

### Interview distinction
A **defect** is a flaw in the software; a **failure** is the incorrect behaviour observed when that flaw is executed.

---

## 2. Bug Life Cycle

The Bug Life Cycle (also called Defect Life Cycle) is the sequence of stages a defect moves through from identification to closure.

### Typical stages

1. **New** — Tester identifies the issue and creates a Jira ticket with reproduction steps, expected and actual results, evidence, environment and relevant details.
2. **Assigned** — Ticket is assigned to the responsible developer or team.
3. **In Progress / Open** — Developer investigates and works on the fix.
4. **Fixed / Resolved** — Developer implements a fix. This does not mean QA has verified it.
5. **Retest** — QA executes the original failed test against the updated build in the appropriate environment.
6. **Verified** — QA confirms that the reported issue is fixed.
7. **Closed** — Defect is formally closed according to the project's workflow.
8. **Reopened** — If the issue still reproduces during retesting, QA reopens it with updated evidence for further investigation.

### Typical flow

New → Assigned → In Progress → Fixed/Resolved → Retest → Verified → Closed

If retesting fails: Retest → Reopened → In Progress → Fixed/Resolved → Retest.

### Important workflow notes
- Jira status names and transitions vary by organisation and project.
- Some workflows use statuses such as Open, Rejected, Duplicate, Deferred or Cannot Reproduce.
- A developer marking a ticket Fixed is not proof that the issue is fixed.
- QA must validate the fix in the correct environment/build.
- If the fix is not deployed to UAT, QA cannot yet retest it.
- A test that cannot be executed because the environment is unavailable is Blocked; this is not automatically a failed test or a reason to reopen a defect.
- Successful retesting should lead to Verified and then Closed, as defined by the team's workflow.

### Roles and responsibilities (typical)
| Stage | Typical owner |
|---|---|
| New | Tester |
| Assigned / triage | Lead or triage team |
| In Progress | Developer |
| Fixed / Resolved | Developer |
| Retest | Tester |
| Verified | Tester |
| Closed | Tester or authorised workflow owner |
| Reopened | Tester |

---

## 3. Severity and Priority — Introduction

These concepts were introduced; the detailed modules are still pending.

- **Severity:** How badly the defect affects the application, functionality, users, data, security or business operations.
- **Priority:** How urgently the defect should be fixed, considering business urgency, release commitments, exposure and risk.

### Typical severity levels
- **Critical / Blocker:** Major functionality unavailable or severe system-wide impact.
- **High:** Important functionality is broken or there is significant user/business impact.
- **Medium:** Partial functionality is affected; a workaround may exist.
- **Low:** Minor impact, such as a cosmetic issue or typo.

### Typical priority levels
- **P1 — Critical:** Requires immediate attention.
- **P2 — High:** Requires urgent attention.
- **P3 — Medium:** Can be handled in the normal development cycle.
- **P4 — Low:** Can be scheduled later.

These labels and mappings are examples, not universal standards. Actual classification must follow the organisation's defect policy and be based on confirmed impact and urgency.

### Examples
- Entire AccessKeeper application unavailable: potentially Critical severity and P1.
- Customer-facing logo incorrect before a major launch: potentially Low severity but High priority.
- Badge deactivation not revoking building access: potentially High or Critical severity depending on the security exposure; priority depends on production exposure and business urgency.

---

## 4. Professional Jira Bug Report — Introduction

A useful defect report should be clear, reproducible and supported by evidence.

Typical fields:
- Summary / Title
- Environment
- Module
- Description
- Preconditions
- Steps to Reproduce
- Expected Result
- Actual Result
- Severity
- Priority
- Attachments / Evidence

### Example from the lesson
**Summary:** [UAT] Deactivate Badge request is marked Completed, but the badge status remains Active.

**Environment:** UAT  
**Module:** Badge Management

**Preconditions:**
- An active employee exists.
- The employee has an active physical badge.
- Tester has the required PIAM Admin permissions.

**Steps to Reproduce:**
1. Log in as an authorised PIAM Admin.
2. Navigate to Deactivate Badge.
3. Select an employee with an active badge.
4. Submit the deactivation request.
5. Complete the workflow.
6. Check the final badge status.

**Expected Result:** After successful completion, the badge should be inactive according to the configured business rules.

**Actual Result:** The request is marked Completed, but the badge remains Active.

**Severity / Priority:** Determine based on confirmed access/security impact, production exposure and business urgency. Do not assume a classification without evidence.

### Good reporting practices
- State what happened, not an unverified theory about why it happened.
- Include exact environment, request/record identifiers, timestamps and build details where relevant.
- Include screenshots, logs or API/database evidence when available and appropriate.
- Separate expected and actual results.
- Avoid vague summaries such as “badge not working.”

---

## 5. RCA, Workaround, Retesting and Regression — Introduction

### RCA (Root Cause Analysis)
Explains why the defect occurred. The observed symptom is not necessarily the root cause.

### Workaround
A temporary, approved way to mitigate the issue until a permanent fix is available. A workaround is not the same as fixing the underlying defect.

### Retesting
Executing the failed test again after a fix is available to confirm that the reported defect has been corrected.

### Regression testing
Testing related and existing functionality after a change to ensure the fix has not introduced new defects or broken previously working behaviour.

Example: After fixing badge deactivation, consider testing related badge activation, replacement and other relevant workflows if they share affected logic. The exact regression scope depends on the change and impact analysis.

---

## 6. Module 1 Assessment — Error, Defect, Bug and Failure

**Result: 10/10 — Passed.**

The 10-question assessment covered:
1. A developer accidentally writes incorrect code — Error.
2. Incorrect logic in badge deactivation — Defect.
3. A deactivated badge still allows building access — Failure.
4. A defect can exist without an observed failure.
5. Testers generally identify and report defects; developers investigate and fix them.
6. Report observed behaviour with evidence, expected and actual results.
7. Developer writes the wrong condition in code — Error.
8. Incorrect status-update logic in the application — Defect.
9. One defect can cause different failures under different conditions.
10. Completed mobile credential request with no credential provisioned — observed failure; root cause still needs investigation.

**Key learning:** Do not confuse the observed failure with the underlying defect or assume the root cause before investigation.

---

## 7. Module 2 Assessment — Bug Life Cycle

The user reported completing the 10-question Module 2 MCQ test. The selected answers and numerical score were not captured in the conversation, so no score is recorded here.

Topics assessed:
- Creating a New defect.
- Developer investigation and fixing.
- Meaning of Fixed versus Closed.
- Retesting after a fix is available in the correct environment.
- Reopening when the issue still reproduces.
- Verifying and closing after successful retesting.
- Waiting for the updated build when it is not deployed to UAT.
- Using Blocked when the environment prevents execution.
- Project-specific Jira workflows.
- Recording a recurrence after a later deployment.

---

## 8. Module 2 Practical Assessment — Deactivate Badge

### Scenario
A PIAM Admin submits a Deactivate Badge request:
- Employee: EMP-1045
- Badge number: 7772-456789
- Initial badge status: Active
- Request status after submission: Completed
- Actual badge status: Active
- Expected badge status: Inactive
- Employee can still access the building.

### User's answers and review

**Task 1 — Defect identification**
- User answer: Create a new bug.
- Review: Correct. Create a New defect with reproducible details.

**Task 2 — Bug title**
- User draft: WF:Prod:Issue with Deactivate badge request,Status not updated and building access still allowed.
- Review: Captured both symptoms, but the scenario environment was UAT, not PROD. Environment labels must be accurate.
- Polished title: [UAT] Deactivate Badge request is marked Completed, but badge remains Active and building access is still allowed.

**Task 3 — Developer marks the issue Fixed**
- User answer: Test it first, and if everything works, get it deployed to the environment.
- Review: Partially correct. The fix must first be available in the appropriate QA/UAT environment. QA retests there. Production deployment is a separate release-management activity; successful UAT verification does not itself authorise production deployment.
- Correct sequence: Developer implements fix → fix deployed to test environment → QA retests → QA verifies → ticket proceeds to closure under the team's workflow.

**Task 4 — Retest still fails**
- User answer: Reopen; attach screenshots of badge still Active and evidence that user still has building access; tell developer status remains Active and access is still allowed.
- Review: Correct.
- Additional useful evidence: request ID, employee ID, badge number, environment, build/version, timestamp, access-control/log evidence and screenshots showing request and badge states.
- Suggested developer communication: “The issue is still reproducible after the latest fix. The Deactivate Badge request is marked Completed, but the badge status remains Active and the employee is still able to access the building. I have attached the supporting evidence and am reopening the defect for further investigation.”

**Task 5 — Retest succeeds**
- User answer: Close the ticket after retesting.
- Review: Correct in principle. Include the verification step: Retest → Verified → Closed, following the Jira workflow.
- Verify request status, badge status and access revocation before closing.

**Practical assessment review:** 8/10 (review estimate based on the response and feedback, not an independently graded platform result).

---

## 9. Learning preference and next steps

The learner is already a working professional who regularly performs PIAM testing, UAT, Jira defect reporting and RCA-related work. Repetitive beginner exercises such as writing ten basic Jira bugs are not useful.

For future practice, prioritise advanced QA engineering:
- Technical root-cause hypotheses and evidence-based investigation.
- Application/API logs, database state and integration boundaries.
- Impact analysis across PIAM modules and external systems.
- Test coverage and edge cases.
- Regression strategy and risk-based testing.
- Advanced defect triage and communication.

### Remaining Day 5 modules
1. Severity — detailed impact assessment.
2. Priority — urgency and business risk.
3. Severity vs Priority — realistic classification exercises.
4. Jira Bug Reporting — advanced reporting and evidence.
5. RCA and Workaround — investigation and mitigation.
6. Retesting and Regression — test selection and risk-based coverage.

**Do not mark Day 5 complete until these remaining modules have been studied and assessed.**
