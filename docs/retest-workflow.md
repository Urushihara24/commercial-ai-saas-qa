# Retest Workflow

## Flow

```text
fix batch
   ↓
reproduce original defect
   ↓
verify original Expected Result
   ↓
affected regression / risk-based smoke
   ↓
record evidence and status
```

## What is recorded

- original defect and its severity/priority;
- fix batch/build and environment;
- exact reproduction steps;
- Expected vs Actual;
- direct or supporting evidence;
- status of the original defect;
- downstream test cases/E2E scenarios that became available or remained BLOCKED;
- evidence limitations and unfinished checks.

## Selected retest outcomes

| Public defect | Retest outcome | Verification |
| --- | --- | --- |
| BUG-001 | PASS | saved agent configuration applied in a new dialog after reload |
| BUG-002 | PASS | `auth:none` flow completed without nonexistent credential input |
| BUG-003 | PASS | duplicate prompt did not reproduce after consecutive reloads |
| BUG-004 | PASS | a new notification did not replace the previous history item |
| BUG-005 | PASS | permanent external error received the correct SaaS-side message |
| BUG-006 | PASS | status and close controls had separate hit areas at the checked viewports |

## Evidence discipline

PASS is assigned only when the Expected Result is confirmed. Historical screenshots are not reused as new retest evidence. If a direct causal artifact is unavailable, that limitation is stated explicitly rather than presenting supporting evidence as stronger proof.
