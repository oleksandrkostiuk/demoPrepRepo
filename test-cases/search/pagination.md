# Search Results Pagination — Test Cases
Feature: search
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 1, Low: 2)

---

ID: TC-SEARCH-PAGINATION-001
Title: Navigating to the next page of search results shows the next set of items
Type: UI
Feature: search
Flow: pagination
Priority: Medium
Tags: [regression]
Preconditions: None
Test Data: query=glass (broad query expected to span multiple result pages)
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Note the items displayed on page 1
  3. Click the "next page" / page 2 pagination control
Expected Result: Page 2 loads showing a different, subsequent set of results (no duplication of page 1 items); the pagination control indicates page 2 is active.
Linked Requirement: None

---

ID: TC-SEARCH-PAGINATION-002
Title: Last page of search results shows no "next" control
Type: UI
Feature: search
Flow: pagination
Priority: Low
Tags: [boundary]
Preconditions: None
Test Data: query=glass, navigate to the final page
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Navigate to the last available page via the pagination controls
Expected Result: The "next" control is disabled or absent on the last page; results shown are the final remaining items (item count may be less than a full page).
Linked Requirement: None

---

ID: TC-SEARCH-PAGINATION-003
Title: Direct navigation to an out-of-range page number is handled gracefully
Type: UI
Feature: search
Flow: pagination
Priority: Low
Tags: [boundary, negative]
Preconditions: None
Test Data: query=glass, page=9999
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass&paged=9999 (or the site's equivalent page parameter)
Expected Result: Page loads without a server error; displays either a "no results" state, a redirect to the last valid page, or an empty results list — no crash/HTTP 500.
Linked Requirement: None
