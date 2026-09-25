# Full Search Results Page — Test Cases
Feature: search
Scope: UI
Total: 8 cases (Critical: 2, High: 2, Medium: 4, Low: 0)

---

ID: TC-SEARCH-RESULTSPAGE-001
Title: Full search results page displays matching results for a valid query
Type: UI
Feature: search
Flow: results-page
Priority: High
Tags: [smoke, regression]
Preconditions: None
Test Data: query=glass
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Wait for the results page to load
Expected Result: Page displays a list of results relevant to "glass" with a result count heading (e.g. "N Search results").
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-002
Title: Empty query on results page returns all site content instead of an error
Type: UI
Feature: search
Flow: results-page
Priority: Medium
Tags: [boundary, negative]
Preconditions: None
Test Data: query=(empty), URL: /?s=
Steps:
  1. Navigate to https://dev.skyline.glass/?s=
Expected Result: Page loads without error and displays the full content set (716 items observed at exploration time), not a validation error or blank state.
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-003
Title: Whitespace-only query is handled without error
Type: UI
Feature: search
Flow: results-page
Priority: Medium
Tags: [boundary, negative]
Preconditions: None
Test Data: query="   " (three spaces, URL-encoded as %20%20%20)
Steps:
  1. Navigate to https://dev.skyline.glass/?s=%20%20%20
Expected Result: Page loads without error; result set matches the same fallback behavior as an empty query (no crash, no unhandled exception).
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-004
Title: No-match query displays "0 Search results" and "No results found"
Type: UI
Feature: search
Flow: results-page
Priority: High
Tags: [smoke, negative]
Preconditions: None
Test Data: query=zzznonexistentqueryzzz
Steps:
  1. Navigate to https://dev.skyline.glass/?s=zzznonexistentqueryzzz
Expected Result: Page displays a "0 Search results" heading and a "No results found" message; no result items are rendered.
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-005
Title: XSS payload in search query is safely escaped and not executed
Type: UI
Feature: search
Flow: results-page
Priority: Critical
Tags: [security, regression]
Preconditions: None
Test Data: query=<script>alert(1)</script>
Steps:
  1. Navigate to https://dev.skyline.glass/?s=%3Cscript%3Ealert(1)%3C%2Fscript%3E
  2. Observe the rendered page and check whether any JS alert/execution occurs
Expected Result: Payload is reflected as inert, escaped text (e.g. in the "no results" message or query echo); no script executes and no alert dialog appears.
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-006
Title: SQL-injection-style payload in search query is handled safely
Type: UI
Feature: search
Flow: results-page
Priority: Critical
Tags: [security, negative]
Preconditions: None
Test Data: query=' OR 1=1 --
Steps:
  1. Navigate to https://dev.skyline.glass/?s=%27%20OR%201%3D1%20--
Expected Result: Page loads normally showing either no results or a safely filtered result set; no database error, stack trace, or evidence of query manipulation (e.g. no unintended full-content dump caused by the injection itself).
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-007
Title: Search is case-insensitive for equivalent query terms
Type: UI
Feature: search
Flow: results-page
Priority: Medium
Tags: [regression]
Preconditions: None
Test Data: "glass" vs "GLASS"
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass and record the result count and item set
  2. Navigate to https://dev.skyline.glass/?s=GLASS and record the result count and item set
Expected Result: Both queries return the same result count and the same set of items.
Linked Requirement: None

---

ID: TC-SEARCH-RESULTSPAGE-008
Title: Very long query string and special characters are handled without error
Type: UI
Feature: search
Flow: results-page
Priority: Medium
Tags: [boundary, negative]
Preconditions: None
Test Data: (a) a 500+ character random alphanumeric string; (b) the string "!@#$%^&*()_+{}:|<>?"
Steps:
  1. Navigate to https://dev.skyline.glass/?s=<500-char string, URL-encoded>
  2. Observe the page response
  3. Repeat step 1-2 with the special-character string in place of the long string
Expected Result: Page loads without a server error (no HTTP 500) for either input; displays either relevant results or a graceful "no results" state.
Linked Requirement: None
