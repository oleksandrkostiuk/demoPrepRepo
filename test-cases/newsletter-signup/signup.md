# Newsletter Signup — Test Cases
Feature: newsletter-signup
Scope: UI
Total: 8 cases (Critical: 1, High: 3, Medium: 3, Low: 1)

---

ID: TC-NEWSLETTER-SIGNUP-001
Title: Valid email is accepted and redirects to the thank-you page
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: Critical
Tags: [smoke, regression]
Preconditions: None
Test Data: email=user@gmail.com
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter "user@gmail.com" in the email field
  4. Submit the form
Expected Result: Browser performs a full-page redirect to `/thanks-for-subscribing-to-our-newsletter/`, displaying "Thank you for signing up for our newsletter" and "Be on the look for an email from us." A stale default inline confirmation may flash briefly during the AJAX-to-redirect transition on slow loads — note this if observed, but it does not affect pass/fail.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-002
Title: Empty email submission is rejected with a required-field error
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: High
Tags: [negative]
Preconditions: None
Test Data: email=(empty)
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Leave the email field empty
  4. Submit the form
Expected Result: Form displays the inline error "This field is required."; no redirect to the thank-you page occurs.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-003
Title: Malformed email format is rejected with a format error
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: High
Tags: [negative, boundary]
Preconditions: None
Test Data: email=notanemail
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter "notanemail" in the email field
  4. Submit the form
Expected Result: Form displays the inline error "The email address entered is invalid, please check the formatting (e.g. email@domain.com)."; no redirect to the thank-you page occurs.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-004
Title: Whitespace-only value in the email field is not accepted as valid
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: Medium
Tags: [negative, boundary]
Preconditions: None
Test Data: email="   " (three spaces)
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter three space characters in the email field
  4. Submit the form
Expected Result: Submission is not treated as successful — either the required-field error ("This field is required.") or the invalid-format error is displayed; no redirect to the thank-you page occurs.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-005
Title: Plus-addressed valid email is accepted like any other valid address
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: Medium
Tags: []
Preconditions: None
Test Data: email=user+tag@gmail.com
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter "user+tag@gmail.com" in the email field
  4. Submit the form
Expected Result: Same success behavior as a plain valid address — full-page redirect to `/thanks-for-subscribing-to-our-newsletter/` with the standard thank-you messaging.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-006
Title: Resubmitting an already-subscribed email succeeds identically (idempotent, no differentiation)
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: Medium
Tags: []
Preconditions: The test email address has already been submitted successfully once before (e.g. reuse the address from TC-NEWSLETTER-SIGNUP-001 after it has run).
Test Data: email=user@gmail.com (same address as a prior successful signup)
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter the previously-subscribed email address again
  4. Submit the form
Expected Result: Redirects to `/thanks-for-subscribing-to-our-newsletter/` with the identical success messaging as a first-time signup — no "already subscribed" differentiation, by design.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-007
Title: XSS/script-injection string in the email field is not executed
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: High
Tags: [security, negative]
Preconditions: None
Test Data: email=<script>alert(1)</script>@x.com
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter "<script>alert(1)</script>@x.com" in the email field
  4. Submit the form
Expected Result: No JavaScript executes (no alert dialog); the payload fails email-format validation and the form displays the standard invalid-email-format error, same as TC-NEWSLETTER-SIGNUP-003. No redirect occurs and no server error is triggered.
Linked Requirement: None

---

ID: TC-NEWSLETTER-SIGNUP-008
Title: Very long email string is handled without a server error
Type: UI
Feature: newsletter-signup
Flow: signup
Priority: Low
Tags: [boundary]
Preconditions: None
Test Data: email=a 254-character address: 244 lowercase "a" characters followed by "@gmail.com"
Steps:
  1. Navigate to https://dev.skyline.glass/
  2. Scroll to the site-wide footer newsletter signup form
  3. Enter the 254-character email string in the email field
  4. Submit the form
Expected Result: No server error (no HTTP 500, no crash). Either the form accepts it and redirects to the thank-you page like a normal valid address, or it is rejected with the standard invalid-email-format/length error — either outcome is acceptable as long as it is handled gracefully.
Linked Requirement: None
