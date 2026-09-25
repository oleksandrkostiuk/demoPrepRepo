# "All Results" Navigation from Autocomplete Dropdown — Test Cases
Feature: search
Scope: UI
Total: 1 case (Critical: 0, High: 0, Medium: 1, Low: 0)

---

ID: TC-SEARCH-ALLRESULTSNAV-001
Title: Clicking "All results" in the autocomplete dropdown navigates to the full results page with the same query
Type: UI
Feature: search
Flow: all-results-nav
Priority: Medium
Tags: [smoke, regression]
Preconditions: None
Test Data: query="gla"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Type "gla" into the header search input, wait for the autocomplete dropdown to appear
  3. Click the "All results" link in the dropdown
Expected Result: Browser navigates to the full search results page (?s=gla) and displays the same result set as a direct search for "gla".
Linked Requirement: None
