# Search API (ajax_search.php) — Test Cases
Feature: search
Scope: API
Total: 6 cases (Critical: 1, High: 1, Medium: 4, Low: 0)

Note: `ajax_search.php` is not documented in a Swagger/API spec (none was
provided for this project). Per human decision recorded in the Explorer
handoff, it still gets this dedicated direct-API test suite, separate from
the UI-driven autocomplete tests, since it is cheap to test and catches
backend-only regressions the UI wouldn't surface.

---

ID: TC-SEARCH-API-001
Title: POST to ajax_search.php with a valid search term returns matching results
Type: API
Feature: search
Flow: api
Priority: High
Tags: [smoke, regression]
Preconditions: None
Test Data: POST body: search_val=glass
Steps:
  1. Send a POST request to https://dev.skyline.glass/wp-content/themes/skyline/ajax_search.php with search_val=glass
  2. Inspect the response
Expected Result: HTTP 200 response containing a result fragment with matching search suggestions for "glass".
Linked Requirement: None

---

ID: TC-SEARCH-API-002
Title: POST to ajax_search.php with missing search_val parameter is handled gracefully
Type: API
Feature: search
Flow: api
Priority: Medium
Tags: [negative, boundary]
Preconditions: None
Test Data: POST body with no search_val parameter
Steps:
  1. Send a POST request to ajax_search.php with the search_val parameter omitted entirely
Expected Result: Endpoint responds without a server error (no HTTP 500); returns an empty result set or a defined error response.
Linked Requirement: None

---

ID: TC-SEARCH-API-003
Title: POST to ajax_search.php with empty search_val parameter is handled gracefully
Type: API
Feature: search
Flow: api
Priority: Medium
Tags: [negative, boundary]
Preconditions: None
Test Data: POST body: search_val=
Steps:
  1. Send a POST request to ajax_search.php with search_val= (empty string)
Expected Result: HTTP 200 response with an empty result set or graceful fallback; no server error.
Linked Requirement: None

---

ID: TC-SEARCH-API-004
Title: POST to ajax_search.php with missing type parameter is handled gracefully
Type: API
Feature: search
Flow: api
Priority: Medium
Tags: [negative, boundary]
Preconditions: None
Test Data: POST body: search_val=glass, type parameter omitted
Steps:
  1. Send a POST request to ajax_search.php with search_val=glass and the type parameter omitted
Expected Result: Endpoint responds without a server error; falls back to a default type/all-types behavior.
Linked Requirement: None

---

ID: TC-SEARCH-API-005
Title: ajax_search.php responds successfully without authentication
Type: API
Feature: search
Flow: api
Priority: Medium
Tags: [regression]
Preconditions: None
Test Data: POST body: search_val=glass, no auth headers/cookies sent
Steps:
  1. Send a POST request to ajax_search.php with a valid search_val, no authentication headers or cookies
Expected Result: HTTP 200 response with valid results, confirming the endpoint requires no authentication (consistent with Explorer findings — no auth surface exists for Search).
Linked Requirement: None

---

ID: TC-SEARCH-API-006
Title: XSS payload in search_val parameter is safely handled by the API
Type: API
Feature: search
Flow: api
Priority: Critical
Tags: [security]
Preconditions: None
Test Data: POST body: search_val=<script>alert(1)</script>
Steps:
  1. Send a POST request to ajax_search.php with search_val=<script>alert(1)</script>
Expected Result: HTTP 200 response; the payload is not executed and is either escaped in the response body or excluded from results; no server error.
Linked Requirement: None
