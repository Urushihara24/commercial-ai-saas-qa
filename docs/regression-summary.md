# Regression Summary

## Source QA cycle summary

- 150+ manual test cases executed.
- 20+ defects documented, with retest where verification was possible.
- P0/P1 risk coverage across authentication, AI runtime, custom agents, integrations, generator, and responsive/mobile flows.
- Targeted regression checks executed after fix batches.
- Chrome, Firefox, mobile emulation, and a real iPhone Safari device were covered.

Exact values from the source QA tracker are intentionally not published because they are unnecessary for demonstrating the work and could make the client easier to identify.

## Regression model

1. Reproduce the original defect after the fix.
2. Verify the original test case Expected Result.
3. Execute affected regression across dependent flows.
4. Run risk-based smoke for the relevant surface: dialog, persistence, integration, generator, or mobile layout.
5. Record evidence and status separately for the original defect and downstream checks.

An upstream FAIL was not automatically converted into downstream FAIL results. If a prerequisite was unreachable because of a confirmed defect, the dependent check was marked BLOCKED BY BUG.

## Verified post-fix areas

| Area | Targeted retest result |
| --- | --- |
| AI dialog/runtime | terminal responses and saved history confirmed on the primary surface |
| Generator analysis/export | core flow reached preview and safe export |
| Saved-answer/reload persistence | stored values restored in the verified scenarios |
| Integration auth semantics | no-auth flow no longer requested nonexistent credential input |
| Agent integration binding | binding persisted through save, exit, reload, and reopen |
| Notification archive | a new event no longer removed the previous stored entry |
| Error mapping | a permanent external cause was presented as permanent rather than as a transient retry condition |
| Responsive controls | status and close controls were separated at the checked widths |

## Final status limitation

The source QA snapshot was still interim. The final regression gate had not yet been run, and several complete E2E flows still required an independent rerun after individual fixes. This document therefore describes completed QA work and targeted evidence without claiming full release approval.
