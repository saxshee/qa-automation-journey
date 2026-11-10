# Day 13 — E-commerce Website Test Cases

**Status:** In Progress  
**Goal:** Create 30 test cases for an e-commerce website, covering the shopping journey from login through order confirmation.

## Application modules and planned coverage

| Module | Planned test cases |
|---|---:|
| Login and Registration | 4 |
| Product Search | 4 |
| Product Details | 3 |
| Cart | 5 |
| Wishlist | 3 |
| Checkout | 5 |
| Payment | 4 |
| Order Confirmation | 2 |
| **Total** | **30** |

## Test case structure

A test case should capture:
- Test Case ID
- Test Scenario
- Preconditions
- Test Steps
- Test Data
- Expected Result
- Actual Result
- Status (Pass/Fail/Blocked/Not Executed, as applicable)

## Module 1 — Login and Registration

Initial examples discussed:

| Test Case ID | Test scenario | Expected result |
|---|---|---|
| TC_001 | Login with valid credentials | User logs in successfully |
| TC_002 | Login with incorrect password | Appropriate error message appears |
| TC_003 | Login with blank username and password | Required-field validation appears |
| TC_004 | Register using an already registered email | Registration is rejected with an appropriate message |

## Module 2 — Product Search

### TC_005 — Search using an existing product name

- **Steps:**
  1. Navigate to the search bar.
  2. Enter the name of an existing product.
  3. Press Enter.
- **Test data:** iPhone 16
- **Expected result:** Relevant products matching the search keyword are displayed.

### TC_006 — Search using a product that does not exist

- **Steps:**
  1. Navigate to the search bar.
  2. Enter a product name that does not exist.
  3. Press Enter.
- **Test data:** XYZ123Unknown
- **Expected result:** No matching products are displayed. A helpful message such as "No products found" appears; the page remains functional and does not crash.
- **Learning note:** A blank screen is not necessarily the expected behavior. The exact message should follow the product requirement.

### TC_007 — Search using a partial product name

- **Steps:**
  1. Navigate to the search bar.
  2. Enter part of an existing product name.
  3. Press Enter.
- **Test data:** iPho
- **Expected result:** Products matching the partial keyword (for example, iPhone 15 and iPhone 16) are displayed, provided partial matching is supported by the requirements.

## Learning notes

- Search results should match the entered keyword or supported partial keyword.
- For a product that does not exist, verify both the absence of results and a useful empty-state message.
- Do not assume a search behavior that is not specified in the requirements; confirm whether partial matching and category-based search are supported.

## Progress

- [x] Product Search: 3 test cases drafted and reviewed.
- [ ] Product Search: 1 more test case (empty search field).
- [ ] Product Details, Cart, Wishlist, Checkout, Payment, and Order Confirmation.
- [ ] Complete and review all 30 test cases.

**Day 13 remains in progress.** The 30-test-case exercise will be completed module by module, one test case at a time.
