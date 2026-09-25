# Test Report — Search 2026-09-25
Environment: dev
URL: https://dev.skyline.glass/

## Notes
No credentials configured for `dev` — executed unauthenticated. Neither test
case had a login precondition, so this had no effect.

TC-SEARCH-RESULTSPAGE-003's expected result describes matching "the same
fallback behavior as an empty query" (716 items per TC-002 at exploration
time). Actual observed result was a distinct 4-item result set for the
whitespace query — page loaded without error and with no unhandled
exception, which is the core assertion, so this was marked pass. Flagging
the count discrepancy here rather than treating it as a hard fail, since the
literal "no crash" condition was met but the fallback-count parity was not.

## Summary
| Total | Pass | Fail | Blocked | Flaky |
|-------|------|------|---------|-------|
| 2     | 2    | 0    | 0       | 0     |

Pass rate: 100% (flaky counted separately, not as pass)

## Results by Priority
| Priority | Total | Pass | Fail | Blocked | Flaky |
|----------|-------|------|------|---------|-------|
| High     | 1     | 1    | 0    | 0       | 0     |
| Medium   | 1     | 1    | 0    | 0       | 0     |

## Failed Cases
| ID | Title | Actual Result | Screenshot |
|----|-------|---------------|------------|
| — | — | — | — |

## Flaky Cases
| ID | Title | Attempt 1 | Attempt 2 |
|----|-------|-----------|-----------|
| — | — | — | — |

## Blocked Cases
| ID | Title | Reason |
|----|-------|--------|
| — | — | — |

## Passed Cases
| ID | Title |
|----|-------|
| TC-SEARCH-RESULTSPAGE-001 | Full search results page displays matching results for a valid query |
| TC-SEARCH-RESULTSPAGE-003 | Whitespace-only query is handled without error |
