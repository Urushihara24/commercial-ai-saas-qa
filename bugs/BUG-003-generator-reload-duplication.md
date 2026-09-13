# BUG-003 — Generator duplicated the active prompt after reload

- **Severity:** Minor
- **Priority:** P2
- **Environment:** Production-safe QA run; Chrome desktop; an authenticated generator draft.
- **Preconditions:** A generator draft is open on an active step with a visible current prompt.

## Steps to Reproduce

1. Open a draft on an active generator step.
2. Confirm the current prompt appears once.
3. Reload the page.
4. Inspect the restored conversation/history and current step.

## Expected Result

The current prompt is restored once; the draft remains usable and the history does not gain an extra copy.

## Actual Result

After reload, the active prompt was duplicated in the conversation/history state.

## Evidence Strategy

Capture a before/after UI sequence with a synthetic prompt. If runtime or network evidence is useful, preserve only safe status information and omit identifiers and content that could identify the client.

## Retest Result

**PASS — fix verified.** Two consecutive reload checks did not reproduce the duplicate prompt. The separate defect concerning unsent-value persistence was not treated as the same bug.

## What this defect demonstrates

Reload/persistence testing, defect boundary discipline, and verification of a fix without collapsing adjacent state-management defects into one report.

