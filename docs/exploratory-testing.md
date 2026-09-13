# Exploratory Testing

Exploratory testing was used as a time-boxed way to investigate risks that could not be fully expressed through a single happy-path test case.

## Charters

### 1. AI runtime and terminal states

Checks covered prolonged waiting, missing responses, repeated submission, result persistence, and reopen behavior. This helped isolate a runtime defect as a separate Critical/P0 risk instead of mixing it with UI layout concerns.

### 2. Persistence and reload

Checks covered stored generator answers, values entered on the active step, duplicate prompts after reload, and whether custom-agent settings were applied in a new dialog. Adjacent symptoms were documented separately when their Expected Results or causal sequences differed.

### 3. Custom integrations

Checks covered authentication semantics, validity of HTTP-style specifications, connection flow, safe binding persistence, and reopening the linked agent. No-auth behavior and binding persistence were treated as separate defect classes.

### 4. Notification/event history

Checks focused on archive integrity after a new event appeared: append behavior, ordering, and retention of the previous record. No real payment action was executed.

### 5. Error communication

External status/error codes were compared with the actual permanence of the condition and the message presented to the user. An external limitation was not classified as a product BUG unless the SaaS-side Expected Result was violated.

### 6. Responsive interaction

Coverage went beyond page load and included hit areas, overlays, dialogs, footer/header behavior, clipping, overlap, horizontal scroll, and generator-control usability at narrow widths.

## Outcome of exploratory work

Exploratory checks extended defect discovery beyond mandatory test cases and surfaced additional issues in notification history, disabled-agent UX, integration-form behavior, and error mapping. Only six representative defect classes are included in this portfolio repository.
