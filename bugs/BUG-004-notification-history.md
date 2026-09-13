# BUG-004 — A new debit notification replaced an earlier history item

- **Severity:** Major
- **Priority:** P1
- **Environment:** Production-safe QA run; Chrome desktop; authenticated QA user; existing safe notification sequence.
- **Preconditions:** Notification history contains one earlier debit event; a new permitted QA event can be observed without executing a real payment.

## Steps to Reproduce

1. Open the notification archive and confirm the earlier debit event.
2. Trigger or observe one new permitted QA event.
3. Return to the notification archive.
4. Compare the new and earlier entries.

## Expected Result

The new notification is appended or inserted according to the documented ordering, while the earlier notification remains available with its original content.

## Actual Result

After the new event appeared, the earlier debit notification was missing or replaced in the archive.

## Evidence Strategy

Use a redacted before/after UI capture with synthetic amounts and dates. Do not perform real payments, include account balances, or publish notification IDs.

## Retest Result

**PASS — fix verified by a causal archive flow.** The new event appeared without replacing the earlier event. No external payment action was used during verification.

## What this defect demonstrates

Event-history integrity, persistence checks, safe financial-adjacent QA, and evidence that distinguishes append/replace behavior.

