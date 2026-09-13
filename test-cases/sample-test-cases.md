# Sample Test Cases

## TC-SAN-001 — Authentication and logout

- **Area:** Authentication
- **Priority:** P0
- **Preconditions:** Registered user; no active session.
- **Steps:** Open the login page; sign in with valid QA credentials; open a protected area; log out.
- **Expected Result:** The protected area becomes available after login; after logout the protected route requires authentication again; the session is not restored unexpectedly.

## TC-SAN-002 — AI response in dialog

- **Area:** AI dialog/runtime
- **Priority:** P0
- **Preconditions:** Authorized QA user with a positive internal balance; a ready-made AI specialist is selected.
- **Steps:** Open the dialog; send a short text message; wait for a terminal state; verify the response content and composer state.
- **Expected Result:** The message is displayed; the AI returns a meaningful terminal response; no endless waiting state or false success is shown.

## TC-SAN-003 — Dialog history persistence

- **Area:** AI dialog / persistence
- **Priority:** P1
- **Preconditions:** The dialog already contains one completed user message and AI response.
- **Steps:** Send a second message; return to the dialog list; reopen the same dialog.
- **Expected Result:** Both messages and responses remain in the correct order; reopening does not create a new empty dialog or lose history.

## TC-SAN-004 — Saved custom-agent configuration is applied in a new dialog

- **Area:** Custom AI agent
- **Priority:** P1
- **Preconditions:** Authenticated QA user; custom agent is editable.
- **Steps:** Change one observable agent setting; save; leave the editor; reload; start a new dialog with the same agent.
- **Expected Result:** The setting persists after reload and affects the new dialog; the value does not revert to the previous state.

## TC-SAN-005 — Integration with `auth:none`

- **Area:** Custom integration
- **Priority:** P1
- **Preconditions:** A safe HTTP-style specification is prepared and does not require credentials.
- **Steps:** Create an integration; select no-auth mode; provide the specification; start the connection flow; verify the result.
- **Expected Result:** The integration connects without requesting credentials that are not defined by the specification; validation errors appear only when actual specification requirements are violated.

## TC-SAN-006 — Bind integration to a custom agent

- **Area:** Custom agent / integration
- **Priority:** P1
- **Preconditions:** Integration is created and available to the QA user; custom agent is open in the editor.
- **Steps:** Select the integration; save agent settings; exit; reload; reopen the same agent.
- **Expected Result:** The binding persists and is visible after reopen; the integration remains available to the agent within the permitted scenario.

## TC-SAN-007 — Edit a previous generator answer

- **Area:** Campaign generator
- **Priority:** P1
- **Preconditions:** A generator draft contains a saved answer from an earlier step.
- **Steps:** Select Edit for the previous answer; verify the edit field; confirm the original or a new value; continue.
- **Expected Result:** The field contains the saved value; confirming the edit changes only the target step and does not clear already stored data.

## TC-SAN-008 — Active-step persistence after reload

- **Area:** Generator / reload persistence
- **Priority:** P1
- **Preconditions:** A unique QA value has been entered on the active step and the flow is not yet complete.
- **Steps:** Enter the value; confirm it is visible; reload; reopen the same draft/step.
- **Expected Result:** The value is restored after reload; the active prompt is not duplicated in history; the user can continue the flow.

## TC-SAN-009 — Mobile menu at 390 px

- **Area:** Responsive
- **Priority:** P0
- **Preconditions:** Viewport is set to exactly 390 px; a public or protected page is open.
- **Steps:** Open the mobile menu; select an item; close the menu; verify the page after close.
- **Expected Result:** Menu items are accessible; the overlay disappears after close; no horizontal scroll, clipping, or stuck overlay remains.

## TC-SAN-010 — Dialog layout on a narrow viewport

- **Area:** Responsive / AI dialog
- **Priority:** P0
- **Preconditions:** Viewport is 390 px; selected AI specialist is available.
- **Steps:** Open the dialog; inspect the panel, composer, send button, and history; send a short message.
- **Expected Result:** Critical controls are not overlapped or clipped; the response remains readable; keyboard/viewport behavior does not block the main workflow.

## TC-SAN-011 — Firefox cross-browser dialog smoke

- **Area:** Cross-browser
- **Priority:** P1
- **Preconditions:** Desktop Firefox; authorized QA data; AI specialist selected.
- **Steps:** Open the product; navigate to a dialog; send a message; wait for the response; return to the list.
- **Expected Result:** Core UI and runtime flow behave consistently with the supported Chrome baseline; no Firefox-specific console/runtime failure blocks the scenario.

## TC-SAN-012 — Real iPhone Safari mobile smoke

- **Area:** Real-device mobile
- **Priority:** P0
- **Preconditions:** Real iPhone; Safari in portrait orientation; an authorized QA scenario is available.
- **Steps:** Verify the menu; open a dialog; send a message; verify a generator step; expand FAQ.
- **Expected Result:** Touch controls are usable; the viewport does not clip critical elements; the key mobile workflow can be completed without an iOS-specific blocker.

## TC-SAN-013 — Mapping a permanent external error

- **Area:** Error handling / integration
- **Priority:** P1
- **Preconditions:** A test condition returns a known permanent external access error.
- **Steps:** Start the flow that depends on the external provider; record the safe external status/error code; compare the SaaS message with the actual error class.
- **Expected Result:** The user receives an accurate message about the permanent cause and a meaningful next step; a retry-later message is not used when retrying cannot change the result.
