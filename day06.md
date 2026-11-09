# Day 6 — Agile, Scrum & Sprint Execution

**Status:** Learning notes published; final Acceptance Criteria assessment and combined Day 6 review are pending.

## Learning objectives

- Understand Agile fundamentals and iterative/incremental delivery.
- Explain Scrum, its accountabilities and events.
- Understand Sprints, Sprint Goals and Sprint Backlogs.
- Distinguish Product Backlog from Sprint Backlog.
- Write and review User Stories.
- Understand Acceptance Criteria and Given–When–Then.

---

## 1. Agile Basics

Agile is an approach to software development based on iterative development, incremental delivery, continuous feedback, collaboration and adaptability.

### Iterative and incremental development

- **Iterative:** Repeatedly review and improve existing functionality.
- **Incremental:** Deliver functionality in smaller pieces, adding capability over time.

Example (illustrative PIAM delivery):
- Increment 1: Vendor Identity Management basics.
- Increment 2: PIAM access workflows.
- Increment 3: Mobile credential requests.
- Later iterations improve validation, error handling and integrations based on feedback.

An iteration may release to QA, staging or selected users; it does not necessarily mean production release every time.

### Agile Manifesto — four values

1. Individuals and interactions over processes and tools.
2. Working software over comprehensive documentation.
3. Customer collaboration over contract negotiation.
4. Responding to change over following a plan.

The items on the right still have value; Agile places greater emphasis on the items on the left.

### Shift-left testing

Shift-left means involving QA earlier: reviewing requirements, identifying ambiguity, edge cases, dependencies and testability before or during development. Early clarification can reduce rework and defect leakage.

### Waterfall vs Agile

| Waterfall | Agile |
|---|---|
| Commonly follows sequential phases | Uses iterative and incremental cycles |
| Requirements are often baselined early | Requirements can evolve through feedback |
| Testing may occur later in the lifecycle | Testing is integrated throughout delivery |
| Changes can be costly late in the process | Change is accommodated through prioritisation and planning |

---

## 2. Scrum

Scrum is a lightweight framework for developing and sustaining products through short, fixed-length Sprints. Agile describes values and principles; Scrum is one framework that can be used to apply them.

### Scrum accountabilities

**Product Owner**
- Accountable for maximising product value.
- Accountable for effective Product Backlog management.
- Orders backlog items and communicates the Product Goal.

**Scrum Master**
- Accountable for establishing Scrum and helping the team improve its effectiveness.
- Helps address impediments and supports effective Scrum events.

**Developers**
- The people in the Scrum Team who create a usable Increment each Sprint.
- This accountability includes the skills needed to deliver the product; QA is not a separate Scrum accountability.

### Scrum events

1. **Sprint:** The container event for all other Scrum events and the work needed to achieve the Sprint Goal.
2. **Sprint Planning:** Establishes why the Sprint is valuable, what can be done and how the work will be done.
3. **Daily Scrum:** Developers inspect progress toward the Sprint Goal and adapt their plan.
4. **Sprint Review:** Scrum Team and stakeholders inspect the outcome and discuss adaptations.
5. **Sprint Retrospective:** Scrum Team plans ways to improve quality and effectiveness.

**Remember:** Scrum has three accountabilities, five events and three artifacts.

### Agile vs Scrum

- Agile: a set of values and principles.
- Scrum: a specific framework with accountabilities, events and artifacts.

---

## 3. Sprint

A Sprint is a fixed-length event of one month or less. Sprints are the heartbeat of Scrum and contain the work needed to achieve the Sprint Goal and create a usable Increment.

Common team durations include one or two weeks, but Scrum's maximum is one month.

### Sprint Goal vs tasks

- **Sprint Goal:** The single objective for the Sprint; it gives the team a shared purpose.
- **Tasks:** The actionable work Developers identify to make progress toward the goal.

Illustrative PIAM Sprint Goal: “Enable eligible employees to submit mobile credential requests.”

Possible work:
- Build the request form.
- Implement eligibility validation.
- Integrate with the NFC server.
- Test successful and failed provisioning.

### QA activities during a Sprint

- Review stories and acceptance criteria during refinement and planning.
- Identify edge cases, risks, dependencies and test-data needs early.
- Prepare test scenarios and cases.
- Test as soon as a sufficiently stable feature is available.
- Retest fixes and perform risk-based regression.
- Communicate evidence-based test status and blockers.

A Sprint ending does not automatically make unfinished work “Done.” The work must satisfy the team's Definition of Done to be part of the Increment. If required testing is incomplete, the item may not meet that definition.

### Sprint vs iteration

A Sprint is a specific Scrum timebox. Iteration is a broader term for a repeated development cycle. A Sprint is iterative, but not every iteration is a Scrum Sprint.

### Scope changes during a Sprint

The Sprint Goal should not be endangered. Scope can be clarified and renegotiated with the Product Owner as more is learned. Quality should not decrease.

---

## 4. Product Backlog

The Product Backlog is an emergent, ordered list of what is needed to improve the product. It can include features, enhancements, bug fixes, security work and technical improvements.

The **Product Owner is accountable** for effective Product Backlog management.

Illustrative PIAM items:
- Mobile credential provisioning.
- Duplicate-request validation.
- Badge deactivation enhancement.
- Reconciliation dashboard.
- Reconciliation performance improvement.

### Product Backlog vs Sprint Backlog

| Product Backlog | Sprint Backlog |
|---|---|
| Ordered list of product work | Sprint Goal, selected Product Backlog items and actionable delivery plan |
| Product Owner is accountable for its management | Developers create and adapt it |
| Evolves as the product and context change | Updated throughout the Sprint as more is learned |
| Covers product work beyond the current Sprint | Focuses on the current Sprint |

A Sprint Backlog is not a list of Sprints. It is the plan for the current Sprint.

### Backlog Refinement

Backlog Refinement is an ongoing activity, not a formal Scrum event. The team may clarify items, split large items, add detail, identify dependencies and estimate effort. QA contributes by identifying missing scenarios, validation rules and testability concerns.

---

## 5. User Stories

A User Story is a short description of a requirement from the perspective of the person who needs the functionality.

### Standard format

**As a** [type of user],  
**I want** [functionality],  
**So that** [benefit or purpose].

Illustrative PIAM example:

“As an employee, I want to request a mobile credential through the PIAM application so that I can access authorised office areas using my mobile phone instead of a physical badge.”

- “As an employee” identifies who.
- “I want to request a mobile credential” describes what.
- “So that…” explains why / business value.

A User Story describes the user's need, not necessarily the technical implementation.

### User Story vs test scenario vs test case

| Term | Meaning | PIAM example |
|---|---|---|
| User Story | User need and value | Employee can request a mobile credential |
| Test Scenario | High-level behaviour to verify | Verify mobile credential request |
| Test Case | Detailed steps, data and expected result | Submit a valid request and verify its status |

### INVEST principles

- **I — Independent:** As independent as practical from other stories.
- **N — Negotiable:** Details can be discussed and refined.
- **V — Valuable:** Provides value to users or the business.
- **E — Estimable:** The team can estimate the effort.
- **S — Small:** Small enough to complete within a Sprint.
- **T — Testable:** Clear enough to verify.

### QA review of User Stories

For “An employee can request a mobile credential,” QA should clarify:
- Which employees are eligible?
- What if an active credential already exists?
- What if a previous request is pending?
- What if provisioning fails on the NFC server?
- What status and message should be displayed?
- What if two identical requests are submitted simultaneously?

Do not assume unspecified business behaviour. Clarify it with the Product Owner and team.

---

## 6. Acceptance Criteria

Acceptance Criteria are specific conditions that a feature must satisfy to meet the agreed requirement.

### User Story vs Acceptance Criteria vs Test Cases

- **User Story:** What does the user need and why?
- **Acceptance Criteria:** What conditions must be satisfied?
- **Test Cases:** How will QA verify those conditions?

Illustrative User Story:

“As an employee, I want to request a mobile credential through PIAM so that I can access authorised office areas using my mobile phone.”

Possible Acceptance Criteria (subject to confirmation of business rules):
1. Only eligible employees can submit a mobile credential request.
2. If duplicate active credentials are prohibited, an employee with an active credential cannot submit another request.
3. Duplicate pending requests are prevented if that is the agreed rule.
4. Successful submission creates a request and displays the appropriate status.
5. Provisioning failure is reflected with an appropriate status or message.

### Given–When–Then

A common BDD-style format for expressing behaviour:

- **Given:** Initial condition / precondition.
- **When:** Action performed.
- **Then:** Expected outcome.

Example:

**Given** an employee already has a pending mobile credential request,  
**When** the employee attempts to submit another request,  
**Then** the system prevents the duplicate submission and displays the agreed message.

### Positive and negative scenarios

| Positive | Negative |
|---|---|
| Eligible employee submits a request | Ineligible employee submits a request |
| Request is created successfully | Duplicate request is submitted |
| Provisioning succeeds | NFC server returns an error |
| Authorised user deactivates a badge | Unauthorised user attempts deactivation |

QA should test both successful and unsuccessful behaviour. Acceptance Criteria should be clear, specific, observable and testable. Clarify ambiguous or missing rules rather than inventing expected behaviour.

### Deriving test cases

For the criterion “Employees with an active mobile credential cannot submit another request,” QA might test:
- Employee with active credential.
- Employee without active credential but otherwise eligible.
- Employee with a pending request.
- Employee whose previous request failed (expected behaviour must be clarified).
- Two simultaneous submissions (if concurrency protection is in scope).

---

## Revision checklist

- [ ] Explain Agile, iterative and incremental development.
- [ ] Recall the four Agile Manifesto values.
- [ ] Distinguish Agile from Scrum.
- [ ] Explain the three Scrum accountabilities.
- [ ] Recall the five Scrum events.
- [ ] Explain Sprint Goal vs Sprint tasks.
- [ ] Distinguish Product Backlog from Sprint Backlog.
- [ ] Explain why Backlog Refinement is not a formal Scrum event.
- [ ] Write a User Story in As a / I want / So that format.
- [ ] Recall all six INVEST principles.
- [ ] Write Acceptance Criteria and Given–When–Then examples.

## Assessments and progress

Topic-level assessments were attempted conversationally for Agile Basics, Scrum, Sprint, Product Backlog and User Stories. Recorded indicative scores:
- Agile Basics: 8/10.
- Scrum: 9/10.
- Sprint: 7/10.
- Product Backlog: 7.5/10.
- User Stories: 8/10.

The Acceptance Criteria lesson has been covered. Its assessment is still pending, as is the combined Day 6 review/assessment. These should be completed before marking Day 6 fully complete.

## Important corrections to remember

- Scrum is an Agile framework, not simply a methodology.
- Scrum's maximum Sprint duration is one month, not 2–4 weeks.
- A Sprint is iterative; it is not merely a module delivery period.
- Sprint Backlog is not a collection of Sprints.
- Backlog Refinement is ongoing work, not a formal Scrum event.
- In INVEST, T means Testable; I means Independent.
- QA is included within the Developers accountability in Scrum, not a separate Scrum accountability.
- A feature is not automatically Done just because a Sprint ends; it must meet the Definition of Done.
