# Header Live-Search Autocomplete — Test Cases
Feature: search
Scope: UI
Total: 6 cases (Critical: 0, High: 1, Medium: 2, Low: 3)

---

ID: TC-SEARCH-AUTOCOMPLETE-001
Title: Autocomplete dropdown does not appear for a 1-character query
Type: UI
Feature: search
Flow: autocomplete
Priority: Low
Tags: [boundary, negative]
Preconditions: None
Test Data: Search term: "g"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "g" using real keystroke events (not programmatic fill)
Expected Result: No autocomplete dropdown appears below the search input.
Linked Requirement: None

---

ID: TC-SEARCH-AUTOCOMPLETE-002
Title: Autocomplete dropdown does not appear for a 2-character query
Type: UI
Feature: search
Flow: autocomplete
Priority: Low
Tags: [boundary, negative]
Preconditions: None
Test Data: Search term: "gl"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "gl" using real keystroke events
Expected Result: No autocomplete dropdown appears below the search input.
Linked Requirement: None

---

ID: TC-SEARCH-AUTOCOMPLETE-003
Title: Autocomplete dropdown appears with suggestions for a 3-character query
Type: UI
Feature: search
Flow: autocomplete
Priority: High
Tags: [smoke, regression]
Preconditions: None
Test Data: Search term: "gla"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "gla" using real keystroke events
Expected Result: Autocomplete dropdown appears showing matching suggestions plus an "All results" link.
Linked Requirement: None

---

ID: TC-SEARCH-AUTOCOMPLETE-004
Title: Autocomplete suggestion list is capped at approximately 7 items plus an "All results" link
Type: UI
Feature: search
Flow: autocomplete
Priority: Medium
Tags: [boundary]
Preconditions: None
Test Data: Search term: "glass" (broad term expected to match more than 7 items)
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "glass" using real keystroke events
  4. Count the suggestion items rendered in the dropdown
Expected Result: Dropdown shows no more than ~7 suggestion items, followed by a single "All results" link at the bottom of the dropdown.
Linked Requirement: None

---

ID: TC-SEARCH-AUTOCOMPLETE-005
Title: Autocomplete suggestions update as the user continues typing
Type: UI
Feature: search
Flow: autocomplete
Priority: Medium
Tags: [regression]
Preconditions: None
Test Data: Search term typed progressively: "gla" -> "glas"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "gla" using real keystroke events and record the suggestions shown
  4. Continue typing to "glas" without clearing the field
Expected Result: Suggestion list refreshes to reflect the updated, narrower query each time, with no page reload required.
Linked Requirement: None

---

ID: TC-SEARCH-AUTOCOMPLETE-006
Title: Autocomplete dropdown closes when the search input is cleared
Type: UI
Feature: search
Flow: autocomplete
Priority: Low
Tags: [regression]
Preconditions: None
Test Data: Search term: "gla", then cleared
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Click the header search input to focus it
  3. Type "gla" using real keystroke events and confirm the dropdown is open
  4. Clear the input field completely
Expected Result: Autocomplete dropdown closes/hides.
Linked Requirement: None
