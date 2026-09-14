# Sanitized E2E Scenarios

These flows demonstrate how individual checks were connected into user journeys. They do not imply that every historical E2E scenario was fully rerun after every fix batch.

## E2E-SAN-001 — authentication → protected area → logout

**Preconditions:** QA account; no active session.

**Flow:** Login → open protected area → navigate to a core section → logout → attempt to reopen a protected route.

**Expected:** Access is granted after login; logout terminates the session; the protected route is no longer accessible after logout.

**Observed in source work:** PASS for the verified login/logout flow. Email-based account recovery was a separate dependency and was not mixed into this scenario.

## E2E-SAN-002 — AI specialist → dialog → response → history

**Preconditions:** Authorized QA user; ready-made AI specialist available; safe internal balance available.

**Flow:** Open specialist → send several messages → receive terminal responses → return to the dialog list → reopen the same dialog.

**Expected:** Responses complete; the dialog remains in history; message order and content persist after reopen.

**Observed in source work:** A historical runtime blocker was registered and later verified as fixed on the primary production surface. This was followed by affected regression and separate cross-browser evidence assessment.

## E2E-SAN-003 — custom agent → settings → save → reload → new dialog

**Preconditions:** Custom agent; safe integration available; QA user.

**Flow:** Change an observable setting → save → exit → reload → start a new dialog with the same agent → verify applied behavior → optionally check disabled state.

**Expected:** The saved setting persists and is applied in the new dialog; integration binding remains intact; disabled state prevents a new request.

**Observed in source work:** A persistence defect was reproduced, documented, and closed through a targeted causal retest. The complete historical lifecycle is not presented as blanket release sign-off.

## E2E-SAN-004 — campaign generator → preview → safe export

**Preconditions:** QA draft with generator-step values; known external limitations documented.

**Flow:** Start draft → complete available steps → verify edit/reload persistence → open preview → perform a safe local export.

**Expected:** Saved values are retained; preview is available; export is structurally valid; excluded external publish actions are not executed.

**Observed in source work:** The core route reached preview and safe export after a fix batch. External publishing and destructive OAuth actions remained outside the production-safe scope.

## E2E-SAN-005 — custom integration → specification → connect → persist

**Preconditions:** Safe HTTP-style specification using `auth:none`; custom agent available.

**Flow:** Create integration → provide specification → connect → bind integration to the agent → save → exit → reload → reopen.

**Expected:** No-auth mode does not request a nonexistent secret; the integration connects; binding persists after reload/reopen.

**Observed in source work:** Auth-semantics and binding-persistence failures were treated as separate defects. Both targeted flows passed after their fixes.

## E2E-SAN-006 — responsive/mobile critical workflow

**Preconditions:** 390/768 px responsive checks and a real iPhone Safari device; safe mobile scenario available.

**Flow:** Open menu → open specialist/dialog → send a message → verify a generator step → open FAQ → verify overlay close behavior.

**Expected:** Touch controls remain usable; no critical clipping, overlap, or horizontal scroll blocks the workflow; dialog and generator remain usable on mobile.

**Observed in source work:** The initial real-device/runtime run exposed an AI-response defect. The defect was fixed and verified on primary and affected surfaces, but this public repository does not claim a blanket post-fix PASS for the entire real-device E2E without a dedicated full rerun.

## Exclusions

Real payments, destructive third-party OAuth/export/bid/campaign actions, and independent testing of external services were excluded from the production-safe QA scope.
