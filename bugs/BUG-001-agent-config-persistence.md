# BUG-001 — Saved agent configuration was not applied to a new conversation

- **Severity:** Major
- **Priority:** P1
- **Environment:** Production-safe QA run; Chrome desktop; responsive viewport around 768 px; authenticated QA user.
- **Preconditions:** A custom AI agent exists and can be edited; a QA-visible configuration value can be changed without external side effects.

## Steps to Reproduce

1. Open the custom agent editor.
2. Change one observable configuration value.
3. Save the agent.
4. Leave the editor and reload the page.
5. Start a new conversation with the same agent.
6. Check the behavior or visible state that should reflect the saved value.

## Expected Result

The saved configuration is restored after reload and is applied to the new conversation.

## Actual Result

The save operation appeared to complete, but the subsequent conversation did not use the newly saved configuration. The previous/default behavior was observed instead.

## Evidence Strategy

Capture a causal before/save/reload/new-conversation sequence with the changed value redacted. Supporting UI state may be accompanied by a runtime observation. Do not include conversation content, user IDs, or production screenshots in a public copy.

## Retest Result

**PASS — fix verified by targeted causal retest.** A clean save → reload → new-conversation check applied the saved value. The historical full lifecycle is not presented as a blanket release sign-off.

## What this defect demonstrates

State persistence, configuration-to-runtime traceability, causal retesting, and disciplined separation of a targeted fix verification from a full regression claim.

