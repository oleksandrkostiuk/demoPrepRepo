# Test Report — Search 2026-09-25
Environment: dev
URL: https://dev.skyline.glass/

## Notes
None — no ambiguity needed resolving (requested `env=dev` matched `PROJECT_CONFIG.json` exactly; no credentials are configured for `dev`, and this case has no login precondition, so it was not affected).

## Summary
| Total | Pass | Fail | Blocked | Flaky |
|-------|------|------|---------|-------|
| 1     | 0    | 1    | 0       | 0     |

Pass rate: 0% (flaky counted separately, not as pass)

## Results by Priority
| Priority | Total | Pass | Fail | Blocked | Flaky |
|----------|-------|------|------|---------|-------|
| Medium   | 1     | 0    | 1    | 0       | 0     |

## Failed Cases
| ID | Title | Actual Result | Screenshot |
|----|-------|---------------|------------|
| TC-SEARCH-RESULTSPAGE-003 | Whitespace-only query is handled without error | Page loaded without error, but returned only 4 results ("4 Search results for “ ”": FAQ, History, The Best Glassboard Marker, Sustainability) instead of falling back to the full site content set like the empty-query case (716 items). Consistent across 2 attempts. | screenshots/TC-SEARCH-RESULTSPAGE-003.png |

## Flaky Cases
| ID | Title | Attempt 1 | Attempt 2 |
|----|-------|-----------|-----------|

## Blocked Cases
| ID | Title | Reason |
|----|-------|--------|

## Passed Cases
| ID | Title |
|----|-------|
