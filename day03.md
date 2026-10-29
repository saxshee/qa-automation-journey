# Day 3 Notes — Types of Software Testing

**Learning path:** Manual QA → Automation QA → AI/LLM Testing  
**Topic:** Functional, Non-functional, Regression, Retesting, Smoke, and Sanity Testing

---

## 1. Functional Testing

**Definition:** Functional testing verifies that a feature behaves according to its specified requirements.

**Main question:** *Does the feature work correctly?*

Examples:
- Login succeeds with valid credentials.
- Login is rejected with an incorrect password.
- A user can submit a badge-deactivation request when authorized.
- A required field displays validation when left empty.

**PIAM example:** Submit a request to deactivate an eligible active badge. Verify that the request is accepted and the resulting workflow/status matches the requirements.

**Remember:** Focus on *what the system does*.

## 2. Non-functional Testing

**Definition:** Non-functional testing evaluates quality attributes and how well the system operates, rather than only checking a feature's business behavior.

**Main question:** *How well does the system work?*

Common areas:
- **Performance:** response time, throughput, behavior under load.
- **Security:** access control, authentication, protection against unauthorized access.
- **Usability:** whether the interface is understandable and usable.
- **Compatibility:** behavior across supported browsers, devices, or environments.
- **Reliability/stability:** whether the system operates consistently over time.

**PIAM example:** Check whether a reconciliation job handles the expected workload within the agreed time, or whether a user without the required role is prevented from accessing a protected function.

**Remember:** Focus on *quality attributes* such as speed, security, usability, and stability.

> Security can include functional checks (for example, a role-based access rule) as well as broader non-functional security testing. The classification depends on the requirement and test objective.

## 3. Retesting (Confirmation Testing)

**Definition:** Retesting verifies that a specific defect has been fixed by executing the previously failed test again.

**Main question:** *Does the exact bug still happen after the fix?*

Example:
1. A test shows that badge deactivation fails.
2. The developer fixes the defect.
3. QA repeats the same steps with appropriate data.
4. If the actual result now matches the expected result, the defect can be marked as fixed, subject to the team's workflow.

**PIAM example:** Repeat the exact steps that previously caused an eligible badge-deactivation request to fail.

**Remember:** Retesting targets the *specific defect*.

## 4. Regression Testing

**Definition:** Regression testing checks whether a code change, configuration change, or defect fix has negatively affected previously working functionality.

**Main question:** *Did the change break anything else that used to work?*

Example: After fixing badge deactivation, also check related badge activation, replacement, and other relevant existing workflows.

**PIAM example:** After changing badge eligibility logic, test the affected flow and related flows that may rely on the same rules or services.

**Remember:** Regression testing looks for *unintended side effects*.

## 5. Smoke Testing

**Definition:** Smoke testing is a broad, shallow check of critical functionality on a new build or deployment to determine whether the build is stable enough for more detailed testing.

**Main question:** *Is this build basically testable?*

Example checks:
- Application opens.
- User can log in.
- Main page loads.
- A critical workflow can be started.
- Key services appear to be available.

**PIAM example:** After a new AccessKeeper build is deployed to a test environment, verify that the application opens, authorized login works, key screens load, and a critical request can be initiated before beginning extensive UAT.

**Remember:** Smoke = *broad coverage, shallow depth, build readiness*.

## 6. Sanity Testing

**Definition:** Sanity testing is a focused check of a particular change or area to determine whether it works as expected and whether further testing in that area is worthwhile.

**Main question:** *Does this specific change appear to work correctly?*

Example: A small change is made to the badge-deactivation screen's filtering logic. Quickly check that the intended badge types appear and the relevant action works.

**PIAM example:** After a targeted fix to a badge filter, check the affected screen and the filter behavior rather than running the entire regression suite.

**Remember:** Sanity = *narrow, focused validation of a change*.

---

## Key Differences

### Retesting vs. Regression Testing

| Retesting | Regression testing |
|---|---|
| Verifies the specific defect fix. | Checks for side effects on existing functionality. |
| Repeats the previously failed test. | Runs relevant tests around and beyond the change. |
| Question: “Is this bug fixed?” | Question: “Did the change break anything else?” |

**Example:** First repeat the failing badge-deactivation test (retesting), then check related activation and replacement workflows (regression testing).

### Smoke vs. Sanity Testing

| Smoke testing | Sanity testing |
|---|---|
| Broad coverage of critical functions. | Narrow focus on a change or affected area. |
| Usually performed on a new build/deployment. | Often performed after a small change or fix. |
| Shallow check of build stability. | Focused check of expected behavior. |
| Question: “Is the build testable?” | Question: “Does this changed area make sense and work?” |

**Note:** Teams may use these terms differently, and their activities can overlap. Follow the project's testing process.

### Functional vs. Non-functional Testing

| Functional | Non-functional |
|---|---|
| Checks specified behavior or business rules. | Checks quality attributes and operational characteristics. |
| Example: valid credentials allow login. | Example: login responds within the agreed performance target. |

---

## One Scenario, Multiple Testing Types

**Scenario:** A developer fixes a bug in badge deactivation.

1. **Retesting:** Repeat the exact failed steps and verify the defect is fixed.
2. **Regression testing:** Check related existing badge workflows for unintended effects.
3. **Sanity testing:** If the change is small and localized, perform a focused check of the affected area.
4. **Smoke testing:** If the fix is delivered in a new build, perform the team's critical build-readiness checks before deeper testing.
5. **Functional testing:** Verify behavior against the relevant requirements.
6. **Non-functional testing:** If the change affects performance, security, reliability, or another quality attribute, test that attribute as appropriate.

These categories are not always mutually exclusive. The same test activity can serve more than one purpose depending on its objective and scope.

---

## Interview-Ready Answers

**Q: What is functional testing?**  
Functional testing verifies whether an application's features behave according to the specified requirements.

**Q: What is non-functional testing?**  
Non-functional testing evaluates quality attributes such as performance, security, usability, compatibility, and reliability.

**Q: What is the difference between retesting and regression testing?**  
Retesting verifies that a specific defect has been fixed. Regression testing checks whether the change has affected previously working functionality.

**Q: What is smoke testing?**  
Smoke testing checks critical functionality broadly and shallowly on a new build to decide whether it is stable enough for further testing.

**Q: What is sanity testing?**  
Sanity testing is a focused check of a particular change or affected area to see whether it behaves as expected.

**Q: Can smoke and sanity testing overlap?**  
Yes. Practices vary by team, but smoke testing is generally broader and build-oriented, while sanity testing is narrower and change-oriented.

---

## Quick Memory Sheet

- **Functional:** Does it work?
- **Non-functional:** How well does it work?
- **Retesting:** Is the specific bug fixed?
- **Regression:** Did the change break anything else?
- **Smoke:** Is the build testable?
- **Sanity:** Does the specific change look right?

## Practice Questions

Try answering without looking at the notes.

1. A developer fixes a failed login test. You repeat the exact failed steps. Which testing type is this?
2. After the login fix, you check that password reset and account lockout still work. Which testing type is this?
3. A new build is deployed. You quickly check that the app opens, login works, and the main page loads. Which testing type is this?
4. A small change is made to a badge filter. You focus your checks on that filter. Which testing type is this?
5. You verify that an authorized user can submit a badge-deactivation request. Is this functional or non-functional testing?
6. You measure whether a reconciliation job completes within an agreed performance target. Is this functional or non-functional testing?

### Answer Key

1. Retesting
2. Regression testing
3. Smoke testing
4. Sanity testing
5. Functional testing
6. Non-functional testing

---

**Day 3 completion goal:** Be able to explain each type in your own words, distinguish the commonly confused pairs, and give a practical example from a real application.
