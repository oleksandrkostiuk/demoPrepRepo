# Search — Test Cases

| Flow | Cases | Critical | High | Medium | Low | Status |
|------|-------|----------|------|--------|-----|--------|
| autocomplete | 6 | 0 | 1 | 2 | 3 | covered |
| results-page | 8 | 2 | 2 | 4 | 0 | covered |
| filter-by-type | 9 | 0 | 0 | 9 | 0 | covered |
| pagination | 3 | 0 | 0 | 1 | 2 | covered |
| all-results-nav | 1 | 0 | 0 | 1 | 0 | covered |
| api | 6 | 1 | 1 | 4 | 0 | covered |

Coverage: 5/5 flows (100%) — plus one additional dedicated API suite
(`api`) covering `ajax_search.php` directly, per human decision recorded
in the Explorer handoff (not one of the 5 UI flows Explorer originally
identified, but added because it's cheap to test and catches backend-only
regressions the UI wouldn't surface).

## Open risks carried from Explorer handoff
- Priority for Search's happy-path flow was not explicitly confirmed by the
  human; proceeded with the suggested default of **High**. See PR
  description for details.
