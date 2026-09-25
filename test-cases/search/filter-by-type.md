# Result Filtering by Post Type — Test Cases
Feature: search
Scope: UI
Total: 9 cases (Critical: 0, High: 0, Medium: 9, Low: 0)

Note: per human decision recorded in the Explorer handoff, each of the 8
post-type filters gets only a lightweight "filter returns a subset" smoke
case (not the full edge-case matrix — boundary/negative cases for those are
covered once against "all results" in results-page.md).

---

ID: TC-SEARCH-FILTERBYTYPE-001
Title: Filtering search results by "project" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=project
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "project" post type filter
Expected Result: Result list updates to show only items of type "project"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-002
Title: Filtering search results by "product" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=product
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "product" post type filter
Expected Result: Result list updates to show only items of type "product"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-003
Title: Filtering search results by "case_study" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=case_study
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "case_study" post type filter
Expected Result: Result list updates to show only items of type "case_study"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-004
Title: Filtering search results by "pattern" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=pattern
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "pattern" post type filter
Expected Result: Result list updates to show only items of type "pattern"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-005
Title: Filtering search results by "color" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=color
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "color" post type filter
Expected Result: Result list updates to show only items of type "color"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-006
Title: Filtering search results by "document" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=document
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "document" post type filter
Expected Result: Result list updates to show only items of type "document"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-007
Title: Filtering search results by "post" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=post
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "post" post type filter
Expected Result: Result list updates to show only items of type "post"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-008
Title: Filtering search results by "page" post type returns a subset of results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [smoke]
Preconditions: None
Test Data: query=glass, post_type=page
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass
  2. Apply the "page" post type filter
Expected Result: Result list updates to show only items of type "page"; result count is less than or equal to the unfiltered "all results" count.
Linked Requirement: None

---

ID: TC-SEARCH-FILTERBYTYPE-009
Title: Invalid/unknown post_type filter value falls back to showing all results
Type: UI
Feature: search
Flow: filter-by-type
Priority: Medium
Tags: [negative, boundary]
Preconditions: None
Test Data: query=glass, post_type=bogus_type
Steps:
  1. Navigate to https://dev.skyline.glass/?s=glass with an unrecognized post_type filter value applied (e.g. via direct URL parameter manipulation)
Expected Result: Page does not error; falls back to displaying the unfiltered "all results" set for the query, matching TC-SEARCH-RESULTSPAGE-001 behavior.
Linked Requirement: None
