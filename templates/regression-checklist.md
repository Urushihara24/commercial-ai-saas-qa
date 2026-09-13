# Risk-based regression checklist

## Before execution

- [ ] Confirm the fix batch and original defect.
- [ ] Confirm safe QA data and reversible scope.
- [ ] Confirm browser, device, viewport, and required role.
- [ ] Identify upstream prerequisites and downstream checks.

## Original defect

- [ ] Reproduce the original flow where possible.
- [ ] Verify Expected vs Actual using current evidence.
- [ ] Record status and severity/priority.

## Affected regression

- [ ] Re-run directly dependent checks.
- [ ] Run risk-based smoke for dialog, persistence, integrations, generator, and mobile layout as applicable.
- [ ] Do not turn an upstream blocker into an unsupported downstream FAIL.
- [ ] Keep product defects separate from external known limitations.

## Evidence and closure

- [ ] Attach current direct evidence for each FAIL.
- [ ] Mark supporting evidence as supporting.
- [ ] Record BLOCKED/SKIPPED reason explicitly.
- [ ] Verify no open Blocker/Critical/Major remains without an accepted decision.
- [ ] State clearly if final regression or full E2E was not run.

